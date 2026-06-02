# Swashbuckle.AspNetCore.SwaggerGen v10.2.1 — API surface

_Generated from the XML doc comments shipped inside these NuGet packages:_

- `Swashbuckle.AspNetCore.SwaggerGen` v10.2.1 (`net8.0+source`)
- `Swashbuckle.AspNetCore.Swagger` v10.2.1 (`net8.0+source`)
- `Swashbuckle.AspNetCore.SwaggerUI` v10.2.1 (`net8.0+source`)
- `Swashbuckle.AspNetCore.Annotations` v10.2.1 (`net8.0+source`)

_Do not edit by hand — rerun `scripts/update_skill.py`._

Use **only** the members listed here when writing code against Swashbuckle.AspNetCore.SwaggerGen v10.2.1. If a member you want isn't here, it doesn't exist in this version and you must pick another approach.

## package `Swashbuckle.AspNetCore.SwaggerGen` v10.2.1

### namespace `Microsoft.Extensions.ApiDescriptions`

#### `IDocumentProvider`

This service will be looked up by name from the service collection when using
the `dotnet-getdocument` tool from the Microsoft.Extensions.ApiDescription.Server package.


### namespace `Microsoft.Extensions.DependencyInjection`

#### `SwaggerGenOptionsExtensions`

**Methods:**

- `AddDocumentAsyncFilterInstance<T>(SwaggerGenOptions, T1)`
  - Extend the Swagger Generator with "filters" that can modify SwaggerDocuments asynchronously after they're initially generated
  - `swaggerGenOptions`
  - `filterInstance`: The filter instance to use.
  - `<TFilter>`: A type that derives from `IDocumentAsyncFilter`
- `AddDocumentAsyncFilterInstance<T>(SwaggerGenOptions, TFilter)`
- `AddDocumentFilterInstance<T>(SwaggerGenOptions, T1)`
  - Extend the Swagger Generator with "filters" that can modify SwaggerDocuments after they're initially generated
  - `swaggerGenOptions`
  - `filterInstance`: The filter instance to use.
  - `<TFilter>`: A type that derives from `IDocumentFilter`
- `AddDocumentFilterInstance<T>(SwaggerGenOptions, TFilter)`
- `AddOperationAsyncFilterInstance<T>(SwaggerGenOptions, T1)`
  - Extend the Swagger Generator with "filters" that can modify Operations asynchronously after they're initially generated
  - `swaggerGenOptions`
  - `filterInstance`: The filter instance to use
  - `<TFilter>`: A type that derives from `IOperationAsyncFilter`
- `AddOperationAsyncFilterInstance<T>(SwaggerGenOptions, TFilter)`
- `AddOperationFilterInstance<T>(SwaggerGenOptions, T1)`
  - Extend the Swagger Generator with "filters" that can modify Operations after they're initially generated
  - `swaggerGenOptions`
  - `filterInstance`: The filter instance to use.
  - `<TFilter>`: A type that derives from `IOperationFilter`
- `AddOperationFilterInstance<T>(SwaggerGenOptions, TFilter)`
- `AddParameterAsyncFilterInstance<T>(SwaggerGenOptions, T1)`
  - Extend the Swagger Generator with "filters" that can modify Parameters asynchronously after they're initially generated
  - `swaggerGenOptions`
  - `filterInstance`: The filter instance to use.
  - `<TFilter>`: A type that derives from `IParameterAsyncFilter`
- `AddParameterAsyncFilterInstance<T>(SwaggerGenOptions, TFilter)`
- `AddParameterFilterInstance<T>(SwaggerGenOptions, T1)`
  - Extend the Swagger Generator with "filters" that can modify Parameters after they're initially generated
  - `swaggerGenOptions`
  - `filterInstance`: The filter instance to use.
  - `<TFilter>`: A type that derives from `IParameterFilter`
- `AddParameterFilterInstance<T>(SwaggerGenOptions, TFilter)`
- `AddRequestBodyAsyncFilterInstance<T>(SwaggerGenOptions, T1)`
  - Extend the Swagger Generator with "filters" that can modify RequestBodys asynchronously after they're initially generated
  - `swaggerGenOptions`
  - `filterInstance`: The filter instance to use.
  - `<TFilter>`: A type that derives from `IRequestBodyAsyncFilter`
- `AddRequestBodyAsyncFilterInstance<T>(SwaggerGenOptions, TFilter)`
- `AddRequestBodyFilterInstance<T>(SwaggerGenOptions, T1)`
  - Extend the Swagger Generator with "filters" that can modify RequestBodys after they're initially generated
  - `swaggerGenOptions`
  - `filterInstance`: The filter instance to use.
  - `<TFilter>`: A type that derives from `IRequestBodyFilter`
- `AddRequestBodyFilterInstance<T>(SwaggerGenOptions, TFilter)`
- `AddSchemaFilterInstance<T>(SwaggerGenOptions, T1)`
  - Extend the Swagger Generator with "filters" that can modify Schemas after they're initially generated
  - `swaggerGenOptions`
  - `filterInstance`: The filter instance to use.
  - `<TFilter>`: A type that derives from `ISchemaFilter`
- `AddSchemaFilterInstance<T>(SwaggerGenOptions, TFilter)`
- `AddSecurityDefinition(SwaggerGenOptions, string, IOpenApiSecurityScheme)`
- `AddSecurityDefinition(SwaggerGenOptions, string, Microsoft.OpenApi.IOpenApiSecurityScheme)`
  - Add one or more "securityDefinitions", describing how your API is protected, to the generated Swagger
  - `swaggerGenOptions`
  - `name`: A unique name for the scheme, as per the Swagger spec.
  - `securityScheme`: A description of the scheme - can be an instance of BasicAuthScheme, ApiKeyScheme or OAuth2Scheme
- `AddSecurityRequirement(SwaggerGenOptions, Func<Microsoft.OpenApi.OpenApiDocument,Microsoft.OpenApi.OpenApiSecurityRequirement>)`
  - Adds a global security requirement
  - `swaggerGenOptions`
  - `securityRequirement`: A dictionary of required schemes (logical AND). Keys must correspond to schemes defined through AddSecurityDefinition
If the scheme is of type "oauth2", then the value is a list of scopes, otherwise it MUST be an empty array
- `AddSecurityRequirement(SwaggerGenOptions, Func<OpenApiDocument, OpenApiSecurityRequirement>)`
- `AddServer(SwaggerGenOptions, Microsoft.OpenApi.OpenApiServer)`
  - Provide specific server information to include in the generated Swagger document
  - `swaggerGenOptions`
  - `server`: A description of the server
- `AddServer(SwaggerGenOptions, OpenApiServer)`
- `CustomOperationIds(SwaggerGenOptions, Func<ApiDescription, string>)`
- `CustomOperationIds(SwaggerGenOptions, Func<Microsoft.AspNetCore.Mvc.ApiExplorer.ApiDescription,string>)`
  - Provide a custom strategy for assigning "operationId" to operations
- `CustomSchemaIds(SwaggerGenOptions, Func<Type, string>)`
- `CustomSchemaIds(SwaggerGenOptions, Func<Type,string>)`
  - Provide a custom strategy for generating the unique Ids that are used to reference object Schemas
  - `swaggerGenOptions`
  - `schemaIdSelector`: A lambda that returns a unique identifier for the provided system type
- `DescribeAllParametersInCamelCase(SwaggerGenOptions)`
  - Describe all parameters, regardless of how they appear in code, in camelCase
- `DocInclusionPredicate(SwaggerGenOptions, Func<string, ApiDescription, bool>)`
- `DocInclusionPredicate(SwaggerGenOptions, Func<string,Microsoft.AspNetCore.Mvc.ApiExplorer.ApiDescription,bool>)`
  - Provide a custom strategy for selecting actions.
  - `swaggerGenOptions`
  - `predicate`: A lambda that returns true/false based on document name and ApiDescription
- `DocumentAsyncFilter<T>(SwaggerGenOptions, object[])`
  - Extend the Swagger Generator with "filters" that can modify SwaggerDocuments asynchronously after they're initially generated
  - `swaggerGenOptions`
  - `arguments`: Optionally inject parameters through filter constructors
  - `<TFilter>`: A type that derives from `IDocumentAsyncFilter`
- `DocumentFilter<T>(SwaggerGenOptions, object[])`
  - Extend the Swagger Generator with "filters" that can modify SwaggerDocuments after they're initially generated
  - `swaggerGenOptions`
  - `arguments`: Optionally inject parameters through filter constructors
  - `<TFilter>`: A type that derives from `IDocumentFilter`
