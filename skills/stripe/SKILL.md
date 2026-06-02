---
name: stripe
description: Write, review, or migrate C# code that uses the Stripe.net NuGet package — the official Stripe SDK for .NET. Covers creating and confirming PaymentIntents, managing Customers/PaymentMethods/SetupIntents, Subscriptions and Invoices, Checkout Sessions, Refunds, Payouts, and verifying webhook signatures with EventUtility.ConstructEvent. Use whenever a project imports Stripe.net, when the user asks about "Stripe", "PaymentIntent", "Checkout Session", "Stripe webhook", "StripeClient", "charge a card", "create a subscription", or when migrating between Stripe.net major versions (which track Stripe's dated API versions and bump roughly monthly). This skill is version-aware: it detects which exact version the project pins (e.g. 51.2.0) and loads the reference files generated against that specific version, never recommending a service, option property, or entity field that doesn't exist in the project's version.
---

# Stripe.net — version-aware skill

You are helping the user write or review C# code that uses the **Stripe.net** NuGet package, the official Stripe SDK for .NET. Stripe.net is **very large** (~17,000 documented members across ~165 service classes), it is **machine-generated from Stripe's OpenAPI spec**, and its **major version tracks Stripe's dated API version** — so `Stripe.net` bumps its MAJOR roughly monthly and option/entity shapes shift between majors. Recommending a property that doesn't exist in the project's pinned version is the single most common failure mode. **Detect the version before writing code, and load the closest-matching reference files.**

Because the surface is too large to dump in full, this skill's `api-surface-v{V}.md` is **two-tier**:
- **Service index** — every API service (`PaymentIntentService`, `Checkout.SessionService`, …) and its operation names. If a service or operation isn't in the index, it doesn't exist in that version.
- **Core resource detail** — full property/option listings for the high-traffic resources (PaymentIntent, Customer, Subscription, Invoice, Checkout.Session, Refund, …). Treat these as authoritative for those resources.

## Step 1 — detect the project's full version (always first)

Resolve the full `MAJOR.MINOR.PATCH` in this priority order. **Stop at the first match.**

**Package name that signals "this is a Stripe.net project":**
- `Stripe.net` (single-package SDK; note the lowercase `.net` suffix)

**Detection priority:**

1. **User stated it.** "We're on 51.2.0", etc.
2. **A project file is visible in the conversation.** Parse the full `Version=` attribute on the first `<PackageReference>` / `<PackageVersion>` whose `Include` is `Stripe.net`.
3. **Filesystem access is available.** Search the user's project directory yourself:
   - `Glob` for `**/*.csproj`, `**/Directory.Packages.props`, and `**/Directory.Build.props` (skip `bin/`, `obj/`, `node_modules/`, `.git/`, `.vs/`).
   - `Read` each match and look for `<PackageReference Include="Stripe.net" ...>`.
   - If nothing matches locally, walk up parent directories.
   - Skip MSBuild property references like `$(StripeNetVersion)`.
4. **Still unknown.** Ask the user **once**: "What exact version of Stripe.net does this project use? (e.g. 51.2.0, 48.4.0)" Don't guess — the API surface differs meaningfully between majors.

If `<skill-dir>` is unclear, it's the directory containing this `SKILL.md`.

## Step 2 — pick the closest matching reference files

You have the project's full version `V = MAJOR.MINOR.PATCH`. The skill ships one trio of reference files per tracked minor (latest patch in that minor) plus historical patch files. Find the best match in this **priority order**:

1. **Exact full match** — `reference/api-surface-v{V}.md` exists → use it.
2. **Same minor, highest patch** in `reference/` → use that. Patches don't change the API surface.
3. **Same major, highest minor ≤ project's minor** in `reference/` → fall back. **Never fall back to a HIGHER minor.**
4. **No safe match found** → tell the user explicitly. Because Stripe.net majors track dated Stripe API versions, using a different major's surface is risky: option properties get added, renamed, and removed between majors. Say: "Your project is on v48.x but this skill only has reference data for v51.2.0. Either upgrade, or add v48.x to `VERSIONS` and rerun `update_skill.py`." Do **not** generate code from a different major's surface.

Once matched, load **all three** files: `api-surface-v{L}.md` (two-tier service index + core detail), `patterns-v{L}.md` (idempotency, async, money/amount handling, error handling, webhook verification, test vs. live keys), `examples-v{L}.md` (canonical flows: create+confirm a PaymentIntent, save a card with SetupIntent, create a Customer, start a Subscription, build a Checkout Session, issue a Refund, verify a webhook).

## Step 3 — write or review the code

Generate code using **only** what the loaded `api-surface-v{L}.md` confirms:

- **Service entry points** come from the service index. A service has both sync and `…Async` overloads — prefer `…Async` in modern code (`await service.CreateAsync(options)`).
- **Option/entity properties** for a CORE resource must appear in that resource's detail section. If you want a property that isn't listed for a core resource, it doesn't exist in this version — don't invent it.
- **Option properties for a resource that's only in the index** (not in core detail): the option class follows the `{Resource}{Operation}Options` convention (e.g. `RefundCreateOptions`, `PayoutCreateOptions`). You may use the well-known fields, but flag to the user that the exact shape wasn't loaded and they should confirm against Stripe's API reference for their version.

