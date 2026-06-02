# Ardalis.Result v10.1.0 — API surface

_Generated from the XML doc comments shipped inside these NuGet packages:_

- `Ardalis.Result` v10.1.0 (`github-source`)
- `Ardalis.Result.AspNetCore` v10.1.0 (`github-source`)
- `Ardalis.Result.FluentValidation` v10.1.0 (`github-source`)

_Do not edit by hand — rerun `scripts/update_skill.py`._

Use **only** the members listed here when writing code against Ardalis.Result v10.1.0. If a member you want isn't here, it doesn't exist in this version and you must pick another approach.

## package `Ardalis.Result` v10.1.0

### namespace `Ardalis.Result`

#### `ErrorList`

**Properties:**

- `ErrorMessages`
- `null`


#### `IResult`


#### `IResultExtensions`

**Methods:**

- `IsConflict(IResult)`
- `IsCreated(IResult)`
- `IsCriticalError(IResult)`
- `IsError(IResult)`
- `IsForbidden(IResult)`
- `IsInvalid(IResult)`
- `IsNoContent(IResult)`
- `IsNotFound(IResult)`
- `IsOk(IResult)`
- `IsUnauthorized(IResult)`
- `IsUnavailable(IResult)`


#### `PagedInfo`

**Methods:**

- `SetPageNumber(long)`
- `SetPageSize(long)`
- `SetTotalPages(long)`
- `SetTotalRecords(long)`

**Properties:**

- `PageNumber`
- `PageSize`
- `TotalPages`
- `TotalRecords`


#### `PagedResult<T>`

**Properties:**

- `PagedInfo`


#### `Result`

**Methods:**

- `#ctor`
- `Conflict`
- `Conflict(string[])`
- `Created<T>(T)`
- `Created<T>(T, string)`
- `CriticalError(string[])`
- `Error(ErrorList)`
- `Error(string)`
- `Forbidden`
- `Forbidden(string[])`
- `Invalid(IEnumerable<ValidationError>)`
- `Invalid(ValidationError)`
- `Invalid(ValidationError[])`
- `NoContent`
- `NotFound`
- `NotFound(string[])`
- `Success`
- `Success<T>(T)`
- `Success<T>(T, string)`
- `SuccessWithMessage(string)`
- `Unauthorized`
- `Unauthorized(string[])`
- `Unavailable(string[])`


#### `ResultExtensions`

**Methods:**

- `Bind<T1, T2>(Result<TSource>, Func<TSource, Result<TDestination>>)`
- `Bind<T>(Result, Func<Result, Result<TDestination>>)`
- `Bind<T>(Result<TSource>, Func<Result<TSource>, Result>)`
- `BindAsync(Result, Func<Result, Task<Result>>)`
- `BindAsync(Task<Result>, Func<Result, Task<Result>>)`
- `BindAsync<T1, T2>(Result<TSource>, Func<TSource, Task<Result<TDestination>>>)`
- `BindAsync<T1, T2>(Result<TSource>, Func<TSource, Task<Result>>)`
- `BindAsync<T1, T2>(Task<Result<TSource>>, Func<TSource, Result<TDestination>>)`
- `BindAsync<T1, T2>(Task<Result<TSource>>, Func<TSource, Task<Result<TDestination>>>)`
- `BindAsync<T>(Result<TSource>, Func<TSource, Task<Result>>)`
- `BindAsync<T>(Task<Result<TSource>>, Func<TSource, Task<Result>>)`
- `BindAsync<T>(Task<Result>, Func<Result, Task<Result<TDestination>>>)`
- `Map<T1, T2>(Result<TSource>, Func<TSource, TDestination>)`
- `Map<T>(Result, Func<TDestination>)`
- `Map<T>(Result<TSource>)`
- `MapAsync<T1, T2>(Result<TSource>, Func<TSource, Task<TDestination>>)`
- `MapAsync<T1, T2>(Task<Result<TSource>>, Func<TSource, TDestination>)`
- `MapAsync<T1, T2>(Task<Result<TSource>>, Func<TSource, Task<TDestination>>)`
- `MapAsync<T>(Result, Func<Task<TDestination>>)`
- `MapAsync<T>(Task<Result>, Func<TDestination>)`
- `MapAsync<T>(Task<Result>, Func<Task<TDestination>>)`


#### `Result<T>`

**Methods:**

- `#ctor(T)`
- `#ctor<T>(Result)`
- `#ctor<T>(T)`
- `Conflict`
- `Conflict(string[])`
- `Created(T)`
- `Created(T, string)`
- `CriticalError(string[])`
- `Error(ErrorList)`
- `Error(string)`
- `Forbidden`
- `Forbidden(string[])`
- `GetValue`
- `Invalid(IEnumerable<ValidationError>)`
- `Invalid(ValidationError)`
- `Invalid(ValidationError[])`
- `NoContent`
- `NotFound`
- `NotFound(string[])`
- `Success(T)`
- `Success(T, string)`
- `T(Result<T>)`
- `ToPagedResult(PagedInfo)`
- `Unauthorized`
- `Unauthorized(string[])`
- `Unavailable(string[])`

**Properties:**

- `CorrelationId`
- `Errors`
- `Location`
- `Status`
- `SuccessMessage`
- `ValidationErrors`
- `Value`

**Fields:**

- `IsSuccess`
- `ValueType`



## package `Ardalis.Result.AspNetCore` v10.1.0

### namespace `Ardalis.Result.AspNetCore`

#### `ExpectedFailuresAttribute`

**Properties:**

- `ResultStatuses`


#### `MvcOptionsExtensions`

**Methods:**

- `AddDefaultResultConvention(MvcOptions)`
- `AddResultConvention(MvcOptions, Action<ResultStatusMap>)`


#### `ResultStatusMap`

**Methods:**

- `AddDefaultMap`
- `ContainsKey(ResultStatus)`
- `For(ResultStatus, HttpStatusCode)`
- `For(ResultStatus, HttpStatusCode, Action<ResultStatusOptions>)`
- `Remove(ResultStatus)`

**Fields:**

- `Keys`


#### `ResultStatusOptions`

**Methods:**

- `For(string, HttpStatusCode)`
- `GetStatusCode(string)`
- `With(Type, Func<ControllerBase, IResult, object>)`
- `With<T>(Func<ControllerBase, IResult, T>)`


#### `TranslateResultToActionResultAttribute`

**Methods:**

- `OnActionExecuted(ActionExecutedContext)`



## package `Ardalis.Result.FluentValidation` v10.1.0

### namespace `Ardalis.Result.FluentValidation`

#### `FluentValidationResultExtensions`

**Methods:**

- `AsErrors(ValidationResult)`
- `FromSeverity(Severity)`
