<!--
Ardalis.Result examples — generated for version 10.1.0.
Do not edit by hand — rerun scripts/update_skill.py to regenerate.
-->

# Ardalis.Result

Canonical usage examples for **Ardalis.Result v10.1.0**, **Ardalis.Result.AspNetCore v10.1.0**, and **Ardalis.Result.FluentValidation v10.1.0**. Every snippet is verified against the public API surface for these exact versions.

## 1. Returning `Result.Success(value)` from a service

The happy path: return a typed value wrapped in `Result<T>`. There is an implicit conversion from `T` to `Result<T>`, so you can also just `return order;`.

```csharp
namespace Shop.Application.Orders;

using Ardalis.Result;

public sealed record OrderDto(int Id, string CustomerName, decimal Total);

public sealed class OrderService(IOrderRepository repo)
{
    public async Task<Result<OrderDto>> GetOrderByIdAsync(int id, CancellationToken ct)
    {
        var order = await repo.FindAsync(id, ct);
        if (order is null) return Result<OrderDto>.NotFound($"Order {id} not found.");

        var dto = new OrderDto(order.Id, order.CustomerName, order.Total);
        return Result<OrderDto>.Success(dto);
    }
}
```

Notes:
- `Result<T>.Success(value)` and the implicit conversion from `T` to `Result<T>` are equivalent.
- Use `Result<T>.Success(value, "message")` (or `Result.SuccessWithMessage(...)` for non-generic) when you want to surface a user-facing success message.

## 2. Returning `Result.NotFound()` from a missed lookup

`NotFound` is its own status — do not conflate it with `Error`. The AspNetCore integration maps it to HTTP 404.

```csharp
namespace Shop.Application.Customers;

using Ardalis.Result;

public sealed class CustomerService(ICustomerRepository repo)
{
    public async Task<Result<Customer>> GetByEmailAsync(string email, CancellationToken ct)
    {
        var customer = await repo.FindByEmailAsync(email, ct);
        if (customer is null)
            return Result<Customer>.NotFound($"No customer with email '{email}'.");

        return customer; // implicit conversion to Result<Customer>
    }
}
```

Notes:
- `NotFound()` and `NotFound(params string[] errorMessages)` are both available.
- Prefer `Result<T>.NotFound(...)` over `Result.Error(...)` for "the thing wasn't there" — it preserves intent and the correct HTTP mapping.

## 3. Returning `Result.Invalid(errors)` from input validation

`Invalid` carries a collection of `ValidationError` objects with structured fields (`Identifier`, `ErrorMessage`, `ErrorCode`, `Severity`) — much richer than free-form error strings.

```csharp
namespace Shop.Application.Orders;

using Ardalis.Result;

public sealed record CreateOrderRequest(string CustomerEmail, decimal Total);

public sealed class CreateOrderService(IOrderRepository repo)
{
    public async Task<Result<int>> CreateOrderAsync(CreateOrderRequest req, CancellationToken ct)
    {
        var errors = new List<ValidationError>();

        if (string.IsNullOrWhiteSpace(req.CustomerEmail))
            errors.Add(new ValidationError(
                identifier: nameof(req.CustomerEmail),
                errorMessage: "Customer email is required.",
                errorCode: "CUSTOMER_EMAIL_REQUIRED",
                severity: ValidationSeverity.Error));

        if (req.Total <= 0m)
            errors.Add(new ValidationError(
                identifier: nameof(req.Total),
                errorMessage: "Total must be positive.",
                errorCode: "TOTAL_NOT_POSITIVE",
                severity: ValidationSeverity.Error));

        if (errors.Count > 0)
            return Result<int>.Invalid(errors);

        var id = await repo.AddAsync(req, ct);
        return Result<int>.Success(id);
    }
}
```

Notes:
- `ValidationError` exposes `Identifier`, `ErrorMessage`, `ErrorCode`, and `Severity`.
- `Invalid` accepts a single `ValidationError`, a `params ValidationError[]`, or any `IEnumerable<ValidationError>`.

