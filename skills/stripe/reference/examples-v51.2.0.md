# Stripe.net

<!--
Generated for Stripe.net v51.2.0.
All monetary amounts are expressed in the smallest currency unit (e.g. cents for USD, yen for JPY).
Do not edit by hand — rerun the update script to regenerate this file.
-->

Canonical server-side examples for the official Stripe SDK for .NET, pinned to v51.2.0.
Each example is a short async method using only members present in this version's public API.

## 1. Configure the client

Pull the secret key from configuration (never a literal) and either set the global
`StripeConfiguration.ApiKey` or construct a `StripeClient` and pass it to a service.

```csharp
using Microsoft.Extensions.Configuration;
using Stripe;

public static class StripeBootstrap
{
    public static StripeClient Build(IConfiguration config)
    {
        var apiKey = config["Stripe:SecretKey"]
            ?? throw new InvalidOperationException("Stripe:SecretKey not configured.");

        // Option A: global default used by all `new XxxService()` calls.
        StripeConfiguration.ApiKey = apiKey;

        // Option B: explicit client instance, ideal for DI / multi-tenant.
        return new StripeClient(apiKey);
    }
}
```

Notes:
- Use `IConfiguration`, environment variables, or a secret store — never check the key into source.
- `new XxxService()` reads `StripeConfiguration.ApiKey`; `new XxxService(stripeClient)` uses the explicit client.

## 2. Create and confirm a PaymentIntent

```csharp
public static async Task<PaymentIntent> CreatePaymentIntentAsync(long amountInCents, string currency)
{
    var options = new PaymentIntentCreateOptions
    {
        Amount = amountInCents,
        Currency = currency,
        AutomaticPaymentMethods = new PaymentIntentAutomaticPaymentMethodsOptions
        {
            Enabled = true,
        },
        Description = "Order #1234",
    };

    var requestOptions = new RequestOptions
    {
        IdempotencyKey = $"pi-create-order-1234",
    };

    var service = new PaymentIntentService();
    return await service.CreateAsync(options, requestOptions);
}
```

Notes:
- `Amount` is `long` in the smallest currency unit (e.g. 1999 = $19.99).
- An idempotency key lets you safely retry the same logical request without double-charging.
- Confirmation typically happens client-side via Stripe.js using the returned `ClientSecret`.

## 3. Save a card for later with a SetupIntent

```csharp
public static async Task<SetupIntent> StartSaveCardAsync(string customerId)
{
    var options = new SetupIntentCreateOptions
    {
        Customer = customerId,
        Usage = "off_session",
        AutomaticPaymentMethods = new SetupIntentAutomaticPaymentMethodsOptions
        {
            Enabled = true,
        },
    };

    var service = new SetupIntentService();
    return await service.CreateAsync(options);
}
```

Notes:
- Return the `ClientSecret` to the browser; Stripe.js collects card details and confirms the SetupIntent.
- On success, the resulting `PaymentMethod` is automatically attached to the `Customer`.
- Use `Usage = "off_session"` when you intend to charge later without the customer present.

## 4. Create a Customer

```csharp
public static async Task<Customer> CreateCustomerAsync(string email, string name)
{
    var options = new CustomerCreateOptions
    {
        Email = email,
        Name = name,
        Metadata = new Dictionary<string, string>
        {
            ["internal_user_id"] = "user_42",
        },
    };

    var service = new CustomerService();
    return await service.CreateAsync(options);
}
```

Notes:
- `Metadata` is a great place for your own foreign keys — visible in the Dashboard and on webhooks.
- Customer creation is cheap; create one per user even before they pay.

## 5. Start a Subscription

```csharp
public static async Task<Subscription> SubscribeAsync(string customerId, string priceId)
{
    var options = new SubscriptionCreateOptions
    {
        Customer = customerId,
        Items = new List<SubscriptionItemOptions>
        {
            new SubscriptionItemOptions { Price = priceId, Quantity = 1 },
        },
        PaymentBehavior = "default_incomplete",
        PaymentSettings = new SubscriptionPaymentSettingsOptions
        {
            SaveDefaultPaymentMethod = "on_subscription",
        },
    };
    options.AddExpand("latest_invoice.confirmation_secret");

    var service = new SubscriptionService();
    return await service.CreateAsync(options);
}
```

Notes:
- `PaymentBehavior = "default_incomplete"` keeps the subscription `incomplete` until the first invoice is paid — the recommended SCA-friendly flow.
- Expand `latest_invoice.confirmation_secret` to get a client secret you can confirm in the browser.

## 6. Build a Checkout Session

```csharp
using Stripe.Checkout;

public static async Task<Session> CreateCheckoutSessionAsync(string priceId)
{
    var options = new SessionCreateOptions
    {
        Mode = "payment",
        LineItems = new List<SessionLineItemOptions>
        {
            new SessionLineItemOptions { Price = priceId, Quantity = 1 },
        },
        SuccessUrl = "https://example.com/success?session_id={CHECKOUT_SESSION_ID}",
        CancelUrl = "https://example.com/cancel",
    };

    var service = new SessionService();
    return await service.CreateAsync(options);
}
```

Notes:
- `SessionService` lives in `Stripe.Checkout`, not `Stripe`.
- Redirect the customer to `session.Url` after creation.
- Use `Mode = "subscription"` and recurring prices for subscription checkout.

