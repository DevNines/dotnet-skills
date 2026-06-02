```markdown
<!-- examples-v1.8.23.md -->
<!-- Generated for Hangfire v1.8.23. Do not edit by hand — rerun the update script. -->

# Hangfire v1.8.23 — Canonical Examples

Working examples for the Hangfire family at v1.8.23 (Core + SqlServer + AspNetCore/NetCore wiring). Snippets assume `using Hangfire;` is in scope.

## 1. Startup wiring (ASP.NET Core)

`AddHangfire` configures the global settings; `AddHangfireServer` registers the
processing server as a hosted service. The connection string comes from
`IConfiguration`, never inlined.

```csharp
using Hangfire;
using Hangfire.SqlServer;

var builder = WebApplication.CreateBuilder(args);

builder.Services.AddHangfire(cfg => cfg
    .SetDataCompatibilityLevel(CompatibilityLevel.Version_180)
    .UseSimpleAssemblyNameTypeSerializer()
    .UseRecommendedSerializerSettings()
    .UseSqlServerStorage(builder.Configuration.GetConnectionString("Hangfire")));

builder.Services.AddHangfireServer();

var app = builder.Build();
app.UseHangfireDashboard("/hangfire");
app.Run();
```

Notes:
- `AddHangfire` / `AddHangfireServer` come from the `Hangfire.NetCore` (or `Hangfire.AspNetCore`) package, not `Hangfire.Core`.
- `UseHangfireDashboard` is an `IApplicationBuilder` extension here; an OWIN extension with the same name also exists in Core.
- Lock the data format with `SetDataCompatibilityLevel(CompatibilityLevel.Version_180)` for new installs.

## 2. Fire-and-forget

Two equivalent forms: the static façade and the injected client. Both go through `IBackgroundJobClient.Create` under the hood.

```csharp
// Static façade — fine for ad-hoc enqueueing.
BackgroundJob.Enqueue(() => emailService.Send(orderId));

// Injected client — preferred in services; the generic overload resolves
// the target type from DI on the server.
public sealed class CheckoutService(IBackgroundJobClient jobs)
{
    public void Checkout(int orderId) =>
        jobs.Enqueue<IEmailService>(s => s.Send(orderId));
}
```

Notes:
- Arguments are serialized to storage, so **pass IDs, not entities**. Reload inside the job.
- Jobs run at-least-once — design the method to be idempotent.
- The generic `Enqueue<T>` overload is an extension defined in `BackgroundJobClientExtensions`.

## 3. Delayed

Same shape as `Enqueue` plus a delay or absolute moment.

```csharp
BackgroundJob.Schedule(() => emailService.SendReminder(orderId),
                       TimeSpan.FromMinutes(30));

// Injected variant
jobs.Schedule<IEmailService>(s => s.SendReminder(orderId),
                             DateTimeOffset.UtcNow.AddHours(2));
```

Notes:
- Delayed jobs are scanned by `DelayedJobScheduler`; the polling interval is `BackgroundJobServerOptions.SchedulePollingInterval`.
- The moment is stored in UTC — pass a `DateTimeOffset` to avoid local-time surprises.

## 4. Recurring

`Cron.Daily` (and friends) are **methods**, not properties. The first overload takes a recurring-job id, an expression, and a cron string.

```csharp
// Cron helper
RecurringJob.AddOrUpdate<IReportService>(
    "daily-report",
    s => s.SendDailyReport(),
    Cron.Daily());

// Raw cron string — 5- or 6-field expressions both work
RecurringJob.AddOrUpdate<IReportService>(
    "hourly-sweep",
    s => s.Sweep(),
    "0 */1 * * *");

// With options (queue, time zone, misfire handling)
RecurringJob.AddOrUpdate<IReportService>(
    "weekly-report",
    s => s.SendWeeklyReport(),
    Cron.Weekly(DayOfWeek.Monday, hour: 7),
    new RecurringJobOptions
    {
        TimeZone = TimeZoneInfo.Utc,
        MisfireHandling = MisfireHandlingMode.Relaxed
    });
