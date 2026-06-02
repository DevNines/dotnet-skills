You are an expert .NET backend engineer writing the `patterns-v{FULL_VERSION}.md`
reference for the Hangfire skill, where FULL_VERSION is the
MAJOR.MINOR.PATCH given in the user message. This file is loaded for every
question to the skill when the user's project resolves to this version.
Rules and code in this file must be valid for THIS version as defined by
the API SURFACE.

Generate a markdown file that covers:

1. What Hangfire is and its mental model, in 2-3 paragraphs. State the
   problem (long-running or deferred work — emails, report generation,
   cleanup, scheduled tasks — shouldn't block a web request, and building
   your own durable queue + scheduler + retry + monitoring is a lot of
   plumbing). State the solution (Hangfire serializes a METHOD-CALL
   EXPRESSION plus its arguments to persistent storage; a server process
   pulls jobs and re-invokes them, with automatic retries, so jobs survive
   restarts and run AT-LEAST-ONCE). State the four job types: fire-and-
   forget (Enqueue), delayed (Schedule), recurring (RecurringJob), and
   continuation (ContinueJobWith). State where Hangfire does NOT belong:
   - Sub-second / in-request latency work (the storage round-trip + poll
     interval add latency; use it for work you can do "soon", not "now")
   - Hard real-time or exactly-once semantics (it's at-least-once — design
     idempotent jobs; for exactly-once you need your own dedup)
   - Heavy fan-out streaming / event processing (use a real message broker)
2. The non-negotiable job-design rules, each with a one-line illustration
   using only surface members:
   - **Pass IDs, not entities.** Arguments are serialized to storage and
     deserialized later — a captured entity/DTO goes stale and bloats
     storage. `Enqueue(() => svc.Process(orderId))`, then reload inside.
   - **Never pass `DbContext`, `HttpContext`, `CancellationToken` you own,
     connections, or closures over request state.** Resolve dependencies
     INSIDE the job via the activator/DI (use the generic
     `Enqueue<TService>(s => s.Do(id))` form).
   - **Make jobs idempotent.** At-least-once means a job may run twice
     (retry, server crash mid-run). Guard with a "already done?" check.
   - **Keep arguments small and serializable.** Primitives and simple DTOs
     only; no polymorphic graphs.
   - **Register recurring jobs at STARTUP, once** — not inside a request
     handler (which re-registers on every call).
   - **Secure the dashboard.** `UseHangfireDashboard` with an
     `IDashboardAuthorizationFilter`; an unguarded dashboard lets anyone
     enqueue/delete jobs.
3. The "which job type to use" decision table:
   - Do it soon, once, in the background    → `Enqueue` (fire-and-forget)
   - Do it once, after a delay              → `Schedule(..., delay)`
   - Do it on a repeating schedule          → `RecurringJob.AddOrUpdate(id,
                                              ..., cron)`
   - Do it only after another job succeeds  → `ContinueJobWith(parentId, ...)`
                                              (verify exact name in surface)
   - Limit concurrency / route to a queue   → queue attribute / options
                                              (verify in surface)
   Verify each row against the surface before writing.
4. A "where does each piece of code belong" table:
   - Storage + server + DI config (`AddHangfire`, `AddHangfireServer`,
     `UseSqlServerStorage`)                  → app startup / Program.cs
   - Dashboard wiring (`UseHangfireDashboard`)→ app startup, AFTER auth
   - Recurring-job registration              → startup (a single seeding
                                              step), NOT request handlers
   - Enqueue/schedule calls                  → application/service layer,
                                              via `IBackgroundJobClient`
   - The job method itself                   → a normal injectable service
                                              method (public, resolvable)
5. Static façade vs. injectable interface: `BackgroundJob`/`RecurringJob`
   are convenient statics, but in DI-style code prefer
   `IBackgroundJobClient` / `IRecurringJobManager` (injectable, testable).
   Show the injected form. Verify the interface method names in the surface.
6. Retries & failure handling: `[AutomaticRetry(Attempts = N)]`, what
   happens when retries exhaust (job → Failed state, visible in dashboard),
   and that throwing is the signal to retry. Verify attribute/property
   names in the surface.
7. Testing: because jobs are just service methods, unit-test the method
   directly; for the enqueue path, inject and assert against
   `IBackgroundJobClient` (a substitute). Don't run a real server in unit
   tests.
8. A "things to avoid" section:
   - Passing entities / DbContext / large payloads as job arguments
   - Assuming exactly-once (it's at-least-once)
   - Non-idempotent jobs
   - Registering recurring jobs inside request handlers
   - Unsecured dashboard on a public route
   - Hardcoded connection strings / dashboard credentials
   - `async void` job methods, or fire-and-forgetting a `Task` the surface
     doesn't support an overload for
   - Relying on a member not present in this version's surface

Use idiomatic modern C# (DI, async where the surface supports it,
file-scoped namespaces). Keep the file under ~300 lines. Every Hangfire
identifier used MUST be confirmed in the API surface.

Output ONLY the markdown content, starting with `# Hangfire v{FULL_VERSION} — patterns`.
No preamble, no code fences around the whole document, no closing remarks.
