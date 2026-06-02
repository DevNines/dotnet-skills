# Stripe.net — release notes by major

_Generated from `https://github.com/stripe/stripe-dotnet/releases`. Use when answering migration questions or when a user asks what changed between versions._

## v51.x

### v51.3.0-beta.1  (v51.3.0-beta.1)
<https://github.com/stripe/stripe-dotnet/releases/tag/v51.3.0-beta.1>

This release changes the pinned API version to 2026-05-27.private.

* [#3376](https://github.com/stripe/stripe-dotnet/pull/3376) Update generated code for beta
  * Add support for `Pause` method on resource `Subscription`
  * Add support for `Get` method on resource `V2.Iam.ActivityLog`
  * ⚠️ Change type of `ProductCatalog.TrialOffer.EndBehavior.Transition.Price` from `string` to `expandable($Price)`
  * Add support for `AmountPaidOffStripe` on `QuotePreviewInvoice`
  * Add support for `Discountable` on `QuotePreviewSubscriptionSchedule.Phase.AddInvoiceItem`
  * Add support for `Bizum` and `Scalapay` on `SharedPayment.GrantedToken.PaymentMethodDetails`
  * Change type of `SubscriptionItem.BilledUntil` from `nullable(DateTime)` to `DateTime`
  * Add support for `PaymentBehavior` on `SubscriptionResumeOptions`
  * Add support for `StatusDetails` on `Subscription`
  * ⚠️ Change type of `V2.MoneyManagement.ReceivedCredit.BankTransfer.GbBankAccount.Network` from `literal('fps')` to `enum('chaps'|'fps')`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v51.3.0-beta.1/CHANGELOG.md).

### v51.3.0-alpha.1  (v51.3.0-alpha.1)
<https://github.com/stripe/stripe-dotnet/releases/tag/v51.3.0-alpha.1>

This release changes the pinned API version to 2026-05-27.private.

* [#3387](https://github.com/stripe/stripe-dotnet/pull/3387) Update generated code for private-preview
  * Change type of `BillingAlertSpendThresholdOptions.GroupBy` from `literal('pricing_plan_subscription')` to `enum('billing_cadence'|'pricing_plan_subscription')`
  * ⚠️ Change type of `Billing.Alert.SpendThreshold.GroupBy` from `literal('pricing_plan_subscription')` to `enum('billing_cadence'|'pricing_plan_subscription')`
  * Add support for `WechatPay` on `Invoice.PaymentSettings.PaymentMethodOptions`, `InvoicePaymentSettingsPaymentMethodOptionsOptions`, `QuotePreviewInvoice.PaymentSettings.PaymentMethodOptions`, `Subscription.PaymentSettings.PaymentMethodOptions`, and `SubscriptionPaymentSettingsPaymentMethodOptionsOptions`
  * Add support for `GiftCard` on `PaymentIntent.PaymentMethodOptions` and `PaymentIntentPaymentMethodOptionsOptions`
  * Add support for `PaymentDetails` on `PaymentIntentPaymentsOrchestrationOptions`
  * Add support for `Enabled` on `PaymentIntent.PaymentDetails.Benefit.FrMealVoucher` and `SetupIntent.SetupDetails.Benefit.FrMealVoucher`
  * ⚠️ Remove support for `LoginFailed`, `RegistrationFailed`, `RegistrationSuccess`, and `Type` on `Radar.CustomerEvaluationUpdateOptions`
  * ⚠️ Remove support for `LatestVersion` on `V2.Billing.LicenseFee`, `V2.Billing.PricingPlan`, and `V2.Billing.RateCard`
  * ⚠️ Remove support for `ServiceIntervalCount` and `ServiceInterval` on `V2.Billing.LicenseFee` and `V2.Billing.RateCard`
  * Add support for `DebitAgreement` on `V2.MoneyManagement.ReceivedCredit.StripeBalancePayment`
  * Add support for `CanonicalPath` on `EventsV2CoreHealthTrafficVolumeDropFiringEventImpact` and `EventsV2CoreHealthTrafficVolumeDropResolvedEventImpact`
  * Add support for snapshot event `PaymentIntentExpired` with resource `PaymentIntent`
  * Add support for event notifications `V2CoreHealthElementsErrorFiringEvent`, `V2CoreHealthElementsErrorResolvedEvent`, `V2CoreHealthInvoiceCountDroppedFiringEvent`, and `V2CoreHealthInvoiceCountDroppedResolvedEvent`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v51.3.0-alpha.1/CHANGELOG.md).

### v51.2.0  (v51.2.0)
<https://github.com/stripe/stripe-dotnet/releases/tag/v51.2.0>

This release changes the pinned API version to 2026-05-27.dahlia.

