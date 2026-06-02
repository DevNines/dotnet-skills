# Ardalis.Specification v9.3.1 — API surface

_Generated from the XML doc comments shipped in `Ardalis.Specification.9.3.1.nupkg` (target framework `netstandard2.0`). Do not edit by hand — rerun `scripts/update_skill.py`._

Use **only** the members listed here when writing code against Ardalis.Specification v9.x. If a member you want isn't here, it doesn't exist in this major and you must pick another approach.

## namespace `Ardalis.Specification`

### `ConcurrentSelectorsException`

Exception thrown when concurrent selector transforms are defined in a specification.

**Methods:**

- `#ctor`
  - Initializes a new instance of the `ConcurrentSelectorsException` class.
- `#ctor(Exception)`
  - Initializes a new instance of the `ConcurrentSelectorsException` class with a specified inner exception.
  - `innerException`: The exception that is the cause of the current exception.


### `ICacheSpecificationBuilder<T>`

Represents a specification builder that supports caching operations.


### `ICacheSpecificationBuilder<T1, T2>`

Represents a specification builder that supports caching operations.


### `IEvaluator`

Represents an evaluator that processes a specification.

**Methods:**

- `GetQuery<T>(IQueryable<T1>, ISpecification<T1>)`
  - Evaluates the given specification on the provided queryable source.
  - `query`: The queryable source.
  - `specification`: The specification to evaluate.
  - `<T>`: The type of the entity.
  - returns: The evaluated queryable source.

**Properties:**

- `IsCriteriaEvaluator`
  - Whether the evaluator should be omitted for pagination purposes.


### `IInMemoryEvaluator`

Represents an in-memory evaluator that processes a specification.

**Methods:**

- `Evaluate<T>(Generic.IEnumerable<T1>, ISpecification<T1>)`
  - Evaluates the given specification on the provided enumerable source.
  - `query`: The enumerable source.
  - `specification`: The specification to evaluate.
  - `<T>`: The type of the entity.
  - returns: The evaluated enumerable source.


### `IInMemorySpecificationEvaluator`

Evaluates specifications in memory.

**Methods:**

- `Evaluate<T1, T2>(Generic.IEnumerable<T1>, ISpecification<T1,T2>)`
  - Evaluates the given specification on the provided enumerable source and returns the result.
  - `source`: The enumerable source.
  - `specification`: The specification to evaluate.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - returns: The evaluated enumerable result.
- `Evaluate<T>(Generic.IEnumerable<T1>, ISpecification<T1>)`
  - Evaluates the given specification on the provided enumerable source and returns the result.
  - `source`: The enumerable source.
  - `specification`: The specification to evaluate.
  - `<T>`: The type of the entity.
  - returns: The evaluated enumerable result.


### `IIncludableSpecificationBuilder<T1, T2>`

Represents a specification builder that supports include operations.


### `IIncludableSpecificationBuilder<T1, T2, T3>`

Represents a specification builder that supports include operations.


### `IOrderedSpecificationBuilder<T>`

Represents a specification builder that supports order operations.


### `IOrderedSpecificationBuilder<T1, T2>`

Represents a specification builder that supports order operations.


### `IReadRepositoryBase<T>`

A `IRepositoryBase<T>` can be used to query instances of T.
An `ISpecification<T>` (or derived) is used to encapsulate the LINQ queries against the database.

**Methods:**

- `AnyAsync(CancellationToken)`
  - Returns a boolean whether any entity exists or not.
  - `cancellationToken`: The cancellation token.
  - returns: A task that represents the asynchronous operation. The task result contains true if the
source sequence contains any elements; otherwise, false.
- `AnyAsync(ISpecification<T1>, CancellationToken)`
  - Returns a boolean that represents whether any entity satisfy the encapsulated query logic
of the specification or not.
  - `specification`: The encapsulated query logic.
  - `cancellationToken`: The cancellation token.
  - returns: A task that represents the asynchronous operation. The task result contains true if the
source sequence contains any elements; otherwise, false.
- `CountAsync(CancellationToken)`
  - Returns the total number of records.
  - `cancellationToken`: The cancellation token.
  - returns: A task that represents the asynchronous operation. The task result contains the
number of elements in the input sequence.
- `CountAsync(ISpecification<T1>, CancellationToken)`
  - Returns a number that represents how many entities satisfy the encapsulated query logic
of the specification.
  - `specification`: The encapsulated query logic.
  - `cancellationToken`: The cancellation token.
  - returns: A task that represents the asynchronous operation. The task result contains the
number of elements in the input sequence.
- `FirstOrDefaultAsync(ISpecification<T1>, CancellationToken)`
  - Returns the first element of a sequence, or a default value if the sequence contains no elements.
  - `specification`: The encapsulated query logic.
  - `cancellationToken`: The cancellation token.
  - returns: A task that represents the asynchronous operation.
The task result contains the T, or .
- `FirstOrDefaultAsync<T>(ISpecification<T1,T1>, CancellationToken)`
  - Returns the first element of a sequence, or a default value if the sequence contains no elements.
  - `specification`: The encapsulated query logic.
  - `cancellationToken`: The cancellation token.
  - returns: A task that represents the asynchronous operation.
The task result contains the TResult, or .
- `GetByIdAsync<T>(T1, CancellationToken)`
  - Finds an entity with the given primary key value.
  - `id`: The value of the primary key for the entity to be found.
  - `cancellationToken`: The cancellation token.
  - `<TId>`: The type of primary key.
  - returns: A task that represents the asynchronous operation.
The task result contains the T, or .
- `ListAsync(CancellationToken)`
  - Finds all entities of T from the database.
  - `cancellationToken`: The cancellation token.
  - returns: A task that represents the asynchronous operation.
The task result contains a `List<T>` that contains elements from the input sequence.
- `ListAsync(ISpecification<T1>, CancellationToken)`
  - Finds all entities of T, that matches the encapsulated query logic of the
specification, from the database.
  - `specification`: The encapsulated query logic.
  - `cancellationToken`: The cancellation token.
  - returns: A task that represents the asynchronous operation.
The task result contains a `List<T>` that contains elements from the input sequence.
- `ListAsync<T>(ISpecification<T1,T1>, CancellationToken)`
  - Finds all entities of T, that matches the encapsulated query logic of the
specification, from the database.


Projects each entity into a new form, being TResult.
  - `specification`: The encapsulated query logic.
  - `cancellationToken`: The cancellation token.
  - `<TResult>`: The type of the value returned by the projection.
  - returns: A task that represents the asynchronous operation.
