---
name: nsubstitute
description: Write, review, or migrate test code that uses the NSubstitute NuGet package — a friendly mocking library for .NET that replaces verbose `Mock<T>` setup/verify ceremony with the natural-reading `Substitute.For<IFoo>()`, `sub.Bar().Returns(42)`, and `sub.Received().Bar(42)` style. Use whenever a project imports NSubstitute, when the user asks for "NSubstitute", "Substitute.For", "Returns", "Received", "DidNotReceive", "mock with NSubstitute", or when migrating between versions (notably the v4 → v5 transition that dropped older TFMs and changed analyzer behaviour). This skill is version-aware: it detects which exact version the project pins (e.g. 5.3.0) and loads the reference files generated against that specific version, never recommending a method or matcher that doesn't exist in the project's version.
---

# NSubstitute — version-aware skill

You are helping the user write or review C# test code that uses the **NSubstitute** NuGet package. NSubstitute creates test doubles for interfaces (and virtual class members) with a fluent surface: `var sub = Substitute.For<IFoo>()` creates a substitute, `sub.Bar(42).Returns("ok")` stubs a return, `sub.Received().Bar(42)` asserts the call was made. Compared to Moq, NSubstitute deliberately omits `.Setup(x => x.Bar(...))` ceremony — you just call the method on the substitute directly, and what looks like an invocation is actually configuration. This trick relies on extension methods (`Returns`, `Received`, `DidNotReceive`, `ReceivedWithAnyArgs`, etc.) and argument matchers (`Arg.Any<T>()`, `Arg.Is<T>(x => predicate)`). **Detect the version before writing code, and load the closest-matching reference files** — the v4 → v5 transition tightened TFM support and shifted some behaviours.

## Step 1 — detect the project's full version (always first)

Resolve the full `MAJOR.MINOR.PATCH` in this priority order. **Stop at the first match.**

