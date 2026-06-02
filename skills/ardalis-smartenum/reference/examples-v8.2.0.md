<!--
Generated examples reference for Ardalis.SmartEnum v8.2.0.
DO NOT EDIT BY HAND — rerun scripts/update_skill.py to regenerate.
-->

# Ardalis.SmartEnum

Canonical examples for **Ardalis.SmartEnum v8.2.0** and its sibling adapters
(`SystemTextJson` 8.1.0, `EFCore` 8.2.0, `AutoFixture` 8.1.0, `Dapper` 8.2.0,
`Utf8Json` 8.1.0). Each block is verified against the public API surface that
ships in those NuGet packages.

## 1. The minimal SmartEnum

A `sealed` class deriving from `SmartEnum<TSelf>` (the `int`-valued
convenience base). Members are `public static readonly` fields and are
discovered reflectively, so adding a new one is a non-breaking change for
existing consumers.

```csharp
using Ardalis.SmartEnum;

namespace Shop.Domain;

public sealed class OrderStatus : SmartEnum<OrderStatus>
{
    public static readonly OrderStatus Pending   = new(nameof(Pending),   1);
    public static readonly OrderStatus Paid      = new(nameof(Paid),      2);
    public static readonly OrderStatus Shipped   = new(nameof(Shipped),   3);
    public static readonly OrderStatus Cancelled = new(nameof(Cancelled), 4);

    private OrderStatus(string name, int value) : base(name, value) { }
}
```

Notes:
- Equality (`==`, `Equals`) compares by `Value`, not by reference — two
  instances with the same value are equal.
- The constructor is `private` so callers cannot mint extra instances.
- `SmartEnum<T>` is the `int`-valued shorthand for `SmartEnum<T, int>`.

## 2. A SmartEnum with a custom value type

Use `SmartEnum<TSelf, TValue>` when the natural identifier isn't an `int`
— for example, ISO 4217 currency codes are strings. `TValue` must implement
`IEquatable<TValue>` and `IComparable<TValue>`.

```csharp
using Ardalis.SmartEnum;

namespace Shop.Domain;

public sealed class Currency : SmartEnum<Currency, string>
{
    public static readonly Currency Usd = new("US Dollar", "USD");
    public static readonly Currency Eur = new("Euro",      "EUR");
    public static readonly Currency Jpy = new("Yen",       "JPY");

    private Currency(string name, string value) : base(name, value) { }
}
```

Notes:
- For string-valued enums, decorate the class with
  `[SmartEnumStringComparer(StringComparison.OrdinalIgnoreCase)]` if you
  want case-insensitive value comparison.
- There is an implicit conversion from `Currency` to `string` and an
  explicit one back (`(Currency)"USD"`).

## 3. A SmartEnum that carries behavior

The whole point of SmartEnum over `enum` is letting each member carry
data and/or behavior. Either expose additional properties via the
constructor, or declare an `abstract`/`virtual` method and override it in
nested subclasses.

```csharp
using Ardalis.SmartEnum;

namespace Shop.Domain;

public abstract class TaxBracket : SmartEnum<TaxBracket>
{
    public static readonly TaxBracket Standard = new StandardBracket();
    public static readonly TaxBracket Reduced  = new ReducedBracket();
    public static readonly TaxBracket Zero     = new ZeroBracket();

    private TaxBracket(string name, int value) : base(name, value) { }

    public abstract decimal Apply(decimal subtotal);

    private sealed class StandardBracket : TaxBracket
    {
        public StandardBracket() : base("Standard", 1) { }
        public override decimal Apply(decimal subtotal) => subtotal * 1.20m;
    }

    private sealed class ReducedBracket : TaxBracket
    {
        public ReducedBracket() : base("Reduced", 2) { }
        public override decimal Apply(decimal subtotal) => subtotal * 1.05m;
    }

    private sealed class ZeroBracket : TaxBracket
    {
        public ZeroBracket() : base("Zero", 3) { }
        public override decimal Apply(decimal subtotal) => subtotal;
    }
}

// Usage:
// decimal total = TaxBracket.Reduced.Apply(100m);   // 105.00
```

Notes:
- The outer class is `abstract`; only the nested implementations are
  instantiable.
- `When(...).Then(...)` is the functional alternative if you don't want
  per-instance subclasses (see example 4).

## 4. Looking up an instance by name or value

```csharp
using Ardalis.SmartEnum;

// By name — throws KeyNotFoundException if missing
var paid = OrderStatus.FromName("Paid");

// Case-insensitive name lookup
var shipped = OrderStatus.FromName("shipped", ignoreCase: true);

// By value — throws KeyNotFoundException if missing
var pending = OrderStatus.FromValue(1);

// By value, with a fallback instead of an exception
var unknown = OrderStatus.FromValue(99, defaultValue: OrderStatus.Pending);

// Try-pattern variants
if (OrderStatus.TryFromName("Cancelled", out var cancelled))
{
    // use cancelled
}

if (OrderStatus.TryFromValue(2, out var byValue))
{
    // use byValue
}

// Switch-style fluent dispatch
OrderStatus.Paid
    .When(OrderStatus.Pending).Then(() => Console.WriteLine("Awaiting payment"))
    .When(OrderStatus.Paid).Then(() => Console.WriteLine("Capture funds"))
    .When(new[] { OrderStatus.Shipped, OrderStatus.Cancelled })
        .Then(() => Console.WriteLine("Terminal state"))
    .Default(() => Console.WriteLine("Unknown"));
```

Notes:
- `FromName` is case-sensitive by default; pass `ignoreCase: true` to
  relax it.
- For unrecognized inputs prefer `TryFromName` / `TryFromValue` over
  catching `KeyNotFoundException`.

## 5. Enumerating all instances

