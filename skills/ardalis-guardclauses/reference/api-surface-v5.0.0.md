# Ardalis.GuardClauses v5.0.0 — API surface

_Generated from the XML doc comments shipped in `Ardalis.GuardClauses.5.0.0.nupkg` (target framework `netstandard2.0`). Do not edit by hand — rerun `scripts/update_skill.py`._

Use **only** the members listed here when writing code against Ardalis.GuardClauses v5.x. If a member you want isn't here, it doesn't exist in this major and you must pick another approach.

## namespace `Ardalis.GuardClauses`

### `Guard`

An entry point to a set of Guard Clauses defined as extension methods on IGuardClause.

**Properties:**

- `Against`
  - An entry point to a set of Guard Clauses.


### `GuardClauseExtensions`

A collection of common guard clauses, implemented as extensions.

**Methods:**

- `AgainstExpression<T>(IGuardClause, Func<T1,bool>, T1, string)`
  - Throws an `ArgumentException` if func evaluates to false for given input
  - `func`
  - `guardClause`
  - `input`
  - `message`
  - `<T>`
  - returns: input if the func evaluates to true
- `AgainstExpression<T>(IGuardClause, Func<T1,bool>, T1, string, string)`
  - Throws an `ArgumentException` if func evaluates to false for given input
  - `func`
  - `guardClause`
  - `input`
  - `message`
  - `paramName`: The name of the parameter that is invalid
  - `<T>`
  - returns: input if the func evaluates to true
- `AgainstExpressionAsync<T>(IGuardClause, Func<T1,Tasks.Task<bool>>, T1, string)`
  - Throws an `ArgumentException` if func evaluates to false for given input
  - `func`
  - `guardClause`
  - `input`
  - `message`
  - `<T>`
  - returns: input if the func evaluates to true
- `Default<T>(IGuardClause, T1, string, string, Func<Exception>)`
  - Throws an `ArgumentException` or a custom `Exception` if input is default for that type.
  - `guardClause`
  - `input`
  - `parameterName`
  - `message`: Optional. Custom error message
  - `exceptionCreator`
  - returns: input if the value is not default for that type.
- `EnumOutOfRange<T>(IGuardClause, T1, string, string, Func<Exception>)`
  - Throws an `InvalidEnumArgumentException` or a custom `Exception` if input is not a valid enum value.
  - `guardClause`
  - `input`
  - `parameterName`
  - `message`: Optional. Custom error message
  - `exceptionCreator`
  - `<T>`
  - returns: input if the value is not out of range.
- `EnumOutOfRange<T>(IGuardClause, int, string, string, Func<Exception>)`
  - Throws an `InvalidEnumArgumentException` or a custom `Exception` if input is not a valid enum value.
  - `guardClause`
  - `input`
  - `parameterName`
  - `message`: Optional. Custom error message
  - `exceptionCreator`
  - `<T>`
  - returns: input if the value is not out of range.
- `Expression<T>(IGuardClause, Func<T1,bool>, T1, string, string, Func<Exception>)`
  - Validates the input using the specified func and throws an `ArgumentException` or a custom `Exception` if it evaluates to true.
The func should return true to indicate an invalid or undesirable state of the input.
If func returns true, an `ArgumentException` or a custom `Exception` is thrown, signifying that the input is invalid.
  - `guardClause`: The guard clause instance.
  - `func`: The function that evaluates the input. It should return true if the input is considered invalid or in a negative state.
  - `input`: The input to evaluate.
  - `message`: The message to include in the exception if the input is invalid.
  - `parameterName`: The name of the parameter to include in the thrown exception, captured automatically from the input expression.
  - `exceptionCreator`
  - `<T>`: The type of the input parameter.
  - returns: The input if the func evaluates to false, indicating a valid state.
- `ExpressionAsync<T>(IGuardClause, Func<T1,Tasks.Task<bool>>, T1, string, string, Func<Exception>)`
  - Validates the func asynchronously and throws an `ArgumentException` or a custom `Exception` if it evaluates to false for given input
The func should return true to indicate an invalid or undesirable state.
If func returns true, indicating that the input is invalid, an `ArgumentException` or a custom `Exception` is thrown.
  - `func`: The function that evaluates the input. It should return true if the input is considered invalid or in a negative state.
  - `guardClause`: The guard clause instance.
  - `input`: The input to evaluate.
  - `message`: The message to include in the exception if the input is invalid.
  - `parameterName`: The name of the parameter to include in the thrown exception, captured automatically from the input expression.
  - `exceptionCreator`
  - `<T>`: The type of the input parameter.
  - returns: input if the func evaluates to true
- `InvalidFormat(IGuardClause, string, string, string, string, Func<Exception>)`
  - Throws an `ArgumentException` or a custom `Exception` if input doesn't match the regexPattern.
  - `guardClause`
  - `input`
  - `parameterName`
  - `regexPattern`
  - `message`: Optional. Custom error message
  - `exceptionCreator`
- `InvalidInput<T>(IGuardClause, T1, string, Func<T1,bool>, string, Func<Exception>)`
  - Throws an `ArgumentException` or a custom `Exception` if input doesn't satisfy the predicate function.
  - `guardClause`
  - `input`
  - `parameterName`
  - `predicate`
  - `message`: Optional. Custom error message
  - `exceptionCreator`
  - `<T>`
- `InvalidInputAsync<T>(IGuardClause, T1, string, Func<T1,Tasks.Task<bool>>, string, Func<Exception>)`
  - Throws an `ArgumentException` or a custom `Exception` if input doesn't satisfy the predicate function.
  - `guardClause`
  - `input`
  - `parameterName`
  - `predicate`
  - `message`: Optional. Custom error message
  - `exceptionCreator`
  - `<T>`