## 7. Issue a Refund

```csharp
public static async Task<Refund> RefundAsync(string paymentIntentId, long? amountInCents = null)
{
    var options = new RefundCreateOptions
    {
        PaymentIntent = paymentIntentId,
        Amount = amountInCents,         // null = full refund
        Reason = "requested_by_customer",
    };

    var requestOptions = new RequestOptions
    {
        IdempotencyKey = $"refund-{paymentIntentId}",
    };

    var service = new RefundService();
    return await service.CreateAsync(options, requestOptions);
}
```

Notes:
- Omit `Amount` for a full refund; otherwise specify the partial amount in the smallest currency unit.
- Refunds are asynchronous for some payment methods — watch the `refund.updated` webhook.

## 8. List with auto-pagination

```csharp
public static async Task<List<Customer>> RecentCustomersAsync(int max = 200)
{
    var options = new CustomerListOptions { Limit = 100 };
    var service = new CustomerService();

    var collected = new List<Customer>();
    await foreach (var customer in service.ListAutoPagingAsync(options))
    {
        collected.Add(customer);
        if (collected.Count >= max) break;
    }
    return collected;
}
```

Notes:
- `ListAutoPagingAsync` transparently pages under the hood — don't track `StartingAfter` yourself.
- For a single page, use `ListAsync` which returns a `StripeList<T>` with `Data` and `HasMore`.

## 9. Verify a webhook

```csharp
using Microsoft.AspNetCore.Http;

public static async Task<IResult> HandleWebhookAsync(HttpRequest request, string webhookSecret)
{
    using var reader = new StreamReader(request.Body);
    var json = await reader.ReadToEndAsync();      // RAW body — do not deserialize then re-serialize
    var signature = request.Headers["Stripe-Signature"];

    Event stripeEvent;
    try
    {
        stripeEvent = EventUtility.ConstructEvent(json, signature, webhookSecret);
    }
    catch (StripeException)
    {
        return Results.BadRequest();               // bad signature or tampered payload
    }

    switch (stripeEvent.Type)
    {
        case EventTypes.PaymentIntentSucceeded:
            var pi = (PaymentIntent)stripeEvent.Data.Object;
            // fulfill the order using pi.Id / pi.Amount
            break;

        case EventTypes.ChargeRefunded:
            var charge = (Charge)stripeEvent.Data.Object;
            // reconcile the refund
            break;
    }

    return Results.Ok();
}
```

Notes:
- Pass the **raw** request body string to `ConstructEvent` — re-serialized JSON will break signature verification.
- `Event.Data.Object` is the concrete resource (`PaymentIntent`, `Charge`, `Subscription`, …) you can cast.
- The default 300-second tolerance is fine for production; lower it only for testing.

## 10. Error handling

```csharp
public static async Task<(PaymentIntent? Intent, string? UserMessage)> TryChargeAsync(
    long amount, string currency, string paymentMethodId, string customerId)
{
    try
    {
        var pi = await new PaymentIntentService().CreateAsync(new PaymentIntentCreateOptions
        {
            Amount = amount,
            Currency = currency,
            Customer = customerId,
            PaymentMethod = paymentMethodId,
            Confirm = true,
            OffSession = true,
        });
        return (pi, null);
    }
    catch (StripeException ex)
    {
        var err = ex.StripeError;
        if (err?.Type == "card_error")
        {
            // Decline — surface a friendly message; `DeclineCode` distinguishes the reason.
            return (null, err.Message ?? "Your card was declined.");
        }

        // Anything else (api_error, invalid_request_error, idempotency_error) is a server problem.
        throw;
    }
}
```

Notes:
- `StripeException.StripeError` carries `Type`, `Code`, `DeclineCode`, `Message`, and `Param`.
- Only card declines (`Type == "card_error"`) are safe to show to the end user as-is.
- Network/transient errors are retried automatically up to `StripeConfiguration.MaxNetworkRetries` times.

## 11. New in v51.2: customized payout settlement timing

v51.2.0 adds a `StartOfDay` configuration on `BalanceSettings.Payments.SettlementTiming`,
letting Connect platforms group automatic payouts around a local "day start" instead of UTC midnight.

```csharp
public static async Task<BalanceSettings> ConfigureStartOfDayAsync()
{
    var options = new BalanceSettingsUpdateOptions
    {
        Payments = new BalanceSettingsPaymentsOptions
        {
            SettlementTiming = new BalanceSettingsPaymentsSettlementTimingOptions
            {
                StartOfDay = new BalanceSettingsPaymentsSettlementTimingStartOfDayOptions
                {
                    Hour = 9,                  // settle at 09:30 local time
                    Minutes = 30,
                    Timezone = "America/New_York",
                },
            },
        },
    };

    var service = new BalanceSettingsService();
    return await service.UpdateAsync(options);
}
```

Notes:
- `Hour` and `Minutes` must match a supported customized-start-of-day combination (minutes must be `0` or `30`).
- `Timezone` is an IANA name like `America/New_York` or `Europe/Berlin`.
- This pairs with the new `BalanceSettingsPaymentsPayoutsAutomaticTransferRulesByCurrencyOptions` shape also introduced in v51.2.0 for per-currency automatic transfer rules to a FinancialAccount.