```

Notes:
- Always give recurring jobs an explicit id — the id is the upsert key.
- All `Cron.*` helpers return UTC-based expressions; use `RecurringJobOptions.TimeZone` for non-UTC scheduling.
- `MisfireHandlingMode.Ignorable` skips missed occurrences entirely; `Strict` schedules one job per missed occurrence.

## 5. Continuations

A continuation runs only when its antecedent reaches a qualifying state (succeeded by default).

```csharp
var parentId = BackgroundJob.Enqueue<IOrderService>(s => s.Capture(orderId));

BackgroundJob.ContinueJobWith<IInvoiceService>(
    parentId,
    s => s.GenerateInvoice(orderId));

// Run the continuation only when the parent ends up Deleted (e.g., failed
// and exhausted retries) — useful for compensation workflows.
BackgroundJob.ContinueJobWith<IOrderService>(
    parentId,
    s => s.Refund(orderId),
    JobContinuationOptions.OnlyOnDeletedState);
```

Notes:
- Prefer `ContinueJobWith` over the older `ContinueWith`; both exist in this version but the former is the documented name.
- `JobContinuationOptions` is `[Flags]`-like in v1.8 — multiple values can be combined.
- Continuations also queue into the parent's queue unless you pass a `queue` argument.

## 6. The job method itself

Jobs are normal services. Resolve the entity inside; never accept the whole aggregate as an argument.

```csharp
public interface IEmailService
{
    Task Send(int orderId);
}

public sealed class EmailService(AppDbContext db, ISmtp smtp, ILogger<EmailService> log)
    : IEmailService
{
    public async Task Send(int orderId)
    {
        var order = await db.Orders.FindAsync(orderId)
            ?? throw new InvalidOperationException($"Order {orderId} missing.");
        await smtp.SendAsync(order.CustomerEmail, $"Order {order.Number}", order.Body);
        log.LogInformation("Sent receipt for {OrderId}", orderId);
    }
}
```

Notes:
- The method runs in a fresh DI scope created by the activator (`AspNetCoreJobActivator`).
- Async jobs are supported — return `Task` (or `Task<T>`); v1.8 also supports `ValueTask`/`ValueTask<T>`.
- Throwing puts the job in the Failed state and triggers `AutomaticRetryAttribute`.

## 7. Retry control

`AutomaticRetryAttribute` is the standard retry filter and is applied globally with 10 attempts by default. Override it per method to tune behaviour.

```csharp
public interface IPaymentService
{
    [AutomaticRetry(
        Attempts = 3,
        DelaysInSeconds = new[] { 30, 120, 600 },
        OnAttemptsExceeded = AttemptsExceededAction.Delete,
        OnlyOn = new[] { typeof(HttpRequestException) },
        ExceptOn = new[] { typeof(OperationCanceledException) })]
    Task Charge(int paymentId);
}
```

Notes:
- `OnlyOn` (new-ish) restricts retries to specific exception types; `ExceptOn` (added in 1.8.15) excludes specific exception types — combine for fine control.
- `OnAttemptsExceeded = Delete` removes the job after the last attempt; `Fail` keeps it on the Failed page for manual triage.
- Set `LogEvents = false` to silence per-retry log messages for noisy jobs.

## 8. Storage options

Pass a `SqlServerStorageOptions` to tune polling, schema and migration behaviour.

```csharp
services.AddHangfire(cfg => cfg.UseSqlServerStorage(
    builder.Configuration.GetConnectionString("Hangfire"),
    new SqlServerStorageOptions
    {
        SchemaName               = "hangfire",
        PrepareSchemaIfNecessary = true,
        EnableHeavyMigrations    = false,
        QueuePollInterval        = TimeSpan.Zero,            // long-poll
        SlidingInvisibilityTimeout = TimeSpan.FromMinutes(5),
        CommandBatchMaxTimeout   = TimeSpan.FromMinutes(5),
        UseRecommendedIsolationLevel = true,
        DisableGlobalLocks       = true,
        TryAutoDetectSchemaDependentOptions = true
    }));