- `LengthOutOfRange(IGuardClause, string, int, int, string, string, Func<Exception>)`
  - Throws an `ArgumentException` or a custom `Exception` if string input length is out of range.
  - `guardClause`
  - `input`
  - `minLength`
  - `maxLength`
  - `parameterName`
  - `message`: Optional. Custom error message
  - `exceptionCreator`
  - returns: input if the value is not negative.
- `Negative(IGuardClause, TimeSpan, string, string, Func<Exception>)`
  - Throws an `ArgumentException` or a custom `Exception` if input is negative.
  - `guardClause`
  - `input`
  - `parameterName`
  - `message`: Optional. Custom error message
  - `exceptionCreator`
  - returns: input if the value is not negative.
- `Negative(IGuardClause, decimal, string, string, Func<Exception>)`
  - Throws an `ArgumentException` or a custom `Exception` if input is negative.
  - `guardClause`
  - `input`
  - `parameterName`
  - `message`: Optional. Custom error message
  - `exceptionCreator`
  - returns: input if the value is not negative.
- `Negative(IGuardClause, double, string, string, Func<Exception>)`
  - Throws an `ArgumentException` or a custom `Exception` if input is negative.
  - `guardClause`
  - `input`
  - `parameterName`
  - `message`: Optional. Custom error message
  - `exceptionCreator`
  - returns: input if the value is not negative.
- `Negative(IGuardClause, float, string, string, Func<Exception>)`
  - Throws an `ArgumentException` or a custom `Exception` if input is negative.
  - `guardClause`
  - `input`
  - `parameterName`
  - `message`: Optional. Custom error message
  - `exceptionCreator`
  - returns: input if the value is not negative.
- `Negative(IGuardClause, int, string, string, Func<Exception>)`
  - Throws an `ArgumentException` or a custom `Exception` if input is negative.
  - `guardClause`
  - `input`
  - `parameterName`
  - `message`: Optional. Custom error message
  - `exceptionCreator`
  - returns: input if the value is not negative.
- `Negative(IGuardClause, long, string, string, Func<Exception>)`
  - Throws an `ArgumentException` or a custom `Exception` if input is negative.
  - `guardClause`
  - `input`
  - `parameterName`
  - `message`: Optional. Custom error message
  - `exceptionCreator`
  - returns: input if the value is not negative.
- `Negative<T>(IGuardClause, T1, string, string, Func<Exception>)`
  - Throws an `ArgumentException` or a custom `Exception` if input is negative.
  - `guardClause`
  - `input`
  - `parameterName`
  - `message`: Optional. Custom error message
  - `exceptionCreator`
  - returns: input if the value is not negative.
- `NegativeOrZero(IGuardClause, TimeSpan, string, string, Func<Exception>)`
  - Throws an `ArgumentException` or a custom `Exception` if input is negative or zero.
  - `guardClause`
  - `input`
  - `parameterName`
  - `message`: Optional. Custom error message
  - `exceptionCreator`
  - returns: input if the value is not negative or zero.
- `NegativeOrZero(IGuardClause, decimal, string, string, Func<Exception>)`
  - Throws an `ArgumentException` or a custom `Exception` if input is negative or zero.
  - `guardClause`
  - `input`
  - `parameterName`
  - `message`: Optional. Custom error message
  - `exceptionCreator`
  - returns: input if the value is not negative or zero.
- `NegativeOrZero(IGuardClause, double, string, string, Func<Exception>)`
  - Throws an `ArgumentException` or a custom `Exception` if input is negative or zero.
  - `guardClause`
  - `input`
  - `parameterName`
  - `message`: Optional. Custom error message
  - `exceptionCreator`
  - returns: input if the value is not negative or zero.
- `NegativeOrZero(IGuardClause, float, string, string, Func<Exception>)`
  - Throws an `ArgumentException` or a custom `Exception` if input is negative or zero.
  - `guardClause`
  - `input`
  - `parameterName`
  - `message`: Optional. Custom error message
  - `exceptionCreator`
  - returns: input if the value is not negative or zero.
- `NegativeOrZero(IGuardClause, int, string, string, Func<Exception>)`
  - Throws an `ArgumentException` or a custom `Exception` if input is negative or zero.
  - `guardClause`
  - `input`
  - `parameterName`
  - `message`: Optional. Custom error message
  - `exceptionCreator`
  - returns: input if the value is not negative or zero.
- `NegativeOrZero(IGuardClause, long, string, string, Func<Exception>)`
  - Throws an `ArgumentException` or a custom `Exception` if input is negative or zero.
  - `guardClause`
  - `input`
  - `parameterName`
  - `message`: Optional. Custom error message
  - `exceptionCreator`
  - returns: input if the value is not negative or zero.
- `NegativeOrZero<T>(IGuardClause, T1, string, string, Func<Exception>)`
  - Throws an `ArgumentException` or a custom `Exception` if input is negative or zero.
  - `guardClause`
  - `input`
  - `parameterName`
  - `message`: Optional. Custom error message
  - `exceptionCreator`
  - `<T>`
  - returns: input if the value is not negative or zero.
- `NotFound<T1, T2>(IGuardClause, T1, T2, string, Func<Exception>)`
  - Throws an `NotFoundException` or a custom `Exception` if input with key is not found.
  - `guardClause`
  - `key`
  - `input`
  - `parameterName`
  - `exceptionCreator`
  - `<T>`
  - `<TKey>`
  - returns: input if the value is not null.
- `NotFound<T>(IGuardClause, string, T1, string, Func<Exception>)`
  - Throws an `NotFoundException` or a custom `Exception` if input with key is not found.
  - `guardClause`
  - `key`
  - `input`
  - `parameterName`
  - `exceptionCreator`
  - `<T>`
  - returns: input if the value is not null.