`SmartEnum<T, TValue>.List` returns every public static readonly field of
the type (and its bases) in name-sorted order.

```csharp
foreach (var status in OrderStatus.List)
{
    Console.WriteLine($"{status.Value}: {status.Name}");
}

// LINQ over the collection
var terminalStatuses = OrderStatus.List
    .Where(s => s == OrderStatus.Shipped || s == OrderStatus.Cancelled)
    .ToArray();
```

Notes:
- `List` is materialized once via a thread-safe `Lazy<>` and cached for
  the lifetime of the type.
- In v8.2 the backing collection type changed from `TEnum[]` to
  `List<TEnum>` — see example 8 for details.

## 6. JSON with `Ardalis.SmartEnum.SystemTextJson`

Two converters ship: `SmartEnumNameConverter<TEnum, TValue>` writes the
`Name`, `SmartEnumValueConverter<TEnum, TValue>` writes the `Value`. Pick
one per property (or per DTO) by attribute.

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
using Ardalis.SmartEnum.SystemTextJson;

public sealed record OrderDto(
    Guid Id,

    [property: JsonConverter(typeof(SmartEnumNameConverter<OrderStatus, int>))]
    OrderStatus Status,

    [property: JsonConverter(typeof(SmartEnumValueConverter<Currency, string>))]
    Currency Currency);

// Round-trip
var dto = new OrderDto(Guid.NewGuid(), OrderStatus.Paid, Currency.Eur);

string json = JsonSerializer.Serialize(dto);
// => {"Id":"…","Status":"Paid","Currency":"EUR"}

var back = JsonSerializer.Deserialize<OrderDto>(json);
// back.Status == OrderStatus.Paid
```

Notes:
- The two generic arguments mirror `SmartEnum<TEnum, TValue>`. For an
  `int`-valued SmartEnum that derives from `SmartEnum<T>`, pass
  `<OrderStatus, int>`.
- Name vs Value is a wire-format decision: Name is human-readable and
  survives value renumbering; Value is compact and survives renaming.
- Both converters also implement `ReadAsPropertyName` / `WriteAsPropertyName`,
  so SmartEnums work as dictionary keys.

## 7. EF Core value conversion with `Ardalis.SmartEnum.EFCore`

Two integration styles. Per-property with `HasConversion`:

```csharp
using Microsoft.EntityFrameworkCore;
using Ardalis.SmartEnum.EFCore;

public sealed class Order
{
    public Guid Id { get; set; }
    public OrderStatus Status { get; set; } = OrderStatus.Pending;
    public Currency Currency { get; set; } = Currency.Usd;
}

public sealed class ShopContext : DbContext
{
    public DbSet<Order> Orders => Set<Order>();

    protected override void OnModelCreating(ModelBuilder modelBuilder)
    {
        modelBuilder.Entity<Order>()
            .Property(o => o.Status)
            .HasConversion(new SmartEnumConverter<OrderStatus, int>());

        modelBuilder.Entity<Order>()
            .Property(o => o.Currency)
            .HasConversion(new SmartEnumConverter<Currency, string>());
    }
}
```

Or, register the converter for **every** SmartEnum-typed property at once
using the extension method:

```csharp
using SmartEnum.EFCore;

public sealed class ShopContext : DbContext
{
    public DbSet<Order> Orders => Set<Order>();

    protected override void OnModelCreating(ModelBuilder modelBuilder)
    {
        // Discovers every SmartEnum<TEnum, TValue>-typed property on every entity
        // and wires up SmartEnumConverter<TEnum, TValue> automatically.
        modelBuilder.ConfigureSmartEnum();
    }

    protected override void ConfigureConventions(ModelConfigurationBuilder configurationBuilder)
    {
        // Or set it up at the model-configuration level instead of per-model.
        configurationBuilder.ConfigureSmartEnum();
    }
}
```

Notes:
- `SmartEnumConverter<TEnum, TValue>` stores the underlying `Value` in the
  column, so a renamed member is a non-breaking schema change but a
  renumbered member is a breaking one.
- `ConfigureSmartEnum` is the bulk-registration shortcut from the
  `SmartEnum.EFCore` namespace (note the slightly different namespace
  from the converter itself).

## 8. New in v8.2: `List` is now backed by `List<TEnum>` (WASM-friendly)

The only public-surface-affecting change in v8.2 is that
`SmartEnum<TEnum, TValue>` and its sibling `SmartFlagEnum<TEnum, TValue>`
build their internal cache as `List<TEnum>` instead of `TEnum[]` to work
around a .NET 9 Blazor WebAssembly trimming/AOT issue
([#557](https://github.com/ardalis/SmartEnum/pull/557)). The `List`
property still exposes an `IReadOnlyCollection<TEnum>`, so no caller
changes are required — but if you were treating it as an array you now
get the more general collection semantics.

```csharp
// Works the same as before — order, count, iteration are unchanged.
IReadOnlyCollection<OrderStatus> all = OrderStatus.List;

Console.WriteLine($"Defined statuses: {all.Count}");
foreach (var s in all)
    Console.WriteLine($"  {s.Value} = {s.Name}");

// If you had code like this it still compiles, because LINQ works
// against any IEnumerable<T>:
var byValue = OrderStatus.List.OrderBy(s => s.Value).ToArray();

// What no longer works (and never officially did): assuming the runtime
// type is TEnum[]. If you had reflection or a cast that depended on
// array-ness, switch to List<T> / IReadOnlyList<T>.
```

Notes:
- This is a runtime-shape change, not an API-shape change — `List`'s
  declared type is unchanged.
- Upgrade impact for Blazor WebAssembly on .NET 9: previously crashed
  during AOT/trimming in some configurations; now works.
- Everything else in the 8.2 release is package-reference bumps.
