<!--
Ardalis.Specification examples for v8.x
Generated against: 8.0.0
Do not edit by hand — rerun scripts/update_skill.py to regenerate.
-->

# Ardalis.Specification

Canonical examples for **Ardalis.Specification v8.x** (built against `8.0.0`). Every snippet uses only members from the v8 public surface. For the conceptual overview see `patterns-v8.md`.

Assumed entity model (used throughout):

```csharp
namespace MyApp.Domain;

public sealed class Customer
{
    public int Id { get; set; }
    public string Name { get; set; } = default!;
    public string Email { get; set; } = default!;
    public bool IsActive { get; set; }
    public DateTime CreatedOn { get; set; }
    public int CountryId { get; set; }
    public Country Country { get; set; } = default!;
    public List<Order> Orders { get; set; } = new();
}

public sealed class Country { public int Id { get; set; } public string Name { get; set; } = default!; }
public sealed class Order   { public int Id { get; set; } public DateTime PlacedOn { get; set; } public List<OrderLine> Lines { get; set; } = new(); }
public sealed class OrderLine { public int Id { get; set; } public string Sku { get; set; } = default!; public decimal Price { get; set; } }
```

---

## 1. Simple single-criterion filter spec

The most common shape: derive from `Specification<T>` and configure the query in the constructor with the fluent builder.

```csharp
using Ardalis.Specification;

namespace MyApp.Specs;

public sealed class ActiveCustomersSpec : Specification<Customer>
{
    public ActiveCustomersSpec()
    {
        Query.Where(c => c.IsActive);
    }
}
```

Notes:
- `Query` is the protected fluent builder exposed by `Specification<T>`.
- `Where` is additive — call it multiple times to AND-combine predicates.

---

## 2. Spec with Include / ThenInclude

Use `Include` for navigation properties and chain `ThenInclude` for nested navigations. Includes are evaluator-driven, so they only materialize when run against EF Core / EF6 — not in-memory `Evaluate`.

```csharp
using Ardalis.Specification;

namespace MyApp.Specs;

public sealed class CustomerWithOrdersByIdSpec : SingleResultSpecification<Customer>
{
    public CustomerWithOrdersByIdSpec(int customerId)
    {
        Query
            .Where(c => c.Id == customerId)
            .Include(c => c.Country)
            .Include(c => c.Orders)
                .ThenInclude(o => o.Lines);
    }
}
```

Notes:
- Inheriting from `SingleResultSpecification<T>` marks the spec as returning at most one row, which makes it usable with `SingleOrDefaultAsync` on the repository.
- Use `AsSplitQuery()` if the cartesian explosion from multiple collection includes becomes a problem (EF Core 5+ only).

---

## 3. Paged + sorted list spec (with constructor validation)

`Skip`, `Take`, `OrderBy` / `OrderByDescending` and their `ThenBy` continuations cover paging and sorting. Validate inputs eagerly — the spec is a domain object and shouldn't accept garbage.

```csharp
using Ardalis.Specification;

namespace MyApp.Specs;

public sealed class CustomersByCountryPagedSpec : Specification<Customer>
{
    public CustomersByCountryPagedSpec(int countryId, int page, int pageSize)
    {
        if (page < 1) throw new ArgumentOutOfRangeException(nameof(page));
        if (pageSize is < 1 or > 200) throw new ArgumentOutOfRangeException(nameof(pageSize));

        Query
            .Where(c => c.CountryId == countryId && c.IsActive)
            .OrderBy(c => c.Name)
                .ThenByDescending(c => c.CreatedOn)
            .Skip((page - 1) * pageSize)
            .Take(pageSize);
    }
}
```

Notes:
- A spec may contain at most one `OrderBy`/`OrderByDescending` root; subsequent ordering must be `ThenBy`/`ThenByDescending` or you'll get `DuplicateOrderChainException` at evaluation time.
- Likewise, only one `Skip` and one `Take` are allowed (`DuplicateSkipException` / `DuplicateTakeException`).

---

## 4. Projected spec (`Specification<TEntity, TResult>`)

Project to a DTO with `Select` so the database returns only the columns you need.

