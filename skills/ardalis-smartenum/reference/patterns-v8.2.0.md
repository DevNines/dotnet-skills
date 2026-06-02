# Ardalis.SmartEnum v8.2.0 — patterns

## What SmartEnum is for

A plain C# `enum` is just a named integer. It carries no behavior, no display
string, no validation: casting an arbitrary `int` to your `OrderStatus` enum
silently succeeds even if no such member exists, and there is no built-in way
to look one up by display name or to attach per-member data like a tax rate or
a localized label. Adding a new member forces you to find and update every
`switch` statement in the codebase, and the compiler will not help you when
you miss one.

`SmartEnum` replaces the integer-with-a-name with a real reference type. Each
member is a singleton `public static readonly` instance of the class, so you
get equality semantics, IntelliSense, the full power of polymorphism, and the
ability to attach arbitrary state and behavior per member. It fits well for
status sets that need a display string, lookup tables (tax/fee per status,
shipping rules per region), dispatch tables that previously lived as ugly
`switch` blocks, and domain enums that need to round-trip through JSON or
EF Core in a controlled way.

It does **not** belong in:

- **Hot inner loops.** Lookups go through dictionaries; for a tight numeric
  loop, a plain `enum` is cheaper.
- **Bit-set / `[Flags]` semantics on the regular `SmartEnum<T>` type.** Use
  `SmartFlagEnum<T>` (also in this package) if you genuinely need OR-able
  composition — don't try to OR `SmartEnum` members yourself.
- **Trivial pairs.** If the type has two states (`On`/`Off`), a `bool` is
  clearer.

## Naming conventions

| Thing | Convention | Example |
|---|---|---|
| SmartEnum class | Singular noun, `sealed` | `OrderStatus`, `Currency` |
| Member field | The identifier callers write in code | `Pending`, `Paid`, `Shipped` |
| Member value | The persisted/wire value; usually mirror the legacy `enum` ints for migration | `1`, `2`, `3` or `"USD"`, `"EUR"` |
| File layout | One file per SmartEnum (`OrderStatus.cs`) | colocate only if the type is tiny and single-use |

## Where each piece of code lives

| Concern | Where it goes |
|---|---|
| The set of members | `public static readonly` fields on the SmartEnum class |
| Per-member data (display, rate, code) | Constructor parameters captured into properties |
| Per-member behavior | `abstract` methods on the base class + nested derived classes per member, **or** captured `Func`/`Action` delegates |
| Lookup by name | `FromName(name)` / `TryFromName(name, out result)` (case-insensitive overloads available) |
| Lookup by value | `FromValue(value)` / `TryFromValue(value, out result)` |
| Enumerate every member | `OrderStatus.List` |
| Persistence as int/string | `Ardalis.SmartEnum.EFCore.SmartEnumConverter<TEnum, TValue>` or the `ConfigureSmartEnum` extension |
| JSON over the wire | `SmartEnumNameConverter<TEnum, TValue>` or `SmartEnumValueConverter<TEnum, TValue>` from `Ardalis.SmartEnum.SystemTextJson` |
| Dapper mapping | Inherit `DapperSmartEnumByName<T>` / `DapperSmartEnumByValue<T>` or call `DapperRegistration<,>.EnsureTypeHandlerAdded()` |
| MVC model validation | `[SmartEnumName(typeof(OrderStatus), nameof(StatusName))]` on the DTO property |

## Canonical shape

Use `SmartEnum<TEnum>` for int-valued enums (the most common case — easy
migration from legacy `enum`):

```csharp
using Ardalis.SmartEnum;

public sealed class OrderStatus : SmartEnum<OrderStatus>
{
    public static readonly OrderStatus Pending = new(nameof(Pending), 1, "Awaiting payment");
    public static readonly OrderStatus Paid    = new(nameof(Paid),    2, "Payment received");
    public static readonly OrderStatus Shipped = new(nameof(Shipped), 3, "On its way");
    public static readonly OrderStatus Closed  = new(nameof(Closed),  4, "Complete");

    public string DisplayName { get; }

    private OrderStatus(string name, int value, string displayName) : base(name, value)
    {
        DisplayName = displayName;
    }
}
```

Use `SmartEnum<TEnum, TValue>` when the value isn't an `int` (ISO codes,
domain strings, longs):

```csharp
public sealed class Currency : SmartEnum<Currency, string>
{
    public static readonly Currency Usd = new(nameof(Usd), "USD", "US Dollar");
    public static readonly Currency Eur = new(nameof(Eur), "EUR", "Euro");
    public static readonly Currency Gbp = new(nameof(Gbp), "GBP", "British Pound");

    public string DisplayName { get; }

    private Currency(string name, string value, string displayName) : base(name, value)
    {
        DisplayName = displayName;
    }
}
```

### Per-member behavior via subclasses

When members need different logic (not just different data), use nested
private subclasses and an `abstract` method on the base:

