# Stripe.net v51.2.0 — patterns

## What Stripe.net is

Stripe.net is the official, OpenAPI-generated .NET SDK for Stripe's REST API.
The library's major version tracks Stripe's dated API version, so option
classes, entity property names, and even whole resources shift between
majors — **do not assume a property or option from another version exists in
v51**; verify against the surface for this version.

The mental model is **resource + service**. Each Stripe resource
(`PaymentIntent`, `Customer`, `Invoice`, …) is a plain entity class you read
after a call returns. You make calls through a `{Resource}Service`
(`PaymentIntentService`, `CustomerService`, …) passing a
`{Resource}{Operation}Options` request shape (`PaymentIntentCreateOptions`,
`CustomerUpdateOptions`, …). Services are constructed against an
`IStripeClient`, which holds the API key, base URLs, and HTTP plumbing.

Stripe.net is **server-side only** and uses your **secret key** (`sk_test_…`
in dev, `sk_live_…` in prod). It does **not** belong in:

- **Client-side payment collection.** Card numbers, bank credentials, and
  similar are collected by Stripe.js, Elements, or the mobile SDKs, which
  return a `PaymentMethod`/`Token` id. Your server uses that id with this SDK.
- **Raw card storage.** Never accept or persist PANs on your server — that
  puts you in PCI scope. Collect via Stripe's client SDKs, pass the resulting
  id to the API.

---

## Non-negotiable safety rules

- **Secret keys never in source.** Pull from configuration, environment, or a
  secrets manager — never check in `sk_live_…`.
  ```csharp
  StripeConfiguration.ApiKey = builder.Configuration["Stripe:SecretKey"];
  ```
- **Money is integer minor units, typed `long`.** `Amount = 2000` means $20.00
  USD. Zero-decimal currencies (JPY) use whole units (`Amount = 2000` = ¥2000).
  Never store dollars in a `decimal` and convert at the boundary.
  ```csharp
  var opts = new PaymentIntentCreateOptions { Amount = 2000, Currency = "usd" };
  ```
- **Idempotency on every write that could be retried.** Pass a stable key per
  logical operation so retries don't double-charge.
  ```csharp
  await service.CreateAsync(opts, new RequestOptions { IdempotencyKey = orderId });
  ```
- **Webhooks must be signature-verified.** Always construct the event from the
  raw body + signature header.
  ```csharp
  var stripeEvent = EventUtility.ConstructEvent(json, sigHeader, webhookSecret);
  ```
- **Prefer async in request pipelines.**
  ```csharp
  var pi = await service.CreateAsync(opts);
  ```
- **Expand what you need.** Related objects come back as ids by default; ask
  for nesting up front instead of a second round-trip.
  ```csharp
  var get = new PaymentIntentGetOptions { Expand = { "latest_charge", "customer" } };
  ```

---

## Where each piece of code belongs

| Concern                                                  | Lives in                                                    |
|----------------------------------------------------------|-------------------------------------------------------------|
| `StripeConfiguration.ApiKey` / `StripeClient` registration | App startup / DI composition root                           |
| Building `{Resource}{Operation}Options`                  | Use-case / application service method                        |
| Calling `{Resource}Service` (e.g. `PaymentIntentService`)| Application/service layer, not directly in controllers       |
| `EventUtility.ConstructEvent`                            | Webhook endpoint, before any business logic                  |
| Amount/currency conversion (dollars↔cents, formatting)   | A single money helper, never literals scattered in handlers  |
| `catch (StripeException)` and mapping to domain errors   | Application/service layer wrapping each call                 |

---

## Canonical shape: create a PaymentIntent

```csharp
using Stripe;

public sealed class PaymentsService
{
    private readonly PaymentIntentService _intents;

    public PaymentsService(IStripeClient client)
    {
        _intents = new PaymentIntentService(client);
    }

    public async Task<PaymentIntent> StartCheckoutAsync(
        string orderId,
        long amountMinorUnits,
        string currency,
        string customerId,
        CancellationToken ct)
    {
        var options = new PaymentIntentCreateOptions
        {
            Amount      = amountMinorUnits,
            Currency    = currency,
            Customer    = customerId,
            Description = $"Order {orderId}",
            AutomaticPaymentMethods = new PaymentIntentAutomaticPaymentMethodsOptions
            {
                Enabled = true,
            },
            Metadata = new Dictionary<string, string> { ["order_id"] = orderId },
        };

        var requestOptions = new RequestOptions
        {
            IdempotencyKey = $"pi-create:{orderId}",
        };

        return await _intents.CreateAsync(options, requestOptions, ct);
    }
}
```

DI registration (ASP.NET Core):