- `Null<T>(IGuardClause, Nullable<T1>, string, string, Func<Exception>)`
  - Throws an `ArgumentNullException` or a custom `Exception` if input is null.
  - `guardClause`
  - `input`
  - `parameterName`
  - `message`: Optional. Custom error message
  - `exceptionCreator`
  - `<T>`: Must be a value type.
  - returns: input if the value is not null.
- `Null<T>(IGuardClause, T1, string, string, Func<Exception>)`
  - Throws an `ArgumentNullException` or a custom `Exception` if input is null.
  - `guardClause`
  - `input`
  - `parameterName`
  - `message`: Optional. Custom error message
  - `exceptionCreator`
  - `<T>`
  - returns: input if the value is not null.
- `NullOrEmpty(IGuardClause, Nullable<Guid>, string, string, Func<Exception>)`
  - Throws an `ArgumentNullException` or a custom `Exception`if input is null.
Throws an `ArgumentException` or a custom `Exception` if input is an empty guid.
  - `guardClause`
  - `input`
  - `parameterName`
  - `message`: Optional. Custom error message
  - `exceptionCreator`
  - returns: input if the value is not an empty guid or null.
- `NullOrEmpty(IGuardClause, string, string, string, Func<Exception>)`
  - Throws an `ArgumentNullException` or a custom `Exception` if input is null.
Throws an `ArgumentException` or a custom `Exception` if input is an empty string.
  - `guardClause`
  - `input`
  - `parameterName`
  - `message`: Optional. Custom error message
  - `exceptionCreator`
  - returns: input if the value is not an empty string or null.
- `NullOrEmpty<T>(IGuardClause, Generic.IEnumerable<T1>, string, string, Func<Exception>)`
  - Throws an `ArgumentNullException` or a custom `Exception` if input is null.
Throws an `ArgumentException` or a custom `Exception` if input is an empty enumerable.
  - `guardClause`
  - `input`
  - `parameterName`
  - `message`: Optional. Custom error message
  - `exceptionCreator`
  - returns: input if the value is not an empty enumerable or null.
- `NullOrInvalidInput<T>(IGuardClause, T1, string, Func<T1,bool>, string, Func<Exception>)`
  - Throws an `ArgumentNullException` or a custom `Exception` if input is null
Throws an `ArgumentException` or a custom `Exception` if input doesn't satisfy the predicate function.
  - `guardClause`
  - `input`
  - `parameterName`
  - `predicate`
  - `message`: Optional. Custom error message
  - `exceptionCreator`
  - `<T>`
- `NullOrOutOfRange<T>(IGuardClause, Nullable<T1>, string, T1, T1, string, Func<Exception>)`
  - Throws an `ArgumentNullException` or a custom `Exception` if input is null.
Throws an `ArgumentOutOfRangeException` or a custom `Exception` if input is less than rangeFrom or greater than rangeTo.
  - `guardClause`
  - `input`
  - `parameterName`
  - `rangeFrom`
  - `rangeTo`
  - `message`: Optional. Custom error message
  - `exceptionCreator`
  - returns: input if the value is not not null or out of range.
- `NullOrOutOfRange<T>(IGuardClause, T1, string, T1, T1, string, Func<Exception>)`
  - Throws an `ArgumentNullException` or a custom `Exception` if input is null.
Throws an `ArgumentOutOfRangeException` or a custom `Exception` if input is less than rangeFrom or greater than rangeTo.
  - `guardClause`
  - `input`
  - `parameterName`
  - `rangeFrom`
  - `rangeTo`
  - `message`: Optional. Custom error message
  - `exceptionCreator`
  - returns: input if the value is not not null or out of range.
- `NullOrOutOfRangeInternal<T>(IGuardClause, T1, string, T1, T1, string, Func<Exception>)`
- `NullOrOutOfSQLDateRange(IGuardClause, Nullable<DateTime>, string, string, Func<Exception>)`
  - Throws an `ArgumentNullException` or a custom `Exception` if input is null.
Throws an `ArgumentOutOfRangeException` or a custom `Exception` if input is not in the range of valid SqlDateTime values.
  - `guardClause`
  - `input`
  - `parameterName`
  - `message`: Optional. Custom error message
  - `exceptionCreator`
  - returns: input if the value is in the range of valid SqlDateTime values.
- `NullOrWhiteSpace(IGuardClause, string, string, string, Func<Exception>)`
  - Throws an `ArgumentNullException` or a custom `Exception` if input is null.
Throws an `ArgumentException` or a custom `Exception` if input is an empty or white space string.
  - `guardClause`
  - `input`
  - `parameterName`
  - `message`: Optional. Custom error message
  - `exceptionCreator`
  - returns: input if the value is not an empty or whitespace string.
- `OutOfRange<T>(IGuardClause, Generic.IEnumerable<T1>, string, T1, T1, string, Func<Exception>)`
  - Throws an `ArgumentOutOfRangeException` or a custom `Exception` if
any input's item is less than rangeFrom or greater than rangeTo.
  - `guardClause`
  - `input`
  - `parameterName`
  - `rangeFrom`
  - `rangeTo`
  - `message`: Optional. Custom error message
  - `exceptionCreator`
  - returns: input if any item is not out of range.
- `OutOfRange<T>(IGuardClause, T1, string, T1, T1, string, Func<Exception>)`
  - Throws an `ArgumentOutOfRangeException` or a custom `Exception` if input is less than rangeFrom or greater than rangeTo.
  - `guardClause`
  - `input`
  - `parameterName`
  - `rangeFrom`
  - `rangeTo`
  - `message`: Optional. Custom error message
  - `exceptionCreator`
  - returns: input if the value is not out of range.
