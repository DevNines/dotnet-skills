# Ardalis.Specification v8.0.0 — API surface

_Generated from the XML doc comments shipped in `Ardalis.Specification.8.0.0.nupkg` (target framework `netstandard2.0`). Do not edit by hand — rerun `scripts/update_skill.py`._

Use **only** the members listed here when writing code against Ardalis.Specification v8.x. If a member you want isn't here, it doesn't exist in this major and you must pick another approach.

## namespace `Ardalis.Specification`

### `IReadRepositoryBase<T>`

A `IRepositoryBase<T>` can be used to query instances of T.
An `ISpecification<T>` (or derived) is used to encapsulate the LINQ queries against the database.

**Methods:**

- `AnyAsync(CancellationToken)`
  - Returns a boolean whether any entity exists or not.
  - returns: A task that represents the asynchronous operation. The task result contains true if the
source sequence contains any elements; otherwise, false.
- `AnyAsync(ISpecification<T1>, CancellationToken)`
  - Returns a boolean that represents whether any entity satisfy the encapsulated query logic
of the specification or not.
  - `specification`: The encapsulated query logic.
  - returns: A task that represents the asynchronous operation. The task result contains true if the
source sequence contains any elements; otherwise, false.
- `CountAsync(CancellationToken)`
  - Returns the total number of records.
  - returns: A task that represents the asynchronous operation. The task result contains the
number of elements in the input sequence.
- `CountAsync(ISpecification<T1>, CancellationToken)`
  - Returns a number that represents how many entities satisfy the encapsulated query logic
of the specification.
  - `specification`: The encapsulated query logic.
  - returns: A task that represents the asynchronous operation. The task result contains the
number of elements in the input sequence.
- `FirstOrDefaultAsync(ISpecification<T1>, CancellationToken)`
  - Returns the first element of a sequence, or a default value if the sequence contains no elements.
  - `specification`: The encapsulated query logic.
  - `cancellationToken`: A `CancellationToken` to observe while waiting for the task to complete.
  - returns: A task that represents the asynchronous operation.
The task result contains the T, or .
- `FirstOrDefaultAsync<T>(ISpecification<T1,T1>, CancellationToken)`
  - Returns the first element of a sequence, or a default value if the sequence contains no elements.
  - `specification`: The encapsulated query logic.
  - `cancellationToken`: A `CancellationToken` to observe while waiting for the task to complete.
  - returns: A task that represents the asynchronous operation.
The task result contains the TResult, or .
- `GetByIdAsync<T>(T1, CancellationToken)`
  - Finds an entity with the given primary key value.
  - `id`: The value of the primary key for the entity to be found.
  - `cancellationToken`
  - `<TId>`: The type of primary key.
  - returns: A task that represents the asynchronous operation.
The task result contains the T, or .
- `GetBySpecAsync(ISpecification<T1>, CancellationToken)`
  - Finds an entity that matches the encapsulated query logic of the specification.
  - `specification`: The encapsulated query logic.
  - returns: A task that represents the asynchronous operation.
The task result contains the T, or .
- `GetBySpecAsync<T>(ISpecification<T1,T1>, CancellationToken)`
  - Finds an entity that matches the encapsulated query logic of the specification.
  - `specification`: The encapsulated query logic.
  - `<TResult>`: The type of the result.
  - returns: A task that represents the asynchronous operation.
The task result contains the TResult.
- `ListAsync(CancellationToken)`
  - Finds all entities of T from the database.
  - returns: A task that represents the asynchronous operation.
The task result contains a `List<T>` that contains elements from the input sequence.
- `ListAsync(ISpecification<T1>, CancellationToken)`
  - Finds all entities of T, that matches the encapsulated query logic of the
specification, from the database.
  - `specification`: The encapsulated query logic.
  - returns: A task that represents the asynchronous operation.
The task result contains a `List<T>` that contains elements from the input sequence.
- `ListAsync<T>(ISpecification<T1,T1>, CancellationToken)`
  - Finds all entities of T, that matches the encapsulated query logic of the
specification, from the database.


