---
name: swagger
description: Write, review, or migrate C# code that uses Swashbuckle.AspNetCore — the standard Swagger / OpenAPI tooling for ASP.NET Core (the "Swagger" most .NET projects mean). Covers the SwaggerGen generator (services.AddSwaggerGen, SwaggerGenOptions, SwaggerDoc, IncludeXmlComments, ISchemaFilter / IOperationFilter / IDocumentFilter), the Swagger middleware (app.UseSwagger), the Swagger UI (app.UseSwaggerUI, SwaggerUIOptions, SwaggerEndpoint), and the [SwaggerOperation] / [SwaggerResponse] annotations. Use whenever a project imports any Swashbuckle.AspNetCore package, when the user asks about "Swagger", "OpenAPI docs", "AddSwaggerGen", "UseSwaggerUI", "swagger.json", "API documentation", a "schema/operation filter", or when migrating between versions. This skill is version-aware: it detects which exact version the project pins (e.g. 10.2.1) and loads the reference files generated against that specific version, never recommending a member that doesn't exist in the project's version.
---

# Swagger (Swashbuckle.AspNetCore) — version-aware skill

You are helping the user write or review C# code that uses **Swashbuckle.AspNetCore**, the de-facto Swagger/OpenAPI implementation for ASP.NET Core. When a .NET developer says "Swagger," they almost always mean Swashbuckle (the alternative is NSwag — a different package this skill does not cover). The standard three-line setup is: register the generator (`services.AddSwaggerGen(...)`), serve the generated `swagger.json` (`app.UseSwagger()`), and serve the interactive UI (`app.UseSwaggerUI(...)`). Beyond that, customization happens through `SwaggerGenOptions` (multiple documents via `SwaggerDoc`, XML comments via `IncludeXmlComments`, security definitions) and pluggable filters (`ISchemaFilter`, `IOperationFilter`, `IDocumentFilter`). **Detect the version before writing code, and load the closest-matching reference files.**

The skill's surface spans the Swashbuckle sub-packages:
- **Swashbuckle.AspNetCore.SwaggerGen** — the generator: `AddSwaggerGen`, `SwaggerGenOptions`, `SwaggerDoc`, `IncludeXmlComments`, `ISchemaFilter` / `IOperationFilter` / `IDocumentFilter`, `SchemaFilterContext` / `OperationFilterContext`.
- **Swashbuckle.AspNetCore.Swagger** — the middleware: `UseSwagger`, `SwaggerOptions`, `ISwaggerProvider`.
- **Swashbuckle.AspNetCore.SwaggerUI** — the UI: `UseSwaggerUI`, `SwaggerUIOptions`, `SwaggerEndpoint`.
- **Swashbuckle.AspNetCore.Annotations** — attributes: `[SwaggerOperation]`, `[SwaggerResponse]`, `[SwaggerSchema]`, `[SwaggerTag]`.

The OpenAPI document model itself (`OpenApiInfo`, `OpenApiSecurityScheme`, `OpenApiContact`, etc.) comes from **Microsoft.OpenApi**, a transitive dependency; those types are referenced constantly in `SwaggerGenOptions` configuration but are not part of Swashbuckle's own surface — treat well-known `OpenApi*` members as available and verify spelling against the user's `Microsoft.OpenApi` version if the IDE flags them.

## Step 1 — detect the project's full version (always first)

Resolve the full `MAJOR.MINOR.PATCH` in this priority order. **Stop at the first match.**

**Package names that signal "this is a Swagger/Swashbuckle project":**
- `Swashbuckle.AspNetCore` (meta-package; pulls in Swagger + SwaggerGen + SwaggerUI)
- `Swashbuckle.AspNetCore.SwaggerGen`, `.Swagger`, `.SwaggerUI` (the individual packages)
- `Swashbuckle.AspNetCore.Annotations` (annotations add-on)

All Swashbuckle.AspNetCore.* packages version in lockstep, so any of them gives the version.

**Detection priority:**

1. **User stated it.** "We're on 10.2.1", etc.
2. **A project file is visible in the conversation.** Parse the full `Version=` attribute on the first `<PackageReference>` / `<PackageVersion>` whose `Include` is one of the package names above.
3. **Filesystem access is available.** Search the user's project directory yourself:
   - `Glob` for `**/*.csproj`, `**/Directory.Packages.props`, and `**/Directory.Build.props` (skip `bin/`, `obj/`, `node_modules/`, `.git/`, `.vs/`).
   - `Read` each match and look for `<PackageReference Include="Swashbuckle.AspNetCore..." ...>`.
   - If nothing matches locally, walk up parent directories.
   - Skip MSBuild property references like `$(SwashbuckleVersion)`.
