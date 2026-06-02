<!--
Generated against FastEndpoints v8.1.0.
Do not edit by hand — rerun scripts/update_skill.py.
-->

# FastEndpoints v8.1.0 — canonical examples

These examples target the exact public surface shipped in FastEndpoints v8.1.0
and its sibling packages. Each endpoint lives in its own file, follows the
REPR pattern, and is configured via `Configure()`.

## 1. Minimal GET endpoint without a request DTO

Use `EndpointWithoutRequest<TResponse>` for endpoints that only emit a response.

```csharp
namespace MyApi.Endpoints.Health;

public sealed record HealthResponse(string Status, DateTime UtcNow);

public sealed class GetHealthEndpoint : EndpointWithoutRequest<HealthResponse>
{
    public override void Configure()
    {
        Get("/health");
        AllowAnonymous();
    }

    public override async Task HandleAsync(CancellationToken ct)
    {
        await Send.OkAsync(new HealthResponse("ok", DateTime.UtcNow), ct);
    }
}
```

Notes:
- `Send.OkAsync(...)` is the v8 idiomatic response sender (the `Send` property
  exposes `IResponseSender` extension methods like `OkAsync`).
- `HandleAsync(CancellationToken)` is the correct override for the no-request
  base class — the `(EmptyRequest, CancellationToken)` overload is sealed
  away and should not be implemented.

## 2. POST endpoint with request + response DTOs

Use `Endpoint<TRequest, TResponse>` when both sides have a shape. Routing,
auth, and metadata are declared inside `Configure()`.

```csharp
namespace MyApi.Endpoints.Orders;

public sealed record CreateOrderRequest(string Sku, int Quantity);
public sealed record CreateOrderResponse(Guid OrderId, string Sku, int Quantity);

public sealed class CreateOrderEndpoint : Endpoint<CreateOrderRequest, CreateOrderResponse>
{
    public override void Configure()
    {
        Post("/orders");
        AllowAnonymous();
        Description(b => b
            .Accepts<CreateOrderRequest>("application/json")
            .Produces<CreateOrderResponse>(201, "application/json")
            .ProducesProblemFE(400));
    }

    public override async Task HandleAsync(CreateOrderRequest req, CancellationToken ct)
    {
        var id = Guid.NewGuid();
        await Send.CreatedAtAsync<GetOrderByIdEndpoint>(
            routeValues: new { OrderId = id },
            responseBody: new CreateOrderResponse(id, req.Sku, req.Quantity),
            cancellation: ct);
    }
}

public sealed record GetOrderByIdRequest(Guid OrderId);

public sealed class GetOrderByIdEndpoint : Endpoint<GetOrderByIdRequest, CreateOrderResponse>
{
    public override void Configure()
    {
        Get("/orders/{OrderId}");
        AllowAnonymous();
    }

    public override async Task HandleAsync(GetOrderByIdRequest req, CancellationToken ct)
    {
        await Send.OkAsync(new CreateOrderResponse(req.OrderId, "demo-sku", 1), ct);
    }
}
```

Notes:
- `Send.CreatedAtAsync<TEndpoint>(...)` writes a 201 with a `Location` header
  pointing at the target endpoint. The target must be a single-verb, single-
  route endpoint.
- Route parameters bind to DTO properties by name (`{OrderId}` → `OrderId`).

## 3. Request validator with FluentValidation rules

Validators inherit `Validator<TRequest>` (registered as singletons; do not
hold state). They're discovered automatically.

```csharp
namespace MyApi.Endpoints.Orders;

public sealed class CreateOrderValidator : Validator<CreateOrderRequest>
{
    public CreateOrderValidator()
    {
        RuleFor(x => x.Sku)
            .NotEmpty()
            .MaximumLength(32);

        RuleFor(x => x.Quantity)
            .GreaterThan(0)
            .LessThanOrEqualTo(1_000);
    }
}
```

Notes:
- A 400 with `ErrorResponse` is sent automatically when validation fails.
  Disable per endpoint with `DontThrowIfValidationFails()` if you want to
  inspect `ValidationFailures` yourself.
- FluentValidation lives under the `FastEndpoints.Validation` namespace in
  this version — the `Validator<T>` base imported via `using FastEndpoints;`
  is already wired up.

## 4. Authentication / authorization on an endpoint

Combine `Roles()`, `Permissions()`, `Policies()`, and (optionally) explicit
`AuthSchemes()` inside `Configure()`.

