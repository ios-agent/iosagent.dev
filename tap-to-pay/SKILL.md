---
name: tap-to-pay-on-iphone
description: >
  Comprehensive reference for Apple's Tap to Pay on iPhone — the ProximityReader framework,
  PSP integration, entitlement workflow, marketing guidelines, and regional availability.
  Use this skill whenever the user asks about implementing contactless payments on iPhone,
  the ProximityReader API, Tap to Pay entitlements, NFC payment acceptance, loyalty card reading
  via NFC, payment service provider (PSP) selection for Tap to Pay, or merchant-facing payment
  app development. Also trigger when the user mentions "Tap to Pay", "TTP", "softPOS",
  "iPhone as terminal", "contactless payment acceptance", or building an app that accepts
  card-present payments on iPhone without external hardware.
---

# Tap to Pay on iPhone — Skill

## What is Tap to Pay on iPhone?

Tap to Pay on iPhone lets payment apps accept contactless payments — from contactless credit/debit cards, Apple Pay, Apple Watch, and other digital wallets — directly on an iPhone, with no external terminal or hardware required. Transactions are encrypted and processed via the Secure Element; Apple never sees what is purchased or who buys it.

Beyond payments, Tap to Pay also supports:

- **Card validation without charging** — adding a card on file for recurring payments, or looking up a previous purchase for refunds without a receipt.
- **NFC loyalty/discount/points cards** — reading Apple Wallet passes independently of, or alongside, a payment transaction. Merchants can also prompt Apple Pay customers to join their loyalty program during checkout.

## Integration Steps (for app developers)

Building Tap to Pay into a payment app follows five steps:

1. **Choose a PSP** that supports Tap to Pay on iPhone in the target region. The PSP processes payments and provides the certified terminal configuration loaded onto the merchant's device. See `references/regions-and-psps.md` for the full list.
2. **Request the entitlement** from Apple via the [Tap to Pay on iPhone Entitlement Request Form](https://developer.apple.com/contact/request/tap-to-pay-on-iphone/).
3. **Integrate the ProximityReader API** (`import ProximityReader`) and/or the PSP's SDK into the app. API docs: [ProximityReader](https://developer.apple.com/documentation/ProximityReader/).
4. **Follow the Human Interface Guidelines** for Tap to Pay on iPhone: [HIG](https://developer.apple.com/design/human-interface-guidelines/technologies/tap-to-pay-on-iphone/).
5. **Submit the app for review.** Ensure compliance with the [App Review Guidelines: Payments](https://developer.apple.com/app-store/review/guidelines/#payments).

## ProximityReader API — Key Concepts

The `ProximityReader` framework provides:

- `PaymentCardReader` — presents the system payment sheet showing amount, merchant name, and category icon; reads contactless payment cards.
- `PaymentCardReadResult` — the encrypted payment data returned to the PSP for processing.
- Loyalty pass reading — can read NFC passes independently of, at the same time as, or instead of a payment card.

The PSP is responsible for all certifications and security requirements. The developer's responsibility is to integrate the API correctly, handle the results, and hand them off to the PSP's backend.

## Merchant Setup (no code needed)

For a merchant to start accepting Tap to Pay, they:

1. Download a supported payment app from the App Store.
2. Accept terms and conditions on-device.
3. Enable their device to be configured (provisioned by the PSP).
4. Start accepting payments immediately.

## Payment Flow — How Transactions Work

1. Merchant opens the payment app and enters the purchase amount.
2. The system payment sheet appears showing amount, merchant name, and category icon.
3. The customer holds their contactless card horizontally, or their iPhone/Apple Watch/other device, near the top of the merchant's iPhone (the tap area).
4. A "Done" checkmark confirms the transaction is complete.

### PIN Entry

Some markets (especially in Europe) require Online or Offline PIN for certain card types. Tap to Pay on iPhone supports PIN entry with built-in accessibility options — audible instructions guide the customer to draw or tap their PIN. If a card cannot complete a contactless PIN transaction, the merchant should ask for an alternative card or digital wallet.

## Marketing Guidelines

When marketing Tap to Pay on iPhone, these rules apply (see `references/marketing-guidelines.md` for full details):

- Always use the full name **"Tap to Pay on iPhone"** — never shorten to "Tap to Pay" and never include "Apple" in the name.
- Only use Apple-approved marketing assets from the official Toolkit.
- Do not create custom videos, illustrations, photography, or stock imagery depicting the feature.
- Do not create illustrations or icons depicting iPhone or Tap to Pay on iPhone.
- All PR announcements mentioning Tap to Pay on iPhone must be submitted to Apple for review before publishing (allow several weeks).
- Only market when the feature is in full general availability in your app.

## Key Resources

| Resource | Link |
|----------|------|
| ProximityReader API | https://developer.apple.com/documentation/ProximityReader/ |
| HIG for Tap to Pay | https://developer.apple.com/design/human-interface-guidelines/technologies/tap-to-pay-on-iphone/ |
| Design Template | https://developer.apple.com/design/resources/#technologies |
| Entitlement Request | https://developer.apple.com/contact/request/tap-to-pay-on-iphone/ |
| Apple Wallet Integration | https://developer.apple.com/wallet/ |
| App Review Guidelines | https://developer.apple.com/app-store/review/guidelines/#payments |
| Cashier Guide (PDF) | https://developer.apple.com/tap-to-pay/files/Tap-to-Pay-on-iPhone-Cashier-Guide-July2023.pdf |
| Merchant FAQ | https://support.apple.com/guide/apple-business-connect/abcb71e19fc3/web |

## Reference Files

- `references/regions-and-psps.md` — Full list of countries and supported PSPs with SDK links. Read this when the user needs to know which PSPs are available in a specific country.
- `references/marketing-guidelines.md` — Detailed marketing dos and don'ts, toolkit access, and asset types. Read this when the user is planning marketing campaigns.