4. **Still unknown.** Ask the user **once**: "What exact version of Swashbuckle.AspNetCore does this project use? (e.g. 10.2.1, 6.6.2)" Don't guess — the surface differs meaningfully across majors.

If `<skill-dir>` is unclear, it's the directory containing this `SKILL.md`.

## Step 2 — pick the closest matching reference files

You have the project's full version `V = MAJOR.MINOR.PATCH`. The skill ships one trio of reference files per tracked minor (latest patch in that minor) plus historical patch files. Find the best match in this **priority order**:

1. **Exact full match** — `reference/api-surface-v{V}.md` exists → use it.
2. **Same minor, highest patch** in `reference/` → use that. Patches don't add public API.
3. **Same major, highest minor ≤ project's minor** in `reference/` → fall back. **Never fall back to a HIGHER minor.** Swashbuckle has changed across majors (notably the v5→v6 move to Microsoft.OpenApi types, and option/method changes since); using a higher major's surface would recommend members that don't exist in the project's version.
4. **No safe match found** → tell the user: "Your project is on v6.x but this skill only has reference data for v10.2.1. Either upgrade, or add v6.x to `VERSIONS` and rerun `update_skill.py`."

Once matched, load **all three** files: `api-surface-v{L}.md` (every Swashbuckle member available across the tracked packages), `patterns-v{L}.md` (how to organize Swagger setup, when to use filters vs. annotations vs. XML comments, security definitions, versioned documents), `examples-v{L}.md` (canonical snippets: minimal setup, XML comments, multiple documents, JWT/bearer security, a schema filter, an operation filter, annotations).

**The rule: if a member doesn't appear in `api-surface-v{L}.md`, it does not exist in this version.** Verify exact method/option names — `SwaggerDoc`, `SwaggerEndpoint`, `IncludeXmlComments`, `AddSecurityDefinition`, `AddSecurityRequirement`, `SchemaFilter<T>()`, `OperationFilter<T>()`, `DocumentFilter<T>()` — before referencing them.

## Step 3 — write or review the code

Generate code using **only** members listed in the loaded `api-surface-v{L}.md`. Cornerstone idioms to verify before referencing:

- **Minimal setup:** `services.AddSwaggerGen()` → `app.UseSwagger()` → `app.UseSwaggerUI()`
- **Document metadata:** `c.SwaggerDoc("v1", new OpenApiInfo { Title = "...", Version = "v1" })` inside `AddSwaggerGen(c => ...)`
- **XML comments:** `c.IncludeXmlComments(Path.Combine(AppContext.BaseDirectory, "MyApi.xml"))` (requires `<GenerateDocumentationFile>true</GenerateDocumentationFile>` in the csproj)
- **Security:** `c.AddSecurityDefinition("Bearer", new OpenApiSecurityScheme { ... })` + `c.AddSecurityRequirement(...)`
- **Filters:** `c.SchemaFilter<MySchemaFilter>()`, `c.OperationFilter<MyOperationFilter>()`, `c.DocumentFilter<MyDocumentFilter>()` — each implementing `ISchemaFilter` / `IOperationFilter` / `IDocumentFilter` with an `Apply(...)` method (verify the `Apply` signature and context type against the surface)
- **UI tuning:** `app.UseSwaggerUI(c => { c.SwaggerEndpoint("/swagger/v1/swagger.json", "v1"); c.RoutePrefix = "..."; })`
- **Annotations:** `[SwaggerOperation(Summary = "...")]`, `[SwaggerResponse(StatusCodes.Status200OK, "...", typeof(Foo))]` (requires `c.EnableAnnotations()` in `AddSwaggerGen`)

