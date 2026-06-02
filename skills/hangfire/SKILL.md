---
name: hangfire
description: Write, review, or migrate C# code that uses the Hangfire NuGet package family (Hangfire.Core + Hangfire.SqlServer + Hangfire.AspNetCore + Hangfire.NetCore) — a background-job framework for .NET that runs fire-and-forget, delayed, recurring, and continuation jobs backed by persistent storage (SQL Server, etc.), with no Windows Service or separate process required. Use whenever a project imports any Hangfire package, when the user asks about "Hangfire", "background job", "BackgroundJob.Enqueue", "RecurringJob.AddOrUpdate", "fire and forget", "delayed job", "the Hangfire dashboard", "AddHangfire", "UseHangfireServer", or when migrating between versions. This skill is version-aware: it detects which exact version the project pins (e.g. 1.8.23) and loads the reference files generated against that specific version, never recommending a member that doesn't exist in the project's version.
---

# Hangfire — version-aware skill

You are helping the user write or review C# code that uses the **Hangfire** background-job framework. Hangfire lets you offload work to a background thread/process without building your own queue or scheduler: `BackgroundJob.Enqueue(() => Console.WriteLine("hi"))` runs a method out-of-band; `BackgroundJob.Schedule(() => DoIt(), TimeSpan.FromHours(1))` delays it; `RecurringJob.AddOrUpdate("report", () => SendReport(), Cron.Daily())` runs it on a cron schedule. Jobs are serialized to **persistent storage** (most commonly SQL Server via `Hangfire.SqlServer`) and picked up by a **server** (`UseHangfireServer` / `AddHangfireServer`), so they survive process restarts and run at-least-once. A built-in **dashboard** (`UseHangfireDashboard`) shows job state. **Detect the version before writing code, and load the closest-matching reference files.**

The skill's surface spans several packages:
- **Hangfire.Core** — the API you call: `BackgroundJob`, `RecurringJob`, `IBackgroundJobClient`, `IRecurringJobManager`, `Cron`, `GlobalConfiguration`, `[AutomaticRetry]`, `IJobFilter`, `JobStorage`, dashboard authorization, etc.
- **Hangfire.SqlServer** — `UseSqlServerStorage(...)` and `SqlServerStorageOptions`.
- **Hangfire.NetCore** — DI setup: `AddHangfire(...)`, `AddHangfireServer(...)` on `IServiceCollection`.
- **Hangfire.AspNetCore** — app wiring: `UseHangfireDashboard(...)`, `UseHangfireServer(...)`, `MapHangfireDashboard(...)`.

## Step 1 — detect the project's full version (always first)

Resolve the full `MAJOR.MINOR.PATCH` in this priority order. **Stop at the first match.**

**Package names that signal "this is a Hangfire project":**
- `Hangfire` (meta-package; pulls in Core + SqlServer + AspNetCore)
- `Hangfire.Core` (the API itself)
- `Hangfire.AspNetCore`, `Hangfire.NetCore` (host/DI integration)
- `Hangfire.SqlServer` (storage)

All Hangfire.* packages version in lockstep, so any of them gives the version.

**Detection priority:**

1. **User stated it.** "We're on 1.8.23", etc.
2. **A project file is visible in the conversation.** Parse the full `Version=` attribute on the first `<PackageReference>` / `<PackageVersion>` whose `Include` is one of the package names above.
3. **Filesystem access is available.** Search the user's project directory yourself:
   - `Glob` for `**/*.csproj`, `**/Directory.Packages.props`, and `**/Directory.Build.props` (skip `bin/`, `obj/`, `node_modules/`, `.git/`, `.vs/`).
   - `Read` each match and look for `<PackageReference Include="Hangfire..." ...>`.
   - If nothing matches locally, walk up parent directories.
   - Skip MSBuild property references like `$(HangfireVersion)`.
4. **Still unknown.** Ask the user **once**: "What exact version of Hangfire does this project use? (e.g. 1.8.23, 1.7.37)" Don't guess.

If `<skill-dir>` is unclear, it's the directory containing this `SKILL.md`.

## Step 2 — pick the closest matching reference files

You have the project's full version `V = MAJOR.MINOR.PATCH`. The skill ships one trio of reference files per tracked minor (latest patch in that minor) plus historical patch files. Find the best match in this **priority order**:

1. **Exact full match** — `reference/api-surface-v{V}.md` exists → use it.
2. **Same minor, highest patch** in `reference/` → use that. Patches don't add public API.
3. **Same major, highest minor ≤ project's minor** in `reference/` → fall back. **Never fall back to a HIGHER minor.** Hangfire added members across 1.7 → 1.8 (e.g. recurring-job options, time-zone handling); using 1.8 references for a 1.7 project would recommend members that don't exist there.
4. **No safe match found** → tell the user: "Your project is on v1.7.x but this skill only has reference data for v1.8.23. Either upgrade, or add v1.7.x to `VERSIONS` and rerun `update_skill.py`."

Once matched, load **all three** files: `api-surface-v{L}.md` (every Hangfire member available across the tracked packages), `patterns-v{L}.md` (job-design rules: keep arguments small & serializable, make jobs idempotent, pass IDs not entities, when to use which job type), `examples-v{L}.md` (canonical snippets: enqueue, schedule, recurring, continuations, DI setup, storage config, dashboard).

**The rule: if a member doesn't appear in `api-surface-v{L}.md`, it does not exist in this version.** Note the static façades (`BackgroundJob`, `RecurringJob`) vs. their injectable interfaces (`IBackgroundJobClient`, `IRecurringJobManager`) — prefer the interfaces in DI code; verify the exact method overloads in the surface.

## Step 3 — write or review the code

Generate code using **only** members listed in the loaded `api-surface-v{L}.md`. Cornerstone idioms to verify before referencing:

