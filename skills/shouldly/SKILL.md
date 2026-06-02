---
name: shouldly
description: Write, review, or migrate test code that uses the Shouldly NuGet package — an assertion library that replaces `Assert.AreEqual(expected, actual)` style with fluent `actual.ShouldBe(expected)` calls. Shouldly's failure messages are richer than xunit/MSTest defaults (they show the actual value, the source expression, and the call site). Use whenever a project imports Shouldly, when the user asks for "Should assertions", "ShouldBe", "ShouldThrow", "ShouldContain", or when migrating between versions. This skill is version-aware: it detects which exact version the project pins (e.g. 4.3.0) and loads the reference files generated against that specific version, never recommending a Should* extension that doesn't exist in the project's version.
---

# Shouldly — version-aware skill

You are helping the user write or review C# test code that uses the **Shouldly** NuGet package. Shouldly provides fluent `Should*()` extension methods on every type: `value.ShouldBe(expected)`, `list.ShouldContain(item)`, `action.ShouldThrow<ArgumentException>()`. Its strength is **failure messages** — instead of "expected `True` but was `False`", Shouldly reports "`result.IsValid` should be `True` but was `False`", reading the source expression off the call site. **Detect the version before writing code, and load the closest-matching reference files.**

## Step 1 — detect the project's full version (always first)

Resolve the full `MAJOR.MINOR.PATCH` in this priority order. **Stop at the first match.**

**Package name that signals "this is a Shouldly project":**
- `Shouldly` (single-package family)

**Detection priority:**

1. **User stated it.** "We're on 4.3.0", etc.
2. **A project file is visible in the conversation.** Parse the full `Version=` attribute on the first `<PackageReference>` / `<PackageVersion>` whose `Include` is `Shouldly`. Note Shouldly is conventionally referenced in `.Tests.csproj` files, not the main project.
3. **Filesystem access is available.** Search the user's project directory yourself:
   - `Glob` for `**/*.csproj`, `**/Directory.Packages.props`, and `**/Directory.Build.props` (skip `bin/`, `obj/`, `node_modules/`, `.git/`, `.vs/`).
   - `Read` each match and look for `<PackageReference Include="Shouldly" ...>`. Test projects (`*.Tests.csproj`, `*.UnitTests.csproj`) are the most likely match.
   - If nothing matches locally, walk up parent directories.
   - Skip MSBuild property references like `$(ShouldlyVersion)`.
4. **Still unknown.** Ask the user **once**: "What exact version of Shouldly does this project use? (e.g. 4.3.0, 4.2.1)" Don't guess.

If `<skill-dir>` is unclear, it's the directory containing this `SKILL.md`.

## Step 2 — pick the closest matching reference files

You have the project's full version `V = MAJOR.MINOR.PATCH`. The skill ships one trio of reference files per tracked minor (latest patch in that minor) plus historical patch files. Find the best match in this **priority order**:

1. **Exact full match** — `reference/api-surface-v{V}.md` exists → use it.
2. **Same minor, highest patch** in `reference/` → use that. Patches don't add public API.
3. **Same major, highest minor ≤ project's minor** in `reference/` → fall back. **Never fall back to a HIGHER minor.** Shouldly added new `Should*` extensions across v4.x minors — using v4.3 references for a v4.0 project would recommend extensions that don't exist there.
4. **No safe match found** → tell the user: "Your project is on v3.0.0 but this skill only has reference data for v4.3.0. Either upgrade, or add v3.0.0 to `VERSIONS` and rerun `update_skill.py`."

Once matched, load **all three** files: `api-surface-v{L}.md` (every `Should*` extension and overload available), `patterns-v{L}.md` (when to use Shouldly vs raw xunit Assert / FluentAssertions, one-assertion-per-test conventions, customMessage usage), `examples-v{L}.md` (canonical assertion patterns: equality, collections, exceptions, async, "new in v{MAJOR.MINOR}" highlight).