The task result contains a `List<T>` that contains elements from the input sequence.
- `SingleOrDefaultAsync(ISingleResultSpecification<T1>, CancellationToken)`
  - Returns the only element of a sequence, or a default value if the sequence is empty; this method throws an exception if there is more than one element in the sequence.
  - `specification`: The encapsulated query logic.
  - `cancellationToken`: The cancellation token.
  - returns: A task that represents the asynchronous operation.
The task result contains the T, or .
- `SingleOrDefaultAsync<T>(ISingleResultSpecification<T1,T1>, CancellationToken)`
  - Returns the only element of a sequence, or a default value if the sequence is empty; this method throws an exception if there is more than one element in the sequence.
  - `specification`: The encapsulated query logic.
  - `cancellationToken`: The cancellation token.
  - returns: A task that represents the asynchronous operation.
The task result contains the TResult, or .


### `IRepositoryBase<T>`

A `IRepositoryBase<T>` can be used to query and save instances of T.
An `ISpecification<T>` (or derived) is used to encapsulate the LINQ queries against the database.

**Methods:**

- `AddAsync(T1, CancellationToken)`
  - Adds an entity in the database.
  - `entity`: The entity to add.
  - `cancellationToken`: The cancellation token.
  - returns: A task that represents the asynchronous operation.
The task result contains the T.
- `AddRangeAsync(Generic.IEnumerable<T1>, CancellationToken)`
  - Adds the given entities in the database
  - `entities`
  - `cancellationToken`: The cancellation token.
  - returns: A task that represents the asynchronous operation.
- `DeleteAsync(T1, CancellationToken)`
  - Removes an entity in the database
  - `entity`: The entity to delete.
  - `cancellationToken`: The cancellation token.
  - returns: A task that represents the asynchronous operation. The task result contains the number of state entries written to the database.
- `DeleteRangeAsync(Generic.IEnumerable<T1>, CancellationToken)`
  - Removes the given entities in the database
  - `entities`: The entities to remove.
  - `cancellationToken`: The cancellation token.
  - returns: A task that represents the asynchronous operation. The task result contains the number of state entries written to the database.
- `DeleteRangeAsync(ISpecification<T1>, CancellationToken)`
  - Removes the all entities of T, that matches the encapsulated query logic of the
specification, from the database.
  - `specification`: The encapsulated query logic.
  - `cancellationToken`: The cancellation token.
  - returns: A task that represents the asynchronous operation. The task result contains the number of state entries written to the database.
- `SaveChangesAsync(CancellationToken)`
  - Persists changes to the database.
  - returns: A task that represents the asynchronous operation.
- `UpdateAsync(T1, CancellationToken)`
  - Updates an entity in the database
  - `entity`: The entity to update.
  - `cancellationToken`: The cancellation token.
  - returns: A task that represents the asynchronous operation. The task result contains the number of state entries written to the database.
- `UpdateRangeAsync(Generic.IEnumerable<T1>, CancellationToken)`
  - Updates the given entities in the database
  - `entities`: The entities to update.
  - `cancellationToken`: The cancellation token.
  - returns: A task that represents the asynchronous operation. The task result contains the number of state entries written to the database.


### `ISingleResultSpecification`

A marker interface for specifications that are meant to return a single entity. Used to constrain methods
that accept a Specification and return a single result rather than a collection of results.


### `ISingleResultSpecification<T>`

Encapsulates query logic for T. It is meant to return a single result.


### `ISingleResultSpecification<T1, T2>`

Encapsulates query logic for T,
and projects the result into TResult. It is meant to return a single result.


### `ISpecificationBuilder<T>`

Represents a specification builder.

**Properties:**

- `Specification`
  - Gets the specification associated with this builder.


### `ISpecificationBuilder<T1, T2>`

Represents a specification builder.

**Properties:**

- `Specification`
  - Gets the specification associated with this builder.


### `ISpecificationEvaluator`

Evaluates the logic encapsulated by an `ISpecification<T>`.

**Methods:**

- `GetQuery<T1, T2>(IQueryable<T1>, ISpecification<T1,T2>)`
  - Applies the logic encapsulated by specification to given inputQuery,
and projects the result into TResult.
  - `inputQuery`: The sequence of T
  - `specification`: The encapsulated query logic.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - returns: A filtered sequence of TResult
- `GetQuery<T>(IQueryable<T1>, ISpecification<T1>, bool)`
  - Applies the logic encapsulated by specification to given inputQuery.
  - `inputQuery`: The sequence of T
  - `specification`: The encapsulated query logic.
  - `evaluateCriteriaOnly`: It ignores pagination and evaluators that don't affect Count.
  - `<T>`: The type of the entity.
  - returns: A filtered sequence of T


### `ISpecification<T>`

Represents a specification for querying entities of type T.

**Methods:**

- `Evaluate(Generic.IEnumerable<T1>)`
  - Applies the specification to the given entities and returns the filtered results.
  - `entities`: The entities to evaluate.
  - returns: The filtered results after applying the specification.
- `IsSatisfiedBy(T1)`
  - Determines whether the given entity satisfies the specification.
  - `entity`: The entity to validate.
  - returns: `true` if the entity satisfies the specification; otherwise, `false`.

**Properties:**

- `AsNoTracking`
  - Returns whether or not the change tracker will track any of the entities
that are returned. When true, if the entity instances are modified, this will not be detected
by the change tracker.
- `AsNoTrackingWithIdentityResolution`
  - Returns whether or not the query will then keep track of returned instances
(without tracking them in the normal way)
and ensure no duplicates are created in the query results
  - remarks: for more info: https://docs.microsoft.com/en-us/ef/core/change-tracking/identity-resolution#identity-resolution-and-queries
- `AsSplitQuery`
  - Returns whether or not the generated sql query should be split into multiple SQL queries
  - remarks: This feature was introduced in EF Core 5.0. It only works when using Include
for more info: https://docs.microsoft.com/en-us/ef/core/querying/single-split-queries
- `AsTracking`
  - Returns whether or not the change tracker will track any of the entities
that are returned.
- `CacheEnabled`
  - Return whether or not the results should be cached.
- `CacheKey`
  - The identifier to use to store and retrieve results from the cache.
- `IgnoreAutoIncludes`
  - Returns whether or not the query should ignore the defined AutoInclude configurations.
- `IgnoreQueryFilters`
  - Returns whether or not the query should ignore the defined global query filters
  - remarks: for more info: https://docs.microsoft.com/en-us/ef/core/querying/filters