Projects each entity into a new form, being TResult.
  - `specification`: The encapsulated query logic.
  - `<TResult>`: The type of the value returned by the projection.
  - returns: A task that represents the asynchronous operation.
The task result contains a `List<T>` that contains elements from the input sequence.
- `SingleOrDefaultAsync(ISingleResultSpecification<T1>, CancellationToken)`
  - Returns the only element of a sequence, or a default value if the sequence is empty; this method throws an exception if there is more than one element in the sequence.
  - `specification`: The encapsulated query logic.
  - `cancellationToken`: A `CancellationToken` to observe while waiting for the task to complete.
  - returns: A task that represents the asynchronous operation.
The task result contains the T, or .
- `SingleOrDefaultAsync<T>(ISingleResultSpecification<T1,T1>, CancellationToken)`
  - Returns the only element of a sequence, or a default value if the sequence is empty; this method throws an exception if there is more than one element in the sequence.
  - `specification`: The encapsulated query logic.
  - `cancellationToken`: A `CancellationToken` to observe while waiting for the task to complete.
  - returns: A task that represents the asynchronous operation.
The task result contains the TResult, or .


### `IRepositoryBase<T>`

A `IRepositoryBase<T>` can be used to query and save instances of T.
An `ISpecification<T>` (or derived) is used to encapsulate the LINQ queries against the database.

**Methods:**

- `AddAsync(T1, CancellationToken)`
  - Adds an entity in the database.
  - `entity`: The entity to add.
  - `cancellationToken`
  - returns: A task that represents the asynchronous operation.
The task result contains the T.
- `AddRangeAsync(Generic.IEnumerable<T1>, CancellationToken)`
  - Adds the given entities in the database
  - `entities`
  - `cancellationToken`
  - returns: A task that represents the asynchronous operation.
- `DeleteAsync(T1, CancellationToken)`
  - Removes an entity in the database
  - `entity`: The entity to delete.
  - returns: A task that represents the asynchronous operation.
- `DeleteRangeAsync(Generic.IEnumerable<T1>, CancellationToken)`
  - Removes the given entities in the database
  - `entities`: The entities to remove.
  - returns: A task that represents the asynchronous operation.
- `DeleteRangeAsync(ISpecification<T1>, CancellationToken)`
  - Removes the all entities of T, that matches the encapsulated query logic of the
specification, from the database.
  - `specification`: The encapsulated query logic.
  - returns: A task that represents the asynchronous operation.
- `SaveChangesAsync(CancellationToken)`
  - Persists changes to the database.
  - returns: A task that represents the asynchronous operation.
- `UpdateAsync(T1, CancellationToken)`
  - Updates an entity in the database
  - `entity`: The entity to update.
  - returns: A task that represents the asynchronous operation.
- `UpdateRangeAsync(Generic.IEnumerable<T1>, CancellationToken)`
  - Updates the given entities in the database
  - `entities`: The entities to update.
  - `cancellationToken`
  - returns: A task that represents the asynchronous operation.


### `ISingleResultSpecification`

A marker interface for specifications that are meant to return a single entity. Used to constrain methods
that accept a Specification and return a single result rather than a collection of results.


### `ISingleResultSpecification<T>`

Encapsulates query logic for T. It is meant to return a single result.


### `ISingleResultSpecification<T1, T2>`

Encapsulates query logic for T,
and projects the result into TResult. It is meant to return a single result.


### `ISpecificationEvaluator`

Evaluates the logic encapsulated by an `ISpecification<T>`.

**Methods:**

- `GetQuery<T1, T2>(IQueryable<T1>, ISpecification<T1,T2>)`
  - Applies the logic encapsulated by specification to given inputQuery,
and projects the result into TResult.
  - `inputQuery`: The sequence of T
  - `specification`: The encapsulated query logic.
  - `<TResult>`: The type of the result.
  - returns: A filtered sequence of TResult
- `GetQuery<T>(IQueryable<T1>, ISpecification<T1>, bool)`
  - Applies the logic encapsulated by specification to given inputQuery.
  - `inputQuery`: The sequence of T
  - `specification`: The encapsulated query logic.
  - returns: A filtered sequence of T


