# Ardalis.Specification — release notes by major

_Generated from `https://github.com/ardalis/Specification/releases`. Use when answering migration questions or when a user asks what changed between versions._

## v9.x

### v9.3.1  (v9.3.1)
<https://github.com/ardalis/Specification/releases/tag/v9.3.1>

## What's Changed
* Fix allocations produced by unreachable fallback code by @fiseni in https://github.com/ardalis/Specification/pull/529
* Use NSubstitute for testing custom spec implementations. by @fiseni in https://github.com/ardalis/Specification/pull/530

**Full Changelog**: https://github.com/ardalis/Specification/compare/v9.3.0...v9.3.1

### v9.3.0  (v9.3.0)
<https://github.com/ardalis/Specification/releases/tag/v9.3.0>

## What's Changed
* Avoid List allocation for PostProcessingAction. by @fiseni in https://github.com/ardalis/Specification/pull/501
* Redefine WithProjectionOf as an extension to Specification instead of ISpecification by @fiseni in https://github.com/ardalis/Specification/pull/517
* Rename TagWithEvaluator to QueryTagEvaluator. by @fiseni in https://github.com/ardalis/Specification/pull/512
* OneOrMany implementation by @fiseni in https://github.com/ardalis/Specification/pull/507
* Refactor the state of where expressions as OneOrMany. by @fiseni in https://github.com/ardalis/Specification/pull/508
* Refactor the state of order expressions as OneOrMany. by @fiseni in https://github.com/ardalis/Specification/pull/509
* Refactor the state of include expressions as OneOrMany. by @fiseni in https://github.com/ardalis/Specification/pull/510
* Refactor the state of search expressions as OneOrMany. by @fiseni in https://github.com/ardalis/Specification/pull/511
* Consolidate OneOrMany implementation and its usage. by @fiseni in https://github.com/ardalis/Specification/pull/513
* Add a fallback to LINQ for search evaluators/validator in case of custom user specifications. by @fiseni in https://github.com/ardalis/Specification/pull/514
* Update dependencies. by @fiseni in https://github.com/ardalis/Specification/pull/526
* Use opencover format for coverage reports. by @fiseni in https://github.com/ardalis/Specification/pull/503
* Added Full Build workflow that publishes coverage reports. by @fiseni in https://github.com/ardalis/Specification/pull/504
* Add benchmarks project. by @fiseni in https://github.com/ardalis/Specification/pull/505
* Cleanup by @fiseni in https://github.com/ardalis/Specification/pull/518
* Add new test fixtures for EF6 provider. by @fiseni in https://github.com/ardalis/Specification/pull/519
* Add tests for EF6 evaluators. by @fiseni in https://github.com/ardalis/Specification/pull/520

**Full Changelog**: https://github.com/ardalis/Specification/compare/v9.2.0...v9.3.0

### v9.2.0  (v9.2.0)
<https://github.com/ardalis/Specification/releases/tag/v9.2.0>

## What's Changed

* Add support for multiple TagWith by @fiseni in https://github.com/ardalis/Specification/pull/493

**Full Changelog**: https://github.com/ardalis/Specification/compare/v9.1.0...v9.2.0

### v9.1.0  (v9.1.0)
<https://github.com/ardalis/Specification/releases/tag/v9.1.0>

## What's Changed
* Add WithProjectionOf feature. by @fiseni in https://github.com/ardalis/Specification/pull/460
* Fix type inference for ThenInclude with casting. by @fiseni in https://github.com/ardalis/Specification/pull/466


**Full Changelog**: https://github.com/ardalis/Specification/compare/v9.0.1...v9.1.0

### v9.0.1  (v9.0.1)
<https://github.com/ardalis/Specification/releases/tag/v9.0.1>

## What's Changed
* Re-add inheritance in the builders. by @fiseni in https://github.com/ardalis/Specification/pull/457

**Full Changelog**: https://github.com/ardalis/Specification/compare/v9.0.0...v9.0.1

### v9.0.0  (v9.0.0)
<https://github.com/ardalis/Specification/releases/tag/v9.0.0>