**Package names that signal "this is an NSubstitute project":**
- `NSubstitute` (primary)
- `NSubstitute.Analyzers.CSharp` (sibling — Roslyn analyzer for C# tests)
- `NSubstitute.Analyzers.VisualBasic` (sibling — Roslyn analyzer for VB tests; rare)

The `NSubstitute.Analyzers.*` siblings track their own version line and are usually pinned alongside `NSubstitute`. The version of the core `NSubstitute` package is the one this skill cares about.

**Detection priority:**

1. **User stated it.** "We're on 5.3.0", etc.
2. **A project file is visible in the conversation.** Parse the full `Version=` attribute on the first `<PackageReference>` / `<PackageVersion>` whose `Include` is `NSubstitute`. NSubstitute is conventionally referenced in `.Tests.csproj` files, not the production project.
3. **Filesystem access is available.** Search the user's project directory yourself:
   - `Glob` for `**/*.csproj`, `**/Directory.Packages.props`, and `**/Directory.Build.props` (skip `bin/`, `obj/`, `node_modules/`, `.git/`, `.vs/`).
   - `Read` each match and look for `<PackageReference Include="NSubstitute" ...>`. Test projects (`*.Tests.csproj`, `*.UnitTests.csproj`, `*.IntegrationTests.csproj`) are the most likely match.
   - If nothing matches locally, walk up parent directories.
   - Skip MSBuild property references like `$(NSubstituteVersion)`.
4. **Still unknown.** Ask the user **once**: "What exact version of NSubstitute does this project use? (e.g. 5.3.0, 5.1.0, 4.4.0)" Don't guess.

If `<skill-dir>` is unclear, it's the directory containing this `SKILL.md`.

## Step 2 — pick the closest matching reference files

You have the project's full version `V = MAJOR.MINOR.PATCH`. The skill ships one trio of reference files per tracked minor (latest patch in that minor) plus historical patch files. Find the best match in this **priority order**:

1. **Exact full match** — `reference/api-surface-v{V}.md` exists → use it.
2. **Same minor, highest patch** in `reference/` → use that. Patches don't add public API.
3. **Same major, highest minor ≤ project's minor** in `reference/` → fall back. **Never fall back to a HIGHER minor.** v5 added overloads (and tightened analyzer behaviour around `ref`/`out` arguments) that don't exist in v4; using v5 references for a v4 project would recommend overloads that aren't there.
4. **No safe match found** → tell the user: "Your project is on v4.4.0 but this skill only has reference data for v5.3.0. Either upgrade, or add v4.4.0 to `VERSIONS` and rerun `update_skill.py`."

Once matched, load **all three** files: `api-surface-v{L}.md` (every member of `Substitute`, `SubstituteExtensions`, `Arg`, `Received` and friends), `patterns-v{L}.md` (when to substitute vs. integration-test, single-vs-multi-call assertion conventions, arg-matcher placement rules, common pitfalls), `examples-v{L}.md` (canonical snippets: stubbing returns, throwing, asserting received/not-received, partial substitutes, events, async).

**The rule: if a member doesn't appear in `api-surface-v{L}.md`, it does not exist in this version.** NSubstitute's surface is small but precise — `Received()`, `Received(int)`, `Received(Quantity)`, `ReceivedWithAnyArgs()`, `DidNotReceive()`, `DidNotReceiveWithAnyArgs()` are distinct entry points; an LLM that guesses signatures will pick a `Received(0)` overload that may or may not exist.

## Step 3 — write or review the code

Generate test code using **only** members listed in the loaded `api-surface-v{L}.md`. The cornerstone idioms to verify before referencing:

- **Creating substitutes:** `var sub = Substitute.For<IFoo>()`, `Substitute.For<IFoo, IDisposable>()` (multi-interface), `Substitute.ForPartsOf<Bar>()` (partial substitute — calls real virtual methods unless explicitly stubbed)
- **Stubbing returns:** `sub.Bar(42).Returns("ok")`, `sub.Bar(Arg.Any<int>()).Returns(call => $"got {call.Arg<int>()}")` (callback-style)
- **Throwing:** `sub.Bar(42).Returns(_ => throw new InvalidOperationException())` or, in newer versions, the explicit `Throws<TException>()` extension on `ExceptionExtensions`
- **Arg matchers:** `Arg.Any<T>()`, `Arg.Is<T>(x => x > 0)`, `Arg.Is<T>(expected)`, `Arg.Do<T>(x => captured = x)` (capture side-channel)
- **Asserting calls:** `sub.Received().Bar(42)`, `sub.Received(2).Bar(Arg.Any<int>())`, `sub.DidNotReceive().Bar(99)`, `sub.ReceivedWithAnyArgs().Bar(default)`
- **Async:** stubbing `Task<T>`-returning methods works with the same `Returns` — `sub.GetAsync(1).Returns(Task.FromResult("ok"))` or the cleaner `Returns("ok")` since NSubstitute unwraps `Task<T>`
- **Events:** `sub.SomeEvent += Raise.Event<EventHandler>(sub, EventArgs.Empty)` raises an event on the substitute

If reviewing existing code:
- Flag any `sub.X(...)` followed by `.Returns(...)` where the arg matchers are mixed with concrete values **incorrectly**. The rule: once you use ANY `Arg.Xxx<T>()` matcher in an invocation, EVERY argument in that invocation must also be a matcher (use `Arg.Is<T>(literal)` for literal values).
- Flag `Received()` checks where the previous configured `Returns()` would have already counted as a "received" call from a previous test (substitutes are stateful — `ClearReceivedCalls()` or fresh substitutes per test are the fix).
- Flag use of `Substitute.For<ConcreteClass>()` when the class has non-virtual members the test wants to verify — NSubstitute can only intercept `virtual`/`abstract` members on classes.
- Flag misuse of `ForPartsOf<T>` where the test then re-stubs every virtual method — that defeats the partial-substitute purpose; a plain `For<T>` is clearer.
- Flag `Arg.Is<T>(x => x.SomeProperty == expectedValue)` predicates without a corresponding identity check — predicate matchers don't print the actual value on failure; an explicit equality assertion gives better diagnostics.

If the `patterns-v{L}.md` or `examples-v{L}.md` files are missing (no `ANTHROPIC_API_KEY` available when running the generator), use `api-surface-v{L}.md` directly as the reference.

## Migration questions

For v4.x → v5.x transitions, read **`reference/migration-notes.md`**. The headline changes were dropping older `netstandard` TFMs, requiring `net6.0`/`net8.0` for newer features, and analyzer improvements that surface incorrect `ref`/`out` and "mixing matchers with literals" usage as warnings/errors at compile time.

## When the user reports the generated code doesn't compile

The first suspect is stale reference data. Re-run the maintenance script:
```bash
python tools/update_skill.py nsubstitute
```

The second suspect is the closest-match fallback. If `detect_version` returned `4.4.0` but the skill only has files for `5.x`, do NOT use 5.x files for a v4 project — the analyzer behaviour is stricter in v5 and some patterns valid in v4 will now be flagged.

The third suspect is the `NSubstitute.Analyzers.CSharp` analyzer firing on code that compiles under plain NSubstitute. If the user added `NSubstitute.Analyzers.CSharp` to a project that previously only had `NSubstitute`, "NS1000"-series compile errors can appear on code that the runtime would have happily executed (e.g. setting up a return on a non-virtual method). Either fix the test code or remove the analyzer.

## What this skill will NOT do

- It will not write production code (only test code).
- It will not convert Moq code to NSubstitute unless explicitly asked. Suggest the swap; don't impose it.
- It will not pick a version for the user. For a fresh test project, recommend the latest tracked version.
- It will not generate test framework setup (xunit, MSTest, NUnit configuration) — those have their own conventions; the skill focuses on the substitute/assertion layer.

## File map (relative to this `SKILL.md`)

```
SKILL.md                              ← you are here
VERSIONS                              ← accumulating ledger; every tracked version on its own line
skill.config.json                     ← per-library configuration (package id, repo)
prompts/
  examples.system.md                  ← examples-prompt body (grounding rules prepended at runtime)
  patterns.system.md                  ← patterns-prompt body (same)
reference/
  api-surface-v5.3.0.md               ← v5.3.0 allowed surface — extracted from .nupkg XML docs
  examples-v5.3.0.md                  ← v5.3.0 examples — LLM-generated, grounded
  patterns-v5.3.0.md                  ← v5.3.0 patterns — LLM-generated, grounded
  migration-notes.md                  ← release notes by major — fetched from GitHub Releases
```

No `scripts/` folder. Version detection happens inline in Step 1 of this workflow using Claude's `Glob`/`Read` tools — no per-skill script needed. The maintenance updater lives at the repo root in `tools/update_skill.py` and is only used when refreshing the skill from upstream; users who install this skill don't need it.

### What's generated by code vs. by Claude

- `api-surface-v*.md` and `migration-notes.md` are **deterministic** — extracted from the NuGet package's XML doc comments and the GitHub Releases API. They never contain anything Claude made up.
- `examples-v*.md` and `patterns-v*.md` are **LLM-generated** by `update_skill.py`. Each file is grounded in a single version's api-surface, so a member that doesn't exist in v4 can't sneak into v4 patterns/examples.