```

Notes:
- `SlidingInvisibilityTimeout` + `QueuePollInterval = Zero` enables the modern non-transactional fetch path (recommended).
- `EnableHeavyMigrations = true` is required to apply some schema upgrades against tables holding data — only set it during a planned maintenance window.
- Leave `TryAutoDetectSchemaDependentOptions = true` so schema-bound options light up automatically when migrations are applied.

## 9. Securing the dashboard

Implement `IDashboardAuthorizationFilter` and attach it via `DashboardOptions.Authorization`. The default filter (`LocalRequestsOnlyAuthorizationFilter`) blocks anything that isn't loopback.

```csharp
public sealed class AdminOnlyDashboardFilter : IDashboardAuthorizationFilter
{
    public bool Authorize(DashboardContext context)
    {
        var http = context.GetHttpContext(); // AspNetCoreDashboardContextExtensions
        return http.User.Identity?.IsAuthenticated == true
               && http.User.IsInRole("HangfireAdmin");
    }
}

app.UseHangfireDashboard("/hangfire", new DashboardOptions
{
    Authorization      = new[] { new AdminOnlyDashboardFilter() },
    DashboardTitle     = "Jobs — Production",
    IsReadOnlyFunc     = ctx => !ctx.GetHttpContext().User.IsInRole("HangfireOperator"),
    DarkModeEnabled    = true,
    IgnoreAntiforgeryToken = false
});
```

Notes:
- The default `Authorization` rejects non-local requests; **always** override it before exposing the dashboard publicly.
- For async auth, implement `IDashboardAsyncAuthorizationFilter` and set `DashboardOptions.AsyncAuthorization` instead.
- `IsReadOnlyFunc` hides destructive buttons without locking users out of the UI.

## 10. New in v1.8: lightweight servers + per-queue retry diagnostics

v1.8 introduced `BackgroundJobServerOptions.IsLightweightServer`, which spins up
workers without the storage-wide schedulers (recurring/delayed). Pair it with
queue-scoped servers when you want a process that *only* drains a hot queue
without competing for `RecurringJobScheduler`/`DelayedJobScheduler` work.

```csharp
// Main app: full server, owns the schedulers and the "default" queue.
builder.Services.AddHangfireServer(opts =>
{
    opts.ServerName  = "primary";
    opts.Queues      = new[] { "default", "low" };
    opts.WorkerCount = Environment.ProcessorCount * 2;
});

// Worker-only sidecar in the same process: drains the "critical" queue,
// no scheduler processes, no recurring/delayed scanning.
builder.Services.AddHangfireServer(opts =>
{
    opts.ServerName          = "critical-workers";
    opts.Queues              = new[] { "critical" };
    opts.IsLightweightServer = true;       // <-- new in 1.8
    opts.WorkerCount         = 8;
});

// Jobs marked with [Queue("critical")] only run on the lightweight server.
public sealed class PriorityWorkflow
{
    [Queue("critical")]
    [AutomaticRetry(Attempts = 5, DelaysInSeconds = new[] { 5, 30, 120, 600, 1800 })]
    public Task Process(long workflowId) => /* ... */ Task.CompletedTask;
}
```

Notes:
- A lightweight server still runs the watchdog and cancellation-watcher processes — only the storage-wide schedulers are omitted.
- Run exactly one non-lightweight server per storage so recurring/delayed scheduling continues to happen.
- The `BackgroundJobServerOptions.MaxDegreeOfParallelismForSchedulers` knob (also new in 1.8) lets the *non*-lightweight server parallelise scheduler work when supported by the storage.
```
