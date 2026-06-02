# Swashbuckle.AspNetCore v10.2.1 — patterns

## What Swashbuckle is and the mental model

An HTTP API needs machine-readable documentation — an OpenAPI (Swagger) document — and a human-browsable UI for exploring it. Hand-writing and maintaining a `swagger.json` by hand is tedious and error-prone: it drifts from the real routes, models, and status codes the moment the code changes. Swashbuckle solves this by inspecting your controllers / minimal-API endpoints and their models at runtime and generating the OpenAPI document for you, then serving both the document and a UI to render it.

There are three moving parts. The **GENERATOR** (`AddSwaggerGen`, configured via `SwaggerGenOptions`) walks ASP.NET Core's `ApiExplorer` metadata and builds the OpenAPI document in memory. The **MIDDLEWARE** (`UseSwagger`) serves that document as `swagger.json` (or YAML). The **UI** (`UseSwaggerUI`) serves the swagger-ui static assets that fetch and render the document in a browser.

Swashbuckle documents what it can **infer** from routing/attribute metadata plus what you explicitly **annotate** — it is not a substitute for correct `[HttpGet]`, `[Route]`, `[ProducesResponseType]`, etc. on your actions. It is also **not** NSwag and **not** the .NET 9+ built-in `Microsoft.AspNetCore.OpenApi` package; those are alternative OpenAPI stacks, and everything below is Swashbuckle-only. Finally, the OpenAPI object model (`OpenApiInfo`, `OpenApiSecurityScheme`, `OpenApiDocument`, `OpenApiOperation`, …) lives in the **Microsoft.OpenApi** dependency. You use those types heavily when configuring Swashbuckle, but they are not part of Swashbuckle's own surface.

## Canonical setup

```csharp
using Microsoft.OpenApi;

var builder = WebApplication.CreateBuilder(args);

builder.Services.AddControllers();
builder.Services.AddSwaggerGen(options =>
{
    options.SwaggerDoc("v1", new OpenApiInfo
    {
        Title = "My API",
        Version = "v1",
        Description = "Sample API documented with Swashbuckle."
    });
});

var app = builder.Build();

// Serve the generated swagger.json
app.UseSwagger();

// Serve the swagger-ui — commonly dev-gated.
// Exposing it in production is a DELIBERATE choice, not a default.
if (app.Environment.IsDevelopment())
{
    app.UseSwaggerUI(options =>
    {
        options.SwaggerEndpoint("/swagger/v1/swagger.json", "My API v1");
    });
}

app.MapControllers();
app.Run();
```

`UseSwagger` / `UseSwaggerUI` go in the middleware pipeline after routing has been established. The `name` you pass to `SwaggerDoc` ("v1") must match the document name segment in the `SwaggerEndpoint` URL.

## Which mechanism to use

| Need | Mechanism (verified in surface) |
|------|---------------------------------|
| Endpoint summaries/descriptions from `///` XML comments | `IncludeXmlComments(...)` (+ `GenerateDocumentationFile`) |
| Per-action summary/response metadata inline | `[SwaggerOperation]` / `[SwaggerResponse]` — require `EnableAnnotations()` |
| Reshape how a TYPE is represented | `ISchemaFilter` via `SchemaFilter<T>(...)` |
| Reshape/augment an OPERATION | `IOperationFilter` via `OperationFilter<T>(...)` |
| Post-process the WHOLE document | `IDocumentFilter` via `DocumentFilter<T>(...)` |
| Multiple API versions / groups | multiple `SwaggerDoc(...)` + matching `SwaggerEndpoint(...)` |
| Auth in the spec + UI "Authorize" button | `AddSecurityDefinition(...)` + `AddSecurityRequirement(...)` |

## Where each piece of code belongs

| Code | Location |
|------|----------|
| `AddSwaggerGen(...)` + all generator config | Service registration (`Program.cs` or an `IServiceCollection` extension method) |
| Filter classes (`ISchemaFilter`, `IOperationFilter`, `IDocumentFilter`) | Their own files, registered via `SchemaFilter<T>()` / `OperationFilter<T>()` / `DocumentFilter<T>()` |
| `UseSwagger` / `UseSwaggerUI` | The middleware pipeline; ordering matters (after routing, typically dev-gated) |
| `[SwaggerOperation]`, `[SwaggerResponse]`, `[SwaggerSchema]`, etc. | On controllers / actions / models |
| XML doc comments (`///`) | On the actions and types themselves |

## XML comments setup gotcha

`IncludeXmlComments` reads a compiler-generated XML file. That file only exists if you enable it in the csproj:

```xml
<PropertyGroup>
  <GenerateDocumentationFile>true</GenerateDocumentationFile>
</PropertyGroup>
```

Then point Swashbuckle at it. The path is typically built from `AppContext.BaseDirectory`:

```csharp
builder.Services.AddSwaggerGen(options =>
{
    var xmlFile = $"{Assembly.GetExecutingAssembly().GetName().Name}.xml";
    var xmlPath = Path.Combine(AppContext.BaseDirectory, xmlFile);

    // includeControllerXmlComments: true uses controller-level /// summaries
    // as Tag descriptions. Omit it if you customize tags via TagActionsBy.
    options.IncludeXmlComments(xmlPath, includeControllerXmlComments: true);
});
```

The `IncludeXmlComments(SwaggerGenOptions, string, bool)` overload and its `includeControllerXmlComments` parameter are both in the surface.

## Filters in depth

