---
name: ardalis-guardclauses
description: Write, review, or migrate code that uses the Ardalis.GuardClauses NuGet package — a precondition-checking library that replaces boilerplate `if (x == null) throw new ArgumentNullException(...)` style checks with chainable `Guard.Against.Null(x, nameof(x))` calls. Use whenever a project imports Ardalis.GuardClauses, when the user asks for "guard clauses", "argument validation", "Guard.Against", or "how to validate inputs without try/catch noise", or when migrating between versions. This skill is version-aware: it detects which exact version the project pins (e.g. 5.0.0) and loads the reference files generated against that specific version, never recommending a guard that doesn't exist in the project's version.
---

# Ardalis.GuardClauses — version-aware skill

You are helping the user write or migrate C# code that uses the **Ardalis.GuardClauses** NuGet package. Guard clauses are short, declarative precondition checks placed at the START of methods, constructors, and factories — `Guard.Against.Null(x, nameof(x))`, `Guard.Against.NegativeOrZero(qty, nameof(qty))`, `Guard.Against.OutOfRange(...)`, etc. They throw an appropriate exception (`ArgumentNullException`, `ArgumentOutOfRangeException`, etc.) when violated. New guard helpers are added across versions, and the extension target shape has shifted between majors. **Detect the version before writing code, and load the closest-matching reference files.**

## Step 1 — detect the project's full version (always first)

Resolve the full `MAJOR.MINOR.PATCH` in this priority order. **Stop at the first match.**

**Package name that signals "this is an Ardalis.GuardClauses project":**
- `Ardalis.GuardClauses` (single-package family)

**Detection priority:**

1. **User stated it.** "We're on 5.0.0", etc.
2. **A project file is visible in the conversation.** Parse the full `Version=` attribute on the first `<PackageReference>` / `<PackageVersion>` whose `Include` is `Ardalis.GuardClauses`.
3. **Filesystem access is available.** Search the user's project directory yourself:
   - `Glob` for `**/*.csproj`, `**/Directory.Packages.props`, and `**/Directory.Build.props` (skip `bin/`, `obj/`, `node_modules/`, `.git/`, `.vs/`).
   - `Read` each match and look for `<PackageReference Include="Ardalis.GuardClauses" ...>`.
   - If nothing matches locally, walk up parent directories.
   - Skip MSBuild property references like `$(GuardClausesVersion)`.
4. **Still unknown.** Ask the user **once**: "What exact version of Ardalis.GuardClauses does this project use? (e.g. 5.0.0, 4.6.0)" Don't guess.

## Step 2 — pick the closest matching reference files

You have the project's full version `V = MAJOR.MINOR.PATCH`. The skill ships one trio of reference files per tracked minor (latest patch in that minor) plus historical patch files. Find the best match in this **priority order**:

