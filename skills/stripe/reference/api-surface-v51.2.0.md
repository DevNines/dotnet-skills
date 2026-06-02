# Stripe.net v51.2.0 — API surface (tiered)

- `Stripe.net` v51.2.0 (`net8.0`)

_Do not edit by hand — rerun `tools/update_skill.py`._

`Stripe.net` is too large to detail in full (~4591 public types). This surface has **three tiers**:

0. A **type index** — every public type by NAME. A type whose name is not in this index does not exist in this version; never `new` up a type name you can't find here.
1. A **service index** — every API service and its operations by name. If a service or operation isn't here, it does not exist in this version.
2. **Core resource detail** — full property/option listings for the most-used resources. For a resource that is only indexed (not detailed), the option class follows the `{Resource}{Operation}Options` naming convention (e.g. `RefundCreateOptions`); confirm the type name in the type index and confirm individual properties against Stripe's API reference for this version before relying on them.

## Type index (all types, names only)

_All 4591 public type names in this version. A type name that is NOT in this list does not exist in this version — do not use it. Member detail for non-core types is not included here; the names are listed so you can verify a type exists before referencing it._

- **Stripe**: `Account`, `AccountBankAccountOptions`, `AccountBusinessProfile`, `AccountBusinessProfileAnnualRevenue`, `AccountBusinessProfileAnnualRevenueOptions`, `AccountBusinessProfileMonthlyEstimatedRevenue`, `AccountBusinessProfileMonthlyEstimatedRevenueOptions`, `AccountBusinessProfileOptions`, `AccountCapabilities`, `AccountCapabilitiesAcssDebitPaymentsOptions`, `AccountCapabilitiesAffirmPaymentsOptions`, `AccountCapabilitiesAfterpayClearpayPaymentsOptions`, `AccountCapabilitiesAlmaPaymentsOptions`, `AccountCapabilitiesAmazonPayPaymentsOptions`, `AccountCapabilitiesAppDistributionOptions`, `AccountCapabilitiesAuBecsDebitPaymentsOptions`, `AccountCapabilitiesBacsDebitPaymentsOptions`, `AccountCapabilitiesBancontactPaymentsOptions`, `AccountCapabilitiesBankTransferPaymentsOptions`, `AccountCapabilitiesBilliePaymentsOptions`, `AccountCapabilitiesBizumPaymentsOptions`, `AccountCapabilitiesBlikPaymentsOptions`, `AccountCapabilitiesBoletoPaymentsOptions`, `AccountCapabilitiesCardIssuingOptions`, `AccountCapabilitiesCardPaymentsOptions`, `AccountCapabilitiesCartesBancairesPaymentsOptions`, `AccountCapabilitiesCashappPaymentsOptions`, `AccountCapabilitiesCryptoPaymentsOptions`, `AccountCapabilitiesEpsPaymentsOptions`, `AccountCapabilitiesFpxPaymentsOptions`, `AccountCapabilitiesGbBankTransferPaymentsOptions`, `AccountCapabilitiesGiropayPaymentsOptions`, `AccountCapabilitiesGrabpayPaymentsOptions`, `AccountCapabilitiesIdealPaymentsOptions`, `AccountCapabilitiesIndiaInternationalPaymentsOptions`, `AccountCapabilitiesJcbPaymentsOptions`, `AccountCapabilitiesJpBankTransferPaymentsOptions`, `AccountCapabilitiesKakaoPayPaymentsOptions`, `AccountCapabilitiesKlarnaPaymentsOptions`, `AccountCapabilitiesKonbiniPaymentsOptions`, `AccountCapabilitiesKrCardPaymentsOptions`, `AccountCapabilitiesLegacyPaymentsOptions`, `AccountCapabilitiesLinkPaymentsOptions`, `AccountCapabilitiesMbWayPaymentsOptions`, `AccountCapabilitiesMobilepayPaymentsOptions`, `AccountCapabilitiesMultibancoPaymentsOptions`, `AccountCapabilitiesMxBankTransferPaymentsOptions`, `AccountCapabilitiesNaverPayPaymentsOptions`, `AccountCapabilitiesNzBankAccountBecsDebitPaymentsOptions`, `AccountCapabilitiesOptions`, `AccountCapabilitiesOxxoPaymentsOptions`, `AccountCapabilitiesP24PaymentsOptions`, `AccountCapabilitiesPayByBankPaymentsOptions`, `AccountCapabilitiesPaycoPaymentsOptions`, `AccountCapabilitiesPaynowPaymentsOptions`, `AccountCapabilitiesPaytoPaymentsOptions`, `AccountCapabilitiesPixPaymentsOptions`, `AccountCapabilitiesPromptpayPaymentsOptions`, `AccountCapabilitiesRevolutPayPaymentsOptions`, `AccountCapabilitiesSamsungPayPaymentsOptions`, `AccountCapabilitiesSatispayPaymentsOptions`, `AccountCapabilitiesScalapayPaymentsOptions`, `AccountCapabilitiesSepaBankTransferPaymentsOptions`, `AccountCapabilitiesSepaDebitPaymentsOptions`, `AccountCapabilitiesSofortPaymentsOptions`, `AccountCapabilitiesSunbitPaymentsOptions`, `AccountCapabilitiesSwishPaymentsOptions`, `AccountCapabilitiesTaxReportingUs1099KOptions`, `AccountCapabilitiesTaxReportingUs1099MiscOptions`, `AccountCapabilitiesTransfersOptions`, `AccountCapabilitiesTreasuryOptions`, `AccountCapabilitiesTwintPaymentsOptions`, `AccountCapabilitiesUpiPaymentsOptions`, `AccountCapabilitiesUsBankAccountAchPaymentsOptions`, `AccountCapabilitiesUsBankTransferPaymentsOptions`, `AccountCapabilitiesZipPaymentsOptions`, `AccountCapabilityService`, `AccountCapabilityUpdateOptions`, `AccountCardOptions`, `AccountCompany`, `AccountCompanyDirectorshipDeclaration`, `AccountCompanyDirectorshipDeclarationOptions`, `AccountCompanyOptions`, `AccountCompanyOwnershipDeclaration`, `AccountCompanyOwnershipDeclarationOptions`, `AccountCompanyRegistrationDate`, `AccountCompanyRegistrationDateOptions`, `AccountCompanyRepresentativeDeclaration`, `AccountCompanyRepresentativeDeclarationOptions`, `AccountCompanyVerificationDocument`, `AccountCompanyVerificationDocumentOptions`, `AccountCompanyVerificationOptions`, `AccountController`, `AccountControllerFees`, `AccountControllerFeesOptions`, `AccountControllerLosses`, `AccountControllerLossesOptions`, `AccountControllerOptions`, `AccountControllerStripeDashboard`, `AccountControllerStripeDashboardOptions`, `AccountCreateOptions`, `AccountDocumentsBankAccountOwnershipVerificationOptions`, `AccountDocumentsCompanyLicenseOptions`, `AccountDocumentsCompanyMemorandumOfAssociationOptions`, `AccountDocumentsCompanyMinisterialDecreeOptions`, `AccountDocumentsCompanyRegistrationVerificationOptions`, `AccountDocumentsCompanyTaxIdVerificationOptions`, `AccountDocumentsOptions`, `AccountDocumentsProofOfAddressOptions`, `AccountDocumentsProofOfRegistrationOptions`, `AccountDocumentsProofOfRegistrationSignerOptions`, `AccountDocumentsProofOfUltimateBeneficialOwnershipOptions`, `AccountDocumentsProofOfUltimateBeneficialOwnershipSignerOptions`, `AccountExternalAccountBankAccountOptions`, `AccountExternalAccountCardOptions`, `AccountExternalAccountCreateOptions`, `AccountExternalAccountDocumentsBankAccountOwnershipVerificationOptions`, `AccountExternalAccountDocumentsOptions`, `AccountExternalAccountListOptions`, `AccountExternalAccountService`, `AccountExternalAccountUpdateOptions`, `AccountFutureRequirements`, `AccountFutureRequirementsAlternative`, `AccountFutureRequirementsError`, `AccountGroups`, `AccountGroupsOptions`, `AccountIndividualOptions`, `AccountIndividualRelationshipOptions`, `AccountIndividualVerificationAdditionalDocumentOptions`, `AccountIndividualVerificationDocumentOptions`, `AccountIndividualVerificationOptions`, `AccountLink`, `AccountLinkCollectionOptionsOptions`, `AccountLinkCreateOptions`, `AccountLinkService`, `AccountListOptions`, `AccountLoginLinkService`, `AccountPersonAdditionalTosAcceptancesAccountOptions`, `AccountPersonAdditionalTosAcceptancesOptions`, `AccountPersonCreateOptions`, `AccountPersonDobOptions`, `AccountPersonDocumentsCompanyAuthorizationOptions`, `AccountPersonDocumentsOptions`, `AccountPersonDocumentsPassportOptions`, `AccountPersonDocumentsVisaOptions`, `AccountPersonListOptions`, `AccountPersonRelationshipOptions`, `AccountPersonService`, `AccountPersonUpdateOptions`, `AccountPersonUsCfpbDataEthnicityDetailsOptions`, `AccountPersonUsCfpbDataOptions`, `AccountPersonUsCfpbDataRaceDetailsOptions`, `AccountPersonVerificationAdditionalDocumentOptions`, `AccountPersonVerificationDocumentOptions`, `AccountPersonVerificationOptions`, `AccountRejectOptions`, `AccountRequirements`, `AccountRequirementsAlternative`, `AccountRequirementsError`, `AccountService`, `AccountSession`, `AccountSessionComponentsAccountManagement`, `AccountSessionComponentsAccountManagementFeatures`, `AccountSessionComponentsAccountManagementFeaturesOptions`, `AccountSessionComponentsAccountManagementOptions`, `AccountSessionComponentsAccountOnboarding`, `AccountSessionComponentsAccountOnboardingFeatures`, `AccountSessionComponentsAccountOnboardingFeaturesOptions`, `AccountSessionComponentsAccountOnboardingOptions`, `AccountSessionComponentsBalanceReport`, `AccountSessionComponentsBalanceReportOptions`, `AccountSessionComponentsBalances`, `AccountSessionComponentsBalancesFeatures`, `AccountSessionComponentsBalancesFeaturesOptions`, `AccountSessionComponentsBalancesOptions`, `AccountSessionComponentsDisputesList`, `AccountSessionComponentsDisputesListFeatures`, `AccountSessionComponentsDisputesListFeaturesOptions`, `AccountSessionComponentsDisputesListOptions`, `AccountSessionComponentsDocuments`, `AccountSessionComponentsDocumentsOptions`, `AccountSessionComponentsFinancialAccount`, `AccountSessionComponentsFinancialAccountFeatures`, `AccountSessionComponentsFinancialAccountFeaturesOptions`, `AccountSessionComponentsFinancialAccountOptions`, `AccountSessionComponentsFinancialAccountTransactions`, `AccountSessionComponentsFinancialAccountTransactionsFeatures`, `AccountSessionComponentsFinancialAccountTransactionsFeaturesOptions`, `AccountSessionComponentsFinancialAccountTransactionsOptions`, `AccountSessionComponentsInstantPayoutsPromotion`, `AccountSessionComponentsInstantPayoutsPromotionFeatures`, `AccountSessionComponentsInstantPayoutsPromotionFeaturesOptions`, `AccountSessionComponentsInstantPayoutsPromotionOptions`, `AccountSessionComponentsIssuingCard`, `AccountSessionComponentsIssuingCardFeatures`, `AccountSessionComponentsIssuingCardFeaturesOptions`, `AccountSessionComponentsIssuingCardOptions`, `AccountSessionComponentsIssuingCardsList`, `AccountSessionComponentsIssuingCardsListFeatures`, `AccountSessionComponentsIssuingCardsListFeaturesOptions`, `AccountSessionComponentsIssuingCardsListOptions`, `AccountSessionComponentsNotificationBanner`, `AccountSessionComponentsNotificationBannerFeatures`, `AccountSessionComponentsNotificationBannerFeaturesOptions`, `AccountSessionComponentsNotificationBannerOptions`, `AccountSessionComponentsOptions`, `AccountSessionComponentsPaymentDetails`, `AccountSessionComponentsPaymentDetailsFeatures`, `AccountSessionComponentsPaymentDetailsFeaturesOptions`, `AccountSessionComponentsPaymentDetailsOptions`, `AccountSessionComponentsPaymentDisputes`, `AccountSessionComponentsPaymentDisputesFeatures`, `AccountSessionComponentsPaymentDisputesFeaturesOptions`, `AccountSessionComponentsPaymentDisputesOptions`, `AccountSessionComponentsPayments`, `AccountSessionComponentsPaymentsFeatures`, `AccountSessionComponentsPaymentsFeaturesOptions`, `AccountSessionComponentsPaymentsOptions`, `AccountSessionComponentsPayoutDetails`, `AccountSessionComponentsPayoutDetailsOptions`, `AccountSessionComponentsPayoutReconciliationReport`, `AccountSessionComponentsPayoutReconciliationReportOptions`, `AccountSessionComponentsPayouts`, `AccountSessionComponentsPayoutsFeatures`, `AccountSessionComponentsPayoutsFeaturesOptions`, `AccountSessionComponentsPayoutsList`, `AccountSessionComponentsPayoutsListOptions`, `AccountSessionComponentsPayoutsOptions`, `AccountSessionComponentsTaxRegistrations`, `AccountSessionComponentsTaxRegistrationsOptions`, `AccountSessionComponentsTaxSettings`, `AccountSessionComponentsTaxSettingsOptions`, `AccountSessionCreateOptions`, `AccountSessionService`, `AccountSettingsBacsDebitPayments`, `AccountSettingsBacsDebitPaymentsOptions`, `AccountSettingsBranding`, `AccountSettingsBrandingOptions`, `AccountSettingsCardIssuingOptions`, `AccountSettingsCardIssuingTosAcceptance`, `AccountSettingsCardIssuingTosAcceptanceOptions`, `AccountSettingsCardPayments`, `AccountSettingsCardPaymentsDeclineOnOptions`, `AccountSettingsCardPaymentsOptions`, `AccountSettingsDashboard`, `AccountSettingsInvoices`, `AccountSettingsInvoicesOptions`, `AccountSettingsOptions`, `AccountSettingsPayments`, `AccountSettingsPaymentsOptions`, `AccountSettingsPayouts`, `AccountSettingsPayoutsOptions`, `AccountSettingsPayoutsSchedule`, `AccountSettingsPayoutsScheduleOptions`, `AccountSettingsSepaDebitPayments`, `AccountSettingsTreasuryOptions`, `AccountSettingsTreasuryTosAcceptance`, `AccountSettingsTreasuryTosAcceptanceOptions`, `AccountTosAcceptance`, `AccountTosAcceptanceOptions`, `AccountUpdateOptions`, `AnyOf`, `AnyOf<T1, T2, T3, T4>`, `AnyOf<T1, T2, T3>`, `AnyOf<T1, T2>`, `ApiMode`, `ApiRequestor`, `ApiRequestorAdapter`, `AppInfo`, `ApplePayDomain`, `ApplePayDomainService`, `Application`, `ApplicationFee`, `ApplicationFeeFeeSource`, `ApplicationFeeListOptions`, `ApplicationFeeRefund`, `ApplicationFeeRefundCreateOptions`, `ApplicationFeeRefundService`, `ApplicationFeeRefundUpdateOptions`, `ApplicationFeeService`, `Balance`, `BalanceInstantAvailable`, `BalanceInstantAvailableNetAvailable`, `BalanceInstantAvailableNetAvailableSourceTypes`, `BalanceInstantAvailableSourceTypes`, `BalanceIssuing`, `BalanceRefundAndDisputePrefunding`, `BalanceRefundAndDisputePrefundingAvailable`, `BalanceRefundAndDisputePrefundingAvailableSourceTypes`, `BalanceRefundAndDisputePrefundingPending`, `BalanceRefundAndDisputePrefundingPendingSourceTypes`, `BalanceService`, `BalanceSettings`, `BalanceSettingsPayments`, `BalanceSettingsPaymentsOptions`, `BalanceSettingsPaymentsPayouts`, `BalanceSettingsPaymentsPayoutsAutomaticTransferRulesByCurrency`, `BalanceSettingsPaymentsPayoutsAutomaticTransferRulesByCurrencyOptions`, `BalanceSettingsPaymentsPayoutsOptions`, `BalanceSettingsPaymentsPayoutsSchedule`, `BalanceSettingsPaymentsPayoutsScheduleOptions`, `BalanceSettingsPaymentsSettlementTiming`, `BalanceSettingsPaymentsSettlementTimingOptions`, `BalanceSettingsPaymentsSettlementTimingStartOfDay`, `BalanceSettingsPaymentsSettlementTimingStartOfDayOptions`, `BalanceSettingsService`, `BalanceSettingsUpdateOptions`, `BalanceTransaction`, `BalanceTransactionFeeDetail`, `BalanceTransactionListOptions`, `BalanceTransactionService`, `BankAccount`, `BankAccountDocumentsBankAccountOwnershipVerificationOptions`, `BankAccountDocumentsOptions`, `BankAccountFutureRequirements`, `BankAccountFutureRequirementsError`, `BankAccountRequirements`, `BankAccountRequirementsError`, `BankAccountUpdateOptions`, `BankAccountVerifyOptions`, `BaseAddress`, `BaseOptions`, `Capability`, `CapabilityFutureRequirements`, `CapabilityFutureRequirementsAlternative`, `CapabilityFutureRequirementsError`, `CapabilityRequirements`, `CapabilityRequirementsAlternative`, `Card`, `CardCreateNestedOptions`, `CardDocumentsBankAccountOwnershipVerificationOptions`, `CardDocumentsOptions`, `CardNetworks`, `CardUpdateOptions`, `CashBalance`, `CashBalanceSettings`, `Charge`, `ChargeBillingDetails`, `ChargeCaptureOptions`, `ChargeCreateOptions`, `ChargeDestinationOptions`, `ChargeFraudDetails`, `ChargeFraudDetailsOptions`, `ChargeListOptions`, `ChargeOutcome`, `ChargePaymentMethodDetails`, `ChargePaymentMethodDetailsAchCreditTransfer`, `ChargePaymentMethodDetailsAchDebit`, `ChargePaymentMethodDetailsAcssDebit`, `ChargePaymentMethodDetailsAffirm`, `ChargePaymentMethodDetailsAfterpayClearpay`, `ChargePaymentMethodDetailsAlipay`, `ChargePaymentMethodDetailsAlma`, `ChargePaymentMethodDetailsAlmaInstallments`, `ChargePaymentMethodDetailsAmazonPay`, `ChargePaymentMethodDetailsAmazonPayFunding`, `ChargePaymentMethodDetailsAmazonPayFundingCard`, `ChargePaymentMethodDetailsAuBecsDebit`, `ChargePaymentMethodDetailsBacsDebit`, `ChargePaymentMethodDetailsBancontact`, `ChargePaymentMethodDetailsBillie`, `ChargePaymentMethodDetailsBizum`, `ChargePaymentMethodDetailsBlik`, `ChargePaymentMethodDetailsBoleto`, `ChargePaymentMethodDetailsCard`, `ChargePaymentMethodDetailsCardChecks`, `ChargePaymentMethodDetailsCardExtendedAuthorization`, `ChargePaymentMethodDetailsCardIncrementalAuthorization`, `ChargePaymentMethodDetailsCardInstallments`, `ChargePaymentMethodDetailsCardMulticapture`, `ChargePaymentMethodDetailsCardNetworkToken`, `ChargePaymentMethodDetailsCardOvercapture`, `ChargePaymentMethodDetailsCardPresent`, `ChargePaymentMethodDetailsCardPresentOffline`, `ChargePaymentMethodDetailsCardPresentReceipt`, `ChargePaymentMethodDetailsCardPresentWallet`, `ChargePaymentMethodDetailsCardThreeDSecure`, `ChargePaymentMethodDetailsCardWallet`, `ChargePaymentMethodDetailsCardWalletMasterpass`, `ChargePaymentMethodDetailsCardWalletVisaCheckout`, `ChargePaymentMethodDetailsCashapp`, `ChargePaymentMethodDetailsCrypto`, `ChargePaymentMethodDetailsEps`, `ChargePaymentMethodDetailsFpx`, `ChargePaymentMethodDetailsGiropay`, `ChargePaymentMethodDetailsGrabpay`, `ChargePaymentMethodDetailsIdeal`, `ChargePaymentMethodDetailsInteracPresent`, `ChargePaymentMethodDetailsInteracPresentReceipt`, `ChargePaymentMethodDetailsKakaoPay`, `ChargePaymentMethodDetailsKlarna`, `ChargePaymentMethodDetailsKlarnaPayerDetails`, `ChargePaymentMethodDetailsKlarnaPayerDetailsAddress`, `ChargePaymentMethodDetailsKonbini`, `ChargePaymentMethodDetailsKonbiniStore`, `ChargePaymentMethodDetailsKrCard`, `ChargePaymentMethodDetailsLink`, `ChargePaymentMethodDetailsMobilepay`, `ChargePaymentMethodDetailsMobilepayCard`, `ChargePaymentMethodDetailsMultibanco`, `ChargePaymentMethodDetailsNaverPay`, `ChargePaymentMethodDetailsNzBankAccount`, `ChargePaymentMethodDetailsOxxo`, `ChargePaymentMethodDetailsP24`, `ChargePaymentMethodDetailsPayco`, `ChargePaymentMethodDetailsPaynow`, `ChargePaymentMethodDetailsPaypal`, `ChargePaymentMethodDetailsPaypalSellerProtection`, `ChargePaymentMethodDetailsPayto`, `ChargePaymentMethodDetailsPix`, `ChargePaymentMethodDetailsPromptpay`, `ChargePaymentMethodDetailsRevolutPay`, `ChargePaymentMethodDetailsRevolutPayFunding`, `ChargePaymentMethodDetailsRevolutPayFundingCard`, `ChargePaymentMethodDetailsSamsungPay`, `ChargePaymentMethodDetailsSatispay`, `ChargePaymentMethodDetailsScalapay`, `ChargePaymentMethodDetailsSepaDebit`, `ChargePaymentMethodDetailsSofort`, `ChargePaymentMethodDetailsSunbit`, `ChargePaymentMethodDetailsSwish`, `ChargePaymentMethodDetailsTwint`, `ChargePaymentMethodDetailsUpi`, `ChargePaymentMethodDetailsUsBankAccount`, `ChargePaymentMethodDetailsWechatPay`, `ChargePresentmentDetails`, `ChargeRadarOptions`, `ChargeRadarOptionsOptions`, `ChargeService`, `ChargeShippingOptions`, `ChargeTransferData`, `ChargeTransferDataOptions`, `ChargeUpdateOptions`, `ConfirmationToken`, `ConfirmationTokenMandateData`, `ConfirmationTokenMandateDataCustomerAcceptance`, `ConfirmationTokenMandateDataCustomerAcceptanceOnline`, `ConfirmationTokenPaymentMethodOptions`, `ConfirmationTokenPaymentMethodOptionsCard`, `ConfirmationTokenPaymentMethodOptionsCardInstallmentsPlan`, `ConfirmationTokenPaymentMethodPreview`, `ConfirmationTokenPaymentMethodPreviewAcssDebit`, `ConfirmationTokenPaymentMethodPreviewAuBecsDebit`, `ConfirmationTokenPaymentMethodPreviewBacsDebit`, `ConfirmationTokenPaymentMethodPreviewBillingDetails`, `ConfirmationTokenPaymentMethodPreviewBoleto`, `ConfirmationTokenPaymentMethodPreviewCard`, `ConfirmationTokenPaymentMethodPreviewCardChecks`, `ConfirmationTokenPaymentMethodPreviewCardGeneratedFrom`, `ConfirmationTokenPaymentMethodPreviewCardGeneratedFromPaymentMethodDetails`, `ConfirmationTokenPaymentMethodPreviewCardGeneratedFromPaymentMethodDetailsCardPresent`, `ConfirmationTokenPaymentMethodPreviewCardGeneratedFromPaymentMethodDetailsCardPresentOffline`, `ConfirmationTokenPaymentMethodPreviewCardGeneratedFromPaymentMethodDetailsCardPresentReceipt`, `ConfirmationTokenPaymentMethodPreviewCardGeneratedFromPaymentMethodDetailsCardPresentWallet`, `ConfirmationTokenPaymentMethodPreviewCardNetworks`, `ConfirmationTokenPaymentMethodPreviewCardPresent`, `ConfirmationTokenPaymentMethodPreviewCardPresentNetworks`, `ConfirmationTokenPaymentMethodPreviewCardPresentOffline`, `ConfirmationTokenPaymentMethodPreviewCardPresentWallet`, `ConfirmationTokenPaymentMethodPreviewCardThreeDSecureUsage`, `ConfirmationTokenPaymentMethodPreviewCardWallet`, `ConfirmationTokenPaymentMethodPreviewCardWalletMasterpass`, `ConfirmationTokenPaymentMethodPreviewCardWalletVisaCheckout`, `ConfirmationTokenPaymentMethodPreviewCashapp`, `ConfirmationTokenPaymentMethodPreviewEps`, `ConfirmationTokenPaymentMethodPreviewFpx`, `ConfirmationTokenPaymentMethodPreviewIdeal`, `ConfirmationTokenPaymentMethodPreviewInteracPresent`, `ConfirmationTokenPaymentMethodPreviewInteracPresentNetworks`, `ConfirmationTokenPaymentMethodPreviewKlarna`, `ConfirmationTokenPaymentMethodPreviewKlarnaDob`, `ConfirmationTokenPaymentMethodPreviewKrCard`, `ConfirmationTokenPaymentMethodPreviewLink`, `ConfirmationTokenPaymentMethodPreviewNaverPay`, `ConfirmationTokenPaymentMethodPreviewNzBankAccount`, `ConfirmationTokenPaymentMethodPreviewP24`, `ConfirmationTokenPaymentMethodPreviewPaypal`, `ConfirmationTokenPaymentMethodPreviewPayto`, `ConfirmationTokenPaymentMethodPreviewSepaDebit`, `ConfirmationTokenPaymentMethodPreviewSepaDebitGeneratedFrom`, `ConfirmationTokenPaymentMethodPreviewSofort`, `ConfirmationTokenPaymentMethodPreviewUpi`, `ConfirmationTokenPaymentMethodPreviewUsBankAccount`, `ConfirmationTokenPaymentMethodPreviewUsBankAccountNetworks`, `ConfirmationTokenPaymentMethodPreviewUsBankAccountStatusDetailsBlocked`, `ConfirmationTokenService`, `ConfirmationTokenShipping`, `ConnectCollectionTransfer`, `CountrySpec`, `CountrySpecService`, `Coupon`, `CouponAppliesTo`, `CouponAppliesToOptions`, `CouponCreateOptions`, `CouponCurrencyOptions`, `CouponCurrencyOptionsOptions`, `CouponListOptions`, `CouponService`, `CouponUpdateOptions`, `CreditNote`, `CreditNoteCreateOptions`, `CreditNoteDiscountAmount`, `CreditNoteLineItem`, `CreditNoteLineItemDiscountAmount`, `CreditNoteLineItemPretaxCreditAmount`, `CreditNoteLineItemTax`, `CreditNoteLineItemTaxTaxRateDetails`, `CreditNoteLineOptions`, `CreditNoteLineTaxAmountOptions`, `CreditNoteListOptions`, `CreditNotePretaxCreditAmount`, `CreditNotePreviewLinesLineOptions`, `CreditNotePreviewLinesLineTaxAmountOptions`, `CreditNotePreviewLinesListOptions`, `CreditNotePreviewLinesRefundOptions`, `CreditNotePreviewLinesRefundPaymentRecordRefundOptions`, `CreditNotePreviewLinesService`, `CreditNotePreviewLinesShippingCostOptions`, `CreditNotePreviewOptions`, `CreditNoteRefund`, `CreditNoteRefundOptions`, `CreditNoteRefundPaymentRecordRefund`, `CreditNoteRefundPaymentRecordRefundOptions`, `CreditNoteShippingCost`, `CreditNoteShippingCostOptions`, `CreditNoteShippingCostTax`, `CreditNoteTotalTax`, `CreditNoteTotalTaxTaxRateDetails`, `CreditNoteUpdateOptions`, `Customer`, `CustomerBalanceTransaction`, `CustomerBalanceTransactionCreateOptions`, `CustomerBalanceTransactionListOptions`, `CustomerBalanceTransactionService`, `CustomerBalanceTransactionUpdateOptions`, `CustomerCashBalanceOptions`, `CustomerCashBalanceService`, `CustomerCashBalanceSettingsOptions`, `CustomerCashBalanceTransaction`, `CustomerCashBalanceTransactionAdjustedForOverdraft`, `CustomerCashBalanceTransactionAppliedToPayment`, `CustomerCashBalanceTransactionFundedBankTransfer`, `CustomerCashBalanceTransactionFundedBankTransferEuBankTransfer`, `CustomerCashBalanceTransactionFundedBankTransferGbBankTransfer`, `CustomerCashBalanceTransactionFundedBankTransferJpBankTransfer`, `CustomerCashBalanceTransactionFundedBankTransferUsBankTransfer`, `CustomerCashBalanceTransactionRefundedFromPayment`, `CustomerCashBalanceTransactionService`, `CustomerCashBalanceTransactionTransferredToBalance`, `CustomerCashBalanceTransactionUnappliedFromPayment`, `CustomerCashBalanceUpdateOptions`, `CustomerCreateOptions`, `CustomerFundingInstructionsBankTransferEuBankTransferOptions`, `CustomerFundingInstructionsBankTransferOptions`, `CustomerFundingInstructionsCreateOptions`, `CustomerFundingInstructionsService`, `CustomerInvoiceSettings`, `CustomerInvoiceSettingsCustomField`, `CustomerInvoiceSettingsCustomFieldOptions`, `CustomerInvoiceSettingsOptions`, `CustomerInvoiceSettingsRenderingOptions`, `CustomerInvoiceSettingsRenderingOptionsOptions`, `CustomerListOptions`, `CustomerPaymentMethodListOptions`, `CustomerPaymentMethodService`, `CustomerPaymentSourceCreateOptions`, `CustomerPaymentSourceListOptions`, `CustomerPaymentSourceOwnerOptions`, `CustomerPaymentSourceService`, `CustomerPaymentSourceUpdateOptions`, `CustomerPaymentSourceVerifyOptions`, `CustomerService`, `CustomerSession`, `CustomerSessionComponents`, `CustomerSessionComponentsBuyButton`, `CustomerSessionComponentsBuyButtonOptions`, `CustomerSessionComponentsCustomerSheet`, `CustomerSessionComponentsCustomerSheetFeatures`, `CustomerSessionComponentsCustomerSheetFeaturesOptions`, `CustomerSessionComponentsCustomerSheetOptions`, `CustomerSessionComponentsMobilePaymentElement`, `CustomerSessionComponentsMobilePaymentElementFeatures`, `CustomerSessionComponentsMobilePaymentElementFeaturesOptions`, `CustomerSessionComponentsMobilePaymentElementOptions`, `CustomerSessionComponentsOptions`, `CustomerSessionComponentsPaymentElement`, `CustomerSessionComponentsPaymentElementFeatures`, `CustomerSessionComponentsPaymentElementFeaturesOptions`, `CustomerSessionComponentsPaymentElementOptions`, `CustomerSessionComponentsPricingTable`, `CustomerSessionComponentsPricingTableOptions`, `CustomerSessionCreateOptions`, `CustomerSessionService`, `CustomerTax`, `CustomerTaxIdCreateOptions`, `CustomerTaxIdDataOptions`, `CustomerTaxIdService`, `CustomerTaxLocation`, `CustomerTaxOptions`, `CustomerUpdateOptions`, `DefaultStripeClient`, `Discount`, `DiscountSource`, `Dispute`, `DisputeEvidence`, `DisputeEvidenceDetails`, `DisputeEvidenceDetailsEnhancedEligibilityVisaCompellingEvidence3`, `DisputeEvidenceDetailsEnhancedEligibilityVisaCompliance`, `DisputeEvidenceEnhancedEvidenceOptions`, `DisputeEvidenceEnhancedEvidenceVisaCompellingEvidence3`, `DisputeEvidenceEnhancedEvidenceVisaCompellingEvidence3DisputedTransaction`, `DisputeEvidenceEnhancedEvidenceVisaCompellingEvidence3DisputedTransactionOptions`, `DisputeEvidenceEnhancedEvidenceVisaCompellingEvidence3DisputedTransactionShippingAddress`, `DisputeEvidenceEnhancedEvidenceVisaCompellingEvidence3Options`, `DisputeEvidenceEnhancedEvidenceVisaCompellingEvidence3PriorUndisputedTransaction`, `DisputeEvidenceEnhancedEvidenceVisaCompellingEvidence3PriorUndisputedTransactionOptions`, `DisputeEvidenceEnhancedEvidenceVisaCompellingEvidence3PriorUndisputedTransactionShippingAddress`, `DisputeEvidenceEnhancedEvidenceVisaCompliance`, `DisputeEvidenceEnhancedEvidenceVisaComplianceOptions`, `DisputeEvidenceOptions`, `DisputeListOptions`, `DisputePaymentMethodDetails`, `DisputePaymentMethodDetailsAmazonPay`, `DisputePaymentMethodDetailsCard`, `DisputePaymentMethodDetailsKlarna`, `DisputePaymentMethodDetailsPaypal`, `DisputeService`, `DisputeUpdateOptions`, `DobOptions`, `EmptyStripeEntity`, `EphemeralKey`, `EphemeralKeyCreateOptions`, `Event`, `EventData`, `EventListOptions`, `EventRequest`, `EventService`, `EventTypes`, `EventUtility`, `ExpandableField<T>`, `File`, `FileCreateOptions`, `FileFileLinkDataOptions`, `FileLink`, `FileLinkCreateOptions`, `FileLinkListOptions`, `FileLinkService`, `FileLinkUpdateOptions`, `FileListOptions`, `FileService`, `FundingInstructions`, `FundingInstructionsBankTransfer`, `FundingInstructionsBankTransferFinancialAddress`, `FundingInstructionsBankTransferFinancialAddressAba`, `FundingInstructionsBankTransferFinancialAddressIban`, `FundingInstructionsBankTransferFinancialAddressSortCode`, `FundingInstructionsBankTransferFinancialAddressSpei`, `FundingInstructionsBankTransferFinancialAddressSwift`, `FundingInstructionsBankTransferFinancialAddressZengin`, `IAnyOf`, `IBalanceTransactionSource`, `IExpandableField`, `IExpandableField<T>`, `IExternalAccount`, `IHasId`, `IHasMetadata`, `IHasObject`, `IHttpClient`, `IPaymentSource`, `IStripeClient`, `IStripeEntity`, `Invoice`, `InvoiceAddLinesOptions`, `InvoiceAttachPaymentOptions`, `InvoiceAutomaticTax`, `InvoiceAutomaticTaxLiability`, `InvoiceAutomaticTaxLiabilityOptions`, `InvoiceAutomaticTaxOptions`, `InvoiceConfirmationSecret`, `InvoiceCreateOptions`, `InvoiceCreatePreviewOptions`, `InvoiceCustomField`, `InvoiceCustomFieldOptions`, `InvoiceCustomerDetailsOptions`, `InvoiceCustomerDetailsTaxIdOptions`, `InvoiceCustomerDetailsTaxOptions`, `InvoiceCustomerTaxId`, `InvoiceDiscountOptions`, `InvoiceFinalizeOptions`, `InvoiceFromInvoice`, `InvoiceFromInvoiceOptions`, `InvoiceIssuer`, `InvoiceIssuerOptions`, `InvoiceItem`, `InvoiceItemCreateOptions`, `InvoiceItemDiscountOptions`, `InvoiceItemListOptions`, `InvoiceItemParent`, `InvoiceItemParentSubscriptionDetails`, `InvoiceItemPeriod`, `InvoiceItemPeriodOptions`, `InvoiceItemPriceDataOptions`, `InvoiceItemPricing`, `InvoiceItemPricingOptions`, `InvoiceItemPricingPriceDetails`, `InvoiceItemProrationDetails`, `InvoiceItemProrationDetailsCreditedItems`, `InvoiceItemProrationDetailsCreditedItemsInvoiceLineItemDetails`, `InvoiceItemProrationDetailsDiscountAmount`, `InvoiceItemService`, `InvoiceItemUpdateOptions`, `InvoiceLineDiscountOptions`, `InvoiceLineItem`, `InvoiceLineItemDiscountAmount`, `InvoiceLineItemDiscountOptions`, `InvoiceLineItemParent`, `InvoiceLineItemParentInvoiceItemDetails`, `InvoiceLineItemParentInvoiceItemDetailsProrationDetails`, `InvoiceLineItemParentInvoiceItemDetailsProrationDetailsCreditedItems`, `InvoiceLineItemParentSubscriptionItemDetails`, `InvoiceLineItemParentSubscriptionItemDetailsProrationDetails`, `InvoiceLineItemParentSubscriptionItemDetailsProrationDetailsCreditedItems`, `InvoiceLineItemPeriod`, `InvoiceLineItemPeriodOptions`, `InvoiceLineItemPretaxCreditAmount`, `InvoiceLineItemPriceDataOptions`, `InvoiceLineItemPriceDataProductDataOptions`, `InvoiceLineItemPricing`, `InvoiceLineItemPricingOptions`, `InvoiceLineItemPricingPriceDetails`, `InvoiceLineItemService`, `InvoiceLineItemTax`, `InvoiceLineItemTaxAmountOptions`, `InvoiceLineItemTaxAmountTaxRateDataOptions`, `InvoiceLineItemTaxTaxRateDetails`, `InvoiceLineItemUpdateOptions`, `InvoiceLineOptions`, `InvoiceLinePeriodOptions`, `InvoiceLinePriceDataOptions`, `InvoiceLinePriceDataProductDataOptions`, `InvoiceLinePricingOptions`, `InvoiceLineTaxAmountOptions`, `InvoiceLineTaxAmountTaxRateDataOptions`, `InvoiceListOptions`, `InvoiceParent`, `InvoiceParentQuoteDetails`, `InvoiceParentSubscriptionDetails`, `InvoicePayOptions`, `InvoicePayment`, `InvoicePaymentListOptions`, `InvoicePaymentPayment`, `InvoicePaymentPaymentOptions`, `InvoicePaymentService`, `InvoicePaymentSettings`, `InvoicePaymentSettingsOptions`, `InvoicePaymentSettingsPaymentMethodOptions`, `InvoicePaymentSettingsPaymentMethodOptionsAcssDebit`, `InvoicePaymentSettingsPaymentMethodOptionsAcssDebitMandateOptions`, `InvoicePaymentSettingsPaymentMethodOptionsAcssDebitMandateOptionsOptions`, `InvoicePaymentSettingsPaymentMethodOptionsAcssDebitOptions`, `InvoicePaymentSettingsPaymentMethodOptionsBancontact`, `InvoicePaymentSettingsPaymentMethodOptionsBancontactOptions`, `InvoicePaymentSettingsPaymentMethodOptionsCard`, `InvoicePaymentSettingsPaymentMethodOptionsCardInstallments`, `InvoicePaymentSettingsPaymentMethodOptionsCardInstallmentsOptions`, `InvoicePaymentSettingsPaymentMethodOptionsCardInstallmentsPlanOptions`, `InvoicePaymentSettingsPaymentMethodOptionsCardOptions`, `InvoicePaymentSettingsPaymentMethodOptionsCustomerBalance`, `InvoicePaymentSettingsPaymentMethodOptionsCustomerBalanceBankTransfer`, `InvoicePaymentSettingsPaymentMethodOptionsCustomerBalanceBankTransferEuBankTransfer`, `InvoicePaymentSettingsPaymentMethodOptionsCustomerBalanceBankTransferEuBankTransferOptions`, `InvoicePaymentSettingsPaymentMethodOptionsCustomerBalanceBankTransferOptions`, `InvoicePaymentSettingsPaymentMethodOptionsCustomerBalanceOptions`, `InvoicePaymentSettingsPaymentMethodOptionsOptions`, `InvoicePaymentSettingsPaymentMethodOptionsPaytoMandateOptions`, `InvoicePaymentSettingsPaymentMethodOptionsPaytoMandateOptionsOptions`, `InvoicePaymentSettingsPaymentMethodOptionsPaytoOptions`, `InvoicePaymentSettingsPaymentMethodOptionsPix`, `InvoicePaymentSettingsPaymentMethodOptionsPixOptions`, `InvoicePaymentSettingsPaymentMethodOptionsUpiMandateOptions`, `InvoicePaymentSettingsPaymentMethodOptionsUpiMandateOptionsOptions`, `InvoicePaymentSettingsPaymentMethodOptionsUpiOptions`, `InvoicePaymentSettingsPaymentMethodOptionsUsBankAccount`, `InvoicePaymentSettingsPaymentMethodOptionsUsBankAccountFinancialConnections`, `InvoicePaymentSettingsPaymentMethodOptionsUsBankAccountFinancialConnectionsFilters`, `InvoicePaymentSettingsPaymentMethodOptionsUsBankAccountFinancialConnectionsFiltersOptions`, `InvoicePaymentSettingsPaymentMethodOptionsUsBankAccountFinancialConnectionsOptions`, `InvoicePaymentSettingsPaymentMethodOptionsUsBankAccountOptions`, `InvoicePaymentStatusTransitions`, `InvoiceRemoveLinesOptions`, `InvoiceRendering`, `InvoiceRenderingOptions`, `InvoiceRenderingPdf`, `InvoiceRenderingPdfOptions`, `InvoiceRenderingTemplate`, `InvoiceRenderingTemplateListOptions`, `InvoiceRenderingTemplateService`, `InvoiceScheduleDetailsBillingModeFlexibleOptions`, `InvoiceScheduleDetailsBillingModeOptions`, `InvoiceScheduleDetailsOptions`, `InvoiceScheduleDetailsPhaseAddInvoiceItemDiscountOptions`, `InvoiceScheduleDetailsPhaseAddInvoiceItemOptions`, `InvoiceScheduleDetailsPhaseAddInvoiceItemPeriodEndOptions`, `InvoiceScheduleDetailsPhaseAddInvoiceItemPeriodOptions`, `InvoiceScheduleDetailsPhaseAddInvoiceItemPeriodStartOptions`, `InvoiceScheduleDetailsPhaseAddInvoiceItemPriceDataOptions`, `InvoiceScheduleDetailsPhaseAutomaticTaxLiabilityOptions`, `InvoiceScheduleDetailsPhaseAutomaticTaxOptions`, `InvoiceScheduleDetailsPhaseBillingThresholdsOptions`, `InvoiceScheduleDetailsPhaseDiscountOptions`, `InvoiceScheduleDetailsPhaseDurationOptions`, `InvoiceScheduleDetailsPhaseInvoiceSettingsIssuerOptions`, `InvoiceScheduleDetailsPhaseInvoiceSettingsOptions`, `InvoiceScheduleDetailsPhaseItemBillingThresholdsOptions`, `InvoiceScheduleDetailsPhaseItemDiscountOptions`, `InvoiceScheduleDetailsPhaseItemOptions`, `InvoiceScheduleDetailsPhaseItemPriceDataOptions`, `InvoiceScheduleDetailsPhaseItemPriceDataRecurringOptions`, `InvoiceScheduleDetailsPhaseOptions`, `InvoiceScheduleDetailsPhaseTransferDataOptions`, `InvoiceService`, `InvoiceShippingCost`, `InvoiceShippingCostOptions`, `InvoiceShippingCostShippingRateDataDeliveryEstimateMaximumOptions`, `InvoiceShippingCostShippingRateDataDeliveryEstimateMinimumOptions`, `InvoiceShippingCostShippingRateDataDeliveryEstimateOptions`, `InvoiceShippingCostShippingRateDataFixedAmountCurrencyOptionsOptions`, `InvoiceShippingCostShippingRateDataFixedAmountOptions`, `InvoiceShippingCostShippingRateDataOptions`, `InvoiceShippingCostTax`, `InvoiceShippingDetails`, `InvoiceShippingDetailsOptions`, `InvoiceStatusTransitions`, `InvoiceSubscriptionDetailsBillingModeFlexibleOptions`, `InvoiceSubscriptionDetailsBillingModeOptions`, `InvoiceSubscriptionDetailsBillingScheduleAppliesToOptions`, `InvoiceSubscriptionDetailsBillingScheduleBillUntilDurationOptions`, `InvoiceSubscriptionDetailsBillingScheduleBillUntilOptions`, `InvoiceSubscriptionDetailsBillingScheduleOptions`, `InvoiceSubscriptionDetailsItemBillingThresholdsOptions`, `InvoiceSubscriptionDetailsItemDiscountOptions`, `InvoiceSubscriptionDetailsItemOptions`, `InvoiceSubscriptionDetailsItemPriceDataOptions`, `InvoiceSubscriptionDetailsItemPriceDataRecurringOptions`, `InvoiceSubscriptionDetailsOptions`, `InvoiceTaxAmount`, `InvoiceThresholdReason`, `InvoiceThresholdReasonItemReason`, `InvoiceTotalPretaxCreditAmount`, `InvoiceTotalTax`, `InvoiceTotalTaxTaxRateDetails`, `InvoiceTransferDataOptions`, `InvoiceUpdateInvoiceLineItemsOptions`, `InvoiceUpdateLinesOptions`, `InvoiceUpdateOptions`, `LineItem`, `LineItemDiscount`, `LineItemTax`, `ListOptions`, `LiveApiRequestor`, `LoginLink`, `Mandate`, `MandateCustomerAcceptance`, `MandateCustomerAcceptanceOnline`, `MandateMultiUse`, `MandatePaymentMethodDetails`, `MandatePaymentMethodDetailsAcssDebit`, `MandatePaymentMethodDetailsAuBecsDebit`, `MandatePaymentMethodDetailsBacsDebit`, `MandatePaymentMethodDetailsPaypal`, `MandatePaymentMethodDetailsPayto`, `MandatePaymentMethodDetailsPix`, `MandatePaymentMethodDetailsSepaDebit`, `MandatePaymentMethodDetailsUpi`, `MandatePaymentMethodDetailsUsBankAccount`, `MandateService`, `MandateSingleUse`, `MultipartFileContent`, `NoSystemTextJsonAttributesNeededAttribute`, `OAuthAuthorizeUrlOptions`, `OAuthAuthorizeUrlStripeUserOptions`, `OAuthDeauthorize`, `OAuthDeauthorizeOptions`, `OAuthToken`, `OAuthTokenCreateOptions`, `PaymentAttemptRecord`, `PaymentAttemptRecordAmount`, `PaymentAttemptRecordAmountAuthorized`, `PaymentAttemptRecordAmountCanceled`, `PaymentAttemptRecordAmountFailed`, `PaymentAttemptRecordAmountGuaranteed`, `PaymentAttemptRecordAmountRefunded`, `PaymentAttemptRecordAmountRequested`, `PaymentAttemptRecordCustomerDetails`, `PaymentAttemptRecordListOptions`, `PaymentAttemptRecordPaymentMethodDetails`, `PaymentAttemptRecordPaymentMethodDetailsAchCreditTransfer`, `PaymentAttemptRecordPaymentMethodDetailsAchDebit`, `PaymentAttemptRecordPaymentMethodDetailsAcssDebit`, `PaymentAttemptRecordPaymentMethodDetailsAffirm`, `PaymentAttemptRecordPaymentMethodDetailsAfterpayClearpay`, `PaymentAttemptRecordPaymentMethodDetailsAlipay`, `PaymentAttemptRecordPaymentMethodDetailsAlma`, `PaymentAttemptRecordPaymentMethodDetailsAlmaInstallments`, `PaymentAttemptRecordPaymentMethodDetailsAmazonPay`, `PaymentAttemptRecordPaymentMethodDetailsAmazonPayFunding`, `PaymentAttemptRecordPaymentMethodDetailsAmazonPayFundingCard`, `PaymentAttemptRecordPaymentMethodDetailsAuBecsDebit`, `PaymentAttemptRecordPaymentMethodDetailsBacsDebit`, `PaymentAttemptRecordPaymentMethodDetailsBancontact`, `PaymentAttemptRecordPaymentMethodDetailsBillie`, `PaymentAttemptRecordPaymentMethodDetailsBillingDetails`, `PaymentAttemptRecordPaymentMethodDetailsBillingDetailsAddress`, `PaymentAttemptRecordPaymentMethodDetailsBizum`, `PaymentAttemptRecordPaymentMethodDetailsBlik`, `PaymentAttemptRecordPaymentMethodDetailsBoleto`, `PaymentAttemptRecordPaymentMethodDetailsCard`, `PaymentAttemptRecordPaymentMethodDetailsCardChecks`, `PaymentAttemptRecordPaymentMethodDetailsCardInstallments`, `PaymentAttemptRecordPaymentMethodDetailsCardInstallmentsPlan`, `PaymentAttemptRecordPaymentMethodDetailsCardNetworkToken`, `PaymentAttemptRecordPaymentMethodDetailsCardPresent`, `PaymentAttemptRecordPaymentMethodDetailsCardPresentOffline`, `PaymentAttemptRecordPaymentMethodDetailsCardPresentReceipt`, `PaymentAttemptRecordPaymentMethodDetailsCardPresentWallet`, `PaymentAttemptRecordPaymentMethodDetailsCardThreeDSecure`, `PaymentAttemptRecordPaymentMethodDetailsCardWallet`, `PaymentAttemptRecordPaymentMethodDetailsCardWalletApplePay`, `PaymentAttemptRecordPaymentMethodDetailsCashapp`, `PaymentAttemptRecordPaymentMethodDetailsCrypto`, `PaymentAttemptRecordPaymentMethodDetailsCustom`, `PaymentAttemptRecordPaymentMethodDetailsEps`, `PaymentAttemptRecordPaymentMethodDetailsFpx`, `PaymentAttemptRecordPaymentMethodDetailsGiropay`, `PaymentAttemptRecordPaymentMethodDetailsGrabpay`, `PaymentAttemptRecordPaymentMethodDetailsIdeal`, `PaymentAttemptRecordPaymentMethodDetailsInteracPresent`, `PaymentAttemptRecordPaymentMethodDetailsInteracPresentReceipt`, `PaymentAttemptRecordPaymentMethodDetailsKakaoPay`, `PaymentAttemptRecordPaymentMethodDetailsKlarna`, `PaymentAttemptRecordPaymentMethodDetailsKlarnaPayerDetails`, `PaymentAttemptRecordPaymentMethodDetailsKlarnaPayerDetailsAddress`, `PaymentAttemptRecordPaymentMethodDetailsKonbini`, `PaymentAttemptRecordPaymentMethodDetailsKonbiniStore`, `PaymentAttemptRecordPaymentMethodDetailsKrCard`, `PaymentAttemptRecordPaymentMethodDetailsLink`, `PaymentAttemptRecordPaymentMethodDetailsMobilepay`, `PaymentAttemptRecordPaymentMethodDetailsMobilepayCard`, `PaymentAttemptRecordPaymentMethodDetailsMultibanco`, `PaymentAttemptRecordPaymentMethodDetailsNaverPay`, `PaymentAttemptRecordPaymentMethodDetailsNzBankAccount`, `PaymentAttemptRecordPaymentMethodDetailsOxxo`, `PaymentAttemptRecordPaymentMethodDetailsP24`, `PaymentAttemptRecordPaymentMethodDetailsPayco`, `PaymentAttemptRecordPaymentMethodDetailsPaynow`, `PaymentAttemptRecordPaymentMethodDetailsPaypal`, `PaymentAttemptRecordPaymentMethodDetailsPaypalSellerProtection`, `PaymentAttemptRecordPaymentMethodDetailsPayto`, `PaymentAttemptRecordPaymentMethodDetailsPix`, `PaymentAttemptRecordPaymentMethodDetailsPromptpay`, `PaymentAttemptRecordPaymentMethodDetailsRevolutPay`, `PaymentAttemptRecordPaymentMethodDetailsRevolutPayFunding`, `PaymentAttemptRecordPaymentMethodDetailsRevolutPayFundingCard`, `PaymentAttemptRecordPaymentMethodDetailsSamsungPay`, `PaymentAttemptRecordPaymentMethodDetailsSatispay`, `PaymentAttemptRecordPaymentMethodDetailsScalapay`, `PaymentAttemptRecordPaymentMethodDetailsSepaCreditTransfer`, `PaymentAttemptRecordPaymentMethodDetailsSepaDebit`, `PaymentAttemptRecordPaymentMethodDetailsSofort`, `PaymentAttemptRecordPaymentMethodDetailsSunbit`, `PaymentAttemptRecordPaymentMethodDetailsSwish`, `PaymentAttemptRecordPaymentMethodDetailsTwint`, `PaymentAttemptRecordPaymentMethodDetailsUpi`, `PaymentAttemptRecordPaymentMethodDetailsUsBankAccount`, `PaymentAttemptRecordPaymentMethodDetailsWechatPay`, `PaymentAttemptRecordProcessorDetails`, `PaymentAttemptRecordProcessorDetailsCustom`, `PaymentAttemptRecordService`, `PaymentAttemptRecordShippingDetails`, `PaymentAttemptRecordShippingDetailsAddress`, `PaymentIntent`, `PaymentIntentAmountDetails`, `PaymentIntentAmountDetailsError`, `PaymentIntentAmountDetailsLineItem`, `PaymentIntentAmountDetailsLineItemOptions`, `PaymentIntentAmountDetailsLineItemPaymentMethodOptionsCardOptions`, `PaymentIntentAmountDetailsLineItemPaymentMethodOptionsCardPresentOptions`, `PaymentIntentAmountDetailsLineItemPaymentMethodOptionsKlarnaOptions`, `PaymentIntentAmountDetailsLineItemPaymentMethodOptionsOptions`, `PaymentIntentAmountDetailsLineItemPaymentMethodOptionsPaypal`, `PaymentIntentAmountDetailsLineItemPaymentMethodOptionsPaypalOptions`, `PaymentIntentAmountDetailsLineItemService`, `PaymentIntentAmountDetailsLineItemTax`, `PaymentIntentAmountDetailsLineItemTaxOptions`, `PaymentIntentAmountDetailsOptions`, `PaymentIntentAmountDetailsShipping`, `PaymentIntentAmountDetailsShippingOptions`, `PaymentIntentAmountDetailsTax`, `PaymentIntentAmountDetailsTaxOptions`, `PaymentIntentAmountDetailsTip`, `PaymentIntentApplyCustomerBalanceOptions`, `PaymentIntentAutomaticPaymentMethods`, `PaymentIntentAutomaticPaymentMethodsOptions`, `PaymentIntentCancelOptions`, `PaymentIntentCaptureOptions`, `PaymentIntentConfirmOptions`, `PaymentIntentCreateOptions`, `PaymentIntentGetOptions`, `PaymentIntentHooksInputsOptions`, `PaymentIntentHooksInputsTax`, `PaymentIntentHooksInputsTaxOptions`, `PaymentIntentHooksOptions`, `PaymentIntentIncrementAuthorizationOptions`, `PaymentIntentListOptions`, `PaymentIntentManagedPayments`, `PaymentIntentMandateDataCustomerAcceptanceOnlineOptions`, `PaymentIntentMandateDataCustomerAcceptanceOptions`, `PaymentIntentMandateDataOptions`, `PaymentIntentNextAction`, `PaymentIntentNextActionAlipayHandleRedirect`, `PaymentIntentNextActionBoletoDisplayDetails`, `PaymentIntentNextActionCardAwaitNotification`, `PaymentIntentNextActionCashappHandleRedirectOrDisplayQrCode`, `PaymentIntentNextActionCashappHandleRedirectOrDisplayQrCodeQrCode`, `PaymentIntentNextActionDisplayBankTransferInstructions`, `PaymentIntentNextActionDisplayBankTransferInstructionsFinancialAddress`, `PaymentIntentNextActionDisplayBankTransferInstructionsFinancialAddressAba`, `PaymentIntentNextActionDisplayBankTransferInstructionsFinancialAddressIban`, `PaymentIntentNextActionDisplayBankTransferInstructionsFinancialAddressSortCode`, `PaymentIntentNextActionDisplayBankTransferInstructionsFinancialAddressSpei`, `PaymentIntentNextActionDisplayBankTransferInstructionsFinancialAddressSwift`, `PaymentIntentNextActionDisplayBankTransferInstructionsFinancialAddressZengin`, `PaymentIntentNextActionKlarnaDisplayQrCode`, `PaymentIntentNextActionKonbiniDisplayDetails`, `PaymentIntentNextActionKonbiniDisplayDetailsStores`, `PaymentIntentNextActionKonbiniDisplayDetailsStoresFamilymart`, `PaymentIntentNextActionKonbiniDisplayDetailsStoresLawson`, `PaymentIntentNextActionKonbiniDisplayDetailsStoresMinistop`, `PaymentIntentNextActionKonbiniDisplayDetailsStoresSeicomart`, `PaymentIntentNextActionMultibancoDisplayDetails`, `PaymentIntentNextActionOxxoDisplayDetails`, `PaymentIntentNextActionPaynowDisplayQrCode`, `PaymentIntentNextActionPixDisplayQrCode`, `PaymentIntentNextActionPromptpayDisplayQrCode`, `PaymentIntentNextActionRedirectToUrl`, `PaymentIntentNextActionSwishHandleRedirectOrDisplayQrCode`, `PaymentIntentNextActionSwishHandleRedirectOrDisplayQrCodeQrCode`, `PaymentIntentNextActionUpiHandleRedirectOrDisplayQrCode`, `PaymentIntentNextActionUpiHandleRedirectOrDisplayQrCodeQrCode`, `PaymentIntentNextActionVerifyWithMicrodeposits`, `PaymentIntentNextActionWechatPayDisplayQrCode`, `PaymentIntentNextActionWechatPayRedirectToAndroidApp`, `PaymentIntentNextActionWechatPayRedirectToIosApp`, `PaymentIntentPaymentDetails`, `PaymentIntentPaymentDetailsOptions`, `PaymentIntentPaymentMethodConfigurationDetails`, `PaymentIntentPaymentMethodDataAcssDebitOptions`, `PaymentIntentPaymentMethodDataAuBecsDebitOptions`, `PaymentIntentPaymentMethodDataBacsDebitOptions`, `PaymentIntentPaymentMethodDataBillingDetailsOptions`, `PaymentIntentPaymentMethodDataBoletoOptions`, `PaymentIntentPaymentMethodDataEpsOptions`, `PaymentIntentPaymentMethodDataFpxOptions`, `PaymentIntentPaymentMethodDataIdealOptions`, `PaymentIntentPaymentMethodDataKlarnaOptions`, `PaymentIntentPaymentMethodDataNaverPayOptions`, `PaymentIntentPaymentMethodDataNzBankAccountOptions`, `PaymentIntentPaymentMethodDataOptions`, `PaymentIntentPaymentMethodDataP24Options`, `PaymentIntentPaymentMethodDataPaytoOptions`, `PaymentIntentPaymentMethodDataRadarOptionsOptions`, `PaymentIntentPaymentMethodDataSepaDebitOptions`, `PaymentIntentPaymentMethodDataSofortOptions`, `PaymentIntentPaymentMethodDataUpiMandateOptionsOptions`, `PaymentIntentPaymentMethodDataUpiOptions`, `PaymentIntentPaymentMethodDataUsBankAccountOptions`, `PaymentIntentPaymentMethodOptionsAcssDebit`, `PaymentIntentPaymentMethodOptionsAcssDebitMandateOptions`, `PaymentIntentPaymentMethodOptionsAcssDebitMandateOptionsOptions`, `PaymentIntentPaymentMethodOptionsAcssDebitOptions`, `PaymentIntentPaymentMethodOptionsAffirm`, `PaymentIntentPaymentMethodOptionsAffirmOptions`, `PaymentIntentPaymentMethodOptionsAfterpayClearpay`, `PaymentIntentPaymentMethodOptionsAfterpayClearpayOptions`, `PaymentIntentPaymentMethodOptionsAlipay`, `PaymentIntentPaymentMethodOptionsAlipayOptions`, `PaymentIntentPaymentMethodOptionsAlma`, `PaymentIntentPaymentMethodOptionsAlmaOptions`, `PaymentIntentPaymentMethodOptionsAmazonPay`, `PaymentIntentPaymentMethodOptionsAmazonPayOptions`, `PaymentIntentPaymentMethodOptionsAuBecsDebit`, `PaymentIntentPaymentMethodOptionsAuBecsDebitOptions`, `PaymentIntentPaymentMethodOptionsBacsDebit`, `PaymentIntentPaymentMethodOptionsBacsDebitMandateOptions`, `PaymentIntentPaymentMethodOptionsBacsDebitMandateOptionsOptions`, `PaymentIntentPaymentMethodOptionsBacsDebitOptions`, `PaymentIntentPaymentMethodOptionsBancontact`, `PaymentIntentPaymentMethodOptionsBancontactOptions`, `PaymentIntentPaymentMethodOptionsBillie`, `PaymentIntentPaymentMethodOptionsBillieOptions`, `PaymentIntentPaymentMethodOptionsBlik`, `PaymentIntentPaymentMethodOptionsBlikOptions`, `PaymentIntentPaymentMethodOptionsBoleto`, `PaymentIntentPaymentMethodOptionsBoletoOptions`, `PaymentIntentPaymentMethodOptionsCard`, `PaymentIntentPaymentMethodOptionsCardInstallments`, `PaymentIntentPaymentMethodOptionsCardInstallmentsOptions`, `PaymentIntentPaymentMethodOptionsCardInstallmentsPlan`, `PaymentIntentPaymentMethodOptionsCardInstallmentsPlanOptions`, `PaymentIntentPaymentMethodOptionsCardMandateOptions`, `PaymentIntentPaymentMethodOptionsCardMandateOptionsOptions`, `PaymentIntentPaymentMethodOptionsCardOptions`, `PaymentIntentPaymentMethodOptionsCardPresent`, `PaymentIntentPaymentMethodOptionsCardPresentOptions`, `PaymentIntentPaymentMethodOptionsCardPresentRouting`, `PaymentIntentPaymentMethodOptionsCardPresentRoutingOptions`, `PaymentIntentPaymentMethodOptionsCardThreeDSecureNetworkOptionsCartesBancairesOptions`, `PaymentIntentPaymentMethodOptionsCardThreeDSecureNetworkOptionsOptions`, `PaymentIntentPaymentMethodOptionsCardThreeDSecureOptions`, `PaymentIntentPaymentMethodOptionsCashapp`, `PaymentIntentPaymentMethodOptionsCashappOptions`, `PaymentIntentPaymentMethodOptionsCrypto`, `PaymentIntentPaymentMethodOptionsCryptoOptions`, `PaymentIntentPaymentMethodOptionsCustomerBalance`, `PaymentIntentPaymentMethodOptionsCustomerBalanceBankTransfer`, `PaymentIntentPaymentMethodOptionsCustomerBalanceBankTransferEuBankTransfer`, `PaymentIntentPaymentMethodOptionsCustomerBalanceBankTransferEuBankTransferOptions`, `PaymentIntentPaymentMethodOptionsCustomerBalanceBankTransferOptions`, `PaymentIntentPaymentMethodOptionsCustomerBalanceOptions`, `PaymentIntentPaymentMethodOptionsEps`, `PaymentIntentPaymentMethodOptionsEpsOptions`, `PaymentIntentPaymentMethodOptionsFpx`, `PaymentIntentPaymentMethodOptionsFpxOptions`, `PaymentIntentPaymentMethodOptionsGiropay`, `PaymentIntentPaymentMethodOptionsGiropayOptions`, `PaymentIntentPaymentMethodOptionsGrabpay`, `PaymentIntentPaymentMethodOptionsGrabpayOptions`, `PaymentIntentPaymentMethodOptionsIdeal`, `PaymentIntentPaymentMethodOptionsIdealOptions`, `PaymentIntentPaymentMethodOptionsKakaoPay`, `PaymentIntentPaymentMethodOptionsKakaoPayOptions`, `PaymentIntentPaymentMethodOptionsKlarna`, `PaymentIntentPaymentMethodOptionsKlarnaOnDemandOptions`, `PaymentIntentPaymentMethodOptionsKlarnaOptions`, `PaymentIntentPaymentMethodOptionsKlarnaSubscriptionNextBillingOptions`, `PaymentIntentPaymentMethodOptionsKlarnaSubscriptionOptions`, `PaymentIntentPaymentMethodOptionsKonbini`, `PaymentIntentPaymentMethodOptionsKonbiniOptions`, `PaymentIntentPaymentMethodOptionsKrCard`, `PaymentIntentPaymentMethodOptionsKrCardOptions`, `PaymentIntentPaymentMethodOptionsLink`, `PaymentIntentPaymentMethodOptionsLinkOptions`, `PaymentIntentPaymentMethodOptionsMbWay`, `PaymentIntentPaymentMethodOptionsMbWayOptions`, `PaymentIntentPaymentMethodOptionsMobilepay`, `PaymentIntentPaymentMethodOptionsMobilepayOptions`, `PaymentIntentPaymentMethodOptionsMultibanco`, `PaymentIntentPaymentMethodOptionsMultibancoOptions`, `PaymentIntentPaymentMethodOptionsNaverPay`, `PaymentIntentPaymentMethodOptionsNaverPayOptions`, `PaymentIntentPaymentMethodOptionsNzBankAccount`, `PaymentIntentPaymentMethodOptionsNzBankAccountOptions`, `PaymentIntentPaymentMethodOptionsOptions`, `PaymentIntentPaymentMethodOptionsOxxo`, `PaymentIntentPaymentMethodOptionsOxxoOptions`, `PaymentIntentPaymentMethodOptionsP24`, `PaymentIntentPaymentMethodOptionsP24Options`, `PaymentIntentPaymentMethodOptionsPayco`, `PaymentIntentPaymentMethodOptionsPaycoOptions`, `PaymentIntentPaymentMethodOptionsPaynow`, `PaymentIntentPaymentMethodOptionsPaynowOptions`, `PaymentIntentPaymentMethodOptionsPaypal`, `PaymentIntentPaymentMethodOptionsPaypalOptions`, `PaymentIntentPaymentMethodOptionsPayto`, `PaymentIntentPaymentMethodOptionsPaytoMandateOptions`, `PaymentIntentPaymentMethodOptionsPaytoMandateOptionsOptions`, `PaymentIntentPaymentMethodOptionsPaytoOptions`, `PaymentIntentPaymentMethodOptionsPix`, `PaymentIntentPaymentMethodOptionsPixMandateOptions`, `PaymentIntentPaymentMethodOptionsPixMandateOptionsOptions`, `PaymentIntentPaymentMethodOptionsPixOptions`, `PaymentIntentPaymentMethodOptionsPromptpay`, `PaymentIntentPaymentMethodOptionsPromptpayOptions`, `PaymentIntentPaymentMethodOptionsRevolutPay`, `PaymentIntentPaymentMethodOptionsRevolutPayOptions`, `PaymentIntentPaymentMethodOptionsSamsungPay`, `PaymentIntentPaymentMethodOptionsSamsungPayOptions`, `PaymentIntentPaymentMethodOptionsSatispay`, `PaymentIntentPaymentMethodOptionsSatispayOptions`, `PaymentIntentPaymentMethodOptionsScalapay`, `PaymentIntentPaymentMethodOptionsScalapayOptions`, `PaymentIntentPaymentMethodOptionsSepaDebit`, `PaymentIntentPaymentMethodOptionsSepaDebitMandateOptions`, `PaymentIntentPaymentMethodOptionsSepaDebitMandateOptionsOptions`, `PaymentIntentPaymentMethodOptionsSepaDebitOptions`, `PaymentIntentPaymentMethodOptionsSofort`, `PaymentIntentPaymentMethodOptionsSofortOptions`, `PaymentIntentPaymentMethodOptionsSwish`, `PaymentIntentPaymentMethodOptionsSwishOptions`, `PaymentIntentPaymentMethodOptionsTwint`, `PaymentIntentPaymentMethodOptionsTwintOptions`, `PaymentIntentPaymentMethodOptionsUpi`, `PaymentIntentPaymentMethodOptionsUpiMandateOptionsOptions`, `PaymentIntentPaymentMethodOptionsUpiOptions`, `PaymentIntentPaymentMethodOptionsUsBankAccount`, `PaymentIntentPaymentMethodOptionsUsBankAccountFinancialConnections`, `PaymentIntentPaymentMethodOptionsUsBankAccountFinancialConnectionsFilters`, `PaymentIntentPaymentMethodOptionsUsBankAccountFinancialConnectionsFiltersOptions`, `PaymentIntentPaymentMethodOptionsUsBankAccountFinancialConnectionsOptions`, `PaymentIntentPaymentMethodOptionsUsBankAccountMandateOptions`, `PaymentIntentPaymentMethodOptionsUsBankAccountMandateOptionsOptions`, `PaymentIntentPaymentMethodOptionsUsBankAccountNetworksOptions`, `PaymentIntentPaymentMethodOptionsUsBankAccountOptions`, `PaymentIntentPaymentMethodOptionsWechatPay`, `PaymentIntentPaymentMethodOptionsWechatPayOptions`, `PaymentIntentPaymentMethodOptionsZip`, `PaymentIntentPaymentMethodOptionsZipOptions`, `PaymentIntentPresentmentDetails`, `PaymentIntentProcessing`, `PaymentIntentProcessingCardCustomerNotification`, `PaymentIntentRadarOptionsOptions`, `PaymentIntentService`, `PaymentIntentTransferData`, `PaymentIntentTransferDataOptions`, `PaymentIntentTransferDataPaymentData`, `PaymentIntentTransferDataPaymentDataOptions`, `PaymentIntentUpdateOptions`, `PaymentIntentVerifyMicrodepositsOptions`, `PaymentLink`, `PaymentLinkAfterCompletion`, `PaymentLinkAfterCompletionHostedConfirmation`, `PaymentLinkAfterCompletionHostedConfirmationOptions`, `PaymentLinkAfterCompletionOptions`, `PaymentLinkAfterCompletionRedirect`, `PaymentLinkAfterCompletionRedirectOptions`, `PaymentLinkAutomaticTax`, `PaymentLinkAutomaticTaxLiability`, `PaymentLinkAutomaticTaxLiabilityOptions`, `PaymentLinkAutomaticTaxOptions`, `PaymentLinkConsentCollection`, `PaymentLinkConsentCollectionOptions`, `PaymentLinkConsentCollectionPaymentMethodReuseAgreement`, `PaymentLinkConsentCollectionPaymentMethodReuseAgreementOptions`, `PaymentLinkCreateOptions`, `PaymentLinkCustomField`, `PaymentLinkCustomFieldDropdown`, `PaymentLinkCustomFieldDropdownOption`, `PaymentLinkCustomFieldDropdownOptionOptions`, `PaymentLinkCustomFieldDropdownOptions`, `PaymentLinkCustomFieldLabel`, `PaymentLinkCustomFieldLabelOptions`, `PaymentLinkCustomFieldNumeric`, `PaymentLinkCustomFieldNumericOptions`, `PaymentLinkCustomFieldOptions`, `PaymentLinkCustomFieldText`, `PaymentLinkCustomFieldTextOptions`, `PaymentLinkCustomText`, `PaymentLinkCustomTextAfterSubmit`, `PaymentLinkCustomTextAfterSubmitOptions`, `PaymentLinkCustomTextOptions`, `PaymentLinkCustomTextShippingAddress`, `PaymentLinkCustomTextShippingAddressOptions`, `PaymentLinkCustomTextSubmit`, `PaymentLinkCustomTextSubmitOptions`, `PaymentLinkCustomTextTermsOfServiceAcceptance`, `PaymentLinkCustomTextTermsOfServiceAcceptanceOptions`, `PaymentLinkInvoiceCreation`, `PaymentLinkInvoiceCreationInvoiceData`, `PaymentLinkInvoiceCreationInvoiceDataCustomField`, `PaymentLinkInvoiceCreationInvoiceDataCustomFieldOptions`, `PaymentLinkInvoiceCreationInvoiceDataIssuer`, `PaymentLinkInvoiceCreationInvoiceDataIssuerOptions`, `PaymentLinkInvoiceCreationInvoiceDataOptions`, `PaymentLinkInvoiceCreationInvoiceDataRenderingOptions`, `PaymentLinkInvoiceCreationInvoiceDataRenderingOptionsOptions`, `PaymentLinkInvoiceCreationOptions`, `PaymentLinkLineItemAdjustableQuantityOptions`, `PaymentLinkLineItemOptions`, `PaymentLinkLineItemPriceDataOptions`, `PaymentLinkLineItemPriceDataProductDataOptions`, `PaymentLinkLineItemPriceDataRecurringOptions`, `PaymentLinkLineItemService`, `PaymentLinkListOptions`, `PaymentLinkManagedPayments`, `PaymentLinkManagedPaymentsOptions`, `PaymentLinkNameCollectionBusiness`, `PaymentLinkNameCollectionBusinessOptions`, `PaymentLinkNameCollectionIndividual`, `PaymentLinkNameCollectionIndividualOptions`, `PaymentLinkNameCollectionOptions`, `PaymentLinkOptionalItemAdjustableQuantity`, `PaymentLinkOptionalItemAdjustableQuantityOptions`, `PaymentLinkOptionalItemOptions`, `PaymentLinkPaymentIntentData`, `PaymentLinkPaymentIntentDataOptions`, `PaymentLinkPaymentMethodOptions`, `PaymentLinkPaymentMethodOptionsCard`, `PaymentLinkPaymentMethodOptionsCardOptions`, `PaymentLinkPaymentMethodOptionsCardRestrictions`, `PaymentLinkPaymentMethodOptionsCardRestrictionsOptions`, `PaymentLinkPaymentMethodOptionsOptions`, `PaymentLinkPhoneNumberCollection`, `PaymentLinkPhoneNumberCollectionOptions`, `PaymentLinkRestrictionsCompletedSessions`, `PaymentLinkRestrictionsCompletedSessionsOptions`, `PaymentLinkRestrictionsOptions`, `PaymentLinkService`, `PaymentLinkShippingAddressCollection`, `PaymentLinkShippingAddressCollectionOptions`, `PaymentLinkShippingOption`, `PaymentLinkShippingOptionOptions`, `PaymentLinkSubscriptionData`, `PaymentLinkSubscriptionDataInvoiceSettingsIssuer`, `PaymentLinkSubscriptionDataInvoiceSettingsIssuerOptions`, `PaymentLinkSubscriptionDataInvoiceSettingsOptions`, `PaymentLinkSubscriptionDataOptions`, `PaymentLinkSubscriptionDataTrialSettings`, `PaymentLinkSubscriptionDataTrialSettingsEndBehavior`, `PaymentLinkSubscriptionDataTrialSettingsEndBehaviorOptions`, `PaymentLinkSubscriptionDataTrialSettingsOptions`, `PaymentLinkTaxIdCollection`, `PaymentLinkTaxIdCollectionOptions`, `PaymentLinkTransferData`, `PaymentLinkTransferDataOptions`, `PaymentLinkUpdateOptions`, `PaymentMethod`, `PaymentMethodAcssDebit`, `PaymentMethodAcssDebitOptions`, `PaymentMethodAttachOptions`, `PaymentMethodAuBecsDebit`, `PaymentMethodAuBecsDebitOptions`, `PaymentMethodBacsDebit`, `PaymentMethodBacsDebitOptions`, `PaymentMethodBillingDetails`, `PaymentMethodBillingDetailsOptions`, `PaymentMethodBoleto`, `PaymentMethodBoletoOptions`, `PaymentMethodCard`, `PaymentMethodCardChecks`, `PaymentMethodCardGeneratedFrom`, `PaymentMethodCardGeneratedFromPaymentMethodDetails`, `PaymentMethodCardGeneratedFromPaymentMethodDetailsCardPresent`, `PaymentMethodCardGeneratedFromPaymentMethodDetailsCardPresentOffline`, `PaymentMethodCardGeneratedFromPaymentMethodDetailsCardPresentReceipt`, `PaymentMethodCardGeneratedFromPaymentMethodDetailsCardPresentWallet`, `PaymentMethodCardNetworks`, `PaymentMethodCardNetworksOptions`, `PaymentMethodCardOptions`, `PaymentMethodCardPresent`, `PaymentMethodCardPresentNetworks`, `PaymentMethodCardPresentOffline`, `PaymentMethodCardPresentWallet`, `PaymentMethodCardThreeDSecureUsage`, `PaymentMethodCardWallet`, `PaymentMethodCardWalletMasterpass`, `PaymentMethodCardWalletVisaCheckout`, `PaymentMethodCashapp`, `PaymentMethodConfiguration`, `PaymentMethodConfigurationAcssDebit`, `PaymentMethodConfigurationAcssDebitDisplayPreference`, `PaymentMethodConfigurationAcssDebitDisplayPreferenceOptions`, `PaymentMethodConfigurationAcssDebitOptions`, `PaymentMethodConfigurationAffirm`, `PaymentMethodConfigurationAffirmDisplayPreference`, `PaymentMethodConfigurationAffirmDisplayPreferenceOptions`, `PaymentMethodConfigurationAffirmOptions`, `PaymentMethodConfigurationAfterpayClearpay`, `PaymentMethodConfigurationAfterpayClearpayDisplayPreference`, `PaymentMethodConfigurationAfterpayClearpayDisplayPreferenceOptions`, `PaymentMethodConfigurationAfterpayClearpayOptions`, `PaymentMethodConfigurationAlipay`, `PaymentMethodConfigurationAlipayDisplayPreference`, `PaymentMethodConfigurationAlipayDisplayPreferenceOptions`, `PaymentMethodConfigurationAlipayOptions`, `PaymentMethodConfigurationAlma`, `PaymentMethodConfigurationAlmaDisplayPreference`, `PaymentMethodConfigurationAlmaDisplayPreferenceOptions`, `PaymentMethodConfigurationAlmaOptions`, `PaymentMethodConfigurationAmazonPay`, `PaymentMethodConfigurationAmazonPayDisplayPreference`, `PaymentMethodConfigurationAmazonPayDisplayPreferenceOptions`, `PaymentMethodConfigurationAmazonPayOptions`, `PaymentMethodConfigurationApplePay`, `PaymentMethodConfigurationApplePayDisplayPreference`, `PaymentMethodConfigurationApplePayDisplayPreferenceOptions`, `PaymentMethodConfigurationApplePayLaterDisplayPreferenceOptions`, `PaymentMethodConfigurationApplePayLaterOptions`, `PaymentMethodConfigurationApplePayOptions`, `PaymentMethodConfigurationAuBecsDebit`, `PaymentMethodConfigurationAuBecsDebitDisplayPreference`, `PaymentMethodConfigurationAuBecsDebitDisplayPreferenceOptions`, `PaymentMethodConfigurationAuBecsDebitOptions`, `PaymentMethodConfigurationBacsDebit`, `PaymentMethodConfigurationBacsDebitDisplayPreference`, `PaymentMethodConfigurationBacsDebitDisplayPreferenceOptions`, `PaymentMethodConfigurationBacsDebitOptions`, `PaymentMethodConfigurationBancontact`, `PaymentMethodConfigurationBancontactDisplayPreference`, `PaymentMethodConfigurationBancontactDisplayPreferenceOptions`, `PaymentMethodConfigurationBancontactOptions`, `PaymentMethodConfigurationBillie`, `PaymentMethodConfigurationBillieDisplayPreference`, `PaymentMethodConfigurationBillieDisplayPreferenceOptions`, `PaymentMethodConfigurationBillieOptions`, `PaymentMethodConfigurationBizum`, `PaymentMethodConfigurationBizumDisplayPreference`, `PaymentMethodConfigurationBizumDisplayPreferenceOptions`, `PaymentMethodConfigurationBizumOptions`, `PaymentMethodConfigurationBlik`, `PaymentMethodConfigurationBlikDisplayPreference`, `PaymentMethodConfigurationBlikDisplayPreferenceOptions`, `PaymentMethodConfigurationBlikOptions`, `PaymentMethodConfigurationBoleto`, `PaymentMethodConfigurationBoletoDisplayPreference`, `PaymentMethodConfigurationBoletoDisplayPreferenceOptions`, `PaymentMethodConfigurationBoletoOptions`, `PaymentMethodConfigurationCard`, `PaymentMethodConfigurationCardDisplayPreference`, `PaymentMethodConfigurationCardDisplayPreferenceOptions`, `PaymentMethodConfigurationCardOptions`, `PaymentMethodConfigurationCartesBancaires`, `PaymentMethodConfigurationCartesBancairesDisplayPreference`, `PaymentMethodConfigurationCartesBancairesDisplayPreferenceOptions`, `PaymentMethodConfigurationCartesBancairesOptions`, `PaymentMethodConfigurationCashapp`, `PaymentMethodConfigurationCashappDisplayPreference`, `PaymentMethodConfigurationCashappDisplayPreferenceOptions`, `PaymentMethodConfigurationCashappOptions`, `PaymentMethodConfigurationCreateOptions`, `PaymentMethodConfigurationCrypto`, `PaymentMethodConfigurationCryptoDisplayPreference`, `PaymentMethodConfigurationCryptoDisplayPreferenceOptions`, `PaymentMethodConfigurationCryptoOptions`, `PaymentMethodConfigurationCustomerBalance`, `PaymentMethodConfigurationCustomerBalanceDisplayPreference`, `PaymentMethodConfigurationCustomerBalanceDisplayPreferenceOptions`, `PaymentMethodConfigurationCustomerBalanceOptions`, `PaymentMethodConfigurationEps`, `PaymentMethodConfigurationEpsDisplayPreference`, `PaymentMethodConfigurationEpsDisplayPreferenceOptions`, `PaymentMethodConfigurationEpsOptions`, `PaymentMethodConfigurationFpx`, `PaymentMethodConfigurationFpxDisplayPreference`, `PaymentMethodConfigurationFpxDisplayPreferenceOptions`, `PaymentMethodConfigurationFpxOptions`, `PaymentMethodConfigurationFrMealVoucherConecsDisplayPreferenceOptions`, `PaymentMethodConfigurationFrMealVoucherConecsOptions`, `PaymentMethodConfigurationGiropay`, `PaymentMethodConfigurationGiropayDisplayPreference`, `PaymentMethodConfigurationGiropayDisplayPreferenceOptions`, `PaymentMethodConfigurationGiropayOptions`, `PaymentMethodConfigurationGooglePay`, `PaymentMethodConfigurationGooglePayDisplayPreference`, `PaymentMethodConfigurationGooglePayDisplayPreferenceOptions`, `PaymentMethodConfigurationGooglePayOptions`, `PaymentMethodConfigurationGrabpay`, `PaymentMethodConfigurationGrabpayDisplayPreference`, `PaymentMethodConfigurationGrabpayDisplayPreferenceOptions`, `PaymentMethodConfigurationGrabpayOptions`, `PaymentMethodConfigurationIdeal`, `PaymentMethodConfigurationIdealDisplayPreference`, `PaymentMethodConfigurationIdealDisplayPreferenceOptions`, `PaymentMethodConfigurationIdealOptions`, `PaymentMethodConfigurationJcb`, `PaymentMethodConfigurationJcbDisplayPreference`, `PaymentMethodConfigurationJcbDisplayPreferenceOptions`, `PaymentMethodConfigurationJcbOptions`, `PaymentMethodConfigurationKakaoPay`, `PaymentMethodConfigurationKakaoPayDisplayPreference`, `PaymentMethodConfigurationKakaoPayDisplayPreferenceOptions`, `PaymentMethodConfigurationKakaoPayOptions`, `PaymentMethodConfigurationKlarna`, `PaymentMethodConfigurationKlarnaDisplayPreference`, `PaymentMethodConfigurationKlarnaDisplayPreferenceOptions`, `PaymentMethodConfigurationKlarnaOptions`, `PaymentMethodConfigurationKonbini`, `PaymentMethodConfigurationKonbiniDisplayPreference`, `PaymentMethodConfigurationKonbiniDisplayPreferenceOptions`, `PaymentMethodConfigurationKonbiniOptions`, `PaymentMethodConfigurationKrCard`, `PaymentMethodConfigurationKrCardDisplayPreference`, `PaymentMethodConfigurationKrCardDisplayPreferenceOptions`, `PaymentMethodConfigurationKrCardOptions`, `PaymentMethodConfigurationLink`, `PaymentMethodConfigurationLinkDisplayPreference`, `PaymentMethodConfigurationLinkDisplayPreferenceOptions`, `PaymentMethodConfigurationLinkOptions`, `PaymentMethodConfigurationListOptions`, `PaymentMethodConfigurationMbWay`, `PaymentMethodConfigurationMbWayDisplayPreference`, `PaymentMethodConfigurationMbWayDisplayPreferenceOptions`, `PaymentMethodConfigurationMbWayOptions`, `PaymentMethodConfigurationMobilepay`, `PaymentMethodConfigurationMobilepayDisplayPreference`, `PaymentMethodConfigurationMobilepayDisplayPreferenceOptions`, `PaymentMethodConfigurationMobilepayOptions`, `PaymentMethodConfigurationMultibanco`, `PaymentMethodConfigurationMultibancoDisplayPreference`, `PaymentMethodConfigurationMultibancoDisplayPreferenceOptions`, `PaymentMethodConfigurationMultibancoOptions`, `PaymentMethodConfigurationNaverPay`, `PaymentMethodConfigurationNaverPayDisplayPreference`, `PaymentMethodConfigurationNaverPayDisplayPreferenceOptions`, `PaymentMethodConfigurationNaverPayOptions`, `PaymentMethodConfigurationNzBankAccount`, `PaymentMethodConfigurationNzBankAccountDisplayPreference`, `PaymentMethodConfigurationNzBankAccountDisplayPreferenceOptions`, `PaymentMethodConfigurationNzBankAccountOptions`, `PaymentMethodConfigurationOxxo`, `PaymentMethodConfigurationOxxoDisplayPreference`, `PaymentMethodConfigurationOxxoDisplayPreferenceOptions`, `PaymentMethodConfigurationOxxoOptions`, `PaymentMethodConfigurationP24`, `PaymentMethodConfigurationP24DisplayPreference`, `PaymentMethodConfigurationP24DisplayPreferenceOptions`, `PaymentMethodConfigurationP24Options`, `PaymentMethodConfigurationPayByBank`, `PaymentMethodConfigurationPayByBankDisplayPreference`, `PaymentMethodConfigurationPayByBankDisplayPreferenceOptions`, `PaymentMethodConfigurationPayByBankOptions`, `PaymentMethodConfigurationPayco`, `PaymentMethodConfigurationPaycoDisplayPreference`, `PaymentMethodConfigurationPaycoDisplayPreferenceOptions`, `PaymentMethodConfigurationPaycoOptions`, `PaymentMethodConfigurationPaynow`, `PaymentMethodConfigurationPaynowDisplayPreference`, `PaymentMethodConfigurationPaynowDisplayPreferenceOptions`, `PaymentMethodConfigurationPaynowOptions`, `PaymentMethodConfigurationPaypal`, `PaymentMethodConfigurationPaypalDisplayPreference`, `PaymentMethodConfigurationPaypalDisplayPreferenceOptions`, `PaymentMethodConfigurationPaypalOptions`, `PaymentMethodConfigurationPayto`, `PaymentMethodConfigurationPaytoDisplayPreference`, `PaymentMethodConfigurationPaytoDisplayPreferenceOptions`, `PaymentMethodConfigurationPaytoOptions`, `PaymentMethodConfigurationPix`, `PaymentMethodConfigurationPixDisplayPreference`, `PaymentMethodConfigurationPixDisplayPreferenceOptions`, `PaymentMethodConfigurationPixOptions`, `PaymentMethodConfigurationPromptpay`, `PaymentMethodConfigurationPromptpayDisplayPreference`, `PaymentMethodConfigurationPromptpayDisplayPreferenceOptions`, `PaymentMethodConfigurationPromptpayOptions`, `PaymentMethodConfigurationRevolutPay`, `PaymentMethodConfigurationRevolutPayDisplayPreference`, `PaymentMethodConfigurationRevolutPayDisplayPreferenceOptions`, `PaymentMethodConfigurationRevolutPayOptions`, `PaymentMethodConfigurationSamsungPay`, `PaymentMethodConfigurationSamsungPayDisplayPreference`, `PaymentMethodConfigurationSamsungPayDisplayPreferenceOptions`, `PaymentMethodConfigurationSamsungPayOptions`, `PaymentMethodConfigurationSatispay`, `PaymentMethodConfigurationSatispayDisplayPreference`, `PaymentMethodConfigurationSatispayDisplayPreferenceOptions`, `PaymentMethodConfigurationSatispayOptions`, `PaymentMethodConfigurationScalapay`, `PaymentMethodConfigurationScalapayDisplayPreference`, `PaymentMethodConfigurationScalapayDisplayPreferenceOptions`, `PaymentMethodConfigurationScalapayOptions`, `PaymentMethodConfigurationSepaDebit`, `PaymentMethodConfigurationSepaDebitDisplayPreference`, `PaymentMethodConfigurationSepaDebitDisplayPreferenceOptions`, `PaymentMethodConfigurationSepaDebitOptions`, `PaymentMethodConfigurationService`, `PaymentMethodConfigurationSofort`, `PaymentMethodConfigurationSofortDisplayPreference`, `PaymentMethodConfigurationSofortDisplayPreferenceOptions`, `PaymentMethodConfigurationSofortOptions`, `PaymentMethodConfigurationSunbit`, `PaymentMethodConfigurationSunbitDisplayPreference`, `PaymentMethodConfigurationSunbitDisplayPreferenceOptions`, `PaymentMethodConfigurationSunbitOptions`, `PaymentMethodConfigurationSwish`, `PaymentMethodConfigurationSwishDisplayPreference`, `PaymentMethodConfigurationSwishDisplayPreferenceOptions`, `PaymentMethodConfigurationSwishOptions`, `PaymentMethodConfigurationTwint`, `PaymentMethodConfigurationTwintDisplayPreference`, `PaymentMethodConfigurationTwintDisplayPreferenceOptions`, `PaymentMethodConfigurationTwintOptions`, `PaymentMethodConfigurationUpdateOptions`, `PaymentMethodConfigurationUpi`, `PaymentMethodConfigurationUpiDisplayPreference`, `PaymentMethodConfigurationUpiDisplayPreferenceOptions`, `PaymentMethodConfigurationUpiOptions`, `PaymentMethodConfigurationUsBankAccount`, `PaymentMethodConfigurationUsBankAccountDisplayPreference`, `PaymentMethodConfigurationUsBankAccountDisplayPreferenceOptions`, `PaymentMethodConfigurationUsBankAccountOptions`, `PaymentMethodConfigurationWechatPay`, `PaymentMethodConfigurationWechatPayDisplayPreference`, `PaymentMethodConfigurationWechatPayDisplayPreferenceOptions`, `PaymentMethodConfigurationWechatPayOptions`, `PaymentMethodConfigurationZip`, `PaymentMethodConfigurationZipDisplayPreference`, `PaymentMethodConfigurationZipDisplayPreferenceOptions`, `PaymentMethodConfigurationZipOptions`, `PaymentMethodCreateOptions`, `PaymentMethodCustom`, `PaymentMethodCustomLogo`, `PaymentMethodCustomOptions`, `PaymentMethodDomain`, `PaymentMethodDomainAmazonPay`, `PaymentMethodDomainAmazonPayStatusDetails`, `PaymentMethodDomainApplePay`, `PaymentMethodDomainApplePayStatusDetails`, `PaymentMethodDomainCreateOptions`, `PaymentMethodDomainGooglePay`, `PaymentMethodDomainGooglePayStatusDetails`, `PaymentMethodDomainKlarna`, `PaymentMethodDomainKlarnaStatusDetails`, `PaymentMethodDomainLink`, `PaymentMethodDomainLinkStatusDetails`, `PaymentMethodDomainListOptions`, `PaymentMethodDomainPaypal`, `PaymentMethodDomainPaypalStatusDetails`, `PaymentMethodDomainService`, `PaymentMethodDomainUpdateOptions`, `PaymentMethodEps`, `PaymentMethodEpsOptions`, `PaymentMethodFpx`, `PaymentMethodFpxOptions`, `PaymentMethodIdeal`, `PaymentMethodIdealOptions`, `PaymentMethodInteracPresent`, `PaymentMethodInteracPresentNetworks`, `PaymentMethodKlarna`, `PaymentMethodKlarnaDob`, `PaymentMethodKlarnaOptions`, `PaymentMethodKrCard`, `PaymentMethodLink`, `PaymentMethodListOptions`, `PaymentMethodNaverPay`, `PaymentMethodNaverPayOptions`, `PaymentMethodNzBankAccount`, `PaymentMethodNzBankAccountOptions`, `PaymentMethodP24`, `PaymentMethodP24Options`, `PaymentMethodPaypal`, `PaymentMethodPayto`, `PaymentMethodPaytoOptions`, `PaymentMethodRadarOptions`, `PaymentMethodRadarOptionsOptions`, `PaymentMethodSepaDebit`, `PaymentMethodSepaDebitGeneratedFrom`, `PaymentMethodSepaDebitOptions`, `PaymentMethodService`, `PaymentMethodSofort`, `PaymentMethodSofortOptions`, `PaymentMethodUpdateOptions`, `PaymentMethodUpi`, `PaymentMethodUpiMandateOptionsOptions`, `PaymentMethodUpiOptions`, `PaymentMethodUsBankAccount`, `PaymentMethodUsBankAccountNetworks`, `PaymentMethodUsBankAccountOptions`, `PaymentMethodUsBankAccountStatusDetailsBlocked`, `PaymentRecord`, `PaymentRecordAmount`, `PaymentRecordAmountAuthorized`, `PaymentRecordAmountCanceled`, `PaymentRecordAmountFailed`, `PaymentRecordAmountGuaranteed`, `PaymentRecordAmountOptions`, `PaymentRecordAmountRefunded`, `PaymentRecordAmountRequested`, `PaymentRecordAmountRequestedOptions`, `PaymentRecordCustomerDetails`, `PaymentRecordCustomerDetailsOptions`, `PaymentRecordFailedOptions`, `PaymentRecordGuaranteedOptions`, `PaymentRecordPaymentMethodDetails`, `PaymentRecordPaymentMethodDetailsAchCreditTransfer`, `PaymentRecordPaymentMethodDetailsAchDebit`, `PaymentRecordPaymentMethodDetailsAcssDebit`, `PaymentRecordPaymentMethodDetailsAffirm`, `PaymentRecordPaymentMethodDetailsAfterpayClearpay`, `PaymentRecordPaymentMethodDetailsAlipay`, `PaymentRecordPaymentMethodDetailsAlma`, `PaymentRecordPaymentMethodDetailsAlmaInstallments`, `PaymentRecordPaymentMethodDetailsAmazonPay`, `PaymentRecordPaymentMethodDetailsAmazonPayFunding`, `PaymentRecordPaymentMethodDetailsAmazonPayFundingCard`, `PaymentRecordPaymentMethodDetailsAuBecsDebit`, `PaymentRecordPaymentMethodDetailsBacsDebit`, `PaymentRecordPaymentMethodDetailsBancontact`, `PaymentRecordPaymentMethodDetailsBillie`, `PaymentRecordPaymentMethodDetailsBillingDetails`, `PaymentRecordPaymentMethodDetailsBillingDetailsAddress`, `PaymentRecordPaymentMethodDetailsBillingDetailsOptions`, `PaymentRecordPaymentMethodDetailsBizum`, `PaymentRecordPaymentMethodDetailsBlik`, `PaymentRecordPaymentMethodDetailsBoleto`, `PaymentRecordPaymentMethodDetailsCard`, `PaymentRecordPaymentMethodDetailsCardChecks`, `PaymentRecordPaymentMethodDetailsCardInstallments`, `PaymentRecordPaymentMethodDetailsCardInstallmentsPlan`, `PaymentRecordPaymentMethodDetailsCardNetworkToken`, `PaymentRecordPaymentMethodDetailsCardPresent`, `PaymentRecordPaymentMethodDetailsCardPresentOffline`, `PaymentRecordPaymentMethodDetailsCardPresentReceipt`, `PaymentRecordPaymentMethodDetailsCardPresentWallet`, `PaymentRecordPaymentMethodDetailsCardThreeDSecure`, `PaymentRecordPaymentMethodDetailsCardWallet`, `PaymentRecordPaymentMethodDetailsCardWalletApplePay`, `PaymentRecordPaymentMethodDetailsCashapp`, `PaymentRecordPaymentMethodDetailsCrypto`, `PaymentRecordPaymentMethodDetailsCustom`, `PaymentRecordPaymentMethodDetailsCustomOptions`, `PaymentRecordPaymentMethodDetailsEps`, `PaymentRecordPaymentMethodDetailsFpx`, `PaymentRecordPaymentMethodDetailsGiropay`, `PaymentRecordPaymentMethodDetailsGrabpay`, `PaymentRecordPaymentMethodDetailsIdeal`, `PaymentRecordPaymentMethodDetailsInteracPresent`, `PaymentRecordPaymentMethodDetailsInteracPresentReceipt`, `PaymentRecordPaymentMethodDetailsKakaoPay`, `PaymentRecordPaymentMethodDetailsKlarna`, `PaymentRecordPaymentMethodDetailsKlarnaPayerDetails`, `PaymentRecordPaymentMethodDetailsKlarnaPayerDetailsAddress`, `PaymentRecordPaymentMethodDetailsKonbini`, `PaymentRecordPaymentMethodDetailsKonbiniStore`, `PaymentRecordPaymentMethodDetailsKrCard`, `PaymentRecordPaymentMethodDetailsLink`, `PaymentRecordPaymentMethodDetailsMobilepay`, `PaymentRecordPaymentMethodDetailsMobilepayCard`, `PaymentRecordPaymentMethodDetailsMultibanco`, `PaymentRecordPaymentMethodDetailsNaverPay`, `PaymentRecordPaymentMethodDetailsNzBankAccount`, `PaymentRecordPaymentMethodDetailsOptions`, `PaymentRecordPaymentMethodDetailsOxxo`, `PaymentRecordPaymentMethodDetailsP24`, `PaymentRecordPaymentMethodDetailsPayco`, `PaymentRecordPaymentMethodDetailsPaynow`, `PaymentRecordPaymentMethodDetailsPaypal`, `PaymentRecordPaymentMethodDetailsPaypalSellerProtection`, `PaymentRecordPaymentMethodDetailsPayto`, `PaymentRecordPaymentMethodDetailsPix`, `PaymentRecordPaymentMethodDetailsPromptpay`, `PaymentRecordPaymentMethodDetailsRevolutPay`, `PaymentRecordPaymentMethodDetailsRevolutPayFunding`, `PaymentRecordPaymentMethodDetailsRevolutPayFundingCard`, `PaymentRecordPaymentMethodDetailsSamsungPay`, `PaymentRecordPaymentMethodDetailsSatispay`, `PaymentRecordPaymentMethodDetailsScalapay`, `PaymentRecordPaymentMethodDetailsSepaCreditTransfer`, `PaymentRecordPaymentMethodDetailsSepaDebit`, `PaymentRecordPaymentMethodDetailsSofort`, `PaymentRecordPaymentMethodDetailsSunbit`, `PaymentRecordPaymentMethodDetailsSwish`, `PaymentRecordPaymentMethodDetailsTwint`, `PaymentRecordPaymentMethodDetailsUpi`, `PaymentRecordPaymentMethodDetailsUsBankAccount`, `PaymentRecordPaymentMethodDetailsWechatPay`, `PaymentRecordProcessorDetails`, `PaymentRecordProcessorDetailsCustom`, `PaymentRecordProcessorDetailsCustomOptions`, `PaymentRecordProcessorDetailsOptions`, `PaymentRecordRefundedOptions`, `PaymentRecordReportPaymentAttemptCanceledOptions`, `PaymentRecordReportPaymentAttemptFailedOptions`, `PaymentRecordReportPaymentAttemptGuaranteedOptions`, `PaymentRecordReportPaymentAttemptInformationalOptions`, `PaymentRecordReportPaymentAttemptOptions`, `PaymentRecordReportPaymentOptions`, `PaymentRecordReportRefundOptions`, `PaymentRecordService`, `PaymentRecordShippingDetails`, `PaymentRecordShippingDetailsAddress`, `PaymentRecordShippingDetailsOptions`, `Payout`, `PayoutCreateOptions`, `PayoutListOptions`, `PayoutReverseOptions`, `PayoutService`, `PayoutTraceId`, `PayoutUpdateOptions`, `Person`, `PersonAdditionalTosAcceptances`, `PersonAdditionalTosAcceptancesAccount`, `PersonFutureRequirements`, `PersonFutureRequirementsAlternative`, `PersonFutureRequirementsError`, `PersonRelationship`, `PersonRequirements`, `PersonRequirementsAlternative`, `PersonRequirementsError`, `PersonUsCfpbData`, `PersonUsCfpbDataEthnicityDetails`, `PersonUsCfpbDataRaceDetails`, `PersonVerification`, `PersonVerificationAdditionalDocument`, `PersonVerificationDocument`, `Plan`, `PlanCreateOptions`, `PlanListOptions`, `PlanProductOptions`, `PlanService`, `PlanTier`, `PlanTierOptions`, `PlanTransformUsage`, `PlanTransformUsageOptions`, `PlanUpdateOptions`, `Price`, `PriceCreateOptions`, `PriceCurrencyOptions`, `PriceCurrencyOptionsCustomUnitAmount`, `PriceCurrencyOptionsCustomUnitAmountOptions`, `PriceCurrencyOptionsOptions`, `PriceCurrencyOptionsTier`, `PriceCurrencyOptionsTierOptions`, `PriceCustomUnitAmount`, `PriceCustomUnitAmountOptions`, `PriceListOptions`, `PriceProductDataOptions`, `PriceRecurring`, `PriceRecurringListOptions`, `PriceRecurringOptions`, `PriceService`, `PriceTier`, `PriceTierOptions`, `PriceTransformQuantity`, `PriceTransformQuantityOptions`, `PriceUpdateOptions`, `Product`, `ProductCreateOptions`, `ProductDefaultPriceDataCurrencyOptionsCustomUnitAmountOptions`, `ProductDefaultPriceDataCurrencyOptionsOptions`, `ProductDefaultPriceDataCurrencyOptionsTierOptions`, `ProductDefaultPriceDataCustomUnitAmountOptions`, `ProductDefaultPriceDataOptions`, `ProductDefaultPriceDataRecurringOptions`, `ProductFeature`, `ProductFeatureCreateOptions`, `ProductFeatureService`, `ProductListOptions`, `ProductMarketingFeature`, `ProductMarketingFeatureOptions`, `ProductPackageDimensions`, `ProductPackageDimensionsOptions`, `ProductService`, `ProductUpdateOptions`, `PromotionCode`, `PromotionCodeCreateOptions`, `PromotionCodeListOptions`, `PromotionCodePromotion`, `PromotionCodePromotionOptions`, `PromotionCodeRestrictions`, `PromotionCodeRestrictionsCurrencyOptions`, `PromotionCodeRestrictionsCurrencyOptionsOptions`, `PromotionCodeRestrictionsOptions`, `PromotionCodeService`, `PromotionCodeUpdateOptions`, `Quote`, `QuoteAutomaticTax`, `QuoteAutomaticTaxLiability`, `QuoteAutomaticTaxLiabilityOptions`, `QuoteAutomaticTaxOptions`, `QuoteComputed`, `QuoteComputedRecurring`, `QuoteComputedRecurringTotalDetails`, `QuoteComputedRecurringTotalDetailsBreakdown`, `QuoteComputedRecurringTotalDetailsBreakdownDiscount`, `QuoteComputedRecurringTotalDetailsBreakdownTax`, `QuoteComputedUpfront`, `QuoteComputedUpfrontLineItemsService`, `QuoteComputedUpfrontTotalDetails`, `QuoteComputedUpfrontTotalDetailsBreakdown`, `QuoteComputedUpfrontTotalDetailsBreakdownDiscount`, `QuoteComputedUpfrontTotalDetailsBreakdownTax`, `QuoteCreateOptions`, `QuoteDiscountOptions`, `QuoteFinalizeOptions`, `QuoteFromQuote`, `QuoteFromQuoteOptions`, `QuoteInvoiceSettings`, `QuoteInvoiceSettingsIssuer`, `QuoteInvoiceSettingsIssuerOptions`, `QuoteInvoiceSettingsOptions`, `QuoteLineItemDiscountOptions`, `QuoteLineItemOptions`, `QuoteLineItemPriceDataOptions`, `QuoteLineItemPriceDataRecurringOptions`, `QuoteLineItemService`, `QuoteListOptions`, `QuoteService`, `QuoteStatusTransitions`, `QuoteSubscriptionData`, `QuoteSubscriptionDataBillingMode`, `QuoteSubscriptionDataBillingModeFlexible`, `QuoteSubscriptionDataBillingModeFlexibleOptions`, `QuoteSubscriptionDataBillingModeOptions`, `QuoteSubscriptionDataOptions`, `QuoteTotalDetails`, `QuoteTotalDetailsBreakdown`, `QuoteTotalDetailsBreakdownDiscount`, `QuoteTotalDetailsBreakdownTax`, `QuoteTransferData`, `QuoteTransferDataOptions`, `QuoteUpdateOptions`, `RawRequestOptions`, `Refund`, `RefundCreateOptions`, `RefundDestinationDetails`, `RefundDestinationDetailsBlik`, `RefundDestinationDetailsBrBankTransfer`, `RefundDestinationDetailsCard`, `RefundDestinationDetailsCrypto`, `RefundDestinationDetailsEuBankTransfer`, `RefundDestinationDetailsGbBankTransfer`, `RefundDestinationDetailsJpBankTransfer`, `RefundDestinationDetailsMbWay`, `RefundDestinationDetailsMultibanco`, `RefundDestinationDetailsMxBankTransfer`, `RefundDestinationDetailsP24`, `RefundDestinationDetailsPaypal`, `RefundDestinationDetailsSwish`, `RefundDestinationDetailsThBankTransfer`, `RefundDestinationDetailsUsBankTransfer`, `RefundListOptions`, `RefundNextAction`, `RefundNextActionDisplayDetails`, `RefundNextActionDisplayDetailsEmailSent`, `RefundPresentmentDetails`, `RefundService`, `RefundUpdateOptions`, `RequestOptions`, `RequestTelemetry`, `ReserveTransaction`, `Review`, `ReviewListOptions`, `ReviewService`, `ReviewSession`, `SearchOptions`, `Service`, `Service<T>`, `SetupAttempt`, `SetupAttemptListOptions`, `SetupAttemptPaymentMethodDetails`, `SetupAttemptPaymentMethodDetailsBancontact`, `SetupAttemptPaymentMethodDetailsCard`, `SetupAttemptPaymentMethodDetailsCardChecks`, `SetupAttemptPaymentMethodDetailsCardPresent`, `SetupAttemptPaymentMethodDetailsCardPresentOffline`, `SetupAttemptPaymentMethodDetailsCardThreeDSecure`, `SetupAttemptPaymentMethodDetailsCardWallet`, `SetupAttemptPaymentMethodDetailsIdeal`, `SetupAttemptPaymentMethodDetailsNaverPay`, `SetupAttemptPaymentMethodDetailsSofort`, `SetupAttemptService`, `SetupIntent`, `SetupIntentAutomaticPaymentMethods`, `SetupIntentAutomaticPaymentMethodsOptions`, `SetupIntentCancelOptions`, `SetupIntentConfirmOptions`, `SetupIntentCreateOptions`, `SetupIntentGetOptions`, `SetupIntentListOptions`, `SetupIntentManagedPayments`, `SetupIntentMandateDataCustomerAcceptanceOnlineOptions`, `SetupIntentMandateDataCustomerAcceptanceOptions`, `SetupIntentMandateDataOptions`, `SetupIntentNextAction`, `SetupIntentNextActionCashappHandleRedirectOrDisplayQrCode`, `SetupIntentNextActionCashappHandleRedirectOrDisplayQrCodeQrCode`, `SetupIntentNextActionPixDisplayQrCode`, `SetupIntentNextActionRedirectToUrl`, `SetupIntentNextActionUpiHandleRedirectOrDisplayQrCode`, `SetupIntentNextActionUpiHandleRedirectOrDisplayQrCodeQrCode`, `SetupIntentNextActionVerifyWithMicrodeposits`, `SetupIntentPaymentMethodConfigurationDetails`, `SetupIntentPaymentMethodDataAcssDebitOptions`, `SetupIntentPaymentMethodDataAuBecsDebitOptions`, `SetupIntentPaymentMethodDataBacsDebitOptions`, `SetupIntentPaymentMethodDataBillingDetailsOptions`, `SetupIntentPaymentMethodDataBoletoOptions`, `SetupIntentPaymentMethodDataEpsOptions`, `SetupIntentPaymentMethodDataFpxOptions`, `SetupIntentPaymentMethodDataIdealOptions`, `SetupIntentPaymentMethodDataKlarnaDobOptions`, `SetupIntentPaymentMethodDataKlarnaOptions`, `SetupIntentPaymentMethodDataNaverPayOptions`, `SetupIntentPaymentMethodDataNzBankAccountOptions`, `SetupIntentPaymentMethodDataOptions`, `SetupIntentPaymentMethodDataP24Options`, `SetupIntentPaymentMethodDataPaytoOptions`, `SetupIntentPaymentMethodDataRadarOptionsOptions`, `SetupIntentPaymentMethodDataSepaDebitOptions`, `SetupIntentPaymentMethodDataSofortOptions`, `SetupIntentPaymentMethodDataUpiMandateOptionsOptions`, `SetupIntentPaymentMethodDataUpiOptions`, `SetupIntentPaymentMethodDataUsBankAccountOptions`, `SetupIntentPaymentMethodOptionsAcssDebit`, `SetupIntentPaymentMethodOptionsAcssDebitMandateOptions`, `SetupIntentPaymentMethodOptionsAcssDebitMandateOptionsOptions`, `SetupIntentPaymentMethodOptionsAcssDebitOptions`, `SetupIntentPaymentMethodOptionsBacsDebitMandateOptions`, `SetupIntentPaymentMethodOptionsBacsDebitMandateOptionsOptions`, `SetupIntentPaymentMethodOptionsBacsDebitOptions`, `SetupIntentPaymentMethodOptionsCard`, `SetupIntentPaymentMethodOptionsCardMandateOptions`, `SetupIntentPaymentMethodOptionsCardMandateOptionsOptions`, `SetupIntentPaymentMethodOptionsCardOptions`, `SetupIntentPaymentMethodOptionsCardThreeDSecureNetworkOptionsCartesBancairesOptions`, `SetupIntentPaymentMethodOptionsCardThreeDSecureNetworkOptionsOptions`, `SetupIntentPaymentMethodOptionsCardThreeDSecureOptions`, `SetupIntentPaymentMethodOptionsKlarna`, `SetupIntentPaymentMethodOptionsKlarnaOnDemandOptions`, `SetupIntentPaymentMethodOptionsKlarnaOptions`, `SetupIntentPaymentMethodOptionsKlarnaSubscriptionNextBillingOptions`, `SetupIntentPaymentMethodOptionsKlarnaSubscriptionOptions`, `SetupIntentPaymentMethodOptionsLink`, `SetupIntentPaymentMethodOptionsLinkOptions`, `SetupIntentPaymentMethodOptionsOptions`, `SetupIntentPaymentMethodOptionsPaypal`, `SetupIntentPaymentMethodOptionsPaypalOptions`, `SetupIntentPaymentMethodOptionsPaytoMandateOptions`, `SetupIntentPaymentMethodOptionsPaytoMandateOptionsOptions`, `SetupIntentPaymentMethodOptionsPaytoOptions`, `SetupIntentPaymentMethodOptionsPixMandateOptions`, `SetupIntentPaymentMethodOptionsPixMandateOptionsOptions`, `SetupIntentPaymentMethodOptionsPixOptions`, `SetupIntentPaymentMethodOptionsSepaDebitMandateOptions`, `SetupIntentPaymentMethodOptionsSepaDebitMandateOptionsOptions`, `SetupIntentPaymentMethodOptionsSepaDebitOptions`, `SetupIntentPaymentMethodOptionsUpiMandateOptions`, `SetupIntentPaymentMethodOptionsUpiMandateOptionsOptions`, `SetupIntentPaymentMethodOptionsUpiOptions`, `SetupIntentPaymentMethodOptionsUsBankAccount`, `SetupIntentPaymentMethodOptionsUsBankAccountFinancialConnections`, `SetupIntentPaymentMethodOptionsUsBankAccountFinancialConnectionsFilters`, `SetupIntentPaymentMethodOptionsUsBankAccountFinancialConnectionsFiltersOptions`, `SetupIntentPaymentMethodOptionsUsBankAccountFinancialConnectionsOptions`, `SetupIntentPaymentMethodOptionsUsBankAccountMandateOptions`, `SetupIntentPaymentMethodOptionsUsBankAccountMandateOptionsOptions`, `SetupIntentPaymentMethodOptionsUsBankAccountNetworksOptions`, `SetupIntentPaymentMethodOptionsUsBankAccountOptions`, `SetupIntentService`, `SetupIntentSingleUseOptions`, `SetupIntentUpdateOptions`, `SetupIntentVerifyMicrodepositsOptions`, `ShippingOptions`, `ShippingRate`, `ShippingRateCreateOptions`, `ShippingRateDeliveryEstimate`, `ShippingRateDeliveryEstimateMaximum`, `ShippingRateDeliveryEstimateMaximumOptions`, `ShippingRateDeliveryEstimateMinimum`, `ShippingRateDeliveryEstimateMinimumOptions`, `ShippingRateDeliveryEstimateOptions`, `ShippingRateFixedAmount`, `ShippingRateFixedAmountCurrencyOptions`, `ShippingRateFixedAmountCurrencyOptionsOptions`, `ShippingRateFixedAmountOptions`, `ShippingRateListOptions`, `ShippingRateService`, `ShippingRateUpdateOptions`, `Source`, `SourceCardOptions`, `SourceCodeVerification`, `SourceGetOptions`, `SourceMandateAcceptanceOfflineOptions`, `SourceMandateAcceptanceOnlineOptions`, `SourceMandateAcceptanceOptions`, `SourceMandateNotification`, `SourceMandateNotificationAcssDebit`, `SourceMandateNotificationBacsDebit`, `SourceMandateNotificationSepaDebit`, `SourceMandateOptions`, `SourceOwner`, `SourceOwnerOptions`, `SourceReceiver`, `SourceReceiverOptions`, `SourceRedirect`, `SourceRedirectOptions`, `SourceSourceOrder`, `SourceSourceOrderItem`, `SourceSourceOrderItemOptions`, `SourceSourceOrderOptions`, `SourceTransaction`, `SourceTransactionAchCreditTransfer`, `SourceTransactionChfCreditTransfer`, `SourceTransactionGbpCreditTransfer`, `SourceTransactionPaperCheck`, `SourceTransactionSepaCreditTransfer`, `SourceTransactionService`, `SourceUpdateOptions`, `SourceVerifyOptions`, `StringEnum`, `StripeClient`, `StripeClientOptions`, `StripeConfiguration`, `StripeContext`, `StripeEntity`, `StripeEntity<T>`, `StripeError`, `StripeList<T>`, `StripeRequest`, `StripeResponse`, `StripeResponseBase`, `StripeSearchResult<T>`, `StripeStreamedResponse`, `StripeTypeRegistry`, `Subscription`, `SubscriptionAddInvoiceItemDiscountOptions`, `SubscriptionAddInvoiceItemOptions`, `SubscriptionAddInvoiceItemPeriodEndOptions`, `SubscriptionAddInvoiceItemPeriodOptions`, `SubscriptionAddInvoiceItemPeriodStartOptions`, `SubscriptionAddInvoiceItemPriceDataOptions`, `SubscriptionAutomaticTax`, `SubscriptionAutomaticTaxLiability`, `SubscriptionAutomaticTaxLiabilityOptions`, `SubscriptionAutomaticTaxOptions`, `SubscriptionBillingCycleAnchor`, `SubscriptionBillingCycleAnchorConfig`, `SubscriptionBillingCycleAnchorConfigOptions`, `SubscriptionBillingMode`, `SubscriptionBillingModeFlexible`, `SubscriptionBillingModeFlexibleOptions`, `SubscriptionBillingModeOptions`, `SubscriptionBillingSchedule`, `SubscriptionBillingScheduleAppliesTo`, `SubscriptionBillingScheduleAppliesToOptions`, `SubscriptionBillingScheduleBillUntil`, `SubscriptionBillingScheduleBillUntilDuration`, `SubscriptionBillingScheduleBillUntilDurationOptions`, `SubscriptionBillingScheduleBillUntilOptions`, `SubscriptionBillingScheduleOptions`, `SubscriptionBillingThresholds`, `SubscriptionBillingThresholdsOptions`, `SubscriptionCancelOptions`, `SubscriptionCancellationDetails`, `SubscriptionCancellationDetailsOptions`, `SubscriptionCreateOptions`, `SubscriptionDiscountOptions`, `SubscriptionInvoiceSettings`, `SubscriptionInvoiceSettingsIssuer`, `SubscriptionInvoiceSettingsIssuerOptions`, `SubscriptionInvoiceSettingsOptions`, `SubscriptionItem`, `SubscriptionItemBillingThresholds`, `SubscriptionItemBillingThresholdsOptions`, `SubscriptionItemCreateOptions`, `SubscriptionItemDeleteOptions`, `SubscriptionItemDiscountOptions`, `SubscriptionItemListOptions`, `SubscriptionItemOptions`, `SubscriptionItemPriceDataOptions`, `SubscriptionItemPriceDataRecurringOptions`, `SubscriptionItemService`, `SubscriptionItemUpdateOptions`, `SubscriptionListOptions`, `SubscriptionManagedPayments`, `SubscriptionMigrateOptions`, `SubscriptionPauseCollection`, `SubscriptionPauseCollectionOptions`, `SubscriptionPaymentSettings`, `SubscriptionPaymentSettingsOptions`, `SubscriptionPaymentSettingsPaymentMethodOptions`, `SubscriptionPaymentSettingsPaymentMethodOptionsAcssDebit`, `SubscriptionPaymentSettingsPaymentMethodOptionsAcssDebitMandateOptions`, `SubscriptionPaymentSettingsPaymentMethodOptionsAcssDebitMandateOptionsOptions`, `SubscriptionPaymentSettingsPaymentMethodOptionsAcssDebitOptions`, `SubscriptionPaymentSettingsPaymentMethodOptionsBancontact`, `SubscriptionPaymentSettingsPaymentMethodOptionsBancontactOptions`, `SubscriptionPaymentSettingsPaymentMethodOptionsCard`, `SubscriptionPaymentSettingsPaymentMethodOptionsCardMandateOptions`, `SubscriptionPaymentSettingsPaymentMethodOptionsCardMandateOptionsOptions`, `SubscriptionPaymentSettingsPaymentMethodOptionsCardOptions`, `SubscriptionPaymentSettingsPaymentMethodOptionsCustomerBalance`, `SubscriptionPaymentSettingsPaymentMethodOptionsCustomerBalanceBankTransfer`, `SubscriptionPaymentSettingsPaymentMethodOptionsCustomerBalanceBankTransferEuBankTransfer`, `SubscriptionPaymentSettingsPaymentMethodOptionsCustomerBalanceBankTransferEuBankTransferOptions`, `SubscriptionPaymentSettingsPaymentMethodOptionsCustomerBalanceBankTransferOptions`, `SubscriptionPaymentSettingsPaymentMethodOptionsCustomerBalanceOptions`, `SubscriptionPaymentSettingsPaymentMethodOptionsOptions`, `SubscriptionPaymentSettingsPaymentMethodOptionsPaytoMandateOptions`, `SubscriptionPaymentSettingsPaymentMethodOptionsPaytoMandateOptionsOptions`, `SubscriptionPaymentSettingsPaymentMethodOptionsPaytoOptions`, `SubscriptionPaymentSettingsPaymentMethodOptionsPix`, `SubscriptionPaymentSettingsPaymentMethodOptionsPixMandateOptions`, `SubscriptionPaymentSettingsPaymentMethodOptionsPixMandateOptionsOptions`, `SubscriptionPaymentSettingsPaymentMethodOptionsPixOptions`, `SubscriptionPaymentSettingsPaymentMethodOptionsUpiMandateOptions`, `SubscriptionPaymentSettingsPaymentMethodOptionsUpiMandateOptionsOptions`, `SubscriptionPaymentSettingsPaymentMethodOptionsUpiOptions`, `SubscriptionPaymentSettingsPaymentMethodOptionsUsBankAccount`, `SubscriptionPaymentSettingsPaymentMethodOptionsUsBankAccountFinancialConnections`, `SubscriptionPaymentSettingsPaymentMethodOptionsUsBankAccountFinancialConnectionsFilters`, `SubscriptionPaymentSettingsPaymentMethodOptionsUsBankAccountFinancialConnectionsFiltersOptions`, `SubscriptionPaymentSettingsPaymentMethodOptionsUsBankAccountFinancialConnectionsOptions`, `SubscriptionPaymentSettingsPaymentMethodOptionsUsBankAccountOptions`, `SubscriptionPendingInvoiceItemInterval`, `SubscriptionPendingInvoiceItemIntervalOptions`, `SubscriptionPendingUpdate`, `SubscriptionPresentmentDetails`, `SubscriptionResumeOptions`, `SubscriptionSchedule`, `SubscriptionScheduleBillingMode`, `SubscriptionScheduleBillingModeFlexible`, `SubscriptionScheduleBillingModeFlexibleOptions`, `SubscriptionScheduleBillingModeOptions`, `SubscriptionScheduleCancelOptions`, `SubscriptionScheduleCreateOptions`, `SubscriptionScheduleCurrentPhase`, `SubscriptionScheduleDefaultSettings`, `SubscriptionScheduleDefaultSettingsAutomaticTax`, `SubscriptionScheduleDefaultSettingsAutomaticTaxLiability`, `SubscriptionScheduleDefaultSettingsAutomaticTaxLiabilityOptions`, `SubscriptionScheduleDefaultSettingsAutomaticTaxOptions`, `SubscriptionScheduleDefaultSettingsBillingThresholds`, `SubscriptionScheduleDefaultSettingsBillingThresholdsOptions`, `SubscriptionScheduleDefaultSettingsInvoiceSettings`, `SubscriptionScheduleDefaultSettingsInvoiceSettingsIssuer`, `SubscriptionScheduleDefaultSettingsInvoiceSettingsIssuerOptions`, `SubscriptionScheduleDefaultSettingsInvoiceSettingsOptions`, `SubscriptionScheduleDefaultSettingsOptions`, `SubscriptionScheduleDefaultSettingsTransferData`, `SubscriptionScheduleDefaultSettingsTransferDataOptions`, `SubscriptionScheduleListOptions`, `SubscriptionSchedulePhase`, `SubscriptionSchedulePhaseAddInvoiceItem`, `SubscriptionSchedulePhaseAddInvoiceItemDiscount`, `SubscriptionSchedulePhaseAddInvoiceItemDiscountOptions`, `SubscriptionSchedulePhaseAddInvoiceItemOptions`, `SubscriptionSchedulePhaseAddInvoiceItemPeriodEnd`, `SubscriptionSchedulePhaseAddInvoiceItemPeriodEndOptions`, `SubscriptionSchedulePhaseAddInvoiceItemPeriodOptions`, `SubscriptionSchedulePhaseAddInvoiceItemPeriodStart`, `SubscriptionSchedulePhaseAddInvoiceItemPeriodStartOptions`, `SubscriptionSchedulePhaseAddInvoiceItemPriceDataOptions`, `SubscriptionSchedulePhaseAutomaticTax`, `SubscriptionSchedulePhaseAutomaticTaxLiability`, `SubscriptionSchedulePhaseAutomaticTaxLiabilityOptions`, `SubscriptionSchedulePhaseAutomaticTaxOptions`, `SubscriptionSchedulePhaseBillingThresholds`, `SubscriptionSchedulePhaseBillingThresholdsOptions`, `SubscriptionSchedulePhaseDiscount`, `SubscriptionSchedulePhaseDiscountOptions`, `SubscriptionSchedulePhaseDurationOptions`, `SubscriptionSchedulePhaseInvoiceSettings`, `SubscriptionSchedulePhaseInvoiceSettingsIssuer`, `SubscriptionSchedulePhaseInvoiceSettingsIssuerOptions`, `SubscriptionSchedulePhaseInvoiceSettingsOptions`, `SubscriptionSchedulePhaseItem`, `SubscriptionSchedulePhaseItemBillingThresholds`, `SubscriptionSchedulePhaseItemBillingThresholdsOptions`, `SubscriptionSchedulePhaseItemDiscount`, `SubscriptionSchedulePhaseItemDiscountOptions`, `SubscriptionSchedulePhaseItemOptions`, `SubscriptionSchedulePhaseItemPriceDataOptions`, `SubscriptionSchedulePhaseItemPriceDataRecurringOptions`, `SubscriptionSchedulePhaseOptions`, `SubscriptionSchedulePhasePlanPriceDataRecurringOptions`, `SubscriptionSchedulePhaseTransferData`, `SubscriptionSchedulePhaseTransferDataOptions`, `SubscriptionScheduleReleaseOptions`, `SubscriptionScheduleService`, `SubscriptionScheduleUpdateOptions`, `SubscriptionService`, `SubscriptionTransferData`, `SubscriptionTransferDataOptions`, `SubscriptionTrialSettings`, `SubscriptionTrialSettingsEndBehavior`, `SubscriptionTrialSettingsEndBehaviorOptions`, `SubscriptionTrialSettingsOptions`, `SubscriptionUpdateOptions`, `SystemNetHttpClient`, `TaxCode`, `TaxCodeService`, `TaxDeductedAtSource`, `TaxId`, `TaxIdCreateOptions`, `TaxIdListOptions`, `TaxIdOwner`, `TaxIdOwnerOptions`, `TaxIdService`, `TaxIdVerification`, `TaxRate`, `TaxRateCreateOptions`, `TaxRateFlatAmount`, `TaxRateListOptions`, `TaxRateService`, `TaxRateUpdateOptions`, `Token`, `TokenAccountCompanyDirectorshipDeclarationOptions`, `TokenAccountCompanyOptions`, `TokenAccountCompanyOwnershipDeclarationOptions`, `TokenAccountCompanyRegistrationDateOptions`, `TokenAccountCompanyRepresentativeDeclarationOptions`, `TokenAccountCompanyVerificationDocumentOptions`, `TokenAccountCompanyVerificationOptions`, `TokenAccountIndividualOptions`, `TokenAccountIndividualRelationshipOptions`, `TokenAccountIndividualVerificationAdditionalDocumentOptions`, `TokenAccountIndividualVerificationDocumentOptions`, `TokenAccountIndividualVerificationOptions`, `TokenAccountOptions`, `TokenBankAccountOptions`, `TokenCardNetworksOptions`, `TokenCardOptions`, `TokenCreateOptions`, `TokenCvcUpdateOptions`, `TokenPersonAdditionalTosAcceptancesAccountOptions`, `TokenPersonAdditionalTosAcceptancesOptions`, `TokenPersonDocumentsCompanyAuthorizationOptions`, `TokenPersonDocumentsOptions`, `TokenPersonDocumentsPassportOptions`, `TokenPersonDocumentsVisaOptions`, `TokenPersonOptions`, `TokenPersonRelationshipOptions`, `TokenPersonUsCfpbDataEthnicityDetailsOptions`, `TokenPersonUsCfpbDataOptions`, `TokenPersonUsCfpbDataRaceDetailsOptions`, `TokenPersonVerificationAdditionalDocumentOptions`, `TokenPersonVerificationDocumentOptions`, `TokenPersonVerificationOptions`, `TokenPiiOptions`, `TokenService`, `Topup`, `TopupCreateOptions`, `TopupListOptions`, `TopupService`, `TopupUpdateOptions`, `Transfer`, `TransferCreateOptions`, `TransferListOptions`, `TransferMethod`, `TransferReversal`, `TransferReversalCreateOptions`, `TransferReversalService`, `TransferReversalUpdateOptions`, `TransferService`, `TransferUpdateOptions`, `UpcomingInvoiceSubscriptionResumeAt`, `WebhookEndpoint`, `WebhookEndpointCreateOptions`, `WebhookEndpointService`, `WebhookEndpointUpdateOptions`
- **Stripe.Apps**: `Secret`, `SecretCreateOptions`, `SecretDeleteWhereOptions`, `SecretFindOptions`, `SecretListOptions`, `SecretScope`, `SecretScopeOptions`, `SecretService`
- **Stripe.Billing**: `Alert`, `AlertCreateOptions`, `AlertListOptions`, `AlertService`, `AlertTriggered`, `AlertUsageThreshold`, `AlertUsageThresholdFilter`, `AlertUsageThresholdFilterOptions`, `AlertUsageThresholdOptions`, `CreditBalanceSummary`, `CreditBalanceSummaryBalanceAvailableBalance`, `CreditBalanceSummaryBalanceAvailableBalanceMonetary`, `CreditBalanceSummaryBalanceLedgerBalance`, `CreditBalanceSummaryBalanceLedgerBalanceMonetary`, `CreditBalanceSummaryFilterApplicabilityScopeOptions`, `CreditBalanceSummaryFilterApplicabilityScopePriceOptions`, `CreditBalanceSummaryFilterOptions`, `CreditBalanceSummaryGetOptions`, `CreditBalanceSummaryService`, `CreditBalanceTransaction`, `CreditBalanceTransactionCredit`, `CreditBalanceTransactionCreditAmount`, `CreditBalanceTransactionCreditAmountMonetary`, `CreditBalanceTransactionCreditCreditsApplicationInvoiceVoided`, `CreditBalanceTransactionDebit`, `CreditBalanceTransactionDebitAmount`, `CreditBalanceTransactionDebitAmountMonetary`, `CreditBalanceTransactionDebitCreditsApplied`, `CreditBalanceTransactionListOptions`, `CreditBalanceTransactionService`, `CreditGrant`, `CreditGrantAmount`, `CreditGrantAmountMonetary`, `CreditGrantAmountMonetaryOptions`, `CreditGrantAmountOptions`, `CreditGrantApplicabilityConfigOptions`, `CreditGrantApplicabilityConfigScope`, `CreditGrantApplicabilityConfigScopeOptions`, `CreditGrantApplicabilityConfigScopePrice`, `CreditGrantApplicabilityConfigScopePriceOptions`, `CreditGrantCreateOptions`, `CreditGrantListOptions`, `CreditGrantService`, `CreditGrantUpdateOptions`, `Meter`, `MeterCreateOptions`, `MeterCustomerMapping`, `MeterCustomerMappingOptions`, `MeterDefaultAggregation`, `MeterDefaultAggregationOptions`, `MeterEvent`, `MeterEventAdjustment`, `MeterEventAdjustmentCancel`, `MeterEventAdjustmentCancelOptions`, `MeterEventAdjustmentCreateOptions`, `MeterEventAdjustmentService`, `MeterEventCreateOptions`, `MeterEventService`, `MeterEventSummary`, `MeterEventSummaryListOptions`, `MeterEventSummaryService`, `MeterListOptions`, `MeterService`, `MeterStatusTransitions`, `MeterUpdateOptions`, `MeterValueSettings`, `MeterValueSettingsOptions`
- **Stripe.BillingPortal**: `Configuration`, `ConfigurationBusinessProfile`, `ConfigurationBusinessProfileOptions`, `ConfigurationCreateOptions`, `ConfigurationFeaturesCustomerUpdate`, `ConfigurationFeaturesCustomerUpdateOptions`, `ConfigurationFeaturesInvoiceHistory`, `ConfigurationFeaturesInvoiceHistoryOptions`, `ConfigurationFeaturesOptions`, `ConfigurationFeaturesPaymentMethodUpdate`, `ConfigurationFeaturesPaymentMethodUpdateOptions`, `ConfigurationFeaturesSubscriptionCancel`, `ConfigurationFeaturesSubscriptionCancelCancellationReason`, `ConfigurationFeaturesSubscriptionCancelCancellationReasonOptions`, `ConfigurationFeaturesSubscriptionCancelOptions`, `ConfigurationFeaturesSubscriptionUpdate`, `ConfigurationFeaturesSubscriptionUpdateOptions`, `ConfigurationFeaturesSubscriptionUpdateProduct`, `ConfigurationFeaturesSubscriptionUpdateProductAdjustableQuantity`, `ConfigurationFeaturesSubscriptionUpdateProductAdjustableQuantityOptions`, `ConfigurationFeaturesSubscriptionUpdateProductOptions`, `ConfigurationFeaturesSubscriptionUpdateScheduleAtPeriodEnd`, `ConfigurationFeaturesSubscriptionUpdateScheduleAtPeriodEndCondition`, `ConfigurationFeaturesSubscriptionUpdateScheduleAtPeriodEndConditionOptions`, `ConfigurationFeaturesSubscriptionUpdateScheduleAtPeriodEndOptions`, `ConfigurationListOptions`, `ConfigurationLoginPage`, `ConfigurationLoginPageOptions`, `ConfigurationService`, `ConfigurationUpdateOptions`, `Session`, `SessionCreateOptions`, `SessionFlow`, `SessionFlowAfterCompletion`, `SessionFlowAfterCompletionHostedConfirmation`, `SessionFlowAfterCompletionRedirect`, `SessionFlowDataAfterCompletionHostedConfirmationOptions`, `SessionFlowDataAfterCompletionOptions`, `SessionFlowDataAfterCompletionRedirectOptions`, `SessionFlowDataOptions`, `SessionFlowDataSubscriptionCancelOptions`, `SessionFlowDataSubscriptionCancelRetentionCouponOfferOptions`, `SessionFlowDataSubscriptionCancelRetentionOptions`, `SessionFlowDataSubscriptionUpdateConfirmDiscountOptions`, `SessionFlowDataSubscriptionUpdateConfirmItemOptions`, `SessionFlowDataSubscriptionUpdateConfirmOptions`, `SessionFlowDataSubscriptionUpdateOptions`, `SessionFlowSubscriptionCancel`, `SessionFlowSubscriptionCancelRetention`, `SessionFlowSubscriptionCancelRetentionCouponOffer`, `SessionFlowSubscriptionUpdate`, `SessionFlowSubscriptionUpdateConfirm`, `SessionFlowSubscriptionUpdateConfirmDiscount`, `SessionFlowSubscriptionUpdateConfirmItem`, `SessionService`
- **Stripe.Checkout**: `Session`, `SessionAdaptivePricing`, `SessionAdaptivePricingOptions`, `SessionAfterExpiration`, `SessionAfterExpirationOptions`, `SessionAfterExpirationRecovery`, `SessionAfterExpirationRecoveryOptions`, `SessionAutomaticTax`, `SessionAutomaticTaxLiability`, `SessionAutomaticTaxLiabilityOptions`, `SessionAutomaticTaxOptions`, `SessionBrandingSettings`, `SessionBrandingSettingsIcon`, `SessionBrandingSettingsIconOptions`, `SessionBrandingSettingsLogo`, `SessionBrandingSettingsLogoOptions`, `SessionBrandingSettingsOptions`, `SessionCollectedInformation`, `SessionCollectedInformationOptions`, `SessionCollectedInformationShippingDetails`, `SessionCollectedInformationShippingDetailsOptions`, `SessionConsent`, `SessionConsentCollection`, `SessionConsentCollectionOptions`, `SessionConsentCollectionPaymentMethodReuseAgreement`, `SessionConsentCollectionPaymentMethodReuseAgreementOptions`, `SessionCreateOptions`, `SessionCurrencyConversion`, `SessionCustomField`, `SessionCustomFieldDropdown`, `SessionCustomFieldDropdownOption`, `SessionCustomFieldDropdownOptionOptions`, `SessionCustomFieldDropdownOptions`, `SessionCustomFieldLabel`, `SessionCustomFieldLabelOptions`, `SessionCustomFieldNumeric`, `SessionCustomFieldNumericOptions`, `SessionCustomFieldOptions`, `SessionCustomFieldText`, `SessionCustomFieldTextOptions`, `SessionCustomText`, `SessionCustomTextAfterSubmit`, `SessionCustomTextAfterSubmitOptions`, `SessionCustomTextOptions`, `SessionCustomTextShippingAddress`, `SessionCustomTextShippingAddressOptions`, `SessionCustomTextSubmit`, `SessionCustomTextSubmitOptions`, `SessionCustomTextTermsOfServiceAcceptance`, `SessionCustomTextTermsOfServiceAcceptanceOptions`, `SessionCustomerDetails`, `SessionCustomerDetailsOptions`, `SessionCustomerDetailsTaxId`, `SessionCustomerUpdateOptions`, `SessionDiscount`, `SessionDiscountOptions`, `SessionInvoiceCreation`, `SessionInvoiceCreationInvoiceData`, `SessionInvoiceCreationInvoiceDataCustomField`, `SessionInvoiceCreationInvoiceDataCustomFieldOptions`, `SessionInvoiceCreationInvoiceDataIssuer`, `SessionInvoiceCreationInvoiceDataIssuerOptions`, `SessionInvoiceCreationInvoiceDataOptions`, `SessionInvoiceCreationInvoiceDataRenderingOptions`, `SessionInvoiceCreationInvoiceDataRenderingOptionsOptions`, `SessionInvoiceCreationOptions`, `SessionLineItemAdjustableQuantityOptions`, `SessionLineItemOptions`, `SessionLineItemPriceDataOptions`, `SessionLineItemPriceDataProductDataOptions`, `SessionLineItemPriceDataRecurringOptions`, `SessionLineItemService`, `SessionListOptions`, `SessionManagedPayments`, `SessionManagedPaymentsOptions`, `SessionNameCollectionBusiness`, `SessionNameCollectionBusinessOptions`, `SessionNameCollectionIndividual`, `SessionNameCollectionIndividualOptions`, `SessionNameCollectionOptions`, `SessionOptionalItemAdjustableQuantity`, `SessionOptionalItemAdjustableQuantityOptions`, `SessionOptionalItemOptions`, `SessionPaymentIntentDataOptions`, `SessionPaymentIntentDataTransferDataOptions`, `SessionPaymentMethodConfigurationDetails`, `SessionPaymentMethodDataOptions`, `SessionPaymentMethodOptionsAcssDebit`, `SessionPaymentMethodOptionsAcssDebitMandateOptions`, `SessionPaymentMethodOptionsAcssDebitMandateOptionsOptions`, `SessionPaymentMethodOptionsAcssDebitOptions`, `SessionPaymentMethodOptionsAffirm`, `SessionPaymentMethodOptionsAffirmOptions`, `SessionPaymentMethodOptionsAfterpayClearpay`, `SessionPaymentMethodOptionsAfterpayClearpayOptions`, `SessionPaymentMethodOptionsAlipay`, `SessionPaymentMethodOptionsAlipayOptions`, `SessionPaymentMethodOptionsAlma`, `SessionPaymentMethodOptionsAlmaOptions`, `SessionPaymentMethodOptionsAmazonPay`, `SessionPaymentMethodOptionsAmazonPayOptions`, `SessionPaymentMethodOptionsAuBecsDebit`, `SessionPaymentMethodOptionsAuBecsDebitOptions`, `SessionPaymentMethodOptionsBacsDebit`, `SessionPaymentMethodOptionsBacsDebitMandateOptions`, `SessionPaymentMethodOptionsBacsDebitMandateOptionsOptions`, `SessionPaymentMethodOptionsBacsDebitOptions`, `SessionPaymentMethodOptionsBancontact`, `SessionPaymentMethodOptionsBancontactOptions`, `SessionPaymentMethodOptionsBillie`, `SessionPaymentMethodOptionsBillieOptions`, `SessionPaymentMethodOptionsBoleto`, `SessionPaymentMethodOptionsBoletoOptions`, `SessionPaymentMethodOptionsCard`, `SessionPaymentMethodOptionsCardInstallments`, `SessionPaymentMethodOptionsCardInstallmentsOptions`, `SessionPaymentMethodOptionsCardOptions`, `SessionPaymentMethodOptionsCardRestrictions`, `SessionPaymentMethodOptionsCardRestrictionsOptions`, `SessionPaymentMethodOptionsCashapp`, `SessionPaymentMethodOptionsCashappOptions`, `SessionPaymentMethodOptionsCryptoOptions`, `SessionPaymentMethodOptionsCustomerBalance`, `SessionPaymentMethodOptionsCustomerBalanceBankTransfer`, `SessionPaymentMethodOptionsCustomerBalanceBankTransferEuBankTransfer`, `SessionPaymentMethodOptionsCustomerBalanceBankTransferEuBankTransferOptions`, `SessionPaymentMethodOptionsCustomerBalanceBankTransferOptions`, `SessionPaymentMethodOptionsCustomerBalanceOptions`, `SessionPaymentMethodOptionsDemoPayOptions`, `SessionPaymentMethodOptionsEps`, `SessionPaymentMethodOptionsEpsOptions`, `SessionPaymentMethodOptionsFpx`, `SessionPaymentMethodOptionsFpxOptions`, `SessionPaymentMethodOptionsGiropay`, `SessionPaymentMethodOptionsGiropayOptions`, `SessionPaymentMethodOptionsGrabpay`, `SessionPaymentMethodOptionsGrabpayOptions`, `SessionPaymentMethodOptionsIdeal`, `SessionPaymentMethodOptionsIdealOptions`, `SessionPaymentMethodOptionsKakaoPay`, `SessionPaymentMethodOptionsKakaoPayOptions`, `SessionPaymentMethodOptionsKlarna`, `SessionPaymentMethodOptionsKlarnaOptions`, `SessionPaymentMethodOptionsKlarnaSubscriptionNextBillingOptions`, `SessionPaymentMethodOptionsKlarnaSubscriptionOptions`, `SessionPaymentMethodOptionsKonbini`, `SessionPaymentMethodOptionsKonbiniOptions`, `SessionPaymentMethodOptionsKrCard`, `SessionPaymentMethodOptionsKrCardOptions`, `SessionPaymentMethodOptionsLink`, `SessionPaymentMethodOptionsLinkOptions`, `SessionPaymentMethodOptionsMobilepay`, `SessionPaymentMethodOptionsMobilepayOptions`, `SessionPaymentMethodOptionsMultibanco`, `SessionPaymentMethodOptionsMultibancoOptions`, `SessionPaymentMethodOptionsNaverPay`, `SessionPaymentMethodOptionsNaverPayOptions`, `SessionPaymentMethodOptionsOptions`, `SessionPaymentMethodOptionsOxxo`, `SessionPaymentMethodOptionsOxxoOptions`, `SessionPaymentMethodOptionsP24`, `SessionPaymentMethodOptionsP24Options`, `SessionPaymentMethodOptionsPayco`, `SessionPaymentMethodOptionsPaycoOptions`, `SessionPaymentMethodOptionsPaynow`, `SessionPaymentMethodOptionsPaynowOptions`, `SessionPaymentMethodOptionsPaypal`, `SessionPaymentMethodOptionsPaypalOptions`, `SessionPaymentMethodOptionsPayto`, `SessionPaymentMethodOptionsPaytoMandateOptions`, `SessionPaymentMethodOptionsPaytoMandateOptionsOptions`, `SessionPaymentMethodOptionsPaytoOptions`, `SessionPaymentMethodOptionsPix`, `SessionPaymentMethodOptionsPixMandateOptions`, `SessionPaymentMethodOptionsPixMandateOptionsOptions`, `SessionPaymentMethodOptionsPixOptions`, `SessionPaymentMethodOptionsRevolutPay`, `SessionPaymentMethodOptionsRevolutPayOptions`, `SessionPaymentMethodOptionsSamsungPay`, `SessionPaymentMethodOptionsSamsungPayOptions`, `SessionPaymentMethodOptionsSatispay`, `SessionPaymentMethodOptionsSatispayOptions`, `SessionPaymentMethodOptionsScalapay`, `SessionPaymentMethodOptionsScalapayOptions`, `SessionPaymentMethodOptionsSepaDebit`, `SessionPaymentMethodOptionsSepaDebitMandateOptions`, `SessionPaymentMethodOptionsSepaDebitMandateOptionsOptions`, `SessionPaymentMethodOptionsSepaDebitOptions`, `SessionPaymentMethodOptionsSofort`, `SessionPaymentMethodOptionsSofortOptions`, `SessionPaymentMethodOptionsSwish`, `SessionPaymentMethodOptionsSwishOptions`, `SessionPaymentMethodOptionsTwint`, `SessionPaymentMethodOptionsTwintOptions`, `SessionPaymentMethodOptionsUpi`, `SessionPaymentMethodOptionsUpiMandateOptions`, `SessionPaymentMethodOptionsUpiMandateOptionsOptions`, `SessionPaymentMethodOptionsUpiOptions`, `SessionPaymentMethodOptionsUsBankAccount`, `SessionPaymentMethodOptionsUsBankAccountFinancialConnections`, `SessionPaymentMethodOptionsUsBankAccountFinancialConnectionsFilters`, `SessionPaymentMethodOptionsUsBankAccountFinancialConnectionsOptions`, `SessionPaymentMethodOptionsUsBankAccountOptions`, `SessionPaymentMethodOptionsWechatPayOptions`, `SessionPermissions`, `SessionPermissionsOptions`, `SessionPhoneNumberCollection`, `SessionPhoneNumberCollectionOptions`, `SessionPresentmentDetails`, `SessionSavedPaymentMethodOptions`, `SessionSavedPaymentMethodOptionsOptions`, `SessionService`, `SessionSetupIntentDataOptions`, `SessionShippingAddressCollection`, `SessionShippingAddressCollectionOptions`, `SessionShippingCost`, `SessionShippingCostTax`, `SessionShippingOption`, `SessionShippingOptionOptions`, `SessionShippingOptionShippingRateDataDeliveryEstimateMaximumOptions`, `SessionShippingOptionShippingRateDataDeliveryEstimateMinimumOptions`, `SessionShippingOptionShippingRateDataDeliveryEstimateOptions`, `SessionShippingOptionShippingRateDataFixedAmountCurrencyOptionsOptions`, `SessionShippingOptionShippingRateDataFixedAmountOptions`, `SessionShippingOptionShippingRateDataOptions`, `SessionSubscriptionDataBillingModeFlexibleOptions`, `SessionSubscriptionDataBillingModeOptions`, `SessionSubscriptionDataInvoiceSettingsIssuerOptions`, `SessionSubscriptionDataInvoiceSettingsOptions`, `SessionSubscriptionDataOptions`, `SessionSubscriptionDataPendingInvoiceItemIntervalOptions`, `SessionSubscriptionDataTransferDataOptions`, `SessionSubscriptionDataTrialSettingsEndBehaviorOptions`, `SessionSubscriptionDataTrialSettingsOptions`, `SessionTaxIdCollection`, `SessionTaxIdCollectionOptions`, `SessionTotalDetails`, `SessionTotalDetailsBreakdown`, `SessionTotalDetailsBreakdownDiscount`, `SessionTotalDetailsBreakdownTax`, `SessionUpdateOptions`, `SessionWalletOptionsLink`, `SessionWalletOptionsLinkOptions`, `SessionWalletOptionsOptions`
- **Stripe.Climate**: `Order`, `OrderBeneficiary`, `OrderBeneficiaryOptions`, `OrderCreateOptions`, `OrderDeliveryDetail`, `OrderDeliveryDetailLocation`, `OrderService`, `OrderUpdateOptions`, `Product`, `ProductCurrentPricesPerMetricTon`, `ProductService`, `Supplier`, `SupplierLocation`, `SupplierService`
- **Stripe.Entitlements**: `ActiveEntitlement`, `ActiveEntitlementListOptions`, `ActiveEntitlementService`, `ActiveEntitlementSummary`, `Feature`, `FeatureCreateOptions`, `FeatureListOptions`, `FeatureService`, `FeatureUpdateOptions`
- **Stripe.Events**: `UnknownEventNotification`, `V1BillingMeterErrorReportTriggeredEvent`, `V1BillingMeterErrorReportTriggeredEventData`, `V1BillingMeterErrorReportTriggeredEventDataReason`, `V1BillingMeterErrorReportTriggeredEventDataReasonErrorType`, `V1BillingMeterErrorReportTriggeredEventDataReasonErrorTypeSampleError`, `V1BillingMeterErrorReportTriggeredEventDataReasonErrorTypeSampleErrorRequest`, `V1BillingMeterErrorReportTriggeredEventNotification`, `V1BillingMeterNoMeterFoundEvent`, `V1BillingMeterNoMeterFoundEventData`, `V1BillingMeterNoMeterFoundEventDataReason`, `V1BillingMeterNoMeterFoundEventDataReasonErrorType`, `V1BillingMeterNoMeterFoundEventDataReasonErrorTypeSampleError`, `V1BillingMeterNoMeterFoundEventDataReasonErrorTypeSampleErrorRequest`, `V1BillingMeterNoMeterFoundEventNotification`, `V2CommerceProductCatalogImportsFailedEvent`, `V2CommerceProductCatalogImportsFailedEventNotification`, `V2CommerceProductCatalogImportsProcessingEvent`, `V2CommerceProductCatalogImportsProcessingEventNotification`, `V2CommerceProductCatalogImportsSucceededEvent`, `V2CommerceProductCatalogImportsSucceededEventNotification`, `V2CommerceProductCatalogImportsSucceededWithErrorsEvent`, `V2CommerceProductCatalogImportsSucceededWithErrorsEventNotification`, `V2CoreAccountClosedEvent`, `V2CoreAccountClosedEventNotification`, `V2CoreAccountCreatedEvent`, `V2CoreAccountCreatedEventNotification`, `V2CoreAccountIncludingConfigurationCustomerCapabilityStatusUpdatedEvent`, `V2CoreAccountIncludingConfigurationCustomerCapabilityStatusUpdatedEventData`, `V2CoreAccountIncludingConfigurationCustomerCapabilityStatusUpdatedEventNotification`, `V2CoreAccountIncludingConfigurationCustomerUpdatedEvent`, `V2CoreAccountIncludingConfigurationCustomerUpdatedEventNotification`, `V2CoreAccountIncludingConfigurationMerchantCapabilityStatusUpdatedEvent`, `V2CoreAccountIncludingConfigurationMerchantCapabilityStatusUpdatedEventData`, `V2CoreAccountIncludingConfigurationMerchantCapabilityStatusUpdatedEventNotification`, `V2CoreAccountIncludingConfigurationMerchantUpdatedEvent`, `V2CoreAccountIncludingConfigurationMerchantUpdatedEventNotification`, `V2CoreAccountIncludingConfigurationRecipientCapabilityStatusUpdatedEvent`, `V2CoreAccountIncludingConfigurationRecipientCapabilityStatusUpdatedEventData`, `V2CoreAccountIncludingConfigurationRecipientCapabilityStatusUpdatedEventNotification`, `V2CoreAccountIncludingConfigurationRecipientUpdatedEvent`, `V2CoreAccountIncludingConfigurationRecipientUpdatedEventNotification`, `V2CoreAccountIncludingDefaultsUpdatedEvent`, `V2CoreAccountIncludingDefaultsUpdatedEventNotification`, `V2CoreAccountIncludingFutureRequirementsUpdatedEvent`, `V2CoreAccountIncludingFutureRequirementsUpdatedEventNotification`, `V2CoreAccountIncludingIdentityUpdatedEvent`, `V2CoreAccountIncludingIdentityUpdatedEventNotification`, `V2CoreAccountIncludingRequirementsUpdatedEvent`, `V2CoreAccountIncludingRequirementsUpdatedEventNotification`, `V2CoreAccountLinkReturnedEvent`, `V2CoreAccountLinkReturnedEventData`, `V2CoreAccountLinkReturnedEventNotification`, `V2CoreAccountPersonCreatedEvent`, `V2CoreAccountPersonCreatedEventData`, `V2CoreAccountPersonCreatedEventNotification`, `V2CoreAccountPersonDeletedEvent`, `V2CoreAccountPersonDeletedEventData`, `V2CoreAccountPersonDeletedEventNotification`, `V2CoreAccountPersonUpdatedEvent`, `V2CoreAccountPersonUpdatedEventData`, `V2CoreAccountPersonUpdatedEventNotification`, `V2CoreAccountUpdatedEvent`, `V2CoreAccountUpdatedEventNotification`, `V2CoreEventDestinationPingEvent`, `V2CoreEventDestinationPingEventNotification`
- **Stripe.FinancialConnections**: `Account`, `AccountAccountHolder`, `AccountAccountHolderOptions`, `AccountAccountNumber`, `AccountBalance`, `AccountBalanceCash`, `AccountBalanceCredit`, `AccountBalanceRefresh`, `AccountListOptions`, `AccountOwner`, `AccountOwnerListOptions`, `AccountOwnerService`, `AccountOwnership`, `AccountOwnershipRefresh`, `AccountRefreshOptions`, `AccountService`, `AccountSubscribeOptions`, `AccountTransactionRefresh`, `AccountUnsubscribeOptions`, `Session`, `SessionAccountHolder`, `SessionAccountHolderOptions`, `SessionCreateOptions`, `SessionFilters`, `SessionFiltersOptions`, `SessionService`, `Transaction`, `TransactionListOptions`, `TransactionService`, `TransactionStatusTransitions`, `TransactionTransactionRefreshOptions`
- **Stripe.Forwarding**: `Request`, `RequestCreateOptions`, `RequestCreatedOptions`, `RequestListOptions`, `RequestRequestContext`, `RequestRequestDetails`, `RequestRequestDetailsHeader`, `RequestRequestHeaderOptions`, `RequestRequestOptions`, `RequestResponseDetails`, `RequestResponseDetailsHeader`, `RequestService`
- **Stripe.Identity**: `VerificationReport`, `VerificationReportDocument`, `VerificationReportDocumentDob`, `VerificationReportDocumentError`, `VerificationReportDocumentExpirationDate`, `VerificationReportDocumentIssuedDate`, `VerificationReportEmail`, `VerificationReportEmailError`, `VerificationReportIdNumber`, `VerificationReportIdNumberDob`, `VerificationReportIdNumberError`, `VerificationReportListOptions`, `VerificationReportOptionsDocument`, `VerificationReportPhone`, `VerificationReportPhoneError`, `VerificationReportSelfie`, `VerificationReportSelfieError`, `VerificationReportService`, `VerificationSession`, `VerificationSessionCreateOptions`, `VerificationSessionLastError`, `VerificationSessionListOptions`, `VerificationSessionOptionsDocument`, `VerificationSessionOptionsDocumentOptions`, `VerificationSessionOptionsEmail`, `VerificationSessionOptionsMatching`, `VerificationSessionOptionsOptions`, `VerificationSessionOptionsPhone`, `VerificationSessionProvidedDetails`, `VerificationSessionProvidedDetailsOptions`, `VerificationSessionRedaction`, `VerificationSessionRelatedPerson`, `VerificationSessionRelatedPersonOptions`, `VerificationSessionService`, `VerificationSessionUpdateOptions`, `VerificationSessionVerifiedOutputs`, `VerificationSessionVerifiedOutputsDob`
- **Stripe.Infrastructure**: `AllowNameMismatch`, `AnyOfConverter`, `AsyncUtils`, `DecimalStringConverter`, `DeserializationContext`, `EventConverter`, `ExpandableFieldConverter<T>`, `IHasSetTracking`, `Int64StringConverter`, `JsonUtils`, `NewtonsoftStringEnumConverter`, `RuntimeInformation`, `STJAnyOfConverter`, `STJDefaultConverter<T>`, `STJEnumerableObjectConverter`, `STJEventConverter`, `STJEventDataConverter`, `STJExpandableFieldConverter<T>`, `STJExpandableFieldConverterFactory`, `STJNullPreservingDictionaryConverter`, `STJStringEnumConverterFactory`, `STJStripeEntityConverter`, `STJStripeObjectConverter`, `STJStripeOptionsConverter`, `STJUnixDateTimeConverter`, `STJV2EventConverter`, `STJV2EventNotificationConverter`, `SerializablePropertyCache`, `SetTracker`, `StringUtils`, `StripeEntityConverter`, `StripeObjectConverter`, `UnixDateTimeConverter`, `V2EventConverter`, `V2EventNotificationConverter`
- **Stripe.Infrastructure.FormEncoding**: `ArrayEncoding`, `ContentEncoder`, `FormEncoder`, `FormUrlEncodedContent`, `JsonEncodedContent`, `MimeTypes`, `MultipartFormDataContent`
- **Stripe.Infrastructure.STJEnumerableObjectConverter**: `STJEnumerableObjectConverterInner<T>`
- **Stripe.Infrastructure.STJStripeObjectConverter**: `STJStripeObjectConverterInner<T>`
- **Stripe.Infrastructure.STJUnixDateTimeConverter**: `DateTimeConverterInner`, `NullableDateTimeConverterInner`
- **Stripe.Infrastructure.SerializablePropertyCache**: `ExtensionDataInfo`, `SerializablePropertyInfo`
- **Stripe.Issuing**: `Authorization`, `AuthorizationAmountDetails`, `AuthorizationApproveOptions`, `AuthorizationDeclineOptions`, `AuthorizationFleet`, `AuthorizationFleetCardholderPromptData`, `AuthorizationFleetReportedBreakdown`, `AuthorizationFleetReportedBreakdownFuel`, `AuthorizationFleetReportedBreakdownNonFuel`, `AuthorizationFleetReportedBreakdownTax`, `AuthorizationFraudChallenge`, `AuthorizationFuel`, `AuthorizationListOptions`, `AuthorizationMerchantData`, `AuthorizationNetworkData`, `AuthorizationPendingRequest`, `AuthorizationPendingRequestAmountDetails`, `AuthorizationRequestHistory`, `AuthorizationRequestHistoryAmountDetails`, `AuthorizationService`, `AuthorizationTreasury`, `AuthorizationUpdateOptions`, `AuthorizationVerificationData`, `AuthorizationVerificationDataAuthenticationExemption`, `AuthorizationVerificationDataThreeDSecure`, `Card`, `CardCreateOptions`, `CardLatestFraudWarning`, `CardLifecycleControlsCancelAfter`, `CardLifecycleControlsCancelAfterOptions`, `CardLifecycleControlsOptions`, `CardListOptions`, `CardPinOptions`, `CardService`, `CardShipping`, `CardShippingAddressValidation`, `CardShippingAddressValidationOptions`, `CardShippingCustoms`, `CardShippingCustomsOptions`, `CardShippingOptions`, `CardSpendingControls`, `CardSpendingControlsOptions`, `CardSpendingControlsSpendingLimit`, `CardSpendingControlsSpendingLimitOptions`, `CardUpdateOptions`, `CardWallets`, `CardWalletsApplePay`, `CardWalletsGooglePay`, `Cardholder`, `CardholderBillingOptions`, `CardholderCompany`, `CardholderCompanyOptions`, `CardholderCreateOptions`, `CardholderIndividual`, `CardholderIndividualCardIssuing`, `CardholderIndividualCardIssuingOptions`, `CardholderIndividualCardIssuingUserTermsAcceptance`, `CardholderIndividualCardIssuingUserTermsAcceptanceOptions`, `CardholderIndividualDob`, `CardholderIndividualDobOptions`, `CardholderIndividualOptions`, `CardholderIndividualVerification`, `CardholderIndividualVerificationDocument`, `CardholderIndividualVerificationDocumentOptions`, `CardholderIndividualVerificationOptions`, `CardholderListOptions`, `CardholderRequirements`, `CardholderService`, `CardholderSpendingControls`, `CardholderSpendingControlsOptions`, `CardholderSpendingControlsSpendingLimit`, `CardholderSpendingControlsSpendingLimitOptions`, `CardholderUpdateOptions`, `Dispute`, `DisputeCreateOptions`, `DisputeEvidence`, `DisputeEvidenceCanceled`, `DisputeEvidenceCanceledOptions`, `DisputeEvidenceDuplicate`, `DisputeEvidenceDuplicateOptions`, `DisputeEvidenceFraudulent`, `DisputeEvidenceFraudulentOptions`, `DisputeEvidenceMerchandiseNotAsDescribed`, `DisputeEvidenceMerchandiseNotAsDescribedOptions`, `DisputeEvidenceNoValidAuthorization`, `DisputeEvidenceNoValidAuthorizationOptions`, `DisputeEvidenceNotReceived`, `DisputeEvidenceNotReceivedOptions`, `DisputeEvidenceOptions`, `DisputeEvidenceOther`, `DisputeEvidenceOtherOptions`, `DisputeEvidenceServiceNotAsDescribed`, `DisputeEvidenceServiceNotAsDescribedOptions`, `DisputeListOptions`, `DisputeService`, `DisputeSubmitOptions`, `DisputeTreasury`, `DisputeTreasuryOptions`, `DisputeUpdateOptions`, `PersonalizationDesign`, `PersonalizationDesignCarrierText`, `PersonalizationDesignCarrierTextOptions`, `PersonalizationDesignCreateOptions`, `PersonalizationDesignListOptions`, `PersonalizationDesignPreferences`, `PersonalizationDesignPreferencesOptions`, `PersonalizationDesignRejectionReasons`, `PersonalizationDesignService`, `PersonalizationDesignUpdateOptions`, `PhysicalBundle`, `PhysicalBundleFeatures`, `PhysicalBundleListOptions`, `PhysicalBundleService`, `Token`, `TokenListOptions`, `TokenNetworkData`, `TokenNetworkDataDevice`, `TokenNetworkDataMastercard`, `TokenNetworkDataVisa`, `TokenNetworkDataWalletProvider`, `TokenNetworkDataWalletProviderCardholderAddress`, `TokenService`, `TokenUpdateOptions`, `Transaction`, `TransactionAmountDetails`, `TransactionListOptions`, `TransactionNetworkData`, `TransactionPurchaseDetails`, `TransactionPurchaseDetailsFleet`, `TransactionPurchaseDetailsFleetCardholderPromptData`, `TransactionPurchaseDetailsFleetReportedBreakdown`, `TransactionPurchaseDetailsFleetReportedBreakdownFuel`, `TransactionPurchaseDetailsFleetReportedBreakdownNonFuel`, `TransactionPurchaseDetailsFleetReportedBreakdownTax`, `TransactionPurchaseDetailsFlight`, `TransactionPurchaseDetailsFlightSegment`, `TransactionPurchaseDetailsFuel`, `TransactionPurchaseDetailsLodging`, `TransactionPurchaseDetailsReceipt`, `TransactionService`, `TransactionTreasury`, `TransactionUpdateOptions`
- **Stripe.Radar**: `EarlyFraudWarning`, `EarlyFraudWarningListOptions`, `EarlyFraudWarningService`, `PaymentEvaluation`, `PaymentEvaluationClientDeviceMetadataDetails`, `PaymentEvaluationClientDeviceMetadataDetailsOptions`, `PaymentEvaluationCreateOptions`, `PaymentEvaluationCustomerDetails`, `PaymentEvaluationCustomerDetailsOptions`, `PaymentEvaluationEvent`, `PaymentEvaluationEventDisputeOpened`, `PaymentEvaluationEventEarlyFraudWarningReceived`, `PaymentEvaluationEventRefunded`, `PaymentEvaluationEventUserInterventionRaised`, `PaymentEvaluationEventUserInterventionRaisedCustom`, `PaymentEvaluationEventUserInterventionResolved`, `PaymentEvaluationOutcome`, `PaymentEvaluationOutcomeMerchantBlocked`, `PaymentEvaluationOutcomeRejected`, `PaymentEvaluationOutcomeRejectedCard`, `PaymentEvaluationOutcomeSucceeded`, `PaymentEvaluationOutcomeSucceededCard`, `PaymentEvaluationPaymentDetails`, `PaymentEvaluationPaymentDetailsMoneyMovementDetails`, `PaymentEvaluationPaymentDetailsMoneyMovementDetailsCard`, `PaymentEvaluationPaymentDetailsMoneyMovementDetailsCardOptions`, `PaymentEvaluationPaymentDetailsMoneyMovementDetailsOptions`, `PaymentEvaluationPaymentDetailsOptions`, `PaymentEvaluationPaymentDetailsPaymentMethodDetails`, `PaymentEvaluationPaymentDetailsPaymentMethodDetailsBillingDetails`, `PaymentEvaluationPaymentDetailsPaymentMethodDetailsBillingDetailsAddress`, `PaymentEvaluationPaymentDetailsPaymentMethodDetailsBillingDetailsOptions`, `PaymentEvaluationPaymentDetailsPaymentMethodDetailsOptions`, `PaymentEvaluationPaymentDetailsShippingDetails`, `PaymentEvaluationPaymentDetailsShippingDetailsAddress`, `PaymentEvaluationPaymentDetailsShippingDetailsOptions`, `PaymentEvaluationService`, `PaymentEvaluationSignals`, `PaymentEvaluationSignalsFraudulentPayment`, `ValueList`, `ValueListCreateOptions`, `ValueListItem`, `ValueListItemCreateOptions`, `ValueListItemListOptions`, `ValueListItemService`, `ValueListListOptions`, `ValueListService`, `ValueListUpdateOptions`
- **Stripe.Reporting**: `ReportRun`, `ReportRunCreateOptions`, `ReportRunListOptions`, `ReportRunParameters`, `ReportRunParametersOptions`, `ReportRunService`, `ReportType`, `ReportTypeService`
- **Stripe.Reserve**: `Hold`, `HoldReleaseSchedule`, `Plan`, `PlanFixedRelease`, `PlanRollingRelease`, `Release`, `ReleaseSourceTransaction`
- **Stripe.Sigma**: `ScheduledQueryRun`, `ScheduledQueryRunError`, `ScheduledQueryRunService`
- **Stripe.Tax**: `Association`, `AssociationFindOptions`, `AssociationService`, `AssociationTaxTransactionAttempt`, `AssociationTaxTransactionAttemptCommitted`, `AssociationTaxTransactionAttemptErrored`, `Calculation`, `CalculationCreateOptions`, `CalculationCustomerDetails`, `CalculationCustomerDetailsAddress`, `CalculationCustomerDetailsOptions`, `CalculationCustomerDetailsTaxId`, `CalculationCustomerDetailsTaxIdOptions`, `CalculationLineItem`, `CalculationLineItemOptions`, `CalculationLineItemService`, `CalculationLineItemTaxBreakdown`, `CalculationLineItemTaxBreakdownJurisdiction`, `CalculationLineItemTaxBreakdownTaxRateDetails`, `CalculationService`, `CalculationShipFromDetailsAddress`, `CalculationShipFromDetailsOptions`, `CalculationShippingCost`, `CalculationShippingCostOptions`, `CalculationShippingCostTaxBreakdown`, `CalculationShippingCostTaxBreakdownJurisdiction`, `CalculationShippingCostTaxBreakdownTaxRateDetails`, `CalculationTaxBreakdown`, `CalculationTaxBreakdownTaxRateDetails`, `CalculationTaxBreakdownTaxRateDetailsFlatAmount`, `Registration`, `RegistrationCountryOptionsAe`, `RegistrationCountryOptionsAeOptions`, `RegistrationCountryOptionsAeStandard`, `RegistrationCountryOptionsAeStandardOptions`, `RegistrationCountryOptionsAl`, `RegistrationCountryOptionsAlOptions`, `RegistrationCountryOptionsAlStandardOptions`, `RegistrationCountryOptionsAm`, `RegistrationCountryOptionsAmOptions`, `RegistrationCountryOptionsAo`, `RegistrationCountryOptionsAoOptions`, `RegistrationCountryOptionsAoStandardOptions`, `RegistrationCountryOptionsAt`, `RegistrationCountryOptionsAtOptions`, `RegistrationCountryOptionsAtStandard`, `RegistrationCountryOptionsAtStandardOptions`, `RegistrationCountryOptionsAu`, `RegistrationCountryOptionsAuOptions`, `RegistrationCountryOptionsAuStandard`, `RegistrationCountryOptionsAuStandardOptions`, `RegistrationCountryOptionsAw`, `RegistrationCountryOptionsAwOptions`, `RegistrationCountryOptionsAwStandardOptions`, `RegistrationCountryOptionsAz`, `RegistrationCountryOptionsAzOptions`, `RegistrationCountryOptionsBa`, `RegistrationCountryOptionsBaOptions`, `RegistrationCountryOptionsBaStandardOptions`, `RegistrationCountryOptionsBb`, `RegistrationCountryOptionsBbOptions`, `RegistrationCountryOptionsBbStandardOptions`, `RegistrationCountryOptionsBd`, `RegistrationCountryOptionsBdOptions`, `RegistrationCountryOptionsBdStandardOptions`, `RegistrationCountryOptionsBe`, `RegistrationCountryOptionsBeOptions`, `RegistrationCountryOptionsBeStandard`, `RegistrationCountryOptionsBeStandardOptions`, `RegistrationCountryOptionsBf`, `RegistrationCountryOptionsBfOptions`, `RegistrationCountryOptionsBfStandardOptions`, `RegistrationCountryOptionsBg`, `RegistrationCountryOptionsBgOptions`, `RegistrationCountryOptionsBgStandard`, `RegistrationCountryOptionsBgStandardOptions`, `RegistrationCountryOptionsBh`, `RegistrationCountryOptionsBhOptions`, `RegistrationCountryOptionsBhStandardOptions`, `RegistrationCountryOptionsBj`, `RegistrationCountryOptionsBjOptions`, `RegistrationCountryOptionsBs`, `RegistrationCountryOptionsBsOptions`, `RegistrationCountryOptionsBsStandardOptions`, `RegistrationCountryOptionsBy`, `RegistrationCountryOptionsByOptions`, `RegistrationCountryOptionsCa`, `RegistrationCountryOptionsCaOptions`, `RegistrationCountryOptionsCaProvinceStandard`, `RegistrationCountryOptionsCaProvinceStandardOptions`, `RegistrationCountryOptionsCd`, `RegistrationCountryOptionsCdOptions`, `RegistrationCountryOptionsCdStandardOptions`, `RegistrationCountryOptionsCh`, `RegistrationCountryOptionsChOptions`, `RegistrationCountryOptionsChStandard`, `RegistrationCountryOptionsChStandardOptions`, `RegistrationCountryOptionsCl`, `RegistrationCountryOptionsClOptions`, `RegistrationCountryOptionsCm`, `RegistrationCountryOptionsCmOptions`, `RegistrationCountryOptionsCo`, `RegistrationCountryOptionsCoOptions`, `RegistrationCountryOptionsCr`, `RegistrationCountryOptionsCrOptions`, `RegistrationCountryOptionsCv`, `RegistrationCountryOptionsCvOptions`, `RegistrationCountryOptionsCy`, `RegistrationCountryOptionsCyOptions`, `RegistrationCountryOptionsCyStandard`, `RegistrationCountryOptionsCyStandardOptions`, `RegistrationCountryOptionsCz`, `RegistrationCountryOptionsCzOptions`, `RegistrationCountryOptionsCzStandard`, `RegistrationCountryOptionsCzStandardOptions`, `RegistrationCountryOptionsDe`, `RegistrationCountryOptionsDeOptions`, `RegistrationCountryOptionsDeStandard`, `RegistrationCountryOptionsDeStandardOptions`, `RegistrationCountryOptionsDk`, `RegistrationCountryOptionsDkOptions`, `RegistrationCountryOptionsDkStandard`, `RegistrationCountryOptionsDkStandardOptions`, `RegistrationCountryOptionsEc`, `RegistrationCountryOptionsEcOptions`, `RegistrationCountryOptionsEe`, `RegistrationCountryOptionsEeOptions`, `RegistrationCountryOptionsEeStandard`, `RegistrationCountryOptionsEeStandardOptions`, `RegistrationCountryOptionsEg`, `RegistrationCountryOptionsEgOptions`, `RegistrationCountryOptionsEs`, `RegistrationCountryOptionsEsOptions`, `RegistrationCountryOptionsEsStandard`, `RegistrationCountryOptionsEsStandardOptions`, `RegistrationCountryOptionsEt`, `RegistrationCountryOptionsEtOptions`, `RegistrationCountryOptionsEtStandardOptions`, `RegistrationCountryOptionsFi`, `RegistrationCountryOptionsFiOptions`, `RegistrationCountryOptionsFiStandard`, `RegistrationCountryOptionsFiStandardOptions`, `RegistrationCountryOptionsFr`, `RegistrationCountryOptionsFrOptions`, `RegistrationCountryOptionsFrStandard`, `RegistrationCountryOptionsFrStandardOptions`, `RegistrationCountryOptionsGb`, `RegistrationCountryOptionsGbOptions`, `RegistrationCountryOptionsGbStandard`, `RegistrationCountryOptionsGbStandardOptions`, `RegistrationCountryOptionsGe`, `RegistrationCountryOptionsGeOptions`, `RegistrationCountryOptionsGn`, `RegistrationCountryOptionsGnOptions`, `RegistrationCountryOptionsGnStandardOptions`, `RegistrationCountryOptionsGr`, `RegistrationCountryOptionsGrOptions`, `RegistrationCountryOptionsGrStandard`, `RegistrationCountryOptionsGrStandardOptions`, `RegistrationCountryOptionsHr`, `RegistrationCountryOptionsHrOptions`, `RegistrationCountryOptionsHrStandard`, `RegistrationCountryOptionsHrStandardOptions`, `RegistrationCountryOptionsHu`, `RegistrationCountryOptionsHuOptions`, `RegistrationCountryOptionsHuStandard`, `RegistrationCountryOptionsHuStandardOptions`, `RegistrationCountryOptionsId`, `RegistrationCountryOptionsIdOptions`, `RegistrationCountryOptionsIe`, `RegistrationCountryOptionsIeOptions`, `RegistrationCountryOptionsIeStandard`, `RegistrationCountryOptionsIeStandardOptions`, `RegistrationCountryOptionsIn`, `RegistrationCountryOptionsInOptions`, `RegistrationCountryOptionsIs`, `RegistrationCountryOptionsIsOptions`, `RegistrationCountryOptionsIsStandardOptions`, `RegistrationCountryOptionsIt`, `RegistrationCountryOptionsItOptions`, `RegistrationCountryOptionsItStandard`, `RegistrationCountryOptionsItStandardOptions`, `RegistrationCountryOptionsJp`, `RegistrationCountryOptionsJpOptions`, `RegistrationCountryOptionsJpStandard`, `RegistrationCountryOptionsJpStandardOptions`, `RegistrationCountryOptionsKe`, `RegistrationCountryOptionsKeOptions`, `RegistrationCountryOptionsKg`, `RegistrationCountryOptionsKgOptions`, `RegistrationCountryOptionsKh`, `RegistrationCountryOptionsKhOptions`, `RegistrationCountryOptionsKr`, `RegistrationCountryOptionsKrOptions`, `RegistrationCountryOptionsKz`, `RegistrationCountryOptionsKzOptions`, `RegistrationCountryOptionsLa`, `RegistrationCountryOptionsLaOptions`, `RegistrationCountryOptionsLk`, `RegistrationCountryOptionsLkOptions`, `RegistrationCountryOptionsLt`, `RegistrationCountryOptionsLtOptions`, `RegistrationCountryOptionsLtStandard`, `RegistrationCountryOptionsLtStandardOptions`, `RegistrationCountryOptionsLu`, `RegistrationCountryOptionsLuOptions`, `RegistrationCountryOptionsLuStandard`, `RegistrationCountryOptionsLuStandardOptions`, `RegistrationCountryOptionsLv`, `RegistrationCountryOptionsLvOptions`, `RegistrationCountryOptionsLvStandard`, `RegistrationCountryOptionsLvStandardOptions`, `RegistrationCountryOptionsMa`, `RegistrationCountryOptionsMaOptions`, `RegistrationCountryOptionsMd`, `RegistrationCountryOptionsMdOptions`, `RegistrationCountryOptionsMe`, `RegistrationCountryOptionsMeOptions`, `RegistrationCountryOptionsMeStandardOptions`, `RegistrationCountryOptionsMk`, `RegistrationCountryOptionsMkOptions`, `RegistrationCountryOptionsMkStandardOptions`, `RegistrationCountryOptionsMr`, `RegistrationCountryOptionsMrOptions`, `RegistrationCountryOptionsMrStandardOptions`, `RegistrationCountryOptionsMt`, `RegistrationCountryOptionsMtOptions`, `RegistrationCountryOptionsMtStandard`, `RegistrationCountryOptionsMtStandardOptions`, `RegistrationCountryOptionsMx`, `RegistrationCountryOptionsMxOptions`, `RegistrationCountryOptionsMy`, `RegistrationCountryOptionsMyOptions`, `RegistrationCountryOptionsNg`, `RegistrationCountryOptionsNgOptions`, `RegistrationCountryOptionsNl`, `RegistrationCountryOptionsNlOptions`, `RegistrationCountryOptionsNlStandard`, `RegistrationCountryOptionsNlStandardOptions`, `RegistrationCountryOptionsNo`, `RegistrationCountryOptionsNoOptions`, `RegistrationCountryOptionsNoStandard`, `RegistrationCountryOptionsNoStandardOptions`, `RegistrationCountryOptionsNp`, `RegistrationCountryOptionsNpOptions`, `RegistrationCountryOptionsNz`, `RegistrationCountryOptionsNzOptions`, `RegistrationCountryOptionsNzStandard`, `RegistrationCountryOptionsNzStandardOptions`, `RegistrationCountryOptionsOm`, `RegistrationCountryOptionsOmOptions`, `RegistrationCountryOptionsOmStandardOptions`, `RegistrationCountryOptionsOptions`, `RegistrationCountryOptionsPe`, `RegistrationCountryOptionsPeOptions`, `RegistrationCountryOptionsPh`, `RegistrationCountryOptionsPhOptions`, `RegistrationCountryOptionsPl`, `RegistrationCountryOptionsPlOptions`, `RegistrationCountryOptionsPlStandard`, `RegistrationCountryOptionsPlStandardOptions`, `RegistrationCountryOptionsPt`, `RegistrationCountryOptionsPtOptions`, `RegistrationCountryOptionsPtStandard`, `RegistrationCountryOptionsPtStandardOptions`, `RegistrationCountryOptionsRo`, `RegistrationCountryOptionsRoOptions`, `RegistrationCountryOptionsRoStandard`, `RegistrationCountryOptionsRoStandardOptions`, `RegistrationCountryOptionsRs`, `RegistrationCountryOptionsRsOptions`, `RegistrationCountryOptionsRsStandardOptions`, `RegistrationCountryOptionsRu`, `RegistrationCountryOptionsRuOptions`, `RegistrationCountryOptionsSa`, `RegistrationCountryOptionsSaOptions`, `RegistrationCountryOptionsSe`, `RegistrationCountryOptionsSeOptions`, `RegistrationCountryOptionsSeStandard`, `RegistrationCountryOptionsSeStandardOptions`, `RegistrationCountryOptionsSg`, `RegistrationCountryOptionsSgOptions`, `RegistrationCountryOptionsSgStandard`, `RegistrationCountryOptionsSgStandardOptions`, `RegistrationCountryOptionsSi`, `RegistrationCountryOptionsSiOptions`, `RegistrationCountryOptionsSiStandard`, `RegistrationCountryOptionsSiStandardOptions`, `RegistrationCountryOptionsSk`, `RegistrationCountryOptionsSkOptions`, `RegistrationCountryOptionsSkStandard`, `RegistrationCountryOptionsSkStandardOptions`, `RegistrationCountryOptionsSn`, `RegistrationCountryOptionsSnOptions`, `RegistrationCountryOptionsSr`, `RegistrationCountryOptionsSrOptions`, `RegistrationCountryOptionsSrStandardOptions`, `RegistrationCountryOptionsTh`, `RegistrationCountryOptionsThOptions`, `RegistrationCountryOptionsTj`, `RegistrationCountryOptionsTjOptions`, `RegistrationCountryOptionsTr`, `RegistrationCountryOptionsTrOptions`, `RegistrationCountryOptionsTw`, `RegistrationCountryOptionsTwOptions`, `RegistrationCountryOptionsTz`, `RegistrationCountryOptionsTzOptions`, `RegistrationCountryOptionsUa`, `RegistrationCountryOptionsUaOptions`, `RegistrationCountryOptionsUg`, `RegistrationCountryOptionsUgOptions`, `RegistrationCountryOptionsUs`, `RegistrationCountryOptionsUsLocalAmusementTax`, `RegistrationCountryOptionsUsLocalAmusementTaxOptions`, `RegistrationCountryOptionsUsLocalLeaseTax`, `RegistrationCountryOptionsUsLocalLeaseTaxOptions`, `RegistrationCountryOptionsUsOptions`, `RegistrationCountryOptionsUsStateSalesTax`, `RegistrationCountryOptionsUsStateSalesTaxElection`, `RegistrationCountryOptionsUsStateSalesTaxElectionOptions`, `RegistrationCountryOptionsUsStateSalesTaxOptions`, `RegistrationCountryOptionsUy`, `RegistrationCountryOptionsUyOptions`, `RegistrationCountryOptionsUyStandardOptions`, `RegistrationCountryOptionsUz`, `RegistrationCountryOptionsUzOptions`, `RegistrationCountryOptionsVn`, `RegistrationCountryOptionsVnOptions`, `RegistrationCountryOptionsZa`, `RegistrationCountryOptionsZaOptions`, `RegistrationCountryOptionsZaStandardOptions`, `RegistrationCountryOptionsZm`, `RegistrationCountryOptionsZmOptions`, `RegistrationCountryOptionsZw`, `RegistrationCountryOptionsZwOptions`, `RegistrationCountryOptionsZwStandardOptions`, `RegistrationCreateOptions`, `RegistrationListOptions`, `RegistrationService`, `RegistrationUpdateOptions`, `Settings`, `SettingsDefaults`, `SettingsDefaultsOptions`, `SettingsHeadOfficeOptions`, `SettingsService`, `SettingsStatusDetailsPending`, `SettingsUpdateOptions`, `Transaction`, `TransactionCreateFromCalculationOptions`, `TransactionCreateReversalOptions`, `TransactionCustomerDetails`, `TransactionCustomerDetailsAddress`, `TransactionCustomerDetailsTaxId`, `TransactionLineItem`, `TransactionLineItemOptions`, `TransactionLineItemReversal`, `TransactionLineItemService`, `TransactionReversal`, `TransactionService`, `TransactionShipFromDetailsAddress`, `TransactionShippingCost`, `TransactionShippingCostOptions`, `TransactionShippingCostTaxBreakdown`, `TransactionShippingCostTaxBreakdownJurisdiction`, `TransactionShippingCostTaxBreakdownTaxRateDetails`
- **Stripe.Terminal**: `Configuration`, `ConfigurationBbposWisepad3`, `ConfigurationBbposWisepad3Options`, `ConfigurationBbposWiseposE`, `ConfigurationBbposWiseposEOptions`, `ConfigurationCellular`, `ConfigurationCellularOptions`, `ConfigurationCreateOptions`, `ConfigurationListOptions`, `ConfigurationOffline`, `ConfigurationOfflineOptions`, `ConfigurationRebootWindow`, `ConfigurationRebootWindowOptions`, `ConfigurationService`, `ConfigurationStripeS700`, `ConfigurationStripeS700Options`, `ConfigurationStripeS710`, `ConfigurationStripeS710Options`, `ConfigurationTippingAed`, `ConfigurationTippingAedOptions`, `ConfigurationTippingAud`, `ConfigurationTippingAudOptions`, `ConfigurationTippingCad`, `ConfigurationTippingCadOptions`, `ConfigurationTippingChf`, `ConfigurationTippingChfOptions`, `ConfigurationTippingCzk`, `ConfigurationTippingCzkOptions`, `ConfigurationTippingDkk`, `ConfigurationTippingDkkOptions`, `ConfigurationTippingEur`, `ConfigurationTippingEurOptions`, `ConfigurationTippingGbp`, `ConfigurationTippingGbpOptions`, `ConfigurationTippingGip`, `ConfigurationTippingGipOptions`, `ConfigurationTippingHkd`, `ConfigurationTippingHkdOptions`, `ConfigurationTippingHuf`, `ConfigurationTippingHufOptions`, `ConfigurationTippingJpy`, `ConfigurationTippingJpyOptions`, `ConfigurationTippingMxn`, `ConfigurationTippingMxnOptions`, `ConfigurationTippingMyr`, `ConfigurationTippingMyrOptions`, `ConfigurationTippingNok`, `ConfigurationTippingNokOptions`, `ConfigurationTippingNzd`, `ConfigurationTippingNzdOptions`, `ConfigurationTippingOptions`, `ConfigurationTippingPln`, `ConfigurationTippingPlnOptions`, `ConfigurationTippingRon`, `ConfigurationTippingRonOptions`, `ConfigurationTippingSek`, `ConfigurationTippingSekOptions`, `ConfigurationTippingSgd`, `ConfigurationTippingSgdOptions`, `ConfigurationTippingUsd`, `ConfigurationTippingUsdOptions`, `ConfigurationUpdateOptions`, `ConfigurationVerifoneM425`, `ConfigurationVerifoneM425Options`, `ConfigurationVerifoneP400`, `ConfigurationVerifoneP400Options`, `ConfigurationVerifoneP630`, `ConfigurationVerifoneP630Options`, `ConfigurationVerifoneUx700`, `ConfigurationVerifoneUx700Options`, `ConfigurationVerifoneV660p`, `ConfigurationVerifoneV660pOptions`, `ConfigurationWifi`, `ConfigurationWifiEnterpriseEapPeap`, `ConfigurationWifiEnterpriseEapPeapOptions`, `ConfigurationWifiEnterpriseEapTls`, `ConfigurationWifiEnterpriseEapTlsOptions`, `ConfigurationWifiOptions`, `ConfigurationWifiPersonalPsk`, `ConfigurationWifiPersonalPskOptions`, `ConnectionToken`, `ConnectionTokenCreateOptions`, `ConnectionTokenService`, `Location`, `LocationAddressKana`, `LocationAddressKanji`, `LocationCreateOptions`, `LocationService`, `LocationUpdateOptions`, `OnboardingLink`, `OnboardingLinkCreateOptions`, `OnboardingLinkLinkOptions`, `OnboardingLinkLinkOptionsAppleTermsAndConditions`, `OnboardingLinkLinkOptionsAppleTermsAndConditionsOptions`, `OnboardingLinkLinkOptionsOptions`, `OnboardingLinkService`, `Reader`, `ReaderAction`, `ReaderActionCollectInputs`, `ReaderActionCollectInputsInput`, `ReaderActionCollectInputsInputCustomText`, `ReaderActionCollectInputsInputEmail`, `ReaderActionCollectInputsInputNumeric`, `ReaderActionCollectInputsInputPhone`, `ReaderActionCollectInputsInputSelection`, `ReaderActionCollectInputsInputSelectionChoice`, `ReaderActionCollectInputsInputSignature`, `ReaderActionCollectInputsInputText`, `ReaderActionCollectInputsInputToggle`, `ReaderActionCollectPaymentMethod`, `ReaderActionCollectPaymentMethodCollectConfig`, `ReaderActionCollectPaymentMethodCollectConfigTipping`, `ReaderActionConfirmPaymentIntent`, `ReaderActionConfirmPaymentIntentConfirmConfig`, `ReaderActionPrintContent`, `ReaderActionPrintContentImage`, `ReaderActionProcessPaymentIntent`, `ReaderActionProcessPaymentIntentProcessConfig`, `ReaderActionProcessPaymentIntentProcessConfigTipping`, `ReaderActionProcessSetupIntent`, `ReaderActionProcessSetupIntentProcessConfig`, `ReaderActionRefundPayment`, `ReaderActionRefundPaymentRefundPaymentConfig`, `ReaderActionSetReaderDisplay`, `ReaderActionSetReaderDisplayCart`, `ReaderActionSetReaderDisplayCartLineItem`, `ReaderCartLineItemOptions`, `ReaderCartOptions`, `ReaderCollectConfigOptions`, `ReaderCollectConfigTippingOptions`, `ReaderCollectInputsOptions`, `ReaderCollectPaymentMethodOptions`, `ReaderConfirmConfigOptions`, `ReaderConfirmPaymentIntentOptions`, `ReaderCreateOptions`, `ReaderInputCustomTextOptions`, `ReaderInputOptions`, `ReaderInputSelectionChoiceOptions`, `ReaderInputSelectionOptions`, `ReaderInputToggleOptions`, `ReaderListOptions`, `ReaderProcessConfigOptions`, `ReaderProcessConfigTippingOptions`, `ReaderProcessPaymentIntentOptions`, `ReaderProcessSetupIntentOptions`, `ReaderRefundPaymentConfigOptions`, `ReaderRefundPaymentOptions`, `ReaderService`, `ReaderSetReaderDisplayOptions`, `ReaderUpdateOptions`
- **Stripe.TestHelpers**: `ConfirmationTokenCreateOptions`, `ConfirmationTokenPaymentMethodDataAcssDebitOptions`, `ConfirmationTokenPaymentMethodDataAuBecsDebitOptions`, `ConfirmationTokenPaymentMethodDataBacsDebitOptions`, `ConfirmationTokenPaymentMethodDataBillingDetailsOptions`, `ConfirmationTokenPaymentMethodDataBoletoOptions`, `ConfirmationTokenPaymentMethodDataEpsOptions`, `ConfirmationTokenPaymentMethodDataFpxOptions`, `ConfirmationTokenPaymentMethodDataIdealOptions`, `ConfirmationTokenPaymentMethodDataKlarnaDobOptions`, `ConfirmationTokenPaymentMethodDataKlarnaOptions`, `ConfirmationTokenPaymentMethodDataNaverPayOptions`, `ConfirmationTokenPaymentMethodDataNzBankAccountOptions`, `ConfirmationTokenPaymentMethodDataOptions`, `ConfirmationTokenPaymentMethodDataP24Options`, `ConfirmationTokenPaymentMethodDataPaytoOptions`, `ConfirmationTokenPaymentMethodDataRadarOptionsOptions`, `ConfirmationTokenPaymentMethodDataSepaDebitOptions`, `ConfirmationTokenPaymentMethodDataSofortOptions`, `ConfirmationTokenPaymentMethodDataUpiMandateOptionsOptions`, `ConfirmationTokenPaymentMethodDataUpiOptions`, `ConfirmationTokenPaymentMethodDataUsBankAccountOptions`, `ConfirmationTokenPaymentMethodOptionsCardInstallmentsOptions`, `ConfirmationTokenPaymentMethodOptionsCardInstallmentsPlanOptions`, `ConfirmationTokenPaymentMethodOptionsCardOptions`, `ConfirmationTokenPaymentMethodOptionsOptions`, `ConfirmationTokenService`, `ConfirmationTokenShippingOptions`, `CustomerFundCashBalanceOptions`, `CustomerService`, `RefundService`, `TestClock`, `TestClockAdvanceOptions`, `TestClockCreateOptions`, `TestClockService`, `TestClockStatusDetailsAdvancing`
- **Stripe.TestHelpers.Issuing**: `AuthorizationAmountDetailsOptions`, `AuthorizationCaptureOptions`, `AuthorizationCreateOptions`, `AuthorizationFinalizeAmountOptions`, `AuthorizationFleetCardholderPromptDataOptions`, `AuthorizationFleetOptions`, `AuthorizationFleetReportedBreakdownFuelOptions`, `AuthorizationFleetReportedBreakdownNonFuelOptions`, `AuthorizationFleetReportedBreakdownOptions`, `AuthorizationFleetReportedBreakdownTaxOptions`, `AuthorizationFuelOptions`, `AuthorizationIncrementOptions`, `AuthorizationMerchantDataOptions`, `AuthorizationNetworkDataOptions`, `AuthorizationPurchaseDetailsFleetCardholderPromptDataOptions`, `AuthorizationPurchaseDetailsFleetOptions`, `AuthorizationPurchaseDetailsFleetReportedBreakdownFuelOptions`, `AuthorizationPurchaseDetailsFleetReportedBreakdownNonFuelOptions`, `AuthorizationPurchaseDetailsFleetReportedBreakdownOptions`, `AuthorizationPurchaseDetailsFleetReportedBreakdownTaxOptions`, `AuthorizationPurchaseDetailsFlightOptions`, `AuthorizationPurchaseDetailsFlightSegmentOptions`, `AuthorizationPurchaseDetailsFuelOptions`, `AuthorizationPurchaseDetailsLodgingOptions`, `AuthorizationPurchaseDetailsOptions`, `AuthorizationRespondOptions`, `AuthorizationReverseOptions`, `AuthorizationRiskAssessmentCardTestingRiskOptions`, `AuthorizationRiskAssessmentFraudRiskOptions`, `AuthorizationRiskAssessmentMerchantDisputeRiskOptions`, `AuthorizationRiskAssessmentOptions`, `AuthorizationService`, `AuthorizationVerificationDataAuthenticationExemptionOptions`, `AuthorizationVerificationDataOptions`, `AuthorizationVerificationDataThreeDSecureOptions`, `CardService`, `PersonalizationDesignRejectOptions`, `PersonalizationDesignRejectionReasonsOptions`, `PersonalizationDesignService`, `TransactionCreateForceCaptureOptions`, `TransactionCreateUnlinkedRefundOptions`, `TransactionMerchantDataOptions`, `TransactionPurchaseDetailsFleetCardholderPromptDataOptions`, `TransactionPurchaseDetailsFleetOptions`, `TransactionPurchaseDetailsFleetReportedBreakdownFuelOptions`, `TransactionPurchaseDetailsFleetReportedBreakdownNonFuelOptions`, `TransactionPurchaseDetailsFleetReportedBreakdownOptions`, `TransactionPurchaseDetailsFleetReportedBreakdownTaxOptions`, `TransactionPurchaseDetailsFlightOptions`, `TransactionPurchaseDetailsFlightSegmentOptions`, `TransactionPurchaseDetailsFuelOptions`, `TransactionPurchaseDetailsLodgingOptions`, `TransactionPurchaseDetailsOptions`, `TransactionRefundOptions`, `TransactionService`
- **Stripe.TestHelpers.Terminal**: `ReaderCardOptions`, `ReaderCardPresentOptions`, `ReaderInteracPresentOptions`, `ReaderPresentPaymentMethodOptions`, `ReaderService`, `ReaderSucceedInputCollectionOptions`
- **Stripe.TestHelpers.Treasury**: `InboundTransferFailOptions`, `InboundTransferFailureDetailsOptions`, `InboundTransferService`, `OutboundPaymentReturnOutboundPaymentOptions`, `OutboundPaymentReturnedDetailsOptions`, `OutboundPaymentService`, `OutboundPaymentTrackingDetailsAchOptions`, `OutboundPaymentTrackingDetailsOptions`, `OutboundPaymentTrackingDetailsUsDomesticWireOptions`, `OutboundPaymentUpdateOptions`, `OutboundTransferReturnOutboundTransferOptions`, `OutboundTransferReturnedDetailsOptions`, `OutboundTransferService`, `OutboundTransferTrackingDetailsAchOptions`, `OutboundTransferTrackingDetailsOptions`, `OutboundTransferTrackingDetailsUsDomesticWireOptions`, `OutboundTransferUpdateOptions`, `ReceivedCreditCreateOptions`, `ReceivedCreditInitiatingPaymentMethodDetailsOptions`, `ReceivedCreditInitiatingPaymentMethodDetailsUsBankAccountOptions`, `ReceivedCreditService`, `ReceivedDebitCreateOptions`, `ReceivedDebitInitiatingPaymentMethodDetailsOptions`, `ReceivedDebitInitiatingPaymentMethodDetailsUsBankAccountOptions`, `ReceivedDebitService`
- **Stripe.Treasury**: `CreditReversal`, `CreditReversalCreateOptions`, `CreditReversalListOptions`, `CreditReversalService`, `CreditReversalStatusTransitions`, `DebitReversal`, `DebitReversalCreateOptions`, `DebitReversalLinkedFlows`, `DebitReversalListOptions`, `DebitReversalService`, `DebitReversalStatusTransitions`, `FinancialAccount`, `FinancialAccountBalance`, `FinancialAccountCloseOptions`, `FinancialAccountCreateOptions`, `FinancialAccountFeatures`, `FinancialAccountFeaturesCardIssuing`, `FinancialAccountFeaturesCardIssuingOptions`, `FinancialAccountFeaturesCardIssuingStatusDetail`, `FinancialAccountFeaturesDepositInsurance`, `FinancialAccountFeaturesDepositInsuranceOptions`, `FinancialAccountFeaturesDepositInsuranceStatusDetail`, `FinancialAccountFeaturesFinancialAddresses`, `FinancialAccountFeaturesFinancialAddressesAba`, `FinancialAccountFeaturesFinancialAddressesAbaOptions`, `FinancialAccountFeaturesFinancialAddressesAbaStatusDetail`, `FinancialAccountFeaturesFinancialAddressesOptions`, `FinancialAccountFeaturesInboundTransfers`, `FinancialAccountFeaturesInboundTransfersAch`, `FinancialAccountFeaturesInboundTransfersAchOptions`, `FinancialAccountFeaturesInboundTransfersAchStatusDetail`, `FinancialAccountFeaturesInboundTransfersOptions`, `FinancialAccountFeaturesIntraStripeFlows`, `FinancialAccountFeaturesIntraStripeFlowsOptions`, `FinancialAccountFeaturesIntraStripeFlowsStatusDetail`, `FinancialAccountFeaturesOptions`, `FinancialAccountFeaturesOutboundPayments`, `FinancialAccountFeaturesOutboundPaymentsAch`, `FinancialAccountFeaturesOutboundPaymentsAchOptions`, `FinancialAccountFeaturesOutboundPaymentsAchStatusDetail`, `FinancialAccountFeaturesOutboundPaymentsOptions`, `FinancialAccountFeaturesOutboundPaymentsUsDomesticWire`, `FinancialAccountFeaturesOutboundPaymentsUsDomesticWireOptions`, `FinancialAccountFeaturesOutboundPaymentsUsDomesticWireStatusDetail`, `FinancialAccountFeaturesOutboundTransfers`, `FinancialAccountFeaturesOutboundTransfersAch`, `FinancialAccountFeaturesOutboundTransfersAchOptions`, `FinancialAccountFeaturesOutboundTransfersAchStatusDetail`, `FinancialAccountFeaturesOutboundTransfersOptions`, `FinancialAccountFeaturesOutboundTransfersUsDomesticWire`, `FinancialAccountFeaturesOutboundTransfersUsDomesticWireOptions`, `FinancialAccountFeaturesOutboundTransfersUsDomesticWireStatusDetail`, `FinancialAccountFeaturesService`, `FinancialAccountFeaturesUpdateOptions`, `FinancialAccountFinancialAddress`, `FinancialAccountFinancialAddressAba`, `FinancialAccountForwardingSettingsOptions`, `FinancialAccountListOptions`, `FinancialAccountPlatformRestrictions`, `FinancialAccountPlatformRestrictionsOptions`, `FinancialAccountService`, `FinancialAccountStatusDetails`, `FinancialAccountStatusDetailsClosed`, `FinancialAccountUpdateOptions`, `InboundTransfer`, `InboundTransferCreateOptions`, `InboundTransferFailureDetails`, `InboundTransferLinkedFlows`, `InboundTransferListOptions`, `InboundTransferOriginPaymentMethodDetails`, `InboundTransferOriginPaymentMethodDetailsBillingDetails`, `InboundTransferOriginPaymentMethodDetailsUsBankAccount`, `InboundTransferService`, `InboundTransferStatusTransitions`, `OutboundPayment`, `OutboundPaymentCreateOptions`, `OutboundPaymentDestinationPaymentMethodDataBillingDetailsOptions`, `OutboundPaymentDestinationPaymentMethodDataOptions`, `OutboundPaymentDestinationPaymentMethodDataUsBankAccountOptions`, `OutboundPaymentDestinationPaymentMethodDetails`, `OutboundPaymentDestinationPaymentMethodDetailsBillingDetails`, `OutboundPaymentDestinationPaymentMethodDetailsFinancialAccount`, `OutboundPaymentDestinationPaymentMethodDetailsUsBankAccount`, `OutboundPaymentDestinationPaymentMethodOptionsOptions`, `OutboundPaymentDestinationPaymentMethodOptionsUsBankAccountOptions`, `OutboundPaymentEndUserDetails`, `OutboundPaymentEndUserDetailsOptions`, `OutboundPaymentListOptions`, `OutboundPaymentReturnedDetails`, `OutboundPaymentService`, `OutboundPaymentStatusTransitions`, `OutboundPaymentTrackingDetails`, `OutboundPaymentTrackingDetailsAch`, `OutboundPaymentTrackingDetailsUsDomesticWire`, `OutboundTransfer`, `OutboundTransferCreateOptions`, `OutboundTransferDestinationPaymentMethodDataOptions`, `OutboundTransferDestinationPaymentMethodDetails`, `OutboundTransferDestinationPaymentMethodDetailsBillingDetails`, `OutboundTransferDestinationPaymentMethodDetailsFinancialAccount`, `OutboundTransferDestinationPaymentMethodDetailsUsBankAccount`, `OutboundTransferDestinationPaymentMethodOptionsOptions`, `OutboundTransferDestinationPaymentMethodOptionsUsBankAccountOptions`, `OutboundTransferListOptions`, `OutboundTransferReturnedDetails`, `OutboundTransferService`, `OutboundTransferStatusTransitions`, `OutboundTransferTrackingDetails`, `OutboundTransferTrackingDetailsAch`, `OutboundTransferTrackingDetailsUsDomesticWire`, `ReceivedCredit`, `ReceivedCreditInitiatingPaymentMethodDetails`, `ReceivedCreditInitiatingPaymentMethodDetailsBillingDetails`, `ReceivedCreditInitiatingPaymentMethodDetailsFinancialAccount`, `ReceivedCreditInitiatingPaymentMethodDetailsUsBankAccount`, `ReceivedCreditLinkedFlows`, `ReceivedCreditLinkedFlowsOptions`, `ReceivedCreditLinkedFlowsSourceFlowDetails`, `ReceivedCreditListOptions`, `ReceivedCreditReversalDetails`, `ReceivedCreditService`, `ReceivedDebit`, `ReceivedDebitInitiatingPaymentMethodDetails`, `ReceivedDebitInitiatingPaymentMethodDetailsBillingDetails`, `ReceivedDebitInitiatingPaymentMethodDetailsFinancialAccount`, `ReceivedDebitInitiatingPaymentMethodDetailsUsBankAccount`, `ReceivedDebitLinkedFlows`, `ReceivedDebitListOptions`, `ReceivedDebitReversalDetails`, `ReceivedDebitService`, `Transaction`, `TransactionBalanceImpact`, `TransactionEntry`, `TransactionEntryBalanceImpact`, `TransactionEntryFlowDetails`, `TransactionEntryListOptions`, `TransactionEntryService`, `TransactionFlowDetails`, `TransactionListOptions`, `TransactionService`, `TransactionStatusTransitions`, `TransactionStatusTransitionsOptions`
- **Stripe.V2**: `DeletedObject`, `ListOptions`, `StripeList<T>`
- **Stripe.V2.Billing**: `MeterEvent`, `MeterEventAdjustment`, `MeterEventAdjustmentCancel`, `MeterEventAdjustmentCreateCancelOptions`, `MeterEventAdjustmentCreateOptions`, `MeterEventAdjustmentService`, `MeterEventCreateOptions`, `MeterEventService`, `MeterEventSession`, `MeterEventSessionService`, `MeterEventStreamCreateEventOptions`, `MeterEventStreamCreateOptions`, `MeterEventStreamService`
- **Stripe.V2.Commerce**: `ProductCatalogImport`, `ProductCatalogImportStatusDetails`, `ProductCatalogImportStatusDetailsAwaitingUpload`, `ProductCatalogImportStatusDetailsAwaitingUploadUploadUrl`, `ProductCatalogImportStatusDetailsFailed`, `ProductCatalogImportStatusDetailsProcessing`, `ProductCatalogImportStatusDetailsSucceeded`, `ProductCatalogImportStatusDetailsSucceededWithErrors`, `ProductCatalogImportStatusDetailsSucceededWithErrorsErrorFile`, `ProductCatalogImportStatusDetailsSucceededWithErrorsErrorFileDownloadUrl`, `ProductCatalogImportStatusDetailsSucceededWithErrorsSample`
- **Stripe.V2.Commerce.ProductCatalog**: `ImportCreateOptions`, `ImportListOptions`, `ImportService`
- **Stripe.V2.Core**: `Account`, `AccountCloseOptions`, `AccountConfiguration`, `AccountConfigurationCustomer`, `AccountConfigurationCustomerAutomaticIndirectTax`, `AccountConfigurationCustomerAutomaticIndirectTaxLocation`, `AccountConfigurationCustomerBilling`, `AccountConfigurationCustomerBillingInvoice`, `AccountConfigurationCustomerBillingInvoiceCustomField`, `AccountConfigurationCustomerBillingInvoiceRendering`, `AccountConfigurationCustomerCapabilities`, `AccountConfigurationCustomerCapabilitiesAutomaticIndirectTax`, `AccountConfigurationCustomerCapabilitiesAutomaticIndirectTaxStatusDetail`, `AccountConfigurationCustomerShipping`, `AccountConfigurationCustomerShippingAddress`, `AccountConfigurationMerchant`, `AccountConfigurationMerchantBacsDebitPayments`, `AccountConfigurationMerchantBranding`, `AccountConfigurationMerchantCapabilities`, `AccountConfigurationMerchantCapabilitiesAchDebitPayments`, `AccountConfigurationMerchantCapabilitiesAchDebitPaymentsStatusDetail`, `AccountConfigurationMerchantCapabilitiesAcssDebitPayments`, `AccountConfigurationMerchantCapabilitiesAcssDebitPaymentsStatusDetail`, `AccountConfigurationMerchantCapabilitiesAffirmPayments`, `AccountConfigurationMerchantCapabilitiesAffirmPaymentsStatusDetail`, `AccountConfigurationMerchantCapabilitiesAfterpayClearpayPayments`, `AccountConfigurationMerchantCapabilitiesAfterpayClearpayPaymentsStatusDetail`, `AccountConfigurationMerchantCapabilitiesAlmaPayments`, `AccountConfigurationMerchantCapabilitiesAlmaPaymentsStatusDetail`, `AccountConfigurationMerchantCapabilitiesAmazonPayPayments`, `AccountConfigurationMerchantCapabilitiesAmazonPayPaymentsStatusDetail`, `AccountConfigurationMerchantCapabilitiesAuBecsDebitPayments`, `AccountConfigurationMerchantCapabilitiesAuBecsDebitPaymentsStatusDetail`, `AccountConfigurationMerchantCapabilitiesBacsDebitPayments`, `AccountConfigurationMerchantCapabilitiesBacsDebitPaymentsStatusDetail`, `AccountConfigurationMerchantCapabilitiesBancontactPayments`, `AccountConfigurationMerchantCapabilitiesBancontactPaymentsStatusDetail`, `AccountConfigurationMerchantCapabilitiesBlikPayments`, `AccountConfigurationMerchantCapabilitiesBlikPaymentsStatusDetail`, `AccountConfigurationMerchantCapabilitiesBoletoPayments`, `AccountConfigurationMerchantCapabilitiesBoletoPaymentsStatusDetail`, `AccountConfigurationMerchantCapabilitiesCardPayments`, `AccountConfigurationMerchantCapabilitiesCardPaymentsStatusDetail`, `AccountConfigurationMerchantCapabilitiesCartesBancairesPayments`, `AccountConfigurationMerchantCapabilitiesCartesBancairesPaymentsStatusDetail`, `AccountConfigurationMerchantCapabilitiesCashappPayments`, `AccountConfigurationMerchantCapabilitiesCashappPaymentsStatusDetail`, `AccountConfigurationMerchantCapabilitiesEpsPayments`, `AccountConfigurationMerchantCapabilitiesEpsPaymentsStatusDetail`, `AccountConfigurationMerchantCapabilitiesFpxPayments`, `AccountConfigurationMerchantCapabilitiesFpxPaymentsStatusDetail`, `AccountConfigurationMerchantCapabilitiesGbBankTransferPayments`, `AccountConfigurationMerchantCapabilitiesGbBankTransferPaymentsStatusDetail`, `AccountConfigurationMerchantCapabilitiesGrabpayPayments`, `AccountConfigurationMerchantCapabilitiesGrabpayPaymentsStatusDetail`, `AccountConfigurationMerchantCapabilitiesIdealPayments`, `AccountConfigurationMerchantCapabilitiesIdealPaymentsStatusDetail`, `AccountConfigurationMerchantCapabilitiesJcbPayments`, `AccountConfigurationMerchantCapabilitiesJcbPaymentsStatusDetail`, `AccountConfigurationMerchantCapabilitiesJpBankTransferPayments`, `AccountConfigurationMerchantCapabilitiesJpBankTransferPaymentsStatusDetail`, `AccountConfigurationMerchantCapabilitiesKakaoPayPayments`, `AccountConfigurationMerchantCapabilitiesKakaoPayPaymentsStatusDetail`, `AccountConfigurationMerchantCapabilitiesKlarnaPayments`, `AccountConfigurationMerchantCapabilitiesKlarnaPaymentsStatusDetail`, `AccountConfigurationMerchantCapabilitiesKonbiniPayments`, `AccountConfigurationMerchantCapabilitiesKonbiniPaymentsStatusDetail`, `AccountConfigurationMerchantCapabilitiesKrCardPayments`, `AccountConfigurationMerchantCapabilitiesKrCardPaymentsStatusDetail`, `AccountConfigurationMerchantCapabilitiesLinkPayments`, `AccountConfigurationMerchantCapabilitiesLinkPaymentsStatusDetail`, `AccountConfigurationMerchantCapabilitiesMobilepayPayments`, `AccountConfigurationMerchantCapabilitiesMobilepayPaymentsStatusDetail`, `AccountConfigurationMerchantCapabilitiesMultibancoPayments`, `AccountConfigurationMerchantCapabilitiesMultibancoPaymentsStatusDetail`, `AccountConfigurationMerchantCapabilitiesMxBankTransferPayments`, `AccountConfigurationMerchantCapabilitiesMxBankTransferPaymentsStatusDetail`, `AccountConfigurationMerchantCapabilitiesNaverPayPayments`, `AccountConfigurationMerchantCapabilitiesNaverPayPaymentsStatusDetail`, `AccountConfigurationMerchantCapabilitiesOxxoPayments`, `AccountConfigurationMerchantCapabilitiesOxxoPaymentsStatusDetail`, `AccountConfigurationMerchantCapabilitiesP24Payments`, `AccountConfigurationMerchantCapabilitiesP24PaymentsStatusDetail`, `AccountConfigurationMerchantCapabilitiesPayByBankPayments`, `AccountConfigurationMerchantCapabilitiesPayByBankPaymentsStatusDetail`, `AccountConfigurationMerchantCapabilitiesPaycoPayments`, `AccountConfigurationMerchantCapabilitiesPaycoPaymentsStatusDetail`, `AccountConfigurationMerchantCapabilitiesPaynowPayments`, `AccountConfigurationMerchantCapabilitiesPaynowPaymentsStatusDetail`, `AccountConfigurationMerchantCapabilitiesPromptpayPayments`, `AccountConfigurationMerchantCapabilitiesPromptpayPaymentsStatusDetail`, `AccountConfigurationMerchantCapabilitiesRevolutPayPayments`, `AccountConfigurationMerchantCapabilitiesRevolutPayPaymentsStatusDetail`, `AccountConfigurationMerchantCapabilitiesSamsungPayPayments`, `AccountConfigurationMerchantCapabilitiesSamsungPayPaymentsStatusDetail`, `AccountConfigurationMerchantCapabilitiesSepaBankTransferPayments`, `AccountConfigurationMerchantCapabilitiesSepaBankTransferPaymentsStatusDetail`, `AccountConfigurationMerchantCapabilitiesSepaDebitPayments`, `AccountConfigurationMerchantCapabilitiesSepaDebitPaymentsStatusDetail`, `AccountConfigurationMerchantCapabilitiesStripeBalance`, `AccountConfigurationMerchantCapabilitiesStripeBalancePayouts`, `AccountConfigurationMerchantCapabilitiesStripeBalancePayoutsStatusDetail`, `AccountConfigurationMerchantCapabilitiesSwishPayments`, `AccountConfigurationMerchantCapabilitiesSwishPaymentsStatusDetail`, `AccountConfigurationMerchantCapabilitiesTwintPayments`, `AccountConfigurationMerchantCapabilitiesTwintPaymentsStatusDetail`, `AccountConfigurationMerchantCapabilitiesUsBankTransferPayments`, `AccountConfigurationMerchantCapabilitiesUsBankTransferPaymentsStatusDetail`, `AccountConfigurationMerchantCapabilitiesZipPayments`, `AccountConfigurationMerchantCapabilitiesZipPaymentsStatusDetail`, `AccountConfigurationMerchantCardPayments`, `AccountConfigurationMerchantCardPaymentsDeclineOn`, `AccountConfigurationMerchantKonbiniPayments`, `AccountConfigurationMerchantKonbiniPaymentsSupport`, `AccountConfigurationMerchantKonbiniPaymentsSupportHours`, `AccountConfigurationMerchantScriptStatementDescriptor`, `AccountConfigurationMerchantScriptStatementDescriptorKana`, `AccountConfigurationMerchantScriptStatementDescriptorKanji`, `AccountConfigurationMerchantSepaDebitPayments`, `AccountConfigurationMerchantStatementDescriptor`, `AccountConfigurationMerchantSupport`, `AccountConfigurationMerchantSupportAddress`, `AccountConfigurationRecipient`, `AccountConfigurationRecipientCapabilities`, `AccountConfigurationRecipientCapabilitiesStripeBalance`, `AccountConfigurationRecipientCapabilitiesStripeBalancePayouts`, `AccountConfigurationRecipientCapabilitiesStripeBalancePayoutsStatusDetail`, `AccountConfigurationRecipientCapabilitiesStripeBalanceStripeTransfers`, `AccountConfigurationRecipientCapabilitiesStripeBalanceStripeTransfersStatusDetail`, `AccountCreateConfigurationCustomerAutomaticIndirectTaxOptions`, `AccountCreateConfigurationCustomerBillingInvoiceCustomFieldOptions`, `AccountCreateConfigurationCustomerBillingInvoiceOptions`, `AccountCreateConfigurationCustomerBillingInvoiceRenderingOptions`, `AccountCreateConfigurationCustomerBillingOptions`, `AccountCreateConfigurationCustomerCapabilitiesAutomaticIndirectTaxOptions`, `AccountCreateConfigurationCustomerCapabilitiesOptions`, `AccountCreateConfigurationCustomerOptions`, `AccountCreateConfigurationCustomerShippingOptions`, `AccountCreateConfigurationMerchantBacsDebitPaymentsOptions`, `AccountCreateConfigurationMerchantBrandingOptions`, `AccountCreateConfigurationMerchantCapabilitiesAchDebitPaymentsOptions`, `AccountCreateConfigurationMerchantCapabilitiesAcssDebitPaymentsOptions`, `AccountCreateConfigurationMerchantCapabilitiesAffirmPaymentsOptions`, `AccountCreateConfigurationMerchantCapabilitiesAfterpayClearpayPaymentsOptions`, `AccountCreateConfigurationMerchantCapabilitiesAlmaPaymentsOptions`, `AccountCreateConfigurationMerchantCapabilitiesAmazonPayPaymentsOptions`, `AccountCreateConfigurationMerchantCapabilitiesAuBecsDebitPaymentsOptions`, `AccountCreateConfigurationMerchantCapabilitiesBacsDebitPaymentsOptions`, `AccountCreateConfigurationMerchantCapabilitiesBancontactPaymentsOptions`, `AccountCreateConfigurationMerchantCapabilitiesBlikPaymentsOptions`, `AccountCreateConfigurationMerchantCapabilitiesBoletoPaymentsOptions`, `AccountCreateConfigurationMerchantCapabilitiesCardPaymentsOptions`, `AccountCreateConfigurationMerchantCapabilitiesCartesBancairesPaymentsOptions`, `AccountCreateConfigurationMerchantCapabilitiesCashappPaymentsOptions`, `AccountCreateConfigurationMerchantCapabilitiesEpsPaymentsOptions`, `AccountCreateConfigurationMerchantCapabilitiesFpxPaymentsOptions`, `AccountCreateConfigurationMerchantCapabilitiesGbBankTransferPaymentsOptions`, `AccountCreateConfigurationMerchantCapabilitiesGrabpayPaymentsOptions`, `AccountCreateConfigurationMerchantCapabilitiesIdealPaymentsOptions`, `AccountCreateConfigurationMerchantCapabilitiesJcbPaymentsOptions`, `AccountCreateConfigurationMerchantCapabilitiesJpBankTransferPaymentsOptions`, `AccountCreateConfigurationMerchantCapabilitiesKakaoPayPaymentsOptions`, `AccountCreateConfigurationMerchantCapabilitiesKlarnaPaymentsOptions`, `AccountCreateConfigurationMerchantCapabilitiesKonbiniPaymentsOptions`, `AccountCreateConfigurationMerchantCapabilitiesKrCardPaymentsOptions`, `AccountCreateConfigurationMerchantCapabilitiesLinkPaymentsOptions`, `AccountCreateConfigurationMerchantCapabilitiesMobilepayPaymentsOptions`, `AccountCreateConfigurationMerchantCapabilitiesMultibancoPaymentsOptions`, `AccountCreateConfigurationMerchantCapabilitiesMxBankTransferPaymentsOptions`, `AccountCreateConfigurationMerchantCapabilitiesNaverPayPaymentsOptions`, `AccountCreateConfigurationMerchantCapabilitiesOptions`, `AccountCreateConfigurationMerchantCapabilitiesOxxoPaymentsOptions`, `AccountCreateConfigurationMerchantCapabilitiesP24PaymentsOptions`, `AccountCreateConfigurationMerchantCapabilitiesPayByBankPaymentsOptions`, `AccountCreateConfigurationMerchantCapabilitiesPaycoPaymentsOptions`, `AccountCreateConfigurationMerchantCapabilitiesPaynowPaymentsOptions`, `AccountCreateConfigurationMerchantCapabilitiesPromptpayPaymentsOptions`, `AccountCreateConfigurationMerchantCapabilitiesRevolutPayPaymentsOptions`, `AccountCreateConfigurationMerchantCapabilitiesSamsungPayPaymentsOptions`, `AccountCreateConfigurationMerchantCapabilitiesSepaBankTransferPaymentsOptions`, `AccountCreateConfigurationMerchantCapabilitiesSepaDebitPaymentsOptions`, `AccountCreateConfigurationMerchantCapabilitiesSwishPaymentsOptions`, `AccountCreateConfigurationMerchantCapabilitiesTwintPaymentsOptions`, `AccountCreateConfigurationMerchantCapabilitiesUsBankTransferPaymentsOptions`, `AccountCreateConfigurationMerchantCapabilitiesZipPaymentsOptions`, `AccountCreateConfigurationMerchantCardPaymentsDeclineOnOptions`, `AccountCreateConfigurationMerchantCardPaymentsOptions`, `AccountCreateConfigurationMerchantKonbiniPaymentsOptions`, `AccountCreateConfigurationMerchantKonbiniPaymentsSupportHoursOptions`, `AccountCreateConfigurationMerchantKonbiniPaymentsSupportOptions`, `AccountCreateConfigurationMerchantOptions`, `AccountCreateConfigurationMerchantScriptStatementDescriptorKanaOptions`, `AccountCreateConfigurationMerchantScriptStatementDescriptorKanjiOptions`, `AccountCreateConfigurationMerchantScriptStatementDescriptorOptions`, `AccountCreateConfigurationMerchantStatementDescriptorOptions`, `AccountCreateConfigurationMerchantSupportOptions`, `AccountCreateConfigurationOptions`, `AccountCreateConfigurationRecipientCapabilitiesOptions`, `AccountCreateConfigurationRecipientCapabilitiesStripeBalanceOptions`, `AccountCreateConfigurationRecipientCapabilitiesStripeBalanceStripeTransfersOptions`, `AccountCreateConfigurationRecipientOptions`, `AccountCreateDefaultsOptions`, `AccountCreateDefaultsProfileOptions`, `AccountCreateDefaultsResponsibilitiesOptions`, `AccountCreateIdentityAttestationsDirectorshipDeclarationOptions`, `AccountCreateIdentityAttestationsOptions`, `AccountCreateIdentityAttestationsOwnershipDeclarationOptions`, `AccountCreateIdentityAttestationsPersonsProvidedOptions`, `AccountCreateIdentityAttestationsRepresentativeDeclarationOptions`, `AccountCreateIdentityAttestationsTermsOfServiceAccountOptions`, `AccountCreateIdentityAttestationsTermsOfServiceOptions`, `AccountCreateIdentityBusinessDetailsAnnualRevenueOptions`, `AccountCreateIdentityBusinessDetailsDocumentsBankAccountOwnershipVerificationOptions`, `AccountCreateIdentityBusinessDetailsDocumentsCompanyLicenseOptions`, `AccountCreateIdentityBusinessDetailsDocumentsCompanyMemorandumOfAssociationOptions`, `AccountCreateIdentityBusinessDetailsDocumentsCompanyMinisterialDecreeOptions`, `AccountCreateIdentityBusinessDetailsDocumentsCompanyRegistrationVerificationOptions`, `AccountCreateIdentityBusinessDetailsDocumentsCompanyTaxIdVerificationOptions`, `AccountCreateIdentityBusinessDetailsDocumentsOptions`, `AccountCreateIdentityBusinessDetailsDocumentsPrimaryVerificationFrontBackOptions`, `AccountCreateIdentityBusinessDetailsDocumentsPrimaryVerificationOptions`, `AccountCreateIdentityBusinessDetailsDocumentsProofOfAddressOptions`, `AccountCreateIdentityBusinessDetailsDocumentsProofOfRegistrationOptions`, `AccountCreateIdentityBusinessDetailsDocumentsProofOfRegistrationSignerOptions`, `AccountCreateIdentityBusinessDetailsDocumentsProofOfUltimateBeneficialOwnershipOptions`, `AccountCreateIdentityBusinessDetailsDocumentsProofOfUltimateBeneficialOwnershipSignerOptions`, `AccountCreateIdentityBusinessDetailsIdNumberOptions`, `AccountCreateIdentityBusinessDetailsMonthlyEstimatedRevenueOptions`, `AccountCreateIdentityBusinessDetailsOptions`, `AccountCreateIdentityBusinessDetailsRegistrationDateOptions`, `AccountCreateIdentityBusinessDetailsScriptAddressesOptions`, `AccountCreateIdentityBusinessDetailsScriptNamesKanaOptions`, `AccountCreateIdentityBusinessDetailsScriptNamesKanjiOptions`, `AccountCreateIdentityBusinessDetailsScriptNamesOptions`, `AccountCreateIdentityIndividualAdditionalAddressOptions`, `AccountCreateIdentityIndividualAdditionalNameOptions`, `AccountCreateIdentityIndividualDateOfBirthOptions`, `AccountCreateIdentityIndividualDocumentsCompanyAuthorizationOptions`, `AccountCreateIdentityIndividualDocumentsOptions`, `AccountCreateIdentityIndividualDocumentsPassportOptions`, `AccountCreateIdentityIndividualDocumentsPrimaryVerificationFrontBackOptions`, `AccountCreateIdentityIndividualDocumentsPrimaryVerificationOptions`, `AccountCreateIdentityIndividualDocumentsSecondaryVerificationFrontBackOptions`, `AccountCreateIdentityIndividualDocumentsSecondaryVerificationOptions`, `AccountCreateIdentityIndividualDocumentsVisaOptions`, `AccountCreateIdentityIndividualIdNumberOptions`, `AccountCreateIdentityIndividualOptions`, `AccountCreateIdentityIndividualRelationshipOptions`, `AccountCreateIdentityIndividualScriptAddressesOptions`, `AccountCreateIdentityIndividualScriptNamesKanaOptions`, `AccountCreateIdentityIndividualScriptNamesKanjiOptions`, `AccountCreateIdentityIndividualScriptNamesOptions`, `AccountCreateIdentityOptions`, `AccountCreateOptions`, `AccountDefaults`, `AccountDefaultsProfile`, `AccountDefaultsResponsibilities`, `AccountFutureRequirements`, `AccountFutureRequirementsEntry`, `AccountFutureRequirementsEntryError`, `AccountFutureRequirementsEntryImpact`, `AccountFutureRequirementsEntryImpactRestrictsCapability`, `AccountFutureRequirementsEntryImpactRestrictsCapabilityDeadline`, `AccountFutureRequirementsEntryMinimumDeadline`, `AccountFutureRequirementsEntryReference`, `AccountFutureRequirementsEntryRequestedReason`, `AccountFutureRequirementsSummary`, `AccountFutureRequirementsSummaryMinimumDeadline`, `AccountGetOptions`, `AccountIdentity`, `AccountIdentityAttestations`, `AccountIdentityAttestationsDirectorshipDeclaration`, `AccountIdentityAttestationsOwnershipDeclaration`, `AccountIdentityAttestationsPersonsProvided`, `AccountIdentityAttestationsRepresentativeDeclaration`, `AccountIdentityAttestationsTermsOfService`, `AccountIdentityAttestationsTermsOfServiceAccount`, `AccountIdentityBusinessDetails`, `AccountIdentityBusinessDetailsAddress`, `AccountIdentityBusinessDetailsAnnualRevenue`, `AccountIdentityBusinessDetailsDocuments`, `AccountIdentityBusinessDetailsDocumentsBankAccountOwnershipVerification`, `AccountIdentityBusinessDetailsDocumentsCompanyLicense`, `AccountIdentityBusinessDetailsDocumentsCompanyMemorandumOfAssociation`, `AccountIdentityBusinessDetailsDocumentsCompanyMinisterialDecree`, `AccountIdentityBusinessDetailsDocumentsCompanyRegistrationVerification`, `AccountIdentityBusinessDetailsDocumentsCompanyTaxIdVerification`, `AccountIdentityBusinessDetailsDocumentsPrimaryVerification`, `AccountIdentityBusinessDetailsDocumentsPrimaryVerificationFrontBack`, `AccountIdentityBusinessDetailsDocumentsProofOfAddress`, `AccountIdentityBusinessDetailsDocumentsProofOfRegistration`, `AccountIdentityBusinessDetailsDocumentsProofOfRegistrationSigner`, `AccountIdentityBusinessDetailsDocumentsProofOfUltimateBeneficialOwnership`, `AccountIdentityBusinessDetailsDocumentsProofOfUltimateBeneficialOwnershipSigner`, `AccountIdentityBusinessDetailsIdNumber`, `AccountIdentityBusinessDetailsMonthlyEstimatedRevenue`, `AccountIdentityBusinessDetailsRegistrationDate`, `AccountIdentityBusinessDetailsScriptAddresses`, `AccountIdentityBusinessDetailsScriptAddressesKana`, `AccountIdentityBusinessDetailsScriptAddressesKanji`, `AccountIdentityBusinessDetailsScriptNames`, `AccountIdentityBusinessDetailsScriptNamesKana`, `AccountIdentityBusinessDetailsScriptNamesKanji`, `AccountIdentityIndividual`, `AccountIdentityIndividualAdditionalAddress`, `AccountIdentityIndividualAdditionalName`, `AccountIdentityIndividualAdditionalTermsOfService`, `AccountIdentityIndividualAdditionalTermsOfServiceAccount`, `AccountIdentityIndividualAddress`, `AccountIdentityIndividualDateOfBirth`, `AccountIdentityIndividualDocuments`, `AccountIdentityIndividualDocumentsCompanyAuthorization`, `AccountIdentityIndividualDocumentsPassport`, `AccountIdentityIndividualDocumentsPrimaryVerification`, `AccountIdentityIndividualDocumentsPrimaryVerificationFrontBack`, `AccountIdentityIndividualDocumentsSecondaryVerification`, `AccountIdentityIndividualDocumentsSecondaryVerificationFrontBack`, `AccountIdentityIndividualDocumentsVisa`, `AccountIdentityIndividualIdNumber`, `AccountIdentityIndividualRelationship`, `AccountIdentityIndividualScriptAddresses`, `AccountIdentityIndividualScriptAddressesKana`, `AccountIdentityIndividualScriptAddressesKanji`, `AccountIdentityIndividualScriptNames`, `AccountIdentityIndividualScriptNamesKana`, `AccountIdentityIndividualScriptNamesKanji`, `AccountLink`, `AccountLinkCreateOptions`, `AccountLinkCreateUseCaseAccountOnboardingCollectionOptionsOptions`, `AccountLinkCreateUseCaseAccountOnboardingOptions`, `AccountLinkCreateUseCaseAccountUpdateCollectionOptionsOptions`, `AccountLinkCreateUseCaseAccountUpdateOptions`, `AccountLinkCreateUseCaseOptions`, `AccountLinkService`, `AccountLinkUseCase`, `AccountLinkUseCaseAccountOnboarding`, `AccountLinkUseCaseAccountOnboardingCollectionOptions`, `AccountLinkUseCaseAccountUpdate`, `AccountLinkUseCaseAccountUpdateCollectionOptions`, `AccountListOptions`, `AccountPerson`, `AccountPersonAdditionalAddress`, `AccountPersonAdditionalName`, `AccountPersonAdditionalTermsOfService`, `AccountPersonAdditionalTermsOfServiceAccount`, `AccountPersonAddress`, `AccountPersonDateOfBirth`, `AccountPersonDocuments`, `AccountPersonDocumentsCompanyAuthorization`, `AccountPersonDocumentsPassport`, `AccountPersonDocumentsPrimaryVerification`, `AccountPersonDocumentsPrimaryVerificationFrontBack`, `AccountPersonDocumentsSecondaryVerification`, `AccountPersonDocumentsSecondaryVerificationFrontBack`, `AccountPersonDocumentsVisa`, `AccountPersonIdNumber`, `AccountPersonRelationship`, `AccountPersonScriptAddresses`, `AccountPersonScriptAddressesKana`, `AccountPersonScriptAddressesKanji`, `AccountPersonScriptNames`, `AccountPersonScriptNamesKana`, `AccountPersonScriptNamesKanji`, `AccountPersonToken`, `AccountRequirements`, `AccountRequirementsEntry`, `AccountRequirementsEntryError`, `AccountRequirementsEntryImpact`, `AccountRequirementsEntryImpactRestrictsCapability`, `AccountRequirementsEntryImpactRestrictsCapabilityDeadline`, `AccountRequirementsEntryMinimumDeadline`, `AccountRequirementsEntryReference`, `AccountRequirementsEntryRequestedReason`, `AccountRequirementsSummary`, `AccountRequirementsSummaryMinimumDeadline`, `AccountService`, `AccountToken`, `AccountTokenCreateIdentityAttestationsDirectorshipDeclarationOptions`, `AccountTokenCreateIdentityAttestationsOptions`, `AccountTokenCreateIdentityAttestationsOwnershipDeclarationOptions`, `AccountTokenCreateIdentityAttestationsPersonsProvidedOptions`, `AccountTokenCreateIdentityAttestationsRepresentativeDeclarationOptions`, `AccountTokenCreateIdentityAttestationsTermsOfServiceAccountOptions`, `AccountTokenCreateIdentityAttestationsTermsOfServiceOptions`, `AccountTokenCreateIdentityBusinessDetailsAnnualRevenueOptions`, `AccountTokenCreateIdentityBusinessDetailsDocumentsBankAccountOwnershipVerificationOptions`, `AccountTokenCreateIdentityBusinessDetailsDocumentsCompanyLicenseOptions`, `AccountTokenCreateIdentityBusinessDetailsDocumentsCompanyMemorandumOfAssociationOptions`, `AccountTokenCreateIdentityBusinessDetailsDocumentsCompanyMinisterialDecreeOptions`, `AccountTokenCreateIdentityBusinessDetailsDocumentsCompanyRegistrationVerificationOptions`, `AccountTokenCreateIdentityBusinessDetailsDocumentsCompanyTaxIdVerificationOptions`, `AccountTokenCreateIdentityBusinessDetailsDocumentsOptions`, `AccountTokenCreateIdentityBusinessDetailsDocumentsPrimaryVerificationFrontBackOptions`, `AccountTokenCreateIdentityBusinessDetailsDocumentsPrimaryVerificationOptions`, `AccountTokenCreateIdentityBusinessDetailsDocumentsProofOfAddressOptions`, `AccountTokenCreateIdentityBusinessDetailsDocumentsProofOfRegistrationOptions`, `AccountTokenCreateIdentityBusinessDetailsDocumentsProofOfRegistrationSignerOptions`, `AccountTokenCreateIdentityBusinessDetailsDocumentsProofOfUltimateBeneficialOwnershipOptions`, `AccountTokenCreateIdentityBusinessDetailsDocumentsProofOfUltimateBeneficialOwnershipSignerOptions`, `AccountTokenCreateIdentityBusinessDetailsIdNumberOptions`, `AccountTokenCreateIdentityBusinessDetailsMonthlyEstimatedRevenueOptions`, `AccountTokenCreateIdentityBusinessDetailsOptions`, `AccountTokenCreateIdentityBusinessDetailsRegistrationDateOptions`, `AccountTokenCreateIdentityBusinessDetailsScriptAddressesOptions`, `AccountTokenCreateIdentityBusinessDetailsScriptNamesKanaOptions`, `AccountTokenCreateIdentityBusinessDetailsScriptNamesKanjiOptions`, `AccountTokenCreateIdentityBusinessDetailsScriptNamesOptions`, `AccountTokenCreateIdentityIndividualAdditionalAddressOptions`, `AccountTokenCreateIdentityIndividualAdditionalNameOptions`, `AccountTokenCreateIdentityIndividualDateOfBirthOptions`, `AccountTokenCreateIdentityIndividualDocumentsCompanyAuthorizationOptions`, `AccountTokenCreateIdentityIndividualDocumentsOptions`, `AccountTokenCreateIdentityIndividualDocumentsPassportOptions`, `AccountTokenCreateIdentityIndividualDocumentsPrimaryVerificationFrontBackOptions`, `AccountTokenCreateIdentityIndividualDocumentsPrimaryVerificationOptions`, `AccountTokenCreateIdentityIndividualDocumentsSecondaryVerificationFrontBackOptions`, `AccountTokenCreateIdentityIndividualDocumentsSecondaryVerificationOptions`, `AccountTokenCreateIdentityIndividualDocumentsVisaOptions`, `AccountTokenCreateIdentityIndividualIdNumberOptions`, `AccountTokenCreateIdentityIndividualOptions`, `AccountTokenCreateIdentityIndividualRelationshipOptions`, `AccountTokenCreateIdentityIndividualScriptAddressesOptions`, `AccountTokenCreateIdentityIndividualScriptNamesKanaOptions`, `AccountTokenCreateIdentityIndividualScriptNamesKanjiOptions`, `AccountTokenCreateIdentityIndividualScriptNamesOptions`, `AccountTokenCreateIdentityOptions`, `AccountTokenCreateOptions`, `AccountTokenService`, `AccountUpdateConfigurationCustomerAutomaticIndirectTaxOptions`, `AccountUpdateConfigurationCustomerBillingInvoiceCustomFieldOptions`, `AccountUpdateConfigurationCustomerBillingInvoiceOptions`, `AccountUpdateConfigurationCustomerBillingInvoiceRenderingOptions`, `AccountUpdateConfigurationCustomerBillingOptions`, `AccountUpdateConfigurationCustomerCapabilitiesAutomaticIndirectTaxOptions`, `AccountUpdateConfigurationCustomerCapabilitiesOptions`, `AccountUpdateConfigurationCustomerOptions`, `AccountUpdateConfigurationCustomerShippingOptions`, `AccountUpdateConfigurationMerchantBacsDebitPaymentsOptions`, `AccountUpdateConfigurationMerchantBrandingOptions`, `AccountUpdateConfigurationMerchantCapabilitiesAchDebitPaymentsOptions`, `AccountUpdateConfigurationMerchantCapabilitiesAcssDebitPaymentsOptions`, `AccountUpdateConfigurationMerchantCapabilitiesAffirmPaymentsOptions`, `AccountUpdateConfigurationMerchantCapabilitiesAfterpayClearpayPaymentsOptions`, `AccountUpdateConfigurationMerchantCapabilitiesAlmaPaymentsOptions`, `AccountUpdateConfigurationMerchantCapabilitiesAmazonPayPaymentsOptions`, `AccountUpdateConfigurationMerchantCapabilitiesAuBecsDebitPaymentsOptions`, `AccountUpdateConfigurationMerchantCapabilitiesBacsDebitPaymentsOptions`, `AccountUpdateConfigurationMerchantCapabilitiesBancontactPaymentsOptions`, `AccountUpdateConfigurationMerchantCapabilitiesBlikPaymentsOptions`, `AccountUpdateConfigurationMerchantCapabilitiesBoletoPaymentsOptions`, `AccountUpdateConfigurationMerchantCapabilitiesCardPaymentsOptions`, `AccountUpdateConfigurationMerchantCapabilitiesCartesBancairesPaymentsOptions`, `AccountUpdateConfigurationMerchantCapabilitiesCashappPaymentsOptions`, `AccountUpdateConfigurationMerchantCapabilitiesEpsPaymentsOptions`, `AccountUpdateConfigurationMerchantCapabilitiesFpxPaymentsOptions`, `AccountUpdateConfigurationMerchantCapabilitiesGbBankTransferPaymentsOptions`, `AccountUpdateConfigurationMerchantCapabilitiesGrabpayPaymentsOptions`, `AccountUpdateConfigurationMerchantCapabilitiesIdealPaymentsOptions`, `AccountUpdateConfigurationMerchantCapabilitiesJcbPaymentsOptions`, `AccountUpdateConfigurationMerchantCapabilitiesJpBankTransferPaymentsOptions`, `AccountUpdateConfigurationMerchantCapabilitiesKakaoPayPaymentsOptions`, `AccountUpdateConfigurationMerchantCapabilitiesKlarnaPaymentsOptions`, `AccountUpdateConfigurationMerchantCapabilitiesKonbiniPaymentsOptions`, `AccountUpdateConfigurationMerchantCapabilitiesKrCardPaymentsOptions`, `AccountUpdateConfigurationMerchantCapabilitiesLinkPaymentsOptions`, `AccountUpdateConfigurationMerchantCapabilitiesMobilepayPaymentsOptions`, `AccountUpdateConfigurationMerchantCapabilitiesMultibancoPaymentsOptions`, `AccountUpdateConfigurationMerchantCapabilitiesMxBankTransferPaymentsOptions`, `AccountUpdateConfigurationMerchantCapabilitiesNaverPayPaymentsOptions`, `AccountUpdateConfigurationMerchantCapabilitiesOptions`, `AccountUpdateConfigurationMerchantCapabilitiesOxxoPaymentsOptions`, `AccountUpdateConfigurationMerchantCapabilitiesP24PaymentsOptions`, `AccountUpdateConfigurationMerchantCapabilitiesPayByBankPaymentsOptions`, `AccountUpdateConfigurationMerchantCapabilitiesPaycoPaymentsOptions`, `AccountUpdateConfigurationMerchantCapabilitiesPaynowPaymentsOptions`, `AccountUpdateConfigurationMerchantCapabilitiesPromptpayPaymentsOptions`, `AccountUpdateConfigurationMerchantCapabilitiesRevolutPayPaymentsOptions`, `AccountUpdateConfigurationMerchantCapabilitiesSamsungPayPaymentsOptions`, `AccountUpdateConfigurationMerchantCapabilitiesSepaBankTransferPaymentsOptions`, `AccountUpdateConfigurationMerchantCapabilitiesSepaDebitPaymentsOptions`, `AccountUpdateConfigurationMerchantCapabilitiesSwishPaymentsOptions`, `AccountUpdateConfigurationMerchantCapabilitiesTwintPaymentsOptions`, `AccountUpdateConfigurationMerchantCapabilitiesUsBankTransferPaymentsOptions`, `AccountUpdateConfigurationMerchantCapabilitiesZipPaymentsOptions`, `AccountUpdateConfigurationMerchantCardPaymentsDeclineOnOptions`, `AccountUpdateConfigurationMerchantCardPaymentsOptions`, `AccountUpdateConfigurationMerchantKonbiniPaymentsOptions`, `AccountUpdateConfigurationMerchantKonbiniPaymentsSupportHoursOptions`, `AccountUpdateConfigurationMerchantKonbiniPaymentsSupportOptions`, `AccountUpdateConfigurationMerchantOptions`, `AccountUpdateConfigurationMerchantScriptStatementDescriptorKanaOptions`, `AccountUpdateConfigurationMerchantScriptStatementDescriptorKanjiOptions`, `AccountUpdateConfigurationMerchantScriptStatementDescriptorOptions`, `AccountUpdateConfigurationMerchantStatementDescriptorOptions`, `AccountUpdateConfigurationMerchantSupportOptions`, `AccountUpdateConfigurationOptions`, `AccountUpdateConfigurationRecipientCapabilitiesOptions`, `AccountUpdateConfigurationRecipientCapabilitiesStripeBalanceOptions`, `AccountUpdateConfigurationRecipientCapabilitiesStripeBalanceStripeTransfersOptions`, `AccountUpdateConfigurationRecipientOptions`, `AccountUpdateDefaultsOptions`, `AccountUpdateDefaultsProfileOptions`, `AccountUpdateDefaultsResponsibilitiesOptions`, `AccountUpdateIdentityAttestationsDirectorshipDeclarationOptions`, `AccountUpdateIdentityAttestationsOptions`, `AccountUpdateIdentityAttestationsOwnershipDeclarationOptions`, `AccountUpdateIdentityAttestationsPersonsProvidedOptions`, `AccountUpdateIdentityAttestationsRepresentativeDeclarationOptions`, `AccountUpdateIdentityAttestationsTermsOfServiceAccountOptions`, `AccountUpdateIdentityAttestationsTermsOfServiceCryptoStorerOptions`, `AccountUpdateIdentityAttestationsTermsOfServiceOptions`, `AccountUpdateIdentityAttestationsTermsOfServiceStorerOptions`, `AccountUpdateIdentityBusinessDetailsAnnualRevenueOptions`, `AccountUpdateIdentityBusinessDetailsDocumentsBankAccountOwnershipVerificationOptions`, `AccountUpdateIdentityBusinessDetailsDocumentsCompanyLicenseOptions`, `AccountUpdateIdentityBusinessDetailsDocumentsCompanyMemorandumOfAssociationOptions`, `AccountUpdateIdentityBusinessDetailsDocumentsCompanyMinisterialDecreeOptions`, `AccountUpdateIdentityBusinessDetailsDocumentsCompanyRegistrationVerificationOptions`, `AccountUpdateIdentityBusinessDetailsDocumentsCompanyTaxIdVerificationOptions`, `AccountUpdateIdentityBusinessDetailsDocumentsOptions`, `AccountUpdateIdentityBusinessDetailsDocumentsPrimaryVerificationFrontBackOptions`, `AccountUpdateIdentityBusinessDetailsDocumentsPrimaryVerificationOptions`, `AccountUpdateIdentityBusinessDetailsDocumentsProofOfAddressOptions`, `AccountUpdateIdentityBusinessDetailsDocumentsProofOfRegistrationOptions`, `AccountUpdateIdentityBusinessDetailsDocumentsProofOfRegistrationSignerOptions`, `AccountUpdateIdentityBusinessDetailsDocumentsProofOfUltimateBeneficialOwnershipOptions`, `AccountUpdateIdentityBusinessDetailsDocumentsProofOfUltimateBeneficialOwnershipSignerOptions`, `AccountUpdateIdentityBusinessDetailsIdNumberOptions`, `AccountUpdateIdentityBusinessDetailsMonthlyEstimatedRevenueOptions`, `AccountUpdateIdentityBusinessDetailsOptions`, `AccountUpdateIdentityBusinessDetailsRegistrationDateOptions`, `AccountUpdateIdentityBusinessDetailsScriptAddressesOptions`, `AccountUpdateIdentityBusinessDetailsScriptNamesKanaOptions`, `AccountUpdateIdentityBusinessDetailsScriptNamesKanjiOptions`, `AccountUpdateIdentityBusinessDetailsScriptNamesOptions`, `AccountUpdateIdentityIndividualAdditionalAddressOptions`, `AccountUpdateIdentityIndividualAdditionalNameOptions`, `AccountUpdateIdentityIndividualDateOfBirthOptions`, `AccountUpdateIdentityIndividualDocumentsCompanyAuthorizationOptions`, `AccountUpdateIdentityIndividualDocumentsOptions`, `AccountUpdateIdentityIndividualDocumentsPassportOptions`, `AccountUpdateIdentityIndividualDocumentsPrimaryVerificationFrontBackOptions`, `AccountUpdateIdentityIndividualDocumentsPrimaryVerificationOptions`, `AccountUpdateIdentityIndividualDocumentsSecondaryVerificationFrontBackOptions`, `AccountUpdateIdentityIndividualDocumentsSecondaryVerificationOptions`, `AccountUpdateIdentityIndividualDocumentsVisaOptions`, `AccountUpdateIdentityIndividualIdNumberOptions`, `AccountUpdateIdentityIndividualOptions`, `AccountUpdateIdentityIndividualRelationshipOptions`, `AccountUpdateIdentityIndividualScriptAddressesOptions`, `AccountUpdateIdentityIndividualScriptNamesKanaOptions`, `AccountUpdateIdentityIndividualScriptNamesKanjiOptions`, `AccountUpdateIdentityIndividualScriptNamesOptions`, `AccountUpdateIdentityOptions`, `AccountUpdateOptions`, `Event`, `EventDestination`, `EventDestinationAmazonEventbridge`, `EventDestinationAzureEventGrid`, `EventDestinationCreateAmazonEventbridgeOptions`, `EventDestinationCreateAzureEventGridOptions`, `EventDestinationCreateOptions`, `EventDestinationCreateWebhookEndpointOptions`, `EventDestinationGetOptions`, `EventDestinationListOptions`, `EventDestinationService`, `EventDestinationStatusDetails`, `EventDestinationStatusDetailsDisabled`, `EventDestinationUpdateOptions`, `EventDestinationUpdateWebhookEndpointOptions`, `EventDestinationWebhookEndpoint`, `EventListCreatedOptions`, `EventListOptions`, `EventNotification`, `EventNotificationReason`, `EventNotificationReasonRequest`, `EventReason`, `EventReasonRequest`, `EventRelatedObject`, `EventService`
- **Stripe.V2.Core.Accounts**: `PersonCreateAdditionalAddressOptions`, `PersonCreateAdditionalNameOptions`, `PersonCreateAdditionalTermsOfServiceAccountOptions`, `PersonCreateAdditionalTermsOfServiceOptions`, `PersonCreateDateOfBirthOptions`, `PersonCreateDocumentsCompanyAuthorizationOptions`, `PersonCreateDocumentsOptions`, `PersonCreateDocumentsPassportOptions`, `PersonCreateDocumentsPrimaryVerificationFrontBackOptions`, `PersonCreateDocumentsPrimaryVerificationOptions`, `PersonCreateDocumentsSecondaryVerificationFrontBackOptions`, `PersonCreateDocumentsSecondaryVerificationOptions`, `PersonCreateDocumentsVisaOptions`, `PersonCreateIdNumberOptions`, `PersonCreateOptions`, `PersonCreateRelationshipOptions`, `PersonCreateScriptAddressesOptions`, `PersonCreateScriptNamesKanaOptions`, `PersonCreateScriptNamesKanjiOptions`, `PersonCreateScriptNamesOptions`, `PersonService`, `PersonTokenCreateAdditionalAddressOptions`, `PersonTokenCreateAdditionalNameOptions`, `PersonTokenCreateAdditionalTermsOfServiceAccountOptions`, `PersonTokenCreateAdditionalTermsOfServiceOptions`, `PersonTokenCreateDateOfBirthOptions`, `PersonTokenCreateDocumentsCompanyAuthorizationOptions`, `PersonTokenCreateDocumentsOptions`, `PersonTokenCreateDocumentsPassportOptions`, `PersonTokenCreateDocumentsPrimaryVerificationFrontBackOptions`, `PersonTokenCreateDocumentsPrimaryVerificationOptions`, `PersonTokenCreateDocumentsSecondaryVerificationFrontBackOptions`, `PersonTokenCreateDocumentsSecondaryVerificationOptions`, `PersonTokenCreateDocumentsVisaOptions`, `PersonTokenCreateIdNumberOptions`, `PersonTokenCreateOptions`, `PersonTokenCreateRelationshipOptions`, `PersonTokenCreateScriptAddressesOptions`, `PersonTokenCreateScriptNamesKanaOptions`, `PersonTokenCreateScriptNamesKanjiOptions`, `PersonTokenCreateScriptNamesOptions`, `PersonTokenService`, `PersonUpdateAdditionalAddressOptions`, `PersonUpdateAdditionalNameOptions`, `PersonUpdateAdditionalTermsOfServiceAccountOptions`, `PersonUpdateAdditionalTermsOfServiceOptions`, `PersonUpdateDateOfBirthOptions`, `PersonUpdateDocumentsCompanyAuthorizationOptions`, `PersonUpdateDocumentsOptions`, `PersonUpdateDocumentsPassportOptions`, `PersonUpdateDocumentsPrimaryVerificationFrontBackOptions`, `PersonUpdateDocumentsPrimaryVerificationOptions`, `PersonUpdateDocumentsSecondaryVerificationFrontBackOptions`, `PersonUpdateDocumentsSecondaryVerificationOptions`, `PersonUpdateDocumentsVisaOptions`, `PersonUpdateIdNumberOptions`, `PersonUpdateOptions`, `PersonUpdateRelationshipOptions`, `PersonUpdateScriptAddressesOptions`, `PersonUpdateScriptNamesKanaOptions`, `PersonUpdateScriptNamesKanjiOptions`, `PersonUpdateScriptNamesOptions`

## Service index

_165 service classes. Operation names are listed without their `Async` suffix; every operation also has an `…Async` overload._

### namespace `Stripe`

- **AccountCapabilityService**: `Get`, `List`, `Update`
- **AccountExternalAccountService**: `Create`, `Delete`, `Get`, `List`, `ListAutoPaging`, `Update`
- **AccountLinkService**: `Create`
- **AccountLoginLinkService**: `Create`
- **AccountPersonService**: `Create`, `Delete`, `Get`, `List`, `ListAutoPaging`, `Update`
- **AccountService**: `Create`, `Delete`, `Get`, `List`, `ListAutoPaging`, `Reject`, `Update`
- **AccountSessionService**: `Create`
- **ApplePayDomainService**: `Create`, `Delete`, `Get`, `List`, `ListAutoPaging`
- **ApplicationFeeRefundService**: `Create`, `Get`, `List`, `ListAutoPaging`, `Update`
- **ApplicationFeeService**: `Get`, `List`, `ListAutoPaging`
- **BalanceService**: `Get`
- **BalanceSettingsService**: `Get`, `Update`
- **BalanceTransactionService**: `Get`, `List`, `ListAutoPaging`
- **ChargeService**: `Capture`, `Create`, `Get`, `List`, `ListAutoPaging`, `Search`, `SearchAutoPaging`, `Update`
- **ConfirmationTokenService**: `Get`
- **CountrySpecService**: `Get`, `List`, `ListAutoPaging`
- **CouponService**: `Create`, `Delete`, `Get`, `List`, `ListAutoPaging`, `Update`
- **CreditNotePreviewLinesService**: `List`, `ListAutoPaging`
- **CustomerBalanceTransactionService**: `Create`, `Get`, `List`, `ListAutoPaging`, `Update`
- **CustomerCashBalanceService**: `Get`, `Update`
- **CustomerCashBalanceTransactionService**: `Get`, `List`, `ListAutoPaging`
- **CustomerFundingInstructionsService**: `Create`
- **CustomerPaymentMethodService**: `Get`, `List`, `ListAutoPaging`
- **CustomerPaymentSourceService**: `Create`, `Delete`, `Get`, `List`, `ListAutoPaging`, `Update`, `Verify`
- **CustomerService**: `Create`, `CreateFundingInstructions`, `Delete`, `DeleteDiscount`, `Get`, `List`, `ListAutoPaging`, `ListPaymentMethods`, `ListPaymentMethodsAutoPaging`, `RetrievePaymentMethod`, `Search`, `SearchAutoPaging`, `Update`
- **CustomerSessionService**: `Create`
- **CustomerTaxIdService**: `Create`, `Delete`, `Get`, `List`, `ListAutoPaging`
- **DisputeService**: `Close`, `Get`, `List`, `ListAutoPaging`, `Update`
- **EventService**: `Get`, `List`, `ListAutoPaging`
- **FileLinkService**: `Create`, `Get`, `List`, `ListAutoPaging`, `Update`
- **FileService**: `Create`, `Get`, `List`, `ListAutoPaging`
- **InvoiceItemService**: `Create`, `Delete`, `Get`, `List`, `ListAutoPaging`, `Update`
- **InvoiceLineItemService**: `List`, `ListAutoPaging`, `Update`
- **InvoicePaymentService**: `Get`, `List`, `ListAutoPaging`
- **InvoiceRenderingTemplateService**: `Archive`, `Get`, `List`, `ListAutoPaging`, `Unarchive`
- **InvoiceService**: `AddLines`, `AttachPayment`, `Create`, `CreatePreview`, `Delete`, `FinalizeInvoice`, `Get`, `List`, `ListAutoPaging`, `ListLineItems`, `ListLineItemsAutoPaging`, `MarkUncollectible`, `Pay`, `RemoveLines`, `Search`, `SearchAutoPaging`, `SendInvoice`, `Update`, `UpdateLines`, `VoidInvoice`
- **MandateService**: `Get`
- **PaymentAttemptRecordService**: `Get`, `List`, `ListAutoPaging`
- **PaymentIntentAmountDetailsLineItemService**: `List`, `ListAutoPaging`
- **PaymentIntentService**: `ApplyCustomerBalance`, `Cancel`, `Capture`, `Confirm`, `Create`, `Get`, `IncrementAuthorization`, `List`, `ListAutoPaging`, `Search`, `SearchAutoPaging`, `Update`, `VerifyMicrodeposits`
- **PaymentLinkLineItemService**: `List`, `ListAutoPaging`
- **PaymentLinkService**: `Create`, `Get`, `List`, `ListAutoPaging`, `ListLineItems`, `ListLineItemsAutoPaging`, `Update`
- **PaymentMethodConfigurationService**: `Create`, `Get`, `List`, `ListAutoPaging`, `Update`
- **PaymentMethodDomainService**: `Create`, `Get`, `List`, `ListAutoPaging`, `Update`, `Validate`
- **PaymentMethodService**: `Attach`, `Create`, `Detach`, `Get`, `List`, `ListAutoPaging`, `Update`
- **PaymentRecordService**: `Get`, `ReportPayment`, `ReportPaymentAttempt`, `ReportPaymentAttemptCanceled`, `ReportPaymentAttemptFailed`, `ReportPaymentAttemptGuaranteed`, `ReportPaymentAttemptInformational`, `ReportRefund`
- **PayoutService**: `Cancel`, `Create`, `Get`, `List`, `ListAutoPaging`, `Reverse`, `Update`
- **PlanService**: `Create`, `Delete`, `Get`, `List`, `ListAutoPaging`, `Update`
- **PriceService**: `Create`, `Get`, `List`, `ListAutoPaging`, `Search`, `SearchAutoPaging`, `Update`
- **ProductFeatureService**: `Create`, `Delete`, `Get`, `List`, `ListAutoPaging`
- **ProductService**: `Create`, `Delete`, `Get`, `List`, `ListAutoPaging`, `Search`, `SearchAutoPaging`, `Update`
- **PromotionCodeService**: `Create`, `Get`, `List`, `ListAutoPaging`, `Update`
- **QuoteComputedUpfrontLineItemsService**: `List`, `ListAutoPaging`
- **QuoteLineItemService**: `List`, `ListAutoPaging`
- **QuoteService**: `Accept`, `Cancel`, `Create`, `FinalizeQuote`, `Get`, `List`, `ListAutoPaging`, `ListComputedUpfrontLineItems`, `ListComputedUpfrontLineItemsAutoPaging`, `ListLineItems`, `ListLineItemsAutoPaging`, `Pdf`, `Update`
- **RefundService**: `Cancel`, `Create`, `Get`, `List`, `ListAutoPaging`, `Update`
- **ReviewService**: `Approve`, `Get`, `List`, `ListAutoPaging`
- **Service**: `#ctor`
- **SetupAttemptService**: `List`, `ListAutoPaging`
- **SetupIntentService**: `Cancel`, `Confirm`, `Create`, `Get`, `List`, `ListAutoPaging`, `Update`, `VerifyMicrodeposits`
- **ShippingRateService**: `Create`, `Get`, `List`, `ListAutoPaging`, `Update`
- **SourceTransactionService**: `List`, `ListAutoPaging`
- **SubscriptionItemService**: `Create`, `Delete`, `Get`, `List`, `ListAutoPaging`, `Update`
- **SubscriptionScheduleService**: `Cancel`, `Create`, `Get`, `List`, `ListAutoPaging`, `Release`, `Update`
- **SubscriptionService**: `Cancel`, `Create`, `DeleteDiscount`, `Get`, `List`, `ListAutoPaging`, `Migrate`, `Resume`, `Search`, `SearchAutoPaging`, `Update`
- **TaxCodeService**: `Get`, `List`, `ListAutoPaging`
- **TaxIdService**: `Create`, `Delete`, `Get`, `List`, `ListAutoPaging`
- **TaxRateService**: `Create`, `Get`, `List`, `ListAutoPaging`, `Update`
- **TokenService**: `Create`, `Get`
- **TopupService**: `Cancel`, `Create`, `Get`, `List`, `ListAutoPaging`, `Update`
- **TransferReversalService**: `Create`, `Get`, `List`, `ListAutoPaging`, `Update`
- **TransferService**: `Create`, `Get`, `List`, `ListAutoPaging`, `Update`
- **WebhookEndpointService**: `Create`, `Delete`, `Get`, `List`, `ListAutoPaging`, `Update`

### namespace `Stripe.Apps`

- **SecretService**: `Create`, `DeleteWhere`, `Find`, `List`, `ListAutoPaging`

### namespace `Stripe.Billing`

- **AlertService**: `Activate`, `Archive`, `Create`, `Deactivate`, `Get`, `List`, `ListAutoPaging`
- **CreditBalanceSummaryService**: `Get`
- **CreditBalanceTransactionService**: `Get`, `List`, `ListAutoPaging`
- **CreditGrantService**: `Create`, `Expire`, `Get`, `List`, `ListAutoPaging`, `Update`, `VoidGrant`
- **MeterEventAdjustmentService**: `Create`
- **MeterEventService**: `Create`
- **MeterEventSummaryService**: `List`, `ListAutoPaging`
- **MeterService**: `Create`, `Deactivate`, `Get`, `List`, `ListAutoPaging`, `Reactivate`, `Update`

### namespace `Stripe.BillingPortal`

- **ConfigurationService**: `Create`, `Get`, `List`, `ListAutoPaging`, `Update`
- **SessionService**: `Create`

### namespace `Stripe.Checkout`

- **SessionLineItemService**: `List`, `ListAutoPaging`
- **SessionService**: `Create`, `Expire`, `Get`, `List`, `ListAutoPaging`, `ListLineItems`, `ListLineItemsAutoPaging`, `Update`

### namespace `Stripe.Climate`

- **OrderService**: `Cancel`, `Create`, `Get`, `List`, `ListAutoPaging`, `Update`
- **ProductService**: `Get`, `List`, `ListAutoPaging`
- **SupplierService**: `Get`, `List`, `ListAutoPaging`

### namespace `Stripe.Entitlements`

- **ActiveEntitlementService**: `Get`, `List`, `ListAutoPaging`
- **FeatureService**: `Create`, `Get`, `List`, `ListAutoPaging`, `Update`

### namespace `Stripe.FinancialConnections`

- **AccountOwnerService**: `List`, `ListAutoPaging`
- **AccountService**: `Disconnect`, `Get`, `List`, `ListAutoPaging`, `ListOwners`, `ListOwnersAutoPaging`, `Refresh`, `Subscribe`, `Unsubscribe`
- **SessionService**: `Create`, `Get`
- **TransactionService**: `Get`, `List`, `ListAutoPaging`

### namespace `Stripe.Forwarding`

- **RequestService**: `Create`, `Get`, `List`, `ListAutoPaging`

### namespace `Stripe.Identity`

- **VerificationReportService**: `Get`, `List`, `ListAutoPaging`
- **VerificationSessionService**: `Cancel`, `Create`, `Get`, `List`, `ListAutoPaging`, `Redact`, `Update`

### namespace `Stripe.Issuing`

- **AuthorizationService**: `Approve`, `Decline`, `Get`, `List`, `ListAutoPaging`, `Update`
- **CardService**: `Create`, `Get`, `List`, `ListAutoPaging`, `Update`
- **CardholderService**: `Create`, `Get`, `List`, `ListAutoPaging`, `Update`
- **DisputeService**: `Create`, `Get`, `List`, `ListAutoPaging`, `Submit`, `Update`
- **PersonalizationDesignService**: `Create`, `Get`, `List`, `ListAutoPaging`, `Update`
- **PhysicalBundleService**: `Get`, `List`, `ListAutoPaging`
- **TokenService**: `Get`, `List`, `ListAutoPaging`, `Update`
- **TransactionService**: `Get`, `List`, `ListAutoPaging`, `Update`

### namespace `Stripe.Radar`

- **EarlyFraudWarningService**: `Get`, `List`, `ListAutoPaging`
- **PaymentEvaluationService**: `Create`
- **ValueListItemService**: `Create`, `Delete`, `Get`, `List`, `ListAutoPaging`
- **ValueListService**: `Create`, `Delete`, `Get`, `List`, `ListAutoPaging`, `Update`

### namespace `Stripe.Reporting`

- **ReportRunService**: `Create`, `Get`, `List`, `ListAutoPaging`
- **ReportTypeService**: `Get`, `List`

### namespace `Stripe.Sigma`

- **ScheduledQueryRunService**: `Get`, `List`, `ListAutoPaging`

### namespace `Stripe.Tax`

- **AssociationService**: `Find`
- **CalculationLineItemService**: `List`, `ListAutoPaging`
- **CalculationService**: `Create`, `Get`, `ListLineItems`, `ListLineItemsAutoPaging`
- **RegistrationService**: `Create`, `Get`, `List`, `ListAutoPaging`, `Update`
- **SettingsService**: `Get`, `Update`
- **TransactionLineItemService**: `List`, `ListAutoPaging`
- **TransactionService**: `CreateFromCalculation`, `CreateReversal`, `Get`, `ListLineItems`, `ListLineItemsAutoPaging`

### namespace `Stripe.Terminal`

- **ConfigurationService**: `Create`, `Delete`, `Get`, `List`, `ListAutoPaging`, `Update`
- **ConnectionTokenService**: `Create`
- **LocationService**: `Create`, `Delete`, `Get`, `List`, `ListAutoPaging`, `Update`
- **OnboardingLinkService**: `Create`
- **ReaderService**: `CancelAction`, `CollectInputs`, `CollectPaymentMethod`, `ConfirmPaymentIntent`, `Create`, `Delete`, `Get`, `List`, `ListAutoPaging`, `ProcessPaymentIntent`, `ProcessSetupIntent`, `RefundPayment`, `SetReaderDisplay`, `Update`

### namespace `Stripe.TestHelpers`

- **ConfirmationTokenService**: `Create`
- **CustomerService**: `FundCashBalance`
- **RefundService**: `Expire`
- **TestClockService**: `Advance`, `Create`, `Delete`, `Get`, `List`, `ListAutoPaging`

### namespace `Stripe.TestHelpers.Issuing`

- **AuthorizationService**: `Capture`, `Create`, `Expire`, `FinalizeAmount`, `Increment`, `Respond`, `Reverse`
- **CardService**: `DeliverCard`, `FailCard`, `ReturnCard`, `ShipCard`, `SubmitCard`
- **PersonalizationDesignService**: `Activate`, `Deactivate`, `Reject`
- **TransactionService**: `CreateForceCapture`, `CreateUnlinkedRefund`, `Refund`

### namespace `Stripe.TestHelpers.Terminal`

- **ReaderService**: `PresentPaymentMethod`, `SucceedInputCollection`, `TimeoutInputCollection`

### namespace `Stripe.TestHelpers.Treasury`

- **InboundTransferService**: `Fail`, `ReturnInboundTransfer`, `Succeed`
- **OutboundPaymentService**: `Fail`, `Post`, `ReturnOutboundPayment`, `Update`
- **OutboundTransferService**: `Fail`, `Post`, `ReturnOutboundTransfer`, `Update`
- **ReceivedCreditService**: `Create`
- **ReceivedDebitService**: `Create`

### namespace `Stripe.Treasury`

- **CreditReversalService**: `Create`, `Get`, `List`, `ListAutoPaging`
- **DebitReversalService**: `Create`, `Get`, `List`, `ListAutoPaging`
- **FinancialAccountFeaturesService**: `Get`, `Update`
- **FinancialAccountService**: `Close`, `Create`, `Get`, `List`, `ListAutoPaging`, `RetrieveFeatures`, `Update`, `UpdateFeatures`
- **InboundTransferService**: `Cancel`, `Create`, `Get`, `List`, `ListAutoPaging`
- **OutboundPaymentService**: `Cancel`, `Create`, `Get`, `List`, `ListAutoPaging`
- **OutboundTransferService**: `Cancel`, `Create`, `Get`, `List`, `ListAutoPaging`
- **ReceivedCreditService**: `Get`, `List`, `ListAutoPaging`
- **ReceivedDebitService**: `Get`, `List`, `ListAutoPaging`
- **TransactionEntryService**: `Get`, `List`, `ListAutoPaging`
- **TransactionService**: `Get`, `List`, `ListAutoPaging`

### namespace `Stripe.V2.Billing`

- **MeterEventAdjustmentService**: `Create`
- **MeterEventService**: `Create`
- **MeterEventSessionService**: `Create`
- **MeterEventStreamService**: `Create`

### namespace `Stripe.V2.Commerce.ProductCatalog`

- **ImportService**: `Create`, `Get`, `List`, `ListAutoPaging`

### namespace `Stripe.V2.Core`

- **AccountIdentityAttestationsTermsOfService**: _(no public operations)_
- **AccountIdentityIndividualAdditionalTermsOfService**: _(no public operations)_
- **AccountLinkService**: `Create`
- **AccountPersonAdditionalTermsOfService**: _(no public operations)_
- **AccountService**: `Close`, `Create`, `Get`, `List`, `ListAutoPaging`, `Update`
- **AccountTokenService**: `Create`, `Get`
- **EventDestinationService**: `Create`, `Delete`, `Disable`, `Enable`, `Get`, `List`, `ListAutoPaging`, `Ping`, `Update`
- **EventService**: `Get`, `List`, `ListAutoPaging`

### namespace `Stripe.V2.Core.Accounts`

- **PersonService**: `Create`, `Delete`, `Get`, `List`, `ListAutoPaging`, `Update`
- **PersonTokenService**: `Create`, `Get`

## Core resource detail

_Full member listings for the high-traffic resources. Use **only** the properties and options shown here for these resources._

### StripeClient

#### `StripeClient`

A Stripe client, used to issue requests to Stripe's API and deserialize responses.

**Methods:**

- `#ctor(string, string, Stripe.IHttpClient, string, string, string, string)`
  - Initializes a new instance of the `StripeClient` class.
  - `apiKey`: The API key used by the client to make requests.
  - `clientId`: The client ID used by the client in OAuth requests.
  - `httpClient`: The `IHttpClient` client to use. If `null`, an HTTP client will be
created with default parameters.
  - `apiBase`: The base URL for Stripe's API. Defaults to `DefaultApiBase`.
  - `connectBase`: The base URL for Stripe's OAuth API. Defaults to `DefaultConnectBase`.
  - `filesBase`: The base URL for Stripe's Files API. Defaults to `DefaultFilesBase`.
  - `meterEventsBase`: The base URL for Stripe's Meter Events API. Defaults to `DefaultMeterEventsBase`.
- `Deserialize<T>(string)`
  - Deserializes a JSON string into a Stripe object.
  - `response`: The HTTP response as a StripeResponse.
  - `<T>`: The type of the Stripe object to deserialize to.
  - returns: The deserialized Stripe object from the JSON string.
- `ParseEventNotification(string, string, string, long)`
  - Parses a JSON string from a Stripe webhook into a `EventNotification` object, while
verifying the webhook's
signature.
  - `json`: The JSON string to parse.
  - `stripeSignatureHeader`: The value of the `Stripe-Signature` header from the webhook request.
  - `secret`: The webhook endpoint's signing secret.
  - `tolerance`: The time tolerance, in seconds (default 300).
  - returns: The deserialized `EventNotification`.
- `RawRequest(Http.HttpMethod, string, string, Stripe.RawRequestOptions)`
  - Sends a request to Stripe's API as a synchronous operation.
  - `method`: The HTTP method.
  - `path`: The path of the request.
  - `content`: The body of the request.
  - `requestOptions`: The special modifiers of the request.
  - returns: The response as a StripeResponse.
- `RawRequestAsync(Http.HttpMethod, string, string, Stripe.RawRequestOptions, CancellationToken)`
  - Sends a request to Stripe's API as an asynchronous operation.
  - `method`: The HTTP method.
  - `path`: The path of the request.
  - `content`: The body of the request.
  - `requestOptions`: The special modifiers of the request.
  - `cancellationToken`: The cancellation token to cancel operation.
  - returns: The task object representing the asynchronous operation.
- `RequestAsync<T>(Http.HttpMethod, string, Stripe.BaseOptions, Stripe.RequestOptions, CancellationToken)`
  - Sends a request to Stripe's API as an asynchronous operation.
  - `method`: The HTTP method.
  - `path`: The path of the request.
  - `options`: The parameters of the request.
  - `requestOptions`: The special modifiers of the request.
  - `cancellationToken`: The cancellation token to cancel operation.
  - `<T>`: Type of the Stripe entity returned by the API.
  - returns: The task object representing the asynchronous operation.
- `RequestStreamingAsync(Http.HttpMethod, string, Stripe.BaseOptions, Stripe.RequestOptions, CancellationToken)`

**Properties:**

- `ApiBase`
  - Gets the base URL for Stripe's API.
- `ApiKey`
  - Gets the API key used by the client to send requests.
- `ClientId`
  - Gets the client ID used by the client in OAuth requests.
- `ConnectBase`
  - Gets the base URL for Stripe's OAuth API.
- `DefaultApiBase`
  - Default base URL for Stripe's API.
- `DefaultConnectBase`
  - Default base URL for Stripe's OAuth API.
- `DefaultFilesBase`
  - Default base URL for Stripe's Files API.
- `DefaultMeterEventsBase`
  - Default base URL for Stripe's Meter Events API.
- `FilesBase`
  - Gets the base URL for Stripe's Files API.
- `HttpClient`
  - Gets the `IHttpClient` used to send HTTP requests.
- `MeterEventsBase`
  - Gets the base URL for Stripe's Meter Events API.


### StripeConfiguration

#### `StripeConfiguration`

Global configuration class for Stripe.net settings.

**Methods:**

- `DefaultSerializerSettings`
  - Returns a new instance of `JsonSerializerSettings` with
the default settings used by Stripe.net.
  - returns: A `JsonSerializerSettings` instance.
- `DefaultSerializerSettings(Stripe.ApiRequestor)`
  - Returns a new instance of `JsonSerializerSettings` with
the default settings used by Stripe.net.
  - returns: A `JsonSerializerSettings` instance.
- `DefaultStjSerializerOptions`
  - Returns a new instance of `JsonSerializerOptions` with
the default settings used by Stripe.net for System.Text.Json serialization.
  - returns: A `JsonSerializerOptions` instance.
- `SetApiKey(string)`
  - Sets the API key.
This method is deprecated and will be removed in a future version, please use the
`ApiKey` property setter instead.
  - `newApiKey`: API key.

**Properties:**

- `ApiKey`
  - Gets or sets the API key.
- `ApiVersion`
  - API version used by Stripe.net.
- `AppInfo`
  - Sets information about the "app" which this integration belongs to. This should be
reserved for plugins that wish to identify themselves with Stripe.
- `ClientId`
  - Gets or sets the client ID.
- `EnableTelemetry`
  - Gets or sets the flag enabling request latency telemetry. Enabled by default.
- `IndentedSerializerOptions`
  - Cached options instance for indented JSON output (used by ToJson()).
- `MaxNetworkRetries`
  - Gets or sets the maximum number of times that the library will retry requests that
appear to have failed due to an intermittent problem.
- `SerializerOptions`
  - Gets or sets the System.Text.Json options used for serialization and deserialization.
- `SerializerSettings`
  - Gets or sets the settings used for deserializing JSON objects returned by Stripe's API.
It is highly recommended you do not change these settings, as doing so can produce
unexpected results. If you do change these settings, make sure that
`StripeObjectConverter` is among the converters,
otherwise Stripe.net will no longer be able to deserialize polymorphic resources
represented by interfaces (e.g. `IPaymentSource`).
- `StripeClient`
  - Gets or sets a custom `StripeClient` for sending requests to Stripe's
API. You can use this to use a custom message handler, set proxy parameters, etc.
- `StripeNetVersion`
  - Gets the version of the Stripe.net client library.


### RequestOptions

#### `RequestOptions`

**Properties:**

- `ApiKey`
  - Gets or sets the API
key to use for the request.
- `IdempotencyKey`
  - Get or sets the idempotency
key to use for the request.
- `InternalBaseUrl`
  - Gets the base URL for the request.
- `StripeAccount`
  - Get or sets the
ID
of the connected account to use for the request.
- `StripeContext`
  - Gets or sets the value or Stripe-Context request header.
- `StripeRequestTrigger`
  - Gets or sets the value of the Stripe-Request-Trigger request header.
- `StripeVersion`
  - Gets or sets the API version for the request.
- `Usage`
  - Tracked behaviors.


### StripeList

#### `StripeList<T>`

**Methods:**

- `Reverse`
  - Reverse the order of the items in Data to support backward iteration
in autopagination with EndingBefore.

**Properties:**

- `Data`
  - A list containing the actual response elements, paginated by any request parameters.
- `HasMore`
  - Whether or not there are more elements available after this set. If `false`,
this set comprises the end of the list.
- `Object`
  - A string describing the object type returned.
- `Url`
  - The URL for accessing this list.


#### `StripeList<T>`

**Properties:**

- `Data`
  - A list containing the actual response elements, paginated by any request parameters.
TODO(jar) does this need an ItemConverterType (like in Stripe.StripeList).
- `NextPageUrl`
  - The URL for accessing this list.
- `PreviousPageUrl`
  - The URL for accessing this list.


### StripeError

#### `StripeError`

**Properties:**

- `Charge`
  - For card errors, the ID of the failed charge.
- `Code`
  - For some errors that could be handled programmatically, a short string indicating the
error code reported.
- `DeclineCode`
  - For card errors resulting from a card issuer decline, a short string indicating the
card issuer's reason for the
decline.
- `DocUrl`
  - A URL to more information about the error
code reported.
- `Message`
  - A human-readable message providing more details about the error. For card errors, these
messages can be shown to your users.
- `Param`
  - If the error is parameter-specific, the parameter related to the error. For example,
you can use this to display a message near the correct form field.
- `PaymentIntent`
  - The `PaymentIntent` object for errors returned on a request
involving a `PaymentIntent`.
- `PaymentMethod`
  - The `PaymentMethod` object for errors returned on a request
involving a `PaymentMethod`.
- `PaymentMethodType`
  - If the error is specific to the type of payment method, the payment method type that had
a problem. This field is only populated for invoice-related errors.
- `RequestLogUrl`
  - A URL to the request log entry in your dashboard.
- `SetupIntent`
  - The `SetupIntent` object for errors returned on a request
involving a `SetupIntent`.
- `Source`
  - The source object for errors returned on a request involving a source.
- `Type`
  - The type of error returned. One of `api_error`, `card_error`,
`idempotency_error`, or `invalid_request_error`.


### EventUtility

#### `EventUtility`

This class contains utility methods to process event objects in Stripe's webhooks.

**Methods:**

- `ComputeSignature(string, string, string)`
  - Computes the signature for a given payload.
  - `secret`: The webhook endpoint's signing secret.
  - `timestamp`: The timestamp of the payload.
  - `payload`: The payload to compute the signature for.
  - returns: The computed signature.
- `ConstructEvent(string, string, string, long, bool)`
  - Parses a JSON string from a Stripe webhook into a `Event` object, while
verifying the webhook's
signature.
  - `json`: The JSON string to parse.
  - `stripeSignatureHeader`: The value of the `Stripe-Signature` header from the webhook request.
  - `secret`: The webhook endpoint's signing secret.
  - `tolerance`: The time tolerance, in seconds (default 300).
  - `throwOnApiVersionMismatch`: If `true` (default), the method will throw a `StripeException` if the
API version of the event doesn't match Stripe.net's default API version (see
`Current`).
  - returns: The deserialized `Event`.
- `ConstructEvent(string, string, string, long, long, bool)`
  - Parses a JSON string from a Stripe webhook into a `Event` object, while
verifying the webhook's
signature.
  - `json`: The JSON string to parse.
  - `stripeSignatureHeader`: The value of the `Stripe-Signature` header from the webhook request.
  - `secret`: The webhook endpoint's signing secret.
  - `tolerance`: The time tolerance, in seconds.
  - `utcNow`: The timestamp to use for the current time.
  - `throwOnApiVersionMismatch`: If `true` (default), the method will throw a `StripeException` if the
API version of the event doesn't match Stripe.net's default API version (see
`Current`).
  - returns: The deserialized `Event`.
- `ParseEvent(string, bool)`
  - Parses a JSON string from a Stripe webhook into a `Event` object.
  - `json`: The JSON string to parse.
  - `throwOnApiVersionMismatch`: If `true` (default), the method will throw a `StripeException` if the
API version of the event doesn't match Stripe.net's default API version (see
`Current`).
  - returns: The deserialized `Event`.


### Event

#### `Event`

Snapshot events allow you to track and react to activity in your Stripe integration.
When the state of another API resource changes, Stripe creates an `Event` object
that contains all the relevant information associated with that action, including the
affected API resource. For example, a successful payment triggers a
`charge.succeeded` event, which contains the `Charge` in the event's data
property. Some actions trigger multiple events. For example, if you create a new
subscription for a customer, it triggers both a `customer.subscription.created`
event and a `charge.succeeded` event.

Configure an event destination in your account to listen for events that represent
actions your integration needs to respond to. Additionally, you can retrieve an
individual event or a list of events from the API.

Connect platforms can also receive event
notifications that occur in their connected accounts. These events include an account
attribute that identifies the relevant connected account.

You can access events through the Retrieve Event API for 30
days.

**Properties:**

- `Account`
  - The connected account that originates the event.
- `ApiVersion`
  - The Stripe API version used to render `data` when the event was created. The
contents of `data` never change, so this value remains static regardless of the API
version currently in use. This property is populated only for events created on or after
October 31, 2014.
- `Context`
  - Authentication context needed to fetch the event or related object.
- `Created`
  - Time at which the object was created. Measured in seconds since the Unix epoch.
- `Id`
  - Unique identifier for the object.
- `Livemode`
  - If the object exists in live mode, the value is `true`. If the object exists in
test mode, the value is `false`.
- `Object`
  - String representing the object's type. Objects of the same type share the same value.
- `PendingWebhooks`
  - Number of webhooks that haven't been successfully delivered (for example, to return a
20x response) to the URLs you specify.
- `Request`
  - Information on the API request that triggers the event.
- `Type`
  - Description of the event (for example, `invoice.created` or
`charge.refunded`).
One of: `account.application.authorized`, `account.application.deauthorized`,
`account.external_account.created`, `account.external_account.deleted`,
`account.external_account.updated`, `account.updated`,
`application_fee.created`, `application_fee.refund.updated`,
`application_fee.refunded`, `balance.available`,
`balance_settings.updated`, `billing.alert.triggered`,
`billing.credit_grant.created`, `billing_portal.configuration.created`,
`billing_portal.configuration.updated`, `billing_portal.session.created`,
`capability.updated`, `cash_balance.funds_available`, `charge.captured`,
`charge.dispute.closed`, `charge.dispute.created`,
`charge.dispute.funds_reinstated`, `charge.dispute.funds_withdrawn`,
`charge.dispute.updated`, `charge.expired`, `charge.failed`,
`charge.pending`, `charge.refund.updated`, `charge.refunded`,
`charge.succeeded`, `charge.updated`,
`checkout.session.async_payment_failed`,
`checkout.session.async_payment_succeeded`, `checkout.session.completed`,
`checkout.session.expired`, `climate.order.canceled`,
`climate.order.created`, `climate.order.delayed`,
`climate.order.delivered`, `climate.order.product_substituted`,
`climate.product.created`, `climate.product.pricing_updated`,
`coupon.created`, `coupon.deleted`, `coupon.updated`,
`credit_note.created`, `credit_note.updated`, `credit_note.voided`,
`customer.created`, `customer.deleted`, `customer.discount.created`,
`customer.discount.deleted`, `customer.discount.updated`,
`customer.source.created`, `customer.source.deleted`,
`customer.source.expiring`, `customer.source.updated`,
`customer.subscription.created`, `customer.subscription.deleted`,
`customer.subscription.paused`,
`customer.subscription.pending_update_applied`,
`customer.subscription.pending_update_expired`,
`customer.subscription.resumed`, `customer.subscription.trial_will_end`,
`customer.subscription.updated`, `customer.tax_id.created`,
`customer.tax_id.deleted`, `customer.tax_id.updated`, `customer.updated`,
`customer_cash_balance_transaction.created`,
`entitlements.active_entitlement_summary.updated`, `file.created`,
`financial_connections.account.account_numbers_updated`,
`financial_connections.account.created`,
`financial_connections.account.deactivated`,
`financial_connections.account.disconnected`,
`financial_connections.account.reactivated`,
`financial_connections.account.refreshed_balance`,
`financial_connections.account.refreshed_ownership`,
`financial_connections.account.refreshed_transactions`,
`financial_connections.account.upcoming_account_number_expiry`,
`identity.verification_session.canceled`,
`identity.verification_session.created`,
`identity.verification_session.processing`,
`identity.verification_session.redacted`,
`identity.verification_session.requires_input`,
`identity.verification_session.verified`, `invoice.created`,
`invoice.deleted`, `invoice.finalization_failed`, `invoice.finalized`,
`invoice.marked_uncollectible`, `invoice.overdue`, `invoice.overpaid`,
`invoice.paid`, `invoice.payment_action_required`,
`invoice.payment_attempt_required`, `invoice.payment_failed`,
`invoice.payment_succeeded`, `invoice.sent`, `invoice.upcoming`,
`invoice.updated`, `invoice.voided`, `invoice.will_be_due`,
`invoice_payment.paid`, `invoiceitem.created`, `invoiceitem.deleted`,
`issuing_authorization.created`, `issuing_authorization.request`,
`issuing_authorization.updated`, `issuing_card.created`,
`issuing_card.updated`, `issuing_cardholder.created`,
`issuing_cardholder.updated`, `issuing_dispute.closed`,
`issuing_dispute.created`, `issuing_dispute.funds_reinstated`,
`issuing_dispute.funds_rescinded`, `issuing_dispute.submitted`,
`issuing_dispute.updated`, `issuing_personalization_design.activated`,
`issuing_personalization_design.deactivated`,
`issuing_personalization_design.rejected`,
`issuing_personalization_design.updated`, `issuing_token.created`,
`issuing_token.updated`, `issuing_transaction.created`,
`issuing_transaction.purchase_details_receipt_updated`,
`issuing_transaction.updated`, `mandate.updated`,
`payment_intent.amount_capturable_updated`, `payment_intent.canceled`,
`payment_intent.created`, `payment_intent.partially_funded`,
`payment_intent.payment_failed`, `payment_intent.processing`,
`payment_intent.requires_action`, `payment_intent.succeeded`,
`payment_link.created`, `payment_link.updated`,
`payment_method.attached`, `payment_method.automatically_updated`,
`payment_method.detached`, `payment_method.updated`, `payout.canceled`,
`payout.created`, `payout.failed`, `payout.paid`,
`payout.reconciliation_completed`, `payout.updated`, `person.created`,
`person.deleted`, `person.updated`, `plan.created`, `plan.deleted`,
`plan.updated`, `price.created`, `price.deleted`, `price.updated`,
`product.created`, `product.deleted`, `product.updated`,
`promotion_code.created`, `promotion_code.updated`, `quote.accepted`,
`quote.canceled`, `quote.created`, `quote.finalized`,
`radar.early_fraud_warning.created`, `radar.early_fraud_warning.updated`,
`refund.created`, `refund.failed`, `refund.updated`,
`reporting.report_run.failed`, `reporting.report_run.succeeded`,
`reporting.report_type.updated`, `reserve.hold.created`,
`reserve.hold.updated`, `reserve.plan.created`, `reserve.plan.disabled`,
`reserve.plan.expired`, `reserve.plan.updated`,
`reserve.release.created`, `review.closed`, `review.opened`,
`setup_intent.canceled`, `setup_intent.created`,
`setup_intent.requires_action`, `setup_intent.setup_failed`,
`setup_intent.succeeded`, `sigma.scheduled_query_run.created`,
`source.canceled`, `source.chargeable`, `source.failed`,
`source.mandate_notification`, `source.refund_attributes_required`,
`source.transaction.created`, `source.transaction.updated`,
`subscription_schedule.aborted`, `subscription_schedule.canceled`,
`subscription_schedule.completed`, `subscription_schedule.created`,
`subscription_schedule.expiring`, `subscription_schedule.released`,
`subscription_schedule.updated`, `tax.settings.updated`,
`tax_rate.created`, `tax_rate.updated`, `terminal.reader.action_failed`,
`terminal.reader.action_succeeded`, `terminal.reader.action_updated`,
`test_helpers.test_clock.advancing`, `test_helpers.test_clock.created`,
`test_helpers.test_clock.deleted`, `test_helpers.test_clock.internal_failure`,
`test_helpers.test_clock.ready`, `topup.canceled`, `topup.created`,
`topup.failed`, `topup.reversed`, `topup.succeeded`,
`transfer.created`, `transfer.reversed`, `transfer.updated`,
`treasury.credit_reversal.created`, `treasury.credit_reversal.posted`,
`treasury.debit_reversal.completed`, `treasury.debit_reversal.created`,
`treasury.debit_reversal.initial_credit_granted`,
`treasury.financial_account.closed`, `treasury.financial_account.created`,
`treasury.financial_account.features_status_updated`,
`treasury.inbound_transfer.canceled`, `treasury.inbound_transfer.created`,
`treasury.inbound_transfer.failed`, `treasury.inbound_transfer.succeeded`,
`treasury.outbound_payment.canceled`, `treasury.outbound_payment.created`,
`treasury.outbound_payment.expected_arrival_date_updated`,
`treasury.outbound_payment.failed`, `treasury.outbound_payment.posted`,
`treasury.outbound_payment.returned`,
`treasury.outbound_payment.tracking_details_updated`,
`treasury.outbound_transfer.canceled`, `treasury.outbound_transfer.created`,
`treasury.outbound_transfer.expected_arrival_date_updated`,
`treasury.outbound_transfer.failed`, `treasury.outbound_transfer.posted`,
`treasury.outbound_transfer.returned`,
`treasury.outbound_transfer.tracking_details_updated`,
`treasury.received_credit.created`, `treasury.received_credit.failed`,
`treasury.received_credit.succeeded`, `treasury.received_debit.created`,
`billing.credit_balance_transaction.created`, `billing.credit_grant.updated`,
`billing.meter.created`, `billing.meter.deactivated`,
`billing.meter.reactivated`, `billing.meter.updated`, or `ping`.


#### `Event`

Code generated portion of V2 Event resource.

**Methods:**

- `FetchRelatedObject<T>(Stripe.V2.Core.EventRelatedObject)`
  - Makes an API request to fetch the object associated with this event.
  - `<T>`: The type of the object to fetch.
- `FetchRelatedObjectAsync<T>(Stripe.V2.Core.EventRelatedObject, CancellationToken)`
  - Makes an API request to fetch the object associated with this event.
  - `<T>`: The type of the object to fetch.

**Properties:**

- `Changes`
  - Before and after changes for the primary related object.
- `Context`
  - Authentication context needed to fetch the event or related object.
- `Created`
  - Time at which the object was created.
- `Id`
  - Unique identifier for the event.
- `Livemode`
  - Has the value `true` if the object exists in live mode or the value `false` if
the object exists in test mode.
- `Object`
  - String representing the object's type. Objects of the same type share the same value of
the object field.
- `Reason`
  - Reason for the event.
- `Requestor`
  - Used for .FetchObject and .FetchData helpers.
- `Type`
  - The type of the event.


#### `EventService`

**Methods:**

- `Get(string, Stripe.V2.Core.EventGetOptions, Stripe.RequestOptions)`
  - Retrieves the details of an event if it was created in the last 30 days. Supply the
unique identifier of the event, which might have been delivered to your event
destination.
- `GetAsync(string, Stripe.V2.Core.EventGetOptions, Stripe.RequestOptions, CancellationToken)`
  - Retrieves the details of an event if it was created in the last 30 days. Supply the
unique identifier of the event, which might have been delivered to your event
destination.
- `List(Stripe.V2.Core.EventListOptions, Stripe.RequestOptions)`
  - List events, going back up to 30 days.
- `ListAsync(Stripe.V2.Core.EventListOptions, Stripe.RequestOptions, CancellationToken)`
  - List events, going back up to 30 days.
- `ListAutoPaging(Stripe.V2.Core.EventListOptions, Stripe.RequestOptions)`
  - List events, going back up to 30 days.
- `ListAutoPagingAsync(Stripe.V2.Core.EventListOptions, Stripe.RequestOptions, CancellationToken)`
  - List events, going back up to 30 days.


#### `EventService`

**Methods:**

- `Get(string, Stripe.EventGetOptions, Stripe.RequestOptions)`
  - Retrieves the details of an event if it was created in the last 30 days. Supply the
unique identifier of the event, which you might have received in a webhook..
- `GetAsync(string, Stripe.EventGetOptions, Stripe.RequestOptions, CancellationToken)`
  - Retrieves the details of an event if it was created in the last 30 days. Supply the
unique identifier of the event, which you might have received in a webhook..
- `List(Stripe.EventListOptions, Stripe.RequestOptions)`
  - List events, going back up to 30 days. Each event data is rendered according to
Stripe API version at its creation time, specified in event object `api_version`
attribute (not according to your current Stripe API version or `Stripe-Version`
header)..
- `ListAsync(Stripe.EventListOptions, Stripe.RequestOptions, CancellationToken)`
  - List events, going back up to 30 days. Each event data is rendered according to
Stripe API version at its creation time, specified in event object `api_version`
attribute (not according to your current Stripe API version or `Stripe-Version`
header)..
- `ListAutoPaging(Stripe.EventListOptions, Stripe.RequestOptions)`
  - List events, going back up to 30 days. Each event data is rendered according to
Stripe API version at its creation time, specified in event object `api_version`
attribute (not according to your current Stripe API version or `Stripe-Version`
header)..
- `ListAutoPagingAsync(Stripe.EventListOptions, Stripe.RequestOptions, CancellationToken)`
  - List events, going back up to 30 days. Each event data is rendered according to
Stripe API version at its creation time, specified in event object `api_version`
attribute (not according to your current Stripe API version or `Stripe-Version`
header)..


#### `EventListOptions`

**Properties:**

- `Created`
  - Set of filters to query events within a range of `created` timestamps.
- `ObjectId`
  - Primary object ID used to retrieve related events.
- `Types`
  - An array of up to 20 strings containing specific event names.


#### `EventListOptions`

**Properties:**

- `Created`
  - Only return events that were created during the given date interval.
- `DeliverySuccess`
  - Filter events by whether all webhooks were successfully delivered. If false, events
which are still pending or have failed all delivery attempts to a webhook endpoint will
be returned.
- `Type`
  - A string containing a specific event name, or group of events using * as a wildcard. The
list will be filtered to include only events with a matching event property.
- `Types`
  - An array of up to 20 strings containing specific event names. The list will be filtered
to include only events with a matching event property. You may pass either `type`
or `types`, but not both.


### PaymentIntent

#### `PaymentIntent`

A PaymentIntent guides you through the process of collecting a payment from your
customer. We recommend that you create exactly one PaymentIntent for each order or
customer session in your system. You can reference the PaymentIntent later to see the
history of payment attempts for a particular session.

A PaymentIntent transitions through multiple statuses
throughout its lifetime as it interfaces with Stripe.js to perform authentication flows
and ultimately creates at most one successful charge.

Related guide: Payment
Intents API.

**Properties:**

- `Amount`
  - Amount intended to be collected by this PaymentIntent. A positive integer representing
how much to charge in the smallest currency unit (e.g.,
100 cents to charge $1.00 or 100 to charge ¥100, a zero-decimal currency). The minimum
amount is $0.50 US or equivalent
in charge currency. The amount value supports up to eight digits (e.g., a value of
99999999 for a USD charge of $999,999.99).
- `AmountCapturable`
  - Amount that can be captured from this PaymentIntent.
- `AmountReceived`
  - Amount that this PaymentIntent collects.
- `Application`
  - (Expanded)
ID of the Connect application that created the PaymentIntent.

For more information, see the expand documentation.
- `ApplicationFeeAmount`
  - The amount of the application fee (if any) that will be requested to be applied to the
payment and transferred to the application owner's Stripe account. The amount of the
application fee collected will be capped at the total amount captured. For more
information, see the PaymentIntents use case for connected
accounts.
- `ApplicationId`
  - (ID of the Application)
ID of the Connect application that created the PaymentIntent.
- `AutomaticPaymentMethods`
  - Settings to configure compatible payment methods from the Stripe Dashboard.
- `CanceledAt`
  - Populated when `status` is `canceled`, this is the time at which the
PaymentIntent was canceled. Measured in seconds since the Unix epoch.
- `CancellationReason`
  - Reason for cancellation of this PaymentIntent, either user-provided (`duplicate`,
`fraudulent`, `requested_by_customer`, or `abandoned`) or generated by
Stripe internally (`failed_invoice`, `void_invoice`, `automatic`, or
`expired`).
One of: `abandoned`, `automatic`, `duplicate`, `expired`,
`failed_invoice`, `fraudulent`, `requested_by_customer`, or
`void_invoice`.
- `CaptureMethod`
  - Controls when the funds will be captured from the customer's account.
One of: `automatic`, `automatic_async`, or `manual`.
- `ClientSecret`
  - The client secret of this PaymentIntent. Used for client-side retrieval using a
publishable key.

The client secret can be used to complete a payment from your frontend. It should not be
stored, logged, or exposed to anyone other than the customer. Make sure that you have
TLS enabled on any page that includes the client secret.

Refer to our docs to accept a
payment and learn about how `client_secret` should be handled.
- `ConfirmationMethod`
  - Describes whether we can confirm this PaymentIntent automatically, or if it requires
customer action to confirm the payment.
One of: `automatic`, or `manual`.
- `Created`
  - Time at which the object was created. Measured in seconds since the Unix epoch.
- `Currency`
  - Three-letter ISO currency
code, in lowercase. Must be a supported
currency.
- `Customer`
  - (Expanded)
ID of the Customer this PaymentIntent belongs to, if one exists.

Payment methods attached to other Customers cannot be used with this PaymentIntent.

If setup_future_usage
is set and this PaymentIntent's payment method is not `card_present`, then the
payment method attaches to the Customer after the PaymentIntent has been confirmed and
any required actions from the user are complete. If the payment method is
`card_present` and isn't a digital wallet, then a generated_card
payment method representing the card is created and attached to the Customer instead.

For more information, see the expand documentation.
- `CustomerAccount`
  - ID of the Account representing the customer that this PaymentIntent belongs to, if one
exists.

Payment methods attached to other Accounts cannot be used with this PaymentIntent.

If setup_future_usage
is set and this PaymentIntent's payment method is not `card_present`, then the
payment method attaches to the Account after the PaymentIntent has been confirmed and
any required actions from the user are complete. If the payment method is
`card_present` and isn't a digital wallet, then a generated_card
payment method representing the card is created and attached to the Account instead.
- `CustomerId`
  - (ID of the Customer)
ID of the Customer this PaymentIntent belongs to, if one exists.

Payment methods attached to other Customers cannot be used with this PaymentIntent.

If setup_future_usage
is set and this PaymentIntent's payment method is not `card_present`, then the
payment method attaches to the Customer after the PaymentIntent has been confirmed and
any required actions from the user are complete. If the payment method is
`card_present` and isn't a digital wallet, then a generated_card
payment method representing the card is created and attached to the Customer instead.
- `Description`
  - An arbitrary string attached to the object. Often useful for displaying to users.
- `ExcludedPaymentMethodTypes`
  - The list of payment method types to exclude from use with this payment.
One of: `acss_debit`, `affirm`, `afterpay_clearpay`, `alipay`,
`alma`, `amazon_pay`, `au_becs_debit`, `bacs_debit`,
`bancontact`, `billie`, `bizum`, `blik`, `boleto`, `card`,
`cashapp`, `crypto`, `customer_balance`, `eps`, `fpx`,
`giropay`, `grabpay`, `ideal`, `kakao_pay`, `klarna`,
`konbini`, `kr_card`, `mb_way`, `mobilepay`, `multibanco`,
`naver_pay`, `nz_bank_account`, `oxxo`, `p24`, `pay_by_bank`,
`payco`, `paynow`, `paypal`, `payto`, `pix`, `promptpay`,
`revolut_pay`, `samsung_pay`, `satispay`, `scalapay`,
`sepa_debit`, `sofort`, `sunbit`, `swish`, `twint`, `upi`,
`us_bank_account`, `wechat_pay`, or `zip`.
- `Id`
  - Unique identifier for the object.
- `LastPaymentError`
  - The payment error encountered in the previous PaymentIntent confirmation. It will be
cleared if the PaymentIntent is later updated for any reason.
- `LatestCharge`
  - (Expanded)
ID of the latest Charge object created
by this PaymentIntent. This property is `null` until PaymentIntent confirmation is
attempted.

For more information, see the expand documentation.
- `LatestChargeId`
  - (ID of the Charge)
ID of the latest Charge object created
by this PaymentIntent. This property is `null` until PaymentIntent confirmation is
attempted.
- `Livemode`
  - If the object exists in live mode, the value is `true`. If the object exists in
test mode, the value is `false`.
- `ManagedPayments`
  - Settings for Managed Payments.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format. Learn more about storing
information in metadata.
- `NextAction`
  - If present, this property tells you what actions you need to take in order for your
customer to fulfill a payment using the provided source.
- `Object`
  - String representing the object's type. Objects of the same type share the same value.
- `OnBehalfOf`
  - (Expanded)
You can specify the settlement merchant as the connected account using the
`on_behalf_of` attribute on the charge. See the PaymentIntents use case for connected
accounts for details.

For more information, see the expand documentation.
- `OnBehalfOfId`
  - (ID of the Account)
You can specify the settlement merchant as the connected account using the
`on_behalf_of` attribute on the charge. See the PaymentIntents use case for connected
accounts for details.
- `PaymentMethod`
  - (Expanded)
ID of the payment method used in this PaymentIntent.

For more information, see the expand documentation.
- `PaymentMethodConfigurationDetails`
  - Information about the payment method
configuration used for this PaymentIntent.
- `PaymentMethodId`
  - (ID of the PaymentMethod)
ID of the payment method used in this PaymentIntent.
- `PaymentMethodOptions`
  - Payment-method-specific configuration for this PaymentIntent.
- `PaymentMethodTypes`
  - The list of payment method types (e.g. card) that this PaymentIntent is allowed to use.
A comprehensive list of valid payment method types can be found here.
- `Processing`
  - If present, this property tells you about the processing state of the payment.
- `ReceiptEmail`
  - Email address that the receipt for the resulting payment will be sent to. If
`receipt_email` is specified for a payment in live mode, a receipt will be sent
regardless of your email
settings.
- `Review`
  - (Expanded)
ID of the review associated with this PaymentIntent, if any.

For more information, see the expand documentation.
- `ReviewId`
  - (ID of the Review)
ID of the review associated with this PaymentIntent, if any.
- `SetupFutureUsage`
  - Indicates that you intend to make future payments with this PaymentIntent's payment
method.

If you provide a Customer with the PaymentIntent, you can use this parameter to attach the payment method to
the Customer after the PaymentIntent is confirmed and the customer completes any
required actions. If you don't provide a Customer, you can still attach the payment method to a
Customer after the transaction completes.

If the payment method is `card_present` and isn't a digital wallet, Stripe creates
and attaches a generated_card
payment method representing the card to the Customer instead.

When processing card payments, Stripe uses `setup_future_usage` to help you comply
with regional legislation and network rules, such as SCA.
One of: `off_session`, or `on_session`.
- `Shipping`
  - Shipping information for this PaymentIntent.
- `Source`
  - (Expanded)
This is a legacy field that will be removed in the future. It is the ID of the Source
object that is associated with this PaymentIntent, if one was supplied.

For more information, see the expand documentation.
- `SourceId`
  - (ID of the IPaymentSource)
This is a legacy field that will be removed in the future. It is the ID of the Source
object that is associated with this PaymentIntent, if one was supplied.
- `StatementDescriptor`
  - Text that appears on the customer's statement as the statement descriptor for a non-card
charge. This value overrides the account's default statement descriptor. For information
about requirements, including the 22-character limit, see the Statement
Descriptor docs.

Setting this value for a card charge returns an error. For card charges, set the statement_descriptor_suffix
instead.
- `StatementDescriptorSuffix`
  - Provides information about a card charge. Concatenated to the account's statement
descriptor prefix to form the complete statement descriptor that appears on the
customer's statement.
- `Status`
  - Status of this PaymentIntent, one of `requires_payment_method`,
`requires_confirmation`, `requires_action`, `processing`,
`requires_capture`, `canceled`, or `succeeded`. Read more about each
PaymentIntent status.
One of: `canceled`, `processing`, `requires_action`,
`requires_capture`, `requires_confirmation`, `requires_payment_method`,
or `succeeded`.
- `TransferData`
  - The data that automatically creates a Transfer after the payment finalizes. Learn more
about the use case for
connected accounts.
- `TransferGroup`
  - A string that identifies the resulting payment as part of a group. Learn more about the
use case for
connected accounts.


#### `PaymentIntentService`

**Methods:**

- `ApplyCustomerBalance(string, Stripe.PaymentIntentApplyCustomerBalanceOptions, Stripe.RequestOptions)`
  - Manually reconcile the remaining amount for a `customer_balance`
PaymentIntent..
- `ApplyCustomerBalanceAsync(string, Stripe.PaymentIntentApplyCustomerBalanceOptions, Stripe.RequestOptions, CancellationToken)`
  - Manually reconcile the remaining amount for a `customer_balance`
PaymentIntent..
- `Cancel(string, Stripe.PaymentIntentCancelOptions, Stripe.RequestOptions)`
  - You can cancel a PaymentIntent object when it’s in one of these statuses:
`requires_payment_method`, `requires_capture`, `requires_confirmation`,
`requires_action` or, in rare
cases, `processing`..

After it’s canceled, no additional charges are made by the PaymentIntent and any
operations on the PaymentIntent fail with an error. For PaymentIntents with a
`status` of `requires_capture`, the remaining `amount_capturable` is
automatically refunded..

You can directly cancel the PaymentIntent for a Checkout Session only when the
PaymentIntent has a status of `requires_capture`. Otherwise, you must expire the Checkout
Session..
- `CancelAsync(string, Stripe.PaymentIntentCancelOptions, Stripe.RequestOptions, CancellationToken)`
  - You can cancel a PaymentIntent object when it’s in one of these statuses:
`requires_payment_method`, `requires_capture`, `requires_confirmation`,
`requires_action` or, in rare
cases, `processing`..

After it’s canceled, no additional charges are made by the PaymentIntent and any
operations on the PaymentIntent fail with an error. For PaymentIntents with a
`status` of `requires_capture`, the remaining `amount_capturable` is
automatically refunded..

You can directly cancel the PaymentIntent for a Checkout Session only when the
PaymentIntent has a status of `requires_capture`. Otherwise, you must expire the Checkout
Session..
- `Capture(string, Stripe.PaymentIntentCaptureOptions, Stripe.RequestOptions)`
  - Capture the funds of an existing uncaptured PaymentIntent when its status is
`requires_capture`..

Uncaptured PaymentIntents are cancelled a set number of days (7 by default) after
their creation..

Learn more about separate
authorization and capture..
- `CaptureAsync(string, Stripe.PaymentIntentCaptureOptions, Stripe.RequestOptions, CancellationToken)`
  - Capture the funds of an existing uncaptured PaymentIntent when its status is
`requires_capture`..

Uncaptured PaymentIntents are cancelled a set number of days (7 by default) after
their creation..

Learn more about separate
authorization and capture..
- `Confirm(string, Stripe.PaymentIntentConfirmOptions, Stripe.RequestOptions)`
  - Confirm that your customer intends to pay with current or provided payment method.
Upon confirmation, the PaymentIntent will attempt to initiate a payment..

If the selected payment method requires additional authentication steps, the
PaymentIntent will transition to the `requires_action` status and suggest
additional actions via `next_action`. If payment fails, the PaymentIntent
transitions to the `requires_payment_method` status or the `canceled` status
if the confirmation limit is reached. If payment succeeds, the PaymentIntent will
transition to the `succeeded` status (or `requires_capture`, if
`capture_method` is set to `manual`)..

If the `confirmation_method` is `automatic`, payment may be attempted using
our client
SDKs and the PaymentIntent’s client_secret.
After `next_action`s are handled by the client, no additional confirmation is
required to complete the payment..

If the `confirmation_method` is `manual`, all payment attempts must be
initiated using a secret key..

If any actions are required for the payment, the PaymentIntent will return to the
`requires_confirmation` state after those actions are completed. Your server needs
to then explicitly re-confirm the PaymentIntent to initiate the next payment
attempt..

There is a variable upper limit on how many times a PaymentIntent can be confirmed.
After this limit is reached, any further calls to this endpoint will transition the
PaymentIntent to the `canceled` state..
- `ConfirmAsync(string, Stripe.PaymentIntentConfirmOptions, Stripe.RequestOptions, CancellationToken)`
  - Confirm that your customer intends to pay with current or provided payment method.
Upon confirmation, the PaymentIntent will attempt to initiate a payment..

If the selected payment method requires additional authentication steps, the
PaymentIntent will transition to the `requires_action` status and suggest
additional actions via `next_action`. If payment fails, the PaymentIntent
transitions to the `requires_payment_method` status or the `canceled` status
if the confirmation limit is reached. If payment succeeds, the PaymentIntent will
transition to the `succeeded` status (or `requires_capture`, if
`capture_method` is set to `manual`)..

If the `confirmation_method` is `automatic`, payment may be attempted using
our client
SDKs and the PaymentIntent’s client_secret.
After `next_action`s are handled by the client, no additional confirmation is
required to complete the payment..

If the `confirmation_method` is `manual`, all payment attempts must be
initiated using a secret key..

If any actions are required for the payment, the PaymentIntent will return to the
`requires_confirmation` state after those actions are completed. Your server needs
to then explicitly re-confirm the PaymentIntent to initiate the next payment
attempt..

There is a variable upper limit on how many times a PaymentIntent can be confirmed.
After this limit is reached, any further calls to this endpoint will transition the
PaymentIntent to the `canceled` state..
- `Create(Stripe.PaymentIntentCreateOptions, Stripe.RequestOptions)`
  - Creates a PaymentIntent object..

After the PaymentIntent is created, attach a payment method and confirm to continue the
payment. Learn more about the
available payment flows with the Payment Intents API..

When you use `confirm=true` during creation, it’s equivalent to creating and
confirming the PaymentIntent in the same call. You can use any parameters available in
the confirm API when
you supply `confirm=true`..
- `CreateAsync(Stripe.PaymentIntentCreateOptions, Stripe.RequestOptions, CancellationToken)`
  - Creates a PaymentIntent object..

After the PaymentIntent is created, attach a payment method and confirm to continue the
payment. Learn more about the
available payment flows with the Payment Intents API..

When you use `confirm=true` during creation, it’s equivalent to creating and
confirming the PaymentIntent in the same call. You can use any parameters available in
the confirm API when
you supply `confirm=true`..
- `Get(string, Stripe.PaymentIntentGetOptions, Stripe.RequestOptions)`
  - Retrieves the details of a PaymentIntent that has previously been created..

You can retrieve a PaymentIntent client-side using a publishable key when the
`client_secret` is in the query string..

If you retrieve a PaymentIntent with a publishable key, it only returns a subset of
properties. Refer to the payment intent object
reference for more details..
- `GetAsync(string, Stripe.PaymentIntentGetOptions, Stripe.RequestOptions, CancellationToken)`
  - Retrieves the details of a PaymentIntent that has previously been created..

You can retrieve a PaymentIntent client-side using a publishable key when the
`client_secret` is in the query string..

If you retrieve a PaymentIntent with a publishable key, it only returns a subset of
properties. Refer to the payment intent object
reference for more details..
- `IncrementAuthorization(string, Stripe.PaymentIntentIncrementAuthorizationOptions, Stripe.RequestOptions)`
  - Perform an incremental authorization on an eligible PaymentIntent. To be
eligible, the PaymentIntent’s status must be `requires_capture` and incremental_authorization_supported
must be `true`..

Incremental authorizations attempt to increase the authorized amount on your
customer’s card to the new, higher `amount` provided. Similar to the initial
authorization, incremental authorizations can be declined. A single PaymentIntent can
call this endpoint multiple times to further increase the authorized amount..

If the incremental authorization succeeds, the PaymentIntent object returns with the
updated amount.
If the incremental authorization fails, a card_declined error
returns, and no other fields on the PaymentIntent or Charge update. The PaymentIntent
object remains capturable for the previously authorized amount..

Each PaymentIntent can have a maximum of 10 incremental authorization attempts,
including declines. After it’s captured, a PaymentIntent can no longer be
incremented..

Learn more about incremental authorizations with in-person
payments and online
payments..
- `IncrementAuthorizationAsync(string, Stripe.PaymentIntentIncrementAuthorizationOptions, Stripe.RequestOptions, CancellationToken)`
  - Perform an incremental authorization on an eligible PaymentIntent. To be
eligible, the PaymentIntent’s status must be `requires_capture` and incremental_authorization_supported
must be `true`..

Incremental authorizations attempt to increase the authorized amount on your
customer’s card to the new, higher `amount` provided. Similar to the initial
authorization, incremental authorizations can be declined. A single PaymentIntent can
call this endpoint multiple times to further increase the authorized amount..

If the incremental authorization succeeds, the PaymentIntent object returns with the
updated amount.
If the incremental authorization fails, a card_declined error
returns, and no other fields on the PaymentIntent or Charge update. The PaymentIntent
object remains capturable for the previously authorized amount..

Each PaymentIntent can have a maximum of 10 incremental authorization attempts,
including declines. After it’s captured, a PaymentIntent can no longer be
incremented..

Learn more about incremental authorizations with in-person
payments and online
payments..
- `List(Stripe.PaymentIntentListOptions, Stripe.RequestOptions)`
  - Returns a list of PaymentIntents..
- `ListAsync(Stripe.PaymentIntentListOptions, Stripe.RequestOptions, CancellationToken)`
  - Returns a list of PaymentIntents..
- `ListAutoPaging(Stripe.PaymentIntentListOptions, Stripe.RequestOptions)`
  - Returns a list of PaymentIntents..
- `ListAutoPagingAsync(Stripe.PaymentIntentListOptions, Stripe.RequestOptions, CancellationToken)`
  - Returns a list of PaymentIntents..
- `Search(Stripe.PaymentIntentSearchOptions, Stripe.RequestOptions)`
  - Search for PaymentIntents you’ve previously created using Stripe’s Search Query Language.
Don’t use search in read-after-write flows where strict consistency is necessary. Under
normal operating conditions, data is searchable in less than a minute. Occasionally,
propagation of new or updated data can be up to an hour behind during outages. Search
functionality is not available to merchants in India..
- `SearchAsync(Stripe.PaymentIntentSearchOptions, Stripe.RequestOptions, CancellationToken)`
  - Search for PaymentIntents you’ve previously created using Stripe’s Search Query Language.
Don’t use search in read-after-write flows where strict consistency is necessary. Under
normal operating conditions, data is searchable in less than a minute. Occasionally,
propagation of new or updated data can be up to an hour behind during outages. Search
functionality is not available to merchants in India..
- `SearchAutoPaging(Stripe.PaymentIntentSearchOptions, Stripe.RequestOptions)`
  - Search for PaymentIntents you’ve previously created using Stripe’s Search Query Language.
Don’t use search in read-after-write flows where strict consistency is necessary. Under
normal operating conditions, data is searchable in less than a minute. Occasionally,
propagation of new or updated data can be up to an hour behind during outages. Search
functionality is not available to merchants in India..
- `SearchAutoPagingAsync(Stripe.PaymentIntentSearchOptions, Stripe.RequestOptions, CancellationToken)`
  - Search for PaymentIntents you’ve previously created using Stripe’s Search Query Language.
Don’t use search in read-after-write flows where strict consistency is necessary. Under
normal operating conditions, data is searchable in less than a minute. Occasionally,
propagation of new or updated data can be up to an hour behind during outages. Search
functionality is not available to merchants in India..
- `Update(string, Stripe.PaymentIntentUpdateOptions, Stripe.RequestOptions)`
  - Updates properties on a PaymentIntent object without confirming..

Depending on which properties you update, you might need to confirm the PaymentIntent
again. For example, updating the `payment_method` always requires you to confirm
the PaymentIntent again. If you prefer to update and confirm at the same time, we
recommend updating properties through the confirm API instead..
- `UpdateAsync(string, Stripe.PaymentIntentUpdateOptions, Stripe.RequestOptions, CancellationToken)`
  - Updates properties on a PaymentIntent object without confirming..

Depending on which properties you update, you might need to confirm the PaymentIntent
again. For example, updating the `payment_method` always requires you to confirm
the PaymentIntent again. If you prefer to update and confirm at the same time, we
recommend updating properties through the confirm API instead..
- `VerifyMicrodeposits(string, Stripe.PaymentIntentVerifyMicrodepositsOptions, Stripe.RequestOptions)`
  - Verifies microdeposits on a PaymentIntent object..
- `VerifyMicrodepositsAsync(string, Stripe.PaymentIntentVerifyMicrodepositsOptions, Stripe.RequestOptions, CancellationToken)`
  - Verifies microdeposits on a PaymentIntent object..


#### `PaymentIntentCreateOptions`

**Properties:**

- `Amount`
  - Amount intended to be collected by this PaymentIntent. A positive integer representing
how much to charge in the smallest currency unit (e.g.,
100 cents to charge $1.00 or 100 to charge ¥100, a zero-decimal currency). The minimum
amount is $0.50 US or equivalent
in charge currency. The amount value supports up to eight digits (e.g., a value of
99999999 for a USD charge of $999,999.99).
- `AmountDetails`
  - Provides industry-specific information about the amount.
- `ApplicationFeeAmount`
  - The amount of the application fee (if any) that will be requested to be applied to the
payment and transferred to the application owner's Stripe account. The amount of the
application fee collected will be capped at the total amount captured. For more
information, see the PaymentIntents use case for connected
accounts.
- `AutomaticPaymentMethods`
  - When you enable this parameter, this PaymentIntent accepts payment methods that you
enable in the Dashboard and that are compatible with this PaymentIntent's other
parameters.
- `CaptureMethod`
  - Controls when the funds will be captured from the customer's account.
One of: `automatic`, `automatic_async`, or `manual`.
- `Confirm`
  - Set to `true` to attempt to confirm this
PaymentIntent immediately. This parameter defaults to `false`. When creating
and confirming a PaymentIntent at the same time, you can also provide the parameters
available in the Confirm
API.
- `ConfirmationMethod`
  - Describes whether we can confirm this PaymentIntent automatically, or if it requires
customer action to confirm the payment.
One of: `automatic`, or `manual`.
- `ConfirmationToken`
  - ID of the ConfirmationToken used to confirm this PaymentIntent.

If the provided ConfirmationToken contains properties that are also being provided in
this request, such as `payment_method`, then the values in this request will take
precedence.
- `Currency`
  - Three-letter ISO currency
code, in lowercase. Must be a supported
currency.
- `Customer`
  - ID of the Customer this PaymentIntent belongs to, if one exists.

Payment methods attached to other Customers cannot be used with this PaymentIntent.

If setup_future_usage
is set and this PaymentIntent's payment method is not `card_present`, then the
payment method attaches to the Customer after the PaymentIntent has been confirmed and
any required actions from the user are complete. If the payment method is
`card_present` and isn't a digital wallet, then a generated_card
payment method representing the card is created and attached to the Customer instead.
- `CustomerAccount`
  - ID of the Account representing the customer that this PaymentIntent belongs to, if one
exists.

Payment methods attached to other Accounts cannot be used with this PaymentIntent.

If setup_future_usage
is set and this PaymentIntent's payment method is not `card_present`, then the
payment method attaches to the Account after the PaymentIntent has been confirmed and
any required actions from the user are complete. If the payment method is
`card_present` and isn't a digital wallet, then a generated_card
payment method representing the card is created and attached to the Account instead.
- `Description`
  - An arbitrary string attached to the object. Often useful for displaying to users.
- `ErrorOnRequiresAction`
  - Set to `true` to fail the payment attempt if the PaymentIntent transitions into
`requires_action`. Use this parameter for simpler integrations that don't handle
customer actions, such as saving cards
without authentication. This parameter can only be used with `confirm=true`.
- `ExcludedPaymentMethodTypes`
  - The list of payment method types to exclude from use with this payment.
One of: `acss_debit`, `affirm`, `afterpay_clearpay`, `alipay`,
`alma`, `amazon_pay`, `au_becs_debit`, `bacs_debit`,
`bancontact`, `billie`, `bizum`, `blik`, `boleto`, `card`,
`cashapp`, `crypto`, `customer_balance`, `eps`, `fpx`,
`giropay`, `grabpay`, `ideal`, `kakao_pay`, `klarna`,
`konbini`, `kr_card`, `mb_way`, `mobilepay`, `multibanco`,
`naver_pay`, `nz_bank_account`, `oxxo`, `p24`, `pay_by_bank`,
`payco`, `paynow`, `paypal`, `payto`, `pix`, `promptpay`,
`revolut_pay`, `samsung_pay`, `satispay`, `scalapay`,
`sepa_debit`, `sofort`, `sunbit`, `swish`, `twint`, `upi`,
`us_bank_account`, `wechat_pay`, or `zip`.
- `Hooks`
  - Automations to be run during the PaymentIntent lifecycle.
- `Mandate`
  - ID of the mandate that's used for this payment. This parameter can only be used with `confirm=true`.
- `MandateData`
  - This hash contains details about the Mandate to create. This parameter can only be used
with `confirm=true`.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format. Individual keys can be unset by posting an empty value to
them. All keys can be unset by posting an empty value to `metadata`.
- `OffSession`
  - Set to `true` to indicate that the customer isn't in your checkout flow during this
payment attempt and can't authenticate. Use this parameter in scenarios where you
collect payment method details and charge them later. This
parameter can only be used with `confirm=true`.
- `OnBehalfOf`
  - The Stripe account ID that these funds are intended for. Learn more about the use case for connected
accounts.
- `PaymentDetails`
  - Provides industry-specific information about the charge.
- `PaymentMethod`
  - ID of the payment method (a PaymentMethod, Card, or compatible
Source object) to attach to this PaymentIntent.

If you don't provide the `payment_method` parameter or the `source` parameter
with `confirm=true`, `source` automatically populates with
`customer.default_source` to improve migration for users of the Charges API. We
recommend that you explicitly provide the `payment_method` moving forward. If the
payment method is attached to a Customer, you must also provide the ID of that Customer
as the customer
parameter of this PaymentIntent. end.
- `PaymentMethodConfiguration`
  - The ID of the payment method
configuration to use with this PaymentIntent.
- `PaymentMethodData`
  - If provided, this hash will be used to create a PaymentMethod. The new PaymentMethod
will appear in the payment_method
property on the PaymentIntent.
- `PaymentMethodOptions`
  - Payment method-specific configuration for this PaymentIntent.
- `PaymentMethodTypes`
  - The list of payment method types (for example, a card) that this PaymentIntent can use.
If you don't provide this, Stripe will dynamically show relevant payment methods from
your payment method
settings. A list of valid payment method types can be found here.
- `RadarOptions`
  - Options to configure Radar. Learn more about Radar Sessions.
- `ReceiptEmail`
  - Email address to send the receipt to. If you specify `receipt_email` for a payment
in live mode, you send a receipt regardless of your email settings.
- `ReturnUrl`
  - The URL to redirect your customer back to after they authenticate or cancel their
payment on the payment method's app or site. If you'd prefer to redirect to a mobile
application, you can alternatively supply an application URI scheme. This parameter can
only be used with `confirm=true`.
- `SetupFutureUsage`
  - Indicates that you intend to make future payments with this PaymentIntent's payment
method.

If you provide a Customer with the PaymentIntent, you can use this parameter to attach the payment method to
the Customer after the PaymentIntent is confirmed and the customer completes any
required actions. If you don't provide a Customer, you can still attach the payment method to a
Customer after the transaction completes.

If the payment method is `card_present` and isn't a digital wallet, Stripe creates
and attaches a generated_card
payment method representing the card to the Customer instead.

When processing card payments, Stripe uses `setup_future_usage` to help you comply
with regional legislation and network rules, such as SCA.
One of: `off_session`, or `on_session`.
- `Shipping`
  - Shipping information for this PaymentIntent.
- `StatementDescriptor`
  - Text that appears on the customer's statement as the statement descriptor for a non-card
charge. This value overrides the account's default statement descriptor. For information
about requirements, including the 22-character limit, see the Statement
Descriptor docs.

Setting this value for a card charge returns an error. For card charges, set the statement_descriptor_suffix
instead.
- `StatementDescriptorSuffix`
  - Provides information about a card charge. Concatenated to the account's statement
descriptor prefix to form the complete statement descriptor that appears on the
customer's statement.
- `TransferData`
  - The parameters that you can use to automatically create a Transfer. Learn more about the
use case for connected
accounts.
- `TransferGroup`
  - A string that identifies the resulting payment as part of a group. Learn more about the
use case for
connected accounts.
- `UseStripeSdk`
  - Set to `true` when confirming server-side and using Stripe.js, iOS, or Android
client-side SDKs to handle the next actions.


#### `PaymentIntentUpdateOptions`

**Properties:**

- `Amount`
  - Amount intended to be collected by this PaymentIntent. A positive integer representing
how much to charge in the smallest currency unit (e.g.,
100 cents to charge $1.00 or 100 to charge ¥100, a zero-decimal currency). The minimum
amount is $0.50 US or equivalent
in charge currency. The amount value supports up to eight digits (e.g., a value of
99999999 for a USD charge of $999,999.99).
- `AmountDetails`
  - Provides industry-specific information about the amount.
- `ApplicationFeeAmount`
  - The amount of the application fee (if any) that will be requested to be applied to the
payment and transferred to the application owner's Stripe account. The amount of the
application fee collected will be capped at the total amount captured. For more
information, see the PaymentIntents use case for connected
accounts.
- `CaptureMethod`
  - Controls when the funds will be captured from the customer's account.
One of: `automatic`, `automatic_async`, or `manual`.
- `Currency`
  - Three-letter ISO currency
code, in lowercase. Must be a supported
currency.
- `Customer`
  - ID of the Customer this PaymentIntent belongs to, if one exists.

Payment methods attached to other Customers cannot be used with this PaymentIntent.

If setup_future_usage
is set and this PaymentIntent's payment method is not `card_present`, then the
payment method attaches to the Customer after the PaymentIntent has been confirmed and
any required actions from the user are complete. If the payment method is
`card_present` and isn't a digital wallet, then a generated_card
payment method representing the card is created and attached to the Customer instead.
- `CustomerAccount`
  - ID of the Account representing the customer that this PaymentIntent belongs to, if one
exists.

Payment methods attached to other Accounts cannot be used with this PaymentIntent.

If setup_future_usage
is set and this PaymentIntent's payment method is not `card_present`, then the
payment method attaches to the Account after the PaymentIntent has been confirmed and
any required actions from the user are complete. If the payment method is
`card_present` and isn't a digital wallet, then a generated_card
payment method representing the card is created and attached to the Account instead.
- `Description`
  - An arbitrary string attached to the object. Often useful for displaying to users.
- `ExcludedPaymentMethodTypes`
  - The list of payment method types to exclude from use with this payment.
One of: `acss_debit`, `affirm`, `afterpay_clearpay`, `alipay`,
`alma`, `amazon_pay`, `au_becs_debit`, `bacs_debit`,
`bancontact`, `billie`, `bizum`, `blik`, `boleto`, `card`,
`cashapp`, `crypto`, `customer_balance`, `eps`, `fpx`,
`giropay`, `grabpay`, `ideal`, `kakao_pay`, `klarna`,
`konbini`, `kr_card`, `mb_way`, `mobilepay`, `multibanco`,
`naver_pay`, `nz_bank_account`, `oxxo`, `p24`, `pay_by_bank`,
`payco`, `paynow`, `paypal`, `payto`, `pix`, `promptpay`,
`revolut_pay`, `samsung_pay`, `satispay`, `scalapay`,
`sepa_debit`, `sofort`, `sunbit`, `swish`, `twint`, `upi`,
`us_bank_account`, `wechat_pay`, or `zip`.
- `Hooks`
  - Automations to be run during the PaymentIntent lifecycle.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format. Individual keys can be unset by posting an empty value to
them. All keys can be unset by posting an empty value to `metadata`.
- `PaymentDetails`
  - Provides industry-specific information about the charge.
- `PaymentMethod`
  - ID of the payment method (a PaymentMethod, Card, or compatible
Source object) to attach to this PaymentIntent. To unset this field to null, pass in
an empty string.
- `PaymentMethodConfiguration`
  - The ID of the payment method
configuration to use with this PaymentIntent.
- `PaymentMethodData`
  - If provided, this hash will be used to create a PaymentMethod. The new PaymentMethod
will appear in the payment_method
property on the PaymentIntent.
- `PaymentMethodOptions`
  - Payment-method-specific configuration for this PaymentIntent.
- `PaymentMethodTypes`
  - The list of payment method types (for example, card) that this PaymentIntent can use.
Use `automatic_payment_methods` to manage payment methods from the Stripe Dashboard. A
list of valid payment method types can be found here.
- `ReceiptEmail`
  - Email address that the receipt for the resulting payment will be sent to. If
`receipt_email` is specified for a payment in live mode, a receipt will be sent
regardless of your email
settings.
- `SetupFutureUsage`
  - Indicates that you intend to make future payments with this PaymentIntent's payment
method.

If you provide a Customer with the PaymentIntent, you can use this parameter to attach the payment method to
the Customer after the PaymentIntent is confirmed and the customer completes any
required actions. If you don't provide a Customer, you can still attach the payment method to a
Customer after the transaction completes.

If the payment method is `card_present` and isn't a digital wallet, Stripe creates
and attaches a generated_card
payment method representing the card to the Customer instead.

When processing card payments, Stripe uses `setup_future_usage` to help you comply
with regional legislation and network rules, such as SCA.

If you've already set `setup_future_usage` and you're performing a request using a
publishable key, you can only update the value from `on_session` to
`off_session`.
One of: `off_session`, or `on_session`.
- `Shipping`
  - Shipping information for this PaymentIntent.
- `StatementDescriptor`
  - Text that appears on the customer's statement as the statement descriptor for a non-card
charge. This value overrides the account's default statement descriptor. For information
about requirements, including the 22-character limit, see the Statement
Descriptor docs.

Setting this value for a card charge returns an error. For card charges, set the statement_descriptor_suffix
instead.
- `StatementDescriptorSuffix`
  - Provides information about a card charge. Concatenated to the account's statement
descriptor prefix to form the complete statement descriptor that appears on the
customer's statement.
- `TransferData`
  - Use this parameter to automatically create a Transfer when the payment succeeds. Learn
more about the use case
for connected accounts.
- `TransferGroup`
  - A string that identifies the resulting payment as part of a group. You can only provide
`transfer_group` if it hasn't been set. Learn more about the use case for connected
accounts.


#### `PaymentIntentListOptions`

**Properties:**

- `Created`
  - A filter on the list, based on the object `created` field. The value can be a
string with an integer Unix timestamp or a dictionary with a number of different query
options.
- `Customer`
  - Only return PaymentIntents for the customer that this customer ID specifies.
- `CustomerAccount`
  - Only return PaymentIntents for the account representing the customer that this ID
specifies.


#### `PaymentIntentGetOptions`

**Properties:**

- `ClientSecret`
  - The client secret of the PaymentIntent. We require it if you use a publishable key to
retrieve the source.


#### `PaymentIntentCancelOptions`

**Properties:**

- `CancellationReason`
  - Reason for canceling this PaymentIntent. Possible values are: `duplicate`,
`fraudulent`, `requested_by_customer`, or `abandoned`.
One of: `abandoned`, `duplicate`, `fraudulent`, or
`requested_by_customer`.


#### `PaymentIntentCaptureOptions`

**Properties:**

- `AmountDetails`
  - Provides industry-specific information about the amount.
- `AmountToCapture`
  - The amount to capture from the PaymentIntent, which must be less than or equal to the
original amount. Defaults to the full `amount_capturable` if it's not provided.
- `ApplicationFeeAmount`
  - The amount of the application fee (if any) that will be requested to be applied to the
payment and transferred to the application owner's Stripe account. The amount of the
application fee collected will be capped at the total amount captured. For more
information, see the PaymentIntents use case for connected
accounts.
- `FinalCapture`
  - Defaults to `true`. When capturing a PaymentIntent, setting `final_capture` to
`false` notifies Stripe to not release the remaining uncaptured funds to make sure
that they're captured in future requests. You can only use this setting when multicapture is available for
PaymentIntents.
- `Hooks`
  - Automations to be run during the PaymentIntent lifecycle.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format. Individual keys can be unset by posting an empty value to
them. All keys can be unset by posting an empty value to `metadata`.
- `PaymentDetails`
  - Provides industry-specific information about the charge.
- `StatementDescriptor`
  - Text that appears on the customer's statement as the statement descriptor for a non-card
charge. This value overrides the account's default statement descriptor. For information
about requirements, including the 22-character limit, see the Statement
Descriptor docs.

Setting this value for a card charge returns an error. For card charges, set the statement_descriptor_suffix
instead.
- `StatementDescriptorSuffix`
  - Provides information about a card charge. Concatenated to the account's statement
descriptor prefix to form the complete statement descriptor that appears on the
customer's statement.
- `TransferData`
  - The parameters that you can use to automatically create a transfer after the payment is
captured. Learn more about the use case for connected
accounts.


#### `PaymentIntentConfirmOptions`

**Properties:**

- `AmountDetails`
  - Provides industry-specific information about the amount.
- `AmountToConfirm`
  - Amount to confirm on the PaymentIntent. Defaults to `amount` if not provided.
- `CaptureMethod`
  - Controls when the funds will be captured from the customer's account.
One of: `automatic`, `automatic_async`, or `manual`.
- `ConfirmationToken`
  - ID of the ConfirmationToken used to confirm this PaymentIntent.

If the provided ConfirmationToken contains properties that are also being provided in
this request, such as `payment_method`, then the values in this request will take
precedence.
- `ErrorOnRequiresAction`
  - Set to `true` to fail the payment attempt if the PaymentIntent transitions into
`requires_action`. This parameter is intended for simpler integrations that do not
handle customer actions, like saving cards
without authentication.
- `ExcludedPaymentMethodTypes`
  - The list of payment method types to exclude from use with this payment.
One of: `acss_debit`, `affirm`, `afterpay_clearpay`, `alipay`,
`alma`, `amazon_pay`, `au_becs_debit`, `bacs_debit`,
`bancontact`, `billie`, `bizum`, `blik`, `boleto`, `card`,
`cashapp`, `crypto`, `customer_balance`, `eps`, `fpx`,
`giropay`, `grabpay`, `ideal`, `kakao_pay`, `klarna`,
`konbini`, `kr_card`, `mb_way`, `mobilepay`, `multibanco`,
`naver_pay`, `nz_bank_account`, `oxxo`, `p24`, `pay_by_bank`,
`payco`, `paynow`, `paypal`, `payto`, `pix`, `promptpay`,
`revolut_pay`, `samsung_pay`, `satispay`, `scalapay`,
`sepa_debit`, `sofort`, `sunbit`, `swish`, `twint`, `upi`,
`us_bank_account`, `wechat_pay`, or `zip`.
- `Hooks`
  - Automations to be run during the PaymentIntent lifecycle.
- `Mandate`
  - ID of the mandate that's used for this payment.
- `OffSession`
  - Set to `true` to indicate that the customer isn't in your checkout flow during this
payment attempt and can't authenticate. Use this parameter in scenarios where you
collect payment method details and charge them later.
- `PaymentDetails`
  - Provides industry-specific information about the charge.
- `PaymentMethod`
  - ID of the payment method (a PaymentMethod, Card, or compatible
Source object) to attach to this PaymentIntent. If the payment method is attached to
a Customer, it must match the customer that is set on
this PaymentIntent.
- `PaymentMethodData`
  - If provided, this hash will be used to create a PaymentMethod. The new PaymentMethod
will appear in the payment_method
property on the PaymentIntent.
- `PaymentMethodOptions`
  - Payment method-specific configuration for this PaymentIntent.
- `PaymentMethodTypes`
  - The list of payment method types (for example, a card) that this PaymentIntent can use.
Use `automatic_payment_methods` to manage payment methods from the Stripe Dashboard. A
list of valid payment method types can be found here.
- `RadarOptions`
  - Options to configure Radar. Learn more about Radar Sessions.
- `ReceiptEmail`
  - Email address that the receipt for the resulting payment will be sent to. If
`receipt_email` is specified for a payment in live mode, a receipt will be sent
regardless of your email
settings.
- `ReturnUrl`
  - The URL to redirect your customer back to after they authenticate or cancel their
payment on the payment method's app or site. If you'd prefer to redirect to a mobile
application, you can alternatively supply an application URI scheme. This parameter is
only used for cards and other redirect-based payment methods.
- `SetupFutureUsage`
  - Indicates that you intend to make future payments with this PaymentIntent's payment
method.

If you provide a Customer with the PaymentIntent, you can use this parameter to attach the payment method to
the Customer after the PaymentIntent is confirmed and the customer completes any
required actions. If you don't provide a Customer, you can still attach the payment method to a
Customer after the transaction completes.

If the payment method is `card_present` and isn't a digital wallet, Stripe creates
and attaches a generated_card
payment method representing the card to the Customer instead.

When processing card payments, Stripe uses `setup_future_usage` to help you comply
with regional legislation and network rules, such as SCA.

If you've already set `setup_future_usage` and you're performing a request using a
publishable key, you can only update the value from `on_session` to
`off_session`.
One of: `off_session`, or `on_session`.
- `Shipping`
  - Shipping information for this PaymentIntent.
- `UseStripeSdk`
  - Set to `true` when confirming server-side and using Stripe.js, iOS, or Android
client-side SDKs to handle the next actions.


### SetupIntent

#### `SetupIntent`

A SetupIntent guides you through the process of setting up and saving a customer's
payment credentials for future payments. For example, you can use a SetupIntent to set
up and save your customer's card without immediately collecting a payment. Later, you
can use PaymentIntents to drive the
payment flow.

Create a SetupIntent when you're ready to collect your customer's payment credentials.
Don't maintain long-lived, unconfirmed SetupIntents because they might not be valid. The
SetupIntent transitions through multiple statuses as it
guides you through the setup process.

Successful SetupIntents result in payment credentials that are optimized for future
payments. For example, cardholders in certain regions
might need to be run through Strong Customer
Authentication during payment method collection to streamline later off-session payments. If you
use the SetupIntent with a Customer, it
automatically attaches the resulting payment method to that Customer after successful
setup. We recommend using SetupIntents or setup_future_usage
on PaymentIntents to save payment methods to prevent saving invalid or unoptimized
payment methods.

By using SetupIntents, you can reduce friction for your customers, even as regulations
change over time.

Related guide: Setup Intents
API.

**Properties:**

- `Application`
  - (Expanded)
ID of the Connect application that created the SetupIntent.

For more information, see the expand documentation.
- `ApplicationId`
  - (ID of the Application)
ID of the Connect application that created the SetupIntent.
- `AttachToSelf`
  - If present, the SetupIntent's payment method will be attached to the in-context Stripe
Account.

It can only be used for this Stripe Account’s own money movement flows like
InboundTransfer and OutboundTransfers. It cannot be set to true when setting up a
PaymentMethod for a Customer, and defaults to false when attaching a PaymentMethod to a
Customer.
- `AutomaticPaymentMethods`
  - Settings for dynamic payment methods compatible with this Setup Intent.
- `CancellationReason`
  - Reason for cancellation of this SetupIntent, one of `abandoned`,
`requested_by_customer`, or `duplicate`.
One of: `abandoned`, `duplicate`, or `requested_by_customer`.
- `ClientSecret`
  - The client secret of this SetupIntent. Used for client-side retrieval using a
publishable key.

The client secret can be used to complete payment setup from your frontend. It should
not be stored, logged, or exposed to anyone other than the customer. Make sure that you
have TLS enabled on any page that includes the client secret.
- `Created`
  - Time at which the object was created. Measured in seconds since the Unix epoch.
- `Customer`
  - (Expanded)
ID of the Customer this SetupIntent belongs to, if one exists.

If present, the SetupIntent's payment method will be attached to the Customer on
successful setup. Payment methods attached to other Customers cannot be used with this
SetupIntent.

For more information, see the expand documentation.
- `CustomerAccount`
  - ID of the Account this SetupIntent belongs to, if one exists.

If present, the SetupIntent's payment method will be attached to the Account on
successful setup. Payment methods attached to other Accounts cannot be used with this
SetupIntent.
- `CustomerId`
  - (ID of the Customer)
ID of the Customer this SetupIntent belongs to, if one exists.

If present, the SetupIntent's payment method will be attached to the Customer on
successful setup. Payment methods attached to other Customers cannot be used with this
SetupIntent.
- `Description`
  - An arbitrary string attached to the object. Often useful for displaying to users.
- `ExcludedPaymentMethodTypes`
  - Payment method types that are excluded from this SetupIntent.
One of: `acss_debit`, `affirm`, `afterpay_clearpay`, `alipay`,
`alma`, `amazon_pay`, `au_becs_debit`, `bacs_debit`,
`bancontact`, `billie`, `bizum`, `blik`, `boleto`, `card`,
`cashapp`, `crypto`, `customer_balance`, `eps`, `fpx`,
`giropay`, `grabpay`, `ideal`, `kakao_pay`, `klarna`,
`konbini`, `kr_card`, `mb_way`, `mobilepay`, `multibanco`,
`naver_pay`, `nz_bank_account`, `oxxo`, `p24`, `pay_by_bank`,
`payco`, `paynow`, `paypal`, `payto`, `pix`, `promptpay`,
`revolut_pay`, `samsung_pay`, `satispay`, `scalapay`,
`sepa_debit`, `sofort`, `sunbit`, `swish`, `twint`, `upi`,
`us_bank_account`, `wechat_pay`, or `zip`.
- `FlowDirections`
  - Indicates the directions of money movement for which this payment method is intended to
be used.

Include `inbound` if you intend to use the payment method as the origin to pull
funds from. Include `outbound` if you intend to use the payment method as the
destination to send funds to. You can include both if you intend to use the payment
method for both purposes.
One of: `inbound`, or `outbound`.
- `Id`
  - Unique identifier for the object.
- `LastSetupError`
  - The error encountered in the previous SetupIntent confirmation.
- `LatestAttempt`
  - (Expanded)
The most recent SetupAttempt for this SetupIntent.

For more information, see the expand documentation.
- `LatestAttemptId`
  - (ID of the SetupAttempt)
The most recent SetupAttempt for this SetupIntent.
- `Livemode`
  - If the object exists in live mode, the value is `true`. If the object exists in
test mode, the value is `false`.
- `Mandate`
  - (Expanded)
ID of the multi use Mandate generated by the SetupIntent.

For more information, see the expand documentation.
- `MandateId`
  - (ID of the Mandate)
ID of the multi use Mandate generated by the SetupIntent.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format.
- `NextAction`
  - If present, this property tells you what actions you need to take in order for your
customer to continue payment setup.
- `Object`
  - String representing the object's type. Objects of the same type share the same value.
- `OnBehalfOf`
  - (Expanded)
The account (if any) for which the setup is intended.

For more information, see the expand documentation.
- `OnBehalfOfId`
  - (ID of the Account)
The account (if any) for which the setup is intended.
- `PaymentMethod`
  - (Expanded)
ID of the payment method used with this SetupIntent. If the payment method is
`card_present` and isn't a digital wallet, then the generated_card
associated with the `latest_attempt` is attached to the Customer instead.

For more information, see the expand documentation.
- `PaymentMethodConfigurationDetails`
  - Information about the payment method
configuration used for this Setup Intent.
- `PaymentMethodId`
  - (ID of the PaymentMethod)
ID of the payment method used with this SetupIntent. If the payment method is
`card_present` and isn't a digital wallet, then the generated_card
associated with the `latest_attempt` is attached to the Customer instead.
- `PaymentMethodOptions`
  - Payment method-specific configuration for this SetupIntent.
- `PaymentMethodTypes`
  - The list of payment method types (e.g. card) that this SetupIntent is allowed to set up.
A list of valid payment method types can be found here.
- `SingleUseMandate`
  - (Expanded)
ID of the single_use Mandate generated by the SetupIntent.

For more information, see the expand documentation.
- `SingleUseMandateId`
  - (ID of the Mandate)
ID of the single_use Mandate generated by the SetupIntent.
- `Status`
  - Status of this
SetupIntent, one of `requires_payment_method`, `requires_confirmation`,
`requires_action`, `processing`, `canceled`, or `succeeded`.
One of: `canceled`, `processing`, `requires_action`,
`requires_confirmation`, `requires_payment_method`, or `succeeded`.
- `Usage`
  - Indicates how the payment method is intended to be used in the future.

Use `on_session` if you intend to only reuse the payment method when the customer
is in your checkout flow. Use `off_session` if your customer may or may not be in
your checkout flow. If not provided, this value defaults to `off_session`.


#### `SetupIntentService`

**Methods:**

- `Cancel(string, Stripe.SetupIntentCancelOptions, Stripe.RequestOptions)`
  - You can cancel a SetupIntent object when it’s in one of these statuses:
`requires_payment_method`, `requires_confirmation`, or `requires_action`..

After you cancel it, setup is abandoned and any operations on the SetupIntent fail
with an error. You can’t cancel the SetupIntent for a Checkout Session. Expire the Checkout
Session instead..
- `CancelAsync(string, Stripe.SetupIntentCancelOptions, Stripe.RequestOptions, CancellationToken)`
  - You can cancel a SetupIntent object when it’s in one of these statuses:
`requires_payment_method`, `requires_confirmation`, or `requires_action`..

After you cancel it, setup is abandoned and any operations on the SetupIntent fail
with an error. You can’t cancel the SetupIntent for a Checkout Session. Expire the Checkout
Session instead..
- `Confirm(string, Stripe.SetupIntentConfirmOptions, Stripe.RequestOptions)`
  - Confirm that your customer intends to set up the current or provided payment method.
For example, you would confirm a SetupIntent when a customer hits the “Save” button on a
payment method management page on your website..

If the selected payment method does not require any additional steps from the
customer, the SetupIntent will transition to the `succeeded` status..

Otherwise, it will transition to the `requires_action` status and suggest
additional actions via `next_action`. If setup fails, the SetupIntent will
transition to the `requires_payment_method` status or the `canceled` status if
the confirmation limit is reached..
- `ConfirmAsync(string, Stripe.SetupIntentConfirmOptions, Stripe.RequestOptions, CancellationToken)`
  - Confirm that your customer intends to set up the current or provided payment method.
For example, you would confirm a SetupIntent when a customer hits the “Save” button on a
payment method management page on your website..

If the selected payment method does not require any additional steps from the
customer, the SetupIntent will transition to the `succeeded` status..

Otherwise, it will transition to the `requires_action` status and suggest
additional actions via `next_action`. If setup fails, the SetupIntent will
transition to the `requires_payment_method` status or the `canceled` status if
the confirmation limit is reached..
- `Create(Stripe.SetupIntentCreateOptions, Stripe.RequestOptions)`
  - Creates a SetupIntent object..

After you create the SetupIntent, attach a payment method and confirm it to collect any
required permissions to charge the payment method later..
- `CreateAsync(Stripe.SetupIntentCreateOptions, Stripe.RequestOptions, CancellationToken)`
  - Creates a SetupIntent object..

After you create the SetupIntent, attach a payment method and confirm it to collect any
required permissions to charge the payment method later..
- `Get(string, Stripe.SetupIntentGetOptions, Stripe.RequestOptions)`
  - Retrieves the details of a SetupIntent that has previously been created..

Client-side retrieval using a publishable key is allowed when the
`client_secret` is provided in the query string..

When retrieved with a publishable key, only a subset of properties will be returned.
Please refer to the SetupIntent object reference
for more details..
- `GetAsync(string, Stripe.SetupIntentGetOptions, Stripe.RequestOptions, CancellationToken)`
  - Retrieves the details of a SetupIntent that has previously been created..

Client-side retrieval using a publishable key is allowed when the
`client_secret` is provided in the query string..

When retrieved with a publishable key, only a subset of properties will be returned.
Please refer to the SetupIntent object reference
for more details..
- `List(Stripe.SetupIntentListOptions, Stripe.RequestOptions)`
  - Returns a list of SetupIntents..
- `ListAsync(Stripe.SetupIntentListOptions, Stripe.RequestOptions, CancellationToken)`
  - Returns a list of SetupIntents..
- `ListAutoPaging(Stripe.SetupIntentListOptions, Stripe.RequestOptions)`
  - Returns a list of SetupIntents..
- `ListAutoPagingAsync(Stripe.SetupIntentListOptions, Stripe.RequestOptions, CancellationToken)`
  - Returns a list of SetupIntents..
- `Update(string, Stripe.SetupIntentUpdateOptions, Stripe.RequestOptions)`
  - Updates a SetupIntent object..
- `UpdateAsync(string, Stripe.SetupIntentUpdateOptions, Stripe.RequestOptions, CancellationToken)`
  - Updates a SetupIntent object..
- `VerifyMicrodeposits(string, Stripe.SetupIntentVerifyMicrodepositsOptions, Stripe.RequestOptions)`
  - Verifies microdeposits on a SetupIntent object..
- `VerifyMicrodepositsAsync(string, Stripe.SetupIntentVerifyMicrodepositsOptions, Stripe.RequestOptions, CancellationToken)`
  - Verifies microdeposits on a SetupIntent object..


#### `SetupIntentCreateOptions`

**Properties:**

- `AttachToSelf`
  - If present, the SetupIntent's payment method will be attached to the in-context Stripe
Account.

It can only be used for this Stripe Account’s own money movement flows like
InboundTransfer and OutboundTransfers. It cannot be set to true when setting up a
PaymentMethod for a Customer, and defaults to false when attaching a PaymentMethod to a
Customer.
- `AutomaticPaymentMethods`
  - When you enable this parameter, this SetupIntent accepts payment methods that you enable
in the Dashboard and that are compatible with its other parameters.
- `Confirm`
  - Set to `true` to attempt to confirm this SetupIntent immediately. This parameter
defaults to `false`. If a card is the attached payment method, you can provide a
`return_url` in case further authentication is necessary.
- `ConfirmationToken`
  - ID of the ConfirmationToken used to confirm this SetupIntent.

If the provided ConfirmationToken contains properties that are also being provided in
this request, such as `payment_method`, then the values in this request will take
precedence.
- `Customer`
  - ID of the Customer this SetupIntent belongs to, if one exists.

If present, the SetupIntent's payment method will be attached to the Customer on
successful setup. Payment methods attached to other Customers cannot be used with this
SetupIntent.
- `CustomerAccount`
  - ID of the Account this SetupIntent belongs to, if one exists.

If present, the SetupIntent's payment method will be attached to the Account on
successful setup. Payment methods attached to other Accounts cannot be used with this
SetupIntent.
- `Description`
  - An arbitrary string attached to the object. Often useful for displaying to users.
- `ExcludedPaymentMethodTypes`
  - The list of payment method types to exclude from use with this SetupIntent.
One of: `acss_debit`, `affirm`, `afterpay_clearpay`, `alipay`,
`alma`, `amazon_pay`, `au_becs_debit`, `bacs_debit`,
`bancontact`, `billie`, `bizum`, `blik`, `boleto`, `card`,
`cashapp`, `crypto`, `customer_balance`, `eps`, `fpx`,
`giropay`, `grabpay`, `ideal`, `kakao_pay`, `klarna`,
`konbini`, `kr_card`, `mb_way`, `mobilepay`, `multibanco`,
`naver_pay`, `nz_bank_account`, `oxxo`, `p24`, `pay_by_bank`,
`payco`, `paynow`, `paypal`, `payto`, `pix`, `promptpay`,
`revolut_pay`, `samsung_pay`, `satispay`, `scalapay`,
`sepa_debit`, `sofort`, `sunbit`, `swish`, `twint`, `upi`,
`us_bank_account`, `wechat_pay`, or `zip`.
- `FlowDirections`
  - Indicates the directions of money movement for which this payment method is intended to
be used.

Include `inbound` if you intend to use the payment method as the origin to pull
funds from. Include `outbound` if you intend to use the payment method as the
destination to send funds to. You can include both if you intend to use the payment
method for both purposes.
One of: `inbound`, or `outbound`.
- `MandateData`
  - This hash contains details about the mandate to create. This parameter can only be used
with `confirm=true`.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format. Individual keys can be unset by posting an empty value to
them. All keys can be unset by posting an empty value to `metadata`.
- `OnBehalfOf`
  - The Stripe account ID created for this SetupIntent.
- `PaymentMethod`
  - ID of the payment method (a PaymentMethod, Card, or saved Source object) to attach to
this SetupIntent.
- `PaymentMethodConfiguration`
  - The ID of the payment method
configuration to use with this SetupIntent.
- `PaymentMethodData`
  - When included, this hash creates a PaymentMethod that is set as the `payment_method`
value in the SetupIntent.
- `PaymentMethodOptions`
  - Payment method-specific configuration for this SetupIntent.
- `PaymentMethodTypes`
  - The list of payment method types (for example, card) that this SetupIntent can use. If
you don't provide this, Stripe will dynamically show relevant payment methods from your
payment method
settings. A list of valid payment method types can be found here.
- `ReturnUrl`
  - The URL to redirect your customer back to after they authenticate or cancel their
payment on the payment method's app or site. To redirect to a mobile application, you
can alternatively supply an application URI scheme. This parameter can only be used with
`confirm=true`.
- `SingleUse`
  - If you populate this hash, this SetupIntent generates a `single_use` mandate after
successful completion.

Single-use mandates are only valid for the following payment methods: `acss_debit`,
`alipay`, `au_becs_debit`, `bacs_debit`, `bancontact`,
`boleto`, `ideal`, `link`, `sepa_debit`, and `us_bank_account`.
- `Usage`
  - Indicates how the payment method is intended to be used in the future. If not provided,
this value defaults to `off_session`.
One of: `off_session`, or `on_session`.
- `UseStripeSdk`
  - Set to `true` when confirming server-side and using Stripe.js, iOS, or Android
client-side SDKs to handle the next actions.


#### `SetupIntentUpdateOptions`

**Properties:**

- `AttachToSelf`
  - If present, the SetupIntent's payment method will be attached to the in-context Stripe
Account.

It can only be used for this Stripe Account’s own money movement flows like
InboundTransfer and OutboundTransfers. It cannot be set to true when setting up a
PaymentMethod for a Customer, and defaults to false when attaching a PaymentMethod to a
Customer.
- `Customer`
  - ID of the Customer this SetupIntent belongs to, if one exists.

If present, the SetupIntent's payment method will be attached to the Customer on
successful setup. Payment methods attached to other Customers cannot be used with this
SetupIntent.
- `CustomerAccount`
  - ID of the Account this SetupIntent belongs to, if one exists.

If present, the SetupIntent's payment method will be attached to the Account on
successful setup. Payment methods attached to other Accounts cannot be used with this
SetupIntent.
- `Description`
  - An arbitrary string attached to the object. Often useful for displaying to users.
- `ExcludedPaymentMethodTypes`
  - The list of payment method types to exclude from use with this SetupIntent.
One of: `acss_debit`, `affirm`, `afterpay_clearpay`, `alipay`,
`alma`, `amazon_pay`, `au_becs_debit`, `bacs_debit`,
`bancontact`, `billie`, `bizum`, `blik`, `boleto`, `card`,
`cashapp`, `crypto`, `customer_balance`, `eps`, `fpx`,
`giropay`, `grabpay`, `ideal`, `kakao_pay`, `klarna`,
`konbini`, `kr_card`, `mb_way`, `mobilepay`, `multibanco`,
`naver_pay`, `nz_bank_account`, `oxxo`, `p24`, `pay_by_bank`,
`payco`, `paynow`, `paypal`, `payto`, `pix`, `promptpay`,
`revolut_pay`, `samsung_pay`, `satispay`, `scalapay`,
`sepa_debit`, `sofort`, `sunbit`, `swish`, `twint`, `upi`,
`us_bank_account`, `wechat_pay`, or `zip`.
- `FlowDirections`
  - Indicates the directions of money movement for which this payment method is intended to
be used.

Include `inbound` if you intend to use the payment method as the origin to pull
funds from. Include `outbound` if you intend to use the payment method as the
destination to send funds to. You can include both if you intend to use the payment
method for both purposes.
One of: `inbound`, or `outbound`.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format. Individual keys can be unset by posting an empty value to
them. All keys can be unset by posting an empty value to `metadata`.
- `PaymentMethod`
  - ID of the payment method (a PaymentMethod, Card, or saved Source object) to attach to
this SetupIntent. To unset this field to null, pass in an empty string.
- `PaymentMethodConfiguration`
  - The ID of the payment method
configuration to use with this SetupIntent.
- `PaymentMethodData`
  - When included, this hash creates a PaymentMethod that is set as the `payment_method`
value in the SetupIntent.
- `PaymentMethodOptions`
  - Payment method-specific configuration for this SetupIntent.
- `PaymentMethodTypes`
  - The list of payment method types (for example, card) that this SetupIntent can set up.
If you don't provide this, Stripe will dynamically show relevant payment methods from
your payment method
settings. A list of valid payment method types can be found here.


#### `SetupIntentListOptions`

**Properties:**

- `AttachToSelf`
  - If present, the SetupIntent's payment method will be attached to the in-context Stripe
Account.

It can only be used for this Stripe Account’s own money movement flows like
InboundTransfer and OutboundTransfers. It cannot be set to true when setting up a
PaymentMethod for a Customer, and defaults to false when attaching a PaymentMethod to a
Customer.
- `Created`
  - A filter on the list, based on the object `created` field. The value can be a
string with an integer Unix timestamp, or it can be a dictionary with a number of
different query options.
- `Customer`
  - Only return SetupIntents for the customer specified by this customer ID.
- `CustomerAccount`
  - Only return SetupIntents for the account specified by this customer ID.
- `PaymentMethod`
  - Only return SetupIntents that associate with the specified payment method.


#### `SetupIntentGetOptions`

**Properties:**

- `ClientSecret`
  - The client secret of the SetupIntent. We require this string if you use a publishable
key to retrieve the SetupIntent.


#### `SetupIntentCancelOptions`

**Properties:**

- `CancellationReason`
  - Reason for canceling this SetupIntent. Possible values are: `abandoned`,
`requested_by_customer`, or `duplicate`.
One of: `abandoned`, `duplicate`, or `requested_by_customer`.


#### `SetupIntentConfirmOptions`

**Properties:**

- `ConfirmationToken`
  - ID of the ConfirmationToken used to confirm this SetupIntent.

If the provided ConfirmationToken contains properties that are also being provided in
this request, such as `payment_method`, then the values in this request will take
precedence.
- `PaymentMethod`
  - ID of the payment method (a PaymentMethod, Card, or saved Source object) to attach to
this SetupIntent.
- `PaymentMethodData`
  - When included, this hash creates a PaymentMethod that is set as the `payment_method`
value in the SetupIntent.
- `PaymentMethodOptions`
  - Payment method-specific configuration for this SetupIntent.
- `ReturnUrl`
  - The URL to redirect your customer back to after they authenticate on the payment
method's app or site. If you'd prefer to redirect to a mobile application, you can
alternatively supply an application URI scheme. This parameter is only used for cards
and other redirect-based payment methods.
- `UseStripeSdk`
  - Set to `true` when confirming server-side and using Stripe.js, iOS, or Android
client-side SDKs to handle the next actions.


### PaymentMethod

#### `PaymentMethod`

PaymentMethod objects represent your customer's payment instruments. You can use them
with PaymentIntents to
collect payments or save them to Customer objects to store instrument details for future
payments.

Related guides: Payment
Methods and More
Payment Scenarios.

**Properties:**

- `AllowRedisplay`
  - This field indicates whether this payment method can be shown again to its customer in a
checkout flow. Stripe products such as Checkout and Elements use this field to determine
whether a payment method can be shown as a saved payment method in a checkout flow. The
field defaults to “unspecified”.
One of: `always`, `limited`, or `unspecified`.
- `Created`
  - Time at which the object was created. Measured in seconds since the Unix epoch.
- `Customer`
  - (Expanded)
The ID of the Customer to which this PaymentMethod is saved. This will not be set when
the PaymentMethod has not been saved to a Customer.

For more information, see the expand documentation.
- `CustomerId`
  - (ID of the Customer)
The ID of the Customer to which this PaymentMethod is saved. This will not be set when
the PaymentMethod has not been saved to a Customer.
- `Id`
  - Unique identifier for the object.
- `Livemode`
  - If the object exists in live mode, the value is `true`. If the object exists in
test mode, the value is `false`.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format.
- `Object`
  - String representing the object's type. Objects of the same type share the same value.
- `RadarOptions`
  - Options to configure Radar. See Radar Session for more
information.
- `Type`
  - The type of the PaymentMethod. An additional hash is included on the PaymentMethod with
a name matching this value. It contains additional information specific to the
PaymentMethod type.
One of: `acss_debit`, `affirm`, `afterpay_clearpay`, `alipay`,
`alma`, `amazon_pay`, `au_becs_debit`, `bacs_debit`,
`bancontact`, `billie`, `bizum`, `blik`, `boleto`, `card`,
`card_present`, `cashapp`, `crypto`, `custom`,
`customer_balance`, `eps`, `fpx`, `giropay`, `grabpay`,
`ideal`, `interac_present`, `kakao_pay`, `klarna`, `konbini`,
`kr_card`, `link`, `mb_way`, `mobilepay`, `multibanco`,
`naver_pay`, `nz_bank_account`, `oxxo`, `p24`, `pay_by_bank`,
`payco`, `paynow`, `paypal`, `payto`, `pix`, `promptpay`,
`revolut_pay`, `samsung_pay`, `satispay`, `scalapay`,
`sepa_debit`, `sofort`, `sunbit`, `swish`, `twint`, `upi`,
`us_bank_account`, `wechat_pay`, or `zip`.


#### `PaymentMethodService`

**Methods:**

- `Attach(string, Stripe.PaymentMethodAttachOptions, Stripe.RequestOptions)`
  - Attaches a PaymentMethod object to a Customer..

To attach a new PaymentMethod to a customer for future payments, we recommend you use
a SetupIntent or a PaymentIntent
with setup_future_usage.
These approaches will perform any necessary steps to set up the PaymentMethod for future
payments. Using the `/v1/payment_methods/:id/attach` endpoint without first using a
SetupIntent or PaymentIntent with `setup_future_usage` does not optimize the
PaymentMethod for future use, which makes later declines and payment friction more
likely. See Optimizing cards
for future payments for more information about setting up future payments..

To use this PaymentMethod as the default for invoice or subscription payments, set `invoice_settings.default_payment_method`,
on the Customer to the PaymentMethod’s ID..
- `AttachAsync(string, Stripe.PaymentMethodAttachOptions, Stripe.RequestOptions, CancellationToken)`
  - Attaches a PaymentMethod object to a Customer..

To attach a new PaymentMethod to a customer for future payments, we recommend you use
a SetupIntent or a PaymentIntent
with setup_future_usage.
These approaches will perform any necessary steps to set up the PaymentMethod for future
payments. Using the `/v1/payment_methods/:id/attach` endpoint without first using a
SetupIntent or PaymentIntent with `setup_future_usage` does not optimize the
PaymentMethod for future use, which makes later declines and payment friction more
likely. See Optimizing cards
for future payments for more information about setting up future payments..

To use this PaymentMethod as the default for invoice or subscription payments, set `invoice_settings.default_payment_method`,
on the Customer to the PaymentMethod’s ID..
- `Create(Stripe.PaymentMethodCreateOptions, Stripe.RequestOptions)`
  - Creates a PaymentMethod object. Read the Stripe.js
reference to learn how to create PaymentMethods via Stripe.js..

Instead of creating a PaymentMethod directly, we recommend using the PaymentIntents API to
accept a payment immediately or the SetupIntent API to collect
payment method details ahead of a future payment..
- `CreateAsync(Stripe.PaymentMethodCreateOptions, Stripe.RequestOptions, CancellationToken)`
  - Creates a PaymentMethod object. Read the Stripe.js
reference to learn how to create PaymentMethods via Stripe.js..

Instead of creating a PaymentMethod directly, we recommend using the PaymentIntents API to
accept a payment immediately or the SetupIntent API to collect
payment method details ahead of a future payment..
- `Detach(string, Stripe.PaymentMethodDetachOptions, Stripe.RequestOptions)`
  - Detaches a PaymentMethod object from a Customer. After a PaymentMethod is detached,
it can no longer be used for a payment or re-attached to a Customer..
- `DetachAsync(string, Stripe.PaymentMethodDetachOptions, Stripe.RequestOptions, CancellationToken)`
  - Detaches a PaymentMethod object from a Customer. After a PaymentMethod is detached,
it can no longer be used for a payment or re-attached to a Customer..
- `Get(string, Stripe.PaymentMethodGetOptions, Stripe.RequestOptions)`
  - Retrieves a PaymentMethod object attached to the StripeAccount. To retrieve a payment
method attached to a Customer, you should use Retrieve a Customer’s
PaymentMethods.
- `GetAsync(string, Stripe.PaymentMethodGetOptions, Stripe.RequestOptions, CancellationToken)`
  - Retrieves a PaymentMethod object attached to the StripeAccount. To retrieve a payment
method attached to a Customer, you should use Retrieve a Customer’s
PaymentMethods.
- `List(Stripe.PaymentMethodListOptions, Stripe.RequestOptions)`
  - Returns a list of all PaymentMethods..
- `ListAsync(Stripe.PaymentMethodListOptions, Stripe.RequestOptions, CancellationToken)`
  - Returns a list of all PaymentMethods..
- `ListAutoPaging(Stripe.PaymentMethodListOptions, Stripe.RequestOptions)`
  - Returns a list of all PaymentMethods..
- `ListAutoPagingAsync(Stripe.PaymentMethodListOptions, Stripe.RequestOptions, CancellationToken)`
  - Returns a list of all PaymentMethods..
- `Update(string, Stripe.PaymentMethodUpdateOptions, Stripe.RequestOptions)`
  - Updates a PaymentMethod object. A PaymentMethod must be attached to a customer to be
updated..
- `UpdateAsync(string, Stripe.PaymentMethodUpdateOptions, Stripe.RequestOptions, CancellationToken)`
  - Updates a PaymentMethod object. A PaymentMethod must be attached to a customer to be
updated..


#### `PaymentMethodCreateOptions`

**Properties:**

- `AcssDebit`
  - If this is an `acss_debit` PaymentMethod, this hash contains details about the ACSS
Debit payment method.
- `Affirm`
  - If this is an `affirm` PaymentMethod, this hash contains details about the Affirm
payment method.
- `AfterpayClearpay`
  - If this is an `AfterpayClearpay` PaymentMethod, this hash contains details about
the AfterpayClearpay payment method.
- `Alipay`
  - If this is an `Alipay` PaymentMethod, this hash contains details about the Alipay
payment method.
- `AllowRedisplay`
  - This field indicates whether this payment method can be shown again to its customer in a
checkout flow. Stripe products such as Checkout and Elements use this field to determine
whether a payment method can be shown as a saved payment method in a checkout flow. The
field defaults to `unspecified`.
One of: `always`, `limited`, or `unspecified`.
- `Alma`
  - If this is a Alma PaymentMethod, this hash contains details about the Alma payment
method.
- `AmazonPay`
  - If this is a AmazonPay PaymentMethod, this hash contains details about the AmazonPay
payment method.
- `AuBecsDebit`
  - If this is an `au_becs_debit` PaymentMethod, this hash contains details about the
bank account.
- `BacsDebit`
  - If this is a `bacs_debit` PaymentMethod, this hash contains details about the Bacs
Direct Debit bank account.
- `Bancontact`
  - If this is a `bancontact` PaymentMethod, this hash contains details about the
Bancontact payment method.
- `Billie`
  - If this is a `billie` PaymentMethod, this hash contains details about the Billie
payment method.
- `BillingDetails`
  - Billing information associated with the PaymentMethod that may be used or required by
particular types of payment methods.
- `Bizum`
  - If this is a `bizum` PaymentMethod, this hash contains details about the Bizum
payment method.
- `Blik`
  - If this is a `blik` PaymentMethod, this hash contains details about the BLIK
payment method.
- `Boleto`
  - If this is a `boleto` PaymentMethod, this hash contains details about the Boleto
payment method.
- `Card`
  - If this is a `card` PaymentMethod, this hash contains the user's card details. For
backwards compatibility, you can alternatively provide a Stripe token (e.g., for Apple
Pay, Amex Express Checkout, or legacy Checkout) into the card hash with format `card:
{token: "tok_visa"}`. When providing a card number, you must meet the requirements
for PCI
compliance. We strongly recommend using Stripe.js instead of interacting with this
API directly.
- `Cashapp`
  - If this is a `cashapp` PaymentMethod, this hash contains details about the Cash App
Pay payment method.
- `Crypto`
  - If this is a Crypto PaymentMethod, this hash contains details about the Crypto payment
method.
- `Custom`
  - If this is a `custom` PaymentMethod, this hash contains details about the Custom
payment method.
- `Customer`
  - The `Customer` to whom the original PaymentMethod is attached.
- `CustomerBalance`
  - If this is a `customer_balance` PaymentMethod, this hash contains details about the
CustomerBalance payment method.
- `Eps`
  - If this is an `eps` PaymentMethod, this hash contains details about the EPS payment
method.
- `Fpx`
  - If this is an `fpx` PaymentMethod, this hash contains details about the FPX payment
method.
- `Giropay`
  - If this is a `giropay` PaymentMethod, this hash contains details about the Giropay
payment method.
- `Grabpay`
  - If this is a `grabpay` PaymentMethod, this hash contains details about the GrabPay
payment method.
- `Ideal`
  - If this is an `ideal` PaymentMethod, this hash contains details about the iDEAL
payment method.
- `InteracPresent`
  - If this is an `interac_present` PaymentMethod, this hash contains details about the
Interac Present payment method.
- `KakaoPay`
  - If this is a `kakao_pay` PaymentMethod, this hash contains details about the Kakao
Pay payment method.
- `Klarna`
  - If this is a `klarna` PaymentMethod, this hash contains details about the Klarna
payment method.
- `Konbini`
  - If this is a `konbini` PaymentMethod, this hash contains details about the Konbini
payment method.
- `KrCard`
  - If this is a `kr_card` PaymentMethod, this hash contains details about the Korean
Card payment method.
- `Link`
  - If this is an `Link` PaymentMethod, this hash contains details about the Link
payment method (Link is also known as Onelink in the UK).
- `MbWay`
  - If this is a MB WAY PaymentMethod, this hash contains details about the MB WAY payment
method.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format. Individual keys can be unset by posting an empty value to
them. All keys can be unset by posting an empty value to `metadata`.
- `Mobilepay`
  - If this is a `mobilepay` PaymentMethod, this hash contains details about the
MobilePay payment method.
- `Multibanco`
  - If this is a `multibanco` PaymentMethod, this hash contains details about the
Multibanco payment method.
- `NaverPay`
  - If this is a `naver_pay` PaymentMethod, this hash contains details about the Naver
Pay payment method.
- `NzBankAccount`
  - If this is an nz_bank_account PaymentMethod, this hash contains details about the
nz_bank_account payment method.
- `Oxxo`
  - If this is an `oxxo` PaymentMethod, this hash contains details about the OXXO
payment method.
- `P24`
  - If this is a `p24` PaymentMethod, this hash contains details about the P24 payment
method.
- `PayByBank`
  - If this is a `pay_by_bank` PaymentMethod, this hash contains details about the
PayByBank payment method.
- `Payco`
  - If this is a `payco` PaymentMethod, this hash contains details about the PAYCO
payment method.
- `PaymentMethod`
  - The PaymentMethod to share.
- `Paynow`
  - If this is a `paynow` PaymentMethod, this hash contains details about the PayNow
payment method.
- `Paypal`
  - If this is a `paypal` PaymentMethod, this hash contains details about the PayPal
payment method.
- `Payto`
  - If this is a `payto` PaymentMethod, this hash contains details about the PayTo
payment method.
- `Pix`
  - If this is a `pix` PaymentMethod, this hash contains details about the Pix payment
method.
- `Promptpay`
  - If this is a `promptpay` PaymentMethod, this hash contains details about the
PromptPay payment method.
- `RadarOptions`
  - Options to configure Radar. See Radar Session for more
information.
- `RevolutPay`
  - If this is a `revolut_pay` PaymentMethod, this hash contains details about the
Revolut Pay payment method.
- `SamsungPay`
  - If this is a `samsung_pay` PaymentMethod, this hash contains details about the
SamsungPay payment method.
- `Satispay`
  - If this is a `satispay` PaymentMethod, this hash contains details about the
Satispay payment method.
- `Scalapay`
  - If this is a Scalapay PaymentMethod, this hash contains details about the Scalapay
payment method.
- `SepaDebit`
  - If this is a `sepa_debit` PaymentMethod, this hash contains details about the SEPA
debit bank account.
- `Sofort`
  - If this is a `sofort` PaymentMethod, this hash contains details about the SOFORT
payment method.
- `Sunbit`
  - If this is a Sunbit PaymentMethod, this hash contains details about the Sunbit payment
method.
- `Swish`
  - If this is a `swish` PaymentMethod, this hash contains details about the Swish
payment method.
- `Twint`
  - If this is a TWINT PaymentMethod, this hash contains details about the TWINT payment
method.
- `Type`
  - The type of the PaymentMethod. An additional hash is included on the PaymentMethod with
a name matching this value. It contains additional information specific to the
PaymentMethod type.
One of: `acss_debit`, `affirm`, `afterpay_clearpay`, `alipay`,
`alma`, `amazon_pay`, `au_becs_debit`, `bacs_debit`,
`bancontact`, `billie`, `bizum`, `blik`, `boleto`, `card`,
`cashapp`, `crypto`, `custom`, `customer_balance`, `eps`,
`fpx`, `giropay`, `grabpay`, `ideal`, `kakao_pay`,
`klarna`, `konbini`, `kr_card`, `link`, `mb_way`,
`mobilepay`, `multibanco`, `naver_pay`, `nz_bank_account`,
`oxxo`, `p24`, `pay_by_bank`, `payco`, `paynow`, `paypal`,
`payto`, `pix`, `promptpay`, `revolut_pay`, `samsung_pay`,
`satispay`, `scalapay`, `sepa_debit`, `sofort`, `sunbit`,
`swish`, `twint`, `upi`, `us_bank_account`, `wechat_pay`, or
`zip`.
- `Upi`
  - If this is a `upi` PaymentMethod, this hash contains details about the UPI payment
method.
- `UsBankAccount`
  - If this is an `us_bank_account` PaymentMethod, this hash contains details about the
US bank account payment method.
- `WechatPay`
  - If this is an `wechat_pay` PaymentMethod, this hash contains details about the
wechat_pay payment method.
- `Zip`
  - If this is a `zip` PaymentMethod, this hash contains details about the Zip payment
method.


#### `PaymentMethodUpdateOptions`

**Properties:**

- `AllowRedisplay`
  - This field indicates whether this payment method can be shown again to its customer in a
checkout flow. Stripe products such as Checkout and Elements use this field to determine
whether a payment method can be shown as a saved payment method in a checkout flow. The
field defaults to `unspecified`.
One of: `always`, `limited`, or `unspecified`.
- `BillingDetails`
  - Billing information associated with the PaymentMethod that may be used or required by
particular types of payment methods.
- `Card`
  - If this is a `card` PaymentMethod, this hash contains the user's card details.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format. Individual keys can be unset by posting an empty value to
them. All keys can be unset by posting an empty value to `metadata`.
- `Payto`
  - If this is a `payto` PaymentMethod, this hash contains details about the PayTo
payment method.
- `UsBankAccount`
  - If this is an `us_bank_account` PaymentMethod, this hash contains details about the
US bank account payment method.


#### `PaymentMethodListOptions`

**Properties:**

- `AllowRedisplay`
  - This field indicates whether this payment method can be shown again to its customer in a
checkout flow. Stripe products such as Checkout and Elements use this field to determine
whether a payment method can be shown as a saved payment method in a checkout flow.
One of: `always`, `limited`, or `unspecified`.
- `Customer`
  - The ID of the customer whose PaymentMethods will be retrieved.
- `CustomerAccount`
  - The ID of the Account whose PaymentMethods will be retrieved.
- `Type`
  - Filters the list by the object `type` field. Unfiltered, the list returns all
payment method types except `custom`. If your integration expects only one type of
payment method in the response, specify that type value in the request to reduce your
payload.
One of: `acss_debit`, `affirm`, `afterpay_clearpay`, `alipay`,
`alma`, `amazon_pay`, `au_becs_debit`, `bacs_debit`,
`bancontact`, `billie`, `bizum`, `blik`, `boleto`, `card`,
`cashapp`, `crypto`, `custom`, `customer_balance`, `eps`,
`fpx`, `giropay`, `grabpay`, `ideal`, `kakao_pay`,
`klarna`, `konbini`, `kr_card`, `link`, `mb_way`,
`mobilepay`, `multibanco`, `naver_pay`, `nz_bank_account`,
`oxxo`, `p24`, `pay_by_bank`, `payco`, `paynow`, `paypal`,
`payto`, `pix`, `promptpay`, `revolut_pay`, `samsung_pay`,
`satispay`, `scalapay`, `sepa_debit`, `sofort`, `sunbit`,
`swish`, `twint`, `upi`, `us_bank_account`, `wechat_pay`, or
`zip`.


### Customer

#### `Customer`

This object represents a customer of your business. Use it to create recurring charges, save payment and contact
information, and track payments that belong to the same customer.

**Properties:**

- `Address`
  - The customer's address.
- `Balance`
  - The current balance, if any, that's stored on the customer in their default currency. If
negative, the customer has credit to apply to their next invoice. If positive, the
customer has an amount owed that's added to their next invoice. The balance only
considers amounts that Stripe hasn't successfully applied to any invoice. It doesn't
reflect unpaid invoices. This balance is only taken into account after invoices
finalize. For multi-currency balances, see invoice_credit_balance.
- `BusinessName`
  - The customer's business name.
- `CashBalance`
  - The current funds being held by Stripe on behalf of the customer. You can apply these
funds towards payment intents when the source is "cash_balance". The
`settings[reconciliation_mode]` field describes if these funds apply to these
payment intents manually or automatically.
- `Created`
  - Time at which the object was created. Measured in seconds since the Unix epoch.
- `Currency`
  - Three-letter ISO code for the currency
the customer can be charged in for recurring billing purposes.
- `CustomerAccount`
  - The ID of an Account representing a customer. You can use this ID with any v1 API that
accepts a customer_account parameter.
- `DefaultSource`
  - (Expanded)
ID of the default payment source for the customer.

If you use payment methods created through the PaymentMethods API, see the invoice_settings.default_payment_method
field instead.

For more information, see the expand documentation.
- `DefaultSourceId`
  - (ID of the IPaymentSource)
ID of the default payment source for the customer.

If you use payment methods created through the PaymentMethods API, see the invoice_settings.default_payment_method
field instead.
- `Deleted`
  - Whether this object is deleted or not.
- `Delinquent`
  - Tracks the most recent state change on any invoice belonging to the customer. Paying an
invoice or marking it uncollectible via the API will set this field to false. An
automatic payment failure or passing the `invoice.due_date` will set this field to
`true`.

If an invoice becomes uncollectible by dunning,
`delinquent` doesn't reset to `false`.

If you care whether the customer has paid their most recent subscription invoice, use
`subscription.status` instead. Paying or marking uncollectible any customer invoice
regardless of whether it is the latest invoice for a subscription will always set this
field to `false`.
- `Description`
  - An arbitrary string attached to the object. Often useful for displaying to users.
- `Discount`
  - Describes the current discount active on the customer, if there is one.
- `Email`
  - The customer's email address.
- `Id`
  - Unique identifier for the object.
- `IndividualName`
  - The customer's individual name.
- `InvoiceCreditBalance`
  - The current multi-currency balances, if any, that's stored on the customer. If positive
in a currency, the customer has a credit to apply to their next invoice denominated in
that currency. If negative, the customer has an amount owed that's added to their next
invoice denominated in that currency. These balances don't apply to unpaid invoices.
They solely track amounts that Stripe hasn't successfully applied to any invoice. Stripe
only applies a balance in a specific currency to an invoice after that invoice (which is
in the same currency) finalizes.
- `InvoicePrefix`
  - The prefix for the customer used to generate unique invoice numbers.
- `Livemode`
  - If the object exists in live mode, the value is `true`. If the object exists in
test mode, the value is `false`.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format.
- `Name`
  - The customer's full name or business name.
- `NextInvoiceSequence`
  - The suffix of the customer's next invoice number (for example, 0001). When the account
uses account level sequencing, this parameter is ignored in API requests and the field
omitted in API responses.
- `Object`
  - String representing the object's type. Objects of the same type share the same value.
- `Phone`
  - The customer's phone number.
- `PreferredLocales`
  - The customer's preferred locales (languages), ordered by preference.
- `Shipping`
  - Mailing and shipping address for the customer. Appears on invoices emailed to this
customer.
- `Sources`
  - The customer's payment sources, if any.
- `Subscriptions`
  - The customer's current subscriptions, if any.
- `TaxExempt`
  - Describes the customer's tax exemption status, which is `none`, `exempt`, or
`reverse`. When set to `reverse`, invoice and receipt PDFs include the
following text: "Reverse charge".
One of: `exempt`, `none`, or `reverse`.
- `TaxIds`
  - The customer's tax IDs.
- `TestClock`
  - (Expanded)
ID of the test clock that this customer belongs to.

For more information, see the expand documentation.
- `TestClockId`
  - (ID of the TestHelpers.TestClock)
ID of the test clock that this customer belongs to.


#### `CustomerService`

**Methods:**

- `FundCashBalance(string, Stripe.TestHelpers.CustomerFundCashBalanceOptions, Stripe.RequestOptions)`
  - Create an incoming testmode bank transfer.
- `FundCashBalanceAsync(string, Stripe.TestHelpers.CustomerFundCashBalanceOptions, Stripe.RequestOptions, CancellationToken)`
  - Create an incoming testmode bank transfer.


#### `CustomerService`

**Methods:**

- `Create(Stripe.CustomerCreateOptions, Stripe.RequestOptions)`
  - Creates a new customer object..
- `CreateAsync(Stripe.CustomerCreateOptions, Stripe.RequestOptions, CancellationToken)`
  - Creates a new customer object..
- `CreateFundingInstructions(string, Stripe.CustomerFundingInstructionsCreateOptions, Stripe.RequestOptions)`
  - Retrieve funding instructions for a customer cash balance. If funding instructions do
not yet exist for the customer, new funding instructions will be created. If funding
instructions have already been created for a given customer, the same funding
instructions will be retrieved. In other words, we will return the same funding
instructions each time..
- `CreateFundingInstructionsAsync(string, Stripe.CustomerFundingInstructionsCreateOptions, Stripe.RequestOptions, CancellationToken)`
  - Retrieve funding instructions for a customer cash balance. If funding instructions do
not yet exist for the customer, new funding instructions will be created. If funding
instructions have already been created for a given customer, the same funding
instructions will be retrieved. In other words, we will return the same funding
instructions each time..
- `Delete(string, Stripe.CustomerDeleteOptions, Stripe.RequestOptions)`
  - Permanently deletes a customer. It cannot be undone. Also immediately cancels any
active subscriptions on the customer..
- `DeleteAsync(string, Stripe.CustomerDeleteOptions, Stripe.RequestOptions, CancellationToken)`
  - Permanently deletes a customer. It cannot be undone. Also immediately cancels any
active subscriptions on the customer..
- `DeleteDiscount(string, Stripe.CustomerDeleteDiscountOptions, Stripe.RequestOptions)`
  - Removes the currently applied discount on a customer..
- `DeleteDiscountAsync(string, Stripe.CustomerDeleteDiscountOptions, Stripe.RequestOptions, CancellationToken)`
  - Removes the currently applied discount on a customer..
- `Get(string, Stripe.CustomerGetOptions, Stripe.RequestOptions)`
  - Retrieves a Customer object..
- `GetAsync(string, Stripe.CustomerGetOptions, Stripe.RequestOptions, CancellationToken)`
  - Retrieves a Customer object..
- `List(Stripe.CustomerListOptions, Stripe.RequestOptions)`
  - Returns a list of your customers. The customers are returned sorted by creation date,
with the most recent customers appearing first..
- `ListAsync(Stripe.CustomerListOptions, Stripe.RequestOptions, CancellationToken)`
  - Returns a list of your customers. The customers are returned sorted by creation date,
with the most recent customers appearing first..
- `ListAutoPaging(Stripe.CustomerListOptions, Stripe.RequestOptions)`
  - Returns a list of your customers. The customers are returned sorted by creation date,
with the most recent customers appearing first..
- `ListAutoPagingAsync(Stripe.CustomerListOptions, Stripe.RequestOptions, CancellationToken)`
  - Returns a list of your customers. The customers are returned sorted by creation date,
with the most recent customers appearing first..
- `ListPaymentMethods(string, Stripe.CustomerPaymentMethodListOptions, Stripe.RequestOptions)`
  - Returns a list of PaymentMethods for a given Customer.
- `ListPaymentMethodsAsync(string, Stripe.CustomerPaymentMethodListOptions, Stripe.RequestOptions, CancellationToken)`
  - Returns a list of PaymentMethods for a given Customer.
- `ListPaymentMethodsAutoPaging(string, Stripe.CustomerPaymentMethodListOptions, Stripe.RequestOptions)`
  - Returns a list of PaymentMethods for a given Customer.
- `ListPaymentMethodsAutoPagingAsync(string, Stripe.CustomerPaymentMethodListOptions, Stripe.RequestOptions, CancellationToken)`
  - Returns a list of PaymentMethods for a given Customer.
- `RetrievePaymentMethod(string, string, Stripe.CustomerPaymentMethodGetOptions, Stripe.RequestOptions)`
  - Retrieves a PaymentMethod object for a given Customer..
- `RetrievePaymentMethodAsync(string, string, Stripe.CustomerPaymentMethodGetOptions, Stripe.RequestOptions, CancellationToken)`
  - Retrieves a PaymentMethod object for a given Customer..
- `Search(Stripe.CustomerSearchOptions, Stripe.RequestOptions)`
  - Search for customers you’ve previously created using Stripe’s Search Query Language.
Don’t use search in read-after-write flows where strict consistency is necessary. Under
normal operating conditions, data is searchable in less than a minute. Occasionally,
propagation of new or updated data can be up to an hour behind during outages. Search
functionality is not available to merchants in India..
- `SearchAsync(Stripe.CustomerSearchOptions, Stripe.RequestOptions, CancellationToken)`
  - Search for customers you’ve previously created using Stripe’s Search Query Language.
Don’t use search in read-after-write flows where strict consistency is necessary. Under
normal operating conditions, data is searchable in less than a minute. Occasionally,
propagation of new or updated data can be up to an hour behind during outages. Search
functionality is not available to merchants in India..
- `SearchAutoPaging(Stripe.CustomerSearchOptions, Stripe.RequestOptions)`
  - Search for customers you’ve previously created using Stripe’s Search Query Language.
Don’t use search in read-after-write flows where strict consistency is necessary. Under
normal operating conditions, data is searchable in less than a minute. Occasionally,
propagation of new or updated data can be up to an hour behind during outages. Search
functionality is not available to merchants in India..
- `SearchAutoPagingAsync(Stripe.CustomerSearchOptions, Stripe.RequestOptions, CancellationToken)`
  - Search for customers you’ve previously created using Stripe’s Search Query Language.
Don’t use search in read-after-write flows where strict consistency is necessary. Under
normal operating conditions, data is searchable in less than a minute. Occasionally,
propagation of new or updated data can be up to an hour behind during outages. Search
functionality is not available to merchants in India..
- `Update(string, Stripe.CustomerUpdateOptions, Stripe.RequestOptions)`
  - Updates the specified customer by setting the values of the parameters passed. Any
parameters not provided are left unchanged. For example, if you pass the
source parameter, that becomes the customer’s active source (such as a
card) to be used for all charges in the future. When you update a customer to a new
valid card source by passing the source parameter: for each of the
customer’s current subscriptions, if the subscription bills automatically and is in the
`past_due` state, then the latest open invoice for the subscription with automatic
collection enabled is retried. This retry doesn’t count as an automatic retry, and
doesn’t affect the next regularly scheduled payment for the invoice. Changing the
default_source for a customer doesn’t trigger this behavior..

This request accepts mostly the same arguments as the customer creation call..
- `UpdateAsync(string, Stripe.CustomerUpdateOptions, Stripe.RequestOptions, CancellationToken)`
  - Updates the specified customer by setting the values of the parameters passed. Any
parameters not provided are left unchanged. For example, if you pass the
source parameter, that becomes the customer’s active source (such as a
card) to be used for all charges in the future. When you update a customer to a new
valid card source by passing the source parameter: for each of the
customer’s current subscriptions, if the subscription bills automatically and is in the
`past_due` state, then the latest open invoice for the subscription with automatic
collection enabled is retried. This retry doesn’t count as an automatic retry, and
doesn’t affect the next regularly scheduled payment for the invoice. Changing the
default_source for a customer doesn’t trigger this behavior..

This request accepts mostly the same arguments as the customer creation call..


#### `CustomerCreateOptions`

**Properties:**

- `Address`
  - The customer's address. Learn about country-specific
requirements for calculating tax.
- `Balance`
  - An integer amount in cents (or local equivalent) that represents the customer's current
balance, which affect the customer's future invoices. A negative amount represents a
credit that decreases the amount due on an invoice; a positive amount increases the
amount due on an invoice.
- `BusinessName`
  - The customer's business name. This may be up to 150 characters.
- `CashBalance`
  - Balance information and default balance settings for this customer.
- `Description`
  - An arbitrary string that you can attach to a customer object. It is displayed alongside
the customer in the dashboard.
- `Email`
  - Customer's email address. It's displayed alongside the customer in your dashboard and
can be useful for searching and tracking. This may be up to 512 characters.
- `IndividualName`
  - The customer's full name. This may be up to 150 characters.
- `InvoicePrefix`
  - The prefix for the customer used to generate unique invoice numbers. Must be 3–12
uppercase letters or numbers.
- `InvoiceSettings`
  - Default invoice settings for this customer.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format. Individual keys can be unset by posting an empty value to
them. All keys can be unset by posting an empty value to `metadata`.
- `Name`
  - The customer's full name or business name.
- `NextInvoiceSequence`
  - The sequence to be used on the customer's next invoice. Defaults to 1.
- `Phone`
  - The customer's phone number.
- `PreferredLocales`
  - Customer's preferred languages, ordered by preference.
- `Shipping`
  - The customer's shipping information. Appears on invoices emailed to this customer.
- `Tax`
  - Tax details about the customer.
- `TaxExempt`
  - The customer's tax exemption. One of `none`, `exempt`, or `reverse`.
One of: `exempt`, `none`, or `reverse`.
- `TaxIdData`
  - The customer's tax IDs.
- `TestClock`
  - ID of the test clock to attach to the customer.


#### `CustomerUpdateOptions`

**Properties:**

- `Address`
  - The customer's address. Learn about country-specific
requirements for calculating tax.
- `Balance`
  - An integer amount in cents (or local equivalent) that represents the customer's current
balance, which affect the customer's future invoices. A negative amount represents a
credit that decreases the amount due on an invoice; a positive amount increases the
amount due on an invoice.
- `BusinessName`
  - The customer's business name. This may be up to 150 characters.
- `CashBalance`
  - Balance information and default balance settings for this customer.
- `DefaultSource`
  - If you are using payment methods created via the PaymentMethods API, see the invoice_settings.default_payment_method
parameter.

Provide the ID of a payment source already attached to this customer to make it this
customer's default payment source.

If you want to add a new payment source and make it the default, see the source
property.
- `Description`
  - An arbitrary string that you can attach to a customer object. It is displayed alongside
the customer in the dashboard.
- `Email`
  - Customer's email address. It's displayed alongside the customer in your dashboard and
can be useful for searching and tracking. This may be up to 512 characters.
- `IndividualName`
  - The customer's full name. This may be up to 150 characters.
- `InvoicePrefix`
  - The prefix for the customer used to generate unique invoice numbers. Must be 3–12
uppercase letters or numbers.
- `InvoiceSettings`
  - Default invoice settings for this customer.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format. Individual keys can be unset by posting an empty value to
them. All keys can be unset by posting an empty value to `metadata`.
- `Name`
  - The customer's full name or business name.
- `NextInvoiceSequence`
  - The sequence to be used on the customer's next invoice. Defaults to 1.
- `Phone`
  - The customer's phone number.
- `PreferredLocales`
  - Customer's preferred languages, ordered by preference.
- `Shipping`
  - The customer's shipping information. Appears on invoices emailed to this customer.
- `Tax`
  - Tax details about the customer.
- `TaxExempt`
  - The customer's tax exemption. One of `none`, `exempt`, or `reverse`.
One of: `exempt`, `none`, or `reverse`.


#### `CustomerListOptions`

**Properties:**

- `Created`
  - Only return customers that were created during the given date interval.
- `Email`
  - A case-sensitive filter on the list based on the customer's `email` field. The
value must be a string.
- `TestClock`
  - Provides a list of customers that are associated with the specified test clock. The
response will not include customers with test clocks if this parameter is not set.


### CustomerBalanceTransaction

#### `CustomerBalanceTransaction`

Each customer has a Balance
value, which denotes a debit or credit that's automatically applied to their next
invoice upon finalization. You may modify the value directly by using the update customer API, or by
creating a Customer Balance Transaction, which increments or decrements the customer's
`balance` by the specified `amount`.

Related guide: Customer
balance.

**Properties:**

- `Amount`
  - The amount of the transaction. A negative value is a credit for the customer's balance,
and a positive value is a debit to the customer's `balance`.
- `CheckoutSession`
  - (Expanded)
The ID of the checkout session (if any) that created the transaction.

For more information, see the expand documentation.
- `CheckoutSessionId`
  - (ID of the Checkout.Session)
The ID of the checkout session (if any) that created the transaction.
- `Created`
  - Time at which the object was created. Measured in seconds since the Unix epoch.
- `CreditNote`
  - (Expanded)
The ID of the credit note (if any) related to the transaction.

For more information, see the expand documentation.
- `CreditNoteId`
  - (ID of the CreditNote)
The ID of the credit note (if any) related to the transaction.
- `Currency`
  - Three-letter ISO currency
code, in lowercase. Must be a supported
currency.
- `Customer`
  - (Expanded)
The ID of the customer the transaction belongs to.

For more information, see the expand documentation.
- `CustomerAccount`
  - The ID of an Account representing a customer that the transaction belongs to.
- `CustomerId`
  - (ID of the Customer)
The ID of the customer the transaction belongs to.
- `Description`
  - An arbitrary string attached to the object. Often useful for displaying to users.
- `EndingBalance`
  - The customer's `balance` after the transaction was applied. A negative value
decreases the amount due on the customer's next invoice. A positive value increases the
amount due on the customer's next invoice.
- `Id`
  - Unique identifier for the object.
- `Invoice`
  - (Expanded)
The ID of the invoice (if any) related to the transaction.

For more information, see the expand documentation.
- `InvoiceId`
  - (ID of the Invoice)
The ID of the invoice (if any) related to the transaction.
- `Livemode`
  - If the object exists in live mode, the value is `true`. If the object exists in
test mode, the value is `false`.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format.
- `Object`
  - String representing the object's type. Objects of the same type share the same value.
- `Type`
  - Transaction type: `adjustment`, `applied_to_invoice`, `credit_note`,
`initial`, `invoice_overpaid`, `invoice_too_large`,
`invoice_too_small`, `unspent_receiver_credit`, `unapplied_from_invoice`,
`checkout_session_subscription_payment`, or
`checkout_session_subscription_payment_canceled`. See the Customer Balance page
to learn more about transaction types.
One of: `adjustment`, `applied_to_invoice`,
`checkout_session_subscription_payment`,
`checkout_session_subscription_payment_canceled`, `credit_note`,
`initial`, `invoice_overpaid`, `invoice_too_large`,
`invoice_too_small`, `migration`, `unapplied_from_invoice`, or
`unspent_receiver_credit`.


#### `CustomerBalanceTransactionService`

**Methods:**

- `Create(string, Stripe.CustomerBalanceTransactionCreateOptions, Stripe.RequestOptions)`
  - Creates an immutable transaction that updates the customer’s credit balance..
- `CreateAsync(string, Stripe.CustomerBalanceTransactionCreateOptions, Stripe.RequestOptions, CancellationToken)`
  - Creates an immutable transaction that updates the customer’s credit balance..
- `Get(string, string, Stripe.CustomerBalanceTransactionGetOptions, Stripe.RequestOptions)`
  - Retrieves a specific customer balance transaction that updated the customer’s balances..
- `GetAsync(string, string, Stripe.CustomerBalanceTransactionGetOptions, Stripe.RequestOptions, CancellationToken)`
  - Retrieves a specific customer balance transaction that updated the customer’s balances..
- `List(string, Stripe.CustomerBalanceTransactionListOptions, Stripe.RequestOptions)`
  - Returns a list of transactions that updated the customer’s balances..
- `ListAsync(string, Stripe.CustomerBalanceTransactionListOptions, Stripe.RequestOptions, CancellationToken)`
  - Returns a list of transactions that updated the customer’s balances..
- `ListAutoPaging(string, Stripe.CustomerBalanceTransactionListOptions, Stripe.RequestOptions)`
  - Returns a list of transactions that updated the customer’s balances..
- `ListAutoPagingAsync(string, Stripe.CustomerBalanceTransactionListOptions, Stripe.RequestOptions, CancellationToken)`
  - Returns a list of transactions that updated the customer’s balances..
- `Update(string, string, Stripe.CustomerBalanceTransactionUpdateOptions, Stripe.RequestOptions)`
  - Most credit balance transaction fields are immutable, but you may update its
`description` and `metadata`..
- `UpdateAsync(string, string, Stripe.CustomerBalanceTransactionUpdateOptions, Stripe.RequestOptions, CancellationToken)`
  - Most credit balance transaction fields are immutable, but you may update its
`description` and `metadata`..


#### `CustomerBalanceTransactionCreateOptions`

**Properties:**

- `Amount`
  - The integer amount in cents (or local equivalent) to apply to the
customer's credit balance.
- `Currency`
  - Three-letter ISO currency
code, in lowercase. Must be a supported
currency. Specifies the `invoice_credit_balance`
that this transaction will apply to. If the customer's `currency` is not set, it
will be updated to this value.
- `Description`
  - An arbitrary string attached to the object. Often useful for displaying to users.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format. Individual keys can be unset by posting an empty value to
them. All keys can be unset by posting an empty value to `metadata`.


#### `CustomerBalanceTransactionUpdateOptions`

**Properties:**

- `Description`
  - An arbitrary string attached to the object. Often useful for displaying to users.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format. Individual keys can be unset by posting an empty value to
them. All keys can be unset by posting an empty value to `metadata`.


#### `CustomerBalanceTransactionListOptions`

**Properties:**

- `Created`
  - Only return customer balance transactions that were created during the given date
interval.
- `Invoice`
  - Only return transactions that are related to the specified invoice.


### Charge

#### `Charge`

The `Charge` object represents a single attempt to move money into your Stripe
account. PaymentIntent confirmation is the most common way to create Charges, but Account Debits may also create
Charges. Some legacy payment flows create Charges directly, which is not recommended for
new integrations.

**Properties:**

- `Amount`
  - Amount intended to be collected by this payment. A positive integer representing how
much to charge in the smallest
currency unit (e.g., 100 cents to charge $1.00 or 100 to charge ¥100, a zero-decimal
currency). The minimum amount is $0.50 US or equivalent
in charge currency. The amount value supports up to eight digits (e.g., a value of
99999999 for a USD charge of $999,999.99).
- `AmountCaptured`
  - Amount in cents (or local equivalent) captured (can be less than the amount attribute on
the charge if a partial capture was made).
- `AmountRefunded`
  - Amount in cents (or local equivalent) refunded (can be less than the amount attribute on
the charge if a partial refund was issued).
- `Application`
  - (Expanded)
ID of the Connect application that created the charge.

For more information, see the expand documentation.
- `ApplicationFee`
  - (Expanded)
The application fee (if any) for the charge. See the Connect
documentation for details.

For more information, see the expand documentation.
- `ApplicationFeeAmount`
  - The amount of the application fee (if any) requested for the charge. See the Connect
documentation for details.
- `ApplicationFeeId`
  - (ID of the ApplicationFee)
The application fee (if any) for the charge. See the Connect
documentation for details.
- `ApplicationId`
  - (ID of the Application)
ID of the Connect application that created the charge.
- `AuthorizationCode`
  - Authorization code on the charge.
- `BalanceTransaction`
  - (Expanded)
ID of the balance transaction that describes the impact of this charge on your account
balance (not including refunds or disputes).

For more information, see the expand documentation.
- `BalanceTransactionId`
  - (ID of the BalanceTransaction)
ID of the balance transaction that describes the impact of this charge on your account
balance (not including refunds or disputes).
- `CalculatedStatementDescriptor`
  - The full statement descriptor that is passed to card networks, and that is displayed on
your customers' credit card and bank statements. Allows you to see what the statement
descriptor looks like after the static and dynamic portions are combined. This value
only exists for card payments.
- `Captured`
  - If the charge was created without capturing, this Boolean represents whether it is still
uncaptured or has since been captured.
- `Created`
  - Time at which the object was created. Measured in seconds since the Unix epoch.
- `Currency`
  - Three-letter ISO currency
code, in lowercase. Must be a supported
currency.
- `Customer`
  - (Expanded)
ID of the customer this charge is for if one exists.

For more information, see the expand documentation.
- `CustomerId`
  - (ID of the Customer)
ID of the customer this charge is for if one exists.
- `Description`
  - An arbitrary string attached to the object. Often useful for displaying to users.
- `Disputed`
  - Whether the charge has been disputed.
- `FailureBalanceTransaction`
  - (Expanded)
ID of the balance transaction that describes the reversal of the balance on your account
due to payment failure.

For more information, see the expand documentation.
- `FailureBalanceTransactionId`
  - (ID of the BalanceTransaction)
ID of the balance transaction that describes the reversal of the balance on your account
due to payment failure.
- `FailureCode`
  - Error code explaining reason for charge failure if available (see the errors section for a list of codes).
- `FailureMessage`
  - Message to user further explaining reason for charge failure if available.
- `FraudDetails`
  - Information on fraud assessments for the charge.
- `Id`
  - Unique identifier for the object.
- `Livemode`
  - If the object exists in live mode, the value is `true`. If the object exists in
test mode, the value is `false`.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format.
- `Object`
  - String representing the object's type. Objects of the same type share the same value.
- `OnBehalfOf`
  - (Expanded)
The account (if any) the charge was made on behalf of without triggering an automatic
transfer. See the Connect
documentation for details.

For more information, see the expand documentation.
- `OnBehalfOfId`
  - (ID of the Account)
The account (if any) the charge was made on behalf of without triggering an automatic
transfer. See the Connect
documentation for details.
- `Outcome`
  - Details about whether the payment was accepted, and why. See understanding declines for details.
- `Paid`
  - `true` if the charge succeeded, or was successfully authorized for later capture.
- `PaymentIntent`
  - (Expanded)
ID of the PaymentIntent associated with this charge, if one exists.

For more information, see the expand documentation.
- `PaymentIntentId`
  - (ID of the PaymentIntent)
ID of the PaymentIntent associated with this charge, if one exists.
- `PaymentMethod`
  - ID of the payment method used in this charge.
- `PaymentMethodDetails`
  - Details about the payment method at the time of the transaction.
- `RadarOptions`
  - Options to configure Radar. See Radar Session for more
information.
- `ReceiptEmail`
  - This is the email address that the receipt for this charge was sent to.
- `ReceiptNumber`
  - This is the transaction number that appears on email receipts sent for this charge. This
attribute will be `null` until a receipt has been sent.
- `ReceiptUrl`
  - This is the URL to view the receipt for this charge. The receipt is kept up-to-date to
the latest state of the charge, including any refunds. If the charge is for an Invoice,
the receipt will be stylized as an Invoice receipt.
- `Refunded`
  - Whether the charge has been fully refunded. If the charge is only partially refunded,
this attribute will still be false.
- `Refunds`
  - A list of refunds that have been applied to the charge.
- `Review`
  - (Expanded)
ID of the review associated with this charge if one exists.

For more information, see the expand documentation.
- `ReviewId`
  - (ID of the Review)
ID of the review associated with this charge if one exists.
- `Shipping`
  - Shipping information for the charge.
- `Source`
  - This is a legacy field that will be removed in the future. It contains the Source, Card,
or BankAccount object used for the charge. For details about the payment method used for
this charge, refer to `payment_method` or `payment_method_details` instead.
- `SourceTransfer`
  - (Expanded)
The transfer ID which created this charge. Only present if the charge came from another
Stripe account. See the
Connect documentation for details.

For more information, see the expand documentation.
- `SourceTransferId`
  - (ID of the Transfer)
The transfer ID which created this charge. Only present if the charge came from another
Stripe account. See the
Connect documentation for details.
- `StatementDescriptor`
  - For a non-card charge, text that appears on the customer's statement as the statement
descriptor. This value overrides the account's default statement descriptor. For
information about requirements, including the 22-character limit, see the Statement
Descriptor docs.

For a card charge, this value is ignored unless you don't specify a
`statement_descriptor_suffix`, in which case this value is used as the suffix.
- `StatementDescriptorSuffix`
  - Provides information about a card charge. Concatenated to the account's statement
descriptor prefix to form the complete statement descriptor that appears on the
customer's statement. If the account has no prefix value, the suffix is concatenated to
the account's statement descriptor.
- `Status`
  - The status of the payment is either `succeeded`, `pending`, or `failed`.
One of: `failed`, `pending`, or `succeeded`.
- `Transfer`
  - (Expanded)
ID of the transfer to the `destination` account (only applicable if the charge was
created using the `destination` parameter).

For more information, see the expand documentation.
- `TransferData`
  - An optional dictionary including the account to automatically transfer to as part of a
destination charge. See
the Connect documentation for details.
- `TransferGroup`
  - A string that identifies this transaction as part of a group. See the Connect
documentation for details.
- `TransferId`
  - (ID of the Transfer)
ID of the transfer to the `destination` account (only applicable if the charge was
created using the `destination` parameter).


#### `ChargeService`

**Methods:**

- `Capture(string, Stripe.ChargeCaptureOptions, Stripe.RequestOptions)`
  - Capture the payment of an existing, uncaptured charge that was created with the
`capture` option set to false..

Uncaptured payments expire a set number of days after they are created (7 by default), after which
they are marked as refunded and capture attempts will fail..

Don’t use this method to capture a PaymentIntent-initiated charge. Use Capture a
PaymentIntent..
- `CaptureAsync(string, Stripe.ChargeCaptureOptions, Stripe.RequestOptions, CancellationToken)`
  - Capture the payment of an existing, uncaptured charge that was created with the
`capture` option set to false..

Uncaptured payments expire a set number of days after they are created (7 by default), after which
they are marked as refunded and capture attempts will fail..

Don’t use this method to capture a PaymentIntent-initiated charge. Use Capture a
PaymentIntent..
- `Create(Stripe.ChargeCreateOptions, Stripe.RequestOptions)`
  - This method is no longer recommended—use the Payment Intents API to initiate a
new payment instead. Confirmation of the PaymentIntent creates the `Charge` object
used to request payment..
- `CreateAsync(Stripe.ChargeCreateOptions, Stripe.RequestOptions, CancellationToken)`
  - This method is no longer recommended—use the Payment Intents API to initiate a
new payment instead. Confirmation of the PaymentIntent creates the `Charge` object
used to request payment..
- `Get(string, Stripe.ChargeGetOptions, Stripe.RequestOptions)`
  - Retrieves the details of a charge that has previously been created. Supply the unique
charge ID that was returned from your previous request, and Stripe will return the
corresponding charge information. The same information is returned when creating or
refunding the charge..
- `GetAsync(string, Stripe.ChargeGetOptions, Stripe.RequestOptions, CancellationToken)`
  - Retrieves the details of a charge that has previously been created. Supply the unique
charge ID that was returned from your previous request, and Stripe will return the
corresponding charge information. The same information is returned when creating or
refunding the charge..
- `List(Stripe.ChargeListOptions, Stripe.RequestOptions)`
  - Returns a list of charges you’ve previously created. The charges are returned in
sorted order, with the most recent charges appearing first..
- `ListAsync(Stripe.ChargeListOptions, Stripe.RequestOptions, CancellationToken)`
  - Returns a list of charges you’ve previously created. The charges are returned in
sorted order, with the most recent charges appearing first..
- `ListAutoPaging(Stripe.ChargeListOptions, Stripe.RequestOptions)`
  - Returns a list of charges you’ve previously created. The charges are returned in
sorted order, with the most recent charges appearing first..
- `ListAutoPagingAsync(Stripe.ChargeListOptions, Stripe.RequestOptions, CancellationToken)`
  - Returns a list of charges you’ve previously created. The charges are returned in
sorted order, with the most recent charges appearing first..
- `Search(Stripe.ChargeSearchOptions, Stripe.RequestOptions)`
  - Search for charges you’ve previously created using Stripe’s Search Query Language.
Don’t use search in read-after-write flows where strict consistency is necessary. Under
normal operating conditions, data is searchable in less than a minute. Occasionally,
propagation of new or updated data can be up to an hour behind during outages. Search
functionality is not available to merchants in India..
- `SearchAsync(Stripe.ChargeSearchOptions, Stripe.RequestOptions, CancellationToken)`
  - Search for charges you’ve previously created using Stripe’s Search Query Language.
Don’t use search in read-after-write flows where strict consistency is necessary. Under
normal operating conditions, data is searchable in less than a minute. Occasionally,
propagation of new or updated data can be up to an hour behind during outages. Search
functionality is not available to merchants in India..
- `SearchAutoPaging(Stripe.ChargeSearchOptions, Stripe.RequestOptions)`
  - Search for charges you’ve previously created using Stripe’s Search Query Language.
Don’t use search in read-after-write flows where strict consistency is necessary. Under
normal operating conditions, data is searchable in less than a minute. Occasionally,
propagation of new or updated data can be up to an hour behind during outages. Search
functionality is not available to merchants in India..
- `SearchAutoPagingAsync(Stripe.ChargeSearchOptions, Stripe.RequestOptions, CancellationToken)`
  - Search for charges you’ve previously created using Stripe’s Search Query Language.
Don’t use search in read-after-write flows where strict consistency is necessary. Under
normal operating conditions, data is searchable in less than a minute. Occasionally,
propagation of new or updated data can be up to an hour behind during outages. Search
functionality is not available to merchants in India..
- `Update(string, Stripe.ChargeUpdateOptions, Stripe.RequestOptions)`
  - Updates the specified charge by setting the values of the parameters passed. Any
parameters not provided will be left unchanged..
- `UpdateAsync(string, Stripe.ChargeUpdateOptions, Stripe.RequestOptions, CancellationToken)`
  - Updates the specified charge by setting the values of the parameters passed. Any
parameters not provided will be left unchanged..


#### `ChargeCreateOptions`

**Properties:**

- `Amount`
  - Amount intended to be collected by this payment. A positive integer representing how
much to charge in the smallest
currency unit (e.g., 100 cents to charge $1.00 or 100 to charge ¥100, a zero-decimal
currency). The minimum amount is $0.50 US or equivalent
in charge currency. The amount value supports up to eight digits (e.g., a value of
99999999 for a USD charge of $999,999.99).
- `ApplicationFeeAmount`
  - A fee in cents (or local equivalent) that will be applied to the charge and transferred
to the application owner's Stripe account. The request must be made with an OAuth key or
the `Stripe-Account` header in order to take an application fee. For more
information, see the application fees documentation.
- `Capture`
  - Whether to immediately capture the charge. Defaults to `true`. When `false`,
the charge issues an authorization (or pre-authorization), and will need to be captured later. Uncaptured charges
expire after a set number of days (7 by default). For more information, see the authorizing charges and settling
later documentation.
- `Currency`
  - Three-letter ISO currency
code, in lowercase. Must be a supported
currency.
- `Customer`
  - The ID of an existing customer that will be charged in this request.
- `Description`
  - An arbitrary string which you can attach to a `Charge` object. It is displayed when
in the web interface alongside the charge. Note that if you use Stripe to send automatic
email receipts to your customers, your receipt emails will include the
`description` of the charge(s) that they are describing.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format. Individual keys can be unset by posting an empty value to
them. All keys can be unset by posting an empty value to `metadata`.
- `OnBehalfOf`
  - The Stripe account ID for which these funds are intended. You can specify the business
of record as the connected account using the `on_behalf_of` attribute on the
charge. For details, see Creating
Separate Charges and Transfers.
- `RadarOptions`
  - Options to configure Radar. See Radar Session for more
information.
- `ReceiptEmail`
  - The email address to which this charge's receipt will be sent. The receipt
will not be sent until the charge is paid, and no receipts will be sent for test mode
charges. If this charge is for a Customer, the email address
specified here will override the customer's email address. If `receipt_email` is
specified for a charge in live mode, a receipt will be sent regardless of your email settings.
- `Shipping`
  - Shipping information for the charge. Helps prevent fraud on charges for physical goods.
- `Source`
  - A payment source to be charged. This can be the ID of a card (i.e., credit or debit card), a bank account, a source, a token, or a connected
account. For certain sources---namely, cards, bank accounts, and attached sources---you must also pass the ID of
the associated customer.
- `StatementDescriptor`
  - For a non-card charge, text that appears on the customer's statement as the statement
descriptor. This value overrides the account's default statement descriptor. For
information about requirements, including the 22-character limit, see the Statement
Descriptor docs.

For a card charge, this value is ignored unless you don't specify a
`statement_descriptor_suffix`, in which case this value is used as the suffix.
- `StatementDescriptorSuffix`
  - Provides information about a card charge. Concatenated to the account's statement
descriptor prefix to form the complete statement descriptor that appears on the
customer's statement. If the account has no prefix value, the suffix is concatenated to
the account's statement descriptor.
- `TransferData`
  - An optional dictionary including the account to automatically transfer to as part of a
destination charge. See
the Connect documentation for details.
- `TransferGroup`
  - A string that identifies this transaction as part of a group. For details, see Grouping
transactions.


#### `ChargeUpdateOptions`

**Properties:**

- `Customer`
  - The ID of an existing customer that will be associated with this request. This field may
only be updated if there is no existing associated customer with this charge.
- `Description`
  - An arbitrary string which you can attach to a charge object. It is displayed when in the
web interface alongside the charge. Note that if you use Stripe to send automatic email
receipts to your customers, your receipt emails will include the `description` of
the charge(s) that they are describing.
- `FraudDetails`
  - A set of key-value pairs you can attach to a charge giving information about its
riskiness. If you believe a charge is fraudulent, include a `user_report` key with
a value of `fraudulent`. If you believe a charge is safe, include a
`user_report` key with a value of `safe`. Stripe will use the information you
send to improve our fraud detection algorithms.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format. Individual keys can be unset by posting an empty value to
them. All keys can be unset by posting an empty value to `metadata`.
- `ReceiptEmail`
  - This is the email address that the receipt for this charge will be sent to. If this
field is updated, then a new email receipt will be sent to the updated address.
- `Shipping`
  - Shipping information for the charge. Helps prevent fraud on charges for physical goods.
- `TransferGroup`
  - A string that identifies this transaction as part of a group. `transfer_group` may
only be provided if it has not been set. See the Connect
documentation for details.


#### `ChargeListOptions`

**Properties:**

- `Created`
  - Only return charges that were created during the given date interval.
- `Customer`
  - Only return charges for the customer specified by this customer ID.
- `PaymentIntent`
  - Only return charges that were created by the PaymentIntent specified by this
PaymentIntent ID.
- `TransferGroup`
  - Only return charges for this transfer group, limited to 100.


#### `ChargeCaptureOptions`

**Properties:**

- `Amount`
  - The amount to capture, which must be less than or equal to the original amount.
- `ApplicationFee`
  - An application fee to add on to this charge.
- `ApplicationFeeAmount`
  - An application fee amount to add on to this charge, which must be less than or equal to
the original amount.
- `ReceiptEmail`
  - The email address to send this charge's receipt to. This will override the
previously-specified email address for this charge, if one was set. Receipts will not be
sent in test mode.
- `StatementDescriptor`
  - For a non-card charge, text that appears on the customer's statement as the statement
descriptor. This value overrides the account's default statement descriptor. For
information about requirements, including the 22-character limit, see the Statement
Descriptor docs.

For a card charge, this value is ignored unless you don't specify a
`statement_descriptor_suffix`, in which case this value is used as the suffix.
- `StatementDescriptorSuffix`
  - Provides information about a card charge. Concatenated to the account's statement
descriptor prefix to form the complete statement descriptor that appears on the
customer's statement. If the account has no prefix value, the suffix is concatenated to
the account's statement descriptor.
- `TransferData`
  - An optional dictionary including the account to automatically transfer to as part of a
destination charge. See
the Connect documentation for details.
- `TransferGroup`
  - A string that identifies this transaction as part of a group. `transfer_group` may
only be provided if it has not been set. See the Connect
documentation for details.


### Refund

#### `Refund`

Refund objects allow you to refund a previously created charge that isn't refunded yet.
Funds are refunded to the credit or debit card that's initially charged.

Related guide: Refunds.

**Properties:**

- `Amount`
  - Amount, in cents (or local equivalent).
- `BalanceTransaction`
  - (Expanded)
Balance transaction that describes the impact on your account balance.

For more information, see the expand documentation.
- `BalanceTransactionId`
  - (ID of the BalanceTransaction)
Balance transaction that describes the impact on your account balance.
- `Charge`
  - (Expanded)
ID of the charge that's refunded.

For more information, see the expand documentation.
- `ChargeId`
  - (ID of the Charge)
ID of the charge that's refunded.
- `Created`
  - Time at which the object was created. Measured in seconds since the Unix epoch.
- `Currency`
  - Three-letter ISO currency
code, in lowercase. Must be a supported
currency.
- `Description`
  - An arbitrary string attached to the object. You can use this for displaying to users
(available on non-card refunds only).
- `FailureBalanceTransaction`
  - (Expanded)
After the refund fails, this balance transaction describes the adjustment made on your
account balance that reverses the initial balance transaction.

For more information, see the expand documentation.
- `FailureBalanceTransactionId`
  - (ID of the BalanceTransaction)
After the refund fails, this balance transaction describes the adjustment made on your
account balance that reverses the initial balance transaction.
- `FailureReason`
  - Provides the reason for the refund failure. Possible values are:
`lost_or_stolen_card`, `expired_or_canceled_card`,
`charge_for_pending_refund_disputed`, `insufficient_funds`, `declined`,
`merchant_request`, or `unknown`.
- `Id`
  - Unique identifier for the object.
- `InstructionsEmail`
  - For payment methods without native refund support (for example, Konbini, PromptPay),
provide an email address for the customer to receive refund instructions.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format.
- `Object`
  - String representing the object's type. Objects of the same type share the same value.
- `PaymentIntent`
  - (Expanded)
ID of the PaymentIntent that's refunded.

For more information, see the expand documentation.
- `PaymentIntentId`
  - (ID of the PaymentIntent)
ID of the PaymentIntent that's refunded.
- `PendingReason`
  - Provides the reason for why the refund is pending. Possible values are:
`processing`, `insufficient_funds`, or `charge_pending`.
One of: `charge_pending`, `insufficient_funds`, or `processing`.
- `Reason`
  - Reason for the refund, which is either user-provided (`duplicate`,
`fraudulent`, or `requested_by_customer`) or generated by Stripe internally
(`expired_uncaptured_charge`).
One of: `duplicate`, `expired_uncaptured_charge`, `fraudulent`, or
`requested_by_customer`.
- `ReceiptNumber`
  - This is the transaction number that appears on email receipts sent for this refund.
- `SourceTransferReversal`
  - (Expanded)
The transfer reversal that's associated with the refund. Only present if the charge came
from another Stripe account.

For more information, see the expand documentation.
- `SourceTransferReversalId`
  - (ID of the TransferReversal)
The transfer reversal that's associated with the refund. Only present if the charge came
from another Stripe account.
- `Status`
  - Status of the refund. This can be `pending`, `requires_action`,
`succeeded`, `failed`, or `canceled`. Learn more about failed refunds.
- `TransferReversal`
  - (Expanded)
This refers to the transfer reversal object if the accompanying transfer reverses. This
is only applicable if the charge was created using the destination parameter.

For more information, see the expand documentation.
- `TransferReversalId`
  - (ID of the TransferReversal)
This refers to the transfer reversal object if the accompanying transfer reverses. This
is only applicable if the charge was created using the destination parameter.


#### `RefundService`

**Methods:**

- `Expire(string, Stripe.TestHelpers.RefundExpireOptions, Stripe.RequestOptions)`
  - Expire a refund with a status of `requires_action`..
- `ExpireAsync(string, Stripe.TestHelpers.RefundExpireOptions, Stripe.RequestOptions, CancellationToken)`
  - Expire a refund with a status of `requires_action`..


#### `RefundService`

**Methods:**

- `Cancel(string, Stripe.RefundCancelOptions, Stripe.RequestOptions)`
  - Cancels a refund with a status of `requires_action`..

You can’t cancel refunds in other states. Only refunds for payment methods that
require customer action can enter the `requires_action` state..
- `CancelAsync(string, Stripe.RefundCancelOptions, Stripe.RequestOptions, CancellationToken)`
  - Cancels a refund with a status of `requires_action`..

You can’t cancel refunds in other states. Only refunds for payment methods that
require customer action can enter the `requires_action` state..
- `Create(Stripe.RefundCreateOptions, Stripe.RequestOptions)`
  - When you create a new refund, you must specify a Charge or a PaymentIntent object on
which to create it..

Creating a new refund will refund a charge that has previously been created but not
yet refunded. Funds will be refunded to the credit or debit card that was originally
charged..

You can optionally refund only part of a charge. You can do so multiple times, until
the entire charge has been refunded..

Once entirely refunded, a charge can’t be refunded again. This method will raise an
error when called on an already-refunded charge, or when trying to refund more money
than is left on a charge..
- `CreateAsync(Stripe.RefundCreateOptions, Stripe.RequestOptions, CancellationToken)`
  - When you create a new refund, you must specify a Charge or a PaymentIntent object on
which to create it..

Creating a new refund will refund a charge that has previously been created but not
yet refunded. Funds will be refunded to the credit or debit card that was originally
charged..

You can optionally refund only part of a charge. You can do so multiple times, until
the entire charge has been refunded..

Once entirely refunded, a charge can’t be refunded again. This method will raise an
error when called on an already-refunded charge, or when trying to refund more money
than is left on a charge..
- `Get(string, Stripe.RefundGetOptions, Stripe.RequestOptions)`
  - Retrieves the details of an existing refund..
- `GetAsync(string, Stripe.RefundGetOptions, Stripe.RequestOptions, CancellationToken)`
  - Retrieves the details of an existing refund..
- `List(Stripe.RefundListOptions, Stripe.RequestOptions)`
  - Returns a list of all refunds you created. We return the refunds in sorted order,
with the most recent refunds appearing first. The 10 most recent refunds are always
available by default on the Charge object..
- `ListAsync(Stripe.RefundListOptions, Stripe.RequestOptions, CancellationToken)`
  - Returns a list of all refunds you created. We return the refunds in sorted order,
with the most recent refunds appearing first. The 10 most recent refunds are always
available by default on the Charge object..
- `ListAutoPaging(Stripe.RefundListOptions, Stripe.RequestOptions)`
  - Returns a list of all refunds you created. We return the refunds in sorted order,
with the most recent refunds appearing first. The 10 most recent refunds are always
available by default on the Charge object..
- `ListAutoPagingAsync(Stripe.RefundListOptions, Stripe.RequestOptions, CancellationToken)`
  - Returns a list of all refunds you created. We return the refunds in sorted order,
with the most recent refunds appearing first. The 10 most recent refunds are always
available by default on the Charge object..
- `Update(string, Stripe.RefundUpdateOptions, Stripe.RequestOptions)`
  - Updates the refund that you specify by setting the values of the passed parameters.
Any parameters that you don’t provide remain unchanged..

This request only accepts `metadata` as an argument..
- `UpdateAsync(string, Stripe.RefundUpdateOptions, Stripe.RequestOptions, CancellationToken)`
  - Updates the refund that you specify by setting the values of the passed parameters.
Any parameters that you don’t provide remain unchanged..

This request only accepts `metadata` as an argument..


#### `RefundCreateOptions`

**Properties:**

- `Charge`
  - The identifier of the charge to refund.
- `Currency`
  - Three-letter ISO currency
code, in lowercase. Must be a supported
currency.
- `Customer`
  - Customer whose customer balance to refund from.
- `InstructionsEmail`
  - For payment methods without native refund support (e.g., Konbini, PromptPay), use this
email from the customer to receive refund instructions.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format. Individual keys can be unset by posting an empty value to
them. All keys can be unset by posting an empty value to `metadata`.
- `Origin`
  - Origin of the refund.
- `PaymentIntent`
  - The identifier of the PaymentIntent to refund.
- `Reason`
  - String indicating the reason for the refund. If set, possible values are
`duplicate`, `fraudulent`, and `requested_by_customer`. If you believe
the charge to be fraudulent, specifying `fraudulent` as the reason will add the
associated card and email to your block
lists, and will also help us improve our fraud detection algorithms.
One of: `duplicate`, `fraudulent`, or `requested_by_customer`.
- `RefundApplicationFee`
  - Boolean indicating whether the application fee should be refunded when refunding this
charge. If a full charge refund is given, the full application fee will be refunded.
Otherwise, the application fee will be refunded in an amount proportional to the amount
of the charge refunded. An application fee can be refunded only by the application that
created the charge.
- `ReverseTransfer`
  - Boolean indicating whether the transfer should be reversed when refunding this charge.
The transfer will be reversed proportionally to the amount being refunded (either the
entire or partial amount).A transfer can be reversed only by the application
that created the charge.


#### `RefundUpdateOptions`

**Properties:**

- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format. Individual keys can be unset by posting an empty value to
them. All keys can be unset by posting an empty value to `metadata`.


#### `RefundListOptions`

**Properties:**

- `Charge`
  - Only return refunds for the charge specified by this charge ID.
- `Created`
  - Only return refunds that were created during the given date interval.
- `PaymentIntent`
  - Only return refunds for the PaymentIntent specified by this ID.


### Subscription

#### `Subscription`

Subscriptions allow you to charge a customer on a recurring basis.

Related guide: Creating
subscriptions.

**Properties:**

- `Application`
  - (Expanded)
ID of the Connect Application that created the subscription.

For more information, see the expand documentation.
- `ApplicationFeePercent`
  - A non-negative decimal between 0 and 100, with at most two decimal places. This
represents the percentage of the subscription invoice total that will be transferred to
the application owner's Stripe account.
- `ApplicationId`
  - (ID of the Application)
ID of the Connect Application that created the subscription.
- `BillingCycleAnchor`
  - The reference point that aligns future billing cycle dates. It
sets the day of week for `week` intervals, the day of month for `month` and
`year` intervals, and the month of year for `year` intervals. The timestamp is
in UTC format.
- `BillingCycleAnchorConfig`
  - The fixed values used to calculate the `billing_cycle_anchor`.
- `BillingMode`
  - The billing mode of the subscription.
- `BillingSchedules`
  - Billing schedules for this subscription.
- `BillingThresholds`
  - Define thresholds at which an invoice will be sent, and the subscription advanced to a
new billing period.
- `CancelAt`
  - A date in the future at which the subscription will automatically get canceled.
- `CancelAtPeriodEnd`
  - Whether this subscription will (if `status=active`) or did (if
`status=canceled`) cancel at the end of the current billing period.
- `CanceledAt`
  - If the subscription has been canceled, the date of that cancellation. If the
subscription was canceled with `cancel_at_period_end`, `canceled_at` will
reflect the time of the most recent update request, not the end of the subscription
period when the subscription is automatically moved to a canceled state.
- `CancellationDetails`
  - Details about why this subscription was cancelled.
- `CollectionMethod`
  - Either `charge_automatically`, or `send_invoice`. When charging automatically,
Stripe will attempt to pay this subscription at the end of the cycle using the default
source attached to the customer. When sending an invoice, Stripe will email your
customer an invoice with payment instructions and mark the subscription as
`active`.
One of: `charge_automatically`, or `send_invoice`.
- `Created`
  - Time at which the object was created. Measured in seconds since the Unix epoch.
- `Currency`
  - Three-letter ISO currency
code, in lowercase. Must be a supported
currency.
- `Customer`
  - (Expanded)
ID of the customer who owns the subscription.

For more information, see the expand documentation.
- `CustomerAccount`
  - ID of the account representing the customer who owns the subscription.
- `CustomerId`
  - (ID of the Customer)
ID of the customer who owns the subscription.
- `DaysUntilDue`
  - Number of days a customer has to pay invoices generated by this subscription. This value
will be `null` for subscriptions where
`collection_method=charge_automatically`.
- `DefaultPaymentMethod`
  - (Expanded)
ID of the default payment method for the subscription. It must belong to the customer
associated with the subscription. This takes precedence over `default_source`. If
neither are set, invoices will use the customer's invoice_settings.default_payment_method
or default_source.

For more information, see the expand documentation.
- `DefaultPaymentMethodId`
  - (ID of the PaymentMethod)
ID of the default payment method for the subscription. It must belong to the customer
associated with the subscription. This takes precedence over `default_source`. If
neither are set, invoices will use the customer's invoice_settings.default_payment_method
or default_source.
- `DefaultSource`
  - (Expanded)
ID of the default payment source for the subscription. It must belong to the customer
associated with the subscription and be in a chargeable state. If
`default_payment_method` is also set, `default_payment_method` will take
precedence. If neither are set, invoices will use the customer's invoice_settings.default_payment_method
or default_source.

For more information, see the expand documentation.
- `DefaultSourceId`
  - (ID of the IPaymentSource)
ID of the default payment source for the subscription. It must belong to the customer
associated with the subscription and be in a chargeable state. If
`default_payment_method` is also set, `default_payment_method` will take
precedence. If neither are set, invoices will use the customer's invoice_settings.default_payment_method
or default_source.
- `DefaultTaxRates`
  - The tax rates that will apply to any subscription item that does not have
`tax_rates` set. Invoices created will have their `default_tax_rates`
populated from the subscription.
- `Description`
  - The subscription's description, meant to be displayable to the customer. Use this field
to optionally store an explanation of the subscription for rendering in Stripe surfaces
and certain local payment methods UIs.
- `DiscountIds`
  - (IDs of the Discounts)
The discounts applied to the subscription. Subscription item discounts are applied
before subscription discounts. Use `expand[]=discounts` to expand each discount.
- `Discounts`
  - (Expanded)
The discounts applied to the subscription. Subscription item discounts are applied
before subscription discounts. Use `expand[]=discounts` to expand each discount.

For more information, see the expand documentation.
- `EndedAt`
  - If the subscription has ended, the date the subscription ended.
- `Id`
  - Unique identifier for the object.
- `Items`
  - List of subscription items, each with an attached price.
- `LatestInvoice`
  - (Expanded)
The most recent invoice this subscription has generated over its lifecycle (for example,
when it cycles or is updated).

For more information, see the expand documentation.
- `LatestInvoiceId`
  - (ID of the Invoice)
The most recent invoice this subscription has generated over its lifecycle (for example,
when it cycles or is updated).
- `Livemode`
  - If the object exists in live mode, the value is `true`. If the object exists in
test mode, the value is `false`.
- `ManagedPayments`
  - Settings for Managed Payments for this Subscription and resulting Invoices and PaymentIntents.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format.
- `NextPendingInvoiceItemInvoice`
  - Specifies the approximate timestamp on which any pending invoice items will be billed
according to the schedule provided at `pending_invoice_item_interval`.
- `Object`
  - String representing the object's type. Objects of the same type share the same value.
- `OnBehalfOf`
  - (Expanded)
The account (if any) the charge was made on behalf of for charges associated with this
subscription. See the Connect
documentation for details.

For more information, see the expand documentation.
- `OnBehalfOfId`
  - (ID of the Account)
The account (if any) the charge was made on behalf of for charges associated with this
subscription. See the Connect
documentation for details.
- `PauseCollection`
  - If specified, payment collection for this subscription will be paused. Note that the
subscription status will be unchanged and will not be updated to `paused`. Learn
more about pausing
collection.
- `PaymentSettings`
  - Payment settings passed on to invoices created by the subscription.
- `PendingInvoiceItemInterval`
  - Specifies an interval for how often to bill for any pending invoice items. It is
analogous to calling Create an
invoice for the given subscription at the specified interval.
- `PendingSetupIntent`
  - (Expanded)
You can use this SetupIntent to
collect user authentication when creating a subscription without immediate payment or
updating a subscription's payment method, allowing you to optimize for off-session
payments. Learn more in the SCA
Migration Guide.

For more information, see the expand documentation.
- `PendingSetupIntentId`
  - (ID of the SetupIntent)
You can use this SetupIntent to
collect user authentication when creating a subscription without immediate payment or
updating a subscription's payment method, allowing you to optimize for off-session
payments. Learn more in the SCA
Migration Guide.
- `PendingUpdate`
  - If specified, pending updates
that will be applied to the subscription once the `latest_invoice` has been paid.
- `Schedule`
  - (Expanded)
The schedule attached to the subscription.

For more information, see the expand documentation.
- `ScheduleId`
  - (ID of the SubscriptionSchedule)
The schedule attached to the subscription.
- `StartDate`
  - Date when the subscription was first created. The date might differ from the
`created` date due to backdating.
- `Status`
  - Possible values are `incomplete`, `incomplete_expired`, `trialing`,
`active`, `past_due`, `canceled`, `unpaid`, or `paused`.

For `collection_method=charge_automatically` a subscription moves into
`incomplete` if the initial payment attempt fails. A subscription in this status
can only have metadata and default_source updated. Once the first invoice is paid, the
subscription moves into an `active` status. If the first invoice is not paid within
23 hours, the subscription transitions to `incomplete_expired`. This is a terminal
status, the open invoice will be voided and no further invoices will be generated.

A subscription that is currently in a trial period is `trialing` and moves to
`active` when the trial period is over.

A subscription can only enter a `paused` status when
a trial ends without a payment method. A `paused` subscription doesn't generate
invoices and can be resumed after your customer adds their payment method. The
`paused` status is different from pausing
collection, which still generates invoices and leaves the subscription's status
unchanged.

If subscription `collection_method=charge_automatically`, it becomes
`past_due` when payment is required but cannot be paid (due to failed payment or
awaiting additional user actions). Once Stripe has exhausted all payment retry attempts,
the subscription will become `canceled` or `unpaid` (depending on your
subscriptions settings).

If subscription `collection_method=send_invoice` it becomes `past_due` when
its invoice is not paid by the due date, and `canceled` or `unpaid` if it is
still not paid by an additional deadline after that. Note that when a subscription has a
status of `unpaid`, no subsequent invoices will be attempted (invoices will be
created, but then immediately automatically closed). After receiving updated payment
information from a customer, you may choose to reopen and pay their closed invoices.
One of: `active`, `canceled`, `incomplete`, `incomplete_expired`,
`past_due`, `paused`, `trialing`, or `unpaid`.
- `TestClock`
  - (Expanded)
ID of the test clock this subscription belongs to.

For more information, see the expand documentation.
- `TestClockId`
  - (ID of the TestHelpers.TestClock)
ID of the test clock this subscription belongs to.
- `TransferData`
  - The account (if any) the subscription's payments will be attributed to for tax
reporting, and where funds from each payment will be transferred to for each of the
subscription's invoices.
- `TrialEnd`
  - If the subscription has a trial, the end of that trial.
- `TrialSettings`
  - Settings related to subscription trials.
- `TrialStart`
  - If the subscription has a trial, the beginning of that trial.


#### `SubscriptionService`

**Methods:**

- `Cancel(string, Stripe.SubscriptionCancelOptions, Stripe.RequestOptions)`
  - Cancels a customer’s subscription immediately. The customer won’t be charged again
for the subscription. After it’s canceled, the subscription is largely immutable. You
can still update its metadata and
`cancellation_details`..

Any pending invoice items that you’ve created are still charged at the end of the
period, unless manually deleted. If you’ve set the
subscription to cancel at the end of the period, any pending prorations are also left in
place and collected at the end of the period. But if the subscription is set to cancel
immediately, pending prorations are removed if `invoice_now` and `prorate` are
both set to true..

By default, upon subscription cancellation, Stripe stops automatic collection of all
finalized invoices for the customer. This is intended to prevent unexpected payment
attempts after the customer has canceled a subscription. However, you can resume
automatic collection of the invoices manually after subscription cancellation to have us
proceed. Or, you could check for unpaid invoices before allowing the customer to cancel
the subscription at all..
- `CancelAsync(string, Stripe.SubscriptionCancelOptions, Stripe.RequestOptions, CancellationToken)`
  - Cancels a customer’s subscription immediately. The customer won’t be charged again
for the subscription. After it’s canceled, the subscription is largely immutable. You
can still update its metadata and
`cancellation_details`..

Any pending invoice items that you’ve created are still charged at the end of the
period, unless manually deleted. If you’ve set the
subscription to cancel at the end of the period, any pending prorations are also left in
place and collected at the end of the period. But if the subscription is set to cancel
immediately, pending prorations are removed if `invoice_now` and `prorate` are
both set to true..

By default, upon subscription cancellation, Stripe stops automatic collection of all
finalized invoices for the customer. This is intended to prevent unexpected payment
attempts after the customer has canceled a subscription. However, you can resume
automatic collection of the invoices manually after subscription cancellation to have us
proceed. Or, you could check for unpaid invoices before allowing the customer to cancel
the subscription at all..
- `Create(Stripe.SubscriptionCreateOptions, Stripe.RequestOptions)`
  - Creates a new subscription on an existing customer. Each customer can have up to 500
active or scheduled subscriptions..

When you create a subscription with `collection_method=charge_automatically`,
the first invoice is finalized as part of the request. The `payment_behavior`
parameter determines the exact behavior of the initial payment..

To start subscriptions where the first invoice always begins in a `draft`
status, use subscription
schedules instead. Schedules provide the flexibility to model more complex billing
configurations that change over time..
- `CreateAsync(Stripe.SubscriptionCreateOptions, Stripe.RequestOptions, CancellationToken)`
  - Creates a new subscription on an existing customer. Each customer can have up to 500
active or scheduled subscriptions..

When you create a subscription with `collection_method=charge_automatically`,
the first invoice is finalized as part of the request. The `payment_behavior`
parameter determines the exact behavior of the initial payment..

To start subscriptions where the first invoice always begins in a `draft`
status, use subscription
schedules instead. Schedules provide the flexibility to model more complex billing
configurations that change over time..
- `DeleteDiscount(string, Stripe.SubscriptionDeleteDiscountOptions, Stripe.RequestOptions)`
  - Removes the currently applied discount on a subscription..
- `DeleteDiscountAsync(string, Stripe.SubscriptionDeleteDiscountOptions, Stripe.RequestOptions, CancellationToken)`
  - Removes the currently applied discount on a subscription..
- `Get(string, Stripe.SubscriptionGetOptions, Stripe.RequestOptions)`
  - Retrieves the subscription with the given ID..
- `GetAsync(string, Stripe.SubscriptionGetOptions, Stripe.RequestOptions, CancellationToken)`
  - Retrieves the subscription with the given ID..
- `List(Stripe.SubscriptionListOptions, Stripe.RequestOptions)`
  - By default, returns a list of subscriptions that have not been canceled. In order to
list canceled subscriptions, specify `status=canceled`..
- `ListAsync(Stripe.SubscriptionListOptions, Stripe.RequestOptions, CancellationToken)`
  - By default, returns a list of subscriptions that have not been canceled. In order to
list canceled subscriptions, specify `status=canceled`..
- `ListAutoPaging(Stripe.SubscriptionListOptions, Stripe.RequestOptions)`
  - By default, returns a list of subscriptions that have not been canceled. In order to
list canceled subscriptions, specify `status=canceled`..
- `ListAutoPagingAsync(Stripe.SubscriptionListOptions, Stripe.RequestOptions, CancellationToken)`
  - By default, returns a list of subscriptions that have not been canceled. In order to
list canceled subscriptions, specify `status=canceled`..
- `Migrate(string, Stripe.SubscriptionMigrateOptions, Stripe.RequestOptions)`
  - Upgrade the billing_mode of an existing subscription..
- `MigrateAsync(string, Stripe.SubscriptionMigrateOptions, Stripe.RequestOptions, CancellationToken)`
  - Upgrade the billing_mode of an existing subscription..
- `Resume(string, Stripe.SubscriptionResumeOptions, Stripe.RequestOptions)`
  - Initiates resumption of a paused subscription, optionally resetting the billing cycle
anchor and creating prorations. Resume is only available for subscriptions that use
`charge_automatically` collection. If Stripe doesn’t generate a resumption invoice,
the subscription becomes `active` immediately. When a resumption invoice is
generated, Stripe finalizes it immediately. If the invoice is paid or marked
uncollectible, the subscription becomes `active`. If the invoice is manually
voided, the subscription stays `paused`. If there is no payment attempt within 23
hours, Stripe voids the invoice and the subscription stays `paused`. Learn more
about resuming
subscriptions..
- `ResumeAsync(string, Stripe.SubscriptionResumeOptions, Stripe.RequestOptions, CancellationToken)`
  - Initiates resumption of a paused subscription, optionally resetting the billing cycle
anchor and creating prorations. Resume is only available for subscriptions that use
`charge_automatically` collection. If Stripe doesn’t generate a resumption invoice,
the subscription becomes `active` immediately. When a resumption invoice is
generated, Stripe finalizes it immediately. If the invoice is paid or marked
uncollectible, the subscription becomes `active`. If the invoice is manually
voided, the subscription stays `paused`. If there is no payment attempt within 23
hours, Stripe voids the invoice and the subscription stays `paused`. Learn more
about resuming
subscriptions..
- `Search(Stripe.SubscriptionSearchOptions, Stripe.RequestOptions)`
  - Search for subscriptions you’ve previously created using Stripe’s Search Query Language.
Don’t use search in read-after-write flows where strict consistency is necessary. Under
normal operating conditions, data is searchable in less than a minute. Occasionally,
propagation of new or updated data can be up to an hour behind during outages. Search
functionality is not available to merchants in India..
- `SearchAsync(Stripe.SubscriptionSearchOptions, Stripe.RequestOptions, CancellationToken)`
  - Search for subscriptions you’ve previously created using Stripe’s Search Query Language.
Don’t use search in read-after-write flows where strict consistency is necessary. Under
normal operating conditions, data is searchable in less than a minute. Occasionally,
propagation of new or updated data can be up to an hour behind during outages. Search
functionality is not available to merchants in India..
- `SearchAutoPaging(Stripe.SubscriptionSearchOptions, Stripe.RequestOptions)`
  - Search for subscriptions you’ve previously created using Stripe’s Search Query Language.
Don’t use search in read-after-write flows where strict consistency is necessary. Under
normal operating conditions, data is searchable in less than a minute. Occasionally,
propagation of new or updated data can be up to an hour behind during outages. Search
functionality is not available to merchants in India..
- `SearchAutoPagingAsync(Stripe.SubscriptionSearchOptions, Stripe.RequestOptions, CancellationToken)`
  - Search for subscriptions you’ve previously created using Stripe’s Search Query Language.
Don’t use search in read-after-write flows where strict consistency is necessary. Under
normal operating conditions, data is searchable in less than a minute. Occasionally,
propagation of new or updated data can be up to an hour behind during outages. Search
functionality is not available to merchants in India..
- `Update(string, Stripe.SubscriptionUpdateOptions, Stripe.RequestOptions)`
  - Updates an existing subscription to match the specified parameters. When changing
prices or quantities, we optionally prorate the price we charge next month to make up
for any price changes. To preview how the proration is calculated, use the create preview
endpoint..

By default, we prorate subscription changes. For example, if a customer signs up on
May 1 for a 100 price, they’ll be billed 100
immediately. If on May 15 they switch to a 200 price, then on June
1 they’ll be billed 250 (200 for a renewal of
her subscription, plus a 50 prorating adjustment for half of the
previous month’s 100 difference). Similarly, a downgrade generates
a credit that is applied to the next invoice. We also prorate when you make quantity
changes..

Switching prices does not normally change the billing date or generate an immediate
charge unless:.

The billing interval is changed (for example, from monthly to yearly).
The subscription moves from free to paid. A trial starts or ends..

In these cases, we apply a credit for the unused time on the previous price,
immediately charge the customer using the new price, and reset the billing date. Learn
about how Stripe
immediately attempts payment for subscription changes..

If you want to charge for an upgrade immediately, pass `proration_behavior` as
`always_invoice` to create prorations, automatically invoice the customer for those
proration adjustments, and attempt to collect payment. If you pass
`create_prorations`, the prorations are created but not automatically invoiced. If
you want to bill the customer for the prorations before the subscription’s renewal date,
you need to manually invoice the
customer..

If you don’t want to prorate, set the `proration_behavior` option to
`none`. With this option, the customer is billed 100 on May 1
and 200 on June 1. Similarly, if you set `proration_behavior`
to `none` when switching between different billing intervals (for example, from
monthly to yearly), we don’t generate any credits for the old subscription’s unused
time. We still reset the billing date and bill immediately for the new subscription..

Updating the quantity on a subscription many times in an hour may result in rate limiting. If you need to bill for a
frequently changing quantity, consider integrating usage-based billing
instead..
- `UpdateAsync(string, Stripe.SubscriptionUpdateOptions, Stripe.RequestOptions, CancellationToken)`
  - Updates an existing subscription to match the specified parameters. When changing
prices or quantities, we optionally prorate the price we charge next month to make up
for any price changes. To preview how the proration is calculated, use the create preview
endpoint..

By default, we prorate subscription changes. For example, if a customer signs up on
May 1 for a 100 price, they’ll be billed 100
immediately. If on May 15 they switch to a 200 price, then on June
1 they’ll be billed 250 (200 for a renewal of
her subscription, plus a 50 prorating adjustment for half of the
previous month’s 100 difference). Similarly, a downgrade generates
a credit that is applied to the next invoice. We also prorate when you make quantity
changes..

Switching prices does not normally change the billing date or generate an immediate
charge unless:.

The billing interval is changed (for example, from monthly to yearly).
The subscription moves from free to paid. A trial starts or ends..

In these cases, we apply a credit for the unused time on the previous price,
immediately charge the customer using the new price, and reset the billing date. Learn
about how Stripe
immediately attempts payment for subscription changes..

If you want to charge for an upgrade immediately, pass `proration_behavior` as
`always_invoice` to create prorations, automatically invoice the customer for those
proration adjustments, and attempt to collect payment. If you pass
`create_prorations`, the prorations are created but not automatically invoiced. If
you want to bill the customer for the prorations before the subscription’s renewal date,
you need to manually invoice the
customer..

If you don’t want to prorate, set the `proration_behavior` option to
`none`. With this option, the customer is billed 100 on May 1
and 200 on June 1. Similarly, if you set `proration_behavior`
to `none` when switching between different billing intervals (for example, from
monthly to yearly), we don’t generate any credits for the old subscription’s unused
time. We still reset the billing date and bill immediately for the new subscription..

Updating the quantity on a subscription many times in an hour may result in rate limiting. If you need to bill for a
frequently changing quantity, consider integrating usage-based billing
instead..


#### `SubscriptionCreateOptions`

**Properties:**

- `AddInvoiceItems`
  - A list of prices and quantities that will generate invoice items appended to the next
invoice for this subscription. You may pass up to 20 items.
- `ApplicationFeePercent`
  - A non-negative decimal between 0 and 100, with at most two decimal places. This
represents the percentage of the subscription invoice total that will be transferred to
the application owner's Stripe account. The request must be made by a platform account
on a connected account in order to set an application fee percentage. For more
information, see the application fees documentation.
- `AutomaticTax`
  - Automatic tax settings for this subscription.
- `BackdateStartDate`
  - A past timestamp to backdate the subscription's start date to. If set, the first invoice
will contain line items for the timespan between the start date and the current time.
Can be combined with trials and the billing cycle anchor.
- `BillingCycleAnchor`
  - A future timestamp in UTC format to anchor the subscription's billing cycle. The anchor
is the reference point that aligns future billing cycle dates. It sets the day of week
for `week` intervals, the day of month for `month` and `year` intervals,
and the month of year for `year` intervals.
- `BillingCycleAnchorConfig`
  - Mutually exclusive with billing_cycle_anchor and only valid with monthly and yearly
price intervals. When provided, the billing_cycle_anchor is set to the next occurrence
of the day_of_month at the hour, minute, and second UTC.
- `BillingMode`
  - Controls how prorations and invoices for subscriptions are calculated and orchestrated.
- `BillingSchedules`
  - Sets the billing schedules for the subscription.
- `BillingThresholds`
  - Define thresholds at which an invoice will be sent, and the subscription advanced to a
new billing period. When updating, pass an empty string to remove previously-defined
thresholds.
- `CancelAt`
  - A timestamp at which the subscription should cancel. If set to a date before the current
period ends, this will cause a proration if prorations have been enabled using
`proration_behavior`. If set during a future period, this will always cause a
proration for that period.
- `CancelAtPeriodEnd`
  - Indicate whether this subscription should cancel at the end of the current period
(`current_period_end`). Defaults to `false`.
- `CollectionMethod`
  - Either `charge_automatically`, or `send_invoice`. When charging automatically,
Stripe will attempt to pay this subscription at the end of the cycle using the default
source attached to the customer. When sending an invoice, Stripe will email your
customer an invoice with payment instructions and mark the subscription as
`active`. Defaults to `charge_automatically`.
One of: `charge_automatically`, or `send_invoice`.
- `Currency`
  - Three-letter ISO currency
code, in lowercase. Must be a supported
currency.
- `Customer`
  - The identifier of the customer to subscribe.
- `CustomerAccount`
  - The identifier of the account representing the customer to subscribe.
- `DaysUntilDue`
  - Number of days a customer has to pay invoices generated by this subscription. Valid only
for subscriptions where `collection_method` is set to `send_invoice`.
- `DefaultPaymentMethod`
  - ID of the default payment method for the subscription. It must belong to the customer
associated with the subscription. This takes precedence over `default_source`. If
neither are set, invoices will use the customer's invoice_settings.default_payment_method
or default_source.
- `DefaultSource`
  - ID of the default payment source for the subscription. It must belong to the customer
associated with the subscription and be in a chargeable state. If
`default_payment_method` is also set, `default_payment_method` will take
precedence. If neither are set, invoices will use the customer's invoice_settings.default_payment_method
or default_source.
- `DefaultTaxRates`
  - The tax rates that will apply to any subscription item that does not have
`tax_rates` set. Invoices created will have their `default_tax_rates`
populated from the subscription.
- `Description`
  - The subscription's description, meant to be displayable to the customer. Use this field
to optionally store an explanation of the subscription for rendering in Stripe surfaces
and certain local payment methods UIs.
- `Discounts`
  - The coupons to redeem into discounts for the subscription. If not specified or empty,
inherits the discount from the subscription's customer.
- `InvoiceSettings`
  - All invoices will be billed using the specified settings.
- `Items`
  - A list of up to 20 subscription items, each with an attached price.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format. Individual keys can be unset by posting an empty value to
them. All keys can be unset by posting an empty value to `metadata`.
- `OffSession`
  - Indicates if a customer is on or off-session while an invoice payment is attempted.
Defaults to `false` (on-session).
- `OnBehalfOf`
  - The account on behalf of which to charge, for each of the subscription's invoices.
- `PaymentBehavior`
  - Controls how Stripe handles the first invoice when payment is required and
`collection_method=charge_automatically`. Subscriptions with
`collection_method=send_invoice` are automatically activated regardless of the
first Invoice status.
One of: `allow_incomplete`, `default_incomplete`, `error_if_incomplete`,
or `pending_if_incomplete`.
- `PaymentSettings`
  - Payment settings to pass to invoices created by the subscription.
- `PendingInvoiceItemInterval`
  - Specifies an interval for how often to bill for any pending invoice items. It is
analogous to calling Create an
invoice for the given subscription at the specified interval.
- `ProrationBehavior`
  - Determines how to handle prorations resulting
from the `billing_cycle_anchor`. If no value is passed, the default is
`create_prorations`.
One of: `always_invoice`, `create_prorations`, or `none`.
- `TransferData`
  - If specified, the funds from the subscription's invoices will be transferred to the
destination and the ID of the resulting transfers will be found on the resulting
charges.
- `TrialEnd`
  - Unix timestamp representing the end of the trial period the customer will get before
being charged for the first time. If set, trial_end will override the default trial
period of the plan the customer is being subscribed to. The special value `now` can
be provided to end the customer's trial immediately. Can be at most two years from
`billing_cycle_anchor`. See Using trial periods on
subscriptions to learn more.
- `TrialFromPlan`
  - Indicates if a plan's `trial_period_days` should be applied to the subscription.
Setting `trial_end` per subscription is preferred, and this defaults to
`false`. Setting this flag to `true` together with `trial_end` is not
allowed. See Using trial
periods on subscriptions to learn more.
- `TrialPeriodDays`
  - Integer representing the number of trial period days before the customer is charged for
the first time. This will always overwrite any trials that might apply via a subscribed
plan. See Using trial
periods on subscriptions to learn more.
- `TrialSettings`
  - Settings related to subscription trials.


#### `SubscriptionUpdateOptions`

**Properties:**

- `AddInvoiceItems`
  - A list of prices and quantities that will generate invoice items appended to the next
invoice for this subscription. You may pass up to 20 items.
- `ApplicationFeePercent`
  - A non-negative decimal between 0 and 100, with at most two decimal places. This
represents the percentage of the subscription invoice total that will be transferred to
the application owner's Stripe account. The request must be made by a platform account
on a connected account in order to set an application fee percentage. For more
information, see the application fees documentation.
- `AutomaticTax`
  - Automatic tax settings for this subscription. We recommend you only include this
parameter when the existing value is being changed.
- `BillingCycleAnchor`
  - Either `now` or `unchanged`. Setting the value to `now` resets the
subscription's billing cycle anchor to the current time (in UTC). For more information,
see the billing cycle documentation.
One of: `now`, or `unchanged`.
- `BillingSchedules`
  - Sets the billing schedules for the subscription.
- `BillingThresholds`
  - Define thresholds at which an invoice will be sent, and the subscription advanced to a
new billing period. When updating, pass an empty string to remove previously-defined
thresholds.
- `CancelAt`
  - A timestamp at which the subscription should cancel. If set to a date before the current
period ends, this will cause a proration if prorations have been enabled using
`proration_behavior`. If set during a future period, this will always cause a
proration for that period.
- `CancelAtPeriodEnd`
  - Indicate whether this subscription should cancel at the end of the current period
(`current_period_end`). Defaults to `false`.
- `CancellationDetails`
  - Details about why this subscription was cancelled.
- `CollectionMethod`
  - Either `charge_automatically`, or `send_invoice`. When charging automatically,
Stripe will attempt to pay this subscription at the end of the cycle using the default
source attached to the customer. When sending an invoice, Stripe will email your
customer an invoice with payment instructions and mark the subscription as
`active`. Defaults to `charge_automatically`.
One of: `charge_automatically`, or `send_invoice`.
- `DaysUntilDue`
  - Number of days a customer has to pay invoices generated by this subscription. Valid only
for subscriptions where `collection_method` is set to `send_invoice`.
- `DefaultPaymentMethod`
  - ID of the default payment method for the subscription. It must belong to the customer
associated with the subscription. This takes precedence over `default_source`. If
neither are set, invoices will use the customer's invoice_settings.default_payment_method
or default_source.
- `DefaultSource`
  - ID of the default payment source for the subscription. It must belong to the customer
associated with the subscription and be in a chargeable state. If
`default_payment_method` is also set, `default_payment_method` will take
precedence. If neither are set, invoices will use the customer's invoice_settings.default_payment_method
or default_source.
- `DefaultTaxRates`
  - The tax rates that will apply to any subscription item that does not have
`tax_rates` set. Invoices created will have their `default_tax_rates`
populated from the subscription. Pass an empty string to remove previously-defined tax
rates.
- `Description`
  - The subscription's description, meant to be displayable to the customer. Use this field
to optionally store an explanation of the subscription for rendering in Stripe surfaces
and certain local payment methods UIs.
- `Discounts`
  - The coupons to redeem into discounts for the subscription. A populated array overwrites
the existing discounts on the subscription. If not specified or empty array, it leaves
the subscription's discounts unchanged. If empty string, it clears the subscription's
discounts.
- `InvoiceSettings`
  - All invoices will be billed using the specified settings.
- `Items`
  - A list of up to 20 subscription items, each with an attached price.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format. Individual keys can be unset by posting an empty value to
them. All keys can be unset by posting an empty value to `metadata`.
- `OffSession`
  - Indicates if a customer is on or off-session while an invoice payment is attempted.
Defaults to `false` (on-session).
- `OnBehalfOf`
  - The account on behalf of which to charge, for each of the subscription's invoices.
- `PauseCollection`
  - If specified, payment collection for this subscription will be paused. Note that the
subscription status will be unchanged and will not be updated to `paused`. Learn
more about pausing
collection.
- `PaymentBehavior`
  - Controls how Stripe handles payment when a subscription update requires payment and
`collection_method=charge_automatically`.
One of: `allow_incomplete`, `default_incomplete`, `error_if_incomplete`,
or `pending_if_incomplete`.
- `PaymentSettings`
  - Payment settings to pass to invoices created by the subscription.
- `PendingInvoiceItemInterval`
  - Specifies an interval for how often to bill for any pending invoice items. It is
analogous to calling Create an
invoice for the given subscription at the specified interval.
- `ProrationBehavior`
  - Determines how to handle prorations when the
billing cycle changes (e.g., when switching plans, resetting
`billing_cycle_anchor=now`, or starting a trial), or if an item's `quantity`
changes. The default value is `create_prorations`.
One of: `always_invoice`, `create_prorations`, or `none`.
- `ProrationDate`
  - If set, prorations will be calculated as though the subscription was updated at the
given time. This can be used to apply exactly the same prorations that were previewed
with the create
preview endpoint. `proration_date` can also be used to implement custom
proration logic, such as prorating by day instead of by second, by providing the time
that you wish to use for proration calculations.
- `TransferData`
  - If specified, the funds from the subscription's invoices will be transferred to the
destination and the ID of the resulting transfers will be found on the resulting
charges. This will be unset if you POST an empty value.
- `TrialEnd`
  - Unix timestamp representing the end of the trial period the customer will get before
being charged for the first time. This will always overwrite any trials that might apply
via a subscribed plan. If set, `trial_end` will override the default trial period
of the plan the customer is being subscribed to. The `billing_cycle_anchor` will be
updated to the `trial_end` value. The special value `now` can be provided to
end the customer's trial immediately. Can be at most two years from
`billing_cycle_anchor`.
- `TrialFromPlan`
  - Indicates if a plan's `trial_period_days` should be applied to the subscription.
Setting `trial_end` per subscription is preferred, and this defaults to
`false`. Setting this flag to `true` together with `trial_end` is not
allowed. See Using trial
periods on subscriptions to learn more.
- `TrialSettings`
  - Settings related to subscription trials.


#### `SubscriptionListOptions`

**Properties:**

- `AutomaticTax`
  - Filter subscriptions by their automatic tax settings.
- `CollectionMethod`
  - The collection method of the subscriptions to retrieve. Either
`charge_automatically` or `send_invoice`.
One of: `charge_automatically`, or `send_invoice`.
- `Created`
  - Only return subscriptions that were created during the given date interval.
- `CurrentPeriodEnd`
  - Only return subscriptions whose minimum item current_period_end falls within the given
date interval.
- `CurrentPeriodStart`
  - Only return subscriptions whose maximum item current_period_start falls within the given
date interval.
- `Customer`
  - The ID of the customer whose subscriptions you're retrieving.
- `CustomerAccount`
  - The ID of the account representing the customer whose subscriptions you're retrieving.
- `Plan`
  - The ID of the plan whose subscriptions will be retrieved.
- `Price`
  - Filter for subscriptions that contain this recurring price ID.
- `Status`
  - The status of the subscriptions to retrieve. Passing in a value of `canceled` will
return all canceled subscriptions, including those belonging to deleted customers. Pass
`ended` to find subscriptions that are canceled and subscriptions that are expired
due to incomplete
payment. Passing in a value of `all` will return subscriptions of all statuses.
If no value is supplied, all subscriptions that have not been canceled are returned.
One of: `active`, `all`, `canceled`, `ended`, `incomplete`,
`incomplete_expired`, `past_due`, `paused`, `trialing`, or
`unpaid`.
- `TestClock`
  - Filter for subscriptions that are associated with the specified test clock. The response
will not include subscriptions with test clocks if this and the customer parameter is
not set.


#### `SubscriptionCancelOptions`

**Properties:**

- `CancellationDetails`
  - Details about why this subscription was cancelled.
- `InvoiceNow`
  - Will generate a final invoice that invoices for any un-invoiced metered usage and
new/pending proration invoice items. Defaults to `false`.
- `Prorate`
  - Will generate a proration invoice item that credits remaining unused time until the
subscription period end. Defaults to `false`.


### SubscriptionItem

#### `SubscriptionItem`

Subscription items allow you to create customer subscriptions with more than one plan,
making it easy to represent complex billing relationships.

**Properties:**

- `BilledUntil`
  - The time period the subscription item has been billed for.
- `BillingThresholds`
  - Define thresholds at which an invoice will be sent, and the related subscription
advanced to a new billing period.
- `Created`
  - Time at which the object was created. Measured in seconds since the Unix epoch.
- `CurrentPeriodEnd`
  - The end time of this subscription item's current billing period.
- `CurrentPeriodStart`
  - The start time of this subscription item's current billing period.
- `Deleted`
  - Whether this object is deleted or not.
- `DiscountIds`
  - (IDs of the Discounts)
The discounts applied to the subscription item. Subscription item discounts are applied
before subscription discounts. Use `expand[]=discounts` to expand each discount.
- `Discounts`
  - (Expanded)
The discounts applied to the subscription item. Subscription item discounts are applied
before subscription discounts. Use `expand[]=discounts` to expand each discount.

For more information, see the expand documentation.
- `Id`
  - Unique identifier for the object.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format.
- `Object`
  - String representing the object's type. Objects of the same type share the same value.
- `Plan`
  - You can now model subscriptions more flexibly using the Prices API. It replaces the Plans API and is
backwards compatible to simplify your migration.

Plans define the base price, currency, and billing cycle for recurring purchases of
products. Products help you track
inventory or provisioning, and plans help you track pricing. Different physical goods or
levels of service should be represented by products, and pricing options should be
represented by plans. This approach lets you change prices without having to change your
provisioning scheme.

For example, you might have a single "gold" product that has plans for $10/month,
$100/year, €9/month, and €90/year.

Related guides: Set up a
subscription and more about products and prices.
- `Price`
  - Prices define the unit cost, currency, and (optional) billing cycle for both recurring
and one-time purchases of products. Products help you track inventory or
provisioning, and prices help you track payment terms. Different physical goods or
levels of service should be represented by products, and pricing options should be
represented by prices. This approach lets you change prices without having to change
your provisioning scheme.

For example, you might have a single "gold" product that has prices for $10/month,
$100/year, and €9 once.

Related guides: Set up a
subscription, create an
invoice, and more about products and prices.
- `Quantity`
  - The quantity of the plan
to which the customer should be subscribed.
- `Subscription`
  - The `subscription` this `subscription_item` belongs to.
- `TaxRates`
  - The tax rates which apply to this `subscription_item`. When set, the
`default_tax_rates` on the subscription do not apply to this
`subscription_item`.


#### `SubscriptionItemService`

**Methods:**

- `Create(Stripe.SubscriptionItemCreateOptions, Stripe.RequestOptions)`
  - Adds a new item to an existing subscription. No existing items will be changed or
replaced..
- `CreateAsync(Stripe.SubscriptionItemCreateOptions, Stripe.RequestOptions, CancellationToken)`
  - Adds a new item to an existing subscription. No existing items will be changed or
replaced..
- `Delete(string, Stripe.SubscriptionItemDeleteOptions, Stripe.RequestOptions)`
  - Deletes an item from the subscription. Removing a subscription item from a
subscription will not cancel the subscription..
- `DeleteAsync(string, Stripe.SubscriptionItemDeleteOptions, Stripe.RequestOptions, CancellationToken)`
  - Deletes an item from the subscription. Removing a subscription item from a
subscription will not cancel the subscription..
- `Get(string, Stripe.SubscriptionItemGetOptions, Stripe.RequestOptions)`
  - Retrieves the subscription item with the given ID..
- `GetAsync(string, Stripe.SubscriptionItemGetOptions, Stripe.RequestOptions, CancellationToken)`
  - Retrieves the subscription item with the given ID..
- `List(Stripe.SubscriptionItemListOptions, Stripe.RequestOptions)`
  - Returns a list of your subscription items for a given subscription..
- `ListAsync(Stripe.SubscriptionItemListOptions, Stripe.RequestOptions, CancellationToken)`
  - Returns a list of your subscription items for a given subscription..
- `ListAutoPaging(Stripe.SubscriptionItemListOptions, Stripe.RequestOptions)`
  - Returns a list of your subscription items for a given subscription..
- `ListAutoPagingAsync(Stripe.SubscriptionItemListOptions, Stripe.RequestOptions, CancellationToken)`
  - Returns a list of your subscription items for a given subscription..
- `Update(string, Stripe.SubscriptionItemUpdateOptions, Stripe.RequestOptions)`
  - Updates the plan or quantity of an item on a current subscription..
- `UpdateAsync(string, Stripe.SubscriptionItemUpdateOptions, Stripe.RequestOptions, CancellationToken)`
  - Updates the plan or quantity of an item on a current subscription..


#### `SubscriptionItemCreateOptions`

**Properties:**

- `BillingThresholds`
  - Define thresholds at which an invoice will be sent, and the subscription advanced to a
new billing period. Pass an empty string to remove previously-defined thresholds.
- `Discounts`
  - The coupons to redeem into discounts for the subscription item.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format. Individual keys can be unset by posting an empty value to
them. All keys can be unset by posting an empty value to `metadata`.
- `PaymentBehavior`
  - Controls how Stripe handles payment when a subscription update requires payment and
`collection_method=charge_automatically`.
One of: `allow_incomplete`, `default_incomplete`, `error_if_incomplete`,
or `pending_if_incomplete`.
- `Plan`
  - The identifier of the plan to add to the subscription.
- `Price`
  - The ID of the price object.
- `PriceData`
  - Data used to generate a new Price
object inline.
- `ProrationBehavior`
  - Determines how to handle prorations when the
billing cycle changes (e.g., when switching plans, resetting
`billing_cycle_anchor=now`, or starting a trial), or if an item's `quantity`
changes. The default value is `create_prorations`.
One of: `always_invoice`, `create_prorations`, or `none`.
- `ProrationDate`
  - If set, the proration will be calculated as though the subscription was updated at the
given time. This can be used to apply the same proration that was previewed with the upcoming invoice endpoint.
- `Quantity`
  - The quantity you'd like to apply to the subscription item you're creating.
- `Subscription`
  - The identifier of the subscription to modify.
- `TaxRates`
  - A list of Tax Rate ids. These Tax
Rates will override the `default_tax_rates`
on the Subscription. When updating, pass an empty string to remove previously-defined
tax rates.


#### `SubscriptionItemUpdateOptions`

**Properties:**

- `BillingThresholds`
  - Define thresholds at which an invoice will be sent, and the subscription advanced to a
new billing period. Pass an empty string to remove previously-defined thresholds.
- `Discounts`
  - The coupons to redeem into discounts for the subscription item.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format. Individual keys can be unset by posting an empty value to
them. All keys can be unset by posting an empty value to `metadata`.
- `OffSession`
  - Indicates if a customer is on or off-session while an invoice payment is attempted.
Defaults to `false` (on-session).
- `PaymentBehavior`
  - Controls how Stripe handles payment when a subscription update requires payment and
`collection_method=charge_automatically`.
One of: `allow_incomplete`, `default_incomplete`, `error_if_incomplete`,
or `pending_if_incomplete`.
- `Plan`
  - The identifier of the new plan for this subscription item.
- `Price`
  - The ID of the price object. One of `price` or `price_data` is required. When
changing a subscription item's price, `quantity` is set to 1 unless a
`quantity` parameter is provided.
- `PriceData`
  - Data used to generate a new Price
object inline. One of `price` or `price_data` is required.
- `ProrationBehavior`
  - Determines how to handle prorations when the
billing cycle changes (e.g., when switching plans, resetting
`billing_cycle_anchor=now`, or starting a trial), or if an item's `quantity`
changes. The default value is `create_prorations`.
One of: `always_invoice`, `create_prorations`, or `none`.
- `ProrationDate`
  - If set, the proration will be calculated as though the subscription was updated at the
given time. This can be used to apply the same proration that was previewed with the upcoming invoice endpoint.
- `Quantity`
  - The quantity you'd like to apply to the subscription item you're creating.
- `TaxRates`
  - A list of Tax Rate ids. These Tax
Rates will override the `default_tax_rates`
on the Subscription. When updating, pass an empty string to remove previously-defined
tax rates.


#### `SubscriptionItemListOptions`

**Properties:**

- `Subscription`
  - The ID of the subscription whose items will be retrieved.


#### `SubscriptionItemDeleteOptions`

**Properties:**

- `ClearUsage`
  - Delete all usage for the given subscription item. Allowed only when the current plan's
`usage_type` is `metered`.
- `PaymentBehavior`
  - Controls how Stripe handles payment when a subscription update requires payment and
`collection_method=charge_automatically`.
One of: `allow_incomplete`, `default_incomplete`, `error_if_incomplete`,
or `pending_if_incomplete`.
- `ProrationBehavior`
  - Determines how to handle prorations when the
billing cycle changes (e.g., when switching plans, resetting
`billing_cycle_anchor=now`, or starting a trial), or if an item's `quantity`
changes. The default value is `create_prorations`.
One of: `always_invoice`, `create_prorations`, or `none`.
- `ProrationDate`
  - If set, the proration will be calculated as though the subscription was updated at the
given time. This can be used to apply the same proration that was previewed with the upcoming invoice endpoint.


### Invoice

#### `Invoice`

Invoices are statements of amounts owed by a customer, and are either generated one-off,
or generated periodically from a subscription.

They contain invoice items, and
proration adjustments that may be caused by subscription upgrades/downgrades (if
necessary).

If your invoice is configured to be billed through automatic charges, Stripe
automatically finalizes your invoice and attempts payment. Note that finalizing the
invoice, when
automatic, does not happen immediately as the invoice is created. Stripe waits until
one hour after the last webhook was successfully sent (or the last webhook timed out
after failing). If you (and the platforms you may have connected to) have no webhooks
configured, Stripe waits one hour after creation to finalize the invoice.

If your invoice is configured to be billed by sending an email, then based on your email settings, Stripe
will email the invoice to your customer and await payment. These emails can contain a
link to a hosted page to pay the invoice.

Stripe applies any customer credit on the account before determining the amount due for
the invoice (i.e., the amount that will be actually charged). If the amount due for the
invoice is less than Stripe's minimum
allowed charge per currency, the invoice is automatically marked paid, and we add
the amount due to the customer's credit balance which is applied to the next invoice.

More details on the customer's credit balance are here.

Related guide: Send invoices
to customers.

**Properties:**

- `AccountCountry`
  - The country of the business associated with this invoice, most often the business
creating the invoice.
- `AccountName`
  - The public name of the business associated with this invoice, most often the business
creating the invoice.
- `AccountTaxIdIds`
  - (IDs of the AccountTaxIds)
The account tax IDs associated with the invoice. Only editable when the invoice is a
draft.
- `AccountTaxIds`
  - (Expanded)
The account tax IDs associated with the invoice. Only editable when the invoice is a
draft.

For more information, see the expand documentation.
- `AmountDue`
  - Final amount due at this time for this invoice. If the invoice's total is smaller than
the minimum charge amount, for example, or if there is account credit that can be
applied to the invoice, the `amount_due` may be 0. If there is a positive
`starting_balance` for the invoice (the customer owes money), the `amount_due`
will also take that into account. The charge that gets generated for the invoice will be
for the amount specified in `amount_due`.
- `AmountOverpaid`
  - Amount that was overpaid on the invoice. The amount overpaid is credited to the
customer's credit balance.
- `AmountPaid`
  - The amount, in cents (or local equivalent), that was paid.
- `AmountPaidOffStripe`
  - Amount, in cents (or local equivalent), that was paid on the invoice outside of Stripe.
- `AmountRemaining`
  - The difference between amount_due and amount_paid, in cents (or local equivalent).
- `AmountShipping`
  - This is the sum of all the shipping amounts.
- `Application`
  - (Expanded)
ID of the Connect Application that created the invoice.

For more information, see the expand documentation.
- `ApplicationId`
  - (ID of the Application)
ID of the Connect Application that created the invoice.
- `AttemptCount`
  - Number of payment attempts made for this invoice, from the perspective of the payment
retry schedule. Any payment attempt counts as the first attempt, and subsequently only
automatic retries increment the attempt count. In other words, manual payment attempts
after the first attempt do not affect the retry schedule. If a failure is returned with
a non-retryable return code, the invoice can no longer be retried unless a new payment
method is obtained. Retries will continue to be scheduled, and attempt_count will
continue to increment, but retries will only be executed if a new payment method is
obtained.
- `Attempted`
  - Whether an attempt has been made to pay the invoice. An invoice is not attempted until 1
hour after the `invoice.created` webhook, for example, so you might not want to
display that invoice as unpaid to your users.
- `AutoAdvance`
  - Controls whether Stripe performs automatic
collection of the invoice. If `false`, the invoice's state doesn't
automatically advance without an explicit action.
- `AutomaticallyFinalizesAt`
  - The time when this invoice is currently scheduled to be automatically finalized. The
field will be `null` if the invoice is not scheduled to finalize in the future. If
the invoice is not in the draft state, this field will always be `null` - see
`finalized_at` for the time when an already-finalized invoice was finalized.
- `BillingReason`
  - Indicates the reason why the invoice was created.

* `manual`: Unrelated to a subscription, for example, created via the invoice
editor. * `subscription`: No longer in use. Applies to subscriptions from before
May 2018 where no distinction was made between updates, cycles, and thresholds. *
`subscription_create`: A new subscription was created. * `subscription_cycle`:
A subscription advanced into a new period. * `subscription_threshold`: A
subscription reached a billing threshold. * `subscription_update`: A subscription
was updated. * `upcoming`: Reserved for upcoming invoices created through the
Create Preview Invoice API or when an `invoice.upcoming` event is generated for an
upcoming invoice on a subscription.
One of: `automatic_pending_invoice_item_invoice`, `manual`,
`quote_accept`, `subscription`, `subscription_create`,
`subscription_cycle`, `subscription_threshold`, `subscription_update`, or
`upcoming`.
- `CollectionMethod`
  - Either `charge_automatically`, or `send_invoice`. When charging automatically,
Stripe will attempt to pay this invoice using the default source attached to the
customer. When sending an invoice, Stripe will email this invoice to the customer with
payment instructions.
One of: `charge_automatically`, or `send_invoice`.
- `ConfirmationSecret`
  - The confirmation secret associated with this invoice. Currently, this contains the
client_secret of the PaymentIntent that Stripe creates during invoice finalization.
- `Created`
  - Time at which the object was created. Measured in seconds since the Unix epoch.
- `Currency`
  - Three-letter ISO currency
code, in lowercase. Must be a supported
currency.
- `CustomFields`
  - Custom fields displayed on the invoice.
- `Customer`
  - (Expanded)
The ID of the customer to bill.

For more information, see the expand documentation.
- `CustomerAccount`
  - The ID of the account representing the customer to bill.
- `CustomerAddress`
  - The customer's address. Until the invoice is finalized, this field will equal
`customer.address`. Once the invoice is finalized, this field will no longer be
updated.
- `CustomerEmail`
  - The customer's email. Until the invoice is finalized, this field will equal
`customer.email`. Once the invoice is finalized, this field will no longer be
updated.
- `CustomerId`
  - (ID of the Customer)
The ID of the customer to bill.
- `CustomerName`
  - The customer's name. Until the invoice is finalized, this field will equal
`customer.name`. Once the invoice is finalized, this field will no longer be
updated.
- `CustomerPhone`
  - The customer's phone number. Until the invoice is finalized, this field will equal
`customer.phone`. Once the invoice is finalized, this field will no longer be
updated.
- `CustomerShipping`
  - The customer's shipping information. Until the invoice is finalized, this field will
equal `customer.shipping`. Once the invoice is finalized, this field will no longer
be updated.
- `CustomerTaxExempt`
  - The customer's tax exempt status. Until the invoice is finalized, this field will equal
`customer.tax_exempt`. Once the invoice is finalized, this field will no longer be
updated.
One of: `exempt`, `none`, or `reverse`.
- `CustomerTaxIds`
  - The customer's tax IDs. Until the invoice is finalized, this field will contain the same
tax IDs as `customer.tax_ids`. Once the invoice is finalized, this field will no
longer be updated.
- `DefaultPaymentMethod`
  - (Expanded)
ID of the default payment method for the invoice. It must belong to the customer
associated with the invoice. If not set, defaults to the subscription's default payment
method, if any, or to the default payment method in the customer's invoice settings.

For more information, see the expand documentation.
- `DefaultPaymentMethodId`
  - (ID of the PaymentMethod)
ID of the default payment method for the invoice. It must belong to the customer
associated with the invoice. If not set, defaults to the subscription's default payment
method, if any, or to the default payment method in the customer's invoice settings.
- `DefaultSource`
  - (Expanded)
ID of the default payment source for the invoice. It must belong to the customer
associated with the invoice and be in a chargeable state. If not set, defaults to the
subscription's default source, if any, or to the customer's default source.

For more information, see the expand documentation.
- `DefaultSourceId`
  - (ID of the IPaymentSource)
ID of the default payment source for the invoice. It must belong to the customer
associated with the invoice and be in a chargeable state. If not set, defaults to the
subscription's default source, if any, or to the customer's default source.
- `DefaultTaxRates`
  - The tax rates applied to this invoice, if any.
- `Deleted`
  - Whether this object is deleted or not.
- `Description`
  - An arbitrary string attached to the object. Often useful for displaying to users.
Referenced as 'memo' in the Dashboard.
- `DiscountIds`
  - (IDs of the Discounts)
The discounts applied to the invoice. Line item discounts are applied before invoice
discounts. Use `expand[]=discounts` to expand each discount.
- `Discounts`
  - (Expanded)
The discounts applied to the invoice. Line item discounts are applied before invoice
discounts. Use `expand[]=discounts` to expand each discount.

For more information, see the expand documentation.
- `DueDate`
  - The date on which payment for this invoice is due. This value will be `null` for
invoices where `collection_method=charge_automatically`.
- `EffectiveAt`
  - The date when this invoice is in effect. Same as `finalized_at` unless overwritten.
When defined, this value replaces the system-generated 'Date of issue' printed on the
invoice PDF and receipt.
- `EndingBalance`
  - Ending customer balance after the invoice is finalized. Invoices are finalized
approximately an hour after successful webhook delivery or when payment collection is
attempted for the invoice. If the invoice has not been finalized yet, this will be null.
- `Footer`
  - Footer displayed on the invoice.
- `FromInvoice`
  - Details of the invoice that was cloned. See the revision documentation
for more details.
- `HostedInvoiceUrl`
  - The URL for the hosted invoice page, which allows customers to view and pay an invoice.
If the invoice has not been finalized yet, this will be null.
- `Id`
  - Unique identifier for the object. For preview invoices created using the create preview endpoint,
this id will be prefixed with `upcoming_in`.
- `InvoicePdf`
  - The link to download the PDF for the invoice. If the invoice has not been finalized yet,
this will be null.
- `LastFinalizationError`
  - The error encountered during the previous attempt to finalize the invoice. This field is
cleared when the invoice is successfully finalized.
- `LatestRevision`
  - (Expanded)
The ID of the most recent non-draft revision of this invoice.

For more information, see the expand documentation.
- `LatestRevisionId`
  - (ID of the Invoice)
The ID of the most recent non-draft revision of this invoice.
- `Lines`
  - The individual line items that make up the invoice. `lines` is sorted as follows:
(1) pending invoice items (including prorations) in reverse chronological order, (2)
subscription items in reverse chronological order, and (3) invoice items added after
invoice creation in chronological order.
- `Livemode`
  - If the object exists in live mode, the value is `true`. If the object exists in
test mode, the value is `false`.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format.
- `NextPaymentAttempt`
  - The time at which payment will next be attempted. This value will be `null` for
invoices where `collection_method=send_invoice`.
- `Number`
  - A unique, identifying string that appears on emails sent to the customer for this
invoice. This starts with the customer's unique invoice_prefix if it is specified.
- `Object`
  - String representing the object's type. Objects of the same type share the same value.
- `OnBehalfOf`
  - (Expanded)
The account (if any) for which the funds of the invoice payment are intended. If set,
the invoice will be presented with the branding and support information of the specified
account. See the Invoices
with Connect documentation for details.

For more information, see the expand documentation.
- `OnBehalfOfId`
  - (ID of the Account)
The account (if any) for which the funds of the invoice payment are intended. If set,
the invoice will be presented with the branding and support information of the specified
account. See the Invoices
with Connect documentation for details.
- `Parent`
  - The parent that generated this invoice.
- `Payments`
  - Payments for this invoice. Use invoice
payment to get more details.
- `PeriodEnd`
  - The latest timestamp at which invoice items can be associated with this invoice. Use the
line
item period to get the service period for each price.
- `PeriodStart`
  - The earliest timestamp at which invoice items can be associated with this invoice. Use
the line
item period to get the service period for each price.
- `PostPaymentCreditNotesAmount`
  - Total amount of all post-payment credit notes issued for this invoice.
- `PrePaymentCreditNotesAmount`
  - Total amount of all pre-payment credit notes issued for this invoice.
- `ReceiptNumber`
  - This is the transaction number that appears on email receipts sent for this invoice.
- `Rendering`
  - The rendering-related settings that control how the invoice is displayed on
customer-facing surfaces such as PDF and Hosted Invoice Page.
- `ShippingCost`
  - The details of the cost of shipping, including the ShippingRate applied on the invoice.
- `ShippingDetails`
  - Shipping details for the invoice. The Invoice PDF will use the `shipping_details`
value if it is set, otherwise the PDF will render the shipping address from the
customer.
- `StartingBalance`
  - Starting customer balance before the invoice is finalized. If the invoice has not been
finalized yet, this will be the current customer balance. For revision invoices, this
also includes any customer balance that was applied to the original invoice.
- `StatementDescriptor`
  - Extra information about an invoice for the customer's credit card statement.
- `Status`
  - The status of the invoice, one of `draft`, `open`, `paid`,
`uncollectible`, or `void`. Learn
more.
One of: `draft`, `open`, `paid`, `uncollectible`, or `void`.
- `Subtotal`
  - Total of all subscriptions, invoice items, and prorations on the invoice before any
invoice level discount or exclusive tax is applied. Item discounts are already
incorporated.
- `SubtotalExcludingTax`
  - The integer amount in cents (or local equivalent) representing the subtotal of the
invoice before any invoice level discount or tax is applied. Item discounts are already
incorporated.
- `TestClock`
  - (Expanded)
ID of the test clock this invoice belongs to.

For more information, see the expand documentation.
- `TestClockId`
  - (ID of the TestHelpers.TestClock)
ID of the test clock this invoice belongs to.
- `Total`
  - Total after discounts and taxes.
- `TotalDiscountAmounts`
  - The aggregate amounts calculated per discount across all line items.
- `TotalExcludingTax`
  - The integer amount in cents (or local equivalent) representing the total amount of the
invoice including all discounts but excluding all tax.
- `TotalPretaxCreditAmounts`
  - Contains pretax credit amounts (ex: discount, credit grants, etc) that apply to this
invoice. This is a combined list of total_pretax_credit_amounts across all invoice line
items.
- `TotalTaxes`
  - The aggregate tax information of all line items.
- `WebhooksDeliveredAt`
  - Invoices are automatically paid or sent 1 hour after webhooks are delivered, or until
all webhook delivery attempts have been exhausted. This
field tracks the time when webhooks for this invoice were successfully delivered. If the
invoice had no webhooks to deliver, this will be set while the invoice is being created.


#### `InvoiceService`

**Methods:**

- `AddLines(string, Stripe.InvoiceAddLinesOptions, Stripe.RequestOptions)`
  - Adds multiple line items to an invoice. This is only possible when an invoice is
still a draft..
- `AddLinesAsync(string, Stripe.InvoiceAddLinesOptions, Stripe.RequestOptions, CancellationToken)`
  - Adds multiple line items to an invoice. This is only possible when an invoice is
still a draft..
- `AttachPayment(string, Stripe.InvoiceAttachPaymentOptions, Stripe.RequestOptions)`
  - Attaches a PaymentIntent or an Out of Band Payment to the invoice, adding it to the
list of `payments`..

For the PaymentIntent, when the PaymentIntent’s status changes to `succeeded`,
the payment is credited to the invoice, increasing its `amount_paid`. When the
invoice is fully paid, the invoice’s status becomes `paid`..

If the PaymentIntent’s status is already `succeeded` when it’s attached, it’s
credited to the invoice immediately..

See: Partial
payments to learn more..
- `AttachPaymentAsync(string, Stripe.InvoiceAttachPaymentOptions, Stripe.RequestOptions, CancellationToken)`
  - Attaches a PaymentIntent or an Out of Band Payment to the invoice, adding it to the
list of `payments`..

For the PaymentIntent, when the PaymentIntent’s status changes to `succeeded`,
the payment is credited to the invoice, increasing its `amount_paid`. When the
invoice is fully paid, the invoice’s status becomes `paid`..

If the PaymentIntent’s status is already `succeeded` when it’s attached, it’s
credited to the invoice immediately..

See: Partial
payments to learn more..
- `Create(Stripe.InvoiceCreateOptions, Stripe.RequestOptions)`
  - This endpoint creates a draft invoice for a given customer. The invoice remains a
draft until you finalize the
invoice, which allows you to pay or send the invoice to your customers..
- `CreateAsync(Stripe.InvoiceCreateOptions, Stripe.RequestOptions, CancellationToken)`
  - This endpoint creates a draft invoice for a given customer. The invoice remains a
draft until you finalize the
invoice, which allows you to pay or send the invoice to your customers..
- `CreatePreview(Stripe.InvoiceCreatePreviewOptions, Stripe.RequestOptions)`
  - At any time, you can preview the upcoming invoice for a subscription or subscription
schedule. This will show you all the charges that are pending, including subscription
renewal charges, invoice item charges, etc. It will also show you any discounts that are
applicable to the invoice..

You can also preview the effects of creating or updating a subscription or
subscription schedule, including a preview of any prorations that will take place. To
ensure that the actual proration is calculated exactly the same as the previewed
proration, you should pass the `subscription_details.proration_date` parameter when
doing the actual subscription update..

The recommended way to get only the prorations being previewed on the invoice is to
consider line items where `parent.subscription_item_details.proration` is
`true`..

Note that when you are viewing an upcoming invoice, you are simply viewing a preview
– the invoice has not yet been created. As such, the upcoming invoice will not show up
in invoice listing calls, and you cannot use the API to pay or edit the invoice. If you
want to change the amount that your customer will be billed, you can add, remove, or
update pending invoice items, or update the customer’s discount..

Note: Currency conversion calculations use the latest exchange rates. Exchange rates
may vary between the time of the preview and the time of the actual invoice creation. Learn more.
- `CreatePreviewAsync(Stripe.InvoiceCreatePreviewOptions, Stripe.RequestOptions, CancellationToken)`
  - At any time, you can preview the upcoming invoice for a subscription or subscription
schedule. This will show you all the charges that are pending, including subscription
renewal charges, invoice item charges, etc. It will also show you any discounts that are
applicable to the invoice..

You can also preview the effects of creating or updating a subscription or
subscription schedule, including a preview of any prorations that will take place. To
ensure that the actual proration is calculated exactly the same as the previewed
proration, you should pass the `subscription_details.proration_date` parameter when
doing the actual subscription update..

The recommended way to get only the prorations being previewed on the invoice is to
consider line items where `parent.subscription_item_details.proration` is
`true`..

Note that when you are viewing an upcoming invoice, you are simply viewing a preview
– the invoice has not yet been created. As such, the upcoming invoice will not show up
in invoice listing calls, and you cannot use the API to pay or edit the invoice. If you
want to change the amount that your customer will be billed, you can add, remove, or
update pending invoice items, or update the customer’s discount..

Note: Currency conversion calculations use the latest exchange rates. Exchange rates
may vary between the time of the preview and the time of the actual invoice creation. Learn more.
- `Delete(string, Stripe.InvoiceDeleteOptions, Stripe.RequestOptions)`
  - Permanently deletes a one-off invoice draft. This cannot be undone. Attempts to
delete invoices that are no longer in a draft state will fail; once an invoice has been
finalized or if an invoice is for a subscription, it must be voided..
- `DeleteAsync(string, Stripe.InvoiceDeleteOptions, Stripe.RequestOptions, CancellationToken)`
  - Permanently deletes a one-off invoice draft. This cannot be undone. Attempts to
delete invoices that are no longer in a draft state will fail; once an invoice has been
finalized or if an invoice is for a subscription, it must be voided..
- `FinalizeInvoice(string, Stripe.InvoiceFinalizeOptions, Stripe.RequestOptions)`
  - Stripe automatically finalizes drafts before sending and attempting payment on
invoices. However, if you’d like to finalize a draft invoice manually, you can do so
using this method..
- `FinalizeInvoiceAsync(string, Stripe.InvoiceFinalizeOptions, Stripe.RequestOptions, CancellationToken)`
  - Stripe automatically finalizes drafts before sending and attempting payment on
invoices. However, if you’d like to finalize a draft invoice manually, you can do so
using this method..
- `Get(string, Stripe.InvoiceGetOptions, Stripe.RequestOptions)`
  - Retrieves the invoice with the given ID..
- `GetAsync(string, Stripe.InvoiceGetOptions, Stripe.RequestOptions, CancellationToken)`
  - Retrieves the invoice with the given ID..
- `List(Stripe.InvoiceListOptions, Stripe.RequestOptions)`
  - You can list all invoices, or list the invoices for a specific customer. The invoices
are returned sorted by creation date, with the most recently created invoices appearing
first..
- `ListAsync(Stripe.InvoiceListOptions, Stripe.RequestOptions, CancellationToken)`
  - You can list all invoices, or list the invoices for a specific customer. The invoices
are returned sorted by creation date, with the most recently created invoices appearing
first..
- `ListAutoPaging(Stripe.InvoiceListOptions, Stripe.RequestOptions)`
  - You can list all invoices, or list the invoices for a specific customer. The invoices
are returned sorted by creation date, with the most recently created invoices appearing
first..
- `ListAutoPagingAsync(Stripe.InvoiceListOptions, Stripe.RequestOptions, CancellationToken)`
  - You can list all invoices, or list the invoices for a specific customer. The invoices
are returned sorted by creation date, with the most recently created invoices appearing
first..
- `ListLineItems(string, Stripe.InvoiceListLineItemsOptions, Stripe.RequestOptions)`
  - When retrieving an invoice, you’ll get a lines property containing
the total count of line items and the first handful of those items. There is also a URL
where you can retrieve the full (paginated) list of line items..
- `ListLineItemsAsync(string, Stripe.InvoiceListLineItemsOptions, Stripe.RequestOptions, CancellationToken)`
  - When retrieving an invoice, you’ll get a lines property containing
the total count of line items and the first handful of those items. There is also a URL
where you can retrieve the full (paginated) list of line items..
- `ListLineItemsAutoPaging(string, Stripe.InvoiceListLineItemsOptions, Stripe.RequestOptions)`
  - When retrieving an invoice, you’ll get a lines property containing
the total count of line items and the first handful of those items. There is also a URL
where you can retrieve the full (paginated) list of line items..
- `ListLineItemsAutoPagingAsync(string, Stripe.InvoiceListLineItemsOptions, Stripe.RequestOptions, CancellationToken)`
  - When retrieving an invoice, you’ll get a lines property containing
the total count of line items and the first handful of those items. There is also a URL
where you can retrieve the full (paginated) list of line items..
- `MarkUncollectible(string, Stripe.InvoiceMarkUncollectibleOptions, Stripe.RequestOptions)`
  - Marking an invoice as uncollectible is useful for keeping track of bad debts that can
be written off for accounting purposes..
- `MarkUncollectibleAsync(string, Stripe.InvoiceMarkUncollectibleOptions, Stripe.RequestOptions, CancellationToken)`
  - Marking an invoice as uncollectible is useful for keeping track of bad debts that can
be written off for accounting purposes..
- `Pay(string, Stripe.InvoicePayOptions, Stripe.RequestOptions)`
  - Stripe automatically creates and then attempts to collect payment on invoices for
customers on subscriptions according to your subscriptions
settings. However, if you’d like to attempt payment on an invoice out of the normal
collection schedule or for some other reason, you can do so..
- `PayAsync(string, Stripe.InvoicePayOptions, Stripe.RequestOptions, CancellationToken)`
  - Stripe automatically creates and then attempts to collect payment on invoices for
customers on subscriptions according to your subscriptions
settings. However, if you’d like to attempt payment on an invoice out of the normal
collection schedule or for some other reason, you can do so..
- `RemoveLines(string, Stripe.InvoiceRemoveLinesOptions, Stripe.RequestOptions)`
  - Removes multiple line items from an invoice. This is only possible when an invoice is
still a draft..
- `RemoveLinesAsync(string, Stripe.InvoiceRemoveLinesOptions, Stripe.RequestOptions, CancellationToken)`
  - Removes multiple line items from an invoice. This is only possible when an invoice is
still a draft..
- `Search(Stripe.InvoiceSearchOptions, Stripe.RequestOptions)`
  - Search for invoices you’ve previously created using Stripe’s Search Query Language.
Don’t use search in read-after-write flows where strict consistency is necessary. Under
normal operating conditions, data is searchable in less than a minute. Occasionally,
propagation of new or updated data can be up to an hour behind during outages. Search
functionality is not available to merchants in India..
- `SearchAsync(Stripe.InvoiceSearchOptions, Stripe.RequestOptions, CancellationToken)`
  - Search for invoices you’ve previously created using Stripe’s Search Query Language.
Don’t use search in read-after-write flows where strict consistency is necessary. Under
normal operating conditions, data is searchable in less than a minute. Occasionally,
propagation of new or updated data can be up to an hour behind during outages. Search
functionality is not available to merchants in India..
- `SearchAutoPaging(Stripe.InvoiceSearchOptions, Stripe.RequestOptions)`
  - Search for invoices you’ve previously created using Stripe’s Search Query Language.
Don’t use search in read-after-write flows where strict consistency is necessary. Under
normal operating conditions, data is searchable in less than a minute. Occasionally,
propagation of new or updated data can be up to an hour behind during outages. Search
functionality is not available to merchants in India..
- `SearchAutoPagingAsync(Stripe.InvoiceSearchOptions, Stripe.RequestOptions, CancellationToken)`
  - Search for invoices you’ve previously created using Stripe’s Search Query Language.
Don’t use search in read-after-write flows where strict consistency is necessary. Under
normal operating conditions, data is searchable in less than a minute. Occasionally,
propagation of new or updated data can be up to an hour behind during outages. Search
functionality is not available to merchants in India..
- `SendInvoice(string, Stripe.InvoiceSendOptions, Stripe.RequestOptions)`
  - Stripe will automatically send invoices to customers according to your subscriptions
settings. However, if you’d like to manually send an invoice to your customer out of
the normal schedule, you can do so. When sending invoices that have already been paid,
there will be no reference to the payment in the email..

Requests made in test-mode result in no emails being sent, despite sending an
`invoice.sent` event..
- `SendInvoiceAsync(string, Stripe.InvoiceSendOptions, Stripe.RequestOptions, CancellationToken)`
  - Stripe will automatically send invoices to customers according to your subscriptions
settings. However, if you’d like to manually send an invoice to your customer out of
the normal schedule, you can do so. When sending invoices that have already been paid,
there will be no reference to the payment in the email..

Requests made in test-mode result in no emails being sent, despite sending an
`invoice.sent` event..
- `Update(string, Stripe.InvoiceUpdateOptions, Stripe.RequestOptions)`
  - Draft invoices are fully editable. Once an invoice is finalized,
monetary values, as well as `collection_method`, become uneditable..

If you would like to stop the Stripe Billing engine from automatically finalizing,
reattempting payments on, sending reminders for, or automatically
reconciling invoices, pass `auto_advance=false`..
- `UpdateAsync(string, Stripe.InvoiceUpdateOptions, Stripe.RequestOptions, CancellationToken)`
  - Draft invoices are fully editable. Once an invoice is finalized,
monetary values, as well as `collection_method`, become uneditable..

If you would like to stop the Stripe Billing engine from automatically finalizing,
reattempting payments on, sending reminders for, or automatically
reconciling invoices, pass `auto_advance=false`..
- `UpdateLines(string, Stripe.InvoiceUpdateLinesOptions, Stripe.RequestOptions)`
  - Updates multiple line items on an invoice. This is only possible when an invoice is
still a draft..
- `UpdateLines(string, string, Stripe.InvoiceUpdateInvoiceLineItemsOptions, Stripe.RequestOptions)`
  - Updates an invoice’s line item. Some fields, such as `tax_amounts`, only live on
the invoice line item, so they can only be updated through this endpoint. Other fields,
such as `amount`, live on both the invoice item and the invoice line item, so
updates on this endpoint will propagate to the invoice item as well. Updating an
invoice’s line item is only possible before the invoice is finalized..
- `UpdateLinesAsync(string, Stripe.InvoiceUpdateLinesOptions, Stripe.RequestOptions, CancellationToken)`
  - Updates multiple line items on an invoice. This is only possible when an invoice is
still a draft..
- `UpdateLinesAsync(string, string, Stripe.InvoiceUpdateInvoiceLineItemsOptions, Stripe.RequestOptions, CancellationToken)`
  - Updates an invoice’s line item. Some fields, such as `tax_amounts`, only live on
the invoice line item, so they can only be updated through this endpoint. Other fields,
such as `amount`, live on both the invoice item and the invoice line item, so
updates on this endpoint will propagate to the invoice item as well. Updating an
invoice’s line item is only possible before the invoice is finalized..
- `VoidInvoice(string, Stripe.InvoiceVoidOptions, Stripe.RequestOptions)`
  - Mark a finalized invoice as void. This cannot be undone. Voiding an invoice is
similar to deletion, however it
only applies to finalized invoices and maintains a papertrail where the invoice can
still be found..

Consult with local regulations to determine whether and how an invoice might be
amended, canceled, or voided in the jurisdiction you’re doing business in. You might
need to issue another invoice or credit note instead. Stripe
recommends that you consult with your legal counsel for advice specific to your
business..
- `VoidInvoiceAsync(string, Stripe.InvoiceVoidOptions, Stripe.RequestOptions, CancellationToken)`
  - Mark a finalized invoice as void. This cannot be undone. Voiding an invoice is
similar to deletion, however it
only applies to finalized invoices and maintains a papertrail where the invoice can
still be found..

Consult with local regulations to determine whether and how an invoice might be
amended, canceled, or voided in the jurisdiction you’re doing business in. You might
need to issue another invoice or credit note instead. Stripe
recommends that you consult with your legal counsel for advice specific to your
business..


#### `InvoiceCreateOptions`

**Properties:**

- `AccountTaxIds`
  - The account tax IDs associated with the invoice. Only editable when the invoice is a
draft.
- `ApplicationFeeAmount`
  - A fee in cents (or local equivalent) that will be applied to the invoice and transferred
to the application owner's Stripe account. The request must be made with an OAuth key or
the Stripe-Account header in order to take an application fee. For more information, see
the application fees documentation.
- `AutoAdvance`
  - Controls whether Stripe performs automatic
collection of the invoice. If `false`, the invoice's state doesn't
automatically advance without an explicit action. Defaults to false.
- `AutomaticTax`
  - Settings for automatic tax lookup for this invoice.
- `AutomaticallyFinalizesAt`
  - The time when this invoice should be scheduled to finalize (up to 5 years in the
future). The invoice is finalized at this time if it's still in draft state.
- `CollectionMethod`
  - Either `charge_automatically`, or `send_invoice`. When charging automatically,
Stripe will attempt to pay this invoice using the default source attached to the
customer. When sending an invoice, Stripe will email this invoice to the customer with
payment instructions. Defaults to `charge_automatically`.
One of: `charge_automatically`, or `send_invoice`.
- `Currency`
  - The currency to create this invoice in. Defaults to that of `customer` if not
specified.
- `CustomFields`
  - A list of up to 4 custom fields to be displayed on the invoice.
- `Customer`
  - The ID of the customer to bill.
- `CustomerAccount`
  - The ID of the account to bill.
- `DaysUntilDue`
  - The number of days from when the invoice is created until it is due. Valid only for
invoices where `collection_method=send_invoice`.
- `DefaultPaymentMethod`
  - ID of the default payment method for the invoice. It must belong to the customer
associated with the invoice. If not set, defaults to the subscription's default payment
method, if any, or to the default payment method in the customer's invoice settings.
- `DefaultSource`
  - ID of the default payment source for the invoice. It must belong to the customer
associated with the invoice and be in a chargeable state. If not set, defaults to the
subscription's default source, if any, or to the customer's default source.
- `DefaultTaxRates`
  - The tax rates that will apply to any line item that does not have `tax_rates` set.
- `Description`
  - An arbitrary string attached to the object. Often useful for displaying to users.
Referenced as 'memo' in the Dashboard.
- `Discounts`
  - The coupons and promotion codes to redeem into discounts for the invoice. If not
specified, inherits the discount from the invoice's customer. Pass an empty string to
avoid inheriting any discounts.
- `DueDate`
  - The date on which payment for this invoice is due. Valid only for invoices where
`collection_method=send_invoice`.
- `EffectiveAt`
  - The date when this invoice is in effect. Same as `finalized_at` unless overwritten.
When defined, this value replaces the system-generated 'Date of issue' printed on the
invoice PDF and receipt.
- `Footer`
  - Footer to be displayed on the invoice.
- `FromInvoice`
  - Revise an existing invoice. The new invoice will be created in `status=draft`. See
the revision
documentation for more details.
- `Issuer`
  - The connected account that issues the invoice. The invoice is presented with the
branding and support information of the specified account.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format. Individual keys can be unset by posting an empty value to
them. All keys can be unset by posting an empty value to `metadata`.
- `Number`
  - Set the number for this invoice. If no number is present then a number will be assigned
automatically when the invoice is finalized. In many markets, regulations require
invoices to be unique, sequential and / or gapless. You are responsible for ensuring
this is true across all your different invoicing systems in the event that you edit the
invoice number using our API. If you use only Stripe for your invoices and do not change
invoice numbers, Stripe handles this aspect of compliance for you automatically.
- `OnBehalfOf`
  - The account (if any) for which the funds of the invoice payment are intended. If set,
the invoice will be presented with the branding and support information of the specified
account. See the Invoices
with Connect documentation for details.
- `PaymentSettings`
  - Configuration settings for the PaymentIntent that is generated when the invoice is
finalized.
- `PendingInvoiceItemsBehavior`
  - How to handle pending invoice items on invoice creation. Defaults to `exclude` if
the parameter is omitted.
One of: `exclude`, or `include`.
- `Rendering`
  - The rendering-related settings that control how the invoice is displayed on
customer-facing surfaces such as PDF and Hosted Invoice Page.
- `ShippingCost`
  - Settings for the cost of shipping for this invoice.
- `ShippingDetails`
  - Shipping details for the invoice. The Invoice PDF will use the `shipping_details`
value if it is set, otherwise the PDF will render the shipping address from the
customer.
- `StatementDescriptor`
  - Extra information about a charge for the customer's credit card statement. It must
contain at least one letter. If not specified and this invoice is part of a
subscription, the default `statement_descriptor` will be set to the first
subscription item's product's `statement_descriptor`.
- `Subscription`
  - The ID of the subscription to invoice, if any. If set, the created invoice will only
include pending invoice items for that subscription. The subscription's billing cycle
and regular subscription events won't be affected.
- `TransferData`
  - If specified, the funds from the invoice will be transferred to the destination and the
ID of the resulting transfer will be found on the invoice's charge.


#### `InvoiceUpdateOptions`

**Properties:**

- `AccountTaxIds`
  - The account tax IDs associated with the invoice. Only editable when the invoice is a
draft.
- `ApplicationFeeAmount`
  - A fee in cents (or local equivalent) that will be applied to the invoice and transferred
to the application owner's Stripe account. The request must be made with an OAuth key or
the Stripe-Account header in order to take an application fee. For more information, see
the application fees documentation.
- `AutoAdvance`
  - Controls whether Stripe performs automatic
collection of the invoice.
- `AutomaticTax`
  - Settings for automatic tax lookup for this invoice.
- `AutomaticallyFinalizesAt`
  - The time when this invoice should be scheduled to finalize (up to 5 years in the
future). The invoice is finalized at this time if it's still in draft state. To turn off
automatic finalization, set `auto_advance` to false.
- `CollectionMethod`
  - Either `charge_automatically` or `send_invoice`. This field can be updated
only on `draft` invoices.
One of: `charge_automatically`, or `send_invoice`.
- `CustomFields`
  - A list of up to 4 custom fields to be displayed on the invoice. If a value for
`custom_fields` is specified, the list specified will replace the existing custom
field list on this invoice. Pass an empty string to remove previously-defined fields.
- `DaysUntilDue`
  - The number of days from which the invoice is created until it is due. Only valid for
invoices where `collection_method=send_invoice`. This field can only be updated on
`draft` invoices.
- `DefaultPaymentMethod`
  - ID of the default payment method for the invoice. It must belong to the customer
associated with the invoice. If not set, defaults to the subscription's default payment
method, if any, or to the default payment method in the customer's invoice settings.
- `DefaultSource`
  - ID of the default payment source for the invoice. It must belong to the customer
associated with the invoice and be in a chargeable state. If not set, defaults to the
subscription's default source, if any, or to the customer's default source.
- `DefaultTaxRates`
  - The tax rates that will apply to any line item that does not have `tax_rates` set.
Pass an empty string to remove previously-defined tax rates.
- `Description`
  - An arbitrary string attached to the object. Often useful for displaying to users.
Referenced as 'memo' in the Dashboard.
- `Discounts`
  - The discounts that will apply to the invoice. Pass an empty string to remove
previously-defined discounts.
- `DueDate`
  - The date on which payment for this invoice is due. Only valid for invoices where
`collection_method=send_invoice`. This field can only be updated on `draft`
invoices.
- `EffectiveAt`
  - The date when this invoice is in effect. Same as `finalized_at` unless overwritten.
When defined, this value replaces the system-generated 'Date of issue' printed on the
invoice PDF and receipt.
- `Footer`
  - Footer to be displayed on the invoice.
- `Issuer`
  - The connected account that issues the invoice. The invoice is presented with the
branding and support information of the specified account.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format. Individual keys can be unset by posting an empty value to
them. All keys can be unset by posting an empty value to `metadata`.
- `Number`
  - Set the number for this invoice. If no number is present then a number will be assigned
automatically when the invoice is finalized. In many markets, regulations require
invoices to be unique, sequential and / or gapless. You are responsible for ensuring
this is true across all your different invoicing systems in the event that you edit the
invoice number using our API. If you use only Stripe for your invoices and do not change
invoice numbers, Stripe handles this aspect of compliance for you automatically.
- `OnBehalfOf`
  - The account (if any) for which the funds of the invoice payment are intended. If set,
the invoice will be presented with the branding and support information of the specified
account. See the Invoices
with Connect documentation for details.
- `PaymentSettings`
  - Configuration settings for the PaymentIntent that is generated when the invoice is
finalized.
- `Rendering`
  - The rendering-related settings that control how the invoice is displayed on
customer-facing surfaces such as PDF and Hosted Invoice Page.
- `ShippingCost`
  - Settings for the cost of shipping for this invoice.
- `ShippingDetails`
  - Shipping details for the invoice. The Invoice PDF will use the `shipping_details`
value if it is set, otherwise the PDF will render the shipping address from the
customer.
- `StatementDescriptor`
  - Extra information about a charge for the customer's credit card statement. It must
contain at least one letter. If not specified and this invoice is part of a
subscription, the default `statement_descriptor` will be set to the first
subscription item's product's `statement_descriptor`.
- `TransferData`
  - If specified, the funds from the invoice will be transferred to the destination and the
ID of the resulting transfer will be found on the invoice's charge. This will be unset
if you POST an empty value.


#### `InvoiceListOptions`

**Properties:**

- `CollectionMethod`
  - The collection method of the invoice to retrieve. Either `charge_automatically` or
`send_invoice`.
One of: `charge_automatically`, or `send_invoice`.
- `Created`
  - Only return invoices that were created during the given date interval.
- `Customer`
  - Only return invoices for the customer specified by this customer ID.
- `CustomerAccount`
  - Only return invoices for the account representing the customer specified by this account
ID.
- `Status`
  - The status of the invoice, one of `draft`, `open`, `paid`,
`uncollectible`, or `void`. Learn
more.
One of: `draft`, `open`, `paid`, `uncollectible`, or `void`.
- `Subscription`
  - Only return invoices for the subscription specified by this subscription ID.


### InvoiceItem

#### `InvoiceItem`

Invoice Items represent the component lines of an invoice. When you create an invoice item
with an `invoice` field, it is attached to the specified invoice and included as an invoice line item within invoice.lines.

Invoice Items can be created before you are ready to actually send the invoice. This can
be particularly useful when combined with a subscription. Sometimes you want to
add a charge or credit to a customer, but actually charge or credit the customer's card
only at the end of a regular billing cycle. This is useful for combining several charges
(to minimize per-transaction fees), or for having Stripe tabulate your usage-based
billing totals.

Related guides: Integrate with
the Invoicing API, Subscription
Invoices.

**Properties:**

- `Amount`
  - Amount (in the `currency` specified) of the invoice item. This should always be
equal to `unit_amount * quantity`.
- `Currency`
  - Three-letter ISO currency
code, in lowercase. Must be a supported
currency.
- `Customer`
  - (Expanded)
The ID of the customer to bill for this invoice item.

For more information, see the expand documentation.
- `CustomerAccount`
  - The ID of the account to bill for this invoice item.
- `CustomerId`
  - (ID of the Customer)
The ID of the customer to bill for this invoice item.
- `Date`
  - Time at which the object was created. Measured in seconds since the Unix epoch.
- `Deleted`
  - Whether this object is deleted or not.
- `Description`
  - An arbitrary string attached to the object. Often useful for displaying to users.
- `DiscountIds`
  - (IDs of the Discounts)
The discounts which apply to the invoice item. Item discounts are applied before invoice
discounts. Use `expand[]=discounts` to expand each discount.
- `Discountable`
  - If true, discounts will apply to this invoice item. Always false for prorations.
- `Discounts`
  - (Expanded)
The discounts which apply to the invoice item. Item discounts are applied before invoice
discounts. Use `expand[]=discounts` to expand each discount.

For more information, see the expand documentation.
- `Id`
  - Unique identifier for the object.
- `Invoice`
  - (Expanded)
The ID of the invoice this invoice item belongs to.

For more information, see the expand documentation.
- `InvoiceId`
  - (ID of the Invoice)
The ID of the invoice this invoice item belongs to.
- `Livemode`
  - If the object exists in live mode, the value is `true`. If the object exists in
test mode, the value is `false`.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format.
- `NetAmount`
  - The amount after discounts, but before credits and taxes. This field is `null` for
`discountable=true` items.
- `Object`
  - String representing the object's type. Objects of the same type share the same value.
- `Parent`
  - The parent that generated this invoice item.
- `Pricing`
  - The pricing information of the invoice item.
- `Proration`
  - Whether the invoice item was created automatically as a proration adjustment when the
customer switched plans.
- `Quantity`
  - Quantity of units for the invoice item in integer format, with any decimal precision
truncated. For the item's full-precision decimal quantity, use `quantity_decimal`.
This field will be deprecated in favor of `quantity_decimal` in a future version.
If the invoice item is a proration, the quantity of the subscription that the proration
was computed for.
- `QuantityDecimal`
  - Non-negative decimal with at most 12 decimal places. The quantity of units for the
invoice item.
- `TaxRates`
  - The tax rates which apply to the invoice item. When set, the `default_tax_rates` on
the invoice do not apply to this invoice item.
- `TestClock`
  - (Expanded)
ID of the test clock this invoice item belongs to.

For more information, see the expand documentation.
- `TestClockId`
  - (ID of the TestHelpers.TestClock)
ID of the test clock this invoice item belongs to.


#### `InvoiceItemService`

**Methods:**

- `Create(Stripe.InvoiceItemCreateOptions, Stripe.RequestOptions)`
  - Creates an item to be added to a draft invoice (up to 250 items per invoice). If no
invoice is specified, the item will be on the next invoice created for the customer
specified..
- `CreateAsync(Stripe.InvoiceItemCreateOptions, Stripe.RequestOptions, CancellationToken)`
  - Creates an item to be added to a draft invoice (up to 250 items per invoice). If no
invoice is specified, the item will be on the next invoice created for the customer
specified..
- `Delete(string, Stripe.InvoiceItemDeleteOptions, Stripe.RequestOptions)`
  - Deletes an invoice item, removing it from an invoice. Deleting invoice items is only
possible when they’re not attached to invoices, or if it’s attached to a draft
invoice..
- `DeleteAsync(string, Stripe.InvoiceItemDeleteOptions, Stripe.RequestOptions, CancellationToken)`
  - Deletes an invoice item, removing it from an invoice. Deleting invoice items is only
possible when they’re not attached to invoices, or if it’s attached to a draft
invoice..
- `Get(string, Stripe.InvoiceItemGetOptions, Stripe.RequestOptions)`
  - Retrieves the invoice item with the given ID..
- `GetAsync(string, Stripe.InvoiceItemGetOptions, Stripe.RequestOptions, CancellationToken)`
  - Retrieves the invoice item with the given ID..
- `List(Stripe.InvoiceItemListOptions, Stripe.RequestOptions)`
  - Returns a list of your invoice items. Invoice items are returned sorted by creation
date, with the most recently created invoice items appearing first..
- `ListAsync(Stripe.InvoiceItemListOptions, Stripe.RequestOptions, CancellationToken)`
  - Returns a list of your invoice items. Invoice items are returned sorted by creation
date, with the most recently created invoice items appearing first..
- `ListAutoPaging(Stripe.InvoiceItemListOptions, Stripe.RequestOptions)`
  - Returns a list of your invoice items. Invoice items are returned sorted by creation
date, with the most recently created invoice items appearing first..
- `ListAutoPagingAsync(Stripe.InvoiceItemListOptions, Stripe.RequestOptions, CancellationToken)`
  - Returns a list of your invoice items. Invoice items are returned sorted by creation
date, with the most recently created invoice items appearing first..
- `Update(string, Stripe.InvoiceItemUpdateOptions, Stripe.RequestOptions)`
  - Updates the amount or description of an invoice item on an upcoming invoice. Updating
an invoice item is only possible before the invoice it’s attached to is closed..
- `UpdateAsync(string, Stripe.InvoiceItemUpdateOptions, Stripe.RequestOptions, CancellationToken)`
  - Updates the amount or description of an invoice item on an upcoming invoice. Updating
an invoice item is only possible before the invoice it’s attached to is closed..


#### `InvoiceItemCreateOptions`

**Properties:**

- `Amount`
  - The integer amount in cents (or local equivalent) of the charge to be applied to the
upcoming invoice. Passing in a negative `amount` will reduce the `amount_due`
on the invoice.
- `Currency`
  - Three-letter ISO currency
code, in lowercase. Must be a supported
currency.
- `Customer`
  - The ID of the customer to bill for this invoice item.
- `CustomerAccount`
  - The ID of the account representing the customer to bill for this invoice item.
- `Description`
  - An arbitrary string which you can attach to the invoice item. The description is
displayed in the invoice for easy tracking.
- `Discountable`
  - Controls whether discounts apply to this invoice item. Defaults to false for prorations
or negative invoice items, and true for all other invoice items.
- `Discounts`
  - The coupons and promotion codes to redeem into discounts for the invoice item or invoice
line item.
- `Invoice`
  - The ID of an existing invoice to add this invoice item to. For subscription invoices,
when left blank, the invoice item will be added to the next upcoming scheduled invoice.
For standalone invoices, the invoice item won't be automatically added unless you pass
`pending_invoice_item_behavior: 'include'` when creating the invoice. This is
useful when adding invoice items in response to an invoice.created webhook. You can only
add invoice items to draft invoices and there is a maximum of 250 items per invoice.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format. Individual keys can be unset by posting an empty value to
them. All keys can be unset by posting an empty value to `metadata`.
- `Period`
  - The period associated with this invoice item. When set to different values, the period
will be rendered on the invoice. If you have Stripe Revenue Recognition
enabled, the period will be used to recognize and defer revenue. See the Revenue
Recognition documentation for details.
- `PriceData`
  - Data used to generate a new Price
object inline.
- `Pricing`
  - The pricing information for the invoice item.
- `Quantity`
  - Non-negative integer. The quantity of units for the invoice item. Use
`quantity_decimal` instead to provide decimal precision. This field will be
deprecated in favor of `quantity_decimal` in a future version.
- `QuantityDecimal`
  - Non-negative decimal with at most 12 decimal places. The quantity of units for the
invoice item.
- `Subscription`
  - The ID of a subscription to add this invoice item to. When left blank, the invoice item
is added to the next upcoming scheduled invoice. When set, scheduled invoices for
subscriptions other than the specified subscription will ignore the invoice item. Use
this when you want to express that an invoice item has been accrued within the context
of a particular subscription.
- `TaxBehavior`
  - Only required if a default
tax behavior was not provided in the Stripe Tax settings. Specifies whether the
price is considered inclusive of taxes or exclusive of taxes. One of `inclusive`,
`exclusive`, or `unspecified`. Once specified as either `inclusive` or
`exclusive`, it cannot be changed.
One of: `exclusive`, `inclusive`, or `unspecified`.
- `TaxCode`
  - A tax code ID.
- `TaxRates`
  - The tax rates which apply to the invoice item. When set, the `default_tax_rates` on
the invoice do not apply to this invoice item.
- `UnitAmountDecimal`
  - The decimal unit amount in cents (or local equivalent) of the charge to be applied to
the upcoming invoice. This `unit_amount_decimal` will be multiplied by the quantity
to get the full amount. Passing in a negative `unit_amount_decimal` will reduce the
`amount_due` on the invoice. Accepts at most 12 decimal places.


#### `InvoiceItemUpdateOptions`

**Properties:**

- `Amount`
  - The integer amount in cents (or local equivalent) of the charge to be applied to the
upcoming invoice. If you want to apply a credit to the customer's account, pass a
negative amount.
- `Description`
  - An arbitrary string which you can attach to the invoice item. The description is
displayed in the invoice for easy tracking.
- `Discountable`
  - Controls whether discounts apply to this invoice item. Defaults to false for prorations
or negative invoice items, and true for all other invoice items. Cannot be set to true
for prorations.
- `Discounts`
  - The coupons, promotion codes & existing discounts which apply to the invoice item or
invoice line item. Item discounts are applied before invoice discounts. Pass an empty
string to remove previously-defined discounts.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format. Individual keys can be unset by posting an empty value to
them. All keys can be unset by posting an empty value to `metadata`.
- `Period`
  - The period associated with this invoice item. When set to different values, the period
will be rendered on the invoice. If you have Stripe Revenue Recognition
enabled, the period will be used to recognize and defer revenue. See the Revenue
Recognition documentation for details.
- `PriceData`
  - Data used to generate a new Price
object inline.
- `Pricing`
  - The pricing information for the invoice item.
- `Quantity`
  - Non-negative integer. The quantity of units for the invoice item. Use
`quantity_decimal` instead to provide decimal precision. This field will be
deprecated in favor of `quantity_decimal` in a future version.
- `QuantityDecimal`
  - Non-negative decimal with at most 12 decimal places. The quantity of units for the line
item.
- `TaxBehavior`
  - Only required if a default
tax behavior was not provided in the Stripe Tax settings. Specifies whether the
price is considered inclusive of taxes or exclusive of taxes. One of `inclusive`,
`exclusive`, or `unspecified`. Once specified as either `inclusive` or
`exclusive`, it cannot be changed.
One of: `exclusive`, `inclusive`, or `unspecified`.
- `TaxCode`
  - A tax code ID.
- `TaxRates`
  - The tax rates which apply to the invoice item. When set, the `default_tax_rates` on
the invoice do not apply to this invoice item. Pass an empty string to remove
previously-defined tax rates.
- `UnitAmountDecimal`
  - The decimal unit amount in cents (or local equivalent) of the charge to be applied to
the upcoming invoice. This `unit_amount_decimal` will be multiplied by the quantity
to get the full amount. Passing in a negative `unit_amount_decimal` will reduce the
`amount_due` on the invoice. Accepts at most 12 decimal places.


#### `InvoiceItemListOptions`

**Properties:**

- `Created`
  - Only return invoice items that were created during the given date interval.
- `Customer`
  - The identifier of the customer whose invoice items to return. If none is provided,
returns all invoice items.
- `CustomerAccount`
  - The identifier of the account representing the customer whose invoice items to return.
If none is provided, returns all invoice items.
- `Invoice`
  - Only return invoice items belonging to this invoice. If none is provided, all invoice
items will be returned. If specifying an invoice, no customer identifier is needed.
- `Pending`
  - Set to `true` to only show pending invoice items, which are not yet attached to any
invoices. Set to `false` to only show invoice items already attached to invoices.
If unspecified, no filter is applied.


### Product

#### `Product`

A Climate product represents a type of carbon removal unit available for reservation.
You can retrieve it to see the current price and availability.

**Properties:**

- `Created`
  - Time at which the object was created. Measured in seconds since the Unix epoch.
- `CurrentPricesPerMetricTon`
  - Current prices for a metric ton of carbon removal in a currency's smallest unit.
- `DeliveryYear`
  - The year in which the carbon removal is expected to be delivered.
- `Id`
  - Unique identifier for the object. For convenience, Climate product IDs are
human-readable strings that start with `climsku_`. See carbon removal
inventory for a list of available carbon removal products.
- `Livemode`
  - Has the value `true` if the object exists in live mode or the value `false` if
the object exists in test mode.
- `MetricTonsAvailable`
  - The quantity of metric tons available for reservation.
- `Name`
  - The Climate product's name.
- `Object`
  - String representing the object's type. Objects of the same type share the same value.
- `Suppliers`
  - The carbon removal suppliers that fulfill orders for this Climate product.


#### `Product`

Products describe the specific goods or services you offer to your customers. For
example, you might offer a Standard and Premium version of your goods or service; each
version would be a separate Product. They can be used in conjunction with Prices to configure pricing in Payment Links,
Checkout, and Subscriptions.

Related guides: Set up a
subscription, share a Payment
Link, accept
payments with Checkout, and more about Products and Prices.

**Properties:**

- `Active`
  - Whether the product is currently available for purchase.
- `Created`
  - Time at which the object was created. Measured in seconds since the Unix epoch.
- `DefaultPrice`
  - (Expanded)
The ID of the Price object that is the
default price for this product.

For more information, see the expand documentation.
- `DefaultPriceId`
  - (ID of the Price)
The ID of the Price object that is the
default price for this product.
- `Deleted`
  - Whether this object is deleted or not.
- `Description`
  - The product's description, meant to be displayable to the customer. Use this field to
optionally store a long form explanation of the product being sold for your own
rendering purposes.
- `Id`
  - Unique identifier for the object.
- `Images`
  - A list of up to 8 URLs of images for this product, meant to be displayable to the
customer.
- `Livemode`
  - If the object exists in live mode, the value is `true`. If the object exists in
test mode, the value is `false`.
- `MarketingFeatures`
  - A list of up to 15 marketing features for this product. These are displayed in pricing tables.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format.
- `Name`
  - The product's name, meant to be displayable to the customer.
- `Object`
  - String representing the object's type. Objects of the same type share the same value.
- `PackageDimensions`
  - The dimensions of this product for shipping purposes.
- `Shippable`
  - Whether this product is shipped (i.e., physical goods).
- `StatementDescriptor`
  - Extra information about a product which will appear on your customer's credit card
statement. In the case that multiple products are billed at once, the first statement
descriptor will be used. Only used for subscription payments.
- `TaxCode`
  - (Expanded)
A tax code ID.

For more information, see the expand documentation.
- `TaxCodeId`
  - (ID of the TaxCode)
A tax code ID.
- `Type`
  - The type of the product. The product is either of type `good`, which is eligible
for use with Orders and SKUs, or `service`, which is eligible for use with
Subscriptions and Plans.
One of: `good`, or `service`.
- `UnitLabel`
  - A label that represents units of this product. When set, this will be included in
customers' receipts, invoices, Checkout, and the customer portal.
- `Updated`
  - Time at which the object was last updated. Measured in seconds since the Unix epoch.
- `Url`
  - A URL of a publicly-accessible webpage for this product.


#### `ProductService`

**Methods:**

- `Get(string, Stripe.Climate.ProductGetOptions, Stripe.RequestOptions)`
  - Retrieves the details of a Climate product with the given ID..
- `GetAsync(string, Stripe.Climate.ProductGetOptions, Stripe.RequestOptions, CancellationToken)`
  - Retrieves the details of a Climate product with the given ID..
- `List(Stripe.Climate.ProductListOptions, Stripe.RequestOptions)`
  - Lists all available Climate product objects..
- `ListAsync(Stripe.Climate.ProductListOptions, Stripe.RequestOptions, CancellationToken)`
  - Lists all available Climate product objects..
- `ListAutoPaging(Stripe.Climate.ProductListOptions, Stripe.RequestOptions)`
  - Lists all available Climate product objects..
- `ListAutoPagingAsync(Stripe.Climate.ProductListOptions, Stripe.RequestOptions, CancellationToken)`
  - Lists all available Climate product objects..


#### `ProductService`

**Methods:**

- `Create(Stripe.ProductCreateOptions, Stripe.RequestOptions)`
  - Creates a new product object..
- `CreateAsync(Stripe.ProductCreateOptions, Stripe.RequestOptions, CancellationToken)`
  - Creates a new product object..
- `Delete(string, Stripe.ProductDeleteOptions, Stripe.RequestOptions)`
  - Delete a product. Deleting a product is only possible if it has no prices associated
with it. Additionally, deleting a product with `type=good` is only possible if it
has no SKUs associated with it..
- `DeleteAsync(string, Stripe.ProductDeleteOptions, Stripe.RequestOptions, CancellationToken)`
  - Delete a product. Deleting a product is only possible if it has no prices associated
with it. Additionally, deleting a product with `type=good` is only possible if it
has no SKUs associated with it..
- `Get(string, Stripe.ProductGetOptions, Stripe.RequestOptions)`
  - Retrieves the details of an existing product. Supply the unique product ID from
either a product creation request or the product list, and Stripe will return the
corresponding product information..
- `GetAsync(string, Stripe.ProductGetOptions, Stripe.RequestOptions, CancellationToken)`
  - Retrieves the details of an existing product. Supply the unique product ID from
either a product creation request or the product list, and Stripe will return the
corresponding product information..
- `List(Stripe.ProductListOptions, Stripe.RequestOptions)`
  - Returns a list of your products. The products are returned sorted by creation date,
with the most recently created products appearing first..
- `ListAsync(Stripe.ProductListOptions, Stripe.RequestOptions, CancellationToken)`
  - Returns a list of your products. The products are returned sorted by creation date,
with the most recently created products appearing first..
- `ListAutoPaging(Stripe.ProductListOptions, Stripe.RequestOptions)`
  - Returns a list of your products. The products are returned sorted by creation date,
with the most recently created products appearing first..
- `ListAutoPagingAsync(Stripe.ProductListOptions, Stripe.RequestOptions, CancellationToken)`
  - Returns a list of your products. The products are returned sorted by creation date,
with the most recently created products appearing first..
- `Search(Stripe.ProductSearchOptions, Stripe.RequestOptions)`
  - Search for products you’ve previously created using Stripe’s Search Query Language.
Don’t use search in read-after-write flows where strict consistency is necessary. Under
normal operating conditions, data is searchable in less than a minute. Occasionally,
propagation of new or updated data can be up to an hour behind during outages. Search
functionality is not available to merchants in India..
- `SearchAsync(Stripe.ProductSearchOptions, Stripe.RequestOptions, CancellationToken)`
  - Search for products you’ve previously created using Stripe’s Search Query Language.
Don’t use search in read-after-write flows where strict consistency is necessary. Under
normal operating conditions, data is searchable in less than a minute. Occasionally,
propagation of new or updated data can be up to an hour behind during outages. Search
functionality is not available to merchants in India..
- `SearchAutoPaging(Stripe.ProductSearchOptions, Stripe.RequestOptions)`
  - Search for products you’ve previously created using Stripe’s Search Query Language.
Don’t use search in read-after-write flows where strict consistency is necessary. Under
normal operating conditions, data is searchable in less than a minute. Occasionally,
propagation of new or updated data can be up to an hour behind during outages. Search
functionality is not available to merchants in India..
- `SearchAutoPagingAsync(Stripe.ProductSearchOptions, Stripe.RequestOptions, CancellationToken)`
  - Search for products you’ve previously created using Stripe’s Search Query Language.
Don’t use search in read-after-write flows where strict consistency is necessary. Under
normal operating conditions, data is searchable in less than a minute. Occasionally,
propagation of new or updated data can be up to an hour behind during outages. Search
functionality is not available to merchants in India..
- `Update(string, Stripe.ProductUpdateOptions, Stripe.RequestOptions)`
  - Updates the specific product by setting the values of the parameters passed. Any
parameters not provided will be left unchanged..
- `UpdateAsync(string, Stripe.ProductUpdateOptions, Stripe.RequestOptions, CancellationToken)`
  - Updates the specific product by setting the values of the parameters passed. Any
parameters not provided will be left unchanged..


#### `ProductCreateOptions`

**Properties:**

- `Active`
  - Whether the product is currently available for purchase. Defaults to `true`.
- `DefaultPriceData`
  - Data used to generate a new Price
object. This Price will be set as the default price for this product.
- `Description`
  - The product's description, meant to be displayable to the customer. Use this field to
optionally store a long form explanation of the product being sold for your own
rendering purposes.
- `Id`
  - An identifier will be randomly generated by Stripe. You can optionally override this ID,
but the ID must be unique across all products in your Stripe account.
- `Images`
  - A list of up to 8 URLs of images for this product, meant to be displayable to the
customer.
- `MarketingFeatures`
  - A list of up to 15 marketing features for this product. These are displayed in pricing tables.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format. Individual keys can be unset by posting an empty value to
them. All keys can be unset by posting an empty value to `metadata`.
- `Name`
  - The product's name, meant to be displayable to the customer.
- `PackageDimensions`
  - The dimensions of this product for shipping purposes.
- `Shippable`
  - Whether this product is shipped (i.e., physical goods).
- `StatementDescriptor`
  - An arbitrary string to be displayed on your customer's credit card or bank statement.
While most banks display this information consistently, some may display it incorrectly
or not at all.

This may be up to 22 characters. The statement description may not include `<`,
`>`, `\`, `"`, `'` characters, and will appear on your customer's
statement in capital letters. Non-ASCII characters are automatically stripped. It must
contain at least one letter. Only used for subscription payments.
- `TaxCode`
  - A tax code ID.
- `Type`
  - The type of the product. Defaults to `service` if not explicitly specified,
enabling use of this product with Subscriptions and Plans. Set this parameter to
`good` to use this product with Orders and SKUs. On API versions before
`2018-02-05`, this field defaults to `good` for compatibility reasons.
One of: `good`, or `service`.
- `UnitLabel`
  - A label that represents units of this product. When set, this will be included in
customers' receipts, invoices, Checkout, and the customer portal.
- `Url`
  - A URL of a publicly-accessible webpage for this product.


#### `ProductUpdateOptions`

**Properties:**

- `Active`
  - Whether the product is available for purchase.
- `DefaultPrice`
  - The ID of the Price object that is the
default price for this product.
- `Description`
  - The product's description, meant to be displayable to the customer. Use this field to
optionally store a long form explanation of the product being sold for your own
rendering purposes.
- `Images`
  - A list of up to 8 URLs of images for this product, meant to be displayable to the
customer.
- `MarketingFeatures`
  - A list of up to 15 marketing features for this product. These are displayed in pricing tables.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format. Individual keys can be unset by posting an empty value to
them. All keys can be unset by posting an empty value to `metadata`.
- `Name`
  - The product's name, meant to be displayable to the customer.
- `PackageDimensions`
  - The dimensions of this product for shipping purposes.
- `Shippable`
  - Whether this product is shipped (i.e., physical goods).
- `StatementDescriptor`
  - An arbitrary string to be displayed on your customer's credit card or bank statement.
While most banks display this information consistently, some may display it incorrectly
or not at all.

This may be up to 22 characters. The statement description may not include `<`,
`>`, `\`, `"`, `'` characters, and will appear on your customer's
statement in capital letters. Non-ASCII characters are automatically stripped. It must
contain at least one letter. May only be set if `type=service`. Only used for
subscription payments.
- `TaxCode`
  - A tax code ID.
- `UnitLabel`
  - A label that represents units of this product. When set, this will be included in
customers' receipts, invoices, Checkout, and the customer portal. May only be set if
`type=service`.
- `Url`
  - A URL of a publicly-accessible webpage for this product.


#### `ProductListOptions`

**Properties:**

- `Active`
  - Only return products that are active or inactive (e.g., pass `false` to list all
inactive products).
- `Created`
  - Only return products that were created during the given date interval.
- `Ids`
  - Only return products with the given IDs. Cannot be used with starting_after or ending_before.
- `Shippable`
  - Only return products that can be shipped (i.e., physical, not digital products).
- `Type`
  - Only return products of this type.
One of: `good`, or `service`.
- `Url`
  - Only return products with the given url.


### Price

#### `Price`

Prices define the unit cost, currency, and (optional) billing cycle for both recurring
and one-time purchases of products. Products help you track inventory or
provisioning, and prices help you track payment terms. Different physical goods or
levels of service should be represented by products, and pricing options should be
represented by prices. This approach lets you change prices without having to change
your provisioning scheme.

For example, you might have a single "gold" product that has prices for $10/month,
$100/year, and €9 once.

Related guides: Set up a
subscription, create an
invoice, and more about products and prices.

**Properties:**

- `Active`
  - Whether the price can be used for new purchases.
- `BillingScheme`
  - Describes how to compute the price per period. Either `per_unit` or `tiered`.
`per_unit` indicates that the fixed amount (specified in `unit_amount` or
`unit_amount_decimal`) will be charged per unit in `quantity` (for prices with
`usage_type=licensed`), or per unit of total usage (for prices with
`usage_type=metered`). `tiered` indicates that the unit pricing will be
computed using a tiering strategy as defined using the `tiers` and
`tiers_mode` attributes.
One of: `per_unit`, or `tiered`.
- `Created`
  - Time at which the object was created. Measured in seconds since the Unix epoch.
- `Currency`
  - Three-letter ISO currency
code, in lowercase. Must be a supported
currency.
- `CurrencyOptions`
  - Prices defined in each available currency option. Each key must be a three-letter ISO currency code and a supported currency.
- `CustomUnitAmount`
  - When set, provides configuration for the amount to be adjusted by the customer during
Checkout Sessions and Payment Links.
- `Deleted`
  - Whether this object is deleted or not.
- `Id`
  - Unique identifier for the object.
- `Livemode`
  - If the object exists in live mode, the value is `true`. If the object exists in
test mode, the value is `false`.
- `LookupKey`
  - A lookup key used to retrieve prices dynamically from a static string. This may be up to
200 characters.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format.
- `Nickname`
  - A brief description of the price, hidden from customers.
- `Object`
  - String representing the object's type. Objects of the same type share the same value.
- `Product`
  - (Expanded)
The ID of the product this price is associated with.

For more information, see the expand documentation.
- `ProductId`
  - (ID of the Product)
The ID of the product this price is associated with.
- `Recurring`
  - The recurring components of a price such as `interval` and `usage_type`.
- `TaxBehavior`
  - Only required if a default
tax behavior was not provided in the Stripe Tax settings. Specifies whether the
price is considered inclusive of taxes or exclusive of taxes. One of `inclusive`,
`exclusive`, or `unspecified`. Once specified as either `inclusive` or
`exclusive`, it cannot be changed.
One of: `exclusive`, `inclusive`, or `unspecified`.
- `Tiers`
  - Each element represents a pricing tier. This parameter requires `billing_scheme` to
be set to `tiered`. See also the documentation for `billing_scheme`.
- `TiersMode`
  - Defines if the tiering price should be `graduated` or `volume` based. In
`volume`-based tiering, the maximum quantity within a period determines the per
unit price. In `graduated` tiering, pricing can change as the quantity grows.
One of: `graduated`, or `volume`.
- `TransformQuantity`
  - Apply a transformation to the reported usage or set quantity before computing the amount
billed. Cannot be combined with `tiers`.
- `Type`
  - One of `one_time` or `recurring` depending on whether the price is for a
one-time purchase or a recurring (subscription) purchase.
One of: `one_time`, or `recurring`.
- `UnitAmount`
  - The unit amount in cents (or local equivalent) to be charged, represented as a whole
integer if possible. Only set if `billing_scheme=per_unit`.
- `UnitAmountDecimal`
  - The unit amount in cents (or local equivalent) to be charged, represented as a decimal
string with at most 12 decimal places. Only set if `billing_scheme=per_unit`.


#### `PriceService`

**Methods:**

- `Create(Stripe.PriceCreateOptions, Stripe.RequestOptions)`
  - Creates a new Price for an existing
Product. The Price can be recurring
or one-time..
- `CreateAsync(Stripe.PriceCreateOptions, Stripe.RequestOptions, CancellationToken)`
  - Creates a new Price for an existing
Product. The Price can be recurring
or one-time..
- `Get(string, Stripe.PriceGetOptions, Stripe.RequestOptions)`
  - Retrieves the price with the given ID..
- `GetAsync(string, Stripe.PriceGetOptions, Stripe.RequestOptions, CancellationToken)`
  - Retrieves the price with the given ID..
- `List(Stripe.PriceListOptions, Stripe.RequestOptions)`
  - Returns a list of your active prices, excluding inline
prices. For the list of inactive prices, set `active` to false..
- `ListAsync(Stripe.PriceListOptions, Stripe.RequestOptions, CancellationToken)`
  - Returns a list of your active prices, excluding inline
prices. For the list of inactive prices, set `active` to false..
- `ListAutoPaging(Stripe.PriceListOptions, Stripe.RequestOptions)`
  - Returns a list of your active prices, excluding inline
prices. For the list of inactive prices, set `active` to false..
- `ListAutoPagingAsync(Stripe.PriceListOptions, Stripe.RequestOptions, CancellationToken)`
  - Returns a list of your active prices, excluding inline
prices. For the list of inactive prices, set `active` to false..
- `Search(Stripe.PriceSearchOptions, Stripe.RequestOptions)`
  - Search for prices you’ve previously created using Stripe’s Search Query Language.
Don’t use search in read-after-write flows where strict consistency is necessary. Under
normal operating conditions, data is searchable in less than a minute. Occasionally,
propagation of new or updated data can be up to an hour behind during outages. Search
functionality is not available to merchants in India..
- `SearchAsync(Stripe.PriceSearchOptions, Stripe.RequestOptions, CancellationToken)`
  - Search for prices you’ve previously created using Stripe’s Search Query Language.
Don’t use search in read-after-write flows where strict consistency is necessary. Under
normal operating conditions, data is searchable in less than a minute. Occasionally,
propagation of new or updated data can be up to an hour behind during outages. Search
functionality is not available to merchants in India..
- `SearchAutoPaging(Stripe.PriceSearchOptions, Stripe.RequestOptions)`
  - Search for prices you’ve previously created using Stripe’s Search Query Language.
Don’t use search in read-after-write flows where strict consistency is necessary. Under
normal operating conditions, data is searchable in less than a minute. Occasionally,
propagation of new or updated data can be up to an hour behind during outages. Search
functionality is not available to merchants in India..
- `SearchAutoPagingAsync(Stripe.PriceSearchOptions, Stripe.RequestOptions, CancellationToken)`
  - Search for prices you’ve previously created using Stripe’s Search Query Language.
Don’t use search in read-after-write flows where strict consistency is necessary. Under
normal operating conditions, data is searchable in less than a minute. Occasionally,
propagation of new or updated data can be up to an hour behind during outages. Search
functionality is not available to merchants in India..
- `Update(string, Stripe.PriceUpdateOptions, Stripe.RequestOptions)`
  - Updates the specified price by setting the values of the parameters passed. Any
parameters not provided are left unchanged..
- `UpdateAsync(string, Stripe.PriceUpdateOptions, Stripe.RequestOptions, CancellationToken)`
  - Updates the specified price by setting the values of the parameters passed. Any
parameters not provided are left unchanged..


#### `PriceCreateOptions`

**Properties:**

- `Active`
  - Whether the price can be used for new purchases. Defaults to `true`.
- `BillingScheme`
  - Describes how to compute the price per period. Either `per_unit` or `tiered`.
`per_unit` indicates that the fixed amount (specified in `unit_amount` or
`unit_amount_decimal`) will be charged per unit in `quantity` (for prices with
`usage_type=licensed`), or per unit of total usage (for prices with
`usage_type=metered`). `tiered` indicates that the unit pricing will be
computed using a tiering strategy as defined using the `tiers` and
`tiers_mode` attributes.
One of: `per_unit`, or `tiered`.
- `Currency`
  - Three-letter ISO currency
code, in lowercase. Must be a supported
currency.
- `CurrencyOptions`
  - Prices defined in each available currency option. Each key must be a three-letter ISO currency code and a supported currency.
- `CustomUnitAmount`
  - When set, provides configuration for the amount to be adjusted by the customer during
Checkout Sessions and Payment Links.
- `LookupKey`
  - A lookup key used to retrieve prices dynamically from a static string. This may be up to
200 characters.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format. Individual keys can be unset by posting an empty value to
them. All keys can be unset by posting an empty value to `metadata`.
- `Nickname`
  - A brief description of the price, hidden from customers.
- `Product`
  - The ID of the Product that this Price will belong to.
- `ProductData`
  - These fields can be used to create a new product that this price will belong to.
- `Recurring`
  - The recurring components of a price such as `interval` and `usage_type`.
- `TaxBehavior`
  - Only required if a default
tax behavior was not provided in the Stripe Tax settings. Specifies whether the
price is considered inclusive of taxes or exclusive of taxes. One of `inclusive`,
`exclusive`, or `unspecified`. Once specified as either `inclusive` or
`exclusive`, it cannot be changed.
One of: `exclusive`, `inclusive`, or `unspecified`.
- `Tiers`
  - Each element represents a pricing tier. This parameter requires `billing_scheme` to
be set to `tiered`. See also the documentation for `billing_scheme`.
- `TiersMode`
  - Defines if the tiering price should be `graduated` or `volume` based. In
`volume`-based tiering, the maximum quantity within a period determines the per
unit price, in `graduated` tiering pricing can successively change as the quantity
grows.
One of: `graduated`, or `volume`.
- `TransferLookupKey`
  - If set to true, will atomically remove the lookup key from the existing price, and
assign it to this price.
- `TransformQuantity`
  - Apply a transformation to the reported usage or set quantity before computing the billed
price. Cannot be combined with `tiers`.
- `UnitAmount`
  - A positive integer in cents (or local equivalent) (or 0 for a free price) representing
how much to charge. One of `unit_amount`, `unit_amount_decimal`, or
`custom_unit_amount` is required, unless `billing_scheme=tiered`.
- `UnitAmountDecimal`
  - Same as `unit_amount`, but accepts a decimal value in cents (or local equivalent)
with at most 12 decimal places. Only one of `unit_amount` and
`unit_amount_decimal` can be set.


#### `PriceUpdateOptions`

**Properties:**

- `Active`
  - Whether the price can be used for new purchases. Defaults to `true`.
- `CurrencyOptions`
  - Prices defined in each available currency option. Each key must be a three-letter ISO currency code and a supported currency.
- `LookupKey`
  - A lookup key used to retrieve prices dynamically from a static string. This may be up to
200 characters.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format. Individual keys can be unset by posting an empty value to
them. All keys can be unset by posting an empty value to `metadata`.
- `Nickname`
  - A brief description of the price, hidden from customers.
- `TaxBehavior`
  - Only required if a default
tax behavior was not provided in the Stripe Tax settings. Specifies whether the
price is considered inclusive of taxes or exclusive of taxes. One of `inclusive`,
`exclusive`, or `unspecified`. Once specified as either `inclusive` or
`exclusive`, it cannot be changed.
One of: `exclusive`, `inclusive`, or `unspecified`.
- `TransferLookupKey`
  - If set to true, will atomically remove the lookup key from the existing price, and
assign it to this price.


#### `PriceListOptions`

**Properties:**

- `Active`
  - Only return prices that are active or inactive (e.g., pass `false` to list all
inactive prices).
- `Created`
  - A filter on the list, based on the object `created` field. The value can be a
string with an integer Unix timestamp, or it can be a dictionary with a number of
different query options.
- `Currency`
  - Only return prices for the given currency.
- `LookupKeys`
  - Only return the price with these lookup_keys, if any exist. You can specify up to 10
lookup_keys.
- `Product`
  - Only return prices for the given product.
- `Recurring`
  - Only return prices with these recurring fields.
- `Type`
  - Only return prices of type `recurring` or `one_time`.
One of: `one_time`, or `recurring`.


### Coupon

#### `Coupon`

A coupon contains information about a percent-off or amount-off discount you might want
to apply to a customer. Coupons may be applied to subscriptions, invoices, checkout sessions, quotes, and more. Coupons do not work with
conventional one-off charges or payment intents.

**Properties:**

- `AmountOff`
  - Amount (in the `currency` specified) that will be taken off the subtotal of any
invoices for this customer.
- `Created`
  - Time at which the object was created. Measured in seconds since the Unix epoch.
- `Currency`
  - If `amount_off` has been set, the three-letter ISO code for the currency of the amount to
take off.
- `CurrencyOptions`
  - Coupons defined in each available currency option. Each key must be a three-letter ISO currency code and a supported currency.
- `Deleted`
  - Whether this object is deleted or not.
- `Duration`
  - One of `forever`, `once`, or `repeating`. Describes how long a customer
who applies this coupon will get the discount.
One of: `forever`, `once`, or `repeating`.
- `DurationInMonths`
  - If `duration` is `repeating`, the number of months the coupon applies. Null if
coupon `duration` is `forever` or `once`.
- `Id`
  - Unique identifier for the object.
- `Livemode`
  - If the object exists in live mode, the value is `true`. If the object exists in
test mode, the value is `false`.
- `MaxRedemptions`
  - Maximum number of times this coupon can be redeemed, in total, across all customers,
before it is no longer valid.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format.
- `Name`
  - Name of the coupon displayed to customers on for instance invoices or receipts.
- `Object`
  - String representing the object's type. Objects of the same type share the same value.
- `PercentOff`
  - Percent that will be taken off the subtotal of any invoices for this customer for the
duration of the coupon. For example, a coupon with percent_off of 50 will make a $ (or
local equivalent)100 invoice $ (or local equivalent)50 instead.
- `RedeemBy`
  - Date after which the coupon can no longer be redeemed.
- `TimesRedeemed`
  - Number of times this coupon has been applied to a customer.
- `Valid`
  - Taking account of the above properties, whether this coupon can still be applied to a
customer.


#### `CouponService`

**Methods:**

- `Create(Stripe.CouponCreateOptions, Stripe.RequestOptions)`
  - You can create coupons easily via the coupon management page of the Stripe
dashboard. Coupon creation is also accessible via the API if you need to create coupons
on the fly..

A coupon has either a `percent_off` or an `amount_off` and `currency`.
If you set an `amount_off`, that amount will be subtracted from any invoice’s
subtotal. For example, an invoice with a subtotal of 100 will have
a final total of 0 if a coupon with an `amount_off` of
200 is applied to it and an invoice with a subtotal of
300 will have a final total of 100 if a coupon
with an `amount_off` of 200 is applied to it..
- `CreateAsync(Stripe.CouponCreateOptions, Stripe.RequestOptions, CancellationToken)`
  - You can create coupons easily via the coupon management page of the Stripe
dashboard. Coupon creation is also accessible via the API if you need to create coupons
on the fly..

A coupon has either a `percent_off` or an `amount_off` and `currency`.
If you set an `amount_off`, that amount will be subtracted from any invoice’s
subtotal. For example, an invoice with a subtotal of 100 will have
a final total of 0 if a coupon with an `amount_off` of
200 is applied to it and an invoice with a subtotal of
300 will have a final total of 100 if a coupon
with an `amount_off` of 200 is applied to it..
- `Delete(string, Stripe.CouponDeleteOptions, Stripe.RequestOptions)`
  - You can delete coupons via the coupon
management page of the Stripe dashboard. However, deleting a coupon does not affect
any customers who have already applied the coupon; it means that new customers can’t
redeem the coupon. You can also delete coupons via the API..
- `DeleteAsync(string, Stripe.CouponDeleteOptions, Stripe.RequestOptions, CancellationToken)`
  - You can delete coupons via the coupon
management page of the Stripe dashboard. However, deleting a coupon does not affect
any customers who have already applied the coupon; it means that new customers can’t
redeem the coupon. You can also delete coupons via the API..
- `Get(string, Stripe.CouponGetOptions, Stripe.RequestOptions)`
  - Retrieves the coupon with the given ID..
- `GetAsync(string, Stripe.CouponGetOptions, Stripe.RequestOptions, CancellationToken)`
  - Retrieves the coupon with the given ID..
- `List(Stripe.CouponListOptions, Stripe.RequestOptions)`
  - Returns a list of your coupons..
- `ListAsync(Stripe.CouponListOptions, Stripe.RequestOptions, CancellationToken)`
  - Returns a list of your coupons..
- `ListAutoPaging(Stripe.CouponListOptions, Stripe.RequestOptions)`
  - Returns a list of your coupons..
- `ListAutoPagingAsync(Stripe.CouponListOptions, Stripe.RequestOptions, CancellationToken)`
  - Returns a list of your coupons..
- `Update(string, Stripe.CouponUpdateOptions, Stripe.RequestOptions)`
  - Updates the metadata of a coupon. Other coupon details (currency, duration,
amount_off) are, by design, not editable..
- `UpdateAsync(string, Stripe.CouponUpdateOptions, Stripe.RequestOptions, CancellationToken)`
  - Updates the metadata of a coupon. Other coupon details (currency, duration,
amount_off) are, by design, not editable..


#### `CouponCreateOptions`

**Properties:**

- `AmountOff`
  - A positive integer representing the amount to subtract from an invoice total (required
if `percent_off` is not passed).
- `AppliesTo`
  - A hash containing directions for what this Coupon will apply discounts to.
- `Currency`
  - Three-letter ISO code for the currency
of the `amount_off` parameter (required if `amount_off` is passed).
- `CurrencyOptions`
  - Coupons defined in each available currency option (only supported if `amount_off`
is passed). Each key must be a three-letter ISO currency code and a supported currency.
- `Duration`
  - Specifies how long the discount will be in effect if used on a subscription. Defaults to
`once`.
One of: `forever`, `once`, or `repeating`.
- `DurationInMonths`
  - Required only if `duration` is `repeating`, in which case it must be a
positive integer that specifies the number of months the discount will be in effect.
- `Id`
  - Unique string of your choice that will be used to identify this coupon when applying it
to a customer. If you don't want to specify a particular code, you can leave the ID
blank and we'll generate a random code for you.
- `MaxRedemptions`
  - A positive integer specifying the number of times the coupon can be redeemed before it's
no longer valid. For example, you might have a 50% off coupon that the first 20 readers
of your blog can use.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format. Individual keys can be unset by posting an empty value to
them. All keys can be unset by posting an empty value to `metadata`.
- `Name`
  - Name of the coupon displayed to customers on, for instance invoices, or receipts. By
default the `id` is shown if `name` is not set.
- `PercentOff`
  - A positive float larger than 0, and smaller or equal to 100, that represents the
discount the coupon will apply (required if `amount_off` is not passed).
- `RedeemBy`
  - Unix timestamp specifying the last time at which the coupon can be redeemed (cannot be
set to more than 5 years in the future). After the redeem_by date, the coupon can no
longer be applied to new customers.


#### `CouponUpdateOptions`

**Properties:**

- `CurrencyOptions`
  - Coupons defined in each available currency option (only supported if the coupon is
amount-based). Each key must be a three-letter ISO currency code and a supported currency.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format. Individual keys can be unset by posting an empty value to
them. All keys can be unset by posting an empty value to `metadata`.
- `Name`
  - Name of the coupon displayed to customers on, for instance invoices, or receipts. By
default the `id` is shown if `name` is not set.


#### `CouponListOptions`

**Properties:**

- `Created`
  - A filter on the list, based on the object `created` field. The value can be a
string with an integer Unix timestamp, or it can be a dictionary with a number of
different query options.


### PromotionCode

#### `PromotionCode`

A Promotion Code represents a customer-redeemable code for an underlying promotion. You
can create multiple codes for a single promotion.

If you enable promotion codes in your customer portal
configuration, then customers can redeem a code themselves when updating a
subscription in the portal. Customers can also view the currently active promotion codes
and coupons on each of their subscriptions in the portal.

**Properties:**

- `Active`
  - Whether the promotion code is currently active. A promotion code is only active if the
coupon is also valid.
- `Code`
  - The customer-facing code. Regardless of case, this code must be unique across all active
promotion codes for each customer. Valid characters are lower case letters (a-z), upper
case letters (A-Z), digits (0-9), and dashes (-).
- `Created`
  - Time at which the object was created. Measured in seconds since the Unix epoch.
- `Customer`
  - (Expanded)
The customer who can use this promotion code.

For more information, see the expand documentation.
- `CustomerAccount`
  - The account representing the customer who can use this promotion code.
- `CustomerId`
  - (ID of the Customer)
The customer who can use this promotion code.
- `ExpiresAt`
  - Date at which the promotion code can no longer be redeemed.
- `Id`
  - Unique identifier for the object.
- `Livemode`
  - If the object exists in live mode, the value is `true`. If the object exists in
test mode, the value is `false`.
- `MaxRedemptions`
  - Maximum number of times this promotion code can be redeemed.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format.
- `Object`
  - String representing the object's type. Objects of the same type share the same value.
- `TimesRedeemed`
  - Number of times this promotion code has been used.


#### `PromotionCodeService`

**Methods:**

- `Create(Stripe.PromotionCodeCreateOptions, Stripe.RequestOptions)`
  - A promotion code points to an underlying promotion. You can optionally restrict the
code to a specific customer, redemption limit, and expiration date..
- `CreateAsync(Stripe.PromotionCodeCreateOptions, Stripe.RequestOptions, CancellationToken)`
  - A promotion code points to an underlying promotion. You can optionally restrict the
code to a specific customer, redemption limit, and expiration date..
- `Get(string, Stripe.PromotionCodeGetOptions, Stripe.RequestOptions)`
  - Retrieves the promotion code with the given ID. In order to retrieve a promotion code
by the customer-facing `code` use list with the desired
`code`..
- `GetAsync(string, Stripe.PromotionCodeGetOptions, Stripe.RequestOptions, CancellationToken)`
  - Retrieves the promotion code with the given ID. In order to retrieve a promotion code
by the customer-facing `code` use list with the desired
`code`..
- `List(Stripe.PromotionCodeListOptions, Stripe.RequestOptions)`
  - Returns a list of your promotion codes..
- `ListAsync(Stripe.PromotionCodeListOptions, Stripe.RequestOptions, CancellationToken)`
  - Returns a list of your promotion codes..
- `ListAutoPaging(Stripe.PromotionCodeListOptions, Stripe.RequestOptions)`
  - Returns a list of your promotion codes..
- `ListAutoPagingAsync(Stripe.PromotionCodeListOptions, Stripe.RequestOptions, CancellationToken)`
  - Returns a list of your promotion codes..
- `Update(string, Stripe.PromotionCodeUpdateOptions, Stripe.RequestOptions)`
  - Updates the specified promotion code by setting the values of the parameters passed.
Most fields are, by design, not editable..
- `UpdateAsync(string, Stripe.PromotionCodeUpdateOptions, Stripe.RequestOptions, CancellationToken)`
  - Updates the specified promotion code by setting the values of the parameters passed.
Most fields are, by design, not editable..


#### `PromotionCodeCreateOptions`

**Properties:**

- `Active`
  - Whether the promotion code is currently active.
- `Code`
  - The customer-facing code. Regardless of case, this code must be unique across all active
promotion codes for a specific customer. Valid characters are lower case letters (a-z),
upper case letters (A-Z), digits (0-9), and dashes (-).

If left blank, we will generate one automatically.
- `Customer`
  - The customer who can use this promotion code. If not set, all customers can use the
promotion code.
- `CustomerAccount`
  - The account representing the customer who can use this promotion code. If not set, all
customers can use the promotion code.
- `ExpiresAt`
  - The timestamp at which this promotion code will expire. If the coupon has specified a
`redeems_by`, then this value cannot be after the coupon's `redeems_by`.
- `MaxRedemptions`
  - A positive integer specifying the number of times the promotion code can be redeemed. If
the coupon has specified a `max_redemptions`, then this value cannot be greater
than the coupon's `max_redemptions`.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format. Individual keys can be unset by posting an empty value to
them. All keys can be unset by posting an empty value to `metadata`.
- `Promotion`
  - The promotion referenced by this promotion code.
- `Restrictions`
  - Settings that restrict the redemption of the promotion code.


#### `PromotionCodeUpdateOptions`

**Properties:**

- `Active`
  - Whether the promotion code is currently active. A promotion code can only be reactivated
when the coupon is still valid and the promotion code is otherwise redeemable.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format. Individual keys can be unset by posting an empty value to
them. All keys can be unset by posting an empty value to `metadata`.
- `Restrictions`
  - Settings that restrict the redemption of the promotion code.


#### `PromotionCodeListOptions`

**Properties:**

- `Active`
  - Filter promotion codes by whether they are active.
- `Code`
  - Only return promotion codes that have this case-insensitive code.
- `Coupon`
  - Only return promotion codes for this coupon.
- `Created`
  - A filter on the list, based on the object `created` field. The value can be a
string with an integer Unix timestamp, or it can be a dictionary with a number of
different query options.
- `Customer`
  - Only return promotion codes that are restricted to this customer.
- `CustomerAccount`
  - Only return promotion codes that are restricted to this account representing the
customer.


### Payout

#### `Payout`

A `Payout` object is created when you receive funds from Stripe, or when you
initiate a payout to either a bank account or debit card of a connected Stripe
account. You can retrieve individual payouts, and list all payouts. Payouts are made
on varying
schedules, depending on your country and industry.

Related guide: Receiving payouts.

**Properties:**

- `Amount`
  - The amount (in cents (or local equivalent)) that transfers to your bank account or debit
card.
- `ApplicationFee`
  - (Expanded)
The application fee (if any) for the payout. See the
Connect documentation for details.

For more information, see the expand documentation.
- `ApplicationFeeAmount`
  - The amount of the application fee (if any) requested for the payout. See the
Connect documentation for details.
- `ApplicationFeeId`
  - (ID of the ApplicationFee)
The application fee (if any) for the payout. See the
Connect documentation for details.
- `ArrivalDate`
  - Date that you can expect the payout to arrive in the bank. This factors in delays to
account for weekends or bank holidays.
- `Automatic`
  - Returns `true` if the payout is created by an automated payout schedule and
`false` if it's requested
manually.
- `BalanceTransaction`
  - (Expanded)
ID of the balance transaction that describes the impact of this payout on your account
balance.

For more information, see the expand documentation.
- `BalanceTransactionId`
  - (ID of the BalanceTransaction)
ID of the balance transaction that describes the impact of this payout on your account
balance.
- `Created`
  - Time at which the object was created. Measured in seconds since the Unix epoch.
- `Currency`
  - Three-letter ISO currency
code, in lowercase. Must be a supported
currency.
- `Description`
  - An arbitrary string attached to the object. Often useful for displaying to users.
- `Destination`
  - (Expanded)
ID of the bank account or card the payout is sent to.

For more information, see the expand documentation.
- `DestinationId`
  - (ID of the IExternalAccount)
ID of the bank account or card the payout is sent to.
- `FailureBalanceTransaction`
  - (Expanded)
If the payout fails or cancels, this is the ID of the balance transaction that reverses
the initial balance transaction and returns the funds from the failed payout back in
your balance.

For more information, see the expand documentation.
- `FailureBalanceTransactionId`
  - (ID of the BalanceTransaction)
If the payout fails or cancels, this is the ID of the balance transaction that reverses
the initial balance transaction and returns the funds from the failed payout back in
your balance.
- `FailureCode`
  - Error code that provides a reason for a payout failure, if available. View our list of failure codes.
- `FailureMessage`
  - Message that provides the reason for a payout failure, if available.
- `Id`
  - Unique identifier for the object.
- `Livemode`
  - If the object exists in live mode, the value is `true`. If the object exists in
test mode, the value is `false`.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format.
- `Method`
  - The method used to send this payout, which can be `standard` or `instant`.
`instant` is supported for payouts to debit cards and bank accounts in certain
countries. Learn more about bank support for Instant
Payouts.
- `Object`
  - String representing the object's type. Objects of the same type share the same value.
- `OriginalPayout`
  - (Expanded)
If the payout reverses another, this is the ID of the original payout.

For more information, see the expand documentation.
- `OriginalPayoutId`
  - (ID of the Payout)
If the payout reverses another, this is the ID of the original payout.
- `PayoutMethod`
  - ID of the v2 FinancialAccount the funds are sent to.
- `ReconciliationStatus`
  - If `completed`, you can use the Balance
Transactions API to list all balance transactions that are paid out in this payout.
One of: `completed`, `in_progress`, or `not_applicable`.
- `ReversedBy`
  - (Expanded)
If the payout reverses, this is the ID of the payout that reverses this payout.

For more information, see the expand documentation.
- `ReversedById`
  - (ID of the Payout)
If the payout reverses, this is the ID of the payout that reverses this payout.
- `SourceType`
  - The source balance this payout came from, which can be one of the following:
`card`, `fpx`, or `bank_account`.
- `StatementDescriptor`
  - Extra information about a payout that displays on the user's bank statement.
- `Status`
  - Current status of the payout: `paid`, `pending`, `in_transit`,
`canceled` or `failed`. A payout is `pending` until it's submitted to the
bank, when it becomes `in_transit`. The status changes to `paid` if the
transaction succeeds, or to `failed` or `canceled` (within 5 business days).
Some payouts that fail might initially show as `paid`, then change to
`failed`.
- `TraceId`
  - A value that generates from the beneficiary's bank that allows users to track payouts
with their bank. Banks might call this a "reference number" or something similar.
- `Type`
  - Can be `bank_account` or `card`.
One of: `bank_account`, or `card`.


#### `PayoutService`

**Methods:**

- `Cancel(string, Stripe.PayoutCancelOptions, Stripe.RequestOptions)`
  - You can cancel a previously created payout if its status is `pending`. Stripe
refunds the funds to your available balance. You can’t cancel automatic Stripe
payouts..
- `CancelAsync(string, Stripe.PayoutCancelOptions, Stripe.RequestOptions, CancellationToken)`
  - You can cancel a previously created payout if its status is `pending`. Stripe
refunds the funds to your available balance. You can’t cancel automatic Stripe
payouts..
- `Create(Stripe.PayoutCreateOptions, Stripe.RequestOptions)`
  - To send funds to your own bank account, create a new payout object. Your Stripe balance must cover the payout
amount. If it doesn’t, you receive an “Insufficient Funds” error..

If your API key is in test mode, money won’t actually be sent, though every other
action occurs as if you’re in live mode..

If you create a manual payout on a Stripe account that uses multiple payment source
types, you need to specify the source type balance that the payout draws from. The balance object details available and
pending amounts by source type..
- `CreateAsync(Stripe.PayoutCreateOptions, Stripe.RequestOptions, CancellationToken)`
  - To send funds to your own bank account, create a new payout object. Your Stripe balance must cover the payout
amount. If it doesn’t, you receive an “Insufficient Funds” error..

If your API key is in test mode, money won’t actually be sent, though every other
action occurs as if you’re in live mode..

If you create a manual payout on a Stripe account that uses multiple payment source
types, you need to specify the source type balance that the payout draws from. The balance object details available and
pending amounts by source type..
- `Get(string, Stripe.PayoutGetOptions, Stripe.RequestOptions)`
  - Retrieves the details of an existing payout. Supply the unique payout ID from either
a payout creation request or the payout list. Stripe returns the corresponding payout
information..
- `GetAsync(string, Stripe.PayoutGetOptions, Stripe.RequestOptions, CancellationToken)`
  - Retrieves the details of an existing payout. Supply the unique payout ID from either
a payout creation request or the payout list. Stripe returns the corresponding payout
information..
- `List(Stripe.PayoutListOptions, Stripe.RequestOptions)`
  - Returns a list of existing payouts sent to third-party bank accounts or payouts that
Stripe sent to you. The payouts return in sorted order, with the most recently created
payouts appearing first..
- `ListAsync(Stripe.PayoutListOptions, Stripe.RequestOptions, CancellationToken)`
  - Returns a list of existing payouts sent to third-party bank accounts or payouts that
Stripe sent to you. The payouts return in sorted order, with the most recently created
payouts appearing first..
- `ListAutoPaging(Stripe.PayoutListOptions, Stripe.RequestOptions)`
  - Returns a list of existing payouts sent to third-party bank accounts or payouts that
Stripe sent to you. The payouts return in sorted order, with the most recently created
payouts appearing first..
- `ListAutoPagingAsync(Stripe.PayoutListOptions, Stripe.RequestOptions, CancellationToken)`
  - Returns a list of existing payouts sent to third-party bank accounts or payouts that
Stripe sent to you. The payouts return in sorted order, with the most recently created
payouts appearing first..
- `Reverse(string, Stripe.PayoutReverseOptions, Stripe.RequestOptions)`
  - Reverses a payout by debiting the destination bank account. At this time, you can
only reverse payouts for connected accounts to US and Canadian bank accounts. If the
payout is manual and in the `pending` status, use `/v1/payouts/:id/cancel`
instead..

By requesting a reversal through `/v1/payouts/:id/reverse`, you confirm that the
authorized signatory of the selected bank account authorizes the debit on the bank
account and that no other authorization is required..
- `ReverseAsync(string, Stripe.PayoutReverseOptions, Stripe.RequestOptions, CancellationToken)`
  - Reverses a payout by debiting the destination bank account. At this time, you can
only reverse payouts for connected accounts to US and Canadian bank accounts. If the
payout is manual and in the `pending` status, use `/v1/payouts/:id/cancel`
instead..

By requesting a reversal through `/v1/payouts/:id/reverse`, you confirm that the
authorized signatory of the selected bank account authorizes the debit on the bank
account and that no other authorization is required..
- `Update(string, Stripe.PayoutUpdateOptions, Stripe.RequestOptions)`
  - Updates the specified payout by setting the values of the parameters you pass. We
don’t change parameters that you don’t provide. This request only accepts the metadata
as arguments..
- `UpdateAsync(string, Stripe.PayoutUpdateOptions, Stripe.RequestOptions, CancellationToken)`
  - Updates the specified payout by setting the values of the parameters you pass. We
don’t change parameters that you don’t provide. This request only accepts the metadata
as arguments..


#### `PayoutCreateOptions`

**Properties:**

- `Amount`
  - A positive integer in cents representing how much to payout.
- `Currency`
  - Three-letter ISO currency
code, in lowercase. Must be a supported
currency.
- `Description`
  - An arbitrary string attached to the object. Often useful for displaying to users.
- `Destination`
  - The ID of a bank account or a card to send the payout to. If you don't provide a
destination, we use the default external account for the specified currency.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format. Individual keys can be unset by posting an empty value to
them. All keys can be unset by posting an empty value to `metadata`.
- `Method`
  - The method used to send this payout, which is `standard` or `instant`. We
support `instant` for payouts to debit cards and bank accounts in certain
countries. Learn more about bank support for Instant
Payouts.
One of: `instant`, or `standard`.
- `PayoutMethod`
  - The ID of a v2 FinancialAccount to send funds to.
- `SourceType`
  - The balance type of your Stripe balance to draw this payout from. Balances for different
payment sources are kept separately. You can find the amounts with the Balances API. One
of `bank_account`, `card`, or `fpx`.
One of: `bank_account`, `card`, or `fpx`.
- `StatementDescriptor`
  - A string that displays on the recipient's bank or card statement (up to 22 characters).
A `statement_descriptor` that's longer than 22 characters return an error. Most
banks truncate this information and display it inconsistently. Some banks might not
display it at all. For US ACH payouts, this maps to the ACH Company Entry Description
field, which the NACHA standard limits to 10 characters. Stripe truncates descriptors
longer than 10 characters for US ACH payouts.


#### `PayoutUpdateOptions`

**Properties:**

- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format. Individual keys can be unset by posting an empty value to
them. All keys can be unset by posting an empty value to `metadata`.


#### `PayoutListOptions`

**Properties:**

- `ArrivalDate`
  - Only return payouts that are expected to arrive during the given date interval.
- `Created`
  - Only return payouts that were created during the given date interval.
- `Destination`
  - The ID of an external account - only return payouts sent to this external account.
- `Status`
  - Only return payouts that have the given status: `pending`, `paid`,
`failed`, or `canceled`.


### Balance

#### `Balance`

This is an object representing your Stripe balance. You can retrieve it to see the
balance currently on your Stripe account.

The top-level `available` and `pending` comprise your "payments balance.".

Related guide: Balances and
settlement time, Understanding Connect account
balances.

**Properties:**

- `Available`
  - Available funds that you can transfer or pay out automatically by Stripe or explicitly
through the Transfers API or Payouts API. You can find the available
balance for each currency and payment type in the `source_types` property.
- `ConnectReserved`
  - Funds held due to negative balances on connected accounts where account.controller.requirement_collection
is `application`, which includes Custom accounts. You can find the connect reserve
balance for each currency and payment type in the `source_types` property.
- `InstantAvailable`
  - Funds that you can pay out using Instant Payouts.
- `Livemode`
  - If the object exists in live mode, the value is `true`. If the object exists in
test mode, the value is `false`.
- `Object`
  - String representing the object's type. Objects of the same type share the same value.
- `Pending`
  - Funds that aren't available in the balance yet. You can find the pending balance for
each currency and each payment type in the `source_types` property.


#### `BalanceService`

**Methods:**

- `Get(Stripe.BalanceGetOptions, Stripe.RequestOptions)`
  - Retrieves the current account balance, based on the authentication that was used to
make the request. For a sample request, see Accounting
for negative balances..
- `Get(Stripe.RequestOptions)`
  - Retrieves the current account balance, based on the authentication that was used to
make the request. For a sample request, see Accounting
for negative balances..
- `GetAsync(Stripe.BalanceGetOptions, Stripe.RequestOptions, CancellationToken)`
  - Retrieves the current account balance, based on the authentication that was used to
make the request. For a sample request, see Accounting
for negative balances..
- `GetAsync(Stripe.RequestOptions, CancellationToken)`
  - Retrieves the current account balance, based on the authentication that was used to
make the request. For a sample request, see Accounting
for negative balances..


### BalanceTransaction

#### `BalanceTransaction`

Balance transactions represent funds moving through your Stripe account. Stripe creates
them for every type of transaction that enters or leaves your Stripe account balance.

Related guide: Balance transaction
types.

**Properties:**

- `Amount`
  - Gross amount of this transaction (in cents (or local equivalent)). A positive value
represents funds charged to another party, and a negative value represents funds sent to
another party.
- `AvailableOn`
  - The date that the transaction's net funds become available in the Stripe balance.
- `BalanceType`
  - The balance that this transaction impacts.
One of: `issuing`, `payments`, `refund_and_dispute_prefunding`, or
`risk_reserved`.
- `Created`
  - Time at which the object was created. Measured in seconds since the Unix epoch.
- `Currency`
  - Three-letter ISO currency
code, in lowercase. Must be a supported
currency.
- `Description`
  - An arbitrary string attached to the object. Often useful for displaying to users.
- `ExchangeRate`
  - If applicable, this transaction uses an exchange rate. If money converts from currency A
to currency B, then the `amount` in currency A, multipled by the
`exchange_rate`, equals the `amount` in currency B. For example, if you charge
a customer 10.00 EUR, the PaymentIntent's `amount` is `1000` and
`currency` is `eur`. If this converts to 12.34 USD in your Stripe account, the
BalanceTransaction's `amount` is `1234`, its `currency` is `usd`,
and the `exchange_rate` is `1.234`.
- `Fee`
  - Fees (in cents (or local equivalent)) paid for this transaction. Represented as a
positive integer when assessed.
- `FeeDetails`
  - Detailed breakdown of fees (in cents (or local equivalent)) paid for this transaction.
- `Id`
  - Unique identifier for the object.
- `Net`
  - Net impact to a Stripe balance (in cents (or local equivalent)). A positive value
represents incrementing a Stripe balance, and a negative value decrementing a Stripe
balance. You can calculate the net impact of a transaction on a balance by `amount`
- `fee`.
- `Object`
  - String representing the object's type. Objects of the same type share the same value.
- `ReportingCategory`
  - Learn more about how reporting categories can
help you understand balance transactions from an accounting perspective.
- `Source`
  - (Expanded)
This transaction relates to the Stripe object.

For more information, see the expand documentation.
- `SourceId`
  - (ID of the IBalanceTransactionSource)
This transaction relates to the Stripe object.
- `Status`
  - The transaction's net funds status in the Stripe balance, which are either
`available` or `pending`.
- `Type`
  - Transaction type: `adjustment`, `advance`, `advance_funding`,
`anticipation_repayment`, `application_fee`, `application_fee_refund`,
`charge`, `climate_order_purchase`, `climate_order_refund`,
`connect_collection_transfer`, `contribution`, `inbound_transfer`,
`inbound_transfer_reversal`, `issuing_authorization_hold`,
`issuing_authorization_release`, `issuing_dispute`,
`issuing_transaction`, `obligation_outbound`,
`obligation_reversal_inbound`, `payment`, `payment_failure_refund`,
`payment_network_reserve_hold`, `payment_network_reserve_release`,
`payment_refund`, `payment_reversal`, `payment_unreconciled`,
`payout`, `payout_cancel`, `payout_failure`,
`payout_minimum_balance_hold`, `payout_minimum_balance_release`,
`refund`, `refund_failure`, `reserve_transaction`, `reserved_funds`,
`reserve_hold`, `reserve_release`, `stripe_fee`, `stripe_fx_fee`,
`stripe_balance_payment_debit`, `stripe_balance_payment_debit_reversal`,
`tax_fee`, `topup`, `topup_reversal`, `transfer`,
`transfer_cancel`, `transfer_failure`, `transfer_refund`, or
`fee_credit_funding`. Learn more about balance transaction
types and what they represent. To classify transactions for accounting purposes,
consider `reporting_category` instead.
One of: `adjustment`, `advance`, `advance_funding`,
`anticipation_repayment`, `application_fee`, `application_fee_refund`,
`charge`, `climate_order_purchase`, `climate_order_refund`,
`connect_collection_transfer`, `contribution`, `fee_credit_funding`,
`inbound_transfer`, `inbound_transfer_reversal`,
`issuing_authorization_hold`, `issuing_authorization_release`,
`issuing_dispute`, `issuing_transaction`, `obligation_outbound`,
`obligation_reversal_inbound`, `payment`, `payment_failure_refund`,
`payment_network_reserve_hold`, `payment_network_reserve_release`,
`payment_refund`, `payment_reversal`, `payment_unreconciled`,
`payout`, `payout_cancel`, `payout_failure`,
`payout_minimum_balance_hold`, `payout_minimum_balance_release`,
`refund`, `refund_failure`, `reserve_hold`, `reserve_release`,
`reserve_transaction`, `reserved_funds`, `stripe_balance_payment_debit`,
`stripe_balance_payment_debit_reversal`, `stripe_fee`, `stripe_fx_fee`,
`tax_fee`, `topup`, `topup_reversal`, `transfer`,
`transfer_cancel`, `transfer_failure`, or `transfer_refund`.


#### `BalanceTransactionService`

**Methods:**

- `Get(string, Stripe.BalanceTransactionGetOptions, Stripe.RequestOptions)`
  - Retrieves the balance transaction with the given ID..

Note that this endpoint previously used the path `/v1/balance/history/:id`..
- `GetAsync(string, Stripe.BalanceTransactionGetOptions, Stripe.RequestOptions, CancellationToken)`
  - Retrieves the balance transaction with the given ID..

Note that this endpoint previously used the path `/v1/balance/history/:id`..
- `List(Stripe.BalanceTransactionListOptions, Stripe.RequestOptions)`
  - Returns a list of transactions that have contributed to the Stripe account balance
(e.g., charges, transfers, and so forth). The transactions are returned in sorted order,
with the most recent transactions appearing first..

Note that this endpoint was previously called “Balance history” and used the path
`/v1/balance/history`..
- `ListAsync(Stripe.BalanceTransactionListOptions, Stripe.RequestOptions, CancellationToken)`
  - Returns a list of transactions that have contributed to the Stripe account balance
(e.g., charges, transfers, and so forth). The transactions are returned in sorted order,
with the most recent transactions appearing first..

Note that this endpoint was previously called “Balance history” and used the path
`/v1/balance/history`..
- `ListAutoPaging(Stripe.BalanceTransactionListOptions, Stripe.RequestOptions)`
  - Returns a list of transactions that have contributed to the Stripe account balance
(e.g., charges, transfers, and so forth). The transactions are returned in sorted order,
with the most recent transactions appearing first..

Note that this endpoint was previously called “Balance history” and used the path
`/v1/balance/history`..
- `ListAutoPagingAsync(Stripe.BalanceTransactionListOptions, Stripe.RequestOptions, CancellationToken)`
  - Returns a list of transactions that have contributed to the Stripe account balance
(e.g., charges, transfers, and so forth). The transactions are returned in sorted order,
with the most recent transactions appearing first..

Note that this endpoint was previously called “Balance history” and used the path
`/v1/balance/history`..


#### `BalanceTransactionListOptions`

**Properties:**

- `Created`
  - Only return transactions that were created during the given date interval.
- `Currency`
  - Only return transactions in a certain currency. Three-letter ISO currency code, in
lowercase. Must be a supported
currency.
- `Payout`
  - For automatic Stripe payouts only, only returns transactions that were paid out on the
specified payout ID.
- `Source`
  - Only returns transactions associated with the given object.
- `Type`
  - Only returns transactions of the given type. One of: `adjustment`, `advance`,
`advance_funding`, `anticipation_repayment`, `application_fee`,
`application_fee_refund`, `charge`, `climate_order_purchase`,
`climate_order_refund`, `connect_collection_transfer`, `contribution`,
`inbound_transfer`, `inbound_transfer_reversal`,
`issuing_authorization_hold`, `issuing_authorization_release`,
`issuing_dispute`, `issuing_transaction`, `obligation_outbound`,
`obligation_reversal_inbound`, `payment`, `payment_failure_refund`,
`payment_network_reserve_hold`, `payment_network_reserve_release`,
`payment_refund`, `payment_reversal`, `payment_unreconciled`,
`payout`, `payout_cancel`, `payout_failure`,
`payout_minimum_balance_hold`, `payout_minimum_balance_release`,
`refund`, `refund_failure`, `reserve_transaction`, `reserved_funds`,
`reserve_hold`, `reserve_release`, `stripe_fee`, `stripe_fx_fee`,
`stripe_balance_payment_debit`, `stripe_balance_payment_debit_reversal`,
`tax_fee`, `topup`, `topup_reversal`, `transfer`,
`transfer_cancel`, `transfer_failure`, `transfer_refund`, or
`fee_credit_funding`.


### Transfer

#### `Transfer`

A `Transfer` object is created when you move funds between Stripe accounts as part
of Connect.

Before April 6, 2017, transfers also represented movement of funds from a Stripe account
to a card or bank account. This behavior has since been split out into a Payout object, with corresponding payout
endpoints. For more information, read about the transfer/payout split.

Related guide: Creating separate
charges and transfers.

**Properties:**

- `Amount`
  - Amount in cents (or local equivalent) to be transferred.
- `AmountReversed`
  - Amount in cents (or local equivalent) reversed (can be less than the amount attribute on
the transfer if a partial reversal was issued).
- `BalanceTransaction`
  - (Expanded)
Balance transaction that describes the impact of this transfer on your account balance.

For more information, see the expand documentation.
- `BalanceTransactionId`
  - (ID of the BalanceTransaction)
Balance transaction that describes the impact of this transfer on your account balance.
- `Created`
  - Time that this record of the transfer was first created.
- `Currency`
  - Three-letter ISO currency
code, in lowercase. Must be a supported
currency.
- `Description`
  - An arbitrary string attached to the object. Often useful for displaying to users.
- `Destination`
  - (Expanded)
ID of the Stripe account the transfer was sent to.

For more information, see the expand documentation.
- `DestinationId`
  - (ID of the Account)
ID of the Stripe account the transfer was sent to.
- `DestinationPayment`
  - (Expanded)
If the destination is a Stripe account, this will be the ID of the payment that the
destination account received for the transfer.

For more information, see the expand documentation.
- `DestinationPaymentId`
  - (ID of the Charge)
If the destination is a Stripe account, this will be the ID of the payment that the
destination account received for the transfer.
- `Id`
  - Unique identifier for the object.
- `Livemode`
  - If the object exists in live mode, the value is `true`. If the object exists in
test mode, the value is `false`.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format.
- `Object`
  - String representing the object's type. Objects of the same type share the same value.
- `Reversals`
  - A list of reversals that have been applied to the transfer.
- `Reversed`
  - Whether the transfer has been fully reversed. If the transfer is only partially
reversed, this attribute will still be false.
- `SourceTransaction`
  - (Expanded)
ID of the charge that was used to fund the transfer. If null, the transfer was funded
from the available balance.

For more information, see the expand documentation.
- `SourceTransactionId`
  - (ID of the Charge)
ID of the charge that was used to fund the transfer. If null, the transfer was funded
from the available balance.
- `SourceType`
  - The source balance this transfer came from. One of `card`, `fpx`, or
`bank_account`.
- `TransferGroup`
  - A string that identifies this transaction as part of a group. See the Connect
documentation for details.


#### `TransferService`

**Methods:**

- `Create(Stripe.TransferCreateOptions, Stripe.RequestOptions)`
  - To send funds from your Stripe account to a connected account, you create a new
transfer object. Your Stripe balance
must be able to cover the transfer amount, or you’ll receive an “Insufficient Funds”
error..
- `CreateAsync(Stripe.TransferCreateOptions, Stripe.RequestOptions, CancellationToken)`
  - To send funds from your Stripe account to a connected account, you create a new
transfer object. Your Stripe balance
must be able to cover the transfer amount, or you’ll receive an “Insufficient Funds”
error..
- `Get(string, Stripe.TransferGetOptions, Stripe.RequestOptions)`
  - Retrieves the details of an existing transfer. Supply the unique transfer ID from
either a transfer creation request or the transfer list, and Stripe will return the
corresponding transfer information..
- `GetAsync(string, Stripe.TransferGetOptions, Stripe.RequestOptions, CancellationToken)`
  - Retrieves the details of an existing transfer. Supply the unique transfer ID from
either a transfer creation request or the transfer list, and Stripe will return the
corresponding transfer information..
- `List(Stripe.TransferListOptions, Stripe.RequestOptions)`
  - Returns a list of existing transfers sent to connected accounts. The transfers are
returned in sorted order, with the most recently created transfers appearing first..
- `ListAsync(Stripe.TransferListOptions, Stripe.RequestOptions, CancellationToken)`
  - Returns a list of existing transfers sent to connected accounts. The transfers are
returned in sorted order, with the most recently created transfers appearing first..
- `ListAutoPaging(Stripe.TransferListOptions, Stripe.RequestOptions)`
  - Returns a list of existing transfers sent to connected accounts. The transfers are
returned in sorted order, with the most recently created transfers appearing first..
- `ListAutoPagingAsync(Stripe.TransferListOptions, Stripe.RequestOptions, CancellationToken)`
  - Returns a list of existing transfers sent to connected accounts. The transfers are
returned in sorted order, with the most recently created transfers appearing first..
- `Update(string, Stripe.TransferUpdateOptions, Stripe.RequestOptions)`
  - Updates the specified transfer by setting the values of the parameters passed. Any
parameters not provided will be left unchanged..

This request accepts only metadata as an argument..
- `UpdateAsync(string, Stripe.TransferUpdateOptions, Stripe.RequestOptions, CancellationToken)`
  - Updates the specified transfer by setting the values of the parameters passed. Any
parameters not provided will be left unchanged..

This request accepts only metadata as an argument..


#### `TransferCreateOptions`

**Properties:**

- `Amount`
  - A positive integer in cents (or local equivalent) representing how much to transfer.
- `Currency`
  - Three-letter ISO code for
currency in lowercase. Must be a supported currency.
- `Description`
  - An arbitrary string attached to the object. Often useful for displaying to users.
- `Destination`
  - The ID of a connected Stripe account. See the Connect
documentation for details.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format. Individual keys can be unset by posting an empty value to
them. All keys can be unset by posting an empty value to `metadata`.
- `SourceTransaction`
  - You can use this parameter to transfer funds from a charge before they are added to your
available balance. A pending balance will transfer immediately but the funds will not
become available until the original charge becomes available. See
the Connect documentation for details.
- `SourceType`
  - The source balance to use for this transfer. One of `bank_account`, `card`, or
`fpx`. For most users, this will default to `card`.
One of: `bank_account`, `card`, or `fpx`.
- `TransferGroup`
  - A string that identifies this transaction as part of a group. See the Connect
documentation for details.


#### `TransferUpdateOptions`

**Properties:**

- `Description`
  - An arbitrary string attached to the object. Often useful for displaying to users.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format. Individual keys can be unset by posting an empty value to
them. All keys can be unset by posting an empty value to `metadata`.


#### `TransferListOptions`

**Properties:**

- `Created`
  - Only return transfers that were created during the given date interval.
- `Destination`
  - Only return transfers for the destination specified by this account ID.
- `TransferGroup`
  - Only return transfers with the specified transfer group.


### Dispute

#### `Dispute`

A dispute occurs when a customer questions your charge with their card issuer. When this
happens, you have the opportunity to respond to the dispute with evidence that shows
that the charge is legitimate.

Related guide: Disputes and fraud.

**Properties:**

- `Amount`
  - Disputed amount. Usually the amount of the charge, but it can differ (usually because of
currency fluctuation or because only part of the order is disputed).
- `BalanceTransactions`
  - List of zero, one, or two balance transactions that show funds withdrawn and reinstated
to your Stripe account as a result of this dispute.
- `Charge`
  - (Expanded)
ID of the charge that's disputed.

For more information, see the expand documentation.
- `ChargeId`
  - (ID of the Charge)
ID of the charge that's disputed.
- `Created`
  - Time at which the object was created. Measured in seconds since the Unix epoch.
- `Currency`
  - Three-letter ISO currency
code, in lowercase. Must be a supported
currency.
- `EnhancedEligibilityTypes`
  - List of eligibility types that are included in `enhanced_evidence`.
One of: `visa_compelling_evidence_3`, or `visa_compliance`.
- `Id`
  - Unique identifier for the object.
- `IsChargeRefundable`
  - If true, it's still possible to refund the disputed payment. After the payment has been
fully refunded, no further funds are withdrawn from your Stripe account as a result of
this dispute.
- `Livemode`
  - If the object exists in live mode, the value is `true`. If the object exists in
test mode, the value is `false`.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format.
- `NetworkReasonCode`
  - Network-dependent reason code for the dispute.
- `Object`
  - String representing the object's type. Objects of the same type share the same value.
- `PaymentIntent`
  - (Expanded)
ID of the PaymentIntent that's disputed.

For more information, see the expand documentation.
- `PaymentIntentId`
  - (ID of the PaymentIntent)
ID of the PaymentIntent that's disputed.
- `Reason`
  - Reason given by cardholder for dispute. Possible values are `bank_cannot_process`,
`check_returned`, `credit_not_processed`, `customer_initiated`,
`debit_not_authorized`, `duplicate`, `fraudulent`, `general`,
`incorrect_account_details`, `insufficient_funds`, `noncompliant`,
`product_not_received`, `product_unacceptable`, `subscription_canceled`,
or `unrecognized`. Learn more about dispute reasons.
- `Status`
  - The current status of a dispute. Possible values include:`warning_needs_response`,
`warning_under_review`, `warning_closed`, `needs_response`,
`under_review`, `won`, `lost`, or `prevented`.
One of: `lost`, `needs_response`, `prevented`, `under_review`,
`warning_closed`, `warning_needs_response`, `warning_under_review`, or
`won`.


#### `Dispute`

As a card issuer, you can dispute
transactions that the cardholder does not recognize, suspects to be fraudulent, or has
other issues with.

Related guide: Issuing
disputes.

**Properties:**

- `Amount`
  - Disputed amount in the card's currency and in the smallest currency unit.
Usually the amount of the `transaction`, but can differ (usually because of
currency fluctuation).
- `BalanceTransactions`
  - List of balance transactions associated with the dispute.
- `Created`
  - Time at which the object was created. Measured in seconds since the Unix epoch.
- `Currency`
  - The currency the `transaction` was made in.
- `Id`
  - Unique identifier for the object.
- `Livemode`
  - If the object exists in live mode, the value is `true`. If the object exists in
test mode, the value is `false`.
- `LossReason`
  - The enum that describes the dispute loss outcome. If the dispute is not lost, this field
will be absent. New enum values may be added in the future, so be sure to handle unknown
values.
One of: `cardholder_authentication_issuer_liability`,
`eci5_token_transaction_with_tavv`, `excess_disputes_in_timeframe`,
`has_not_met_the_minimum_dispute_amount_requirements`,
`invalid_duplicate_dispute`, `invalid_incorrect_amount_dispute`,
`invalid_no_authorization`, `invalid_use_of_disputes`,
`merchandise_delivered_or_shipped`, `merchandise_or_service_as_described`,
`not_cancelled`, `other`, `refund_issued`,
`submitted_beyond_allowable_time_limit`, `transaction_3ds_required`,
`transaction_approved_after_prior_fraud_dispute`, `transaction_authorized`,
`transaction_electronically_read`,
`transaction_qualifies_for_visa_easy_payment_service`, or
`transaction_unattended`.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format.
- `Object`
  - String representing the object's type. Objects of the same type share the same value.
- `Status`
  - Current status of the dispute.
One of: `expired`, `lost`, `submitted`, `unsubmitted`, or
`won`.
- `Transaction`
  - (Expanded)
The transaction being disputed.

For more information, see the expand documentation.
- `TransactionId`
  - (ID of the Transaction)
The transaction being disputed.
- `Treasury`
  - Treasury details related to this
dispute if it was created on a FinancialAccount.


#### `DisputeService`

**Methods:**

- `Create(Stripe.Issuing.DisputeCreateOptions, Stripe.RequestOptions)`
  - Creates an Issuing `Dispute` object. Individual pieces of evidence within the
`evidence` object are optional at this point. Stripe only validates that required
evidence is present during submission. Refer to Dispute
reasons and evidence for more details about evidence requirements..
- `CreateAsync(Stripe.Issuing.DisputeCreateOptions, Stripe.RequestOptions, CancellationToken)`
  - Creates an Issuing `Dispute` object. Individual pieces of evidence within the
`evidence` object are optional at this point. Stripe only validates that required
evidence is present during submission. Refer to Dispute
reasons and evidence for more details about evidence requirements..
- `Get(string, Stripe.Issuing.DisputeGetOptions, Stripe.RequestOptions)`
  - Retrieves an Issuing `Dispute` object..
- `GetAsync(string, Stripe.Issuing.DisputeGetOptions, Stripe.RequestOptions, CancellationToken)`
  - Retrieves an Issuing `Dispute` object..
- `List(Stripe.Issuing.DisputeListOptions, Stripe.RequestOptions)`
  - Returns a list of Issuing `Dispute` objects. The objects are sorted in
descending order by creation date, with the most recently created object appearing
first..
- `ListAsync(Stripe.Issuing.DisputeListOptions, Stripe.RequestOptions, CancellationToken)`
  - Returns a list of Issuing `Dispute` objects. The objects are sorted in
descending order by creation date, with the most recently created object appearing
first..
- `ListAutoPaging(Stripe.Issuing.DisputeListOptions, Stripe.RequestOptions)`
  - Returns a list of Issuing `Dispute` objects. The objects are sorted in
descending order by creation date, with the most recently created object appearing
first..
- `ListAutoPagingAsync(Stripe.Issuing.DisputeListOptions, Stripe.RequestOptions, CancellationToken)`
  - Returns a list of Issuing `Dispute` objects. The objects are sorted in
descending order by creation date, with the most recently created object appearing
first..
- `Submit(string, Stripe.Issuing.DisputeSubmitOptions, Stripe.RequestOptions)`
  - Submits an Issuing `Dispute` to the card network. Stripe validates that all
evidence fields required for the dispute’s reason are present. For more details, see Dispute
reasons and evidence..
- `SubmitAsync(string, Stripe.Issuing.DisputeSubmitOptions, Stripe.RequestOptions, CancellationToken)`
  - Submits an Issuing `Dispute` to the card network. Stripe validates that all
evidence fields required for the dispute’s reason are present. For more details, see Dispute
reasons and evidence..
- `Update(string, Stripe.Issuing.DisputeUpdateOptions, Stripe.RequestOptions)`
  - Updates the specified Issuing `Dispute` object by setting the values of the
parameters passed. Any parameters not provided will be left unchanged. Properties on the
`evidence` object can be unset by passing in an empty string..
- `UpdateAsync(string, Stripe.Issuing.DisputeUpdateOptions, Stripe.RequestOptions, CancellationToken)`
  - Updates the specified Issuing `Dispute` object by setting the values of the
parameters passed. Any parameters not provided will be left unchanged. Properties on the
`evidence` object can be unset by passing in an empty string..


#### `DisputeService`

**Methods:**

- `Close(string, Stripe.DisputeCloseOptions, Stripe.RequestOptions)`
  - Closing the dispute for a charge indicates that you do not have any evidence to
submit and are essentially dismissing the dispute, acknowledging it as lost..

The status of the dispute will change from `needs_response` to `lost`.
Closing a dispute is irreversible..
- `CloseAsync(string, Stripe.DisputeCloseOptions, Stripe.RequestOptions, CancellationToken)`
  - Closing the dispute for a charge indicates that you do not have any evidence to
submit and are essentially dismissing the dispute, acknowledging it as lost..

The status of the dispute will change from `needs_response` to `lost`.
Closing a dispute is irreversible..
- `Get(string, Stripe.DisputeGetOptions, Stripe.RequestOptions)`
  - Retrieves the dispute with the given ID..
- `GetAsync(string, Stripe.DisputeGetOptions, Stripe.RequestOptions, CancellationToken)`
  - Retrieves the dispute with the given ID..
- `List(Stripe.DisputeListOptions, Stripe.RequestOptions)`
  - Returns a list of your disputes..
- `ListAsync(Stripe.DisputeListOptions, Stripe.RequestOptions, CancellationToken)`
  - Returns a list of your disputes..
- `ListAutoPaging(Stripe.DisputeListOptions, Stripe.RequestOptions)`
  - Returns a list of your disputes..
- `ListAutoPagingAsync(Stripe.DisputeListOptions, Stripe.RequestOptions, CancellationToken)`
  - Returns a list of your disputes..
- `Update(string, Stripe.DisputeUpdateOptions, Stripe.RequestOptions)`
  - When you get a dispute, contacting your customer is always the best first step. If
that doesn’t work, you can submit evidence to help us resolve the dispute in your favor.
You can do this in your dashboard,
but if you prefer, you can use the API to submit evidence programmatically..

Depending on your dispute type, different evidence fields will give you a better
chance of winning your dispute. To figure out which evidence fields to provide, see our
guide to dispute types..
- `UpdateAsync(string, Stripe.DisputeUpdateOptions, Stripe.RequestOptions, CancellationToken)`
  - When you get a dispute, contacting your customer is always the best first step. If
that doesn’t work, you can submit evidence to help us resolve the dispute in your favor.
You can do this in your dashboard,
but if you prefer, you can use the API to submit evidence programmatically..

Depending on your dispute type, different evidence fields will give you a better
chance of winning your dispute. To figure out which evidence fields to provide, see our
guide to dispute types..


#### `DisputeCreateOptions`

**Properties:**

- `Amount`
  - The dispute amount in the card's currency and in the smallest currency unit. If
not set, defaults to the full transaction amount.
- `Evidence`
  - Evidence provided for the dispute.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format. Individual keys can be unset by posting an empty value to
them. All keys can be unset by posting an empty value to `metadata`.
- `Transaction`
  - The ID of the issuing transaction to create a dispute for. For transaction on Treasury
FinancialAccounts, use `treasury.received_debit`.
- `Treasury`
  - Params for disputes related to Treasury FinancialAccounts.


#### `DisputeUpdateOptions`

**Properties:**

- `Amount`
  - The dispute amount in the card's currency and in the smallest currency unit.
- `Evidence`
  - Evidence provided for the dispute.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format. Individual keys can be unset by posting an empty value to
them. All keys can be unset by posting an empty value to `metadata`.


#### `DisputeUpdateOptions`

**Properties:**

- `Evidence`
  - Evidence to upload, to respond to a dispute. Updating any field in the hash will submit
all fields in the hash for review. The combined character count of all fields is limited
to 150,000.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format. Individual keys can be unset by posting an empty value to
them. All keys can be unset by posting an empty value to `metadata`.
- `Submit`
  - Whether to immediately submit evidence to the bank. If `false`, evidence is staged
on the dispute. Staged evidence is visible in the API and Dashboard, and can be
submitted to the bank by making another request with this attribute set to `true`
(the default).


#### `DisputeListOptions`

**Properties:**

- `Created`
  - Only return Issuing disputes that were created during the given date interval.
- `Status`
  - Select Issuing disputes with the given status.
One of: `expired`, `lost`, `submitted`, `unsubmitted`, or
`won`.
- `Transaction`
  - Select the Issuing dispute for the given transaction.


#### `DisputeListOptions`

**Properties:**

- `Charge`
  - Only return disputes associated to the charge specified by this charge ID.
- `Created`
  - Only return disputes that were created during the given date interval.
- `PaymentIntent`
  - Only return disputes associated to the PaymentIntent specified by this PaymentIntent ID.


### Token

#### `Token`

An issuing token object is created when an issued card is added to a digital wallet. As
a card issuer, you can view and manage these
tokens through Stripe.

**Properties:**

- `Card`
  - (Expanded)
Card associated with this token.

For more information, see the expand documentation.
- `CardId`
  - (ID of the Card)
Card associated with this token.
- `Created`
  - Time at which the object was created. Measured in seconds since the Unix epoch.
- `DeviceFingerprint`
  - The hashed ID derived from the device ID from the card network associated with the
token.
- `Id`
  - Unique identifier for the object.
- `Last4`
  - The last four digits of the token.
- `Livemode`
  - If the object exists in live mode, the value is `true`. If the object exists in
test mode, the value is `false`.
- `Network`
  - The token service provider / card network associated with the token.
One of: `mastercard`, or `visa`.
- `NetworkUpdatedAt`
  - Time at which the token was last updated by the card network. Measured in seconds since
the Unix epoch.
- `Object`
  - String representing the object's type. Objects of the same type share the same value.
- `Status`
  - The usage state of the token.
One of: `active`, `deleted`, `requested`, or `suspended`.
- `WalletProvider`
  - The digital wallet for this token, if one was used.
One of: `apple_pay`, `google_pay`, or `samsung_pay`.


#### `Token`

Tokenization is the process Stripe uses to collect sensitive card or bank account
details, or personally identifiable information (PII), directly from your customers in a
secure manner. A token representing this information is returned to your server to use.
Use our recommended payments integrations
to perform this process on the client-side. This guarantees that no sensitive card data
touches your server, and allows your integration to operate in a PCI-compliant way.

If you can't use client-side tokenization, you can also create tokens using the API with
either your publishable or secret API key. If your integration uses this method, you're
responsible for any PCI compliance that it might require, and you must keep your secret
API key safe. Unlike with client-side tokenization, your customer's information isn't
sent directly to Stripe, so we can't determine how it's handled or stored.

You can't store or use tokens more than once. To store card or bank account information
for later use, create Customer
objects or External accounts. Radar, our integrated solution for automatic
fraud protection, performs best with integrations that use client-side tokenization.

**Properties:**

- `BankAccount`
  - These bank accounts are payment methods on `Customer` objects.

On the other hand External
Accounts are transfer destinations on `Account` objects for connected accounts.
They can be bank accounts or debit cards as well, and are documented in the links above.

Related guide: Bank debits
and transfers.
- `Card`
  - You can store multiple cards on a customer in order to charge the customer later. You
can also store multiple debit cards on a recipient in order to transfer to those cards
later.

Related guide: Card payments with
Sources.
- `ClientIp`
  - IP address of the client that generates the token.
- `Created`
  - Time at which the object was created. Measured in seconds since the Unix epoch.
- `Id`
  - Unique identifier for the object.
- `Livemode`
  - If the object exists in live mode, the value is `true`. If the object exists in
test mode, the value is `false`.
- `Object`
  - String representing the object's type. Objects of the same type share the same value.
- `Type`
  - Type of the token: `account`, `bank_account`, `card`, or `pii`.
- `Used`
  - Determines if you have already used this token (you can only use tokens once).


#### `TokenService`

**Methods:**

- `Get(string, Stripe.Issuing.TokenGetOptions, Stripe.RequestOptions)`
  - Retrieves an Issuing `Token` object..
- `GetAsync(string, Stripe.Issuing.TokenGetOptions, Stripe.RequestOptions, CancellationToken)`
  - Retrieves an Issuing `Token` object..
- `List(Stripe.Issuing.TokenListOptions, Stripe.RequestOptions)`
  - Lists all Issuing `Token` objects for a given card..
- `ListAsync(Stripe.Issuing.TokenListOptions, Stripe.RequestOptions, CancellationToken)`
  - Lists all Issuing `Token` objects for a given card..
- `ListAutoPaging(Stripe.Issuing.TokenListOptions, Stripe.RequestOptions)`
  - Lists all Issuing `Token` objects for a given card..
- `ListAutoPagingAsync(Stripe.Issuing.TokenListOptions, Stripe.RequestOptions, CancellationToken)`
  - Lists all Issuing `Token` objects for a given card..
- `Update(string, Stripe.Issuing.TokenUpdateOptions, Stripe.RequestOptions)`
  - Attempts to update the specified Issuing `Token` object to the status
specified..
- `UpdateAsync(string, Stripe.Issuing.TokenUpdateOptions, Stripe.RequestOptions, CancellationToken)`
  - Attempts to update the specified Issuing `Token` object to the status
specified..


#### `TokenService`

**Methods:**

- `Create(Stripe.TokenCreateOptions, Stripe.RequestOptions)`
  - Creates a single-use token that represents a bank account’s details. You can use this
token with any v1 API method in place of a bank account dictionary. You can only use
this token once. To do so, attach it to a connected account where controller.requirement_collection
is `application`, which includes Custom accounts..
- `CreateAsync(Stripe.TokenCreateOptions, Stripe.RequestOptions, CancellationToken)`
  - Creates a single-use token that represents a bank account’s details. You can use this
token with any v1 API method in place of a bank account dictionary. You can only use
this token once. To do so, attach it to a connected account where controller.requirement_collection
is `application`, which includes Custom accounts..
- `Get(string, Stripe.TokenGetOptions, Stripe.RequestOptions)`
  - Retrieves the token with the given ID..
- `GetAsync(string, Stripe.TokenGetOptions, Stripe.RequestOptions, CancellationToken)`
  - Retrieves the token with the given ID..


#### `TokenCreateOptions`

**Properties:**

- `Account`
  - Information for the account this token represents.
- `BankAccount`
  - The bank account this token will represent.
- `Card`
  - The card this token will represent. If you also pass in a customer, the card must be the
ID of a card belonging to the customer. Otherwise, if you do not pass in a customer,
this is a dictionary containing a user's credit card details, with the options described
below.
- `Customer`
  - Create a token for the customer, which is owned by the application's account. You can
only use this with an OAuth
access token or Stripe-Account header. Learn
more about cloning saved
payment methods.
- `CvcUpdate`
  - The updated CVC value this token represents.
- `Person`
  - Information for the person this token represents.
- `Pii`
  - The PII this token represents.


#### `TokenUpdateOptions`

**Properties:**

- `Status`
  - Specifies which status the token should be updated to.
One of: `active`, `deleted`, or `suspended`.


#### `TokenListOptions`

**Properties:**

- `Card`
  - The Issuing card identifier to list tokens for.
- `Created`
  - Only return Issuing tokens that were created during the given date interval.
- `Status`
  - Select Issuing tokens with the given status.
One of: `active`, `deleted`, `requested`, or `suspended`.


### Checkout.Session

#### `Session`

A Checkout Session represents your customer's session as they pay for one-time purchases
or subscriptions through Checkout or Payment Links. We recommend
creating a new Session each time your customer attempts to pay.

Once payment is successful, the Checkout Session will contain a reference to the Customer, and either the successful PaymentIntent or an active Subscription.

You can create a Checkout Session on your server and redirect to its URL to begin
Checkout.

Related guide: Checkout
quickstart.

**Properties:**

- `AdaptivePricing`
  - Settings for price localization with Adaptive Pricing.
- `AfterExpiration`
  - When set, provides configuration for actions to take if this Checkout Session expires.
- `AllowPromotionCodes`
  - Enables user redeemable promotion codes.
- `AmountSubtotal`
  - Total of all items before discounts or taxes are applied.
- `AmountTotal`
  - Total of all items after discounts and taxes are applied.
- `BillingAddressCollection`
  - Describes whether Checkout should collect the customer's billing address. Defaults to
`auto`.
One of: `auto`, or `required`.
- `CancelUrl`
  - If set, Checkout displays a back button and customers will be directed to this URL if
they decide to cancel payment and return to your website.
- `ClientReferenceId`
  - A unique string to reference the Checkout Session. This can be a customer ID, a cart ID,
or similar, and can be used to reconcile the Session with your internal systems.
- `ClientSecret`
  - The client secret of your Checkout Session. Applies to Checkout Sessions with
`ui_mode: embedded_page` or `ui_mode: elements`. For `ui_mode:
embedded_page`, the client secret is to be used when initializing Stripe.js embedded
checkout. For `ui_mode: elements`, use the client secret with initCheckout on your front
end.
- `CollectedInformation`
  - Information about the customer collected within the Checkout Session.
- `Consent`
  - Results of `consent_collection` for this session.
- `ConsentCollection`
  - When set, provides configuration for the Checkout Session to gather active consent from
customers.
- `Created`
  - Time at which the object was created. Measured in seconds since the Unix epoch.
- `Currency`
  - Three-letter ISO currency
code, in lowercase. Must be a supported
currency.
- `CurrencyConversion`
  - Currency conversion details for Adaptive Pricing
sessions created before 2025-03-31.
- `CustomFields`
  - Collect additional information from your customer using custom fields. Up to 3 fields
are supported. You can't set this parameter if `ui_mode` is `custom`.
- `Customer`
  - (Expanded)
The ID of the customer for this Session. For Checkout Sessions in `subscription`
mode or Checkout Sessions with `customer_creation` set as `always` in
`payment` mode, Checkout will create a new customer object based on information
provided during the payment flow unless an existing customer was provided when the
Session was created.

For more information, see the expand documentation.
- `CustomerAccount`
  - The ID of the account for this Session.
- `CustomerCreation`
  - Configure whether a Checkout Session creates a Customer when the Checkout Session
completes.
One of: `always`, or `if_required`.
- `CustomerDetails`
  - The customer details including the customer's tax exempt status and the customer's tax
IDs. Customer's address details are not present on Sessions in `setup` mode.
- `CustomerEmail`
  - If provided, this value will be used when the Customer object is created. If not
provided, customers will be asked to enter their email address. Use this parameter to
prefill customer data if you already have an email on file. To access information about
the customer once the payment flow is complete, use the `customer` attribute.
- `CustomerId`
  - (ID of the Customer)
The ID of the customer for this Session. For Checkout Sessions in `subscription`
mode or Checkout Sessions with `customer_creation` set as `always` in
`payment` mode, Checkout will create a new customer object based on information
provided during the payment flow unless an existing customer was provided when the
Session was created.
- `Discounts`
  - List of coupons and promotion codes attached to the Checkout Session.
- `ExcludedPaymentMethodTypes`
  - A list of the types of payment methods (e.g., `card`) that should be excluded from
this Checkout Session. This should only be used when payment methods for this Checkout
Session are managed through the Stripe Dashboard.
- `ExpiresAt`
  - The timestamp at which the Checkout Session will expire.
- `Id`
  - Unique identifier for the object.
- `IntegrationIdentifier`
  - The integration identifier for this Checkout Session. Multiple Checkout Sessions can
have the same integration identifier.
- `Invoice`
  - (Expanded)
ID of the invoice created by the Checkout Session, if it exists.

For more information, see the expand documentation.
- `InvoiceCreation`
  - Details on the state of invoice creation for the Checkout Session.
- `InvoiceId`
  - (ID of the Invoice)
ID of the invoice created by the Checkout Session, if it exists.
- `LineItems`
  - The line items purchased by the customer.
- `Livemode`
  - If the object exists in live mode, the value is `true`. If the object exists in
test mode, the value is `false`.
- `Locale`
  - The IETF language tag of the locale Checkout is displayed in. If blank or `auto`,
the browser's locale is used.
One of: `auto`, `bg`, `cs`, `da`, `de`, `el`, `en`,
`en-GB`, `es`, `es-419`, `et`, `fi`, `fil`, `fr`,
`fr-CA`, `hr`, `hu`, `id`, `it`, `ja`, `ko`,
`lt`, `lv`, `ms`, `mt`, `nb`, `nl`, `pl`, `pt`,
`pt-BR`, `ro`, `ru`, `sk`, `sl`, `sv`, `th`,
`tr`, `vi`, `zh`, `zh-HK`, or `zh-TW`.
- `ManagedPayments`
  - Settings for Managed Payments for this Checkout Session and resulting PaymentIntents, Invoices, and Subscriptions.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format.
- `Mode`
  - The mode of the Checkout Session.
One of: `payment`, `setup`, or `subscription`.
- `Object`
  - String representing the object's type. Objects of the same type share the same value.
- `OptionalItems`
  - The optional items presented to the customer at checkout.
- `OriginContext`
  - Where the user is coming from. This informs the optimizations that are applied to the
session.
One of: `mobile_app`, or `web`.
- `PaymentIntent`
  - (Expanded)
The ID of the PaymentIntent for Checkout Sessions in `payment` mode. You can't
confirm or cancel the PaymentIntent for a Checkout Session. To cancel, expire the Checkout
Session instead.

For more information, see the expand documentation.
- `PaymentIntentId`
  - (ID of the PaymentIntent)
The ID of the PaymentIntent for Checkout Sessions in `payment` mode. You can't
confirm or cancel the PaymentIntent for a Checkout Session. To cancel, expire the Checkout
Session instead.
- `PaymentLink`
  - (Expanded)
The ID of the Payment Link that created this Session.

For more information, see the expand documentation.
- `PaymentLinkId`
  - (ID of the PaymentLink)
The ID of the Payment Link that created this Session.
- `PaymentMethodCollection`
  - Configure whether a Checkout Session should collect a payment method. Defaults to
`always`.
One of: `always`, or `if_required`.
- `PaymentMethodConfigurationDetails`
  - Information about the payment method configuration used for this Checkout session if
using dynamic payment methods.
- `PaymentMethodOptions`
  - Payment-method-specific configuration for the PaymentIntent or SetupIntent of this
CheckoutSession.
- `PaymentMethodTypes`
  - A list of the types of payment methods (e.g. card) this Checkout Session is allowed to
accept.
- `PaymentStatus`
  - The payment status of the Checkout Session, one of `paid`, `unpaid`, or
`no_payment_required`. You can use this value to decide when to fulfill your
customer's order.
One of: `no_payment_required`, `paid`, or `unpaid`.
- `Permissions`
  - This property is used to set up permissions for various actions (e.g., update) on the
CheckoutSession object.

For specific permissions, please refer to their dedicated subsections, such as
`permissions.update_shipping_details`.
- `RecoveredFrom`
  - The ID of the original expired Checkout Session that triggered the recovery flow.
- `RedirectOnCompletion`
  - This parameter applies to `ui_mode: embedded_page`. Learn more about the redirect
behavior of embedded sessions. Defaults to `always`.
One of: `always`, `if_required`, or `never`.
- `ReturnUrl`
  - Applies to Checkout Sessions with `ui_mode: embedded_page` or `ui_mode:
elements`. The URL to redirect your customer back to after they authenticate or
cancel their payment on the payment method's app or site.
- `SavedPaymentMethodOptions`
  - Controls saved payment method settings for the session. Only available in `payment`
and `subscription` mode.
- `SetupIntent`
  - (Expanded)
The ID of the SetupIntent for Checkout Sessions in `setup` mode. You can't confirm
or cancel the SetupIntent for a Checkout Session. To cancel, expire the Checkout
Session instead.

For more information, see the expand documentation.
- `SetupIntentId`
  - (ID of the SetupIntent)
The ID of the SetupIntent for Checkout Sessions in `setup` mode. You can't confirm
or cancel the SetupIntent for a Checkout Session. To cancel, expire the Checkout
Session instead.
- `ShippingAddressCollection`
  - When set, provides configuration for Checkout to collect a shipping address from a
customer.
- `ShippingCost`
  - The details of the customer cost of shipping, including the customer chosen
ShippingRate.
- `ShippingOptions`
  - The shipping rate options applied to this Session.
- `Status`
  - The status of the Checkout Session, one of `open`, `complete`, or
`expired`.
One of: `complete`, `expired`, or `open`.
- `SubmitType`
  - Describes the type of transaction being performed by Checkout in order to customize
relevant text on the page, such as the submit button. `submit_type` can only be
specified on Checkout Sessions in `payment` mode. If blank or `auto`,
`pay` is used.
One of: `auto`, `book`, `donate`, `pay`, or `subscribe`.
- `Subscription`
  - (Expanded)
The ID of the Subscription for
Checkout Sessions in `subscription` mode.

For more information, see the expand documentation.
- `SubscriptionId`
  - (ID of the Subscription)
The ID of the Subscription for
Checkout Sessions in `subscription` mode.
- `SuccessUrl`
  - The URL the customer will be directed to after the payment or subscription creation is
successful.
- `TotalDetails`
  - Tax and discount details for the computed total amount.
- `UiMode`
  - The UI mode of the Session. Defaults to `hosted_page`.
One of: `elements`, `embedded_page`, `form`, or `hosted_page`.
- `Url`
  - The URL to the Checkout Session. Applies to Checkout Sessions with `ui_mode:
hosted_page`. Redirect customers to this URL to take them to Checkout. If you’re
using Custom
Domains, the URL will use your subdomain. Otherwise, it’ll use
`checkout.stripe.com.` This value is only present when the session is active.
- `WalletOptions`
  - Wallet-specific configuration for this Checkout Session.


#### `SessionService`

**Methods:**

- `Create(Stripe.Checkout.SessionCreateOptions, Stripe.RequestOptions)`
  - Creates a Checkout Session object..
- `CreateAsync(Stripe.Checkout.SessionCreateOptions, Stripe.RequestOptions, CancellationToken)`
  - Creates a Checkout Session object..
- `Expire(string, Stripe.Checkout.SessionExpireOptions, Stripe.RequestOptions)`
  - A Checkout Session can be expired when it is in one of these statuses: `open`.

After it expires, a customer can’t complete a Checkout Session and customers loading
the Checkout Session see a message saying the Checkout Session is expired..
- `ExpireAsync(string, Stripe.Checkout.SessionExpireOptions, Stripe.RequestOptions, CancellationToken)`
  - A Checkout Session can be expired when it is in one of these statuses: `open`.

After it expires, a customer can’t complete a Checkout Session and customers loading
the Checkout Session see a message saying the Checkout Session is expired..
- `Get(string, Stripe.Checkout.SessionGetOptions, Stripe.RequestOptions)`
  - Retrieves a Checkout Session object..
- `GetAsync(string, Stripe.Checkout.SessionGetOptions, Stripe.RequestOptions, CancellationToken)`
  - Retrieves a Checkout Session object..
- `List(Stripe.Checkout.SessionListOptions, Stripe.RequestOptions)`
  - Returns a list of Checkout Sessions..
- `ListAsync(Stripe.Checkout.SessionListOptions, Stripe.RequestOptions, CancellationToken)`
  - Returns a list of Checkout Sessions..
- `ListAutoPaging(Stripe.Checkout.SessionListOptions, Stripe.RequestOptions)`
  - Returns a list of Checkout Sessions..
- `ListAutoPagingAsync(Stripe.Checkout.SessionListOptions, Stripe.RequestOptions, CancellationToken)`
  - Returns a list of Checkout Sessions..
- `ListLineItems(string, Stripe.Checkout.SessionLineItemListOptions, Stripe.RequestOptions)`
  - When retrieving a Checkout Session, there is an includable
line_items property containing the first handful of those items. There
is also a URL where you can retrieve the full (paginated) list of line items..
- `ListLineItemsAsync(string, Stripe.Checkout.SessionLineItemListOptions, Stripe.RequestOptions, CancellationToken)`
  - When retrieving a Checkout Session, there is an includable
line_items property containing the first handful of those items. There
is also a URL where you can retrieve the full (paginated) list of line items..
- `ListLineItemsAutoPaging(string, Stripe.Checkout.SessionLineItemListOptions, Stripe.RequestOptions)`
  - When retrieving a Checkout Session, there is an includable
line_items property containing the first handful of those items. There
is also a URL where you can retrieve the full (paginated) list of line items..
- `ListLineItemsAutoPagingAsync(string, Stripe.Checkout.SessionLineItemListOptions, Stripe.RequestOptions, CancellationToken)`
  - When retrieving a Checkout Session, there is an includable
line_items property containing the first handful of those items. There
is also a URL where you can retrieve the full (paginated) list of line items..
- `Update(string, Stripe.Checkout.SessionUpdateOptions, Stripe.RequestOptions)`
  - Updates a Checkout Session object..

Related guide: Dynamically update a
Checkout Session.
- `UpdateAsync(string, Stripe.Checkout.SessionUpdateOptions, Stripe.RequestOptions, CancellationToken)`
  - Updates a Checkout Session object..

Related guide: Dynamically update a
Checkout Session.


#### `SessionCreateOptions`

**Properties:**

- `AdaptivePricing`
  - Settings for price localization with Adaptive Pricing.
- `AfterExpiration`
  - Configure actions after a Checkout Session has expired. You can't set this parameter if
`ui_mode` is `elements`.
- `AllowPromotionCodes`
  - Enables user redeemable promotion codes.
- `AutomaticTax`
  - Settings for automatic tax lookup for this session and resulting payments, invoices, and
subscriptions.
- `BillingAddressCollection`
  - Specify whether Checkout should collect the customer's billing address. Defaults to
`auto`.
One of: `auto`, or `required`.
- `BrandingSettings`
  - The branding settings for the Checkout Session. This parameter is not allowed if ui_mode
is `elements`.
- `CancelUrl`
  - If set, Checkout displays a back button and customers will be directed to this URL if
they decide to cancel payment and return to your website. This parameter is not allowed
if ui_mode is `embedded_page` or `elements`.
- `ClientReferenceId`
  - A unique string to reference the Checkout Session. This can be a customer ID, a cart ID,
or similar, and can be used to reconcile the session with your internal systems.
- `ConsentCollection`
  - Configure fields for the Checkout Session to gather active consent from customers.
- `Currency`
  - Three-letter ISO currency
code, in lowercase. Must be a supported
currency. Required in `setup` mode when `payment_method_types` is not set.
- `CustomFields`
  - Collect additional information from your customer using custom fields. Up to 3 fields
are supported. You can't set this parameter if `ui_mode` is `custom`.
- `CustomText`
  - Display additional text for your customers using custom text. You can't set this
parameter if `ui_mode` is `custom`.
- `Customer`
  - ID of an existing Customer, if one exists. In `payment` mode, the customer’s most
recently saved card payment method will be used to prefill the email, name, card
details, and billing address on the Checkout page. In `subscription` mode, the
customer’s default
payment method will be used if it’s a card, otherwise the most recently saved card
will be used. A valid billing address, billing name and billing email are required on
the payment method for Checkout to prefill the customer's card details.

If the Customer already has a valid email set,
the email will be prefilled and not editable in Checkout. If the Customer does not have
a valid `email`, Checkout will set the email entered during the session on the
Customer.

If blank for Checkout Sessions in `subscription` mode or with
`customer_creation` set as `always` in `payment` mode, Checkout will
create a new Customer object based on information provided during the payment flow.

You can set `payment_intent_data.setup_future_usage`
to have Checkout automatically attach the payment method to the Customer you pass in for
future reuse.
- `CustomerAccount`
  - ID of an existing Account, if one exists. Has the same behavior as `customer`.
- `CustomerCreation`
  - Configure whether a Checkout Session creates a Customer during Session confirmation.

When a Customer is not created, you can still retrieve email, address, and other
customer data entered in Checkout with customer_details.

Sessions that don't create Customers instead are grouped by guest customers in
the Dashboard. Promotion codes limited to first time customers will return invalid for
these Sessions.

Can only be set in `payment` and `setup` mode.
One of: `always`, or `if_required`.
- `CustomerEmail`
  - If provided, this value will be used when the Customer object is created. If not
provided, customers will be asked to enter their email address. Use this parameter to
prefill customer data if you already have an email on file. To access information about
the customer once a session is complete, use the `customer` field.
- `CustomerUpdate`
  - Controls what fields on Customer can be updated by the Checkout Session. Can only be
provided when `customer` is provided.
- `Discounts`
  - The coupon or promotion code to apply to this Session. Currently, only up to one may be
specified.
- `ExcludedPaymentMethodTypes`
  - A list of the types of payment methods (e.g., `card`) that should be excluded from
this Checkout Session. This should only be used when payment methods for this Checkout
Session are managed through the Stripe Dashboard.
One of: `acss_debit`, `affirm`, `afterpay_clearpay`, `alipay`,
`alma`, `amazon_pay`, `au_becs_debit`, `bacs_debit`,
`bancontact`, `billie`, `bizum`, `blik`, `boleto`, `card`,
`cashapp`, `crypto`, `customer_balance`, `eps`, `fpx`,
`giropay`, `grabpay`, `ideal`, `kakao_pay`, `klarna`,
`konbini`, `kr_card`, `mb_way`, `mobilepay`, `multibanco`,
`naver_pay`, `nz_bank_account`, `oxxo`, `p24`, `pay_by_bank`,
`payco`, `paynow`, `paypal`, `payto`, `pix`, `promptpay`,
`revolut_pay`, `samsung_pay`, `satispay`, `scalapay`,
`sepa_debit`, `sofort`, `sunbit`, `swish`, `twint`, `upi`,
`us_bank_account`, `wechat_pay`, or `zip`.
- `ExpiresAt`
  - The Epoch time in seconds at which the Checkout Session will expire. It can be anywhere
from 30 minutes to 24 hours after Checkout Session creation. By default, this value is
24 hours from creation.
- `IntegrationIdentifier`
  - The integration identifier for this Checkout Session. Multiple Checkout Sessions can
have the same integration identifier.
- `InvoiceCreation`
  - Generate a post-purchase Invoice for one-time payments.
- `LineItems`
  - A list of items the customer is purchasing. Use this parameter to pass one-time or
recurring Prices. The parameter is
required for `payment` and `subscription` mode.

For `payment` mode, there is a maximum of 100 line items, however it is recommended
to consolidate line items if there are more than a few dozen.

For `subscription` mode, there is a maximum of 20 line items with recurring Prices
and 20 line items with one-time Prices. Line items with one-time Prices will be on the
initial invoice only.
- `Locale`
  - The IETF language tag of the locale Checkout is displayed in. If blank or `auto`,
the browser's locale is used.
One of: `auto`, `bg`, `cs`, `da`, `de`, `el`, `en`,
`en-GB`, `es`, `es-419`, `et`, `fi`, `fil`, `fr`,
`fr-CA`, `hr`, `hu`, `id`, `it`, `ja`, `ko`,
`lt`, `lv`, `ms`, `mt`, `nb`, `nl`, `pl`, `pt`,
`pt-BR`, `ro`, `ru`, `sk`, `sl`, `sv`, `th`,
`tr`, `vi`, `zh`, `zh-HK`, or `zh-TW`.
- `ManagedPayments`
  - Settings for Managed Payments for this Checkout Session and resulting PaymentIntents, Invoices, and Subscriptions.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format. Individual keys can be unset by posting an empty value to
them. All keys can be unset by posting an empty value to `metadata`.
- `Mode`
  - The mode of the Checkout Session. Pass `subscription` if the Checkout Session
includes at least one recurring item.
One of: `payment`, `setup`, or `subscription`.
- `NameCollection`
  - Controls name collection settings for the session.

You can configure Checkout to collect your customers' business names, individual names,
or both. Each name field can be either required or optional.

If a Customer is created or
provided, the names can be saved to the Customer object as well.

You can't set this parameter if `ui_mode` is `custom`.
- `OptionalItems`
  - A list of optional items the customer can add to their order at checkout. Use this
parameter to pass one-time or recurring Prices.

There is a maximum of 10 optional items allowed on a Checkout Session, and the existing
limits on the number of line items allowed on a Checkout Session apply to the combined
number of line items and optional items.

For `payment` mode, there is a maximum of 100 combined line items and optional
items, however it is recommended to consolidate items if there are more than a few
dozen.

For `subscription` mode, there is a maximum of 20 line items and optional items
with recurring Prices and 20 line items and optional items with one-time Prices.

You can't set this parameter if `ui_mode` is `custom`.
- `OriginContext`
  - Where the user is coming from. This informs the optimizations that are applied to the
session. You can't set this parameter if `ui_mode` is `elements`.
One of: `mobile_app`, or `web`.
- `PaymentIntentData`
  - A subset of parameters to be passed to PaymentIntent creation for Checkout Sessions in
`payment` mode.
- `PaymentMethodCollection`
  - Specify whether Checkout should collect a payment method. When set to
`if_required`, Checkout will not collect a payment method when the total due for
the session is 0. This may occur if the Checkout Session includes a free trial or a
discount.

Can only be set in `subscription` mode. Defaults to `always`.

If you'd like information on how to collect a payment method outside of Checkout, read
the guide on configuring subscriptions with a free
trial.
One of: `always`, or `if_required`.
- `PaymentMethodConfiguration`
  - The ID of the payment method configuration to use with this Checkout session.
- `PaymentMethodData`
  - This parameter allows you to set some attributes on the payment method created during a
Checkout session.
- `PaymentMethodOptions`
  - Payment-method-specific configuration.
- `PaymentMethodTypes`
  - A list of the types of payment methods (e.g., `card`) this Checkout Session can
accept.

You can omit this attribute to manage your payment methods from the Stripe Dashboard. See
Dynamic
Payment Methods for more details.

Read more about the supported payment methods and their requirements in our payment method details
guide.

If multiple payment methods are passed, Checkout will dynamically reorder them to
prioritize the most relevant payment methods based on the customer's location and other
characteristics.
One of: `acss_debit`, `affirm`, `afterpay_clearpay`, `alipay`,
`alma`, `amazon_pay`, `au_becs_debit`, `bacs_debit`,
`bancontact`, `billie`, `bizum`, `blik`, `boleto`, `card`,
`cashapp`, `crypto`, `customer_balance`, `eps`, `fpx`,
`giropay`, `grabpay`, `ideal`, `kakao_pay`, `klarna`,
`konbini`, `kr_card`, `link`, `mb_way`, `mobilepay`,
`multibanco`, `naver_pay`, `nz_bank_account`, `oxxo`, `p24`,
`pay_by_bank`, `payco`, `paynow`, `paypal`, `payto`,
`pix`, `promptpay`, `revolut_pay`, `samsung_pay`, `satispay`,
`scalapay`, `sepa_debit`, `sofort`, `sunbit`, `swish`,
`twint`, `upi`, `us_bank_account`, `wechat_pay`, or `zip`.
- `Permissions`
  - This property is used to set up permissions for various actions (e.g., update) on the
CheckoutSession object. Can only be set when creating `embedded` or `custom`
sessions.

For specific permissions, please refer to their dedicated subsections, such as
`permissions.update_shipping_details`.
- `PhoneNumberCollection`
  - Controls phone number collection settings for the session.

We recommend that you review your privacy policy and check with your legal contacts
before using this feature. Learn more about collecting phone numbers
with Checkout.
- `RedirectOnCompletion`
  - This parameter applies to `ui_mode: embedded_page`. Learn more about the redirect
behavior of embedded sessions. Defaults to `always`.
One of: `always`, `if_required`, or `never`.
- `ReturnUrl`
  - The URL to redirect your customer back to after they authenticate or cancel their
payment on the payment method's app or site. This parameter is required if
`ui_mode` is `embedded_page` or `elements` and redirect-based payment
methods are enabled on the session.
- `SavedPaymentMethodOptions`
  - Controls saved payment method settings for the session. Only available in `payment`
and `subscription` mode.
- `SetupIntentData`
  - A subset of parameters to be passed to SetupIntent creation for Checkout Sessions in
`setup` mode.
- `ShippingAddressCollection`
  - When set, provides configuration for Checkout to collect a shipping address from a
customer.
- `ShippingOptions`
  - The shipping rate options to apply to this Session. Up to a maximum of 5.
- `SubmitType`
  - Describes the type of transaction being performed by Checkout in order to customize
relevant text on the page, such as the submit button. `submit_type` can only be
specified on Checkout Sessions in `payment` or `subscription` mode. If blank
or `auto`, `pay` is used. You can't set this parameter if `ui_mode` is
`elements`.
One of: `auto`, `book`, `donate`, `pay`, or `subscribe`.
- `SubscriptionData`
  - A subset of parameters to be passed to subscription creation for Checkout Sessions in
`subscription` mode.
- `SuccessUrl`
  - The URL to which Stripe should send customers when payment or setup is complete. This
parameter is not allowed if ui_mode is `embedded_page` or `elements`. If you'd
like to use information from the successful Checkout Session on your page, read the
guide on customizing your
success page.
- `TaxIdCollection`
  - Controls tax ID collection during checkout.
- `UiMode`
  - The UI mode of the Session. Defaults to `hosted_page`.
One of: `elements`, `embedded_page`, `form`, or `hosted_page`.
- `WalletOptions`
  - Wallet-specific configuration.


#### `SessionUpdateOptions`

**Properties:**

- `CollectedInformation`
  - Information about the customer collected within the Checkout Session. Can only be set
when updating `embedded` or `custom` sessions.
- `LineItems`
  - A list of items the customer is purchasing.

When updating line items, you must retransmit the entire array of line items.

To retain an existing line item, specify its `id`.

To update an existing line item, specify its `id` along with the new values of the
fields to update.

To add a new line item, specify one of `price` or `price_data` and
`quantity`.

To remove an existing line item, omit the line item's ID from the retransmitted array.

To reorder a line item, specify it at the desired position in the retransmitted array.
- `Metadata`
  - Set of key-value pairs that you can
attach to an object. This can be useful for storing additional information about the
object in a structured format. Individual keys can be unset by posting an empty value to
them. All keys can be unset by posting an empty value to `metadata`.
- `ShippingOptions`
  - The shipping rate options to apply to this Session. Up to a maximum of 5.


#### `SessionListOptions`

**Properties:**

- `Created`
  - Only return Checkout Sessions that were created during the given date interval.
- `Customer`
  - Only return the Checkout Sessions for the Customer specified.
- `CustomerAccount`
  - Only return the Checkout Sessions for the Account specified.
- `CustomerDetails`
  - Only return the Checkout Sessions for the Customer details specified.
- `PaymentIntent`
  - Only return the Checkout Session for the PaymentIntent specified.
- `PaymentLink`
  - Only return the Checkout Sessions for the Payment Link specified.
- `Status`
  - Only return the Checkout Sessions matching the given status.
One of: `complete`, `expired`, or `open`.
- `Subscription`
  - Only return the Checkout Session for the subscription specified.