Filters are the extension point for shaping the generated document. An `IOperationFilter` runs for **every** operation; an `ISchemaFilter` runs for **every** schema. Keep them cheap and defensive — null-check `context` members before touching them.

In v10.2.1 the `Apply` signatures use the Microsoft.OpenApi v2 interface types. Verify against the surface:

- `IOperationFilter.Apply(OpenApiOperation operation, OperationFilterContext context)`
- `ISchemaFilter.Apply(IOpenApiSchema schema, SchemaFilterContext context)` (see `XmlCommentsSchemaFilter.Apply`)
- `IDocumentFilter.Apply(OpenApiDocument document, DocumentFilterContext context)` (see `XmlCommentsDocumentFilter.Apply`)

`OperationFilterContext` exposes `ApiDescription`, `MethodInfo`, `SchemaGenerator`, `SchemaRepository`, `Document`, and the `DocumentName` field — all in the surface.

```csharp
using Microsoft.OpenApi;
using Swashbuckle.AspNetCore.SwaggerGen;

public sealed class AddCorrelationIdHeaderOperationFilter : IOperationFilter
{
    public void Apply(OpenApiOperation operation, OperationFilterContext context)
    {
        // Defensive: filters run for every operation.
        if (context.ApiDescription is null)
        {
            return;
        }

        operation.Description ??= context.ApiDescription.RelativePath;
    }
}
```

Register it in service registration:

```csharp
builder.Services.AddSwaggerGen(options =>
{
    options.OperationFilter<AddCorrelationIdHeaderOperationFilter>();
});
```

## Security definitions

`AddSecurityDefinition` describes a scheme; `AddSecurityRequirement` declares it as globally required so the UI shows an **Authorize** button and sends the header on "Try it out". This only **documents** auth in the spec/UI — it enforces nothing. Real protection comes from your authentication/authorization middleware.

```csharp
using Microsoft.OpenApi;

builder.Services.AddSwaggerGen(options =>
{
    options.AddSecurityDefinition("Bearer", new OpenApiSecurityScheme
    {
        Name = "Authorization",
        Type = SecuritySchemeType.Http,
        Scheme = "bearer",
        BearerFormat = "JWT",
        In = ParameterLocation.Header,
        Description = "Enter the JWT bearer token."
    });

    options.AddSecurityRequirement(document => new OpenApiSecurityRequirement
    {
        [new OpenApiSecuritySchemeReference("Bearer", document)] = []
    });
});
```

The `AddSecurityRequirement(SwaggerGenOptions, Func<OpenApiDocument, OpenApiSecurityRequirement>)` overload — taking a factory that receives the `OpenApiDocument` — is the one present in this version's surface; use it rather than passing a bare requirement object. (`OpenApiSecurityScheme`, `OpenApiSecurityRequirement`, and reference types belong to Microsoft.OpenApi.)

## Multiple documents

```csharp
builder.Services.AddSwaggerGen(options =>
{
    options.SwaggerDoc("v1", new OpenApiInfo { Title = "API", Version = "v1" });
    options.SwaggerDoc("v2", new OpenApiInfo { Title = "API", Version = "v2" });
});

app.UseSwaggerUI(options =>
{
    options.SwaggerEndpoint("/swagger/v1/swagger.json", "API v1");
    options.SwaggerEndpoint("/swagger/v2/swagger.json", "API v2");
});
```

Each `SwaggerEndpoint` URL's document-name segment must match a `SwaggerDoc` name.

## Annotations (require `EnableAnnotations`)

```csharp
builder.Services.AddSwaggerGen(options =>
{
    options.EnableAnnotations();
});
```

```csharp
using Swashbuckle.AspNetCore.Annotations;

[HttpGet("{id:int}")]
[SwaggerOperation(Summary = "Get a widget", Description = "Returns a single widget by id.")]
[SwaggerResponse(200, "The widget was found", typeof(Widget))]
[SwaggerResponse(404, "No widget with that id exists")]
public IActionResult GetById(int id) => Ok();
```

`SwaggerOperationAttribute` (with `Summary`, `Description`, `OperationId`, `Tags`) and `SwaggerResponseAttribute` (ctors `(int, string, Type)` and `(int, string, Type, string[])`) are confirmed in the Annotations surface. Without `EnableAnnotations()` these attributes are silently ignored.

## Things to avoid

- **`SwaggerEndpoint` name not matching a `SwaggerDoc` name** — the UI requests a document that the middleware never produced, yielding a 404 in the UI's network calls.
- **`IncludeXmlComments` without `<GenerateDocumentationFile>true</GenerateDocumentationFile>`** — at runtime the `.xml` file is missing and the comment injection fails.
- **`[SwaggerOperation]` / `[SwaggerResponse]` without `EnableAnnotations()`** — the attributes are silently ignored.
- **Heavy work inside filters** — `Apply` runs per-operation and per-schema; expensive reflection or I/O there multiplies across the whole document.
- **Assuming a filter's `Apply` signature from another major** — in v10.2.1, schema/parameter/request-body filters take the `IOpenApi*` interface types (e.g. `ISchemaFilter.Apply(IOpenApiSchema, SchemaFilterContext)`). Always verify against this surface.
- **Leaking an internal API's full spec publicly** — the UI is dev-gated above for a reason; exposing `UseSwaggerUI` in production is a deliberate decision, not a default.
- **Using a member not present in this version's surface** — if an identifier isn't listed in the API surface, it does not exist in v10.2.1; pick another approach.
