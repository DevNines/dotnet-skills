# Hangfire v1.8.23 — patterns

## What Hangfire is

Hangfire solves a recurring backend problem: a lot of work — sending emails,
generating reports, cleaning up data, calling slow third-party APIs, running
nightly aggregations — should not happen inside an HTTP request. The request
needs to return quickly; the work needs to happen *reliably*, survive process
restarts, and be observable. Rolling your own durable queue + scheduler +
retry policy + dashboard is a serious amount of plumbing.

Hangfire's mental model is unusual but powerful: you write a normal C# method
call as an expression (`() => svc.SendInvoice(orderId)`), and Hangfire
**serializes the method-call metadata plus arguments** to persistent storage
(SQL Server, in this skill). A `BackgroundJobServer` polls that storage, picks
up the entry, re-resolves the target type through the `JobActivator`,
deserializes the arguments, and re-invokes the method. If it throws, the
`AutomaticRetryAttribute` filter reschedules it. Because everything lives in
storage, jobs survive process restarts and Hangfire delivers them
**at-least-once**.

Four job types cover the vast majority of needs:

- **Fire-and-forget** — `Enqueue(...)`, run once, soon, in the background.
- **Delayed** — `Schedule(..., delay)`, run once, later.
- **Recurring** — `RecurringJob.AddOrUpdate(id, ..., cron)`, run on a cron.
- **Continuation** — `ContinueJobWith(parentId, ...)`, run after another job
  finishes.

Where Hangfire does **not** belong:

- **Sub-second / in-request latency.** Storage round-trips plus the
  `SchedulePollingInterval` add latency. Hangfire is for work you can do
  "soon", not "now".
- **Hard real-time or exactly-once.** It is **at-least-once**. A job can run
  twice (worker crash after the method runs but before storage is updated,
  retries after transient infra failures, etc.). Design idempotent jobs; if
  you need exactly-once, add your own dedup key.
- **Heavy fan-out / streaming / event processing.** Use a real broker
  (Kafka, RabbitMQ, Azure Service Bus). Hangfire is a durable *job* system.

## Non-negotiable job design rules

```csharp
// 1. Pass IDs, not entities. Arguments are serialized and may be replayed
//    minutes or hours later — entities go stale and bloat storage.
_client.Enqueue<IInvoiceService>(s => s.SendInvoice(orderId));   // ✅
// _client.Enqueue<IInvoiceService>(s => s.SendInvoice(orderEntity)); // ❌

// 2. Never close over request state. Resolve dependencies inside the job
//    via the generic Enqueue<T> form so DI gives you fresh scopes.
_client.Enqueue<IReportService>(s => s.RunDaily(reportId));      // ✅
// _client.Enqueue(() => MyController.Build(_dbContext, ...));   // ❌

// 3. Make jobs idempotent. At-least-once means "may run twice".
public async Task SendInvoice(Guid orderId)
{
    if (await _db.IsInvoiceSent(orderId)) return;   // guard
    await _mailer.SendAsync(orderId);
    await _db.MarkInvoiceSent(orderId);
}

// 4. Keep arguments small and serializable: primitives, Guids, small DTOs.
//    No DbContext, HttpContext, CancellationTokens you own, no Streams,
//    no polymorphic graphs.

// 5. Register recurring jobs at STARTUP exactly once — not in a controller.
//    (See the Program.cs example below.)

// 6. Secure the dashboard. An unguarded /hangfire lets anyone on the
//    internet enqueue or delete jobs.
```

## Which job type to use