### `ISpecification<T>`

Encapsulates query logic for T.

**Methods:**

- `Evaluate(Generic.IEnumerable<T1>)`
  - Applies the query defined within the specification to the given objects.
This is specially helpful when unit testing specification classes
  - `entities`: the list of entities to which the specification will be applied
- `IsSatisfiedBy(T1)`
  - It returns whether the given entity satisfies the conditions of the specification.
  - `entity`: The entity to be validated

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
- `SearchCriterias`
  - The collection of 'SQL LIKE' operations.
- `Skip`
  - The number of elements to skip before returning the remaining elements.
- `Take`
  - The number of elements to return.
- `WhereExpressions`
  - The collection of filters.


### `ISpecification<T1, T2>`

Encapsulates query logic for T,
and projects the result into TResult.

**Properties:**

- `PostProcessingAction`
  - The transform function to apply to the result of the query encapsulated by the `ISpecification<T1, T2>`.
- `Selector`
  - The Select transform function to apply to the T element.
- `SelectorMany`
  - The SelectMany transform function to apply to the T element.


### `IncludeExpressionInfo`

Encapsulates data needed to build Include/ThenInclude query.

**Methods:**

- `#ctor(Expressions.LambdaExpression, Type, Type)`
  - Creates instance of `IncludeExpressionInfo` which describes 'Include' query part.


Source (entityType) -> Include (propertyType).
  - `expression`: The expression represents a related entity that should be included.
  - `entityType`: The type of the source entity.
  - `propertyType`: The type of the included entity.
- `#ctor(Expressions.LambdaExpression, Type, Type, Type)`
  - Creates instance of `IncludeExpressionInfo` which describes 'ThenInclude' query part.


Source (entityType) -> Include (previousPropertyType) -> ThenInclude (propertyType).
  - `expression`: The expression represents a related entity that should be included as part of the previously included entity.
  - `entityType`: The type of the source entity.
  - `propertyType`: The type of the included entity.
  - `previousPropertyType`: The type of the previously included entity.

**Properties:**

- `EntityType`
  - The type of the source entity.
- `LambdaExpression`
  - If `Type` is `Include`, represents a related entity that should be included.


If `Type` is `ThenInclude`, represents a related entity that should be included as part of the previously included entity.
- `PreviousPropertyType`
  - The type of the previously included entity.
- `PropertyType`
  - The type of the included entity.
- `Type`
  - The include type.


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


### `SingleResultSpecification<T>`


### `SingleResultSpecification<T1, T2>`


### `SpecificationBuilderExtensions`

**Methods:**

- `AsNoTracking<T>(ISpecificationBuilder<T1>)`
  - If the entity instances are modified, this will not be detected
by the change tracker.
  - `specificationBuilder`
- `AsNoTracking<T>(ISpecificationBuilder<T1>, bool)`
  - If the entity instances are modified, this will not be detected
by the change tracker.
  - `specificationBuilder`
  - `condition`: If false, the setting will be discarded.
- `AsNoTrackingWithIdentityResolution<T>(ISpecificationBuilder<T1>)`
  - The query will then keep track of returned instances
(without tracking them in the normal way)
and ensure no duplicates are created in the query results
  - `specificationBuilder`
  - `<T>`
  - remarks: for more info: https://docs.microsoft.com/en-us/ef/core/change-tracking/identity-resolution#identity-resolution-and-queries
- `AsNoTrackingWithIdentityResolution<T>(ISpecificationBuilder<T1>, bool)`
  - The query will then keep track of returned instances
(without tracking them in the normal way)
and ensure no duplicates are created in the query results
  - `specificationBuilder`
  - `condition`: If false, the setting will be discarded.
  - `<T>`
  - remarks: for more info: https://docs.microsoft.com/en-us/ef/core/change-tracking/identity-resolution#identity-resolution-and-queries
- `AsSplitQuery<T>(ISpecificationBuilder<T1>)`
  - The generated sql query will be split into multiple SQL queries
  - `specificationBuilder`
  - `<T>`
  - remarks: This feature was introduced in EF Core 5.0. It only works when using Include