Cornerstone idioms to verify before referencing:

- **Client setup:** modern `var client = new StripeClient(apiKey);` then a service `new PaymentIntentService(client)`, OR the global `StripeConfiguration.ApiKey = "sk_test_...";` then `new PaymentIntentService()`. Check the surface for which constructors exist.
- **Create + confirm a payment:** `new PaymentIntentService().CreateAsync(new PaymentIntentCreateOptions { Amount = 2000, Currency = "usd", ... })`. **Amounts are in the smallest currency unit** (cents) as `long` — `2000` = $20.00.
- **Webhook verification:** `EventUtility.ConstructEvent(json, signatureHeader, webhookSecret)` — never trust an `Event` deserialized without signature verification.
- **Idempotency:** pass a `RequestOptions { IdempotencyKey = ... }` on create calls that must not double-charge on retry.
- **Pagination:** list calls return `StripeList<T>`; use `service.ListAutoPagingAsync(...)` to iterate beyond one page when the surface exposes it.
- **Expansion:** related objects are IDs by default; request nested objects via the `Expand` option (e.g. `Expand = new List<string> { "customer" }`).

If reviewing existing code:
- Flag any option/entity property not present in the core detail (likely removed/renamed in this major, or a different major's field).
- Flag amounts written as decimals/dollars (`19.99m`) where Stripe expects integer minor units (`1999`).
- Flag webhook handlers that deserialize the body to `Event` directly instead of `EventUtility.ConstructEvent(...)` with the signing secret.
- Flag a live key (`sk_live_…`) hardcoded in source, or any secret key committed rather than read from configuration/secrets.
- Flag create calls in retry-prone paths (HTTP handlers, queue consumers) without an `IdempotencyKey`.
- Flag synchronous service calls (`service.Create(...)`) in async request pipelines — prefer `await service.CreateAsync(...)`.

If the `patterns-v{L}.md` or `examples-v{L}.md` files are missing (no `ANTHROPIC_API_KEY` available when running the generator), use `api-surface-v{L}.md` directly as the reference.

## Migration questions

Stripe.net majors track Stripe's dated API versions, so cross-major upgrades can rename or remove option/entity properties. Read **`reference/migration-notes.md`** (GitHub release notes grouped by major). When upgrading, the safest path is: bump one major at a time, re-pin `VERSIONS`, regenerate, and re-check each option property your code sets against the new major's core detail.

## When the user reports the generated code doesn't compile

The first suspect is stale or mismatched reference data. Re-run the maintenance script:
```bash
python tools/update_skill.py stripe
```

The second suspect is the closest-match fallback firing across majors. If the project is on v48 but only v51 reference data exists, do NOT use v51's surface — properties differ. Add the project's major to `VERSIONS` and rerun.

The third suspect is a property that lives on a resource the skill only indexed (not detailed). The service/operation is real, but the exact option property wasn't loaded into context. Point the user at Stripe's API reference for their version, or add that resource to `core_resources` in `skill.config.json` and rerun to pull its full detail.

## What this skill will NOT do

- It will not handle Stripe's other SDKs (stripe-node, stripe-python, stripe-php, Stripe.js) — only the .NET `Stripe.net` package.
- It will not pick a Stripe API version / `Stripe.net` major for the user. For a fresh project, recommend the latest tracked version.
- It will not invent option properties. If a field isn't in the loaded surface for a core resource, it doesn't exist in that version.
- It will not put secret keys in source. It always reads them from configuration / environment / a secrets store.

## File map (relative to this `SKILL.md`)

```
SKILL.md                              ← you are here
VERSIONS                              ← accumulating ledger; every tracked version on its own line
skill.config.json                     ← per-library config (package id, repo, two-tier surface settings)
prompts/
  examples.system.md                  ← examples-prompt body (grounding rules prepended at runtime)
  patterns.system.md                  ← patterns-prompt body (same)
reference/
  api-surface-v51.2.0.md              ← v51.2.0 two-tier surface (service index + core detail) — from .nupkg XML docs
  examples-v51.2.0.md                 ← v51.2.0 examples — LLM-generated, grounded
  patterns-v51.2.0.md                 ← v51.2.0 patterns — LLM-generated, grounded
  migration-notes.md                  ← release notes by major — fetched from GitHub Releases
```

No `scripts/` folder. Version detection happens inline in Step 1 of this workflow using Claude's `Glob`/`Read` tools — no per-skill script needed. The maintenance updater lives at the repo root in `tools/update_skill.py` and is only used when refreshing the skill from upstream; users who install this skill don't need it.

### What's generated by code vs. by Claude

- `api-surface-v*.md` and `migration-notes.md` are **deterministic** — extracted from the NuGet package's XML doc comments and the GitHub Releases API. They never contain anything Claude made up. The api-surface is rendered in **two-tier** mode (configured in `skill.config.json`): a name-only index of all services plus full detail for the `core_resources` list.
- `examples-v*.md` and `patterns-v*.md` are **LLM-generated** by `update_skill.py`, grounded in that version's two-tier surface so a property that doesn't exist in v51 can't sneak into v51 examples.
