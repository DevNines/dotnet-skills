# Ardalis.Specification v9.x — patterns

## What the Specification pattern is for

A **Specification** encapsulates the query logic for a single read use-case: the `Where` predicates, ordering, `Include`s, paging, and the projection (`Select` / `SelectMany`) needed to answer one question about an aggregate. It moves that logic out of controllers, handlers, and service methods into a small, named, testable class that lives next to the domain model — so the same "active customers in region X, ordered by name" query isn't reinvented in three places with subtle drift.

It solves three concrete problems: (1) repository explosion (`GetActiveCustomersInRegionOrderedByName(...)` etc.), (2) ad-hoc `IQueryable` leaks across architectural boundaries, and (3) untestable LINQ buried inside infrastructure. The spec is a value object describing a query; an `ISpecificationEvaluator` translates it to EF, and `InMemorySpecificationEvaluator` evaluates it against an `IEnumerable<T>` for unit tests.

It does **not** belong on: single-row primary-key lookups (use `IReadRepositoryBase<T>.GetByIdAsync`), any mutation path (`AddAsync` / `UpdateAsync` / `DeleteAsync` take entities directly — the only spec-driven mutation is `DeleteRangeAsync(ISpecification<T>)`, used sparingly), cross-aggregate transactional workflows (those belong in a domain or application service that coordinates repositories), or anything that requires an open `IQueryable` to be composed downstream.

## Naming conventions

- **One spec per file.** Filename matches the class name.
- **Class name shape:** `<Entity><Filter><Modifier>Spec`, e.g. `CustomerByEmailSpec`, `OrdersPendingShipmentSpec`, `ProductsByCategoryPagedSpec`.
- Use the suffix **`Spec`**, not `Specification`. Shorter, reads better at call sites: `new CustomerByEmailSpec(email)`.
- Single-result specs implement `ISingleResultSpecification<T>` and are named in the singular: `CustomerByIdSpec`, not `CustomersByIdSpec`.
- Projecting specs are named after the result shape: `CustomerListItemSpec` for a `Specification<Customer, CustomerListItem>`.
- **Constructor parameters become the spec's parameters.** No setters, no `With…` fluent mutators on the spec itself. If a filter is conditional, pass the value (or a nullable) and use the `condition` overloads inside the constructor.

## Where each piece of code belongs

| Concern                                        | Inside the spec?                                                                 |
| ---------------------------------------------- | -------------------------------------------------------------------------------- |
| Filtering (`Where`)                            | ✅ Yes — via `Query.Where(...)`                                                  |
| Ordering (`OrderBy` / `ThenBy`)                | ✅ Yes — via `Query.OrderBy(...).ThenBy(...)`                                    |
| Includes / ThenIncludes                        | ✅ Yes — via `Query.Include(...).ThenInclude(...)`                               |
| Paging (`Skip` / `Take`)                       | ✅ Yes — via `Query.Skip(n).Take(n)`                                             |
| Projection (`Select` / `SelectMany`)           | ✅ Yes — on `Specification<T, TResult>` via `Query.Select(...)`                  |
| Search (`SQL LIKE`)                            | ✅ Yes — via `Query.Search(...)`                                                 |
| Tracking flags (`AsNoTracking`, `AsTracking`)  | ✅ Yes when query-specific; otherwise leave at DbContext default                 |
| Split queries (`AsSplitQuery`)                 | ✅ Yes when the spec has multiple collection-includes                            |
| Query tags (`TagWith`)                         | ✅ Yes — aids log correlation                                                    |
| Cache key (`EnableCache` / `WithCacheKey`)     | ✅ Yes — keep cache identity next to query identity                              |
| Validation of ctor inputs (null/empty guards)  | ✅ Yes — in the constructor, before `Query.…` calls                              |
| Authorization / "can this user see this?"      | ❌ No — enforce in the handler/policy layer; pass already-scoped values in       |
| Soft-delete / multitenant filters              | ❌ No — use EF Core global query filters                                         |
| DbContext config, connection strings, retries  | ❌ No — infrastructure concern                                                   |
| `DbContext` / `IServiceProvider` injection     | ❌ No — specs are pure value objects                                             |

## Canonical constructor shape

```csharp
public sealed class CustomersInRegionSpec : Specification<Customer>
{
    public CustomersInRegionSpec(string region, int page, int pageSize)
    {
        ArgumentException.ThrowIfNullOrWhiteSpace(region);
        ArgumentOutOfRangeException.ThrowIfNegative(page);
        ArgumentOutOfRangeException.ThrowIfLessThan(pageSize, 1);

        Query
            .Where(c => c.Region == region)                 // filter
            .Where(c => c.IsActive)
            .OrderBy(c => c.Name).ThenBy(c => c.Id)         // sort
            .Skip(page * pageSize).Take(pageSize)           // page
            .Include(c => c.Addresses)                      // include
            .AsNoTracking()
            .TagWith($"{nameof(CustomersInRegionSpec)}:{region}");
    }
}
```

Rules baked into this shape:

