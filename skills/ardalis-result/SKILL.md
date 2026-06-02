---
name: ardalis-result
description: Write, review, or migrate code that uses the Ardalis.Result NuGet package family (Ardalis.Result + Ardalis.Result.AspNetCore + Ardalis.Result.FluentValidation). Implements the Result pattern for .NET — methods return Result<T> carrying success values or categorized failure statuses (NotFound, Invalid, Unauthorized, Conflict, Error, CriticalError) instead of throwing exceptions for non-exceptional outcomes. Use whenever a project imports any Ardalis.Result package, when the user asks for "Result pattern", "Result<T>", or how to return errors without exceptions, or when migrating between versions. This skill is version-aware: it detects which exact version the project pins and loads reference files generated against that specific version, never recommending a member that doesn't exist in the project's version.
---

# Ardalis.Result — version-aware skill

You are helping the user write or migrate C# code that uses the **Ardalis.Result** family of NuGet packages. These implement the Result pattern: methods return `Result<T>` (or `Result` for void-equivalent operations) carrying either a success value plus optional message, or a categorized failure (`NotFound`, `Invalid` with validation errors, `Unauthorized`, `Forbidden`, `Conflict`, `Error`, `CriticalError`, etc.). The library evolves across both majors and minors, so the same question has different correct answers depending on the **exact** version the project is pinned to. **Detect the version before writing code, and load the closest-matching reference files.**

## Step 1 — detect the project's full version (always first)

Resolve the full `MAJOR.MINOR.PATCH` in this priority order. **Stop at the first match.**

**Package names that signal "this is an Ardalis.Result project":**
- `Ardalis.Result`
- `Ardalis.Result.AspNetCore`
- `Ardalis.Result.FluentValidation`

**Detection priority:**

1. **User stated it.** If the user said "we're on 10.1.0" or "this project uses Ardalis.Result 9.1", use that.
2. **A project file is visible in the conversation.** Parse the full `Version=` attribute on the first `<PackageReference>` / `<PackageVersion>` whose `Include` matches one of the names above.
3. **Filesystem access is available.** Search the user's project directory yourself:
   - `Glob` for `**/*.csproj`, `**/Directory.Packages.props`, and `**/Directory.Build.props` from the current working directory (skip `bin/`, `obj/`, `node_modules/`, `.git/`, `.vs/`).
   - `Read` each match and look for a `<PackageReference>` / `<PackageVersion>` whose `Include` matches one of the names above.
   - If nothing matches locally, repeat the Glob in each parent directory walking up to the filesystem root.
   - Skip MSBuild property references like `$(ResultVersion)` — those are unresolved placeholders.
4. **Still unknown.** Ask the user **once**: "What exact version of Ardalis.Result does this project use? (e.g. 10.1.0, 9.1.0)" Do not guess.

## Step 2 — pick the closest matching reference files

You have the project's full version `V = MAJOR.MINOR.PATCH`. The skill ships one trio of reference files per tracked minor (latest patch in that minor) plus historical patch files. Find the best match in this **priority order**:

1. **Exact full match** — `reference/api-surface-v{V}.md` exists → use it. Best case.
2. **Same minor, highest patch in `reference/`** → use that. Patches in this library don't add public API; safe to fall back.
3. **Same major, highest minor ≤ project's minor** in `reference/` → fall back. **Never fall back to a HIGHER minor.** Higher minors may include statuses or extension methods that don't exist in the project's older minor.
4. **No safe match found** → tell the user explicitly: "Your project is on v8.0.0 but this skill only has reference data for v10.1.0. Either upgrade the project to 10.x, or have the maintainer add v8.0.0 to the skill's `VERSIONS` file and re-run `update_skill.py`." Do not generate code from the surface of a higher minor.

To list what's available, use `ls <skill-dir>/reference/api-surface-v*.md`.

Once you've picked the matching version label `L`, load **all three** files:
- `reference/api-surface-v{L}.md` — authoritative allowed members across core + AspNetCore + FluentValidation siblings
- `reference/patterns-v{L}.md` — when to use which `Result.X(...)` factory, where translation belongs, anti-patterns
- `reference/examples-v{L}.md` — service-method shape, controller integration, FluentValidation bridge, "new in v{MAJOR.MINOR}" highlight

**The rule: if a type / method / property doesn't appear in `api-surface-v{L}.md`, it does not exist in this version.** Do not invent overloads. The api-surface entries have NO documentation text (the maintainer doesn't enable `<GenerateDocumentationFile>`), so you can only rely on the **member names and signatures** — not on prose descriptions. When in doubt about behavior, point the user to the source on GitHub (`ardalis/Result`) for that specific tag.

