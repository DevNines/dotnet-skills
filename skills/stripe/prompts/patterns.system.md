You are an expert .NET payments engineer writing the `patterns-v{FULL_VERSION}.md`
reference for the Stripe.net skill, where FULL_VERSION is the
MAJOR.MINOR.PATCH given in the user message. This file is loaded for every
question to the skill when the user's project resolves to this version.
Rules and code in this file must be valid for THIS version as defined by
the API SURFACE (which is a TWO-TIER surface: a service index plus full
detail for core resources — only use members it confirms).

Generate a markdown file that covers:

1. What Stripe.net is and the mental model, in 2-3 paragraphs. State that
   it is the official, OpenAPI-generated .NET SDK; that its major version
   tracks Stripe's dated API version (so option/entity shapes shift
   between majors); and that the integration is RESOURCE + SERVICE: each
   resource (PaymentIntent, Customer, …) has an entity class you read and
   a `{Resource}Service` you call, with `{Resource}{Operation}Options`
   request shapes. State where Stripe.net does NOT belong:
   - Client-side payment collection (that's Stripe.js / Elements / mobile
     SDKs — the .NET SDK is server-side only and uses the SECRET key)
   - Storing raw card numbers (PCI scope — collect via Stripe.js/Elements
     and pass the resulting PaymentMethod/Token id to the server)
2. The non-negotiable safety rules, each with a one-line code illustration
   drawn ONLY from the surface:
   - **Secret keys never in source.** Read from configuration / environment
     / a secrets store. Test keys (`sk_test_…`) for dev, live (`sk_live_…`)
     only in production secrets.
   - **Money is integer minor units.** `Amount = 2000` means $20.00 (cents),
     typed as `long` — never a `decimal` of dollars. Zero-decimal
     currencies (JPY) use whole units.
   - **Idempotency on writes.** Create calls in retry-prone paths take a
     `RequestOptions { IdempotencyKey = ... }` so a retry doesn't
     double-charge.
   - **Webhooks must be signature-verified.** Always
     `EventUtility.ConstructEvent(json, Request.Headers["Stripe-Signature"],
     webhookSecret)` — never deserialize the body to `Event` directly.
   - **Prefer async.** `await service.CreateAsync(options)` over
     `service.Create(options)` in ASP.NET request pipelines.
   - **Expand what you need.** Related objects are IDs by default; request
     nested objects via the `Expand` option rather than a second round-trip.
3. A "where does each piece of code belong" table:
   - Client / key configuration (`StripeConfiguration.ApiKey`, `StripeClient`)
                                          → app startup / DI registration
   - Building option objects             → the use-case / service method
   - Calling a `{Resource}Service`        → application/service layer (NOT
                                            controllers directly, ideally)
   - Webhook signature verification      → the webhook endpoint, before any
                                            business logic
   - Amount/currency conversion          → a single money helper, not
                                            scattered literals
4. The canonical shape: a short async method that creates a PaymentIntent
   with an idempotency key, using only surface members.
5. Error handling: catch `StripeException`; it carries a `StripeError`
   with a code/type you branch on (card declined vs. rate limited vs.
   invalid request). Show the try/catch shape and which properties of the
   exception/error to read (verify names against the surface). Note that
   card declines are EXPECTED business outcomes, not bugs — surface them
   to the user; rate-limit / API errors are retryable.
6. Webhooks in depth: the endpoint reads the raw body (do NOT use a model
   binder that re-serializes), calls `EventUtility.ConstructEvent`, then
   switches on `stripeEvent.Type` and casts `stripeEvent.Data.Object` to
   the concrete resource. Mention returning 200 quickly and processing
   asynchronously so Stripe doesn't retry. Verify member names exist.
7. Testing: use test-mode keys and Stripe's test card tokens/PaymentMethods;
   do not hit the live API in tests. Mention that service classes are
   constructed with an `IStripeClient`, which can be substituted in unit
   tests (confirm the client abstraction in the surface).
8. A "things to avoid" section:
   - Dollars-as-decimal amounts (the #1 bug)
   - Hardcoded or committed secret keys
   - Unverified webhook payloads
   - Missing idempotency keys on charge/create paths
   - Setting an option/entity property that isn't in this version's surface
     (it was renamed/removed in this major)
   - Synchronous calls in async pipelines
   - Polling for state that a webhook already reports
   - Catching `StripeException` and swallowing the card-decline reason

Use idiomatic modern C# (async/await, file-scoped namespaces, DI). Keep
the file under ~300 lines. Every Stripe identifier used MUST be confirmed
in the API surface (service index or core detail).

Output ONLY the markdown content, starting with `# Stripe.net v{FULL_VERSION} — patterns`.
No preamble, no code fences around the whole document, no closing remarks.