- `IgnoreObsoleteActions(SwaggerGenOptions)`
  - Ignore any actions that are decorated with the ObsoleteAttribute
- `IgnoreObsoleteProperties(SwaggerGenOptions)`
  - Ignore any properties that are decorated with the ObsoleteAttribute
- `IncludeXmlComments(SwaggerGenOptions, Assembly, bool)`
  - Inject human-friendly descriptions for Operations, Parameters and Schemas based on XML comments
from specific Assembly
  - `swaggerGenOptions`
  - `assembly`: Assembly that contains XML Comments
  - `includeControllerXmlComments`: Flag to indicate if controller XML comments (i.e. summary) should be used to assign Tag descriptions.
Don't set this flag if you're customizing the default tag for operations via TagActionsBy.
- `IncludeXmlComments(SwaggerGenOptions, Func<XPath.XPathDocument>, bool)`
  - Inject human-friendly descriptions for Operations, Parameters and Schemas based on XML Comment files
  - `swaggerGenOptions`
  - `xmlDocFactory`: A factory method that returns XML Comments as an XPathDocument
  - `includeControllerXmlComments`: Flag to indicate if controller XML comments (i.e. summary) should be used to assign Tag descriptions.
Don't set this flag if you're customizing the default tag for operations via TagActionsBy.
- `IncludeXmlComments(SwaggerGenOptions, Func<XPathDocument>, bool)`
- `IncludeXmlComments(SwaggerGenOptions, string, bool)`
  - Inject human-friendly descriptions for Operations, Parameters and Schemas based on XML Comment files
  - `swaggerGenOptions`
  - `filePath`: An absolute path to the file that contains XML Comments
  - `includeControllerXmlComments`: Flag to indicate if controller XML comments (i.e. summary) should be used to assign Tag descriptions.
Don't set this flag if you're customizing the default tag for operations via TagActionsBy.
- `InferSecuritySchemes(SwaggerGenOptions, Func<Generic.IEnumerable<Microsoft.AspNetCore.Authentication.AuthenticationScheme>,Generic.IDictionary<string,Microsoft.OpenApi.IOpenApiSecurityScheme>>)`
  - Automatically infer security schemes from authentication/authorization state in ASP.NET Core.
  - `swaggerGenOptions`
  - `securitySchemesSelector`: Provide alternative implementation that maps ASP.NET Core Authentication schemes to Open API security schemes
  - remarks: Currently only supports JWT Bearer authentication
- `InferSecuritySchemes(SwaggerGenOptions, Func<IEnumerable<AuthenticationScheme>, IDictionary<string, IOpenApiSecurityScheme>>)`
- `MapType(SwaggerGenOptions, Type, Func<IOpenApiSchema>)`
- `MapType(SwaggerGenOptions, Type, Func<Microsoft.OpenApi.IOpenApiSchema>)`
  - Provide a custom mapping, for a given type, to the Swagger-flavored JSONSchema
  - `swaggerGenOptions`
  - `type`: System type
  - `schemaFactory`: A factory method that generates Schema's for the provided type
- `MapType<T>(SwaggerGenOptions, Func<IOpenApiSchema>)`
- `MapType<T>(SwaggerGenOptions, Func<Microsoft.OpenApi.IOpenApiSchema>)`
  - Provide a custom mapping, for a given type, to the Swagger-flavored JSONSchema
  - `swaggerGenOptions`
  - `schemaFactory`: A factory method that generates Schema's for the provided type
  - `<T>`: System type
- `NonNullableReferenceTypesAsRequired(SwaggerGenOptions)`
  - Enable detection of non nullable reference types to mark the member as required in schema properties
  - `swaggerGenOptions`
- `OperationAsyncFilter<T>(SwaggerGenOptions, object[])`
  - Extend the Swagger Generator with "filters" that can modify Operations asynchronously after they're initially generated
  - `swaggerGenOptions`
  - `arguments`: Optionally inject parameters through filter constructors
  - `<TFilter>`: A type that derives from `IOperationAsyncFilter`
- `OperationFilter<T>(SwaggerGenOptions, object[])`
  - Extend the Swagger Generator with "filters" that can modify Operations after they're initially generated
  - `swaggerGenOptions`
  - `arguments`: Optionally inject parameters through filter constructors
  - `<TFilter>`: A type that derives from `IOperationFilter`
- `OrderActionsBy(SwaggerGenOptions, Func<ApiDescription, string>)`
- `OrderActionsBy(SwaggerGenOptions, Func<Microsoft.AspNetCore.Mvc.ApiExplorer.ApiDescription,string>)`
  - Provide a custom strategy for sorting actions before they're transformed into the Swagger format
  - `swaggerGenOptions`
  - `sortKeySelector`
- `ParameterAsyncFilter<T>(SwaggerGenOptions, object[])`
  - Extend the Swagger Generator with "filters" that can modify Parameters asynchronously after they're initially generated
  - `swaggerGenOptions`
  - `arguments`: Optionally inject parameters through filter constructors
  - `<TFilter>`: A type that derives from `IParameterAsyncFilter`
- `ParameterFilter<T>(SwaggerGenOptions, object[])`
  - Extend the Swagger Generator with "filters" that can modify Parameters after they're initially generated
  - `swaggerGenOptions`
  - `arguments`: Optionally inject parameters through filter constructors
  - `<TFilter>`: A type that derives from `IParameterFilter`
- `RequestBodyAsyncFilter<T>(SwaggerGenOptions, object[])`
  - Extend the Swagger Generator with "filters" that can modify RequestBodys asynchronously after they're initially generated
  - `swaggerGenOptions`
  - `arguments`: Optionally inject parameters through filter constructors
  - `<TFilter>`: A type that derives from `IRequestBodyAsyncFilter`
- `RequestBodyFilter<T>(SwaggerGenOptions, object[])`
  - Extend the Swagger Generator with "filters" that can modify RequestBodys after they're initially generated
  - `swaggerGenOptions`
  - `arguments`: Optionally inject parameters through filter constructors
  - `<TFilter>`: A type that derives from `IRequestBodyFilter`
- `ResolveConflictingActions(SwaggerGenOptions, Func<Generic.IEnumerable<Microsoft.AspNetCore.Mvc.ApiExplorer.ApiDescription>,Microsoft.AspNetCore.Mvc.ApiExplorer.ApiDescription>)`
  - Merge actions that have conflicting HTTP methods and paths (must be unique for Swagger 2.0)
  - `swaggerGenOptions`
  - `resolver`
- `ResolveConflictingActions(SwaggerGenOptions, Func<IEnumerable<ApiDescription>, ApiDescription>)`
- `SchemaFilter<T>(SwaggerGenOptions, object[])`
  - Extend the Swagger Generator with "filters" that can modify Schemas after they're initially generated
  - `swaggerGenOptions`
  - `arguments`: Optionally inject parameters through filter constructors
  - `<TFilter>`: A type that derives from `ISchemaFilter`
- `SelectDiscriminatorNameUsing(SwaggerGenOptions, Func<Type, string>)`
- `SelectDiscriminatorNameUsing(SwaggerGenOptions, Func<Type,string>)`
  - If the configured serializer supports polymorphic serialization/deserialization by emitting/accepting a special "discriminator" property,
and UseOneOfForPolymorphism is enabled, then Swashbuckle will include a description for that property based on the serializer's behavior.
However, if you've customized your serializer to support polymorphism, you can provide a custom strategy to tell Swashbuckle which property,
for a given type, will be used as a discriminator. This setting is only applicable when used in conjunction with UseOneOfForPolymorphism.
  - `swaggerGenOptions`
  - `customSelector`
- `SelectDiscriminatorValueUsing(SwaggerGenOptions, Func<Type, string>)`
- `SelectDiscriminatorValueUsing(SwaggerGenOptions, Func<Type,string>)`
  - If the configured serializer supports polymorphic serialization/deserialization by emitting/accepting a special "discriminator" property,
and UseOneOfForPolymorphism is enabled, then Swashbuckle will include a mapping of possible discriminator values to schema definitions.
However, if you've customized your serializer to support polymorphism, you can provide a custom mapping strategy to tell Swashbuckle what
the discriminator value should be for a given sub type. This setting is only applicable when used in conjunction with UseOneOfForPolymorphism.
  - `swaggerGenOptions`
  - `customSelector`
