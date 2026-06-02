# Ardalis.Result v10.1.0 — patterns

## What this pattern is for

The Result pattern turns *expected* failure modes — "not found", "invalid input", "conflict with current state", "forbidden" — into ordinary return values instead of thrown exceptions. Exceptions are expensive (stack unwinding, allocation), they're awkward to compose across async boundaries, and they force the caller to know an implementation detail (which exception type means what) in order to translate a failure into the correct HTTP status code. A `Result<T>` carries both the success payload and a categorized failure status, so a service can say "the order doesn't exist" once and every caller — controllers, background jobs, other services — gets a uniform, type-safe answer.

`Ardalis.Result` is for the predictable, domain-shaped failures that show up in business logic: validation, authorization, missing entities, rule violations, concurrency conflicts. It is **not** a replacement for exceptions in genuinely exceptional situations: programming bugs (null reference, arg out of range), I/O failures you can't meaningfully recover from, `OutOfMemoryException`, cancellation, database connectivity loss. Let those crash so your global handler / logging picks them up. If you find yourself writing `catch (Exception) { return Result.Error(...); }` around a whole service method, you're hiding bugs.

The companion packages plug Result into the ASP.NET Core pipeline (`Ardalis.Result.AspNetCore`) and into FluentValidation (`Ardalis.Result.FluentValidation`) so input validation and HTTP translation stay at the edges and your services stay clean.

## Naming conventions

- Service methods describe **what** they return, in the singular happy-path sense: `GetOrderByIdAsync`, `CreateCustomerAsync`, `ShipOrderAsync`. Avoid `TryX` / `FindOrCreateX` — one call, one `Result`.
- Async methods return `Task<Result<T>>`. Use the non-generic `Result` only for operations with no payload (e.g. `DeleteAsync` returning `Task<Result>`).
- Use `Result<T>.Success(value)` / `Result.Success` for happy paths and the specific named failure factories (`NotFound`, `Invalid`, `Conflict`, `Unauthorized`, `Forbidden`, `Unavailable`, `CriticalError`, `Error`) — never `Result.Error("not found")` for a not-found, because the AspNetCore convention maps `ResultStatus` to HTTP status codes by category.

## Where each piece of code belongs

| Concern | Lives in | Mechanism |
|---|---|---|
| Input shape validation (required, length, format) | A FluentValidation `AbstractValidator<T>` | Call `validator.Validate(request).AsErrors()` and pass to `Result<T>.Invalid(...)` |
| Business rule failure (entity missing, rule violated, conflict) | The service / handler method | Return `Result<T>.NotFound("...")`, `.Conflict(...)`, `.Invalid(...)`, `.Unauthorized(...)`, `.Forbidden(...)` |
| Translating `Result<T>` to an HTTP response | Controller action / endpoint boundary | `[TranslateResultToActionResult]` attribute, plus `AddDefaultResultConvention()` or a custom `ResultStatusMap` at startup |
| Propagating a failure from a downstream call | Outer service method | Return the inner `Result` directly (or use `Bind` / `BindAsync`) — don't re-wrap |
| Logging the failure | The caller that decides what to do about it | Inspect `result.Status`, `result.Errors`, `result.ValidationErrors` after the call |
| Truly exceptional faults (DB down, bug) | Nowhere in Result | Let the exception propagate to the host's exception handler |

## Canonical service-method shape

```csharp
using Ardalis.Result;
using Ardalis.Result.FluentValidation;
using FluentValidation;

public class ShipOrderService
{
    private readonly IOrderRepository _orders;
    private readonly IValidator<ShipOrderRequest> _validator;

    public ShipOrderService(IOrderRepository orders, IValidator<ShipOrderRequest> validator)
    {
        _orders = orders;
        _validator = validator;
    }

    public async Task<Result<ShipmentDto>> ShipOrderAsync(
        ShipOrderRequest request,
        CancellationToken ct)
    {
        // 1. Input shape validation -> Invalid
        var validation = await _validator.ValidateAsync(request, ct);
        if (!validation.IsValid)
            return Result<ShipmentDto>.Invalid(validation.AsErrors());

        // 2. Entity lookup -> NotFound
        var order = await _orders.GetByIdAsync(request.OrderId, ct);
        if (order is null)
            return Result<ShipmentDto>.NotFound($"Order {request.OrderId} does not exist.");

        // 3. Business rule -> Conflict
        if (order.IsShipped)
            return Result<ShipmentDto>.Conflict("Order has already been shipped.");

        // 4. Authorization rule -> Forbidden
        if (!order.CanBeShippedBy(request.UserId))
            return Result<ShipmentDto>.Forbidden("User cannot ship this order.");

        // 5. Happy path
        var shipment = order.Ship();
        await _orders.SaveAsync(order, ct);
        return Result<ShipmentDto>.Success(ShipmentDto.From(shipment));
    }
}
```

