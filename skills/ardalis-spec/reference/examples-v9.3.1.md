<!--
  examples-v9.md
  Major: v9
  Generated against: Ardalis.Specification 9.3.1
  DO NOT EDIT BY HAND — rerun scripts/update_skill.py to regenerate.
-->

# Ardalis.Specification

Canonical, copy-pasteable examples for **Ardalis.Specification v9** (9.3.1).
The package targets `netstandard2.0`; the examples here use modern C# (file-scoped
namespaces, target-typed `new`, records, `sealed` by default). Repository
interfaces (`IReadRepositoryBase<T>`, `IRepositoryBase<T>`) are typically
backed by `Ardalis.Specification.EntityFrameworkCore`.

---

## 1. Simple single-criterion filter spec

```csharp
using Ardalis.Specification;

namespace Sales.Specs;

public sealed class CustomersByCountrySpec : Specification<Customer>
{
    public CustomersByCountrySpec(string country)
    {
        ArgumentException.ThrowIfNullOrWhiteSpace(country);

        Query
            .Where(c => c.Country == country)
            .OrderBy(c => c.LastName);
    }
}
```

Notes:
- Constructors are `public` since v9 — you can compose them directly from
  application code, but keeping a parameter object/validation in the constructor
  is still recommended.
- `Where` is appended via `SpecificationBuilderExtensions.Where`; calling it
  twice ANDs the predicates.

---

## 2. Spec with `Include` / `ThenInclude`

```csharp
using Ardalis.Specification;

namespace Sales.Specs;

public sealed class OrderWithLinesAndProductSpec : Specification<Order>, ISingleResultSpecification<Order>
{
    public OrderWithLinesAndProductSpec(int orderId)
    {
        Query
            .Where(o => o.Id == orderId)
            .Include(o => o.Customer)
            .Include(o => o.Lines)
                .ThenInclude(line => line.Product)
            .AsSplitQuery();
    }
}
```

Notes:
- Implementing `ISingleResultSpecification<T>` makes the spec compatible with
  `IReadRepositoryBase<T>.SingleOrDefaultAsync`.
- `AsSplitQuery()` is recommended whenever you `Include` more than one
  collection navigation to avoid Cartesian explosion.

---

## 3. Paged + sorted list spec with constructor validation

```csharp
using Ardalis.Specification;

namespace Sales.Specs;

public sealed class CustomersPagedSpec : Specification<Customer>
{
    public CustomersPagedSpec(int pageNumber, int pageSize, string? search)
    {
        if (pageNumber < 1) throw new ArgumentOutOfRangeException(nameof(pageNumber));
        if (pageSize is < 1 or > 200) throw new ArgumentOutOfRangeException(nameof(pageSize));

        Query
            .Where(c => c.IsActive)
            .Search(c => c.LastName, $"%{search}%", condition: !string.IsNullOrWhiteSpace(search))
            .OrderBy(c => c.LastName)
                .ThenBy(c => c.FirstName)
            .Skip((pageNumber - 1) * pageSize)
            .Take(pageSize)
            .AsNoTracking();
    }
}
```

Notes:
- The conditional overload of `Search` lets you skip the LIKE filter entirely
  when no search term is supplied — no need for an `if` block.
- `AsNoTracking` is appropriate for read-only list endpoints; in v9 it also
  disables `AsTracking` / `AsNoTrackingWithIdentityResolution` flags if they
  were set earlier in the chain.

---

## 4. Projected spec (`Specification<T, TResult>`)

```csharp
using Ardalis.Specification;

namespace Sales.Specs;

public sealed record CustomerListItem(int Id, string FullName, string Country);

public sealed class CustomerListItemsSpec : Specification<Customer, CustomerListItem>
{
    public CustomerListItemsSpec(string country)
    {
        ArgumentException.ThrowIfNullOrWhiteSpace(country);

        Query
            .Where(c => c.Country == country)
            .OrderBy(c => c.LastName);

        Query.Select(c => new CustomerListItem(
            c.Id,
            c.FirstName + " " + c.LastName,
            c.Country));
    }
}
```