```csharp
namespace MyApi.Endpoints.Admin;

public sealed record PurgeRequest(string Reason);

public sealed class PurgeCacheEndpoint : Endpoint<PurgeRequest>
{
    public override void Configure()
    {
        Post("/admin/cache/purge");
        Roles("admin", "ops");
        Permissions("Cache_Purge");
        Policies("RequireMfa");
        AuthSchemes("Bearer");
        Description(b => b.Produces(204).ProducesProblemFE(401).ProducesProblemFE(403));
    }

    public override async Task HandleAsync(PurgeRequest req, CancellationToken ct)
    {
        Logger.LogInformation("Cache purged by {User}: {Reason}", User.Identity?.Name, req.Reason);
        await Send.NoContentAsync(ct);
    }
}
```

Notes:
- `Roles(...)` is "any of"; use `Permissions(...)` for permission codes and
  `PermissionsAll(...)` when all are required.
- `Policies("RequireMfa")` must reference a policy registered with
  `services.AddAuthorization(...)` at startup.

## 5. Swagger / OpenAPI metadata

`Summary()` describes the endpoint; `Description()` lets you add raw OpenAPI
metadata via the underlying `RouteHandlerBuilder`.

```csharp
namespace MyApi.Endpoints.Orders;

public sealed class ListOrdersRequest
{
    public int Page { get; init; } = 1;
    public int PageSize { get; init; } = 20;
}

public sealed record OrderSummary(Guid OrderId, string Sku, int Quantity);

public sealed class ListOrdersEndpoint : Endpoint<ListOrdersRequest, List<OrderSummary>>
{
    public override void Configure()
    {
        Get("/orders");
        AllowAnonymous();
        Description(b => b
            .Produces<List<OrderSummary>>(200)
            .ProducesProblemFE(400));

        Summary(s =>
        {
            s.Summary = "List orders.";
            s.Description = "Returns a paged list of orders. Defaults: page=1, size=20.";
            s.Params[nameof(ListOrdersRequest.Page)] = "1-based page number.";
            s.Params[nameof(ListOrdersRequest.PageSize)] = "Items per page (max 100).";
            s.Responses[200] = "Orders returned successfully.";
            s.Responses[400] = "Invalid paging parameters.";
        });
    }

    public override async Task HandleAsync(ListOrdersRequest req, CancellationToken ct)
    {
        var orders = new List<OrderSummary>
        {
            new(Guid.NewGuid(), "sku-1", 2),
            new(Guid.NewGuid(), "sku-2", 5)
        };
        await Send.OkAsync(orders, ct);
    }
}
```

Notes:
- `Summary.Responses[statusCode] = "..."` is the indexer-based form. Use
  `s.Response<T>(...)` if you want to attach a typed example.
- `ProducesProblemFE(400)` advertises FastEndpoints' default `ErrorResponse`
  shape. Switch to `ProducesProblemDetails(400)` if you've opted into
  RFC7807 via `c.Errors.UseProblemDetails()`.

## 6. App registration in Program.cs

A minimal Program.cs that wires up FastEndpoints + Swagger.

```csharp
using FastEndpoints;
using FastEndpoints.Swagger;

var builder = WebApplication.CreateBuilder(args);

builder.Services
    .AddFastEndpoints()
    .SwaggerDocument(o =>
    {
        o.ShortSchemaNames = true;
        o.DocumentSettings = s =>
        {
            s.Title = "My API";
            s.Version = "v1";
        };
    });

builder.Services.AddAuthentication("Bearer").AddJwtBearer();
builder.Services.AddAuthorization();

var app = builder.Build();

app.UseAuthentication();
app.UseAuthorization();

app.UseFastEndpoints(c =>
{
    c.Endpoints.RoutePrefix = "api";
    c.Errors.UseProblemDetails(); // RFC7807 error bodies; optional
});

app.UseSwaggerGen(); // serves the OpenAPI doc + Swagger UI

app.Run();
```

Notes:
- `SwaggerDocument(...)` is the v8 entry point (extension on `IServiceCollection`)
  and `UseSwaggerGen()` mounts both the OpenAPI middleware and Swagger UI with
  FastEndpoints-friendly defaults.
- `RoutePrefix = "api"` prefixes every endpoint route. Override per endpoint
  via `RoutePrefixOverride("...")` or set `string.Empty` to opt out.