- `IncludeExpressions`
  - The collection of `IncludeExpressionInfo`s describing each include expression.
This information is utilized to build Include/ThenInclude functions in the query.
- `IncludeStrings`
  - The collection of navigation properties, as strings, to include in the query.
- `Items`
  - Arbitrary state to be accessed from builders and evaluators.
- `OrderExpressions`
  - The collections of functions used to determine the sorting (and subsequent sorting),
to apply to the result of the query encapsulated by the `ISpecification<T>`.
- `PostProcessingAction`
  - The transform function to apply to the result of the query encapsulated by the `ISpecification<T>`.
- `Query`
  - Gets the specification builder.
- `QueryTags`
  - Query tags to help correlate specification with generated SQL queries captured in logs.
- `SearchCriterias`
  - The collection of 'SQL LIKE' operations.
- `Skip`
  - The number of elements to skip before returning the remaining elements.
- `Take`
  - The number of elements to return.
- `WhereExpressions`
  - The collection of filters.


### `ISpecification<T1, T2>`

Represents a specification with a selector for projecting entities of type T to TResult.

**Methods:**

- `Evaluate(Generic.IEnumerable<T1>)`
  - Applies the specification to the given entities and returns the filtered results.
  - `entities`: The entities to evaluate.
  - returns: The filtered results after applying the specification.

**Properties:**

- `PostProcessingAction`
  - The transform function to apply to the result of the query encapsulated by the `ISpecification<T1, T2>`.
- `Query`
  - Gets the specification builder.
- `Selector`
  - The Select transform function to apply to the T element.
- `SelectorMany`
  - The SelectMany transform function to apply to the T element.


### `InMemorySpecificationEvaluator`

**Methods:**

- `#ctor`
  - Initializes a new instance of the `InMemorySpecificationEvaluator` class.
  - remarks: This constructor sets up the evaluator with a predefined set of in-memory evaluators.
- `#ctor(Generic.IEnumerable<IInMemoryEvaluator>)`
  - Initializes a new instance of the `InMemorySpecificationEvaluator` class with the specified
collection of in-memory evaluators.
  - `evaluators`: A collection of `IInMemoryEvaluator` instances used to evaluate specifications.
- `Evaluate<T1, T2>(Generic.IEnumerable<T1>, ISpecification<T1,T2>)`
- `Evaluate<T>(Generic.IEnumerable<T1>, ISpecification<T1>)`

**Properties:**

- `Default`
  - Gets the default singleton instance of the `InMemorySpecificationEvaluator` class.
  - remarks: This instance is a singleton and is intended for scenarios where a shared, default
configuration is sufficient. If customization is required, a new instance of `InMemorySpecificationEvaluator` can be created.
- `Evaluators`
  - List of partial evaluators that will be used to evaluate specifications in memory.


### `IncludeExpressionInfo`

Encapsulates data needed to build Include/ThenInclude query.

**Properties:**

- `LambdaExpression`
  - If `Type` is `Include`, represents a related entity that should be included.


If `Type` is `ThenInclude`, represents a related entity that should be included as part of the previously included entity.
- `PreviousPropertyType`
  - The type of the previously included entity.
- `Type`
  - The include type.


### `OneOrMany<T>`

**Properties:**

- `List`
  - Gets the list value stored in the instance.
- `Single`
  - Gets the single value stored in the instance.
- `SingleOrDefault`
  - Gets the single value stored in the instance.
If the value is Empty or Many, returns null.


### `OrderEvaluator`

Represents an evaluator for order expressions.

**Methods:**

- `Evaluate<T>(Generic.IEnumerable<T1>, ISpecification<T1>)`
- `GetQuery<T>(IQueryable<T1>, ISpecification<T1>)`

**Properties:**

- `Instance`
  - Gets the singleton instance of the `OrderEvaluator` class.
- `IsCriteriaEvaluator`


### `OrderExpressionInfo<T>`

Encapsulates data needed to perform sorting.

**Methods:**

- `#ctor(Expressions.Expression<Func<T1,object>>, OrderTypeEnum)`
  - Creates instance of `OrderExpressionInfo<T>`.
  - `keySelector`: A function to extract a key from an element.
  - `orderType`: Whether to (subsequently) sort ascending or descending.

**Properties:**

- `KeySelector`
  - A function to extract a key from an element.
- `KeySelectorFunc`
  - Compiled `KeySelector`.
- `OrderType`
  - Whether to (subsequently) sort ascending or descending.


### `OrderTypeEnum`

Whether to (subsequently) sort ascending or descending.


### `PaginationEvaluator`

Represents an evaluator for take and skip expressions.

**Methods:**

- `Evaluate<T>(Generic.IEnumerable<T1>, ISpecification<T1>)`
- `GetQuery<T>(IQueryable<T1>, ISpecification<T1>)`

**Properties:**

- `Instance`
  - Gets the singleton instance of the `PaginationEvaluator` class.
- `IsCriteriaEvaluator`


### `SearchExpressionInfo<T>`

Encapsulates data needed to perform 'SQL LIKE' operation.

**Methods:**

- `#ctor(Expressions.Expression<Func<T1,string>>, string, int)`
  - Creates instance of `SearchExpressionInfo<T>`.
  - `selector`: The property to apply the SQL LIKE against.
  - `searchTerm`: The value to use for the SQL LIKE.
  - `searchGroup`: The index used to group sets of Selectors and SearchTerms together.

**Properties:**

- `SearchGroup`
  - The index used to group sets of Selectors and SearchTerms together.
- `SearchTerm`
  - The value to use for the SQL LIKE.
- `Selector`
  - The property to apply the SQL LIKE against.
- `SelectorFunc`
  - Compiled `Selector`.


### `SearchMemoryEvaluator`

Represents an in-memory evaluator for search expressions.

**Methods:**

- `Evaluate<T>(Generic.IEnumerable<T1>, ISpecification<T1>)`

**Properties:**

- `Instance`
  - Gets the singleton instance of the `SearchMemoryEvaluator` class.


### `SingleResultSpecification<T>`


### `SingleResultSpecification<T1, T2>`


### `SpecificationBuilderExtensions`

Extension methods for building specifications.

**Methods:**

- `AsNoTracking<T1, T2>(ISpecificationBuilder<T1,T2>)`
  - Configures the specification to apply NoTracking behavior.
It will also disable AsNoTrackingWithIdentityResolution and AsTracking flags.
  - `builder`: The specification builder.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - returns: The updated specification builder.