- `SelectSubTypesUsing(SwaggerGenOptions, Func<Type, IEnumerable<Type>>)`
- `SelectSubTypesUsing(SwaggerGenOptions, Func<Type,Generic.IEnumerable<Type>>)`
  - To support polymorphism and inheritance behavior, Swashbuckle needs to detect the "known" subtypes for a given base type.
That is, the subtypes exposed by your API. By default, this will be any subtypes in the same assembly as the base type.
To override this, you can provide a custom selector function. This setting is only applicable when used in conjunction with
UseOneOfForPolymorphism and/or UseAllOfForInheritance.
  - `swaggerGenOptions`
  - `customSelector`
- `SortSchemasWith(SwaggerGenOptions, Generic.IComparer<string>)`
  - Provide a custom comprarer to sort schemas with
  - `swaggerGenOptions`
  - `schemaComparer`
- `SortSchemasWith(SwaggerGenOptions, IComparer<string>)`
- `SupportNonNullableReferenceTypes(SwaggerGenOptions)`
  - Enable detection of non nullable reference types to set Nullable flag accordingly on schema properties
  - `swaggerGenOptions`
- `SwaggerDoc(SwaggerGenOptions, string, Microsoft.OpenApi.OpenApiInfo)`
  - Define one or more documents to be created by the Swagger generator
  - `swaggerGenOptions`
  - `name`: A URI-friendly name that uniquely identifies the document
  - `info`: Global metadata to be included in the Swagger output
- `SwaggerDoc(SwaggerGenOptions, string, OpenApiInfo)`
- `TagActionsBy(SwaggerGenOptions, Func<ApiDescription, IList<string>>)`
- `TagActionsBy(SwaggerGenOptions, Func<Microsoft.AspNetCore.Mvc.ApiExplorer.ApiDescription,Generic.IList<string>>)`
  - Provide a custom strategy for assigning "tags" to actions
  - `swaggerGenOptions`
  - `tagsSelector`
- `UseAllOfForInheritance(SwaggerGenOptions)`
  - Enables composite schema generation. If enabled, subtype schemas will contain the allOf construct to
incorporate properties from the base class instead of defining those properties inline.
  - `swaggerGenOptions`
- `UseAllOfToExtendReferenceSchemas(SwaggerGenOptions)`
  - Extend reference schemas (using the allOf construct) so that contextual metadata can be applied to all parameter and property schemas
  - `swaggerGenOptions`
- `UseInlineDefinitionsForEnums(SwaggerGenOptions)`
  - Generate inline schema definitions (as opposed to referencing a shared definition) for enum parameters and properties
  - `swaggerGenOptions`
- `UseOneOfForPolymorphism(SwaggerGenOptions)`
  - Enables polymorphic schema generation. If enabled, request and response schemas will contain the oneOf
construct to describe sub types as a set of alternative schemas.
  - `swaggerGenOptions`


#### `SwaggerGenServiceCollectionExtensions`

**Methods:**

- `AddSwaggerGen(IServiceCollection, Action<SwaggerGenOptions>)`
- `ConfigureSwaggerGen(IServiceCollection, Action<SwaggerGenOptions>)`


### namespace `Swashbuckle.AspNetCore.Annotations`

#### `SwaggerIgnoreAttribute`

Causes the annotated member to be ignored during schema generation.
Does not alter serialization behavior.


### namespace `Swashbuckle.AspNetCore.SwaggerGen`

#### `ApiDescriptionExtensions`

**Methods:**

- `CustomAttributes(ApiDescription)`
- `TryGetMethodInfo(ApiDescription, MethodInfo)`


#### `ApiParameterDescriptionExtensions`

**Methods:**

- `CustomAttributes(ApiParameterDescription)`
- `IsRequiredParameter(ApiParameterDescription)`
- `ParameterInfo(ApiParameterDescription)`
- `PropertyInfo(ApiParameterDescription)`


#### `ApiResponseTypeExtensions`


#### `DataContract`

**Methods:**

- `ForArray(Type, Type, Func<object, string>)`
- `ForDictionary(Type, Type, IEnumerable<string>, Func<object, string>)`
- `ForDynamic(Type, Func<object, string>)`
- `ForObject(Type, IEnumerable<DataProperty>, Type, string, string, Func<object, string>)`
- `ForPrimitive(Type, DataType, string, Func<object, string>)`

**Properties:**

- `ArrayItemType`
- `DataFormat`
- `DataType`
- `DictionaryKeys`
- `DictionaryValueType`
- `JsonConverter`
- `ObjectExtensionDataType`
- `ObjectProperties`
- `ObjectTypeNameProperty`
- `ObjectTypeNameValue`
- `UnderlyingType`


#### `DataProperty`

**Properties:**

- `IsNullable`
- `IsReadOnly`
- `IsRequired`
- `IsWriteOnly`
- `MemberInfo`
- `MemberType`
- `Name`


#### `DataType`

**Fields:**

- `Array`
- `Boolean`
- `Dictionary`
- `Integer`
- `Number`
- `Object`
- `String`
- `Unknown`


#### `DocumentFilterContext`

**Properties:**

- `ApiDescriptions`
- `SchemaGenerator`
- `SchemaRepository`

**Fields:**

- `DocumentName`


#### `FilterDescriptor`

**Properties:**

- `Arguments`
- `FilterInstance`
- `Type`


#### `IDictionary<T>`


#### `IDocumentAsyncFilter`


#### `IDocumentFilter`


#### `IOperationAsyncFilter`


#### `IOperationFilter`


#### `IParameterAsyncFilter`


#### `IParameterFilter`


#### `IRequestBodyAsyncFilter`


#### `IRequestBodyFilter`


#### `ISchemaFilter`


#### `ISchemaGenerator`


#### `ISerializerDataContractResolver`


#### `JsonSerializerDataContractResolver`

**Methods:**

- `GetDataContractForType(Type)`
- `IsSupportedCollection(Type, Type)`
- `IsSupportedDictionary(Type, Type, Type)`


#### `MemberInfoExtensions`

**Methods:**

- `GetInlineAndMetadataAttributes(MemberInfo)`
- `IsDictionaryValueNonNullable(MemberInfo)`
- `IsNonNullableReferenceType(MemberInfo)`


#### `MethodInfoExtensions`

**Methods:**

- `GetUnderlyingGenericTypeMethod(MethodInfo)`


#### `OpenApiSchemaExtensions`

**Methods:**

- `ApplyRouteConstraints(IOpenApiSchema, ApiParameterRouteInfo)`
- `ApplyValidationAttributes(IOpenApiSchema, IEnumerable<object>)`


#### `OperationFilterContext`

**Properties:**

- `ApiDescription`
- `Document`
- `MethodInfo`
- `SchemaGenerator`
- `SchemaRepository`

**Fields:**

- `DocumentName`


#### `ParameterFilterContext`

**Properties:**

- `ApiParameterDescription`
- `Document`
- `ParameterInfo`
- `PropertyInfo`
- `SchemaGenerator`
- `SchemaRepository`

**Fields:**

- `DocumentName`


#### `PropertyInfoExtensions`

**Methods:**

- `HasAttribute<T>(PropertyInfo)`
- `IsPubliclyReadable(PropertyInfo)`
- `IsPubliclyWritable(PropertyInfo)`


#### `RequestBodyFilterContext`

**Properties:**

- `BodyParameterDescription`
- `Document`
- `FormParameterDescriptions`
- `SchemaGenerator`
- `SchemaRepository`

**Fields:**

- `DocumentName`


#### `SchemaFilterContext`

**Properties:**

- `MemberInfo`
- `ParameterInfo`
- `SchemaGenerator`
- `SchemaRepository`
- `Type`

**Fields:**

- `DocumentName`


#### `SchemaGenerator`

**Methods:**

- `GenerateSchema(Type, SchemaRepository, MemberInfo, ParameterInfo, ApiParameterRouteInfo)`


#### `SchemaGeneratorOptions`

**Methods:**

- `#ctor`

**Properties:**

- `CustomTypeMappings`
- `DiscriminatorNameSelector`
- `DiscriminatorValueSelector`
- `IgnoreObsoleteProperties`
- `NonNullableReferenceTypesAsRequired`
- `SchemaFilters`
- `SchemaIdSelector`
- `SubTypesSelector`
- `SupportNonNullableReferenceTypes`
- `UseAllOfForInheritance`
- `UseAllOfToExtendReferenceSchemas`
- `UseInlineDefinitionsForEnums`
- `UseOneOfForPolymorphism`


