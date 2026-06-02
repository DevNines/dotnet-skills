---
name: fastendpoints
description: Write, review, or migrate code that uses the FastEndpoints NuGet package family (FastEndpoints + FastEndpoints.Swagger + FastEndpoints.Security + FastEndpoints.Validation + FastEndpoints.Generator + FastEndpoints.Messaging.* + FastEndpoints.Attributes). FastEndpoints implements the REPR pattern (Request → Endpoint → Response) for ASP.NET Core. Use whenever a project imports any FastEndpoints package, when the user asks for an "endpoint" / "validator" / "request DTO" / "Configure()" / "HandleAsync" against an HTTP route, or when migrating between versions. This skill is version-aware: it detects which exact version the project pins (e.g. 8.1.0) and loads the reference files generated against that specific version, never recommending a member that doesn't exist in the project's version.
---

# FastEndpoints — version-aware skill

You are helping the user write or migrate C# / ASP.NET Core code that uses the **FastEndpoints** family of NuGet packages. The library follows the REPR pattern: each HTTP endpoint is a class inheriting from `Endpoint<TRequest>` / `Endpoint<TRequest, TResponse>` / `EndpointWithoutRequest<TResponse>`, with routing, auth, OpenAPI metadata, and validation configured in `Configure()` and the single request → response transform in `HandleAsync()`. New members are added in minor releases, so the same question has different correct answers depending on the **exact** version the project is pinned to. **Detect the version before writing code, and load the closest-matching reference files.**

## Step 1 — detect the project's full version (always first)

Resolve the full `MAJOR.MINOR.PATCH` in this priority order. **Stop at the first match.**

**Package names that signal "this is a FastEndpoints project":**
- `FastEndpoints`
- `FastEndpoints.Swagger`
- `FastEndpoints.Security`
- `FastEndpoints.Validation`
- `FastEndpoints.Generator`
- `FastEndpoints.Messaging.Core`
- `FastEndpoints.Messaging.Remote`
- `FastEndpoints.Attributes`

**Detection priority:**

1. **User stated it.** If the user said "we're on 8.1.0" or "this project uses FastEndpoints 7.2.0", use that.
2. **A project file is visible in the conversation.** If a `.csproj`, `Directory.Packages.props`, or `Directory.Build.props` is in the conversation, parse the full `Version=` attribute on the first `<PackageReference>` / `<PackageVersion>` whose `Include` matches one of the names above.
3. **Filesystem access is available.** Search the user's project directory yourself:
   - `Glob` for `**/*.csproj`, `**/Directory.Packages.props`, and `**/Directory.Build.props` from the current working directory (skip `bin/`, `obj/`, `node_modules/`, `.git/`, `.vs/`).
   - `Read` each match.
   - Look for a `<PackageReference>` or `<PackageVersion>` whose `Include` is one of the names above, and pull the `Version=` attribute (or the `<Version>` child element).
   - If nothing matches in the current directory tree, repeat the Glob in each parent directory walking up to the filesystem root — handles being invoked from a deep subdirectory.
   - If a `Version` value is an MSBuild property reference like `$(FastEndpointsVersion)`, that's an unresolved placeholder; keep searching.
4. **Still unknown.** Ask the user **once**: "What exact version of FastEndpoints does this project use? (e.g. 8.1.0, 7.2.0)" Do not guess and do not silently default. A wrong-version answer will hand the user uncompilable code.

### Note about sibling versions

FastEndpoints sibling packages version **independently** of core. Your project might pin `FastEndpoints 8.1.0` alongside `FastEndpoints.Validation 3.11.0` — these are normal, not a mistake. The skill's reference data is keyed by **core version**; sibling APIs at that point in time are concatenated into the same reference. So detect from the *core* package if present; if only a sibling is referenced, use the sibling's version as the closest signal and verify against the user.

## Step 2 — pick the closest matching reference files

You have the project's full core version `V = MAJOR.MINOR.PATCH`. The skill ships one trio of reference files per tracked minor (latest patch in that minor) plus historical patch files. Find the best match in this **priority order**:

1. **Exact full match** — `reference/api-surface-v{V}.md` exists → use it. Best case.
2. **Same minor, highest patch in `reference/`** — e.g. project is on 8.1.0 and skill has `api-surface-v8.1.0.md` (or 8.1.1 if a later patch shipped) → use the closest. Patches almost never add public API, so this is safe.
3. **Same major, highest minor ≤ project's minor** in `reference/` — e.g. project is on 8.0.1, skill has files for 8.1.x but not 8.0.x → fall back to `8.0.x` if present, else `7.x` of an earlier minor. **Never fall back to a HIGHER minor**: higher minors include features the project doesn't have, and recommending them gives the user uncompilable code.
4. **No safe match found** → tell the user explicitly: "Your project is on v7.2.0 but this skill only has reference data for v8.1.0. Either upgrade the project to 8.1.x, or have the maintainer add v7.2.0 to the skill's `VERSIONS` file and re-run `update_skill.py`." Do not generate code from the surface of a higher minor.

To list what's available, use `ls <skill-dir>/reference/api-surface-v*.md` and read the version part of each filename.

Once you've picked the matching version label `L` (e.g. `8.1.0`), load **all three** files:
- `reference/api-surface-v{L}.md` — authoritative allowed members across **all** FastEndpoints siblings at that point in time
- `reference/patterns-v{L}.md` — naming, validation, wiring rules grounded in this version
- `reference/examples-v{L}.md` — canonical skeletons grounded in this version, including a "new in v{major.minor}" example