- **`sealed`** — specs are not an inheritance hierarchy. Compose by writing another spec.
- **Required args are positional** — the spec is meaningless without them.
- **No nullable "optional filter" parameters.** If a filter is conditional, model it explicitly with the boolean-condition overloads (`Query.Where(predicate, condition)`) or write a separate spec.
- **Chain order:** filter → sort → page → include → flags/tags. Mechanically the builder doesn't care, but reading top-to-bottom this is what most humans expect.
- **Projecting specs** subclass `Specification<TSource, TResult>` and call `Query.Select(...)` last:

```csharp
public sealed class CustomerListItemSpec : Specification<Customer, CustomerListItem>
{
    public CustomerListItemSpec()
    {
        Query.OrderBy(c => c.Name).AsNoTracking();
        Query.Select(c => new CustomerListItem(c.Id, c.Name, c.Email));
    }
}
```

A `Specification<T>` can be promoted to a projected one at the call site via `SpecificationExtensions.WithProjectionOf(...)` when the projection is reusable across many filters.

## Repository wiring

Use the library's own `IRepositoryBase<T>` and `IReadRepositoryBase<T>` directly. **Do not** wrap them in a homegrown `IGenericRepository<T>` — the library's interfaces already are the abstraction. Wrapping just hides `ListAsync(ISpec)`, `FirstOrDefaultAsync(ISpec)`, `SingleOrDefaultAsync(ISingleResultSpecification<T>)`, `AnyAsync`, `CountAsync`, and the projecting `ListAsync<TResult>` overloads behind a thinner, worse surface.

Register your EF-backed implementations (typically from `Ardalis.Specification.EntityFrameworkCore`) as open generics:

```csharp
services.AddScoped(typeof(IRepositoryBase<>), typeof(EfRepository<>));
services.AddScoped(typeof(IReadRepositoryBase<>), typeof(EfRepository<>));
```

Aggregate-specific repositories are only justified when you need methods that **can't** be expressed as a spec — e.g. raw SQL, bulk operations, or cross-aggregate writes. In that case, derive `ICustomerRepository : IRepositoryBase<Customer>` and add only those extra methods.

Handler usage:

```csharp
public async Task<List<CustomerListItem>> Handle(ListCustomersQuery q, CancellationToken ct)
{
    var spec = new CustomerListItemSpec();
    return await _readRepo.ListAsync(spec, ct);
}
```

## Testing specs against in-memory data

v9 ships `InMemorySpecificationEvaluator` with a `Default` singleton. Use it to assert spec behavior without spinning up a database:

```csharp
[Fact]
public void CustomersInRegionSpec_filters_orders_and_pages()
{
    var data = new[]
    {
        new Customer { Id = 1, Name = "Bea",  Region = "EU", IsActive = true  },
        new Customer { Id = 2, Name = "Ana",  Region = "EU", IsActive = true  },
        new Customer { Id = 3, Name = "Carl", Region = "US", IsActive = true  },
        new Customer { Id = 4, Name = "Dee",  Region = "EU", IsActive = false },
    };

    var spec = new CustomersInRegionSpec(region: "EU", page: 0, pageSize: 10);

    var result = InMemorySpecificationEvaluator.Default.Evaluate(data, spec).ToList();

    Assert.Collection(result,
        c => Assert.Equal("Ana", c.Name),
        c => Assert.Equal("Bea", c.Name));
}
```

For projecting specs, the same `Evaluate` works against `ISpecification<T, TResult>`. You can also call `spec.IsSatisfiedBy(entity)` for a single-entity predicate check or `spec.Evaluate(enumerable)` directly — `Specification<T>` carries its own evaluator.

Caveat: `InMemorySpecificationEvaluator` does **not** model EF behaviors such as `Include`, global query filters, or `AsSplitQuery`. Tests cover *predicate, ordering, paging, projection* — for navigation loading, write an integration test against a real (or SQLite-in-memory) `DbContext`.

## Things to avoid

- **Don't expose `IQueryable` from a spec or repository.** Specs describe a query declaratively; an `IQueryable` escape hatch lets callers re-add `Where`/`Include` and silently bypasses the pattern. Add a new spec instead.
- **Don't subclass `Specification<T>` to inject soft-delete or tenant filters.** That's what EF Core global query filters are for. Use `Query.IgnoreQueryFilters()` on the spec only when a use-case genuinely needs to read across them.
- **Don't inject `IServiceProvider`, `DbContext`, `IHttpContextAccessor`, or `ICurrentUser` into a spec.** Specs are constructed with plain data. If the query depends on the current user, resolve the user *in the handler* and pass `userId` / `tenantId` into the spec constructor.
- **Don't generate specs dynamically from arbitrary client input** (e.g. building `Expression` trees from a JSON DSL at runtime). You lose the named, reviewable, testable benefits and re-create the IQueryable-leak problem. Enumerate the supported sorts/filters as discrete specs or constructor parameters.
- **Don't put mutation logic in specs.** `Query.…` describes a read. The only spec-driven write is `IRepositoryBase<T>.DeleteRangeAsync(ISpecification<T>, ...)`, and even then prefer loading + domain-method + `UpdateAsync` when invariants matter.
- **Don't reuse a spec instance across requests.** They're cheap; construct per call. The `Query` builder mutates internal state.
- **Don't combine projection and `SingleOrDefault` without `ISingleResultSpecification<T, TResult>`.** The repo's single-result overloads are constrained to that marker for a reason — it documents intent at the type level.