#### `SchemaRepository`

**Methods:**

- `AddDefinition(string, OpenApiSchema)`
- `RegisterType(Type, string)`
- `ReplaceSchemaId(Type, string)`
- `TryLookupByType(Type, [CodeAnalysis.NotNullWhen(true)] out OpenApiSchemaReference)`

**Properties:**

- `DocumentName`
- `Schemas`


#### `SwaggerApplicationConvention`

**Methods:**

- `Apply(ApplicationModel)`


#### `SwaggerGenOptions`

**Properties:**

- `DocumentFilterDescriptors`
- `OperationFilterDescriptors`
- `ParameterFilterDescriptors`
- `RequestBodyFilterDescriptors`
- `SchemaFilterDescriptors`
- `SchemaGeneratorOptions`
- `SwaggerGeneratorOptions`


#### `SwaggerGenerator`


#### `SwaggerGeneratorException`

**Methods:**

- `#ctor(string)`
- `#ctor(string, Exception)`


#### `SwaggerGeneratorOptions`

**Methods:**

- `#ctor`

**Properties:**

- `ConflictingActionsResolver`
- `DescribeAllParametersInCamelCase`
- `DocInclusionPredicate`
- `DocumentAsyncFilters`
- `DocumentFilters`
- `IgnoreObsoleteActions`
- `InferSecuritySchemes`
- `OperationAsyncFilters`
- `OperationFilters`
- `OperationIdSelector`
- `ParameterAsyncFilters`
- `ParameterFilters`
- `PathGroupSelector`
- `RequestBodyAsyncFilters`
- `RequestBodyFilters`
- `SchemaComparer`
- `SecurityRequirements`
- `SecuritySchemes`
- `SecuritySchemesSelector`
- `Servers`
- `SortKeySelector`
- `SwaggerDocs`
- `TagsSelector`
- `XmlCommentEndOfLine`


#### `TypeExtensions`

**Methods:**

- `GetDefaultValue(Type)`
- `GetInheritanceChain(Type)`
- `IsAssignableTo(Type, Type)`
- `IsAssignableToOneOf(Type, Type[])`
- `IsConstructedFrom(Type, Type, Type)`
- `IsOneOf(Type, Type[])`
- `IsReferenceOrNullableType(Type)`


#### `XmlCommentsDocumentFilter`

**Methods:**

- `Apply(OpenApiDocument, DocumentFilterContext)`


#### `XmlCommentsNodeNameHelper`

**Methods:**

- `GetMemberNameForFieldOrProperty(MemberInfo)`
- `GetMemberNameForMethod(MethodInfo)`
- `GetMemberNameForType(Type)`


#### `XmlCommentsOperationFilter`

**Methods:**

- `Apply(OpenApiOperation, OperationFilterContext)`


#### `XmlCommentsParameterFilter`

**Methods:**

- `Apply(IOpenApiParameter, ParameterFilterContext)`


#### `XmlCommentsRequestBodyFilter`

**Methods:**

- `Apply(IOpenApiRequestBody, RequestBodyFilterContext)`


#### `XmlCommentsSchemaFilter`

**Methods:**

- `Apply(IOpenApiSchema, SchemaFilterContext)`


#### `XmlCommentsTextHelper`

**Methods:**

- `BrTag`
  - remarks: Pattern:
`(<br ?\\/?>)`
Explanation:
`○ 1st capture group.
○ Match the string "<br".
○ Match ' ' atomically, optionally.
○ Match '/' atomically, optionally.
○ Match '>'.`
- `CodeTag`
  - remarks: Pattern:
`<c>(?<display>.+?)</c>`
Explanation:
`○ Match the string "<c>".
○ "display" capture group.
○ Match a character other than '\n' lazily at least once.
○ Match the string "</c>".`
- `DoubleUpLineBreaks`
  - remarks: Pattern:
`(\\r?\\n){2,}`
Explanation:
`○ Loop greedily and atomically at least twice.
○ 1st capture group.
○ Match '\r' atomically, optionally.
○ Match '\n'.`
- `HrefTag`
  - remarks: Pattern:
`<see\\s+href=\\"([^"]*)\\">\\s*(.*?)\\s*<\\/see>`
Options:
`RegexOptions.Singleline`
Explanation:
`○ Match the string "<see".
○ Match a whitespace character atomically at least once.
○ Match the string "href=\"".
○ 1st capture group.
○ Match a character other than '"' atomically any number of times.
○ Match the string "\">".
○ Match a whitespace character greedily any number of times.
○ 2nd capture group.
○ Match any character lazily any number of times.
○ Match a whitespace character atomically any number of times.
○ Match the string "</see>".`
- `Humanize(string)`
- `Humanize(string, string)`
- `LineBreaks`
  - remarks: Pattern:
`\\r?\\n`
Explanation:
`○ Match '\r' atomically, optionally.
○ Match '\n'.`
- `MultilineCodeTag`
  - remarks: Pattern:
`<code>(?<display>.+?)</code>`
Options:
`RegexOptions.Singleline`
Explanation:
`○ Match the string "<code>".
○ "display" capture group.
○ Match any character lazily at least once.
○ Match the string "</code>".`
- `ParaTag`
  - remarks: Pattern:
`<para>(?<display>.+?)</para>`
Options:
`RegexOptions.Singleline`
Explanation:
`○ Match the string "<para>".
○ "display" capture group.
○ Match any character lazily at least once.
○ Match the string "</para>".`
- `RefTag`
  - remarks: Pattern:
`<(see|paramref) (name|cref|langword)="([TPF]{1}:)?(?<display>.+?)" ?/>`
Explanation:
`○ Match '<'.
○ 1st capture group.
○ Match with 2 alternative expressions.
○ Match the string "see".
○ Match the string "paramref".
○ Match ' '.
○ 2nd capture group.
○ Match with 3 alternative expressions.
○ Match the string "name".
○ Match the string "cref".
○ Match the string "langword".
○ Match the string "=\"".
○ Optional (greedy).
○ 3rd capture group.
○ Match a character in the set [FPT].
○ Match ':'.
○ "display" capture group.
○ Match a character other than '\n' lazily at least once.
○ Match '"'.
○ Match ' ' atomically, optionally.
○ Match the string "/>".`


### namespace `System.Text.RegularExpressions.Generated`

#### `BrTag_5`

Custom `Regex`-derived type for the BrTag method.

**Methods:**

- `#ctor`
  - Initializes the instance.

**Fields:**

- `Instance`
  - Cached, thread-safe singleton instance.


#### `CodeTag_1`

Custom `Regex`-derived type for the CodeTag method.

**Methods:**

- `#ctor`
  - Initializes the instance.

**Fields:**

- `Instance`
  - Cached, thread-safe singleton instance.


#### `DoubleUpLineBreaks_7`

Custom `Regex`-derived type for the DoubleUpLineBreaks method.

**Methods:**

- `#ctor`
  - Initializes the instance.

**Fields:**

- `Instance`
  - Cached, thread-safe singleton instance.


#### `HrefTag_4`

Custom `Regex`-derived type for the HrefTag method.

**Methods:**

- `#ctor`
  - Initializes the instance.

**Fields:**

- `Instance`
  - Cached, thread-safe singleton instance.


#### `LineBreaks_6`

Custom `Regex`-derived type for the LineBreaks method.

**Methods:**

- `#ctor`
  - Initializes the instance.

**Fields:**

- `Instance`
  - Cached, thread-safe singleton instance.


#### `MultilineCodeTag_2`

Custom `Regex`-derived type for the MultilineCodeTag method.

**Methods:**

- `#ctor`
  - Initializes the instance.

**Fields:**

- `Instance`
  - Cached, thread-safe singleton instance.


#### `ParaTag_3`

Custom `Regex`-derived type for the ParaTag method.

**Methods:**

- `#ctor`
  - Initializes the instance.

**Fields:**

- `Instance`
  - Cached, thread-safe singleton instance.


#### `RefTag_0`

Custom `Regex`-derived type for the RefTag method.

**Methods:**

- `#ctor`
  - Initializes the instance.

**Fields:**

- `Instance`
  - Cached, thread-safe singleton instance.


#### `Utilities`

Helper methods used by generated `Regex`-derived implementations.

**Methods:**

- `StackPush(int[]@, int@, int, int)`
  - Pushes 2 values onto the backtracking stack.