Notes:
- In v9, `Select` returns `void` — it must be the last call (or live on its own
  `Query.Select(...)` statement). Chaining further builder calls onto `Select`
  is no longer possible.
- Use `SelectMany` instead of `Select` if you are flattening a collection
  navigation. Defining both throws `ConcurrentSelectorsException` at evaluation.

---

## 5. Read-only repository injection in a service

```csharp
using Ardalis.Specification;

namespace Sales.Application;

public sealed class CustomerQueryService
{
    private readonly IReadRepositoryBase<Customer> _customers;

    public CustomerQueryService(IReadRepositoryBase<Customer> customers)
    {
        _customers = customers ?? throw new ArgumentNullException(nameof(customers));
    }

    public Task<List<CustomerListItem>> GetByCountryAsync(string country, CancellationToken ct)
    {
        var spec = new CustomerListItemsSpec(country);
        return _customers.ListAsync(spec, ct);
    }

    public Task<Customer?> GetWithOrdersAsync(int id, CancellationToken ct)
    {
        var spec = new OrderWithLinesAndProductSpec(id);
        // SingleOrDefaultAsync requires ISingleResultSpecification<T>.
        return _customers.FirstOrDefaultAsync(new CustomersByIdSpec(id), ct);
    }
}

internal sealed class CustomersByIdSpec : Specification<Customer>, ISingleResultSpecification<Customer>
{
    public CustomersByIdSpec(int id) => Query.Where(c => c.Id == id);
}
```

Notes:
- Prefer `IReadRepositoryBase<T>` over `IRepositoryBase<T>` in query services —
  it advertises read-only intent and excludes `AddAsync` / `UpdateAsync` etc.
- `CancellationToken` is the trailing parameter on every async repository
  method; propagate it.

---

## 6. DI registration in the composition root

The concrete repository lives in `Ardalis.Specification.EntityFrameworkCore`
(`RepositoryBase<T>`). Register the open generics once and let DI resolve them
per `DbContext`-typed entity.

```csharp
using Ardalis.Specification;
using Ardalis.Specification.EntityFrameworkCore;
using Microsoft.EntityFrameworkCore;
using Microsoft.Extensions.DependencyInjection;

var builder = WebApplication.CreateBuilder(args);

builder.Services.AddDbContext<SalesDbContext>(opt =>
    opt.UseSqlServer(builder.Configuration.GetConnectionString("Sales")));

// Open-generic repositories — work for any entity in SalesDbContext.
builder.Services.AddScoped(typeof(IRepositoryBase<>), typeof(EfRepository<>));
builder.Services.AddScoped(typeof(IReadRepositoryBase<>), typeof(EfRepository<>));

builder.Services.AddScoped<CustomerQueryService>();

var app = builder.Build();
app.Run();

// Thin concrete repository bound to the app's DbContext.
internal sealed class EfRepository<T> : RepositoryBase<T> where T : class
{
    public EfRepository(SalesDbContext db) : base(db) { }
}
```

Notes:
- `RepositoryBase<T>` and `EfRepository<T>` come from
  `Ardalis.Specification.EntityFrameworkCore`, not the core package. Add that
  NuGet to your composition-root project.
- Scope must match your `DbContext` scope (typically `Scoped` in ASP.NET Core).

---

## 7. Unit-testing a spec without a `DbContext`

`InMemorySpecificationEvaluator.Default` evaluates a spec against an in-memory
sequence using the exact same `Where` / `Search` / `Order` / `Skip` / `Take` /
`Select` semantics it would apply to `IQueryable`. No database required.