## 4. Returning `Result.Error(...)` / `CriticalError(...)` for unexpected failures

Use `Error` for general failures, and `CriticalError` for cases that warrant escalation (the AspNetCore integration maps it to HTTP 500).

```csharp
namespace Shop.Application.Payments;

using Ardalis.Result;

public sealed class PaymentService(IPaymentGateway gateway, ILogger<PaymentService> log)
{
    public async Task<Result<string>> ChargeAsync(int orderId, decimal amount, CancellationToken ct)
    {
        try
        {
            var receipt = await gateway.ChargeAsync(orderId, amount, ct);
            return Result<string>.Success(receipt);
        }
        catch (PaymentDeclinedException ex)
        {
            return Result<string>.Error($"Payment declined: {ex.Reason}");
        }
        catch (Exception ex)
        {
            log.LogError(ex, "Payment gateway failure for order {OrderId}", orderId);
            return Result<string>.CriticalError("Payment gateway is unreachable.");
        }
    }
}
```

Notes:
- `Error` ≠ `Invalid`: `Invalid` is for user-correctable input problems; `Error` is for runtime failures the user can't fix.
- `Error` also accepts an `ErrorList` if you want to attach a correlation id alongside messages.

## 5. Consuming a `Result<T>` at the call site

Branch on `Status` (or use the `IResultExtensions` helpers like `IsNotFound`, `IsInvalid`) to map results to outcomes. Avoid touching `Value` unless `IsSuccess` is true.

```csharp
namespace Shop.Application.Orders;

using Ardalis.Result;

public sealed class OrderWorkflow(OrderService orders, PaymentService payments)
{
    public async Task<Result<string>> CheckoutAsync(int orderId, CancellationToken ct)
    {
        var orderResult = await orders.GetOrderByIdAsync(orderId, ct);

        return orderResult.Status switch
        {
            ResultStatus.Ok       => await payments.ChargeAsync(orderId, orderResult.Value.Total, ct),
            ResultStatus.NotFound => Result<string>.NotFound(orderResult.Errors.ToArray()),
            ResultStatus.Invalid  => Result<string>.Invalid(orderResult.ValidationErrors),
            _                     => Result<string>.Error(orderResult.Errors.ToArray()),
        };
    }
}
```

Notes:
- `Errors` is `IEnumerable<string>` of plain messages; `ValidationErrors` is `IEnumerable<ValidationError>` with structured fields.
- For functional composition across multiple service calls, prefer `Bind` / `BindAsync` (see example 8).

## 6. ASP.NET Core: translating `Result<T>` to an `ActionResult`

Decorate the controller (or action) with `[TranslateResultToActionResult]` and register the convention in `Program.cs`. Return `Result<T>` directly from the action — the attribute converts it to the appropriate `ActionResult`.

```csharp
// Program.cs
using Ardalis.Result.AspNetCore;

var builder = WebApplication.CreateBuilder(args);

builder.Services.AddControllers(options =>
{
    options.AddDefaultResultConvention();
});

var app = builder.Build();
app.MapControllers();
app.Run();
```

```csharp
// OrdersController.cs
namespace Shop.Api.Controllers;

using Ardalis.Result;
using Ardalis.Result.AspNetCore;
using Microsoft.AspNetCore.Mvc;

[ApiController]
[Route("orders")]
[TranslateResultToActionResult]
public sealed class OrdersController(OrderService orders, CreateOrderService createOrder) : ControllerBase
{
    [HttpGet("{id:int}")]
    [ExpectedFailures(ResultStatus.NotFound)]
    public Task<Result<OrderDto>> Get(int id, CancellationToken ct)
        => orders.GetOrderByIdAsync(id, ct);

    [HttpPost]
    [ExpectedFailures(ResultStatus.Invalid)]
    public Task<Result<int>> Create([FromBody] CreateOrderRequest req, CancellationToken ct)
        => createOrder.CreateOrderAsync(req, ct);
}
```

