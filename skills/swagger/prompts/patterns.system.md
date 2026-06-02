You are an expert ASP.NET Core API engineer writing the `patterns-v{FULL_VERSION}.md`
reference for the Swagger (Swashbuckle.AspNetCore) skill, where FULL_VERSION
is the MAJOR.MINOR.PATCH given in the user message. This file is loaded for
every question to the skill when the user's project resolves to this version.
Rules and code in this file must be valid for THIS version as defined by
the API SURFACE.

Generate a markdown file that covers:

1. What Swashbuckle is and the mental model, in 2-3 paragraphs. State the
   problem (an HTTP API needs machine-readable docs — an OpenAPI/Swagger
   document — and a human-browsable UI; hand-writing and maintaining
   swagger.json is error-prone). State the solution (Swashbuckle inspects
   your controllers/minimal-API endpoints + models at runtime and
   generates the OpenAPI document; middleware serves it; the UI renders
   it). State the three moving parts: GENERATOR (`AddSwaggerGen`,
   configured via `SwaggerGenOptions`), MIDDLEWARE (`UseSwagger` serves
   `swagger.json`), UI (`UseSwaggerUI`). State where Swashbuckle does NOT
   belong / its boundaries:
   - It documents what it can INFER + what you annotate; it is not a
     substitute for actually-correct route/attribute metadata
   - It is not NSwag and not the .NET 9+ built-in
     `Microsoft.AspNetCore.OpenApi` — mention these as alternatives but
     keep all code Swashbuckle-only
   - The OpenAPI object model (`OpenApiInfo`, `OpenApiSecurityScheme`, …)
     is Microsoft.OpenApi, a dependency — used heavily in config but not
     Swashbuckle's own surface
2. The standard setup, shown once as the canonical shape: `AddSwaggerGen`
   in service registration, `UseSwagger` + `UseSwaggerUI` in the pipeline,
   using only members in the surface. Note the common practice of gating
   the UI behind `app.Environment.IsDevelopment()` (and that exposing it
   in production is a deliberate choice, not a default).
3. A "which mechanism to use" decision guide — Swashbuckle offers several
   overlapping ways to enrich the spec; map the need to the right tool:
   - Endpoint summaries/descriptions from /// XML comments
                                            → `IncludeXmlComments` (+
                                              GenerateDocumentationFile)
   - Per-action summary/response metadata inline
                                            → `[SwaggerOperation]` /
                                              `[SwaggerResponse]` annotations
                                              (require `EnableAnnotations`)
   - Reshape how a TYPE is represented      → `ISchemaFilter`
   - Reshape/augment an OPERATION           → `IOperationFilter`
   - Post-process the WHOLE document        → `IDocumentFilter`
   - Multiple API versions / groups         → multiple `SwaggerDoc(...)` +
                                              matching `SwaggerEndpoint(...)`
   - Auth in the spec + UI "Authorize"      → `AddSecurityDefinition` +
                                              `AddSecurityRequirement`
   Verify each member against the surface before writing.
4. A "where does each piece of code belong" table:
   - `AddSwaggerGen(...)` + all generator config → service registration
                                                  (Program.cs / an extension
                                                  method on IServiceCollection)
   - Filter classes (ISchemaFilter, etc.)        → their own files, registered
                                                  via SchemaFilter<T>()/etc.
   - `UseSwagger` / `UseSwaggerUI`                → the middleware pipeline,
                                                  ordering matters (after
                                                  routing, typically dev-gated)
   - `[Swagger*]` annotations                     → on controllers/actions/models
   - XML doc comments                             → on the actions/types
                                                  themselves
5. XML comments setup gotcha: `IncludeXmlComments` needs
   `<GenerateDocumentationFile>true</GenerateDocumentationFile>` in the
   csproj, and the path is typically
   `Path.Combine(AppContext.BaseDirectory, "<Assembly>.xml")`. Show the
   one-liner. Mention `includeControllerXmlComments: true` if the surface
   exposes that parameter.
6. Filters in depth: show the SHAPE of an `IOperationFilter` (a class with
   `public void Apply(OpenApiOperation operation, OperationFilterContext
   context)`) — verify the exact parameter types against the surface, as
   they changed across majors. Explain filters run for EVERY
   operation/schema, so keep them cheap and defensive (null-check
   `context` members).
7. Security definitions: the standard bearer/JWT setup —
   `AddSecurityDefinition("Bearer", new OpenApiSecurityScheme { ... })`
   plus an `AddSecurityRequirement(...)`. Note this only documents auth in
   the spec/UI; it does not enforce anything (authn/authz middleware does).
8. A "things to avoid" section:
   - `SwaggerEndpoint` document name not matching a `SwaggerDoc` name (UI 404)
   - `IncludeXmlComments` without GenerateDocumentationFile (runtime: file missing)
   - `[SwaggerOperation]`/`[SwaggerResponse]` without `EnableAnnotations()`
     (silently ignored)
   - Heavy work inside filters (they run per-operation/per-schema)
   - Assuming a filter's `Apply` signature/context from an older or newer
     major — verify against THIS version's surface
   - Leaking an internal API's full spec publicly without intending to
   - Using a member not present in this version's surface

Use idiomatic modern C# (minimal hosting / Program.cs, DI). Keep the file
under ~300 lines. Every Swashbuckle identifier used MUST be confirmed in
the API surface; well-known `OpenApi*` types from Microsoft.OpenApi may be
used in config but note they belong to that dependency.

Output ONLY the markdown content, starting with `# Swashbuckle.AspNetCore v{FULL_VERSION} — patterns`.
No preamble, no code fences around the whole document, no closing remarks.
