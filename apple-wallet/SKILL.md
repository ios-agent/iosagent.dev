---
name: apple-wallet-passes
description: >
  Guide users through creating, designing, signing, distributing, and updating Apple Wallet passes
  using the PassKit framework. Use this skill whenever the user mentions Wallet passes, .pkpass files,
  boarding passes, event tickets, store cards, coupons, loyalty cards, membership cards, NFC passes,
  or anything related to Apple Wallet integration. Also trigger when the user asks about "Add to Wallet"
  badges, pass signing certificates, pass updates via push notifications, or barcode/NFC-based
  redemption flows. Even if the user just says "I want to create a digital ticket" or "loyalty card
  for my app", this skill applies.
---

# Apple Wallet Passes

This skill helps you guide users through the full lifecycle of Apple Wallet passes — from choosing
the right pass style, through design and development, to signing, distribution, and updates.

## When to Use

Trigger this skill for any of these scenarios:

- Creating a new Wallet pass (boarding pass, coupon, event ticket, store card, generic pass)
- Designing pass layouts and choosing the right pass style
- Setting up pass signing with Apple-issued certificates
- Distributing passes via app, email, or web
- Implementing pass updates with push notifications
- Working with NFC readers or barcode scanning
- Adding "Add to Apple Wallet" badges
- Implementing the Verify with Wallet API or ID Verifier
- Questions about PassKit framework or WalletPasses documentation

## Pass Styles Overview

Apple Wallet supports five pass styles. Choosing the correct style is critical because it determines
the visual layout, the information hierarchy, and how time/location relevance works.

| Style | Use Case | Examples |
|-------|----------|---------|
| **Boarding Pass** | Travel & transit | Flight, train, bus passes |
| **Coupon** | Promotions & discounts | Store coupons, promotional offers |
| **Event Ticket** | Time-bound events | Concert, movie, sports tickets |
| **Store Card** | Loyalty & rewards | Loyalty cards, gift cards, membership |
| **Generic Pass** | Everything else | Membership cards, claim tickets, insurance cards |

The style affects how relevance (time window and location radius) is interpreted. A boarding pass
relevance window is very different from a movie ticket — always match the style to the actual use case.

## Development Workflow

Walk the user through these steps in order, adapting to where they are in the process:

### 1. Choose the Pass Style

Ask the user what kind of pass they're building. Help them pick the right style based on
their use case. If it's ambiguous (e.g., a gym membership), explain the tradeoffs between
Store Card and Generic Pass.

### 2. Design the Pass

- Passes should be clear, optimized, and look great on all devices
- Point users to the [Human Interface Guidelines](https://developer.apple.com/design/human-interface-guidelines/wallet/) for design best practices
- Key design considerations: logo, strip image, icon, relevant text fields, barcode placement

### 3. Build the Pass with PassKit

- Use the PassKit framework for creating, distributing, and updating passes
- A pass is a signed bundle (`.pkpass` file) containing a `pass.json` manifest and assets
- Point to [PassKit documentation](https://developer.apple.com/documentation/passkit/) for API details
- For web distribution, see [WalletPasses documentation](https://developer.apple.com/documentation/walletpasses/)

### 4. Sign the Pass

Passes must be signed with an Apple-issued certificate tied to the developer's Apple Developer account.

Key points to communicate:
- Certificates are managed in [Certificates, Identifiers & Profiles](https://developer.apple.com/help/account/create-certificates/certificates-overview/)
- Only apps from the same team with proper entitlements can access the passes
- **Expired certificate**: Existing passes on devices still work, but no new passes can be signed and no updates sent
- **Revoked certificate**: Passes stop functioning — this is a critical distinction to highlight

### 5. Distribute the Pass

Three distribution channels:
1. **In-app** — Use PassKit API to present the pass with the "Add to Wallet" badge
2. **Email** — Attach the `.pkpass` file; recipients tap to add
3. **Web** — Host the pass for download; use the "Add to Wallet" badge

Important details:
- Users can add passes without installing a related app
- If there is a related app, users can install it directly from the pass
- iCloud syncs passes across all of a user's devices
- Use the [Add to Apple Wallet badge guidelines](https://developer.apple.com/wallet/add-to-apple-wallet-guidelines/) for branding

### 6. Update Passes

Two update mechanisms:
- **Push notifications** — Server sends update notification; user taps to see changes
- **Pull-to-refresh** — User manually refreshes on the back of the pass

Common update scenarios: gate changes, balance adjustments, schedule changes.

### 7. Accept / Redeem Passes

Three redemption methods:

| Method | Details |
|--------|---------|
| **NFC** | Contactless redemption; user holds device near reader. No barcode needed. For Apple Pay loyalty, see [loyalty passes docs](https://developer.apple.com/wallet/loyalty-passes/). |
| **Barcode** | Supports QR, Aztec, PDF417 formats. Screen locks to portrait and boosts backlight. Optical scanners work better than laser scanners for iPhone screens. |
| **Text fallback** | Membership/account number displayed below barcode for manual entry. |

### 8. Identity Verification (Optional)

Two APIs for identity verification:
- **Verify with Wallet API** — Age or identity verification using ID stored in Wallet. [Learn more](https://developer.apple.com/wallet/get-started-with-verify-with-wallet/)
- **ID Verifier** — Use iPhone as a mobile ID reader for in-person verification, no external hardware needed. [Learn more](https://developer.apple.com/wallet/id-verifier/)

## Common Questions

When users ask these, here's how to respond:

**"What happens if my certificate expires?"**
→ Existing passes on devices continue to work. You just can't sign new passes or push updates.

**"What barcode format should I use?"**
→ QR is the most universal. Aztec is compact and used by airlines. PDF417 is used for some legacy systems. Test with your actual scanning hardware.

**"Can users add passes without my app?"**
→ Yes. Passes can be added via email or web without any app installed.

**"How do I test pass scanning?"**
→ Always test with the actual hardware you'll use. Optical scanners handle iPhone screens much better than laser scanners.

## Reference

For deeper technical details, read `references/passkit-technical.md` which covers the pass.json
structure, server-side update flow, and code examples.