```csharp
using Ardalis.Specification;

namespace MyApp.Specs;

public sealed record CustomerListItem(int Id, string Name, string CountryName);

public sealed class CustomerListItemsSpec : Specification<Customer, CustomerListItem>
{
    public CustomerListItemsSpec(string? nameFilter)
    {
        Query
            .Where(c => c.IsActive)
            .Where(c => c.Name.Contains(nameFilter!), !string.IsNullOrWhiteSpace(nameFilter))
            .OrderBy(c => c.Name);

        Query.Select(c => new CustomerListItem(c.Id, c.Name, c.Country.Name));
    }
}
```

Notes:
- The two-argument `Where` overload accepts a `condition` boolean — if `false`, the predicate is skipped. Same pattern works for `OrderBy`, `Include`, `Skip`, `Take`, etc.
- Exactly one of `Select` or `SelectMany` may be used per spec — using both throws `ConcurrentSelectorsException`.

---

## 5. Read-only repository injection in a service

Inject `IReadRepositoryBase<T>` (read-only) where the service only queries, and `IRepositoryBase<T>` only when it must mutate.

```csharp
using Ardalis.Specification;
using MyApp.Domain;
using MyApp.Specs;

namespace MyApp.Application;

public sealed class CustomerQueryService
{
    private readonly IReadRepositoryBase<Customer> _customers;

    public CustomerQueryService(IReadRepositoryBase<Customer> customers)
    {
        ArgumentNullException.ThrowIfNull(customers);
        _customers = customers;
    }

    public Task<List<CustomerListItem>> SearchAsync(
        string? nameFilter,
        CancellationToken ct = default)
    {
        var spec = new CustomerListItemsSpec(nameFilter);
        return _customers.ListAsync(spec, ct);
    }

    public Task<Customer?> GetWithOrdersAsync(int id, CancellationToken ct = default)
    {
        var spec = new CustomerWithOrdersByIdSpec(id);
        return _customers.SingleOrDefaultAsync(spec, ct);
    }
}
```

Notes:
- Prefer `SingleOrDefaultAsync` (which requires `ISingleResultSpecification<T>`) over the obsolete `GetBySpecAsync` for single-row queries — `GetBySpecAsync` is marked `[Obsolete]` in v8.
- `FirstOrDefaultAsync(ISpecification<T>, …)` is the right choice when the spec may legitimately match more than one row and you only want the first.

---

## 6. DI registration in the composition root

Register the EF Core repository implementation (`Ardalis.Specification.EntityFrameworkCore.RepositoryBase<T>`) once and expose both interfaces.

```csharp
using Ardalis.Specification;
using Ardalis.Specification.EntityFrameworkCore;
using Microsoft.EntityFrameworkCore;
using MyApp.Infrastructure;

var builder = WebApplication.CreateBuilder(args);

builder.Services.AddDbContext<AppDbContext>(o =>
    o.UseSqlServer(builder.Configuration.GetConnectionString("Default")));

// Generic repository — same instance satisfies both interfaces.
builder.Services.AddScoped(typeof(IRepositoryBase<>), typeof(EfRepository<>));
builder.Services.AddScoped(typeof(IReadRepositoryBase<>), typeof(EfRepository<>));

builder.Services.AddScoped<CustomerQueryService>();

var app = builder.Build();
app.Run();
```

Where `EfRepository<T>` is the thin derived class you keep in your infrastructure project:

```csharp
using Ardalis.Specification.EntityFrameworkCore;
using MyApp.Infrastructure;

public sealed class EfRepository<T> : RepositoryBase<T>, IReadRepositoryBase<T>, IRepositoryBase<T>
    where T : class
{
    public EfRepository(AppDbContext db) : base(db) { }
}
```

Notes:
- `RepositoryBase<T>` lives in the `Ardalis.Specification.EntityFrameworkCore` package, not the core package documented here.
- Registering the same concrete type for both interfaces lets you inject the read-only view in query handlers without a second DbContext or duplicated registration.

---

## 7. Unit-testing a spec without a DbContext

`Specification<T>` ships an `Evaluate(IEnumerable<T>)` method (and `IsSatisfiedBy(T)`) that runs the spec's filtering, searching, ordering, and pagination directly against in-memory data — no `InMemorySpecificationEvaluator` needed at the call site.