If reviewing existing code:
- Flag a filter class whose `Apply(...)` signature doesn't match this version's `ISchemaFilter`/`IOperationFilter`/`IDocumentFilter` (the context types and OpenAPI model types changed across majors).
- Flag `UseSwaggerUI` pointing at a `SwaggerEndpoint` whose document name doesn't match a `SwaggerDoc("name", ...)` registration — the UI dropdown will 404.
- Flag `IncludeXmlComments` without `<GenerateDocumentationFile>true</GenerateDocumentationFile>` in the project — the XML won't exist at runtime.
- Flag Swagger middleware/UI exposed in Production without intent — many teams gate `UseSwagger`/`UseSwaggerUI` behind `app.Environment.IsDevelopment()`; if it's intentionally public, that's fine, but flag an *unintended* public spec.
- Flag `[SwaggerOperation]`/`[SwaggerResponse]` usage without `c.EnableAnnotations()` — the attributes are silently ignored.
- Flag hand-written `OpenApiInfo`/security objects that reference `OpenApi*` members not in the project's Microsoft.OpenApi version.

If the `patterns-v{L}.md` or `examples-v{L}.md` files are missing (no `ANTHROPIC_API_KEY` available when running the generator), use `api-surface-v{L}.md` directly as the reference.

## Migration questions

For cross-major upgrades read **`reference/migration-notes.md`** (GitHub release notes by major). The biggest historical break was **v5 → v6**, which replaced Swashbuckle's own OpenAPI model with **Microsoft.OpenApi** types (`Info` → `OpenApiInfo`, etc.) and changed filter context types. More recent majors adjusted `SwaggerGenOptions`, minimal-API support, and the UI. After upgrading, re-check every filter's `Apply` signature and every `OpenApi*` type your setup constructs.

## When the user reports the generated code doesn't compile

The first suspect is stale or mismatched reference data. Re-run the maintenance script:
```bash
python tools/update_skill.py swagger
```

The second suspect is the closest-match fallback across majors. If the project is on v6 but only v10 data exists, do NOT use v10's surface — the filter context and option APIs differ. Add the project's version to `VERSIONS` and rerun.

The third suspect is a package-not-referenced member: `[SwaggerOperation]`/`[SwaggerResponse]` need `Swashbuckle.AspNetCore.Annotations` (plus `EnableAnnotations()`); the `OpenApiInfo`/`OpenApiSecurityScheme` types come from `Microsoft.OpenApi`. If those don't resolve, the package isn't installed.

## What this skill will NOT do

- It will not cover **NSwag** (the other "Swagger for .NET" toolchain) — only Swashbuckle.AspNetCore.
- It will not cover the built-in `Microsoft.AspNetCore.OpenApi` (`AddOpenApi`/`MapOpenApi`, the .NET 9+ native generator) — that's a separate library; mention it as an alternative if the user is choosing, but this skill is for Swashbuckle.
- It will not pick a version for the user. For a fresh project, recommend the latest tracked version.
- It will not invent option/filter members. If a method or context type isn't in the loaded surface, it doesn't exist in that version.

## File map (relative to this `SKILL.md`)

```
SKILL.md                              ← you are here
VERSIONS                              ← accumulating ledger; every tracked version on its own line
skill.config.json                     ← per-library config (package ids, repo, siblings, source-augment)
prompts/
  examples.system.md                  ← examples-prompt body (grounding rules prepended at runtime)
  patterns.system.md                  ← patterns-prompt body (same)
reference/
  api-surface-v10.2.1.md              ← v10.2.1 allowed members — from .nupkg XML docs + source-augmented setup methods
  examples-v10.2.1.md                 ← v10.2.1 examples — LLM-generated, grounded
  patterns-v10.2.1.md                 ← v10.2.1 patterns — LLM-generated, grounded
  migration-notes.md                  ← release notes by major — fetched from GitHub Releases
```

No `scripts/` folder. Version detection happens inline in Step 1 of this workflow using Claude's `Glob`/`Read` tools — no per-skill script needed. The maintenance updater lives at the repo root in `tools/update_skill.py` and is only used when refreshing the skill from upstream; users who install this skill don't need it.

### What's generated by code vs. by Claude

- `api-surface-v*.md` and `migration-notes.md` are **deterministic** — extracted from the NuGet packages' XML doc comments (Swagger, SwaggerGen, SwaggerUI, Annotations) and, for the undocumented `AddSwaggerGen` (and any other XML-omitted setup members), augmented from the GitHub source tree at the matching tag. They never contain anything Claude made up.
- `examples-v*.md` and `patterns-v*.md` are **LLM-generated** by `update_skill.py`, grounded in a single version's api-surface so a member that doesn't exist in v6 can't sneak into v6 examples.