- `AsNoTracking<T1, T2>(ISpecificationBuilder<T1,T2>, bool)`
  - Configures the specification to apply NoTracking behavior if the condition is true.
It will also disable AsNoTrackingWithIdentityResolution and AsTracking flags.
  - `builder`: The specification builder.
  - `condition`: The condition to evaluate.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - returns: The updated specification builder.
- `AsNoTracking<T>(ISpecificationBuilder<T1>)`
  - Configures the specification to apply NoTracking behavior.
It will also disable AsNoTrackingWithIdentityResolution and AsTracking flags.
  - `builder`: The specification builder.
  - `<T>`: The type of the entity.
  - returns: The updated specification builder.
- `AsNoTracking<T>(ISpecificationBuilder<T1>, bool)`
  - Configures the specification to apply NoTracking behavior if the condition is true.
It will also disable AsNoTrackingWithIdentityResolution and AsTracking flags.
  - `builder`: The specification builder.
  - `condition`: The condition to evaluate.
  - `<T>`: The type of the entity.
  - returns: The updated specification builder.
- `AsNoTrackingWithIdentityResolution<T1, T2>(ISpecificationBuilder<T1,T2>)`
  - Configures the specification to apply AsNoTrackingWithIdentityResolution behavior.
It will also disable AsNoTracking and AsTracking flags.
  - `builder`: The specification builder.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - returns: The updated specification builder.
- `AsNoTrackingWithIdentityResolution<T1, T2>(ISpecificationBuilder<T1,T2>, bool)`
  - Configures the specification to apply AsNoTrackingWithIdentityResolution behavior if the condition is true.
It will also disable AsNoTracking and AsTracking flags.
  - `builder`: The specification builder.
  - `condition`: The condition to evaluate.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - returns: The updated specification builder.
- `AsNoTrackingWithIdentityResolution<T>(ISpecificationBuilder<T1>)`
  - Configures the specification to apply AsNoTrackingWithIdentityResolution behavior.
It will also disable AsNoTracking and AsTracking flags.
  - `builder`: The specification builder.
  - `<T>`: The type of the entity.
  - returns: The updated specification builder.
- `AsNoTrackingWithIdentityResolution<T>(ISpecificationBuilder<T1>, bool)`
  - Configures the specification to apply AsNoTrackingWithIdentityResolution behavior if the condition is true.
It will also disable AsNoTracking and AsTracking flags.
  - `builder`: The specification builder.
  - `condition`: The condition to evaluate.
  - `<T>`: The type of the entity.
  - returns: The updated specification builder.
- `AsSplitQuery<T1, T2>(ISpecificationBuilder<T1,T2>)`
  - Configures the specification to use split queries.
  - `builder`: The specification builder.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - returns: The updated specification builder.
- `AsSplitQuery<T1, T2>(ISpecificationBuilder<T1,T2>, bool)`
  - Configures the specification to use split queries if the condition is true.
  - `builder`: The specification builder.
  - `condition`: The condition to evaluate.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - returns: The updated specification builder.
- `AsSplitQuery<T>(ISpecificationBuilder<T1>)`
  - Configures the specification to use split queries.
  - `builder`: The specification builder.
  - `<T>`: The type of the entity.
  - returns: The updated specification builder.
- `AsSplitQuery<T>(ISpecificationBuilder<T1>, bool)`
  - Configures the specification to use split queries if the condition is true.
  - `builder`: The specification builder.
  - `condition`: The condition to evaluate.
  - `<T>`: The type of the entity.
  - returns: The updated specification builder.
- `AsTracking<T1, T2>(ISpecificationBuilder<T1,T2>)`
  - Configures the specification to apply AsTracking behavior.
It will also disable AsNoTrackingWithIdentityResolution and AsNoTracking flags.
  - `builder`: The specification builder.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - returns: The updated specification builder.
- `AsTracking<T1, T2>(ISpecificationBuilder<T1,T2>, bool)`
  - Configures the specification to apply AsTracking behavior if the condition is true.
It will also disable AsNoTrackingWithIdentityResolution and AsNoTracking flags.
  - `builder`: The specification builder.
  - `condition`: The condition to evaluate.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - returns: The updated specification builder.
- `AsTracking<T>(ISpecificationBuilder<T1>)`
  - Configures the specification to apply AsTracking behavior.
It will also disable AsNoTrackingWithIdentityResolution and AsNoTracking flags.
  - `builder`: The specification builder.
  - `<T>`: The type of the entity.
  - returns: The updated specification builder.
- `AsTracking<T>(ISpecificationBuilder<T1>, bool)`
  - Configures the specification to apply AsTracking behavior if the condition is true.
It will also disable AsNoTrackingWithIdentityResolution and AsNoTracking flags.
  - `builder`: The specification builder.
  - `condition`: The condition to evaluate.
  - `<T>`: The type of the entity.
  - returns: The updated specification builder.
- `EnableCache<T1, T2>(ISpecificationBuilder<T1,T2>, string, bool, object[])`
  - Sets the cache key for the specification.
  - `builder`: The specification builder.
  - `specificationName`: Used as prefix for the cache key.
  - `condition`: The condition to evaluate.
  - `args`: To be appended to the cache key, separated by dash.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - returns: A cache specification builder, useful for applying further caching functionalities.
- `EnableCache<T1, T2>(ISpecificationBuilder<T1,T2>, string, object[])`
  - Sets the cache key for the specification.
  - `builder`: The specification builder.
  - `specificationName`: Used as prefix for the cache key.
  - `args`: To be appended to the cache key, separated by dash.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - returns: A cache specification builder, useful for applying further caching functionalities.
- `EnableCache<T>(ISpecificationBuilder<T1>, string, bool, object[])`
  - Sets the cache key for the specification.
  - `builder`: The specification builder.
  - `specificationName`: Used as prefix for the cache key.
  - `condition`: The condition to evaluate.
  - `args`: To be appended to the cache key, separated by dash.
  - `<T>`: The type of the entity.
  - returns: A cache specification builder, useful for applying further caching functionalities.
- `EnableCache<T>(ISpecificationBuilder<T1>, string, object[])`
  - Sets the cache key for the specification.
  - `builder`: The specification builder.
  - `specificationName`: Used as prefix for the cache key.
  - `args`: To be appended to the cache key, separated by dash.
  - `<T>`: The type of the entity.
  - returns: A cache specification builder, useful for applying further caching functionalities.
- `IgnoreAutoIncludes<T1, T2>(ISpecificationBuilder<T1,T2>)`
  - Configures the specification to ignore auto includes.
  - `builder`: The specification builder.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - returns: The updated specification builder.