* [#3386](https://github.com/stripe/stripe-dotnet/pull/3386) Update generated code
  * Add support for new resource `V2.Commerce.ProductCatalogImport`
  * Add support for `Create` and `Get` methods on resource `V2.Commerce.ProductCatalogImport`
  * Add support for `BizumPayments` and `ScalapayPayments` on `Account.Capabilities` and `AccountCapabilitiesOptions`
  * Add support for `AutomaticTransferRulesByCurrency` on `BalanceSettings.Payments.Payouts` and `BalanceSettingsPaymentsPayoutsOptions`
  * Add support for `StartOfDay` on `BalanceSettings.Payments.SettlementTiming` and `BalanceSettingsPaymentsSettlementTimingOptions`
  * Add support for `Description` on `ChargeTransferDataOptions`, `PaymentIntent.TransferData`, and `PaymentIntentTransferDataOptions`
  * Add support for `Bizum` on `Charge.PaymentMethodDetails`, `ConfirmationToken.PaymentMethodPreview`, `ConfirmationTokenPaymentMethodDataOptions`, `PaymentAttemptRecord.PaymentMethodDetails`, `PaymentIntent.PaymentMethodOptions`, `PaymentIntentPaymentMethodDataOptions`, `PaymentIntentPaymentMethodOptionsOptions`, `PaymentMethodConfigurationCreateOptions`, `PaymentMethodConfigurationUpdateOptions`, `PaymentMethodConfiguration`, `PaymentMethodCreateOptions`, `PaymentMethod`, `PaymentRecord.PaymentMethodDetails`, `SetupIntent.PaymentMethodOptions`, `SetupIntentPaymentMethodDataOptions`, and `SetupIntentPaymentMethodOptionsOptions`
  * Add support for `Scalapay` on `Charge.PaymentMethodDetails`, `Checkout.Session.PaymentMethodOptions`, `CheckoutSessionPaymentMethodOptionsOptions`, `ConfirmationToken.PaymentMethodPreview`, `ConfirmationTokenPaymentMethodDataOptions`, `PaymentAttemptRecord.PaymentMethodDetails`, `PaymentIntent.PaymentMethodOptions`, `PaymentIntentPaymentMethodDataOptions`, `PaymentIntentPaymentMethodOptionsOptions`, `PaymentMethodConfigurationCreateOptions`, `PaymentMethodConfigurationUpdateOptions`, `PaymentMethodConfiguration`, `PaymentMethodCreateOptions`, `PaymentMethod`, `PaymentRecord.PaymentMethodDetails`, `Refund.DestinationDetails`, and `SetupIntentPaymentMethodDataOptions`
  * Add support for `Mandate` on `Charge.PaymentMethodDetails.Twint`, `PaymentAttemptRecord.PaymentMethodDetails.Twint`, and `PaymentRecord.PaymentMethodDetails.Twint`
  * Change type of `CheckoutSessionPaymentMethodOptionsTwintOptions.SetupFutureUsage` and `PaymentIntentPaymentMethodOptionsTwintOptions.SetupFutureUsage` from `literal('none')` to `enum('none'|'off_session')`
  * ⚠️ Change type of `Checkout.Session.PaymentMethodOptions.Twint.SetupFutureUsage` and `PaymentIntent.PaymentMethodOptions.Twint.SetupFutureUsage` from `literal('none')` to `enum('none'|'off_session')`
  * Add support for `CreditedItems` on `InvoiceItem.ProrationDetails`
  * Add support for `Discountable` on `InvoiceScheduleDetailsPhaseAddInvoiceItemOptions`, `SubscriptionAddInvoiceItemOptions`, `SubscriptionSchedule.Phase.AddInvoiceItem`, and `SubscriptionSchedulePhaseAddInvoiceItemOptions`
  * Add support for `BillingSchedules` on `InvoiceSubscriptionDetailsOptions`, `SubscriptionCreateOptions`, `SubscriptionUpdateOptions`, and `Subscription`
  * Add support for `AmountPaidOffStripe` on `Invoice`
  * Add support for `Twint` on `Mandate.PaymentMethodDetails` and `SetupAttempt.PaymentMethodDetails`
  * Add support for `Metadata` on `PaymentIntent.TransferData`, `PaymentIntentTransferDataOptions`, and `Subscription.PendingUpdate`
  * Add support for `PaymentData` on `PaymentIntent.TransferData` and `PaymentIntentTransferDataOptions`
  * Add support for `BlikAuthorize` on `PaymentIntent.NextAction` and `SetupIntent.NextAction`
  * Add support for `PaymentMethodOptions` on `PaymentLinkCreateOptions`, `PaymentLinkUpdateOptions`, and `PaymentLink`
  * Add support for `Active` on `PaymentMethodConfigurationListOptions`
  * Add support for `BilledUntil` on `SubscriptionItem`
  * Add support for `Discount` and `Discounts` on `Subscription.PendingUpdate`
  * Add support for `VerifoneM425`, `VerifoneP630`, `VerifoneUx700`, and `VerifoneV660p` on `Terminal.ConfigurationCreateOptions`, `Terminal.ConfigurationUpdateOptions`, and `Terminal.Configuration`
  * Add support for `ApiError` and `PrintContent` on `Terminal.Reader.Action`
  * Add support for `Customer` on `TestHelpers.TestClockCreateOptions`
  * Add support for `Signer` on `V2.Core.Account.Identity.BusinessDetails.Documents.ProofOfRegistration`, `V2.Core.Account.Identity.BusinessDetails.Documents.ProofOfUltimateBeneficialOwnership`, `V2CoreAccountIdentityBusinessDetailsDocumentsProofOfRegistrationOptions`, `V2CoreAccountIdentityBusinessDetailsDocumentsProofOfUltimateBeneficialOwnershipOptions`, `V2CoreAccountTokenIdentityBusinessDetailsDocumentsProofOfRegistrationOptions`, and `V2CoreAccountTokenIdentityBusinessDetailsDocumentsProofOfUltimateBeneficialOwnershipOptions`
  * Add support for `AzureEventGrid` on `V2.Core.EventDestinationCreateOptions` and `V2.Core.EventDestination`
  * Add support for event notifications `V2CommerceProductCatalogImportsFailedEvent`, `V2CommerceProductCatalogImportsProcessingEvent`, `V2CommerceProductCatalogImportsSucceededEvent`, and `V2CommerceProductCatalogImportsSucceededWithErrorsEvent` with related object `V2.Commerce.ProductCatalogImport`
* [#3385](https://github.com/stripe/stripe-dotnet/pull/3385) Emit warning when `stripe-notify` header is present in response

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v51.2.0/CHANGELOG.md).

### v51.2.0-alpha.6  (v51.2.0-alpha.6)
<https://github.com/stripe/stripe-dotnet/releases/tag/v51.2.0-alpha.6>

* [#3384](https://github.com/stripe/stripe-dotnet/pull/3384) Update generated code for private-preview
  * Add support for new resource `PaymentLocationCapability`
  * Add support for `Get`, `List`, and `Update` methods on resource `PaymentLocationCapability`
  * Add support for `Close` and `SimulateNetworkLifecycleDisputeResponse` test helper methods on resource `Issuing.Dispute`
  * Change type of `DelegatedCheckoutRequestedSessionDiscountsOptions.Codes` from `array(string)` to `emptyable(array(string))`
  * ⚠️ Remove support for `CreditedItems` on `InvoiceItem.ProrationDetails`
  * Add support for `BalanceResponse` on `Issuing.Authorization`
  * Add support for `PaymentEvaluations` on `PaymentAttemptRecordReportCanceledOptions`, `PaymentAttemptRecordReportFailedOptions`, `PaymentRecordFailedOptions`, `PaymentRecordReportPaymentAttemptCanceledOptions`, and `PaymentRecordReportPaymentAttemptFailedOptions`
  * Add support for `Enabled` on `PaymentIntentPaymentDetailsBenefitFrMealVoucherOptions` and `SetupIntentSetupDetailsBenefitFrMealVoucherOptions`
  * Add support for `AdvancedFeatureDetails` and `AllowedPaymentMethodTypes` on `PaymentIntent`
  * Change type of `PaymentLocationAddressOptions.City` from `string` to `emptyable(string)`
  * Change type of `PaymentLocationAddressOptions.Line1` from `string` to `emptyable(string)`
  * Change type of `PaymentLocationAddressOptions.Line2` from `string` to `emptyable(string)`
  * Change type of `PaymentLocationAddressOptions.PostalCode` from `string` to `emptyable(string)`
  * Change type of `PaymentLocationAddressOptions.State` from `string` to `emptyable(string)`
  * ⚠️ Remove support for `PaymentBehavior` on `SubscriptionResumeOptions`
  * ⚠️ Remove support for `StatusDetails` on `Subscription`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v51.2.0-alpha.6/CHANGELOG.md).

### v51.2.0-alpha.5  (v51.2.0-alpha.5)
<https://github.com/stripe/stripe-dotnet/releases/tag/v51.2.0-alpha.5>

* [#3382](https://github.com/stripe/stripe-dotnet/pull/3382) Update generated code for private-preview
  * Add support for new resources `V2.Core.FeeBatch`, `V2.Core.FeeEntry`, `V2.MoneyManagement.DebitDispute`, and `V2.MoneyManagement.FinancialAccountStatement`
  * Add support for `SimulateNetworkLifecyclePreArbitrationResponse` and `SimulateNetworkLifecyclePreArbitrationSubmission` test helper methods on resource `Issuing.Dispute`
  * Add support for `List` method on resource `PaymentLocation`
  * Add support for `Get` and `List` methods on resources `V2.Core.FeeBatch`, `V2.Core.FeeEntry`, and `V2.MoneyManagement.FinancialAccountStatement`
  * Add support for `Create`, `Get`, and `List` methods on resource `V2.MoneyManagement.DebitDispute`
  * Add support for `Discounts` on `DelegatedCheckout.RequestedSessionCreateOptions`, `DelegatedCheckout.RequestedSessionUpdateOptions`, and `DelegatedCheckout.RequestedSession`
  * Add support for `AmountSale` on `DelegatedCheckout.RequestedSession.LineItemDetail` and `DelegatedCheckout.RequestedSession.TotalDetails`
  * Add support for `AmountDiscount` and `Breakdown` on `DelegatedCheckout.RequestedSession.TotalDetails`
  * ⚠️ Remove support for `CheckDepositAddress` on `Invoice.PaymentSettings.PaymentMethodOptions.CheckScan`, `InvoicePaymentSettingsPaymentMethodOptionsCheckScanOptions`, `QuotePreviewInvoice.PaymentSettings.PaymentMethodOptions.CheckScan`, `Subscription.PaymentSettings.PaymentMethodOptions.CheckScan`, and `SubscriptionPaymentSettingsPaymentMethodOptionsCheckScanOptions`
  * Add support for `PaymentEvaluations` on `PaymentAttemptRecordReportGuaranteedOptions`, `PaymentRecordGuaranteedOptions`, and `PaymentRecordReportPaymentAttemptGuaranteedOptions`
  * Add support for `Location` on `PaymentIntentPaymentDetailsOptions` and `SetupIntentSetupDetailsOptions`
  * Add support for `OnboardingDataUpdateAcknowledged` on `PaymentLocationUpdateOptions`
  * Add support for `Customer` on `Radar.CustomerEvaluationUpdateOptions`
  * Add support for `Status` on `Radar.CustomerEvaluationUpdateOptions` and `Radar.CustomerEvaluation`
  * Add support for `PaymentBehavior` on `SubscriptionResumeOptions`
  * Add support for `DisputeDetails` on `V2.MoneyManagement.ReceivedDebit`
  * Add support for `DebitDispute` on `V2.MoneyManagement.Transaction.Flow` and `V2.MoneyManagement.TransactionEntry.TransactionDetails.Flow`
  * Add support for `PaymentAttemptRecord` on `EventsV2PaymentsOffSessionPaymentAttemptFailedEvent` and `EventsV2PaymentsOffSessionPaymentFailedEvent`
  * Add support for event notifications `V2MoneyManagementFinancialAccountStatementCreatedEvent` and `V2MoneyManagementFinancialAccountStatementRestatedEvent` with related object `V2.MoneyManagement.FinancialAccountStatement`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v51.2.0-alpha.5/CHANGELOG.md).

### v51.2.0-alpha.4  (v51.2.0-alpha.4)
<https://github.com/stripe/stripe-dotnet/releases/tag/v51.2.0-alpha.4>

* [#3378](https://github.com/stripe/stripe-dotnet/pull/3378) Update generated code for private-preview
  * Add support for new resource `PaymentLocation`
  * Add support for `Create`, `Delete`, `Get`, and `Update` methods on resource `PaymentLocation`
  * Add support for `Protections` on `AccountCapabilitiesCardPaymentsOptions` and `Capability`
  * Add support for `GiftCard` on `ConfirmationToken.PaymentMethodPreview`, `ConfirmationTokenPaymentMethodDataOptions`, `PaymentIntentPaymentMethodDataOptions`, `PaymentMethodCreateOptions`, `PaymentMethod`, `SetupIntentPaymentMethodDataOptions`, and `SharedPayment.GrantedToken.PaymentMethodDetails`
  * Add support for `Metadata` on `DelegatedCheckout.RequestedSessionConfirmOptions`
  * Add support for `CreditedItems` on `InvoiceItem.ProrationDetails`
  * Add support for `NetworkLifecycle` on `Issuing.Dispute`
  * Add support for `StatusDetails` on `Subscription`
* [#3379](https://github.com/stripe/stripe-dotnet/pull/3379) Add EventNotificationHandler (private preview)

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v51.2.0-alpha.4/CHANGELOG.md).

### v51.2.0-alpha.3  (v51.2.0-alpha.3)
<https://github.com/stripe/stripe-dotnet/releases/tag/v51.2.0-alpha.3>

* [#3377](https://github.com/stripe/stripe-dotnet/pull/3377) Update generated code for private-preview
  * Add support for `DebitCard` on `V2.Core.Account.Configuration.CardCreator.Capabilities.Consumer.Lead`, `V2.Core.Account.Identity.Attestations.TermsOfService.CardCreator.Consumer.Lead`, `V2CoreAccountConfigurationCardCreatorCapabilitiesConsumerLeadOptions`, and `V2CoreAccountIdentityAttestationsTermsOfServiceCardCreatorConsumerLeadOptions`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v51.2.0-alpha.3/CHANGELOG.md).

### v51.2.0-alpha.2  (v51.2.0-alpha.2)
<https://github.com/stripe/stripe-dotnet/releases/tag/v51.2.0-alpha.2>

* [#3375](https://github.com/stripe/stripe-dotnet/pull/3375) Update generated code for private-preview
  * Add support for new resource `V2.Data.Analytics.MetricQueryResult`
  * Add support for `Create`, `Get`, and `Revoke` methods on resource `SharedPayment.IssuedToken`
  * Add support for `Create` method on resource `V2.Data.Analytics.MetricQueryResult`
  * Add support for `BalanceReport` and `PayoutReconciliationReport` on `AccountSession.Components` and `AccountSessionComponentsOptions`
  * Add support for `AppDistribution` and `SunbitPayments` on `Account.Capabilities` and `AccountCapabilitiesOptions`
  * Add support for `Sunbit` on `Charge.PaymentMethodDetails`, `ConfirmationToken.PaymentMethodPreview`, `ConfirmationTokenPaymentMethodDataOptions`, `PaymentAttemptRecord.PaymentMethodDetails`, `PaymentIntentPaymentMethodDataOptions`, `PaymentMethodConfigurationCreateOptions`, `PaymentMethodConfigurationUpdateOptions`, `PaymentMethodConfiguration`, `PaymentMethodCreateOptions`, `PaymentMethod`, `PaymentRecord.PaymentMethodDetails`, and `SetupIntentPaymentMethodDataOptions`
  * Add support for `Last4` on `Charge.PaymentMethodDetails.GiftCard`, `PaymentAttemptRecord.PaymentMethodDetails.GiftCard`, and `PaymentRecord.PaymentMethodDetails.GiftCard`
  * Add support for `Location` and `Reader` on `Charge.PaymentMethodDetails.Klarna`, `PaymentAttemptRecord.PaymentMethodDetails.Klarna`, and `PaymentRecord.PaymentMethodDetails.Klarna`
  * Add support for `Blik` on `CheckoutSessionPaymentMethodOptionsOptions`, `Invoice.PaymentSettings.PaymentMethodOptions`, `InvoicePaymentSettingsPaymentMethodOptionsOptions`, `QuotePreviewInvoice.PaymentSettings.PaymentMethodOptions`, `Subscription.PaymentSettings.PaymentMethodOptions`, and `SubscriptionPaymentSettingsPaymentMethodOptionsOptions`
  * Add support for `SharedPaymentGrantedToken` on `ConfirmationTokenPaymentMethodDataOptions`, `PaymentIntentPaymentMethodDataOptions`, `PaymentMethod`, and `SetupIntentPaymentMethodDataOptions`
  * ⚠️ Change type of `CreditNote.TotalTaxes.TaxRateDetails.TaxRate`, `CreditNoteLineItem.Taxes.TaxRateDetails.TaxRate`, `Invoice.TotalTaxes.TaxRateDetails.TaxRate`, `InvoiceLineItem.Taxes.TaxRateDetails.TaxRate`, and `QuotePreviewInvoice.TotalTaxes.TaxRateDetails.TaxRate` from `string` to `expandable($TaxRate)`
  * Add support for `BuyerConsents` on `DelegatedCheckout.RequestedSessionConfirmOptions`
  * Add support for `Consents` on `DelegatedCheckout.RequestedSession.BuyerConsents.Marketing`
  * Add support for `PaymentFacilitatorId` and `SubMerchantId` on `IssuingAuthorizationMerchantDataOptions` and `IssuingTransactionMerchantDataOptions`
  * Add support for `CardPresence` on `Issuing.Authorization`
  * Add support for `AllowedCardPresences` and `BlockedCardPresences` on `Issuing.Card.SpendingControls`, `Issuing.Cardholder.SpendingControls`, `IssuingCardSpendingControlsOptions`, and `IssuingCardholderSpendingControlsOptions`
  * ⚠️ Change type of `PaymentAttemptRecord.PaymentMethodDetails.GiftCard.Balance` and `PaymentRecord.PaymentMethodDetails.GiftCard.Balance` from `PaymentFlowsPrivatePaymentMethodsGiftCardDeprecatedDetailsResourceBalanceAmount` to `nullable(PaymentsPrimitivesPaymentRecordsResourcePaymentMethodGiftCardDetailsResourceBalance)`
  * Add support for `AmountToConfirm` on `PaymentIntentConfirmOptions`
  * Add support for `KlarnaDisplayQrCode` on `PaymentIntent.NextAction`
  * Add support for `ValidationErrors` on `Privacy.RedactionJob`
  * Add support for `TaxDetails` on `Product`
  * Add support for `Moto` on `SetupAttempt.PaymentMethodDetails.Card`
  * Add support for `AdmissionsTax`, `AttendanceTax`, `EntertainmentTax`, `GrossReceiptsTax`, `HospitalityTax`, `LuxuryTax`, `ResortTax`, and `TourismTax` on `TaxRegistrationCountryOptionsUsOptions`
  * Add support for `Purpose` on `Treasury.OutboundPaymentCreateOptions` and `Treasury.OutboundPayment`
  * Add support for `CryptoWallet` on `V2.MoneyManagement.FinancialAddress.Credentials`
  * Add support for `MxBankAccount` on `V2.MoneyManagement.FinancialAddress.Credentials` and `V2.MoneyManagement.ReceivedCredit.BankTransfer`
  * Add support for `CryptoWalletTransfer` on `V2.MoneyManagement.ReceivedCredit`
  * Add support for `EuBankAccount` on `V2.MoneyManagement.ReceivedCredit.BankTransfer`
  * Add support for `CryptoProperties` and `SettlementCurrency` on `V2.MoneyManagement.FinancialAddressCreateOptions`
  * Add support for event notifications `V2CoreApprovalRequestCreatedEvent` and `V2CoreApprovalRequestExpiredEvent` with related object `V2.Core.ApprovalRequest`
  * Add support for event notification `V2ExtendExtensionRunFailedEvent`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v51.2.0-alpha.2/CHANGELOG.md).

### v51.2.0-beta.2  (v51.2.0-beta.2)
<https://github.com/stripe/stripe-dotnet/releases/tag/v51.2.0-beta.2>

* [#3374](https://github.com/stripe/stripe-dotnet/pull/3374) Update generated code for beta
  * Add support for new resources `V2.Commerce.ProductCatalogImport`, `V2.Data.Reporting.QueryRun`, `V2.Extend.WorkflowRun`, `V2.Extend.Workflow`, `V2.Iam.ActivityLog`, `V2.Network.BusinessProfile`, and `V2.OrchestratedCommerce.Agreement`
  * Add support for `Confirm`, `Create`, `Get`, `List`, and `Terminate` methods on resource `V2.OrchestratedCommerce.Agreement`
  * Add support for `Get` and `Me` methods on resource `V2.Network.BusinessProfile`
  * Add support for `List` method on resource `V2.Iam.ActivityLog`
  * Add support for `Get` and `List` methods on resource `V2.Extend.WorkflowRun`
  * Add support for `Get`, `Invoke`, and `List` methods on resource `V2.Extend.Workflow`
  * Add support for `Create` and `Get` methods on resources `V2.Commerce.ProductCatalogImport` and `V2.Data.Reporting.QueryRun`
  * ⚠️ Change type of `V2.Billing.Cadence.SettingsData.Collection.PaymentMethodOptions.Konbini`, `V2.Billing.CollectionSetting.PaymentMethodOptions.Konbini`, `V2.Billing.CollectionSettingVersion.PaymentMethodOptions.Konbini`, and `V2BillingCollectionSettingPaymentMethodOptionsOptions.Konbini` from `map(string: dynamic)` to `an object`
  * ⚠️ Change type of `V2.Billing.Cadence.SettingsData.Collection.PaymentMethodOptions.SepaDebit`, `V2.Billing.CollectionSetting.PaymentMethodOptions.SepaDebit`, `V2.Billing.CollectionSettingVersion.PaymentMethodOptions.SepaDebit`, and `V2BillingCollectionSettingPaymentMethodOptionsOptions.SepaDebit` from `map(string: dynamic)` to `an object`
  * ⚠️ Change type of `V2.MoneyManagement.InboundTransfer.TransferHistory.BankDebitProcessing` from `map(string: dynamic)` to `an object`
  * ⚠️ Change type of `V2.MoneyManagement.InboundTransfer.TransferHistory.BankDebitQueued` from `map(string: dynamic)` to `an object`
  * ⚠️ Change type of `V2.MoneyManagement.InboundTransfer.TransferHistory.BankDebitSucceeded` from `map(string: dynamic)` to `an object`
  * Change type of `V2CoreBatchJobEndpointOptions.HttpMethod` from `literal('post')` to `enum('delete'|'post')`
  * Add support for `TreasuryTransaction` on `EventsV2MoneyManagementTransactionCreatedEvent`
  * Add support for event notifications `V2CommerceProductCatalogImportsFailedEvent`, `V2CommerceProductCatalogImportsProcessingEvent`, `V2CommerceProductCatalogImportsSucceededEvent`, and `V2CommerceProductCatalogImportsSucceededWithErrorsEvent` with related object `V2.Commerce.ProductCatalogImport`
  * Add support for event notifications `V2DataReportingQueryRunCreatedEvent`, `V2DataReportingQueryRunFailedEvent`, `V2DataReportingQueryRunSucceededEvent`, and `V2DataReportingQueryRunUpdatedEvent` with related object `V2.Data.Reporting.QueryRun`
  * Add support for event notifications `V2ExtendWorkflowRunFailedEvent`, `V2ExtendWorkflowRunStartedEvent`, and `V2ExtendWorkflowRunSucceededEvent` with related object `V2.Extend.WorkflowRun`
  * Add support for event notifications `V2OrchestratedCommerceAgreementConfirmedEvent`, `V2OrchestratedCommerceAgreementCreatedEvent`, `V2OrchestratedCommerceAgreementPartiallyConfirmedEvent`, and `V2OrchestratedCommerceAgreementTerminatedEvent` with related object `V2.OrchestratedCommerce.Agreement`
  * Add support for error type `CannotProceedException`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v51.2.0-beta.2/CHANGELOG.md).

### v51.2.0-beta.1  (v51.2.0-beta.1)
<https://github.com/stripe/stripe-dotnet/releases/tag/v51.2.0-beta.1>

This release changes the pinned API version to 2026-04-22.private.

* [#3367](https://github.com/stripe/stripe-dotnet/pull/3367) Update generated code for beta
  * Add support for new resources `SharedPayment.GrantedToken` and `SharedPayment.IssuedToken`
  * Add support for `Get` method on resource `SharedPayment.GrantedToken`
  * Add support for `Create` and `Revoke` test helper methods on resource `SharedPayment.GrantedToken`
  * Add support for `Create`, `Get`, and `Revoke` methods on resource `SharedPayment.IssuedToken`
  * Add support for `Blik` on `CheckoutSessionPaymentMethodOptionsOptions`, `Invoice.PaymentSettings.PaymentMethodOptions`, `InvoicePaymentSettingsPaymentMethodOptionsOptions`, `QuotePreviewInvoice.PaymentSettings.PaymentMethodOptions`, `Subscription.PaymentSettings.PaymentMethodOptions`, and `SubscriptionPaymentSettingsPaymentMethodOptionsOptions`
  * Add support for `SharedPaymentGrantedToken` on `ConfirmationTokenPaymentMethodDataOptions`, `PaymentIntentPaymentMethodDataOptions`, `PaymentMethod`, and `SetupIntentPaymentMethodDataOptions`
  * Add support for `ValidationErrors` on `Privacy.RedactionJob`
  * Add support for `TaxDetails` on `Product`
  * ⚠️ Change type of `QuotePreviewInvoice.TotalTaxes.TaxRateDetails.TaxRate` from `string` to `expandable($TaxRate)`
  * Add support for `AdmissionsTax`, `AttendanceTax`, `EntertainmentTax`, `GrossReceiptsTax`, `HospitalityTax`, `LuxuryTax`, `ResortTax`, and `TourismTax` on `TaxRegistrationCountryOptionsUsOptions`
  * Add support for `Purpose` on `Treasury.OutboundPaymentCreateOptions` and `Treasury.OutboundPayment`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v51.2.0-beta.1/CHANGELOG.md).

### v51.2.0-alpha.1  (v51.2.0-alpha.1)
<https://github.com/stripe/stripe-dotnet/releases/tag/v51.2.0-alpha.1>

This release changes the pinned API version to 2026-04-22.private.

* [#3369](https://github.com/stripe/stripe-dotnet/pull/3369) Update generated code for private-preview
  * Add support for new resources `V2.Commerce.ProductCatalogImport`, `V2.Core.ApprovalRequest`, `V2.Extend.WorkflowRun`, `V2.Extend.Workflow`, `V2.Iam.ActivityLog`, `V2.Network.BusinessProfile`, and `V2.OrchestratedCommerce.Agreement`
  * ⚠️ Remove support for resources `V2.Core.WorkflowRun` and `V2.Core.Workflow`
  * Add support for `Confirm`, `Create`, `Get`, `List`, and `Terminate` methods on resource `V2.OrchestratedCommerce.Agreement`
  * Add support for `Get` and `Me` methods on resource `V2.Network.BusinessProfile`
  * Add support for `List` method on resource `V2.Iam.ActivityLog`
  * Add support for `Get` and `List` methods on resource `V2.Extend.WorkflowRun`
  * Add support for `Get`, `Invoke`, and `List` methods on resource `V2.Extend.Workflow`
  * Add support for `Cancel`, `Execute`, `Get`, `List`, and `Submit` methods on resource `V2.Core.ApprovalRequest`
  * Add support for `Create` and `Get` methods on resource `V2.Commerce.ProductCatalogImport`
  * ⚠️ Remove support for `Get` and `List` methods on resource `V2.Core.WorkflowRun`
  * ⚠️ Remove support for `Get`, `Invoke`, and `List` methods on resource `V2.Core.Workflow`
  * Add support for `RenewOnboardingLink` method on resource `V2.Core.ClaimableSandbox`
  * ⚠️ Remove support for `Customer` on `SharedPayment.IssuedToken`
  * Add support for `BillManagement` and `SendMoney` on `AccountSession.Components.Bills.Features`
  * Add support for `GiftCard` on `Charge.PaymentMethodDetails`, `PaymentAttemptRecord.PaymentMethodDetails`, and `PaymentRecord.PaymentMethodDetails`
  * Add support for `CustomPaymentMethodTypes` on `Checkout.SessionCreateOptions` and `Checkout.Session`
  * Add support for `PaymentRecord` on `Checkout.Session`
  * ⚠️ Remove support for `SharedPaymentGrantedToken` on `ConfirmationTokenPaymentMethodDataOptions`, `PaymentIntentPaymentMethodDataOptions`, `PaymentIntent`, `PaymentMethod`, and `SetupIntentPaymentMethodDataOptions`
  * Add support for `PaymentMethod` on `ConfirmationToken.PaymentMethodPreview.SepaDebit.GeneratedFrom`, `PaymentMethod.SepaDebit.GeneratedFrom`, and `SharedPayment.GrantedToken.PaymentMethodDetails.SepaDebit.GeneratedFrom`
  * Add support for `ReturnUrl` on `DelegatedCheckout.RequestedSessionConfirmOptions`
  * Add support for `BuyerConsents` on `DelegatedCheckout.RequestedSession`
  * Add support for `CryptoTransactions` on `Issuing.Authorization`, `Issuing.Dispute`, and `Issuing.Transaction`
  * Add support for `PaymentFacilitatorId` and `SubMerchantId` on `Issuing.Authorization.MerchantData` and `Issuing.Transaction.MerchantData`
  * Add support for `Identifiers` on `OrderLineItemProductDataOptions`, `ProductCreateOptions`, `ProductUpdateOptions`, and `Product`
  * Add support for `AgentDetails` on `PaymentIntent`
  * Add support for `ExternalReference` on `PriceCreateOptions` and `PriceUpdateOptions`
  * Add support for `LoginSucceeded` and `RegistrationSucceeded` on `Radar.AccountEvaluation.Events` and `Radar.AccountEvaluationUpdateOptions`
  * Add support for `PrintContent` on `Terminal.Reader.Action`
  * Add support for `AppChannel` on `V2.Core.ClaimableSandboxCreateOptions` and `V2.Core.ClaimableSandbox`
  * Add support for `OnboardingLinkDetails` and `OwnerDetails` on `V2.Core.ClaimableSandbox`
  * ⚠️ Remove support for `ClaimUrl` on `V2.Core.ClaimableSandbox`
  * ⚠️ Remove support for `OwnerAccount` on `V2.Core.ClaimableSandbox.SandboxDetails`
  * Add support for `SnapshotEvent` on `V2.Core.Event`
  * Add support for `MultiprocessorSettlement` on `V2.MoneyManagement.FinancialAccount`
  * Add support for `CaBankAccount` on `V2.MoneyManagement.FinancialAddress.Credentials` and `V2.MoneyManagement.ReceivedCredit.BankTransfer`
  * Add support for `AmountDetails` and `PaymentDetails` on `V2.Payments.OffSessionPaymentCaptureOptions`, `V2.Payments.OffSessionPaymentCreateOptions`, and `V2.Payments.OffSessionPayment`
  * Add support for `Description` on `V2.Payments.OffSessionPaymentCreateOptions` and `V2.Payments.OffSessionPayment`
  * Add support for `Mcc` on `V2PaymentsOffSessionPaymentPaymentMethodOptionsCardOptions`
  * Add support for `Storage` on `V2.MoneyManagement.FinancialAccountUpdateOptions`
  * Add support for `FxQuote` on `V2.MoneyManagement.CurrencyConversionCreateOptions`
  * ⚠️ Add support for `OnboardingLinkDetails` on `V2.Core.ClaimableSandboxCreateOptions`
  * Change type of `V2CoreBatchJobEndpointOptions.HttpMethod` from `literal('post')` to `enum('delete'|'post')`
  * Add support for `TreasuryTransaction` on `EventsV2MoneyManagementTransactionCreatedEvent`
  * Add support for event notifications `V1AccountApplicationAuthorizedEvent`, `V1AccountApplicationDeauthorizedEvent`, `V1AccountExternalAccountCreatedEvent`, `V1AccountExternalAccountDeletedEvent`, `V1AccountExternalAccountUpdatedEvent`, `V1BillingPortalSessionCreatedEvent`, `V1EntitlementsActiveEntitlementSummaryUpdatedEvent`, `V2CoreHealthMeterEventSummariesDelayedFiringEvent`, and `V2CoreHealthMeterEventSummariesDelayedResolvedEvent`
  * Add support for event notification `V1AccountUpdatedEvent` with related object `Account`
  * Add support for event notifications `V1ApplicationFeeCreatedEvent` and `V1ApplicationFeeRefundedEvent` with related object `ApplicationFee`
  * Add support for event notification `V1ApplicationFeeRefundUpdatedEvent` with related object `ApplicationFeeRefund`
  * Add support for event notification `V1BalanceAvailableEvent` with related object `Balance`
  * Add support for event notification `V1BillingAlertTriggeredEvent` with related object `Billing.Alert`
  * Add support for event notifications `V1BillingPortalConfigurationCreatedEvent` and `V1BillingPortalConfigurationUpdatedEvent` with related object `BillingPortal.Configuration`
  * Add support for event notification `V1CapabilityUpdatedEvent` with related ob

_…truncated…_

### v51.1.0  (v51.1.0)
<https://github.com/stripe/stripe-dotnet/releases/tag/v51.1.0>

This release changes the pinned API version to 2026-04-22.dahlia.

* [#3365](https://github.com/stripe/stripe-dotnet/pull/3365) Update generated code
  * Add support for `BalanceReport` and `PayoutReconciliationReport` on `AccountSession.Components` and `AccountSessionComponentsOptions`
  * Add support for `AppDistribution` and `SunbitPayments` on `Account.Capabilities` and `AccountCapabilitiesOptions`
  * Add support for `Sunbit` on `Charge.PaymentMethodDetails`, `ConfirmationToken.PaymentMethodPreview`, `ConfirmationTokenPaymentMethodDataOptions`, `PaymentAttemptRecord.PaymentMethodDetails`, `PaymentIntentPaymentMethodDataOptions`, `PaymentMethodConfigurationCreateOptions`, `PaymentMethodConfigurationUpdateOptions`, `PaymentMethodConfiguration`, `PaymentMethodCreateOptions`, `PaymentMethod`, `PaymentRecord.PaymentMethodDetails`, and `SetupIntentPaymentMethodDataOptions`
  * Add support for `Location` and `Reader` on `Charge.PaymentMethodDetails.Klarna`, `PaymentAttemptRecord.PaymentMethodDetails.Klarna`, and `PaymentRecord.PaymentMethodDetails.Klarna`
  * Add support for `Mandate` on `Charge.PaymentMethodDetails.Pix`, `PaymentAttemptRecord.PaymentMethodDetails.Pix`, and `PaymentRecord.PaymentMethodDetails.Pix`
  * Add support for `ManagedPayments` on `Checkout.SessionCreateOptions`, `Checkout.Session`, `PaymentIntent`, `PaymentLinkCreateOptions`, `PaymentLink`, `SetupIntent`, and `Subscription`
  * Add support for `MandateOptions` on `Checkout.Session.PaymentMethodOptions.Pix`, `CheckoutSessionPaymentMethodOptionsPixOptions`, `PaymentIntent.PaymentMethodOptions.Pix`, and `PaymentIntentPaymentMethodOptionsPixOptions`
  * Change type of `CheckoutSessionPaymentMethodOptionsPixOptions.SetupFutureUsage` and `PaymentIntentPaymentMethodOptionsPixOptions.SetupFutureUsage` from `literal('none')` to `enum('none'|'off_session')`
  * ⚠️ Change type of `Checkout.Session.PaymentMethodOptions.Pix.SetupFutureUsage` and `PaymentIntent.PaymentMethodOptions.Pix.SetupFutureUsage` from `literal('none')` to `enum('none'|'off_session')`
  * Add support for `Pix` on `Invoice.PaymentSettings.PaymentMethodOptions`, `InvoicePaymentSettingsPaymentMethodOptionsOptions`, `Mandate.PaymentMethodDetails`, `SetupAttempt.PaymentMethodDetails`, `SetupIntent.PaymentMethodOptions`, `SetupIntentPaymentMethodOptionsOptions`, `Subscription.PaymentSettings.PaymentMethodOptions`, and `SubscriptionPaymentSettingsPaymentMethodOptionsOptions`
  * Add support for `Upi` on `Invoice.PaymentSettings.PaymentMethodOptions`, `InvoicePaymentSettingsPaymentMethodOptionsOptions`, `Subscription.PaymentSettings.PaymentMethodOptions`, and `SubscriptionPaymentSettingsPaymentMethodOptionsOptions`
  * Add support for `CardPresence` on `Issuing.Authorization`
  * Add support for `AllowedCardPresences` and `BlockedCardPresences` on `Issuing.Card.SpendingControls`, `Issuing.Cardholder.SpendingControls`, `IssuingCardSpendingControlsOptions`, and `IssuingCardholderSpendingControlsOptions`
  * Add support for `Amount` and `Currency` on `Mandate.MultiUse`
  * Add support for `AmountToConfirm` on `PaymentIntentConfirmOptions`
  * Add support for `KlarnaDisplayQrCode` on `PaymentIntent.NextAction`
  * Add support for `Moto` on `SetupAttempt.PaymentMethodDetails.Card`
  * Add support for `PixDisplayQrCode` on `SetupIntent.NextAction`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v51.1.0/CHANGELOG.md).

### v51.1.0-beta.2  (v51.1.0-beta.2)
<https://github.com/stripe/stripe-dotnet/releases/tag/v51.1.0-beta.2>

Please review the [changelog for 51.0.1](https://github.com/stripe/stripe-dotnet/blob/master/CHANGELOG.md#5101---2026-04-17) for more information about changes in this release.

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v51.1.0-beta.2/CHANGELOG.md).

### v51.1.0-alpha.4  (v51.1.0-alpha.4)
<https://github.com/stripe/stripe-dotnet/releases/tag/v51.1.0-alpha.4>

* [#3368](https://github.com/stripe/stripe-dotnet/pull/3368) Update generated code for private-preview
  * Add support for `LatestVersion` on `V2.Billing.LicenseFee`, `V2.Billing.PricingPlan`, and `V2.Billing.RateCard`
  * Add support for `ServiceIntervalCount` and `ServiceInterval` on `V2.Billing.LicenseFee` and `V2.Billing.RateCard`
* [#3363](https://github.com/stripe/stripe-dotnet/pull/3363) Update generated code for private-preview
  * Add support for new resources `V2.Core.WorkflowRun` and `V2.Core.Workflow`
  * Add support for `ReportAuthorized` method on resource `PaymentAttemptRecord`
  * Add support for `Get` and `List` methods on resource `V2.Core.WorkflowRun`
  * Add support for `Get`, `Invoke`, and `List` methods on resource `V2.Core.Workflow`
  * Add support for `NextAction` and `Status` on `SharedPayment.IssuedToken`
  * ⚠️ Remove support for `NetworkId` on `SharedPayment.IssuedToken.SellerDetails`
  * Add support for `Bills` on `AccountSession.Components`
  * Add support for `SettlementCurrencies` on `BalanceSettings.Payments` and `BalanceSettingsPaymentsOptions`
  * Add support for `DefaultSettlementCurrency` on `BalanceSettings.Payments`
  * Add support for `AccountFunding` on `Charge.PaymentMethodDetails.Card`
  * Add support for `AutomaticSurcharge` on `Checkout.SessionCreateOptions`, `Checkout.Session`, `PaymentLinkCreateOptions`, and `PaymentLink`
  * Add support for `Bizum` on `Checkout.Session.PaymentMethodOptions` and `CheckoutSessionPaymentMethodOptionsOptions`
  * Add support for `SurchargeCost` on `Checkout.Session`
  * Add support for `AmountSurcharge` on `Checkout.Session.TotalDetails`
  * Add support for `SharedPaymentGrantedToken` on `ConfirmationTokenPaymentMethodDataOptions`, `PaymentIntentPaymentMethodDataOptions`, and `SetupIntentPaymentMethodDataOptions`
  * Add support for `Details` on `Identity.VerificationReport.Email`
  * Add support for `Confirm` on `Identity.VerificationSessionCreateOptions` and `Identity.VerificationSessionUpdateOptions`
  * Add support for `Subscription` on `InvoiceItem.Parent.ScheduleDetails`
  * ⚠️ Remove support for `SharedPaymentGrantedToken` on `PaymentIntentConfirmOptions` and `PaymentIntentCreateOptions`
  * Add support for `MoneyServices` on `PaymentIntent.PaymentDetails`
  * ⚠️ Remove support for `ExternalReference` on `Plan`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v51.1.0-alpha.4/CHANGELOG.md).

### v51.1.0-alpha.3  (v51.1.0-alpha.3)
<https://github.com/stripe/stripe-dotnet/releases/tag/v51.1.0-alpha.3>

* [#3361](https://github.com/stripe/stripe-dotnet/pull/3361) Update generated code for private-preview
  * Add support for `PaymentRecord` on `ApplicationFee.FeeSource`
  * Add support for `FleetData` on `ChargePaymentDetailsOptions`, `PaymentIntent.PaymentDetails`, `PaymentIntentAmountDetailsLineItem.PaymentMethodOptions.Card`, `PaymentIntentAmountDetailsLineItemsPaymentMethodOptionsCardOptions`, and `PaymentIntentPaymentDetailsOptions`
  * Add support for `BeneficiaryAccount`, `BeneficiaryDetails`, `SenderAccount`, and `SenderDetails` on `ChargePaymentDetailsMoneyServicesAccountFundingOptions` and `PaymentIntentPaymentDetailsMoneyServicesAccountFundingOptions`
  * Change type of `ChargePaymentDetailsMoneyServicesOptions.TransactionType` and `PaymentIntentPaymentDetailsMoneyServicesOptions.TransactionType` from `literal('account_funding')` to `emptyable(literal('account_funding'))`
  * Add support for `Bizum` on `Invoice.PaymentSettings.PaymentMethodOptions`, `InvoicePaymentSettingsPaymentMethodOptionsOptions`, `QuotePreviewInvoice.PaymentSettings.PaymentMethodOptions`, `Subscription.PaymentSettings.PaymentMethodOptions`, and `SubscriptionPaymentSettingsPaymentMethodOptionsOptions`
  * Add support for `QuantityPrecision` on `PaymentIntentAmountDetailsLineItem` and `PaymentIntentAmountDetailsLineItemsOptions`
  * Add support for `LiquidAsset` and `Wallet` on `PaymentIntentPaymentMethodOptionsCardPaymentDetailsMoneyServicesAccountFundingOptions` and `PaymentIntentPaymentMethodOptionsCardPresentPaymentDetailsMoneyServicesAccountFundingOptions`
  * Add support for `SharedPaymentGrantedToken` on `PaymentMethod`
  * Add support for `Data` on `Radar.PaymentEvaluation.ClientDeviceMetadataDetails` and `RadarPaymentEvaluationClientDeviceMetadataDetailsOptions`
  * Add support for `Sunbit` on `SharedPayment.GrantedToken.PaymentMethodDetails`
  * Add support for error type `CannotProceedException`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v51.1.0-alpha.3/CHANGELOG.md).

### v51.1.0-alpha.2  (v51.1.0-alpha.2)
<https://github.com/stripe/stripe-dotnet/releases/tag/v51.1.0-alpha.2>

* [#3360](https://github.com/stripe/stripe-dotnet/pull/3360) Update generated code for private-preview
  * Add support for new resources `SharedPayment.IssuedToken` and `V2.Data.Reporting.QueryRun`
  * Add support for `Create` and `Get` methods on resource `V2.Data.Reporting.QueryRun`
  * Add support for `Pause` and `Resume` methods on resource `V2.Payments.OffSessionPayment`
  * Add support for `TenantKeys`, `TenantOperator`, and `TenantValues` on `Billing.BillingMeterMeterEventSummaryListOptions`
  * Add support for `MoneyServices` on `ChargePaymentDetailsOptions` and `PaymentIntentPaymentDetailsOptions`
  * Add support for `PaymentMethodOptions` on `DelegatedCheckout.RequestedSessionCreateOptions`, `DelegatedCheckout.RequestedSessionUpdateOptions`, and `DelegatedCheckout.RequestedSession`
  * ⚠️ Remove support for `PaymentMethodData` on `DelegatedCheckout.RequestedSessionConfirmOptions`, `DelegatedCheckout.RequestedSessionCreateOptions`, and `DelegatedCheckout.RequestedSessionUpdateOptions`
  * Add support for `CardBrands` and `PaymentMethodTypes` on `DelegatedCheckout.RequestedSession.SellerDetails`
  * ⚠️ Change type of `DelegatedCheckout.RequestedSession.SharedPaymentIssuedToken` from `string` to `expandable($SharedPayment.IssuedToken)`
  * Add support for `CheckScan` on `Invoice.PaymentSettings.PaymentMethodOptions`, `InvoicePaymentSettingsPaymentMethodOptionsOptions`, `QuotePreviewInvoice.PaymentSettings.PaymentMethodOptions`, `Subscription.PaymentSettings.PaymentMethodOptions`, and `SubscriptionPaymentSettingsPaymentMethodOptionsOptions`
  * Add support for `ProcessorDetails` on `PaymentAttemptRecordReportFailedOptions`, `PaymentAttemptRecordReportGuaranteedOptions`, `PaymentRecordFailedOptions`, `PaymentRecordGuaranteedOptions`, `PaymentRecordReportPaymentAttemptFailedOptions`, and `PaymentRecordReportPaymentAttemptGuaranteedOptions`
  * Add support for `PaymentDetails` on `PaymentIntentPaymentMethodOptionsCardOptions` and `PaymentIntentPaymentMethodOptionsCardPresentOptions`
  * ⚠️ Remove support for `BillFrom` on `QuotePreviewSubscriptionSchedule.BillingSchedule`, `Subscription.BillingSchedule`, and `SubscriptionSchedule.BillingSchedule`
  * Add support for `AgentDetails`, `PaymentMethodDetails`, and `RiskDetails` on `SharedPayment.GrantedToken`
  * Add support for `PaperChecks` on `V2.Account.Configuration.RecipientData.Features`, `V2.Core.Account.Configuration.Recipient.Capabilities`, `V2.Core.Account.Configuration.Storer.Capabilities.OutboundPayments`, `V2AccountConfigurationRecipientDataFeaturesOptions`, `V2CoreAccountConfigurationRecipientCapabilitiesOptions`, and `V2CoreAccountConfigurationStorerCapabilitiesOutboundPaymentsOptions`
  * ⚠️ Change type of `V2.Billing.Cadence.SettingsData.Collection.PaymentMethodOptions.Konbini`, `V2.Billing.CollectionSetting.PaymentMethodOptions.Konbini`, `V2.Billing.CollectionSettingVersion.PaymentMethodOptions.Konbini`, and `V2BillingCollectionSettingPaymentMethodOptionsOptions.Konbini` from `map(string: dynamic)` to `an object`
  * ⚠️ Change type of `V2.Billing.Cadence.SettingsData.Collection.PaymentMethodOptions.SepaDebit`, `V2.Billing.CollectionSetting.PaymentMethodOptions.SepaDebit`, `V2.Billing.CollectionSettingVersion.PaymentMethodOptions.SepaDebit`, and `V2BillingCollectionSettingPaymentMethodOptionsOptions.SepaDebit` from `map(string: dynamic)` to `an object`
  * Add support for `Id` on `V2.Billing.CadenceSpendModifier.MaxBillingPeriodSpend.Amount.CustomPricingUnit`, `V2.Billing.IntentAction.Apply.SpendModifierRule.MaxBillingPeriodSpend.Amount.CustomPricingUnit`, and `V2BillingIntentActionApplySpendModifierRuleMaxBillingPeriodSpendAmountCustomPricingUnitOptions`
  * ⚠️ Change type of `V2.Core.Event.Reason.Request.Client.StripeAction` from `map(string: dynamic)` to `an object`
  * ⚠️ Change type of `V2.MoneyManagement.InboundTransfer.TransferHistory.BankDebitProcessing` from `map(string: dynamic)` to `an object`
  * ⚠️ Change type of `V2.MoneyManagement.InboundTransfer.TransferHistory.BankDebitQueued` from `map(string: dynamic)` to `an object`
  * ⚠️ Change type of `V2.MoneyManagement.InboundTransfer.TransferHistory.BankDebitSucceeded` from `map(string: dynamic)` to `an object`
  * ⚠️ Remove support for `Town` on `V2.MoneyManagement.OutboundPayment.TrackingDetails.PaperCheck.MailingAddress`
  * Add support for `ApplicationFeeAmountRequested` on `V2.Payments.OffSessionPayment`
  * ⚠️ Remove support for `CompartmentId` on `V2.Payments.OffSessionPayment`
  * Add support for `RetryUntil` on `V2.Payments.OffSessionPayment.RetryDetails`
  * Add support for `ApplicationFeeAmount` on `V2.Payments.OffSessionPaymentCaptureOptions` and `V2.Payments.OffSessionPaymentCreateOptions`
  * Add support for `AlertId` on `EventsV2CoreHealthApiErrorResolvedEvent`, `EventsV2CoreHealthApiLatencyResolvedEvent`, `EventsV2CoreHealthAuthorizationRateDropResolvedEvent`, `EventsV2CoreHealthIssuingAuthorizationRequestErrorsFiringEvent`, `EventsV2CoreHealthIssuingAuthorizationRequestErrorsResolvedEvent`, `EventsV2CoreHealthIssuingAuthorizationRequestTimeoutResolvedEvent`, `EventsV2CoreHealthPaymentMethodErrorResolvedEvent`, `EventsV2CoreHealthSepaDebitDelayedFiringEvent`, `EventsV2CoreHealthSepaDebitDelayedResolvedEvent`, `EventsV2CoreHealthTrafficVolumeDropResolvedEvent`, and `EventsV2CoreHealthWebhookLatencyResolvedEvent`
  * Add support for `ApiKey` on `EventsV2IamApiKeyCreatedEvent`, `EventsV2IamApiKeyDefaultSecretRevealedEvent`, `EventsV2IamApiKeyExpiredEvent`, `EventsV2IamApiKeyPermissionsUpdatedEvent`, `EventsV2IamApiKeyRotatedEvent`, and `EventsV2IamApiKeyUpdatedEvent`
  * Add support for `StripeAccessGrant` on `EventsV2IamStripeAccessGrantApprovedEvent`, `EventsV2IamStripeAccessGrantCanceledEvent`, `EventsV2IamStripeAccessGrantDeniedEvent`, `EventsV2IamStripeAccessGrantRemovedEvent`, `EventsV2IamStripeAccessGrantRequestedEvent`, and `EventsV2IamStripeAccessGrantUpdatedEvent`
  * Add support for event notifications `V2DataReportingQueryRunCreatedEvent`

_…truncated…_

### v51.1.0-beta.1  (v51.1.0-beta.1)
<https://github.com/stripe/stripe-dotnet/releases/tag/v51.1.0-beta.1>

This release changes the pinned API version to `2026-03-25.preview`. It is built on top of SDK version 51.0.0 which contains breaking changes. Please review the [changelog for 51.0.0](https://github.com/stripe/stripe-dotnet/blob/master/CHANGELOG.md#5100---2026-03-25) if upgrading from older SDK versions.

* [#3349](https://github.com/stripe/stripe-dotnet/pull/3349) Update generated code for beta
* [#3347](https://github.com/stripe/stripe-dotnet/pull/3347) Merge to beta
  
  - Merged latest master changes into the beta branch.
* [#3337](https://github.com/stripe/stripe-dotnet/pull/3337) Update generated code for beta
  * Add support for new resources `ProductCatalog.TrialOffer`, `Tax.Location`, and `V2.Core.BatchJob`
  * Add support for `Create` method on resource `ProductCatalog.TrialOffer`
  * Add support for `Create`, `Get`, and `List` methods on resource `Tax.Location`
  * Add support for `Cancel`, `Create`, and `Get` methods on resource `V2.Core.BatchJob`
  * Add support for `PerformanceLocation` on `Tax.CalculationLineItem` and `TaxCalculationLineItemOptions`
  * Add support for `TrialOffer` on `InvoiceScheduleDetailsAmendmentItemActionAddOptions`, `InvoiceScheduleDetailsAmendmentItemActionSetOptions`, `InvoiceScheduleDetailsPhaseItemOptions`, `QuoteLine.Action.AddItem`, `QuoteLine.Action.SetItems`, `QuoteLineActionAddItemOptions`, `QuoteLineActionSetItemOptions`, `QuotePreviewSubscriptionSchedule.Phase.Item`, `SubscriptionSchedule.Phase.Item`, `SubscriptionScheduleAmendmentItemActionAddOptions`, `SubscriptionScheduleAmendmentItemActionSetOptions`, and `SubscriptionSchedulePhaseItemOptions`
  * Add support for `RiskReserved` on `Balance`
  * ⚠️ Remove support for `SourceType` on `Charge.PaymentMethodDetails.StripeBalance`, `ConfirmationToken.PaymentMethodPreview.StripeBalance`, `ConfirmationTokenPaymentMethodDataStripeBalanceOptions`, `PaymentAttemptRecord.PaymentMethodDetails.StripeBalance`, `PaymentIntentPaymentMethodDataStripeBalanceOptions`, `PaymentMethod.StripeBalance`, `PaymentMethodStripeBalanceOptions`, `PaymentRecord.PaymentMethodDetails.StripeBalance`, and `SetupIntentPaymentMethodDataStripeBalanceOptions`
  * Add support for `TaxDetails` on `CheckoutSessionLineItemPriceDataProductDataOptions`, `InvoiceLineItemPriceDataProductDataOptions`, `InvoiceLinePriceDataProductDataOptions`, `PaymentLinkLineItemPriceDataProductDataOptions`, `PlanProductOptions`, `PriceProductDataOptions`, `ProductCreateOptions`, and `ProductUpdateOptions`
  * Add support for `PendingInvoiceItemInterval` on `CheckoutSessionSubscriptionDataOptions`
  * Add support for `Hosted` and `UiMode` on `FinancialConnections.SessionCreateOptions` and `FinancialConnections.Session`
  * Add support for `Url` on `FinancialConnections.Session`
  * Add support for `ExpiresAfterSeconds` on `Invoice.PaymentSettings.PaymentMethodOptions.Pix`, `InvoicePaymentSettingsPaymentMethodOptionsPixOptions`, `QuotePreviewInvoice.PaymentSettings.PaymentMethodOptions.Pix`, `Subscription.PaymentSettings.PaymentMethodOptions.Pix`, and `SubscriptionPaymentSettingsPaymentMethodOptionsPixOptions`
  * Add support for `CurrentTrial` on `InvoiceSubscriptionDetailsItemOptions`, `SubscriptionItemCreateOptions`, `SubscriptionItemOptions`, `SubscriptionItemUpdateOptions`, and `SubscriptionItem`
  * Add support for `Surcharge` on `PaymentIntent.AmountDetails` and `PaymentIntentAmountDetailsOptions`
  * Add support for `AmountDetails` and `PaymentDetails` on `PaymentIntentDecrementAuthorizationOptions`
  * Add support for `MandateOptions` on `PaymentIntent.PaymentMethodOptions.StripeBalance`
  * Add support for `ManagedPayments` on `PaymentLinkCreateOptions` and `PaymentLink`
  * Add support for `StripeBalance` on `SetupIntent.PaymentMethodOptions` and `SetupIntentPaymentMethodOptionsOptions`
  * Add support for `BillingCycleAnchor` on `Subscription.TrialSettings.EndBehavior` and `SubscriptionTrialSettingsEndBehaviorOptions`
  * Add support for `AdmissionsTax`, `AttendanceTax`, `EntertainmentTax`, `GrossReceiptsTax`, `HospitalityTax`, `LuxuryTax`, `ResortTax`, and `TourismTax` on `Tax.Registration.CountryOptions.Us`
  * Add support for `Requirements` on `TaxCode`
  * ⚠️ Change type of `V2.Billing.Cadence.SettingsData.Collection.PaymentMethodOptions.Card.MandateOptions.Amount`, `V2.Billing.CollectionSetting.PaymentMethodOptions.Card.MandateOptions.Amount`, `V2.Billing.CollectionSettingVersion.PaymentMethodOptions.Card.MandateOptions.Amount`, and `V2BillingCollectionSettingPaymentMethodOptionsCardMandateOptionsOptions.Amount` from `longInteger` to `int64_string`
  * Add support for `Timezone` on `V2.Core.Account.Defaults` and `V2CoreAccountDefaultsOptions`
  * Add support for `AzureEventGrid` on `V2.Core.EventDestinationCreateOptions` and `V2.Core.EventDestination`
  * Add support for `SupportedCurrencies` on `V2.Core.Vault.GbBankAccount`, `V2.Core.Vault.UsBankAccount`, and `V2.MoneyManagement.PayoutMethod.Card`
  * Add support for `Restricted` on `V2.MoneyManagement.PayoutMethod`
  * Add support for `Currencies` on `V2.MoneyManagement.PayoutMethodsBankAccountSpec.Countries.Field`
  * Add support for `Counterparty` and `Description` on `V2.MoneyManagement.Transaction`
  * ⚠️ Add support for `Currency` on `V2.Core.Vault.GbBankAccountCreateOptions`, `V2.Core.Vault.UsBankAccountCreateOptions`, `V2MoneyManagementOutboundSetupIntentPayoutMethodDataBankAccountOptions`, and `V2MoneyManagementOutboundSetupIntentPayoutMethodDataCardOptions`
  * Add support for `Iban` on `V2.Core.Vault.GbBankAccountCreateOptions`
  * Add support for event notifications `V2CoreBatchJobBatchFailedEvent`, `V2CoreBatchJobCanceledEvent`, `V2CoreBatchJobCompletedEvent`, `V2CoreBatchJobCreatedEvent`, `V2CoreBatchJobReadyForUploadEvent`, `V2CoreBatchJobTimeoutEvent`, `V2CoreBatchJobUpdatedEvent`, `V2CoreBatchJobUploadTimeoutEvent`, `V2CoreBatchJobValidatingEvent`, and `V2CoreBatchJobValidationFailedEvent` with related object `V2.Core.BatchJob`
* [#3334](https://github.com/stripe/str

_…truncated…_

### v51.1.0-alpha.1  (v51.1.0-alpha.1)
<https://github.com/stripe/stripe-dotnet/releases/tag/v51.1.0-alpha.1>

This release changes the pinned API version to 2026-03-25.preview and contains additional breaking changes. See the [GA changelog](https://github.com/stripe/stripe-dotnet/blob/master/CHANGELOG.md#4900---2025-09-30) for more information.


* [#3352](https://github.com/stripe/stripe-dotnet/pull/3352) Update generated code for private-preview
  * Add support for new resource `RiskSignals`
  * Add support for `FinancialAccountRewards` and `NestingDemo` on `AccountSession.Components`
  * Add support for `UpiPayments` on `Account.Capabilities` and `AccountCapabilitiesOptions`
  * Add support for `RiskSignals` on `Account`
  * Add support for `FraudIntent` on `AccountSignals`
  * Add support for `RiskReserved` on `Balance`
  * ⚠️ Remove support for `BillableItems` on `Billing.Alert.SpendThreshold.Filters`
  * Add support for `Upi` on `Charge.PaymentMethodDetails`, `Checkout.Session.PaymentMethodOptions`, `CheckoutSessionPaymentMethodOptionsOptions`, `ConfirmationToken.PaymentMethodPreview`, `ConfirmationTokenPaymentMethodDataOptions`, `Mandate.PaymentMethodDetails`, `PaymentAttemptRecord.PaymentMethodDetails`, `PaymentIntent.PaymentMethodOptions`, `PaymentIntentPaymentMethodDataOptions`, `PaymentIntentPaymentMethodOptionsOptions`, `PaymentMethodConfigurationCreateOptions`, `PaymentMethodConfigurationUpdateOptions`, `PaymentMethodConfiguration`, `PaymentMethodCreateOptions`, `PaymentMethod`, `PaymentRecord.PaymentMethodDetails`, `SetupAttempt.PaymentMethodDetails`, `SetupIntent.PaymentMethodOptions`, `SetupIntentPaymentMethodDataOptions`, and `SetupIntentPaymentMethodOptionsOptions`
  * ⚠️ Remove support for `SourceType` on `Charge.PaymentMethodDetails.StripeBalance`, `ConfirmationToken.PaymentMethodPreview.StripeBalance`, `ConfirmationTokenPaymentMethodDataStripeBalanceOptions`, `PaymentAttemptRecord.PaymentMethodDetails.StripeBalance`, `PaymentIntentPaymentMethodDataStripeBalanceOptions`, `PaymentMethod.StripeBalance`, `PaymentMethodStripeBalanceOptions`, `PaymentRecord.PaymentMethodDetails.StripeBalance`, and `SetupIntentPaymentMethodDataStripeBalanceOptions`
  * Add support for `IntegrationIdentifier` on `Checkout.SessionCreateOptions` and `Checkout.Session`
  * Change type of `CheckoutSessionLineItemPriceDataProductDataTaxDetailsOptions.TaxCode`, `InvoiceLineItemPriceDataProductDataTaxDetailsOptions.TaxCode`, `InvoiceLinePriceDataProductDataTaxDetailsOptions.TaxCode`, `PaymentLinkLineItemPriceDataProductDataTaxDetailsOptions.TaxCode`, `PlanProductTaxDetailsOptions.TaxCode`, `PriceProductDataTaxDetailsOptions.TaxCode`, and `ProductTaxDetailsOptions.TaxCode` from `string` to `emptyable(string)`
  * Add support for `Crypto` on `CheckoutSessionPaymentMethodOptionsOptions`
  * Add support for `PendingInvoiceItemInterval` on `CheckoutSessionSubscriptionDataOptions`
  * Add support for `AuBecsDebit`, `BacsDebit`, `Boleto`, `Link`, `SepaDebit`, and `UsBankAccount` on `Checkout.Session.CurrentAttempt.PaymentMethodDetails`
  * Add support for `Metadata` on `CreditNoteLineItem` and `CreditNoteLineOptions`
  * Add support for `SelectedFulfillmentOptionOverrides` on `DelegatedCheckout.RequestedSession.FulfillmentDetails`
  * Add support for `LineItemKeys` on `DelegatedCheckout.RequestedSession.FulfillmentDetails.FulfillmentOptions.Digital.DigitalOptions` and `DelegatedCheckout.RequestedSession.FulfillmentDetails.FulfillmentOptions.Shipping.ShippingOptions`
  * Add support for `QuantityDecimal` on `InvoiceInvoiceItemOptions`, `InvoiceItemCreateOptions`, `InvoiceItemUpdateOptions`, `InvoiceItem`, `InvoiceLineItemUpdateOptions`, `InvoiceLineItem`, and `InvoiceLineOptions`
  * Add support for `ExpiresAfterSeconds` on `Invoice.PaymentSettings.PaymentMethodOptions.Pix`, `InvoicePaymentSettingsPaymentMethodOptionsPixOptions`, `QuotePreviewInvoice.PaymentSettings.PaymentMethodOptions.Pix`, `Subscription.PaymentSettings.PaymentMethodOptions.Pix`, and `SubscriptionPaymentSettingsPaymentMethodOptionsPixOptions`
  * ⚠️ Add support for `Level` on `IssuingAuthorizationRiskAssessmentCardTestingRiskOptions` and `IssuingAuthorizationRiskAssessmentMerchantDisputeRiskOptions`
  * ⚠️ Remove support for `RiskLevel` on `IssuingAuthorizationRiskAssessmentCardTestingRiskOptions` and `IssuingAuthorizationRiskAssessmentMerchantDisputeRiskOptions`
  * Add support for `LifecycleControls` on `Issuing.CardCreateOptions` and `Issuing.Card`
  * ⚠️ Change type of `PaymentAttemptRecord.PaymentMethodDetails.Card.ExpMonth` and `PaymentRecord.PaymentMethodDetails.Card.ExpMonth` from `longInteger` to `nullable(longInteger)`
  * ⚠️ Change type of `PaymentAttemptRecord.PaymentMethodDetails.Card.ExpYear` and `PaymentRecord.PaymentMethodDetails.Card.ExpYear` from `longInteger` to `nullable(longInteger)`
  * ⚠️ Change type of `PaymentAttemptRecord.PaymentMethodDetails.Card.Moto` and `PaymentRecord.PaymentMethodDetails.Card.Moto` from `boolean` to `nullable(boolean)`
  * Add support for `Cryptogram`, `ElectronicCommerceIndicator`, `ExemptionIndicatorApplied`, and `ExemptionIndicator` on `PaymentAttemptRecord.PaymentMethodDetails.Card.ThreeDSecure` and `PaymentRecord.PaymentMethodDetails.Card.ThreeDSecure`
  * Add support for `Surcharge` on `PaymentIntent.AmountDetails` and `PaymentIntentAmountDetailsOptions`
  * Add support for `MandateOptions` on `PaymentIntent.PaymentMethodOptions.StripeBalance` and `PaymentIntentPaymentMethodOptionsStripeBalanceOptions`
  * Add support for `AmountDetails` and `PaymentDetails` on `PaymentIntentDecrementAuthorizationOptions`
  * Add support for `UpiHandleRedirectOrDisplayQrCode` on `PaymentIntent.NextAction` and `SetupIntent.NextAction`
  * Add support for `ManagedPayments` on `PaymentLinkCreateOptions` and `PaymentLink`
  * Add support for `RecommendedAction` and `Signals` on `Radar.PaymentEvaluation`
  * ⚠️ Remove support for `Insights` on `Radar.PaymentEvaluation`
  * Add support for `StripeBalance` on `SetupIntent.PaymentMethodOptions` and `SetupIntentPaymentMethodOptionsOptions`
  * Add support for `Recurri

_…truncated…_

### v51.0.1  (v51.0.1)
<https://github.com/stripe/stripe-dotnet/releases/tag/v51.0.1>

* [#3366](https://github.com/stripe/stripe-dotnet/pull/3366) Fix emptyable property serialization for third-party serializers
  
  * Fixes a bug where serializing Options objects through a third-party serializer (e.g. AWS Lambda) could cause the SDK to unintentionally clear fields on the API. Emptyable properties now have null-skipping annotations so third-party serializers omit unset properties during round-trips.

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v51.0.1/CHANGELOG.md).

### v51.0.0  (v51.0.0)
<https://github.com/stripe/stripe-dotnet/releases/tag/v51.0.0>

This release changes the pinned API version to `2026-03-25.dahlia` and contains breaking changes (prefixed with ⚠️ below). There's also a [detailed migration guide](https://github.com/stripe/stripe-dotnet/wiki/Migration-guide-for-v51) to simplify your upgrade process.

Please review details for the breaking changes and alternatives in the [Stripe API changelog](https://docs.stripe.com/changelog/dahlia) before upgrading.

* ⚠️ **Breaking change:** [#3338](https://github.com/stripe/stripe-dotnet/pull/3338) Throw an error when using the wrong webhook parsing method
* ⚠️ **Breaking change:** [#3328](https://github.com/stripe/stripe-dotnet/pull/3328) Drop support for .NET 5 & 7
* ⚠️ **Breaking change:** [#3327](https://github.com/stripe/stripe-dotnet/pull/3327) Migrate core deserialization and default JSON library to System.Text.Json
  - System.Text.Json replaces Newtonsoft Json.NET as the default JSON library used in serialization and deserialization of Stripe.net objects.  This is most likely non-breaking for most users.
  - Serializing Stripe objects using either System.Text.Json or Newtonsoft Json.NET now represents decimal-format strings as JSON string values to match the Stripe API format.
* ⚠️ **Breaking change:** [#3342](https://github.com/stripe/stripe-dotnet/pull/3342) Replace Emptyable<T> with SetTracker pattern for explicit null support
  - ⚠️  Full support for unsetting metadata entries and certain Options properties.  Set the metadata entry or nullable property to `null` and the SDK will send an empty string for V1 APIs and a null value for V2 APIs.
    - ⚠️  This changes the meaning of setting a property to `null` if that property is defined as nullable in our API Ref.  If you currently pre-initialize your Options values to null this could have unintended consequences.
  - ⚠️  Removed `IEmptyable`, `IEmptyable<T>`, `Emptyable<T>`, `EmptyableConverter<T>`, and `STJEmptyableConverter<T>` - replaced by SetTracker pattern on Options properties.
* ⚠️ **Breaking change:** [#3329](https://github.com/stripe/stripe-dotnet/pull/3329) Regenerate with decimal_string enabled for v2 APIs
  - V2 API decimal fields changed type from `string` to `decimal?`. Code that reads or writes these fields as `string` will need to use `decimal?` instead. Affected fields:
    - **AccountPersonRelationship**: `PercentOwnership`
    - **AccountIdentityIndividualRelationship**: `PercentOwnership`
    - Options: `AccountCreateIdentityIndividualRelationshipOptions`, `AccountUpdateIdentityIndividualRelationshipOptions`, `AccountTokenCreateIdentityIndividualRelationshipOptions`, `PersonCreateRelationshipOptions`, `PersonUpdateRelationshipOptions`, `PersonTokenCreateRelationshipOptions`
* [#3300](https://github.com/stripe/stripe-dotnet/pull/3300) Add StringEnum JSON converters for batch jobs
* [#3330](https://github.com/stripe/stripe-dotnet/pull/3330) Bump System.Text.Json from 6.0.0 to 6.0.10
* [#3321](https://github.com/stripe/stripe-dotnet/pull/3321) Add runtime support for V2 int64 string-encoded fields

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v51.0.0/CHANGELOG.md).


## v50.x

### v50.5.0-alpha.4  (v50.5.0-alpha.4)
<https://github.com/stripe/stripe-dotnet/releases/tag/v50.5.0-alpha.4>

* [#3324](https://github.com/stripe/stripe-dotnet/pull/3324) Update generated code for private-preview
  * Add support for `SimulateCryptoDeposit` test helper method on resource `PaymentIntent`
  * Add support for `DepositOptions` and `Mode` on `PaymentIntent.PaymentMethodOptions.Crypto` and `PaymentIntentPaymentMethodOptionsCryptoOptions`
  * Add support for `CryptoDisplayDetails` on `PaymentIntent.NextAction`
* [#3319](https://github.com/stripe/stripe-dotnet/pull/3319) Update generated code for private-preview
  * Add support for new resources `Orchestration.PaymentAttempt` and `Radar.CustomerEvaluation`
  * Add support for `Get` method on resource `Orchestration.PaymentAttempt`
  * Add support for `Create` and `Update` methods on resource `Radar.CustomerEvaluation`
  * Add support for `Approve` method on resource `Checkout.Session`
  * Add support for `ReportAuthenticated`, `ReportCanceled`, `ReportFailed`, `ReportGuaranteed`, `ReportInformational`, and `ReportRefund` methods on resource `PaymentAttemptRecord`
  * Add support for `CreateUsPaperCheckOnApplication` on `AccountSessionComponentsCheckScanningFeaturesOptions`
  * Add support for `ApprovalMethod` on `Checkout.SessionCreateOptions` and `Checkout.Session`
  * Add support for `CurrentAttempt` on `Checkout.Session`
  * Add support for `SelectedFulfillmentOptionOverrides` on `DelegatedCheckoutRequestedSessionFulfillmentDetailsOptions`
  * Add support for `PricingPlanSubscriptionDetails` on `InvoiceItem.Parent` and `InvoiceLineItem.Parent`
  * ⚠️ Remove support for `LicenseFeeSubscriptionDetails` on `InvoiceItem.Parent` and `InvoiceLineItem.Parent`
  * ⚠️ Remove support for `PricingPlanSubscription` and `PricingPlanVersion` on `InvoiceItem.Parent.RateCardSubscriptionDetails` and `InvoiceLineItem.Parent.RateCardSubscriptionDetails`
  * Add support for `TokenDetails` on `Issuing.Authorization`
  * Add support for `FailureCode` on `PaymentRecordFailedOptions` and `PaymentRecordReportPaymentAttemptFailedOptions`
  * Add support for `RecurringInterval` on `SharedPaymentGrantedTokenUsageLimitsOptions`
  * Add support for `HomeRuleTax` on `Tax.Registration.CountryOptions.Us` and `TaxRegistrationCountryOptionsUsOptions`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v50.5.0-alpha.4/CHANGELOG.md).

### v50.5.0-alpha.3  (v50.5.0-alpha.3)
<https://github.com/stripe/stripe-dotnet/releases/tag/v50.5.0-alpha.3>

* [#3314](https://github.com/stripe/stripe-dotnet/pull/3314) Update generated code for private-preview
  * Add support for new resource `Radar.IssuingAuthorizationEvaluation`
  * Add support for `Create` method on resource `Radar.IssuingAuthorizationEvaluation`
  * ⚠️ Rename `AffiliateAttributions` to `AffiliateAttribution` on `DelegatedCheckout.RequestedSessionConfirmOptions` and `DelegatedCheckout.RequestedSessionCreateOptions`
  * Add support for `AmountToCounter` on `Dispute`
  * Add support for `FrozenFields` on `InvoiceItem`
  * Add support for `Consumer` on `V2.Core.Account.Configuration.CardCreator.Capabilities`, `V2.Core.Account.Identity.Attestations.TermsOfService.CardCreator`, `V2CoreAccountConfigurationCardCreatorCapabilitiesOptions`, and `V2CoreAccountIdentityAttestationsTermsOfServiceCardCreatorOptions`
  * Add support for `FifthThird` on `V2.Core.Account.Configuration.CardCreator.Capabilities.Commercial`, `V2.Core.Account.Identity.Attestations.TermsOfService.CardCreator.Commercial`, `V2CoreAccountConfigurationCardCreatorCapabilitiesCommercialOptions`, and `V2CoreAccountIdentityAttestationsTermsOfServiceCardCreatorCommercialOptions`
  * Add support for `PrepaidCard` on `V2.Core.Account.Configuration.CardCreator.Capabilities.Commercial.CrossRiverBank`, `V2.Core.Account.Identity.Attestations.TermsOfService.CardCreator.Commercial.CrossRiverBank`, `V2CoreAccountConfigurationCardCreatorCapabilitiesCommercialCrossRiverBankOptions`, and `V2CoreAccountIdentityAttestationsTermsOfServiceCardCreatorCommercialCrossRiverBankOptions`
  * Add support for `PaymentMethodData` on `V2.Payments.OffSessionPaymentCreateOptions`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v50.5.0-alpha.3/CHANGELOG.md).

### v50.5.0-alpha.2  (v50.5.0-alpha.2)
<https://github.com/stripe/stripe-dotnet/releases/tag/v50.5.0-alpha.2>

This release changes the pinned API version to `2026-03-04.preview`.

* [#3309](https://github.com/stripe/stripe-dotnet/pull/3309) Update generated code for private-preview
  * Add support for new resources `Billing.AlertRecovered` and `Profile`
  * Add support for `Reauthorize` method on resource `PaymentIntent`
  * Add support for `Settings` on `QuoteLine.Action.AddDiscount`, `QuoteLine.Action.AddItem.Discount`, `QuoteLine.Action.SetDiscounts`, `QuoteLine.Action.SetItems.Discount`, `QuotePreviewSubscriptionSchedule.Phase.Discount`, `QuotePreviewSubscriptionSchedule.Phase.Item.Discount`, `SubscriptionSchedule.Phase.Discount`, and `SubscriptionSchedule.Phase.Item.Discount`
  * Add support for `SmartDisputes` on `Account.Settings`, `AccountSettingsOptions`, `V2.Core.Account.Configuration.Merchant`, and `V2CoreAccountConfigurationMerchantOptions`
  * Add support for `EmailCustomersOnSuccessfulPayment` on `Account.Settings.Payments` and `AccountSettingsPaymentsOptions`
  * Add support for `BalanceUpdateDetails` on `Billing.CreditBalanceSummary.Balance`
  * Add support for `Reauthorization` and `ReauthorizeBefore` on `Charge.PaymentMethodDetails.CardPresent`, `Charge.PaymentMethodDetails.Card`, `ConfirmationToken.PaymentMethodPreview.Card.GeneratedFrom.PaymentMethodDetails.CardPresent`, `PaymentAttemptRecord.PaymentMethodDetails.CardPresent`, `PaymentMethod.Card.GeneratedFrom.PaymentMethodDetails.CardPresent`, and `PaymentRecord.PaymentMethodDetails.CardPresent`
  * Add support for `Location` and `Reader` on `Charge.PaymentMethodDetails.CardPresent`, `Charge.PaymentMethodDetails.InteracPresent`, `ConfirmationToken.PaymentMethodPreview.Card.GeneratedFrom.PaymentMethodDetails.CardPresent`, `PaymentAttemptRecord.PaymentMethodDetails.CardPresent`, `PaymentAttemptRecord.PaymentMethodDetails.InteracPresent`, `PaymentMethod.Card.GeneratedFrom.PaymentMethodDetails.CardPresent`, `PaymentRecord.PaymentMethodDetails.CardPresent`, and `PaymentRecord.PaymentMethodDetails.InteracPresent`
  * Add support for `ManagedPayments` on `Checkout.SessionCreateOptions`, `Checkout.Session`, `PaymentIntent`, `SetupIntent`, and `Subscription`
  * Add support for `Digital` on `DelegatedCheckout.RequestedSession.FulfillmentDetails.FulfillmentOptions`, `DelegatedCheckout.RequestedSession.FulfillmentDetails.SelectedFulfillmentOption`, and `DelegatedCheckoutRequestedSessionFulfillmentDetailsSelectedFulfillmentOptionOptions`
  * Add support for `AffiliateAttributions` on `DelegatedCheckout.RequestedSessionConfirmOptions`, `DelegatedCheckout.RequestedSessionCreateOptions`, and `DelegatedCheckout.RequestedSession`
  * Add support for `FulfillmentType` on `DelegatedCheckout.RequestedSession.LineItemDetail`
  * Add support for `MarketplaceSellerDetails`, `NetworkProfile`, `PrivacyNoticeUrl`, `ReturnPolicyUrl`, `StorePolicyUrl`, and `TermsOfServiceUrl` on `DelegatedCheckout.RequestedSession.SellerDetails`
  * Add support for `AmountToCounter` on `DisputeUpdateOptions`
  * Add support for `DisplayName` and `ServiceUserNumber` on `Mandate.PaymentMethodDetails.BacsDebit`
  * Add support for `RequestReauthorization` on `PaymentIntent.PaymentMethodOptions.CardPresent`, `PaymentIntent.PaymentMethodOptions.Card`, `PaymentIntentPaymentMethodOptionsCardOptions`, and `PaymentIntentPaymentMethodOptionsCardPresentOptions`
  * Add support for `TransactionPurpose` on `PaymentIntent.PaymentMethodOptions.UsBankAccount` and `PaymentIntentPaymentMethodOptionsUsBankAccountOptions`
  * Add support for `OptionalItems` on `PaymentLinkUpdateOptions`
  * ⚠️ Remove support for `CardIssuerDecline` on `Radar.PaymentEvaluation.Insights`
  * Add support for `PaymentBehavior` on `SubscriptionItemDeleteOptions`
  * Add support for `BillingCycleAnchor` on `Subscription.TrialSettings.EndBehavior`
  * Add support for `Lk` on `Tax.Registration.CountryOptions` and `TaxRegistrationCountryOptionsOptions`
  * Add support for `Cellular` and `StripeS710` on `Terminal.ConfigurationCreateOptions`, `Terminal.ConfigurationUpdateOptions`, and `Terminal.Configuration`
  * Add support for `RecipientOnboarding` and `RecipientUpdate` on `V2.Core.AccountLink.UseCase` and `V2CoreAccountLinkUseCaseOptions`
  * Add support for `Consumer` on `V2.Core.Account.Configuration.Storer.Capabilities` and `V2CoreAccountConfigurationStorerCapabilitiesOptions`
  * Add support for `FundsUsageType` on `V2.MoneyManagement.FinancialAccount.Storage` and `V2MoneyManagementFinancialAccountStorageOptions`
  * Add support for `Purpose` on `V2.MoneyManagement.OutboundPaymentCreateOptions` and `V2.MoneyManagement.OutboundPayment`
  * Add support for `BranchNumber` and `SwiftCode` on `V2.MoneyManagement.PayoutMethod.BankAccount`
  * Add support for snapshot event `BillingAlertRecovered` with resource `Billing.AlertRecovered`
  * Add support for snapshot events `ReserveHoldCreated` and `ReserveHoldUpdated` with resource `Reserve.Hold`
  * Add support for snapshot events `ReservePlanCreated`, `ReservePlanDisabled`, `ReservePlanExpired`, and `ReservePlanUpdated` with resource `Reserve.Plan`
  * Add support for snapshot event `ReserveReleaseCreated` with resource `Reserve.Release`
  * Add support for event notification `V2BillingRateCardCustomPricingUnitOverageRateCreatedEvent` with related object `V2.Billing.RateCardCustomPricingUnitOverageRate`
  * Add support for event notifications `V2IamStripeAccessGrantApprovedEvent`, `V2IamStripeAccessGrantCanceledEvent`, `V2IamStripeAccessGrantDeniedEvent`, `V2IamStripeAccessGrantRemovedEvent`, `V2IamStripeAccessGrantRequestedEvent`, and `V2IamStripeAccessGrantUpdatedEvent`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v50.5.0-alpha.2/CHANGELOG.md).

### v50.5.0-beta.1  (v50.5.0-beta.1)
<https://github.com/stripe/stripe-dotnet/releases/tag/v50.5.0-beta.1>

This release changes the pinned API version to `2026-02-25.preview`.

* [#3298](https://github.com/stripe/stripe-dotnet/pull/3298) Update generated code for beta
  * Add support for `SmartDisputes` on `Account.Settings`, `AccountSettingsOptions`, `V2.Core.Account.Configuration.Merchant`, and `V2CoreAccountConfigurationMerchantOptions`
  * Add support for `EmailCustomersOnSuccessfulPayment` on `Account.Settings.Payments` and `AccountSettingsPaymentsOptions`
  * Add support for `ManagedPayments` on `Checkout.SessionCreateOptions`, `Checkout.Session`, `PaymentIntent`, `SetupIntent`, and `Subscription`
  * Add support for `Purpose` on `V2.MoneyManagement.OutboundPaymentCreateOptions` and `V2.MoneyManagement.OutboundPayment`
  * Add support for `BranchNumber` and `SwiftCode` on `V2.MoneyManagement.PayoutMethod.BankAccount`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v50.5.0-beta.1/CHANGELOG.md).

### v50.5.0-alpha.1  (v50.5.0-alpha.1)
<https://github.com/stripe/stripe-dotnet/releases/tag/v50.5.0-alpha.1>

This release changes the pinned API version to `2026-02-25.preview`.

* [#3303](https://github.com/stripe/stripe-dotnet/pull/3303) Update generated code for private-preview
  * Add support for new resource `AccountSignals`
  * Add support for `Get` method on resource `AccountSignals`
  * Add support for `AggregationPeriod`, `GroupBy`, and `TriggeredAt` on `Billing.AlertTriggered`
  * Add support for `ExternalAccountCollection` on `AccountLinkCollectionOptionsOptions`
  * Add support for `FundingSource` on `ApplicationFee`
  * Add support for `Hosted` and `UiMode` on `FinancialConnections.SessionCreateOptions` and `FinancialConnections.Session`
  * Add support for `Url` on `FinancialConnections.Session`
  * Add support for `BillingCycleAnchor` on `SubscriptionTrialSettingsEndBehaviorOptions`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v50.5.0-alpha.1/CHANGELOG.md).

### v50.4.1  (v50.4.1)
<https://github.com/stripe/stripe-dotnet/releases/tag/v50.4.1>

* [#3313](https://github.com/stripe/stripe-dotnet/pull/3313) Add Stripe-Request-Trigger header
* [#3310](https://github.com/stripe/stripe-dotnet/pull/3310) Add agent information to UserAgent

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v50.4.1/CHANGELOG.md).

### v50.4.0  (v50.4.0)
<https://github.com/stripe/stripe-dotnet/releases/tag/v50.4.0>

This release changes the pinned API version to `2026-02-25.clover`.

* [#3304](https://github.com/stripe/stripe-dotnet/pull/3304) Update generated code
  * Add support for new resources `Reserve.Hold`, `Reserve.Plan`, and `Reserve.Release`
  * Add support for `Location` and `Reader` on `Charge.PaymentMethodDetails.CardPresent`, `Charge.PaymentMethodDetails.InteracPresent`, `ConfirmationToken.PaymentMethodPreview.Card.GeneratedFrom.PaymentMethodDetails.CardPresent`, `PaymentAttemptRecord.PaymentMethodDetails.CardPresent`, `PaymentAttemptRecord.PaymentMethodDetails.InteracPresent`, `PaymentMethod.Card.GeneratedFrom.PaymentMethodDetails.CardPresent`, `PaymentRecord.PaymentMethodDetails.CardPresent`, and `PaymentRecord.PaymentMethodDetails.InteracPresent`
  * Add support for `DisplayName` and `ServiceUserNumber` on `Mandate.PaymentMethodDetails.BacsDebit`
  * Add support for `TransactionPurpose` on `PaymentIntent.PaymentMethodOptions.UsBankAccount` and `PaymentIntentPaymentMethodOptionsUsBankAccountOptions`
  * Add support for `OptionalItems` on `PaymentLinkUpdateOptions`
  * Remove support for unused `CardIssuerDecline` on `Radar.PaymentEvaluation.Insights`
  * Add support for `PaymentBehavior` on `SubscriptionItemDeleteOptions`
  * Add support for `Lk` on `Tax.Registration.CountryOptions` and `TaxRegistrationCountryOptionsOptions`
  * Add support for `Cellular` and `StripeS710` on `Terminal.ConfigurationCreateOptions`, `Terminal.ConfigurationUpdateOptions`, and `Terminal.Configuration`
  * Add support for snapshot events `ReserveHoldCreated` and `ReserveHoldUpdated` with resource `Reserve.Hold`
  * Add support for snapshot events `ReservePlanCreated`, `ReservePlanDisabled`, `ReservePlanExpired`, and `ReservePlanUpdated` with resource `Reserve.Plan`
  * Add support for snapshot event `ReserveReleaseCreated` with resource `Reserve.Release`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v50.4.0/CHANGELOG.md).

### v50.4.0-alpha.4  (v50.4.0-alpha.4)
<https://github.com/stripe/stripe-dotnet/releases/tag/v50.4.0-alpha.4>

* [#3302](https://github.com/stripe/stripe-dotnet/pull/3302) Update generated code for private-preview
  * Add support for `SpendThreshold` on `Billing.AlertCreateOptions` and `Billing.Alert`
  * Add support for `InvoiceItem`, `ProrationDetails`, `Proration`, and `Subscription` on `InvoiceLineItem.Parent.ScheduleDetails`
  * Add support for `Custom` on `PaymentMethodUpdateOptions`
  * Add support for `PaymentMethodReference` and `Usage` on `PaymentMethod.Custom`
  * ⚠️ Change type of `QuoteSubscriptionDataOverridesOptions.BillingSchedules` from `emptyable(array(billing_schedules_update_specs))` to `array(billing_schedules_update_specs)`
  * Add support for `OutstandingUsageThrough` and `UnusedTimeFrom` on `SubscriptionBillForOptions`
  * ⚠️ Remove support for `OutstandingUsage` and `UnusedTime` on `SubscriptionBillForOptions`
  * ⚠️ Remove support for `PaymentBehavior` on `SubscriptionResumeOptions`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v50.4.0-alpha.4/CHANGELOG.md).

### v50.4.0-alpha.3  (v50.4.0-alpha.3)
<https://github.com/stripe/stripe-dotnet/releases/tag/v50.4.0-alpha.3>

* [#3301](https://github.com/stripe/stripe-dotnet/pull/3301) Update generated code for private-preview
  * Add support for new resources `V2.Billing.CadenceSpendModifier`, `V2.Billing.OneTimeItem`, and `V2.Billing.RateCardCustomPricingUnitOverageRate`
  * Add support for `Create`, `Delete`, `Get`, and `List` methods on resource `V2.Billing.RateCardCustomPricingUnitOverageRate`
  * Add support for `Create`, `Get`, `List`, and `Update` methods on resource `V2.Billing.OneTimeItem`
  * Add support for `Get` method on resource `V2.Billing.CadenceSpendModifier`
  * Add support for `SettlementType` on `ApplicationFee`
  * Add support for `RateCardCustomPricingUnitOverageRateDetails` on `InvoiceItem.Pricing` and `InvoiceLineItem.Pricing`
  * Add support for `DefaultSettings` on `InvoiceScheduleDetailsOptions`
  * Add support for `PaymentBehavior` on `SubscriptionResumeOptions`
  * Add support for `EffectiveAt` and `SpendModifierRule` on `V2.Billing.IntentAction.Apply`, `V2.Billing.IntentAction.Remove`, `V2BillingIntentActionApplyOptions`, and `V2BillingIntentActionRemoveOptions`
  * Change type of `V2.Billing.IntentAction.Apply.Type`, `V2.Billing.IntentAction.Remove.Type`, `V2BillingIntentActionApplyOptions.Type`, and `V2BillingIntentActionRemoveOptions.Type` from `literal('invoice_discount_rule')` to `enum('invoice_discount_rule'|'spend_modifier_rule')`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v50.4.0-alpha.3/CHANGELOG.md).

### v50.4.0-alpha.2  (v50.4.0-alpha.2)
<https://github.com/stripe/stripe-dotnet/releases/tag/v50.4.0-alpha.2>

* [#3299](https://github.com/stripe/stripe-dotnet/pull/3299) Update generated code for private-preview
  * Add support for new resource `V2.Core.ConnectionSession`
  * Add support for `Create` and `Get` methods on resource `V2.Core.ConnectionSession`
  * Add support for `List` method on resources `V2.Payments.SettlementAllocationIntentSplit` and `V2.Payments.SettlementAllocationIntent`
  * Add support for `AgenticCommerceSettings` on `AccountSessionComponentsOptions`
  * Add support for `TerminalHardwareOrders` and `TerminalHardwareShop` on `AccountSession.Components` and `AccountSessionComponentsOptions`
  * Add support for `NetworkCostPassthroughReport` on `AccountSession.Components`
  * Add support for `CadenceData` on `V2.Billing.IntentCreateOptions` and `V2.Billing.Intent`
  * Add support for `CancellationDetails` on `V2.Billing.IntentAction.Deactivate`, `V2.Billing.PricingPlanSubscription`, and `V2BillingIntentActionDeactivateOptions`
  * Add support for `ContactPhone` on `V2.Core.AccountCreateOptions`, `V2.Core.AccountTokenCreateOptions`, `V2.Core.AccountUpdateOptions`, and `V2.Core.Account`
  * Add support for `RegistrationDate` on `V2.Core.Account.Identity.BusinessDetails`, `V2CoreAccountIdentityBusinessDetailsOptions`, and `V2CoreAccountTokenIdentityBusinessDetailsOptions`
  * Add support for `Reference` on `V2.MoneyManagement.Adjustment`
  * Add support for `AccruedFees` on `V2.MoneyManagement.FinancialAccount`
  * Add support for `StartingBalance` on `V2.MoneyManagement.FinancialAccount.Payments`
  * Add support for `AccountHolderAddress` and `AccountHolderName` on `V2.MoneyManagement.FinancialAddress.Credentials.UsBankAccount`
  * Add support for `Fingerprint` on `V2.MoneyManagement.PayoutMethod.Card`
  * Add support for `CardSpend` on `V2.MoneyManagement.ReceivedCredit` and `V2.MoneyManagement.ReceivedDebit`
  * Add support for `ApplicationFeeRefund`, `ApplicationFee`, `Charge`, `Dispute`, `Payout`, `Refund`, `ReserveHold`, `ReserveRelease`, `Topup`, `TransferReversal`, and `Transfer` on `V2.MoneyManagement.Transaction.Flow` and `V2.MoneyManagement.TransactionEntry.TransactionDetails.Flow`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v50.4.0-alpha.2/CHANGELOG.md).

### v50.4.0-beta.1  (v50.4.0-beta.1)
<https://github.com/stripe/stripe-dotnet/releases/tag/v50.4.0-beta.1>

This release changes the pinned API version to `2026-01-28.preview`.

* [#3291](https://github.com/stripe/stripe-dotnet/pull/3291) Update generated code for beta
  * Add support for new resource `FinancialConnections.Authorization`
  * Add support for `Get` method on resource `FinancialConnections.Authorization`
  * Add support for `DetachPayment` method on resource `Invoice`
  * Remove support for `Cancel`, `ListLineItems`, and `Reopen` methods on resource `Order`
  * Remove support for `AttachCadence` method on resource `Subscription`
  * Add support for `AdditionalFiles` and `Site` on `Account.Settings.PaypayPayments` and `AccountSettingsPaypayPaymentsOptions`
  * Remove support for `Capital` on `Account.Settings`
  * Add support for `Authorization` and `StatusDetails` on `FinancialConnections.Account`
  * Add support for `RelinkOptions` on `FinancialConnections.SessionCreateOptions` and `FinancialConnections.Session`
  * Add support for `RelinkResult` on `FinancialConnections.Session`
  * Remove support for `BillingCadence` on `InvoiceCreatePreviewOptions`, `SubscriptionCreateOptions`, `SubscriptionUpdateOptions`, and `Subscription`
  * Remove support for `BillingCadenceDetails` on `Invoice.Parent` and `QuotePreviewInvoice.Parent`
  * Add support for `CarRentalData`, `FlightData`, and `LodgingData` on `PaymentIntent.PaymentDetails`
  * Add support for `AlternativeReference` on `V2.Core.Vault.GbBankAccount`, `V2.Core.Vault.UsBankAccount`, and `V2.MoneyManagement.PayoutMethod`
  * Add support for `AccountHolderAddress` and `AccountHolderName` on `V2.MoneyManagement.FinancialAddress.Credentials.UsBankAccount`
  * Add support for `Fingerprint` on `V2.MoneyManagement.PayoutMethod.Card`
  * Add support for snapshot event `InvoicePaymentDetached` with resource `InvoicePayment`
* [#3276](https://github.com/stripe/stripe-dotnet/pull/3276) Add EventNotificationHandler example

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v50.4.0-beta.1/CHANGELOG.md).

### v50.4.0-alpha.1  (v50.4.0-alpha.1)
<https://github.com/stripe/stripe-dotnet/releases/tag/v50.4.0-alpha.1>

This release changes the pinned API version to `2026-01-28.preview`.

* [#3297](https://github.com/stripe/stripe-dotnet/pull/3297) Update generated code for private-preview
  * Add support for new resources `FrMealVouchersOnboarding`, `Reserve.Hold`, `Reserve.Plan`, and `Reserve.Release`
  * Add support for `Create`, `Get`, `List`, and `Update` methods on resource `FrMealVouchersOnboarding`
  * Add support for `Get` and `List` methods on resources `Reserve.Hold` and `Reserve.Release`
  * Add support for `Get` method on resource `Reserve.Plan`
  * Add support for `Pause` method on resource `Subscription`
  * Add support for `ServicePeriodDetails` on `Discount`
  * Add support for `AgenticCommerceSettings` on `AccountSession.Components`
  * Add support for `ServicePeriod` on `CouponCreateOptions` and `Coupon`
  * Change type of `InvoiceItem.Pricing.PriceDetails.Price` and `InvoiceLineItem.Pricing.PriceDetails.Price` from `string` to `expandable($Price)`
  * Add support for `Settings` on `InvoiceDiscountsOptions`, `InvoiceScheduleDetailsAmendmentDiscountActionAddOptions`, `InvoiceScheduleDetailsAmendmentDiscountActionSetOptions`, `InvoiceScheduleDetailsAmendmentItemActionAddDiscountOptions`, `InvoiceScheduleDetailsAmendmentItemActionSetDiscountOptions`, `InvoiceScheduleDetailsPhaseDiscountsOptions`, `InvoiceScheduleDetailsPhaseItemDiscountsOptions`, `InvoiceSubscriptionDetailsItemDiscountsOptions`, `QuoteLineActionAddDiscountOptions`, `QuoteLineActionAddItemDiscountOptions`, `QuoteLineActionSetDiscountOptions`, `QuoteLineActionSetItemDiscountOptions`, `SubscriptionDiscountsOptions`, `SubscriptionItemDiscountsOptions`, `SubscriptionScheduleAmendmentDiscountActionAddOptions`, `SubscriptionScheduleAmendmentDiscountActionSetOptions`, `SubscriptionScheduleAmendmentItemActionAddDiscountOptions`, `SubscriptionScheduleAmendmentItemActionSetDiscountOptions`, `SubscriptionSchedulePhaseDiscountsOptions`, and `SubscriptionSchedulePhaseItemDiscountsOptions`
  * Add support for `Subtotal` on `InvoiceLineItem`
  * Add support for `BillingCadence` on `SubscriptionListOptions`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v50.4.0-alpha.1/CHANGELOG.md).

### v50.3.0  (v50.3.0)
<https://github.com/stripe/stripe-dotnet/releases/tag/v50.3.0>

This release changes the pinned API version to `2026-01-28.clover`.

* [#3296](https://github.com/stripe/stripe-dotnet/pull/3296) Update generated code
  * Add support for new resource `Radar.PaymentEvaluation`
  * Add support for `Create` method on resource `Radar.PaymentEvaluation`
  * Add support for `AdjustableQuantity` on `LineItem`
  * Add support for `EnforceArithmeticValidation` on `PaymentIntentAmountDetailsOptions`
  * Add support for `Error` on `PaymentIntent.AmountDetails`
  * Remove support for `Bgn` on `Terminal.Configuration.Tipping` and `TerminalConfigurationTippingOptions`
  * Add support for `Topup` on `Treasury.ReceivedDebit.LinkedFlows`
  * Add support for `ContactPhone` on `V2.Core.AccountCreateOptions`, `V2.Core.AccountTokenCreateOptions`, `V2.Core.AccountUpdateOptions`, and `V2.Core.Account`
  * Add support for `RegistrationDate` on `V2.Core.Account.Identity.BusinessDetails`, `V2CoreAccountIdentityBusinessDetailsOptions`, and `V2CoreAccountTokenIdentityBusinessDetailsOptions`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v50.3.0/CHANGELOG.md).

### v50.3.0-alpha.1  (v50.3.0-alpha.1)
<https://github.com/stripe/stripe-dotnet/releases/tag/v50.3.0-alpha.1>

* [#3295](https://github.com/stripe/stripe-dotnet/pull/3295) Update generated code for private-preview
  * Remove support for `Pause` method on resource `Subscription`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v50.3.0-alpha.1/CHANGELOG.md).

### v50.2.0  (v50.2.0)
<https://github.com/stripe/stripe-dotnet/releases/tag/v50.2.0>

* [#3292](https://github.com/stripe/stripe-dotnet/pull/3292) Update generated code
  * Add support for event notifications `V2CoreAccountClosedEvent`, `V2CoreAccountCreatedEvent`, `V2CoreAccountIncludingConfigurationCustomerCapabilityStatusUpdatedEvent`, `V2CoreAccountIncludingConfigurationCustomerUpdatedEvent`, `V2CoreAccountIncludingConfigurationMerchantCapabilityStatusUpdatedEvent`, `V2CoreAccountIncludingConfigurationMerchantUpdatedEvent`, `V2CoreAccountIncludingConfigurationRecipientCapabilityStatusUpdatedEvent`, `V2CoreAccountIncludingConfigurationRecipientUpdatedEvent`, `V2CoreAccountIncludingDefaultsUpdatedEvent`, `V2CoreAccountIncludingFutureRequirementsUpdatedEvent`, `V2CoreAccountIncludingIdentityUpdatedEvent`, `V2CoreAccountIncludingRequirementsUpdatedEvent`, and `V2CoreAccountUpdatedEvent` with related object `V2.Core.Account`
  * Add support for event notification `V2CoreAccountLinkReturnedEvent`
  * Add support for event notifications `V2CoreAccountPersonCreatedEvent`, `V2CoreAccountPersonDeletedEvent`, and `V2CoreAccountPersonUpdatedEvent` with related object `V2.Core.AccountPerson`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v50.2.0/CHANGELOG.md).

### v50.2.0-alpha.3  (v50.2.0-alpha.3)
<https://github.com/stripe/stripe-dotnet/releases/tag/v50.2.0-alpha.3>

* [#3290](https://github.com/stripe/stripe-dotnet/pull/3290) Update generated code for private-preview
  * Add support for `RiskDetails` on `DelegatedCheckout.RequestedSession`
  * Remove support for `Description`, `Images`, and `Name` on `DelegatedCheckout.RequestedSession.LineItemDetail`
  * Add support for `Name` on `ProductCatalog.TrialOfferCreateOptions` and `ProductCatalog.TrialOffer`
  * Add support for `LoginFailed` and `RegistrationFailed` on `Radar.AccountEvaluation.Events` and `Radar.AccountEvaluationUpdateOptions`
  * Change type of `Radar.AccountEvaluationUpdateOptions.Type` from `literal('registration_succeeded')` to `enum('login_failed'|'login_succeeded'|'registration_failed'|'registration_succeeded')`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v50.2.0-alpha.3/CHANGELOG.md).

### v50.2.0-alpha.2  (v50.2.0-alpha.2)
<https://github.com/stripe/stripe-dotnet/releases/tag/v50.2.0-alpha.2>

* [#3283](https://github.com/stripe/stripe-dotnet/pull/3283) Update generated code for private-preview
  * Add support for `Pause` method on resource `Subscription`
  * Add support for `ExternalReference` on `Plan` and `Price`
  * Add support for `TrackingDetails` on `V2.MoneyManagement.OutboundPayment`
  * Add support for `PaperCheck` on `V2.MoneyManagement.OutboundPayment.DeliveryOptions` and `V2MoneyManagementOutboundPaymentDeliveryOptionsOptions`
  * Add support for event notification `V2CoreAccountIncludingFutureRequirementsUpdatedEvent` with related object `V2.Core.Account`
* [#3274](https://github.com/stripe/stripe-dotnet/pull/3274) Update generated code for private-preview
  * Add support for new resource `Tax.Location`
  * Add support for `Create`, `Get`, and `List` methods on resource `Tax.Location`
  * Add support for `PerformanceLocation` on `CheckoutSessionLineItemPriceDataProductDataTaxDetailsOptions`, `InvoiceLineItemPriceDataProductDataTaxDetailsOptions`, `InvoiceLinePriceDataProductDataTaxDetailsOptions`, `PaymentLinkLineItemPriceDataProductDataTaxDetailsOptions`, `ProductTaxDetailsOptions`, `Tax.CalculationLineItem`, and `TaxCalculationLineItemOptions`
  * Change type of `DelegatedCheckout.RequestedSessionUpdateOptions.Metadata` from `map(string: string)` to `emptyable(map(string: string))`
  * Change type of `DelegatedCheckout.RequestedSessionUpdateOptions.PaymentMethodData` from `payment_method_data` to `emptyable(payment_method_data)`
  * Change type of `DelegatedCheckout.RequestedSessionUpdateOptions.SharedMetadata` from `map(string: string)` to `emptyable(map(string: string))`
  * Add support for `Subscription` on `Invoice.Parent.ScheduleDetails` and `QuotePreviewInvoice.Parent.ScheduleDetails`
  * Change type of `PaymentIntentPaymentDetailsBenefitOptions.FrMealVoucher` and `SetupIntentSetupDetailsBenefitOptions.FrMealVoucher` from `payment_details_benefit_fr_meal_voucher` to `emptyable(payment_details_benefit_fr_meal_voucher)`
  * Add support for `TaxDetails` on `PlanProductOptions` and `PriceProductDataOptions`
  * Add support for `AdmissionsTax`, `AttendanceTax`, `EntertainmentTax`, `GrossReceiptsTax`, `HospitalityTax`, `LuxuryTax`, `ResortTax`, and `TourismTax` on `Tax.Registration.CountryOptions.Us`
  * Add support for `Requirements` on `TaxCode`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v50.2.0-alpha.2/CHANGELOG.md).

### v50.2.0-beta.1  (v50.2.0-beta.1)
<https://github.com/stripe/stripe-dotnet/releases/tag/v50.2.0-beta.1>

This release changes the pinned API version to `2025-12-15.preview`.

* [#3250](https://github.com/stripe/stripe-dotnet/pull/3250) Add EventNotificationHandler
* [#3263](https://github.com/stripe/stripe-dotnet/pull/3263) Update generated code for beta
  * Add support for new resources `Reserve.Hold`, `Reserve.Plan`, and `Reserve.Release`
  * Add support for `Get` and `List` methods on resources `Reserve.Hold` and `Reserve.Release`
  * Add support for `Get` method on resource `Reserve.Plan`
  * Change type of `V2.FinancialAddressGeneratedMicrodeposits.Amounts` from `amount` to `an object`
  * Change type of `CheckoutSessionPaymentMethodOptionsPaytoMandateOptionsOptions.Amount`, `PaymentIntentPaymentMethodOptionsPaytoMandateOptionsOptions.Amount`, and `SetupIntentPaymentMethodOptionsPaytoMandateOptionsOptions.Amount` from `longInteger` to `emptyable(longInteger)`
  * Change type of `CheckoutSessionPaymentMethodOptionsPaytoMandateOptionsOptions.AmountType`, `PaymentIntentPaymentMethodOptionsPaytoMandateOptionsOptions.AmountType`, and `SetupIntentPaymentMethodOptionsPaytoMandateOptionsOptions.AmountType` from `enum('fixed'|'maximum')` to `emptyable(enum('fixed'|'maximum'))`
  * Change type of `CheckoutSessionPaymentMethodOptionsPaytoMandateOptionsOptions.EndDate`, `PaymentIntentPaymentMethodOptionsPaytoMandateOptionsOptions.EndDate`, and `SetupIntentPaymentMethodOptionsPaytoMandateOptionsOptions.EndDate` from `string` to `emptyable(string)`
  * Change type of `CheckoutSessionPaymentMethodOptionsPaytoMandateOptionsOptions.PaymentSchedule`, `PaymentIntentPaymentMethodOptionsPaytoMandateOptionsOptions.PaymentSchedule`, and `SetupIntentPaymentMethodOptionsPaytoMandateOptionsOptions.PaymentSchedule` from `enum` to `emptyable(enum)`
  * Change type of `CheckoutSessionPaymentMethodOptionsPaytoMandateOptionsOptions.PaymentsPerPeriod`, `PaymentIntentPaymentMethodOptionsPaytoMandateOptionsOptions.PaymentsPerPeriod`, and `SetupIntentPaymentMethodOptionsPaytoMandateOptionsOptions.PaymentsPerPeriod` from `longInteger` to `emptyable(longInteger)`
  * Change type of `CheckoutSessionPaymentMethodOptionsPaytoMandateOptionsOptions.Purpose`, `PaymentIntentPaymentMethodOptionsPaytoMandateOptionsOptions.Purpose`, and `SetupIntentPaymentMethodOptionsPaytoMandateOptionsOptions.Purpose` from `enum` to `emptyable(enum)`
  * Change type of `CheckoutSessionPaymentMethodOptionsPaytoMandateOptionsOptions.StartDate` and `SetupIntentPaymentMethodOptionsPaytoMandateOptionsOptions.StartDate` from `string` to `emptyable(string)`
  * Add support for `AsyncWorkflows` on `PaymentIntent`
  * Add support for `Payto` on `QuotePreviewInvoice.PaymentSettings.PaymentMethodOptions`
  * Remove support for `Requested` on `V2.Core.Account.Configuration.Customer.Capabilities.AutomaticIndirectTax`, `V2.Core.Account.Configuration.Merchant.Capabilities.AchDebitPayments`, `V2.Core.Account.Configuration.Merchant.Capabilities.AcssDebitPayments`, `V2.Core.Account.Configuration.Merchant.Capabilities.AffirmPayments`, `V2.Core.Account.Configuration.Merchant.Capabilities.AfterpayClearpayPayments`, `V2.Core.Account.Configuration.Merchant.Capabilities.AlmaPayments`, `V2.Core.Account.Configuration.Merchant.Capabilities.AmazonPayPayments`, `V2.Core.Account.Configuration.Merchant.Capabilities.AuBecsDebitPayments`, `V2.Core.Account.Configuration.Merchant.Capabilities.BacsDebitPayments`, `V2.Core.Account.Configuration.Merchant.Capabilities.BancontactPayments`, `V2.Core.Account.Configuration.Merchant.Capabilities.BlikPayments`, `V2.Core.Account.Configuration.Merchant.Capabilities.BoletoPayments`, `V2.Core.Account.Configuration.Merchant.Capabilities.CardPayments`, `V2.Core.Account.Configuration.Merchant.Capabilities.CartesBancairesPayments`, `V2.Core.Account.Configuration.Merchant.Capabilities.CashappPayments`, `V2.Core.Account.Configuration.Merchant.Capabilities.EpsPayments`, `V2.Core.Account.Configuration.Merchant.Capabilities.FpxPayments`, `V2.Core.Account.Configuration.Merchant.Capabilities.GbBankTransferPayments`, `V2.Core.Account.Configuration.Merchant.Capabilities.GrabpayPayments`, `V2.Core.Account.Configuration.Merchant.Capabilities.IdealPayments`, `V2.Core.Account.Configuration.Merchant.Capabilities.JcbPayments`, `V2.Core.Account.Configuration.Merchant.Capabilities.JpBankTransferPayments`, `V2.Core.Account.Configuration.Merchant.Capabilities.KakaoPayPayments`, `V2.Core.Account.Configuration.Merchant.Capabilities.KlarnaPayments`, `V2.Core.Account.Configuration.Merchant.Capabilities.KonbiniPayments`, `V2.Core.Account.Configuration.Merchant.Capabilities.KrCardPayments`, `V2.Core.Account.Configuration.Merchant.Capabilities.LinkPayments`, `V2.Core.Account.Configuration.Merchant.Capabilities.MobilepayPayments`, `V2.Core.Account.Configuration.Merchant.Capabilities.MultibancoPayments`, `V2.Core.Account.Configuration.Merchant.Capabilities.MxBankTransferPayments`, `V2.Core.Account.Configuration.Merchant.Capabilities.NaverPayPayments`, `V2.Core.Account.Configuration.Merchant.Capabilities.OxxoPayments`, `V2.Core.Account.Configuration.Merchant.Capabilities.P24Payments`, `V2.Core.Account.Configuration.Merchant.Capabilities.PayByBankPayments`, `V2.Core.Account.Configuration.Merchant.Capabilities.PaycoPayments`, `V2.Core.Account.Configuration.Merchant.Capabilities.PaynowPayments`, `V2.Core.Account.Configuration.Merchant.Capabilities.PromptpayPayments`, `V2.Core.Account.Configuration.Merchant.Capabilities.RevolutPayPayments`, `V2.Core.Account.Configuration.Merchant.Capabilities.SamsungPayPayments`, `V2.Core.Account.Configuration.Merchant.Capabilities.SepaBankTransferPayments`, `V2.Core.Account.Configuration.Merchant.Capabilities.SepaDebitPayments`, `V2.Core.Account.Configuration.Merchant.Capabilities.StripeBalance.Payouts`, `V2.Core.Account.Configuration.Merchant.Capabilities.SwishPayments`, `V2.Core.Account.Configuration.Merchant.Capabilities.TwintPayments`, `V2.Core.Account.Configuration.Merchant.Capabilities.UsBankTransferPayments`, `V2.Core.Account.Configuration

_…truncated…_

### v50.2.0-alpha.1  (v50.2.0-alpha.1)
<https://github.com/stripe/stripe-dotnet/releases/tag/v50.2.0-alpha.1>

* [#3273](https://github.com/stripe/stripe-dotnet/pull/3273) Update generated code for private-preview
  * Add support for new resources `SharedPayment.GrantedToken`, `V2.Iam.ApiKey`, `V2.Payments.SettlementAllocationIntentSplit`, `V2.Payments.SettlementAllocationIntent`, and `V2.Tax.ManualRule`
  * Add support for `Get` method on resource `SharedPayment.GrantedToken`
  * Add support for `Create` and `Update` test helper methods on resource `SharedPayment.GrantedToken`
  * Add support for `Create`, `Deactivate`, `Get`, `List`, and `Update` methods on resource `V2.Tax.ManualRule`
  * Add support for `Cancel`, `Create`, `Get`, `Submit`, and `Update` methods on resource `V2.Payments.SettlementAllocationIntent`
  * Add support for `Cancel`, `Create`, and `Get` methods on resource `V2.Payments.SettlementAllocationIntentSplit`
  * Add support for `Create`, `Expire`, `Get`, `List`, `Rotate`, and `Update` methods on resource `V2.Iam.ApiKey`
  * Add support for `CheckScanning` on `AccountSessionComponentsOptions`
  * Add support for `TaxDetails` on `CheckoutSessionLineItemPriceDataProductDataOptions`, `InvoiceLineItemPriceDataProductDataOptions`, `InvoiceLinePriceDataProductDataOptions`, `PaymentLinkLineItemPriceDataProductDataOptions`, `ProductCreateOptions`, and `ProductUpdateOptions`
  * Add support for `PaymentMethodData` on `DelegatedCheckout.RequestedSessionConfirmOptions`
  * Add support for `ProductDetails` on `DelegatedCheckout.RequestedSession.LineItemDetail`
  * Add support for `Wallets` on `Issuing.CardListOptions`
  * Add support for `PrimaryAccountIdentifier` on `Issuing.Card.Wallets.ApplePay` and `Issuing.Card.Wallets.GooglePay`
  * Add support for `SharedPaymentGrantedToken` on `PaymentIntentConfirmOptions`, `PaymentIntentCreateOptions`, and `PaymentIntent`
  * Add support for `Instant` on `V2.Account.Configuration.RecipientData.Features.BankAccounts`, `V2.Core.Account.Configuration.Recipient.Capabilities.BankAccounts`, `V2AccountConfigurationRecipientDataFeaturesBankAccountsOptions`, and `V2CoreAccountConfigurationRecipientCapabilitiesBankAccountsOptions`
  * Add support for `CollectAt` on `V2.Billing.IntentAction.Deactivate`, `V2.Billing.IntentAction.Modify`, `V2.Billing.IntentAction.Subscribe`, `V2BillingIntentActionDeactivateOptions`, `V2BillingIntentActionModifyOptions`, and `V2BillingIntentActionSubscribeOptions`
  * Remove support for `BillingDetails` on `V2.Billing.IntentAction.Deactivate`, `V2.Billing.IntentAction.Modify`, `V2.Billing.IntentAction.Subscribe`, `V2BillingIntentActionDeactivateOptions`, `V2BillingIntentActionModifyOptions`, and `V2BillingIntentActionSubscribeOptions`
  * Add support for `Overrides` on `V2.Billing.IntentAction.Deactivate.PricingPlanSubscriptionDetails`, `V2.Billing.IntentAction.Modify.PricingPlanSubscriptionDetails`, `V2.Billing.IntentAction.Subscribe.PricingPlanSubscriptionDetails`, `V2BillingIntentActionDeactivatePricingPlanSubscriptionDetailsOptions`, `V2BillingIntentActionModifyPricingPlanSubscriptionDetailsOptions`, and `V2BillingIntentActionSubscribePricingPlanSubscriptionDetailsOptions`
  * Remove support for `Requested` on `V2.Core.Account.Configuration.CardCreator.Capabilities.Commercial.Celtic.ChargeCard`, `V2.Core.Account.Configuration.CardCreator.Capabilities.Commercial.Celtic.SpendCard`, `V2.Core.Account.Configuration.CardCreator.Capabilities.Commercial.CrossRiverBank.ChargeCard`, `V2.Core.Account.Configuration.CardCreator.Capabilities.Commercial.CrossRiverBank.SpendCard`, `V2.Core.Account.Configuration.CardCreator.Capabilities.Commercial.Lead.PrepaidCard`, `V2.Core.Account.Configuration.CardCreator.Capabilities.Commercial.Stripe.ChargeCard`, `V2.Core.Account.Configuration.CardCreator.Capabilities.Commercial.Stripe.PrepaidCard`, `V2.Core.Account.Configuration.Recipient.Capabilities.CryptoWallets`, `V2.Core.Account.Configuration.Storer.Capabilities.FinancialAddresses.CryptoWallets`, `V2.Core.Account.Configuration.Storer.Capabilities.HoldsCurrencies.Usdc`, `V2.Core.Account.Configuration.Storer.Capabilities.OutboundPayments.CryptoWallets`, and `V2.Core.Account.Configuration.Storer.Capabilities.OutboundTransfers.CryptoWallets`
  * Add support for `AlternativeReference` on `V2.Core.Vault.GbBankAccount`, `V2.Core.Vault.UsBankAccount`, and `V2.MoneyManagement.PayoutMethod`
  * Add support for `ManagedBy` and `Payments` on `V2.MoneyManagement.FinancialAccount`
  * Add support for `Speed` on `V2.MoneyManagement.OutboundPayment.DeliveryOptions`, `V2.MoneyManagement.OutboundPaymentQuote.DeliveryOptions`, `V2MoneyManagementOutboundPaymentDeliveryOptionsOptions`, and `V2MoneyManagementOutboundPaymentQuoteDeliveryOptionsOptions`
  * Add support for `Types` on `V2.MoneyManagement.FinancialAccountListOptions`
  * Add support for `TopImpactedAccounts` on `EventsV2CoreHealthApiErrorFiringEventImpact`, `EventsV2CoreHealthApiErrorResolvedEventImpact`, `EventsV2CoreHealthApiLatencyFiringEventImpact`, `EventsV2CoreHealthApiLatencyResolvedEventImpact`, `EventsV2CoreHealthPaymentMethodErrorFiringEventImpact`, and `EventsV2CoreHealthPaymentMethodErrorResolvedEventImpact`
  * Add support for event notifications `V2CoreHealthSepaDebitDelayedFiringEvent`, `V2CoreHealthSepaDebitDelayedResolvedEvent`, and `V2PaymentsSettlementAllocationIntentNotFoundEvent`
  * Add support for event notifications `V2PaymentsSettlementAllocationIntentCanceledEvent`, `V2PaymentsSettlementAllocationIntentCreatedEvent`, `V2PaymentsSettlementAllocationIntentErroredEvent`, `V2PaymentsSettlementAllocationIntentFundsNotReceivedEvent`, `V2PaymentsSettlementAllocationIntentMatchedEvent`, `V2PaymentsSettlementAllocationIntentSettledEvent`, and `V2PaymentsSettlementAllocationIntentSubmittedEvent` with related object `V2.Payments.SettlementAllocationIntent`
  * Add support for event notifications `V2PaymentsSettlementAllocationIntentSplitCanceledEvent`, `V2PaymentsSettlementAllocationIntentSplitCreatedEvent`, and `V2PaymentsSettlementAllocationIntentSplitSettledEvent` with related object `

_…truncated…_

### v50.1.0  (v50.1.0)
<https://github.com/stripe/stripe-dotnet/releases/tag/v50.1.0>

This release changes the pinned API version to `2025-12-15.clover`.

* [#3271](https://github.com/stripe/stripe-dotnet/pull/3271) Update generated code
  * Add support for new resources `V2.Core.AccountLink`, `V2.Core.AccountPersonToken`, `V2.Core.AccountPerson`, `V2.Core.AccountToken`, and `V2.Core.Account`
  * Add support for `Create` and `Get` methods on resources `V2.Core.AccountPersonToken` and `V2.Core.AccountToken`
  * Add support for `Create` method on resource `V2.Core.AccountLink`
  * Add support for `Close`, `Create`, `Get`, `List`, and `Update` methods on resource `V2.Core.Account`
  * Add support for `Create`, `Delete`, `Get`, `List`, and `Update` methods on resource `V2.Core.AccountPerson`
  * Add support for `CustomerAccount` on `Billing.CreditBalanceSummaryGetOptions`, `Billing.CreditBalanceSummary`, `Billing.CreditBalanceTransactionListOptions`, `Billing.CreditGrantCreateOptions`, `Billing.CreditGrantListOptions`, `Billing.CreditGrant`, `BillingPortal.SessionCreateOptions`, `BillingPortal.Session`, `CashBalance`, `Checkout.SessionCreateOptions`, `Checkout.SessionListOptions`, `Checkout.Session`, `ConfirmationToken.PaymentMethodPreview`, `CreditNoteListOptions`, `CreditNote`, `CustomerBalanceTransaction`, `CustomerCashBalanceTransaction`, `CustomerSessionCreateOptions`, `CustomerSession`, `Customer`, `Discount`, `FinancialConnections.Account.AccountHolder`, `FinancialConnections.Session.AccountHolder`, `FinancialConnectionsAccountAccountHolderOptions`, `FinancialConnectionsSessionAccountHolderOptions`, `InvoiceCreateOptions`, `InvoiceCreatePreviewOptions`, `InvoiceItemCreateOptions`, `InvoiceItemListOptions`, `InvoiceItem`, `InvoiceListOptions`, `Invoice`, `PaymentIntentCreateOptions`, `PaymentIntentListOptions`, `PaymentIntentUpdateOptions`, `PaymentIntent`, `PaymentMethodAttachOptions`, `PaymentMethodListOptions`, `PaymentMethod`, `PromotionCodeCreateOptions`, `PromotionCodeListOptions`, `PromotionCode`, `QuoteCreateOptions`, `QuoteListOptions`, `QuoteUpdateOptions`, `Quote`, `SetupAttempt`, `SetupIntentCreateOptions`, `SetupIntentListOptions`, `SetupIntentUpdateOptions`, `SetupIntent`, `SubscriptionCreateOptions`, `SubscriptionListOptions`, `SubscriptionScheduleCreateOptions`, `SubscriptionScheduleListOptions`, `SubscriptionSchedule`, `Subscription`, `TaxId.Owner`, `TaxIdOwnerOptions`, and `TaxId`
  * Add support for `Metadata` on `CheckoutSessionLineItemOptions` and `LineItem`
  * Add support for `PaytoPayments` on `Account.Capabilities` and `AccountCapabilitiesOptions`
  * Add support for `Signer` on `AccountDocumentsProofOfRegistrationOptions` and `AccountDocumentsProofOfUltimateBeneficialOwnershipOptions`
  * Add support for `BillingCycleAnchor` on `BillingPortal.Configuration.Features.SubscriptionUpdate` and `BillingPortalConfigurationFeaturesSubscriptionUpdateOptions`
  * Add support for `Payto` on `Charge.PaymentMethodDetails`, `Checkout.Session.PaymentMethodOptions`, `CheckoutSessionPaymentMethodOptionsOptions`, `ConfirmationToken.PaymentMethodPreview`, `ConfirmationTokenPaymentMethodDataOptions`, `Invoice.PaymentSettings.PaymentMethodOptions`, `InvoicePaymentSettingsPaymentMethodOptionsOptions`, `Mandate.PaymentMethodDetails`, `PaymentAttemptRecord.PaymentMethodDetails`, `PaymentIntent.PaymentMethodOptions`, `PaymentIntentPaymentMethodDataOptions`, `PaymentIntentPaymentMethodOptionsOptions`, `PaymentMethodConfigurationCreateOptions`, `PaymentMethodConfigurationUpdateOptions`, `PaymentMethodConfiguration`, `PaymentMethodCreateOptions`, `PaymentMethodUpdateOptions`, `PaymentMethod`, `PaymentRecord.PaymentMethodDetails`, `SetupAttempt.PaymentMethodDetails`, `SetupIntent.PaymentMethodOptions`, `SetupIntentPaymentMethodDataOptions`, `SetupIntentPaymentMethodOptionsOptions`, `Subscription.PaymentSettings.PaymentMethodOptions`, and `SubscriptionPaymentSettingsPaymentMethodOptionsOptions`
  * Add support for `ExpectedDebitDate` on `Charge.PaymentMethodDetails.AcssDebit`, `Charge.PaymentMethodDetails.AuBecsDebit`, `Charge.PaymentMethodDetails.BacsDebit`, `Charge.PaymentMethodDetails.NzBankAccount`, `Charge.PaymentMethodDetails.SepaDebit`, `Charge.PaymentMethodDetails.UsBankAccount`, `PaymentAttemptRecord.PaymentMethodDetails.AcssDebit`, `PaymentAttemptRecord.PaymentMethodDetails.AuBecsDebit`, `PaymentAttemptRecord.PaymentMethodDetails.BacsDebit`, `PaymentAttemptRecord.PaymentMethodDetails.NzBankAccount`, `PaymentAttemptRecord.PaymentMethodDetails.SepaDebit`, `PaymentAttemptRecord.PaymentMethodDetails.UsBankAccount`, `PaymentRecord.PaymentMethodDetails.AcssDebit`, `PaymentRecord.PaymentMethodDetails.AuBecsDebit`, `PaymentRecord.PaymentMethodDetails.BacsDebit`, `PaymentRecord.PaymentMethodDetails.NzBankAccount`, `PaymentRecord.PaymentMethodDetails.SepaDebit`, and `PaymentRecord.PaymentMethodDetails.UsBankAccount`
  * Add support for `LineItems` on `Checkout.SessionUpdateOptions`
  * Add support for `Invoice` on `CustomerCustomerBalanceTransactionListOptions`
  * Add support for `RelatedCustomerAccount` on `Identity.VerificationSessionCreateOptions`, `Identity.VerificationSessionListOptions`, and `Identity.VerificationSession`
  * Add support for `Subtotal` on `InvoiceLineItem`
  * Add support for `AuthorizationCode`, `Description`, `Iin`, `Installments`, `Issuer`, `NetworkAdviceCode`, `NetworkDeclineCode`, and `StoredCredentialUsage` on `PaymentAttemptRecord.PaymentMethodDetails.Card` and `PaymentRecord.PaymentMethodDetails.Card`
  * Add support for `AllowRedisplay` on `PaymentMethodListOptions`
  * Add support for `ReportedBy` on `PaymentRecord`
  * Add support for `Changes` on `V2.Core.Event`
* [#3270](https://github.com/stripe/stripe-dotnet/pull/3270) Make `EventUtility.ComputeSignature` public

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v50.1.0/CHANGELOG.md).

### v50.1.0-alpha.4  (v50.1.0-alpha.4)
<https://github.com/stripe/stripe-dotnet/releases/tag/v50.1.0-alpha.4>

* [#3272](https://github.com/stripe/stripe-dotnet/pull/3272) Update generated code for private-preview
  * Add support for `CheckScanning` on `AccountSession.Components`
  * Add support for `Client` on `V2.Core.Event.Reason.Request`
  * Add support for `StripeBalancePayment` on `V2.MoneyManagement.ReceivedCredit` and `V2.MoneyManagement.ReceivedDebit`
  * Add support for `BalanceTransfer` on `V2.MoneyManagement.ReceivedDebit`
  * Add support for `Include` on `V2.Core.EventGetOptions` and `V2.Core.EventListOptions`
  * Add support for event notifications `V2IamApiKeyCreatedEvent`, `V2IamApiKeyDefaultSecretRevealedEvent`, `V2IamApiKeyExpiredEvent`, `V2IamApiKeyPermissionsUpdatedEvent`, `V2IamApiKeyRotatedEvent`, and `V2IamApiKeyUpdatedEvent`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v50.1.0-alpha.4/CHANGELOG.md).

### v50.1.0-alpha.3  (v50.1.0-alpha.3)
<https://github.com/stripe/stripe-dotnet/releases/tag/v50.1.0-alpha.3>

* [#3269](https://github.com/stripe/stripe-dotnet/pull/3269) Update generated code for private-preview
  * Add support for new resource `ProductCatalog.TrialOffer`
  * Add support for `Create` method on resource `ProductCatalog.TrialOffer`
  * Remove support for `AmountSubtotalAfterDiscount` on `DelegatedCheckout.RequestedSession.LineItemDetail` and `DelegatedCheckout.RequestedSession.TotalDetails`
  * Remove support for `AmountTotal`, `UnitAmountAfterDiscount`, and `UnitDiscount` on `DelegatedCheckout.RequestedSession.LineItemDetail`
  * Add support for `AmountCartDiscount` and `AmountItemsDiscount` on `DelegatedCheckout.RequestedSession.TotalDetails`
  * Remove support for `AmountDiscount` on `DelegatedCheckout.RequestedSession.TotalDetails`
  * Add support for `PaymentsOrchestration` on `PaymentIntentCreateOptions` and `PaymentIntent`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v50.1.0-alpha.3/CHANGELOG.md).

### v50.1.0-alpha.2  (v50.1.0-alpha.2)
<https://github.com/stripe/stripe-dotnet/releases/tag/v50.1.0-alpha.2>

This release changes the pinned API version to `2025-11-17.preview`.

* [#3264](https://github.com/stripe/stripe-dotnet/pull/3264) Update generated code for private-preview
  * Add support for new resources `V2.Core.AccountPersonToken`, `V2.Core.AccountToken`, and `V2.MoneyManagement.CurrencyConversion`
  * Add support for `Create`, `Get`, and `List` methods on resource `V2.MoneyManagement.CurrencyConversion`
  * Add support for `Create` and `Get` methods on resources `V2.Core.AccountPersonToken` and `V2.Core.AccountToken`
  * Add support for `EffectiveAt` on `InvoiceScheduleDetailsAmendmentOptions`, `InvoiceScheduleDetailsPhaseOptions`, `QuoteLineOptions`, `QuoteLine`, `QuotePreviewSubscriptionSchedule.Phase`, `SubscriptionSchedule.Phase`, `SubscriptionScheduleAmendmentOptions`, and `SubscriptionSchedulePhaseOptions`
  * Add support for `TrialOffer` on `InvoiceScheduleDetailsAmendmentItemActionAddOptions`, `InvoiceScheduleDetailsAmendmentItemActionSetOptions`, `InvoiceScheduleDetailsPhaseItemOptions`, `QuoteLine.Action.AddItem`, `QuoteLine.Action.SetItems`, `QuoteLineActionAddItemOptions`, `QuoteLineActionSetItemOptions`, `QuotePreviewSubscriptionSchedule.Phase.Item`, `SubscriptionSchedule.Phase.Item`, `SubscriptionScheduleAmendmentItemActionAddOptions`, `SubscriptionScheduleAmendmentItemActionSetOptions`, and `SubscriptionSchedulePhaseItemOptions`
  * Change type of `DelegatedCheckout.RequestedSession.AmountSubtotal` from `longInteger` to `nullable(longInteger)`
  * Change type of `DelegatedCheckout.RequestedSession.AmountTotal` from `longInteger` to `nullable(longInteger)`
  * Add support for `AmountDiscount`, `AmountSubtotal`, `AmountTotal`, `UnitAmountAfterDiscount`, and `UnitDiscount` on `DelegatedCheckout.RequestedSession.LineItemDetail`
  * Add support for `AmountSubtotalAfterDiscount` on `DelegatedCheckout.RequestedSession.LineItemDetail` and `DelegatedCheckout.RequestedSession.TotalDetails`
  * Change type of `InvoiceScheduleDetailsOptions.BillingSchedules` from `array(billing_schedules_update_params)` to `emptyable(array(billing_schedules_update_params))`
  * Add support for `CurrentTrial` on `InvoiceSubscriptionDetailsItemOptions`, `SubscriptionItemCreateOptions`, `SubscriptionItemOptions`, `SubscriptionItemUpdateOptions`, and `SubscriptionItem`
  * Change type of `QuoteSubscriptionDataOptions.BillingSchedules` and `QuoteSubscriptionDataOverrideOptions.BillingSchedules` from `emptyable(array(billing_schedules_create_specs))` to `array(billing_schedules_create_specs)`
  * Change type of `Quote.SubscriptionData.BillingSchedules` and `Quote.SubscriptionDataOverrides.BillingSchedules` from `nullable(array(SubscriptionsResourceBillingSchedules))` to `array(QuotesResourceSubscriptionDataBillingSchedules)`
  * Change type of `Quote.SubscriptionData.PhaseEffectiveAt` and `Quote.SubscriptionDataOverrides.PhaseEffectiveAt` from `nullable(enum('billing_period_start'|'phase_start'))` to `enum('billing_period_start'|'line_start')`
  * Change type of `QuotePreviewSubscriptionSchedule.BillingSchedules` and `SubscriptionSchedule.BillingSchedules` from `nullable(array(SubscriptionsResourceBillingSchedules))` to `array(SubscriptionsResourceBillingSchedules)`
  * Remove support for `AmendmentStart`, `LineStartsAt`, and `Relative` on `Subscription.BillingSchedule.BillFrom`
  * Change type of `Subscription.BillingSchedule.BillFrom.ComputedTimestamp` from `nullable(DateTime)` to `DateTime`
  * Change type of `Subscription.BillingSchedule.BillFrom.Type` from `enum` to `literal('timestamp')`
  * Remove support for `AmendmentEnd` and `LineEndsAt` on `Subscription.BillingSchedule.BillUntil`
  * Change type of `V2.Billing.ServiceAction.CreditGrant.Amount.Monetary`, `V2.Billing.ServiceAction.CreditGrantPerTenant.Amount.Monetary`, `V2BillingServiceActionCreditGrantAmountOptions.Monetary`, and `V2BillingServiceActionCreditGrantPerTenantAmountOptions.Monetary` from `amount` to `an object`
  * Add support for `FutureRequirements` on `V2.Core.Account`
  * Add support for `KonbiniPayments` and `ScriptStatementDescriptor` on `V2.Core.Account.Configuration.Merchant` and `V2CoreAccountConfigurationMerchantOptions`
  * Add support for `Eur` on `V2.Core.Account.Configuration.Storer.Capabilities.HoldsCurrencies` and `V2CoreAccountConfigurationStorerCapabilitiesHoldsCurrenciesOptions`
  * Add support for `RequirementsCollector` on `V2.Core.Account.Defaults.Responsibilities`
  * Remove support for `Collector` on `V2.Core.Account.Requirements`
  * Remove support for `V1EventId` on `V2.Core.Event`
  * Remove support for `AmountDetails` and `CaptureMethod` on `V2.Payments.OffSessionPaymentCreateOptions` and `V2.Payments.OffSessionPayment`
  * Change type of `V2.Payments.OffSessionPayment.AmountCapturable` from `amount` to `an object`
  * Change type of `V2.Payments.OffSessionPayment.AmountRequested` from `amount` to `an object`
  * Change type of `V2.Payments.OffSessionPaymentCreateOptions.Amount` from `amount` to `an object`
  * Remove support for `Destination` on `V2PaymentsOffSessionPaymentTransferDataOptions`
  * Add support for `Created` on `V2.Core.EventListOptions`
  * Remove support for `Gt`, `Gte`, `Lt`, and `Lte` on `V2.Core.EventListOptions`
  * Add support for `AccountToken` on `V2.Core.AccountCreateOptions` and `V2.Core.AccountUpdateOptions`
  * Add support for `PersonToken` on `V2.Core.AccountPersonCreateOptions` and `V2.Core.AccountPersonUpdateOptions`
  * Add support for `ImpactedRequestsPercentage` on `EventsV2CoreHealthApiErrorFiringEventImpact`, `EventsV2CoreHealthApiErrorResolvedEventImpact`, `EventsV2CoreHealthApiLatencyFiringEventImpact`, `EventsV2CoreHealthApiLatencyResolvedEventImpact`, `EventsV2CoreHealthPaymentMethodErrorFiringEventImpact`, and `EventsV2CoreHealthPaymentMethodErrorResolvedEventImpact`
  * Add support for `Context` and `RelatedObject` on `EventsV2CoreHealthEventGenerationFailureResolvedEventImpact`
  * Remove support for `Account`, `Livemode`, `MissingDeliveryAttempts`, and `Rel

_…truncated…_

### v50.1.0-beta.1  (v50.1.0-beta.1)
<https://github.com/stripe/stripe-dotnet/releases/tag/v50.1.0-beta.1>

This release changes the pinned API version to `2025-11-17.preview`.

* [#3241](https://github.com/stripe/stripe-dotnet/pull/3241) Update generated code for beta
  * Add support for new resources `V2.Core.AccountPersonToken` and `V2.Core.AccountToken`
  * Remove support for resource `V2.Payments.OffSessionPayment`
  * Add support for `Create` and `Get` methods on resources `V2.Core.AccountPersonToken` and `V2.Core.AccountToken`
  * Remove support for `Cancel`, `Capture`, `Create`, `Get`, and `List` methods on resource `V2.Payments.OffSessionPayment`
  * Add support for `SpecifiedCommercialTransactionsActUrl` on `Account.BusinessProfile` and `AccountBusinessProfileOptions`
  * Add support for `PaypayPayments` on `Account.Settings` and `AccountSettingsOptions`
  * Change type of `BillingAnalyticsMeterUsageMeterOptions.DimensionFilters` from `string` to `array(string)`
  * Change type of `BillingAnalyticsMeterUsageMeterOptions.TenantFilters` from `string` to `array(string)`
  * Add support for `CarRentalData`, `FlightData`, and `LodgingData` on `ChargePaymentDetailsOptions` and `PaymentIntentPaymentDetailsOptions`
  * Add support for `SupplementaryPurchaseData` on `OrderPaymentSettingsPaymentMethodOptionsKlarnaOptions` and `PaymentIntentPaymentMethodOptionsKlarnaOptions`
  * Add support for `AllowRedisplay` and `CustomerAccount` on `PaymentMethodListOptions`
  * Add support for `FutureRequirements` on `V2.Core.Account`
  * Add support for `KonbiniPayments` and `ScriptStatementDescriptor` on `V2.Core.Account.Configuration.Merchant` and `V2CoreAccountConfigurationMerchantOptions`
  * Add support for `Eur` on `V2.Core.Account.Configuration.Storer.Capabilities.HoldsCurrencies` and `V2CoreAccountConfigurationStorerCapabilitiesHoldsCurrenciesOptions`
  * Add support for `RequirementsCollector` on `V2.Core.Account.Defaults.Responsibilities`
  * Remove support for `Collector` on `V2.Core.Account.Requirements`
  * Add support for `Changes` on `V2.Core.Event`
  * Add support for `AccountToken` on `V2.Core.AccountCreateOptions` and `V2.Core.AccountUpdateOptions`
  * Add support for `PersonToken` on `V2.Core.AccountPersonCreateOptions` and `V2.Core.AccountPersonUpdateOptions`
  * Add support for thin event `V2CoreHealthEventGenerationFailureResolvedEvent`
  * Remove support for thin events `V2PaymentsOffSessionPaymentAuthorizationAttemptFailedEvent`, `V2PaymentsOffSessionPaymentAuthorizationAttemptStartedEvent`, `V2PaymentsOffSessionPaymentCanceledEvent`, `V2PaymentsOffSessionPaymentCreatedEvent`, `V2PaymentsOffSessionPaymentFailedEvent`, `V2PaymentsOffSessionPaymentRequiresCaptureEvent`, and `V2PaymentsOffSessionPaymentSucceededEvent` with related object `V2.Payments.OffSessionPayment`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v50.1.0-beta.1/CHANGELOG.md).

### v50.1.0-alpha.1  (v50.1.0-alpha.1)
<https://github.com/stripe/stripe-dotnet/releases/tag/v50.1.0-alpha.1>

* [#3257](https://github.com/stripe/stripe-dotnet/pull/3257) Update generated code for private-preview
  * Add support for `BillingSchedulesActions` on `InvoiceScheduleDetailsAmendmentOptions` and `SubscriptionScheduleAmendmentOptions`
* [#3252](https://github.com/stripe/stripe-dotnet/pull/3252) Update generated code for private-preview
  * Add support for new resources `BalanceTransfer` and `Radar.AccountEvaluation`
  * Add support for `Create` method on resource `BalanceTransfer`
  * Add support for `Create`, `Get`, and `Update` methods on resource `Radar.AccountEvaluation`
  * Add support for `Schedule` on `Discount`
  * Add support for `SpecifiedCommercialTransactionsActUrl` on `Account.BusinessProfile` and `AccountBusinessProfileOptions`
  * Add support for `PaypayPayments` on `Account.Settings` and `AccountSettingsOptions`
  * Change type of `BillingAnalyticsMeterUsageMeterOptions.DimensionFilters` from `string` to `array(string)`
  * Change type of `BillingAnalyticsMeterUsageMeterOptions.TenantFilters` from `string` to `array(string)`
  * Add support for `PaymentMethodConfiguration` on `BillingPortal.Configuration.Features.PaymentMethodUpdate`
  * Add support for `CarRentalData`, `FlightData`, and `LodgingData` on `ChargePaymentDetailsOptions` and `PaymentIntentPaymentDetailsOptions`
  * Add support for `TransactionId` on `Charge.PaymentMethodDetails.Ideal`, `PaymentAttemptRecord.PaymentMethodDetails.Ideal`, and `PaymentRecord.PaymentMethodDetails.Ideal`
  * Add support for `Created` on `CustomerCustomerBalanceTransactionListOptions` and `InvoicePaymentListOptions`
  * Add support for `AccountNumbers` on `FinancialConnections.Account`
  * Add support for `ScheduleDetails` on `Invoice.Parent`, `InvoiceItem.Parent`, `InvoiceLineItem.Parent`, and `QuotePreviewInvoice.Parent`
  * Add support for `BillingSchedules` on `InvoiceScheduleDetailsOptions`, `QuotePreviewSubscriptionSchedule`, `SubscriptionScheduleCreateOptions`, `SubscriptionScheduleUpdateOptions`, and `SubscriptionSchedule`
  * Add support for `FraudRisk` on `IssuingAuthorizationRiskAssessmentOptions`
  * Add support for `LatestFraudWarning` on `Issuing.Card`
  * Add support for `SupplementaryPurchaseData` on `OrderPaymentSettingsPaymentMethodOptionsKlarnaOptions` and `PaymentIntentPaymentMethodOptionsKlarnaOptions`
  * Add support for `CaptureMethod` on `PaymentIntent.PaymentMethodOptions.CardPresent` and `PaymentIntentPaymentMethodOptionsCardPresentOptions`
  * Add support for `AllowRedisplay` and `CustomerAccount` on `PaymentMethodListOptions`
  * Add support for `LatestInvoice` on `QuotePreviewSubscriptionSchedule` and `SubscriptionSchedule`
  * Add support for `PhaseEffectiveAt` on `QuotePreviewSubscriptionSchedule.DefaultSettings`, `SubscriptionSchedule.DefaultSettings`, and `SubscriptionScheduleDefaultSettingsOptions`
  * Add support for `MbWay` and `Twint` on `Refund.DestinationDetails`
  * Add support for snapshot events `FinancialConnectionsAccountAccountNumbersUpdated` and `FinancialConnectionsAccountUpcomingAccountNumberExpiry` with resource `FinancialConnections.Account`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v50.1.0-alpha.1/CHANGELOG.md).

### v50.0.0  (v50.0.0)
<https://github.com/stripe/stripe-dotnet/releases/tag/v50.0.0>

This release changes the pinned API version to `2025-11-17.clover`.

* [#3256](https://github.com/stripe/stripe-dotnet/pull/3256) Update generated code
  * ⚠️ Remove support for `Gt`, `Gte`, `Lt`, and `Lte` on `V2.Core.EventListOptions` in favor of `Created`.
* [#3254](https://github.com/stripe/stripe-dotnet/pull/3254) Check if a datetime is in millis
  * Bug fix for [#3253](https://github.com/stripe/stripe-dotnet/issues/3253). UnixDateTimeConverter now handles timestamps in milliseconds. 
* [#3249](https://github.com/stripe/stripe-dotnet/pull/3249) Update v2 array parameter serialization to use indexed format
  - `Retrieve` and `List` calls for `/v2` endpoints now use indexed format (e.g., `?include[0]=foo&include[1]=bar`) instead of repeated parameter format (e.g., `?include=foo&include=bar`) when communicating with the Stripe API. This may break any unit tests that expect the latter behavior when setting up a mock server. Instead, they should now expect the former.
* [#3246](https://github.com/stripe/stripe-dotnet/pull/3246) Update generated code
  * Add support for new resources `Tax.Association` and `Terminal.OnboardingLink`
  * Add support for `Find` method on resource `Tax.Association`
  * Add support for `Create` method on resource `Terminal.OnboardingLink`
  * Add support for `PaymentMethodConfiguration` on `BillingPortal.Configuration.Features.PaymentMethodUpdate`
  * Add support for `TransactionId` on `Charge.PaymentMethodDetails.Ideal`, `PaymentAttemptRecord.PaymentMethodDetails.Ideal`, and `PaymentRecord.PaymentMethodDetails.Ideal`
  * Add support for `Created` on `CustomerCustomerBalanceTransactionListOptions` and `InvoicePaymentListOptions`
  * Add support for `AccountNumbers` on `FinancialConnections.Account`
  * Add support for `FraudRisk` on `IssuingAuthorizationRiskAssessmentOptions`
  * Add support for `LatestFraudWarning` on `Issuing.Card`
  * Add support for `Hooks` on `PaymentIntentCaptureOptions`, `PaymentIntentConfirmOptions`, `PaymentIntentCreateOptions`, `PaymentIntentIncrementAuthorizationOptions`, `PaymentIntentUpdateOptions`, and `PaymentIntent`
  * Add support for `MbWay` and `Twint` on `Refund.DestinationDetails`
  * Add support for snapshot events `FinancialConnectionsAccountAccountNumbersUpdated` and `FinancialConnectionsAccountUpcomingAccountNumberExpiry` with resource `FinancialConnections.Account`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v50.0.0/CHANGELOG.md).


## v49.x

### v49.3.0-alpha.2  (v49.3.0-alpha.2)
<https://github.com/stripe/stripe-dotnet/releases/tag/v49.3.0-alpha.2>

This release changes the pinned API version to `2025-10-29.preview`.

* [#3251](https://github.com/stripe/stripe-dotnet/pull/3251) Update generated code for private-preview
  * Add support for new resource `Issuing.Program`
  * Add support for `Create`, `Get`, `List`, and `Update` methods on resource `Issuing.Program`
  * Add support for `ApplicableFees` on `DelegatedCheckout.RequestedSession.TotalDetails`
* [#3245](https://github.com/stripe/stripe-dotnet/pull/3245) Update generated code for private-preview
  * Remove support for resource `V2.Tax.AutomaticRule`
  * Remove support for `Create`, `Deactivate`, `Find`, `Get`, and `Update` methods on resource `V2.Tax.AutomaticRule`
  * Add support for `SelfReportedIncome` and `SelfReportedMonthlyHousingPayment` on `AccountIndividualOptions`, `AccountPersonCreateOptions`, `AccountPersonUpdateOptions`, `Person`, `TokenAccountIndividualOptions`, and `TokenPersonOptions`
  * Add support for `BillingSchedules` and `PhaseEffectiveAt` on `Quote.SubscriptionDataOverrides`, `Quote.SubscriptionData`, `QuoteSubscriptionDataOptions`, `QuoteSubscriptionDataOverrideOptions`, and `QuoteSubscriptionDataOverridesOptions`
  * Add support for `BillFrom` on `Subscription.BillingSchedule`
  * Add support for `AmendmentEnd` and `LineEndsAt` on `Subscription.BillingSchedule.BillUntil`
  * Remove support for `Data` and `RelatedObject` on `V2.Core.Event`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v49.3.0-alpha.2/CHANGELOG.md).

### v49.3.0-alpha.1  (v49.3.0-alpha.1)
<https://github.com/stripe/stripe-dotnet/releases/tag/v49.3.0-alpha.1>

* [#3243](https://github.com/stripe/stripe-dotnet/pull/3243) Update generated code for private-preview
  * Add support for new resource `TransitBalance`, `V2.Reporting.ReportRun`, `V2.Reporting.Report`
  * Add support for `Create` and `Get` methods on resource `V2.Reporting.ReportRun`
  * Add support for `Get` method on resource `V2.Reporting.Report`
  * Add support for `Create` and `Refill` test helper methods on resource `Capital.FinancingOffer`
  * Add support for `AllocatedFunds` on `Charge`, `PaymentIntentConfirmOptions`, `PaymentIntentCreateOptions`, and `PaymentIntentUpdateOptions`
  * Add support for thin events `V2ReportingReportRunCreatedEvent`, `V2ReportingReportRunFailedEvent`, `V2ReportingReportRunSucceededEvent`, and `V2ReportingReportRunUpdatedEvent` with related object `V2.Reporting.ReportRun`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v49.3.0-alpha.1/CHANGELOG.md).

### v49.2.0  (v49.2.0)
<https://github.com/stripe/stripe-dotnet/releases/tag/v49.2.0>

* [#3244](https://github.com/stripe/stripe-dotnet/pull/3244) Update generated code
  * Add support for `CaptureMethod` on `PaymentIntent.PaymentMethodOptions.CardPresent` and `PaymentIntentPaymentMethodOptionsCardPresentOptions`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v49.2.0/CHANGELOG.md).

### v49.2.0-alpha.2  (v49.2.0-alpha.2)
<https://github.com/stripe/stripe-dotnet/releases/tag/v49.2.0-alpha.2>

* [#3242](https://github.com/stripe/stripe-dotnet/pull/3242) Update generated code for private-preview
  * Add support for `PaymentMethodPreview` on `DelegatedCheckout.RequestedSession`
  * Add support for `OrderId` on `DelegatedCheckout.RequestedSession.OrderDetails`
  * Add support for `Lead` on `V2.Core.Account.Configuration.CardCreator.Capabilities.Commercial`, `V2.Core.Account.Identity.Attestations.TermsOfService.CardCreator.Commercial`, `V2CoreAccountConfigurationCardCreatorCapabilitiesCommercialOptions`, and `V2CoreAccountIdentityAttestationsTermsOfServiceCardCreatorCommercialOptions`
  * Add support for `GlobalAccountHolder` on `V2.Core.Account.Identity.Attestations.TermsOfService.CardCreator.Commercial` and `V2CoreAccountIdentityAttestationsTermsOfServiceCardCreatorCommercialOptions`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v49.2.0-alpha.2/CHANGELOG.md).

### v49.2.0-beta.1  (v49.2.0-beta.1)
<https://github.com/stripe/stripe-dotnet/releases/tag/v49.2.0-beta.1>

This release changes the pinned API version to `2025-10-29.preview`.

* [#3234](https://github.com/stripe/stripe-dotnet/pull/3234) Update generated code for beta
  * Add support for `CryptoStorer` on `V2CoreAccountIdentityAttestationsTermsOfServiceOptions`
* [#3211](https://github.com/stripe/stripe-dotnet/pull/3211) Update generated code for beta
  * Add support for `Update` method on resource `V2.MoneyManagement.FinancialAccount`
  * Add support for `ConfirmMicrodeposits`, `List`, and `SendMicrodeposits` methods on resource `V2.Core.Vault.UsBankAccount`
  * Add support for `List` method on resource `V2.Core.Vault.GbBankAccount`
  * Add support for `PaymentPortalUrl` on `Charge.PaymentMethodDetails.Rechnung`, `PaymentAttemptRecord.PaymentMethodDetails.Rechnung`, and `PaymentRecord.PaymentMethodDetails.Rechnung`
  * Add support for `TaxIdElement` on `CustomerSession.Components` and `CustomerSessionComponentsOptions`
  * Add support for `StartingAfter` on `PaymentAttemptRecordListOptions`
  * Add support for `Reference` on `PaymentIntentAmountDetailsLineItem.PaymentMethodOptions.Klarna` and `PaymentIntentAmountDetailsLineItemsPaymentMethodOptionsKlarnaOptions`
  * Add support for `SubscriptionReference` on `PaymentIntentAmountDetailsLineItem.PaymentMethodOptions.Klarna`
  * Add support for `Closed` on `V2.Core.AccountListOptions` and `V2.Core.Account`
  * Add support for `Usd` on `V2.Core.Account.Configuration.Storer.Capabilities.HoldsCurrencies` and `V2CoreAccountConfigurationStorerCapabilitiesHoldsCurrenciesOptions`
  * Add support for `RepresentativeDeclaration` on `V2.Core.Account.Identity.Attestations` and `V2CoreAccountIdentityAttestationsOptions`
  * Add support for `Verification` on `V2.Core.Vault.UsBankAccount`
  * Add support for `V1Id` on `EventsV2MoneyManagementTransactionCreatedEvent`
  * Remove support for thin event `V2BillingBillSettingUpdatedEvent` with related object `V2.Billing.BillSetting`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v49.2.0-beta.1/CHANGELOG.md).

### v49.2.0-alpha.1  (v49.2.0-alpha.1)
<https://github.com/stripe/stripe-dotnet/releases/tag/v49.2.0-alpha.1>

* [#3237](https://github.com/stripe/stripe-dotnet/pull/3237) Update generated code for private-preview
  * Add support for `Tenants` on `Billing.Analytics.MeterUsageRow`
  * Add support for `Transfer` on `ApplicationFee.FeeSource`
  * Add support for `TransitBalancesTotal` on `Balance`
  * Add support for `TenantGroupByKeys` on `BillingAnalyticsMeterUsageMeterOptions`
  * Remove support for `RiskDetails` on `DelegatedCheckout.RequestedSessionCreateOptions`
  * Add support for `RiskDetails` on `DelegatedCheckout.RequestedSessionConfirmOptions`
  * Add support for `AllocatedFunds` on `PaymentIntent`
  * Add support for `ApplicationFeeAmount` on `TransferCreateOptions` and `Transfer`
  * Add support for `ApplicationFee` on `Transfer`
* [#3235](https://github.com/stripe/stripe-dotnet/pull/3235) Update generated code for private-preview
  * Add support for `ReportRefund` method on resource `PaymentRecord`
  * Add support for `RepresentativeDeclaration` on `Account.Company`, `AccountCompanyOptions`, and `TokenAccountCompanyOptions`
  * Add support for `PaymentMethodConfiguration` on `BillingPortalConfigurationFeaturesPaymentMethodUpdateOptions`
  * Add support for `PaymentPortalUrl` on `Charge.PaymentMethodDetails.Rechnung`, `PaymentAttemptRecord.PaymentMethodDetails.Rechnung`, and `PaymentRecord.PaymentMethodDetails.Rechnung`
  * Add support for `Twint` on `Checkout.Session.PaymentMethodOptions` and `CheckoutSessionPaymentMethodOptionsOptions`
  * Add support for `CustomerSheet`, `MobilePaymentElement`, and `TaxIdElement` on `CustomerSession.Components` and `CustomerSessionComponentsOptions`
  * Add support for `Provider` on `Customer.Tax`
  * Add support for `StartingAfter` on `PaymentAttemptRecordListOptions`
  * Add support for `Reference` on `PaymentIntentAmountDetailsLineItem.PaymentMethodOptions.Klarna` and `PaymentIntentAmountDetailsLineItemsPaymentMethodOptionsKlarnaOptions`
  * Add support for `SubscriptionReference` on `PaymentIntentAmountDetailsLineItem.PaymentMethodOptions.Klarna`
  * Add support for `NameCollection` on `PaymentLinkCreateOptions`, `PaymentLinkUpdateOptions`, and `PaymentLink`
  * Add support for `Crypto` on `PaymentMethodConfigurationCreateOptions`, `PaymentMethodConfigurationUpdateOptions`, `PaymentMethodConfiguration`, and `Refund.DestinationDetails`
  * Add support for `MbWay` on `PaymentMethodConfigurationCreateOptions`, `PaymentMethodConfigurationUpdateOptions`, and `PaymentMethodConfiguration`
  * Add support for `Custom` on `PaymentMethodCreateOptions` and `PaymentMethod`
  * Add support for `ExcludedPaymentMethodTypes` on `SetupIntentCreateOptions`, `SetupIntentUpdateOptions`, and `SetupIntent`
  * Add support for `Tw` on `Tax.Registration.CountryOptions` and `TaxRegistrationCountryOptionsOptions`
  * Add support for `Gip` on `Terminal.Configuration.Tipping` and `TerminalConfigurationTippingOptions`
  * Add support for `LastSeenAt` on `Terminal.Reader`
  * Add support for `HighRiskActivitiesDescription`, `HighRiskActivities`, `MoneyServicesDescription`, `OperatesInProhibitedCountries`, `ParticipatesInRegulatedActivity`, `PurposeOfFundsDescription`, `PurposeOfFunds`, `RegulatedActivity`, `SourceOfFundsDescription`, and `SourceOfFunds` on `V2.Core.Account.Configuration.Storer` and `V2CoreAccountConfigurationStorerOptions`
  * Add support for `CryptoWallets` on `V2.Core.Account.Configuration.Storer.Capabilities.FinancialAddresses`, `V2.Core.Account.Configuration.Storer.Capabilities.OutboundPayments`, `V2.Core.Account.Configuration.Storer.Capabilities.OutboundTransfers`, `V2CoreAccountConfigurationStorerCapabilitiesFinancialAddressesOptions`, `V2CoreAccountConfigurationStorerCapabilitiesOutboundPaymentsOptions`, and `V2CoreAccountConfigurationStorerCapabilitiesOutboundTransfersOptions`
  * Add support for `Usdc` on `V2.Core.Account.Configuration.Storer.Capabilities.HoldsCurrencies` and `V2CoreAccountConfigurationStorerCapabilitiesHoldsCurrenciesOptions`
  * Add support for `CryptoStorer` on `V2.Core.Account.Identity.Attestations.TermsOfService` and `V2CoreAccountIdentityAttestationsTermsOfServiceOptions`
  * Add support for `ComplianceScreeningDescription` on `V2.Core.Account.Identity.BusinessDetails` and `V2CoreAccountIdentityBusinessDetailsOptions`
  * Add support for `ExternalAmount` on `V2.MoneyManagement.ReceivedCredit` and `V2.MoneyManagement.ReceivedDebit`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v49.2.0-alpha.1/CHANGELOG.md).

### v49.1.0  (v49.1.0)
<https://github.com/stripe/stripe-dotnet/releases/tag/v49.1.0>

* [#3236](https://github.com/stripe/stripe-dotnet/pull/3236) Update generated code
  * Improve docs for PaymentIntent related endpoints
* [#3230](https://github.com/stripe/stripe-dotnet/pull/3230) Update generated code
  * Add support for new resources `PaymentAttemptRecord`, `PaymentIntentAmountDetailsLineItem`, and `PaymentRecord`
  * Add support for `Get` and `List` methods on resource `PaymentAttemptRecord`
  * Add support for `Get`, `ReportPaymentAttemptCanceled`, `ReportPaymentAttemptFailed`, `ReportPaymentAttemptGuaranteed`, `ReportPaymentAttemptInformational`, `ReportPaymentAttempt`, `ReportPayment`, and `ReportRefund` methods on resource `PaymentRecord`
  * Add support for `List` method on resource `PaymentIntentAmountDetailsLineItem`
  * Add support for `RepresentativeDeclaration` on `Account.Company`, `AccountCompanyOptions`, and `TokenAccountCompanyOptions`
  * Add support for `PaymentMethodConfiguration` on `BillingPortalConfigurationFeaturesPaymentMethodUpdateOptions`
  * Add support for `Twint` on `Checkout.Session.PaymentMethodOptions` and `CheckoutSessionPaymentMethodOptionsOptions`
  * Add support for `PaymentRecordRefund` and `Type` on `CreditNote.Refund` and `CreditNoteRefundOptions`
  * Add support for `CustomerSheet` and `MobilePaymentElement` on `CustomerSession.Components` and `CustomerSessionComponentsOptions`
  * Add support for `Provider` on `Customer.Tax`
  * Add support for `PaymentRecord` on `InvoiceAttachPaymentOptions`, `InvoicePayment.Payment`, and `InvoicePaymentPaymentOptions`
  * Change type of `InvoicePaymentPaymentOptions.Type` from `literal('payment_intent')` to `enum('payment_intent'|'payment_record')`
  * Add support for `AmountDetails` on `PaymentIntentCaptureOptions`, `PaymentIntentConfirmOptions`, `PaymentIntentCreateOptions`, `PaymentIntentIncrementAuthorizationOptions`, and `PaymentIntentUpdateOptions`
  * Add support for `PaymentDetails` on `PaymentIntentCaptureOptions`, `PaymentIntentConfirmOptions`, `PaymentIntentCreateOptions`, `PaymentIntentIncrementAuthorizationOptions`, `PaymentIntentUpdateOptions`, and `PaymentIntent`
  * Add support for `DiscountAmount`, `LineItems`, `Shipping`, and `Tax` on `PaymentIntent.AmountDetails`
  * Add support for `NameCollection` on `PaymentLinkCreateOptions`, `PaymentLinkUpdateOptions`, and `PaymentLink`
  * Add support for `Crypto` on `PaymentMethodConfigurationCreateOptions`, `PaymentMethodConfigurationUpdateOptions`, `PaymentMethodConfiguration`, and `Refund.DestinationDetails`
  * Add support for `MbWay` on `PaymentMethodConfigurationCreateOptions`, `PaymentMethodConfigurationUpdateOptions`, and `PaymentMethodConfiguration`
  * Add support for `Custom` on `PaymentMethodCreateOptions` and `PaymentMethod`
  * Add support for `ExcludedPaymentMethodTypes` on `SetupIntentCreateOptions`, `SetupIntentUpdateOptions`, and `SetupIntent`
  * Add support for `Tw` on `Tax.Registration.CountryOptions` and `TaxRegistrationCountryOptionsOptions`
  * Add support for `Gip` on `Terminal.Configuration.Tipping` and `TerminalConfigurationTippingOptions`
  * Add support for `LastSeenAt` on `Terminal.Reader`
  * Add support for `Gt`, `Gte`, `Lt`, `Lte`, and `Types` on `V2.Core.EventListOptions`
  * Add support for snapshot event `BalanceSettingsUpdated` with resource `BalanceSettings`
  * Add support for snapshot event `InvoicePaymentAttemptRequired` with resource `Invoice`
* [#3223](https://github.com/stripe/stripe-dotnet/pull/3223) Fixes STJDefaultConverter to safely ignore unknown properties
  * Fixes a bug when using System.Text.Json to deserialize JSON that has properties not present in the target object.

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v49.1.0/CHANGELOG.md).

### v49.1.0-alpha.4  (v49.1.0-alpha.4)
<https://github.com/stripe/stripe-dotnet/releases/tag/v49.1.0-alpha.4>

* [#3232](https://github.com/stripe/stripe-dotnet/pull/3232) Update generated code for private-preview
  * Add support for new resource `V2.Billing.PricingPlanSubscriptionComponents`
  * Add support for `Get` method on resource `V2.Billing.PricingPlanSubscriptionComponents`
  * Add support for `DimensionPayloadKeys` on `Billing.MeterCreateOptions` and `Billing.Meter`
  * Add support for `DimensionFilters` and `DimensionGroupByKeys` on `Billing.BillingMeterMeterEventSummaryListOptions`
  * Add support for `Dimensions` on `Billing.MeterEventSummary`
  * Add support for `FulfillmentDetails` and `PaymentMethodData` on `DelegatedCheckout.RequestedSessionCreateOptions` and `DelegatedCheckout.RequestedSessionUpdateOptions`
  * Add support for `LineItemDetails`, `Metadata`, `PaymentMethod`, and `SharedMetadata` on `DelegatedCheckout.RequestedSessionCreateOptions`, `DelegatedCheckout.RequestedSessionUpdateOptions`, and `DelegatedCheckout.RequestedSession`
  * Add support for `Currency`, `Customer`, and `RiskDetails` on `DelegatedCheckout.RequestedSessionCreateOptions`
  * Add support for `SellerDetails` and `SetupFutureUsage` on `DelegatedCheckout.RequestedSessionCreateOptions` and `DelegatedCheckout.RequestedSession`
  * Add support for `AmountSubtotal`, `AmountTotal`, `CreatedAt`, `ExpiresAt`, `OrderDetails`, `SharedPaymentIssuedToken`, `Status`, `TotalDetails`, and `UpdatedAt` on `DelegatedCheckout.RequestedSession`
  * Add support for `Address`, `Email`, `FulfillmentOptions`, `Name`, `Phone`, and `SelectedFulfillmentOption` on `DelegatedCheckout.RequestedSession.FulfillmentDetails`
* [#3231](https://github.com/stripe/stripe-dotnet/pull/3231) Empty commit
* [#3229](https://github.com/stripe/stripe-dotnet/pull/3229) Merge to private preview

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v49.1.0-alpha.4/CHANGELOG.md).

### v49.1.0-alpha.3  (v49.1.0-alpha.3)
<https://github.com/stripe/stripe-dotnet/releases/tag/v49.1.0-alpha.3>

* [#3220](https://github.com/stripe/stripe-dotnet/pull/3220) Update generated code for private-preview
  * Add support for new resources `DelegatedCheckout.RequestedSession` and `Identity.BlocklistEntry`
  * Add support for `Confirm`, `Create`, `Expire`, `Get`, and `Update` methods on resource `DelegatedCheckout.RequestedSession`
  * Add support for `Create`, `Disable`, `Get`, and `List` methods on resource `Identity.BlocklistEntry`
  * Add support for `BlockedByEntry` on `Identity.VerificationReport.Document`, `Identity.VerificationReport.Selfie`, and `Identity.VerificationReportListOptions`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v49.1.0-alpha.3/CHANGELOG.md).

### v49.1.0-alpha.2  (v49.1.0-alpha.2)
<https://github.com/stripe/stripe-dotnet/releases/tag/v49.1.0-alpha.2>

* [#3218](https://github.com/stripe/stripe-dotnet/pull/3218) Update generated code for private-preview
  * Add support for new resource `PaymentMethodBalance`
  * Add support for `CheckBalance` method on resource `PaymentMethod`
  * Add support for `Benefits` on `Card`, `Charge.PaymentMethodDetails.Card`, `ConfirmationToken.PaymentMethodPreview.Card`, and `PaymentMethod.Card`
  * Add support for `Benefit` on `PaymentIntent.PaymentDetails` and `PaymentIntentPaymentDetailsOptions`
  * Add support for `SetupDetails` on `SetupIntentConfirmOptions`, `SetupIntentCreateOptions`, `SetupIntentUpdateOptions`, and `SetupIntent`
  * Add support for `CardCreator` on `V2.Core.Account.Configuration`, `V2.Core.Account.Identity.Attestations.TermsOfService`, `V2CoreAccountConfigurationOptions`, and `V2CoreAccountIdentityAttestationsTermsOfServiceOptions`
  * Add support for thin events `V2CoreAccountIncludingConfigurationCardCreatorCapabilityStatusUpdatedEvent` and `V2CoreAccountIncludingConfigurationCardCreatorUpdatedEvent` with related object `V2.Core.Account`
  * Remove support for thin events `V1CustomerDiscountCreatedEvent`, `V1CustomerDiscountDeletedEvent`, and `V1CustomerDiscountUpdatedEvent` with related object `Discount`
* [#3214](https://github.com/stripe/stripe-dotnet/pull/3214) Update generated code for private-preview
  * Release specs are identical.

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v49.1.0-alpha.2/CHANGELOG.md).

### v49.1.0-beta.1  (v49.1.0-beta.1)
<https://github.com/stripe/stripe-dotnet/releases/tag/v49.1.0-beta.1>

This release changes the pinned API version to `2025-09-30.preview`. It is built on top of SDK version 49.0.0 which contains breaking changes. Please review the [changelog for 49.0.0](https://github.com/stripe/stripe-dotnet/blob/master/CHANGELOG.md#4900---2025-09-30) if upgrading from older SDK versions.

* [#3193](https://github.com/stripe/stripe-dotnet/pull/3193) Update generated code for beta
  * Add support for `AttachCadence` method on resource `Subscription`
  * Add support for `BillingCadence` on `InvoiceCreatePreviewOptions`, `SubscriptionCreateOptions`, `SubscriptionUpdateOptions`, and `Subscription`
  * Add support for `BillingCadenceDetails` on `Invoice.Parent` and `QuotePreviewInvoice.Parent`
* [#3191](https://github.com/stripe/stripe-dotnet/pull/3191) Update generated code for beta
  * Add support for new resources `V2.Billing.BillSettingVersion`, `V2.Billing.BillSetting`, `V2.Billing.Cadence`, `V2.Billing.CollectionSettingVersion`, `V2.Billing.CollectionSetting`, and `V2.Billing.Profile`
  * Add support for `Create`, `Get`, `List`, and `Update` methods on resources `V2.Billing.BillSetting`, `V2.Billing.CollectionSetting`, and `V2.Billing.Profile`
  * Add support for `Get` and `List` methods on resources `V2.Billing.BillSettingVersion` and `V2.Billing.CollectionSettingVersion`
  * Add support for `Cancel`, `Create`, `Get`, `List`, and `Update` methods on resource `V2.Billing.Cadence`
  * Add support for `Profile` on `V2.Core.Account.Defaults` and `V2CoreAccountDefaultsOptions`
  * Add support for `IP` on `V2.Core.Account.Identity.Attestations.DirectorshipDeclaration`, `V2.Core.Account.Identity.Attestations.OwnershipDeclaration`, `V2.Core.Account.Identity.Attestations.TermsOfService.Account`, `V2.Core.Account.Identity.Attestations.TermsOfService.Storer`, `V2.Core.Account.Identity.Individual.AdditionalTermsOfService.Account`, `V2.Core.Person.AdditionalTermsOfService.Account`, `V2CoreAccountIdentityAttestationsTermsOfServiceAccountOptions`, `V2CoreAccountIdentityAttestationsTermsOfServiceStorerOptions`, and `V2CorePersonAdditionalTermsOfServiceAccountOptions`
  * Remove support for `Ip` on `V2.Core.Account.Identity.Attestations.DirectorshipDeclaration`, `V2.Core.Account.Identity.Attestations.OwnershipDeclaration`, `V2.Core.Account.Identity.Attestations.TermsOfService.Account`, `V2.Core.Account.Identity.Attestations.TermsOfService.Storer`, `V2.Core.Account.Identity.Individual.AdditionalTermsOfService.Account`, `V2.Core.Person.AdditionalTermsOfService.Account`, `V2CoreAccountIdentityAttestationsTermsOfServiceAccountOptions`, `V2CoreAccountIdentityAttestationsTermsOfServiceStorerOptions`, and `V2CorePersonAdditionalTermsOfServiceAccountOptions`
  * Remove support for `DoingBusinessAs`, `ProductDescription`, and `Url` on `V2.Core.Account.Identity.BusinessDetails` and `V2CoreAccountIdentityBusinessDetailsOptions`
  * Add support for `SettlementCurrency` on `V2.MoneyManagement.FinancialAddress`
  * Add support for `SepaBankAccount` on `V2.MoneyManagement.FinancialAddress.Credentials` and `V2.MoneyManagement.ReceivedCredit.BankTransfer`
  * Add support for `AmountDetails` and `PaymentsOrchestration` on `V2.Payments.OffSessionPaymentCreateOptions` and `V2.Payments.OffSessionPayment`
  * Add support for `RetryPolicy` on `V2.Payments.OffSessionPayment.RetryDetails` and `V2PaymentsOffSessionPaymentRetryDetailsOptions`
  * Change type of `V2.MoneyManagement.OutboundPaymentQuote.FxQuote.LockDuration` from `literal('five_minutes')` to `enum('five_minutes'|'none')`
  * Change type of `V2.MoneyManagement.OutboundPaymentQuote.FxQuote.LockExpiresAt` from `DateTime` to `nullable(DateTime)`
  * Add support for `OriginType` on `V2.MoneyManagement.ReceivedCredit.BankTransfer`
  * Remove support for `PaymentMethodType` on `V2.MoneyManagement.ReceivedCredit.BankTransfer`
  * Add support for `MandateData` and `PaymentMethodOptions` on `V2.Payments.OffSessionPaymentCreateOptions`
  * Add support for `Type` on `V2.MoneyManagement.FinancialAddressCreateOptions`
  * Remove support for `Currency` on `V2.MoneyManagement.FinancialAddressCreateOptions`
  * Add support for thin event `V2BillingBillSettingUpdatedEvent` with related object `V2.Billing.BillSetting`
  * Add support for error type `RateLimitException`
* [#3180](https://github.com/stripe/stripe-dotnet/pull/3180) Update generated code for beta
  * Add support for new resources `V2.Billing.BillSettingVersion`, `V2.Billing.BillSetting`, `V2.Billing.Cadence`, `V2.Billing.CollectionSettingVersion`, `V2.Billing.CollectionSetting`, and `V2.Billing.Profile`
  * Add support for `Create`, `Get`, `List`, and `Update` methods on resources `V2.Billing.BillSetting`, `V2.Billing.CollectionSetting`, and `V2.Billing.Profile`
  * Add support for `Get` and `List` methods on resources `V2.Billing.BillSettingVersion` and `V2.Billing.CollectionSettingVersion`
  * Add support for `Cancel`, `Create`, `Get`, `List`, and `Update` methods on resource `V2.Billing.Cadence`
  * Add support for `Profile` on `V2.Core.Account.Defaults` and `V2CoreAccountDefaultsOptions`
  * Add support for `IP` on `V2.Core.Account.Identity.Attestations.DirectorshipDeclaration`, `V2.Core.Account.Identity.Attestations.OwnershipDeclaration`, `V2.Core.Account.Identity.Attestations.TermsOfService.Account`, `V2.Core.Account.Identity.Attestations.TermsOfService.Storer`, `V2.Core.Account.Identity.Individual.AdditionalTermsOfService.Account`, `V2.Core.Person.AdditionalTermsOfService.Account`, `V2CoreAccountIdentityAttestationsTermsOfServiceAccountOptions`, `V2CoreAccountIdentityAttestationsTermsOfServiceStorerOptions`, and `V2CorePersonAdditionalTermsOfServiceAccountOptions`
  * Remove support for `Ip` on `V2.Core.Account.Identity.Attestations.DirectorshipDeclaration`, `V2.Core.Account.Identity.Attestations.OwnershipDeclaration`, `V2.Core.Account.Identity.Attestations.TermsOfService.Account`, `V2.Core.Account.Identity.Attestations.TermsOfService.Storer`, `V2.Core.Account.Identity.Individual.AdditionalTermsOf

_…truncated…_

### v49.1.0-alpha.1  (v49.1.0-alpha.1)
<https://github.com/stripe/stripe-dotnet/releases/tag/v49.1.0-alpha.1>

This release changes the pinned API version to `2025-09-30.preview`. It is built on top of SDK version 49.0.0 and 49.1.0-beta.1 which contain breaking changes. Please review the changelog for these versions if upgrading from older SDK versions.

* [#3183](https://github.com/stripe/stripe-dotnet/pull/3183) Update generated code for private-preview
  * Add support for new resource `V2.MoneyManagement.RecipientVerification`
  * Add support for `Acknowledge`, `Create`, `Get`, and `RecipientVerifications` methods on resource `V2.MoneyManagement.RecipientVerification`
  * Add support for `Update` method on resources `V2.Billing.PricingPlanSubscription` and `V2.Billing.ServiceAction`
  * Add support for `CryptoWallets` on `V2.Account.Configuration.RecipientData.Features`, `V2.Core.Account.Configuration.Recipient.Capabilities`, `V2AccountConfigurationRecipientDataFeaturesOptions`, and `V2CoreAccountConfigurationRecipientCapabilitiesOptions`
  * Add support for `LookupKey` on `V2.Billing.CadenceCreateOptions`, `V2.Billing.CadenceUpdateOptions`, and `V2.Billing.Cadence`
  * Add support for `SettingsData` on `V2.Billing.Cadence`
  * Add support for `MonthOfYear` on `V2.Billing.Cadence.BillingCycle.Month` and `V2BillingCadenceBillingCycleMonthOptions`
  * Add support for `ClaimedAt`, `ExpiresAt`, `SandboxDetails`, and `Status` on `V2.Core.ClaimableSandbox`
  * Remove support for `ApiKeys` on `V2.Core.ClaimableSandbox`
  * Add support for `V1EventId` on `V2.Event`
  * Add support for `RecipientVerification` on `V2.MoneyManagement.OutboundPaymentCreateOptions`, `V2.MoneyManagement.OutboundPayment`, `V2.MoneyManagement.OutboundTransferCreateOptions`, and `V2.MoneyManagement.OutboundTransfer`
  * Add support for `CryptoWallet` on `V2.MoneyManagement.PayoutMethod` and `V2MoneyManagementOutboundSetupIntentPayoutMethodDataOptions`
  * Add support for `WillActivateAt` and `WillCancelAt` on `V2.Billing.PricingPlanSubscription.ServicingStatusTransitions` and `V2.Billing.RateCardSubscription.ServicingStatusTransitions`
  * Add support for `CustomPricingUnitDetails` on `V2.Billing.RateCardRate.CustomPricingUnitAmount`, `V2.Billing.ServiceAction.CreditGrant.Amount.CustomPricingUnit`, and `V2.Billing.ServiceAction.CreditGrantPerTenant.Amount.CustomPricingUnit`
  * Add support for `OriginType` on `V2.MoneyManagement.ReceivedDebit.BankTransfer`
  * Add support for `SepaBankAccount` on `V2.MoneyManagement.FinancialAddressCreateOptions`
  * Remove support for `Price` on `V2.Billing.RateCardRateCreateOptions`
  * Add support for `LookupKeys` on `V2.Billing.CadenceListOptions`
  * Change type of `V2.Billing.CadenceCancelOptions.Include`, `V2.Billing.CadenceCreateOptions.Include`, `V2.Billing.CadenceGetOptions.Include`, `V2.Billing.CadenceListOptions.Include`, and `V2.Billing.CadenceUpdateOptions.Include` from `literal('invoice_discount_rules')` to `enum('invoice_discount_rules'|'settings_data')`
  * Remove support for `Customer` and `Type` on `V2BillingCadencePayerOptions`
  * Remove support for `AlertId` on `EventsV2CoreHealthApiErrorResolvedEvent`, `EventsV2CoreHealthApiLatencyResolvedEvent`, `EventsV2CoreHealthAuthorizationRateDropResolvedEvent`, `EventsV2CoreHealthIssuingAuthorizationRequestTimeoutResolvedEvent`, `EventsV2CoreHealthPaymentMethodErrorResolvedEvent`, `EventsV2CoreHealthTrafficVolumeDropResolvedEvent`, and `EventsV2CoreHealthWebhookLatencyResolvedEvent`
  * Add support for thin event `V1AccountUpdatedEvent` with related object `V2.Account`
  * Add support for thin events `V1ApplicationFeeCreatedEvent`, `V1ApplicationFeeRefundedEvent`, `V1BillingPortalConfigurationCreatedEvent`, `V1BillingPortalConfigurationUpdatedEvent`, `V1CapabilityUpdatedEvent`, `V1ChargeCapturedEvent`, `V1ChargeDisputeClosedEvent`, `V1ChargeDisputeCreatedEvent`, `V1ChargeDisputeFundsReinstatedEvent`, `V1ChargeDisputeFundsWithdrawnEvent`, `V1ChargeDisputeUpdatedEvent`, `V1ChargeExpiredEvent`, `V1ChargeFailedEvent`, `V1ChargePendingEvent`, `V1ChargeRefundUpdatedEvent`, `V1ChargeRefundedEvent`, `V1ChargeSucceededEvent`, `V1ChargeUpdatedEvent`, `V1CheckoutSessionAsyncPaymentFailedEvent`, `V1CheckoutSessionAsyncPaymentSucceededEvent`, `V1CheckoutSessionCompletedEvent`, `V1CheckoutSessionExpiredEvent`, `V1ClimateOrderCanceledEvent`, `V1ClimateOrderCreatedEvent`, `V1ClimateOrderDelayedEvent`, `V1ClimateOrderDeliveredEvent`, `V1ClimateOrderProductSubstitutedEvent`, `V1ClimateProductCreatedEvent`, `V1ClimateProductPricingUpdatedEvent`, `V1CouponCreatedEvent`, `V1CouponDeletedEvent`, `V1CouponUpdatedEvent`, `V1CreditNoteCreatedEvent`, `V1CreditNoteUpdatedEvent`, `V1CreditNoteVoidedEvent`, `V1CustomerCreatedEvent`, `V1CustomerDeletedEvent`, `V1CustomerDiscountCreatedEvent`, `V1CustomerDiscountDeletedEvent`, `V1CustomerDiscountUpdatedEvent`, `V1CustomerSubscriptionCreatedEvent`, `V1CustomerSubscriptionDeletedEvent`, `V1CustomerSubscriptionPausedEvent`, `V1CustomerSubscriptionPendingUpdateAppliedEvent`, `V1CustomerSubscriptionPendingUpdateExpiredEvent`, `V1CustomerSubscriptionResumedEvent`, `V1CustomerSubscriptionTrialWillEndEvent`, `V1CustomerSubscriptionUpdatedEvent`, `V1CustomerTaxIdCreatedEvent`, `V1CustomerTaxIdDeletedEvent`, `V1CustomerTaxIdUpdatedEvent`, `V1CustomerUpdatedEvent`, `V1FileCreatedEvent`, `V1FinancialConnectionsAccountCreatedEvent`, `V1FinancialConnectionsAccountDeactivatedEvent`, `V1FinancialConnectionsAccountDisconnectedEvent`, `V1FinancialConnectionsAccountReactivatedEvent`, `V1FinancialConnectionsAccountRefreshedBalanceEvent`, `V1FinancialConnectionsAccountRefreshedOwnershipEvent`, `V1FinancialConnectionsAccountRefreshedTransactionsEvent`, `V1IdentityVerificationSessionCanceledEvent`, `V1IdentityVerificationSessionCreatedEvent`, `V1IdentityVerificationSessionProcessingEvent`, `V1IdentityVerificationSessionRedactedEvent`, `V1IdentityVerificationSessionRequiresInputEvent`, `V1IdentityVerificationSessionVerifiedEvent`, `V1InvoiceCreatedEvent`, `V1InvoiceDeletedEvent`, `V1InvoiceFinalizationFailedEvent`, `V1InvoiceFinalized

_…truncated…_

### v49.0.0  (v49.0.0)
<https://github.com/stripe/stripe-dotnet/releases/tag/v49.0.0>

This release changes the pinned API version to `2025-09-30.clover` and contains breaking changes (prefixed with ⚠️ below)

* [#3168](https://github.com/stripe/stripe-dotnet/pull/3168) ⚠️ Add strongly typed EventNotifications
  We've overhauled how V2 Events are handled in the SDK! This approach should provide a lot more information at authoring and compile time, leading to more robust integrations. As part of this process, there are a number of changes to be aware of.
  - Added matching `EventNotification` classes to every v2 `Event`. For example, there's now a `V1BillingMeterErrorReportTriggeredEventNotification` to match the existing `V1BillingMeterErrorReportTriggeredEvent`. Each notification class defines a `fetchEvent()` method to retrieve its corresponding event. For events with related objects, there's a `fetchRelatedObject()` method that performs the API call and casts the response to the correct type.
  - ⚠️ Rename function `StripeClient.parseThinEvent` to `StripeClient.parseEventNotification` and remove the `Stripe.ThinEvent` class.
      - This function now returns a `Stripe.V2.Core.EventNotification` (which is the shared base class that all of the more specific `Stripe..Events.*EventNotification` classes  share) instead of `Stripe.ThinEvent`. When applicable, these event notifications will have the `relatedObject` property and a `fetchRelatedObject()` function. They also have a `fetchEvent()` method to retrieve their corresponding `Stripe.Event.*Event` instance.
      - If you parse an event the SDK doesn't have types for (e.g. it's newer than the SDK you're using), you'll get an instance of `Stripe.Events.UnknownEventNotification` instead of a more specific type. It has both the `relatedObject` property and the `FetchRelatedObject()` function (but they may be/return `null`)
* [#3194](https://github.com/stripe/stripe-dotnet/pull/3194) Add `StripeContext` object
  - Add the `StripeContext` class. Previously, one could only pass a string for `StripeContext` property of the `RequestOptions` class. You can now use the new class as well.
  - ⚠️ Change `EventNotification` (formerly known as `ThinEvent`)'s `context` property from `string` to `StripeContext`
* [#3200](https://github.com/stripe/stripe-dotnet/pull/3200) Move `V2.Event` API resources to `V2.Core.Events`
  - ⚠️ Move all V2 Event-related classes (`Event`, `EventDestination`,`EventReason` etc) from `Stripe.V2` to `Stripe.V2.Core`. They now correctly match their API path and are in line with all other resources. To update your code:
     - `Stripe.V2.Event` -> `Stripe.V2.Core.Event`
     - `Stripe.V2.EventDestination` -> `Stripe.V2.Core.EventDestination`
     - `Stripe.V2.EventReason` -> `Stripe.V2.Core.EventReason`
     - `Stripe.V2.EventReasonRequest` -> `Stripe.V2.Core.EventReasonRequest`
     - `Stripe.V2.EventRelatedObject` -> `Stripe.V2.Core.EventRelatedObject`
* [#3206](https://github.com/stripe/stripe-dotnet/pull/3206) ⚠️ Drop support for .NET Core 3.1 & clarify policy
  -  Read our new [language version support policy](https://docs.stripe.com/sdks/versioning?server=dotnet#stripe-sdk-language-version-support-policy)
       - ⚠️ In this release, we drop support for .NET Core 3.1.
       - Support for .NET Core versions 5 & 7 are deprecated and will be removed in the next major version scheduled for March 2026
* [#3197](https://github.com/stripe/stripe-dotnet/pull/3197) Remove unused obsolete classes SourceTransactionsListOptions and SourceTransactionsGetOptions
  * ⚠️ Removed class `SourceTransactionsListOptions` in favor of `SourceTransactionListOptions`
  * ⚠️ Removed unused class `SourceTransactionsGetOptions`
* [#3167](https://github.com/stripe/stripe-dotnet/pull/3167) ⚠️ Build SDK w/ V2 OpenAPI spec
  - ⚠️ The delete methods for v2 APIs (the ones in the `StripeClient.v2` namespace) now return a `V2DeletedObject` which has the id of the object that has been deleted and a string representing the type of the object that has been deleted.
* [#3171](https://github.com/stripe/stripe-dotnet/pull/3171) Adds ability to specify file name and type when calling FileService.Create
  * ⚠️ Changes `FileCreateOptions`.`File` from a `Stream` to a `MultipartFileContent` type.  This type lets you optionally specify a `Name` and `Type` to use when creating the file.
* [#3174](https://github.com/stripe/stripe-dotnet/pull/3174) `just format` formats entire solution
* [#3172](https://github.com/stripe/stripe-dotnet/pull/3172) Update generated code
  * ⚠️ Changes type of `UseStripeSdk` in `PaymentIntentNextAction` and `SetupIntentNextAction` to be `Dictionary<string, object>`
  * ⚠️ Removes `PaymentIntentNextActionUseStripeSdk` and `SetupIntentNextActionUseStripeSdk`
* [#3170](https://github.com/stripe/stripe-dotnet/pull/3170) Adds public BaseUrl to RawRequestOptions
  * Adds `BaseUrl` to `RawRequestOptions` for raw request calls to endpoints at hosts other than `api.stripe.com`


* [#3175](https://github.com/stripe/stripe-dotnet/pull/3175), [#3190](https://github.com/stripe/stripe-dotnet/pull/3190), [#3205](https://github.com/stripe/stripe-dotnet/pull/3205) Update generated code based on incoming API changes in the `2025-09-30.clover` API version.
  * ⚠️ Remove support for `BalanceReport` and `PayoutReconciliationReport` on `AccountSession.Components` and `AccountSessionComponentsOptions`
  * ⚠️ Change type of `InvoiceSubscriptionDetailsOptions.CancelAt`, `SubscriptionCreateOptions.CancelAt` and `SubscriptionUpdateOptions.CancelAt` from `DateTime` to `DateTime | enum('max_period_end'|'min_period_end')`
  * ⚠️ Remove support for `Coupon` on `Discount`, `PromotionCodeCreateOptions`, and `PromotionCode`. Use `Discount.Source.Coupon`, `PromotionCodeCreateOptions.Promotion.Coupon`, and `PromotionCode.Promotion.Coupon` instead.
  * ⚠️ Remove support for `Link` and `PayByBank` on `PaymentMethodUpdateOptions`
  * Add support for new resource `BalanceSettings`
  * Add support for `Get` and `Update` methods on resource `BalanceSettings`
  * Add

_…truncated…_


## v48.x

### v48.6.0-alpha.2  (v48.6.0-alpha.2)
<https://github.com/stripe/stripe-dotnet/releases/tag/v48.6.0-alpha.2>

* [#3173](https://github.com/stripe/stripe-dotnet/pull/3173) generate private-preview SDK w/ mid Sept changes
  * Add support for `retrieve` method on resource `V2.Core.ClaimableSandbox`
  * Add support for `month_of_year` on `V2.Billing.Cadence#create.billing_cycle.month` and `V2.Billing.Cadence.billing_cycle.month`
  * Add support for `claimed_at`, `expires_at`, `sandbox_details`, and `status` on `V2.Core.ClaimableSandbox`
  * Remove support for `api_keys` on `V2.Core.ClaimableSandbox`
  * Change type of `V2.Core.ClaimableSandbox.claim_url` from `string` to `nullable(string)`
  * Add support for new value `current_billing_period_end` on enums `V2.Billing.Intent#create.actions[].deactivate.effective_at.type` and `V2.Billing.IntentAction.deactivate.effective_at.type`
  * Add support for `will_activate_at` and `will_cancel_at` on `V2.Billing.PricingPlanSubscription.servicing_status_transitions` and `V2.Billing.RateCardSubscription.servicing_status_transitions`
  * Add support for `category` and `priority` on `V2.Billing.ServiceAction#create.credit_grant_per_tenant`, `V2.Billing.ServiceAction#create.credit_grant`, `V2.Billing.ServiceAction.credit_grant_per_tenant`, and `V2.Billing.ServiceAction.credit_grant`
  * Change `V2.Billing.LicenseFee#update.display_name` to be optional
  * Add support for `invoices` on `EventsV2BillingCadenceBilledEvent`
  * Add support for thin events `V2CoreClaimableSandboxClaimedEvent`, `V2CoreClaimableSandboxExpiredEvent`, `V2CoreClaimableSandboxExpiringEvent`, and `V2CoreClaimableSandboxSandboxDetailsOwnerAccountUpdatedEvent` with related object `V2.Core.ClaimableSandbox`
  * Remove support for thin event `V2BillingCadenceErroredEvent` with related object `V2.Billing.Cadence`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v48.6.0-alpha.2/CHANGELOG.md).

### v48.6.0-beta.1  (v48.6.0-beta.1)
<https://github.com/stripe/stripe-dotnet/releases/tag/v48.6.0-beta.1>

This release changes the pinned API version to `2025-08-27.preview`.

* [#3156](https://github.com/stripe/stripe-dotnet/pull/3156) Update generated code for beta
  * Add support for `Get` and `List` methods on resource `InvoicePayment`
  * Add support for `List` method on resource `Mandate`
  * Add support for `Applied` on `V2.Core.Account.Configuration.Customer`, `V2.Core.Account.Configuration.Merchant`, `V2.Core.Account.Configuration.Recipient`, `V2.Core.Account.Configuration.Storer`, `V2CoreAccountConfigurationCustomerOptions`, `V2CoreAccountConfigurationMerchantOptions`, `V2CoreAccountConfigurationRecipientOptions`, and `V2CoreAccountConfigurationStorerOptions`
  * Change type of `Billing.AlertTriggered.Value` from `longInteger` to `decimal_string`
  * Add support for `DisplayName` on `V2.MoneyManagement.FinancialAccountCreateOptions` and `V2.MoneyManagement.FinancialAccount`
  * Add support for `CurrencyConversion` on `V2.MoneyManagement.Transaction.Flow` and `V2.MoneyManagement.TransactionEntry.TransactionDetails.Flow`
  * Add support for `Payments` on `BalanceSettingsUpdateOptions` and `BalanceSettings`
  * Remove support for `DebitNegativeBalances`, `Payouts`, and `SettlementTiming` on `BalanceSettingsUpdateOptions` and `BalanceSettings`
  * Add support for `Mandate` on `Charge.PaymentMethodDetails.Pix`, `PaymentAttemptRecord.PaymentMethodDetails.Pix`, and `PaymentRecord.PaymentMethodDetails.Pix`
  * Add support for `CouponData` on `CheckoutSessionDiscountOptions`
  * Add support for `MandateOptions` on `Checkout.Session.PaymentMethodOptions.Pix`, `CheckoutSessionPaymentMethodOptionsPixOptions`, `PaymentIntent.PaymentMethodOptions.Pix`, and `PaymentIntentPaymentMethodOptionsPixOptions`
  * Change type of `Checkout.Session.PaymentMethodOptions.Pix.SetupFutureUsage`, `CheckoutSessionPaymentMethodOptionsPixOptions.SetupFutureUsage`, `PaymentIntent.PaymentMethodOptions.Pix.SetupFutureUsage`, and `PaymentIntentPaymentMethodOptionsPixOptions.SetupFutureUsage` from `literal('none')` to `enum('none'|'off_session')`
  * Add support for `Amount` on `Mandate.MultiUse`, `PaymentAttemptRecord`, and `PaymentRecord`
  * Add support for `Currency` on `Mandate.MultiUse`
  * Add support for `Pix` on `Mandate.PaymentMethodDetails`, `SetupAttempt.PaymentMethodDetails`, `SetupIntent.PaymentMethodOptions`, and `SetupIntentPaymentMethodOptionsOptions`
  * Add support for `Limit` on `PaymentAttemptRecordListOptions`
  * Add support for `AmountAuthorized`, `AmountRefunded`, and `Application` on `PaymentAttemptRecord` and `PaymentRecord`
  * Add support for `ProcessorDetails` on `PaymentAttemptRecord`, `PaymentRecordReportPaymentOptions`, and `PaymentRecord`
  * Remove support for `PaymentReference` on `PaymentAttemptRecord`, `PaymentRecordReportPaymentOptions`, and `PaymentRecord`
  * Add support for `Installments` on `PaymentAttemptRecord.PaymentMethodDetails.Alma` and `PaymentRecord.PaymentMethodDetails.Alma`
  * Add support for `TransactionId` on `PaymentAttemptRecord.PaymentMethodDetails.Alma`, `PaymentAttemptRecord.PaymentMethodDetails.AmazonPay`, `PaymentAttemptRecord.PaymentMethodDetails.Billie`, `PaymentAttemptRecord.PaymentMethodDetails.KakaoPay`, `PaymentAttemptRecord.PaymentMethodDetails.KrCard`, `PaymentAttemptRecord.PaymentMethodDetails.NaverPay`, `PaymentAttemptRecord.PaymentMethodDetails.Payco`, `PaymentAttemptRecord.PaymentMethodDetails.RevolutPay`, `PaymentAttemptRecord.PaymentMethodDetails.SamsungPay`, `PaymentAttemptRecord.PaymentMethodDetails.Satispay`, `PaymentRecord.PaymentMethodDetails.Alma`, `PaymentRecord.PaymentMethodDetails.AmazonPay`, `PaymentRecord.PaymentMethodDetails.Billie`, `PaymentRecord.PaymentMethodDetails.KakaoPay`, `PaymentRecord.PaymentMethodDetails.KrCard`, `PaymentRecord.PaymentMethodDetails.NaverPay`, `PaymentRecord.PaymentMethodDetails.Payco`, `PaymentRecord.PaymentMethodDetails.RevolutPay`, `PaymentRecord.PaymentMethodDetails.SamsungPay`, and `PaymentRecord.PaymentMethodDetails.Satispay`
  * Add support for `Location` and `Reader` on `PaymentAttemptRecord.PaymentMethodDetails.Paynow` and `PaymentRecord.PaymentMethodDetails.Paynow`
  * Add support for `LatestActiveMandate` on `PaymentMethod`
  * Add support for `Metadata` and `Period` on `QuotePreviewSubscriptionSchedule.Phase.AddInvoiceItem`
  * Add support for `PixDisplayQrCode` on `SetupIntent.NextAction`
  * Add support for `ReaderSecurity` on `Terminal.ConfigurationCreateOptions`, `Terminal.ConfigurationUpdateOptions`, and `Terminal.Configuration`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v48.6.0-beta.1/CHANGELOG.md).

### v48.6.0-alpha.1  (v48.6.0-alpha.1)
<https://github.com/stripe/stripe-dotnet/releases/tag/v48.6.0-alpha.1>

* [#3166](https://github.com/stripe/stripe-dotnet/pull/3166) Use the right API version 2025-08-27.preview
* [#3162](https://github.com/stripe/stripe-dotnet/pull/3162) Update generated code for private-preview
  
  * Add support for `AttachCadence` method on resource `Subscription`
  * Add support for `Currency` and `ExternalCustomerId` on `Billing.AlertTriggered`
  * Add support for `CustomPricingUnit` on `Billing.AlertTriggered`, `Billing.CreditBalanceSummary.Balance.AvailableBalance`, `Billing.CreditBalanceSummary.Balance.LedgerBalance`, `Billing.CreditBalanceTransaction.Credit.Amount`, `Billing.CreditBalanceTransaction.Debit.Amount`, `Billing.CreditGrant.Amount`, and `BillingCreditGrantAmountOptions`
  * Add support for `Customer` on `Billing.AlertListOptions`
  * Change type of `Billing.Alert.AlertType`, `Billing.AlertCreateOptions.AlertType`, and `Billing.AlertListOptions.AlertType` from `literal('usage_threshold')` to `enum('credit_balance_threshold'|'usage_threshold')`
  * Add support for `CreditBalanceThreshold` on `Billing.AlertCreateOptions` and `Billing.Alert`
  * Add support for `BillableItems` on `Billing.CreditGrant.ApplicabilityConfig.Scope`, `BillingCreditBalanceSummaryFilterApplicabilityScopeOptions`, and `BillingCreditGrantApplicabilityConfigScopeOptions`
  * Change type of `Billing.CreditBalanceSummary.Balance.AvailableBalance.Type`, `Billing.CreditBalanceSummary.Balance.LedgerBalance.Type`, `Billing.CreditBalanceTransaction.Credit.Amount.Type`, `Billing.CreditBalanceTransaction.Debit.Amount.Type`, `Billing.CreditGrant.Amount.Type`, and `BillingCreditGrantAmountOptions.Type` from `literal('monetary')` to `enum('custom_pricing_unit'|'monetary')`
  * Add support for `LicenseFeeSubscriptionDetails` and `RateCardSubscriptionDetails` on `InvoiceItem.Parent` and `InvoiceLineItem.Parent`
  * Change type of `InvoiceItem.Parent.Type` from `literal('subscription_details')` to `enum('license_fee_subscription_details'|'rate_card_subscription_details'|'subscription_details')`
  * Add support for `LicenseFeeDetails` and `RateCardRateDetails` on `InvoiceItem.Pricing` and `InvoiceLineItem.Pricing`
  * Change type of `InvoiceItem.Pricing.Type` and `InvoiceLineItem.Pricing.Type` from `literal('price_details')` to `enum('license_fee_details'|'price_details'|'rate_card_rate_details')`
  * Add support for `BillingCadence` on `InvoiceCreatePreviewOptions`, `SubscriptionCreateOptions`, and `Subscription`
  * Add support for `BillingCadenceDetails` on `Invoice.Parent` and `QuotePreviewInvoice.Parent`
  * Add support for new resources `V2.AccountLink`, `V2.Account`, `V2.Billing.BillSettingVersion`, `V2.Billing.BillSetting`, `V2.Billing.Cadence`, `V2.Billing.CollectionSettingVersion`, `V2.Billing.CollectionSetting`, `V2.Billing.CustomPricingUnit`, `V2.Billing.IntentAction`, `V2.Billing.Intent`, `V2.Billing.LicenseFeeSubscription`, `V2.Billing.LicenseFeeVersion`, `V2.Billing.LicenseFee`, `V2.Billing.LicensedItem`, `V2.Billing.MeteredItem`, `V2.Billing.PricingPlanComponent`, `V2.Billing.PricingPlanSubscription`, `V2.Billing.PricingPlanVersion`, `V2.Billing.PricingPlan`, `V2.Billing.Profile`, `V2.Billing.RateCardRate`, `V2.Billing.RateCardSubscription`, `V2.Billing.RateCardVersion`, `V2.Billing.RateCard`, `V2.Billing.ServiceAction`, `V2.Core.ClaimableSandbox`, `V2.Reporting.ReportRun`, `V2.Reporting.Report`, and `V2.Tax.AutomaticRule`
  * Add support for `Create`, `Deactivate`, `Find`, `Get`, and `Update` methods on resource `V2.Tax.AutomaticRule`
  * Add support for `Create` and `Get` methods on resources `V2.Billing.ServiceAction` and `V2.Reporting.ReportRun`
  * Add support for `Get` method on resources `V2.Billing.LicenseFeeSubscription` and `V2.Reporting.Report`
  * Add support for `Create` method on resources `V2.AccountLink` and `V2.Core.ClaimableSandbox`
  * Add support for `Cancel`, `Create`, `Get`, `List`, and `Update` methods on resources `V2.Billing.Cadence` and `V2.Billing.RateCardSubscription`
  * Add support for `Create`, `Get`, `List`, and `Update` methods on resources `V2.Billing.BillSetting`, `V2.Billing.CollectionSetting`, `V2.Billing.CustomPricingUnit`, `V2.Billing.LicenseFee`, `V2.Billing.LicensedItem`, `V2.Billing.MeteredItem`, `V2.Billing.PricingPlan`, `V2.Billing.Profile`, and `V2.Billing.RateCard`
  * Add support for `Get` and `List` methods on resources `V2.Billing.BillSettingVersion`, `V2.Billing.CollectionSettingVersion`, `V2.Billing.IntentAction`, `V2.Billing.LicenseFeeVersion`, `V2.Billing.PricingPlanSubscription`, `V2.Billing.PricingPlanVersion`, and `V2.Billing.RateCardVersion`
  * Add support for `Create`, `Delete`, `Get`, and `List` methods on resource `V2.Billing.RateCardRate`
  * Add support for `Create`, `Delete`, `Get`, `List`, and `Update` methods on resource `V2.Billing.PricingPlanComponent`
  * Add support for `Cancel`, `Commit`, `Create`, `Get`, `List`, `ReleaseReservation`, and `Reserve` methods on resource `V2.Billing.Intent`
  * Add support for `Close`, `Create`, `Get`, `List`, and `Update` methods on resource `V2.Account`
  * Add support for `Changes` on `V2.Event`
  * Add support for thin events `AccountConfigurationRecipientDataAccountLinkCompletedEvent`, `AccountConfigurationRecipientDataFeatureStatusUpdatedEvent`, and `AccountRequirementsUpdatedEvent` with related object `V2.Account`
  * Add support for thin events `V2BillingCadenceBilledEvent`, `V2BillingCadenceCanceledEvent`, `V2BillingCadenceCreatedEvent`, and `V2BillingCadenceErroredEvent` with related object `V2.Billing.Cadence`
  * Add support for thin events `V2BillingLicenseFeeCreatedEvent` and `V2BillingLicenseFeeUpdatedEvent` with related object `V2.Billing.LicenseFee`
  * Add support for thin event `V2BillingLicenseFeeVersionCreatedEvent` with related object `V2.Billing.LicenseFeeVersion`
  * Add support for thin events `V2BillingLicensedItemCreatedEvent` and `V2BillingLicensedItemUpdatedEvent` with related object `V2.Billing.LicensedItem`
  * Add support for thin events `V2BillingMetere

_…truncated…_

### v48.5.0  (v48.5.0)
<https://github.com/stripe/stripe-dotnet/releases/tag/v48.5.0>

* [#3164](https://github.com/stripe/stripe-dotnet/pull/3164) Add section on private preview SDKs in readme
* [#3159](https://github.com/stripe/stripe-dotnet/pull/3159) Update generated code. This release changes the pinned API version to `2025-08-27.basil`.
  * Add support for `BalanceReport`, `PayoutDetails`, and `PayoutReconciliationReport` on `AccountSession.Components` and `AccountSessionComponentsOptions`
  * Add support for `Name` on `BillingPortal.ConfigurationCreateOptions`, `BillingPortal.ConfigurationUpdateOptions`, and `BillingPortal.Configuration`
  * Add support for `Installments` on `Charge.PaymentMethodDetails.Alma`
  * Add support for `TransactionId` on `Charge.PaymentMethodDetails.Alma`, `Charge.PaymentMethodDetails.AmazonPay`, `Charge.PaymentMethodDetails.Billie`, `Charge.PaymentMethodDetails.KakaoPay`, `Charge.PaymentMethodDetails.KrCard`, `Charge.PaymentMethodDetails.NaverPay`, `Charge.PaymentMethodDetails.Payco`, `Charge.PaymentMethodDetails.RevolutPay`, `Charge.PaymentMethodDetails.SamsungPay`, and `Charge.PaymentMethodDetails.Satispay`
  * Add support for `Location` and `Reader` on `Charge.PaymentMethodDetails.Paynow`
  * Add support for `AmountIncludesIof` on `Checkout.Session.PaymentMethodOptions.Pix`, `CheckoutSessionPaymentMethodOptionsPixOptions`, `PaymentIntent.PaymentMethodOptions.Pix`, and `PaymentIntentPaymentMethodOptionsPixOptions`
  * Add support for `Metadata` and `Period` on `InvoiceScheduleDetailsPhaseAddInvoiceItemOptions`, `SubscriptionAddInvoiceItemOptions`, `SubscriptionSchedule.Phase.AddInvoiceItem`, and `SubscriptionSchedulePhaseAddInvoiceItemOptions`
  * Add support for `ExpMonth` and `ExpYear` on `Issuing.CardCreateOptions`
  * Add support for `ExcludedPaymentMethodTypes` on `PaymentIntentCreateOptions` and `PaymentIntent`
  * Add support for `PayoutMethod` on `PayoutCreateOptions` and `Payout`
  * Add support for `Mxn` on `Terminal.Configuration.Tipping` and `TerminalConfigurationTippingOptions`
  * Add support for `Card` on `Terminal.TestHelpersReaderPresentPaymentMethodOptions`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v48.5.0/CHANGELOG.md).

### v48.5.0-beta.2  (v48.5.0-beta.2)
<https://github.com/stripe/stripe-dotnet/releases/tag/v48.5.0-beta.2>

* [#3160](https://github.com/stripe/stripe-dotnet/pull/3160) Bring back invoice payments APIs that were missing in the public preview SDKs
    * Add support for new resource `InvoicePayment`
    * Add support for `Get` and `List` methods on resource `InvoicePayment`
  
* [#3155](https://github.com/stripe/stripe-dotnet/pull/3155) Fix links to pinned api versions in CHANGELOG.md in beta branch

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v48.5.0-beta.2/CHANGELOG.md).

### v48.5.0-beta.1  (v48.5.0-beta.1)
<https://github.com/stripe/stripe-dotnet/releases/tag/v48.5.0-beta.1>

This release changes the pinned API version to `2025-07-30.preview`.

* [#3143](https://github.com/stripe/stripe-dotnet/pull/3143) Update generated code for beta
  * Add support for new resources `Billing.MeterUsageRow`, `Billing.MeterUsage`, and `Terminal.OnboardingLink`
  * Add support for `Get` method on resource `Billing.MeterUsage`
  * Add support for `Create` method on resource `Terminal.OnboardingLink`
  * Add support for `MonthlyPayoutDays` and `WeeklyPayoutDays` on `BalanceSettings.Payouts.Schedule` and `BalanceSettingsPayoutsScheduleOptions`
  * Remove support for `MonthlyAnchor` and `WeeklyAnchor` on `BalanceSettings.Payouts.Schedule` and `BalanceSettingsPayoutsScheduleOptions`
  * Add support for `DelayDaysOverride` on `BalanceSettingsSettlementTimingOptions`
  * Remove support for `DelayDays` on `BalanceSettingsSettlementTimingOptions`
  * Add support for `UpdateDiscounts` on `CheckoutSessionPermissionsOptions`
  * Add support for `Discounts` and `SubscriptionData` on `Checkout.SessionUpdateOptions`
  * Add support for `SmartDisputes` on `Dispute`
  * Add support for `Upi` on `Invoice.PaymentSettings.PaymentMethodOptions`, `InvoicePaymentSettingsPaymentMethodOptionsOptions`, `QuotePreviewInvoice.PaymentSettings.PaymentMethodOptions`, `Subscription.PaymentSettings.PaymentMethodOptions`, and `SubscriptionPaymentSettingsPaymentMethodOptionsOptions`
  * Add support for `TransactionId` on `PaymentAttemptRecord.PaymentMethodDetails.Cashapp` and `PaymentRecord.PaymentMethodDetails.Cashapp`
  * Add support for `AmountDetails` on `PaymentIntentCaptureOptions`, `PaymentIntentConfirmOptions`, `PaymentIntentCreateOptions`, `PaymentIntentIncrementAuthorizationOptions`, and `PaymentIntentUpdateOptions`
  * Add support for `PaymentDetails` on `PaymentIntentIncrementAuthorizationOptions`
  * Add support for `Storer` on `V2.Core.Account.Identity.Attestations.TermsOfService` and `V2CoreAccountIdentityAttestationsTermsOfServiceOptions`
  * Add support for `CollectionOptions` on `V2.Core.AccountLink.UseCase.AccountOnboarding`, `V2.Core.AccountLink.UseCase.AccountUpdate`, `V2CoreAccountLinkUseCaseAccountOnboardingOptions`, and `V2CoreAccountLinkUseCaseAccountUpdateOptions`
  * Change type of `V2.Core.AccountLink.UseCase.AccountOnboarding.Configurations`, `V2.Core.AccountLink.UseCase.AccountUpdate.Configurations`, `V2CoreAccountLinkUseCaseAccountOnboardingOptions.Configurations`, and `V2CoreAccountLinkUseCaseAccountUpdateOptions.Configurations` from `literal('recipient')` to `enum('customer'|'merchant'|'recipient'|'storer')`
  * Add support for `BankAccountType` on `V2.MoneyManagement.PayoutMethod.BankAccount`
  * Add support for thin event `V2CoreAccountLinkReturnedEvent`
  * Add support for thin event `V2MoneyManagementPayoutMethodUpdatedEvent` with related object `V2.MoneyManagement.PayoutMethod`
  * Remove support for thin event `V2CoreAccountLinkCompletedEvent`
  * Remove support for thin event `V2OffSessionPaymentRequiresCaptureEvent` with related object `V2.Payments.OffSessionPayment`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v48.5.0-beta.1/CHANGELOG.md).

### v48.4.0  (v48.4.0)
<https://github.com/stripe/stripe-dotnet/releases/tag/v48.4.0>

This release changes the pinned API version to `2025-07-30.basil`.

* [#3151](https://github.com/stripe/stripe-dotnet/pull/3151) Update generated code
  * Add support for `InstantPayoutsPromotion` on `AccountSession.Components` and `AccountSessionComponentsOptions`
  * Add support for `AdjustableQuantity` on `BillingPortal.Configuration.Features.SubscriptionUpdate.Products` and `BillingPortalConfigurationFeaturesSubscriptionUpdateProductsOptions`
  * Add support for `TransactionId` on `Charge.PaymentMethodDetails.Cashapp`
  * Add support for `OriginContext` on `Checkout.SessionCreateOptions` and `Checkout.Session`
  * Add support for `Template` on `Checkout.Session.InvoiceCreation.InvoiceData.RenderingOptions`, `CheckoutSessionInvoiceCreationInvoiceDataRenderingOptionsOptions`, `PaymentLink.InvoiceCreation.InvoiceData.RenderingOptions`, and `PaymentLinkInvoiceCreationInvoiceDataRenderingOptionsOptions`
  * Add support for `SetupFutureUsage` on `Checkout.Session.PaymentMethodOptions.Pix` and `CheckoutSessionPaymentMethodOptionsPixOptions`
  * Add support for `Duration` on `InvoiceScheduleDetailsPhaseOptions` and `SubscriptionSchedulePhaseOptions`
  * Add support for `PriceData` on `PaymentLinkLineItemOptions`
  * Add support for `Standard` on `Tax.Registration.CountryOptions.Ae`, `Tax.Registration.CountryOptions.Au`, `Tax.Registration.CountryOptions.Ch`, `Tax.Registration.CountryOptions.Gb`, `Tax.Registration.CountryOptions.Jp`, `Tax.Registration.CountryOptions.No`, `Tax.Registration.CountryOptions.Nz`, `Tax.Registration.CountryOptions.Sg`, `TaxRegistrationCountryOptionsAeOptions`, `TaxRegistrationCountryOptionsAlOptions`, `TaxRegistrationCountryOptionsAoOptions`, `TaxRegistrationCountryOptionsAuOptions`, `TaxRegistrationCountryOptionsAwOptions`, `TaxRegistrationCountryOptionsBaOptions`, `TaxRegistrationCountryOptionsBbOptions`, `TaxRegistrationCountryOptionsBdOptions`, `TaxRegistrationCountryOptionsBfOptions`, `TaxRegistrationCountryOptionsBhOptions`, `TaxRegistrationCountryOptionsBsOptions`, `TaxRegistrationCountryOptionsCdOptions`, `TaxRegistrationCountryOptionsChOptions`, `TaxRegistrationCountryOptionsEtOptions`, `TaxRegistrationCountryOptionsGbOptions`, `TaxRegistrationCountryOptionsGnOptions`, `TaxRegistrationCountryOptionsIsOptions`, `TaxRegistrationCountryOptionsJpOptions`, `TaxRegistrationCountryOptionsMeOptions`, `TaxRegistrationCountryOptionsMkOptions`, `TaxRegistrationCountryOptionsMrOptions`, `TaxRegistrationCountryOptionsNoOptions`, `TaxRegistrationCountryOptionsNzOptions`, `TaxRegistrationCountryOptionsOmOptions`, `TaxRegistrationCountryOptionsRsOptions`, `TaxRegistrationCountryOptionsSgOptions`, `TaxRegistrationCountryOptionsSrOptions`, `TaxRegistrationCountryOptionsUyOptions`, `TaxRegistrationCountryOptionsZaOptions`, and `TaxRegistrationCountryOptionsZwOptions`
  * Add support for `Aed`, `Bgn`, `Huf`, and `Ron` on `Terminal.Configuration.Tipping` and `TerminalConfigurationTippingOptions`
* [#3152](https://github.com/stripe/stripe-dotnet/pull/3152) Mark StripeConfiguration as partial so we can add configuration in beta branch
* [#3150](https://github.com/stripe/stripe-dotnet/pull/3150) Adds usage string to telemetry on API calls made through `StripeClient` service accessors

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v48.4.0/CHANGELOG.md).

### v48.4.0-beta.2  (v48.4.0-beta.2)
<https://github.com/stripe/stripe-dotnet/releases/tag/v48.4.0-beta.2>

* [#3145](https://github.com/stripe/stripe-dotnet/pull/3145) Pull in V2 FinancialAccount changes for June release
  * Add support for `Close` and `Create` methods on resource `V2.MoneyManagement.FinancialAccount`
  * Add support for `Storer` on `V2.Core.Account.Configuration` and `V2CoreAccountConfigurationOptions`
  * Add support for `StatusDetails` on `V2.MoneyManagement.FinancialAccount`
  * Add support for `Status` on `V2.MoneyManagement.FinancialAccountListOptions`
  * Add support for thin events `V2CoreAccountIncludingConfigurationStorerCapabilityStatusUpdatedEvent` and `V2CoreAccountIncludingConfigurationStorerUpdatedEvent` with related object `V2.Core.Account`
  * Add support for error types `AlreadyExistsException` and `NonZeroBalanceException`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v48.4.0-beta.2/CHANGELOG.md).

### v48.4.0-beta.1  (v48.4.0-beta.1)
<https://github.com/stripe/stripe-dotnet/releases/tag/v48.4.0-beta.1>

This release changes the pinned API version to `2025-06-30.preview`.

* [#3132](https://github.com/stripe/stripe-dotnet/pull/3132) Update generated code for beta
  * Change type of `CheckoutSessionSubscriptionDataOptions.BillingMode`, `InvoiceScheduleDetailsOptions.BillingMode`, `InvoiceSubscriptionDetailsOptions.BillingMode`, `Quote.SubscriptionData.BillingMode`, `QuoteSubscriptionDataOptions.BillingMode`, `SubscriptionCreateOptions.BillingMode`, and `SubscriptionScheduleCreateOptions.BillingMode` from `enum('classic'|'flexible')` to `billing_mode`
  * Add support for `SubmissionMethod` on `Dispute.EvidenceDetails`
  * Add support for `OnDemand` and `Subscriptions` on `OrderPaymentSettingsPaymentMethodOptionsKlarnaOptions`
  * Change type of `Order.Payment.Settings.PaymentMethodOptions.Klarna.SetupFutureUsage` and `OrderPaymentSettingsPaymentMethodOptionsKlarnaOptions.SetupFutureUsage` from `literal('none')` to `enum('none'|'off_session'|'on_session')`
  * Add support for `Crypto` on `PaymentAttemptRecord.PaymentMethodDetails` and `PaymentRecord.PaymentMethodDetails`
  * Change type of `PaymentIntent.PaymentMethodOptions.Gopay.SetupFutureUsage` and `PaymentIntentPaymentMethodOptionsGopayOptions.SetupFutureUsage` from `literal('none')` to `enum('none'|'off_session')`
  * Change type of `QuotePreviewSubscriptionSchedule.BillingMode`, `Subscription.BillingMode`, and `SubscriptionSchedule.BillingMode` from `enum('classic'|'flexible')` to `SubscriptionsResourceBillingMode`
  * Change type of `SubscriptionMigrateOptions.BillingMode` from `literal('flexible')` to `billing_mode_migrate`
  * Remove support for `BillingModeDetails` on `Subscription`
  * Add support for `ProofOfAddress` on `V2.Core.Account.Identity.BusinessDetails.Documents` and `V2CoreAccountIdentityBusinessDetailsDocumentsOptions`
  * Add support for `Metadata` on `V2.MoneyManagement.FinancialAccount`
  * Remove support for `Description` on `V2.MoneyManagement.FinancialAccount`
  * Remove support for `Attempts` on `V2.Payments.OffSessionPayment`
  * Change type of `V2.Payments.OffSessionPayment.TransferData.Amount` from `integer` to `nullable(integer)`
  * Add support for `FromAccount`, `OutboundPayment`, and `OutboundTransfer` on `V2.MoneyManagement.ReceivedCredit.BalanceTransfer`
  * Change type of `V2.MoneyManagement.ReceivedCredit.BalanceTransfer.Type` from `literal('payout_v1')` to `enum('outbound_payment'|'outbound_transfer'|'payout_v1')`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v48.4.0-beta.1/CHANGELOG.md).

### v48.3.0  (v48.3.0)
<https://github.com/stripe/stripe-dotnet/releases/tag/v48.3.0>

* [#3139](https://github.com/stripe/stripe-dotnet/pull/3139) Update generated code
  * Add support for `Migrate` method on resource `Subscription`
  * Add support for `CollectPaymentMethod` and `ConfirmPaymentIntent` methods on resource `Terminal.Reader`
  * Add support for `CryptoPayments` on `Account.Capabilities` and `AccountCapabilitiesOptions`
  * Add support for `ProofOfAddress` on `AccountDocumentsOptions`
  * Add support for `MonthlyPayoutDays` and `WeeklyPayoutDays` on `Account.Settings.Payouts.Schedule` and `AccountSettingsPayoutsScheduleOptions`
  * Add support for `Crypto` on `Charge.PaymentMethodDetails`, `ConfirmationToken.PaymentMethodPreview`, `ConfirmationTokenPaymentMethodDataOptions`, `PaymentIntent.PaymentMethodOptions`, `PaymentIntentPaymentMethodDataOptions`, `PaymentIntentPaymentMethodOptionsOptions`, `PaymentMethodCreateOptions`, `PaymentMethod`, and `SetupIntentPaymentMethodDataOptions`
  * Change type of `Charge.PaymentMethodDetails.Card.Installments.Plan.Type`, `ConfirmationToken.PaymentMethodOptions.Card.Installments.Plan.Type`, `ConfirmationTokenPaymentMethodOptionsCardInstallmentsPlanOptions.Type`, `InvoicePaymentSettingsPaymentMethodOptionsCardInstallmentsPlanOptions.Type`, `PaymentIntent.PaymentMethodOptions.Card.Installments.AvailablePlans.Type`, `PaymentIntent.PaymentMethodOptions.Card.Installments.Plan.Type`, and `PaymentIntentPaymentMethodOptionsCardInstallmentsPlanOptions.Type` from `literal('fixed_count')` to `enum('bonus'|'fixed_count'|'revolving')`
  * Add support for `Subscriptions` on `CheckoutSessionPaymentMethodOptionsKlarnaOptions` and `PaymentIntentPaymentMethodOptionsKlarnaOptions`
  * Add support for `BillingMode` on `CheckoutSessionSubscriptionDataOptions`, `InvoiceScheduleDetailsOptions`, `InvoiceSubscriptionDetailsOptions`, `Quote.SubscriptionData`, `QuoteSubscriptionDataOptions`, `SubscriptionCreateOptions`, `SubscriptionScheduleCreateOptions`, `SubscriptionSchedule`, and `Subscription`
  * Change type of `Dispute.EnhancedEligibilityTypes` from `literal('visa_compelling_evidence_3')` to `enum('visa_compelling_evidence_3'|'visa_compliance')`
  * Add support for `RelatedPerson` on `Identity.VerificationSessionCreateOptions` and `Identity.VerificationSession`
  * Add support for `Matching` on `Identity.VerificationSession.Options`
  * Add support for `Klarna` on `Mandate.PaymentMethodDetails`, `SetupIntent.PaymentMethodOptions`, and `SetupIntentPaymentMethodOptionsOptions`
  * Add support for `OnDemand` on `PaymentIntentPaymentMethodOptionsKlarnaOptions`
  * Change type of `PaymentIntent.PaymentMethodOptions.Klarna.SetupFutureUsage` and `PaymentIntentPaymentMethodOptionsKlarnaOptions.SetupFutureUsage` from `literal('none')` to `enum('none'|'off_session'|'on_session')`
  * Add support for `Ua` on `Tax.Registration.CountryOptions` and `TaxRegistrationCountryOptionsOptions`
  * Change type of `Terminal.LocationUpdateOptions.DisplayName` from `string` to `emptyable(string)`
  * Add support for `CollectPaymentMethod` and `ConfirmPaymentIntent` on `Terminal.Reader.Action`
  * Add support for `Status` on `Treasury.FinancialAccountListOptions`
  * Add support for snapshot event `TerminalReaderActionUpdated` with resource `Terminal.Reader`
* [#3137](https://github.com/stripe/stripe-dotnet/pull/3137) Updated StripeClient snippets in Readme.md

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v48.3.0/CHANGELOG.md).

### v48.3.0-beta.2  (v48.3.0-beta.2)
<https://github.com/stripe/stripe-dotnet/releases/tag/v48.3.0-beta.2>

* [#3142](https://github.com/stripe/stripe-dotnet/pull/3142) Pull in OffSessionPayment changes for the May release

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v48.3.0-beta.2/CHANGELOG.md).

### v48.3.0-beta.1  (v48.3.0-beta.1)
<https://github.com/stripe/stripe-dotnet/releases/tag/v48.3.0-beta.1>

This release changes the pinned API version to `2025-05-28.preview`.

* [#3123](https://github.com/stripe/stripe-dotnet/pull/3123) Update generated code for beta
  ### Breaking changes
  * Remove support for deprecated previews
    * Remove support for resources `Billing.MeterErrorReport`, `GiftCards.Card`, `GiftCards.Transaction`, and `Privacy.RedactionJobRootObjects`
    * Remove support for `Create`, `Get`, `List`, `Update`, and `Validate` methods on resource `GiftCards.Card`
    * Remove support for `Cancel`, `Confirm`, `Create`, `Get`, `List`, and `Update` methods on resource `GiftCards.Transaction`
    * Remove support for `Provisioning` on `ProductCreateOptions` and `Product`
  * Change type of `CheckoutSessionLineItemOptions.Quantity` from `emptyable(longInteger)` to `longInteger`
  * Change type of `InvoiceSubscriptionDetailsOptions.CancelAt`, `SubscriptionCreateOptions.CancelAt`, and `SubscriptionUpdateOptions.CancelAt` from `DateTime` to `DateTime | enum('max_period_end'|'min_period_end')`
  * Remove support for `Credits` on `OrderCreateOptions`, `OrderUpdateOptions`, and `Order`
  * Remove support for `AmountRemaining` on `Order`
  * Remove support for `AmountCredit` on `Order.TotalDetails`
  * Remove support for `AsyncWorkflows` on `PaymentIntentCaptureOptions`, `PaymentIntentConfirmOptions`, `PaymentIntentCreateOptions`, `PaymentIntentDecrementAuthorizationOptions`, `PaymentIntentIncrementAuthorizationOptions`, `PaymentIntentUpdateOptions`, and `PaymentIntent`
  * Change type of `PaymentRecordReportPaymentAttemptCanceledOptions.Metadata`, `PaymentRecordReportPaymentAttemptFailedOptions.Metadata`, `PaymentRecordReportPaymentAttemptGuaranteedOptions.Metadata`, `PaymentRecordReportPaymentAttemptOptions.Metadata`, and `PaymentRecordReportPaymentOptions.Metadata` from `map(string: string)` to `emptyable(map(string: string))`
  * Change type of `Privacy.RedactionJob.Objects` from `$Privacy.RedactionJobRootObjects` to `RedactionResourceRootObjects`
  * Change type of `Privacy.RedactionJobValidationError.ErroringObject` from `map(string: string)` to `RedactionResourceErroringObject`
  * Remove support for `StatusDetails` and `Status` on `Tax.Association`
  * Remove support for snapshot event `BillingMeterErrorReportTriggered` with resource `Billing.MeterErrorReport`

  ### Other changes
  * Add support for `Migrate` method on resource `Subscription`
  * Add support for `Distance`, `PickupLocationName`, `ReturnLocationName`, and `VehicleIdentificationNumber` on `ChargePaymentDetailsCarRentalOptions`, `PaymentIntent.PaymentDetails.CarRental`, and `PaymentIntentPaymentDetailsCarRentalOptions`
  * Add support for `DriverIdentificationNumber` and `DriverTaxNumber` on `ChargePaymentDetailsCarRentalDriverOptions`, `PaymentIntent.PaymentDetails.CarRental.Driver`, and `PaymentIntentPaymentDetailsCarRentalDriverOptions`
  * Add support for `Institution` on `FinancialConnections.Account`
  * Add support for `Countries` on `FinancialConnections.Institution`
  * Add support for `Location` and `Reader` on `PaymentAttemptRecord.PaymentMethodDetails.Affirm`, `PaymentAttemptRecord.PaymentMethodDetails.WechatPay`, `PaymentRecord.PaymentMethodDetails.Affirm`, and `PaymentRecord.PaymentMethodDetails.WechatPay`
  * Add support for `Hooks` on `PaymentIntentCaptureOptions`, `PaymentIntentConfirmOptions`, `PaymentIntentCreateOptions`, `PaymentIntentDecrementAuthorizationOptions`, `PaymentIntentIncrementAuthorizationOptions`, `PaymentIntentUpdateOptions`, and `PaymentIntent`
  * Add support for `CardPresent` on `PaymentIntentAmountDetailsLineItem.PaymentMethodOptions`
  * Add support for `Livemode` on `Privacy.RedactionJob`
  * Add support for `BillingThresholds` on `QuotePreviewSubscriptionSchedule.DefaultSettings`, `QuotePreviewSubscriptionSchedule.Phase.Item`, and `QuotePreviewSubscriptionSchedule.Phase`
  * Add support for `BillingModeDetails` on `Subscription`
  * Add support for `TaxTransactionAttempts` on `Tax.Association`
  * Add support for `ConfirmConfig` on `Terminal.Reader.Action.ConfirmPaymentIntent` and `Terminal.ReaderConfirmPaymentIntentOptions`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v48.3.0-beta.1/CHANGELOG.md).

### v48.2.0  (v48.2.0)
<https://github.com/stripe/stripe-dotnet/releases/tag/v48.2.0>

This release changes the pinned API version to `2025-05-28.basil`.

* [#3128](https://github.com/stripe/stripe-dotnet/pull/3128) Update generated code. 
  * Add support for `AttachPayment` method on resource `Invoice`
  * Add support for `CollectInputs` method on resource `Terminal.Reader`
  * Add support for `SucceedInputCollection` and `TimeoutInputCollection` test helper methods on resource `Terminal.Reader`
  * Add support for `PixPayments` on `Account.Capabilities` and `AccountCapabilitiesOptions`
  * Add support for `DisputesList` and `PaymentDisputes` on `AccountSession.Components` and `AccountSessionComponentsOptions`
  * Add support for `RefundAndDisputePrefunding` on `Balance`
  * Add support for `BalanceType` on `BalanceTransaction`
  * Add support for `Location` and `Reader` on `Charge.PaymentMethodDetails.Affirm` and `Charge.PaymentMethodDetails.WechatPay`
  * Add support for `PaymentMethodRemove` on `CheckoutSessionSavedPaymentMethodOptionsOptions`
  * Add support for `SetupFutureUsage` on `Checkout.Session.PaymentMethodOptions.NaverPay`
  * Add support for `PostPaymentAmount` and `PrePaymentAmount` on `CreditNote`
  * Add support for `Sex`, `UnparsedPlaceOfBirth`, and `UnparsedSex` on `Identity.VerificationReport.Document` and `Identity.VerificationSession.VerifiedOutputs`
  * Add support for `BillingThresholds` on `InvoiceScheduleDetailsPhaseItemOptions`, `InvoiceScheduleDetailsPhaseOptions`, `InvoiceSubscriptionDetailsItemOptions`, `SubscriptionCreateOptions`, `SubscriptionItemCreateOptions`, `SubscriptionItemOptions`, `SubscriptionItemUpdateOptions`, `SubscriptionItem`, `SubscriptionSchedule.DefaultSettings`, `SubscriptionSchedule.Phase.Item`, `SubscriptionSchedule.Phase`, `SubscriptionScheduleDefaultSettingsOptions`, `SubscriptionSchedulePhaseItemOptions`, `SubscriptionSchedulePhaseOptions`, `SubscriptionUpdateOptions`, and `Subscription`
  * Add support for `Satispay` on `PaymentIntent.PaymentMethodOptions` and `PaymentIntentPaymentMethodOptionsOptions`
  * Add support for `CaptureMethod` on `PaymentIntent.PaymentMethodOptions.Billie`
  * Add support for `KakaoPay`, `KrCard`, `NaverPay`, `Payco`, and `SamsungPay` on `PaymentMethodConfigurationCreateOptions`, `PaymentMethodConfigurationUpdateOptions`, and `PaymentMethodConfiguration`
  * Add support for `NetworkDeclineCode` on `Refund.DestinationDetails.Paypal`
  * Add support for `Metadata` on `Tax.CalculationLineItem` and `TaxCalculationLineItemOptions`
  * Add support for `ReturnUrl` on `Terminal.Reader.Action.ProcessPaymentIntent.ProcessConfig` and `TerminalReaderProcessConfigOptions`
  * Add support for `CollectInputs` on `Terminal.Reader.Action`
  * Add support for snapshot event `InvoicePaymentPaid` with resource `InvoicePayment`
* [#3124](https://github.com/stripe/stripe-dotnet/pull/3124) Adds CONTRIBUTING.md

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v48.2.0/CHANGELOG.md).

### v48.2.0-beta.2  (v48.2.0-beta.2)
<https://github.com/stripe/stripe-dotnet/releases/tag/v48.2.0-beta.2>

* [#3122](https://github.com/stripe/stripe-dotnet/pull/3122) Update generated code for beta
  Release specs are identical.

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v48.2.0-beta.2/CHANGELOG.md).

### v48.2.0-beta.1  (v48.2.0-beta.1)
<https://github.com/stripe/stripe-dotnet/releases/tag/v48.2.0-beta.1>

* [#3107](https://github.com/stripe/stripe-dotnet/pull/3107) Update generated code for beta
  This release changes the pinned API version to `2025-04-30.preview`.

  * Add support for `BillingMode` on `CheckoutSessionSubscriptionDataOptions`, `InvoiceScheduleDetailsOptions`, `InvoiceSubscriptionDetailsOptions`, `Quote.SubscriptionData`, `QuotePreviewSubscriptionSchedule`, `QuoteSubscriptionDataOptions`, `SubscriptionCreateOptions`, `SubscriptionScheduleCreateOptions`, `SubscriptionSchedule`, and `Subscription`
  * Add support for `AccountNumber` on `ConfirmationToken.PaymentMethodPreview.AcssDebit` and `PaymentMethod.AcssDebit`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v48.2.0-beta.1/CHANGELOG.md).

### v48.1.0  (v48.1.0)
<https://github.com/stripe/stripe-dotnet/releases/tag/v48.1.0>

This release changes the pinned API version to `2025-04-30.basil`.

* [#3102](https://github.com/stripe/stripe-dotnet/pull/3102) Update generated code
  * Add support for `MinorityOwnedBusinessDesignation` on `Account.BusinessProfile` and `AccountBusinessProfileOptions`
  * Add support for `RegistrationDate` on `Account.Company`, `AccountCompanyOptions`, and `TokenAccountCompanyOptions`
  * Add support for `UsCfpbData` on `AccountCreateOptions`, `AccountUpdateOptions`, `Person`, and `TokenPersonOptions`
  * Add support for `TaxId` on `Charge.BillingDetails`, `ConfirmationToken.PaymentMethodPreview.BillingDetails`, `ConfirmationTokenPaymentMethodDataBillingDetailsOptions`, `PaymentIntentPaymentMethodDataBillingDetailsOptions`, `PaymentMethod.BillingDetails`, `PaymentMethodBillingDetailsOptions`, and `SetupIntentPaymentMethodDataBillingDetailsOptions`
  * Add support for `WalletOptions` on `Checkout.SessionCreateOptions` and `Checkout.Session`
  * Add support for `Provider` on `Checkout.Session.AutomaticTax`, `Invoice.AutomaticTax`, and `Quote.AutomaticTax`
  * Add support for `PaymentMethodOptions` on `TestHelpersConfirmationTokenCreateOptions`
  * Add support for `Installments` on `ConfirmationToken.PaymentMethodOptions.Card`
  * Add support for `Context` on `Event`
  * Add support for `Billie` on `PaymentIntent.PaymentMethodOptions` and `PaymentIntentPaymentMethodOptionsOptions`
  * Add support for `Pix` on `PaymentMethodConfigurationCreateOptions`, `PaymentMethodConfigurationUpdateOptions`, and `PaymentMethodConfiguration`
  * Add support for `Klarna` on `PaymentMethodDomain`
  * Add support for `PendingReason` on `Refund`
  * Add support for `Aw`, `Az`, `Bd`, `Bf`, `Bj`, `Cm`, `Cv`, `Et`, `In`, `Kg`, `La`, and `Ph` on `Tax.Registration.CountryOptions` and `TaxRegistrationCountryOptionsOptions`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v48.1.0/CHANGELOG.md).

### v48.1.0-beta.4  (v48.1.0-beta.4)
<https://github.com/stripe/stripe-dotnet/releases/tag/v48.1.0-beta.4>

* [#3099](https://github.com/stripe/stripe-dotnet/pull/3099) Update generated code for beta
  * Add support for new resources `FxQuote` and `PaymentIntentAmountDetailsLineItem`
  * Add support for `Create`, `Get`, and `List` methods on resource `FxQuote`
  * Remove support for `AttachPaymentIntent` method on resource `Invoice`
  * Add support for `RegistrationDate` on `AccountCompanyOptions`, `AccountCompany`, and `TokenAccountCompanyOptions`
  * Add support for `CustomerReference` and `OrderReference` on `ChargePaymentDetailsOptions`, `PaymentIntentPaymentDetailsOptions`, and `PaymentIntentPaymentDetails`
  * Add support for `TaxId` on `ChargeBillingDetails`, `ConfirmationTokenPaymentMethodDataBillingDetailsOptions`, `ConfirmationTokenPaymentMethodPreviewBillingDetails`, `PaymentIntentPaymentMethodDataBillingDetailsOptions`, `PaymentMethodBillingDetailsOptions`, `PaymentMethodBillingDetails`, `SetupIntentPaymentMethodDataBillingDetailsOptions`, and `TreasuryOutboundPaymentDestinationPaymentMethodDataBillingDetailsOptions`
  * Add support for `PriceData` on `CheckoutSessionLineItemsOptions`
  * Change type of `CheckoutSessionLineItemsOptions.Quantity` from `longInteger` to `emptyable(longInteger)`
  * Add support for `Script` on `CouponCreateOptions` and `Coupon`
  * Add support for `Type` on `Coupon`
  * Add support for `FxQuote` on `PaymentIntentConfirmOptions`, `PaymentIntentCreateOptions`, `PaymentIntentUpdateOptions`, `PaymentIntent`, `TransferCreateOptions`, and `Transfer`
  * Add support for `DiscountAmount`, `LineItems`, `Shipping`, and `Tax` on `PaymentIntentAmountDetails`
  * Add support for `Pix` on `PaymentMethodConfigurationCreateOptions`, `PaymentMethodConfigurationUpdateOptions`, and `PaymentMethodConfiguration`
  * Add support for `UsCfpbData` on `Person` and `TokenPersonOptions`
  * Add support for `PendingReason` on `Refund`
  * Add support for `Aw`, `Az`, `Bd`, `Bj`, `Et`, `Kg`, `La`, and `Ph` on `TaxRegistrationCountryOptionsOptions` and `TaxRegistrationCountryOptions`
  * Add support for snapshot event `FxQuoteExpired` with resource `FxQuote`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v48.1.0-beta.4/CHANGELOG.md).

### v48.1.0-beta.3  (v48.1.0-beta.3)
<https://github.com/stripe/stripe-dotnet/releases/tag/v48.1.0-beta.3>

* [#3094](https://github.com/stripe/stripe-dotnet/pull/3094) Update generated code for beta
  * Add support for new resources `Privacy.RedactionJobRootObjects`, `Privacy.RedactionJobValidationError`, and `Privacy.RedactionJob`
  * Add support for `Cancel`, `Create`, `Get`, `List`, `Run`, `Update`, and `Validate` methods on resource `RedactionJob`
  * Add support for `Get` and `List` methods on resource `RedactionJobValidationError`
  * Add support for `MinorityOwnedBusinessDesignation` on `AccountBusinessProfileOptions` and `AccountBusinessProfile`
  * Add support for `ExportTaxTransactions` and `PaymentDisputes` on `AccountSessionComponentsOptions`
  * Add support for `WalletOptions` on `Checkout.SessionCreateOptions` and `CheckoutSession`
  * Add support for `Klarna` on `PaymentMethodDomain`
  * Add support for `In` on `TaxRegistrationCountryOptionsOptions` and `TaxRegistrationCountryOptions`
* [#3092](https://github.com/stripe/stripe-dotnet/pull/3092) Handle `ExternalAccount` field in `ExternalAccountCreateOptions`
  - Changes `ExternalAccount` property in `ExternalAccountCreateOptions` from a `string` to a union type.

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v48.1.0-beta.3/CHANGELOG.md).

### v48.1.0-beta.2  (v48.1.0-beta.2)
<https://github.com/stripe/stripe-dotnet/releases/tag/v48.1.0-beta.2>

* Re-releasing 48.1.0-beta.1 as it had publishing issues

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v48.1.0-beta.2/CHANGELOG.md).

### v48.1.0-beta.1  (v48.1.0-beta.1)
<https://github.com/stripe/stripe-dotnet/releases/tag/v48.1.0-beta.1>

* [#3079](https://github.com/stripe/stripe-dotnet/pull/3079) Update generated code for beta

This release changes the pinned API version to `2025-03-31.preview`

### Breaking Changes
  * Remove support for `AmountOverpaid` on `InvoicePayment`
  * Change type of `InvoicePayment.IsDefault` from `nullable(boolean)` to `boolean`
  * Remove support for `InterchangeFees`, `NetTotal`, `NetworkFees`, and `TransactionVolume` on `IssuingSettlement`
  * Change type of `PaymentAttemptRecordPaymentMethodDetails.Type` and `PaymentRecordPaymentMethodDetails.Type` from `literal('custom')` to `string`
  * Remove support for `ApplicationFeeAmount`, `Discount`, `PaidOutOfBand`, `Paid`, `PaymentIntent`, `Quote`, `SubscriptionDetails`, `SubscriptionProrationDate`, `Tax`, `TotalTaxAmounts`, and `TransferData` on `QuotePreviewInvoice`
  * Remove support for `BillingThresholds` on `QuotePreviewSubscriptionScheduleDefaultSettings`, `QuotePreviewSubscriptionSchedulePhasesItems`, and `QuotePreviewSubscriptionSchedulePhases`
  * Remove support for `Coupon` on `QuotePreviewSubscriptionSchedulePhases`
  * Remove support for `Value` on `TerminalReaderActionCollectInputsInputsSelectionChoices`, `TerminalReaderActionCollectInputsInputsSelection`, and `TerminalReaderInputsSelectionChoicesOptions`
  * Change type of `QuotePreviewInvoice.Parent.SubscriptionDetail.subscription` from `string` to `expandable($Subscription)`
  * Change `CheckoutSession.Permission.update` to be optional
  * Change type of `PaymentAttemptRecord.PaymentMethodDetail.type` and `PaymentRecord.PaymentMethodDetail.type` from `literal('custom')` to `string`
  * Change type of `PaymentAttemptRecord.payment_record` from `string` to `nullable(string)`
  * Change `PaymentAttemptRecord.PaymentMethodDetail.custom` and `PaymentRecord.PaymentMethodDetail.custom` to be optional
  * Change type of `PaymentRecord.latest_payment_attempt_record` from `string` to `nullable(string)`
  * Change type of `Order.CreateParamsPaymentSettingPaymentMethodOptionWechatPay.client` and `Order.UpdateParamsPaymentSettingPaymentMethodOptionWechatPay.client` to be optional


### Additions
  * Add support for new resources `BalanceSettings`
  * Add support for `Get` and `Update` methods on resource `BalanceSettings`
  * Add support for `Create`, `Delete`, `Get`, `List`, and `Update` methods on a new `ExternalAccountService` to access cards and bank accounts made available in the new path `v1/external_accounts`
  * Add support for `StripeBalancePayments` on `AccountCapabilitiesOptions` and `AccountCapabilities`
  * Add support for `CustomerAccount` on `Billing.CreditBalanceSummaryRetrieveOptions`, `Billing.CreditBalanceTransactionListOptions`, `Billing.CreditGrantCreateOptions`, `Billing.CreditGrantListOptions`, `BillingCreditBalanceSummary`, `BillingCreditGrant`, `BillingPortal.SessionCreateOptions`, `BillingPortalSession`, `Checkout.SessionCreateOptions`, `Checkout.SessionListOptions`, `CheckoutSession`, `ConfirmationTokenPaymentMethodPreview`, `CreditNoteListOptions`, `CreditNote`, `CustomerBalanceTransaction`, `CustomerCashBalanceTransaction`, `CustomerCashBalance`, `CustomerPaymentMethod`, `CustomerSessionCreateOptions`, `CustomerSession`, `CustomerTaxIdOwner`, `CustomerTaxId`, `Customer`, `Discount`, `FinancialConnectionsAccountAccountHolderOptions`, `FinancialConnectionsAccountAccountHolder`, `FinancialConnectionsSessionAccountHolderOptions`, `FinancialConnectionsSessionAccountHolder`, `InvoiceCreateOptions`, `InvoiceCreatePreviewOptions`, `InvoiceItemCreateOptions`, `InvoiceItemListOptions`, `InvoiceItem`, `InvoiceListOptions`, `Invoice`, `PaymentIntentCreateOptions`, `PaymentIntentListOptions`, `PaymentIntentUpdateOptions`, `PaymentIntent`, `PaymentMethodAttachOptions`, `PaymentMethod`, `PromotionCodeCreateOptions`, `PromotionCodeListOptions`, `PromotionCode`, `QuoteCreateOptions`, `QuoteListOptions`, `QuotePreviewInvoice`, `QuotePreviewSubscriptionSchedule`, `QuoteUpdateOptions`, `Quote`, `SetupAttempt`, `SetupIntentCreateOptions`, `SetupIntentListOptions`, `SetupIntentUpdateOptions`, `SetupIntent`, `Subscription.CreateParams`, `Subscription.ListParams`, `SubscriptionSchedule.CreateParams`, `SubscriptionSchedule.ListParams`, `SubscriptionSchedule`, `Subscription`, `TaxIdOwnerOptions`, `TaxIdOwner`, and `TaxId`
  * Add support for `StripeBalance` on `ChargePaymentMethodDetails`, `ConfirmationTokenPaymentMethodDataOptions`, `ConfirmationTokenPaymentMethodPreview`, `CustomerPaymentMethod`, `PaymentAttemptRecordPaymentMethodDetails`, `PaymentIntentPaymentMethodDataOptions`, `PaymentIntentPaymentMethodOptionsOptions`, `PaymentIntentPaymentMethodOptions`, `PaymentMethodCreateOptions`, `PaymentMethod`, `PaymentRecordPaymentMethodDetails`, `SetupAttemptPaymentMethodDetails`, and `SetupIntentPaymentMethodDataOptions`
  * Add support for `UpdateLineItems` and `UpdateShippingDetails` on `CheckoutSessionPermissionsOptions` and `CheckoutSessionPermissions`
  * Add support for `Provider` on `CheckoutSessionAutomaticTax`, `InvoiceAutomaticTax`, `QuoteAutomaticTax`, and `QuotePreviewInvoiceAutomaticTax`
  * Add support for `TaxCalculationReference` on `CreditNoteLineItem`, `CreditNotePreviewLines`, `InvoiceLineItem`, `LineItem`, `PaymentLinkLineItem`, `QuoteComputedUpfrontLineItems`, `QuoteLineItem`, and `SessionLineItem`
  * Add support for `PaymentMethodOptions` on `TestHelpersConfirmationTokenCreateOptions`
  * Add support for `Installments` on `ConfirmationTokenPaymentMethodOptionsCard`
  * Add support for `Context` on `Event`
  * Add support for `RelatedCustomerAccount` on `Identity.VerificationSessionCreateOptions`, `Identity.VerificationSessionListOptions`, and `IdentityVerificationSession`
  * Add support for `NetworkData` on `IssuingDisputeSettlementDetail`
  * Add support for `InterchangeFeesAmount`, `NetTotalAmount`, `NetworkFeesAmount`, `OtherFeesAmount`, `OtherFeesCount`, and `TransactionAmount` on `IssuingSettlement`
  * Add support for `R

_…truncated…_

### v48.0.2  (v48.0.2)
<https://github.com/stripe/stripe-dotnet/releases/tag/v48.0.2>

* [#3101](https://github.com/stripe/stripe-dotnet/pull/3101) Replace Dictionary with ConcurrentDictionary in SerializablePropertyCache to fix a concurrency related error reported in [#3100](https://github.com/stripe/stripe-dotnet/issues/3100)

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v48.0.2/CHANGELOG.md).

### v48.0.1  (v48.0.1)
<https://github.com/stripe/stripe-dotnet/releases/tag/v48.0.1>

* [#3090](https://github.com/stripe/stripe-dotnet/pull/3090) Disable Json.NET metadata special handling. Fixes issue [#3068](https://github.com/stripe/stripe-dotnet/issues/3068)

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v48.0.1/CHANGELOG.md).

### v48.0.0  (v48.0.0)
<https://github.com/stripe/stripe-dotnet/releases/tag/v48.0.0>

* [#3074](https://github.com/stripe/stripe-dotnet/pull/3074) System.Text.Json Serialization Support release to GA
  * Add System.Text.Json support for serializing Stripe.net entities and objects for applications running on .NET 6 and above. Now you can pass a Stripe.net object or collection of objects to the System.Text.Json serializer and it will produce the correct JSON string.
* [#3056](https://github.com/stripe/stripe-dotnet/pull/3056) Support for APIs in the new API version 2025-03-31.basil
  
  This release changes the pinned API version to `2025-03-31.basil`.
  
  ### ⚠️ Breaking changes  due to changes in the Stripe API
  
  Please review details for the breaking changes and alternatives in the [Stripe API changelog](https://docs.stripe.com/changelog/basil#2025-03-31.basil) before upgrading.

  * Remove support for resources `SubscriptionItemUsageRecordSummary` and `SubscriptionItemUsageRecord`
  * Remove support for `Create` method on resource `SubscriptionItemUsageRecord`
  * Remove support for `List`, `ListAsync`, `ListAutoPaginating`, and `ListAutoPaginatingAsync` methods on resource `SubscriptionItemUsageRecordSummary`
  * Remove support for `Upcoming` and `UpcomingAsync` methods on resource `Invoice`
  * Remove support for `Invoice` on `Charge` and `PaymentIntent`
  * Remove support for `ShippingDetails` on `CheckoutSession`
  * Remove support for `Carrier`, `Phone`, and `TrackingNumber` on `SessionCollectedInformationShippingDetails`
  * Remove support for `Refund` on `CreditNoteCreateOptions`, `CreditNotePreviewLinesListOptions`, `CreditNotePreviewOptions`, and `CreditNote`
  * Remove support for `TaxAmounts` on `CreditNoteLineItem`, `CreditNote`, and `InvoiceLineItem`
  * Remove support for `AmountExcludingTax` and `UnitAmountExcludingTax` on `CreditNoteLineItem` and `InvoiceLineItem`
  * Remove support for `Coupon` on `CustomerCreateOptions`, `CustomerUpdateOptions`, `InvoiceCreatePreviewOptions`, `InvoiceScheduleDetailsPhasesOptions`, `SubscriptionCreateOptions`, `SubscriptionSchedulePhasesOptions`, `SubscriptionSchedulePhases`, and `SubscriptionUpdateOptions`
  * Remove support for `PromotionCode` on `CustomerCreateOptions`, `CustomerUpdateOptions`, `SubscriptionCreateOptions`, and `SubscriptionUpdateOptions`
  * Remove support for `Price` on `InvoiceItemCreateOptions`, `InvoiceItemUpdateOptions`, `InvoiceItem`, `InvoiceLineItemUpdateOptions`, `InvoiceLineItem`, and `InvoiceLinesOptions`
  * Remove support for `BillingThresholds` on `InvoiceScheduleDetailsPhaseItemOptions`, `InvoiceScheduleDetailsPhaseOptions`, `InvoiceSubscriptionDetailsItemOptions`, `SubscriptionCreateOptions`, `SubscriptionItemCreateOptions`, `SubscriptionItemUpdateOptions`, `SubscriptionItem`, `SubscriptionItemsOptions`, `SubscriptionScheduleDefaultSettingsOptions`, `SubscriptionScheduleDefaultSettings`, `SubscriptionSchedulePhaseItemOptions`, `SubscriptionSchedulePhaseItem`, `SubscriptionSchedulePhaseOptions`, `SubscriptionSchedulePhase`, `SubscriptionUpdateOptions`, and `Subscription`
  * Remove support for `ApplicationFeeAmount`, `Charge`, `PaidOutOfBand`, `Paid`, `PaymentIntent`, `Quote`, `Subscription`, `SubscriptionDetails`, `SubscriptionProrationDate`, `Tax`, `TotalTaxAmounts`, and `TransferData` on `Invoice`
  * Remove support for `Discount` on `Invoice` and `Subscription`
  * Remove support for `InvoiceItem`, `ProrationDetails`, `Proration`, `TaxRates`, and `Type` on `InvoiceLineItem`
  * Remove support for `Plan` and `SubscriptionItem` on `InvoiceItem` and `InvoiceLineItem`
  * Remove support for `UnitAmount` on `InvoiceItemCreateOptions`, `InvoiceItemUpdateOptions`, and `InvoiceItem`
  * Remove support for `SubscriptionItems` on `InvoiceLineItemListOptions` and `InvoiceLineItemsListOptions`
  * Remove support for `Subscription` and `UnitAmountDecimal` on `InvoiceItem`
  * Remove support for `NaverPay` on `PaymentMethodUpdateOptions`
  * Remove support for `AggregateUsage` on `PlanCreateOptions`, `Plan`, `PriceRecurringOptions`, and `PriceRecurring`
  * Remove support for `CurrentPeriodEnd` and `CurrentPeriodStart` on `Subscription`
  * Remove support for Page on `V2.EventDestinationListOptions` and `V2.EventListOptions`
  
  ### Additions
  
  * Add support for new resource `InvoicePayment`
  * Add support for `Get` and `List` methods on resource `InvoicePayment`
  * Add support for `BilliePayments`, `NzBankAccountBecsDebitPayments`, and `SatispayPayments` on `AccountCapabilitiesOptions` and `AccountCapabilities`
  * Add support for `HostedPaymentMethodSave` on `AccountSettingsInvoicesOptions` and `AccountSettingsInvoices`
  * Add support for `Invoices` on `AccountSettingsOptions`
  * Add support for `PresentmentDetails` on `Charge`, `CheckoutSession`, `PaymentIntent`, and `Refund`
  * Add support for `Billie` and `Satispay` on `ChargePaymentMethodDetails`, `ConfirmationTokenPaymentMethodDataOptions`, `ConfirmationTokenPaymentMethodPreview`, `CustomerPaymentMethod`, `PaymentIntentPaymentMethodDataOptions`, `PaymentMethodConfigurationCreateOptions`, `PaymentMethodConfigurationUpdateOptions`, `PaymentMethodConfiguration`, `PaymentMethodCreateOptions`, `PaymentMethod`, and `SetupIntentPaymentMethodDataOptions`
  * Add support for `NzBankAccount` on `ChargePaymentMethodDetails`, `ConfirmationTokenPaymentMethodDataOptions`, `ConfirmationTokenPaymentMethodPreview`, `CustomerPaymentMethod`, `MandatePaymentMethodDetails`, `PaymentIntentPaymentMethodDataOptions`, `PaymentIntentPaymentMethodOptionsOptions`, `PaymentIntentPaymentMethodOptions`, `PaymentMethodConfigurationCreateOptions`, `PaymentMethodConfigurationUpdateOptions`, `PaymentMethodConfiguration`, `PaymentMethodCreateOptions`, `PaymentMethod`, `SetupAttemptPaymentMethodDetails`, and `SetupIntentPaymentMethodDataOptions`
  * Add support for `OptionalItems` on `Checkout.SessionCreateOptions`, `CheckoutSession`, `PaymentLinkCreateOptions`, and `PaymentLink`
  * Add support for `Permissions` on

_…truncated…_


## v47.x

### v47.5.0-beta.1  (v47.5.0-beta.1)
<https://github.com/stripe/stripe-dotnet/releases/tag/v47.5.0-beta.1>

* [#3062](https://github.com/stripe/stripe-dotnet/pull/3062) Beta SDK updates between Open API versions 1473 and 1505
  
  * Add support for `SucceedInputCollection` and `TimeoutInputCollection` test helper methods on resource `Terminal.Reader`
  * Add support for `TargetDate` on `OrderPaymentSettingsPaymentMethodOptionsAcssDebitOptions`, `OrderPaymentSettingsPaymentMethodOptionsAcssDebit`, `OrderPaymentSettingsPaymentMethodOptionsSepaDebitOptions`, and `OrderPaymentSettingsPaymentMethodOptionsSepaDebit`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v47.5.0-beta.1/CHANGELOG.md).

### v47.4.0  (v47.4.0)
<https://github.com/stripe/stripe-dotnet/releases/tag/v47.4.0>

* [#3050](https://github.com/stripe/stripe-dotnet/pull/3050) Update generated code
  * Add support for `Prices` on `BillingCreditBalanceSummaryFilterApplicabilityScopeOptions`, `BillingCreditGrantApplicabilityConfigScopeOptions`, and `BillingCreditGrantApplicabilityConfigScope`
  * Add support for `Priority` on `Billing.CreditGrantCreateOptions` and `BillingCreditGrant`
  * Add support for `TargetDate` on `CheckoutSessionPaymentMethodOptionsAcssDebitOptions`, `CheckoutSessionPaymentMethodOptionsAcssDebit`, `CheckoutSessionPaymentMethodOptionsAuBecsDebitOptions`, `CheckoutSessionPaymentMethodOptionsAuBecsDebit`, `CheckoutSessionPaymentMethodOptionsBacsDebitOptions`, `CheckoutSessionPaymentMethodOptionsBacsDebit`, `CheckoutSessionPaymentMethodOptionsSepaDebitOptions`, `CheckoutSessionPaymentMethodOptionsSepaDebit`, `CheckoutSessionPaymentMethodOptionsUsBankAccountOptions`, `CheckoutSessionPaymentMethodOptionsUsBankAccount`, `PaymentIntentPaymentMethodOptionsAcssDebitOptions`, `PaymentIntentPaymentMethodOptionsAcssDebit`, `PaymentIntentPaymentMethodOptionsAuBecsDebitOptions`, `PaymentIntentPaymentMethodOptionsAuBecsDebit`, `PaymentIntentPaymentMethodOptionsBacsDebitOptions`, `PaymentIntentPaymentMethodOptionsBacsDebit`, `PaymentIntentPaymentMethodOptionsSepaDebitOptions`, `PaymentIntentPaymentMethodOptionsSepaDebit`, `PaymentIntentPaymentMethodOptionsUsBankAccountOptions`, and `PaymentIntentPaymentMethodOptionsUsBankAccount`
  * Add support for `Restrictions` on `CheckoutSessionPaymentMethodOptionsCardOptions` and `CheckoutSessionPaymentMethodOptionsCard`
  * Add support for `CollectedInformation` on `Checkout.SessionUpdateOptions` and `CheckoutSession`
  * Add support for `Metadata` on `ProductDefaultPriceDataOptions`
* [#3054](https://github.com/stripe/stripe-dotnet/pull/3054) Improved examples
* [#3055](https://github.com/stripe/stripe-dotnet/pull/3055) add codeowners file

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v47.4.0/CHANGELOG.md).

### v47.4.0-beta.1  (v47.4.0-beta.1)
<https://github.com/stripe/stripe-dotnet/releases/tag/v47.4.0-beta.1>

* [#3049](https://github.com/stripe/stripe-dotnet/pull/3049) Update generated code for beta
  * Add support for `RejectedReason` on `AccountRiskControls`
  * Add support for `ProductTaxCodeSelector` on `AccountSessionComponentsOptions`
  * Add support for `Prices` on `BillingCreditBalanceSummaryFilterApplicabilityScopeOptions`, `BillingCreditGrantApplicabilityConfigScopeOptions`, and `BillingCreditGrantApplicabilityConfigScope`
  * Add support for `BrandProduct` on `ChargePaymentMethodDetailsAmazonPayFundingCard` and `ChargePaymentMethodDetailsRevolutPayFundingCard`
  * Add support for `Restrictions` on `CheckoutSessionPaymentMethodOptionsCardOptions` and `CheckoutSessionPaymentMethodOptionsCard`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v47.4.0-beta.1/CHANGELOG.md).

### v47.3.0  (v47.3.0)
<https://github.com/stripe/stripe-dotnet/releases/tag/v47.3.0>

* [#3044](https://github.com/stripe/stripe-dotnet/pull/3044) Update generated code
  * Add support for `Close` method on resource `Treasury.FinancialAccount`
  * Add support for `PayByBankPayments` on `AccountCapabilitiesOptions` and `AccountCapabilities`
  * Add support for `DirectorshipDeclaration` and `OwnershipExemptionReason` on `AccountCompanyOptions`, `AccountCompany`, and `TokenAccountCompanyOptions`
  * Add support for `ProofOfUltimateBeneficialOwnership` on `AccountDocumentsOptions`
  * Add support for `FinancialAccount` on `AccountSessionComponentsOptions`, `AccountSessionComponents`, and `TreasuryOutboundTransferDestinationPaymentMethodDetails`
  * Add support for `FinancialAccountTransactions`, `IssuingCard`, and `IssuingCardsList` on `AccountSessionComponentsOptions` and `AccountSessionComponents`
  * Add support for `AdviceCode` on `ChargeOutcome`, `InvoiceLastFinalizationError`, `PaymentIntentLastPaymentError`, `SetupAttemptSetupError`, `SetupIntentLastSetupError`, and `StripeError`
  * Add support for `PayByBank` on `ChargePaymentMethodDetails`, `CheckoutSessionPaymentMethodOptionsOptions`, `ConfirmationTokenPaymentMethodDataOptions`, `ConfirmationTokenPaymentMethodPreview`, `PaymentIntentPaymentMethodDataOptions`, `PaymentIntentPaymentMethodOptionsOptions`, `PaymentIntentPaymentMethodOptions`, `PaymentMethodConfigurationCreateOptions`, `PaymentMethodConfigurationUpdateOptions`, `PaymentMethodConfiguration`, `PaymentMethodCreateOptions`, `PaymentMethodUpdateOptions`, `PaymentMethod`, and `SetupIntentPaymentMethodDataOptions`
  * Add support for `Country` on `ChargePaymentMethodDetailsPaypal`, `ConfirmationTokenPaymentMethodPreviewPaypal`, and `PaymentMethodPaypal`
  * Add support for `Discounts` on `CheckoutSession`
  * Add support for `PhoneNumberCollection` on `PaymentLinkUpdateOptions`
  * Add support for `Jpy` on `TerminalConfigurationTippingOptions` and `TerminalConfigurationTipping`
  * Add support for `Nickname` on `Treasury.FinancialAccountCreateOptions`, `Treasury.FinancialAccountUpdateOptions`, and `TreasuryFinancialAccount`
  * Add support for `ForwardingSettings` on `Treasury.FinancialAccountUpdateOptions`
  * Add support for `IsDefault` on `TreasuryFinancialAccount`
  * Add support for `DestinationPaymentMethodData` on `Treasury.OutboundTransferCreateOptions`
  * Change type of `TreasuryOutboundTransferDestinationPaymentMethodDetailsType` from `literal('us_bank_account')` to `enum('financial_account'|'us_bank_account')`
  * Add support for `OutboundTransfer` on `TreasuryReceivedCreditLinkedFlowsSourceFlowDetails`
* [#3046](https://github.com/stripe/stripe-dotnet/pull/3046) update justfile import
* [#3045](https://github.com/stripe/stripe-dotnet/pull/3045) Added CONTRIBUTING.md file
* [#3047](https://github.com/stripe/stripe-dotnet/pull/3047) Pin ubuntu version in ci
* [#3040](https://github.com/stripe/stripe-dotnet/pull/3040) Add justfile, remove coveralls
* [#3042](https://github.com/stripe/stripe-dotnet/pull/3042) Remove debug build and test from CI
* [#3039](https://github.com/stripe/stripe-dotnet/pull/3039) Fixed supported frameworks in project description and readme
* [#3038](https://github.com/stripe/stripe-dotnet/pull/3038) Added pull request template

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v47.3.0/CHANGELOG.md).

### v47.3.0-beta.3  (v47.3.0-beta.3)
<https://github.com/stripe/stripe-dotnet/releases/tag/v47.3.0-beta.3>

* [#3048](https://github.com/stripe/stripe-dotnet/pull/3048) Update generated code for beta
  * Remove support for `StripeAccount` on `TerminalReaderActionCollectPaymentMethod`, `TerminalReaderActionConfirmPaymentIntent`, `TerminalReaderActionProcessPaymentIntent`, and `TerminalReaderActionRefundPayment`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v47.3.0-beta.3/CHANGELOG.md).

### v47.3.0-beta.2  (v47.3.0-beta.2)
<https://github.com/stripe/stripe-dotnet/releases/tag/v47.3.0-beta.2>

* [#3043](https://github.com/stripe/stripe-dotnet/pull/3043) Update generated code for beta
  * Add support for `PayByBankPayments` on `AccountCapabilitiesOptions` and `AccountCapabilities`
  * Add support for `DirectorshipDeclaration` on `AccountCompanyOptions` and `TokenAccountCompanyOptions`
  * Add support for `ProofOfUltimateBeneficialOwnership` on `AccountDocumentsOptions`
  * Add support for `TaxThresholdMonitoring` on `AccountSessionComponentsOptions`
  * Add support for `FinancialAccountTransactions`, `FinancialAccount`, `IssuingCard`, and `IssuingCardsList` on `AccountSessionComponents`
  * Add support for `PayByBank` on `ChargePaymentMethodDetails`, `CheckoutSessionPaymentMethodOptionsOptions`, `ConfirmationTokenPaymentMethodDataOptions`, `ConfirmationTokenPaymentMethodPreview`, `PaymentIntentPaymentMethodDataOptions`, `PaymentIntentPaymentMethodOptionsOptions`, `PaymentIntentPaymentMethodOptions`, `PaymentMethodConfigurationCreateOptions`, `PaymentMethodConfigurationUpdateOptions`, `PaymentMethodConfiguration`, `PaymentMethodCreateOptions`, `PaymentMethodUpdateOptions`, `PaymentMethod`, and `SetupIntentPaymentMethodDataOptions`
  * Add support for `Discounts` on `CheckoutSession`
  * Add support for `Jpy` on `TerminalConfigurationTippingOptions` and `TerminalConfigurationTipping`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v47.3.0-beta.2/CHANGELOG.md).

### v47.3.0-beta.1  (v47.3.0-beta.1)
<https://github.com/stripe/stripe-dotnet/releases/tag/v47.3.0-beta.1>

* [#3037](https://github.com/stripe/stripe-dotnet/pull/3037) Update generated code for beta
  * Add support for `Close` method on resource `Treasury.FinancialAccount`
  * Add support for `OwnershipExemptionReason` on `AccountCompanyOptions`, `AccountCompany`, and `TokenAccountCompanyOptions`
  * Add support for `DirectorshipDeclaration` on `AccountCompany`
  * Add support for `AdviceCode` on `ChargeOutcome`, `InvoiceLastFinalizationError`, `PaymentIntentLastPaymentError`, `SetupAttemptSetupError`, `SetupIntentLastSetupError`, and `StripeError`
  * Add support for `BrandProduct` on `Card`, `SourceCardPresent`, `SourceCard`, and `SourceThreeDSecure`
  * Add support for `Country` on `ChargePaymentMethodDetailsPaypal`, `ConfirmationTokenPaymentMethodPreviewPaypal`, and `PaymentMethodPaypal`
  * Add support for `PhoneNumberCollection` on `PaymentLinkUpdateOptions`
  * Add support for `Nickname` on `Treasury.FinancialAccountCreateOptions`, `Treasury.FinancialAccountUpdateOptions`, and `TreasuryFinancialAccount`
  * Add support for `ForwardingSettings` on `Treasury.FinancialAccountUpdateOptions`
  * Add support for `IsDefault` on `TreasuryFinancialAccount`
  * Add support for `DestinationPaymentMethodData` on `Treasury.OutboundTransferCreateOptions`
  * Add support for `FinancialAccount` on `TreasuryOutboundTransferDestinationPaymentMethodDetails`
  * Change type of `TreasuryOutboundTransferDestinationPaymentMethodDetailsType` from `literal('us_bank_account')` to `enum('financial_account'|'us_bank_account')`
  * Add support for `OutboundTransfer` on `TreasuryReceivedCreditLinkedFlowsSourceFlowDetails`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v47.3.0-beta.1/CHANGELOG.md).

### v47.2.0  (v47.2.0)
<https://github.com/stripe/stripe-dotnet/releases/tag/v47.2.0>

* [#3036](https://github.com/stripe/stripe-dotnet/pull/3036) This release changes the pinned API version to `2024-12-18.acacia`.
  * Add support for `NetworkAdviceCode` and `NetworkDeclineCode` on `ChargeOutcome`, `InvoiceLastFinalizationError`, `PaymentIntentLastPaymentError`, `SetupAttemptSetupError`, `SetupIntentLastSetupError`, and `StripeError`
  * Add support for `CreditsApplicationInvoiceVoided` on `BillingCreditBalanceTransactionCredit`
  * Change type of `BillingCreditBalanceTransactionCreditType` from `literal('credits_granted')` to `enum('credits_application_invoice_voided'|'credits_granted')`
  * Add support for `AllowRedisplay` on `Card` and `Source`
  * Add support for `RegulatedStatus` on `Card`, `ChargePaymentMethodDetailsCard`, `ConfirmationTokenPaymentMethodPreviewCard`, and `PaymentMethodCard`
  * Add support for `Funding` on `ChargePaymentMethodDetailsAmazonPay` and `ChargePaymentMethodDetailsRevolutPay`
  * Add support for `NetworkTransactionId` on `ChargePaymentMethodDetailsCard`
  * Add support for `ReferencePrefix` on `CheckoutSessionPaymentMethodOptionsBacsDebitMandateOptionsOptions`, `CheckoutSessionPaymentMethodOptionsBacsDebitMandateOptions`, `CheckoutSessionPaymentMethodOptionsSepaDebitMandateOptionsOptions`, `CheckoutSessionPaymentMethodOptionsSepaDebitMandateOptions`, `PaymentIntentPaymentMethodOptionsBacsDebitMandateOptionsOptions`, `PaymentIntentPaymentMethodOptionsBacsDebitMandateOptions`, `PaymentIntentPaymentMethodOptionsSepaDebitMandateOptionsOptions`, `PaymentIntentPaymentMethodOptionsSepaDebitMandateOptions`, `SetupIntentPaymentMethodOptionsBacsDebitMandateOptionsOptions`, `SetupIntentPaymentMethodOptionsBacsDebitMandateOptions`, `SetupIntentPaymentMethodOptionsSepaDebitMandateOptionsOptions`, and `SetupIntentPaymentMethodOptionsSepaDebitMandateOptions`
  * Add support for `VisaCompliance` on `DisputeEvidenceDetailsEnhancedEligibility`, `DisputeEvidenceEnhancedEvidenceOptions`, and `DisputeEvidenceEnhancedEvidence`
  * Add support for `AccountHolderAddress` and `BankAddress` on `FundingInstructionsBankTransferFinancialAddressesIban`, `FundingInstructionsBankTransferFinancialAddressesSortCode`, `FundingInstructionsBankTransferFinancialAddressesSpei`, `FundingInstructionsBankTransferFinancialAddressesZengin`, `PaymentIntentNextActionDisplayBankTransferInstructionsFinancialAddressesIban`, `PaymentIntentNextActionDisplayBankTransferInstructionsFinancialAddressesSortCode`, `PaymentIntentNextActionDisplayBankTransferInstructionsFinancialAddressesSpei`, and `PaymentIntentNextActionDisplayBankTransferInstructionsFinancialAddressesZengin`
  * Add support for `AccountHolderName` on `FundingInstructionsBankTransferFinancialAddressesSpei` and `PaymentIntentNextActionDisplayBankTransferInstructionsFinancialAddressesSpei`
  * Add support for `DisabledReason` on `InvoiceAutomaticTax`, `SubscriptionAutomaticTax`, `SubscriptionScheduleDefaultSettingsAutomaticTax`, and `SubscriptionSchedulePhasesAutomaticTax`
  * Add support for `TaxId` on `IssuingAuthorizationMerchantData` and `IssuingTransactionMerchantData`
  * Add support for `TrialPeriodDays` on `PaymentLinkSubscriptionDataOptions`
  * Add support for `Al`, `Am`, `Ao`, `Ba`, `Bb`, `Bs`, `Cd`, `Gn`, `Kh`, `Me`, `Mk`, `Mr`, `Np`, `Pe`, `Sn`, `Sr`, `Tj`, `Ug`, `Uy`, `Zm`, and `Zw` on `TaxRegistrationCountryOptionsOptions` and `TaxRegistrationCountryOptions`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v47.2.0/CHANGELOG.md).

### v47.2.0-beta.3  (v47.2.0-beta.3)
<https://github.com/stripe/stripe-dotnet/releases/tag/v47.2.0-beta.3>

* [#3035](https://github.com/stripe/stripe-dotnet/pull/3035) Update generated code for beta
  * Add support for `AllowRedisplay` on `Card` and `Source`
  * Remove support for `AmountRefunded` on `PaymentRecord`
  * Add support for `Account` on `TerminalReaderActionCollectPaymentMethod`, `TerminalReaderActionConfirmPaymentIntent`, `TerminalReaderActionProcessPaymentIntent`, and `TerminalReaderActionRefundPayment`
* [#3033](https://github.com/stripe/stripe-dotnet/pull/3033) System.Text.Json Serialization Support in .NET SDK Objects
  - Add System.Text.Json support for serializing Stripe.net entities and objects for applications running on .NET 6 and above. Now you can pass a Stripe.net object or collection of objects to the System.Text.Json serializer and it will produce the correct JSON string.

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v47.2.0-beta.3/CHANGELOG.md).

### v47.2.0-beta.2  (v47.2.0-beta.2)
<https://github.com/stripe/stripe-dotnet/releases/tag/v47.2.0-beta.2>

* [#3032](https://github.com/stripe/stripe-dotnet/pull/3032) Update generated code for beta
  * Add support for `AutomaticIndirectTax` on `AccountCapabilitiesOptions` and `AccountCapabilities`
  * Add support for `ReferencePrefix` on `CheckoutSessionPaymentMethodOptionsBacsDebitMandateOptionsOptions`, `CheckoutSessionPaymentMethodOptionsBacsDebitMandateOptions`, `CheckoutSessionPaymentMethodOptionsSepaDebitMandateOptionsOptions`, `CheckoutSessionPaymentMethodOptionsSepaDebitMandateOptions`, `OrderPaymentSettingsPaymentMethodOptionsSepaDebitMandateOptionsOptions`, `OrderPaymentSettingsPaymentMethodOptionsSepaDebitMandateOptions`, `PaymentIntentPaymentMethodOptionsBacsDebitMandateOptionsOptions`, `PaymentIntentPaymentMethodOptionsBacsDebitMandateOptions`, `PaymentIntentPaymentMethodOptionsSepaDebitMandateOptionsOptions`, `PaymentIntentPaymentMethodOptionsSepaDebitMandateOptions`, `SetupIntentPaymentMethodOptionsBacsDebitMandateOptionsOptions`, `SetupIntentPaymentMethodOptionsBacsDebitMandateOptions`, `SetupIntentPaymentMethodOptionsSepaDebitMandateOptionsOptions`, and `SetupIntentPaymentMethodOptionsSepaDebitMandateOptions`
  * Add support for `DisabledReason` on `InvoiceAutomaticTax`, `SubscriptionAutomaticTax`, `SubscriptionScheduleDefaultSettingsAutomaticTax`, and `SubscriptionSchedulePhasesAutomaticTax`
  * Add support for `TrialPeriodDays` on `PaymentLinkSubscriptionDataOptions`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v47.2.0-beta.2/CHANGELOG.md).

### v47.2.0-beta.1  (v47.2.0-beta.1)
<https://github.com/stripe/stripe-dotnet/releases/tag/v47.2.0-beta.1>

* [#3031](https://github.com/stripe/stripe-dotnet/pull/3031) Update generated code for beta
  * Add support for `NetworkAdviceCode` and `NetworkDeclineCode` on `ChargeOutcome`, `InvoiceLastFinalizationError`, `PaymentIntentLastPaymentError`, `SetupAttemptSetupError`, `SetupIntentLastSetupError`, and `StripeError`
  * Add support for `Funding` on `ChargePaymentMethodDetailsAmazonPay` and `ChargePaymentMethodDetailsRevolutPay`
  * Add support for `AmountRequested` and `PartialAuthorization` on `ChargePaymentMethodDetailsCard`
  * Add support for `Metadata` on `CheckoutSessionLineItemsOptions` and `LineItem`
  * Add support for `LineItems` on `Checkout.SessionUpdateOptions`, `CheckoutSessionPermissionsUpdateOptions`, and `CheckoutSessionPermissionsUpdate`
  * Add support for `AdjustableQuantity` and `Display` on `LineItem`
  * Add support for `RequestPartialAuthorization` on `PaymentIntentPaymentMethodOptionsCardOptions` and `PaymentIntentPaymentMethodOptionsCard`
  * Add support for `PaymentMethodOptions` on `PaymentIntentIncrementAuthorizationOptions`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v47.2.0-beta.1/CHANGELOG.md).

### v47.1.0  (v47.1.0)
<https://github.com/stripe/stripe-dotnet/releases/tag/v47.1.0>

* [#3025](https://github.com/stripe/stripe-dotnet/pull/3025) This release changes the pinned API version to `2024-11-20.acacia`.
  * Add support for `Respond` test helper method on resource `Issuing.Authorization`
  * Add support for `Authorizer` on `AccountRelationshipOptions` and `TokenPersonRelationshipOptions`
  * Add support for `AdaptivePricing` on `Checkout.SessionCreateOptions` and `CheckoutSession`
  * Add support for `MandateOptions` on `CheckoutSessionPaymentMethodOptionsBacsDebitOptions`, `CheckoutSessionPaymentMethodOptionsBacsDebit`, `CheckoutSessionPaymentMethodOptionsSepaDebitOptions`, and `CheckoutSessionPaymentMethodOptionsSepaDebit`
  * Add support for `RequestExtendedAuthorization`, `RequestIncrementalAuthorization`, `RequestMulticapture`, and `RequestOvercapture` on `CheckoutSessionPaymentMethodOptionsCardOptions` and `CheckoutSessionPaymentMethodOptionsCard`
  * Add support for `CaptureMethod` on `CheckoutSessionPaymentMethodOptionsKakaoPayOptions`, `CheckoutSessionPaymentMethodOptionsKrCardOptions`, `CheckoutSessionPaymentMethodOptionsNaverPayOptions`, `CheckoutSessionPaymentMethodOptionsPaycoOptions`, and `CheckoutSessionPaymentMethodOptionsSamsungPayOptions`
  * Add support for `AccountHolderAddress`, `AccountHolderName`, `AccountType`, and `BankAddress` on `FundingInstructionsBankTransferFinancialAddressesAba`, `FundingInstructionsBankTransferFinancialAddressesSwift`, `PaymentIntentNextActionDisplayBankTransferInstructionsFinancialAddressesAba`, and `PaymentIntentNextActionDisplayBankTransferInstructionsFinancialAddressesSwift`
  * Add support for `MerchantAmount` and `MerchantCurrency` on `Issuing.TestHelpersAuthorizationCreateOptions`
  * Add support for `FraudChallenges` and `VerifiedByFraudChallenge` on `IssuingAuthorization`
  * Add support for `SubmitType` on `PaymentLinkUpdateOptions`
  * Add support for `TraceId` on `Payout`
  * Add support for `NetworkDeclineCode` on `RefundDestinationDetailsBlik` and `RefundDestinationDetailsSwish`
* [#3021](https://github.com/stripe/stripe-dotnet/pull/3021) Fix URL encoding of id strings passed to service methods
* [#3026](https://github.com/stripe/stripe-dotnet/pull/3026) Fix V2 list options base class
  * Remove `StartingAfter` and `EndingBefore` properties from `Stripe.V2.EventListOptions` and `Stripe.V2.EventDestinationListOptions`.  These properties are not supported on V2 List APIs and would result in a HTTP 400 error if provided.

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v47.1.0/CHANGELOG.md).

### v47.1.0-beta.3  (v47.1.0-beta.3)
<https://github.com/stripe/stripe-dotnet/releases/tag/v47.1.0-beta.3>

* [#3027](https://github.com/stripe/stripe-dotnet/pull/3027) Update generated code for beta
  * Add support for `AccountHolderAddress` and `BankAddress` on `FundingInstructionsBankTransferFinancialAddressesIban`, `FundingInstructionsBankTransferFinancialAddressesSortCode`, `FundingInstructionsBankTransferFinancialAddressesSpei`, `FundingInstructionsBankTransferFinancialAddressesZengin`, `PaymentIntentNextActionDisplayBankTransferInstructionsFinancialAddressesIban`, `PaymentIntentNextActionDisplayBankTransferInstructionsFinancialAddressesSortCode`, `PaymentIntentNextActionDisplayBankTransferInstructionsFinancialAddressesSpei`, and `PaymentIntentNextActionDisplayBankTransferInstructionsFinancialAddressesZengin`
  * Add support for `AccountHolderName` on `FundingInstructionsBankTransferFinancialAddressesSpei` and `PaymentIntentNextActionDisplayBankTransferInstructionsFinancialAddressesSpei`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v47.1.0-beta.3/CHANGELOG.md).

### v47.1.0-beta.2  (v47.1.0-beta.2)
<https://github.com/stripe/stripe-dotnet/releases/tag/v47.1.0-beta.2>

* [#3022](https://github.com/stripe/stripe-dotnet/pull/3022) Update generated code for beta
  * Add support for new resources `Issuing.FraudLiabilityDebit`, `PaymentAttemptRecord`, and `PaymentRecord`
  * Add support for `Get` and `List` methods on resources `FraudLiabilityDebit` and `PaymentAttemptRecord`
  * Add support for `Get`, `ReportPaymentAttemptCanceled`, `ReportPaymentAttemptFailed`, `ReportPaymentAttemptGuaranteed`, `ReportPaymentAttempt`, and `ReportPayment` methods on resource `PaymentRecord`
  * Remove support for `MoneyMovement` on `AccountSessionComponentsFinancialAccountFeaturesOptions`
  * Add support for `CardManagement`, `CardSpendDisputeManagement`, `CardholderManagement`, and `SpendControlManagement` on `AccountSessionComponentsIssuingCardFeaturesOptions`
  * Add support for `DisableStripeUserAuthentication` on `AccountSessionComponentsIssuingCardsListFeaturesOptions`
  * Add support for `AdaptivePricing` on `Checkout.SessionCreateOptions` and `CheckoutSession`
  * Add support for `MandateOptions` on `CheckoutSessionPaymentMethodOptionsBacsDebitOptions`, `CheckoutSessionPaymentMethodOptionsBacsDebit`, `CheckoutSessionPaymentMethodOptionsSepaDebitOptions`, and `CheckoutSessionPaymentMethodOptionsSepaDebit`
  * Add support for `RequestDecrementalAuthorization`, `RequestExtendedAuthorization`, `RequestIncrementalAuthorization`, `RequestMulticapture`, and `RequestOvercapture` on `CheckoutSessionPaymentMethodOptionsCardOptions` and `CheckoutSessionPaymentMethodOptionsCard`
  * Add support for `CaptureMethod` on `CheckoutSessionPaymentMethodOptionsKakaoPayOptions`, `CheckoutSessionPaymentMethodOptionsKrCardOptions`, `CheckoutSessionPaymentMethodOptionsNaverPayOptions`, `CheckoutSessionPaymentMethodOptionsPaycoOptions`, and `CheckoutSessionPaymentMethodOptionsSamsungPayOptions`
  * Add support for `AccountHolderAddress`, `AccountHolderName`, `AccountType`, and `BankAddress` on `FundingInstructionsBankTransferFinancialAddressesAba`, `FundingInstructionsBankTransferFinancialAddressesSwift`, `PaymentIntentNextActionDisplayBankTransferInstructionsFinancialAddressesAba`, and `PaymentIntentNextActionDisplayBankTransferInstructionsFinancialAddressesSwift`
  * Add support for `PaymentRecordData` and `PaymentRecord` on `InvoiceAttachPaymentOptions`
  * Remove support for `OutOfBandPayment` on `InvoiceAttachPaymentOptions`
  * Add support for `AmountOverpaid` on `Invoice`
  * Add support for `MerchantAmount` and `MerchantCurrency` on `Issuing.TestHelpersAuthorizationCreateOptions`
  * Add support for `SubmitType` on `PaymentLinkUpdateOptions`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v47.1.0-beta.2/CHANGELOG.md).

### v47.1.0-beta.1  (v47.1.0-beta.1)
<https://github.com/stripe/stripe-dotnet/releases/tag/v47.1.0-beta.1>

* [#3018](https://github.com/stripe/stripe-dotnet/pull/3018) Update generated code for beta
  * Add support for `TriggerAction` method on resource `PaymentIntent`
  * Add support for `IdBankTransferPaymentsBca` and `IdBankTransferPayments` on `AccountCapabilitiesOptions` and `AccountCapabilities`
  * Add support for `BankBcaOnboarding` on `AccountSettingsOptions` and `AccountSettings`
  * Add support for `SendMoney` on `AccountSessionComponentsRecipientsFeaturesOptions`
  * Add support for `IdBankTransfer` on `ChargePaymentMethodDetails`, `ConfirmationTokenPaymentMethodDataOptions`, `ConfirmationTokenPaymentMethodPreview`, `InvoicePaymentSettingsPaymentMethodOptionsOptions`, `InvoicePaymentSettingsPaymentMethodOptions`, `PaymentIntentPaymentMethodDataOptions`, `PaymentIntentPaymentMethodOptionsOptions`, `PaymentIntentPaymentMethodOptions`, `PaymentMethodConfigurationCreateOptions`, `PaymentMethodConfigurationUpdateOptions`, `PaymentMethodConfiguration`, `PaymentMethodCreateOptions`, `PaymentMethod`, `RefundDestinationDetails`, `SetupAttemptPaymentMethodDetails`, `SetupIntentPaymentMethodDataOptions`, `SubscriptionPaymentSettingsPaymentMethodOptionsOptions`, and `SubscriptionPaymentSettingsPaymentMethodOptions`
  * Add support for `Gopay`, `Qris`, and `Shopeepay` on `PaymentMethodConfigurationCreateOptions`, `PaymentMethodConfigurationUpdateOptions`, and `PaymentMethodConfiguration`
* [#3011](https://github.com/stripe/stripe-dotnet/pull/3011) Do not allow setting API Version directly on StripeConfiguration
  * `StripeConfiguration.ApiVersion` is no longer settable. If you were using this to set the beta headers, use the helper method `StripeConfiguration.AddBetaVersion()` instead.

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v47.1.0-beta.1/CHANGELOG.md).

### v47.0.0  (v47.0.0)
<https://github.com/stripe/stripe-dotnet/releases/tag/v47.0.0>

Historically, when upgrading webhooks to a new API version, you also had to upgrade your SDK version. Your webhook's API version needed to match the API version pinned by the SDK you were using to ensure successful deserialization of events. With the `2024-09-30.acacia` release, Stripe follows a [new API release process](https://stripe.com/blog/introducing-stripes-new-api-release-process). As a result, you can safely upgrade your webhook endpoints to any API version within a biannual release (like `acacia`) without upgrading the SDK.

However, [a bug](https://github.com/stripe/stripe-dotnet/pull/3010) in the `46.x.y` SDK releases meant that webhook version upgrades from the SDK's pinned `2024-09-30.acacia` version to the new `2024-10-28.acacia` version would fail. Therefore, we are shipping SDK support for `2024-10-28.acacia` as a major version to enforce the idea that an SDK upgrade is also required. Future API versions in the `acacia` line will be released as minor versions.

* [#2997](https://github.com/stripe/stripe-dotnet/pull/2997) This release changes the pinned API version to `2024-10-28.acacia`."
  * Add support for new resource `V2.EventDestinations`
  * Add support for `Create`, `Get`, `Update`, `List`, `Delete`, `Disable`, `Enable` and `Ping` methods on resource `V2.EventDestinations`
  * Add support for `SubmitCard` test helper method on resource `Issuing.Card`
  * Add support for `Groups` on `AccountCreateOptions`, `AccountUpdateOptions`, and `Account`
  * Add support for `AlmaPayments`, `KakaoPayPayments`, `KrCardPayments`, `NaverPayPayments`, `PaycoPayments`, and `SamsungPayPayments` on `AccountCapabilitiesOptions` and `AccountCapabilities`
  * Add support for `DisableStripeUserAuthentication` on `AccountSessionComponentsAccountManagementFeaturesOptions`, `AccountSessionComponentsAccountManagementFeatures`, `AccountSessionComponentsAccountOnboardingFeaturesOptions`, `AccountSessionComponentsAccountOnboardingFeatures`, `AccountSessionComponentsBalancesFeaturesOptions`, `AccountSessionComponentsBalancesFeatures`, `AccountSessionComponentsNotificationBannerFeaturesOptions`, `AccountSessionComponentsNotificationBannerFeatures`, `AccountSessionComponentsPayoutsFeaturesOptions`, and `AccountSessionComponentsPayoutsFeatures`
  * Add support for `ScheduleAtPeriodEnd` on `BillingPortalConfigurationFeaturesSubscriptionUpdateOptions` and `BillingPortalConfigurationFeaturesSubscriptionUpdate`
  * Add support for `Alma` on `ChargePaymentMethodDetails`, `ConfirmationTokenPaymentMethodDataOptions`, `ConfirmationTokenPaymentMethodPreview`, `PaymentIntentPaymentMethodDataOptions`, `PaymentIntentPaymentMethodOptionsOptions`, `PaymentIntentPaymentMethodOptions`, `PaymentMethodConfigurationCreateOptions`, `PaymentMethodConfigurationUpdateOptions`, `PaymentMethodConfiguration`, `PaymentMethodCreateOptions`, `PaymentMethod`, `RefundDestinationDetails`, and `SetupIntentPaymentMethodDataOptions`
  * Add support for `KakaoPay` and `KrCard` on `ChargePaymentMethodDetails`, `CheckoutSessionPaymentMethodOptionsOptions`, `CheckoutSessionPaymentMethodOptions`, `ConfirmationTokenPaymentMethodDataOptions`, `ConfirmationTokenPaymentMethodPreview`, `MandatePaymentMethodDetails`, `PaymentIntentPaymentMethodDataOptions`, `PaymentIntentPaymentMethodOptionsOptions`, `PaymentIntentPaymentMethodOptions`, `PaymentMethodCreateOptions`, `PaymentMethod`, `SetupAttemptPaymentMethodDetails`, and `SetupIntentPaymentMethodDataOptions`
  * Add support for `NaverPay` on `ChargePaymentMethodDetails`, `CheckoutSessionPaymentMethodOptionsOptions`, `CheckoutSessionPaymentMethodOptions`, `ConfirmationTokenPaymentMethodDataOptions`, `ConfirmationTokenPaymentMethodPreview`, `PaymentIntentPaymentMethodDataOptions`, `PaymentIntentPaymentMethodOptionsOptions`, `PaymentIntentPaymentMethodOptions`, `PaymentMethodCreateOptions`, `PaymentMethodUpdateOptions`, `PaymentMethod`, and `SetupIntentPaymentMethodDataOptions`
  * Add support for `Payco` and `SamsungPay` on `ChargePaymentMethodDetails`, `CheckoutSessionPaymentMethodOptionsOptions`, `CheckoutSessionPaymentMethodOptions`, `ConfirmationTokenPaymentMethodDataOptions`, `ConfirmationTokenPaymentMethodPreview`, `PaymentIntentPaymentMethodDataOptions`, `PaymentIntentPaymentMethodOptionsOptions`, `PaymentIntentPaymentMethodOptions`, `PaymentMethodCreateOptions`, `PaymentMethod`, and `SetupIntentPaymentMethodDataOptions`
  * Add support for `EnhancedEvidence` on `DisputeEvidenceOptions` and `DisputeEvidence`
  * Add support for `EnhancedEligibilityTypes` on `Dispute`
  * Add support for `EnhancedEligibility` on `DisputeEvidenceDetails`
  * Add support for `Metadata` on `Forwarding.RequestCreateOptions` and `ForwardingRequest`
  * Add support for `AutomaticallyFinalizesAt` on `InvoiceCreateOptions` and `InvoiceUpdateOptions`
  * Add support for `AmazonPay` on `PaymentMethodDomain`
  * Add support for `FlatAmount` and `RateType` on `TaxCalculationTaxBreakdownTaxRateDetails` and `TaxRate`
  * Add support for `By`, `Cr`, `Ec`, `Ma`, `Md`, `Rs`, `Ru`, `Tz`, and `Uz` on `TaxRegistrationCountryOptionsOptions` and `TaxRegistrationCountryOptions`
  * Add support for `Pln` on `TerminalConfigurationTippingOptions` and `TerminalConfigurationTipping`

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v47.0.0/CHANGELOG.md).


## v46.x

### v46.3.0-beta.1  (v46.3.0-beta.1)
<https://github.com/stripe/stripe-dotnet/releases/tag/v46.3.0-beta.1>

* [#3000](https://github.com/stripe/stripe-dotnet/pull/3000) Update generated code for beta
  * Add support for `AlmaPayments`, `GopayPayments`, `KakaoPayPayments`, `KrCardPayments`, `NaverPayPayments`, `PaycoPayments`, `QrisPayments`, `SamsungPayPayments`, `ShopeepayPayments`, `TreasuryEvolve`, `TreasuryFifthThird`, and `TreasuryGoldmanSachs` on `AccountCapabilitiesOptions` and `AccountCapabilities`
  * Add support for `ScheduleAtPeriodEnd` on `BillingPortalConfigurationFeaturesSubscriptionUpdateOptions` and `BillingPortalConfigurationFeaturesSubscriptionUpdate`
  * Add support for `Alma` on `ChargePaymentMethodDetails`, `ConfirmationTokenPaymentMethodDataOptions`, `ConfirmationTokenPaymentMethodPreview`, `PaymentIntentPaymentMethodDataOptions`, `PaymentIntentPaymentMethodOptionsOptions`, `PaymentIntentPaymentMethodOptions`, `PaymentMethodConfigurationCreateOptions`, `PaymentMethodConfigurationUpdateOptions`, `PaymentMethodConfiguration`, `PaymentMethodCreateOptions`, `PaymentMethod`, `RefundDestinationDetails`, and `SetupIntentPaymentMethodDataOptions`
  * Add support for `Gopay`, `Qris`, and `Shopeepay` on `ChargePaymentMethodDetails`, `ConfirmationTokenPaymentMethodDataOptions`, `ConfirmationTokenPaymentMethodPreview`, `PaymentIntentPaymentMethodDataOptions`, `PaymentIntentPaymentMethodOptionsOptions`, `PaymentIntentPaymentMethodOptions`, `PaymentMethodCreateOptions`, `PaymentMethod`, and `SetupIntentPaymentMethodDataOptions`
  * Add support for `Metadata` on `Forwarding.RequestCreateOptions`
  * Add support for `AmazonPay` on `PaymentMethodDomain`
  * Add support for `ExternalReference` on `TaxFormPayeeOptions` and `TaxFormPayee`
  * Change type of `TaxFormPayeeTypeOptions` and `TaxFormPayeeType` from `literal('account')` to `enum('account'|'external_reference')`
  * Add support for `AuSerr`, `CaMrdp`, `EuDac7`, `GbMrdp`, and `NzMrdp` on `TaxForm`
  * Add support for `Pln` on `TerminalConfigurationTippingOptions` and `TerminalConfigurationTipping`
  * Add support for `Bank` on `TreasuryFinancialAccountFeaturesFinancialAddressesAbaOptions`, `TreasuryFinancialAccountFeaturesFinancialAddressesAba`, and `TreasuryFinancialAccountFinancialAddressesAbaOptions`
* [#3004](https://github.com/stripe/stripe-dotnet/pull/3004) Ramya/merge dotnet beta

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v46.3.0-beta.1/CHANGELOG.md).

### v46.2.2  (v46.2.2)
<https://github.com/stripe/stripe-dotnet/releases/tag/v46.2.2>

* [#3010](https://github.com/stripe/stripe-dotnet/pull/3010) Update webhook API version validation
  - Update webhook event processing to accept events from any API version within the supported major release

See [the changelog for more details](https://github.com/stripe/stripe-dotnet/blob/v46.2.2/CHANGELOG.md).