for more info: https://docs.microsoft.com/en-us/ef/core/querying/single-split-queries
- `AsSplitQuery<T>(ISpecificationBuilder<T1>, bool)`
  - The generated sql query will be split into multiple SQL queries
  - `specificationBuilder`
  - `condition`: If false, the setting will be discarded.
  - `<T>`
  - remarks: This feature was introduced in EF Core 5.0. It only works when using Include
for more info: https://docs.microsoft.com/en-us/ef/core/querying/single-split-queries
- `AsTracking<T>(ISpecificationBuilder<T1>)`
  - If the entity instances are modified, this will be detected
by the change tracker.
  - `specificationBuilder`
- `AsTracking<T>(ISpecificationBuilder<T1>, bool)`
  - If the entity instances are modified, this will be detected
by the change tracker.
  - `specificationBuilder`
  - `condition`: If false, the setting will be discarded.
- `EnableCache<T>(ISpecificationBuilder<T1>, string, bool, object[])`
  - Must be called after specifying criteria
  - `specificationName`
  - `args`: Any arguments used in defining the specification
  - `condition`: If false, the caching won't be enabled.
- `EnableCache<T>(ISpecificationBuilder<T1>, string, object[])`
  - Must be called after specifying criteria
  - `specificationName`
  - `args`: Any arguments used in defining the specification
- `IgnoreQueryFilters<T>(ISpecificationBuilder<T1>)`
  - The query will ignore the defined global query filters
  - `specificationBuilder`
  - `<T>`
  - remarks: for more info: https://docs.microsoft.com/en-us/ef/core/querying/filters
- `IgnoreQueryFilters<T>(ISpecificationBuilder<T1>, bool)`
  - The query will ignore the defined global query filters
  - `specificationBuilder`
  - `condition`: If false, the setting will be discarded.
  - `<T>`
  - remarks: for more info: https://docs.microsoft.com/en-us/ef/core/querying/filters
- `Include<T1, T2>(ISpecificationBuilder<T1>, Expressions.Expression<Func<T1,T2>>)`
  - Specify an include expression.
This information is utilized to build Include function in the query, which ORM tools like Entity Framework use
to include related entities (via navigation properties) in the query result.
  - `specificationBuilder`
  - `includeExpression`
  - `<T>`
  - `<TProperty>`
- `Include<T1, T2>(ISpecificationBuilder<T1>, Expressions.Expression<Func<T1,T2>>, bool)`
  - Specify an include expression.
This information is utilized to build Include function in the query, which ORM tools like Entity Framework use
to include related entities (via navigation properties) in the query result.
  - `specificationBuilder`
  - `includeExpression`
  - `condition`: If false, the expression won't be added. The whole Include chain will be discarded.
  - `<T>`
  - `<TProperty>`
- `Include<T>(ISpecificationBuilder<T1>, string)`
  - Specify a collection of navigation properties, as strings, to include in the query.
  - `specificationBuilder`
  - `includeString`
  - `<T>`
- `Include<T>(ISpecificationBuilder<T1>, string, bool)`
  - Specify a collection of navigation properties, as strings, to include in the query.
  - `specificationBuilder`
  - `includeString`
  - `condition`: If false, the include expression won't be added.
  - `<T>`
- `OrderBy<T>(ISpecificationBuilder<T1>, Expressions.Expression<Func<T1,object>>)`
  - Specify the query result will be ordered by orderExpression in an ascending order
  - `specificationBuilder`
  - `orderExpression`
  - `<T>`
- `OrderBy<T>(ISpecificationBuilder<T1>, Expressions.Expression<Func<T1,object>>, bool)`
  - Specify the query result will be ordered by orderExpression in an ascending order
  - `specificationBuilder`
  - `orderExpression`
  - `condition`: If false, the expression won't be added. The whole Order chain will be discarded.
  - `<T>`
- `OrderByDescending<T>(ISpecificationBuilder<T1>, Expressions.Expression<Func<T1,object>>)`
  - Specify the query result will be ordered by orderExpression in a descending order
  - `specificationBuilder`
  - `orderExpression`
  - `<T>`
