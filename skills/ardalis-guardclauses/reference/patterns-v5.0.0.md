# Ardalis.GuardClauses v5.0.0 — patterns

## What guard clauses are for

A guard clause is a short, declarative precondition check at the top of a method or constructor that fails fast with a clear exception when an argument violates a stated assumption. Without them, defensive code degenerates into repetitive `if (x == null) throw new ArgumentNullException(nameof(x));` lines, inconsistent exception types ("did I throw `ArgumentException` here or `InvalidOperationException`?"), and easy-to-skip checks that surface as confusing `NullReferenceException`s deep in the call stack. `Ardalis.GuardClauses` consolidates these checks into a single, well-named vocabulary (`Guard.Against.Null`, `Guard.Against.NegativeOrZero`, ...) so the intent is obvious and the exception thrown is always the conventional one.

Guards belong wherever **untrusted or external input crosses an API boundary in code**: public and internal constructors, factory methods, public service methods, application-service entry points, and the constructors of domain entities and value objects. They document the contract in executable form.

Guards do **not** belong:

- **Inside hot loops.** Validate at the entry boundary; do not re-check the same arguments on every iteration.
- **As a replacement for FluentValidation / DataAnnotations on incoming DTOs.** Guards throw — they are for programmer-error preconditions, not for shape validation of user input.
- **For business invariants that need a domain-specific result.** If "customer has no active subscription" is an expected outcome, return `Ardalis.Result` or throw a domain exception — do not bend a guard into throwing `ArgumentException` for a business rule.

## Canonical usage

```csharp
using Ardalis.GuardClauses;

public sealed class Order
{
    public Order(Guid id, string customerEmail, int quantity, decimal unitPrice, DateTime placedAt)
    {
        Id           = Guard.Against.NullOrEmpty(id, nameof(id));
        CustomerEmail = Guard.Against.NullOrWhiteSpace(customerEmail, nameof(customerEmail));
        Quantity     = Guard.Against.NegativeOrZero(quantity, nameof(quantity));
        UnitPrice    = Guard.Against.Negative(unitPrice, nameof(unitPrice));
        PlacedAt     = Guard.Against.OutOfSQLDateRange(placedAt, nameof(placedAt));
    }

    public Guid     Id            { get; }
    public string   CustomerEmail { get; }
    public int      Quantity      { get; }
    public decimal  UnitPrice     { get; }
    public DateTime PlacedAt      { get; }
}
```

Two things to note:

1. Every guard **returns the validated value**, so you can assign in one line.
2. Always pass `nameof(arg)` as the second argument so `ArgumentException.ParamName` is correct.

## Which guard to use

| Precondition shape                     | Guard (v5.0.0)                                                  |
| -------------------------------------- | --------------------------------------------------------------- |
| Reference is null                      | `Guard.Against.Null(input, nameof(input))`                      |
| Nullable value type is null            | `Guard.Against.Null(nullableInput, nameof(nullableInput))`      |
| String null or `""`                    | `Guard.Against.NullOrEmpty(s, nameof(s))`                       |
| String null/empty/whitespace           | `Guard.Against.NullOrWhiteSpace(s, nameof(s))`                  |
| String too long / too short            | `Guard.Against.StringTooLong(s, 100, nameof(s))` / `StringTooShort` |
| String length outside `[min,max]`      | `Guard.Against.LengthOutOfRange(s, 1, 100, nameof(s))`          |
| String must match regex                | `Guard.Against.InvalidFormat(s, nameof(s), @"^\d{5}$")`         |
| Empty `Guid`                           | `Guard.Against.NullOrEmpty(guid, nameof(guid))`                 |
| Empty `IEnumerable<T>`                 | `Guard.Against.NullOrEmpty(items, nameof(items))`               |
| Numeric below zero                     | `Guard.Against.Negative(n, nameof(n))`                          |
| Numeric `<= 0`                         | `Guard.Against.NegativeOrZero(n, nameof(n))`                    |
| Numeric `== 0`                         | `Guard.Against.Zero(n, nameof(n))`                              |
| Value outside `[from, to]`             | `Guard.Against.OutOfRange(n, nameof(n), 1, 10)`                 |
| Every item in collection in `[from, to]`| `Guard.Against.OutOfRange(items, nameof(items), 1, 10)`        |
| `default(T)` for value/struct type     | `Guard.Against.Default(value, nameof(value))`                   |
| Invalid enum value                     | `Guard.Against.EnumOutOfRange(e, nameof(e))`                    |
| `DateTime` outside SQL Server range    | `Guard.Against.OutOfSQLDateRange(dt, nameof(dt))`               |
| Arbitrary predicate must hold          | `Guard.Against.InvalidInput(x, nameof(x), v => v.IsValid())`    |
| Lookup returned null                   | `Guard.Against.NotFound(key, entity, nameof(key))`              |
| Generic expression must be true        | `Guard.Against.AgainstExpression(v => v > 0, x, "must be > 0")` |