```csharp
using FluentAssertions;
using MyApp.Domain;
using MyApp.Specs;
using Xunit;

public sealed class CustomersByCountryPagedSpecTests
{
    private static readonly List<Customer> Sample = new()
    {
        new() { Id = 1, Name = "Alice",   IsActive = true,  CountryId = 1, CreatedOn = new(2024, 1, 1) },
        new() { Id = 2, Name = "Bob",     IsActive = true,  CountryId = 1, CreatedOn = new(2024, 6, 1) },
        new() { Id = 3, Name = "Charlie", IsActive = false, CountryId = 1, CreatedOn = new(2024, 3, 1) },
        new() { Id = 4, Name = "Dave",    IsActive = true,  CountryId = 2, CreatedOn = new(2024, 2, 1) },
    };

    [Fact]
    public void FiltersByCountry_OrdersByName_AndPages()
    {
        var spec = new CustomersByCountryPagedSpec(countryId: 1, page: 1, pageSize: 10);

        var result = spec.Evaluate(Sample).ToList();

        result.Should().HaveCount(2);
        result.Select(c => c.Name).Should().ContainInOrder("Alice", "Bob");
    }

    [Fact]
    public void IsSatisfiedBy_ReturnsTrue_ForMatchingEntity()
    {
        var spec = new ActiveCustomersSpec();
        spec.IsSatisfiedBy(Sample[0]).Should().BeTrue();
        spec.IsSatisfiedBy(Sample[2]).Should().BeFalse();
    }
}
```

Notes:
- `Evaluate` honors `Where`, `Search`, `OrderBy`/`ThenBy`, `Skip`, `Take`, and `PostProcessingAction`. It does **not** honor `Include`/`ThenInclude` (includes are an ORM concern).
- For projected specs (`Specification<T, TResult>`), use `InMemorySpecificationEvaluator.Default.Evaluate(source, spec)` from the same namespace if you want to test the projection in isolation.

---

## 8. New in v8.x: `AsTracking()` and `DeleteRangeAsync(ISpecification<T>)`

Two notable additions in v8:

1. `AsTracking()` (and its conditional overload) on `ISpecificationBuilder<T>` — the explicit counterpart to `AsNoTracking()`. Useful when the underlying DbContext is configured with `QueryTrackingBehavior.NoTracking` globally but a specific query needs change tracking.
2. `IRepositoryBase<T>.DeleteRangeAsync(ISpecification<T>, …)` — delete every row that matches a spec in one call, without first loading and iterating.

```csharp
using Ardalis.Specification;
using MyApp.Domain;

namespace MyApp.Specs;

// (1) Force tracking on a spec used by an update use-case.
public sealed class TrackedCustomerByIdSpec : SingleResultSpecification<Customer>
{
    public TrackedCustomerByIdSpec(int id)
    {
        Query
            .Where(c => c.Id == id)
            .Include(c => c.Orders)
            .AsTracking();
    }
}

// (2) Spec describing rows to be bulk-deleted.
public sealed class StaleInactiveCustomersSpec : Specification<Customer>
{
    public StaleInactiveCustomersSpec(DateTime olderThan)
    {
        Query.Where(c => !c.IsActive && c.CreatedOn < olderThan);
    }
}
```

Calling site:

```csharp
public sealed class CustomerMaintenanceService
{
    private readonly IRepositoryBase<Customer> _customers;

    public CustomerMaintenanceService(IRepositoryBase<Customer> customers) => _customers = customers;

    public async Task RenameAsync(int id, string newName, CancellationToken ct = default)
    {
        ArgumentException.ThrowIfNullOrWhiteSpace(newName);

        var customer = await _customers.SingleOrDefaultAsync(new TrackedCustomerByIdSpec(id), ct)
            ?? throw new InvalidOperationException($"Customer {id} not found.");

        customer.Name = newName;
        await _customers.SaveChangesAsync(ct);
    }

    public Task PurgeStaleAsync(DateTime olderThan, CancellationToken ct = default)
        => _customers.DeleteRangeAsync(new StaleInactiveCustomersSpec(olderThan), ct);
}
```

Notes:
- `AsTracking()` wins over any earlier `AsNoTracking()` / `AsNoTrackingWithIdentityResolution()` on the same spec, and vice versa — the last call configures the spec.
- `DeleteRangeAsync(ISpecification<T>, …)` still flows through the change tracker in the EF Core implementation; it's a convenience over `ListAsync` + `DeleteRangeAsync(entities)`, not a raw `ExecuteDelete`. Call `SaveChangesAsync` is **not** required — the repository persists internally, matching the other `*Async` mutators.