## What's Changed
* Update TFMs and reorganize solution. by @fiseni in https://github.com/ardalis/Specification/pull/439
* Revise EF Core dependencies per TFM. by @fiseni in https://github.com/ardalis/Specification/pull/449
* Refactor specification constructors as public. by @fiseni in https://github.com/ardalis/Specification/pull/431
* Remove IEntity contract. by @fiseni in https://github.com/ardalis/Specification/pull/432
* Reduce the size of specifications and avoid unnecessary memory allocations by @fiseni in https://github.com/ardalis/Specification/pull/441
* Fix InMemory SearchExtension bug by @fiseni in https://github.com/ardalis/Specification/pull/391
* Update and improve the builder infrastructure. by @fiseni in https://github.com/ardalis/Specification/pull/442
* Improve search validator and in-memory evaluator. by @fiseni in https://github.com/ardalis/Specification/pull/443
* Optimize the search EF evaluator. by @fiseni in https://github.com/ardalis/Specification/pull/444
* Optimize include evaluators. by @fiseni in https://github.com/ardalis/Specification/pull/447
* Simplify and minimize expression containers. by @fiseni in https://github.com/ardalis/Specification/pull/448
* Add TagWith and IgnoreAutoIncludes features. by @fiseni in https://github.com/ardalis/Specification/pull/451
* Add WithCacheKey extensions. by @fiseni in https://github.com/ardalis/Specification/pull/452
* 397 make fields and methods protected by @eldamir in https://github.com/ardalis/Specification/pull/398
* Update repository methods. by @fiseni in https://github.com/ardalis/Specification/pull/450
* Refactor the test suite by @fiseni in https://github.com/ardalis/Specification/pull/437
* Update GitHub workflows to use Linux hosts. by @fiseni in https://github.com/ardalis/Specification/pull/440
* Update Readme files. by @fiseni in https://github.com/ardalis/Specification/pull/453
* Add tests by @fiseni in https://github.com/ardalis/Specification/pull/454
* Prepare for publish, version 9.0.0 by @fiseni in https://github.com/ardalis/Specification/pull/455

## New Contributors
* @eldamir made their first contribution in https://github.com/ardalis/Specification/pull/398

**Full Changelog**: https://github.com/ardalis/Specification/compare/v8.0...v9.0.0

## Breaking Changes

The "standard" use of the library remains fairly intact.

- The obsolete `GetBySpec` repository methods are removed.
- The `IEntity` interface is removed.
- The `Select`/`SelectMany` are applied at the end of the chain or in a separate Query clause. These extension methods return void and no further chaining is possible.

In this version, we refactored the internals and the building blocks significantly. The "advanced" use cases are affected by these changes. Users who have custom extensions or have been relying on the internals need to migrate accordingly.

- The expression collections no longer are initialized to a new `List<T>` by default and will return `Enumerable.Empty<T>` if empty.
- The default value for `Take` and `Skip` properties no longer is `null`. They're updated to a non-nullable `int` type with a default value of `-1`.
- The specification constructors no longer accept `IInMemorySpecificationEvaluator` and `ISpecificationValidator` parameters. The properties are still defined as virtual and can be overridden.
- The builder infrastructure is refactored to accommodate better flow for specs with projections. All extensions should be written for both `ISpecificationBuilder<T>` and `ISpecificationBuilder<T, TResult>` builders.
- The `OrderedSpecificationBuilder` and `CacheSpecificationBuilder` are removed.
- The in-memory `SearchEvaluator` is renamed to `SearchMemoryEvaluator`.
- The `IncludeEvaluator.Default` and `IncludeEvaluator.Cached` singleton instances are removed. Instead, use the `IncludeEvaluator.Instance`.
- The `SpecificationEvaluator` no longer accepts `bool cacheEnabled` parameter. The caching is applied by default wherever necessary.
- The `EntityType`, `PropertyType`, and `PreviousPropertyType` are removed from `IncludeExpressionInfo`.
- The `Update` and `Delete` repository methods return `Task<int>` (the affected rows).


## v8.x

### v8.0  (v8.0)
<https://github.com/ardalis/Specification/releases/tag/v8.0>