Notes:
- `AddDefaultResultConvention()` wires up the default `ResultStatus` → `HttpStatusCode` map (Ok→200, NotFound→404, Invalid→400, Unauthorized→401, Forbidden→403, Error→500, …).
- Use `AddResultConvention(map => map.For(ResultStatus.Conflict, HttpStatusCode.Conflict))` to customize specific statuses.
- `[ExpectedFailures(...)]` documents which non-success statuses are intentional outcomes of the action.

## 7. FluentValidation bridge: `ValidationResult.AsErrors()` → `Result.Invalid(...)`

`AsErrors()` (from `Ardalis.Result.FluentValidation`) converts FluentValidation's `ValidationResult` into an `IEnumerable<ValidationError>` ready for `Result.Invalid(...)`, including severity translation via `FromSeverity`.

```csharp
namespace Shop.Application.Orders;

using Ardalis.Result;
using Ardalis.Result.FluentValidation;
using FluentValidation;

public sealed class CreateOrderValidator : AbstractValidator<CreateOrderRequest>
{
    public CreateOrderValidator()
    {
        RuleFor(x => x.CustomerEmail).NotEmpty().EmailAddress();
        RuleFor(x => x.Total).GreaterThan(0m);
    }
}

public sealed class CreateOrderHandler(
    IValidator<CreateOrderRequest> validator,
    IOrderRepository repo)
{
    public async Task<Result<int>> HandleAsync(CreateOrderRequest req, CancellationToken ct)
    {
        var validation = await validator.ValidateAsync(req, ct);
        if (!validation.IsValid)
            return Result<int>.Invalid(validation.AsErrors());

        var id = await repo.AddAsync(req, ct);
        return Result<int>.Success(id);
    }
}
```

Notes:
- `AsErrors()` populates each `ValidationError` with the FluentValidation property name (`Identifier`), the message, the error code, and a mapped `Severity`.

## 8. New in v10.1: `Bind` / `BindAsync` for Railway-Oriented Programming

v10.1 added `Bind` and a full set of `BindAsync` overloads to `ResultExtensions`, alongside a new `Map` overload from `Result<T>` to `Result` and a new two-argument `ValidationError(identifier, errorMessage)` constructor. `Bind` chains operations that themselves return a `Result`: if any step fails, the failure short-circuits the rest of the pipeline.

```csharp
namespace Shop.Application.Orders;

using Ardalis.Result;

public sealed record SubmitOrderRequest(string CustomerEmail, decimal Total);

public sealed class SubmitOrderPipeline(
    OrderService orders,
    PaymentService payments,
    IShippingService shipping)
{
    public Task<Result<string>> SubmitAsync(int orderId, CancellationToken ct) =>
        // 1. Look up the order (Result<OrderDto>)
        orders.GetOrderByIdAsync(orderId, ct)
            // 2. Charge it (Result<string> — receipt) — async bind
            .BindAsync(order => payments.ChargeAsync(order.Id, order.Total, ct))
            // 3. Hand off to shipping (Result<string> — tracking number)
            .BindAsync(receipt => shipping.ShipAsync(orderId, receipt, ct));

    // A purely synchronous variant using Bind + the new ValidationError(identifier, message) ctor.
    public Result<decimal> ApplyDiscount(Result<OrderDto> orderResult, decimal percent)
    {
        if (percent is < 0m or > 100m)
            return Result<decimal>.Invalid(new ValidationError(nameof(percent), "Discount must be 0–100%."));

        return orderResult.Bind(order =>
        {
            var discounted = order.Total * (1m - percent / 100m);
            return Result<decimal>.Success(discounted);
        });
    }
}
```

Notes:
- `Bind` is for chaining `Result`-returning steps; `Map` is for chaining plain value-returning steps. Mixing them lets you build clean railway pipelines.
- `BindAsync` has overloads for every combination of `Task<Result<T>>` / `Result<T>` source and `Task<Result<U>>` / `Result<U>` continuation — including `Result<T>` → `Result` (void-like) variants.
- The new `ValidationError(identifier, errorMessage)` constructor is a lighter alternative to the four-argument form when you don't need an error code or custom severity.
