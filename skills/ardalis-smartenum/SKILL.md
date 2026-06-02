---
name: ardalis-smartenum
description: Write, review, or migrate code that uses the Ardalis.SmartEnum NuGet package family (Ardalis.SmartEnum + .SystemTextJson + .EFCore + .AutoFixture + .Dapper + .Utf8Json). SmartEnum is a strongly-typed enum replacement — instead of `enum OrderStatus { Pending, Paid, Shipped }`, you write a `sealed class OrderStatus : SmartEnum<OrderStatus>` with named static instances. Members can carry data (display strings, decimals, behavior), serialize/deserialize through the sibling adapters (System.Text.Json, EF Core, Dapper, Utf8Json, AutoFixture), and be tested with full type safety. Use whenever a project imports any Ardalis.SmartEnum.* package, when the user asks for "smart enum", "enum class", or "strongly-typed enum", or when migrating between versions. This skill is version-aware: it detects which exact version the project pins (e.g. 8.2.0) and loads the reference files generated against that specific version.
---

# Ardalis.SmartEnum — version-aware skill

You are helping the user write or migrate C# code that uses the **Ardalis.SmartEnum** family of NuGet packages. SmartEnum is the "strongly-typed enum" pattern: each enum value is a static instance of a `sealed class` derived from `SmartEnum<T>` (or `SmartEnum<T, TValue>`), with explicit name + value pairs declared as `public static readonly T Pending = new(...)`. Members can carry behavior (methods, properties), serialize through one of the sibling adapters, and be enumerated/compared with full type safety. **Detect the version before writing code, and load the closest-matching reference files.**

## Step 1 — detect the project's full version (always first)

Resolve the full `MAJOR.MINOR.PATCH` in this priority order. **Stop at the first match.**

**Package names that signal "this is an Ardalis.SmartEnum project":**
- `Ardalis.SmartEnum`
- `Ardalis.SmartEnum.SystemTextJson`
- `Ardalis.SmartEnum.EFCore`
- `Ardalis.SmartEnum.AutoFixture`
- `Ardalis.SmartEnum.Dapper`
- `Ardalis.SmartEnum.Utf8Json`

The siblings **version independently of core** — a project may have core at `8.2.0` while `.Utf8Json` is at `2.1.0`. Use the **core** version when both are present; if only a sibling is referenced, use the sibling's version as the closest signal and verify with the user.

**Detection priority:**

1. **User stated it.** "We're on 8.2.0", etc.
2. **A project file is visible in the conversation.** Parse the full `Version=` attribute on the first `<PackageReference>` / `<PackageVersion>` whose `Include` matches one of the names above.
3. **Filesystem access is available.** Search the user's project directory yourself:
   - `Glob` for `**/*.csproj`, `**/Directory.Packages.props`, and `**/Directory.Build.props` (skip `bin/`, `obj/`, `node_modules/`, `.git/`, `.vs/`).
   - `Read` each match and look for a `<PackageReference>` / `<PackageVersion>` whose `Include` matches one of the names above.
   - If nothing matches locally, walk up parent directories.
   - Skip MSBuild property references like `$(SmartEnumVersion)` — those are unresolved placeholders.
4. **Still unknown.** Ask the user **once** for the exact version. Don't guess.

## Step 2 — pick the closest matching reference files

You have the project's full core version `V = MAJOR.MINOR.PATCH`. Find the best match in **priority order**:

1. **Exact full match** — `reference/api-surface-v{V}.md` exists → use it.
2. **Same minor, highest patch** in `reference/` → use that. Patches don't add public API.
3. **Same major, highest minor ≤ project's minor** in `reference/` → fall back. **Never fall back to a HIGHER minor.**
4. **No safe match found** → tell the user: "Your project is on v7.0.0 but this skill only has reference data for v8.2.0. Either upgrade, or add v7.0.0 to `VERSIONS` and rerun `update_skill.py`."

