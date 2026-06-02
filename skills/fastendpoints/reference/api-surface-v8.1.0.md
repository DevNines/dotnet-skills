# FastEndpoints v8.1.0 — API surface

_Generated from the XML doc comments shipped inside these NuGet packages:_

- `FastEndpoints` v8.1.0 (`net8.0`)
- `FastEndpoints.Swagger` v8.1.0 (`net8.0`)
- `FastEndpoints.Security` v8.1.0 (`net8.0`)
- `FastEndpoints.Validation` v3.11.0 (`net6.0`)  ← independent versioning
- `FastEndpoints.Generator` v8.1.0 (`netstandard2.0`)
- `FastEndpoints.Messaging.Core` v8.1.0 (`net8.0`)
- `FastEndpoints.Messaging.Remote` v8.1.0 (`net8.0`)
- `FastEndpoints.Attributes` v8.1.0 (`net8.0`)

_Do not edit by hand — rerun `scripts/update_skill.py`._

Use **only** the members listed here when writing code against FastEndpoints v8.1.0. If a member you want isn't here, it doesn't exist in this version and you must pick another approach.

## package `FastEndpoints` v8.1.0

### namespace `FastEndpoints`

#### `BaseEndpoint`

the base class all fast endpoints inherit from

**Methods:**

- `Configure`
  - use this method to configure how the endpoint should be listening to incoming requests.


HINT: it is only called once during endpoint auto registration during app startup.
- `LetterOrDigitRegex`
  - remarks: Pattern:
`[^a-zA-Z0-9]+`
Explanation:
`○ Match a character in the set [^0-9A-Za-z] atomically at least once.`


#### `BinderContext`

binder context supplied to custom request binders.

**Methods:**

- `#ctor(Microsoft.AspNetCore.Http.HttpContext, Generic.List<FluentValidation.Results.ValidationFailure>, Json.Serialization.JsonSerializerContext, bool, Generic.IEnumerable<string>)`
  - constructor of the binder context
  - `httpContext`: the http context of the current request
  - `validationFailures`: the validation failure collection of the endpoint
  - `jsonSerializerContext`: json serializer context of the endpoint if applicable
  - `dontAutoBindForms`: whether to enable auto binding of form data
  - `bindRequiredProps`: collection of required property names
- `CreateScope`
- `Resolve(Type)`
- `Resolve(Type, string)`
- `Resolve<T>`
- `Resolve<T>(string)`
- `TryResolve(Type)`
- `TryResolve(Type, string)`
- `TryResolve<T>`
- `TryResolve<T>(string)`

**Properties:**

- `DontAutoBindForms`
  - set 'true' to disable auto binding of form data which enables uploading and reading of large files without buffering to memory/disk.
you can access the multipart sections for reading via the FormFileSectionsAsync() method.
- `HttpContext`
  - the http context of the current request
- `JsonSerializerContext`
  - if the current endpoint is configured with a json serializer context, it will be provided to the custom request binder with this property.
- `SerializerOptions`
  - the configured json serializer options of the app, which was specified at app startup.
- `UnboundRequiredProperties`
  - indicates which required properties were not bound due to missing input from the request.
- `ValidationFailures`
  - a list of validation failures for the endpoint. you can add your own validation failures for properties of the request dto using this property.


#### `BindingOptions`

request binding options

**Methods:**

- `ValueParserFor(Type, Func<Microsoft.Extensions.Primitives.StringValues,ParseResult>)`
  - add a custom value parser function for any given type which the default model binder will use to parse values when model binding request dto
properties from query/route/forms/headers/claims.
this is an alternative approach to adding a `TryParse()` function to your types that need model binding support from the abovementioned binding
sources.
once you register a parser function here for a type, any `TryParse()` method on the type will not be used for parsing.
also, these parser functions do not apply to JSON deserialization done by STJ and can be considered the equivalent to registering a custom converter
in STJ when it comes to query/route/forms/headers/claims binding sources.
  - `type`: the type of the class which this parser function will target
  - `parser`: a function that takes in a nullable object and returns a `ParseResult` as the output.
`app.UseFastEndpoints(c =>
{
c.Binding.ValueParserFor(typeof(Guid), MyParsers.GuidParser);
});

public static class MyParsers
{
public static ParseResult GuidParser(object? input)
{
Guid result;
bool success = Guid.TryParse(input?.ToString(), out result);
return new(success, result);
}
}`
- `ValueParserFor<T>(Func<Microsoft.Extensions.Primitives.StringValues,ParseResult>)`
  - add a custom value parser function for any given type which the default model binder will use to parse values when model binding request dto
properties from query/route/forms/headers/claims.
this is an alternative approach to adding a `TryParse()` function to your types that need model binding support from the abovementioned binding
sources.
once you register a parser function here for a type, any `TryParse()` method on the type will not be used for parsing.
also, these parser functions do not apply to JSON deserialization done by STJ and can be considered the equivalent to registering a custom converter
in STJ when it comes to query/route/forms/headers/claims binding sources.
  - `parser`: a function that takes in a nullable object and returns a `ParseResult` as the output.
`app.UseFastEndpoints(c =>
{
c.Binding.ValueParserFor<Guid>(MyParsers.GuidParser);
});

public static class MyParsers
{
public static ParseResult GuidParser(object? input)
{
Guid result;
bool success = Guid.TryParse(input?.ToString(), out result);
return new(success, result);
}
}`
  - `<T>`: the type of the class which this parser function will target
- `ValueParserWhen(Func<PropertyInfo,bool>, Func<object,Type,ParseResult>)`
  - override value parsers for request dto properties that match a predicate.


WARNING: might lead to weird/untraceable behavior. use at own risk!
  - `propertyMatcher`: a predicate for qualifying a property
  - `parser`: the value parser for the matched property type

**Properties:**

- `FailureMessage`
  - a function used to construct the failure message when a supplied value cannot be successfully bound to a dto property during model binding.


NOTE: this only applies to non-STJ operations. for customizing error messages of STJ binding failures, specify a
`JsonExceptionTransformer` func.
the following arguments are supplied to the function.


`Type`: the type of the property which failed to bind


`String`: the name of the property which failed to bind


`StringValues`: the value that was attempted which resulted in the failure
use these input parameters and construct your own error message string and return it from the function.
- `FormExceptionTransformer`
  - if this function is specified, any internal exceptions that are thrown by asp.net when accessing multipart form data will be caught and transformed to
