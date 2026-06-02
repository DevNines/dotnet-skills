<!-- ============================================================
     examples-v10.2.1.md
     Generated against Swashbuckle.AspNetCore v10.2.1
     (SwaggerGen / Swagger / SwaggerUI / Annotations).
     DO NOT EDIT BY HAND — rerun scripts/update_skill.py.
     ============================================================ -->

# Swashbuckle.AspNetCore v10.2.1 — Examples

Canonical, copy-paste examples for the generator (`AddSwaggerGen`), the
middleware (`UseSwagger`), and the UI (`UseSwaggerUI`). Every snippet uses only
members present in the v10.2.1 public surface.

> `OpenApi*` types (`OpenApiInfo`, `OpenApiSecurityScheme`, `OpenApiContact`,
> etc.) come from the Microsoft.OpenApi dependency, not from Swashbuckle itself.

## 1. Minimal setup

The smallest working wiring: register the generator, then serve the JSON and
the UI (dev-gated).

```csharp
var builder = WebApplication.CreateBuilder(args);

builder.Services.AddControllers();
builder.Services.AddSwaggerGen();

var app = builder.Build();

if (app.Environment.IsDevelopment())
{
    app.UseSwagger();
    app.UseSwaggerUI();
}

app.MapControllers();
app.Run();
```

Notes:
- With no `SwaggerDoc` call, a default `v1` document is generated and the UI
  defaults its endpoint to `v1/swagger.json`.
- `UseSwagger`/`UseSwaggerUI` are the middleware/UI entry points from the
  `Swagger` and `SwaggerUI` packages.

## 2. Document metadata

Describe the document via `SwaggerDoc` and an `OpenApiInfo`.

```csharp
builder.Services.AddSwaggerGen(c =>
{
    c.SwaggerDoc("v1", new OpenApiInfo
    {
        Title = "My API",
        Version = "v1",
        Description = "Sample service",
        Contact = new OpenApiContact { Name = "API Team", Email = "api@example.com" },
        License = new OpenApiLicense { Name = "MIT" },
    });
});
```

Notes:
- `OpenApiInfo`, `OpenApiContact`, and `OpenApiLicense` are Microsoft.OpenApi types.
- The first `SwaggerDoc` argument (`"v1"`) is the document name used in routes.

## 3. XML comments

Feed XML doc comments into operations, parameters, and schemas.

```csharp
builder.Services.AddSwaggerGen(c =>
{
    var xmlPath = Path.Combine(AppContext.BaseDirectory, "MyApi.xml");
    c.IncludeXmlComments(xmlPath, includeControllerXmlComments: true);
});
```

Notes:
- Requires `<GenerateDocumentationFile>true</GenerateDocumentationFile>` in the csproj.
- `includeControllerXmlComments: true` promotes controller `<summary>` text to
  tag descriptions; omit it if you customize tags via `TagActionsBy`.
- Overloads also accept an `Assembly` or a `Func<XPathDocument>`.

## 4. Multiple documents / API versions

Two `SwaggerDoc` calls, two matching `SwaggerEndpoint` entries.

```csharp
builder.Services.AddSwaggerGen(c =>
{
    c.SwaggerDoc("v1", new OpenApiInfo { Title = "My API", Version = "v1" });
    c.SwaggerDoc("v2", new OpenApiInfo { Title = "My API", Version = "v2" });
});

// ...
app.UseSwagger();
app.UseSwaggerUI(c =>
{
    c.SwaggerEndpoint("/swagger/v1/swagger.json", "My API v1");
    c.SwaggerEndpoint("/swagger/v2/swagger.json", "My API v2");
});
```

Notes:
- The `{documentName}` in each endpoint URL must match a `SwaggerDoc` name.
- Use `DocInclusionPredicate` if you need explicit control over which actions
  land in which document.

## 5. JWT / bearer security

Define a bearer scheme and require it globally.

```csharp
builder.Services.AddSwaggerGen(c =>
{
    c.AddSecurityDefinition("Bearer", new OpenApiSecurityScheme
    {
        Name = "Authorization",
        Type = SecuritySchemeType.Http,
        Scheme = "bearer",
        BearerFormat = "JWT",
        In = ParameterLocation.Header,
        Description = "Enter the JWT bearer token",
    });

    c.AddSecurityRequirement(document => new OpenApiSecurityRequirement
    {
        [new OpenApiSecuritySchemeReference("Bearer", document)] = []
    });
});
```

Notes:
- In v10, `AddSecurityRequirement` takes a `Func<OpenApiDocument, OpenApiSecurityRequirement>`
  — the document is passed in so references can be resolved against it.
- The scheme name in the requirement (`"Bearer"`) must match the
  `AddSecurityDefinition` name.
- `OpenApiSecurityScheme` / `OpenApiSecurityRequirement` are Microsoft.OpenApi types.

## 6. A schema filter

Implement `ISchemaFilter` with the v10 `Apply(IOpenApiSchema, SchemaFilterContext)`
signature and register it.