- `OutOfSQLDateRange(IGuardClause, DateTime, string, string, Func<Exception>)`
  - Throws an `ArgumentOutOfRangeException` or a custom `Exception` if input is not in the range of valid SqlDateTime values.
  - `guardClause`
  - `input`
  - `parameterName`
  - `message`: Optional. Custom error message
  - `exceptionCreator`
  - returns: input if the value is in the range of valid SqlDateTime values.
- `StringTooLong(IGuardClause, string, int, string, string, Func<Exception>)`
  - Throws an `ArgumentException` or a custom `Exception` if string input is too long.
  - `guardClause`
  - `input`
  - `maxLength`
  - `parameterName`
  - `message`: Optional. Custom error message
  - `exceptionCreator`
  - returns: input if the value is not negative.
- `StringTooShort(IGuardClause, string, int, string, string, Func<Exception>)`
  - Throws an `ArgumentException` or a custom `Exception` if string input is too short.
  - `guardClause`
  - `input`
  - `minLength`
  - `parameterName`
  - `message`: Optional. Custom error message
  - `exceptionCreator`
  - returns: input if the value is not negative.
- `Zero(IGuardClause, TimeSpan, string, Func<Exception>)`
  - Throws an `ArgumentException` or a custom `Exception` if input is zero.
  - `guardClause`
  - `input`
  - `parameterName`
  - `exceptionCreator`
  - returns: input if the value is not zero.
- `Zero(IGuardClause, decimal, string, string, Func<Exception>)`
  - Throws an `ArgumentException` or a custom `Exception` if input is zero.
  - `guardClause`
  - `input`
  - `parameterName`
  - `message`: Optional. Custom error message
  - `exceptionCreator`
  - returns: input if the value is not zero.
- `Zero(IGuardClause, double, string, string, Func<Exception>)`
  - Throws an `ArgumentException` or a custom `Exception` if input is zero.
  - `guardClause`
  - `input`
  - `parameterName`
  - `message`: Optional. Custom error message
  - `exceptionCreator`
  - returns: input if the value is not zero.
- `Zero(IGuardClause, float, string, string, Func<Exception>)`
  - Throws an `ArgumentException` or a custom `Exception` if input is zero.
  - `guardClause`
  - `input`
  - `parameterName`
  - `message`: Optional. Custom error message
  - `exceptionCreator`
  - returns: input if the value is not zero.
- `Zero(IGuardClause, int, string, string, Func<Exception>)`
  - Throws an `ArgumentException` or a custom `Exception` if input is zero.
  - `guardClause`
  - `input`
  - `parameterName`
  - `message`: Optional. Custom error message
  - `exceptionCreator`
  - returns: input if the value is not zero.
- `Zero(IGuardClause, long, string, string, Func<Exception>)`
  - Throws an `ArgumentException` or a custom `Exception` if input is zero.
  - `guardClause`
  - `input`
  - `parameterName`
  - `message`: Optional. Custom error message
  - `exceptionCreator`
  - returns: input if the value is not zero.
- `Zero<T>(IGuardClause, T1, string, string, Func<Exception>)`
  - Throws an `ArgumentException` or a custom `Exception` if input is zero.
  - `guardClause`
  - `input`
  - `parameterName`
  - `message`: Optional. Custom error message
  - `exceptionCreator`
  - returns: input if the value is not zero.


### `IGuardClause`

Simple interface to provide a generic mechanism to build guard clause extension methods from.


### `NotFoundException`

Represents error that occurs if a queried object by a particular key is null (not found).

**Methods:**

- `#ctor(string, string)`
  - Initializes a new instance of the NotFoundException class with a specified name of the queried object and its key.
  - `objectName`: Name of the queried object.
  - `key`: The value by which the object is queried.
- `#ctor(string, string, Exception)`
  - Initializes a new instance of the NotFoundException class with a specified name of the queried object, its key,
and the exception that is the cause of this exception.
  - `objectName`: Name of the queried object.
  - `key`: The value by which the object is queried.
  - `innerException`: The exception that is the cause of the current exception.


### `ValidatedNotNullAttribute`

Add to methods that check input for null and throw if the input is null.


## namespace `JetBrains.Annotations`

### `AspAttributeRoutingAttribute`

Indicates that the marked attribute is used for attribute routing in ASP.NET.


### `AspDefaultRouteValuesAttribute`

Indicates that the marked method parameter contains default route values of routing convention for ASP.NET.


### `AspMinimalApiDeclarationAttribute`

Indicates that the marked method declares an ASP.NET Minimal API endpoint.


### `AspMinimalApiGroupAttribute`

Indicates that the marked method declares an ASP.NET Minimal API endpoints group.


### `AspMinimalApiHandlerAttribute`

Indicates that the marked parameter contains an ASP.NET Minimal API endpoint handler.


### `AspMvcActionAttribute`

ASP.NET MVC attribute. If applied to a parameter, indicates that the parameter
is an MVC action. If applied to a method, the MVC action name is calculated
implicitly from the context. Use this attribute for custom wrappers similar to
`System.Web.Mvc.Html.ChildActionExtensions.RenderAction(HtmlHelper, String)`.


### `AspMvcActionSelectorAttribute`

ASP.NET MVC attribute. When applied to a parameter of an attribute,
indicates that this parameter is an MVC action name.


### `AspMvcAreaAttribute`

ASP.NET MVC attribute. Indicates that the marked parameter is an MVC area.
Use this attribute for custom wrappers similar to
`System.Web.Mvc.Html.ChildActionExtensions.RenderAction(HtmlHelper, String)`.


### `AspMvcControllerAttribute`

ASP.NET MVC attribute. If applied to a parameter, indicates that the parameter is
an MVC controller. If applied to a method, the MVC controller name is calculated
implicitly from the context. Use this attribute for custom wrappers similar to
`System.Web.Mvc.Html.ChildActionExtensions.RenderAction(HtmlHelper, String, String)`.