validation
failures using this function. by default those exceptions are not caught and thrown out to the middleware pipeline. setting this func might come in handy
if
you need 413 responses (that arise from incoming request body size exceeding kestrel's `MaxRequestBodySize`) automatically transformed to 400 problem
details
responses.
- `JsonExceptionStatusCode`
  - this http status code will be used for all automatically sent `JsonException` responses which are built using the
`JsonExceptionTransformer`
func. defaults to 400.
- `JsonExceptionTransformer`
  - by default, all STJ `JsonException`s thrown during deserialization are automatically caught and transformed using this function.
if you'd like to disable this behavior, simply set this property to `null` or specify a function to construct a
`ValidationFailure` when STJ throws an exception due to invalid json input.


NOTE: this only applies to STJ based operations. for customizing error messages of non-STJ binding failures, specify a
`FailureMessage` func.
- `Modifier`
  - an optional action to be run after the endpoint level request binding has occured.
it is intended as a way to perform common model binding logic that applies to all endpoints/requests.
the action is passed in the following arguments:


`Object`: the request dto instance


`Type`: the type of the request dto


`BinderContext`: the request binding context


`CancellationToken`: a cancellation token


WARNING: be mindful of the performance cost of using reflection to modify the request dto object
- `ReflectionCache`
  - the central cache of request dto related reflection data.
populating this cache with source generated data will eliminate expression compilations during runtime as well as usage of
reflection based property setters, etc. see the source generator documentation on how to populate this cache with generated data.
- `UseDefaultValuesForNullableProps`
  - by default, if a dto property is nullable and an incoming parameter value is omitted while only the parameter name exists, the default value for the property
will be populated. setting `false` will prevent that from happening. only applies to non-STJ binding paths such as when binding from
route/query/claims/headers/form fields etc.
- `UsePropertyNamingPolicy`
  - specify whether to use the json property naming policy when matching incoming field names to dto property names for non-json model binding.
only applies when field names are not specified on properties with attributes such as [BindFrom(...)], [FromClaim(...)], [FromHeader(...)] etc.


#### `BindingSource`

enum for choosing which binding sources the default request binder should use


#### `CommandHandlerBase<T>`

the base class from which all `CommandHandler<T>` classes inherit from


#### `CommandHandler<T>`

inherit this base class if you'd like to manipulate validation state of the calling endpoint from within the command handler.


#### `CommandHandler<T1, T2>`

inherit this base class if you'd like to manipulate validation state of the calling endpoint from within the command handler.


#### `Config`

global configuration settings for FastEndpoints

**Properties:**

- `Binding`
  - request binding settings
- `Endpoints`
  - endpoint discovery & registration settings
- `Errors`
  - error response customization settings
- `Security`
  - security related settings
- `Serializer`
  - settings for customizing serialization behavior
- `Throttle`
  - endpoint throttling/ rate limiting settings
- `Validation`
  - endpoint validation settings
- `Versioning`
  - endpoint versioning settings


#### `EmptyRequest`

a request dto that doesn't have any properties

**Properties:**

- `Instance`
  - a cached empty request instance.


#### `EmptyResponse`

a response dto that doesn't have any properties

**Properties:**

- `Instance`
  - a cached empty response instance


#### `EndpointDefinition`

represents the configuration settings of an endpoint

**Methods:**

- `#ctor(Type, Type, Type)`
  - represents the configuration settings of an endpoint
- `AdditionalVerbs(Http[])`
  - specify extra http verbs in addition to the endpoint level verbs.
- `AdditionalVerbs(string[])`
  - specify extra http verbs in addition to the endpoint level verbs.
- `AllowAnonymous(Http[])`
  - allow unauthenticated requests to this endpoint. optionally specify a set of verbs to allow unauthenticated access with.
i.e. if the endpoint is listening to POST, PUT & PATCH and you specify AllowAnonymous(Http.POST), then only PUT & PATCH will require
authentication.
- `AllowAnonymous(string[])`
  - allow unauthenticated requests to this endpoint for a specified set of http verbs.
- `AllowFileUploads(bool)`
  - enable file uploads with multipart/form-data content type
  - `dontAutoBindFormData`: set 'true' to disable auto binding of form data which enables uploading and reading of large files without buffering to memory/disk.
you can access the multipart sections for reading via the `FormFileSectionsAsync` method.
- `AllowFormData(bool)`
  - enable form-data submissions
  - `urlEncoded`: set to true to accept `application/x-www-form-urlencoded` content instead of `multipart/form-data` content.
- `AuthSchemes(string[])`
  - specify which authentication schemes to use for authenticating requests to this endpoint


HINT: these auth schemes will be applied in addition to endpoint level auth schemes if there's any
  - `authSchemeNames`: the authentication scheme names
- `Claims(string[])`
  - allows access if the claims principal has ANY of the given claim types


HINT: these claims will be applied in addition to endpoint level claims if there's any
  - `claimTypes`: the claim types
- `ClaimsAll(string[])`
  - allows access if the claims principal has ALL the given claim types


HINT: these claims will be applied in addition to endpoint level claims if there's any
  - `claimTypes`: the claim types
- `Description(Action<Microsoft.AspNetCore.Builder.RouteHandlerBuilder>, bool)`
  - describe openapi metadata for this endpoint. optionally specify whether you want to clear the default Accepts/Produces metadata.


EXAMPLE: `b => b.Accepts<Request>("text/plain")`
  - `builder`: the route handler builder for this endpoint
  - `clearDefaults`: set to true if the defaults should be cleared
- `DontAutoSendResponse`
  - disables auto sending of responses when the endpoint handler doesn't explicitly send a response. most useful for allowing a post-processor to
handle sending of the response.
- `DontAutoTag`
  - if swagger auto tagging based on path segment is enabled, calling this method will prevent a tag from being added to this endpoint.
- `DontCatchExceptions`
  - use this only if you have your own exception catching middleware.
if this method is called in config, an automatic error response will not be sent to the client by the library.
all exceptions will be thrown, and it would be your exception catching middleware to handle them.
- `DontThrowIfValidationFails`
  - disable auto validation failure responses (400 bad request with error details) for this endpoint.


HINT: this only applies to request dto validation.
- `EnableAntiforgery`
  - enable antiforgery token verification for an endpoint
- `EndpointVersion(int, int)`
  - specify the version of this endpoint.
  - `version`: the version of this endpoint
  - `deprecateAt`: the version number starting at which this endpoint should not be included in swagger document
- `FeatureFlag<T>(string)`
  - specify a feature flag to run in order to determine if this endpoint is enabled or disabled for the current request.
  - `featureName`: optional name of the feature flag
  - `<TFlag>`: type of the feature flag
- `Group<T>`
  - if this endpoint is part of an endpoint group, specify the type of the `Group` concrete class where the common
configuration for the group is specified.
  - `<TEndpointGroup>`: the type of your `Group` concrete class
- `Idempotency(Action<IdempotencyOptions>)`
  - specify idempotency requirements for this endpoint
  - `options`: the idempotency options
- `MaxRequestBodySize(long)`
  - specify a custom maximum request body size to be set on `MaxRequestBodySize` which would apply to this particular
endpoint only. typically useful with `AllowFormData` and `AllowFileUploads`.
  - `size`
- `Metadata(object[])`
  - register metadata objects for the endpoint. these will be auto added to the endpoint metadata collection during startup.
  - `metadata`: the metadata to add to the endpoint
- `Options(Action<Microsoft.AspNetCore.Builder.RouteHandlerBuilder>)`
  - set endpoint configurations options using an endpoint builder action
  - `builder`: the builder for this endpoint
- `Permissions(string[])`
  - allows access if the claims principal has ANY of the given permissions


HINT: these permissions will be applied in addition to endpoint level permissions if there's any
  - `permissions`: the permissions
- `PermissionsAll(string[])`
  - allows access if the claims principal has ALL the given permissions


HINT: these permissions will be applied in addition to endpoint level permissions if there's any
  - `permissions`: the permissions
- `Policies(string[])`
  - specify one or more authorization policy names you have added to the middleware pipeline during app startup/ service configuration that should be
applied to this endpoint.


HINT: these policies will be applied in addition to endpoint level policies if there's any
  - `policyNames`: one or more policy names (must have been added to the pipeline on startup)
- `Policy(Action<Microsoft.AspNetCore.Authorization.AuthorizationPolicyBuilder>)`
  - specify an action for building an authorization requirement which should be added to all endpoints globally.


HINT: these global level requirements will be combined with the requirements specified at the endpoint level if there's any.
  - `policy`: th policy builder action
- `PostProcessor<T>(Order)`
  - adds global post-processor to an endpoint definition which are to be executed in addition to the ones configured at the endpoint level.
  - `order`: set to `Before` if the global post-processors should be executed before endpoint post-processors.
`After` will execute global processors after endpoint level processors
  - `<TPostProcessor>`: the post-processor to add
- `PostProcessors(Order, IGlobalPostProcessor[])`
  - adds global post-processors to an endpoint definition which are to be executed in addition to the ones configured at the endpoint level.
  - `order`: set to `Before` if the global post-processors should be executed before endpoint post-processors.
`After` will execute global processors after endpoint level processors
  - `postProcessors`: the post-processors to add
- `PostProcessors(Order, Type[])`
  - adds open-generic post-processors to the endpoint definition which are to be executed in addition to the ones configured at the endpoint level.
  - `order`: set to `Before` if the global post-processors should be executed before endpoint post-processors.
`After` will execute global processors after endpoint level processors
  - `processorTypes`: open generic post-processor types
- `PreProcessor<T>(Order)`
  - adds global pre-processor to an endpoint definition which are to be executed in addition to the ones configured at the endpoint level.
  - `order`: set to `Before` if the global pre-processors should be executed before endpoint pre-processors.
`After` will execute global processors after endpoint level processors
  - `<TPreProcessor>`: the pre-processor to add
- `PreProcessors(Order, IGlobalPreProcessor[])`
  - adds global pre-processors to an endpoint definition which are to be executed in addition to the ones configured at the endpoint level.
  - `order`: set to `Before` if the global pre-processors should be executed before endpoint pre-processors.
`After` will execute global processors after endpoint level processors
  - `preProcessors`: the pre-processors to add
- `PreProcessors(Order, Type[])`
  - adds open-generic pre-processors to the endpoint definition which are to be executed in addition to the ones configured at the endpoint level.
  - `order`: set to `Before` if the global pre-processors should be executed before endpoint pre-processors.
`After` will execute global processors after endpoint level processors
  - `processorTypes`: open generic pre-processor types
- `RequestBinder(Type)`
  - sets an open-generic request binder for the endpoint.
  - `binderType`: the open generic type of the request binder
- `ResponseCache(int, Microsoft.AspNetCore.Mvc.ResponseCacheLocation, bool, string, string[])`
  - specify response caching settings for this endpoint
  - `durationSeconds`: the duration in seconds for which the response is cached
  - `location`: the location where the data from a particular URL must be cached
  - `noStore`: specify whether the data should be stored or not
  - `varyByHeader`: the value for the Vary response header
  - `varyByQueryKeys`: the query keys to vary by
- `ResponseInterceptor(IResponseInterceptor)`
  - configure a response interceptor to be called before any SendAsync() methods are called.
if the interceptor sends a response to the client, the SendAsync() will be ignored.
  - `responseInterceptor`: the response interceptor to be configured for the endpoint
- `Roles(string[])`
  - allows access if the claims principal has ANY of the given roles


HINT: these roles will be applied in addition to endpoint level roles if there's any
  - `rolesNames`: one or more roles that has access
- `RoutePrefixOverride(string)`
  - specify an override route prefix for this endpoint if a global route prefix is enabled.
this is ignored if a global route prefix is not configured.
global prefix can be ignored by setting `string.Empty`


WARNING: setting a route prefix override globally makes the endpoint level override ineffective. i.e. RoutePrefixOverride() method call on
endpoint level will be ignored.
  - `routePrefix`: route prefix value
- `Scopes(string[])`
  - allows access if the 'scope' claim has ANY of the given scopes.


HINT: these scopes will be applied in addition to endpoint level scopes if there's any
  - `scopes`: the permissions
- `ScopesAll(string[])`
  - allows access if the 'scope' claim has ALL the given scopes.


HINT: these scopes will be applied in addition to endpoint level scopes if there's any
  - `scopes`: the permissions
- `Summary(Action<EndpointSummary>)`
  - provide a summary/description for this endpoint to be used in swagger/ openapi
  - `endpointSummary`: an action that sets values of an endpoint summary object
- `Summary(EndpointSummary)`
  - provide a summary/description for this endpoint to be used in swagger/ openapi
  - `endpointSummary`: an endpoint summary instance
- `Summary<T>(Action<EndpointSummary<T1>>)`
  - provide a summary/description for this endpoint to be used in swagger/ openapi
  - `endpointSummary`: an action that sets values of an endpoint summary object
- `Tags(string[])`
  - specify one or more string tags for this endpoint so they can be used in the exclusion filter during registration.


HINT: these tags will be applied in addition to endpoint level tags if there's any


TIP: these tags have nothing to do with swagger tags!
  - `endpointTags`: the tag values to associate with this endpoint
- `Throttle(int, double, string)`
  - rate limit requests to this endpoint based on a request http header sent by the client.
  - `hitLimit`: how many requests are allowed within the given duration
  - `durationSeconds`: the frequency in seconds where the accrued hit count should be reset
  - `headerName`: the name of the request header used to uniquely identify clients.
header name can also be configured globally using `app.UseFastEndpoints(c=> c.Throttle...)`
not specifying a header name will first look for 'X-Forwarded-For' header and if not present, will use `HttpContext.Connection.RemoteIpAddress`.
- `Validator<T>`
  - validator that should be used for this endpoint
  - `<TValidator>`: the type of the validator


#### `EndpointDiscoveryOptions`

defines how endpoint discovery and registration should be done at startup

**Properties:**

- `Assemblies`
  - an optional collection of assemblies to discover endpoints from in addition to the auto discovered ones.
if `DisableAutoDiscovery` is set to true, this must be provided.


NOTE: not applicable when using FastEndpoints.Generator package
- `AssemblyFilter`
  - an optional predicate to filter out the final collection of assemblies before scanning for endpoints.


NOTE: not applicable when using FastEndpoints.Generator package
- `DisableAutoDiscovery`
  - set to true if only the provided Assemblies should be scanned for endpoints.
if `Assemblies` is null and this is set to true, an exception will be thrown.


NOTE: not applicable when using FastEndpoints.Generator package
- `Filter`
  - a function to filter out types from auto discovery.
the function you set here will be executed for each discovered type during startup.
return 'false' from the function if you want to exclude a type from discovery.
return 'true' to include.
alternatively you can annotate the type/class with the `DontRegisterAttribute` to skip auto registration for that type.
- `IncludeAbstractValidators`
  - by default only validators inheriting `Validator<T>` are auto registered.
if you'd like to also include validators inheriting `AbstractValidator<T>`, set this to true.
- `SourceGeneratorDiscoveredTypes`
  - when using the FastEndpoints.Generator package, do .AddRange(`<AssemblyName>.DiscoveredTypes.All`) on this property,
per referenced assembly if your solution has multiple projects, or simply assign to this property if there's only one project/assembly.
doing so will use the types discovered during source generation instead of reflection based type discovery.


#### `EndpointExtensions`

**Methods:**

- `RequiresAuthorization(EndpointDefinition)`
  - determines if a given endpoint requires authorization.
- `RouteBuilderRegex`
  - remarks: Pattern:
`(@[\\w]*)`
Explanation:
`○ 1st capture group.
○ Match '@'.
○ Match a word character atomically any number of times.`


#### `EndpointFactory`

the default endpoint factory.
it creates an instance of the endpoint and injects both constructor and property dependencies.

**Methods:**

- `Create(EndpointDefinition, Microsoft.AspNetCore.Http.HttpContext)`
  - this method is called per each request.
  - `definition`: the endpoint definition
  - `ctx`: the http context for the current request


#### `EndpointOptions`

endpoint registration options

**Properties:**

- `AllowEmptyRequestDtos`
  - allows the use of empty request dtos
- `Configurator`
  - a configuration action to be performed on each endpoint definition during startup.
some of the same methods you use inside `Configure()` method are available to be called on the `EndpointDefinition` parameter.
this can be used to apply a set of common configuration settings globally to all endpoints.
i.e. apply globally applicable settings here and specify only the settings applicable to individual endpoints from within each endpoints'
`Configure()` method.
`app.UseFastEndpoints(c => c.Configurator = ep =>
{
ep.AllowAnonymous();
ep.Description(b => b.Produces<ErrorResponse>(400));
});`
- `Filter`
  - a function to filter out endpoints from auto registration.
the function you set here will be executed for each endpoint during startup.
you can inspect the EndpointSettings to check what the current endpoint is, if needed.
return 'false' from the function if you want to exclude an endpoint from registration.
return 'true' to include.
this function will execute for each endpoint that has been discovered during startup.
- `GlobalResponseModifier`
  - a global response modifier which will be executed right before any response is written to the response stream, giving you a chance to modify the
response before being sent.
the arguments for the func are:
`HttpContext : the http context of the current request/response
object? : response content which may be null`
- `GlobalResponseModifierAsync`
  - an async global response modifier function which will be executed right before any response is written to the response stream, giving you a chance to
modify the response before being sent.
the arguments for the func are:
`HttpContext : the http context of the current request/response
object? : response content which may be null`
- `NameGenerator`
  - specify a function to customize the endpoint name/swagger operation id. generate an endpoint name however you wish and return a string
from your function. all available info for name generation is supplied via the `EndpointNameGenerationContext`.
- `PrefixNameWithFirstTag`
  - set to true if you'd like to automatically prefix endpoint name (swagger operation id) with the first endpoint tag.
the generated the operation id would be in the form of: `MyTag_CreateOrderEndpoint`. this should come in handy with generating separate api clients
with nswag using the "MultipleClientsFromOperationId" setting which requires operation ids to be have a group name prefix with an underscore.
- `RoutePrefix`
  - prefix for all routes (example 'api').
- `ShortNames`
  - set to true if you'd like the endpoint names/ swagger operation ids to be just the endpoint class names instead of the full names including
namespace.


#### `EndpointSummary`

a class used for providing a textual description about an endpoint for swagger

**Methods:**

- `Response(int, string, string)`
  - add a response description that doesn't have a response dto to the swagger document
NOTE: if you use this method, the default 200 response is automatically removed, and you'd have to specify the 200 response yourself if it
applies to your endpoint.
  - `statusCode`: http status code
  - `description`: the description of the response
  - `contentType`: the media/content type of the response
- `Response<T>(int, string, string, T1)`
  - add a response description to the swagger document


NOTE: if you use this method, the default 200 response is automatically removed, and you'd have to specify the 200 response yourself if it
applies to your endpoint.
  - `statusCode`: http status code
  - `description`: the description of the response
  - `contentType`: the media/content type of the response
  - `example`: and example response dto instance
  - `<TResponse>`: the type of the response dto
- `ResponseParam<T>(Expressions.Expression<Func<T1,object>>, string)`
  - add a description for a given property of the 200 response dto
  - `property`: a member expression for specifying which property the description is for
  - `description`: the description text
- `ResponseParam<T>(int, Expressions.Expression<Func<T1,object>>, string)`
  - add a description for a given property of a given response dto
  - `statusCode`: the status code of the response you want to add the descriptions for
  - `property`: a member expression for specifying which property the description is for
  - `description`: the description text

**Properties:**

- `Description`
  - the long description of the endpoint
- `ExampleRequest`
  - an example request object to be used in swagger/ openapi.
multiple examples can be specified by setting this property multiple times or by adding to the `RequestExamples` collection.
- `Item`
  - indexer for the response descriptions
  - `statusCode`: the status code of the response you want to access
  - returns: the text description
- `Params`
  - the descriptions for endpoint parameters. you can add descriptions for route/query params and request dto properties.
what you specify here will take precedence over xml comments of dto classes (if they are also specified).
- `RequestExamples`
  - specify multiple request examples by adding to this collection.
- `ResponseExamples`
  - the response examples for each status code
- `Responses`
  - the descriptions of the different responses/ status codes an endpoint can return
- `Summary`
  - the short summary of the endpoint


#### `EndpointSummary<T>`

**Methods:**

- `RequestParam(Expressions.Expression<Func<T1,object>>, string)`
  - add a description for a request param for a given property of the request dto
  - `property`: a member expression for specifying which property the description is for
  - `description`: the description text


#### `EndpointWithMapper<T1, T2>`

use this base class for defining endpoints that only use a request dto and don't use a response dto but uses a request mapper.

**Properties:**

- `Map`
  - the entity mapper for the endpoint


HINT: entity mappers are singletons for performance reasons. do not maintain state in the mappers.


#### `EndpointWithMapping<T1, T2, T3>`

use this base class for defining endpoints that use both request and response dtos as well as require mapping to and from a domain entity.

**Methods:**

- `MapFromEntity(T3)`
  - override this method and place the logic for mapping a domain entity to a response dto
  - `e`: the domain entity to map from
- `MapFromEntityAsync(T3, CancellationToken)`
  - override this method and place the logic for mapping a domain entity to a response dto
  - `e`: the domain entity to map from
  - `ct`: a cancellation token
- `MapToEntity(T1)`
  - override this method and place the logic for mapping the request dto to the desired domain entity
  - `r`: the request dto
- `MapToEntityAsync(T1, CancellationToken)`
  - override this method and place the logic for mapping the request dto to the desired domain entity
  - `r`: the request dto to map from
  - `ct`: a cancellation token


#### `EndpointWithoutRequest`

use this base class for defining endpoints that doesn't need a request dto. usually used for routes that doesn't have any parameters.

**Methods:**

- `ExecuteAsync(CancellationToken)`
  - the handler method for the endpoint. this method is called for each request received.
  - `ct`: a cancellation token
- `ExecuteAsync(EmptyRequest, CancellationToken)`
  - override the ExecuteAsync(CancellationToken ct) method instead of using this method!
- `HandleAsync(CancellationToken)`
  - the handler method for the endpoint. this method is called for each request received.
  - `ct`: a cancellation token
- `HandleAsync(EmptyRequest, CancellationToken)`
  - override the HandleAsync(CancellationToken ct) method instead of using this method!


#### `EndpointWithoutRequest<T>`

use this base class for defining endpoints that doesn't need a request dto but return a response dto.

**Methods:**

- `ExecuteAsync(CancellationToken)`
  - the handler method for the endpoint that returns the response dto. this method is called for each request received.
  - `ct`: a cancellation token
- `ExecuteAsync(EmptyRequest, CancellationToken)`
  - override the ExecuteAsync(CancellationToken ct) method instead of using this method!
- `HandleAsync(CancellationToken)`
  - the handler method for the endpoint. this method is called for each request received.
  - `ct`: a cancellation token
- `HandleAsync(EmptyRequest, CancellationToken)`
  - override the HandleAsync(CancellationToken ct) method instead of using this method!


#### `EndpointWithoutRequest<T1, T2>`

use this base class for defining endpoints that doesn't need a request dto but return a response dto and uses a response mapper.

**Methods:**

- `SendMapped<T>(T1, int, CancellationToken)`
  - send a response by mapping the supplied entity using this endpoint's mapper's SYNC mapping method.
  - `entity`: the entity instance to map to the response
  - `statusCode`: the status code to send
  - `ct`: optional cancellation token
  - `<TEntity>`: the type of the entity supplied
- `SendMappedAsync<T>(T1, int, CancellationToken)`
  - send a response by mapping the supplied entity using this endpoint's mapper's ASYNC mapping method.
  - `entity`: the entity instance to map to the response
  - `statusCode`: the status code to send
  - `ct`: optional cancellation token
  - `<TEntity>`: the type of the entity supplied

**Properties:**

- `Map`
  - the entity mapper for the endpoint


HINT: entity mappers are singletons for performance reasons. do not maintain state in the mappers.


#### `Endpoint<T>`

use this base class for defining endpoints that only use a request dto and don't use a response dto.


#### `Endpoint<T1, T2>`

use this base class for defining endpoints that use both request and response dtos.

**Methods:**

- `AccessControl(string, Nullable<Apply>, string[])`
  - if the 'FastEndpoints.Generator' package is used, calling this method will generate a static class called '{assembly-name}.Auth.Allow'
with a const field with this keyName that has a 3 digit auto generated value (permission code). doesn't do anything without the
source
generator package installed.
  - `keyName`: the name of the constant field to generate
  - `behavior`: specify whether to add the generated permission code as a permission requirement for this endpoint.
this does the same thing as calling "Permissions(...)" method.
i.e. if this optional argument is set to `ToThisEndpoint`, then a user principal must possess this permission code
in order to be allowed access to this endpoint. you don't need to explicitly specify it via a `Permissions(...)` call, when setting the
behavior.
  - `groupNames`: optionally specify one or more groups (sets of permissions) this keyName belongs to.
for example if you want to generate a const/key called "Edit_Stock_Item" and want to assign it to an "Admin" group as well as a "Manager"
group, you'd specify it with this parameter. The generated const/key is accessible via "Allow.Admin.Edit_Stock_Item" as well as
"Allow.Manager.Edit_Stock_Item"
- `AccessControl(string, string[])`
  - if the 'FastEndpoints.Generator' package is used, calling this method will generate a static class called '{assembly-name}.Auth.Allow'
with a const field with this keyName that has a 3 digit auto generated value (permission code). doesn't do anything without the
source
generator package installed.
  - `keyName`: the name of the constant field to generate
  - `groupNames`: optionally specify one or more groups (sets of permissions) this keyName belongs to.
for example if you want to generate a const/key called "Edit_Stock_Item" and want to assign it to an "Admin" group as well as a "Manager"
group, you'd specify it with this parameter. The generated const/key is accessible via "Allow.Admin.Edit_Stock_Item" as well as
"Allow.Manager.Edit_Stock_Item"
- `AllowAnonymous(Http[])`
  - allow unauthenticated requests to this endpoint. optionally specify a set of verbs to allow unauthenticated access with.
i.e. if the endpoint is listening to POST, PUT & PATCH and you specify AllowAnonymous(Http.POST), then only PUT & PATCH will require
authentication.
- `AllowAnonymous(string[])`
  - allow unauthenticated requests to this endpoint for a specified set of http verbs.
i.e. if the endpoint is listening to POST, PUT & PATCH and you specify AllowAnonymous(Http.POST), then only PUT & PATCH will require
authentication.
- `AllowFileUploads(bool)`
  - enable file uploads with multipart/form-data content type
  - `dontAutoBindFormData`: set 'true' to disable auto binding of form data which enables uploading and reading of large files without buffering to memory/disk.
you can access the multipart sections for reading via the `FormFileSectionsAsync` method.
- `AllowFormData(bool)`
  - enable form-data submissions
  - `urlEncoded`: set to true to accept `application/x-www-form-urlencoded` content instead of `multipart/form-data` content.
- `AuthSchemes(string[])`
  - specify which authentication schemes to use for authenticating requests to this endpoint
  - `authSchemeNames`: the authentication scheme names
- `Claims(string[])`
  - allows access if the claims principal has ANY of the given claim types
  - `claimTypes`: the claim types
- `ClaimsAll(string[])`
  - allows access if the claims principal has ALL the given claim types
  - `claimTypes`: the claim types
- `Connect(string, Expressions.Expression<Func<T1,object>>)`
  - specify a CONNECT route pattern using a replacement expression.
  - `routePattern`: the words prefixed with @ will be replaced by property names of the `new` expression in the order they are specified.
the replacement words do not have to match the request dto property names.


`/invoice/{@id}`
  - `members`: `r => new { r.InvoiceID }`
- `Connect(string[])`
  - specify to listen for CONNECT requests on one or more routes.
- `CreateScope`
- `CreateTokenWith<T>(string, Action<UserPrivileges>, T1)`
  - create the access/refresh token pair response with a given refresh-token service.
  - `userId`: the id of the user for which the tokens will be generated for
  - `userPrivileges`: the user privileges to be embedded in the jwt such as roles/claims/permissions
  - `<TService>`: the type of the token service
- `Delete(string, Expressions.Expression<Func<T1,object>>)`
  - specify a DELETE route pattern using a replacement expression.
  - `routePattern`: the words prefixed with @ will be replaced by property names of the `new` expression in the order they are specified.
the replacement words do not have to match the request dto property names.


`/invoice/{@id}/soft-delete`
  - `members`: `r => new { r.InvoiceID }`
- `Delete(string[])`
  - specify to listen for DELETE requests on one or more routes.
- `Description(Action<Microsoft.AspNetCore.Builder.RouteHandlerBuilder>, bool)`
  - describe openapi metadata for this endpoint. optionally specify whether you want to clear the default Accepts/Produces metadata.


EXAMPLE: `b => b.Accepts<Request>("text/plain")`
  - `builder`: the route handler builder for this endpoint
  - `clearDefaults`: set to true if the defaults should be cleared
- `DontAutoSendResponse`
  - disables auto sending of responses when the endpoint handler doesn't explicitly send a response. most useful for allowing a post-processor to
handle sending of the response.
- `DontAutoTag`
  - if swagger auto tagging based on path segment is enabled, calling this method will prevent a tag from being added to this endpoint.
- `DontCatchExceptions`
  - use this only if you have your own exception catching middleware.
if this method is called in config, an automatic error response will not be sent to the client by the library.
all exceptions will be thrown, and it would be the responsibility of your exception catching middleware to handle them.
- `DontThrowIfValidationFails`
  - disable auto validation failure responses (400 bad request with error details) for this endpoint.


HINT: this only applies to request dto validation.
- `EnableAntiforgery`
  - enables antiforgery token verification for this endpoint
- `ExecuteAsync(T1, CancellationToken)`
  - the handler method for the endpoint that returns the response dto. this method is called for each request received.
  - `req`: the request dto
  - `ct`: a cancellation token
- `FeatureFlag<T>(string)`
  - specify a feature flag to run in order to determine if this endpoint is enabled or disabled for the current request.
  - `featureName`: optional name of the feature flag
  - `<TFlag>`: type of the feature flag
- `FormFileSectionsAsync(CancellationToken)`
  - gets a stream of nullable `FileMultipartSection`s from the incoming multipart/form-data without buffering data to memory/disk
as done with `IFormFile`s.
  - `cancellation`: optional cancellation token
- `FormMultipartSectionsAsync(CancellationToken)`
  - gets a stream of `MultipartSection`s from the incoming multipart/form-data without buffering to memory/disk.
  - `cancellation`: optional cancellation token
- `Get(string, Expressions.Expression<Func<T1,object>>)`
  - specify a GET route pattern using a replacement expression.
  - `routePattern`: the words prefixed with @ will be replaced by property names of the `new` expression in the order they are specified.
the replacement words do not have to match the request dto property names.


`/invoice/{@id}/print/{@pageNum}`
  - `members`: `r => new { r.InvoiceID, r.PageNumber }`
- `Get(string[])`
  - specify to listen for GET requests on one or more routes.
- `Group<T>`
  - if this endpoint is part of an endpoint group, specify the type of the `Group` concrete class where the common
configuration for the group is specified.


WARNING: this method can only be called after the endpoint route has been specified.
  - `<TEndpointGroup>`: the type of your `Group` concrete class
- `HandleAsync(T1, CancellationToken)`
  - the handler method for the endpoint. this method is called for each request received.
  - `req`: the request dto
  - `ct`: a cancellation token
- `Head(string, Expressions.Expression<Func<T1,object>>)`
  - specify a HEAD route pattern using a replacement expression.
  - `routePattern`: the words prefixed with @ will be replaced by property names of the `new` expression in the order they are specified.
the replacement words do not have to match the request dto property names.


`/invoice/{@id}/print/{@pageNum}`
  - `members`: `r => new { r.InvoiceID, r.PageNumber }`
- `Head(string[])`
  - specify to listen for HEAD requests on one or more routes.
- `Idempotency(Action<IdempotencyOptions>)`
  - specify idempotency requirements for this endpoint
  - `options`: the idempotency options
- `MaxRequestBodySize(long)`
  - specify a custom maximum request body size to be set on `MaxRequestBodySize` which would apply to this particular
endpoint only. typically useful with `AllowFormData` and `AllowFileUploads`.
  - `size`
- `Metadata(object[])`
  - register metadata objects for the endpoint. these will be auto added to the endpoint metadata collection during startup.
  - `metadata`
- `OnAfterHandle(T1, T2)`
  - override this method if you'd like to do something after the handler is executed.
  - `req`: the request dto
  - `res`: the response dto that was sent to the client
- `OnAfterHandleAsync(T1, T2, CancellationToken)`
  - override this method if you'd like to do something after the handler is executed.
  - `req`: the request dto
  - `res`: the response dto that was sent to the client
  - `ct`: a cancellation token
- `OnAfterValidate(T1)`
  - override this method if you'd like to do something to the request dto after it gets validated.
  - `req`: the request dto
- `OnAfterValidateAsync(T1, CancellationToken)`
  - override this method if you'd like to do something to the request dto after it gets validated.
  - `req`: the request dto
  - `ct`: a cancellation token
- `OnBeforeHandle(T1)`
  - override this method if you'd like to do something to the request dto before the handler is executed.
  - `req`: the request dto
- `OnBeforeHandleAsync(T1, CancellationToken)`
  - override this method if you'd like to do something to the request dto before the handler is executed.
  - `req`: the request dto
  - `ct`: a cancellation token
- `OnBeforeValidate(T1)`
  - override this method if you'd like to do something to the request dto before it gets validated.
  - `req`: the request dto
- `OnBeforeValidateAsync(T1, CancellationToken)`
  - override this method if you'd like to do something to the request dto before it gets validated.
  - `req`: the request dto
  - `ct`: a cancellation token
- `OnValidationFailed`
  - override this method if you'd like to do something when a validation failure occurs.
- `OnValidationFailedAsync(CancellationToken)`
  - override this method if you'd like to do something when a validation failure occurs.
  - `ct`: a cancellation token
- `Options(Action<Microsoft.AspNetCore.Builder.RouteHandlerBuilder>)`
  - set endpoint configurations options using an endpoint builder action ///
  - `builder`: the builder for this endpoint
- `Options(string, Expressions.Expression<Func<T1,object>>)`
  - specify a OPTIONS route pattern using a replacement expression.
  - `routePattern`: the words prefixed with @ will be replaced by property names of the `new` expression in the order they are specified.
the replacement words do not have to match the request dto property names.


`/invoice/{@id}`
  - `members`: `r => new { r.InvoiceID }`
- `Options(string[])`
  - specify to listen for OPTIONS requests on one or more routes.
- `Patch(string, Expressions.Expression<Func<T1,object>>)`
  - specify a PATCH route pattern using a replacement expression.
  - `routePattern`: the words prefixed with @ will be replaced by property names of the `new` expression in the order they are specified.
the replacement words do not have to match the request dto property names.


`/invoice/{@id}`
  - `members`: `r => new { r.InvoiceID }`
- `Patch(string[])`
  - specify to listen for PATCH requests on one or more routes.
- `Permissions(string[])`
  - allows access if the claims principal has ANY of the given permissions
  - `permissions`: the permissions
- `PermissionsAll(string[])`
  - allows access if the claims principal has ALL the given permissions
  - `permissions`: the permissions
- `Policies(string[])`
  - specify one or more authorization policy names you have added to the middleware pipeline during app startup/ service configuration that should be
applied to this endpoint.
  - `policyNames`: one or more policy names (must have been added to the pipeline on startup)
- `Policy(Action<Microsoft.AspNetCore.Authorization.AuthorizationPolicyBuilder>)`
  - specify an action for building an authorization requirement which applies only to this endpoint.
  - `policy`: the policy builder action
- `Post(string, Expressions.Expression<Func<T1,object>>)`
  - specify a POST route pattern using a replacement expression.
  - `routePattern`: the words prefixed with @ will be replaced by property names of the `new` expression in the order they are specified.
the replacement words do not have to match the request dto property names.


`/invoice/{@id}/page/{@pageNum}`
  - `members`: `r => new { r.InvoiceID, r.PageNumber }`
- `Post(string[])`
  - specify to listen for POST requests on one or more routes.
- `PostProcessor<T>`
  - configure a post-processor to be executed after the main handler function is done. call this method multiple times to add multiple post-processors.
processors are executed in the order they are configured in the endpoint.
  - `<TPostProcessor>`: the post-processor to add
- `PostProcessors(IPostProcessor<T1,T2>[])`
  - configure a collection of post-processors to be executed after the main handler function is done. processors are executed in the order they are defined
here.
  - `postProcessors`: the post processors to be executed
- `PreProcessor<T>`
  - configure a pre-processor to be executed before the main handler function is called. call this method multiple times to add multiple pre-processors.
processors are executed in the order they are configured in the endpoint.
  - `<TPreProcessor>`: the pre-processor to add
- `PreProcessors(IPreProcessor<T1>[])`
  - configure a collection of pre-processors to be executed before the main handler function is called. processors are executed in the order they are defined
here.
  - `preProcessors`: the pre-processors to be executed
- `ProcessorState<T>`
  - retrieve the common processor state for this endpoint.
  - `<TState>`: the type of the processor state
- `PublishAsync<T>(T1, Mode, CancellationToken)`
- `Put(string, Expressions.Expression<Func<T1,object>>)`
  - specify a PUT route pattern using a replacement expression.
  - `routePattern`: the words prefixed with @ will be replaced by property names of the `new` expression in the order they are specified.
the replacement words do not have to match the request dto property names.


`/invoice/{@id}/page/{@pageNum}`
  - `members`: `r => new { r.InvoiceID, r.PageNumber }`
- `Put(string[])`
  - specify to listen for PUT requests on one or more routes.
- `Query<T>(string, bool)`
  - get the value of a given query parameter by specifying the resulting type and query parameter name.
NOTE: an automatic validation error is sent to the client when value retrieval is not successful.
  - `paramName`: query parameter name
  - `isRequired`: set to false for disabling the automatic validation error
  - `<T>`: type of the result
  - returns: the value if retrieval is successful or null if isRequired is set to false
- `RequestBinder(IRequestBinder<T1>)`
  - configure custom model binding for this endpoint by supplying an IRequestBinder implementation.
by calling this method, you're completely bypassing the built-in model binding and taking things into your own hands for this endpoint.
  - `binder`: custom model binder implementation to use for this endpoint
- `Resolve(Type)`
- `Resolve(Type, string)`
- `Resolve<T>`
- `Resolve<T>(string)`
- `ResponseCache(int, Microsoft.AspNetCore.Mvc.ResponseCacheLocation, bool, string, string[])`
  - specify response caching settings for this endpoint
  - `durationSeconds`: the duration in seconds for which the response is cached
  - `location`: the location where the data from a particular URL must be cached
  - `noStore`: specify whether the data should be stored or not
  - `varyByHeader`: the value for the Vary response header
  - `varyByQueryKeys`: the query keys to vary by
- `ResponseInterceptor(IResponseInterceptor)`
  - configure a response interceptor to be called before the SendAsync response is sent to the browser.
this will override any globally configured interceptor. if you return a response to the browser, then
the rest of the SendAsync method will be skipped.
  - `responseInterceptor`: the response interceptor to be executed
- `Roles(string[])`
  - allows access if the claims principal has ANY of the given roles
  - `rolesNames`: one or more roles that has access
- `Route<T>(string, bool)`
  - get the value of a given route parameter by specifying the resulting type and param name.
NOTE: an automatic validation error is sent to the client when value retrieval is not successful.
  - `paramName`: route parameter name
  - `isRequired`: set to false for disabling the automatic validation error
  - `<T>`: type of the result
  - returns: the value if retrieval is successful or null if isRequired is set to false
- `RoutePrefixOverride(string)`
  - specify an override route prefix for this endpoint if a global route prefix is enabled.
this is ignored if a global route prefix is not configured.
global prefix can be ignored by setting `string.Empty`
  - `routePrefix`: route prefix value
- `Routes(string[])`
  - specify one or more route patterns this endpoint should be listening for
- `Scopes(string[])`
  - allows access if the 'scope' claim has ANY of the given scopes
  - `scopes`: the scopes
- `ScopesAll(string[])`
  - allows access if the 'scope' claim has ALL the given scopes
  - `scopes`: the scopes
- `SerializerContext<T>`
  - specify the type of the json serializer context if code generation for request/response dtos is being used.
the json serializer context will be instantiated with `SerializerOptions` from the UseFastEndpoints(...) call.
  - `<TContext>`: the type of the json serializer context for this endpoint
- `SerializerContext<T>(T1)`
  - specify the json serializer context if code generation for request/response dtos is being used by supplying your own instance.
  - `<TContext>`: the type of the json serializer context for this endpoint
- `Summary(Action<EndpointSummary<T1>>)`
  - provide a summary/description for this endpoint to be used in swagger/ openapi
  - `endpointSummary`: an action that sets values of an endpoint summary object
- `Summary(Action<EndpointSummary>)`
  - provide a summary/description for this endpoint to be used in swagger/ openapi
  - `endpointSummary`: an action that sets values of an endpoint summary object
- `Summary(EndpointSummary)`
  - provide a summary/description for this endpoint to be used in swagger/ openapi
  - `endpointSummary`: an endpoint summary instance
- `Tags(string[])`
  - specify one or more string tags for this endpoint so they can be used in the exclusion filter during registration.


HINT: these tags have nothing to do with swagger tags!
  - `endpointTags`: the tag values to associate with this endpoint
- `Throttle(int, double, string)`
  - rate limit requests to this endpoint based on a request http header sent by the client.
  - `hitLimit`: how many requests are allowed within the given duration
  - `durationSeconds`: the frequency in seconds where the accrued hit count should be reset
  - `headerName`: the name of the request header used to uniquely identify clients.
header name can also be configured globally using `app.UseFastEndpoints(c=> c.ThrottleOptions...)`
not specifying a header name will first look for 'X-Forwarded-For' header and if not present, will use `HttpContext.Connection.RemoteIpAddress`.
- `Trace(string, Expressions.Expression<Func<T1,object>>)`
  - specify a TRACE route pattern using a replacement expression.
  - `routePattern`: the words prefixed with @ will be replaced by property names of the `new` expression in the order they are specified.
the replacement words do not have to match the request dto property names.


`/invoice/{@id}`
  - `members`: `r => new { r.InvoiceID }`
- `Trace(string[])`
  - specify to listen for TRACE requests on one or more routes.
- `TryResolve(Type)`
- `TryResolve(Type, string)`
- `TryResolve<T>`
- `TryResolve<T>(string)`
- `Validator<T>`
  - specify the validator that should be used for this endpoint.


TIP: you only need to call this method if you have more than one validator for the same request dto in the solution or if you just want to be
explicit about what validator is used by the endpoint.
  - `<TValidator>`: the type of the validator
- `Verbs(Http[])`
  - specify one or more http method verbs this endpoint should be accepting requests for
- `Verbs(string[])`
  - specify one or more http method verbs this endpoint should be accepting requests for
- `Version(int, int)`
  - specify the version of this endpoint.
  - `version`: the version of this endpoint
  - `deprecateAt`: the version number starting at which this endpoint should not be included in swagger document

**Properties:**

- `BaseURL`
  - the base url of the current request
- `Config`
  - gives access to the app configuration.
- `Env`
  - gives access to the hosting environment
- `Files`
  - the files sent with the request. only populated when content-type is 'multipart/form-data'
- `Form`
  - the form sent with the request. only populated if content-type is 'application/x-www-form-urlencoded' or 'multipart/form-data'
- `HttpMethod`
  - the http method of the current request
- `Logger`
  - the logger for the current endpoint type
- `Response`
  - the response object that is serialized to the response stream.
- `ResponseStarted`
  - get or set whether the response has started. you'd only use this if you're writing to the response stream by yourself.
- `Send`
  - gives access to response sending methods for the endpoint. you can add your own custom response sending methods via extension methods targeting the
`IResponseSender` interface.
- `User`
  - the current user principal


#### `Endpoint<T1, T2, T3>`

use this base class for defining endpoints that use both request and response dtos as well as require mapping to and from a domain entity
using a seperate entity mapper.

**Methods:**

- `SendMapped<T>(T1, int, CancellationToken)`
  - send a response by mapping the supplied entity using this endpoint's mapper's SYNC mapping method.
  - `entity`: the entity instance to map to the response
  - `statusCode`: the status code to send
  - `ct`: optional cancellation token
  - `<TEntity>`: the type of the entity supplied
- `SendMappedAsync<T>(T1, int, CancellationToken)`
  - send a response by mapping the supplied entity using this endpoint's mapper's ASYNC mapping method.
  - `entity`: the entity instance to map to the response
  - `statusCode`: the status code to send
  - `ct`: optional cancellation token
  - `<TEntity>`: the type of the entity supplied

**Properties:**

- `Map`
  - the entity mapper for the endpoint


HINT: entity mappers are singletons for performance reasons. do not maintain state in the mappers.


#### `Ep`

endpoint base class picker starting point


#### `EpVersion`

represents an endpoint version

**Methods:**

- `DeprecateAt(int)`
  - specify starting at which version this endpoint should be considered deprecated.


NOTE: it would be the endpoint version to deprecate at for "release group" strategy, and the "release version" of the swagger doc when using the
"release version" strategy.
  - `version`
- `StartingRelease(int)`
  - specify the "release" number of the swagger document where this endpoint should start showing up in.
for example, if a swagger doc such as the following is defined:
`bld.Services.SwaggerDocument(
o =>
{
o.DocumentSettings = d => d.DocumentName = "Release 2";
o.ReleaseVersion = 2;
})`
this endpoint will only show up for the above doc and later if you do the following:
`Version(n).StartingRelease(2);`
  - `version`: the starting release version number of the swagger doc


#### `ErrorOptions`

error response customization settings

**Methods:**

- `UseProblemDetails(Action<ErrorOptions.ProblemDetailsConfig>)`
  - change the default error response builder to `ProblemDetails` instead of `ErrorResponse`
  - `config`: an action for configuring global settings for `ProblemDetails`

**Properties:**

- `ContentType`
  - the content-type header value for 400 error responses
- `GeneralErrorsField`
  - the general errors field name. this is the field name used for general errors when AddError() method is called without specifying a request dto
property.
- `ProducesMetadataType`
  - if this property is not null, a `IProducesResponseTypeMetadata` will automatically be added to endpoints that has a
`Validator<T>` associated with it.
if you're specifying your own `ResponseBuilder`, don't forget to set this property to the correct type of the error response dto that
your error response builder will be returning.


TIP: set this to null if you'd like to disable the auto adding of produces 400 metadata to endpoints even if they have validators associated with
them.
- `ResponseBuilder`
  - a function for transforming validation errors to an error response dto.
set it to any func that returns an object that can be serialized to json.
this function will be run everytime an error response needs to be sent to the client.
the arguments for the func will be a list of validation failures, the http context and a http status code.


HINT: if changing the default, make sure to also set `ProducesMetadataType` to the correct type of the error response dto.
- `StatusCode`
  - this http status code will be used for all automatically sent validation failure responses. defaults to 400.


#### `ErrorResponse`

the dto used to send an error response to the client

**Methods:**

- `#ctor`
  - instantiate a new error response without any errors
- `#ctor(Generic.List<FluentValidation.Results.ValidationFailure>, int)`
  - instantiate an error response with the given collection validation failures
  - `failures`: validation failures to initialize the DTO with
- `PopulateMetadata(MethodInfo, Microsoft.AspNetCore.Builder.EndpointBuilder)`

**Properties:**

- `Errors`
  - the collection of errors for the current context
- `Message`
  - the message for the error response
- `StatusCode`
  - the http status code sent to the client. default is 400.


#### `ExceptionHandlerExtensions`

extensions for global exception handling

**Methods:**

- `UseDefaultExceptionHandler(Microsoft.AspNetCore.Builder.IApplicationBuilder, Microsoft.Extensions.Logging.ILogger, bool, bool)`
  - registers the default global exception handler which will log the exceptions on the server and return a user-friendly json response to the client
when unhandled exceptions occur.
TIP: when using this exception handler, you may want to turn off the asp.net core exception middleware logging to avoid duplication like so:
`"Logging": { "LogLevel": { "Default": "Warning", "Microsoft.AspNetCore.Diagnostics.ExceptionHandlerMiddleware": "None" } }`
  - `logger`: an optional logger instance
  - `logStructuredException`: set to true if you'd like to log the error in a structured manner
  - `useGenericReason`: set to true if you don't want to expose the actual exception reason in the json response sent to the client


#### `Factory`

a factory for instantiating endpoints/event/mappers/validators/etc. for testing purposes

**Methods:**

- `AddServicesForUnitTesting(Microsoft.Extensions.DependencyInjection.IServiceCollection)`
  - adds the minimum required set of services for unit testing FE endpoints
- `AddTestServices(Microsoft.AspNetCore.Http.HttpContext, Action<Microsoft.Extensions.DependencyInjection.IServiceCollection>)`
  - register fake/mock/test services for the http context. typically only used with unit tests with the `Factory.Create()` method/>
  - `s`: an action for adding services to the `IServiceCollection`
- `Create<T>(Action<Microsoft.AspNetCore.Http.DefaultHttpContext>, object[])`
  - get an instance of an endpoint suitable for unit testing
  - `httpContext`: an action for configuring the default http context object
  - `ctorDependencies`: the dependencies of the endpoint if it has any constructor injected arguments
  - `<TEndpoint>`: the type of the endpoint to create an instance of
- `Create<T>(Microsoft.AspNetCore.Http.DefaultHttpContext, object[])`
  - get an instance of an endpoint suitable for unit testing
  - `httpContext`: a default http context object
  - `ctorDependencies`: the dependencies of the endpoint if it has any constructor injected dependencies
  - `<TEndpoint>`: the type of the endpoint to create an instance of
- `Create<T>(object[])`
  - get an instance of an endpoint suitable for unit testing
  - `ctorDependencies`: the dependencies of the endpoint if it has any constructor injected dependencies
  - `<TEndpoint>`: the type of the endpoint to create an instance of
- `CreateEvent<T>(Generic.IEnumerable<IEventHandler<T1>>, Action<Microsoft.Extensions.DependencyInjection.IServiceCollection>)`
  - get an instance of an event suitable for unit testing.
  - `handlers`: the fake/mock event handlers to register for this event
  - `s`: an optional action for adding services to the `IServiceCollection`
  - `<TEvent>`: the type of the event
- `CreateMapper<T>(Action<Microsoft.Extensions.DependencyInjection.IServiceCollection>)`
  - get an instance of a mapper that uses Resolve<T>() methods to obtain services registered in the DI container.
  - `s`: an action for adding services to the `IServiceCollection`
  - `<TMapper>`: the type of the mapper
- `CreateValidator<T>(Action<Microsoft.Extensions.DependencyInjection.IServiceCollection>)`
  - get an instance of a validator that uses Resolve<T>() methods to obtain services registered in the DI container.
  - `s`: an action for adding services to the `IServiceCollection`
  - `<TValidator>`: the type of the validator
- `RegisterTestServices(Action<Microsoft.Extensions.DependencyInjection.IServiceCollection>)`
  - register fake/mock/test services for the current test execution context.
  - `s`: an action for adding services to the `IServiceCollection`


#### `FastEndpointsSerializerContext`

**Methods:**

- `#ctor`
- `#ctor(Json.JsonSerializerOptions)`
- `GetTypeInfo(Type)`

**Properties:**

- `Default`
  - The default `JsonSerializerContext` associated with a default `JsonSerializerOptions` instance.
- `DictionaryStringListString`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `Error`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `ErrorResponse`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `GeneratedSerializerOptions`
  - The source-generated options associated with this context.
- `IEnumerableError`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `IEnumerableString`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `Int32`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `ListString`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `ProblemDetails`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `String`
  - Defines the source generated JSON serialization contract metadata for a given type.


#### `GlobalPostProcessor<T>`

inherit this class to create a global post-processor with access to the common processor state of the endpoint

**Methods:**

- `PostProcessAsync(IPostProcessorContext, CancellationToken)`
  - not intended for direct external use.
- `PostProcessAsync(IPostProcessorContext, T1, CancellationToken)`
  - implement this method to define the post-processing logic using the provided context and state.
  - `context`: the context object encapsulating all necessary information for post-processing.
  - `state`: the common processor state object, derived from the HttpContext or newly instantiated.
  - `ct`: cancellation token.
  - returns: a Task representing the asynchronous operation.


#### `GlobalPreProcessor<T>`

inherit this class to create a global pre-processor with access to the common processor state of the endpoint

**Methods:**

- `PreProcessAsync(IPreProcessorContext, CancellationToken)`
  - not intended for direct external use.
- `PreProcessAsync(IPreProcessorContext, T1, CancellationToken)`
  - this method is called with the given arguments when the pre-processor executes.
  - `context`: the context object encapsulating all necessary information for pre-processing.
  - `state`: the common processor state object
  - `ct`: cancellation token


#### `Group`

common configuration for a group of endpoints can be specified by implementing this abstract class and calling
`Configure` in the constructor.

**Methods:**

- `Configure(string, Action<EndpointDefinition>)`
  - call this method in the constructor in order to configure the endpoint group.
  - `routePrefix`: the route prefix for the group
  - `ep`: the configuration action to be performed on the `EndpointDefinition`
- `CreateScope`
- `Resolve(Type)`
- `Resolve(Type, string)`
- `Resolve<T>`
- `Resolve<T>(string)`
- `TryResolve(Type)`
- `TryResolve(Type, string)`
- `TryResolve<T>`
- `TryResolve<T>(string)`


#### `GroupAttribute<T>`

generic attribute for designating a group that an endpoint belongs. only effective when attribute based endpoint configuration is being used.


#### `HttpClientExtensions`

a set of extensions to the httpclient in order to facilitate route-less integration testing

**Methods:**

- `DELETEAsync<T1, T2, T3>(Http.HttpClient, T2, bool, bool)`
- `DELETEAsync<T1, T2>(Http.HttpClient)`
- `DELETEAsync<T1, T2>(Http.HttpClient, T2, bool, bool)`
- `DELETEAsync<T1, T2>(Http.HttpClient, string, T1, bool, bool)`
- `GETAsync<T1, T2, T3>(Http.HttpClient, T2, bool, bool)`
- `GETAsync<T1, T2>(Http.HttpClient)`
- `GETAsync<T1, T2>(Http.HttpClient, T2, bool, bool)`
- `GETAsync<T1, T2>(Http.HttpClient, string, T1, bool, bool)`
- `PATCHAsync<T1, T2, T3>(Http.HttpClient, T2, bool, bool, bool)`
- `PATCHAsync<T1, T2>(Http.HttpClient)`
- `PATCHAsync<T1, T2>(Http.HttpClient, T2, bool, bool, bool)`
- `PATCHAsync<T1, T2>(Http.HttpClient, string, T1, bool, bool, bool)`
- `POSTAsync<T1, T2, T3>(Http.HttpClient, T2, bool, bool, bool)`
- `POSTAsync<T1, T2>(Http.HttpClient)`
- `POSTAsync<T1, T2>(Http.HttpClient, T2, bool, bool, bool)`
- `POSTAsync<T1, T2>(Http.HttpClient, string, T1, bool, bool, bool)`
- `PUTAsync<T1, T2, T3>(Http.HttpClient, T2, bool, bool, bool)`
- `PUTAsync<T1, T2>(Http.HttpClient)`
- `PUTAsync<T1, T2>(Http.HttpClient, T2, bool, bool, bool)`
- `PUTAsync<T1, T2>(Http.HttpClient, string, T1, bool, bool, bool)`
- `SENDAsync<T1, T2>(Http.HttpClient, Http.HttpMethod, string, T1, bool, bool, bool)`


#### `HttpContextExtensions`

**Methods:**

- `MarkResponseStart(Microsoft.AspNetCore.Http.HttpContext)`
  - marks the current response as started so that `ResponseStarted` can return the correct result.
  - `ctx`
- `PopulateResponseHeadersFromResponseDto(Microsoft.AspNetCore.Http.HttpContext, object)`
  - adds headers to the http response by reading response dto properties decorated with the [ToHeader(...)] attribute
  - `response`: the response dto instance
- `ProcessorState<T>(Microsoft.AspNetCore.Http.HttpContext)`
  - retrieve the common processor state for the current http context.
  - `<TState>`: the type of the processor state
- `Resolve(Microsoft.AspNetCore.Http.HttpContext, Type)`
  - resolve an instance for the given type from the dependency injection container. will throw if unresolvable.
  - `typeOfService`: the type of the service to resolve
- `Resolve(Microsoft.AspNetCore.Http.HttpContext, Type, string)`
  - resolve an instance for the given type from the dependency injection container. will throw if unresolvable.
  - `typeOfService`: the type of the service to resolve
  - `keyName`: the key name to resolve a keyed service
- `Resolve<T>(Microsoft.AspNetCore.Http.HttpContext)`
  - resolve an instance for the given type from the dependency injection container. will throw if unresolvable.
  - `<TService>`: the type of the service to resolve
- `Resolve<T>(Microsoft.AspNetCore.Http.HttpContext, string)`
  - resolve an instance for the given type from the dependency injection container. will throw if unresolvable.
  - `keyName`: the key name to resolve a keyed service
  - `<TService>`: the type of the service to resolve
- `ResponseStarted(Microsoft.AspNetCore.Http.HttpContext)`
  - check if the current response has already started or not.
- `TryResolve(Microsoft.AspNetCore.Http.HttpContext, Type)`
  - try to resolve an instance for the given type from the dependency injection container. will return null if unresolvable.
  - `typeOfService`: the type of the service to resolve
- `TryResolve(Microsoft.AspNetCore.Http.HttpContext, Type, string)`
  - try to resolve an instance for the given type from the dependency injection container. will return null if unresolvable.
  - `typeOfService`: the type of the service to resolve
  - `keyName`: the key name to resolve a keyed service
- `TryResolve<T>(Microsoft.AspNetCore.Http.HttpContext)`
  - try to resolve an instance for the given type from the dependency injection container. will return null if unresolvable.
  - `<TService>`: the type of the service to resolve
- `TryResolve<T>(Microsoft.AspNetCore.Http.HttpContext, string)`
  - try to resolve an instance for the given type from the dependency injection container. will return null if unresolvable.
  - `keyName`: the key name to resolve a keyed service
  - `<TService>`: the type of the service to resolve


#### `HttpResponseExtensions`

**Methods:**

- `SendAcceptedAtAsync(Microsoft.AspNetCore.Http.HttpResponse, string, object, object, Json.Serialization.JsonSerializerContext, bool, CancellationToken)`
- `SendAcceptedAtAsync<T>(Microsoft.AspNetCore.Http.HttpResponse, object, object, Nullable<Http>, Nullable<int>, Json.Serialization.JsonSerializerContext, bool, CancellationToken)`
- `SendAsync<T>(Microsoft.AspNetCore.Http.HttpResponse, T1, int, Json.Serialization.JsonSerializerContext, CancellationToken)`
- `SendAtAsync(Microsoft.AspNetCore.Http.HttpResponse, int, string, object, bool, string, object, Json.Serialization.JsonSerializerContext, CancellationToken)`
- `SendAtAsync<T>(Microsoft.AspNetCore.Http.HttpResponse, int, object, bool, string, object, Nullable<Http>, Nullable<int>, Json.Serialization.JsonSerializerContext, CancellationToken)`
- `SendBytesAsync(Microsoft.AspNetCore.Http.HttpResponse, byte[], string, string, Nullable<DateTimeOffset>, bool, CancellationToken)`
- `SendCreatedAtAsync(Microsoft.AspNetCore.Http.HttpResponse, string, object, object, Json.Serialization.JsonSerializerContext, bool, CancellationToken)`
- `SendCreatedAtAsync<T>(Microsoft.AspNetCore.Http.HttpResponse, object, object, Nullable<Http>, Nullable<int>, Json.Serialization.JsonSerializerContext, bool, CancellationToken)`
- `SendEmptyJsonObject(Microsoft.AspNetCore.Http.HttpResponse, Json.Serialization.JsonSerializerContext, CancellationToken)`
- `SendErrorsAsync(Microsoft.AspNetCore.Http.HttpResponse, Generic.List<FluentValidation.Results.ValidationFailure>, int, Json.Serialization.JsonSerializerContext, CancellationToken)`
- `SendEventStreamAsync(Microsoft.AspNetCore.Http.HttpResponse, Generic.IAsyncEnumerable<StreamItem>, CancellationToken)`
- `SendEventStreamAsync<T>(Microsoft.AspNetCore.Http.HttpResponse, string, Generic.IAsyncEnumerable<T1>, CancellationToken)`
- `SendFileAsync(Microsoft.AspNetCore.Http.HttpResponse, FileInfo, string, Nullable<DateTimeOffset>, bool, CancellationToken)`
- `SendForbiddenAsync(Microsoft.AspNetCore.Http.HttpResponse, CancellationToken)`
- `SendHeadersAsync(Microsoft.AspNetCore.Http.HttpResponse, Action<Microsoft.AspNetCore.Http.IHeaderDictionary>, int, CancellationToken)`
- `SendNoContentAsync(Microsoft.AspNetCore.Http.HttpResponse, CancellationToken)`
- `SendNotFoundAsync(Microsoft.AspNetCore.Http.HttpResponse, CancellationToken)`
- `SendNotModifiedAsync(Microsoft.AspNetCore.Http.HttpResponse, CancellationToken)`
- `SendOkAsync(Microsoft.AspNetCore.Http.HttpResponse, CancellationToken)`
- `SendOkAsync<T>(Microsoft.AspNetCore.Http.HttpResponse, T1, Json.Serialization.JsonSerializerContext, CancellationToken)`
- `SendRedirectAsync(Microsoft.AspNetCore.Http.HttpResponse, string, bool, bool)`
- `SendResultAsync(Microsoft.AspNetCore.Http.HttpResponse, Microsoft.AspNetCore.Http.IResult)`
- `SendStatusCodeAsync(Microsoft.AspNetCore.Http.HttpResponse, int, CancellationToken)`
- `SendStreamAsync(Microsoft.AspNetCore.Http.HttpResponse, Stream, string, Nullable<long>, string, Nullable<DateTimeOffset>, bool, CancellationToken)`
- `SendStringAsync(Microsoft.AspNetCore.Http.HttpResponse, string, int, string, CancellationToken)`
- `SendUnauthorizedAsync(Microsoft.AspNetCore.Http.HttpResponse, CancellationToken)`


#### `IEndpoint`

the common interface implemented by all endpoints

**Methods:**

- `GetName<T>(Nullable<Http>, Nullable<int>, string)`
  - retrieves the name of a given endpoint by supplying its type. the name is generated using the `NameGenerator` func.
  - `verb`: the http verb, if the target is a multi-verb endpoint.
  - `routeNumber`: the route number, if the target is a multi route endpoint.
  - `tagPrefix`: tag prefix


#### `IEndpointFactory`

interface for the creation of endpoints.

**Methods:**

- `Create(EndpointDefinition, Microsoft.AspNetCore.Http.HttpContext)`
  - returns the instantiated fast endpoint from a given `EndpointDefinition` and `HttpContext`
  - `definition`: the endpoint definition for the current request
  - `ctx`: the http context of the current request


#### `IFeatureFlag`

implement this interface for creating a feature flag for an endpoint.

**Methods:**

- `IsEnabledAsync(IEndpoint)`
  - return `false` from this method to disable the endpoint during runtime.
  - `endpoint`: the endpoint instance

**Properties:**

- `Name`
  - optional name of the feature flag


#### `IGlobalPostProcessor`

interface for defining global post-processors to be executed after the main endpoint handler is done


#### `IGlobalPreProcessor`

interface for defining global pre-processors to be executed before the main endpoint handler is called


#### `IHasMapper<T>`

marker/constraint for endpoints that have a mapper generic argument

**Properties:**

- `Map`
  - the mapper property


#### `IMapper`

marker interface for entity mappers


#### `INoRequest`

marker interface for endpoint base classes without a request dto


#### `IPlainTextRequest`

implement this interface on your request dto if you need to model bind the raw content body of an incoming http request

**Properties:**

- `Content`
  - the request body content will be bound to this property


#### `IPostProcessor`

defines the interface for a post-processor that can perform asynchronous post-processing tasks after a request has been handled.

**Methods:**

- `PostProcessAsync(IPostProcessorContext, CancellationToken)`
  - asynchronously performs post-processing on the provided context.
  - `context`: the post-processor context containing request, response, and other processing details.
  - `ct`: the `CancellationToken` to observe while waiting for the task to complete.
  - returns: a `Task` that represents the asynchronous post-process operation.


#### `IPostProcessorContext`

defines the basic interface for a post-processor context, containing essential properties
to access request, response, and associated processing details.

**Methods:**

- `MarkExceptionAsHandled`
  - call this method if you're handling the captured exception (via `ExceptionDispatchInfo`) in a post-processor and the exception should not be thrown.
not calling this method will result in the captured exception being thrown after all the post-processors have run.

**Properties:**

- `ExceptionDispatchInfo`
  - gets information about any exception that was thrown during processing.
this will be null if no exception has occurred.
- `HasExceptionOccurred`
  - determines if an exception has occurred during processing.
- `HasValidationFailures`
  - determines if any validation failures have occurred during processing.
- `HttpContext`
  - gets the `HttpContext` associated with the current request and response.
- `Request`
  - gets the request object, which may be null if request binding has failed.
- `Response`
  - gets the response object, which may be null if the response is not available.
- `ValidationFailures`
  - gets a read-only collection of `ValidationFailure` that occurred during processing.


#### `IPostProcessorContext<T1, T2>`

defines the generic interface for a post-processor context with specific types for the request and response.

**Properties:**

- `FastEndpoints#IPostProcessorContext#Request`
  - explicit implementation to return the request object from the non-generic context.
- `FastEndpoints#IPostProcessorContext#Response`
  - explicit implementation to return the response object from the non-generic context.
- `Request`
  - gets the request object of the generic type TRequest,
which may be null if request binding has failed.
this hides the non-generic version from `IPostProcessorContext`.
- `Response`
  - gets the response object of the generic type TResponse,
which may be null if the response is not available. this hides the non-generic
version from `IPostProcessorContext`.


#### `IPostProcessor<T1, T2>`

defines the generic interface for a post-processor with specific types for the request and response,
enabling type-safe post-processing.

**Methods:**

- `FastEndpoints#IPostProcessor#PostProcessAsync(IPostProcessorContext, CancellationToken)`
  - explicit interface method implementation for `IPostProcessor`.
converts the non-generic context to a generic context and calls the generic PostProcessAsync method.
  - `context`: the non-generic post-processor context.
  - `ct`: the cancellation token.
  - returns: the task resulting from the asynchronous operation.
- `PostProcessAsync(IPostProcessorContext<T1,T2>, CancellationToken)`
  - asynchronously performs post-processing on the provided context with specific request and response types.
  - `context`: the post-processor context containing the typed request, response, and other processing details.
  - `ct`: the `CancellationToken` to observe while waiting for the task to complete.
  - returns: a `Task` that represents the asynchronous post-process operation.


#### `IPreProcessor`

defines the interface for a pre-processor that can perform asynchronous pre-processing tasks before a request has been handled.

**Methods:**

- `PreProcessAsync(IPreProcessorContext, CancellationToken)`
  - asynchronously performs pre-processing on the provided context.
  - `context`: the pre-processor context containing request, and other processing details.
  - `ct`: the `CancellationToken` to observe while waiting for the task to complete.
  - returns: a `Task` that represents the asynchronous pre-process operation.


#### `IPreProcessorContext`

defines the basic interface for a pre-processor context, containing essential properties to access request, and associated processing details.

**Properties:**

- `HasValidationFailures`
  - determines if any validation failures have occurred during processing.
- `HttpContext`
  - gets the `HttpContext` associated with the current request.
- `Request`
  - gets the request object. may be null if request binding has failed.
- `ValidationFailures`
  - gets a collection of `ValidationFailure` that occurred during processing.


#### `IPreProcessorContext<T>`

defines the generic interface for a pre-processor context with a specific type for the request.

**Properties:**

- `FastEndpoints#IPreProcessorContext#Request`
  - explicit implementation to return the request object from the non-generic context.
- `Request`
  - gets the request object of the generic type TRequest.
may be null if request binding has failed.


#### `IPreProcessor<T>`

defines the generic interface for a pre-processor with specific types for the request,
enabling type-safe pre-processing.

**Methods:**

- `FastEndpoints#IPreProcessor#PreProcessAsync(IPreProcessorContext, CancellationToken)`
  - explicit interface method implementation for `IPreProcessor`.
converts the non-generic context to a generic context and calls the generic PreProcessAsync method.
  - `context`: the non-generic pre-processor context.
  - `ct`: the cancellation token.
  - returns: the task resulting from the asynchronous operation.
- `PreProcessAsync(IPreProcessorContext<T1>, CancellationToken)`
  - asynchronously performs pre-processing on the provided context with a specific request type.
  - `context`: the pre-processor context containing the typed request, and other processing details.
  - `ct`: The `CancellationToken` to observe while waiting for the task to complete.
  - returns: a `Task` that represents the asynchronous pre-process operation.


#### `IProcessor`

base marker interface for pre & post processor interfaces


#### `IRequestBinder<T>`

create custom request binders by implementing this interface. by registering a custom modelbinder for an endpoint will completely disable the
built-in model binding and completely depend on your implementation of the custom binder to return a correctly populated request dto for the
endpoint.

**Methods:**

- `BindAsync(BinderContext, CancellationToken)`
  - this method will be called by the library for binding the incoming request data and return a populated request dto object.
access the incoming request data via the `RequestBinderContext` and populate a new request dto instance and return it from this method.
  - `ctx`: request binder context encapsulating the incoming http request context, a list of validation failures for the endpoint, and an
optional json serializer context.
  - `ct`: cancellation token


#### `IRequestMapper`

marker interface for request only mappers


#### `IRequestMapper<T1, T2>`

use this interface to implement a domain entity mapper for your endpoints that only has a request dto and no response dto.


HINT: entity mappers are used as singletons for performance reasons. do not maintain state in the mappers.

**Methods:**

- `ToEntity(T1)`
  - implement this method and place the logic for mapping the request dto to the desired domain entity
  - `r`: the request dto
- `ToEntityAsync(T1, CancellationToken)`
  - implement this method and place the logic for mapping the request dto to the desired domain entity
  - `r`: the request dto to map from
  - `ct`: a cancellation token
- `UpdateEntity(T1, T2)`
  - implement this method and place the logic for mapping the updated request dto to the desired domain entity
  - `r`: the request dto to update from
  - `e`: the domain entity to update
- `UpdateEntityAsync(T1, T2, CancellationToken)`
  - implement this method and place the logic for mapping the updated request dto to the desired domain entity
  - `r`: the request dto to update from
  - `e`: the domain entity to update
  - `ct`: a cancellation token


#### `IResponseInterceptor`

interface for defining a response interceptor to be executed before the main endpoint handler executes

**Methods:**

- `InterceptResponseAsync(object, int, Microsoft.AspNetCore.Http.HttpContext, Generic.IReadOnlyCollection<FluentValidation.Results.ValidationFailure>, CancellationToken)`
  - implement this method to intercept the http response with the use of SendInterceptedAsync() method.
  - `response`: the response object
  - `statusCode`
  - `ctx`: the http context of the current request
  - `failures`: the collection of validation failures for the endpoint
  - `ct`: cancellation token


#### `IResponseMapper`

marker interface for response only mappers


#### `IResponseMapper<T1, T2>`

use this interface to implement a domain entity mapper for your endpoints that only has a response dto and no request dto.


HINT: entity mappers are used as singletons for performance reasons. do not maintain state in the mappers.

**Methods:**

- `FromEntity(T2)`
  - implement this method and place the logic for mapping a domain entity to a response dto
  - `e`: the domain entity to map from
- `FromEntityAsync(T2, CancellationToken)`
  - implement this method and place the logic for mapping a domain entity to a response dto
  - `e`: the domain entity to map from
  - `ct`: a cancellation token


#### `IResponseSender`

target this interface type for creating your own custom response sending methods.

**Properties:**

- `Definition`
  - gets the endpoint definition which contains all the configuration info for the endpoint
- `HttpContext`
  - the http context of the current request
- `ValidationFailures`
  - validation failures collection for the endpoint


#### `IValidationErrors`

**Methods:**

- `AddError(FluentValidation.Results.ValidationFailure)`
  - add a `ValidationFailure` to the current collection of validation failures of the endpoint
  - `failure`: the validation failure to add
- `AddError(string, string, FluentValidation.Severity)`
  - adds a "GeneralError" to the current list of validation failures
  - `message`: the error message
  - `errorCode`: the error code associated with the error
  - `severity`: the severity of the error
- `ThrowError(FluentValidation.Results.ValidationFailure, Nullable<int>)`
  - adds a `ValidationFailure` to the validation failure collection of the endpoint and send back a 400 bad request with error details
immediately interrupting handler execution flow. i.e. execution will not continue past this call.
  - `failure`: the validation failure to add
  - `statusCode`: an optional status code to be used when building the error response
- `ThrowError(string, Nullable<int>)`
  - adds a "GeneralError" to the validation failure list and sends back a 400 bad request with error details immediately interrupting handler execution
flow. i.e. execution will not continue past this call.
  - `message`: the error message
  - `statusCode`: an optional status code to be used when building the error response
- `ThrowError(string, string, FluentValidation.Severity, Nullable<int>)`
  - adds a "GeneralError" to the validation failure list and sends back a 400 bad request with error details immediately interrupting handler execution
flow. i.e. execution will not continue past this call.
  - `message`: the error message
  - `errorCode`: the error code associated with the error
  - `severity`: the severity of the error
  - `statusCode`: an optional status code to be used when building the error response
- `ThrowIfAnyErrors(Nullable<int>)`
  - interrupt the flow of handler execution and send a 400 bad request with error details if there are any validation failures in the current request. if
there are no validation failures, execution will continue past this call.
  - `statusCode`: an optional status code to be used when building the error response

**Properties:**

- `ValidationFailed`
  - indicates if there are any validation failures for the current request
- `ValidationFailures`
  - validation failures collection for the endpoint


#### `IValidationErrors<T>`

**Methods:**

- `AddError(Expressions.Expression<Func<T1,object>>, string, string, FluentValidation.Severity)`
  - adds an error message for the specified property of the request dto
  - `property`: the property to add the error message for
  - `errorMessage`: the error message
  - `errorCode`: the error code associated with the error
  - `severity`: the severity of the error
- `ThrowError(Expressions.Expression<Func<T1,object>>, string, Nullable<int>)`
  - adds an error message for the specified property of the request dto and sends back a 400 bad request with error details immediately interrupting
handler execution flow. no execution will continue past this call.
  - `property`: the property to add the error message for
  - `errorMessage`: the error message
  - `statusCode`: an optional status code to be used when building the error response
- `ThrowError(Expressions.Expression<Func<T1,object>>, string, string, FluentValidation.Severity, Nullable<int>)`
  - adds an error message for the specified property of the request dto and sends back a 400 bad request with error details immediately interrupting
handler execution flow. no execution will continue past this call.
  - `property`: the property to add the error message for
  - `errorMessage`: the error message
  - `errorCode`: the error code associated with the error
  - `severity`: the severity of the error
  - `statusCode`: an optional status code to be used when building the error response


#### `IdempotencyConfig`

**Properties:**

- `InMemoryCacheSize`
  - the in-memory output cache storage size. default value is 1024 mb.
when this limit is exceeded, no new responses will be cached until older entries are evicted.
this setting will not be applicable if using some other cache store such as redis.
- `MaxResponseBodySize`
  - the largest cacheable size of the response body. default is set to 128 mb.
if the response body exceeds this limit, it will not be cached.
- `UseCaseSensitivePaths`
  - set to `true` if request paths are case-sensitive. default is to treat paths as case-insensitive.


#### `IdempotencyExtensions`

**Methods:**

- `AddIdempotency(Microsoft.Extensions.DependencyInjection.IServiceCollection, Action<IdempotencyConfig>)`
  - enable idempotency features
  - `cfg`: global configuration settings for idempotency middleware


#### `IdempotencyOptions`

idempotency settings for an endpoint

**Properties:**

- `AddHeaderToResponse`
  - by default, the idempotency header will be automatically added to the response headers collection. set `false` to prevent that from happening.
- `AdditionalHeaders`
  - any additional headers that should participate in the generation of the cache-key.
see the source/definition for the list of default additional headers.
- `CacheDuration`
  - determines how long the cached responses will remain in the cache store before being evicted.
defaults to 10 minutes.
- `HeaderName`
  - the header name that will contain the idempotency key. defaults to `Idempotency-Key`
- `IgnoreRequestBody`
  - by default, the contents of the request body (form data/json) is taken into consideration when determining the uniqueness of incoming requests even if the
idempotency-key is the same among them. i.e. if two different requests come in with the same idempotency-key but with different request body content, they
will be considered to be unique requests and the endpoint will be executed for each request.
  - remarks: this involves buffering the request body content per each request in order to generate a sha512 hash of the incoming body content. if the clients making
requests are under strict quality control and are guaranteed to not reuse idempotency keys, you can set this to `true` to prevent the hashing of
request body content.
- `SwaggerExampleGenerator`
  - a function to generate an example value for the swagger request param header
- `SwaggerHeaderDescription`
  - the description text for the swagger request header parameter
- `SwaggerHeaderType`
  - the type/format of the swagger example value


#### `InternalErrorResponse`

the dto used to send an error response to the client when an unhandled exception occurs on the server

**Properties:**

- `Code`
  - http status code of the error response
- `Note`
  - additional information or instructions
- `Reason`
  - the reason for the error
- `Status`
  - error status


#### `MainExtensions`

provides extensions to easily bootstrap fastendpoints in the asp.net middleware pipeline

**Methods:**

- `AddFastEndpoints(Microsoft.Extensions.DependencyInjection.IServiceCollection, Action<EndpointDiscoveryOptions>)`
  - adds the FastEndpoints services to the ASP.Net middleware pipeline
  - `options`: optionally specify the endpoint discovery options
- `UseFastEndpoints(Microsoft.AspNetCore.Builder.IApplicationBuilder, Action<Config>)`
  - finalizes auto discovery of endpoints and prepares FastEndpoints to start processing requests


HINT: you can use `MapFastEndpoints` instead of this method if you have some special
requirement such as using "Startup.cs", etc.
  - `configAction`: an optional action to configure FastEndpoints


#### `Mapper<T1, T2, T3>`

use this base class to define domain entity mappers for your endpoints.


HINT: entity mappers are used as singletons for performance reasons. do not maintain state in the mappers.


#### `MiddlewareExtensions`

**Methods:**

- `UseAntiforgeryFE(Microsoft.AspNetCore.Builder.IApplicationBuilder, Func<Microsoft.AspNetCore.Http.HttpContext,bool>, string[])`
  - enable anti-forgery token verification middleware.
make sure to also add the anti-forgery services with `builder.Services.AddAntiForgery()`
  - `skipRequestFilter`: an optional predicate which can be used to skip anti-forgery checks for requests that satisfy a given condition.
provide a function that returns `true` for requests that you'd want the anti-forgery middleware to skip processing.
  - `additionalContentTypes`: optional array of additional content-types to enforce antiforgery checks for (if the endpoint has enabled antiforgery).


#### `MultipartSection`

represents a multipart form section which could contain either a `FormMultipartSection` or a `FileMultipartSection`

**Methods:**

- `#ctor(Microsoft.AspNetCore.WebUtilities.FormMultipartSection, Microsoft.AspNetCore.WebUtilities.FileMultipartSection)`
  - represents a multipart form section which could contain either a `FormMultipartSection` or a `FileMultipartSection`
  - `form`
  - `file`


#### `Order`

enum used to specify whether to execute global pre/post processors before endpoint level processors

**Fields:**

- `After`
  - execute global processors after the endpoint level processors
- `Before`
  - execute global processors before the endpoint level processors


#### `PlainTextRequest`

use this dto if you need to model bind the raw content body of an incoming http request or you may implement the IPlainTextRequest interface on your own request dto.

**Properties:**

- `Content`
  - the body content of the incoming request


#### `PostProcessorAttribute<T>`

generic attribute for adding a post-processor to an endpoint. only effective when attribute based endpoint configuration is being used.


#### `PostProcessorContext<T1, T2>`

represents the context for a post-processing operation with a request and response pair.

**Properties:**

- `ExceptionDispatchInfo`
  - gets the `ExceptionDispatchInfo` if an exception was captured during the processing.
may be null if no exception was captured.
- `HttpContext`
  - gets the `HttpContext` associated with the current request and response.
- `Request`
  - gets the request associated with the post-processing context.
may be null if request binding has failed.
- `Response`
  - gets the response associated with the post-processing context.
may be null if the response is not available or not yet created.
- `ValidationFailures`
  - gets a collection of `ValidationFailure` instances that describe any validation failures.


#### `PostProcessor<T1, T2, T3>`

inherit this class to create a post-processor with access to the common processor state of the endpoint.

**Methods:**

- `PostProcessAsync(IPostProcessorContext<T1,T3>, CancellationToken)`
  - not intended for direct external use.
- `PostProcessAsync(IPostProcessorContext<T1,T3>, T2, CancellationToken)`
  - implement this method to define the post-processing logic using the provided context and state.
  - `context`: the context object encapsulating all necessary information for post-processing.
  - `state`: the common processor state object, derived from the HttpContext or newly instantiated.
  - `ct`: cancellation token.
  - returns: a Task representing the asynchronous operation.


#### `PreProcessorAttribute<T>`

generic attribute for adding a pre-processor to an endpoint. only effective when attribute based endpoint configuration is being used.


#### `PreProcessorContext<T>`

represents the context for a pre-processing operation with a request.

**Properties:**

- `HttpContext`
  - gets the `HttpContext` associated with the current request.
- `Request`
  - gets the request associated with the pre-processing context.
may be null if model binding has failed.
- `ValidationFailures`
  - gets a collection of `ValidationFailure` instances that describe any validation failures.


#### `PreProcessor<T1, T2>`

inherit this class to create a pre-processor with access to the common processor state of the endpoint

**Methods:**

- `PreProcessAsync(IPreProcessorContext<T1>, CancellationToken)`
  - not intended for direct external use.
- `PreProcessAsync(IPreProcessorContext<T1>, T2, CancellationToken)`
  - this method is called with the given arguments when the pre-processor executes.
  - `context`: the context object encapsulating all necessary information for pre-processing.
  - `state`: the common processor state object
  - `ct`: cancellation token


#### `ProblemDetails`

RFC7807 compatible problem details/ error response class. this can be used by configuring startup like so:
`app.UseFastEndpoints(c => c.Errors.UseProblemDetails())`

**Methods:**

- `ExecuteAsync(Microsoft.AspNetCore.Http.HttpContext)`
- `PopulateMetadata(MethodInfo, Microsoft.AspNetCore.Builder.EndpointBuilder)`

**Properties:**

- `Detail`
  - the details of the error


#### `RequestBinder<T>`

the default request binder for a given request dto type

**Methods:**

- `#ctor`
  - default constructor which enables all binding sources
- `#ctor(BindingSource)`
  - constructor accepting a bitwise combination of enums which enables only the specified binding sources
  - `enabledSources`: a bitwise combination of enum values
- `BindAsync(BinderContext, CancellationToken)`
  - override this method to customize the request binding logic
  - `ctx`: the request binder context which holds all the data required for binding the incoming request
  - `ct`: cancellation token


#### `RequestExample`

represents a swagger example request analogous to an OpenApiExample

**Methods:**

- `#ctor(object, string, string, string)`
  - represents a swagger example request analogous to an OpenApiExample
  - `value`: the actual example request object
  - `label`: the label/name for this example request
  - `summary`: the summary text of this example request
  - `description`: the description of this example request

**Properties:**

- `Description`
  - the description of this example request
- `Label`
  - the label/name for this example request
- `Summary`
  - the summary text of this example request
- `Value`
  - the actual example request object


#### `RequestMapper<T1, T2>`

use this base class to define a domain entity mapper for your endpoints that only has a request dto and no response dto.


HINT: entity mappers are used as singletons for performance reasons. do not maintain state in the mappers.


#### `ResponseHeader`

describes a swagger response header for a certain response dto

**Properties:**

- `Description`
  - description for the header
- `Example`
  - an example header value
- `HeaderName`
  - the name of the header
- `StatusCode`
  - specify which http status code this response header applies to


#### `ResponseMapper<T1, T2>`

use this base class to define a domain entity mapper for your endpoints that only has a response dto and no request dto.


HINT: entity mappers are used as singletons for performance reasons. do not maintain state in the mappers.


#### `ResponseSender<T1, T2>`

this struct encapsulates the default response sending methods for endpoints.
you can add your own custom send methods by writing extension methods targeting `IResponseSender` interface.

**Methods:**

- `#ctor(Endpoint<T1,T2>)`
  - this struct encapsulates the default response sending methods for endpoints.
you can add your own custom send methods by writing extension methods targeting `IResponseSender` interface.
- `AcceptedAtAsync(string, object, T2, bool, CancellationToken)`
  - send a 202 accepted response with a location header containing where the resource can be retrieved from.


WARNING: this method is only supported on single verb/route endpoints. it will not produce a `Location` header if used in a multi verb or multi
route endpoint.
  - `endpointName`: the name of the endpoint to use for link generation (openapi route id)
  - `routeValues`: a route values object with key/value pairs of route information
  - `responseBody`: the content to be serialized in the response body
  - `generateAbsoluteUrl`: set to true for generating an absolute url instead of relative url for the location header
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used
- `AcceptedAtAsync<T>(object, T2, Nullable<Http>, Nullable<int>, bool, CancellationToken)`
  - send a 202 accepted response with a location header containing where the resource can be retrieved from.


HINT: if pointing to an endpoint with multiple verbs, make sure to specify the 'verb' argument and if pointing to a multi route endpoint,
specify the 'routeNumber' argument.


WARNING: this overload will not add a location header if you've set a custom endpoint name using .WithName() method. use the other overload
that accepts a string endpoint name instead.
  - `routeValues`: a route values object with key/value pairs of route information
  - `responseBody`: the content to be serialized in the response body
  - `verb`: only useful when pointing to a multi verb endpoint
  - `routeNumber`: only useful when pointing to a multi route endpoint
  - `generateAbsoluteUrl`: set to true for generating an absolute url instead of relative url for the location header
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used
  - `<TEndpoint>`: the type of the endpoint where the resource can be retrieved from
- `BytesAsync(byte[], string, string, Nullable<DateTimeOffset>, bool, CancellationToken)`
  - send a byte array to the client
  - `bytes`: the bytes to send
  - `contentType`: optional content type to set on the http response
  - `lastModified`: optional last modified date-time-offset for the data stream
  - `enableRangeProcessing`: optional switch for enabling range processing
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used
- `CreatedAtAsync(string, object, T2, bool, CancellationToken)`
  - send a 201 created response with a location header containing where the resource can be retrieved from.


WARNING: this method is only supported on single verb/route endpoints. it will not produce a `Location` header if used in a multi verb or multi
route endpoint.
  - `endpointName`: the name of the endpoint to use for link generation (openapi route id)
  - `routeValues`: a route values object with key/value pairs of route information
  - `responseBody`: the content to be serialized in the response body
  - `generateAbsoluteUrl`: set to true for generating an absolute url instead of relative url for the location header
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used
- `CreatedAtAsync<T>(object, T2, Nullable<Http>, Nullable<int>, bool, CancellationToken)`
  - send a 201 created response with a location header containing where the resource can be retrieved from.


HINT: if pointing to an endpoint with multiple verbs, make sure to specify the 'verb' argument and if pointing to a multi route endpoint,
specify the 'routeNumber' argument.


WARNING: this overload will not add a location header if you've set a custom endpoint name using .WithName() method. use the other overload
that accepts a string endpoint name instead.
  - `routeValues`: a route values object with key/value pairs of route information
  - `responseBody`: the content to be serialized in the response body
  - `verb`: only useful when pointing to a multi verb endpoint
  - `routeNumber`: only useful when pointing to a multi route endpoint
  - `generateAbsoluteUrl`: set to true for generating an absolute url instead of relative url for the location header
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used
  - `<TEndpoint>`: the type of the endpoint where the resource can be retrieved from
- `EmptyJsonObject(CancellationToken)`
  - send an empty json object in the body
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used
- `ErrorsAsync(int, CancellationToken)`
  - send a 400 bad request with error details of the current validation failures
  - `statusCode`: the status code for the error response
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used
- `EventStreamAsync(Generic.IAsyncEnumerable<StreamItem>, CancellationToken)`
  - start an asynchronous "server-sent-events" data stream for the client with items that might be of different types, without blocking any threads
  - `eventStream`: an IAsyncEnumerable of stream items that is the source of the data
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used.
- `EventStreamAsync<T>(string, Generic.IAsyncEnumerable<T1>, CancellationToken)`
  - start an asynchronous "server-sent-events" data stream for the client with items of the same type, without blocking any threads
  - `eventName`: the name of the event stream
  - `eventStream`: an IAsyncEnumerable that is the source of the data
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used.
  - `<T>`: the type of the objects being sent in the event stream
- `FileAsync(FileInfo, string, Nullable<DateTimeOffset>, bool, CancellationToken)`
  - send a file to the client
  - `fileInfo`
  - `contentType`: optional content type to set on the http response
  - `lastModified`: optional last modified date-time-offset for the data stream
  - `enableRangeProcessing`: optional switch for enabling range processing
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used
- `ForbiddenAsync(CancellationToken)`
  - send a 403 unauthorized response
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used
- `HeadersAsync(Action<Microsoft.AspNetCore.Http.IHeaderDictionary>, int, CancellationToken)`
  - send headers in response to a HEAD request
  - `headers`: an action to be performed on the headers dictionary of the response
  - `statusCode`: optional custom http status code
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used.
- `InterceptedAsync(object, int, CancellationToken)`
  - sends an object serialized as json to the client. if a response interceptor has been defined,
then that will be executed before the normal response is sent.
  - `response`: the object to serialize to json
  - `statusCode`: optional custom http status code
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used
- `NoContentAsync(CancellationToken)`
  - send a 204 no content response
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used
- `NotFoundAsync(CancellationToken)`
  - send a 404 not found response
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used
- `NotModifiedAsync(CancellationToken)`
  - send a 304 not modified response
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used
- `OkAsync`
  - send an http 200 ok response without a body.
- `OkAsync(CancellationToken)`
  - send an http 200 ok response without a body.
  - `cancellation`: cancellation token
- `OkAsync(T2)`
  - send an http 200 ok response with the supplied response dto serialized as json to the client.
  - `response`: the object to serialize to json
- `OkAsync(T2, CancellationToken)`
  - send an http 200 ok response with the supplied response dto serialized as json to the client.
  - `response`: the object to serialize to json
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used
- `RedirectAsync(string, bool, bool)`
  - send a 302/301 redirect response
  - `location`: the location to redirect to
  - `isPermanent`: set to true for a 301 redirect. 302 is the default.
  - `allowRemoteRedirects`: set to true if it's ok to redirect to remote addresses, which is prone to open redirect attacks.
- `ResponseAsync(T2, int, CancellationToken)`
  - send the supplied response dto serialized as json to the client.
  - `response`: the object to serialize to json
  - `statusCode`: optional custom http status code
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used
- `ResultAsync(Microsoft.AspNetCore.Http.IResult)`
  - execute and send any `IResult` produced by the `Results` class in minimal apis.
  - `result`: the `IResult` instance to execute such as:
`Results.Forbid();
Results.Ok(...);`
- `StatusCodeAsync(int, CancellationToken)`
  - send any http status code
  - `statusCode`: the http status code
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used.
- `StreamAsync(Stream, string, Nullable<long>, string, Nullable<DateTimeOffset>, bool, CancellationToken)`
  - send the contents of a stream to the client
  - `stream`: the stream to read the data from
  - `fileName`: and optional file name to set in the content-disposition header
  - `fileLengthBytes`: optional total size of the file/stream
  - `contentType`: optional content type to set on the http response
  - `lastModified`: optional last modified date-time-offset for the data stream
  - `enableRangeProcessing`: optional switch for enabling range processing
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used
- `StringAsync(string, int, string, CancellationToken)`
  - send the supplied string content to the client.
  - `content`: the string to write to the response body
  - `statusCode`: optional custom http status code
  - `contentType`: optional content type header value
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used
- `UnauthorizedAsync(CancellationToken)`
  - send a 401 unauthorized response
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used


#### `RouteHandlerBuilderExtensions`

**Methods:**

- `Accepts<T>(Microsoft.AspNetCore.Builder.RouteHandlerBuilder)`
  - override the default "accepts metadata" in order to accept any content-type from the client.
  - `<TRequest>`: the type of the request dto
- `ClearDefaultAccepts(Microsoft.AspNetCore.Builder.RouteHandlerBuilder)`
  - clears just the default "accepts metadata" from the endpoint.
- `ClearDefaultProduces(Microsoft.AspNetCore.Builder.RouteHandlerBuilder, int[])`
  - clears any number of given "produces metadata" from the endpoint by supplying the status codes of the responses to remove.
not specifying any status codes will result in all produces metadata being removed.
  - `statusCodes`: one or more status codes of the defaults to remove
- `ProducesProblemDetails(Microsoft.AspNetCore.Builder.RouteHandlerBuilder, int, string)`
  - adds produces metadata of type `ProblemDetails` (RFC7807 compatible) to the endpoint description
  - `statusCode`: the status code of the error response
  - `contentType`: content type header value
- `ProducesProblemFE(Microsoft.AspNetCore.Builder.RouteHandlerBuilder, int, string)`
  - adds produces metadata of type `ErrorResponse` to the endpoint description
  - `statusCode`: the status code of the error response
  - `contentType`: content type header value
- `ProducesProblemFE<T>(Microsoft.AspNetCore.Builder.RouteHandlerBuilder, int, string)`
  - adds produces metadata for a given type of error response dto
  - `statusCode`: the status code of the error response
  - `contentType`: content type header value
  - `<TResponse>`: the type of the error response


#### `SecurityOptions`

global security options

**Properties:**

- `NameClaimType`
  - specify a custom claim type used to identity the name of a user principal. defaults to `name`.


WARNING: do not change the default unless you fully comprehend what you're doing!!!
- `PermissionsClaimType`
  - specify a custom claim type used to identify permissions of a user principal. defaults to `permissions`.


WARNING: do not change the default unless you fully comprehend what you're doing!!!
- `RoleClaimType`
  - specify a custom claim type used to identify roles of a user principal. defaults to `role`.


WARNING: do not change the default unless you fully comprehend what you're doing!!!
- `ScopeClaimType`
  - specify a custom claim type used to identify scopes. defaults to `scope`.


WARNING: do not change the default unless you fully comprehend what you're doing!!!
- `ScopeParser`
  - a function for parsing the 'scope' claim value and producing a collection of scopes.
the default function simply splits the input string using the space character.


#### `SerializerOptions`

serialization options for the endpoints

**Properties:**

- `AspNetCoreOptions`
  - the original json serializer options from the di-registered JsonOptions.
used by IResult types (like Ok<T>) which get their serializer options from di.
- `CharacterEncoding`
  - the charset used for responses. this will be appended to the content-type header when the `ResponseSerializer` func is used.
defaults to `utf-8`. set to `null` to disable appending a charset.
- `Options`
  - the json serializer options
- `RequestDeserializer`
  - a function for deserializing the incoming http request body. this function will be executed for each request received if it has a json request body.
the input parameters of the func are as follows:
`HttpRequest : the incoming request
Type : the type of the request dto which the request body will be deserialized into
JsonSerializerContext? : json serializer context if code generation is used
CancellationToken : a cancellation token`
- `ResponseSerializer`
  - a function for writing serialized response dtos to the response body.
this function will be executed whenever a json response is being sent to the client.
you should set the content-type and write directly to the http response body stream in this function.
the parameters of the func are as follows:
`HttpResponse : the http response object.
object : the response dto to be serialized.
string : the response content-type.
JsonSerializerContext? : json serializer context if code generation is used.
CancellationToken : a cancellation token.`


example:
`config.ResponseSerializer = (rsp, dto, cType, jCtx , ct) =>
{
rsp.ContentType = cType;
return rsp.WriteAsync(Newtonsoft.Json.JsonConvert.SerializeObject(dto), ct);
};`
- `SerializerErrorsField`
  - this is the field name used for adding serializer errors when the serializer throws due to bad json input and the error is not concerning a
particular property/field of the incoming json.


#### `StreamItem`

**Methods:**

- `#ctor(string, object)`
  - `eventName`: the name of the event
  - `data`: the event data
- `#ctor(string, string, object, Nullable<int>)`
  - `id`: the id of the event
  - `eventName`: the name of the event
  - `data`: the event data
  - `retry`: reconnection time in milliseconds
- `GetDataString(Json.JsonSerializerOptions)`
  - override this method in order to take control of the serialization of the event data
  - `options`: json serializer options

**Properties:**

- `Data`
  - event data
- `EventName`
  - event name
- `Id`
  - event id
- `Retry`
  - reconnection time in milliseconds


#### `SubGroup<T>`

common configuration for a sub group of endpoints can be specified by implementing this abstract class and calling
`Configure` in the constructor.

**Methods:**

- `Configure(string, Action<EndpointDefinition>)`


#### `Summary<T>`


#### `Summary<T1, T2>`


#### `TestResult<T>`

a record encapsulating the http response as well as the resulting dto of a test execution

**Methods:**

- `#ctor(Http.HttpResponseMessage, T1, string)`
  - a record encapsulating the http response as well as the resulting dto of a test execution
  - `Response`: http response message object
  - `Result`: the resulting dto object. default when response is not successful.
  - `ErrorContent`: the body content from error responses. null when response is successful.
  - `<TResponse>`: the type of the response dto

**Properties:**

- `ErrorContent`
  - the body content from error responses. null when response is successful.
- `Response`
  - http response message object
- `Result`
  - the resulting dto object. default when response is not successful.


#### `TestingExtensions`

extension methods for registering fake/test/mock command and event handlers for integration testing

**Methods:**

- `GetTestCommandReceiver<T>(IServiceProvider)`
- `GetTestEventReceiver<T>(IServiceProvider)`
- `RegisterTestCommandHandler<T1, T2, T3>(Microsoft.Extensions.DependencyInjection.IServiceCollection)`
- `RegisterTestCommandHandler<T1, T2>(Microsoft.Extensions.DependencyInjection.IServiceCollection)`
- `RegisterTestCommandReceivers(Microsoft.Extensions.DependencyInjection.IServiceCollection)`
- `RegisterTestEventHandler<T1, T2>(Microsoft.Extensions.DependencyInjection.IServiceCollection)`
- `RegisterTestEventReceivers(Microsoft.Extensions.DependencyInjection.IServiceCollection)`


#### `ThrottleOptions`

global settings for throttling

**Properties:**

- `HeaderName`
  - header used to track rate limits
- `Message`
  - custom error response message for throttled requests


#### `UserPrivileges`

the priviledges of the user which will be embedded in the jwt or cookie

**Properties:**

- `Claims`
  - claims of the user
- `Item`
  - shortcut for adding a new `Claim` to the claim list for the given claim type and value
  - `claimType`: the claim type to add
- `Permissions`
  - allowed permissions for the user
- `Roles`
  - roles of the user


#### `ValidationContext`

provides a way to manipulate the validation failures of the current endpoint context.
call `Instance` to obtain an instance of the current validation context.

**Methods:**

- `AddError(FluentValidation.Results.ValidationFailure)`
  - add a `ValidationFailure` to the current collection of validation failures of the endpoint
  - `failure`: the validation failure to add
- `AddError(string, string, FluentValidation.Severity)`
  - adds a "GeneralError" to the current list of validation failures
  - `message`: the error message
  - `errorCode`: the error code associated with the error
  - `severity`: the severity of the error
- `ThrowError(FluentValidation.Results.ValidationFailure, Nullable<int>)`
  - adds a `ValidationFailure` to the validation failure collection of the endpoint and send back a 400 bad request with error details
immediately interrupting handler execution flow. i.e. execution will not continue past this call.
  - `failure`: the validation failure to add
  - `statusCode`: an optional status code to be used when building the error response
- `ThrowError(string, Nullable<int>)`
  - adds a "GeneralError" to the validation failure list and sends back a 400 bad request with error details immediately interrupting handler execution
flow. i.e. execution will not continue past this call.
  - `message`: the error message
  - `statusCode`: an optional status code to be used when building the error response
- `ThrowError(string, string, FluentValidation.Severity, Nullable<int>)`
  - adds a "GeneralError" to the validation failure list and sends back a 400 bad request with error details immediately interrupting handler execution
flow. i.e. execution will not continue past this call.
  - `message`: the error message
  - `errorCode`: the error code associated with the error
  - `severity`: the severity of the error
  - `statusCode`: an optional status code to be used when building the error response
- `ThrowIfAnyErrors(Nullable<int>)`
  - interrupt the flow of handler execution and send a 400 bad request with error details if there are any validation failures in the current request. if
there are no validation failures, execution will continue past this call.
  - `statusCode`: an optional status code to be used when building the error response

**Properties:**

- `Instance`
  - provides access to the validation context of the currently executing endpoint.
- `ValidationFailed`
  - indicates if there are any validation failures for the current request
- `ValidationFailures`
  - validation failures collection for the endpoint


#### `ValidationFailureException`

the exception thrown when validation failure occurs.
inspect the `Failures` property for details.

**Properties:**

- `Failures`
  - the collection of failures that have occured.
- `StatusCode`
  - the status code to be used when building the error response.


#### `ValidationOptions`

validation related options

**Properties:**

- `EnableDataAnnotationsSupport`
  - set this property to `true` if you'd like to enable support for `System.ComponentModel.DataAnnotations` attributes for basic validation.
- `UsePropertyNamingPolicy`
  - specify whether to use the json property naming policy of the application for converting property names produced by fluentvalidations library


#### `Validator<T>`

inherit from this base class to define your dto validators


HINT: validators are registered as singletons. i.e. the same validator instance is used to validate each request for best performance. hance,
do not maintain state in your validators.

**Methods:**

- `CreateScope`
- `Resolve(Type)`
- `Resolve(Type, string)`
- `Resolve<T>`
- `Resolve<T>(string)`
- `TryResolve(Type)`
- `TryResolve(Type, string)`
- `TryResolve<T>`
- `TryResolve<T>(string)`


#### `VersioningOptions`

global endpoint versioning options

**Properties:**

- `DefaultVersion`
  - this value will be used on endpoints that does not specify a version
- `Prefix`
  - the prefix used in front of the version (for example 'v' produces 'v{version}').
- `PrependToRoute`
  - set to true if you'd like to prefix the version to the route instead of being suffixed which is the default.
if `RouteTemplate` is specified, that will take precedence over this setting.
- `RouteTemplate`
  - if a route template is specified here, the template string in endpoint routes will be replaced by the version of the endpoint.
this setting will render `PrependToRoute` ineffective if also set.
setting a value here makes it mandatory to specify the template in all routes of versioned endpoints.


### namespace `FastEndpoints.Ep`

#### `NoReq`

specifies that the endpoint has no request dto


#### `Req<T>`

specify the request dto type of the endpoint


### namespace `FastEndpoints.Ep.NoReq`

#### `NoRes`

specifies that the endpoint has no response dto


#### `Res<T>`

specify the response dto type of the endpoint


### namespace `FastEndpoints.Ep.NoReq.Res`1`

#### `Map<T>`

specify the mapper type of the endpoint


### namespace `FastEndpoints.Ep.Req`1`

#### `NoRes`

specifies that the endpoint has no response dto


#### `Res<T>`

specify the response dto type of the endpoint


### namespace `FastEndpoints.Ep.Req`1.NoRes`

#### `Map<T>`

specify the request mapper type of the endpoint


### namespace `FastEndpoints.Ep.Req`1.Res`1`

#### `Map<T>`

specify the mapper type of the endpoint


### namespace `FastEndpoints.ErrorOptions`

#### `ProblemDetailsConfig`

global settings for `ProblemDetails` error responses.

**Properties:**

- `AllowDuplicateErrors`
  - controls whether duplicate errors with the same name should be allowed for `Errors`.
- `DetailTransformer`
  - sets a function that will be called per instance/response that allows customization of the `Detail` value.
- `IndicateErrorCode`
  - if set to true, the `ErrorCode` value of the failure will be serialized to the response.
- `IndicateErrorSeverity`
  - if set to true, the `Severity` value of the failure will be serialized to the response.
- `Map`
  - the built-in map that ties together status codes to the relevant title and type values.
- `ResponseBuilder`
  - sets a function used for transforming validation errors to a RFC7807 compatible problem details error response dto.
- `TitleTransformer`
  - sets a function that will be called per instance/response that allows customization of the `Title` value.
- `TitleValue`
  - globally sets the value of `Title`.
- `TypeTransformer`
  - sets a function that will be called per instance/response that allows customization of the `Type` value.
- `TypeValue`
  - globally sets the value of `Type`.


### namespace `FastEndpoints.HttpClientExtensions`

#### `<G>$2C76DB3DB4BE8E5FC629D93AC0513B6F`

**Methods:**

- `DELETEAsync<T1, T2, T3>(T2, bool, bool)`
  - make a DELETE request to an endpoint using auto route discovery using a request dto and get back a `TestResult<T>` containing
the `HttpResponseMessage` as well as the TResponse DTO.
  - `request`: the request dto
  - `populateHeaders`: when set to false, headers will not be automatically added to the http request from request dto properties decorated with the
[FromHeader] attribute.
  - `populateCookies`: when set to false, cookies will not be automatically added to the http request from request dto properties decorated with the
[FromCookie] attribute.
  - `<TEndpoint>`: the type of the endpoint
  - `<TRequest>`: the type of the request dto
  - `<TResponse>`: the type of the response dto
- `DELETEAsync<T1, T2>`
  - make a DELETE request to an endpoint using auto route discovery without a request dto and get back a `TestResult<T>` containing
the `HttpResponseMessage` as well as the TResponse DTO.
  - `<TEndpoint>`: the type of the endpoint
  - `<TResponse>`: the type of the response dto
- `DELETEAsync<T1, T2>(T2, bool, bool)`
  - make a DELETE request to an endpoint using auto route discovery using a request dto that does not send back a response dto.
  - `request`: the request dto
  - `populateHeaders`: when set to false, headers will not be automatically added to the http request from request dto properties decorated with the
[FromHeader] attribute.
  - `populateCookies`: when set to false, cookies will not be automatically added to the http request from request dto properties decorated with the
[FromCookie] attribute.
  - `<TEndpoint>`: the type of the endpoint
  - `<TRequest>`: the type of the request dto
- `DELETEAsync<T1, T2>(string, T1, bool, bool)`
  - make a DELETE request using a request dto and get back a `TestResult<T>` containing the `HttpResponseMessage` as
well as the TResponse DTO.
  - `requestUri`: the route url to post to
  - `request`: the request dto
  - `populateHeaders`: when set to false, headers will not be automatically added to the http request from request dto properties decorated with the
[FromHeader] attribute.
  - `populateCookies`: when set to false, cookies will not be automatically added to the http request from request dto properties decorated with the
[FromCookie] attribute.
  - `<TRequest>`: type of the request dto
  - `<TResponse>`: type of the response dto
- `GETAsync<T1, T2, T3>(T2, bool, bool)`
  - make a GET request to an endpoint using auto route discovery using a request dto and get back a `TestResult<T>` containing the
`HttpResponseMessage` as well as the TResponse DTO.
  - `request`: the request dto
  - `populateHeaders`: when set to false, headers will not be automatically added to the http request from request dto properties decorated with the
[FromHeader] attribute.
  - `populateCookies`: when set to false, cookies will not be automatically added to the http request from request dto properties decorated with the
[FromCookie] attribute.
  - `<TEndpoint>`: the type of the endpoint
  - `<TRequest>`: the type of the request dto
  - `<TResponse>`: the type of the response dto
- `GETAsync<T1, T2>`
  - make a GET request to an endpoint using auto route discovery without a request dto and get back a `TestResult<T>` containing the
`HttpResponseMessage` as well as the TResponse DTO.
  - `<TEndpoint>`: the type of the endpoint
  - `<TResponse>`: the type of the response dto
- `GETAsync<T1, T2>(T2, bool, bool)`
  - make a GET request to an endpoint using auto route discovery using a request dto that does not send back a response dto.
  - `request`: the request dto
  - `populateHeaders`: when set to false, headers will not be automatically added to the http request from request dto properties decorated with the
[FromHeader] attribute.
  - `populateCookies`: when set to false, cookies will not be automatically added to the http request from request dto properties decorated with the
[FromCookie] attribute.
  - `<TEndpoint>`: the type of the endpoint
  - `<TRequest>`: the type of the request dto
- `GETAsync<T1, T2>(string, T1, bool, bool)`
  - make a GET request using a request dto and get back a `TestResult<T>` containing the `HttpResponseMessage` as well
as the TResponse DTO.
  - `requestUri`: the route url to post to
  - `request`: the request dto
  - `populateHeaders`: when set to false, headers will not be automatically added to the http request from request dto properties decorated with the
[FromHeader] attribute.
  - `populateCookies`: when set to false, cookies will not be automatically added to the http request from request dto properties decorated with the
[FromCookie] attribute.
  - `<TRequest>`: type of the request dto
  - `<TResponse>`: type of the response dto
- `PATCHAsync<T1, T2, T3>(T2, bool, bool, bool)`
  - make a PATCH request to an endpoint using auto route discovery using a request dto and get back a `TestResult<T>` containing the
`HttpResponseMessage` as well as the TResponse DTO.
  - `request`: the request dto
  - `sendAsFormData`: when set to true, the request dto will be automatically converted to a `MultipartFormDataContent`
  - `populateHeaders`: when set to true, headers will be automatically added to the http request from request dto properties decorated with the [FromHeader] attribute.
  - `<TEndpoint>`: the type of the endpoint
  - `<TRequest>`: the type of the request dto
  - `<TResponse>`: the type of the response dto
- `PATCHAsync<T1, T2>`
  - make a PATCH request to an endpoint using auto route discovery without a request dto and get back a `TestResult<T>` containing
the `HttpResponseMessage` as well as the TResponse DTO.
  - `<TEndpoint>`: the type of the endpoint
  - `<TResponse>`: the type of the response dto
- `PATCHAsync<T1, T2>(T2, bool, bool, bool)`
  - make a PATCH request to an endpoint using auto route discovery using a request dto that does not send back a response dto.
  - `request`: the request dto
  - `sendAsFormData`: when set to true, the request dto will be automatically converted to a `MultipartFormDataContent`
  - `populateHeaders`: when set to false, headers will not be automatically added to the http request from request dto properties decorated with the
[FromHeader] attribute.
  - `populateCookies`: when set to false, cookies will not be automatically added to the http request from request dto properties decorated with the
[FromCookie] attribute.
  - `<TEndpoint>`: the type of the endpoint
  - `<TRequest>`: the type of the request dto
- `PATCHAsync<T1, T2>(string, T1, bool, bool, bool)`
  - make a PATCH request using a request dto and get back a `TestResult<T>` containing the `HttpResponseMessage` as
well as the TResponse DTO.
  - `requestUri`: the route url to PATCH to
  - `request`: the request dto
  - `sendAsFormData`: when set to true, the request dto will be automatically converted to a `MultipartFormDataContent`
  - `populateHeaders`: when set to false, headers will not be automatically added to the http request from request dto properties decorated with the
[FromHeader] attribute.
  - `populateCookies`: when set to false, cookies will not be automatically added to the http request from request dto properties decorated with the
[FromCookie] attribute.
  - `<TRequest>`: type of the request dto
  - `<TResponse>`: type of the response dto
- `POSTAsync<T1, T2, T3>(T2, bool, bool, bool)`
  - make a POST request to an endpoint using auto route discovery using a request dto and get back a `TestResult<T>` containing the
`HttpResponseMessage` as well as the TResponse DTO.
  - `request`: the request dto
  - `sendAsFormData`: when set to true, the request dto will be automatically converted to a `MultipartFormDataContent`
  - `populateHeaders`: when set to false, headers will not be automatically added to the http request from request dto properties decorated with the
[FromHeader] attribute.
  - `populateCookies`: when set to false, cookies will not be automatically added to the http request from request dto properties decorated with the
[FromCookie] attribute.
  - `<TEndpoint>`: the type of the endpoint
  - `<TRequest>`: the type of the request dto
  - `<TResponse>`: the type of the response dto
- `POSTAsync<T1, T2>`
  - make a POST request to an endpoint using auto route discovery without a request dto and get back a `TestResult<T>` containing
the `HttpResponseMessage` as well as the TResponse DTO.
  - `<TEndpoint>`: the type of the endpoint
  - `<TResponse>`: the type of the response dto
- `POSTAsync<T1, T2>(T2, bool, bool, bool)`
  - make a POST request to an endpoint using auto route discovery using a request dto that does not send back a response dto.
  - `request`: the request dto
  - `sendAsFormData`: when set to true, the request dto will be automatically converted to a `MultipartFormDataContent`
  - `populateHeaders`: when set to false, headers will not be automatically added to the http request from request dto properties decorated with the
[FromHeader] attribute.
  - `populateCookies`: when set to false, cookies will not be automatically added to the http request from request dto properties decorated with the
[FromCookie] attribute.
  - `<TEndpoint>`: the type of the endpoint
  - `<TRequest>`: the type of the request dto
- `POSTAsync<T1, T2>(string, T1, bool, bool, bool)`
  - make a POST request using a request dto and get back a `TestResult<T>` containing the `HttpResponseMessage` as well
as the TResponse DTO/>.
  - `requestUri`: the route url to post to
  - `request`: the request dto
  - `sendAsFormData`: when set to true, the request dto will be automatically converted to a `MultipartFormDataContent`
  - `populateHeaders`: when set to false, headers will not be automatically added to the http request from request dto properties decorated with the
[FromHeader] attribute.
  - `populateCookies`: when set to false, cookies will not be automatically added to the http request from request dto properties decorated with the
[FromCookie] attribute.
  - `<TRequest>`: type of the request dto
  - `<TResponse>`: type of the response dto
- `PUTAsync<T1, T2, T3>(T2, bool, bool, bool)`
  - make a PUT request to an endpoint using auto route discovery using a request dto and get back a `TestResult<T>` containing the
`HttpResponseMessage` as well as the TResponse DTO.
  - `request`: the request dto
  - `sendAsFormData`: when set to true, the request dto will be automatically converted to a `MultipartFormDataContent`
  - `populateHeaders`: when set to false, headers will not be automatically added to the http request from request dto properties decorated with the
[FromHeader] attribute.
  - `populateCookies`: when set to false, cookies will not be automatically added to the http request from request dto properties decorated with the
[FromCookie] attribute.
  - `<TEndpoint>`: the type of the endpoint
  - `<TRequest>`: the type of the request dto
  - `<TResponse>`: the type of the response dto
- `PUTAsync<T1, T2>`
  - make a PUT request to an endpoint using auto route discovery without a request dto and get back a `TestResult<T>` containing the
`HttpResponseMessage` as well as the TResponse DTO.
  - `<TEndpoint>`: the type of the endpoint
  - `<TResponse>`: the type of the response dto
- `PUTAsync<T1, T2>(T2, bool, bool, bool)`
  - make a PUT request to an endpoint using auto route discovery using a request dto that does not send back a response dto.
  - `request`: the request dto
  - `sendAsFormData`: when set to true, the request dto will be automatically converted to a `MultipartFormDataContent`
  - `populateHeaders`: when set to false, headers will not be automatically added to the http request from request dto properties decorated with the
[FromHeader] attribute.
  - `populateCookies`: when set to false, cookies will not be automatically added to the http request from request dto properties decorated with the
[FromCookie] attribute.
  - `<TEndpoint>`: the type of the endpoint
  - `<TRequest>`: the type of the request dto
- `PUTAsync<T1, T2>(string, T1, bool, bool, bool)`
  - make a PUT request using a request dto and get back a `TestResult<T>` containing the `HttpResponseMessage` as well
as the TResponse DTO.
  - `requestUri`: the route url to post to
  - `request`: the request dto
  - `sendAsFormData`: when set to true, the request dto will be automatically converted to a `MultipartFormDataContent`
  - `populateHeaders`: when set to false, headers will not be automatically added to the http request from request dto properties decorated with the
[FromHeader] attribute.
  - `populateCookies`: when set to false, cookies will not be automatically added to the http request from request dto properties decorated with the
[FromCookie] attribute.
  - `<TRequest>`: type of the request dto
  - `<TResponse>`: type of the response dto
- `SENDAsync<T1, T2>(Http.HttpMethod, string, T1, bool, bool, bool)`
  - send a request DTO to a given endpoint URL and get back a `TestResult<T>` containing the `HttpResponseMessage` as
well as the TResponse DTO
  - `method`: the http method to use
  - `requestUri`: the route url of the endpoint
  - `request`: the request dto
  - `sendAsFormData`: when set to true, the request dto will be automatically converted to a `MultipartFormDataContent`
  - `populateHeaders`: when set to false, headers will not be automatically added to the http request from request dto properties decorated with the
[FromHeader] attribute.
  - `populateCookies`: when set to false, cookies will not be automatically added to the http request from request dto properties decorated with the
[FromCookie] attribute.
  - `<TRequest>`: type of the request dto
  - `<TResponse>`: type of the response dto


### namespace `FastEndpoints.HttpResponseExtensions`

#### `<G>$8B7FDD3D869A4E98364DD81D882DB183`

**Methods:**

- `SendAcceptedAtAsync(string, object, object, Json.Serialization.JsonSerializerContext, bool, CancellationToken)`
  - send a 202 accepted response with a location header containing where the resource can be retrieved from.


WARNING: this method is only supported on single verb/route endpoints. it will not produce a `Location` header if used in a multi verb or multi
route endpoint.
  - `endpointName`: the name of the endpoint to use for link generation (openapi route id)
  - `routeValues`: a route values object with key/value pairs of route information
  - `responseBody`: the content to be serialized in the response body
  - `jsonSerializerContext`: json serializer context if code generation is used
  - `generateAbsoluteUrl`: set to true for generating an absolute url instead of relative url for the location header
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used.
- `SendAcceptedAtAsync<T>(object, object, Nullable<Http>, Nullable<int>, Json.Serialization.JsonSerializerContext, bool, CancellationToken)`
  - send a 202 accepted response with a location header containing where the resource can be retrieved from.


HINT: if pointing to an endpoint with multiple verbs, make sure to specify the 'verb' argument and if pointing to a multi route endpoint,
specify the 'routeNumber' argument.


WARNING: this overload will not add a location header if you've set a custom endpoint name using .WithName() method. use the other overload
that accepts a string endpoint name instead.
  - `routeValues`: a route values object with key/value pairs of route information
  - `responseBody`: the content to be serialized in the response body
  - `verb`: only useful when pointing to a multi verb endpoint
  - `routeNumber`: only useful when pointing to a multi route endpoint
  - `jsonSerializerContext`: json serializer context if code generation is used
  - `generateAbsoluteUrl`: set to true for generating an absolute url instead of relative url for the location header
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used.
  - `<TEndpoint>`: the type of the endpoint where the resource can be retrieved from
- `SendAsync<T>(T1, int, Json.Serialization.JsonSerializerContext, CancellationToken)`
  - send the supplied response dto serialized as json to the client.
  - `response`: the object to serialize to json
  - `statusCode`: optional custom http status code
  - `jsonSerializerContext`: json serializer context if code generation is used
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used.
- `SendAtAsync(int, string, object, bool, string, object, Json.Serialization.JsonSerializerContext, CancellationToken)`
  - send a custom 20X (accepted/created) response with a location header containing where the resource can be retrieved from.


WARNING: this method is only supported on single verb/route endpoints. it will not produce a `Location` header if used in a multi verb or multi
route endpoint.
  - `statusCode`: the http status code to send
  - `endpointName`: the name of the endpoint to use for link generation (openapi route id)
  - `routeValues`: a route values object with key/value pairs of route information
  - `generateAbsoluteUrl`: set to true for generating an absolute url instead of relative url for the location header
  - `contentType`: the content type for the response
  - `responseBody`: the content to be serialized in the response body
  - `jsonSerializerContext`: json serializer context if code generation is used
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used.
- `SendAtAsync<T>(int, object, bool, string, object, Nullable<Http>, Nullable<int>, Json.Serialization.JsonSerializerContext, CancellationToken)`
  - send a custom 20X (accepted/created) response with a location header containing where the resource can be retrieved from.


HINT: if pointing to an endpoint with multiple verbs, make sure to specify the 'verb' argument and if pointing to a multi route endpoint,
specify the 'routeNumber' argument.


WARNING: this overload will not add a location header if you've set a custom endpoint name using .WithName() method. use the other overload
that accepts a string endpoint name instead.
  - `statusCode`: the http status code to send
  - `routeValues`: a route values object with key/value pairs of route information
  - `generateAbsoluteUrl`: set to true for generating an absolute url instead of relative url for the location header
  - `responseBody`: the content to be serialized in the response body
  - `contentType`: the content type for the response
  - `verb`: only useful when pointing to a multi verb endpoint
  - `routeNumber`: only useful when pointing to a multi route endpoint
  - `jsonSerializerContext`: json serializer context if code generation is used
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used.
  - `<TEndpoint>`: the type of the endpoint where the resource can be retrieved from
- `SendBytesAsync(byte[], string, string, Nullable<DateTimeOffset>, bool, CancellationToken)`
  - send a byte array to the client
  - `bytes`: the bytes to send
  - `contentType`: optional content type to set on the http response
  - `lastModified`: optional last modified date-time-offset for the data stream
  - `enableRangeProcessing`: optional switch for enabling range processing
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used.
- `SendCreatedAtAsync(string, object, object, Json.Serialization.JsonSerializerContext, bool, CancellationToken)`
  - send a 201 created response with a location header containing where the resource can be retrieved from.


WARNING: this method is only supported on single verb/route endpoints. it will not produce a `Location` header if used in a multi verb or multi
route endpoint.
  - `endpointName`: the name of the endpoint to use for link generation (openapi route id)
  - `routeValues`: a route values object with key/value pairs of route information
  - `responseBody`: the content to be serialized in the response body
  - `jsonSerializerContext`: json serializer context if code generation is used
  - `generateAbsoluteUrl`: set to true for generating an absolute url instead of relative url for the location header
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used.
- `SendCreatedAtAsync<T>(object, object, Nullable<Http>, Nullable<int>, Json.Serialization.JsonSerializerContext, bool, CancellationToken)`
  - send a 201 created response with a location header containing where the resource can be retrieved from.


HINT: if pointing to an endpoint with multiple verbs, make sure to specify the 'verb' argument and if pointing to a multi route endpoint,
specify the 'routeNumber' argument.


WARNING: this overload will not add a location header if you've set a custom endpoint name using .WithName() method. use the other overload
that accepts a string endpoint name instead.
  - `routeValues`: a route values object with key/value pairs of route information
  - `responseBody`: the content to be serialized in the response body
  - `verb`: only useful when pointing to a multi verb endpoint
  - `routeNumber`: only useful when pointing to a multi route endpoint
  - `jsonSerializerContext`: json serializer context if code generation is used
  - `generateAbsoluteUrl`: set to true for generating an absolute url instead of relative url for the location header
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used.
  - `<TEndpoint>`: the type of the endpoint where the resource can be retrieved from
- `SendEmptyJsonObject(Json.Serialization.JsonSerializerContext, CancellationToken)`
  - send an empty json object in the body
  - `jsonSerializerContext`: json serializer context if code generation is used
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used.
- `SendErrorsAsync(Generic.List<FluentValidation.Results.ValidationFailure>, int, Json.Serialization.JsonSerializerContext, CancellationToken)`
  - send a 400 bad request with error details of the current validation failures
  - `failures`: the collection of failures
  - `statusCode`: the http status code for the error response
  - `jsonSerializerContext`: json serializer context if code generation is used
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used.
- `SendEventStreamAsync(Generic.IAsyncEnumerable<StreamItem>, CancellationToken)`
  - start a "server-sent-events" data stream for the client asynchronously without blocking any threads
  - `eventStream`: an IAsyncEnumerable that is the source of the data
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used.
- `SendEventStreamAsync<T>(string, Generic.IAsyncEnumerable<T1>, CancellationToken)`
  - start a "server-sent-events" data stream for the client asynchronously without blocking any threads
  - `eventName`: the name of the event stream
  - `eventStream`: an IAsyncEnumerable that is the source of the data
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used.
  - `<T>`: the type of the objects being sent in the event stream
- `SendFileAsync(FileInfo, string, Nullable<DateTimeOffset>, bool, CancellationToken)`
  - send a file to the client
  - `fileInfo`
  - `contentType`: optional content type to set on the http response
  - `lastModified`: optional last modified date-time-offset for the data stream
  - `enableRangeProcessing`: optional switch for enabling range processing
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used.
- `SendForbiddenAsync(CancellationToken)`
  - send a 403 unauthorized response
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used.
- `SendHeadersAsync(Action<Microsoft.AspNetCore.Http.IHeaderDictionary>, int, CancellationToken)`
  - send headers in response to a HEAD request
  - `headers`: an action to be performed on the headers dictionary of the response
  - `statusCode`: optional custom http status code
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used.
- `SendNoContentAsync(CancellationToken)`
  - send a 204 no content response
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used.
- `SendNotFoundAsync(CancellationToken)`
  - send a 404 not found response
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used.
- `SendNotModifiedAsync(CancellationToken)`
  - send a 304 not modified response
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used.
- `SendOkAsync(CancellationToken)`
  - send an http 200 ok response without a body.
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used.
- `SendOkAsync<T>(T1, Json.Serialization.JsonSerializerContext, CancellationToken)`
  - send an http 200 ok response with the supplied response dto serialized as json to the client.
  - `response`: the object to serialize to json
  - `jsonSerializerContext`: json serializer context if code generation is used
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used.
- `SendRedirectAsync(string, bool, bool)`
  - send a 302/301 redirect response
  - `location`: the location to redirect to
  - `isPermanent`: set to true for a 301 redirect. 302 is the default.
  - `allowRemoteRedirects`: set to true if it's ok to redirect to remote addresses, which is prone to open redirect attacks.
- `SendResultAsync(Microsoft.AspNetCore.Http.IResult)`
  - execute and send any `IResult` produced by the `Results` or `TypedResults` classes in minimal apis.
  - `result`: the `IResult` instance to execute such as from:
`- Results.Ok();
- TypedResults.NotFound();`
- `SendStatusCodeAsync(int, CancellationToken)`
  - send any http status code
  - `statusCode`: the http status code
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used.
- `SendStreamAsync(Stream, string, Nullable<long>, string, Nullable<DateTimeOffset>, bool, CancellationToken)`
  - send the contents of a stream to the client
  - `stream`: the stream to read the data from
  - `fileName`: and optional file name to set in the content-disposition header
  - `fileLengthBytes`: optional total size of the file/stream
  - `contentType`: optional content type to set on the http response
  - `lastModified`: optional last modified date-time-offset for the data stream
  - `enableRangeProcessing`: optional switch for enabling range processing
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used.
- `SendStringAsync(string, int, string, CancellationToken)`
  - send the supplied string content to the client.
  - `content`: the string to write to the response body
  - `statusCode`: optional custom http status code
  - `contentType`: optional content type header value
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used.
- `SendUnauthorizedAsync(CancellationToken)`
  - send a 401 unauthorized response
  - `cancellation`: optional cancellation token. if not specified, the `HttpContext.RequestAborted` token is used.


### namespace `FastEndpoints.LoggingExtensions`

#### `__LogUnStructuredExceptionStruct`

This API supports the logging infrastructure and is not intended to be used directly from your code. It is subject to change in the future.


### namespace `FastEndpoints.ProblemDetails`

#### `Error`

the error details object

**Properties:**

- `Code`
  - the code of the error
- `Name`
  - the name of the error or property of the dto that caused the error
- `Reason`
  - the reason for the error
- `Severity`
  - the severity of the error


### namespace `FastEndpoints.TestingExtensions`

#### `<G>$7B30185E57B8298C6754F16C0BCF4773`

**Methods:**

- `RegisterTestCommandHandler<T1, T2, T3>`
  - register test/fake/mock command handlers for integration testing commands that returns a result
  - `<TCommand>`: the type of the command model to register a test handler for
  - `<THandler>`: the type of the test command handler
  - `<TResult>`: the type of the result
- `RegisterTestCommandHandler<T1, T2>`
  - register test/fake/mock command handlers for integration testing commands that don't return a result
  - `<TCommand>`: the type of the command model to register a test handler for
  - `<THandler>`: the type of the test command handler
- `RegisterTestCommandReceivers`
  - registers test command receivers for the purpose of testing receipt of commands.
- `RegisterTestEventHandler<T1, T2>`
  - register test/fake/mock event handlers for integration testing events
  - `<TEvent>`: the type of the event model to register a test handler for
  - `<THandler>`: the type of the test event handler
- `RegisterTestEventReceivers`
  - registers test event receivers for the purpose of testing receipt of events.


#### `<G>$AEA33270220B6BEE5910F5E99F6B03EE`

**Methods:**

- `GetTestCommandReceiver<T>`
  - gets a test command receiver for a given command type.
  - `<TCommand>`: the type of the command
- `GetTestEventReceiver<T>`
  - gets a test event receiver for a given event type.
  - `<TEvent>`: the type of the event


### namespace `System.Text.RegularExpressions.Generated`

#### `LetterOrDigitRegex_1`

Custom `Regex`-derived type for the LetterOrDigitRegex method.

**Methods:**

- `#ctor`
  - Initializes the instance.

**Fields:**

- `Instance`
  - Cached, thread-safe singleton instance.


#### `RouteBuilderRegex_0`

Custom `Regex`-derived type for the RouteBuilderRegex method.

**Methods:**

- `#ctor`
  - Initializes the instance.

**Fields:**

- `Instance`
  - Cached, thread-safe singleton instance.


#### `Utilities`

Helper methods used by generated `Regex`-derived implementations.

**Methods:**

- `IsWordChar(char)`
  - Determines whether the character is part of the [\w] set.

**Fields:**

- `s_asciiLettersAndDigits`
  - Supports searching for characters in or not in "0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz".
- `s_defaultTimeout`
  - Default timeout value set in `AppContext`, or `InfiniteMatchTimeout` if none was set.
- `s_hasTimeout`
  - Whether `s_defaultTimeout` is non-infinite.


### namespace `System.Text.RegularExpressions.Generated.LetterOrDigitRegex_1`

#### `RunnerFactory`

Provides a factory for creating `RegexRunner` instances to be used by methods on `Regex`.

**Methods:**

- `CreateInstance`
  - Creates an instance of a `RegexRunner` used by methods on `Regex`.


### namespace `System.Text.RegularExpressions.Generated.LetterOrDigitRegex_1.RunnerFactory`

#### `Runner`

Provides the runner that contains the custom logic implementing the specified regular expression.

**Methods:**

- `Scan(ReadOnlySpan<char>)`
  - Scan the inputSpan starting from base.runtextstart for the next match.
  - `inputSpan`: The text being scanned by the regular expression.
- `TryFindNextPossibleStartingPosition(ReadOnlySpan<char>)`
  - Search inputSpan starting from base.runtextpos for the next location a match could possibly start.
  - `inputSpan`: The text being scanned by the regular expression.
  - returns: true if a possible match was found; false if no more matches are possible.
- `TryMatchAtCurrentPosition(ReadOnlySpan<char>)`
  - Determine whether inputSpan at base.runtextpos is a match for the regular expression.
  - `inputSpan`: The text being scanned by the regular expression.
  - returns: true if the regular expression matches at the current position; otherwise, false.


### namespace `System.Text.RegularExpressions.Generated.RouteBuilderRegex_0`

#### `RunnerFactory`

Provides a factory for creating `RegexRunner` instances to be used by methods on `Regex`.

**Methods:**

- `CreateInstance`
  - Creates an instance of a `RegexRunner` used by methods on `Regex`.


### namespace `System.Text.RegularExpressions.Generated.RouteBuilderRegex_0.RunnerFactory`

#### `Runner`

Provides the runner that contains the custom logic implementing the specified regular expression.

**Methods:**

- `Scan(ReadOnlySpan<char>)`
  - Scan the inputSpan starting from base.runtextstart for the next match.
  - `inputSpan`: The text being scanned by the regular expression.
- `TryFindNextPossibleStartingPosition(ReadOnlySpan<char>)`
  - Search inputSpan starting from base.runtextpos for the next location a match could possibly start.
  - `inputSpan`: The text being scanned by the regular expression.
  - returns: true if a possible match was found; false if no more matches are possible.
- `TryMatchAtCurrentPosition(ReadOnlySpan<char>)`
  - Determine whether inputSpan at base.runtextpos is a match for the regular expression.
  - `inputSpan`: The text being scanned by the regular expression.
  - returns: true if the regular expression matches at the current position; otherwise, false.



## package `FastEndpoints.Swagger` v8.1.0

### namespace `FastEndpoints.Swagger`

#### `AutoTagOverride`

represents an auto-tag override value.

**Methods:**

- `#ctor(string)`
  - represents an auto-tag override value.
  - `tagName`


#### `DocumentOptions`

options for the swagger document

**Methods:**

- `#ctor(IServiceProvider)`
  - options for the swagger document

**Properties:**

- `AutoTagPathSegmentIndex`
  - the index of the route path segment to use for tagging/grouping endpoints. set 0 to disable auto tagging.
- `DocumentSettings`
  - a function for configuring the swagger document generator settings
- `EnableGetRequestsWithBody`
  - by default GET request DTO properties are automatically converted to query parameters because fetch-client/swagger ui doesn't support it.
set this to true if for some reason you'd like to disable this auto conversion and allow GET requests with a body.
- `EnableJWTBearerAuth`
  - set to `false` to disable auto addition of jwt bearer auth support
- `EndpointFilter`
  - a function to filter out endpoints from the swagger document.
this function will be run against every fast endpoint discovered.
return true to include the endpoint and return false to exclude the endpoint from the swagger doc.
- `ExcludeNonFastEndpoints`
  - if set to true, only FastEndpoints will show up in the swagger doc
- `FlattenSchema`
  - enabling this flattens the inheritance hierarchy of all the schema.
- `MaxEndpointVersion`
  - endpoints greater than this version will not be included in this swagger doc.
- `MinEndpointVersion`
  - endpoints lower than this version will not be included in the swagger doc.
- `NewtonsoftSettings`
  - any additional newtonsoft serializer settings. most useful for registering custom converters.
- `ReleaseVersion`
  - specify a "release version" for this swagger document. you can exclude endpoints from showing up under this swagger doc by specifying a higher
number than this on the endpoint like so:
`Version(x).StartingRelease(2)`
i.e. if the starting release of the endpoint is higher than the release version of this swagger doc, that endpoint will not show up for this
swagger doc.
- `RemoveEmptyRequestSchema`
  - set to true for removing empty request dto schema from the swagger document.


WARNING: enabling this also flattens the inheritance hierarchy of the schema.
- `SerializerSettings`
  - json serializer options
- `Services`
  - service provider instance for resolving any services from the di container
- `ShortSchemaNames`
  - set to true if you'd like schema names to be just the class name instead of the full name.
- `ShowDeprecatedOps`
  - by default deprecated endpoints/operations will not show up in the swagger doc.
set this to true if you instead want them to show up but displayed as "obsolete".
- `SwaggerExportPath`
  - the path where swagger documents will be exported. set via SwaggerExportPath MSBuild property (default: wwwroot/openapi).
- `TagCase`
  - the casing strategy to use when naming endpoint tags.
- `TagDescriptions`
  - specify swagger tag descriptions for the document.
the key of the dictionary is the name of the tag to add a description for.
- `TagStripSymbols`
  - specify whether to strip non-alphanumeric characters from tags.
- `UseOneOfForPolymorphism`
  - by setting this to `true`, you can have base class types as request/response dtos and get swagger to generate possible derived types within a `oneOf`
field.
for this to take effect, you must correctly annotate the base type as follows:
`[JsonPolymorphic(TypeDiscriminatorPropertyName = "_t")]
[JsonDerivedType(typeof(Apple), "a")]
[JsonDerivedType(typeof(Orange), "o")]
public class FruitBase
{
...
}`
- `UsePropertyNamingPolicy`
  - specify if `PropertyNamingPolicy` should be used by the default swagger operation processor for
identifying/matching schema properties. default is 'true'.


#### `Extensions`

a set of extension methods for adding swagger support

**Methods:**

- `AddAuth(NSwag.Generation.OpenApiDocumentGeneratorSettings, string, NSwag.OpenApiSecurityScheme, Generic.IEnumerable<string>)`
  - add swagger auth for this open api document
  - `schemeName`: the authentication scheme
  - `securityScheme`: an open api security scheme object
  - `globalScopeNames`: a collection of global scope names
- `AutoTagOverride(Microsoft.AspNetCore.Builder.IEndpointConventionBuilder, string)`
  - when path based auto-tagging is enabled, you can use this method to specify an override tag name if necessary.
  - `tag`: the tag name to use instead of the auto tag
- `ConfigureDefaults(NSwag.AspNetCore.SwaggerUiSettings, Action<NSwag.AspNetCore.SwaggerUiSettings>)`
  - configure swagger ui with some sensible defaults for FastEndpoints which can be overridden if needed.
  - `settings`: provide an action that overrides any of the defaults
- `DeActivateTryItOut(NSwag.AspNetCore.SwaggerUiSettings)`
  - the "Try It Out" button is activated by default. call this method to de-activate it by default.
set `EnableTryItOut` to `false` to remove the button from ui.
- `EnableFastEndpoints(NSwag.Generation.AspNetCore.AspNetCoreOpenApiDocumentGeneratorSettings, Action<Swagger.DocumentOptions>, IServiceProvider)`
  - enable support for FastEndpoints in swagger
  - `documentOptions`: the document options
  - `serviceProvider`: the service provider
- `EnableJWTBearerAuth(NSwag.Generation.AspNetCore.AspNetCoreOpenApiDocumentGeneratorSettings)`
  - enable jwt bearer authorization support
- `ExportSwaggerDocsAndExitAsync(Microsoft.AspNetCore.Builder.WebApplication, string[])`
  - exports swagger.json files to disk (ONLY DURING NATIVE AOT PUBLISHING) and exits the program.


HINT: make sure to place the call straight after `app.UseFastEndpoints()`


to enable automatic export during AOT publish builds, add this to your .csproj:
`<PropertyGroup>
<ExportSwaggerDocs>true</ExportSwaggerDocs>
</PropertyGroup>`


to customize the export path, add this to your .csproj:
`<PropertyGroup>
<SwaggerExportPath>wwwroot/swagger</SwaggerExportPath>
</PropertyGroup>`


to force generate swagger docs outside a AOT publish, run the following in a terminal:
`dotnet run --export-swagger-docs true -p:PublishAot=false`
optionally specify the output folder:
`dotnet run --export-swagger-docs true -p:PublishAot=false -p:SwaggerExportPath=wwwroot/swagger`
  - `documentNames`: the swagger document names to export. these must match the names used in `.SwaggerDocument()` configuration.
- `GetEndpointDefinition(NSwag.Generation.Processors.Contexts.OperationProcessorContext)`
  - gets the `EndpointDefinition` from the nswag operation processor context if this is a FastEndpoint operation. otherwise returns null.
- `GetExampleFromMetaData(Microsoft.AspNetCore.Http.Metadata.IProducesResponseTypeMetadata)`
  - gets the example object if any, from a given `DefaultProducesResponseMetadata` internal class
- `MarkNonNullablePropsAsRequired(NSwag.Generation.AspNetCore.AspNetCoreOpenApiDocumentGeneratorSettings)`
  - mark all non-nullable properties of the schema as required in the swagger document.
this may only be needed for TS client generation with OAS3 swagger definitions.
- `ShowOperationIDs(NSwag.AspNetCore.SwaggerUiSettings)`
  - displays the swagger operation id in the swagger ui
- `SwaggerDocument(Microsoft.Extensions.DependencyInjection.IServiceCollection, Action<Swagger.DocumentOptions>)`
  - enable support for FastEndpoints and create a swagger document.
  - `options`: swagger document configuration options
- `SwaggerIgnore<T1, T2>(FluentValidation.IRuleBuilderOptions<T1,T2>, FluentValidation.ApplyConditionTo)`
  - disable swagger+fluentvalidation integration for a property rule
  - `applyConditionTo`
  - `<T>`
  - `<TProperty>`
- `UseSwaggerGen(Microsoft.AspNetCore.Builder.IApplicationBuilder, Action<NSwag.AspNetCore.OpenApiDocumentMiddlewareSettings>, Action<NSwag.AspNetCore.SwaggerUiSettings>)`
  - enables the open-api/swagger middleware for fastendpoints.
this method is simply a shortcut for the two calls [`app.UseOpenApi()`] and [`app.UseSwaggerUi3(c => c.ConfigureDefaults())`]
  - `config`: optional config action for the open-api middleware
  - `uiConfig`: optional config action for the swagger-ui

**Properties:**

- `SelectedJsonNamingPolicy`
  - JsonNamingPolicy chosen for swagger


#### `GlobalConfig`

gives access to the fastendpoints global configuration settings

**Properties:**

- `AllowEmptyRequestDtos`
  - allows the use of empty request dtos
- `EndpointRoutePrefix`
  - prefix for all routes (example 'api').
- `IsUsingAspVersioning`
  - Asp.Versioning.Http library is being used for versioning
- `RouteConstraintMap`
  - this route constraint type map will be used to determine the type for a route parameter if there's no matching property on the request dto.
the dictionary key is the name of the constraint and the value is the corresponding `Type`
- `VersioningPrefix`
  - the prefix used in front of the version (for example 'v' produces 'v{version}').


#### `OperationProcessor`

**Methods:**

- `RouteConstraintsRegex`
  - remarks: Pattern:
`(?<={)([^?:}]+)[^}]*(?=})`
Explanation:
`○ Zero-width positive lookbehind.
○ Match '{' right-to-left.
○ 1st capture group.
○ Match a character in the set [^:?}] greedily at least once.
○ Match a character other than '}' atomically any number of times.
○ Zero-width positive lookahead.
○ Match '}'.`
- `RouteParamsRegex`
  - remarks: Pattern:
`(?<={)(?:.*?)*(?=})`
Explanation:
`○ Zero-width positive lookbehind.
○ Match '{' right-to-left.
○ Loop greedily any number of times.
○ Match a character other than '\n' lazily any number of times.
○ Zero-width positive lookahead.
○ Match '}'.`


#### `SwaggerExportRunner`

marker type for swagger export logging


#### `TagCase`

enum values for swagger tag naming strategy


### namespace `FastEndpoints.Swagger.OperationProcessor`

#### `ParamCreationContext`

**Methods:**

- `MyRegex`
  - remarks: Pattern:
`\\{[^{}]*:[^{}]*\\}`
Explanation:
`○ Match '{'.
○ Match a character in the set [^{}] greedily any number of times.
○ Match ':'.
○ Match a character in the set [^{}] atomically any number of times.
○ Match '}'.`


### namespace `FastEndpoints.Swagger.ValidationProcessor`

#### `FluentValidationRule`

**Properties:**

- `Apply`
  - Modify Swagger schema action.
- `Matches`
  - Predicate to match property validator.


### namespace `FastEndpoints.Swagger.ValidationProcessor.Extensions`

#### `IgnoreAllStringComparer`

Returns string equality only by symbols ignore case.
It can be used for comparing camelCase, PascalCase, snake_case, kebab-case identifiers.

**Methods:**

- `Compare(string, string)`
- `Equals(string, string)`
- `GetHashCode(string)`

**Fields:**

- `Instance`
  - Instance of StringComparer


#### `StringExtensions`

**Methods:**

- `EqualsIgnoreAll(string, string)`
  - Returns string equality only by symbols ignore case.
It can be used for comparing camelCase, PascalCase, snake_case, kebab-case identifiers.
  - `left`: Left string to compare.
  - `right`: Right string to compare.
  - returns: `true` if input strings are equals in terms of identifier formatting.
- `ToLowerCamelCase(string)`
  - Converts string to lowerCamelCase.
  - `inputString`: Input string.
  - returns: lowerCamelCase string.


#### `ValidationExtensions`

Extensions for some swagger specific work.

**Methods:**

- `ConvertToSchemaCasing(string, Json.JsonNamingPolicy)`
  - Converts a property name (route of) to the schema casing by using the selected JsonNamingPolicy
  - `propertyName`
  - `namingPolicy`
  - remarks: The property name can have points as it defines the object composition hierarchy
- `GetDictionaryOfRules(FluentValidation.IValidator)`
  - Creates a dictionary with the validation rules.
Keys are the property names of the rules, converted to the schema casing by using the selected JsonNamingPolicy
  - `validator`
- `IsNumeric(object)`
  - Is supported swagger numeric type.
- `NotNull<T>(Generic.IEnumerable<T1>)`
  - Returns not null enumeration.


### namespace `FastEndpoints.Swagger.ValidationProcessor.Extensions.ValidationExtensions`

#### `ValidationRuleContext`

Contains `IValidationRule` and additional info.

**Methods:**

- `#ctor(FluentValidation.IValidationRule, bool)`
  - Initializes a new instance of the `ValidationRuleContext` struct.
  - `validationRule`: PropertyRule.
  - `isCollectionRule`: Is a CollectionPropertyRule.

**Fields:**

- `IsCollectionRule`
  - Flag indication whether the `IValidationRule` is the CollectionRule.
- `ValidationRule`
  - PropertyRule.


### namespace `NJsonSchema.Generation`

#### `SystemTextJsonUtilities`

Utility methods for dealing with System.Text.Json.

**Methods:**

- `ConvertJsonOptionsToNewtonsoftSettings(object)`
  - Converts System.Text.Json serializer options to Newtonsoft JSON settings.
  - `serializerOptions`: The options.
  - returns: The settings.


### namespace `System.Text.RegularExpressions.Generated`

#### `MyRegex_2`

Custom `Regex`-derived type for the MyRegex method.

**Methods:**

- `#ctor`
  - Initializes the instance.

**Fields:**

- `Instance`
  - Cached, thread-safe singleton instance.


#### `RouteConstraintsRegex_1`

Custom `Regex`-derived type for the RouteConstraintsRegex method.

**Methods:**

- `#ctor`
  - Initializes the instance.

**Fields:**

- `Instance`
  - Cached, thread-safe singleton instance.


#### `RouteParamsRegex_0`

Custom `Regex`-derived type for the RouteParamsRegex method.

**Methods:**

- `#ctor`
  - Initializes the instance.

**Fields:**

- `Instance`
  - Cached, thread-safe singleton instance.


#### `Utilities`

Helper methods used by generated `Regex`-derived implementations.

**Methods:**

- `StackPop(int[], int@, int@, int@)`
  - Pops 2 values from the backtracking stack.
- `StackPush(int[]@, int@, int)`
  - Pushes 1 value onto the backtracking stack.
- `StackPush(int[]@, int@, int, int)`
  - Pushes 2 values onto the backtracking stack.

**Fields:**

- `s_defaultTimeout`
  - Default timeout value set in `AppContext`, or `InfiniteMatchTimeout` if none was set.
- `s_hasTimeout`
  - Whether `s_defaultTimeout` is non-infinite.


### namespace `System.Text.RegularExpressions.Generated.MyRegex_2`

#### `RunnerFactory`

Provides a factory for creating `RegexRunner` instances to be used by methods on `Regex`.

**Methods:**

- `CreateInstance`
  - Creates an instance of a `RegexRunner` used by methods on `Regex`.


### namespace `System.Text.RegularExpressions.Generated.MyRegex_2.RunnerFactory`

#### `Runner`

Provides the runner that contains the custom logic implementing the specified regular expression.

**Methods:**

- `Scan(ReadOnlySpan<char>)`
  - Scan the inputSpan starting from base.runtextstart for the next match.
  - `inputSpan`: The text being scanned by the regular expression.
- `TryFindNextPossibleStartingPosition(ReadOnlySpan<char>)`
  - Search inputSpan starting from base.runtextpos for the next location a match could possibly start.
  - `inputSpan`: The text being scanned by the regular expression.
  - returns: true if a possible match was found; false if no more matches are possible.
- `TryMatchAtCurrentPosition(ReadOnlySpan<char>)`
  - Determine whether inputSpan at base.runtextpos is a match for the regular expression.
  - `inputSpan`: The text being scanned by the regular expression.
  - returns: true if the regular expression matches at the current position; otherwise, false.


### namespace `System.Text.RegularExpressions.Generated.RouteConstraintsRegex_1`

#### `RunnerFactory`

Provides a factory for creating `RegexRunner` instances to be used by methods on `Regex`.

**Methods:**

- `CreateInstance`
  - Creates an instance of a `RegexRunner` used by methods on `Regex`.


### namespace `System.Text.RegularExpressions.Generated.RouteConstraintsRegex_1.RunnerFactory`

#### `Runner`

Provides the runner that contains the custom logic implementing the specified regular expression.

**Methods:**

- `Scan(ReadOnlySpan<char>)`
  - Scan the inputSpan starting from base.runtextstart for the next match.
  - `inputSpan`: The text being scanned by the regular expression.
- `TryFindNextPossibleStartingPosition(ReadOnlySpan<char>)`
  - Search inputSpan starting from base.runtextpos for the next location a match could possibly start.
  - `inputSpan`: The text being scanned by the regular expression.
  - returns: true if a possible match was found; false if no more matches are possible.
- `TryMatchAtCurrentPosition(ReadOnlySpan<char>)`
  - Determine whether inputSpan at base.runtextpos is a match for the regular expression.
  - `inputSpan`: The text being scanned by the regular expression.
  - returns: true if the regular expression matches at the current position; otherwise, false.


### namespace `System.Text.RegularExpressions.Generated.RouteParamsRegex_0`

#### `RunnerFactory`

Provides a factory for creating `RegexRunner` instances to be used by methods on `Regex`.

**Methods:**

- `CreateInstance`
  - Creates an instance of a `RegexRunner` used by methods on `Regex`.


### namespace `System.Text.RegularExpressions.Generated.RouteParamsRegex_0.RunnerFactory`

#### `Runner`

Provides the runner that contains the custom logic implementing the specified regular expression.

**Methods:**

- `Scan(ReadOnlySpan<char>)`
  - Scan the inputSpan starting from base.runtextstart for the next match.
  - `inputSpan`: The text being scanned by the regular expression.
- `TryMatchAtCurrentPosition(ReadOnlySpan<char>)`
  - Determine whether inputSpan at base.runtextpos is a match for the regular expression.
  - `inputSpan`: The text being scanned by the regular expression.
  - returns: true if the regular expression matches at the current position; otherwise, false.



## package `FastEndpoints.Security` v8.1.0

### namespace `FastEndpoints.Security`

#### `AuthExtensions`

a set of auth related extensions

**Methods:**

- `Add(Generic.List<Claims.Claim>, Claims.Claim[])`
  - adds multiple `Claim`s to the list.
  - `claims`: the `Claim`s to append to the list.
- `Add(Generic.List<Claims.Claim>, ValueTuple<string,string>[])`
  - adds multiple `Claim`s to the list.
  - `claims`: the claim `Type` & `Value` tuples to add to the list.
- `Add(Generic.List<string>, string[])`
  - adds multiple strings to a list.
  - `values`: the strings to append to the list.
- `AddAuthenticationCookie(Microsoft.Extensions.DependencyInjection.IServiceCollection, TimeSpan, Action<Microsoft.AspNetCore.Authentication.Cookies.CookieAuthenticationOptions>)`
  - configure and enable cookie based authentication
  - `validFor`: specify how long the created cookie is valid for with a `TimeSpan`
  - `options`: optional action for configuring cookie authentication options
- `AddAuthenticationJwtBearer(Microsoft.Extensions.DependencyInjection.IServiceCollection, Action<Security.JwtSigningOptions>, Action<Microsoft.AspNetCore.Authentication.JwtBearer.JwtBearerOptions>)`
  - configure and enable jwt bearer authentication
  - `signingOptions`: an action to configure `JwtSigningOptions`
  - `bearerOptions`: an action to configure `JwtBearerOptions`
- `ClaimValue(Claims.ClaimsPrincipal, string)`
  - get the claim value for a given claim type of the current user principal. if the user doesn't have the requested claim type, a null will be returned.
  - `claimType`: the claim type to look for
- `HasClaimType(Claims.ClaimsPrincipal, string)`
  - determines if the current user principal has the given claim type
  - `claimType`: the claim type to check for
- `HasPermission(Claims.ClaimsPrincipal, string)`
  - returns true of the current user principal has a given permission code.
  - `permissionCode`: the permission code to check for


#### `CookieAuth`

static class for easy cookie based auth

**Methods:**

- `SignInAsync(Action<UserPrivileges>, Action<Microsoft.AspNetCore.Authentication.AuthenticationProperties>)`
  - creates the auth cookie and adds it to the current http response
  - `privileges`: the privileges to be assigned to the user such as claims, permissions, and roles
  - `properties`: an optional action to configure authentication properties
- `SignOutAsync(Action<Microsoft.AspNetCore.Authentication.AuthenticationProperties>)`
  - signs the user out from the cookie authentication scheme
  - `properties`: an optional action to configure authentication properties


#### `JwtBearer`

static class for easy creation of jwt bearer tokens

**Methods:**

- `CreateToken(Action<Security.JwtCreationOptions>)`
  - generates jwt tokens with supplied settings.
  - `options`: action to configure jwt creation options.


#### `JwtCreationOptions`

options for creating jwt tokens

**Properties:**

- `AsymmetricKidGenerator`
  - if specified, this function will be used to generate a `kid` for asymmetric key generation.
the `string` value returned from this function will be set on the `RsaSecurityKey`.`KeyId` property.
- `Audience`
  - the value for the 'audience' claim.
- `CompressionAlgorithm`
  - the compression algorithm compressing the token payload.
- `ExpireAt`
  - the value of the 'expiration' claim. should be in utc.
NOTE: this should be set at the time of token creation.
- `Issuer`
  - the issuer
- `KeyIsPemEncoded`
  - specifies whether the key is pem encoded.
- `SigningAlgorithm`
  - security algorithm used to sign keys.
  - remarks: defaults to HmacSha256 for symmetric keys. don't forget to set an appropriate algorithm when changing `SigningStyle` to
`Asymmetric`
- `SigningKey`
  - the key used to sign jwts symmetrically or the base64 encoded private-key when jwts are signed asymmetrically.
  - remarks: the key can be in PEM format. make sure to set `KeyIsPemEncoded` to `true` if the key is PEM encoded.
- `SigningStyle`
  - specifies how tokens are to be signed. symmetrically or asymmetrically.
  - remarks: don't forget to set an appropriate `SigningAlgorithm` if changing to `Symmetric`
- `User`
  - specify the privileges of the user
NOTE: this should be specified at the time of jwt creation.


#### `JwtRevocationExtensions`

**Methods:**

- `UseJwtRevocation<T>(Microsoft.AspNetCore.Builder.IApplicationBuilder)`
  - adds an implementation of `JwtRevocationMiddleware` to the pipeline for the purpose of checking incoming jwt bearer tokens for validity.
  - `<T>`: implementation type of the token revocation middleware


#### `JwtRevocationMiddleware`

abstract class for implementing a jwt revocation middleware

**Methods:**

- `#ctor(Microsoft.AspNetCore.Http.RequestDelegate)`
  - abstract class for implementing a jwt revocation middleware
  - `next`: the next request delegate to execute
- `JwtTokenIsValidAsync(string, CancellationToken)`
  - implement this method and return whether the supplied jwt token is still valid or not.
  - `jwtToken`: the jwt token that should be checked against a blacklist.
  - `ct`: cancellation token
  - returns: true if the token is valid
- `SendTokenRevokedResponseAsync(Microsoft.AspNetCore.Http.HttpContext, CancellationToken)`
  - override this method in order to customize the unauthorized response that is sent when the jwt token is no longer valid.
  - `ctx`: the http context
  - `ct`: cancellation token


#### `JwtSigningOptions`

jwt signing options for consuming jwts.

**Methods:**

- `UpdateSigningKey(string)`
  - call this method to update the jwt signing key during runtime. all future token verifications will use the supplied key.
  - `key`: the new jwt signing key to use for generating a `SecurityKey`

**Properties:**

- `KeyIsPemEncoded`
  - specifies whether the key is pem encoded.
- `SigningKey`
  - the key used to sign jwts symmetrically or the base64 encoded public-key when jwts are signed asymmetrically.
the key can be optional when used to verify tokens issued by an idp where public key retrieval happens dynamically.
  - remarks: the key can be in PEM format. make sure to set `KeyIsPemEncoded` to `true` if the key is PEM encoded.
- `SigningStyle`
  - specifies how tokens were signed. symmetrically or asymmetrically.


#### `Permissions`

inherit from this class and define your applications permissions as `public const string`


`public const string Inventory_Create_Item = "100";
public const string Inventory_Retrieve_Item = "101";
public const string Inventory_Update_Item = "102";
public const string Inventory_Delete_Item = "103";`

**Methods:**

- `AllCodes`
  - get a list of all permission codes
- `AllNames`
  - get a list of all permission names
- `CodesFor(Generic.IEnumerable<string>)`
  - get a list of permission codes for a given list of permission names
  - `names`: the permission names to get the codes for
- `GetEnumerator`
- `NamesFor(Generic.IEnumerable<string>)`
  - gets a list of permission names for the given list of permission codes
  - `codes`: the permission codes to get the permission names for
- `PermissionFromCode(string)`
  - get the permission tuple using it's code. returns null if not found
  - `permissionCode`: code of the permission to get
- `PermissionFromName(string)`
  - get the permission tuple using it's name. returns null if not found
  - `permissionName`: name of the permission


#### `RefreshServiceOptions`

**Methods:**

- `Endpoint(string, Action<EndpointDefinition>)`
  - endpoint configuration action
  - `refreshEndpointRoute`: the route of the refresh token endpoint
  - `ep`: the action to be performed on the endpoint definition

**Properties:**

- `AccessTokenValidity`
  - specifies how long the access token should be valid for. default is 5 minutes.
- `Audience`
  - specifies the token audience
- `Issuer`
  - specifies the token issuer
- `RefreshTokenValidity`
  - specifies how long the refresh token should be valid for. default is 4 hours.
- `SigningKeyIsPemEncoded`
  - specifies whether the key is pem encoded.
- `TokenCompressionAlgorithm`
  - the compression algorithm compressing the token payload.
- `TokenSigningAlgorithm`
  - security algo used to sign tokens.
defaults to HmacSha256 for symmetric keys.
- `TokenSigningKey`
  - specifies the secret key used to sign the jwt.
an exception will be thrown if a value is not specified when global `JwtCreationOptions` is not configured.
i.e. if global `JwtCreationOptions` is configured, you don't need to set the following properties because the values will come from the globally
configured settings:


`TokenSigningKey` / `TokenSigningStyle` / `TokenSigningAlgorithm` / `Issuer` / `Audience`
- `TokenSigningStyle`
  - specifies the signing style of the jwt. default is symmetric.


#### `RefreshTokenService<T1, T2>`

implement this class to define your own refresh token endpoints.

**Methods:**

- `Configure`
  - WARNING: do not call this method!
- `CreateCustomToken<T>(string, Action<UserPrivileges>, Func<T2,T1>, bool, object)`
  - create a token response and map it to a different type. useful if you need to create the token manually by yourself.
  - `userId`: the id of the user to create the token for
  - `privileges`: the user privileges to be embedded in the jwt such as roles/claims/permissions
  - `map`: a func that maps properties from TResponse to T
  - `isRenewal`: specify if this is an initial login request or a renewal/refresh request
  - `request`: the request dto
  - `<T>`: the type to map to
- `HandleAsync(T1, CancellationToken)`
  - WARNING: do not call this method!
- `OnAfterInitialTokenCreationAsync(object, T2)`
  - a hook for modifying the created token response when a login request comes in.
  - `request`: the request dto. maybe null unless you supply it to the `CreateTokenWith<T>` method.
  - `response`: the token response dto that is created
- `OnAfterRenewalTokenCreationAsync(T1, T2)`
  - a hook for modifying the created token response when a renewal request comes in.
  - `request`: the request dto. maybe null unless you supply it to the `CreateTokenWith<T>` method.
  - `response`: the token response dto that is created
- `OnBeforeInitialTokenCreationAsync(Security.JwtCreationOptions, object)`
  - a hook for modifying jwt creation options per request when a login request comes in. this method is called right before the actual jwt token is created
allowing you to override token creation parameters per request if needed.
  - `jwtOptions`: jwt token creation options which you can modify per request
  - `request`: the request dto. maybe null unless you supply it to the `CreateTokenWith<T>` method.
- `OnBeforeRenewalTokenCreationAsync(Security.JwtCreationOptions, T1)`
  - a hook for modifying jwt creation options per request when a renewal request comes in. this method is called right before the actual jwt token is created
allowing you to override token creation parameters per request if needed.
  - `jwtOptions`: jwt token creation options which you can modify per request
  - `request`: the request dto. maybe null unless you supply it to the `CreateTokenWith<T>` method.
- `PersistTokenAsync(T2)`
  - this method will be called whenever a new access/refresh token pair is being generated.
store the tokens and expiry dates however you wish for the purpose of verifying future refresh requests.
  - `response`: the response dto containing the tokens that's about to be sent to the requesting client
- `RefreshRequestValidationAsync(T1)`
  - validate the incoming refresh request by checking the token and expiry against the previously stored data.
if the token is not valid and a new token pair should not be created, simply add validation errors using the `AddError()` method.
the failures you add will be sent to the requesting client. if no failures are added, validation passes and a new token pair will be created and sent to
the client.
  - `req`: the incoming refresh request dto
- `SetRenewalPrivilegesAsync(T1, UserPrivileges)`
  - specify the user privileges to be embedded in the jwt when a refresh request is received and validation has passed.
this only applies to renewal/refresh requests received to the refresh endpoint and not the initial jwt creation.
  - `request`: the request dto received from the client
  - `privileges`: the user privileges to be embedded in the jwt such as roles/claims/permissions
- `Setup(Action<Security.RefreshServiceOptions>)`
  - configure the refresh token service options
  - `options`: action to be performed on the refresh service options object


#### `TokenRequest`

base dto for access/refresh token renewal requests

**Properties:**

- `RefreshToken`
  - a single-use refresh token which will be valid for the duration specified by `RefreshExpiry`
- `UserId`
  - unique identifier of a user


#### `TokenResponse`

base dto for access/refresh token responses

**Properties:**

- `AccessExpiry`
  - the expiry date-time of the access token
- `AccessToken`
  - the jwt access token which will be valid for the duration specified by `AccessExpiry`
- `RefreshExpiry`
  - the expiry date-time of the refresh token


#### `TokenSigningStyle`

token signing style enum



## package `FastEndpoints.Validation` v3.11.0

### namespace `FastEndpoints.Validation`

#### `AbstractComparisonValidator<T1, T2>`

Base class for all comparison validators

**Methods:**

- `#ctor(Func<T1,T2>, MemberInfo, string)`
  - `valueToCompareFunc`
  - `member`
  - `memberDisplayName`
- `#ctor(Func<T1,ValueTuple<bool,T2>>, MemberInfo, string)`
  - `valueToCompareFunc`
  - `member`
  - `memberDisplayName`
- `#ctor(T2)`
  - `value`
- `IsValid(T2, T2)`
  - Override to perform the comparison
  - `value`
  - `valueToCompare`
- `IsValid(Validation.ValidationContext<T1>, T2)`
  - Performs the comparison
  - `context`
  - `propertyValue`

**Properties:**

- `Comparison`
  - Metadata- the comparison type
- `FastEndpoints#Validation#IComparisonValidator#ValueToCompare`
  - Comparison value as non-generic for metadata.
- `MemberToCompare`
  - Metadata- the member being compared
- `ValueToCompare`
  - The value being compared


#### `AbstractValidator<T>`

Base class for object validators.

**Methods:**

- `CreateDescriptor`
  - Creates a `IValidatorDescriptor` that can be used to obtain metadata about the current validator.
- `EnsureInstanceNotNull(object)`
  - Throws an exception if the instance being validated is null.
  - `instanceToValidate`
- `GetEnumerator`
  - Returns an enumerator that iterates through the collection of validation rules.
  - returns: A `IEnumerator<T>` that can be used to iterate through the collection.
- `Include(Validation.IValidator<T1>)`
  - Includes the rules from the specified validator
- `Include<T>(Func<T1,T1>)`
  - Includes the rules from the specified validator
- `PreValidate(Validation.ValidationContext<T1>, Validation.ValidationResult)`
  - Determines if validation should occur and provides a means to modify the context and ValidationResult prior to execution.
If this method returns false, then the ValidationResult is immediately returned from Validate/ValidateAsync.
  - `context`
  - `result`
- `RaiseValidationException(Validation.ValidationContext<T1>, Validation.ValidationResult)`
  - Throws a ValidationException. This method will only be called if the validator has been configured
to throw exceptions if validation fails. The default behaviour is not to throw an exception.
  - `context`
  - `result`
- `RuleFor<T>(Expressions.Expression<Func<T1,T1>>)`
  - Defines a validation rule for a specify property.
  - `expression`: The expression representing the property to validate
  - `<TProperty>`: The type of property being validated
  - returns: an IRuleBuilder instance on which validators can be defined
- `RuleForEach<T>(Expressions.Expression<Func<T1,Generic.IEnumerable<T1>>>)`
  - Invokes a rule for each item in the collection.
  - `expression`: Expression representing the collection to validate
  - `<TElement>`: Type of property
  - returns: An IRuleBuilder instance on which validators can be defined
- `RuleSet(string, Action)`
  - Defines a RuleSet that can be used to group together several validators.
  - `ruleSetName`: The name of the ruleset.
  - `action`: Action that encapsulates the rules in the ruleset.
- `Transform<T1, T2>(Expressions.Expression<Func<T1,T1>>, Func<T1,T1,T2>)`
  - Defines a validation rule for a specify property and transform it to a different type.
  - `from`: The expression representing the property to transform
  - `to`: Function to transform the property value into a different type
  - `<TProperty>`: The type of property being validated
  - `<TTransformed>`: The type after the transformer has been applied
  - returns: an IRuleBuilder instance on which validators can be defined
- `Transform<T1, T2>(Expressions.Expression<Func<T1,T1>>, Func<T1,T2>)`
  - Defines a validation rule for a specify property and transform it to a different type.
  - `from`: The expression representing the property to transform
  - `to`: Function to transform the property value into a different type
  - `<TProperty>`: The type of property being validated
  - `<TTransformed>`: The type after the transformer has been applied
  - returns: an IRuleBuilder instance on which validators can be defined
- `TransformForEach<T1, T2>(Expressions.Expression<Func<T1,Generic.IEnumerable<T1>>>, Func<T1,T1,T2>)`
  - Invokes a rule for each item in the collection, transforming the element from one type to another.
  - `expression`: Expression representing the collection to validate
  - `to`: Function to transform the collection element into a different type
  - `<TElement>`: Type of property
  - `<TTransformed>`: The type after the transformer has been applied
  - returns: An IRuleBuilder instance on which validators can be defined
- `TransformForEach<T1, T2>(Expressions.Expression<Func<T1,Generic.IEnumerable<T1>>>, Func<T1,T2>)`
  - Invokes a rule for each item in the collection, transforming the element from one type to another.
  - `expression`: Expression representing the collection to validate
  - `to`: Function to transform the collection element into a different type
  - `<TElement>`: Type of property
  - `<TTransformed>`: The type after the transformer has been applied
  - returns: An IRuleBuilder instance on which validators can be defined
- `Unless(Func<T1,Validation.ValidationContext<T1>,bool>, Action)`
  - Defines an inverse condition that applies to several rules
  - `predicate`: The condition that should be applied to multiple rules
  - `action`: Action that encapsulates the rules
- `Unless(Func<T1,bool>, Action)`
  - Defines an inverse condition that applies to several rules
  - `predicate`: The condition that should be applied to multiple rules
  - `action`: Action that encapsulates the rules
- `UnlessAsync(Func<T1,CancellationToken,Tasks.Task<bool>>, Action)`
  - Defines an inverse asynchronous condition that applies to several rules
  - `predicate`: The asynchronous condition that should be applied to multiple rules
  - `action`: Action that encapsulates the rules
- `UnlessAsync(Func<T1,Validation.ValidationContext<T1>,CancellationToken,Tasks.Task<bool>>, Action)`
  - Defines an inverse asynchronous condition that applies to several rules
  - `predicate`: The asynchronous condition that should be applied to multiple rules
  - `action`: Action that encapsulates the rules
- `Validate(T1)`
  - Validates the specified instance
  - `instance`: The object to validate
  - returns: A ValidationResult object containing any validation failures
- `Validate(Validation.ValidationContext<T1>)`
  - Validates the specified instance.
  - `context`: Validation Context
  - returns: A ValidationResult object containing any validation failures.
- `ValidateAsync(T1, CancellationToken)`
  - Validates the specified instance asynchronously
  - `instance`: The object to validate
  - `cancellation`: Cancellation token
  - returns: A ValidationResult object containing any validation failures
- `ValidateAsync(Validation.ValidationContext<T1>, CancellationToken)`
  - Validates the specified instance asynchronously.
  - `context`: Validation Context
  - `cancellation`: Cancellation token
  - returns: A ValidationResult object containing any validation failures.
- `When(Func<T1,Validation.ValidationContext<T1>,bool>, Action)`
  - Defines a condition that applies to several rules
  - `predicate`: The condition that should apply to multiple rules
  - `action`: Action that encapsulates the rules.
- `When(Func<T1,bool>, Action)`
  - Defines a condition that applies to several rules
  - `predicate`: The condition that should apply to multiple rules
  - `action`: Action that encapsulates the rules.
- `WhenAsync(Func<T1,CancellationToken,Tasks.Task<bool>>, Action)`
  - Defines an asynchronous condition that applies to several rules
  - `predicate`: The asynchronous condition that should apply to multiple rules
  - `action`: Action that encapsulates the rules.
- `WhenAsync(Func<T1,Validation.ValidationContext<T1>,CancellationToken,Tasks.Task<bool>>, Action)`
  - Defines an asynchronous condition that applies to several rules
  - `predicate`: The asynchronous condition that should apply to multiple rules
  - `action`: Action that encapsulates the rules.

**Properties:**

- `CascadeMode`
  - Sets the cascade mode for all rules within this validator.


#### `AccessorCache<T>`

Member accessor cache.

**Methods:**

- `GetCachedAccessor<T>(MemberInfo, Expressions.Expression<Func<T1,T1>>, bool, string)`
  - Gets an accessor func based on an expression
  - `member`: The member represented by the expression
  - `expression`
  - `bypassCache`
  - `cachePrefix`: Cache prefix
  - `<TProperty>`
  - returns: Accessor func


#### `ApplyConditionTo`

Specifies where a When/Unless condition should be applied

**Fields:**

- `AllValidators`
  - Applies the condition to all validators declared so far in the chain.
- `CurrentValidator`
  - Applies the condition to the current validator only.


#### `AsyncConditionBuilder<T>`

**Methods:**

- `UnlessAsync(Func<T1,Validation.ValidationContext<T1>,CancellationToken,Tasks.Task<bool>>, Action)`
  - Defines an inverse asynchronous condition that applies to several rules
  - `predicate`: The asynchronous condition that should be applied to multiple rules
  - `action`: Action that encapsulates the rules
- `WhenAsync(Func<T1,Validation.ValidationContext<T1>,CancellationToken,Tasks.Task<bool>>, Action)`
  - Defines an asynchronous condition that applies to several rules
  - `predicate`: The asynchronous condition that should apply to multiple rules
  - `action`: Action that encapsulates the rules.


#### `AsyncPredicateValidator<T1, T2>`

Asynchronous custom validator

**Methods:**

- `#ctor(Func<T1,T2,Validation.ValidationContext<T1>,CancellationToken,Tasks.Task<bool>>)`
  - Creates a new AsyncPredicateValidator
  - `predicate`


#### `AsyncPropertyValidator<T1, T2>`

**Methods:**

- `GetDefaultMessageTemplate(string)`
  - Returns the default error message template for this validator, when not overridden.
  - `errorCode`: The currently configured error code for the validator.
- `IsValidAsync(Validation.ValidationContext<T1>, T2, CancellationToken)`
- `Localized(string, string)`
  - Retrieves a localized string from the LanguageManager.
If an ErrorCode is defined for this validator, the error code is used as the key.
If no ErrorCode is defined (or the language manager doesn't have a translation for the error code)
then the fallback key is used instead.
  - `errorCode`: The currently configured error code for the validator.
  - `fallbackKey`: The fallback key to use for translation, if no ErrorCode is available.
  - returns: The translated error message template.

**Properties:**

- `Name`


#### `CascadeMode`

Specifies how rules should cascade when one fails.

**Fields:**

- `Continue`
  - When a rule fails, execution continues to the next rule.
- `Stop`
  - When a rule fails, validation is immediately halted.
- `StopOnFirstFailure`
  - When a rule fails, validation is stopped and all other rules in the chain will not be executed.


#### `CollectionPropertyRule<T1, T2>`

Rule definition for collection properties

**Methods:**

- `#ctor(MemberInfo, Func<T1,Generic.IEnumerable<T2>>, Expressions.LambdaExpression, Func<Validation.CascadeMode>, Type)`
  - Initializes new instance of the CollectionPropertyRule class
- `Create(Expressions.Expression<Func<T1,Generic.IEnumerable<T2>>>, Func<Validation.CascadeMode>, bool)`
  - Creates a new property rule from a lambda expression.
- `CreateTransformed<T>(Expressions.Expression<Func<T1,Generic.IEnumerable<T1>>>, Func<T1,T1,T2>, Func<Validation.CascadeMode>, bool)`
  - Creates a new property rule from a lambda expression.
- `CreateTransformed<T>(Expressions.Expression<Func<T1,Generic.IEnumerable<T1>>>, Func<T1,T2>, Func<Validation.CascadeMode>, bool)`
  - Creates a new property rule from a lambda expression.

**Properties:**

- `Filter`
  - Filter that should include/exclude items in the collection.
- `IndexBuilder`
  - Constructs the indexer in the property name associated with the error message.
By default this is "[" + index + "]"


#### `ConditionBuilder<T>`

**Methods:**

- `Unless(Func<T1,Validation.ValidationContext<T1>,bool>, Action)`
  - Defines an inverse condition that applies to several rules
  - `predicate`: The condition that should be applied to multiple rules
  - `action`: Action that encapsulates the rules
- `When(Func<T1,Validation.ValidationContext<T1>,bool>, Action)`
  - Defines a condition that applies to several rules
  - `predicate`: The condition that should apply to multiple rules
  - `action`: Action that encapsulates the rules.


#### `CreditCardValidator<T>`

Ensures that the property value is a valid credit card number.


#### `DefaultValidatorExtensions`

Extension methods that provide the default set of validators.

**Methods:**

- `ChildRules<T1, T2>(Validation.IRuleBuilder<T1,T2>, Action<Validation.InlineValidator<T2>>)`
  - Defines child rules for a nested property.
  - `ruleBuilder`: The rule builder.
  - `action`: Callback that will be invoked to build the rules.
  - `<T>`
  - `<TProperty>`
- `CreditCard<T>(Validation.IRuleBuilder<T1,string>)`
  - Defines a credit card validator for the current rule builder that ensures that the specified string is a valid credit card number.
- `Custom<T1, T2>(Validation.IRuleBuilder<T1,T2>, Action<T2,Validation.ValidationContext<T1>>)`
  - Defines a custom validation rule
  - `ruleBuilder`
  - `action`
  - `<T>`
  - `<TProperty>`
- `CustomAsync<T1, T2>(Validation.IRuleBuilder<T1,T2>, Func<T2,Validation.ValidationContext<T1>,CancellationToken,Tasks.Task>)`
  - Defines a custom validation rule
  - `ruleBuilder`
  - `action`
  - `<T>`
  - `<TProperty>`
- `EmailAddress<T>(Validation.IRuleBuilder<T1,string>, Validation.EmailValidationMode)`
  - Defines an email validator on the current rule builder for string properties.
Validation will fail if the value returned by the lambda is not a valid email address.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `mode`: The mode to use for email validation. If set to `Net4xRegex`, then a regular expression will be used. This is the same regex used by the EmailAddressAttribute in .NET 4.x. If set to `AspNetCoreCompatible` then this uses the simplified ASP.NET Core logic for checking an email address, which just checks for the presence of an @ sign.
  - `<T>`: Type of object being validated
- `Empty<T1, T2>(Validation.IRuleBuilder<T1,T2>)`
  - Defines a 'empty' validator on the current rule builder.
Validation will fail if the property is not null, an empty or the default value for the type (for example, 0 for integers)
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `<T>`: Type of object being validated
  - `<TProperty>`: Type of property being validated
- `Equal<T1, T2>(Validation.IRuleBuilder<T1,T2>, Expressions.Expression<Func<T1,T2>>, Generic.IEqualityComparer<T2>)`
  - Defines an 'equals' validator on the current rule builder using a lambda to specify the comparison value.
Validation will fail if the value returned by the lambda is not equal to the value of the property.
For strings, this performs an ordinal comparison unless you specify a different comparer.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `expression`: A lambda expression to provide the comparison value
  - `comparer`: Equality comparer to use
  - `<T>`: The type of object being validated
  - `<TProperty>`: Type of property being validated
- `Equal<T1, T2>(Validation.IRuleBuilder<T1,T2>, T2, Generic.IEqualityComparer<T2>)`
  - Defines an 'equals' validator on the current rule builder.
Validation will fail if the specified value is not equal to the value of the property.
For strings, this performs an ordinal comparison unless you specify a different comparer.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `toCompare`: The value to compare
  - `comparer`: Equality Comparer to use
  - `<T>`: Type of object being validated
  - `<TProperty>`: Type of property being validated
- `Equal<T>(Validation.IRuleBuilder<T1,string>, Expressions.Expression<Func<T1,string>>, Generic.IEqualityComparer<string>)`
  - Defines an 'equals' validator on the current rule builder using a lambda to specify the comparison value.
Validation will fail if the value returned by the lambda is not equal to the value of the property.
For strings, this performs an ordinal comparison unless you specify a different comparer.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `expression`: A lambda expression to provide the comparison value
  - `comparer`: Equality comparer to use
  - `<T>`: The type of object being validated
- `Equal<T>(Validation.IRuleBuilder<T1,string>, string, Generic.IEqualityComparer<string>)`
  - Defines an 'equals' validator on the current rule builder.
Validation will fail if the specified value is not equal to the value of the property.
For strings, this performs an ordinal comparison unless you specify a different comparer.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `toCompare`: The value to compare
  - `comparer`: Equality Comparer to use
  - `<T>`: Type of object being validated
- `ExclusiveBetween<T1, T2>(Validation.IRuleBuilder<T1,Nullable<T2>>, T2, T2)`
  - Defines an 'exclusive between' validator on the current rule builder, but only for properties of types that implement IComparable.
Validation will fail if the value of the property is outside of the specified range. The range is exclusive.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `from`: The lowest allowed value
  - `to`: The highest allowed value
  - `<T>`: Type of object being validated
  - `<TProperty>`: Type of property being validated
- `ExclusiveBetween<T1, T2>(Validation.IRuleBuilder<T1,T2>, T2, T2)`
  - Defines an 'exclusive between' validator on the current rule builder, but only for properties of types that implement IComparable.
Validation will fail if the value of the property is outside of the specified range. The range is exclusive.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `from`: The lowest allowed value
  - `to`: The highest allowed value
  - `<T>`: Type of object being validated
  - `<TProperty>`: Type of property being validated
- `ExclusiveBetween<T1, T2>(Validation.IRuleBuilder<T1,T2>, T2, T2, Generic.IComparer<T2>)`
  - Defines an 'exclusive between' validator on the current rule builder.
Validation will fail if the value of the property is outside of the specified range. The range is exclusive.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `from`: The lowest allowed value
  - `to`: The highest allowed value
  - `comparer`: Comparer to use
  - `<T>`: Type of object being validated
  - `<TProperty>`: Type of property being validated
- `ForEach<T1, T2>(Validation.IRuleBuilder<T1,Generic.IEnumerable<T2>>, Action<Validation.IRuleBuilderInitialCollection<Generic.IEnumerable<T2>,T2>>)`
  - Allows rules to be built against individual elements in the collection.
  - `ruleBuilder`
  - `action`
  - `<T>`
  - `<TElement>`
- `GreaterThan<T1, T2>(Validation.IRuleBuilder<T1,Nullable<T2>>, Expressions.Expression<Func<T1,Nullable<T2>>>)`
  - Defines a 'less than' validator on the current rule builder using a lambda expression.
The validation will succeed if the property value is greater than the specified value.
The validation will fail if the property value is less than or equal to the specified value.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `expression`: The value being compared
  - `<T>`: Type of object being validated
  - `<TProperty>`: Type of property being validated
- `GreaterThan<T1, T2>(Validation.IRuleBuilder<T1,Nullable<T2>>, Expressions.Expression<Func<T1,T2>>)`
  - Defines a 'less than' validator on the current rule builder using a lambda expression.
The validation will succeed if the property value is greater than the specified value.
The validation will fail if the property value is less than or equal to the specified value.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `expression`: The value being compared
  - `<T>`: Type of object being validated
  - `<TProperty>`: Type of property being validated
- `GreaterThan<T1, T2>(Validation.IRuleBuilder<T1,Nullable<T2>>, T2)`
  - Defines a 'greater than' validator on the current rule builder.
The validation will succeed if the property value is greater than the specified value.
The validation will fail if the property value is less than or equal to the specified value.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `valueToCompare`: The value being compared
  - `<T>`: Type of object being validated
  - `<TProperty>`: Type of property being validated
- `GreaterThan<T1, T2>(Validation.IRuleBuilder<T1,T2>, Expressions.Expression<Func<T1,Nullable<T2>>>)`
  - Defines a 'less than' validator on the current rule builder using a lambda expression.
The validation will succeed if the property value is greater than the specified value.
The validation will fail if the property value is less than or equal to the specified value.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `expression`: The value being compared
  - `<T>`: Type of object being validated
  - `<TProperty>`: Type of property being validated
- `GreaterThan<T1, T2>(Validation.IRuleBuilder<T1,T2>, Expressions.Expression<Func<T1,T2>>)`
  - Defines a 'less than' validator on the current rule builder using a lambda expression.
The validation will succeed if the property value is greater than the specified value.
The validation will fail if the property value is less than or equal to the specified value.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `expression`: The value being compared
  - `<T>`: Type of object being validated
  - `<TProperty>`: Type of property being validated
- `GreaterThan<T1, T2>(Validation.IRuleBuilder<T1,T2>, T2)`
  - Defines a 'greater than' validator on the current rule builder.
The validation will succeed if the property value is greater than the specified value.
The validation will fail if the property value is less than or equal to the specified value.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `valueToCompare`: The value being compared
  - `<T>`: Type of object being validated
  - `<TProperty>`: Type of property being validated
- `GreaterThanOrEqualTo<T1, T2>(Validation.IRuleBuilder<T1,Nullable<T2>>, Expressions.Expression<Func<T1,Nullable<T2>>>)`
  - Defines a 'greater than or equal to' validator on the current rule builder using a lambda expression.
The validation will succeed if the property value is greater than or equal the specified value.
The validation will fail if the property value is less than the specified value.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `valueToCompare`: The value being compared
  - `<T>`: Type of object being validated
  - `<TProperty>`: Type of property being validated
- `GreaterThanOrEqualTo<T1, T2>(Validation.IRuleBuilder<T1,Nullable<T2>>, Expressions.Expression<Func<T1,T2>>)`
  - Defines a 'greater than or equal to' validator on the current rule builder using a lambda expression.
The validation will succeed if the property value is greater than or equal the specified value.
The validation will fail if the property value is less than the specified value.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `valueToCompare`: The value being compared
  - `<T>`: Type of object being validated
  - `<TProperty>`: Type of property being validated
- `GreaterThanOrEqualTo<T1, T2>(Validation.IRuleBuilder<T1,Nullable<T2>>, T2)`
  - Defines a 'greater than or equal' validator on the current rule builder.
The validation will succeed if the property value is greater than or equal the specified value.
The validation will fail if the property value is less than the specified value.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `valueToCompare`: The value being compared
  - `<T>`: Type of object being validated
  - `<TProperty>`: Type of property being validated
- `GreaterThanOrEqualTo<T1, T2>(Validation.IRuleBuilder<T1,T2>, Expressions.Expression<Func<T1,Nullable<T2>>>)`
  - Defines a 'greater than' validator on the current rule builder using a lambda expression.
The validation will succeed if the property value is greater than or equal the specified value.
The validation will fail if the property value is less than the specified value.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `valueToCompare`: The value being compared
  - `<T>`: Type of object being validated
  - `<TProperty>`: Type of property being validated
- `GreaterThanOrEqualTo<T1, T2>(Validation.IRuleBuilder<T1,T2>, Expressions.Expression<Func<T1,T2>>)`
  - Defines a 'greater than' validator on the current rule builder using a lambda expression.
The validation will succeed if the property value is greater than or equal the specified value.
The validation will fail if the property value is less than the specified value.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `valueToCompare`: The value being compared
  - `<T>`: Type of object being validated
  - `<TProperty>`: Type of property being validated
- `GreaterThanOrEqualTo<T1, T2>(Validation.IRuleBuilder<T1,T2>, T2)`
  - Defines a 'greater than or equal' validator on the current rule builder.
The validation will succeed if the property value is greater than or equal the specified value.
The validation will fail if the property value is less than the specified value.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `valueToCompare`: The value being compared
  - `<T>`: Type of object being validated
  - `<TProperty>`: Type of property being validated
- `InclusiveBetween<T1, T2>(Validation.IRuleBuilder<T1,Nullable<T2>>, T2, T2)`
  - Defines an 'inclusive between' validator on the current rule builder, but only for properties of types that implement IComparable.
Validation will fail if the value of the property is outside of the specified range. The range is inclusive.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `from`: The lowest allowed value
  - `to`: The highest allowed value
  - `<T>`: Type of object being validated
  - `<TProperty>`: Type of property being validated
- `InclusiveBetween<T1, T2>(Validation.IRuleBuilder<T1,T2>, T2, T2)`
  - Defines an 'inclusive between' validator on the current rule builder, but only for properties of types that implement IComparable.
Validation will fail if the value of the property is outside of the specified range. The range is inclusive.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `from`: The lowest allowed value
  - `to`: The highest allowed value
  - `<T>`: Type of object being validated
  - `<TProperty>`: Type of property being validated
- `InclusiveBetween<T1, T2>(Validation.IRuleBuilder<T1,T2>, T2, T2, Generic.IComparer<T2>)`
  - Defines an 'inclusive between' validator on the current rule builder.
Validation will fail if the value of the property is outside of the specified range. The range is inclusive.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `from`: The lowest allowed value
  - `to`: The highest allowed value
  - `comparer`: Comparer to use
  - `<T>`: Type of object being validated
  - `<TProperty>`: Type of property being validated
- `IsEnumName<T>(Validation.IRuleBuilder<T1,string>, Type, bool)`
  - Defines a enum value validator on the current rule builder that ensures that the specific value is a valid enum name.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `enumType`: The enum whose the string should match any name
  - `caseSensitive`: If the comparison between the string and the enum names should be case sensitive
  - `<T>`: Type of Enum being validated
- `IsInEnum<T1, T2>(Validation.IRuleBuilder<T1,T2>)`
  - Defines a enum value validator on the current rule builder that ensures that the specific value is a valid enum value.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `<T>`: Type of Enum being validated
  - `<TProperty>`: Type of property being validated
- `Length<T>(Validation.IRuleBuilder<T1,string>, Func<T1,int>)`
  - Defines a length validator on the current rule builder, but only for string properties.
Validation will fail if the length of the string is not equal to the length specified.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `exactLength`
  - `<T>`: Type of object being validated
- `Length<T>(Validation.IRuleBuilder<T1,string>, Func<T1,int>, Func<T1,int>)`
  - Defines a length validator on the current rule builder, but only for string properties.
Validation will fail if the length of the string is outside of the specified range. The range is inclusive.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `min`
  - `max`
  - `<T>`: Type of object being validated
- `Length<T>(Validation.IRuleBuilder<T1,string>, int)`
  - Defines a length validator on the current rule builder, but only for string properties.
Validation will fail if the length of the string is not equal to the length specified.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `exactLength`
  - `<T>`: Type of object being validated
- `Length<T>(Validation.IRuleBuilder<T1,string>, int, int)`
  - Defines a length validator on the current rule builder, but only for string properties.
Validation will fail if the length of the string is outside of the specified range. The range is inclusive.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `min`
  - `max`
  - `<T>`: Type of object being validated
- `LessThan<T1, T2>(Validation.IRuleBuilder<T1,Nullable<T2>>, Expressions.Expression<Func<T1,Nullable<T2>>>)`
  - Defines a 'less than' validator on the current rule builder using a lambda expression.
The validation will succeed if the property value is less than the specified value.
The validation will fail if the property value is greater than or equal to the specified value.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `expression`: A lambda that should return the value being compared
  - `<T>`: Type of object being validated
  - `<TProperty>`: Type of property being validated
- `LessThan<T1, T2>(Validation.IRuleBuilder<T1,Nullable<T2>>, Expressions.Expression<Func<T1,T2>>)`
  - Defines a 'less than' validator on the current rule builder using a lambda expression.
The validation will succeed if the property value is less than the specified value.
The validation will fail if the property value is greater than or equal to the specified value.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `expression`: A lambda that should return the value being compared
  - `<T>`: Type of object being validated
  - `<TProperty>`: Type of property being validated
- `LessThan<T1, T2>(Validation.IRuleBuilder<T1,Nullable<T2>>, T2)`
  - Defines a 'less than' validator on the current rule builder.
The validation will succeed if the property value is less than the specified value.
The validation will fail if the property value is greater than or equal to the specified value.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `valueToCompare`: The value being compared
  - `<T>`: Type of object being validated
  - `<TProperty>`: Type of property being validated
- `LessThan<T1, T2>(Validation.IRuleBuilder<T1,T2>, Expressions.Expression<Func<T1,Nullable<T2>>>)`
  - Defines a 'less than' validator on the current rule builder using a lambda expression.
The validation will succeed if the property value is less than the specified value.
The validation will fail if the property value is greater than or equal to the specified value.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `expression`: A lambda that should return the value being compared
  - `<T>`: Type of object being validated
  - `<TProperty>`: Type of property being validated
- `LessThan<T1, T2>(Validation.IRuleBuilder<T1,T2>, Expressions.Expression<Func<T1,T2>>)`
  - Defines a 'less than' validator on the current rule builder using a lambda expression.
The validation will succeed if the property value is less than the specified value.
The validation will fail if the property value is greater than or equal to the specified value.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `expression`: A lambda that should return the value being compared
  - `<T>`: Type of object being validated
  - `<TProperty>`: Type of property being validated
- `LessThan<T1, T2>(Validation.IRuleBuilder<T1,T2>, T2)`
  - Defines a 'less than' validator on the current rule builder.
The validation will succeed if the property value is less than the specified value.
The validation will fail if the property value is greater than or equal to the specified value.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `valueToCompare`: The value being compared
  - `<T>`: Type of object being validated
  - `<TProperty>`: Type of property being validated
- `LessThanOrEqualTo<T1, T2>(Validation.IRuleBuilder<T1,Nullable<T2>>, Expressions.Expression<Func<T1,Nullable<T2>>>)`
  - Defines a 'less than or equal' validator on the current rule builder using a lambda expression.
The validation will succeed if the property value is less than or equal to the specified value.
The validation will fail if the property value is greater than the specified value.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `expression`: The value being compared
  - `<T>`: Type of object being validated
  - `<TProperty>`: Type of property being validated
- `LessThanOrEqualTo<T1, T2>(Validation.IRuleBuilder<T1,Nullable<T2>>, Expressions.Expression<Func<T1,T2>>)`
  - Defines a 'less than or equal' validator on the current rule builder using a lambda expression.
The validation will succeed if the property value is less than or equal to the specified value.
The validation will fail if the property value is greater than the specified value.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `expression`: The value being compared
  - `<T>`: Type of object being validated
  - `<TProperty>`: Type of property being validated
- `LessThanOrEqualTo<T1, T2>(Validation.IRuleBuilder<T1,Nullable<T2>>, T2)`
  - Defines a 'less than or equal' validator on the current rule builder.
The validation will succeed if the property value is less than or equal to the specified value.
The validation will fail if the property value is greater than the specified value.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `valueToCompare`: The value being compared
  - `<T>`: Type of object being validated
  - `<TProperty>`: Type of property being validated
- `LessThanOrEqualTo<T1, T2>(Validation.IRuleBuilder<T1,T2>, Expressions.Expression<Func<T1,Nullable<T2>>>)`
  - Defines a 'less than or equal' validator on the current rule builder using a lambda expression.
The validation will succeed if the property value is less than or equal to the specified value.
The validation will fail if the property value is greater than the specified value.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `expression`: The value being compared
  - `<T>`: Type of object being validated
  - `<TProperty>`: Type of property being validated
- `LessThanOrEqualTo<T1, T2>(Validation.IRuleBuilder<T1,T2>, Expressions.Expression<Func<T1,T2>>)`
  - Defines a 'less than or equal' validator on the current rule builder using a lambda expression.
The validation will succeed if the property value is less than or equal to the specified value.
The validation will fail if the property value is greater than the specified value.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `expression`: The value being compared
  - `<T>`: Type of object being validated
  - `<TProperty>`: Type of property being validated
- `LessThanOrEqualTo<T1, T2>(Validation.IRuleBuilder<T1,T2>, T2)`
  - Defines a 'less than or equal' validator on the current rule builder.
The validation will succeed if the property value is less than or equal to the specified value.
The validation will fail if the property value is greater than the specified value.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `valueToCompare`: The value being compared
  - `<T>`: Type of object being validated
  - `<TProperty>`: Type of property being validated
- `Matches<T>(Validation.IRuleBuilder<T1,string>, Func<T1,RegularExpressions.Regex>)`
  - Defines a regular expression validator on the current rule builder, but only for string properties.
Validation will fail if the value returned by the lambda does not match the regular expression.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `regex`: The regular expression to use
  - `<T>`: Type of object being validated
- `Matches<T>(Validation.IRuleBuilder<T1,string>, Func<T1,string>)`
  - Defines a regular expression validator on the current rule builder, but only for string properties.
Validation will fail if the value returned by the lambda does not match the regular expression.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `expression`: The regular expression to check the value against.
  - `<T>`: Type of object being validated
- `Matches<T>(Validation.IRuleBuilder<T1,string>, Func<T1,string>, RegularExpressions.RegexOptions)`
  - Defines a regular expression validator on the current rule builder, but only for string properties.
Validation will fail if the value returned by the lambda does not match the regular expression.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `expression`: The regular expression to check the value against.
  - `options`: Regex options
  - `<T>`: Type of object being validated
- `Matches<T>(Validation.IRuleBuilder<T1,string>, RegularExpressions.Regex)`
  - Defines a regular expression validator on the current rule builder, but only for string properties.
Validation will fail if the value returned by the lambda does not match the regular expression.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `regex`: The regular expression to use
  - `<T>`: Type of object being validated
- `Matches<T>(Validation.IRuleBuilder<T1,string>, string)`
  - Defines a regular expression validator on the current rule builder, but only for string properties.
Validation will fail if the value returned by the lambda does not match the regular expression.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `expression`: The regular expression to check the value against.
  - `<T>`: Type of object being validated
- `Matches<T>(Validation.IRuleBuilder<T1,string>, string, RegularExpressions.RegexOptions)`
  - Defines a regular expression validator on the current rule builder, but only for string properties.
Validation will fail if the value returned by the lambda does not match the regular expression.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `expression`: The regular expression to check the value against.
  - `options`: Regex options
  - `<T>`: Type of object being validated
- `MaximumLength<T>(Validation.IRuleBuilder<T1,string>, int)`
  - Defines a length validator on the current rule builder, but only for string properties.
Validation will fail if the length of the string is larger than the length specified.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `maximumLength`
  - `<T>`: Type of object being validated
- `MinimumLength<T>(Validation.IRuleBuilder<T1,string>, int)`
  - Defines a length validator on the current rule builder, but only for string properties.
Validation will fail if the length of the string is less than the length specified.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `minimumLength`
  - `<T>`: Type of object being validated
- `Must<T1, T2>(Validation.IRuleBuilder<T1,T2>, Func<T1,T2,Validation.ValidationContext<T1>,bool>)`
  - Defines a predicate validator on the current rule builder using a lambda expression to specify the predicate.
Validation will fail if the specified lambda returns false.
Validation will succeed if the specified lambda returns true.
This overload accepts the object being validated in addition to the property being validated.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `predicate`: A lambda expression specifying the predicate
  - `<T>`: Type of object being validated
  - `<TProperty>`: Type of property being validated
- `Must<T1, T2>(Validation.IRuleBuilder<T1,T2>, Func<T1,T2,bool>)`
  - Defines a predicate validator on the current rule builder using a lambda expression to specify the predicate.
Validation will fail if the specified lambda returns false.
Validation will succeed if the specified lambda returns true.
This overload accepts the object being validated in addition to the property being validated.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `predicate`: A lambda expression specifying the predicate
  - `<T>`: Type of object being validated
  - `<TProperty>`: Type of property being validated
- `Must<T1, T2>(Validation.IRuleBuilder<T1,T2>, Func<T2,bool>)`
  - Defines a predicate validator on the current rule builder using a lambda expression to specify the predicate.
Validation will fail if the specified lambda returns false.
Validation will succeed if the specified lambda returns true.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `predicate`: A lambda expression specifying the predicate
  - `<T>`: Type of object being validated
  - `<TProperty>`: Type of property being validated
- `MustAsync<T1, T2>(Validation.IRuleBuilder<T1,T2>, Func<T1,T2,CancellationToken,Tasks.Task<bool>>)`
  - Defines an asynchronous predicate validator on the current rule builder using a lambda expression to specify the predicate.
Validation will fail if the specified lambda returns false.
Validation will succeed if the specified lambda returns true.
This overload accepts the object being validated in addition to the property being validated.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `predicate`: A lambda expression specifying the predicate
  - `<T>`: Type of object being validated
  - `<TProperty>`: Type of property being validated
- `MustAsync<T1, T2>(Validation.IRuleBuilder<T1,T2>, Func<T1,T2,Validation.ValidationContext<T1>,CancellationToken,Tasks.Task<bool>>)`
  - Defines an asynchronous predicate validator on the current rule builder using a lambda expression to specify the predicate.
Validation will fail if the specified lambda returns false.
Validation will succeed if the specified lambda returns true.
This overload accepts the object being validated in addition to the property being validated.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `predicate`: A lambda expression specifying the predicate
  - `<T>`: Type of object being validated
  - `<TProperty>`: Type of property being validated
- `MustAsync<T1, T2>(Validation.IRuleBuilder<T1,T2>, Func<T2,CancellationToken,Tasks.Task<bool>>)`
  - Defines an asynchronous predicate validator on the current rule builder using a lambda expression to specify the predicate.
Validation will fail if the specified lambda returns false.
Validation will succeed if the specified lambda returns true.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `predicate`: A lambda expression specifying the predicate
  - `<T>`: Type of object being validated
  - `<TProperty>`: Type of property being validated
- `NotEmpty<T1, T2>(Validation.IRuleBuilder<T1,T2>)`
  - Defines a 'not empty' validator on the current rule builder.
Validation will fail if the property is null, an empty string, whitespace, an empty collection or the default value for the type (for example, 0 for integers but null for nullable integers)
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `<T>`: Type of object being validated
  - `<TProperty>`: Type of property being validated
- `NotEqual<T1, T2>(Validation.IRuleBuilder<T1,T2>, Expressions.Expression<Func<T1,T2>>, Generic.IEqualityComparer<T2>)`
  - Defines a 'not equal' validator on the current rule builder using a lambda to specify the value.
Validation will fail if the value returned by the lambda is equal to the value of the property.
For strings, this performs an ordinal comparison unless you specify a different comparer.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `expression`: A lambda expression to provide the comparison value
  - `comparer`: Equality Comparer to use
  - `<T>`: Type of object being validated
  - `<TProperty>`: Type of property being validated
- `NotEqual<T1, T2>(Validation.IRuleBuilder<T1,T2>, T2, Generic.IEqualityComparer<T2>)`
  - Defines a 'not equal' validator on the current rule builder.
Validation will fail if the specified value is equal to the value of the property.
For strings, this performs an ordinal comparison unless you specify a different comparer.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `toCompare`: The value to compare
  - `comparer`: Equality comparer to use
  - `<T>`: Type of object being validated
  - `<TProperty>`: Type of property being validated
- `NotEqual<T>(Validation.IRuleBuilder<T1,string>, Expressions.Expression<Func<T1,string>>, Generic.IEqualityComparer<string>)`
  - Defines a 'not equal' validator on the current rule builder using a lambda to specify the value.
Validation will fail if the value returned by the lambda is equal to the value of the property.
For strings, this performs an ordinal comparison unless you specify a different comparer.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `expression`: A lambda expression to provide the comparison value
  - `comparer`: Equality Comparer to use
  - `<T>`: Type of object being validated
- `NotEqual<T>(Validation.IRuleBuilder<T1,string>, string, Generic.IEqualityComparer<string>)`
  - Defines a 'not equal' validator on the current rule builder.
Validation will fail if the specified value is equal to the value of the property.
For strings, this performs an ordinal comparison unless you specify a different comparer.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `toCompare`: The value to compare
  - `comparer`: Equality comparer to use
  - `<T>`: Type of object being validated
- `NotNull<T1, T2>(Validation.IRuleBuilder<T1,T2>)`
  - Defines a 'not null' validator on the current rule builder.
Validation will fail if the property is null.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `<T>`: Type of object being validated
  - `<TProperty>`: Type of property being validated
- `Null<T1, T2>(Validation.IRuleBuilder<T1,T2>)`
  - Defines a 'null' validator on the current rule builder.
Validation will fail if the property is not null.
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `<T>`: Type of object being validated
  - `<TProperty>`: Type of property being validated
- `ScalePrecision<T>(Validation.IRuleBuilder<T1,Nullable<decimal>>, int, int, bool)`
  - Defines a scale precision validator on the current rule builder that ensures that the specific value has a certain scale and precision
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `scale`: Allowed scale of the value
  - `precision`: Allowed precision of the value
  - `ignoreTrailingZeros`: Whether the validator will ignore trailing zeros.
  - `<T>`: Type of object being validated
- `ScalePrecision<T>(Validation.IRuleBuilder<T1,decimal>, int, int, bool)`
  - Defines a scale precision validator on the current rule builder that ensures that the specific value has a certain scale and precision
  - `ruleBuilder`: The rule builder on which the validator should be defined
  - `scale`: Allowed scale of the value
  - `precision`: Allowed precision of the value
  - `ignoreTrailingZeros`: Whether the validator will ignore trailing zeros.
  - `<T>`: Type of object being validated
- `SetAsyncValidator<T1, T2>(Validation.IRuleBuilder<T1,Nullable<T2>>, Validation.IAsyncPropertyValidator<T1,T2>)`
  - Associates an async validator with this the property for this rule builder.
This overload handles type conversion for nullable value types, allowing a validator for TProperty to be applied to a property of type Nullable<TProperty>
  - `ruleBuilder`
  - `validator`: The validator to set
- `SetInheritanceValidator<T1, T2>(Validation.IRuleBuilder<T1,T2>, Action<Validation.PolymorphicValidator<T1,T2>>)`
  - Defines one or more validators that can be used to validate sub-classes or implementors
in an inheritance hierarchy. This is useful when the property being validated is an interface
or base-class, but you want to define rules for properties of a specific subclass.
  - `ruleBuilder`
  - `validatorConfiguration`: Callback for setting up the inheritance validators.
- `SetValidator<T1, T2>(Validation.IRuleBuilder<T1,Nullable<T2>>, Validation.IPropertyValidator<T1,T2>)`
  - Associates a validator with this the property for this rule builder.
This overload handles type conversion for nullable value types, allowing a validator for TProperty to be applied to a property of type Nullable<TProperty>
  - `ruleBuilder`
  - `validator`: The validator to set
- `SetValidator<T1, T2>(Validation.IRuleBuilder<T1,T2>, Validation.PropertyValidator)`
  - Associates a legacy property validator with this rule.
  - `rule`
  - `legacyPropertyValidator`: The validator to set
- `Validate<T>(Validation.IValidator<T1>, T1, Action<Validation.ValidationStrategy<T1>>)`
  - Validates the specified instance using a combination of extra options
  - `validator`: The validator
  - `instance`: The instance to validate
  - `options`: Callback to configure additional options
  - `<T>`
- `ValidateAndThrow<T>(Validation.IValidator<T1>, T1)`
  - Performs validation and then throws an exception if validation fails.
This method is a shortcut for: Validate(instance, options => options.ThrowOnFailures());
  - `validator`: The validator this method is extending.
  - `instance`: The instance of the type we are validating.
- `ValidateAndThrowAsync<T>(Validation.IValidator<T1>, T1, CancellationToken)`
  - Performs validation asynchronously and then throws an exception if validation fails.
This method is a shortcut for: ValidateAsync(instance, options => options.ThrowOnFailures());
  - `validator`: The validator this method is extending.
  - `instance`: The instance of the type we are validating.
  - `cancellationToken`
- `ValidateAsync<T>(Validation.IValidator<T1>, T1, Action<Validation.ValidationStrategy<T1>>, CancellationToken)`
  - Validates the specified instance using a combination of extra options
  - `validator`: The validator
  - `instance`: The instance to validate
  - `cancellation`: Cancellation token
  - `options`: Callback to configure additional options
  - `<T>`


#### `DefaultValidatorOptions`

Default options that can be used to configure a validator.

**Methods:**

- `Cascade<T1, T2>(Validation.IRuleBuilderInitial<T1,T2>, Validation.CascadeMode)`
  - Specifies the cascade mode for failures.
If set to 'Stop' then execution of the rule will stop once the first validator in the chain fails.
If set to 'Continue' then all validators in the chain will execute regardless of failures.
- `Cascade<T1, T2>(Validation.IRuleBuilderInitialCollection<T1,T2>, Validation.CascadeMode)`
  - Specifies the cascade mode for failures.
If set to 'Stop' then execution of the rule will stop once the first validator in the chain fails.
If set to 'Continue' then all validators in the chain will execute regardless of failures.
- `Configurable<T1, T2>(Validation.IRuleBuilder<T1,T2>)`
  - Gets the configurable rule instance from a rule builder.
  - `ruleBuilder`: The rule builder.
  - returns: A configurable IValidationRule instance.
- `Configurable<T1, T2>(Validation.IRuleBuilderInitialCollection<T1,T2>)`
  - Gets the configurable rule instance from a rule builder.
  - `ruleBuilder`: The rule builder.
  - returns: A configurable IValidationRule instance.
- `Configure<T1, T2>(Validation.IRuleBuilderInitial<T1,T2>, Action<Validation.IValidationRule<T1,T2>>)`
  - Configures the rule.
  - `ruleBuilder`
  - `configurator`: Action to configure the object.
- `Configure<T1, T2>(Validation.IRuleBuilderInitialCollection<T1,T2>, Action<Validation.ICollectionRule<T1,T2>>)`
  - Configures the rule object.
  - `ruleBuilder`
  - `configurator`: Action to configure the object.
- `Configure<T1, T2>(Validation.IRuleBuilderOptions<T1,T2>, Action<Validation.IValidationRule<T1,T2>>)`
  - Configures the current object.
  - `ruleBuilder`
  - `configurator`: Action to configure the object.
- `OnAnyFailure<T1, T2>(Validation.IRuleBuilderOptions<T1,T2>, Action<T1,Generic.IEnumerable<Validation.ValidationFailure>>)`
  - Specifies a custom action to be invoked when the validator fails.
  - `rule`
  - `onFailure`
  - `<T>`
  - `<TProperty>`
- `OnAnyFailure<T1, T2>(Validation.IRuleBuilderOptions<T1,T2>, Action<T1>)`
  - Specifies a custom action to be invoked when the validator fails.
  - `rule`
  - `onFailure`
  - `<T>`
  - `<TProperty>`
- `OnFailure<T1, T2>(Validation.IRuleBuilderOptions<T1,T2>, Action<T1,Validation.ValidationContext<T1>,T2,string>)`
  - Specifies custom method that will be called when specific rule fails
  - `rule`
  - `onFailure`
  - `<T>`
  - `<TProperty>`
- `OnFailure<T1, T2>(Validation.IRuleBuilderOptions<T1,T2>, Action<T1,Validation.ValidationContext<T1>,T2>)`
  - Specifies custom method that will be called when specific rule fails
  - `rule`
  - `onFailure`
  - `<T>`
  - `<TProperty>`
- `OnFailure<T1, T2>(Validation.IRuleBuilderOptions<T1,T2>, Action<T1>)`
  - Specifies custom method that will be called when specific rule fails
  - `rule`
  - `onFailure`
  - `<T>`
  - `<TProperty>`
- `OverrideIndexer<T1, T2>(Validation.IRuleBuilderInitialCollection<T1,T2>, Func<T1,Generic.IEnumerable<T2>,T2,int,string>)`
  - Allows the generated indexer to be overridden for collection rules.
  - `rule`: The current rule
  - `callback`: The callback. Receives the model, the collection, the current element and the current index as parameters. Should return a string representation of the indexer. The default is "[" + index + "]"
- `OverridePropertyName<T1, T2>(Validation.IRuleBuilderOptions<T1,T2>, Expressions.Expression<Func<T1,object>>)`
  - Overrides the name of the property associated with this rule.
NOTE: This is a considered to be an advanced feature. Most of the time that you use this, you actually meant to use WithName.
  - `rule`: The current rule
  - `expr`: An expression referencing another property
- `OverridePropertyName<T1, T2>(Validation.IRuleBuilderOptions<T1,T2>, string)`
  - Overrides the name of the property associated with this rule.
NOTE: This is a considered to be an advanced feature. Most of the time that you use this, you actually meant to use WithName.
  - `rule`: The current rule
  - `propertyName`: The property name to use
- `Unless<T1, T2>(Validation.IRuleBuilderOptions<T1,T2>, Func<T1,Validation.ValidationContext<T1>,bool>, Validation.ApplyConditionTo)`
  - Specifies a condition limiting when the validator should not run.
The validator will only be executed if the result of the lambda returns false.
  - `rule`: The current rule
  - `predicate`: A lambda expression that specifies a condition for when the validator should not run
  - `applyConditionTo`: Whether the condition should be applied to the current rule or all rules in the chain
- `Unless<T1, T2>(Validation.IRuleBuilderOptions<T1,T2>, Func<T1,bool>, Validation.ApplyConditionTo)`
  - Specifies a condition limiting when the validator should not run.
The validator will only be executed if the result of the lambda returns false.
  - `rule`: The current rule
  - `predicate`: A lambda expression that specifies a condition for when the validator should not run
  - `applyConditionTo`: Whether the condition should be applied to the current rule or all rules in the chain
- `Unless<T1, T2>(Validation.IRuleBuilderOptionsConditions<T1,T2>, Func<T1,Validation.ValidationContext<T1>,bool>, Validation.ApplyConditionTo)`
  - Specifies a condition limiting when the validator should not run.
The validator will only be executed if the result of the lambda returns false.
  - `rule`: The current rule
  - `predicate`: A lambda expression that specifies a condition for when the validator should not run
  - `applyConditionTo`: Whether the condition should be applied to the current rule or all rules in the chain
- `Unless<T1, T2>(Validation.IRuleBuilderOptionsConditions<T1,T2>, Func<T1,bool>, Validation.ApplyConditionTo)`
  - Specifies a condition limiting when the validator should not run.
The validator will only be executed if the result of the lambda returns false.
  - `rule`: The current rule
  - `predicate`: A lambda expression that specifies a condition for when the validator should not run
  - `applyConditionTo`: Whether the condition should be applied to the current rule or all rules in the chain
- `UnlessAsync<T1, T2>(Validation.IRuleBuilderOptions<T1,T2>, Func<T1,CancellationToken,Tasks.Task<bool>>, Validation.ApplyConditionTo)`
  - Specifies an asynchronous condition limiting when the validator should not run.
The validator will only be executed if the result of the lambda returns false.
  - `rule`: The current rule
  - `predicate`: A lambda expression that specifies a condition for when the validator should not run
  - `applyConditionTo`: Whether the condition should be applied to the current rule or all rules in the chain
- `UnlessAsync<T1, T2>(Validation.IRuleBuilderOptions<T1,T2>, Func<T1,Validation.ValidationContext<T1>,CancellationToken,Tasks.Task<bool>>, Validation.ApplyConditionTo)`
  - Specifies an asynchronous condition limiting when the validator should not run.
The validator will only be executed if the result of the lambda returns false.
  - `rule`: The current rule
  - `predicate`: A lambda expression that specifies a condition for when the validator should not run
  - `applyConditionTo`: Whether the condition should be applied to the current rule or all rules in the chain
- `UnlessAsync<T1, T2>(Validation.IRuleBuilderOptionsConditions<T1,T2>, Func<T1,CancellationToken,Tasks.Task<bool>>, Validation.ApplyConditionTo)`
  - Specifies an asynchronous condition limiting when the validator should not run.
The validator will only be executed if the result of the lambda returns false.
  - `rule`: The current rule
  - `predicate`: A lambda expression that specifies a condition for when the validator should not run
  - `applyConditionTo`: Whether the condition should be applied to the current rule or all rules in the chain
- `UnlessAsync<T1, T2>(Validation.IRuleBuilderOptionsConditions<T1,T2>, Func<T1,Validation.ValidationContext<T1>,CancellationToken,Tasks.Task<bool>>, Validation.ApplyConditionTo)`
  - Specifies an asynchronous condition limiting when the validator should not run.
The validator will only be executed if the result of the lambda returns false.
  - `rule`: The current rule
  - `predicate`: A lambda expression that specifies a condition for when the validator should not run
  - `applyConditionTo`: Whether the condition should be applied to the current rule or all rules in the chain
- `When<T1, T2>(Validation.IRuleBuilderOptions<T1,T2>, Func<T1,Validation.ValidationContext<T1>,bool>, Validation.ApplyConditionTo)`
  - Specifies a condition limiting when the validator should run.
The validator will only be executed if the result of the lambda returns true.
  - `rule`: The current rule
  - `predicate`: A lambda expression that specifies a condition for when the validator should run
  - `applyConditionTo`: Whether the condition should be applied to the current rule or all rules in the chain
- `When<T1, T2>(Validation.IRuleBuilderOptions<T1,T2>, Func<T1,bool>, Validation.ApplyConditionTo)`
  - Specifies a condition limiting when the validator should run.
The validator will only be executed if the result of the lambda returns true.
  - `rule`: The current rule
  - `predicate`: A lambda expression that specifies a condition for when the validator should run
  - `applyConditionTo`: Whether the condition should be applied to the current rule or all rules in the chain
- `When<T1, T2>(Validation.IRuleBuilderOptionsConditions<T1,T2>, Func<T1,Validation.ValidationContext<T1>,bool>, Validation.ApplyConditionTo)`
  - Specifies a condition limiting when the validator should run.
The validator will only be executed if the result of the lambda returns true.
  - `rule`: The current rule
  - `predicate`: A lambda expression that specifies a condition for when the validator should run
  - `applyConditionTo`: Whether the condition should be applied to the current rule or all rules in the chain
- `When<T1, T2>(Validation.IRuleBuilderOptionsConditions<T1,T2>, Func<T1,bool>, Validation.ApplyConditionTo)`
  - Specifies a condition limiting when the validator should run.
The validator will only be executed if the result of the lambda returns true.
  - `rule`: The current rule
  - `predicate`: A lambda expression that specifies a condition for when the validator should run
  - `applyConditionTo`: Whether the condition should be applied to the current rule or all rules in the chain
- `WhenAsync<T1, T2>(Validation.IRuleBuilderOptions<T1,T2>, Func<T1,CancellationToken,Tasks.Task<bool>>, Validation.ApplyConditionTo)`
  - Specifies an asynchronous condition limiting when the validator should run.
The validator will only be executed if the result of the lambda returns true.
  - `rule`: The current rule
  - `predicate`: A lambda expression that specifies a condition for when the validator should run
  - `applyConditionTo`: Whether the condition should be applied to the current rule or all rules in the chain
- `WhenAsync<T1, T2>(Validation.IRuleBuilderOptions<T1,T2>, Func<T1,Validation.ValidationContext<T1>,CancellationToken,Tasks.Task<bool>>, Validation.ApplyConditionTo)`
  - Specifies an asynchronous condition limiting when the validator should run.
The validator will only be executed if the result of the lambda returns true.
  - `rule`: The current rule
  - `predicate`: A lambda expression that specifies a condition for when the validator should run
  - `applyConditionTo`: Whether the condition should be applied to the current rule or all rules in the chain
- `WhenAsync<T1, T2>(Validation.IRuleBuilderOptionsConditions<T1,T2>, Func<T1,CancellationToken,Tasks.Task<bool>>, Validation.ApplyConditionTo)`
  - Specifies an asynchronous condition limiting when the validator should run.
The validator will only be executed if the result of the lambda returns true.
  - `rule`: The current rule
  - `predicate`: A lambda expression that specifies a condition for when the validator should run
  - `applyConditionTo`: Whether the condition should be applied to the current rule or all rules in the chain
- `WhenAsync<T1, T2>(Validation.IRuleBuilderOptionsConditions<T1,T2>, Func<T1,Validation.ValidationContext<T1>,CancellationToken,Tasks.Task<bool>>, Validation.ApplyConditionTo)`
  - Specifies an asynchronous condition limiting when the validator should run.
The validator will only be executed if the result of the lambda returns true.
  - `rule`: The current rule
  - `predicate`: A lambda expression that specifies a condition for when the validator should run
  - `applyConditionTo`: Whether the condition should be applied to the current rule or all rules in the chain
- `Where<T1, T2>(Validation.IRuleBuilderInitialCollection<T1,T2>, Func<T2,bool>)`
  - Applies a filter to a collection property.
  - `rule`: The current rule
  - `predicate`: The condition
- `WithErrorCode<T1, T2>(Validation.IRuleBuilderOptions<T1,T2>, string)`
  - Specifies a custom error code to use if validation fails.
  - `rule`: The current rule
  - `errorCode`: The error code to use
- `WithMessage<T1, T2>(Validation.IRuleBuilderOptions<T1,T2>, Func<T1,T2,string>)`
  - Specifies a custom error message to use when validation fails. Only applies to the rule that directly precedes it.
  - `rule`: The current rule
  - `messageProvider`: Delegate that will be invoked.Uses_localized_name to retrieve the localized message.
- `WithMessage<T1, T2>(Validation.IRuleBuilderOptions<T1,T2>, Func<T1,string>)`
  - Specifies a custom error message to use when validation fails. Only applies to the rule that directly precedes it.
  - `rule`: The current rule
  - `messageProvider`: Delegate that will be invoked to retrieve the localized message.
- `WithMessage<T1, T2>(Validation.IRuleBuilderOptions<T1,T2>, string)`
  - Specifies a custom error message to use when validation fails. Only applies to the rule that directly precedes it.
  - `rule`: The current rule
  - `errorMessage`: The error message to use
- `WithName<T1, T2>(Validation.IRuleBuilderOptions<T1,T2>, Func<T1,string>)`
  - Specifies a custom property name to use within the error message.
  - `rule`: The current rule
  - `nameProvider`: Func used to retrieve the property's display name
- `WithName<T1, T2>(Validation.IRuleBuilderOptions<T1,T2>, string)`
  - Specifies a custom property name to use within the error message.
  - `rule`: The current rule
  - `overridePropertyName`: The property name to use
- `WithSeverity<T1, T2>(Validation.IRuleBuilderOptions<T1,T2>, Func<T1,T2,Validation.Severity>)`
  - Specifies custom severity that should be stored alongside the validation message when validation fails for this rule.
  - `rule`
  - `severityProvider`
  - `<T>`
  - `<TProperty>`
- `WithSeverity<T1, T2>(Validation.IRuleBuilderOptions<T1,T2>, Func<T1,Validation.Severity>)`
  - Specifies custom severity that should be stored alongside the validation message when validation fails for this rule.
  - `rule`
  - `severityProvider`
  - `<T>`
  - `<TProperty>`
- `WithSeverity<T1, T2>(Validation.IRuleBuilderOptions<T1,T2>, Validation.Severity)`
  - Specifies custom severity that should be stored alongside the validation message when validation fails for this rule.
  - `rule`
  - `severity`
  - `<T>`
  - `<TProperty>`
- `WithState<T1, T2>(Validation.IRuleBuilderOptions<T1,T2>, Func<T1,T2,object>)`
  - Specifies custom state that should be stored alongside the validation message when validation fails for this rule.
  - `rule`
  - `stateProvider`
  - `<T>`
  - `<TProperty>`
- `WithState<T1, T2>(Validation.IRuleBuilderOptions<T1,T2>, Func<T1,object>)`
  - Specifies custom state that should be stored alongside the validation message when validation fails for this rule.
  - `rule`
  - `stateProvider`
  - `<T>`
  - `<TProperty>`


#### `DefaultValidatorSelector`

Default validator selector that will execute all rules that do not belong to a RuleSet.

**Methods:**

- `CanExecute(Validation.IValidationRule, string, Validation.IValidationContext)`
  - Determines whether or not a rule should execute.
  - `rule`: The rule
  - `propertyPath`: Property path (eg Customer.Address.Line1)
  - `context`: Contextual information
  - returns: Whether or not the validator can execute.


#### `EmailValidationMode`

Defines which mode should be used for email validation.

**Fields:**

- `AspNetCoreCompatible`
  - Uses the simplified ASP.NET Core logic for checking an email address, which just checks for the presence of an @ sign.
- `Net4xRegex`
  - Uses a regular expression for email validation. This is the same regex used by the EmailAddressAttribute in .NET 4.x.


#### `ExclusiveBetweenValidator<T1, T2>`

Performs range validation where the property value must be between the two specified values (exclusive).


#### `Extensions`

Useful extensions

**Methods:**

- `GetMember<T1, T2>(Expressions.Expression<Func<T1,T2>>)`
  - Gets a MemberInfo from a member expression.


#### `ExtensionsInternal`

**Methods:**

- `IsParameterExpression(Expressions.LambdaExpression)`
  - Checks if the expression is a parameter expression
  - `expression`
- `SplitPascalCase(string)`
  - Splits pascal case, so "FooBar" would become "Foo Bar".
  - remarks: Pascal case strings with periods delimiting the upper case letters,
such as "Address.Line1", will have the periods removed.


#### `IAsyncPropertyValidator<T1, T2>`

**Methods:**

- `IsValidAsync(Validation.ValidationContext<T1>, T2, CancellationToken)`
  - Validates a specific property value asynchronously.
  - `context`: The validation context. The parent object can be obtained from here.
  - `value`: The current property value to validate
  - `cancellation`: Cancellation token
  - returns: True if valid, otherwise false.


#### `IChildValidatorAdaptor`

Indicates that this validator wraps another validator.

**Properties:**

- `ValidatorType`
  - The type of the underlying validator


#### `ICollectionRule<T1, T2>`

Represents a rule defined against a collection with RuleForEach.

**Properties:**

- `Filter`
  - Filter that should include/exclude items in the collection.
- `IndexBuilder`
  - Constructs the indexer in the property name associated with the error message.
By default this is "[" + index + "]"


#### `IComparisonValidator`

Defines a comparison validator

**Properties:**

- `Comparison`
  - Metadata- the comparison type
- `MemberToCompare`
  - Metadata- the member being compared
- `ValueToCompare`
  - Metadata- the value being compared


#### `IConditionBuilder`

Fluent interface for conditions (When/Unless/WhenAsync/UnlessAsync)

**Methods:**

- `Otherwise(Action)`
  - Rules to be invoked if the condition fails.
  - `action`


#### `IIncludeRule`

Marker interface indicating an include rule.


#### `ILanguageManager`

Allows the default error message translations to be managed.

**Methods:**

- `GetString(string, CultureInfo)`
  - Gets a translated string based on its key. If the culture is specific and it isn't registered, we try the neutral culture instead.
If no matching culture is found to be registered we use English.
  - `key`: The key
  - `culture`: The culture to translate into

**Properties:**

- `Culture`
  - Default culture to use for all requests to the LanguageManager. If not specified, uses the current UI culture.
- `Enabled`
  - Whether localization is enabled.


#### `IPropertyValidator`

A custom property validator.
This interface should not be implemented directly in your code as it is subject to change.
Please inherit from `PropertyValidator<T1, T2>` instead.

**Methods:**

- `GetDefaultMessageTemplate(string)`
  - Returns the default error message template for this validator, when not overridden.
  - `errorCode`

**Properties:**

- `Name`
  - The name of the validator. This is usually the type name without any generic parameters.
This is used as the default Error Code for the validator.


#### `IPropertyValidator<T1, T2>`

**Methods:**

- `IsValid(Validation.ValidationContext<T1>, T2)`
  - Validates a specific property value.
  - `context`: The validation context. The parent object can be obtained from here.
  - `value`: The current property value to validate
  - returns: True if valid, otherwise false.


#### `IRuleBuilderInitialCollection<T1, T2>`

Rule builder that starts the chain for a child collection


#### `IRuleBuilderInitial<T1, T2>`

Rule builder that starts the chain


#### `IRuleBuilderOptionsConditions<T1, T2>`

Rule builder (for validators that only support conditions, but no other options)


#### `IRuleBuilderOptions<T1, T2>`

Rule builder

**Methods:**

- `DependentRules(Action)`
  - Creates a scope for declaring dependent rules.


#### `IRuleBuilder<T1, T2>`

Rule builder

**Methods:**

- `SetAsyncValidator(Validation.IAsyncPropertyValidator<T1,T2>)`
  - Associates an async validator with this the property for this rule builder.
  - `validator`: The validator to set
- `SetValidator(Validation.IPropertyValidator<T1,T2>)`
  - Associates a validator with this the property for this rule builder.
  - `validator`: The validator to set
- `SetValidator(Validation.IValidator<T2>, string[])`
  - Associates an instance of IValidator with the current property rule.
  - `validator`: The validator to use
  - `ruleSets`
- `SetValidator<T>(Func<T1,T1>, string[])`
  - Associates a validator provider with the current property rule.
  - `validatorProvider`: The validator provider to use
  - `ruleSets`
- `SetValidator<T>(Func<T1,T2,T1>, string[])`
  - Associates a validator provider with the current property rule.
  - `validatorProvider`: The validator provider to use
  - `ruleSets`


#### `IRuleComponent`

An individual component within a rule with a validator attached.

**Methods:**

- `GetUnformattedErrorMessage`
  - Gets the raw unformatted error message. Placeholders will not have been rewritten.

**Properties:**

- `ErrorCode`
  - The error code associated with this rule component.
- `HasAsyncCondition`
  - Whether or not this validator has an async condition associated with it.
- `HasCondition`
  - Whether or not this validator has a condition associated with it.
- `Validator`
  - The validator associated with this component.


#### `IRuleComponent<T1, T2>`

An individual component within a rule with a validator attached.

**Methods:**

- `ApplyAsyncCondition(Func<Validation.ValidationContext<T1>,CancellationToken,Tasks.Task<bool>>)`
  - Adds a condition for this validator. If there's already a condition, they're combined together with an AND.
  - `condition`
- `ApplyCondition(Func<Validation.ValidationContext<T1>,bool>)`
  - Adds a condition for this validator. If there's already a condition, they're combined together with an AND.
  - `condition`
- `SetErrorMessage(Func<Validation.ValidationContext<T1>,T2,string>)`
  - Sets the overridden error message template for this validator.
  - `errorFactory`: A function for retrieving the error message template.
- `SetErrorMessage(string)`
  - Sets the overridden error message template for this validator.
  - `errorMessage`: The error message to set

**Properties:**

- `CustomStateProvider`
  - Function used to retrieve custom state for the validator
- `ErrorCode`
  - The error code associated with this rule component.
- `OnFailure`
  - Sets the on failure callback.
- `SeverityProvider`
  - Function used to retrieve the severity for the validator


#### `IValidationContext`

**Properties:**

- `InstanceToValidate`
  - The object currently being validated.
- `IsAsync`
  - Whether this context is async.
- `IsChildCollectionContext`
  - Whether this is a child collection context.
- `IsChildContext`
  - Whether this is a child context
- `ParentContext`
  - Parent validation context.
- `PropertyChain`
  - Property chain
- `RootContextData`
  - Additional data associated with the validation request.
- `Selector`
  - Selector


#### `IValidationRule`

Defines a rule associated with a property which can have multiple validators.

**Methods:**

- `GetDisplayName(Validation.IValidationContext)`
  - Gets the display name for the property.
  - `context`: Current context
  - returns: Display name

**Properties:**

- `Components`
  - The components in this rule.
- `DependentRules`
  - Dependent rules.
- `Expression`
  - Expression that was used to create the rule.
- `HasAsyncCondition`
  - Whether the rule has an async condition defined.
- `HasCondition`
  - Whether the rule has a condition defined.
- `Member`
  - Property associated with this rule.
- `PropertyName`
  - Returns the property name for the property being validated.
Returns null if it is not a property being validated (eg a method call)
- `RuleSets`
  - Name of the rule-set to which this rule belongs.
- `TypeToValidate`
  - Type of the property being validated


#### `IValidationRuleConfigurable<T1, T2>`

**Methods:**

- `AddAsyncValidator(Validation.IAsyncPropertyValidator<T1,T2>, Validation.IPropertyValidator<T1,T2>)`
  - Adds an async validator to this rule.
  - `asyncValidator`: The async property validator to invoke
  - `fallback`: A synchronous property validator to use as a fallback if executed synchronously. This parameter is optional. If omitted, the async validator will be called synchronously if needed.
- `AddValidator(Validation.IPropertyValidator<T1,T2>)`
  - Adds a validator to this rule.
- `SetDisplayName(Func<Validation.ValidationContext<T1>,string>)`
  - Sets the display name for the property using a function.
  - `factory`: The function for building the display name
- `SetDisplayName(string)`
  - Sets the display name for the property.
  - `name`: The property's display name

**Properties:**

- `CascadeMode`
  - Cascade mode for this rule.
- `Current`
  - The current rule component.
- `MessageBuilder`
  - Allows custom creation of an error message
- `OnFailure`
  - Function that will be invoked if any of the validators associated with this rule fail.


#### `IValidationRule<T>`

**Methods:**

- `ApplyAsyncCondition(Func<Validation.ValidationContext<T1>,CancellationToken,Tasks.Task<bool>>, Validation.ApplyConditionTo)`
  - Applies an async condition to a single rule chain.
The condition can be applied to either the current property validator in the chain,
or all preceding property validators in the chain (the default).
  - `predicate`: The condition to apply
  - `applyConditionTo`: Whether the condition should be applied to the current property validator in the chain, or all preceding property validators in the chain.
- `ApplyCondition(Func<Validation.ValidationContext<T1>,bool>, Validation.ApplyConditionTo)`
  - Applies a condition to a single rule chain.
The condition can be applied to either the current property validator in the chain,
or all preceding property validators in the chain (the default).
  - `predicate`: The condition to apply
  - `applyConditionTo`: Whether the condition should be applied to the current property validator in the chain, or all preceding property validators in the chain.
- `ApplySharedAsyncCondition(Func<Validation.ValidationContext<T1>,CancellationToken,Tasks.Task<bool>>)`
  - Applies an async pre-condition to this rule.
  - `condition`
- `ApplySharedCondition(Func<Validation.ValidationContext<T1>,bool>)`
  - Applies a pre-condition to this rule.
  - `condition`
- `GetPropertyValue(T1)`
  - Gets the property value for this rule. Note that this bypasses all conditions.
  - `instance`: The model from which the property value should be retrieved.
  - returns: The property value.


#### `IValidationRule<T1, T2>`

**Methods:**

- `AddAsyncValidator(Validation.IAsyncPropertyValidator<T1,T2>, Validation.IPropertyValidator<T1,T2>)`
  - Adds an async validator to this rule.
  - `asyncValidator`: The async property validator to invoke
  - `fallback`: A synchronous property validator to use as a fallback if executed synchronously. This parameter is optional. If omitted, the async validator will be called synchronously if needed.
- `AddValidator(Validation.IPropertyValidator<T1,T2>)`
  - Adds a validator to this rule.
- `SetDisplayName(Func<Validation.ValidationContext<T1>,string>)`
  - Sets the display name for the property using a function.
  - `factory`: The function for building the display name
- `SetDisplayName(string)`
  - Sets the display name for the property.
  - `name`: The property's display name

**Properties:**

- `CascadeMode`
  - Cascade mode for this rule.
- `Current`
  - The current rule component.
- `MessageBuilder`
  - Allows custom creation of an error message
- `OnFailure`
  - Function that will be invoked if any of the validators associated with this rule fail.


#### `IValidator`

Defines a validator for a particular type.

**Methods:**

- `CanValidateInstancesOfType(Type)`
  - Checks to see whether the validator can validate objects of the specified type
- `CreateDescriptor`
  - Creates a hook to access various meta data properties
  - returns: A IValidatorDescriptor object which contains methods to access metadata
- `Validate(Validation.IValidationContext)`
  - Validates the specified instance.
  - `context`: A ValidationContext
  - returns: A ValidationResult object contains any validation failures.
- `ValidateAsync(Validation.IValidationContext, CancellationToken)`
  - Validates the specified instance asynchronously.
  - `context`: A ValidationContext
  - `cancellation`: Cancellation token
  - returns: A ValidationResult object contains any validation failures.


#### `IValidatorDescriptor`

Provides metadata about a validator.

**Methods:**

- `GetMembersWithValidators`
  - Gets a collection of validators grouped by property.
- `GetName(string)`
  - Gets the name display name for a property.
- `GetRulesForMember(string)`
  - Gets rules for a property.
- `GetValidatorsForMember(string)`
  - Gets validators for a particular property.

**Properties:**

- `Rules`
  - All rules defined in the validator.


#### `IValidatorFactory`

Gets validators for a particular type.

**Methods:**

- `GetValidator(Type)`
  - Gets the validator for the specified type.
- `GetValidator<T>`
  - Gets the validator for the specified type.


#### `IValidatorSelector`

Determines whether or not a rule should execute.

**Methods:**

- `CanExecute(Validation.IValidationRule, string, Validation.IValidationContext)`
  - Determines whether or not a rule should execute.
  - `rule`: The rule
  - `propertyPath`: Property path (eg Customer.Address.Line1)
  - `context`: Contextual information
  - returns: Whether or not the validator can execute.


#### `IValidator<T>`

Defines a validator for a particular type.

**Methods:**

- `Validate(T1)`
  - Validates the specified instance.
  - `instance`: The instance to validate
  - returns: A ValidationResult object containing any validation failures.
- `ValidateAsync(T1, CancellationToken)`
  - Validate the specified instance asynchronously
  - `instance`: The instance to validate
  - `cancellation`
  - returns: A ValidationResult object containing any validation failures.


#### `IncludeRule<T>`

Include rule

**Methods:**

- `#ctor(Func<Validation.ValidationContext<T1>,T1,Validation.IValidator<T1>>, Func<Validation.CascadeMode>, Type, Type)`
  - Creates a new IncludeRule
- `#ctor(Validation.IValidator<T1>, Func<Validation.CascadeMode>, Type)`
  - Creates a new IncludeRule
- `Create(Validation.IValidator<T1>, Func<Validation.CascadeMode>)`
  - Creates a new include rule from an existing validator
- `Create<T>(Func<T1,T1>, Func<Validation.CascadeMode>)`
  - Creates a new include rule from an existing validator


#### `InclusiveBetweenValidator<T1, T2>`

Performs range validation where the property value must be between the two specified values (inclusive).


#### `InlineValidator<T>`

Validator implementation that allows rules to be defined without inheriting from AbstractValidator.

**Methods:**

- `Add<T>(Func<Validation.InlineValidator<T1>,Validation.IRuleBuilderOptions<T1,T1>>)`
  - Allows configuration of the validator.


#### `LanguageManager`

Allows the default error message translations to be managed.

**Methods:**

- `Clear`
  - Removes all languages except the default.
- `GetString(string, CultureInfo)`
  - Gets a translated string based on its key. If the culture is specific and it isn't registered, we try the neutral culture instead.
If no matching culture is found to be registered we use English.
  - `key`: The key
  - `culture`: The culture to translate into
- `GetTranslation(string, string)`
  - Language factory.
  - `culture`: The culture code.
  - `key`: The key to load
  - returns: The corresponding Language instance or null.

**Properties:**

- `Culture`
  - Default culture to use for all requests to the LanguageManager. If not specified, uses the current UI culture.
- `Enabled`
  - Whether localization is enabled.


#### `MemberNameValidatorSelector`

Selects validators that are associated with a particular property.

**Methods:**

- `#ctor(Generic.IEnumerable<string>)`
  - Creates a new instance of MemberNameValidatorSelector.
- `CanExecute(Validation.IValidationRule, string, Validation.IValidationContext)`
  - Determines whether or not a rule should execute.
  - `rule`: The rule
  - `propertyPath`: Property path (eg Customer.Address.Line1)
  - `context`: Contextual information
  - returns: Whether or not the validator can execute.
- `MemberNamesFromExpressions<T>(Expressions.Expression<Func<T1,object>>[])`
  - Gets member names from expressions
  - `propertyExpressions`
  - `<T>`

**Properties:**

- `MemberNames`
  - Member names that are validated.


#### `MessageFormatter`

Assists in the construction of validation messages.

**Methods:**

- `AppendArgument(string, object)`
  - Adds a value for a validation message placeholder.
  - `name`
  - `value`
- `AppendPropertyName(string)`
  - Appends a property name to the message.
  - `name`: The name of the property
- `AppendPropertyValue(object)`
  - Appends a property value to the message.
  - `value`: The value of the property
- `BuildMessage(string)`
  - Constructs the final message from the specified template.
  - `messageTemplate`: Message template
  - returns: The message with placeholders replaced with their appropriate values

**Properties:**

- `PlaceholderValues`
  - Additional placeholder values

**Fields:**

- `PropertyName`
  - Default Property Name placeholder.
- `PropertyValue`
  - Default Property Value placeholder.


#### `PolymorphicValidator<T1, T2>`

Performs runtime checking of the value being validated, and passes validation off to a subclass validator.

**Methods:**

- `Add(Type, Validation.IValidator, string[])`
  - Adds a validator to handle a specific subclass. This method is not publicly exposed as it
takes a non-generic IValidator instance which could result in a type-unsafe validation operation.
It allows derived validaors more flexibility in handling type conversion. If you make use of this method, you
should ensure that the validator can correctly handle the type being validated.
  - `subclassType`
  - `validator`
  - `ruleSets`: Optionally specify rulesets to execute. If set, rules not in these rulesets will not be run
- `Add<T>(Func<T1,T1,Validation.IValidator<T1>>, string[])`
  - Adds a validator to handle a specific subclass.
  - `validatorFactory`: The derived validator
  - `ruleSets`: Optionally specify rulesets to execute. If set, rules not in these rulesets will not be run
  - `<TDerived>`
- `Add<T>(Func<T1,Validation.IValidator<T1>>, string[])`
  - Adds a validator to handle a specific subclass.
  - `validatorFactory`: The derived validator
  - `ruleSets`: Optionally specify rulesets to execute. If set, rules not in these rulesets will not be run
  - `<TDerived>`
- `Add<T>(Validation.IValidator<T1>, string[])`
  - Adds a validator to handle a specific subclass.
  - `derivedValidator`: The derived validator
  - `ruleSets`: Optionally specify rulesets to execute. If set, rules not in these rulesets will not be run
  - `<TDerived>`


#### `PropertyChain`

Represents a chain of properties

**Methods:**

- `#ctor`
  - Creates a new PropertyChain.
- `#ctor(Generic.IEnumerable<string>)`
  - Creates a new PropertyChain
  - `memberNames`
- `#ctor(Validation.PropertyChain)`
  - Creates a new PropertyChain based on another.
- `Add(MemberInfo)`
  - Adds a MemberInfo instance to the chain
  - `member`: Member to add
- `Add(string)`
  - Adds a property name to the chain
  - `propertyName`: Name of the property to add
- `AddIndexer(object, bool)`
  - Adds an indexer to the property chain. For example, if the following chain has been constructed:
Parent.Child
then calling AddIndexer(0) would convert this to:
Parent.Child[0]
  - `indexer`
  - `surroundWithBrackets`: Whether square brackets should be applied before and after the indexer. Default true.
- `BuildPropertyName(string)`
  - Builds a property path.
- `FromExpression(Expressions.LambdaExpression)`
  - Creates a PropertyChain from a lambda expression
  - `expression`
- `IsChildChainOf(Validation.PropertyChain)`
  - Checks if the current chain is the child of another chain.
For example, if chain1 were for "Parent.Child" and chain2 were for "Parent.Child.GrandChild" then
chain2.IsChildChainOf(chain1) would be true.
  - `parentChain`: The parent chain to compare
  - returns: True if the current chain is the child of the other chain, otherwise false
- `ToString`
  - Creates a string representation of a property chain.

**Properties:**

- `Count`
  - Number of member names in the chain


#### `PropertyRule<T1, T2>`

Defines a rule associated with a property.

**Methods:**

- `Create(Expressions.Expression<Func<T1,T2>>, Func<Validation.CascadeMode>, bool)`
  - Creates a new property rule from a lambda expression.
- `Create<T>(Expressions.Expression<Func<T1,T1>>, Func<T1,T1,T2>, Func<Validation.CascadeMode>, bool)`
  - Creates a new property rule from a lambda expression.
- `Create<T>(Expressions.Expression<Func<T1,T1>>, Func<T1,T2>, Func<Validation.CascadeMode>, bool)`
  - Creates a new property rule from a lambda expression.
- `Validate(Validation.ValidationContext<T1>)`
  - Performs validation using a validation context and returns a collection of Validation Failures.
  - `context`: Validation Context
  - returns: A collection of validation failures
- `ValidateAsync(Validation.ValidationContext<T1>, CancellationToken)`
  - Performs asynchronous validation using a validation context and returns a collection of Validation Failures.
  - `context`: Validation Context
  - `cancellation`
  - returns: A collection of validation failures


#### `PropertyValidator<T1, T2>`

**Methods:**

- `GetDefaultMessageTemplate(string)`
  - Returns the default error message template for this validator, when not overridden.
  - `errorCode`: The currently configured error code for the validator.
- `IsValid(Validation.ValidationContext<T1>, T2)`
  - Validates a specific property value.
  - `context`: The validation context. The parent object can be obtained from here.
  - `value`: The current property value to validate
  - returns: True if valid, otherwise false.
- `Localized(string, string)`
  - Retrieves a localized string from the LanguageManager.
If an ErrorCode is defined for this validator, the error code is used as the key.
If no ErrorCode is defined (or the language manager doesn't have a translation for the error code)
then the fallback key is used instead.
  - `errorCode`: The currently configured error code for the validator.
  - `fallbackKey`: The fallback key to use for translation, if no ErrorCode is available.
  - returns: The translated error message template.

**Properties:**

- `Name`


#### `RangeValidator<T1, T2>`

Base class for range validation.


#### `RuleBase<T1, T2, T3>`

**Methods:**

- `#ctor(MemberInfo, Func<T1,T2>, Expressions.LambdaExpression, Func<Validation.CascadeMode>, Type)`
  - Creates a new property rule.
  - `member`: Property
  - `propertyFunc`: Function to get the property value
  - `expression`: Lambda expression used to create the rule
  - `cascadeModeThunk`: Function to get the cascade mode.
  - `typeToValidate`: Type to validate
- `ApplyAsyncCondition(Func<Validation.ValidationContext<T1>,CancellationToken,Tasks.Task<bool>>, Validation.ApplyConditionTo)`
  - Applies the condition to the rule asynchronously
  - `predicate`
  - `applyConditionTo`
- `ApplyCondition(Func<Validation.ValidationContext<T1>,bool>, Validation.ApplyConditionTo)`
  - Applies a condition to the rule
  - `predicate`
  - `applyConditionTo`
- `ClearValidators`
  - Clear all validators from this rule.
- `CreateValidationError(Validation.ValidationContext<T1>, T3, Validation.RuleComponent<T1,T3>)`
  - Creates an error validation result for this validator.
  - `context`: The validator context
  - `value`: The property value
  - `component`: The current rule component.
  - returns: Returns an error validation result.
- `GetDisplayName(Validation.ValidationContext<T1>)`
  - Display name for the property.
- `PrepareMessageFormatterForValidationError(Validation.ValidationContext<T1>, T3)`
  - Prepares the `MessageFormatter` of context for an upcoming `ValidationFailure`.
  - `context`: The validator context
  - `value`: Property value.
- `SetDisplayName(Func<Validation.ValidationContext<T1>,string>)`
  - Sets the display name for the property using a function.
  - `factory`: The function for building the display name
- `SetDisplayName(string)`
  - Sets the display name for the property.
  - `name`: The property's display name

**Properties:**

- `AsyncCondition`
  - Asynchronous condition for all validators in this rule.
- `CascadeMode`
  - Cascade mode for this rule.
- `Condition`
  - Condition for all validators in this rule.
- `Current`
  - The current rule component.
- `CurrentValidator`
  - The current validator being configured by this rule.
- `DependentRules`
  - Dependent rules
- `Expression`
  - Expression that was used to create the rule.
- `FastEndpoints#Validation#IValidationRule#Components`
- `HasAsyncCondition`
- `HasCondition`
- `Member`
  - Property associated with this rule.
- `MessageBuilder`
  - Allows custom creation of an error message
- `OnFailure`
  - Function that will be invoked if any of the validators associated with this rule fail.
- `PropertyFunc`
  - Function that can be invoked to retrieve the value of the property.
- `PropertyName`
  - Returns the property name for the property being validated.
Returns null if it is not a property being validated (eg a method call)
- `RuleSets`
  - Rule set that this rule belongs to (if specified)
- `TypeToValidate`
  - Type of the property being validated


#### `RuleBuilder<T1, T2>`

Builds a validation rule and constructs a validator.

**Methods:**

- `#ctor(Validation.IValidationRuleInternal<T1,T2>, Validation.AbstractValidator<T1>)`
  - Creates a new instance of the `RuleBuilder<T1, T2>` class.

**Properties:**

- `ParentValidator`
  - Parent validator
- `Rule`
  - The rule being created by this RuleBuilder.


#### `RuleComponent<T1, T2>`

An individual component within a rule.
In a rule definition such as RuleFor(x => x.Name).NotNull().NotEqual("Foo")
the NotNull and the NotEqual are both rule components.

**Methods:**

- `ApplyAsyncCondition(Func<Validation.ValidationContext<T1>,CancellationToken,Tasks.Task<bool>>)`
  - Adds a condition for this validator. If there's already a condition, they're combined together with an AND.
  - `condition`
- `ApplyCondition(Func<Validation.ValidationContext<T1>,bool>)`
  - Adds a condition for this validator. If there's already a condition, they're combined together with an AND.
  - `condition`
- `GetErrorMessage(Validation.ValidationContext<T1>, T2)`
  - Gets the error message. If a context is supplied, it will be used to format the message if it has placeholders.
If no context is supplied, the raw unformatted message will be returned, containing placeholders.
  - `context`: The validation context.
  - `value`: The current property value.
  - returns: Either the formatted or unformatted error message.
- `GetUnformattedErrorMessage`
  - Gets the raw unformatted error message. Placeholders will not have been rewritten.
- `SetErrorMessage(Func<Validation.ValidationContext<T1>,T2,string>)`
  - Sets the overridden error message template for this validator.
  - `errorFactory`: A function for retrieving the error message template.
- `SetErrorMessage(string)`
  - Sets the overridden error message template for this validator.
  - `errorMessage`: The error message to set

**Properties:**

- `CustomStateProvider`
  - Function used to retrieve custom state for the validator
- `ErrorCode`
  - Retrieves the error code.
- `HasAsyncCondition`
- `HasCondition`
- `SeverityProvider`
  - Function used to retrieve the severity for the validator
- `Validator`


#### `RulesetValidatorSelector`

Selects validators that belong to the specified rulesets.

**Methods:**

- `#ctor(Generic.IEnumerable<string>)`
  - Creates a new instance of the RulesetValidatorSelector.
- `CanExecute(Validation.IValidationRule, string, Validation.IValidationContext)`
  - Determines whether or not a rule should execute.
  - `rule`: The rule
  - `propertyPath`: Property path (eg Customer.Address.Line1)
  - `context`: Contextual information
  - returns: Whether or not the validator can execute.
- `IsIncludeRule(Validation.IValidationRule)`
  - Checks if the rule is an IncludeRule
  - `rule`

**Properties:**

- `RuleSets`
  - Rule sets


#### `ScalePrecisionValidator<T>`

Allows a decimal to be validated for scale and precision.
Scale would be the number of digits to the right of the decimal point.
Precision would be the number of digits. This number includes both the left and the right sides of the decimal point.

It can be configured to use the effective scale and precision
(i.e. ignore trailing zeros) if required.

123.4500 has an scale of 4 and a precision of 7, but an effective scale
and precision of 2 and 5 respectively.


#### `Severity`

Specifies the severity of a rule.

**Fields:**

- `Error`
  - Error
- `Info`
  - Info
- `Warning`
  - Warning


#### `ValidationContext<T>`

Validation context

**Methods:**

- `#ctor(T1)`
  - Creates a new validation context
  - `instanceToValidate`
- `#ctor(T1, Validation.PropertyChain, Validation.IValidatorSelector)`
  - Creates a new validation context with a custom property chain and selector
  - `instanceToValidate`
  - `propertyChain`
  - `validatorSelector`
- `AddFailure(Validation.ValidationFailure)`
  - Adds a new validation failure.
  - `failure`: The failure to add.
- `AddFailure(string)`
  - Adds a new validation failure for the specified message.
The failure will be associated with the current property being validated.
  - `errorMessage`: The error message
- `AddFailure(string, string)`
  - Adds a new validation failure for the specified property.
  - `propertyName`: The property name
  - `errorMessage`: The error message
- `CloneForChildValidator<T>(T1, bool, Validation.IValidatorSelector)`
  - Creates a new validation context for use with a child validator
  - `instanceToValidate`
  - `preserveParentContext`
  - `selector`
- `CreateWithOptions(T1, Action<Validation.ValidationStrategy<T1>>)`
  - Creates a new validation context using the specified options.
  - `instanceToValidate`: The instance to validate
  - `options`: Callback that allows extra options to be configured.
- `GetFromNonGenericContext(Validation.IValidationContext)`
  - Gets or creates generic validation context from non-generic validation context.
  - `context`

**Properties:**

- `DisplayName`
  - Gets the display name for the current property being validated.
- `FastEndpoints#Validation#IValidationContext#InstanceToValidate`
  - Object being validated
- `InstanceToValidate`
  - The object to validate
- `IsAsync`
- `IsChildCollectionContext`
  - Whether this is a child collection context.
- `IsChildContext`
  - Whether this is a child context
- `MessageFormatter`
  - The message formatter used to construct error messages.
- `PropertyChain`
  - Property chain
- `PropertyName`
  - The full name of the current property being validated.
If accessed inside a child validator, this will include the parent's path too.
- `RootContextData`
  - Additional data associated with the validation request.
- `Selector`
  - Selector
- `SharedConditionCache`
  - Shared condition results cache.
The key of the outer dictionary is the ID of the condition, and its value is the cache for that condition.
The key of the inner dictionary is the instance being validated, and the value is the condition result.
- `ThrowOnFailures`
  - Whether the root validator should throw an exception when validation fails.
Defaults to false.


#### `ValidationException`

An exception that represents failed validation

**Methods:**

- `#ctor(Generic.IEnumerable<Validation.ValidationFailure>)`
  - Creates a new ValidationException
  - `errors`
- `#ctor(string)`
  - Creates a new ValidationException
  - `message`
- `#ctor(string, Generic.IEnumerable<Validation.ValidationFailure>)`
  - Creates a new ValidationException
  - `message`
  - `errors`
- `#ctor(string, Generic.IEnumerable<Validation.ValidationFailure>, bool)`
  - Creates a new ValidationException
  - `message`
  - `errors`
  - `appendDefaultMessage`: appends default validation error message to message

**Properties:**

- `Errors`
  - Validation errors


#### `ValidationFailure`

Defines a validation failure

**Methods:**

- `#ctor(string, string)`
  - Creates a new validation failure.
- `#ctor(string, string, object)`
  - Creates a new ValidationFailure.
- `ToString`
  - Creates a textual representation of the failure.

**Properties:**

- `AttemptedValue`
  - The property value that caused the failure.
- `CustomState`
  - Custom state associated with the failure.
- `ErrorCode`
  - Gets or sets the error code.
- `ErrorMessage`
  - The error message
- `FormattedMessagePlaceholderValues`
  - Gets or sets the formatted message placeholder values.
- `PropertyName`
  - The name of the property.
- `Severity`
  - Custom severity level associated with the failure.


#### `ValidationResult`

The result of running a validator

**Methods:**

- `#ctor`
  - Creates a new validationResult
- `#ctor(Generic.IEnumerable<Validation.ValidationFailure>)`
  - Creates a new ValidationResult from a collection of failures
  - `failures`: List of `ValidationFailure` which is later available through `Errors`. This list get's copied.
  - remarks: Every caller is responsible for not adding `null` to the list.
- `ToString`
  - Generates a string representation of the error messages separated by new lines.
- `ToString(string)`
  - Generates a string representation of the error messages separated by the specified character.
  - `separator`: The character to separate the error messages.

**Properties:**

- `Errors`
  - A collection of errors
- `IsValid`
  - Whether validation succeeded


#### `ValidationStrategy<T>`

**Methods:**

- `IncludeAllRuleSets`
  - Indicates that all rules should be executed, regardless of whether or not they're in a ruleset.
This is the equivalent of IncludeRuleSets("*").
- `IncludeProperties(Expressions.Expression<Func<T1,object>>[])`
  - Indicates that only the specified properties should be validated.
  - `propertyExpressions`: The properties to validate, defined as expressions.
- `IncludeProperties(string[])`
  - Indicates that only the specified properties should be validated.
  - `properties`: The property names to validate.
- `IncludeRuleSets(string[])`
  - Indicates that only the specified rule sets should be validated.
  - `ruleSets`: The names of the rulesets to validate.
- `IncludeRulesNotInRuleSet`
  - Indicates that all rules not in a rule-set should be included for validation (the equivalent of calling IncludeRuleSets("default")).
This method can be combined with IncludeRuleSets.
- `ThrowOnFailures`
  - Indicates that the validator should throw an exception if it fails, rather than return a validation result.
- `UseCustomSelector(Validation.IValidatorSelector)`
  - Indicates that the specified selector should be used to control which rules are executed.
  - `selector`: The custom selector to use


#### `ValidatorConfiguration`

Configuration options for validators.

**Properties:**

- `CascadeMode`
  - Default cascade mode
- `DisableAccessorCache`
  - Disables the expression accessor cache. Not recommended.
- `DisplayNameResolver`
  - Pluggable logic for resolving display names
- `ErrorCodeResolver`
  - Pluggable resolver for default error codes
- `LanguageManager`
  - Default language manager
- `MessageFormatterFactory`
  - Specifies a factory for creating MessageFormatter instances.
- `PropertyChainSeparator`
  - Default property chain separator
- `PropertyNameResolver`
  - Pluggable logic for resolving property names
- `Severity`
  - Default severity level
- `ValidatorSelectors`
  - Customizations of validator selector


#### `ValidatorDescriptor<T>`

Used for providing metadata about a validator.

**Methods:**

- `#ctor(Generic.IEnumerable<Validation.IValidationRule>)`
  - Creates a ValidatorDescriptor
  - `rules`
- `GetMembersWithValidators`
  - Gets all members with their associated validators
- `GetName(Expressions.Expression<Func<T1,object>>)`
  - Gets the member name from an expression
  - `propertyExpression`
- `GetName(string)`
  - Gets the display name or a property property
  - `property`
- `GetRulesByRuleset`
  - Gets rules grouped by ruleset
- `GetRulesForMember(string)`
  - Gets rules for a specific member
  - `name`
- `GetValidatorsForMember(string)`
  - Gets validators for a specific member
  - `name`
- `GetValidatorsForMember<T>(Validation.MemberAccessor<T1,T1>)`
  - Gets validators for a member
  - `accessor`
  - `<TValue>`

**Properties:**

- `Rules`
  - Rules associated with the validator


#### `ValidatorFactoryBase`

Factory for creating validators

**Methods:**

- `CreateInstance(Type)`
  - Instantiates the validator
  - `validatorType`
- `GetValidator(Type)`
  - Gets a validator for a type
  - `type`
- `GetValidator<T>`
  - Gets a validator for a type
  - `<T>`


#### `ValidatorOptions`

Validator runtime options

**Properties:**

- `Global`
  - Global configuration for all validators.


#### `ValidatorSelectorOptions`

ValidatorSelector options

**Properties:**

- `DefaultValidatorSelectorFactory`
  - Factory func for creating the default validator selector
- `MemberNameValidatorSelectorFactory`
  - Factory func for creating the member validator selector
- `RulesetValidatorSelectorFactory`
  - Factory func for creating the ruleset validator selector


### namespace `FastEndpoints.Validation.ValidatorDescriptor`1`

#### `RulesetMetadata`

Information about rulesets

**Methods:**

- `#ctor(string, Generic.IEnumerable<Validation.IValidationRule>)`
  - Creates a new RulesetMetadata
  - `name`
  - `rules`

**Properties:**

- `Name`
  - Ruleset name
- `Rules`
  - Rules in the ruleset



## package `FastEndpoints.Messaging.Core` v8.1.0

### namespace `FastEndpoints`

#### `CommandReceiver<T>`

the default implementation of a command receiver that can be used to test the execution of a command.

**Methods:**

- `WaitForMatchAsync(Func<T1,bool>, int, CancellationToken)`


#### `EventReceiver<T>`

the default implementation of an event receiver that can be used to test the execution of and event.

**Methods:**

- `WaitForMatchAsync(Func<T1,bool>, int, CancellationToken)`


#### `IClientStreamCommandHandler<T1, T2>`

interface to be implemented by a command handler for a stream of T that returns a single TResult.

**Methods:**

- `ExecuteAsync(Generic.IAsyncEnumerable<T1>, CancellationToken)`
  - accepts a stream of T and returns a TResult when the stream ends.
  - `stream`: the stream of incoming items
  - `ct`: optional cancellation token


#### `ICommand`

interface for a command that does not return anything


#### `ICommandBase`

common marker interface for all command types.


#### `ICommandHandler`

marker interface for all command handlers


#### `ICommandHandler<T>`

interface to be implemented by a command handler for a given command type that does not return a result

**Methods:**

- `ExecuteAsync(T1, CancellationToken)`
  - accepts a command and does not return a result.
  - `command`: the input command object
  - `ct`: optional cancellation token


#### `ICommandHandler<T1, T2>`

interface to be implemented by a command handler for a given command type that returns a result

**Methods:**

- `ExecuteAsync(T1, CancellationToken)`
  - receives a command and returns a result.
  - `command`: the input command object
  - `ct`: optional cancellation token


#### `ICommandReceiver<T>`

interface for a command receiver that can be used to test the receipt of commands in testing.

**Methods:**

- `AddCommand(T1)`
- `WaitForMatchAsync(Func<T1,bool>, int, CancellationToken)`
  - waits until at least one matching command is received not exceeding the timeout period.
  - `match`: a predicate for matching commands that should be returned by the method
  - `timeoutSeconds`: how long the method will wait until a matching command is received. default value is 2 seconds
  - `ct`: optional cancellation token


#### `ICommand<T>`

interface for a command that returns a TResult


#### `IEvent`

marker interface for an event model


#### `IEventHandler`

marker interface for all event handlers


#### `IEventHandler<T>`

interface to be implemented by event handlers

**Methods:**

- `HandleAsync(T1, CancellationToken)`
  - the handler logic for the event handler
  - `eventModel`: the input event model
  - `ct`: optional cancellation token


#### `IEventReceiver<T>`

interface for an event receiver that can be used to test the receipt of events in testing.

**Methods:**

- `AddEvent(T1)`
- `WaitForMatchAsync(Func<T1,bool>, int, CancellationToken)`
  - waits until at least one matching event is received not exceeding the timeout period.
  - `match`: a predicate for matching events that should be returned by the method
  - `timeoutSeconds`: how long the method will wait until a matching event is received. default value is 2 seconds
  - `ct`: optional cancellation token


#### `IHasTrackingID`

**Properties:**

- `TrackingID`
  - tracking id of the job


#### `IJobResult`


#### `IServerStreamCommandHandler<T1, T2>`

interface to be implemented by a command handler for a given command type that returns TResult stream

**Methods:**

- `ExecuteAsync(T1, CancellationToken)`
  - receives a command and returns a stream of TResult.
  - `command`: the input command object
  - `ct`: optional cancellation token


#### `IServerStreamCommand<T>`

interface for a command that returns a stream of TResult


#### `ITrackableJob<T>`

interface for a trackable job that returns a TResult


#### `Void`



## package `FastEndpoints.Messaging.Remote` v8.1.0

### namespace `FastEndpoints`

#### `EventDispatcherWorker`

dispatches persisted event records to a connected subscriber over a gRPC server stream.
extracted from EventHub to isolate the dispatcher loop as a self-contained unit.


#### `EventExtensions`

**Methods:**

- `Broadcast<T>(T1)`
  - broadcast/publish an event to all remote subscribers.
this method should only be called when the server is running in `EventPublisher` hub mode
  - `<TEvent>`: the type of the event being broadcast


#### `EventHubExceptionReceiver`

inherit this class and override it's methods in order to receive event hub exceptions.

**Methods:**

- `OnGetNextBatchError<T>(string, int, Exception, CancellationToken)`
  - this method is triggered when the storage provider has trouble retrieving the next batch of event records.
  - `subscriberID`: the unique ID of the subscriber
  - `attemptCount`: the number of times the operation was attempted
  - `exception`: the actual exception that was thrown by the operation
  - `ct`: cancellation token
  - `<TEvent>`: the type of the event
- `OnInMemoryQueueOverflow<T>(IEventStorageRecord, CancellationToken)`
  - this method is triggered when the default in-memory storage provider's internal queue for the given event type has been stagnant and in an overflow state.
  - `record`: the event storage record that was supposed to be added to the queue
  - `ct`: cancellation token
  - `<TEvent>`: the type of the event
- `OnMarkEventAsCompleteError<T>(IEventStorageRecord, int, Exception, CancellationToken)`
  - this method is triggered when the storage provider has trouble marking an event record as complete.
  - `record`: the event storage record that was supposed to be marked complete
  - `attemptCount`: the number of times the record was attempted to be marked complete
  - `exception`: the actual exception that was thrown by the operation
  - `ct`: cancellation token
  - `<TEvent>`: the type of the event
- `OnRestoreSubscriberIDsError(Type, int, Exception, CancellationToken)`
  - this method is triggered when the storage provider has trouble restoring event subscribers.
  - `eventType`: the type of the event
  - `attemptCount`: the number of times the subscriber were attempted to be retrieved
  - `exception`: the actual exception that was thrown by the operation
  - `ct`: cancellation token
- `OnSerializeEventError<T>(T1, Exception, CancellationToken)`
  - this method is triggered when the storage provider has trouble serializing an event object calling the
`IEventStorageRecord`.`SetEvent<T>` method.
  - `event`: the event object that failed to serialize
  - `exception`: the actual exception that was thrown by the operation
  - `ct`: cancellation token
  - `<TEvent>`: the type of the event
- `OnStoreEventRecordsError<T>(Generic.IEnumerable<IEventStorageRecord>, int, Exception, CancellationToken)`
  - this method is triggered when the storage provider has trouble persisting event storage records.
  - `records`: the event storage records that were supposed to be persisted
  - `attemptCount`: the number of times the operation was attempted
  - `exception`: the actual exception that was thrown by the operation
  - `ct`: cancellation token
  - `<TEvent>`: the type of the events


#### `EventHubExceptionReceiverExtensions`

**Methods:**

- `AddEventHubExceptionReceiver<T>(Microsoft.Extensions.DependencyInjection.IServiceCollection)`
  - register a custom exception receiver for receiving event hub exceptions.
  - `<TReceiver>`: the implementation type of the receiver


#### `EventHubSettings`

centralizes all timing constants and sizing defaults used by the event hub dispatcher and broadcast tasks.
having them in one place makes them easy to find, tune, and override in tests.

**Fields:**

- `BatchSize`
  - maximum number of event records fetched from storage per subscriber per iteration.
- `EventExpiry`
  - default time-to-live for persisted event records.
- `InitializationTimeout`
  - maximum time allowed for restoring subscriber IDs from the storage provider during initialization.
if the timeout is exceeded the application will not be allowed to start.
- `NoSubscriberRetryDelay`
  - delay between polls when no subscribers are registered for an event being broadcast.
- `NoSubscriberTimeout`
  - maximum time to wait for at least one subscriber to appear before silently dropping a broadcast event.
- `StorageRetryDelay`
  - delay between retries when a storage operation fails (get-next-batch, store-events, mark-complete, restore-subscriber-ids).
- `WaitForSignalTimeout`
  - how long the dispatcher waits for a semaphore signal before polling storage again.
acts as the maximum idle interval between fetch cycles.
this field is non-readonly so tests can override it.


#### `HandlerOptions<T1, T2>`

handler registration options

**Methods:**

- `Register<T1, T2, T3>`
  - registers a "unary" command handler this server is hosting.
  - `<TCommand>`: the type of the incoming command
  - `<THandler>`: the type of the handler for the incoming command
  - `<TResult>`: the type of the result that will be returned from the handler
- `Register<T1, T2>`
  - registers a "void" command handler this server is hosting.
  - `<TCommand>`: the type of the incoming command
  - `<THandler>`: the type of the handler for the incoming command
- `RegisterClientStream<T1, T2, T3>`
  - registers a "client stream" command handler this server is hosting.
  - `<T>`: the type of the incoming item stream
  - `<THandler>`: the type of the handler for the incoming stream
  - `<TResult>`: the type of the result that will be returned from the handler when the stream ends
- `RegisterEventHub<T>(Generic.IEnumerable<string>, HubMode)`
  - registers an "event hub" that broadcasts events of the given type to all remote subscribers in an asynchronous manner.
use knownSubscriberIDs when the hub should start storing events for named subscribers before they first connect.


NOTE: known subscriber ids are not supported when the hub is configured in `RoundRobin` mode.
  - `knownSubscriberIDs`: the explicit subscriber ids that should start receiving queued events from app startup onward. the same id may be
reused across different event types because pending-record lookups are scoped by both subscriber id and event type.
  - `mode`: the operation mode of this event hub
  - `<TEvent>`: the type of event this hub deals with
- `RegisterEventHub<T>(HubMode)`
  - registers an "event hub" that broadcasts events of the given type to all remote subscribers in an asynchronous manner
  - `mode`: the operation mode of this event hub
  - `<TEvent>`: the type of event this hub deals with
- `RegisterServerStream<T1, T2, T3>`
  - registers a "server stream" command handler this server is hosting.
  - `<TCommand>`: the type of the incoming command
  - `<THandler>`: the type of the handler for the incoming command
  - `<TResult>`: the type of the result stream that will be returned from the handler


#### `HandlerServerExtensions`

gRPC handler server extensions

**Methods:**

- `AddHandlerServer(Microsoft.AspNetCore.Builder.WebApplicationBuilder, Action<Grpc.AspNetCore.Server.GrpcServiceOptions>)`
  - configure the handler server which will host a collection of command handlers and event hubs. this should only be called once per application.


IMPORTANT: specify which handlers/hubs this server will be hosting via
`MapHandlers<T1, T2>` method.
  - `bld`
  - `o`: optional grpc service settings
- `AddHandlerServer(Microsoft.Extensions.DependencyInjection.IServiceCollection, Action<Grpc.AspNetCore.Server.GrpcServiceOptions>)`
  - configure the handler server which will host a collection of command handlers. this should only be called once per application.


IMPORTANT: specify which handlers this server will be hosting via
`MapHandlers<T1, T2>` method.
  - `sc`
  - `o`: optional grpc service settings
- `MapHandlers(Microsoft.AspNetCore.Routing.IEndpointRouteBuilder, Action<HandlerOptions<InMemoryEventStorageRecord,InMemoryEventHubStorage>>)`
- `MapHandlers<T1, T2>(Microsoft.AspNetCore.Routing.IEndpointRouteBuilder, Action<HandlerOptions<T1,T2>>)`


#### `HubContext`

captures the common context (logger, exception receiver, event type name, app cancellation) shared across
all retry and error-receiver invocations within the event hub, eliminating the need to pass these values
repeatedly at every call site.

**Methods:**

- `InvokeExceptionReceiverSafely(Func<Tasks.Task>)`
  - safely invokes a user-provided exception receiver callback. any exception thrown by user code is logged but never propagated,
ensuring a faulty receiver can never tear down the event hub worker.
- `RetryUntilSuccess(Func<Tasks.ValueTask>, Func<int,Exception,Tasks.Task>, Action<string>, TimeSpan, CancellationToken)`
  - retries operation in a loop until it succeeds or ct is canceled.
on each failure the error callback is invoked safely (exceptions from user code are caught),
the error is logged, and execution is delayed before the next attempt.


#### `HubMode`

enum for specifying which mode the event hub should be running in.

**Fields:**

- `EventBroker`
  - enable remote event publishers to send events to this server which will be relayed to the connected subscribers.
this mode also allows this server itself to publish events as well.
- `EventPublisher`
  - this server/application itself is the sole publisher of events. no external publishers will be accepted. this is the default mode.
- `RoundRobin`
  - with this mode events will only be delivered to just one of the subscribers connected to the hub in a round robin fashion.
if for example, there's two subscribers (A and B) connected, event 1 will be delivered to subscriber A.
event 2 will be delivered to subscriber B. event 3 will be delivered to subscriber A again and so on.


#### `HubStorageBehavior`

encapsulates the behavioral differences between in-memory and durable event hub storage providers.
this eliminates scattered boolean checks throughout the dispatcher and broadcast logic.

**Methods:**

- `GetStoreEventsToken(CancellationToken)`
  - durable providers must persist outgoing fan-out records even during app shutdown so published
events remain available for delivery after restart, so they use `None`.
in-memory providers use the app token since there's nothing to persist beyond the process lifetime.

**Properties:**

- `ShouldInitialize`
  - only durable providers need initialization (restoring subscriber IDs from storage on startup).
in-memory providers start with an empty state each time.
- `ShouldMarkComplete`
  - durable providers need an explicit completion marker so events are not replayed.
in-memory providers dequeue on read, so no completion tracking is needed.
- `ShouldRequeueOnStreamFailure`
  - in-memory providers dequeue records from the queue on read, so stream write failures must re-queue
the current record and all remaining unattempted records in the batch. durable providers do not
dequeue on read, so the records remain available for the next fetch cycle.


#### `IEventHubStorageProvider<T>`

interface for implementing a storage provider for event hub app (gRPC server)

**Methods:**

- `GetNextBatchAsync(PendingRecordSearchParams<T1>)`
  - fetch the next batch of pending event storage records that need to be processed.
  - `parameters`: use these supplied search parameters to find the next batch of event records from your database
- `MarkEventAsCompleteAsync(T1, CancellationToken)`
  - mark the event storage record as complete by either replacing the entity on storage with the supplied instance or
simply update the `IsComplete` field to true with a partial update operation.
  - `r`
  - `ct`: cancellation token
- `PurgeStaleRecordsAsync(StaleRecordSearchParams<T1>)`
  - this method will be called hourly. implement this method to remove stale records (completed or expired) from storage.
or instead of removing them, you can move them to some other location (dead-letter-queue maybe) or for inspection by a human.
or if you'd like to retry expired events, update the `ExpireOn` field to a future date/time.


NOTE: the default match criteria is:
`r => r.IsComplete || DateTime.UtcNow >= r.ExpireOn`
  - `parameters`: use these supplied search parameters to find relevant event records from your database
- `RestoreSubscriberIDsForEventTypeAsync(SubscriberIDRestorationParams<T1>)`
  - this method will only be called once (for each event type) on app startup. if there are any pending records on storage from a previous app run,
simply return a collection of unique subscriber IDs.
  - `parameters`: use these supplied search parameters to find relevant event records from your database
- `StoreEventsAsync(Generic.IEnumerable<T1>, CancellationToken)`
  - store the event storage records however you please. ideally on a nosql database.


WARNING: make sure to use a transaction or batch insert to ensure all the records are committed in one go.
if only some of the records succeed in being stored, it could lead to duplicate events being published due to the built-in retry mechanism.
  - `r`: the event storage records which contains the actual event objects as well as some metadata
  - `ct`: cancellation token


#### `IHasServerCallContext`

implement this interface on command handler classes in order to access the `ServerCallContext`


#### `KestrelExtensions`

**Methods:**

- `ListenInterProcess(Microsoft.AspNetCore.Server.Kestrel.Core.KestrelServerOptions, string, Action<Microsoft.AspNetCore.Server.Kestrel.Core.ListenOptions>)`
  - enable inter-process-communication via unix domain sockets instead of tcp transport when everything is running on the same machine.
a unix socket will be created with the provided serviceName
  - `ko`
  - `serviceName`: a unique name to identity this service. clients must use the same name in order to connect to this server with the
`.MapRemote()` call.
  - `o`: kestrel listen options


#### `RemoteConnection`

represents a connection to a remote server that hosts command and event handlers

**Methods:**

- `RegisterEvent<T>`
  - register an "event" that the remote server will be accepting (in `EventBroker`) mode for distribution to subscribers.
  - `<TEvent>`: the type of the event


#### `RemoteConnectionExtensions`

client extension methods

**Methods:**

- `AddEventSubscriberStorageProvider<T1, T2>(Microsoft.Extensions.DependencyInjection.IServiceCollection, Nullable<TimeSpan>)`
  - register a custom event subscriber storage provider
  - `services`
  - `expiry`: optional duration after which an event record expires. defaults to 4 hours if not specified.
  - `<TStorageRecord>`: the type of the storage record
  - `<TStorageProvider>`
- `MapRemote(Microsoft.Extensions.Hosting.IHost, string, Action<RemoteConnection>)`
  - creates a grpc channel/connection to a remote server that hosts a known collection of command handlers and event hubs.


IMPORTANT: call the `Register<T1, T2>` method (using action r) to specify which commands are
handled by this remote server. event subscriptions can be specified using `app.Subscribe<TEvent, TEventHandler>()` method.
  - `host`
  - `remoteAddress`: the address of the remote server
  - `r`: a configuration action for the connection
- `RemotePublishAsync(IEvent, CancellationToken)`
- `RemotePublishAsync(IEvent, Grpc.Core.CallOptions)`


#### `SubscriberIDRestorationParams<T>`

parameters to use in finding subscriber IDs to restore

**Properties:**

- `CancellationToken`
  - a cancellation token
- `EventType`
  - the type name of the events to search for which correlates to `EventType`
- `Match`
  - a boolean lambda expression to match pending records.
`r => r.EventType == "xxx" && !r.IsComplete && DateTime.UtcNow <= r.ExpireOn)`
- `Projection`
  - member expression to select/project the UNIQUE `SubscriberID` values.
`e => e.SubscriberID`


### namespace `FastEndpoints.HandlerServerExtensions`

#### `<G>$AA6A55FA96EEB935F04A86FBF0CC54DA`

**Methods:**

- `MapHandlers(Action<HandlerOptions<InMemoryEventStorageRecord,InMemoryEventHubStorage>>)`
  - specify which handlers/event hubs this server will be hosting. the in-memory storage provider will be used.
  - `h`: handler options
- `MapHandlers<T1, T2>(Action<HandlerOptions<T1,T2>>)`
  - specify which handlers/event hubs this server will be hosting together with a custom storage provider
  - `h`: handler options
  - `<TStorageRecord>`: the type of the event storage record
  - `<TStorageProvider>`: the type of the event storage provider


### namespace `FastEndpoints.HandlerServerExtensions.<G>$AA6A55FA96EEB935F04A86FBF0CC54DA`

#### `<M>$AE21605245F75F0E887A7AEEA47FF5B0`


### namespace `FastEndpoints.RemoteConnectionExtensions`

#### `<G>$8DBF87D1890CB028D0175A7D68DD8B33`

**Methods:**

- `RemotePublishAsync(CancellationToken)`
  - publish the event to the relevant remote server that's running in `EventBroker` mode.
  - `ct`: cancellation token
- `RemotePublishAsync(Grpc.Core.CallOptions)`
  - publish the event to the relevant remote server that's running in `EventBroker` mode.
  - `options`: call options


### namespace `FastEndpoints.RemoteConnectionExtensions.<G>$8DBF87D1890CB028D0175A7D68DD8B33`

#### `<M>$BCD1702719EF1047603C41B4D8C0A9C1`



## package `FastEndpoints.Attributes` v8.1.0

### namespace `FastEndpoints`

#### `AllowFileUploadsAttribute`

enable file uploads with multipart/form-data content type

**Methods:**

- `#ctor(bool)`
  - enable file uploads with multipart/form-data content type
  - `dontAutoBindFormData`: set 'true' to disable auto binding of form data which enables uploading and reading of large files without buffering to memory/disk.
you can access the multipart sections for reading via the `FormFileSectionsAsync()` method.

**Properties:**

- `DontAutoBindFormData`
  - set 'true' to disable auto binding of form data which enables uploading and reading of large files without buffering to memory/disk.
you can access the multipart sections for reading via the `FormFileSectionsAsync()` method.


#### `BindFromAttribute`

use this attribute to specify the name of route param, query param, or form field if it's different from the name of the property being bound to.

**Methods:**

- `#ctor(string)`
  - use this attribute to specify the name of route param, query param, or form field if it's different from the name of the property being bound to.
  - `name`: the name to use for binding

**Properties:**

- `Name`
  - the name of the incoming query param, route param or form field


#### `DontBindAttribute`

you can prevent one or more binding sources from supplying values for a dto property decorated with this attribute.

**Methods:**

- `#ctor(Source)`
  - specify a bitwise combination of binding sources to disable for the property.

**Properties:**

- `BindingSources`
  - gets the disabled binding sources.
- `IsRequired`
  - set to true if a validation error should be thrown when the request doesn't have a value for this property.


#### `DontInjectAttribute`

endpoint properties marked with this attribute will disable property injection for that property


#### `DontRegisterAttribute`

classes marked with this attribute will be skipped during assembly scanning for auto registration


#### `FormFieldAttribute`

disables all other binding sources for a dto property except form fields.

**Methods:**

- `#ctor`
  - disables all other binding sources for a dto property except form fields.


#### `FromAttribute`

properties decorated with this attribute will have their values auto bound from the relevant claim of the current user principal.
this is a shorter alias for the [FromClaim] attribute.

**Methods:**

- `#ctor(string, bool)`
  - properties decorated with this attribute will have their values auto bound from the relevant claim of the current user principal.
this is a shorter alias for the [FromClaim] attribute.
  - `claimType`: the claim type to auto bind
  - `isRequired`: set to true if a validation error should be thrown when the current user principal doesn't have the specified claim


#### `FromBodyAttribute`

properties decorated with this attribute will have their values auto bound from the incoming request's json body.


HINT: no other binding sources will be used for binding that property.


#### `FromClaimAttribute`

properties decorated with this attribute will have their values auto bound from the relevant claim of the current user principal

**Methods:**

- `#ctor(bool, bool)`
  - properties decorated with this attribute will have their values auto bound from the relevant claim of the current user principal
  - `isRequired`: set to false if a validation error shouldn't be thrown when the current user principal doesn't have a claim type matching the property name
being bound to.
  - `removeFromSchema`: set to true if your header is not required but shouldn't be added to schema model.
- `#ctor(string, bool, bool)`
  - properties decorated with this attribute will have their values auto bound from the relevant claim of the current user principal
  - `claimType`: optionally specify the claim type to bind from. if not specified, the claim type of the user principal must match the name of the property being
bound to.
  - `isRequired`: set to false if a validation error shouldn't be thrown when the current user principal doesn't have the specified claim type
  - `removeFromSchema`: set to true if your header is not required but shouldn't be added to schema model.

**Properties:**

- `ClaimType`
  - the claim type to auto bind
- `IsRequired`
  - set to true if a validation error should be thrown when the current user principal doesn't have the specified claim
- `RemoveFromSchema`
  - set to true if your header is not required but shouldn't be added to schema model


#### `FromCookieAttribute`

properties decorated with this attribute will have their values auto bound from the relevant cookie of the current request.

**Methods:**

- `#ctor(bool, bool)`
  - properties decorated with this attribute will have their values auto bound from the relevant http cookie of the current request.
  - `isRequired`: set to false if a validation error shouldn't be thrown when the current user request doesn't have a cookie matching the property name being
bound to.
  - `removeFromSchema`: set to true if your cookie is not required but shouldn't be added to schema model.
- `#ctor(string, bool, bool)`
  - properties decorated with this attribute will have their values auto bound from the relevant http cookie of the current request.
  - `cookieName`: optionally specify the cookie name to bind from. if not specified, the cookie name must match the name of the property being bound to.
  - `isRequired`: set to false if a validation error shouldn't be thrown when the current request doesn't have the specified cookie.
  - `removeFromSchema`: set to true if your cookie is not required but shouldn't be added to schema model.

**Properties:**

- `CookieName`
  - the cookie name to auto bind from
- `IsRequired`
  - set to true if a validation error should be thrown when the current request doesn't have the specified cookie
- `RemoveFromSchema`
  - set to true if your cookie is not required but shouldn't be added to schema model


#### `FromFormAttribute`

if a request dto property is decorated with this attribute, that property will be bound from complex multipart form data (including files) from the
incoming request. only valid on complex type properties. only one dto property can be decorated. the incoming form data should be in the correct format.
incoming content-type must be `multipart/form-data`


HINT: recursively binding complex object graphs from form data is less performant than binding to top level dto properties.
so... use sparingly!


#### `FromHeaderAttribute`

properties decorated with this attribute will have their values auto bound from the relevant http header of the current request.

**Methods:**

- `#ctor(bool, bool)`
  - properties decorated with this attribute will have their values auto bound from the relevant http header of the current request.
  - `isRequired`: set to false if a validation error shouldn't be thrown when the current user request doesn't have a header matching the property name being
bound to.
  - `removeFromSchema`: set to true if your header is not required but shouldn't be added to schema model.
- `#ctor(string, bool, bool)`
  - properties decorated with this attribute will have their values auto bound from the relevant http header of the current request.
  - `headerName`: optionally specify the header name to bind from. if not specified, the header name must match the name of the property being bound to.
  - `isRequired`: set to false if a validation error shouldn't be thrown when the current request doesn't have the specified header.
  - `removeFromSchema`: set to true if your header is not required but shouldn't be added to schema model.

**Properties:**

- `HeaderName`
  - the header name to auto bind from
- `IsRequired`
  - set to true if a validation error should be thrown when the current request doesn't have the specified header
- `RemoveFromSchema`
  - set to true if your header is not required but shouldn't be added to schema model


#### `FromQueryAttribute`

if a request dto property is decorated with this attribute, that property will be bound from complex query parameter data from the incoming request.
only valid on complex type properties. only one dto property can be decorated. the incoming query parameters should be in the correct format.


HINT: recursively binding complex object graphs from query parameters is less performant than binding to top level primitive dto properties.
so... use sparingly!


#### `HasPermissionAttribute`

boolean properties decorated with this attribute will have their values set to true if the current principal has the specified permission.

**Methods:**

- `#ctor(string, bool, bool)`
  - boolean properties decorated with this attribute will have their values set to true if the current principal has the specified permission.
  - `permission`: the permission to check for
  - `isRequired`: set to false if a validation error shouldn't be thrown when the current principal doesn't have the specified permission.
  - `removeFromSchema`: set to true if your header is not required but shouldn't be added to body model.

**Properties:**

- `IsRequired`
  - set to true if a validation error should be thrown when the current user principal doesn't have the specified permission
- `Permission`
  - the permission to check for
- `RemoveFromSchema`
  - set to true if your header is not required but shouldn't be added to model


#### `HideFromDocsAttribute`

attribute used to mark classes, properties, methods that should be hidden from public api


#### `Http`

enum for specifying a http verb

**Fields:**

- `CONNECT`
  - establish a communication tunnel
- `DELETE`
  - remove a record
- `GET`
  - retrieve a record
- `HEAD`
  - retrieve only headers
- `OPTIONS`
  - retrieve communication options
- `PATCH`
  - partially update a record
- `POST`
  - create a record
- `PUT`
  - replace a record
- `TRACE`
  - perform a message loop-back test for debugging purposes


#### `HttpAttribute`

base http attribute class

**Methods:**

- `#ctor(Http, string)`
  - constructor
  - `verb`: verb
  - `route`: route
- `#ctor(Http, string[])`
  - constructor
  - `verb`: verb
  - `routes`: routes


#### `HttpDeleteAttribute`

use this attribute to specify a DELETE route for an endpoint

**Methods:**

- `#ctor(string[])`
  - use this attribute to specify a DELETE route for an endpoint
  - `routes`: the routes for the endpoint


#### `HttpGetAttribute`

use this attribute to specify a GET route for an endpoint

**Methods:**

- `#ctor(string[])`
  - use this attribute to specify a GET route for an endpoint
  - `routes`: the routes for the endpoint


#### `HttpPatchAttribute`

use this attribute to specify a PATCH route for an endpoint

**Methods:**

- `#ctor(string[])`
  - use this attribute to specify a PATCH route for an endpoint
  - `routes`: the routes for the endpoint


#### `HttpPostAttribute`

use this attribute to specify a POST route for an endpoint

**Methods:**

- `#ctor(string[])`
  - use this attribute to specify a POST route for an endpoint
  - `routes`: the routes for the endpoint


#### `HttpPutAttribute`

use this attribute to specify a PUT route for an endpoint

**Methods:**

- `#ctor(string[])`
  - use this attribute to specify a PUT route for an endpoint
  - `routes`: the routes for the endpoint


#### `KeyedServiceAttribute`

use this attribute to mark a property to be auto injected from the DI container.

**Methods:**

- `#ctor(string)`
  - use this attribute to mark a property to be auto injected from the DI container.
  - `keyName`: the key name

**Properties:**

- `Key`
  - the key to use for obtaining the service from the DI container.


#### `LifeTime`

enum for selecting the DI service lifetime

**Fields:**

- `Scoped`
  - scoped service lifetime
- `Singleton`
  - singleton service lifetime
- `Transient`
  - transient service lifetime


#### `NonJsonBindingAttribute`


#### `NotImplementedAttribute`

indicates a base/abstract method that's not implemented.


#### `ParseResult`

dto used to hold the result of a value parsing operation

**Methods:**

- `#ctor(bool, object)`
  - constructor for initializing a ParseResult instance
  - `isSuccess`: set to true of parsing was successful
  - `value`: set the value that was obtained from the parsing operation

**Properties:**

- `IsSuccess`
  - will be true if the parsing operation was a success
- `Value`
  - will hold the parsed value if the parsing was successful


#### `PropertyDefinition`

represents reflection data for a property of a type

**Properties:**

- `Setter`
  - action used for setting the value of a property on a class


#### `QueryParamAttribute`

disables all other binding sources for a dto property except query params.

**Methods:**

- `#ctor`
  - disables all other binding sources for a dto property except query params.


#### `ReflectionCache`

the central repository of reflection related data for request dtos and their children


#### `RegisterServiceAttribute<T>`

When using the 'FastEndpoints.Generator' package, any concrete class can be decorated with this attribute to source generate extension methods
in the form of `.RegisterServicesFrom{assembly-name}()` which can be used to automatically register services with a single call per assembly.
instead of multiple calls per each service you need registered in DI.


specify the service type with the TService generic attribute argument. the service type would typically be an interface type.

**Methods:**

- `#ctor(LifeTime)`
  - mark a class for registration in DI using the 'FastEndpoints.Generator' package by specifying the service lifetime.
  - `serviceLifetime`: the service lifetime to use when registering in DI


#### `RouteParamAttribute`

disables all other binding sources for a dto property except route params.

**Methods:**

- `#ctor`
  - disables all other binding sources for a dto property except route params.


#### `Source`

enum for choosing which binding sources to disable for a given property using the `DontBindAttribute`


#### `ThrottleAttribute`

rate limit requests to this endpoint based on a request http header sent by the client.

**Methods:**

- `#ctor(int, double, string)`
  - rate limit requests to this endpoint based on a request http header sent by the client.
  - `hitLimit`: how many requests are allowed within the given duration
  - `durationSeconds`: the frequency in seconds where the accrued hit count should be reset
  - `headerName`: the name of the request header used to uniquely identify clients.
header name can also be configured globally using `app.UseFastEndpoints(c=> c.ThrottleOptions...)`
not specifying a header name will first look for 'X-Forwarded-For' header and if not present, will use `HttpContext.Connection.RemoteIpAddress`.

**Properties:**

- `DurationSeconds`
  - the frequency in seconds where the accrued hit count should be reset
- `HeaderName`
  - the name of the request header used to uniquely identify clients.
header name can also be configured globally using `app.UseFastEndpoints(c=> c.Throttle...)`
not specifying a header name will first look for 'X-Forwarded-For' header and if not present, will use `HttpContext.Connection.RemoteIpAddress`.
- `HitLimit`
  - how many requests are allowed within the given duration


#### `ToHeaderAttribute`

response dto properties marked with this attribute will cause an automatic response header to be added to the http response with the value from the property that is
annotated.

**Methods:**

- `#ctor(string)`
  - response dto properties marked with this attribute will cause an automatic response header to be added to the http response with the value from the property that is
annotated.
  - `headerName`: a custom name for the header. if not supplied, the property name will be used.

**Properties:**

- `HeaderName`
  - a custom name for the header. if not supplied, the property name will be used.


#### `TypeDefinition`

represents reflection data for a given type

**Properties:**

- `IsValidatable`
  - indicates if this type, or it's immediate properties has data annotation validation attributes.
- `ObjectFactory`
  - a func for creating a new blank instance of a type
- `Properties`
  - the reflection data for all the properties of a type
- `ValueParser`
  - a func used for converting string values to the respective type by calling it's `TryParse()` method.


### namespace `JetBrains.Annotations`

#### `ImplicitUseKindFlags`

Specifies the details of an implicitly used symbol when it is marked with `UsedImplicitlyAttribute`.

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


#### `ImplicitUseTargetFlags`

Specifies what is considered to be used implicitly when marked with `UsedImplicitlyAttribute`.

**Fields:**

- `Members`
  - Members of the type marked with the attribute are considered used.
- `WithInheritors`
  - Inherited entities are considered used.
- `WithMembers`
  - Entity marked with the attribute and all its members considered used.


#### `RouteTemplateAttribute`

Indicates that the marked parameter, field, or property is a route template.


#### `UsedImplicitlyAttribute`

Indicates that the marked symbol is used implicitly (e.g. via reflection, in external library), so this symbol will be ignored by usage-checking inspections. You can use
`ImplicitUseKindFlags` and `ImplicitUseTargetFlags` to configure how this attribute is applied.

**Methods:**

- `#ctor(JetBrains.Annotations.ImplicitUseKindFlags, JetBrains.Annotations.ImplicitUseTargetFlags)`
  - Indicates that the marked symbol is used implicitly (e.g. via reflection, in external library), so this symbol will be ignored by usage-checking inspections. You can use
`ImplicitUseKindFlags` and `ImplicitUseTargetFlags` to configure how this attribute is applied.