1. **Exact full match** — `reference/api-surface-v{V}.md` exists → use it.
2. **Same minor, highest patch in `reference/`** → use that.
3. **Same major, highest minor ≤ project's minor** in `reference/` → fall back. **Never fall back to a HIGHER minor.**
4. **No safe match found** → tell the user explicitly: "Your project is on v4.5 but this skill only has reference data for v5.0.0. Either upgrade, or add v4.5 to `VERSIONS` and re-run `update_skill.py`." Do not generate code from the surface of a higher minor (it may recommend guard methods that don't exist in their version).

To list what's available, use `ls <skill-dir>/reference/api-surface-v*.md`.

Once you've picked the matching version label `L`, load **all three** files:
- `reference/api-surface-v{L}.md` — authoritative list of every `Guard.Against.X(...)` available
- `reference/patterns-v{L}.md` — when to use which guard, anti-patterns
- `reference/examples-v{L}.md` — small snippets showing each guard in context, plus a "new in v{MAJOR.MINOR}" highlight

**The rule: if a guard method doesn't appear in `api-surface-v{L}.md`, it does not exist in this version.** Don't invent overloads. Common guards (`Null`, `NullOrEmpty`, `NullOrWhiteSpace`, `OutOfRange`, `Negative`, `NegativeOrZero`, `Zero`, `Default`, `InvalidInput`, `InvalidFormat`) have shifted between majors — verify each one against the surface before referencing it.

## Step 3 — write or review the code

Generate code that uses **only** guards listed in the loaded `api-surface-v{L}.md`. Guard clauses are line-level, so most "code" the user wants is a single constructor or a 5-line method opening with a sequence of guards before the real logic.

If the user is reviewing existing code:
- Flag any `Guard.Against.X(...)` call where `X` isn't in the surface (probably a typo, wrong version, or a custom extension method that should be defined locally)
- Flag guards that pass a string literal instead of `nameof(arg)` for the second argument — the exception's `ParamName` will be wrong
- Flag guard usage inside hot loops or inside `HandleAsync`-style request handlers where validation should be done with FluentValidation / model binding instead (guards throw; bad UX for user-facing input)

If the `patterns-v{L}.md` or `examples-v{L}.md` files are missing (no `ANTHROPIC_API_KEY` available when running the generator), use `api-surface-v{L}.md` directly as the reference.

## Migration questions

If the user is upgrading across majors or minors, read **`reference/migration-notes.md`** — GitHub release notes grouped by major. The v3 → v4 → v5 transitions in particular changed which extension methods are available, the parameter order conventions, and the default exception types.

## When the user reports the generated code doesn't compile

The first suspect is stale or mismatched reference data. Run:
```bash
python <skill-dir>/scripts/update_skill.py
```
…then re-pick the closest matching `api-surface-v{L}.md`. The update script is **version-aware**: it reads each tracked minor's recorded patch, compares to NuGet's latest, and only refreshes when the patch moved or LLM files are missing. It auto-adds NEWER minors in already-tracked majors AND NEWER majors entirely (so v5.1.0 and v6.0.0 both land automatically when NuGet ships them). Forward-only — OLDER versions you never tracked require manual addition.

The second suspect is the user's code defining a CUSTOM extension method on `IGuardClause` that isn't in the package — those won't be in the api-surface. If a method like `Guard.Against.InvalidEmail(...)` doesn't exist in the surface, ask the user where it's defined locally before assuming it's a library method.

## What this skill will NOT do

- It will not write code for unrelated Ardalis libraries (`Ardalis.Specification`, `Ardalis.Result`, `Ardalis.SmartEnum`, `Ardalis.ApiEndpoints`). Each has its own skill.
- It will not impose guard clauses everywhere. Use them at API boundaries (public constructors, factories, public service methods); skip them inside hot loops or inside request handlers where validation should be input-validator-based instead.
- It will not pick a version for the user. For a fresh project, recommend the latest tracked version.

## File map (relative to this `SKILL.md`)

```
SKILL.md                              ← you are here
VERSIONS                              ← accumulating ledger; every tracked version on its own line
skill.config.json                     ← per-library configuration (package id, repo)
prompts/
  examples.system.md                  ← examples-prompt body (grounding rules prepended at runtime)
  patterns.system.md                  ← patterns-prompt body (same)
reference/
  api-surface-v5.0.0.md               ← v5.0.0 allowed guards — extracted from .nupkg XML docs
  examples-v5.0.0.md                  ← v5.0.0 examples — LLM-generated, grounded
  patterns-v5.0.0.md                  ← v5.0.0 patterns — LLM-generated, grounded
  migration-notes.md                  ← release notes by major — fetched from GitHub Releases
```

No `scripts/` folder. Version detection happens inline in Step 1 of this workflow using Claude's `Glob`/`Read` tools — no per-skill script needed. The maintenance updater lives at the repo root in `tools/update_skill.py` and is only used when refreshing the skill from upstream; users who install this skill don't need it.

### What's generated by code vs. by Claude

- `api-surface-v*.md` and `migration-notes.md` are **deterministic** — extracted from the NuGet package's XML doc comments and the GitHub Releases API. They never contain anything Claude made up.
- `examples-v*.md` and `patterns-v*.md` are **LLM-generated** by `update_skill.py`. Each file is grounded in a single version's api-surface, so a guard that doesn't exist in v4 can't sneak into v4 patterns/examples.