Once matched, load **all three** files: `api-surface-v{L}.md` (allowed members across core + all sibling adapters), `patterns-v{L}.md` (when to use SmartEnum vs plain enum, naming, sibling adapter wiring), `examples-v{L}.md` (canonical SmartEnum class skeletons and the "new in v{MAJOR.MINOR}" highlight).

**The rule: if a type / method doesn't appear in `api-surface-v{L}.md`, it does not exist in this version.** The api-surface groups types by package (`## package Ardalis.SmartEnum`, `## package Ardalis.SmartEnum.SystemTextJson`, etc.), so you can see *which* sibling each type lives in.

## Step 3 — write or review the code

Generate code using **only** members listed in the loaded `api-surface-v{L}.md`. SmartEnum has two main base classes: `SmartEnum<TEnum>` (default int-valued) and `SmartEnum<TEnum, TValue>` (any value type, e.g. `SmartEnum<HttpStatus, int>`, `SmartEnum<Currency, string>`). When recommending adapters, look up the exact type names in the appropriate sibling section of the api-surface.

If reviewing existing code:
- Flag any `new YourEnum(name, value)` outside a `public static readonly` field — instances should be singletons declared at the class level
- Flag use of `==`/`!=` on SmartEnum instances when reference equality isn't appropriate (the base class implements value equality correctly, so this is rarely a bug — but verify)
- Flag any sibling package use where the corresponding type isn't in the surface (probably a version mismatch — check sibling pinned version)

## Migration questions

For v1 → v2 → v7/8 transitions, read **`reference/migration-notes.md`**. The major bumps removed some legacy serializers (e.g. JsonNet was deprecated in favor of SystemTextJson).

## When the user reports the generated code doesn't compile

The first suspect is stale reference data. Re-run the maintenance script (from the skills repo root):
```bash
python tools/update_skill.py ardalis-smartenum
```

The second suspect is **sibling drift** — SmartEnum siblings version independently of core. If the surface was generated against `Utf8Json 2.1.0` but the user's project pins `Utf8Json 1.0.3`, methods listed in the surface may not exist in the user's pinned sibling. Ask which exact sibling versions they have and reconcile.

The third suspect is the closest-match fallback. If `detect_version.py` returned `7.0.0` but the skill only has files for `8.x`, do NOT use 8.x files for a v7 project. Add v7.0.0 to `VERSIONS` and rerun.

## What this skill will NOT do

- It will not generate code for unrelated Ardalis libraries (Specification, Result, GuardClauses, ApiEndpoints). Each has its own skill.
- It will not convert a plain `enum` to a SmartEnum unless explicitly asked. Suggest the pattern; don't impose it (plain enums are still right for many cases).
- It will not pick a version for the user. For a fresh project, recommend the latest tracked version.

## File map (relative to this `SKILL.md`)

```
SKILL.md                              ← you are here
VERSIONS                              ← accumulating ledger; every tracked version on its own line
skill.config.json                     ← per-library configuration (package id, repo, siblings, tag_prefix)
prompts/
  examples.system.md                  ← examples-prompt body (grounding rules prepended at runtime)
  patterns.system.md                  ← patterns-prompt body (same)
reference/
  api-surface-v8.2.0.md               ← v8.2.0 allowed API across core + all siblings
  examples-v8.2.0.md                  ← v8.2.0 examples — LLM-generated, grounded
  patterns-v8.2.0.md                  ← v8.2.0 patterns — LLM-generated, grounded
  migration-notes.md                  ← release notes — fetched from GitHub Releases
```

No `scripts/` folder. Version detection happens inline in Step 1 of this workflow using Claude's `Glob`/`Read` tools — no per-skill script needed. The maintenance updater lives at the repo root in `tools/update_skill.py` (which reads this skill's `skill.config.json` — note `tag_prefix: "SmartEnum-"` because the SmartEnum repo scopes git tags by sub-package) and is only used when refreshing the skill from upstream.