```csharp
using Ardalis.Specification;
using FluentAssertions;
using Xunit;

namespace Sales.Tests;

public sealed class CustomersPagedSpecTests
{
    private static readonly Customer[] Seed =
    [
        new() { Id = 1, FirstName = "Ada",   LastName = "Lovelace", Country = "UK", IsActive = true  },
        new() { Id = 2, FirstName = "Alan",  LastName = "Turing",   Country = "UK", IsActive = true  },
        new() { Id = 3, FirstName = "Grace", LastName = "Hopper",   Country = "US", IsActive = true  },
        new() { Id = 4, FirstName = "Edsger",LastName = "Dijkstra", Country = "NL", IsActive = false },
    ];

    [Fact]
    public void Filters_orders_and_pages()
    {
        var spec = new CustomersPagedSpec(pageNumber: 1, pageSize: 2, search: null);

        var result = InMemorySpecificationEvaluator.Default
            .Evaluate(Seed, spec)
            .ToList();

        result.Should().HaveCount(2);
        result[0].LastName.Should().Be("Hopper");   // active, alphabetical
        result[1].LastName.Should().Be("Lovelace");
    }

    [Fact]
    public void IsSatisfiedBy_short_circuits_predicates()
    {
        var spec = new CustomersByCountrySpec("UK");

        spec.IsSatisfiedBy(Seed[0]).Should().BeTrue();   // UK
        spec.IsSatisfiedBy(Seed[2]).Should().BeFalse();  // US
    }
}
```

Notes:
- Use `InMemorySpecificationEvaluator.Default` for the singleton; instantiate
  `new InMemorySpecificationEvaluator(customEvaluators)` only when you have a
  custom `IInMemoryEvaluator`.
- `IsSatisfiedBy` evaluates only `WhereExpressions` and `SearchCriterias` — it
  is a fast way to validate a single entity without materializing a sequence.

---

## 8. New in v9.x: `WithProjectionOf` — compose a filter spec with a projection spec

v9.1 introduced `WithProjectionOf` (refined in v9.3 to live on
`SpecificationExtensions` and target `Specification<T>` directly). It lets you
keep filtering specs and projection specs as independent, reusable units and
merge them on the call site.

```csharp
using Ardalis.Specification;

namespace Sales.Specs;

// Projection-only spec: defines just the Select shape.
public sealed class CustomerListItemProjection : Specification<Customer, CustomerListItem>
{
    public CustomerListItemProjection()
    {
        Query.Select(c => new CustomerListItem(
            c.Id,
            c.FirstName + " " + c.LastName,
            c.Country));
    }
}

// Plain filter spec — knows nothing about the DTO.
public sealed class ActiveCustomersInCountrySpec : Specification<Customer>
{
    public ActiveCustomersInCountrySpec(string country)
    {
        ArgumentException.ThrowIfNullOrWhiteSpace(country);

        Query
            .Where(c => c.IsActive && c.Country == country)
            .OrderBy(c => c.LastName);
    }
}

// Usage: compose at the call site.
public sealed class CustomerListService
{
    private readonly IReadRepositoryBase<Customer> _customers;

    public CustomerListService(IReadRepositoryBase<Customer> customers) => _customers = customers;

    public Task<List<CustomerListItem>> ListAsync(string country, CancellationToken ct)
    {
        var filter     = new ActiveCustomersInCountrySpec(country);
        var projection = new CustomerListItemProjection();

        Specification<Customer, CustomerListItem> combined = filter.WithProjectionOf(projection);

        return _customers.ListAsync(combined, ct);
    }
}
```

Notes:
- `WithProjectionOf` clones the source spec and applies the projection's
  `Select` / `SelectMany`; both input specs are left unchanged, so they remain
  safely reusable.
- The result is a `Specification<T, TResult>` you can pass to `ListAsync`,
  `FirstOrDefaultAsync<TResult>`, etc.
- Pair with `ISingleResultSpecification<T, TResult>`-shaped wrappers if you
  need single-result semantics.