**Fields:**

- `s_defaultTimeout`
  - Default timeout value set in `AppContext`, or `InfiniteMatchTimeout` if none was set.
- `s_hasTimeout`
  - Whether `s_defaultTimeout` is non-infinite.


### namespace `System.Text.RegularExpressions.Generated.BrTag_5`

#### `RunnerFactory`

Provides a factory for creating `RegexRunner` instances to be used by methods on `Regex`.

**Methods:**

- `CreateInstance`
  - Creates an instance of a `RegexRunner` used by methods on `Regex`.


### namespace `System.Text.RegularExpressions.Generated.BrTag_5.RunnerFactory`

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


### namespace `System.Text.RegularExpressions.Generated.CodeTag_1`

#### `RunnerFactory`

Provides a factory for creating `RegexRunner` instances to be used by methods on `Regex`.

**Methods:**

- `CreateInstance`
  - Creates an instance of a `RegexRunner` used by methods on `Regex`.


### namespace `System.Text.RegularExpressions.Generated.CodeTag_1.RunnerFactory`

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


### namespace `System.Text.RegularExpressions.Generated.DoubleUpLineBreaks_7`

#### `RunnerFactory`

Provides a factory for creating `RegexRunner` instances to be used by methods on `Regex`.

**Methods:**

- `CreateInstance`
  - Creates an instance of a `RegexRunner` used by methods on `Regex`.


### namespace `System.Text.RegularExpressions.Generated.DoubleUpLineBreaks_7.RunnerFactory`

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


### namespace `System.Text.RegularExpressions.Generated.HrefTag_4`

#### `RunnerFactory`

Provides a factory for creating `RegexRunner` instances to be used by methods on `Regex`.

**Methods:**

- `CreateInstance`
  - Creates an instance of a `RegexRunner` used by methods on `Regex`.


### namespace `System.Text.RegularExpressions.Generated.HrefTag_4.RunnerFactory`

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


### namespace `System.Text.RegularExpressions.Generated.LineBreaks_6`

#### `RunnerFactory`

Provides a factory for creating `RegexRunner` instances to be used by methods on `Regex`.

**Methods:**

- `CreateInstance`
  - Creates an instance of a `RegexRunner` used by methods on `Regex`.


### namespace `System.Text.RegularExpressions.Generated.LineBreaks_6.RunnerFactory`

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


### namespace `System.Text.RegularExpressions.Generated.MultilineCodeTag_2`

#### `RunnerFactory`

Provides a factory for creating `RegexRunner` instances to be used by methods on `Regex`.

**Methods:**

- `CreateInstance`
  - Creates an instance of a `RegexRunner` used by methods on `Regex`.


### namespace `System.Text.RegularExpressions.Generated.MultilineCodeTag_2.RunnerFactory`

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


### namespace `System.Text.RegularExpressions.Generated.ParaTag_3`

#### `RunnerFactory`

Provides a factory for creating `RegexRunner` instances to be used by methods on `Regex`.

**Methods:**

- `CreateInstance`
  - Creates an instance of a `RegexRunner` used by methods on `Regex`.


### namespace `System.Text.RegularExpressions.Generated.ParaTag_3.RunnerFactory`

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


### namespace `System.Text.RegularExpressions.Generated.RefTag_0`

#### `RunnerFactory`

Provides a factory for creating `RegexRunner` instances to be used by methods on `Regex`.

**Methods:**

- `CreateInstance`
  - Creates an instance of a `RegexRunner` used by methods on `Regex`.


### namespace `System.Text.RegularExpressions.Generated.RefTag_0.RunnerFactory`

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



## package `Swashbuckle.AspNetCore.Swagger` v10.2.1

### namespace `Microsoft.AspNetCore.Builder`

#### `SwaggerBuilderExtensions`

**Methods:**

- `MapSwagger(IEndpointRouteBuilder, string, Action<SwaggerEndpointOptions>)`
- `UseSwagger(IApplicationBuilder, Action<SwaggerOptions>)`
- `UseSwagger(IApplicationBuilder, SwaggerOptions)`
- `UseSwagger(Microsoft.AspNetCore.Builder.IApplicationBuilder, Action<Swashbuckle.AspNetCore.Swagger.SwaggerOptions>)`
  - Register the Swagger middleware with optional setup action for DI-injected options
- `UseSwagger(Microsoft.AspNetCore.Builder.IApplicationBuilder, Swashbuckle.AspNetCore.Swagger.SwaggerOptions)`
  - Register the Swagger middleware with provided options


### namespace `Microsoft.Extensions.DependencyInjection`

#### `SwaggerOptionsExtensions`

Extensions for helping with configuring instances of `SwaggerOptions`.

**Methods:**

- `SetCustomDocumentSerializer<T>(SwaggerOptions, object[])`
- `SetCustomDocumentSerializer<T>(Swashbuckle.AspNetCore.Swagger.SwaggerOptions, object[])`
  - Sets a custom Swagger document serializer to use.
  - `swaggerOptions`: The options to configure the serializer for.
  - `constructorParameters`: The parameters to pass into the constructor of the custom Swagger document serializer implementation.
  - `<TDocumentSerializer>`: The type of the custom Swagger document serializer implementation.
  - remarks: For the CLI tool to be able to use this, this needs to be configured for use in the service collection of your application.


#### `SwaggerServiceCollectionExtensions`

Extensions to configure dependencies for Swagger.

**Methods:**

- `ConfigureSwagger(IServiceCollection, Action<SwaggerOptions>)`
- `ConfigureSwagger(Microsoft.Extensions.DependencyInjection.IServiceCollection, Action<Swashbuckle.AspNetCore.Swagger.SwaggerOptions>)`
  - Configures Swagger options in the specified service collection.
  - `services`: The service collection to configure the Swagger options for.
  - `setupAction`: A delegate to a method to use to configure the Swagger options.


### namespace `Swashbuckle.AspNetCore.Swagger`

#### `IAsyncSwaggerProvider`


#### `ISwaggerDocumentMetadataProvider`


#### `ISwaggerDocumentSerializer`

Provide an implementation for this interface if you wish to customize how the OpenAPI document is written.

**Methods:**

- `SerializeDocument(Microsoft.OpenApi.OpenApiDocument, Microsoft.OpenApi.IOpenApiWriter, Microsoft.OpenApi.OpenApiSpecVersion)`
  - Serializes an OpenAPI document.
  - `document`: The OpenAPI document that should be serialized.
  - `writer`: The writer to which the document needs to be written.
  - `specVersion`: The OpenAPI specification version to serialize as.


#### `ISwaggerProvider`


#### `SwaggerEndpointOptions`

**Methods:**

- `#ctor`

**Properties:**

- `OpenApiVersion`
  - Gets or sets the OpenAPI (Swagger) document version to use.
  - remarks: The default value is `OpenApi3_0`.
- `PreSerializeFilters`
  - Actions that can be applied SwaggerDocument's before they're serialized to JSON.
Useful for setting metadata that's derived from the current request


#### `SwaggerOptions`

**Methods:**

- `#ctor`

**Properties:**

- `CustomDocumentSerializer`
  - Gets or sets an optional custom `ISwaggerDocumentSerializer` implementation to use to serialize Swagger documents.
  - remarks: For the CLI tool to be able to use this, this needs to be configured for use in the service collection of your application.
- `OpenApiVersion`
  - Gets or sets the OpenAPI (Swagger) document version to use.
  - remarks: The default value is `OpenApi3_0`.
- `PreSerializeFilters`
  - Actions that can be applied to an OpenApiDocument before it's serialized.
Useful for setting metadata that's derived from the current request.
- `RouteTemplate`
  - Sets a custom route for the Swagger JSON/YAML endpoint(s). Must include the {documentName} parameter


#### `UnknownSwaggerDocument`



## package `Swashbuckle.AspNetCore.SwaggerUI` v10.2.1

### namespace `Microsoft.AspNetCore.Builder`

#### `SwaggerUIBuilderExtensions`

**Methods:**