| Goal | API (verified in surface) |
|------|---------------------------|
| Run once, soon, in the background | `IBackgroundJobClient.Enqueue<T>(s => s.Do(id))` |
| Run once, after a delay or at a moment | `IBackgroundJobClient.Schedule<T>(s => s.Do(id), TimeSpan / DateTimeOffset)` |
| Run on a repeating schedule | `IRecurringJobManager.AddOrUpdate<T>(id, s => s.Do(), cron)` |
| Run only after a parent job finishes | `IBackgroundJobClient.ContinueJobWith<T>(parentId, s => s.Do())` |
| Route to a specific queue | `[Queue("critical")]` on the method, or the `queue` parameter overloads on `Enqueue`/`Schedule`/`ContinueJobWith` |
| Limit retry attempts | `[AutomaticRetry(Attempts = 3)]` on the method |
| Prevent concurrent execution of the same method | `[DisableConcurrentExecution(timeoutInSeconds: 60)]` |

Cron strings: prefer the `Cron` helpers — `Cron.Daily()`, `Cron.Hourly()`,
`Cron.MinuteInterval(15)`, `Cron.Weekly(DayOfWeek.Monday, 3, 30)`, etc.

## Where each piece of code belongs

| Concern | Location |
|---------|----------|
| `AddHangfire`, `AddHangfireServer`, `UseSqlServerStorage` | `Program.cs` / startup |
| `UseHangfireDashboard` middleware | `Program.cs`, **after** auth middleware |
| Recurring-job registration (`RecurringJob.AddOrUpdate` / `IRecurringJobManager.AddOrUpdate`) | A single seeding step at startup |
| `IBackgroundJobClient.Enqueue` / `Schedule` / `ContinueJobWith` calls | Application/service layer |
| The job method body | A normal injectable service — public, resolvable, idempotent |

## Startup wiring (ASP.NET Core, SQL Server)

```csharp
using Hangfire;
using Hangfire.SqlServer;

var builder = WebApplication.CreateBuilder(args);

builder.Services.AddHangfire((sp, cfg) => cfg
    .SetDataCompatibilityLevel(CompatibilityLevel.Version_180)
    .UseSimpleAssemblyNameTypeSerializer()
    .UseRecommendedSerializerSettings()
    .UseSqlServerStorage(
        builder.Configuration.GetConnectionString("Hangfire"),
        new SqlServerStorageOptions
        {
            CommandBatchMaxTimeout       = TimeSpan.FromMinutes(5),
            SlidingInvisibilityTimeout   = TimeSpan.FromMinutes(5),
            QueuePollInterval            = TimeSpan.Zero,
            UseRecommendedIsolationLevel = true,
            DisableGlobalLocks           = true,
        }));

builder.Services.AddHangfireServer(options =>
{
    options.WorkerCount = Environment.ProcessorCount * 5;
    options.Queues      = new[] { "critical", "default" };
});

builder.Services.AddScoped<IInvoiceService, InvoiceService>();

var app = builder.Build();

app.UseAuthentication();
app.UseAuthorization();

app.UseHangfireDashboard("/hangfire", new DashboardOptions
{
    Authorization = new[] { new AdminOnlyAuthorizationFilter() },
    IsReadOnlyFunc = ctx => false,
});

// Seed recurring jobs exactly once at startup.
using (var scope = app.Services.CreateScope())
{
    var recurring = scope.ServiceProvider.GetRequiredService<IRecurringJobManager>();
    recurring.AddOrUpdate<IReportService>(
        "daily-rollup",
        svc => svc.RunDailyRollup(),
        Cron.Daily(hour: 2));
}

app.MapControllers();
app.Run();
```

## Securing the dashboard

```csharp
using Hangfire.Dashboard;

public sealed class AdminOnlyAuthorizationFilter : IDashboardAuthorizationFilter
{
    public bool Authorize(DashboardContext context)
    {
        var http = context.GetHttpContext();
        return http.User.Identity?.IsAuthenticated == true
            && http.User.IsInRole("Admin");
    }
}
```

For local-only access during dev, `LocalRequestsOnlyAuthorizationFilter` is
built in.

## Static façade vs. injected interfaces

The `BackgroundJob` and `RecurringJob` static classes are convenient but hard
to test. In DI code, inject `IBackgroundJobClient` and `IRecurringJobManager`
— they're registered by `AddHangfire`.