Notice that nothing in this method throws to signal a domain failure, and the method does not log — that's the caller's job, once it knows the `Status`.

## Consumer-side pattern

When one service calls another and can't recover, pass the failure straight through:

```csharp
public async Task<Result<InvoiceDto>> GenerateInvoiceAsync(Guid orderId, CancellationToken ct)
{
    var shipResult = await _ship.ShipOrderAsync(new ShipOrderRequest(orderId), ct);
    if (!shipResult.IsSuccess)
        // Preserve original Status (NotFound stays NotFound, Conflict stays Conflict)
        return new Result<InvoiceDto>(shipResult);

    var invoice = _invoices.CreateFor(shipResult.Value);
    return Result<InvoiceDto>.Success(invoice);
}
```

Or use `Bind` / `BindAsync` for the composed form:

```csharp
public Task<Result<InvoiceDto>> GenerateInvoiceAsync(Guid orderId, CancellationToken ct) =>
    _ship.ShipOrderAsync(new ShipOrderRequest(orderId), ct)
         .BindAsync(shipment => _invoices.CreateForAsync(shipment, ct));
```

A caller that *does* want to inspect categories uses the `IResultExtensions` predicates:

```csharp
if (result.IsNotFound())     _logger.LogInformation("Missing: {Errors}", result.Errors);
else if (result.IsInvalid()) _logger.LogWarning("Bad input: {@V}", result.ValidationErrors);
else if (result.IsConflict())_logger.LogWarning("Conflict: {Errors}", result.Errors);
```

## AspNetCore integration

Register the default `ResultStatus` → HTTP status code map once at startup:

```csharp
builder.Services
    .AddControllers(mvc => mvc.AddDefaultResultConvention())
    // or: mvc.AddResultConvention(map => map
    //     .AddDefaultMap()
    //     .For(ResultStatus.Conflict, HttpStatusCode.Conflict));
    ;
```

Then return `Result<T>` directly from controllers and let the attribute translate:

```csharp
[ApiController]
[Route("orders")]
[TranslateResultToActionResult]
public class OrdersController : ControllerBase
{
    private readonly ShipOrderService _ship;
    public OrdersController(ShipOrderService ship) => _ship = ship;

    [HttpPost("{id:guid}/ship")]
    [ExpectedFailures(ResultStatus.NotFound, ResultStatus.Conflict, ResultStatus.Invalid)]
    public Task<Result<ShipmentDto>> Ship(Guid id, [FromBody] ShipOrderBody body, CancellationToken ct)
        => _ship.ShipOrderAsync(new ShipOrderRequest(id, body.UserId), ct);
}
```

`[TranslateResultToActionResult]` runs `OnActionExecuted` and converts the `Result<T>` into the `ActionResult` that matches its `Status` per the configured `ResultStatusMap`. `[ExpectedFailures(...)]` documents which non-success statuses this endpoint actually produces so Swagger / clients see them.

## Things to avoid

- **Throwing exceptions for validation, not-found, or conflicts.** That puts the categorization in a `catch` block somewhere upstream and defeats the whole point. Use `Result<T>.Invalid` / `NotFound` / `Conflict`.
- **Letting a raw `Result<T>` reach the wire.** Without the AspNetCore convention, clients receive a JSON blob containing a `Status` enum and an HTTP 200 — which is wrong for every failure case. Always register `AddDefaultResultConvention()` (or a custom map) and apply `[TranslateResultToActionResult]`.
- **Re-wrapping a downstream Result** (`return Result<Foo>.Error(inner.Errors.First())`). You lose the original `Status` — a `NotFound` becomes a generic 500. Use `new Result<TOuter>(innerResult)` or `Bind` / `BindAsync` to forward it intact.
- **Mixing return styles in one aggregate.** Pick `Result<T>` for the whole service surface or pick exceptions — don't have `GetX` throw `NotFoundException` while `UpdateX` returns `Result<T>.NotFound`. Callers can't reason about it.
- **Catch-all `try { ... } catch (Exception ex) { return Result.Error(ex.Message); }`** wrapped around service methods. This swallows bugs (NREs, misconfigurations) as if they were domain failures. Catch only what you can categorize; let the rest crash to your global handler.
- **Logging inside the service that produced the `Result`.** The service doesn't know whether this failure is expected by the caller (e.g. an `Exists`-style check). Log at the boundary that decides whether the failure is noteworthy.