### `AspMvcDisplayTemplateAttribute`

ASP.NET MVC attribute. Indicates that a parameter is an MVC display template.
Use this attribute for custom wrappers similar to
`System.Web.Mvc.Html.DisplayExtensions.DisplayForModel(HtmlHelper, String)`.


### `AspMvcEditorTemplateAttribute`

ASP.NET MVC attribute. Indicates that the marked parameter is an MVC editor template.
Use this attribute for custom wrappers similar to
`System.Web.Mvc.Html.EditorExtensions.EditorForModel(HtmlHelper, String)`.


### `AspMvcMasterAttribute`

ASP.NET MVC attribute. Indicates that the marked parameter is an MVC Master. Use this attribute
for custom wrappers similar to `System.Web.Mvc.Controller.View(String, String)`.


### `AspMvcModelTypeAttribute`

ASP.NET MVC attribute. Indicates that the marked parameter is an MVC model type. Use this attribute
for custom wrappers similar to `System.Web.Mvc.Controller.View(String, Object)`.


### `AspMvcPartialViewAttribute`

ASP.NET MVC attribute. If applied to a parameter, indicates that the parameter is an MVC
partial view. If applied to a method, the MVC partial view name is calculated implicitly
from the context. Use this attribute for custom wrappers similar to
`System.Web.Mvc.Html.RenderPartialExtensions.RenderPartial(HtmlHelper, String)`.


### `AspMvcSuppressViewErrorAttribute`

ASP.NET MVC attribute. Allows disabling inspections for MVC views within a class or a method.


### `AspMvcTemplateAttribute`

ASP.NET MVC attribute. Indicates that the marked parameter is an MVC template.
Use this attribute for custom wrappers similar to
`System.ComponentModel.DataAnnotations.UIHintAttribute(System.String)`.


### `AspMvcViewAttribute`

ASP.NET MVC attribute. If applied to a parameter, indicates that the parameter
is an MVC view component. If applied to a method, the MVC view name is calculated implicitly
from the context. Use this attribute for custom wrappers similar to
`System.Web.Mvc.Controller.View(Object)`.


### `AspMvcViewComponentAttribute`

ASP.NET MVC attribute. If applied to a parameter, indicates that the parameter
is an MVC view component name.


### `AspMvcViewComponentViewAttribute`

ASP.NET MVC attribute. If applied to a parameter, indicates that the parameter
is an MVC view component view. If applied to a method, the MVC view component view name is default.


### `AspRouteConventionAttribute`

Indicates that the marked method declares routing convention for ASP.NET.


### `AspRouteOrderAttribute`

Indicates that the marked parameter or property contains routing order provided by ASP.NET routing attribute.


### `AspRouteValuesConstraintsAttribute`

Indicates that the marked method parameter contains constraints on route values of routing convention for ASP.NET.


### `AspRouteVerbsAttribute`

Indicates that the marked parameter or property contains HTTP verbs provided by ASP.NET routing attribute.


### `AssertionConditionAttribute`

Indicates the condition parameter of the assertion method. The method itself should be
marked by the `AssertionMethodAttribute` attribute. The mandatory argument of
the attribute is the assertion type.


### `AssertionConditionType`

Specifies the assertion type. If the assertion method argument satisfies the condition,
then the execution continues. Otherwise, execution is assumed to be halted.

**Fields:**

- `IS_FALSE`
  - Marked parameter should be evaluated to false.
- `IS_NOT_NULL`
  - Marked parameter should be evaluated to not null value.
- `IS_NULL`
  - Marked parameter should be evaluated to null value.
- `IS_TRUE`
  - Marked parameter should be evaluated to true.


### `AssertionMethodAttribute`

Indicates that the marked method is an assertion method, i.e. it halts the control flow if
one of the conditions is satisfied. To set the condition, mark one of the parameters with
`AssertionConditionAttribute` attribute.


### `BaseTypeRequiredAttribute`

When applied to a target attribute, specifies a requirement for any type marked
with the target attribute to implement or inherit the specific type or types.


### `CanBeNullAttribute`

Indicates that the value of the marked element could be `null` sometimes,
so checking for `null` is required before its usage.


### `CannotApplyEqualityOperatorAttribute`

Indicates that the value of the marked type (or its derivatives)
cannot be compared using '==' or '!=' operators and `Equals()`
should be used instead. However, using '==' or '!=' for comparison
with `null` is always permitted.


### `CodeTemplateAttribute`

Defines the code search template using the Structural Search and Replace syntax.
It allows you to find and, if necessary, replace blocks of code that match a specific pattern.
Search and replace patterns consist of a textual part and placeholders.
Textural part must contain only identifiers allowed in the target language and will be matched exactly (white spaces, tabulation characters, and line breaks are ignored).
Placeholders allow matching variable parts of the target code blocks.
A placeholder has the following format: $placeholder_name$- where placeholder_name is an arbitrary identifier.


Available placeholders:

- $this$ - expression of containing type

- $thisType$ - containing type

- $member$ - current member placeholder

- $qualifier$ - this placeholder is available in the replace pattern and can be used to insert a qualifier expression matched by the $member$ placeholder.
(Note that if $qualifier$ placeholder is used, then $member$ placeholder will match only qualified references)

- $expression$ - expression of any type

- $identifier$ - identifier placeholder

- $args$ - any number of arguments

- $arg$ - single argument

- $arg1$ ... $arg10$ - single argument

- $stmts$ - any number of statements

- $stmt$ - single statement

- $stmt1$ ... $stmt10$ - single statement

- $name{Expression, 'Namespace.FooType'}$ - expression with 'Namespace.FooType' type

- $expression{'Namespace.FooType'}$ - expression with 'Namespace.FooType' type