- `OrderByDescending<T>(ISpecificationBuilder<T1>, Expressions.Expression<Func<T1,object>>, bool)`
  - Specify the query result will be ordered by orderExpression in a descending order
  - `specificationBuilder`
  - `orderExpression`
  - `condition`: If false, the expression won't be added. The whole Order chain will be discarded.
  - `<T>`
- `PostProcessingAction<T1, T2>(ISpecificationBuilder<T1,T2>, Func<Generic.IEnumerable<T2>,Generic.IEnumerable<T2>>)`
  - Specify a transform function to apply to the result of the query.
and returns another TResult type
- `PostProcessingAction<T>(ISpecificationBuilder<T1>, Func<Generic.IEnumerable<T1>,Generic.IEnumerable<T1>>)`
  - Specify a transform function to apply to the result of the query
and returns the same T type
- `Search<T>(ISpecificationBuilder<T1>, Expressions.Expression<Func<T1,string>>, string, bool, int)`
  - Specify a 'SQL LIKE' operations for search purposes
  - `specificationBuilder`
  - `selector`: the property to apply the SQL LIKE against
  - `searchTerm`: the value to use for the SQL LIKE
  - `condition`: If false, the expression won't be added.
  - `searchGroup`: the index used to group sets of Selectors and SearchTerms together
  - `<T>`
- `Search<T>(ISpecificationBuilder<T1>, Expressions.Expression<Func<T1,string>>, string, int)`
  - Specify a 'SQL LIKE' operations for search purposes
  - `specificationBuilder`
  - `selector`: the property to apply the SQL LIKE against
  - `searchTerm`: the value to use for the SQL LIKE
  - `searchGroup`: the index used to group sets of Selectors and SearchTerms together
  - `<T>`
- `Select<T1, T2>(ISpecificationBuilder<T1,T2>, Expressions.Expression<Func<T1,T2>>)`
  - Specify a transform function to apply to the T element
to produce another TResult element.
- `SelectMany<T1, T2>(ISpecificationBuilder<T1,T2>, Expressions.Expression<Func<T1,Generic.IEnumerable<T2>>>)`
  - Specify a transform function to apply to the T element
to produce a flattened sequence of TResult elements.
- `Skip<T>(ISpecificationBuilder<T1>, int)`
  - Specify the number of elements to skip before returning the remaining elements.
  - `specificationBuilder`
  - `skip`: number of elements to skip
  - `<T>`
- `Skip<T>(ISpecificationBuilder<T1>, int, bool)`
  - Specify the number of elements to skip before returning the remaining elements.
  - `specificationBuilder`
  - `skip`: number of elements to skip
  - `condition`: If false, the value will be discarded.
  - `<T>`
- `Take<T>(ISpecificationBuilder<T1>, int)`
  - Specify the number of elements to return.
  - `specificationBuilder`
  - `take`: number of elements to take
- `Take<T>(ISpecificationBuilder<T1>, int, bool)`
  - Specify the number of elements to return.
  - `specificationBuilder`
  - `take`: number of elements to take
  - `condition`: If false, the value will be discarded.
- `Where<T>(ISpecificationBuilder<T1>, Expressions.Expression<Func<T1,bool>>)`
  - Specify a predicate that will be applied to the query
  - `specificationBuilder`
  - `criteria`
  - `<T>`
- `Where<T>(ISpecificationBuilder<T1>, Expressions.Expression<Func<T1,bool>>, bool)`
  - Specify a predicate that will be applied to the query
  - `specificationBuilder`
  - `criteria`
  - `condition`: If false, the criteria won't be added.
  - `<T>`


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
- `IgnoreQueryFilters`
- `IncludeExpressions`
- `IncludeStrings`
- `Items`
- `PostProcessingAction`
- `SearchCriterias`
- `Skip`
- `Take`
- `WhereExpressions`


### `Specification<T1, T2>`

**Properties:**

- `PostProcessingAction`
- `Selector`
- `SelectorMany`


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