## What's Changed
* Add AsTracking feature. by @fiseni in https://github.com/ardalis/Specification/pull/338
* Update LangVersion. Consolidate styling and conventions. by @fiseni in https://github.com/ardalis/Specification/pull/345
* Add sample applications. by @fiseni in https://github.com/ardalis/Specification/pull/347
* Add net6.0 TFM for EntityFramework6 package. by @fiseni in https://github.com/ardalis/Specification/pull/348
* Create new CI and Release workflows. by @fiseni in https://github.com/ardalis/Specification/pull/350
* Add scripts for test and coverage reports. by @fiseni in https://github.com/ardalis/Specification/pull/351
* Dummy PR to test the triggers. by @fiseni in https://github.com/ardalis/Specification/pull/352
* Update the action status badge in Readme. by @fiseni in https://github.com/ardalis/Specification/pull/353
* Add more samples. by @fiseni in https://github.com/ardalis/Specification/pull/354
* Add script for SQL Local DB setup. by @fiseni in https://github.com/ardalis/Specification/pull/357
* Refactor and improve integration test fixtures. by @fiseni in https://github.com/ardalis/Specification/pull/360
* Talpers/delete range by spec by @thorstenalpers in https://github.com/ardalis/Specification/pull/369
* Add messages to obsolete specs for clarity by @Rowe2ryWA in https://github.com/ardalis/Specification/pull/373
* Update CONTRIBUTING.md by @sadukie in https://github.com/ardalis/Specification/pull/374
* Publish version 8.0 by @fiseni in https://github.com/ardalis/Specification/pull/355

## New Contributors
* @thorstenalpers made their first contribution in https://github.com/ardalis/Specification/pull/369
* @Rowe2ryWA made their first contribution in https://github.com/ardalis/Specification/pull/373
* @sadukie made their first contribution in https://github.com/ardalis/Specification/pull/374

**Full Changelog**: https://github.com/ardalis/Specification/compare/v7.0...v8.0


## v7.x

### v7.0  (v7.0)
<https://github.com/ardalis/Specification/releases/tag/v7.0>

## What's Changed
* Patch 2 by @davidhenley in https://github.com/ardalis/Specification/pull/283
* Fix `Just the Docs` link in docs home page by @snowfrogdev in https://github.com/ardalis/Specification/pull/293
* Update url path by @ta1H3n in https://github.com/ardalis/Specification/pull/303
* Implement SelectMany support by @amdavie in https://github.com/ardalis/Specification/pull/320
* Add two methods for consuming repositories in scenarios where repositories could be longer lived (e.g. Blazor component Injections) by @jasonsummers in https://github.com/ardalis/Specification/pull/289
* Added support for AsAsyncEnumerable by @nkz-soft in https://github.com/ardalis/Specification/pull/316
* Lamadelrae/doc faq ef versions by @Lamadelrae in https://github.com/ardalis/Specification/pull/324
* Updated projects, drop support for old TFMs. by @fiseni in https://github.com/ardalis/Specification/pull/326
* Update the search feature to generate parameterized query. by @fiseni in https://github.com/ardalis/Specification/pull/327
* Add support for extending default evaluator list by @fiseni in https://github.com/ardalis/Specification/pull/328
* Ardalis/cleanup by @ardalis in https://github.com/ardalis/Specification/pull/332

## New Contributors
* @snowfrogdev made their first contribution in https://github.com/ardalis/Specification/pull/293
* @ta1H3n made their first contribution in https://github.com/ardalis/Specification/pull/303
* @amdavie made their first contribution in https://github.com/ardalis/Specification/pull/320
* @jasonsummers made their first contribution in https://github.com/ardalis/Specification/pull/289
* @nkz-soft made their first contribution in https://github.com/ardalis/Specification/pull/316
* @Lamadelrae made their first contribution in https://github.com/ardalis/Specification/pull/324

**Full Changelog**: https://github.com/ardalis/Specification/compare/v6.1.0...v7.0


## v6.x

### v6.1.0  (v6.1.0)
<https://github.com/ardalis/Specification/releases/tag/v6.1.0>

Added AddRangeAsync. https://github.com/ardalis/Specification/pull/239
Added dictionary as arbitrary state for specifications. https://github.com/ardalis/Specification/pull/248
Added support for updating specifications. https://github.com/ardalis/Specification/pull/251
Updated base specifications as non-abstract classes. https://github.com/ardalis/Specification/pull/252
Update the infrastructure for single result specifications. https://github.com/ardalis/Specification/pull/272
Added UpdateRangeAsync. https://github.com/ardalis/Specification/pull/272
Add WithSpecification overload for specifications with Select. https://github.com/ardalis/Specification/pull/273

### v6.0.1  (v6.0.1)
<https://github.com/ardalis/Specification/releases/tag/v6.0.1>

Updated XML docs filename

### v6.0.0  (v6.0.0)
<https://github.com/ardalis/Specification/releases/tag/v6.0.0>

Release 6.0.0