## 7. Pre-processor / post-processor pipeline

Implement `IPreProcessor<TRequest>` / `IPostProcessor<TRequest, TResponse>`
and attach them in `Configure()`. Generic variants give type safety.

```csharp
namespace MyApi.Pipeline;

public sealed class RequestLogger<TRequest> : IPreProcessor<TRequest>
{
    public Task PreProcessAsync(IPreProcessorContext<TRequest> ctx, CancellationToken ct)
    {
        var log = ctx.HttpContext.Resolve<ILoggerFactory>().CreateLogger("RequestLogger");
        log.LogInformation("Incoming {Type}", typeof(TRequest).Name);
        return Task.CompletedTask;
    }
}

public sealed class AuditTrail : IPostProcessor<CreateOrderRequest, CreateOrderResponse>
{
    public Task PostProcessAsync(
        IPostProcessorContext<CreateOrderRequest, CreateOrderResponse> ctx,
        CancellationToken ct)
    {
        if (ctx.HasExceptionOccurred || ctx.Response is null)
            return Task.CompletedTask;

        var log = ctx.HttpContext.Resolve<ILoggerFactory>().CreateLogger("AuditTrail");
        log.LogInformation("Order {OrderId} created for {Sku}", ctx.Response.OrderId, ctx.Response.Sku);
        return Task.CompletedTask;
    }
}
```

Attach to the endpoint:

```csharp
public sealed class CreateOrderEndpointWithPipeline : Endpoint<CreateOrderRequest, CreateOrderResponse>
{
    public override void Configure()
    {
        Post("/orders");
        AllowAnonymous();
        PreProcessor<RequestLogger<CreateOrderRequest>>();
        PostProcessor<AuditTrail>();
    }

    public override async Task HandleAsync(CreateOrderRequest req, CancellationToken ct)
    {
        var id = Guid.NewGuid();
        await Send.OkAsync(new CreateOrderResponse(id, req.Sku, req.Quantity), ct);
    }
}
```

Notes:
- The post-processor's context exposes `HasExceptionOccurred`,
  `ExceptionDispatchInfo`, and `MarkExceptionAsHandled()` — handle errors
  here if you want to swallow them centrally.
- Register processors globally via `c.Endpoints.Configurator = ep => ep.PreProcessor<...>(Order.Before);`
  inside `UseFastEndpoints(...)`.

## 8. New in v8.1: known-subscriber pre-seeding for event hubs

v8.1 lets a publisher-side event hub start queueing events for a fixed,
pre-known set of subscriber IDs from app startup, even before those clients
have connected. This way no events are missed for "expected" subscribers.

Publisher (`Program.cs`) — register an event hub for a given event type with
known subscriber IDs:

```csharp
using FastEndpoints;

var builder = WebApplication.CreateBuilder(args);
builder.AddHandlerServer();

var app = builder.Build();

app.MapHandlers(h =>
{
    // event hub for OrderPlaced events; queue records for these
    // subscriber ids from startup, even before they connect.
    h.RegisterEventHub<OrderPlaced>(
        knownSubscriberIDs: new[] { "billing-service", "shipping-service" },
        mode: HubMode.EventPublisher);
});

app.Run();

public sealed class OrderPlaced : IEvent
{
    public Guid OrderId { get; init; }
    public string Sku { get; init; } = "";
}
```

Broadcast the event from anywhere on the publisher (e.g. inside an endpoint):

```csharp
public sealed class PlaceOrderEndpoint : EndpointWithoutRequest
{
    public override void Configure()
    {
        Post("/orders/place");
        AllowAnonymous();
    }

    public override async Task HandleAsync(CancellationToken ct)
    {
        var evt = new OrderPlaced { OrderId = Guid.NewGuid(), Sku = "demo" };
        evt.Broadcast(); // fans out to all subscribers of OrderPlaced
        await Send.OkAsync(ct);
    }
}
```

Notes:
- `RegisterEventHub<TEvent>(knownSubscriberIDs, mode)` is new in v8.1; the
  older parameterless overload still works for the "connect first, then
  queue" model.
- Known-subscriber pre-seeding is **not** supported in `HubMode.RoundRobin`
  — round-robin still only targets currently connected subscribers.
- Subscriber-side wiring (`MapRemote(...)` + `Subscribe<OrderPlaced, …>()`)
  hasn't changed; pass a stable `subscriberID` via the connection so the
  publisher matches records to the right consumer.