- `IgnoreAutoIncludes<T1, T2>(ISpecificationBuilder<T1,T2>, bool)`
  - Configures the specification to ignore auto includes if the condition is true.
  - `builder`: The specification builder.
  - `condition`: The condition to evaluate.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - returns: The updated specification builder.
- `IgnoreAutoIncludes<T>(ISpecificationBuilder<T1>)`
  - Configures the specification to ignore auto includes.
  - `builder`: The specification builder.
  - `<T>`: The type of the entity.
  - returns: The updated specification builder.
- `IgnoreAutoIncludes<T>(ISpecificationBuilder<T1>, bool)`
  - Configures the specification to ignore auto includes if the condition is true.
  - `builder`: The specification builder.
  - `condition`: The condition to evaluate.
  - `<T>`: The type of the entity.
  - returns: The updated specification builder.
- `IgnoreQueryFilters<T1, T2>(ISpecificationBuilder<T1,T2>)`
  - Configures the specification to ignore query filters.
  - `builder`: The specification builder.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - returns: The updated specification builder.
- `IgnoreQueryFilters<T1, T2>(ISpecificationBuilder<T1,T2>, bool)`
  - Configures the specification to ignore query filters if the condition is true.
  - `builder`: The specification builder.
  - `condition`: The condition to evaluate.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - returns: The updated specification builder.
- `IgnoreQueryFilters<T>(ISpecificationBuilder<T1>)`
  - Configures the specification to ignore query filters.
  - `builder`: The specification builder.
  - `<T>`: The type of the entity.
  - returns: The updated specification builder.
- `IgnoreQueryFilters<T>(ISpecificationBuilder<T1>, bool)`
  - Configures the specification to ignore query filters if the condition is true.
  - `builder`: The specification builder.
  - `condition`: The condition to evaluate.
  - `<T>`: The type of the entity.
  - returns: The updated specification builder.
- `Include<T1, T2, T3>(ISpecificationBuilder<T1,T2>, Expressions.Expression<Func<T1,T3>>)`
  - Adds an Include clause to the specification.
  - `builder`: The specification builder.
  - `navigationSelector`: The include expression.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - `<TProperty>`: The type of the property.
  - returns: The updated includable specification builder.
- `Include<T1, T2, T3>(ISpecificationBuilder<T1,T2>, Expressions.Expression<Func<T1,T3>>, bool)`
  - Adds an Include clause to the specification if the condition is true.
  - `builder`: The specification builder.
  - `navigationSelector`: The include expression.
  - `condition`: The condition to evaluate.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - `<TProperty>`: The type of the property.
  - returns: The updated includable specification builder.
- `Include<T1, T2>(ISpecificationBuilder<T1,T2>, string)`
  - Adds an Include clause to the specification.
  - `builder`: The specification builder.
  - `includeString`: The include string.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - returns: The updated specification builder.
- `Include<T1, T2>(ISpecificationBuilder<T1,T2>, string, bool)`
  - Adds an Include clause to the specification if the condition is true.
  - `builder`: The specification builder.
  - `includeString`: The include string.
  - `condition`: The condition to evaluate.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - returns: The updated specification builder.
- `Include<T1, T2>(ISpecificationBuilder<T1>, Expressions.Expression<Func<T1,T2>>)`
  - Adds an Include clause to the specification.
  - `builder`: The specification builder.
  - `navigationSelector`: The include expression.
  - `<T>`: The type of the entity.
  - `<TProperty>`: The type of the property.
  - returns: The updated includable specification builder.
- `Include<T1, T2>(ISpecificationBuilder<T1>, Expressions.Expression<Func<T1,T2>>, bool)`
  - Adds an Include clause to the specification if the condition is true.
  - `builder`: The specification builder.
  - `navigationSelector`: The include expression.
  - `condition`: The condition to evaluate.
  - `<T>`: The type of the entity.
  - `<TProperty>`: The type of the property.
  - returns: The updated includable specification builder.
- `Include<T>(ISpecificationBuilder<T1>, string)`
  - Adds an Include clause to the specification.
  - `builder`: The specification builder.
  - `includeString`: The include string.
  - `<T>`: The type of the entity.
  - returns: The updated specification builder.
- `Include<T>(ISpecificationBuilder<T1>, string, bool)`
  - Adds an Include clause to the specification if the condition is true.
  - `builder`: The specification builder.
  - `includeString`: The include string.
  - `condition`: The condition to evaluate.
  - `<T>`: The type of the entity.
  - returns: The updated specification builder.
- `OrderBy<T1, T2>(ISpecificationBuilder<T1,T2>, Expressions.Expression<Func<T1,object>>)`
  - Adds an OrderBy clause to the specification.
  - `builder`: The specification builder.
  - `keySelector`: The key selector expression.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - returns: The updated ordered specification builder.
- `OrderBy<T1, T2>(ISpecificationBuilder<T1,T2>, Expressions.Expression<Func<T1,object>>, bool)`
  - Adds an OrderBy clause to the specification if the condition is true.
  - `builder`: The specification builder.
  - `keySelector`: The key selector expression.
  - `condition`: The condition to evaluate.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - returns: The updated ordered specification builder.
- `OrderBy<T>(ISpecificationBuilder<T1>, Expressions.Expression<Func<T1,object>>)`
  - Adds an OrderBy clause to the specification.
  - `builder`: The specification builder.
  - `keySelector`: The key selector expression.
  - `<T>`: The type of the entity.
  - returns: The updated ordered specification builder.
- `OrderBy<T>(ISpecificationBuilder<T1>, Expressions.Expression<Func<T1,object>>, bool)`
  - Adds an OrderBy clause to the specification if the condition is true.
  - `builder`: The specification builder.
  - `keySelector`: The key selector expression.
  - `condition`: The condition to evaluate.
  - `<T>`: The type of the entity.
  - returns: The updated ordered specification builder.
- `OrderByDescending<T1, T2>(ISpecificationBuilder<T1,T2>, Expressions.Expression<Func<T1,object>>)`
  - Adds an OrderBy descending clause to the specification.
  - `builder`: The specification builder.
  - `keySelector`: The key selector expression.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - returns: The updated ordered specification builder.
- `OrderByDescending<T1, T2>(ISpecificationBuilder<T1,T2>, Expressions.Expression<Func<T1,object>>, bool)`
  - Adds an OrderByDescending clause to the specification if the condition is true.
  - `builder`: The specification builder.
  - `keySelector`: The key selector expression.
  - `condition`: The condition to evaluate.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - returns: The updated ordered specification builder.