- $name{Type, 'Namespace.FooType'}$ - 'Namespace.FooType' type

- $type{'Namespace.FooType'}$ - 'Namespace.FooType' type

- $statement{1,2}$ - 1 or 2 statements


Note that you can also define your own placeholders of the supported types and specify arguments for each placeholder type.
This can be done using the following format: $name{type, arguments}$. Where 'name' - is the name of your placeholder,
'type' - is the type of your placeholder (one of the following: Expression, Type, Identifier, Statement, Argument, Member),
'arguments' - arguments list for your placeholder. Each placeholder type supports its own arguments, check examples below for more details.
The placeholder type may be omitted and determined from the placeholder name, if the name has one of the following prefixes:

- expr, expression - expression placeholder, e.g. $exprPlaceholder{}$, $expressionFoo{}$

- arg, argument - argument placeholder, e.g. $argPlaceholder{}$, $argumentFoo{}$

- ident, identifier - identifier placeholder, e.g. $identPlaceholder{}$, $identifierFoo{}$

- stmt, statement - statement placeholder, e.g. $stmtPlaceholder{}$, $statementFoo{}$

- type - type placeholder, e.g. $typePlaceholder{}$, $typeFoo{}$

- member - member placeholder, e.g. $memberPlaceholder{}$, $memberFoo{}$


Expression placeholder arguments:

- expressionType - string value in single quotes, specifies full type name to match (empty string by default)

- exactType - boolean value, specifies if expression should have exact type match (false by default)
Examples:

- $myExpr{Expression, 'Namespace.FooType', true}$ - defines expression placeholder, matching expressions of the 'Namespace.FooType' type with exact matching.

- $myExpr{Expression, 'Namespace.FooType'}$ - defines expression placeholder, matching expressions of the 'Namespace.FooType' type or expressions which can be implicitly converted to 'Namespace.FooType'.

- $myExpr{Expression}$ - defines expression placeholder, matching expressions of any type.

- $exprFoo{'Namespace.FooType', true}$ - defines expression placeholder, matching expressions of the 'Namespace.FooType' type with exact matching.


Type placeholder arguments:

- type - string value in single quotes, specifies full type name to match (empty string by default)

- exactType - boolean value, specifies if expression should have exact type match (false by default)
Examples:

- $myType{Type, 'Namespace.FooType', true}$ - defines type placeholder, matching 'Namespace.FooType' types with exact matching.

- $myType{Type, 'Namespace.FooType'}$ - defines type placeholder, matching 'Namespace.FooType' types or types, which can be implicitly converted to 'Namespace.FooType'.

- $myType{Type}$ - defines type placeholder, matching any type.

- $typeFoo{'Namespace.FooType', true}$ - defines types placeholder, matching 'Namespace.FooType' types with exact matching.


Identifier placeholder arguments:

- nameRegex - string value in single quotes, specifies regex to use for matching (empty string by default)

- nameRegexCaseSensitive - boolean value, specifies if name regex is case sensitive (true by default)

- type - string value in single quotes, specifies full type name to match (empty string by default)

- exactType - boolean value, specifies if expression should have exact type match (false by default)
Examples:

- $myIdentifier{Identifier, 'my.*', false, 'Namespace.FooType', true}$ - defines identifier placeholder, matching identifiers (ignoring case) starting with 'my' prefix with 'Namespace.FooType' type.

- $myIdentifier{Identifier, 'my.*', true, 'Namespace.FooType', true}$ - defines identifier placeholder, matching identifiers (case sensitively) starting with 'my' prefix with 'Namespace.FooType' type.

- $identFoo{'my.*'}$ - defines identifier placeholder, matching identifiers (case sensitively) starting with 'my' prefix.


Statement placeholder arguments:

- minimalOccurrences - minimal number of statements to match (-1 by default)

- maximalOccurrences - maximal number of statements to match (-1 by default)
Examples:

- $myStmt{Statement, 1, 2}$ - defines statement placeholder, matching 1 or 2 statements.

- $myStmt{Statement}$ - defines statement placeholder, matching any number of statements.

- $stmtFoo{1, 2}$ - defines statement placeholder, matching 1 or 2 statements.


Argument placeholder arguments:

- minimalOccurrences - minimal number of arguments to match (-1 by default)

- maximalOccurrences - maximal number of arguments to match (-1 by default)
Examples:

- $myArg{Argument, 1, 2}$ - defines argument placeholder, matching 1 or 2 arguments.

- $myArg{Argument}$ - defines argument placeholder, matching any number of arguments.

- $argFoo{1, 2}$ - defines argument placeholder, matching 1 or 2 arguments.


Member placeholder arguments:

- docId - string value in single quotes, specifies XML documentation id of the member to match (empty by default)
Examples:

- $myMember{Member, 'M:System.String.IsNullOrEmpty(System.String)'}$ - defines member placeholder, matching 'IsNullOrEmpty' member of the 'System.String' type.

- $memberFoo{'M:System.String.IsNullOrEmpty(System.String)'}$ - defines member placeholder, matching 'IsNullOrEmpty' member of the 'System.String' type.


For more information please refer to the Structural Search and Replace article.

**Properties:**

- `FormatAfterReplace`
  - Apply code formatting after code replacement.
- `MatchSimilarConstructs`
  - Whether similar code blocks should be matched.
- `Message`
  - Message to show when the search pattern was found.
You can also prepend the message text with "Error:", "Warning:", "Suggestion:" or "Hint:" prefix to specify the pattern severity.
Code patterns with replace templates produce suggestions by default.
However, if a replace template is not provided, then warning severity will be used.
- `ReplaceMessage`
  - The replace message to show in the light bulb.
- `ReplaceTemplate`
  - Structural search replace pattern to use in code template replacement.