- `MapSwaggerUI(IEndpointRouteBuilder, string, Action<SwaggerUIOptions>)`
- `MapSwaggerUI(Microsoft.AspNetCore.Routing.IEndpointRouteBuilder, string, Action<Swashbuckle.AspNetCore.SwaggerUI.SwaggerUIOptions>)`
  - Maps the SwaggerUI middleware to the specified endpoint route.
  - `endpoints`: Endpoint route builder to which the SwaggerUI middleware will be mapped.
  - `routePrefix`: Optional: The route to register SwaggerUI on. Defaults to the `RoutePrefix` value.
  - `setupAction`: Optional setup action to configure the `SwaggerUIOptions`.
  - returns: An `IEndpointConventionBuilder` that can be used to further configure the endpoint.
  - remarks: This is a convenience extension method that combines the registration of the SwaggerUI middleware with endpoint
routing. It allows you to specify the route pattern for the SwaggerUI and optionally configure the `SwaggerUIOptions`.
- `UseSwaggerUI(IApplicationBuilder, Action<SwaggerUIOptions>)`
- `UseSwaggerUI(IApplicationBuilder, SwaggerUIOptions)`
- `UseSwaggerUI(Microsoft.AspNetCore.Builder.IApplicationBuilder, Action<Swashbuckle.AspNetCore.SwaggerUI.SwaggerUIOptions>)`
  - Register the SwaggerUI middleware with optional setup action for DI-injected options
- `UseSwaggerUI(Microsoft.AspNetCore.Builder.IApplicationBuilder, Swashbuckle.AspNetCore.SwaggerUI.SwaggerUIOptions)`
  - Register the SwaggerUI middleware with provided options


#### `SwaggerUIOptionsExtensions`

**Methods:**

- `DefaultModelExpandDepth(SwaggerUIOptions, int)`
- `DefaultModelExpandDepth(Swashbuckle.AspNetCore.SwaggerUI.SwaggerUIOptions, int)`
  - The default expansion depth for the model on the model-example section
  - `options`
  - `depth`
- `DefaultModelRendering(SwaggerUIOptions, ModelRendering)`
- `DefaultModelRendering(Swashbuckle.AspNetCore.SwaggerUI.SwaggerUIOptions, Swashbuckle.AspNetCore.SwaggerUI.ModelRendering)`
  - Controls how the model is shown when the API is first rendered.
(The user can always switch the rendering for a given model by clicking the 'Model' and 'Example Value' links.)
  - `options`
  - `modelRendering`
- `DefaultModelsExpandDepth(SwaggerUIOptions, int)`
- `DefaultModelsExpandDepth(Swashbuckle.AspNetCore.SwaggerUI.SwaggerUIOptions, int)`
  - The default expansion depth for models (set to -1 completely hide the models)
  - `options`
  - `depth`
- `DisplayOperationId(SwaggerUIOptions)`
- `DisplayOperationId(Swashbuckle.AspNetCore.SwaggerUI.SwaggerUIOptions)`
  - Controls the display of operationId in operations list
  - `options`
- `DisplayRequestDuration(SwaggerUIOptions)`
- `DisplayRequestDuration(Swashbuckle.AspNetCore.SwaggerUI.SwaggerUIOptions)`
  - Controls the display of the request duration (in milliseconds) for Try-It-Out requests
  - `options`
- `DocExpansion(SwaggerUIOptions, DocExpansion)`
- `DocExpansion(Swashbuckle.AspNetCore.SwaggerUI.SwaggerUIOptions, Swashbuckle.AspNetCore.SwaggerUI.DocExpansion)`
  - Controls the default expansion setting for the operations and tags.
It can be 'List' (expands only the tags), 'Full' (expands the tags and operations) or 'None' (expands nothing)
  - `options`
  - `docExpansion`
- `EnableDeepLinking(SwaggerUIOptions)`
- `EnableDeepLinking(Swashbuckle.AspNetCore.SwaggerUI.SwaggerUIOptions)`
  - Enables deep linking for tags and operations
  - `options`
- `EnableFilter(SwaggerUIOptions, string)`
- `EnableFilter(Swashbuckle.AspNetCore.SwaggerUI.SwaggerUIOptions, string)`
  - Enables filtering. The top bar will show an edit box that you can use to filter the tagged operations that are shown.
If an expression is provided it will be used and applied initially.
Filtering is case sensitive matching the filter expression anywhere inside the tag
  - `options`
  - `expression`
- `EnablePersistAuthorization(SwaggerUIOptions)`
- `EnablePersistAuthorization(Swashbuckle.AspNetCore.SwaggerUI.SwaggerUIOptions)`
  - Enables persist authorization data
  - `options`
- `EnableSwaggerDocumentUrlsEndpoint(SwaggerUIOptions)`
- `EnableSwaggerDocumentUrlsEndpoint(Swashbuckle.AspNetCore.SwaggerUI.SwaggerUIOptions)`
  - Function to enable the `ExposeSwaggerDocumentUrlsRoute` option to expose the available
Swagger document urls to external parties.
  - `options`
- `EnableTryItOutByDefault(SwaggerUIOptions)`
- `EnableTryItOutByDefault(Swashbuckle.AspNetCore.SwaggerUI.SwaggerUIOptions)`
  - Enables the "Try it out" section by default.
  - `options`
- `EnableValidator`
- `EnableValidator(Swashbuckle.AspNetCore.SwaggerUI.SwaggerUIOptions, string)`
  - You can use this parameter to enable the swagger-ui's built-in validator (badge) functionality
Setting it to null will disable validation
  - `options`
  - `url`
- `InjectJavascript(SwaggerUIOptions, string, string)`
- `InjectJavascript(Swashbuckle.AspNetCore.SwaggerUI.SwaggerUIOptions, string, string)`
  - Injects additional Javascript files into the index.html page
  - `options`
  - `path`: A path to the javascript - i.e. the script "src" attribute
  - `type`: The script type - i.e. the script "type" attribute
- `InjectStylesheet(SwaggerUIOptions, string, string)`
- `InjectStylesheet(Swashbuckle.AspNetCore.SwaggerUI.SwaggerUIOptions, string, string)`
  - Injects additional CSS stylesheets into the index.html page
  - `options`
  - `path`: A path to the stylesheet - i.e. the link "href" attribute
  - `media`: The target media - i.e. the link "media" attribute
- `MaxDisplayedTags(SwaggerUIOptions, int)`
- `MaxDisplayedTags(Swashbuckle.AspNetCore.SwaggerUI.SwaggerUIOptions, int)`
  - Limits the number of tagged operations displayed to at most this many. The default is to show all operations
  - `options`
  - `count`
- `OAuth2RedirectUrl(SwaggerUIOptions, string)`
- `OAuth2RedirectUrl(Swashbuckle.AspNetCore.SwaggerUI.SwaggerUIOptions, string)`
  - OAuth redirect URL
  - `options`
  - `url`
- `OAuthAdditionalQueryStringParams(SwaggerUIOptions, Dictionary<string, string>)`
- `OAuthAdditionalQueryStringParams(Swashbuckle.AspNetCore.SwaggerUI.SwaggerUIOptions, Generic.Dictionary<string,string>)`
  - Additional query parameters added to authorizationUrl and tokenUrl
  - `options`
  - `value`
- `OAuthAppName(SwaggerUIOptions, string)`
- `OAuthAppName(Swashbuckle.AspNetCore.SwaggerUI.SwaggerUIOptions, string)`
  - Application name, displayed in authorization popup
  - `options`
  - `value`
- `OAuthClientId(SwaggerUIOptions, string)`
- `OAuthClientId(Swashbuckle.AspNetCore.SwaggerUI.SwaggerUIOptions, string)`
  - Default clientId
  - `options`
  - `value`
- `OAuthClientSecret(SwaggerUIOptions, string)`
- `OAuthClientSecret(Swashbuckle.AspNetCore.SwaggerUI.SwaggerUIOptions, string)`
  - Default clientSecret
  - `options`
  - `value`
  - remarks: Setting this exposes the client secrets in inline javascript in the swagger-ui generated html.
- `OAuthRealm(SwaggerUIOptions, string)`
- `OAuthRealm(Swashbuckle.AspNetCore.SwaggerUI.SwaggerUIOptions, string)`
  - realm query parameter (for oauth1) added to authorizationUrl and tokenUrl
  - `options`
  - `value`
- `OAuthScopeSeparator(SwaggerUIOptions, string)`
- `OAuthScopeSeparator(Swashbuckle.AspNetCore.SwaggerUI.SwaggerUIOptions, string)`
  - Scope separator for passing scopes, encoded before calling, default value is a space (encoded value %20)
  - `options`
  - `value`
- `OAuthScopes(SwaggerUIOptions, string[])`
- `OAuthScopes(Swashbuckle.AspNetCore.SwaggerUI.SwaggerUIOptions, string[])`
  - String array of initially selected oauth scopes, default is empty array