```csharp
builder.Services.AddSingleton<IStripeClient>(
    _ => new StripeClient(builder.Configuration["Stripe:SecretKey"]));
builder.Services.AddScoped<PaymentsService>();
```

---

## Error handling

Stripe API failures surface as `StripeException`, which carries a
`StripeError` whose `Code`, `Type`, and `DeclineCode` you branch on. Card
declines are **expected business outcomes** — surface a friendly message to
the user; treat rate-limit and API errors as retryable.

```csharp
try
{
    var pi = await _intents.CreateAsync(options, requestOptions, ct);
    return PaymentResult.Ok(pi.Id, pi.Status);
}
catch (StripeException ex)
{
    var err = ex.StripeError;        // may be null on transport-level failures
    switch (err?.Type)
    {
        case "card_error":
            // Show err.Message to the user; err.DeclineCode tells you why
            // (e.g. "insufficient_funds", "lost_card").
            return PaymentResult.Declined(err.Code, err.DeclineCode, err.Message);

        case "rate_limit_error":
        case "api_error":
            // Transient — retry with the same IdempotencyKey.
            throw new TransientPaymentException(ex.Message, ex);

        case "invalid_request_error":
            // Programmer error: bad params, wrong id, etc.
            throw new InvalidOperationException(err.Message, ex);

        default:
            throw;
    }
}
```

Useful members on the error payload (see surface): `Code`, `DeclineCode`,
`Type`, `Message`, `Param`, `PaymentIntent`, `RequestLogUrl`.

---

## Webhooks

The endpoint must read the **raw body** (no model binder that re-serializes —
the signature is computed over the exact bytes Stripe sent). Verify, then
switch on `Type` and cast `Data.Object`.

```csharp
app.MapPost("/webhooks/stripe", async (HttpRequest req, IConfiguration cfg) =>
{
    using var reader = new StreamReader(req.Body);
    var json = await reader.ReadToEndAsync();

    Event stripeEvent;
    try
    {
        stripeEvent = EventUtility.ConstructEvent(
            json,
            req.Headers["Stripe-Signature"],
            cfg["Stripe:WebhookSecret"]);
    }
    catch (StripeException)
    {
        return Results.BadRequest();   // bad signature / replay / malformed
    }

    switch (stripeEvent.Type)
    {
        case "payment_intent.succeeded":
            var pi = (PaymentIntent)stripeEvent.Data.Object;
            // Enqueue fulfilment — do NOT do heavy work synchronously.
            break;

        case "charge.refunded":
            var charge = (Charge)stripeEvent.Data.Object;
            break;

        // ignore the rest
    }

    return Results.Ok();   // 200 fast — Stripe retries non-2xx
});
```

Notes:

- Return 200 quickly; do the actual work on a background queue. Stripe retries
  on non-2xx, so a slow handler turns into duplicate events.
- The same event id may be delivered more than once — make handlers
  idempotent (use `stripeEvent.Id` as a dedupe key).
- Never deserialize the body straight into `Event` — that skips signature
  verification.

---

## Testing

- Use test-mode keys (`sk_test_…`) and Stripe's published test PaymentMethod
  ids / test cards. Live keys never appear in tests.
- `{Resource}Service` constructors accept an `IStripeClient`, so substitute a
  fake client in unit tests rather than hitting the network:

  ```csharp
  public sealed class FakeStripeClient : IStripeClient { /* implement members */ }

  var svc = new PaymentIntentService(new FakeStripeClient());
  ```

- For end-to-end tests against test mode, drive the API with throwaway
  customers and clean up with the test clock helpers
  (`Stripe.TestHelpers.TestClockService`) where time-based logic is involved.

---

## Things to avoid

- **Dollars-as-`decimal` for `Amount`.** The field is `long` minor units.
  `Amount = 19.99m` is a compile error; `Amount = 1999` is $19.99.
- **Hardcoded or committed secret keys.** Config + secret store only.
- **Unverified webhook payloads.** Always go through `EventUtility.ConstructEvent`.
- **Missing `IdempotencyKey` on create/charge paths.** Network blips become
  duplicate charges.
- **Setting properties from a different major.** Option shapes change between
  majors — if the property isn't on the v51 surface, it doesn't exist here.
- **Synchronous `Create` / `Get` in ASP.NET request handlers.** Use the
  `…Async` overloads to avoid thread-pool starvation.
- **Polling `PaymentIntent.Status` instead of listening to webhooks.** The
  authoritative state transitions arrive as events
  (`payment_intent.succeeded`, `payment_intent.payment_failed`, …).
- **`catch (StripeException) { /* log and swallow */ }`.** You'll hide card
  declines from the user and rate-limit signals from your retry policy. Branch
  on `StripeError.Type` / `Code` and act accordingly.