- `SearchTemplate`
  - Structural search pattern to use in the code template.
The pattern includes a textual part, which must contain only identifiers allowed in the target language,
and placeholders, which allow matching variable parts of the target code blocks.
- `ShortenReferences`
  - Automatically insert namespace import directives or remove qualifiers that become redundant after the template is applied.
- `SuppressionKey`
  - The string to use as a suppression key.
By default the following suppression key is used 'CodeTemplate_SomeType_SomeMember',
where 'SomeType' and 'SomeMember' are names of the associated containing type and member to which this attribute is applied.


### `CollectionAccessAttribute`

Indicates how a method, constructor invocation, or property access
over a collection type affects the contents of the collection.
When applied to a return value of a method, indicates if the returned collection
is created exclusively for the caller (CollectionAccessType.UpdatedContent) or
can be read/updated from outside (CollectionAccessType.Read | CollectionAccessType.UpdatedContent)
Use `CollectionAccessType` to specify the access type.


### `CollectionAccessType`

Provides a value for the `CollectionAccessAttribute` to define
how the collection method invocation affects the contents of the collection.

**Fields:**

- `ModifyExistingContent`
  - Method can change content of the collection but does not add new elements.
- `None`
  - Method does not use or modify content of the collection.
- `Read`
  - Method only reads content of the collection but does not modify it.
- `UpdatedContent`
  - Method can add new elements to the collection.


### `ContractAnnotationAttribute`

Describes dependence between method input and output.


### `ImplicitUseKindFlags`

Specifies the details of an implicitly used symbol when it is marked
with `MeansImplicitUseAttribute` or `UsedImplicitlyAttribute`.

**Fields:**

- `Access`
  - Only entity marked with attribute considered used.
- `Assign`
  - Indicates implicit assignment to a member.
- `InstantiatedNoFixedConstructorSignature`
  - Indicates implicit instantiation of a type.
- `InstantiatedWithFixedConstructorSignature`
  - Indicates implicit instantiation of a type with fixed constructor signature.
That means any unused constructor parameters won't be reported as such.


### `ImplicitUseTargetFlags`

Specifies what is considered to be used implicitly when marked
with `MeansImplicitUseAttribute` or `UsedImplicitlyAttribute`.

**Fields:**

- `Members`
  - Members of the type marked with the attribute are considered used.
- `WithInheritors`
  - Inherited entities are considered used.
- `WithMembers`
  - Entity marked with the attribute and all its members considered used.


### `InjectedLanguage`

Language of injected code fragment inside marked by the `LanguageInjectionAttribute` string literal.


### `InstantHandleAttribute`

Tells the code analysis engine if the parameter is completely handled when the invoked method is on stack.
If the parameter is a delegate, indicates that the delegate can only be invoked during method execution
(the delegate can be invoked zero or multiple times, but not stored to some field and invoked later,
when the containing method is no longer on the execution stack).
If the parameter is an enumerable, indicates that it is enumerated while the method is executed.
If `RequireAwait` is true, the attribute will only take effect if the method invocation is located under the 'await' expression.

**Properties:**

- `RequireAwait`
  - Require the method invocation to be used under the 'await' expression for this attribute to take effect on the code analysis engine.
Can be used for delegate/enumerable parameters of 'async' methods.


### `InvokerParameterNameAttribute`

Indicates that the function argument should be a string literal and match
one of the parameters of the caller function. This annotation is used for parameters
like 'string paramName' parameter of the `ArgumentNullException` constructor.


### `ItemCanBeNullAttribute`

Can be applied to symbols of types derived from IEnumerable as well as to symbols of Task
and Lazy classes to indicate that the value of a collection item, of the Task.Result property
or of the Lazy.Value property can be null.


### `ItemNotNullAttribute`

Can be applied to symbols of types derived from IEnumerable as well as to symbols of Task
and Lazy classes to indicate that the value of a collection item, of the Task.Result property
or of the Lazy.Value property can never be null.


### `LanguageInjectionAttribute`

Indicates that the marked parameter, field, or property is accepting a string literal
containing code fragments in a specified language.

**Properties:**

- `InjectedLanguage`
  - Specifies a language of the injected code fragment.
- `InjectedLanguageName`
  - Specifies a language name of the injected code fragment.
- `Prefix`
  - Specifies a string that "precedes" the injected string literal.
- `Suffix`
  - Specifies a string that "follows" the injected string literal.


### `LinqTunnelAttribute`

Indicates that the method is a pure LINQ method, with postponed enumeration (like Enumerable.Select,
.Where). This annotation allows inference of [InstantHandle] annotation for parameters
of delegate type by analyzing LINQ method chains.


### `LocalizationRequiredAttribute`

Indicates whether the marked element should be localized.


### `MacroAttribute`

Allows specifying a macro for a parameter of a `SourceTemplateAttribute`.

**Properties:**

- `Editable`
  - Allows specifying which occurrence of the target parameter becomes editable when the template is deployed.
  - remarks: If the target parameter is used several times in the template, only one occurrence becomes editable;
other occurrences are changed synchronously. To specify the zero-based index of the editable occurrence,
use values >= 0. To make the parameter non-editable when the template is expanded, use -1.
- `Expression`
  - Allows specifying a macro that will be executed for a `SourceTemplateAttribute`
parameter when the template is expanded.
- `Target`
  - Identifies the target parameter of a `SourceTemplateAttribute` if the
`MacroAttribute` is applied on a template method.


### `MeansImplicitUseAttribute`

Can be applied to attributes, type parameters, and parameters of a type assignable from `Type` .
When applied to an attribute, the decorated attribute behaves the same as `UsedImplicitlyAttribute`.
When applied to a type parameter or to a parameter of type `Type`,
indicates that the corresponding type is used implicitly.


