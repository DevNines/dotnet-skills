# Ardalis.Specification v8.x — patterns

## What the Specification pattern is for

The Specification pattern encapsulates a single read-side query — its filters,
ordering, includes, paging, and projection — as a named, testable, reusable
class. It moves query intent out of repository methods and controllers into a
small object that names what is being asked for (e.g. "active customers in
region X, paged, with their open orders"), so the same query is not
re-implemented inline in three places with subtle differences.

Specifications belong on **read paths** where the query has shape worth naming:
list endpoints, report queries, anything with filters/sorts/includes. They are
worth their weight when the query is reused, parameterized, or complex enough
to warrant a unit test.

Specifications do **not** belong: (a) on single-row primary-key lookups — use
`IReadRepositoryBase<T>.GetByIdAsync` directly; (b) on mutations — `AddAsync`,
`UpdateAsync`, `DeleteAsync` take entities, not specs (the one exception is
`DeleteRangeAsync(ISpecification<T>)` for bulk delete by criteria); (c) for
orchestrating cross-aggregate transactions — that is application/handler
concern, not query concern.

## Naming conventions

- **One file per spec.** `Specifications/CustomersByRegionSpec.cs`.
- **Class name shape:** `<Entity><Filter>Spec`. Examples:
  `CustomerByEmailSpec`, `OrdersPendingShipmentSpec`, `ProductSearchSpec`.
- Use the **`Spec` suffix**, not `Specification` — shorter, and the base type
  already says `Specification`.
- **Constructor parameters become spec parameters.** A spec is a value object
  describing one parameterized query; if it needs a `Guid customerId`, that is
  a ctor arg, not a settable property.
- **Single-result specs** implement `ISingleResultSpecification<T>` (or inherit
  `SingleResultSpecification<T>`) so they may be passed to `SingleOrDefaultAsync`.
- **Projection specs** derive from `Specification<T, TResult>` and are named
  after the result shape: `CustomerListItemSpec : Specification<Customer, CustomerListItemDto>`.

## Where does each piece of code belong?

| Concern                              | In the spec?                         | Notes                                                                 |
| ------------------------------------ | ------------------------------------ | --------------------------------------------------------------------- |
| Filtering (`Query.Where`)            | ✅ Yes                                | All predicate logic for this query.                                   |
| Ordering (`OrderBy`/`OrderByDescending`) | ✅ Yes                            | Default sort lives with the spec.                                     |
| Includes (`Include` / `.ThenInclude`)| ✅ Yes                                | Eager-load graph for this query.                                      |
| Paging (`Skip` / `Take`)             | ✅ Yes                                | Often via ctor args `(int skip, int take)`.                           |
| Projection (`Select` / `SelectMany`) | ✅ Yes — in `Specification<T, TResult>` | Keep DTO shaping out of handlers.                                  |
| `AsNoTracking` / `AsSplitQuery`      | ✅ Yes                                | Read-shape concern; set via builder extensions.                       |
| Cache tags (`EnableCache`)           | ✅ Yes                                | `EnableCache("CustomersByRegion", region)` after criteria.            |
| Authorization / tenant scoping       | ❌ No                                 | Use EF Core global query filters, or scope in the repository factory. |
| Validation of ctor inputs            | ✅ Yes — in the ctor itself           | Guard clauses (`ArgumentNullException`, range checks).                |
| `DbContext` / provider configuration | ❌ No                                 | Specs are persistence-agnostic. No `DbContext` access.                |
| Soft-delete / `IsDeleted` filter     | ❌ No                                 | EF Core query filter on the entity, not a base spec.                  |

## Canonical constructor shape

```csharp
public sealed class CustomersByRegionSpec : Specification<Customer>
{
    public CustomersByRegionSpec(string region, int skip, int take)
    {
        ArgumentException.ThrowIfNullOrWhiteSpace(region);
        if (skip < 0) throw new ArgumentOutOfRangeException(nameof(skip));
        if (take is <= 0 or > 200) throw new ArgumentOutOfRangeException(nameof(take));

        Query
            .Where(c => c.Region == region && c.IsActive)   // filter
            .OrderBy(c => c.Name)                           // sort
            .Skip(skip).Take(take)                          // page
            .Include(c => c.PrimaryContact)                 // include
            .AsNoTracking();
    }
}
```

Why this shape:

- **`sealed`** — specs are leaves, not extension points. Don't subclass them.
- **Positional required args, no optional nullable "filter" params.** If you
  find yourself adding `string? region = null`, make a separate spec or use
  the conditional overloads (`.Where(predicate, condition)`) with an
  explicitly-named ctor arg.
- **Chain order:** filter → sort → page → include → flags. This reads top to
  bottom the way the query executes logically and keeps diffs small.
- **Projection variant:** derive from `Specification<Customer, CustomerDto>`
  and end the chain with `.Select(c => new CustomerDto(...))`.

Single-result spec:

```csharp
public sealed class CustomerByEmailSpec : SingleResultSpecification<Customer>
{
    public CustomerByEmailSpec(string email)
    {
        ArgumentException.ThrowIfNullOrWhiteSpace(email);
        Query.Where(c => c.Email == email).Include(c => c.PrimaryContact);
    }
}
```

## Repository wiring

Use the library interfaces directly. **Do not wrap them in your own
`IGenericRepository<T>`** — it adds a layer that hides the spec API and tempts
people to add `IQueryable`-returning methods.

- Inject `IReadRepositoryBase<T>` on read paths (query handlers, list endpoints).
- Inject `IRepositoryBase<T>` on write paths (command handlers).

```csharp
// Program.cs
services.AddScoped(typeof(IRepositoryBase<>), typeof(EfRepository<>));
services.AddScoped(typeof(IReadRepositoryBase<>), typeof(EfRepository<>));
```

Per-aggregate interfaces (`ICustomerRepository : IRepositoryBase<Customer>`)
are fine when you want to attach aggregate-specific methods, but they should
still inherit the base interfaces, not replace them.

Calling a spec:

```csharp
var page  = await _read.ListAsync(new CustomersByRegionSpec(region, skip, take), ct);
var one   = await _read.SingleOrDefaultAsync(new CustomerByEmailSpec(email), ct);
var count = await _read.CountAsync(new CustomersByRegionSpec(region, 0, int.MaxValue), ct);
var dtos  = await _read.ListAsync(new CustomerListItemSpec(region), ct); // Specification<T,TResult>
```

## Testing specs against in-memory data

v8 does **not** ship a public `InMemorySpecificationEvaluator`. Use the
`Evaluate(IEnumerable<T>)` method that `Specification<T>` exposes — it applies
the spec's `Where`, ordering, and paging to an in-memory sequence. This is
exactly what it is documented for ("specially helpful when unit testing").

```csharp
[Fact]
public void CustomersByRegionSpec_filters_sorts_and_pages()
{
    var data = new[]
    {
        new Customer { Name = "Bea",   Region = "EU", IsActive = true  },
        new Customer { Name = "Ada",   Region = "EU", IsActive = true  },
        new Customer { Name = "Carol", Region = "US", IsActive = true  },
        new Customer { Name = "Dan",   Region = "EU", IsActive = false },
    };

    var spec = new CustomersByRegionSpec(region: "EU", skip: 0, take: 10);
    var result = spec.Evaluate(data).ToList();

    Assert.Equal(new[] { "Ada", "Bea" }, result.Select(c => c.Name));
}
```

For a single predicate, `spec.IsSatisfiedBy(entity)` answers "does this row
match the filter?" without materializing the full pipeline.

Note: `Evaluate` does **not** project (`Select`) or run includes — for
projection specs, test the selector lambda directly, or integration-test the
spec against an EF Core in-memory / SQLite provider through the real
repository.

## Things to avoid

- **`IQueryable`-returning methods on the spec or repository.** It defeats the
  point: callers compose ad-hoc query fragments in handlers again, untestable.
- **Subclassing `Specification<T>` to add cross-cutting filters** like
  soft-delete or tenant scoping. Use **EF Core global query filters** on the
  entity configuration; opt out per-spec with `Query.IgnoreQueryFilters()`
  when (rarely) needed.
- **Injecting `IServiceProvider`, `DbContext`, `IHttpContextAccessor`, or
  `ICurrentUser` into a spec.** Specs are pure value objects describing a
  query; if you need the current user's id, pass it as a ctor arg from the
  handler that already has it.
- **Dynamic spec generation at runtime** (building `Expression` trees from
  strings, reflection over property names from query strings). If you need
  dynamic search, model it as a small set of explicit ctor args plus
  conditional builder overloads (`.Where(p, condition)`, `.OrderBy(e, condition)`).
- **Mutating a spec after construction.** Treat them as immutable — build in
  the ctor, never expose setters.
- **One mega-spec with twelve nullable parameters.** Split into named specs
  per use case; duplicated `.Where` lines are cheaper than a spec nobody
  understands.