```csharp
public sealed class CheckoutService
{
    private readonly IBackgroundJobClient _jobs;

    public CheckoutService(IBackgroundJobClient jobs) => _jobs = jobs;

    public Task PlaceOrderAsync(Guid orderId)
    {
        // Fire-and-forget: run as soon as a worker picks it up.
        _jobs.Enqueue<IInvoiceService>(s => s.SendInvoice(orderId));

        // Delayed: poke the customer in 24h if they haven't paid.
        var followUpId = _jobs.Schedule<IDunningService>(
            s => s.RemindIfUnpaid(orderId),
            TimeSpan.FromHours(24));

        // Continuation: archive only after the reminder ran.
        _jobs.ContinueJobWith<IArchiveService>(
            followUpId,
            s => s.Archive(orderId));

        return Task.CompletedTask;
    }
}
```

## Retries & failure handling

`AutomaticRetryAttribute` is registered globally by default (10 attempts).
Override per-method when needed.

```csharp
using Hangfire;

public sealed class PaymentJob
{
    [AutomaticRetry(
        Attempts             = 5,
        DelaysInSeconds      = new[] { 10, 30, 60, 300, 900 },
        OnAttemptsExceeded   = AttemptsExceededAction.Fail,   // or Delete
        LogEvents            = true)]
    [Queue("critical")]
    [DisableConcurrentExecution(timeoutInSeconds: 120)]
    public async Task ChargeAsync(Guid paymentId)
    {
        // Throwing is the signal to retry. Don't swallow transient failures.
        await _gateway.ChargeAsync(paymentId);
    }
}
```

When attempts are exhausted and `OnAttemptsExceeded = Fail`, the job lands in
the **Failed** state and is visible in the dashboard until a human (or another
process) requeues or deletes it. With `Delete`, it goes straight to the
Deleted state and expires per `JobExpirationTimeout`.

## Testing

Job methods are just service methods — unit-test them directly:

```csharp
[Fact]
public async Task SendInvoice_is_idempotent()
{
    var db     = new FakeInvoiceDb { AlreadySent = { OrderId } };
    var mailer = new SpyMailer();
    var svc    = new InvoiceService(db, mailer);

    await svc.SendInvoice(OrderId);
    await svc.SendInvoice(OrderId);   // simulated retry

    Assert.Equal(0, mailer.SendCount);
}
```

For the enqueue path, inject `IBackgroundJobClient` as a substitute and
assert it was called. Do **not** stand up a real `BackgroundJobServer` in
unit tests — that's an integration concern.

## Things to avoid

- **Passing entities, `DbContext`, `HttpContext`, large payloads, or streams
  as job arguments.** Pass IDs.
- **Assuming exactly-once.** Hangfire is at-least-once; bake in idempotency.
- **Non-idempotent jobs** (e.g. sending money without a dedup key).
- **Registering recurring jobs in a controller / request handler.** That
  re-registers them on every call. Do it once at startup.
- **Mounting `/hangfire` without an `IDashboardAuthorizationFilter`** — by
  default ASP.NET Core middleware allows remote access, and the default
  filter only allows local. Always wire `DashboardOptions.Authorization`
  explicitly in production.
- **Hardcoded connection strings or dashboard credentials.** Use config /
  user-secrets / KeyVault.
- **`async void` job methods.** Use `Task` (the surface has `Func<Task>` and
  `Func<T, Task>` overloads of `Enqueue` / `Schedule` / `ContinueJobWith`).
- **Heavy CPU-bound work without bounding `WorkerCount`.** Default workers
  is `5 * Environment.ProcessorCount`; cap it on small boxes.
- **Catching and swallowing exceptions inside a job** — you've just told
  Hangfire it succeeded, defeating retries.
- **Relying on members that aren't in this version's API surface.** If it
  isn't listed for v1.8.23, it doesn't exist here.
