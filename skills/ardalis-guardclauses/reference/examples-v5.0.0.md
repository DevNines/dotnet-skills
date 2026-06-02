<!--
Generated for Ardalis.GuardClauses v5.0.0.
Do not edit by hand — rerun scripts/update_skill.py to regenerate.
-->

# Ardalis.GuardClauses

Canonical use-case reference for **Ardalis.GuardClauses v5.0.0**. Each example shows a guard at the top of a constructor or method, validating input before any real work begins. All identifiers are taken verbatim from the v5.0.0 public API surface.

## 1. Guard against null reference

Use `Guard.Against.Null` for any reference (or `Nullable<T>`) you can't proceed without.

```csharp
using Ardalis.GuardClauses;

namespace Billing;

public sealed class InvoiceService
{
    private readonly ICustomerRepository _customers;

    public InvoiceService(ICustomerRepository customers)
    {
        _customers = Guard.Against.Null(customers, nameof(customers));
    }
}
```

Notes:
- Throws `ArgumentNullException` by default.
- Returns the input on success, so it composes nicely with field assignment.
- A `Func<Exception>` overload (`exceptionCreator`) is available if you need to throw a custom exception type.

## 2. Guard against null or empty strings / collections

`NullOrEmpty` covers strings, `IEnumerable<T>`, and `Nullable<Guid>`. Use `NullOrWhiteSpace` when whitespace-only is also invalid.

```csharp
public sealed class EmailMessage
{
    public EmailMessage(string subject, IEnumerable<string> recipients, Guid? correlationId)
    {
        Subject       = Guard.Against.NullOrWhiteSpace(subject, nameof(subject));
        Recipients    = Guard.Against.NullOrEmpty(recipients, nameof(recipients));
        CorrelationId = Guard.Against.NullOrEmpty(correlationId, nameof(correlationId)).Value;
    }

    public string Subject { get; }
    public IEnumerable<string> Recipients { get; }
    public Guid CorrelationId { get; }
}
```

Notes:
- `NullOrEmpty` throws `ArgumentNullException` when the input is null and `ArgumentException` when it is empty.
- The `Nullable<Guid>` overload also rejects `Guid.Empty`.

## 3. Guard against out-of-range values

`OutOfRange` works on any `IComparable<T>` — numbers, `DateTime`, `TimeSpan`, custom value types. There is also an overload that validates every item in an `IEnumerable<T>`.

```csharp
public sealed record DateWindow
{
    public DateWindow(DateTime start, DateTime end)
    {
        Start = Guard.Against.OutOfRange(start, nameof(start), DateTime.UtcNow.AddYears(-10), DateTime.UtcNow.AddYears(10));
        End   = Guard.Against.OutOfRange(end,   nameof(end),   start, start.AddYears(1));
    }

    public DateTime Start { get; }
    public DateTime End { get; }
}
```

Notes:
- Throws `ArgumentOutOfRangeException` when `input < rangeFrom` or `input > rangeTo`.
- For SQL Server `datetime` columns, prefer `OutOfSQLDateRange` (see example 5).

## 4. Guard against negative or zero numeric arguments

`Negative` and `NegativeOrZero` have overloads for `int`, `long`, `float`, `double`, `decimal`, `TimeSpan`, and a generic `T : IComparable`. There's a matching `Zero` guard too.

```csharp
public sealed class Order
{
    public Order(int quantity, decimal unitPrice, TimeSpan shippingDelay)
    {
        Quantity      = Guard.Against.NegativeOrZero(quantity, nameof(quantity));
        UnitPrice     = Guard.Against.Negative(unitPrice, nameof(unitPrice));
        ShippingDelay = Guard.Against.Negative(shippingDelay, nameof(shippingDelay));
    }

    public int Quantity { get; }
    public decimal UnitPrice { get; }
    public TimeSpan ShippingDelay { get; }
}
```

Notes:
- All of these throw `ArgumentException` (not `ArgumentOutOfRangeException`).
- Pass a `message` argument for a custom error string, or an `exceptionCreator` to throw your own exception type.

## 5. Domain-specific guards: `Default`, `EnumOutOfRange`, `OutOfSQLDateRange`, `InvalidFormat`, `StringTooLong`, `LengthOutOfRange`

These cover common precondition shapes that go beyond plain null/range checks.