```csharp
using Microsoft.OpenApi;
using Swashbuckle.AspNetCore.SwaggerGen;

public sealed class DescriptionSchemaFilter : ISchemaFilter
{
    public void Apply(IOpenApiSchema schema, SchemaFilterContext context)
    {
        if (context.Type == typeof(DateTime))
        {
            schema.Description = "ISO-8601 date/time value.";
        }
    }
}

// Registration:
builder.Services.AddSwaggerGen(c => c.SchemaFilter<DescriptionSchemaFilter>());
```

Notes:
- The first parameter is `IOpenApiSchema` (not `OpenApiSchema`) in v10 — this
  signature is version-specific.
- `context.Type`, `context.MemberInfo`, and `context.SchemaRepository` are
  available on `SchemaFilterContext`.

## 7. An operation filter

Implement `IOperationFilter` with the v10 `Apply(OpenApiOperation, OperationFilterContext)`
signature.

```csharp
using Microsoft.OpenApi;
using Swashbuckle.AspNetCore.SwaggerGen;

public sealed class AddCorrelationHeaderFilter : IOperationFilter
{
    public void Apply(OpenApiOperation operation, OperationFilterContext context)
    {
        operation.Parameters ??= [];
        operation.Parameters.Add(new OpenApiParameter
        {
            Name = "X-Correlation-Id",
            In = ParameterLocation.Header,
            Required = false,
            Schema = new OpenApiSchema { Type = JsonSchemaType.String },
        });
    }
}

// Registration:
builder.Services.AddSwaggerGen(c => c.OperationFilter<AddCorrelationHeaderFilter>());
```

Notes:
- `OperationFilterContext` exposes `ApiDescription`, `MethodInfo`, `Document`,
  `SchemaGenerator`, and `SchemaRepository`.
- `OpenApiOperation` / `OpenApiParameter` / `OpenApiSchema` are Microsoft.OpenApi types.

## 8. Annotations

Enable annotations, then decorate actions with the `Swashbuckle.AspNetCore.Annotations`
attributes.

```csharp
builder.Services.AddSwaggerGen(c => c.EnableAnnotations());
```

```csharp
using Microsoft.AspNetCore.Mvc;
using Swashbuckle.AspNetCore.Annotations;

[ApiController]
[Route("products")]
public sealed class ProductsController : ControllerBase
{
    [HttpGet("{id}")]
    [SwaggerOperation(
        Summary = "Get a product",
        Description = "Returns a single product by id.",
        OperationId = "GetProduct")]
    [SwaggerResponse(200, "The product was found", typeof(Product))]
    [SwaggerResponse(404, "No product with that id exists")]
    public IActionResult Get(int id) => Ok();
}
```

Notes:
- `EnableAnnotations()` must be called or the attributes are ignored.
- `SwaggerOperation` exposes `Summary`, `Description`, `OperationId`, and `Tags`.
- `SwaggerResponse(int, string, Type)` describes a status code, message, and body type.

## 9. UI tuning

Configure UI presentation with options present in the surface.

```csharp
app.UseSwagger();
app.UseSwaggerUI(c =>
{
    c.RoutePrefix = "docs";            // UI served at /docs
    c.DocumentTitle = "My API Docs";
    c.DefaultModelsExpandDepth(-1);    // hide the models section
    c.DocExpansion(DocExpansion.List);
    c.DisplayRequestDuration();
    c.EnablePersistAuthorization();
    c.SwaggerEndpoint("/swagger/v1/swagger.json", "My API v1");
});
```

Notes:
- `RoutePrefix` and `DocumentTitle` are properties on `SwaggerUIOptions`; the
  rest are extension methods in `SwaggerUIOptionsExtensions`.
- `DocExpansion` and `ModelRendering` are enums in the `SwaggerUI` namespace.

## 10. New in v10.2: endpoint-routed UI with `MapSwaggerUI`

v10.2 added `MapSwaggerUI`, letting you register the UI through endpoint routing
(so it participates in the endpoint pipeline) instead of as raw middleware.

```csharp
var app = builder.Build();

app.UseSwagger();

if (app.Environment.IsDevelopment())
{
    app.MapSwaggerUI("docs", c =>
    {
        c.DocumentTitle = "My API Docs";
        c.SwaggerEndpoint("/swagger/v1/swagger.json", "My API v1");
    });
}

app.MapControllers();
app.Run();
```

Notes:
- `MapSwaggerUI(IEndpointRouteBuilder, string routePrefix, Action<SwaggerUIOptions>)`
  is new in v10.2; the `routePrefix` argument overrides `SwaggerUIOptions.RoutePrefix`.
- It returns an `IEndpointConventionBuilder`, so you can chain endpoint
  conventions (auth, metadata) onto the UI route.
- Also new in this minor: the Swagger JSON, UI, and document endpoints now
  answer `HEAD` requests (returning the correct `Content-Length` with an empty
  body) in addition to `GET`.