- `OAuthUseBasicAuthenticationWithAccessCodeGrant(SwaggerUIOptions)`
- `OAuthUseBasicAuthenticationWithAccessCodeGrant(Swashbuckle.AspNetCore.SwaggerUI.SwaggerUIOptions)`
  - Only activated for the accessCode flow. During the authorization_code request to the tokenUrl,
pass the Client Password using the HTTP Basic Authentication scheme (Authorization header with
Basic base64encoded[client_id:client_secret]). The default is false
  - `options`
- `OAuthUsePkce(SwaggerUIOptions)`
- `OAuthUsePkce(Swashbuckle.AspNetCore.SwaggerUI.SwaggerUIOptions)`
  - Only applies to authorizatonCode flows. Proof Key for Code Exchange brings enhanced security for OAuth public clients.
The default is false
  - `options`
- `OAuthUsername(SwaggerUIOptions, string)`
- `OAuthUsername(Swashbuckle.AspNetCore.SwaggerUI.SwaggerUIOptions, string)`
  - Default userName
  - `options`
  - `value`
- `ShowCommonExtensions(SwaggerUIOptions)`
- `ShowCommonExtensions(Swashbuckle.AspNetCore.SwaggerUI.SwaggerUIOptions)`
  - Controls the display of extensions (pattern, maxLength, minLength, maximum, minimum) fields and values for Parameters
  - `options`
- `ShowExtensions(SwaggerUIOptions)`
- `ShowExtensions(Swashbuckle.AspNetCore.SwaggerUI.SwaggerUIOptions)`
  - Controls the display of vendor extension (x-) fields and values for Operations, Parameters, and Schema
  - `options`
- `SupportedSubmitMethods(SwaggerUIOptions, SubmitMethod[])`
- `SupportedSubmitMethods(Swashbuckle.AspNetCore.SwaggerUI.SwaggerUIOptions, Swashbuckle.AspNetCore.SwaggerUI.SubmitMethod[])`
  - List of HTTP methods that have the Try it out feature enabled. An empty array disables Try it out for all operations.
This does not filter the operations from the display
  - `options`
  - `submitMethods`
- `SwaggerEndpoint(SwaggerUIOptions, string, string)`
- `SwaggerEndpoint(Swashbuckle.AspNetCore.SwaggerUI.SwaggerUIOptions, string, string)`
  - Adds Swagger JSON endpoints. Can be fully-qualified or relative to the UI page
  - `options`
  - `url`: Can be fully qualified or relative to the current host
  - `name`: The description that appears in the document selector drop-down
- `UseRequestInterceptor(SwaggerUIOptions, string)`
- `UseRequestInterceptor(Swashbuckle.AspNetCore.SwaggerUI.SwaggerUIOptions, string)`
  - Function to intercept remote definition, "Try it out", and OAuth 2.0 requests.
  - `options`
  - `value`: MUST be a valid Javascript function: (request: SwaggerRequest) => SwaggerRequest
- `UseResponseInterceptor(SwaggerUIOptions, string)`
- `UseResponseInterceptor(Swashbuckle.AspNetCore.SwaggerUI.SwaggerUIOptions, string)`
  - Function to intercept remote definition, "Try it out", and OAuth 2.0 responses.
  - `options`
  - `value`: MUST be a valid Javascript function: (response: SwaggerResponse ) => SwaggerResponse


### namespace `Swashbuckle.AspNetCore.SwaggerUI`

#### `ConfigObject`

**Properties:**

- `AdditionalItems`
- `DeepLinking`
  - If set to true, enables deep linking for tags and operations
- `DefaultModelExpandDepth`
  - The default expansion depth for the model on the model-example section
- `DefaultModelRendering`
  - Controls how the model is shown when the API is first rendered.
(The user can always switch the rendering for a given model by clicking the 'Model' and 'Example Value' links)
- `DefaultModelsExpandDepth`
  - The default expansion depth for models (set to -1 completely hide the models)
- `DisplayOperationId`
  - Controls the display of operationId in operations list
- `DisplayRequestDuration`
  - Controls the display of the request duration (in milliseconds) for Try-It-Out requests
- `DocExpansion`
  - Controls the default expansion setting for the operations and tags.
It can be 'list' (expands only the tags), 'full' (expands the tags and operations) or 'none' (expands nothing)
- `Filter`
  - If set, enables filtering. The top bar will show an edit box that you can use to filter the tagged operations
that are shown. Can be an empty string or specific value, in which case filtering will be enabled using that
value as the filter expression. Filtering is case sensitive matching the filter expression anywhere inside the tag
- `MaxDisplayedTags`
  - If set, limits the number of tagged operations displayed to at most this many. The default is to show all operations
- `OAuth2RedirectUrl`
  - OAuth redirect URL
- `PersistAuthorization`
  - If set to true, it persists authorization data and it would not be lost on browser close/refresh
- `Plugins`
  - Any custom plugins' function names.
- `ShowCommonExtensions`
  - Controls the display of extensions (pattern, maxLength, minLength, maximum, minimum) fields and values for Parameters
- `ShowExtensions`
  - Controls the display of vendor extension (x-) fields and values for Operations, Parameters, and Schema
- `SupportedSubmitMethods`
  - List of HTTP methods that have the Try it out feature enabled.
An empty array disables Try it out for all operations. This does not filter the operations from the display
- `TryItOutEnabled`
  - Controls whether the "Try it out" section should be enabled by default.
- `Urls`
  - One or more Swagger JSON endpoints (url and name) to power the UI
- `ValidatorUrl`
  - By default, Swagger-UI attempts to validate specs against swagger.io's online validator.
You can use this parameter to set a different validator URL, for example for locally deployed validators (Validator Badge).
Setting it to null will disable validation


#### `DocExpansion`

**Fields:**

- `Full`
- `List`
- `None`


#### `InterceptorFunctions`

**Properties:**

- `RequestInterceptorFunction`
  - MUST be a valid Javascript function.
Function to intercept remote definition, "Try it out", and OAuth 2.0 requests.
Accepts one argument requestInterceptor(request) and must return the modified request, or a Promise that resolves to the modified request.
Ex: "function (req) { req.headers['MyCustomHeader'] = 'CustomValue'; return req; }"
- `ResponseInterceptorFunction`
  - MUST be a valid Javascript function.
Function to intercept remote definition, "Try it out", and OAuth 2.0 responses.
Accepts one argument responseInterceptor(response) and must return the modified response, or a Promise that resolves to the modified response.
Ex: "function (res) { console.log(res); return res; }"


#### `ModelRendering`

**Fields:**

- `Example`
- `Model`


#### `OAuthConfigObject`

**Properties:**

- `AdditionalQueryStringParams`
  - Additional query parameters added to authorizationUrl and tokenUrl
- `AppName`
  - Application name, displayed in authorization popup
- `ClientId`
  - Default clientId
- `ClientSecret`
  - Default clientSecret
  - remarks: Setting this exposes the client secrets in inline javascript in the swagger-ui generated html.
- `Realm`
  - Realm query parameter (for oauth1) added to authorizationUrl and tokenUrl
- `ScopeSeparator`
  - Scope separator for passing scopes, encoded before calling, default value is a space (encoded value %20)
- `Scopes`
  - String array of initially selected oauth scopes, default is empty array
- `UseBasicAuthenticationWithAccessCodeGrant`
  - Only activated for the accessCode flow. During the authorization_code request to the tokenUrl,
pass the Client Password using the HTTP Basic Authentication scheme
(Authorization header with Basic base64encode(client_id + client_secret))
- `UsePkceWithAuthorizationCodeGrant`
  - Only applies to authorizatonCode flows. Proof Key for Code Exchange brings enhanced security for OAuth public clients.
The default is false
- `Username`
  - Default username for OAuth2 password flow.


#### `SubmitMethod`

**Fields:**

- `Delete`
- `Get`
- `Head`
- `Options`
- `Patch`
- `Post`
- `Put`
- `Trace`


#### `SwaggerUIOptions`

**Properties:**

- `CacheLifetime`
  - Gets or sets the cache lifetime to use for the SwaggerUI files, if any.
  - remarks: The default value is 0 days (ETags are used to check if resources have been updated).
- `ConfigObject`
  - Gets the JavaScript config object, represented as JSON, that will be passed to the SwaggerUI
- `DocumentTitle`
  - Gets or sets a title for the swagger-ui page