- `OrderByDescending<T>(ISpecificationBuilder<T1>, Expressions.Expression<Func<T1,object>>)`
  - Adds an OrderByDescending clause to the specification.
  - `builder`: The specification builder.
  - `keySelector`: The key selector expression.
  - `<T>`: The type of the entity.
  - returns: The updated ordered specification builder.
- `OrderByDescending<T>(ISpecificationBuilder<T1>, Expressions.Expression<Func<T1,object>>, bool)`
  - Adds an OrderByDescending clause to the specification if the condition is true.
  - `builder`: The specification builder.
  - `keySelector`: The key selector expression.
  - `condition`: The condition to evaluate.
  - `<T>`: The type of the entity.
  - returns: The updated ordered specification builder.
- `PostProcessingAction<T1, T2>(ISpecificationBuilder<T1,T2>, Func<Generic.IEnumerable<T2>,Generic.IEnumerable<T2>>)`
  - Specify a function to apply to the result of the query. It's an in-memory operation.
  - `builder`: The specification builder.
  - `filter`: The filter function.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - returns: The updated specification builder.
- `PostProcessingAction<T>(ISpecificationBuilder<T1>, Func<Generic.IEnumerable<T1>,Generic.IEnumerable<T1>>)`
  - Specify a function to apply to the result of the query. It's an in-memory operation.
  - `builder`: The specification builder.
  - `filter`: The filter function.
  - `<T>`: The type of the entity.
  - returns: The updated specification builder.
- `Search<T1, T2>(ISpecificationBuilder<T1,T2>, Expressions.Expression<Func<T1,string>>, string, bool, int)`
  - Adds a Like clause to the specification if the condition is true.
  - `builder`: The specification builder.
  - `keySelector`: The key selector expression.
  - `pattern`: The pattern to match.
  - `condition`: The condition to evaluate.
  - `group`: The group number. Like clauses within the same group are evaluated using OR logic.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - returns: The updated specification builder.
- `Search<T1, T2>(ISpecificationBuilder<T1,T2>, Expressions.Expression<Func<T1,string>>, string, int)`
  - Adds a Like clause to the specification.
  - `builder`: The specification builder.
  - `keySelector`: The key selector expression.
  - `pattern`: The pattern to match.
  - `group`: The group number. Like clauses within the same group are evaluated using OR logic.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - returns: The updated specification builder.
- `Search<T>(ISpecificationBuilder<T1>, Expressions.Expression<Func<T1,string>>, string, bool, int)`
  - Adds a Like clause to the specification if the condition is true.
  - `builder`: The specification builder.
  - `keySelector`: The key selector expression.
  - `pattern`: The pattern to match.
  - `condition`: The condition to evaluate.
  - `group`: The group number. Like clauses within the same group are evaluated using OR logic.
  - `<T>`: The type of the entity.
  - returns: The updated specification builder.
- `Search<T>(ISpecificationBuilder<T1>, Expressions.Expression<Func<T1,string>>, string, int)`
  - Adds a Like clause to the specification.
  - `builder`: The specification builder.
  - `keySelector`: The key selector expression.
  - `pattern`: The pattern to match.
  - `group`: The group number. Like clauses within the same group are evaluated using OR logic.
  - `<T>`: The type of the entity.
  - returns: The updated specification builder.
- `Select<T1, T2>(ISpecificationBuilder<T1,T2>, Expressions.Expression<Func<T1,T2>>)`
  - Adds a Select clause to the specification.
  - `builder`: The specification builder.
  - `selector`: The selector expression.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
- `SelectMany<T1, T2>(ISpecificationBuilder<T1,T2>, Expressions.Expression<Func<T1,Generic.IEnumerable<T2>>>)`
  - Adds a SelectMany clause to the specification.
  - `builder`: The specification builder.
  - `selector`: The selector expression.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
- `Skip<T1, T2>(ISpecificationBuilder<T1,T2>, int)`
  - Sets the number of items to skip in the specification.
  - `builder`: The specification builder.
  - `skip`: The number of items to skip.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - returns: The updated specification builder.
- `Skip<T1, T2>(ISpecificationBuilder<T1,T2>, int, bool)`
  - Sets the number of items to skip in the specification if the condition is true.
  - `builder`: The specification builder.
  - `skip`: The number of items to skip.
  - `condition`: The condition to evaluate.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - returns: The updated specification builder.
- `Skip<T>(ISpecificationBuilder<T1>, int)`
  - Sets the number of items to skip in the specification.
  - `builder`: The specification builder.
  - `skip`: The number of items to skip.
  - `<T>`: The type of the entity.
  - returns: The updated specification builder.
- `Skip<T>(ISpecificationBuilder<T1>, int, bool)`
  - Sets the number of items to skip in the specification if the condition is true.
  - `builder`: The specification builder.
  - `skip`: The number of items to skip.
  - `condition`: The condition to evaluate.
  - `<T>`: The type of the entity.
  - returns: The updated specification builder.
- `TagWith<T1, T2>(ISpecificationBuilder<T1,T2>, string)`
  - Adds a query tag to the specification.
  - `builder`: The specification builder.
  - `tag`: The query tag.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - returns: The updated specification builder.
- `TagWith<T1, T2>(ISpecificationBuilder<T1,T2>, string, bool)`
  - Adds a query tag to the specification if the condition is true.
  - `builder`: The specification builder.
  - `tag`: The query tag.
  - `condition`: The condition to evaluate.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - returns: The updated specification builder.
- `TagWith<T>(ISpecificationBuilder<T1>, string)`
  - Adds a query tag to the specification.
  - `builder`: The specification builder.
  - `tag`: The query tag.
  - `<T>`: The type of the entity.
  - returns: The updated specification builder.
- `TagWith<T>(ISpecificationBuilder<T1>, string, bool)`
  - Adds a query tag to the specification if the condition is true.
  - `builder`: The specification builder.
  - `tag`: The query tag.
  - `condition`: The condition to evaluate.
  - `<T>`: The type of the entity.
  - returns: The updated specification builder.
- `Take<T1, T2>(ISpecificationBuilder<T1,T2>, int)`
  - Sets the number of items to take in the specification.
  - `builder`: The specification builder.
  - `take`: The number of items to take.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - returns: The updated specification builder.
- `Take<T1, T2>(ISpecificationBuilder<T1,T2>, int, bool)`
  - Sets the number of items to take in the specification if the condition is true.
  - `builder`: The specification builder.
  - `take`: The number of items to take.
  - `condition`: The condition to evaluate.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - returns: The updated specification builder.