**The rule: if a type / method / property doesn't appear in `api-surface-v{L}.md`, it does not exist in this version.** The api-surface file groups types by package (`## package FastEndpoints`, `## package FastEndpoints.Swagger`, etc.), so you can also tell *which* package a type lives in. Do not invent overloads, do not rely on members that were added in a later version, do not rely on members that were removed. If you need a capability that isn't listed, say so explicitly and propose either (a) a different approach using the listed members or (b) upgrading the project to a minor/major that has it.

## Step 3 — write or review the code

Generate code that uses **only** members listed in the loaded `api-surface-v{L}.md`. When you reference a type or method in an explanation, link it mentally to its entry in the api-surface file — that's your source of truth.

If the user is reviewing existing code, flag any call site that uses a member not in the api-surface file (it's either misnamed, from a different version, or you are looking at an older copy of the docs — rerun `scripts/update_skill.py` to refresh).

If the `patterns-v{L}.md` or `examples-v{L}.md` files are missing (e.g. the skill was installed without `ANTHROPIC_API_KEY` available to run the generator), do not invent your own. Tell the user to run `python <skill-dir>/scripts/update_skill.py` with `ANTHROPIC_API_KEY` set, then proceed using `api-surface-v{L}.md` directly as the authoritative reference.

## Migration questions

If the user is upgrading across majors or minors (e.g. v7 → v8), read **`reference/migration-notes.md`**. It's the GitHub release notes grouped by major, with the breaking-change entries and feature additions. Walk through every release between the source and target versions in order.

## When the user reports the generated code doesn't compile

The first suspect is stale or mismatched reference data. Run:
```bash
python <skill-dir>/scripts/update_skill.py
```
…then re-pick the closest matching `api-surface-v{L}.md` (the patch may have bumped) and regenerate. The update script is **version-aware**: it reads each tracked minor's recorded patch from `VERSIONS`, compares to NuGet's latest patch in that minor, and only refreshes when the patch moved or the LLM files are missing. It auto-adds NEWER minors in already-tracked majors AND NEWER majors entirely (so v8.2.0 lands automatically when NuGet ships it stable, and v9.0.0 lands automatically too when it eventually ships). Forward-only — OLDER versions you never tracked require manual addition. When a patch bumps, new full-version-labeled files are written and the old patch's files are kept on disk as historical reference.

The second suspect is wrong-version detection. If the user mentioned a version that contradicts what the detector returned (e.g. they manually upgraded the package but a `Directory.Packages.props` upstream still pins the old version), ask which is authoritative.

The third suspect is a no-safe-match fallback. If `detect_version.py` returned `7.2.0` but the skill only has files for `8.1.0` (a higher major), do NOT silently use `8.1.0`'s files — they will recommend members added in 8.x that don't exist in 7.x. Tell the user to either upgrade or add `7.2.0` to `VERSIONS` and re-run the updater.

The fourth suspect — specific to FastEndpoints — is **sibling drift**. The api-surface concatenates XML docs from core + every sibling at the latest each was published, NOT necessarily at versions matching the core's release date. If the user is on `FastEndpoints.Validation 3.10.0` but the skill's surface was generated against `FastEndpoints.Validation 3.11.0`, a method in the surface might not yet exist in the user's pinned sibling. Ask which exact sibling versions they have and reconcile.

## What this skill will NOT do

- It will not generate code for unrelated packages with similar themes (e.g. `Carter`, `Ardalis.ApiEndpoints`, raw `Microsoft.AspNetCore.Mvc` controllers). Those have different idioms.
- It will not convert an MVC project into FastEndpoints unless explicitly asked. Suggest the pattern; don't impose it.
- It will not pick a version for the user. If they have no project pinned and they're starting fresh, recommend the latest tracked version (whatever's in `VERSIONS` at the top patch) and say so explicitly.

## File map (relative to this `SKILL.md`)

```
SKILL.md                              ← you are here
VERSIONS                              ← accumulating ledger; every tracked version on its own line
skill.config.json                     ← per-library configuration (package id, repo, siblings)
prompts/
  examples.system.md                  ← examples-prompt body (grounding rules prepended at runtime)
  patterns.system.md                  ← patterns-prompt body (same)
reference/
  api-surface-v8.1.0.md               ← v8.1.0 allowed API across core + all siblings — extracted from .nupkg XML docs
  examples-v8.1.0.md                  ← v8.1.0 examples — LLM-generated, grounded in the above
  patterns-v8.1.0.md                  ← v8.1.0 patterns — LLM-generated, grounded in the above
  migration-notes.md                  ← release notes by major — fetched from GitHub Releases
```

No `scripts/` folder. Version detection happens inline in Step 1 of this workflow using Claude's `Glob`/`Read` tools — no per-skill script needed. The maintenance updater lives at the repo root in `tools/update_skill.py` and is only used when refreshing the skill from upstream; users who install this skill don't need it.

The exact filenames in `reference/` depend on the latest patches tracked. To list what's available right now:
```bash
ls <skill-dir>/reference/api-surface-v*.md
```

### What's generated by code vs. by Claude

- `api-surface-v*.md` and `migration-notes.md` are **deterministic** — extracted byte-for-byte from NuGet packages (core + all sibling FastEndpoints.* packages, concatenated) and the GitHub Releases API. They never contain anything Claude made up.
- `examples-v*.md` and `patterns-v*.md` are **LLM-generated** by `update_skill.py` calling the Anthropic Messages API. Each file is grounded in a single full version's api-surface, so identifiers can't drift across versions. The prompt for examples additionally includes the GitHub diff against the previous tracked minor and that major's release notes; the prompt for patterns is grounded in the api-surface only. Generation is skipped silently if `ANTHROPIC_API_KEY` is unset, in which case existing copies (if any) are left untouched.