- `ExposeSwaggerDocumentUrlsRoute`
  - Gets or sets whether to expose the ``ConfigObject`.Urls` object via an
HTTP endpoint with the URL specified by `SwaggerDocumentUrlsPath`
so that external code can auto-discover all Swagger documents.
- `HeadContent`
  - Gets or sets additional content to place in the head of the swagger-ui page
- `IndexStream`
  - Gets or sets a Stream function for retrieving the swagger-ui page
- `Interceptors`
  - Gets the interceptor functions that define client-side request/response interceptors
- `JsonSerializerOptions`
  - Gets or sets the optional JSON serialization options to use to serialize options to the HTML document.
- `OAuthConfigObject`
  - Gets the JavaScript config object, represented as JSON, that will be passed to the initOAuth method
- `RoutePrefix`
  - Gets or sets a route prefix for accessing the swagger-ui
- `ScriptBundlePath`
  - Gets or sets the path or URL to the Swagger UI JavaScript bundle file.
- `ScriptPresetsPath`
  - Gets or sets the path or URL to the Swagger UI JavaScript standalone presets file.
- `StylesPath`
  - Gets or sets the path or URL to the Swagger UI CSS file.
- `SwaggerDocumentUrlsPath`
  - Gets or sets the relative URL path to the route that exposes the values of the configured `Urls` values.


#### `SwaggerUIOptionsJsonContext`

**Methods:**

- `#ctor`
- `#ctor(Json.JsonSerializerOptions)`
- `GetTypeInfo(Type)`

**Properties:**

- `Boolean`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `Byte`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `Char`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `ConfigObject`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `DateOnly`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `DateTime`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `DateTimeOffset`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `Decimal`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `Default`
  - The default `JsonSerializerContext` associated with a default `JsonSerializerOptions` instance.
- `DictionaryStringObject`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `DictionaryStringString`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `DocExpansion`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `Double`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `GeneratedSerializerOptions`
  - The source-generated options associated with this context.
- `Half`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `IEnumerableString`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `IEnumerableSubmitMethod`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `IEnumerableUrlDescriptor`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `IListString`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `Int128`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `Int16`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `Int32`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `Int64`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `InterceptorFunctions`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `JsonArray`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `JsonDocument`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `JsonObject`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `ListUrlDescriptor`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `ModelRendering`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `NullableInt32`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `OAuthConfigObject`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `Object`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `SByte`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `Single`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `String`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `SubmitMethod`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `TimeOnly`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `TimeSpan`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `UInt128`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `UInt16`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `UInt32`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `UInt64`
  - Defines the source generated JSON serialization contract metadata for a given type.
- `UrlDescriptor`
  - Defines the source generated JSON serialization contract metadata for a given type.


#### `UrlDescriptor`

**Properties:**

- `Name`
- `Url`



## package `Swashbuckle.AspNetCore.Annotations` v10.2.1

### namespace `Microsoft.Extensions.DependencyInjection`

#### `AnnotationsSwaggerGenOptionsExtensions`

**Methods:**

- `EnableAnnotations(SwaggerGenOptions)`
  - Enables Swagger annotations (SwaggerOperationAttribute, SwaggerParameterAttribute etc.)
  - `options`
- `EnableAnnotations(SwaggerGenOptions, bool, bool)`
  - Enables Swagger annotations (SwaggerOperationAttribute, SwaggerParameterAttribute etc.)
  - `options`
  - `enableAnnotationsForInheritance`: Enables SwaggerSubType attribute for inheritance
  - `enableAnnotationsForPolymorphism`: Enables SwaggerSubType and SwaggerDiscriminator attributes for polymorphism


### namespace `Microsoft.OpenApi`

#### `OpenApiTagComparer`

This comparer is used to maintain a globally unique list of tags encountered
in a particular OpenAPI document.

**Methods:**

- `Equals(Microsoft.OpenApi.IOpenApiTag, Microsoft.OpenApi.IOpenApiTag)`
- `Equals(Microsoft.OpenApi.OpenApiTagReference, Microsoft.OpenApi.OpenApiTagReference)`
- `GetHashCode(Microsoft.OpenApi.IOpenApiTag)`
- `GetHashCode(Microsoft.OpenApi.OpenApiTagReference)`

**Properties:**

- `Instance`
  - Default instance for the comparer.


### namespace `Swashbuckle.AspNetCore.Annotations`

#### `AnnotationsDocumentFilter`

**Methods:**

- `Apply(OpenApiDocument, DocumentFilterContext)`


#### `AnnotationsOperationFilter`

**Methods:**

- `Apply(OpenApiOperation, OperationFilterContext)`
- `ApplySwaggerOperationFilterAttributes(OpenApiOperation, OperationFilterContext, IEnumerable<object>)`


#### `AnnotationsParameterFilter`

**Methods:**

- `Apply(IOpenApiParameter, ParameterFilterContext)`


#### `AnnotationsRequestBodyFilter`

**Methods:**

- `Apply(IOpenApiRequestBody, RequestBodyFilterContext)`


#### `AnnotationsSchemaFilter`

**Methods:**

- `Apply(IOpenApiSchema, SchemaFilterContext)`


#### `SwaggerDiscriminatorAttribute`

**Properties:**

- `PropertyName`


#### `SwaggerOperationAttribute`

Enriches Operation metadata for a given action method

**Methods:**

- `#ctor(string, string)`
  - Enriches Operation metadata for a given action method

**Properties:**

- `Description`
  - A verbose explanation of the operation behavior. GFM syntax can be used for rich text representation.
- `OperationId`
  - Unique string used to identify the operation. The id MUST be unique among all operations described
in the API. Tools and libraries MAY use the operationId to uniquely identify an operation, therefore,
it is recommended to follow common programming naming conventions.
- `Summary`
  - A short summary of what the operation does. For maximum readability in the swagger-ui,
this field SHOULD be less than 120 characters.
- `Tags`
  - A list of tags for API documentation control. Tags can be used for logical grouping of operations
by resources or any other qualifier.


#### `SwaggerOperationFilterAttribute`

**Properties:**

- `FilterType`


#### `SwaggerParameterAttribute`

Enriches Parameter metadata for "path", "query" or "header" bound parameters or properties

**Methods:**

- `#ctor(string)`
  - Enriches Parameter metadata for "path", "query" or "header" bound parameters or properties

**Properties:**

- `Description`
  - A brief description of the parameter. This could contain examples of use.
GFM syntax can be used for rich text representation
- `Required`
  - Determines whether the parameter is mandatory. If the parameter is in "path",
it will be required by default as Swagger does not allow optional path parameters


#### `SwaggerRequestBodyAttribute`

Enriches RequestBody metadata for "body" bound parameters or properties

**Methods:**

- `#ctor(string)`
  - Enriches RequestBody metadata for "body" bound parameters or properties

**Properties:**

- `Description`
  - A brief description of the requestBody. This could contain examples of use.
GFM syntax can be used for rich text representation
- `Required`
  - Determines whether the requestBody is mandatory. If the parameter is in "path",
it will be required by default as Swagger does not allow optional path parameters


#### `SwaggerResponseAttribute`

Adds or enriches Response metadata for a given action method

**Methods:**

- `#ctor(int, string, Type)`
- `#ctor(int, string, Type, string[])`

**Properties:**

- `ContentTypes`
  - A collection of MIME types that the response can be produced with.
- `Description`
  - A short description of the response. GFM syntax can be used for rich text representation.


#### `SwaggerSchemaAttribute`

**Properties:**

- `Description`
- `Format`
- `Nullable`
- `ReadOnly`
- `Required`
- `Title`
- `WriteOnly`


#### `SwaggerSchemaFilterAttribute`

**Properties:**

- `Arguments`
- `Type`


#### `SwaggerSubTypeAttribute`

**Properties:**

- `DiscriminatorValue`
- `SubType`


#### `SwaggerTagAttribute`

Adds Tag metadata for a given controller (i.e. the controller name tag)

**Methods:**

- `#ctor(string, string)`
  - Adds Tag metadata for a given controller (i.e. the controller name tag)
  - remarks: Don't use this attribute if you're tagging Operations with something other than controller name
e.g. if you're customizing the tagging behavior with TagActionsBy.

**Properties:**

- `Description`
  - A short description for the tag. GFM syntax can be used for rich text representation.
- `ExternalDocsUrl`
  - A URL for additional external documentation. Value MUST be in the format of a URL.