- `Take<T>(ISpecificationBuilder<T1>, int)`
  - Sets the number of items to take in the specification.
  - `builder`: The specification builder.
  - `take`: The number of items to take.
  - `<T>`: The type of the entity.
  - returns: The updated specification builder.
- `Take<T>(ISpecificationBuilder<T1>, int, bool)`
  - Sets the number of items to take in the specification if the condition is true.
  - `builder`: The specification builder.
  - `take`: The number of items to take.
  - `condition`: The condition to evaluate.
  - `<T>`: The type of the entity.
  - returns: The updated specification builder.
- `ThenBy<T1, T2>(IOrderedSpecificationBuilder<T1,T2>, Expressions.Expression<Func<T1,object>>)`
  - Adds a ThenBy clause to the specification.
  - `builder`: The ordered specification builder.
  - `keySelector`: The key selector expression.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - returns: The updated ordered specification builder.
- `ThenBy<T1, T2>(IOrderedSpecificationBuilder<T1,T2>, Expressions.Expression<Func<T1,object>>, bool)`
  - Adds a ThenBy clause to the specification if the condition is true.
  - `builder`: The ordered specification builder.
  - `keySelector`: The key selector expression.
  - `condition`: The condition to evaluate.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - returns: The updated ordered specification builder.
- `ThenBy<T>(IOrderedSpecificationBuilder<T1>, Expressions.Expression<Func<T1,object>>)`
  - Adds a ThenBy clause to the specification.
  - `builder`: The ordered specification builder.
  - `keySelector`: The key selector expression.
  - `<T>`: The type of the entity.
  - returns: The updated ordered specification builder.
- `ThenBy<T>(IOrderedSpecificationBuilder<T1>, Expressions.Expression<Func<T1,object>>, bool)`
  - Adds a ThenBy clause to the specification if the condition is true.
  - `builder`: The ordered specification builder.
  - `keySelector`: The key selector expression.
  - `condition`: The condition to evaluate.
  - `<T>`: The type of the entity.
  - returns: The updated ordered specification builder.
- `ThenByDescending<T1, T2>(IOrderedSpecificationBuilder<T1,T2>, Expressions.Expression<Func<T1,object>>)`
  - Adds a ThenByDescending clause to the specification.
  - `builder`: The ordered specification builder.
  - `keySelector`: The key selector expression.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - returns: The updated ordered specification builder.
- `ThenByDescending<T1, T2>(IOrderedSpecificationBuilder<T1,T2>, Expressions.Expression<Func<T1,object>>, bool)`
  - Adds a ThenByDescending clause to the specification if the condition is true.
  - `builder`: The ordered specification builder.
  - `keySelector`: The key selector expression.
  - `condition`: The condition to evaluate.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - returns: The updated ordered specification builder.
- `ThenByDescending<T>(IOrderedSpecificationBuilder<T1>, Expressions.Expression<Func<T1,object>>)`
  - Adds a ThenByDescending clause to the specification.
  - `builder`: The ordered specification builder.
  - `keySelector`: The key selector expression.
  - `<T>`: The type of the entity.
  - returns: The updated ordered specification builder.
- `ThenByDescending<T>(IOrderedSpecificationBuilder<T1>, Expressions.Expression<Func<T1,object>>, bool)`
  - Adds a ThenByDescending clause to the specification if the condition is true.
  - `builder`: The ordered specification builder.
  - `keySelector`: The key selector expression.
  - `condition`: The condition to evaluate.
  - `<T>`: The type of the entity.
  - returns: The updated ordered specification builder.
- `ThenInclude<T1, T2, T3, T4>(IIncludableSpecificationBuilder<T1,T2,Generic.IEnumerable<T3>>, Expressions.Expression<Func<T3,T4>>)`
  - Adds a ThenInclude clause to the specification.
  - `builder`: The previous includable specification builder.
  - `navigationSelector`: The include expression.
  - `<TEntity>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - `<TPreviousProperty>`: The type of the previous property.
  - `<TProperty>`: The type of the property.
  - returns: The updated includable specification builder.
- `ThenInclude<T1, T2, T3, T4>(IIncludableSpecificationBuilder<T1,T2,Generic.IEnumerable<T3>>, Expressions.Expression<Func<T3,T4>>, bool)`
  - Adds a ThenInclude clause to the specification if the condition is true.
  - `builder`: The previous includable specification builder.
  - `navigationSelector`: The include expression.
  - `condition`: The condition to evaluate.
  - `<TEntity>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - `<TPreviousProperty>`: The type of the previous property.
  - `<TProperty>`: The type of the property.
  - returns: The updated includable specification builder.
- `ThenInclude<T1, T2, T3, T4>(IIncludableSpecificationBuilder<T1,T2,T3>, Expressions.Expression<Func<T3,T4>>)`
  - Adds a ThenInclude clause to the specification.
  - `builder`: The previous includable specification builder.
  - `navigationSelector`: The include expression.
  - `<TEntity>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - `<TPreviousProperty>`: The type of the previous property.
  - `<TProperty>`: The type of the property.
  - returns: The updated includable specification builder.
- `ThenInclude<T1, T2, T3, T4>(IIncludableSpecificationBuilder<T1,T2,T3>, Expressions.Expression<Func<T3,T4>>, bool)`
  - Adds a ThenInclude clause to the specification if the condition is true.
  - `builder`: The previous includable specification builder.
  - `navigationSelector`: The include expression.
  - `condition`: The condition to evaluate.
  - `<TEntity>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - `<TPreviousProperty>`: The type of the previous property.
  - `<TProperty>`: The type of the property.
  - returns: The updated includable specification builder.
- `ThenInclude<T1, T2, T3>(IIncludableSpecificationBuilder<T1,Generic.IEnumerable<T2>>, Expressions.Expression<Func<T2,T3>>)`
  - Adds a ThenInclude clause to the specification.
  - `builder`: The previous includable specification builder.
  - `navigationSelector`: The include expression.
  - `<TEntity>`: The type of the entity.
  - `<TPreviousProperty>`: The type of the previous property.
  - `<TProperty>`: The type of the property.
  - returns: The updated includable specification builder.