## Step 3 — write or review the code

Generate code that uses **only** members listed in the loaded `api-surface-v{L}.md`. When you reference a status or factory in an explanation, link it mentally to its entry in the api-surface file.

If the user is reviewing existing code, flag any call site that uses a member not in the api-surface file — it's either misnamed, from a different version, or you are looking at an older copy of the docs (rerun `scripts/update_skill.py` to refresh).

If the `patterns-v{L}.md` or `examples-v{L}.md` files are missing (e.g. the skill was installed without `ANTHROPIC_API_KEY` available to run the generator), do not invent your own. Tell the user to run `python <skill-dir>/scripts/update_skill.py` with `ANTHROPIC_API_KEY` set.

## Migration questions

If the user is upgrading across majors or minors, read **`reference/migration-notes.md`** — GitHub release notes grouped by major. The Ardalis.Result project has historically renamed and reshaped statuses across majors (notably the v8 → v9 rework), so the migration notes are the canonical answer for "what changed."

## When the user reports the generated code doesn't compile

The first suspect is stale or mismatched reference data. Run:
```bash
python <skill-dir>/scripts/update_skill.py
```
…then re-pick the closest matching `api-surface-v{L}.md` and regenerate. The update script is **version-aware**: it reads each tracked minor's recorded patch, compares to NuGet's latest, and only refreshes when the patch moved or the LLM files are missing. It also auto-adds NEWER minors in already-tracked majors.

The second suspect is wrong-version detection. If the user mentioned a version that contradicts what the detector returned, ask which is authoritative.

The third suspect is the **no-XML-docs limitation**: Ardalis.Result does not ship doc comments in its `.nupkg`, so the api-surface is extracted by parsing C# source from GitHub at the matching tag. The parser is best-effort and may miss exotic constructs (operator overloads with unusual modifiers, deeply-nested types). If the user references a member that genuinely exists in source but isn't in the surface, ask them to paste the relevant `.cs` snippet so you can validate against the real signature.

## What this skill will NOT do

- It will not generate code for unrelated Ardalis libraries (`Ardalis.GuardClauses`, `Ardalis.Specification`, `Ardalis.SmartEnum`, `Ardalis.ApiEndpoints`). Those have separate skills (or no skill yet).
- It will not impose the Result pattern on a project that uses exceptions consistently. Suggest the pattern as a fit-for-purpose tool, don't force it.
- It will not pick a version for the user. For a fresh project, recommend the latest tracked version and say so explicitly.

## File map (relative to this `SKILL.md`)

```
SKILL.md                              ← you are here
VERSIONS                              ← accumulating ledger; every tracked version on its own line
skill.config.json                     ← per-library configuration (package id, repo, siblings, source-fallback subpaths)
prompts/
  examples.system.md                  ← examples-prompt body (grounding rules prepended at runtime)
  patterns.system.md                  ← patterns-prompt body (same)
reference/
  api-surface-v10.1.0.md              ← v10.1.0 allowed API — extracted by source parsing
  examples-v10.1.0.md                 ← v10.1.0 examples — LLM-generated, grounded in the above
  patterns-v10.1.0.md                 ← v10.1.0 patterns — LLM-generated, grounded in the above
  migration-notes.md                  ← release notes by major — fetched from GitHub Releases
```

No `scripts/` folder. Version detection happens inline in Step 1 of this workflow using Claude's `Glob`/`Read` tools — no per-skill script needed. The maintenance updater lives at the repo root in `tools/update_skill.py` (which reads this skill's `skill.config.json` for the source-fallback `subpaths`, since Ardalis.Result ships no XML docs) and is only used when refreshing the skill from upstream.

### What's generated by code vs. by Claude

- `api-surface-v*.md` is **deterministic but extracted from source**, not from XML doc comments. The update script clones the GitHub repo at the matching tag (e.g. `v10.1.0`), walks `.cs` files in each tracked package's subdirectory, and parses public type / method / property / field declarations using a best-effort regex parser. Member names and signatures are accurate; descriptions are absent because the source has no `///` comments.
- `migration-notes.md` is **deterministic**, fetched from `https://github.com/ardalis/Result/releases`.
- `examples-v*.md` and `patterns-v*.md` are **LLM-generated** by `update_skill.py` calling the Anthropic Messages API. Each file is grounded in a single full version's api-surface, so identifiers can't drift across versions.
