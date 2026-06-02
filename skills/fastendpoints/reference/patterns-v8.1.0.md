# FastEndpoints v8.1.0 — patterns

## What REPR is for

REPR stands for **Request-Endpoint-Response**. Each HTTP operation is a self-contained class whose only job is: accept a typed request, produce a typed response. FastEndpoints solves the well-known MVC anti-pattern where a single `[ApiController]` class (`OrdersController`, `UsersController`) accretes a dozen unrelated actions, each with its own parameter binding quirks, ad-hoc filters, and shared private helpers. Those controllers turn into junk drawers — touching one action risks breaking five others, and the surface area of the type grows without bound.

In REPR, the unit of code matches the unit of behavior: one route + verb = one class. Cross-cutting concerns (auth, validation, logging) attach to the endpoint *declaratively* via `Configure()`, and dependencies arrive through constructor or property injection. The result is small, focused, testable classes that you can read top-to-bottom in under a minute.

REPR is for **HTTP endpoints only**. It does not belong in gRPC services (use FastEndpoints' messaging primitives like `ICommandHandler<TCommand, TResult>` and `MapHandlers`), SignalR hubs, background workers (`IHostedService`), or domain services. Those each have their own contract shape and lifecycle.

## Naming conventions

- **One endpoint per file.** File name matches the class name.
- **Class name shape:** `{Verb}{Resource}Endpoint` — e.g. `GetOrderByIdEndpoint`, `CreateOrderEndpoint`, `ListCustomersEndpoint`.
- **`sealed` by default.** Endpoints are not meant to be inherited.
- **Request DTOs** are `record` types named `{Verb}{Resource}Request` (e.g. `CreateOrderRequest`).
- **Response DTOs** are `record` types named `{Verb}{Resource}Response`, or a domain-shaped value record.
- **Validators** colocate with the endpoint file (nested or sibling) or live under `Validators/`. One `Validator<TRequest>` per request DTO.
- Endpoints, request/response DTOs, and validators are auto-discovered from the assembly on startup.

## Where each piece of code belongs

| Concern | Goes in | Notes |
|---|---|---|
| Route, HTTP verb | `Configure()` | `Get("/orders/{id}")`, `Post("/orders")` etc. |
| OpenAPI metadata | `Configure()` | `Summary(...)`, `Description(...)`, `Tags(...)` |
| Auth requirements | `Configure()` | `Roles(...)`, `Policies(...)`, `Permissions(...)`, `Claims(...)`, `AllowAnonymous()` |
| Request shape validation | `Validator<TRequest>` | required fields, ranges, regex, lengths |
| Single request→response transform | `HandleAsync(req, ct)` | the *only* place business behavior runs |
| Cross-cutting concerns (logging, audit, caching) | Pre/post-processors | implement `IPreProcessor<TRequest>` / `IPostProcessor<TRequest, TResponse>` and wire via `PreProcessor<T>()` / `PostProcessor<T>()` in `Configure()` |
| Throttling | `Configure()` | `Throttle(hitLimit, durationSeconds, headerName)` |
| Response caching | `Configure()` | `ResponseCache(...)` |
| Data access | injected service / repository | never read `DbContext` from the endpoint directly |
| Returning a response | `Send.OkAsync(...)`, `Send.NotFoundAsync()`, etc. | via the `Send` property on `Endpoint<TReq, TRes>` |

## The canonical endpoint shape

```csharp
public sealed record GetOrderByIdRequest(Guid Id);

public sealed record GetOrderByIdResponse(Guid Id, string CustomerName, decimal Total);

public sealed class GetOrderByIdEndpoint(IOrderRepository orders)
    : Endpoint<GetOrderByIdRequest, GetOrderByIdResponse>
{
    public override void Configure()
    {
        Get("/orders/{Id}");
        Permissions("orders:read");
        Description(b => b
            .Produces<GetOrderByIdResponse>(200)
            .ProducesProblemFE(404));
    }

    public override async Task HandleAsync(GetOrderByIdRequest req, CancellationToken ct)
    {
        var order = await orders.FindAsync(req.Id, ct);

        if (order is null)
        {
            await Send.NotFoundAsync(ct);
            return;
        }

        await Send.OkAsync(
            new GetOrderByIdResponse(order.Id, order.CustomerName, order.Total),
            ct);
    }
}
```

- `Configure()` is **metadata only** — declare routes, verbs, auth, swagger info. It runs once at startup.
- `HandleAsync(req, ct)` is where you do work and call one of the `Send.*Async(...)` methods on the `Send` property. Do not return a value from this method.
- For endpoints with no request body, inherit `EndpointWithoutRequest` or `EndpointWithoutRequest<TResponse>` and override `HandleAsync(CancellationToken ct)`.

## Validator wiring

Place a validator next to the endpoint. It auto-registers on startup when FastEndpoints scans the assembly. Validators are **singletons** — do not maintain state in them.

```csharp
public sealed class CreateOrderRequest
{
    public string CustomerEmail { get; init; } = "";
    public List<OrderLine> Lines { get; init; } = [];
}

public sealed class CreateOrderValidator : Validator<CreateOrderRequest>
{
    public CreateOrderValidator()
    {
        RuleFor(x => x.CustomerEmail)
            .NotEmpty()
            .EmailAddress();

        RuleFor(x => x.Lines)
            .NotEmpty()
            .WithMessage("at least one order line is required");

        RuleForEach(x => x.Lines).ChildRules(line =>
        {
            line.RuleFor(l => l.Sku).NotEmpty();
            line.RuleFor(l => l.Quantity).GreaterThan(0);
        });
    }
}
```

If validation fails, FastEndpoints automatically returns a 400 with `ErrorResponse` before `HandleAsync` runs. Inside the handler you can also call `AddError(...)` and `ThrowIfAnyErrors()` (from the `IValidationErrors`/`IValidationErrors<T>` surface) to push semantic/business validation failures.

If you have multiple validators for the same DTO, disambiguate explicitly via `Validator<TValidator>()` inside `Configure()`.

## Composition root

```csharp
var bld = WebApplication.CreateBuilder(args);

bld.Services
    .AddFastEndpoints()
    .SwaggerDocument(); // from FastEndpoints.Swagger

bld.Services.AddAuthenticationJwtBearer(s => s.SigningKey = bld.Configuration["Jwt:Key"]);
bld.Services.AddAuthorization();

var app = bld.Build();

app.UseAuthentication();
app.UseAuthorization();
app.UseFastEndpoints(c =>
{
    c.Endpoints.RoutePrefix = "api";
    c.Errors.UseProblemDetails(); // optional: RFC7807 responses
});
app.UseSwaggerGen();

app.Run();
```

`AddFastEndpoints()` scans the entry assembly (and any assemblies you list in `EndpointDiscoveryOptions.Assemblies`) for endpoints, validators, mappers, and event handlers. `UseFastEndpoints(...)` finalizes registration and inserts the pipeline.

## Things to avoid

- **Do not** add MVC controllers (`ControllerBase` / `[ApiController]`) alongside FastEndpoints in the same project. It defeats the whole point of REPR and creates two parallel routing conventions.
- **Do not** put business logic in `Configure()`. It runs once at startup, not per request — anything that depends on the current request belongs in `HandleAsync`.
- **Do not** `throw new Exception(...)` for control flow. To short-circuit with a validation failure, use `ThrowError(...)` or `AddError(...)` + `ThrowIfAnyErrors()`. To send a specific status, call `Send.NotFoundAsync(ct)`, `Send.UnauthorizedAsync(ct)`, `Send.ForbiddenAsync(ct)`, `Send.StatusCodeAsync(code, ct)`, etc.
- **Do not** bypass the request DTO by reading from `HttpContext.Request.Query`/`Form`/`Headers` directly when the value fits in a DTO property. Use `[FromHeader]`, `[FromClaim]`, `[FromCookie]`, `[FromQuery]`, `[FromForm]`, `[BindFrom]`, `[QueryParam]`, `[RouteParam]`, `[FormField]`, or `IPlainTextRequest` instead — these are part of the binding contract and show up in OpenAPI.
- **Do not** inject `DbContext` straight into the endpoint. Wrap data access in a service/repository so endpoints remain about request→response shaping.
- **Do not** put authorization checks inside `HandleAsync`. Express them in `Configure()` via `Roles()`, `Policies()`, `Permissions()`, `Claims()`, `Scopes()` — they become part of the endpoint's metadata and the OpenAPI document.
- **Do not** make validators stateful. They are reused as singletons across requests.
- **Do not** unseal endpoints to share code via inheritance. Share via injected services or by using `Group<TGroup>` for common `Configure()` settings across an endpoint group.