- **Fire-and-forget:** `BackgroundJob.Enqueue(() => service.Process(id))` or, injected, `_client.Enqueue<IMyService>(s => s.Process(id))`
- **Delayed:** `BackgroundJob.Schedule(() => service.Process(id), TimeSpan.FromMinutes(30))`
- **Recurring:** `RecurringJob.AddOrUpdate("job-id", () => service.Run(), Cron.Daily)` (verify whether `Cron.Daily` is a property or `Cron.Daily()` a method in this version)
- **Continuation:** `BackgroundJob.ContinueJobWith(parentId, () => service.After())` (verify the exact name — `ContinueJobWith` vs `ContinueWith`)
- **DI registration:** `services.AddHangfire(cfg => cfg.UseSqlServerStorage(connString))` then `services.AddHangfireServer()`
- **App wiring:** `app.UseHangfireDashboard("/hangfire")` and (older host style) `app.UseHangfireServer()`
- **Retry control:** `[AutomaticRetry(Attempts = 3)]` on the job method
- **Storage options:** `new SqlServerStorageOptions { ... }` passed to `UseSqlServerStorage`

The expression-based API is the heart of Hangfire: you pass a **method-call expression** (`() => service.Process(id)`), not a delegate. Hangfire serializes the method + arguments to storage and re-invokes it later (resolving the target from the job activator / DI). This is why arguments must be simple and serializable.

If reviewing existing code:
- Flag jobs that capture or pass **entities / large objects / `DbContext` / `HttpContext`** as arguments — pass an **ID** and reload inside the job. Captured state is serialized and goes stale.
- Flag **non-idempotent** jobs — Hangfire guarantees at-least-once, so a job can run more than once; design for it.
- Flag `BackgroundJob.Enqueue(() => SomeAsyncMethod())` where the async method's `Task` is discarded incorrectly — verify the surface supports the async-returning overload before relying on it.
- Flag a dashboard exposed without authorization (`UseHangfireDashboard` with no `IDashboardAuthorizationFilter`) on a public endpoint — it lets anyone trigger/delete jobs.
- Flag a recurring job registered inside a request handler (it re-registers on every request) instead of at startup.
- Flag a connection string or storage secret hardcoded in source rather than read from configuration.

If the `patterns-v{L}.md` or `examples-v{L}.md` files are missing (no `ANTHROPIC_API_KEY` available when running the generator), use `api-surface-v{L}.md` directly as the reference.

## Migration questions

For 1.7.x → 1.8.x transitions, read **`reference/migration-notes.md`** (GitHub release notes by major). The 1.8 line changed recurring-job scheduling/time-zone handling, added options objects to several methods, and adjusted the ASP.NET Core integration. Verify each method's current overloads against the matched api-surface.

## When the user reports the generated code doesn't compile

The first suspect is stale or mismatched reference data. Re-run the maintenance script:
```bash
python tools/update_skill.py hangfire
```

The second suspect is the closest-match fallback across minors. If the project is on 1.7 but only 1.8 data exists, do NOT use 1.8's surface — add 1.7.x to `VERSIONS` and rerun.

The third suspect is a missing-package member: the setup methods (`AddHangfire`, `AddHangfireServer`, `UseHangfireDashboard`, `UseHangfireServer`, `MapHangfireDashboard`) live in `Hangfire.NetCore` / `Hangfire.AspNetCore`, and `UseSqlServerStorage` in `Hangfire.SqlServer`. If the user only references `Hangfire.Core`, those methods won't resolve — they need the matching package installed.

## What this skill will NOT do

- It will not configure storage providers other than SQL Server in detail (Redis, PostgreSQL, etc. are third-party packages with their own surfaces) — though it can describe the generic `IStorageConnection` / `JobStorage` shape from Core.
- It will not pick a version for the user. For a fresh project, recommend the latest tracked version.
- It will not invent overloads. If a method signature isn't in the loaded surface, it doesn't exist in that version.
- It will not hardcode connection strings or dashboard credentials in source.

## File map (relative to this `SKILL.md`)

```
SKILL.md                              ← you are here
VERSIONS                              ← accumulating ledger; every tracked version on its own line
skill.config.json                     ← per-library configuration (package id, repo, siblings, source fallback)
prompts/
  examples.system.md                  ← examples-prompt body (grounding rules prepended at runtime)
  patterns.system.md                  ← patterns-prompt body (same)
reference/
  api-surface-v1.8.23.md              ← v1.8.23 allowed members — from .nupkg XML docs + source-parsed setup methods
  examples-v1.8.23.md                 ← v1.8.23 examples — LLM-generated, grounded
  patterns-v1.8.23.md                 ← v1.8.23 patterns — LLM-generated, grounded
  migration-notes.md                  ← release notes by major — fetched from GitHub Releases
```

No `scripts/` folder. Version detection happens inline in Step 1 of this workflow using Claude's `Glob`/`Read` tools — no per-skill script needed. The maintenance updater lives at the repo root in `tools/update_skill.py` and is only used when refreshing the skill from upstream; users who install this skill don't need it.

### What's generated by code vs. by Claude

- `api-surface-v*.md` and `migration-notes.md` are **deterministic** — extracted from the NuGet packages' XML doc comments (Hangfire.Core + Hangfire.SqlServer) and, for the otherwise-undocumented ASP.NET Core / .NET host setup methods, parsed from the GitHub source tree (`Hangfire.AspNetCore` and `Hangfire.NetCore`). They never contain anything Claude made up.
- `examples-v*.md` and `patterns-v*.md` are **LLM-generated** by `update_skill.py`, grounded in a single version's api-surface so a member that doesn't exist in 1.7 can't sneak into 1.7 examples.