```csharp
public abstract class PaymentMethod : SmartEnum<PaymentMethod>
{
    public static readonly PaymentMethod Card   = new CardMethod();
    public static readonly PaymentMethod Cash   = new CashMethod();
    public static readonly PaymentMethod Invoice = new InvoiceMethod();

    private PaymentMethod(string name, int value) : base(name, value) { }

    public abstract decimal SurchargeOn(decimal amount);

    private sealed class CardMethod    : PaymentMethod { public CardMethod()    : base("Card", 1)    { } public override decimal SurchargeOn(decimal a) => a * 0.025m; }
    private sealed class CashMethod    : PaymentMethod { public CashMethod()    : base("Cash", 2)    { } public override decimal SurchargeOn(decimal a) => 0m; }
    private sealed class InvoiceMethod : PaymentMethod { public InvoiceMethod() : base("Invoice", 3) { } public override decimal SurchargeOn(decimal a) => 5m; }
}
```

## JSON serialization (System.Text.Json)

Pick one form per type. Name converters produce `"Paid"`; value converters
produce `2`. Name is friendlier for humans/APIs; value is more compact and
matches legacy `enum` payloads.

```csharp
using System.Text.Json.Serialization;
using Ardalis.SmartEnum;
using Ardalis.SmartEnum.SystemTextJson;

[JsonConverter(typeof(SmartEnumNameConverter<OrderStatus, int>))]
public sealed class OrderStatus : SmartEnum<OrderStatus>
{
    // members as above...
    private OrderStatus(string name, int value) : base(name, value) { }
}
```

For the string-valued `Currency`, the second generic argument is the value
type:

```csharp
[JsonConverter(typeof(SmartEnumValueConverter<Currency, string>))]
public sealed class Currency : SmartEnum<Currency, string> { /* ... */ }
```

## EF Core persistence

The simplest wiring uses `ConfigureSmartEnum` from `SmartEnum.EFCore`, which
attaches a `SmartEnumConverter<,>` to every SmartEnum-typed property in the
model:

```csharp
using SmartEnum.EFCore;

public sealed class AppDbContext : DbContext
{
    protected override void ConfigureConventions(ModelConfigurationBuilder builder)
    {
        builder.ConfigureSmartEnum();
    }
}
```

Or attach the converter per-property explicitly:

```csharp
modelBuilder.Entity<Order>()
    .Property(o => o.Status)
    .HasConversion(new SmartEnumConverter<OrderStatus, int>());
```

## Testing

`SmartEnum<T>.List` exposes every public static readonly member at runtime,
which makes "did someone accidentally remove a status?" a test failure
rather than a 3am production surprise:

```csharp
[Fact]
public void OrderStatus_has_the_expected_members()
{
    var expected = new (string Name, int Value)[]
    {
        ("Pending", 1), ("Paid", 2), ("Shipped", 3), ("Closed", 4),
    };

    OrderStatus.List
        .Select(s => (s.Name, s.Value))
        .Should().BeEquivalentTo(expected);
}

[Fact]
public void FromValue_rejects_unknown_value()
{
    Action act = () => OrderStatus.FromValue(99);
    act.Should().Throw<KeyNotFoundException>();
}
```

## Things to avoid

- **Don't instantiate a SmartEnum outside a `public static readonly` field.**
  Singletons are the whole point — ad-hoc `new OrderStatus(...)` calls break
  reference equality and won't appear in `List`, `FromName`, or `FromValue`.
- **Don't OR `SmartEnum` members together** to build a flag set. If you need
  flags, use the dedicated `SmartFlagEnum<T>` base (which has its own
  `FromValue`/`FromName` semantics for power-of-two composition) or a plain
  `[Flags] enum`. Never try to make regular `SmartEnum` act as a bit-set.
- **Don't `switch` on `instance.Value` across the codebase.** That recreates
  the original `enum` problem — every new member is another bug waiting to
  ship. Prefer either:
  - pattern-matching on the singleton instance reference, or
  - the fluent `instance.When(X).Then(...).When(Y).Then(...).Default(...)`
    helper, or
  - pushing the dispatch into the SmartEnum class as an `abstract`/`virtual`
    method (see `PaymentMethod` above).
- **Don't cast `int -> SmartEnum`.** There is no such cast for the normal
  `SmartEnum<T>`. Use `FromValue(int)` — it throws `KeyNotFoundException` on
  unknown input — or `TryFromValue` when the input is untrusted. (There is
  an implicit `SmartEnum -> TValue` conversion the other direction, which is
  fine to use.)
- **Don't mix serializer libraries within one project.** The package ships
  adapters for System.Text.Json, Utf8Json, Dapper, and EF Core; they can
  coexist on the type, but pick one wire format per project so the same
  domain value doesn't appear as `"Paid"` in one endpoint and `2` in
  another.
- **Don't omit the `[SmartEnumName]` attribute on inbound DTOs** if you bind
  status names from query strings or JSON property fields directly. It
  validates against the actual `List`, so a typo fails model binding instead
  of producing a `KeyNotFoundException` deeper in the handler.