- `ThenInclude<T1, T2, T3>(IIncludableSpecificationBuilder<T1,Generic.IEnumerable<T2>>, Expressions.Expression<Func<T2,T3>>, bool)`
  - Adds a ThenInclude clause to the specification if the condition is true.
  - `builder`: The previous includable specification builder.
  - `navigationSelector`: The include expression.
  - `condition`: The condition to evaluate.
  - `<TEntity>`: The type of the entity.
  - `<TPreviousProperty>`: The type of the previous property.
  - `<TProperty>`: The type of the property.
  - returns: The updated includable specification builder.
- `ThenInclude<T1, T2, T3>(IIncludableSpecificationBuilder<T1,T2>, Expressions.Expression<Func<T2,T3>>)`
  - Adds a ThenInclude clause to the specification.
  - `builder`: The previous includable specification builder.
  - `navigationSelector`: The include expression.
  - `<TEntity>`: The type of the entity.
  - `<TPreviousProperty>`: The type of the previous property.
  - `<TProperty>`: The type of the property.
  - returns: The updated includable specification builder.
- `ThenInclude<T1, T2, T3>(IIncludableSpecificationBuilder<T1,T2>, Expressions.Expression<Func<T2,T3>>, bool)`
  - Adds a ThenInclude clause to the specification if the condition is true.
  - `builder`: The previous includable specification builder.
  - `navigationSelector`: The include expression.
  - `condition`: The condition to evaluate.
  - `<TEntity>`: The type of the entity.
  - `<TPreviousProperty>`: The type of the previous property.
  - `<TProperty>`: The type of the property.
  - returns: The updated includable specification builder.
- `Where<T1, T2>(ISpecificationBuilder<T1,T2>, Expressions.Expression<Func<T1,bool>>)`
  - Adds a Where clause to the specification.
  - `builder`: The specification builder.
  - `predicate`: The predicate expression.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - returns: The updated specification builder.
- `Where<T1, T2>(ISpecificationBuilder<T1,T2>, Expressions.Expression<Func<T1,bool>>, bool)`
  - Adds a Where clause to the specification if the condition is true.
  - `builder`: The specification builder.
  - `predicate`: The predicate expression.
  - `condition`: The condition to evaluate.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - returns: The updated specification builder.
- `Where<T>(ISpecificationBuilder<T1>, Expressions.Expression<Func<T1,bool>>)`
  - Adds a Where clause to the specification.
  - `builder`: The specification builder.
  - `predicate`: The predicate expression.
  - `<T>`: The type of the entity.
  - returns: The updated specification builder.
- `Where<T>(ISpecificationBuilder<T1>, Expressions.Expression<Func<T1,bool>>, bool)`
  - Adds a Where clause to the specification if the condition is true.
  - `builder`: The specification builder.
  - `predicate`: The predicate expression.
  - `condition`: The condition to evaluate.
  - `<T>`: The type of the entity.
  - returns: The updated specification builder.
- `WithCacheKey<T1, T2>(ISpecificationBuilder<T1,T2>, string)`
  - Sets the cache key for the specification.
  - `builder`: The specification builder.
  - `cacheKey`: The cache key to be used.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - returns: A cache specification builder, useful for applying further caching functionalities.
- `WithCacheKey<T1, T2>(ISpecificationBuilder<T1,T2>, string, bool)`
  - Sets the cache key for the specification.
  - `builder`: The specification builder.
  - `cacheKey`: The cache key to be used.
  - `condition`: The condition to evaluate.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - returns: A cache specification builder, useful for applying further caching functionalities.
- `WithCacheKey<T>(ISpecificationBuilder<T1>, string)`
  - Sets the cache key for the specification.
  - `builder`: The specification builder.
  - `cacheKey`: The cache key to be used.
  - `<T>`: The type of the entity.
  - returns: A cache specification builder, useful for applying further caching functionalities.
- `WithCacheKey<T>(ISpecificationBuilder<T1>, string, bool)`
  - Sets the cache key for the specification.
  - `builder`: The specification builder.
  - `cacheKey`: The cache key to be used.
  - `condition`: The condition to evaluate.
  - `<T>`: The type of the entity.
  - returns: A cache specification builder, useful for applying further caching functionalities.


### `SpecificationExtensions`

Extension methods for specifications.

**Methods:**

- `WithProjectionOf<T1, T2>(Specification<T1>, Specification<T1,T2>)`
  - Creates a new specification by applying a projection specification to the current specification.
  - `source`: The source specification to which the projection will be applied. Cannot be .
  - `projectionSpec`: The projection specification that defines the transformation to apply to the source specification. Cannot be
.
  - `<T>`: The type of the entity.
  - `<TResult>`: The type of the result.
  - returns: A new `Specification<T1, T2>` that represents the result of applying the projection to the
source specification.
  - remarks: This method clones the source specification and applies the projection specification's select
statements to create a new specification. The input specifications remain unchanged.


### `Specification<T>`

**Methods:**

- `Evaluate(Generic.IEnumerable<T1>)`
- `IsSatisfiedBy(T1)`

**Properties:**

- `AsNoTracking`
- `AsNoTrackingWithIdentityResolution`
- `AsSplitQuery`
- `AsTracking`
- `CacheEnabled`
- `CacheKey`
- `Evaluator`
  - Gets the evaluator used to process the specification in memory.
- `IgnoreAutoIncludes`
- `IgnoreQueryFilters`
- `IncludeExpressions`
- `IncludeStrings`
- `Items`
- `OrderExpressions`
- `PostProcessingAction`
- `Query`
- `QueryTags`
- `SearchCriterias`
- `Skip`
- `Take`
- `Validator`
  - Gets the validator used to validate entities against the specification.
- `WhereExpressions`


### `Specification<T1, T2>`

**Methods:**

- `Evaluate(Generic.IEnumerable<T1>)`

**Properties:**

- `PostProcessingAction`
- `Query`
- `Selector`
- `SelectorMany`


### `WhereEvaluator`

Represents an evaluator for where expressions.

**Methods:**

- `Evaluate<T>(Generic.IEnumerable<T1>, ISpecification<T1>)`
- `GetQuery<T>(IQueryable<T1>, ISpecification<T1>)`

**Properties:**

- `Instance`
  - Gets the singleton instance of the `WhereEvaluator` class.
- `IsCriteriaEvaluator`


### `WhereExpressionInfo<T>`

Encapsulates data needed to perform filtering.

**Methods:**

- `#ctor(Expressions.Expression<Func<T1,bool>>)`
  - Creates instance of `WhereExpressionInfo<T>`.
  - `filter`: Condition which should be satisfied by instances of T.

**Properties:**

- `Filter`
  - Condition which should be satisfied by instances of T.
- `FilterFunc`
  - Compiled `Filter`.