**The rule: if a `Should*` extension doesn't appear in `api-surface-v{L}.md`, it does not exist in this version.** Some extensions are version-specific (e.g. `ShouldBeOrderedByDescending` may not exist in older majors; `ShouldHaveSingleItem` is newer).

## Step 3 — write or review the code

Generate test code using **only** members listed in the loaded `api-surface-v{L}.md`. The most common entry points to verify before referencing:

- `value.ShouldBe(expected)` — value equality
- `value.ShouldNotBe(notExpected)` — value inequality
- `value.ShouldBeNull()` / `ShouldNotBeNull()`
- `bool.ShouldBeTrue()` / `ShouldBeFalse()`
- `collection.ShouldContain(item)` / `ShouldNotContain` / `ShouldBeEmpty` / `ShouldNotBeEmpty`
- `string.ShouldStartWith` / `ShouldEndWith` / `ShouldContain`
- `Should.Throw<TException>(() => action)` — exception assertions (static)
- `Should.ThrowAsync<TException>(async () => await action)` — async exception assertions
- `value.ShouldBeOfType<T>()` — type assertions

If reviewing existing code:
- Flag any `Should*` extension where the exact overload (taking `customMessage`, taking `tolerance`, etc.) isn't in the surface
- Flag any `Assert.X(...)` calls in a Shouldly-using test class — those should usually be Shouldly equivalents for consistency
- Flag bare `Assert.True(condition)` where Shouldly's `condition.ShouldBeTrue()` would give a better failure message
- Flag use of `Shouldly.ShouldlyConfiguration` overrides without a clear comment explaining why

## Migration questions

For v3.x → v4.x transitions, read **`reference/migration-notes.md`**. The v3 → v4 jump removed some legacy extensions and changed exception throw-helper signatures.

## When the user reports the generated code doesn't compile

The first suspect is stale reference data. Re-run the maintenance script:
```bash
python tools/update_skill.py shouldly
```

The second suspect is the closest-match fallback. If `detect_version` returned `3.0.2` but the skill only has files for `4.x`, do NOT use 4.x files for a v3 project — Shouldly v4 removed several v3 extensions. Add v3.0.2 to `VERSIONS` and rerun.

The third suspect is a missing custom-message overload. Several Shouldly extensions overload as `ShouldBe(expected)` AND `ShouldBe(expected, customMessage)`. Always check the surface for the overload the user is calling — the customMessage variant might be available in some versions and not others.

## What this skill will NOT do

- It will not generate test framework setup (xunit, MSTest, NUnit configuration) — those have their own conventions; the skill focuses on the assertion layer.
- It will not convert FluentAssertions code to Shouldly unless explicitly asked. Suggest the swap; don't impose it.
- It will not pick a version for the user. For a fresh test project, recommend the latest tracked version.

## File map (relative to this `SKILL.md`)

```
SKILL.md                              ← you are here
VERSIONS                              ← accumulating ledger; every tracked version on its own line
skill.config.json                     ← per-library configuration (package id, repo)
prompts/
  examples.system.md                  ← examples-prompt body (grounding rules prepended at runtime)
  patterns.system.md                  ← patterns-prompt body (same)
reference/
  api-surface-v4.3.0.md               ← v4.3.0 allowed Should* extensions — extracted from .nupkg XML docs
  examples-v4.3.0.md                  ← v4.3.0 examples — LLM-generated, grounded
  patterns-v4.3.0.md                  ← v4.3.0 patterns — LLM-generated, grounded
  migration-notes.md                  ← release notes by major — fetched from GitHub Releases
```

No `scripts/` folder. Version detection happens inline in Step 1 of this workflow using Claude's `Glob`/`Read` tools — no per-skill script needed. The maintenance updater lives at the repo root in `tools/update_skill.py` and is only used when refreshing the skill from upstream; users who install this skill don't need it.