Every method above also accepts an optional `message` and an optional `Func<Exception> exceptionCreator` if you need to throw a custom exception instead of the default `ArgumentException` family.

## Custom guard clauses

Add a domain-specific guard by writing an extension on `IGuardClause`. That's the same interface the built-in extensions hang off, so it slots into the `Guard.Against.X` syntax cleanly.

```csharp
using System.Text.RegularExpressions;
using Ardalis.GuardClauses;

public static class EmailGuard
{
    private static readonly Regex EmailRegex =
        new(@"^[^@\s]+@[^@\s]+\.[^@\s]+$", RegexOptions.Compiled);

    public static string InvalidEmail(
        this IGuardClause guardClause,
        string input,
        string parameterName)
    {
        Guard.Against.NullOrWhiteSpace(input, parameterName);

        if (!EmailRegex.IsMatch(input))
            throw new ArgumentException($"'{input}' is not a valid email.", parameterName);

        return input;
    }
}

// Usage:
// CustomerEmail = Guard.Against.InvalidEmail(customerEmail, nameof(customerEmail));
```

Tip: for simple regex cases, prefer the built-in `Guard.Against.InvalidFormat(input, parameterName, pattern)` — only write a custom extension when you want a dedicated name in the call site or extra logic.

## Things to avoid

- **Do not run guards over user-supplied request data inside an endpoint or handler.** A guard throws — the request will crash with a 500. Validate user input with FluentValidation, model binding attributes, or `Ardalis.Result`. Reserve guards for arguments that *should never* be wrong if the calling code is correct.

- **Do not `catch` `ArgumentException` / `ArgumentNullException` / `NotFoundException` to "recover".** Guard failures signal programming errors. Let them bubble. If you have a recoverable scenario (entity not found is expected), return a result type instead of relying on `Guard.Against.NotFound`.

- **Do not omit `nameof(arg)`.** Without the parameter name the resulting `ParamName` is `null` or wrong, and stack traces are far less useful when triaging in production. v5.0.0's signatures take `parameterName` as a regular string argument — pass it explicitly:

  ```csharp
  // BAD — ParamName is empty
  Guard.Against.Null(customer, "");

  // GOOD
  Guard.Against.Null(customer, nameof(customer));
  ```

- **Do not "guard and then dereference unsafely anyway."** A guard's return value is the validated value; use it.

  ```csharp
  // BAD — the guard return is discarded, and a later refactor could
  // remove the guard without the compiler noticing the NRE risk.
  Guard.Against.Null(customer, nameof(customer));
  _repo.Save(customer);

  // GOOD — assignment makes the dependency explicit.
  var safeCustomer = Guard.Against.Null(customer, nameof(customer));
  _repo.Save(safeCustomer);
  ```

- **Do not use `Guard.Against.NotFound` as a substitute for a Result type in query paths.** It throws `NotFoundException`, which is appropriate at a service boundary that maps it to HTTP 404, but it is not appropriate for control flow where "missing" is just one of several normal outcomes.

- **Do not stack guards inside tight loops.** If `items` must all be positive integers, prefer the collection-aware overload (`Guard.Against.OutOfRange(items, nameof(items), 1, int.MaxValue)`) once, rather than guarding inside a `foreach`.
