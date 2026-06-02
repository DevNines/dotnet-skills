---
name: ardalis-spec
description: Write, review, or migrate code that uses the Ardalis.Specification NuGet package (the Specification pattern for EF Core / EF6 / in-memory queries in C#). Use whenever a project imports Ardalis.Specification or any sibling package (Ardalis.Specification.EntityFrameworkCore, Ardalis.Specification.EntityFramework6), when the user asks for a "spec" / "specification" / repository helper against an entity, or when migrating between versions of the library. This skill is version-aware: it detects which exact version the project pins (e.g. 8.0.0, 9.3.1) and loads the reference files generated against that specific version, never recommending a member that doesn't exist in the project's version.
---

# Ardalis.Specification — version-aware skill

You are helping the user write or migrate C# code that uses the **Ardalis.Specification** NuGet package. The library evolves across both majors and minors — new members are added in minor releases (e.g. `WithProjectionOf` arrived in 9.1, `OneOrMany` in 9.3), so the same question has different correct answers depending on the **exact** version the project is pinned to. **Detect the version before writing code, and load the closest-matching reference files.**

## Step 1 — detect the project's full version (always first)

Resolve the full `MAJOR.MINOR.PATCH` in this priority order. **Stop at the first match.**

**Package names that signal "this is an Ardalis.Specification project":**
- `Ardalis.Specification`
- `Ardalis.Specification.EntityFrameworkCore`
- `Ardalis.Specification.EntityFramework6`

**Detection priority:**

1. **User stated it.** If the user said "we're on 9.3.1" or "Project A uses 8.0.0" in this conversation, use that.
2. **A project file is visible in the conversation.** If a `.csproj`, `Directory.Packages.props`, or `Directory.Build.props` is in the conversation (paste, tool result, prior Read), parse the full `Version=` attribute on the first `<PackageReference>` / `<PackageVersion>` whose `Include` matches one of the names above.
3. **Filesystem access is available.** Search the user's project directory yourself:
   - `Glob` for `**/*.csproj`, `**/Directory.Packages.props`, and `**/Directory.Build.props` from the current working directory (skip `bin/`, `obj/`, `node_modules/`, `.git/`, `.vs/`).
   - `Read` each match.
   - Look for a `<PackageReference>` or `<PackageVersion>` whose `Include` is one of the names above, and pull the `Version=` attribute (or the `<Version>` child element).
   - If nothing matches in the current directory tree, repeat the Glob in each parent directory walking up to the filesystem root — handles being invoked from a deep subdirectory of the solution.
   - If a `Version` value is an MSBuild property reference like `$(SpecVersion)`, that's an unresolved placeholder; keep searching.
4. **Still unknown.** Ask the user **once**: "What exact version of Ardalis.Specification does this project use? (e.g. 8.0.0, 9.3.1)" Do not guess and do not silently default. A wrong-version answer will hand the user uncompilable code.

## Step 2 — pick the closest matching reference files

You have the project's full version `V = MAJOR.MINOR.PATCH`. The skill ships one trio of reference files per tracked minor (latest patch in that minor) plus historical patch files. Find the best match in this **priority order**:

1. **Exact full match** — `reference/api-surface-v{V}.md` exists → use it. Best case.
2. **Same minor, highest patch in `reference/`** — e.g. project is on 9.3.0, skill has `api-surface-v9.3.1.md` → use 9.3.1. Patches almost never add public API, so this is safe.
3. **Same major, highest minor ≤ project's minor** in `reference/` — e.g. project is on 9.2.5, skill has files for 9.3.x but not 9.2.x → fall back to `9.1.x` if present, else `9.0.x`. **Never fall back to a HIGHER minor** (e.g. project on 9.0.1 using 9.3.x files): higher minors include features the project doesn't have, and recommending them gives the user uncompilable code.
4. **No safe match found** → tell the user explicitly: "Your project is on v9.0.1 but this skill only has reference data for v9.3.1 and v8.0.0. Either upgrade the project to 9.3.x, or have the maintainer add v9.0.x to the skill's `VERSIONS` file and re-run `update_skill.py`." Do not generate code from the surface of a higher minor.

To list what's available, use `ls <skill-dir>/reference/api-surface-v*.md` and read the version part of each filename.

Once you've picked the matching version label `L` (e.g. `9.3.1`), load **all three** files:
- `reference/api-surface-v{L}.md` — authoritative allowed members
- `reference/patterns-v{L}.md` — naming, validation, wiring rules grounded in this version
- `reference/examples-v{L}.md` — canonical skeletons grounded in this version, including a "new in v{major.minor}" example

**The rule: if a type / method / property doesn't appear in `api-surface-v{L}.md`, it does not exist in this version.** Do not invent overloads, do not rely on members that were added in a later version, do not rely on members that were removed. If you need a capability that isn't listed, say so explicitly and propose either (a) a different approach using the listed members or (b) upgrading the project to a minor/major that has it.

## Step 3 — write or review the code

Generate code that uses **only** members listed in the loaded `api-surface-v{L}.md`. When you reference a type or method in an explanation, link it mentally to its entry in the api-surface file — that's your source of truth.

If the user is reviewing existing code, flag any call site that uses a member not in the api-surface file (it's either misnamed, from a different version, or you are looking at an older copy of the docs — rerun `scripts/update_skill.py` to refresh).

If the `patterns-v{L}.md` or `examples-v{L}.md` files are missing (e.g. the skill was installed without `ANTHROPIC_API_KEY` available to run the generator), do not invent your own. Tell the user to run `python <skill-dir>/scripts/update_skill.py` with `ANTHROPIC_API_KEY` set, then proceed using `api-surface-v{L}.md` directly as the authoritative reference.

## Migration questions

If the user is upgrading across majors (e.g. v8 → v9), read **`reference/migration-notes.md`**. It's the GitHub release notes grouped by major, with the breaking-change entries and feature additions. Walk through every release between the source and target majors in order.

## When the user reports the generated code doesn't compile

The first suspect is stale or mismatched reference data. Run:
```bash
python <skill-dir>/scripts/update_skill.py
```
…then re-pick the closest matching `api-surface-v{L}.md` (the patch may have bumped) and regenerate. The update script is **version-aware**: it reads each tracked minor's recorded patch from `VERSIONS`, compares to NuGet's latest patch in that minor, and only refreshes when the patch moved or the LLM files are missing. It auto-adds NEWER minors in already-tracked majors AND NEWER majors entirely (so v9.4.0 lands automatically when NuGet ships it and v9.3.x was tracked, and v10.0.0 lands automatically when NuGet ships it). Forward-only — OLDER versions you never tracked require manual addition. When a patch bumps, new full-version-labeled files are written and the old patch's files are kept on disk as historical reference.

The second suspect is wrong-version detection. If the user mentioned a version that contradicts what the detector returned (e.g. they manually upgraded the package but a `Directory.Packages.props` upstream still pins the old version), ask which is authoritative.

The third suspect is a no-safe-match fallback. If `detect_version.py` returned `9.0.1` but the skill only has files for `9.3.1` (a higher minor), do NOT silently use `9.3.1`'s files — they will recommend members added in 9.1 / 9.2 / 9.3 that don't exist in 9.0.x. Tell the user to either upgrade or add `9.0.0` to `VERSIONS` and re-run the updater.

## What this skill will NOT do

- It will not generate code for `Ardalis.GuardClauses`, `Ardalis.Result`, `Ardalis.SmartEnum`, `Ardalis.ApiEndpoints`, or any other Ardalis library. Those are separate packages with separate skills (or no skill yet).
- It will not refactor a project from a non-Specification pattern (e.g. raw EF Core repositories) into Specification-pattern unless the user explicitly asks for that. Suggest the pattern as an option; don't impose it.
- It will not pick a version for the user. If they have no project pinned and they're starting fresh, recommend v9 (latest stable) and say so explicitly.

## File map (relative to this `SKILL.md`)

```
SKILL.md                              ← you are here
VERSIONS                              ← accumulating ledger; every tracked version on its own line
skill.config.json                     ← per-library configuration (package id, repo, siblings)
prompts/
  examples.system.md                  ← examples-prompt body (grounding rules prepended at runtime)
  patterns.system.md                  ← patterns-prompt body (same)
reference/
  api-surface-v8.0.0.md               ← v8.0.0 allowed API — extracted from .nupkg XML docs
  api-surface-v9.3.1.md               ← v9.3.1 allowed API — extracted from .nupkg XML docs
  examples-v8.0.0.md                  ← v8.0.0 examples — LLM-generated, grounded in the above
  examples-v9.3.1.md                  ← v9.3.1 examples — LLM-generated, grounded in the above
  patterns-v8.0.0.md                  ← v8.0.0 patterns — LLM-generated, grounded in the above
  patterns-v9.3.1.md                  ← v9.3.1 patterns — LLM-generated, grounded in the above
  migration-notes.md                  ← release notes by major — fetched from GitHub Releases
```

No `scripts/` folder. Version detection happens inline in Step 1 of this workflow using Claude's `Glob`/`Read` tools — no per-skill script needed. The maintenance updater lives at the repo root in `tools/update_skill.py` and is only used when refreshing the skill from upstream; users who install this skill don't need it.

The exact filenames in `reference/` depend on the latest patches tracked. To list what's available right now:
```bash
ls <skill-dir>/reference/api-surface-v*.md
```

### What's generated by code vs. by Claude

- `api-surface-v*.md` and `migration-notes.md` are **deterministic** — extracted byte-for-byte from NuGet packages and the GitHub Releases API. They never contain anything Claude made up.
- `examples-v*.md` and `patterns-v*.md` are **LLM-generated** by `update_skill.py` calling the Anthropic Messages API. Each file is grounded in a single full version's api-surface, so identifiers can't drift across versions. The prompt for examples additionally includes the GitHub diff against the previous tracked minor and that major's release notes; the prompt for patterns is grounded in the api-surface only. Generation is skipped silently if `ANTHROPIC_API_KEY` is unset, in which case existing copies (if any) are left untouched.