See README.md
      Breaking changes
      Improve in-memory evaluation performance. #182. Breaking Changes: The specification state for Where, Order, and Search expressions is stored in separate types.
      Remove Paginate builder action. Breaking Change (It was marked as obsolete since version 4). Issue #189

      Other updates
      Add support for AnyAsync in the base repository. #180
      Add SQL Like implementation for the in-memory evaluator. #150
      Add support for IgnoreQueryFilters. #159
      Return Task&lt;int&gt; from SaveChangesAsync. #174
      Add support for condition in the specification builder methods. #143
      Improve Include evaluation performance by implementing caching (opt-in feature). Issue #187
      Implement infrastructure for specification validators. Issue #111
      Adding XML Comments #224

## What's Changed
* update build workflows by @halilkocaoz in https://github.com/ardalis/Specification/pull/151
* Add dependency injection for Repository to Getting Started guide by @davidhenley in https://github.com/ardalis/Specification/pull/157
* Docs builder extensions #162 by @vittorelli in https://github.com/ardalis/Specification/pull/163
* ICacheSpecificationBuilder by @vittorelli in https://github.com/ardalis/Specification/pull/161
* Adding some xml comments by @mustafaelshobaky in https://github.com/ardalis/Specification/pull/168
* Add SQL LIKE implementation for the in-memory evaluator. by @fiseni in https://github.com/ardalis/Specification/pull/153
* Implemented AnyAsync method by @gabrielheming in https://github.com/ardalis/Specification/pull/183
* Refactor specification expressions by @devbased in https://github.com/ardalis/Specification/pull/185
* Implement Include/ThenInclude as adapter by @devbased in https://github.com/ardalis/Specification/pull/188
* Restore ISingleResultSpecificationOfT by @vittorelli in https://github.com/ardalis/Specification/pull/196
* Remove paginate by @MarkusGnigler in https://github.com/ardalis/Specification/pull/195
* Update docs for use with DbContext and Repository Pattern by @KyleMcMaster in https://github.com/ardalis/Specification/pull/204
* Return Task<int> from SaveChangesAsync. by @fiseni in https://github.com/ardalis/Specification/pull/190
* Implement IgnoreQueryFilters feature. by @fiseni in https://github.com/ardalis/Specification/pull/191
* Add support for condition in the specification builder methods. by @fiseni in https://github.com/ardalis/Specification/pull/192
* Implement specification validators. by @fiseni in https://github.com/ardalis/Specification/pull/193
* Update dependencies for all projects. by @fiseni in https://github.com/ardalis/Specification/pull/210
* use DbSet Update method in repo Update method by @ardalis in https://github.com/ardalis/Specification/pull/211
* Ardalis/doc ignorequeryfilters by @ardalis in https://github.com/ardalis/Specification/pull/212
* Update specification with in memory collections documentation by @KyleMcMaster in https://github.com/ardalis/Specification/pull/213
* Move the selector checks to the evaluators. by @fiseni in https://github.com/ardalis/Specification/pull/214
* Docs: AsNoTracking by @ardalis in https://github.com/ardalis/Specification/pull/216
* Update quick-start-guide.md by @KyleMcMaster in https://github.com/ardalis/Specification/pull/218
* Update abstract repository documentation by @KyleMcMaster in https://github.com/ardalis/Specification/pull/220
* Update abstract repository documentation by @KyleMcMaster in https://github.com/ardalis/Specification/pull/221
* Update Evaluate documentation by @KyleMcMaster in https://github.com/ardalis/Specification/pull/222
* Fix preprocessor directives in EF Core project to account for net6.0 by @fiseni in https://github.com/ardalis/Specification/pull/219
* Fix nullability warnings. by @fiseni in https://github.com/ardalis/Specification/pull/223
* Adding and Applying EditorConfig by @ardalis in https://github.com/ardalis/Specification/pull/226

## New Contributors
* @halilkocaoz made their first contribution in https://github.com/ardalis/Specification/pull/151
* @davidhenley made their first contribution in https://github.com/ardalis/Specification/pull/157
* @vittorelli made their first contribution in https://github.com/ardalis/Specification/pull/163
* @gabrielheming made their first contribution in https://github.com/ardalis/Specification/pull/183
* @devbased made their first contribution in https://github.com/ardalis/Specification/pull/185
* @MarkusGnigler made their first contribution in https://github.com/ardalis/Specification/pull/195
* @KyleMcMaster made their first contribution in https://github.com/ardalis/Specification/pull/204

**Full Changelog**: https://github.com/ardalis/Specification/compare/v5.2.0...v6.0.0


## v1.x

### 1.2.0  (1.2.0)
<https://github.com/ardalis/Specification/releases/tag/1.2.0>

Added SpecificationEvaluator and some unit tests to verify behavior.