### `MeansTestSubjectAttribute`

Signifies a generic argument as the test subject for a test class.


### `MustUseReturnValueAttribute`

Indicates that the return value of the method invocation must be used.


### `NoEnumerationAttribute`

Indicates that IEnumerable passed as a parameter is not enumerated.
Use this annotation to suppress the 'Possible multiple enumeration of IEnumerable' inspection.


### `NoReorderAttribute`

Prevents the Member Reordering feature from tossing members of the marked class.


### `NonNegativeValueAttribute`

Indicates that the integral value never falls below zero.


### `NotNullAttribute`

Indicates that the value of the marked element can never be `null`.


### `NotifyPropertyChangedInvocatorAttribute`

Indicates that the method is contained in a type that implements
`System.ComponentModel.INotifyPropertyChanged` interface and this method
is used to notify that some property value changed.


### `PathReferenceAttribute`

Indicates that a parameter is a path to a file or a folder within a web project.
Path can be relative or absolute, starting from web root (~).


### `ProvidesContextAttribute`

Indicates the type member or parameter of some type that should be used instead of all other ways
to get the value of that type. This annotation is useful when you have some "context" value evaluated
and stored somewhere, meaning that all other ways to get this value must be consolidated with the existing one.


### `PublicAPIAttribute`

This attribute is intended to mark publicly available APIs,
which should not be removed and so is treated as used.


### `PureAttribute`

Indicates that a method does not make any observable state changes.
The same as `System.Diagnostics.Contracts.PureAttribute`.


### `RazorSectionAttribute`

Razor attribute. Indicates that the marked parameter or method is a Razor section.
Use this attribute for custom wrappers similar to
`System.Web.WebPages.WebPageBase.RenderSection(String)`.


### `RegexPatternAttribute`

Indicates that the marked parameter, field, or property is a regular expression pattern.


### `RequireStaticDelegateAttribute`

This annotation allows to enforce allocation-less usage patterns of delegates for performance-critical APIs.
When this annotation is applied to the parameter of delegate type, the IDE checks the input argument of this parameter:
* When a lambda expression or anonymous method is passed as an argument, the IDE verifies that the passed closure
has no captures of the containing local variables and the compiler is able to cache the delegate instance
to avoid heap allocations. Otherwise a warning is produced.
* The IDE warns when the method name or local function name is passed as an argument as this always results
in heap allocation of the delegate instance.


### `RouteParameterConstraintAttribute`

Indicates that the marked type is custom route parameter constraint,
which is registered in the application's Startup with the name `ConstraintName`.


### `RouteTemplateAttribute`

Indicates that the marked parameter, field, or property is a route template.


### `SourceTemplateAttribute`

An extension method marked with this attribute is processed by code completion
as a 'Source Template'. When the extension method is completed over some expression, its source code
is automatically expanded like a template at the call site.


### `StringFormatMethodAttribute`

Indicates that the marked method builds a string by the format pattern and (optional) arguments.
The parameter, which contains the format string, should be given in the constructor. The format string
should be in `Format`-like form.

**Methods:**

- `#ctor(string)`
  - `formatParameterName`: Specifies which parameter of an annotated method should be treated as the format string.


### `StructuredMessageTemplateAttribute`

Indicates that the marked parameter is a message template where placeholders are to be replaced by the following arguments
in the order in which they appear.


### `TerminatesProgramAttribute`

Indicates that the marked method unconditionally terminates control flow execution.
For example, it could unconditionally throw an exception.


### `TestSubjectAttribute`

Specifies the subject being tested by a test class or a test method.

**Methods:**

- `#ctor(Type)`
  - Initializes a new instance of the `TestSubjectAttribute` class with the specified subject type.
  - `subject`: The type of the subject being tested.

**Properties:**

- `Subject`
  - Gets the type of the subject being tested.


### `UriStringAttribute`

Indicates that the marked parameter, field, or property is an URI string.


### `UsedImplicitlyAttribute`

Indicates that the marked symbol is used implicitly (e.g. via reflection, in external library),
so this symbol will be ignored by usage-checking inspections.
You can use `ImplicitUseKindFlags` and `ImplicitUseTargetFlags`
to configure how this attribute is applied.


### `ValueProviderAttribute`

Use this annotation to specify a type that contains static or const fields
with values for the annotated property/field/parameter.
The specified type will be used to improve completion suggestions.


### `ValueRangeAttribute`

Indicates that the integral value falls into the specified interval.
It's allowed to specify multiple non-intersecting intervals.
Values of interval boundaries are inclusive.


### `XamlItemBindingOfItemsControlAttribute`

XAML attribute. Indicates the property of some `BindingBase`-derived type, that
is used to bind some item of an `ItemsControl`-derived type. This annotation will
enable the `DataContext` type resolve for XAML bindings for such properties.


### `XamlItemStyleOfItemsControlAttribute`

XAML attribute. Indicates the property of some `Style`-derived type that
is used to style items of an `ItemsControl`-derived type. This annotation will
enable the `DataContext` type resolve for XAML bindings for such properties.


### `XamlItemsControlAttribute`

XAML attribute. Indicates the type that has an `ItemsSource` property and should be treated
as an `ItemsControl`-derived type, to enable inner items `DataContext` type resolution.


### `XamlOneWayBindingModeByDefaultAttribute`

XAML attribute. Indicates that DependencyProperty has `OneWay` binding mode by default.


### `XamlTwoWayBindingModeByDefaultAttribute`

XAML attribute. Indicates that DependencyProperty has `TwoWay` binding mode by default.


## namespace `System.Runtime.CompilerServices`

### `CallerArgumentExpressionAttribute`

This a special exception for backwards compatibility.
Please upgrade your dependent package to the latest supported netN.N version rather than using netstandard2.1