```csharp
public enum Priority { Low = 1, Normal = 2, High = 3 }

public sealed class Ticket
{
    public Ticket(Guid id, Priority priority, string emailAddress, string title, DateTime dueDate)
    {
        Id        = Guard.Against.Default(id, nameof(id));
        Priority  = Guard.Against.EnumOutOfRange(priority, nameof(priority));
        Email     = Guard.Against.InvalidFormat(emailAddress, nameof(emailAddress), @"^[^@\s]+@[^@\s]+\.[^@\s]+$");
        Title     = Guard.Against.LengthOutOfRange(title, 3, 120, nameof(title));
        DueDate   = Guard.Against.OutOfSQLDateRange(dueDate, nameof(dueDate));
    }

    public Guid Id { get; }
    public Priority Priority { get; }
    public string Email { get; }
    public string Title { get; }
    public DateTime DueDate { get; }
}
```

Notes:
- `Default(T)` throws `ArgumentException` when `input` equals `default(T)` — handy for `Guid`, `DateTime`, and value-typed IDs.
- `EnumOutOfRange` throws `InvalidEnumArgumentException` for values not defined on the enum.
- `OutOfSQLDateRange` rejects dates outside `SqlDateTime.MinValue..SqlDateTime.MaxValue`, avoiding round-trip surprises with SQL Server.
- `StringTooLong` / `StringTooShort` exist when you only need a one-sided length check.

## 6. `NotFound` for repository / lookup results

Pair `NotFound` with a lookup that returns null, so callers see a meaningful `NotFoundException` rather than a downstream NRE.

```csharp
public async Task<Customer> GetCustomerAsync(string customerId, CancellationToken ct)
{
    Guard.Against.NullOrWhiteSpace(customerId, nameof(customerId));

    var customer = await _customers.FindByIdAsync(customerId, ct);
    return Guard.Against.NotFound(customerId, customer, nameof(customerId));
}
```

Notes:
- Throws the library's own `NotFoundException` (the message embeds both the object name and the key).
- The generic overload `NotFound<TKey, T>` accepts any key type, not just `string`.

## 7. Writing a custom guard extension

Custom guards are just extension methods on `IGuardClause`. Once defined, they chain off `Guard.Against.*` like any built-in.

```csharp
namespace MyApp.Guards;

public static class IbanGuard
{
    public static string Iban(this IGuardClause guardClause, string input, string parameterName)
    {
        Guard.Against.NullOrWhiteSpace(input, parameterName);

        // Very rough IBAN sanity check: 2 letters, 2 digits, then up to 30 alphanumerics.
        return Guard.Against.InvalidFormat(
            input,
            parameterName,
            @"^[A-Z]{2}\d{2}[A-Z0-9]{1,30}$",
            message: $"'{parameterName}' is not a valid IBAN.");
    }
}

// Usage:
public sealed class BankAccount
{
    public BankAccount(string iban) => Iban = Guard.Against.Iban(iban, nameof(iban));
    public string Iban { get; }
}
```

Notes:
- Extending `IGuardClause` (not `Guard` itself) is what makes the `Guard.Against.Iban(...)` call site work.
- Compose with existing guards inside your own — there is no need to re-implement null or format checks.

## 8. New in v5.0: deprecated `AgainstExpression` reminds you to reverse the predicate

v5.0 sharpens the `[Obsolete]` message on the legacy `AgainstExpression` overloads to call out that the modern `Expression` API uses the **opposite** predicate convention. `AgainstExpression` throws when `func` returns **false**; `Expression` throws when `func` returns **true** (the predicate describes the *invalid* state).

```csharp
// Old (deprecated in v5.0 — kept for source compatibility, emits an Obsolete warning):
#pragma warning disable CS0618
Guard.Against.AgainstExpression<int>(
    func:    x => x > 0,                 // returns TRUE for VALID input
    input:   age,
    message: "Age must be positive.");
#pragma warning restore CS0618

// New (preferred): predicate describes the INVALID state.
Guard.Against.Expression<int>(
    func:          x => x <= 0,          // returns TRUE for INVALID input
    input:         age,
    message:       "Age must be positive.",
    parameterName: nameof(age));

// Async variant follows the same reversed convention.
await Guard.Against.ExpressionAsync<string>(
    func:          async s => string.IsNullOrEmpty(await NormalizeAsync(s)),
    input:         rawCode,
    message:       "Code normalizes to an empty value.",
    parameterName: nameof(rawCode));
```

Notes:
- If you upgrade from v4.x and silence the `Obsolete` warning without flipping the predicate, **every call will now throw on valid input**. Read each warning carefully and invert the logic when you migrate.
- `Expression` / `ExpressionAsync` also accept an `exceptionCreator` (`Func<Exception>`) for fully custom exception types.
