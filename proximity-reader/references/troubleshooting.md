# Troubleshooting ProximityReader

Common issues, debugging tips, and solutions for ProximityReader integration.

## Table of Contents

1. [Setup & Entitlement Issues](#setup--entitlement-issues)
2. [Reader Token Problems](#reader-token-problems)
3. [Runtime Errors](#runtime-errors)
4. [Device & Compatibility](#device--compatibility)
5. [Testing & Debugging](#testing--debugging)
6. [Common Pitfalls](#common-pitfalls)

---

## Setup & Entitlement Issues

### `PaymentCardReaderError.notAllowed`

**Cause**: Missing or misconfigured entitlement.

**Fix**:
1. Ensure you've requested the Tap to Pay on iPhone entitlement from Apple
2. Add the entitlement to your app target's `.entitlements` file:
   ```xml
   <key>com.apple.developer.proximity-reader.payment.acceptance</key>
   <true/>
   ```
3. For development: request the **development** entitlement
4. For App Store: request the **distribution** entitlement
5. Verify your provisioning profile includes the entitlement

### Entitlement Not Appearing in Developer Portal

- Tap to Pay requires a relationship with a Level 3 certified PSP
- Contact Apple Developer support with your PSP partnership details
- Ensure your Apple Developer account is enrolled as an Organization (not Individual)

---

## Reader Token Problems

### `PaymentCardReaderError.invalidReaderToken`

**Cause**: The JWT token from your PSP is invalid, expired, or malformed.

**Debugging steps**:
1. Decode the JWT at jwt.io and check:
   - `exp` claim is in the future
   - `iss` matches your PSP's expected issuer
   - Signature is valid
2. Ensure you're passing the raw JWT string (not base64-encoded again)
3. Check your PSP's documentation for token format requirements
4. Some PSPs require a fresh token per session — don't cache indefinitely

```swift
// Common mistake: double-encoding
// WRONG
let token = PaymentCardReader.Token(rawValue: Data(jwt.utf8).base64EncodedString())

// CORRECT
let token = PaymentCardReader.Token(rawValue: jwt)
```

### Token Refresh Strategy

```swift
class TokenManager {
    private var currentToken: String?
    private var tokenExpiry: Date?
    
    func getValidToken() async throws -> PaymentCardReader.Token {
        if let token = currentToken, let expiry = tokenExpiry, expiry > Date().addingTimeInterval(300) {
            return PaymentCardReader.Token(rawValue: token)
        }
        
        // Refresh token from PSP/server
        let newToken = try await psp.fetchReaderToken()
        currentToken = newToken.jwt
        tokenExpiry = newToken.expiresAt
        
        return PaymentCardReader.Token(rawValue: newToken.jwt)
    }
}
```

---

## Runtime Errors

### `PaymentCardReaderError.backgrounded`

**Cause**: The app moved to the background during a read session.

**Fix**: Always re-prepare after returning to the foreground:

```swift
.onChange(of: scenePhase) { _, newPhase in
    if newPhase == .active {
        Task { try? await session?.prepare() }
    }
}
```

### `PaymentCardReaderError.readerBusy`

**Cause**: Another `PaymentCardReaderSession` or `StoreAndForwardPaymentCardReaderSession` is active.

**Fix**: 
- Only create one session at a time
- Cancel existing sessions before creating new ones
- This can also occur if another app on the device is using Tap to Pay

### `PaymentCardReaderSession.ReadError.notReady`

**Cause**: `prepare()` was not called, or hasn't completed yet.

**Fix**:
```swift
// Always await prepare() before reading
try await session.prepare()
// Now safe to read
let result = try await session.readPaymentCard(request)
```

### `PaymentCardReaderSession.ReadError.invalidAmount`

**Cause**: Amount is zero, negative, or has too many decimal places.

**Fix**:
```swift
// Validate before creating request
guard amount > 0 else { return }

// Round to 2 decimal places for most currencies
let roundedAmount = NSDecimalNumber(decimal: amount)
    .rounding(accordingToBehavior: NSDecimalNumberHandler(
        roundingMode: .plain,
        scale: 2,
        raiseOnExactness: false,
        raiseOnOverflow: false,
        raiseOnUnderflow: false,
        raiseOnDivideByZero: false
    )).decimalValue
```

### `PaymentCardReaderError.passcodeDisabled`

**Cause**: The device has no passcode set. Tap to Pay requires a device passcode for security.

**Fix**: Prompt the user to set a device passcode in Settings.

### `PaymentCardReaderError.readerMemoryFull`

**Cause**: Too many Store and Forward transactions stored on device.

**Fix**: Process pending batches before accepting more transactions:
```swift
let store = PaymentCardReaderStore()
let batches = try await store.allBatches()
for batch in batches {
    try await psp.submitBatch(batch.data)
    try await store.delete(using: batch.deletionToken)
}
```

---

## Device & Compatibility

### Supported Devices

Tap to Pay on iPhone requires **iPhone XS or later**:
- iPhone XS, XS Max, XR (2018)
- iPhone 11, 11 Pro, 11 Pro Max (2019)
- iPhone SE (2nd gen, 2020)
- iPhone 12 series (2020)
- iPhone 13 series (2021)
- iPhone 14 series (2022)
- iPhone 15 series (2023)
- iPhone 16 series (2024)
- All later models

**Not supported**: iPhone X, iPhone 8, iPhone SE (1st gen), any iPad.

### OS Requirements

| Feature | Minimum iOS |
|---------|-------------|
| Tap to Pay (basic) | iOS 15.4 |
| PIN entry | iOS 16.4 |
| Store and Forward | iOS 17.0 |
| Verifier API | iOS 17.0 |
| ProximityReaderDiscovery | iOS 18.0 |

### Checking Capability at Runtime

```swift
if PaymentCardReader.isSupported {
    // Device supports Tap to Pay
} else {
    // Show alternative payment method or explain requirement
}

if MobileDocumentReader.isSupported {
    // Device supports Verifier API
}
```

### Regional Availability

Tap to Pay on iPhone is available in: US, UK, Canada, Australia, France, Germany, Netherlands, Taiwan, Brazil, Japan, and more (expanding). Check Apple's current list at developer.apple.com.

PIN entry regional notes:
- **UK**: Some cards require Strong Customer Authentication (chip insertion) — not supported via Tap to Pay
- **Canada/Finland**: Many cards are offline-PIN-only (requires chip insertion) — suggest alternative payment method
- **US**: PIN entry works normally for cards that require it

---

## Testing & Debugging

### Simulator Testing

Use `ProximityReaderStub` for basic testing in the simulator:
```swift
#if targetEnvironment(simulator)
import ProximityReaderStub
#else
import ProximityReader
#endif
```

**Limitations**: Stub provides basic API surface but cannot simulate actual NFC reads.

### TestFlight Testing

- Tap to Pay works in TestFlight builds with the development entitlement
- Use a real contactless card or Apple Pay on a second device
- Test with both credit and debit cards
- Test with Apple Pay, Google Pay, and physical cards

### Debugging Tips

1. **Enable console logging**: Filter Xcode console for "ProximityReader" to see framework-level logs
2. **Monitor events stream**: Log all events from `session.events` to track state transitions
3. **Network diagnostics**: Many operations require network connectivity — test with poor/no connectivity
4. **Background handling**: Test by switching apps during a read to ensure proper recovery

```swift
// Detailed event logging for debugging
Task {
    for await event in session.events {
        print("[ProximityReader] Event: \(event)")
    }
}
```

### Common Test Scenarios

1. ✅ Happy path: payment succeeds
2. ✅ Customer cancels the tap
3. ✅ App backgrounded during read → returns to foreground → retries
4. ✅ Invalid amount (0, negative)
5. ✅ Network loss during transaction
6. ✅ Token expiry during session
7. ✅ Multiple rapid transactions
8. ✅ Refund flow
9. ✅ Card verification (no charge)
10. ✅ Combined payment + loyalty read

---

## Common Pitfalls

### 1. Forgetting to Re-prepare

The #1 source of bugs. You must call `prepare()`:
- After app returns to foreground
- After each successful/failed transaction
- After session creation

### 2. Holding Strong Reference to Session in Background

```swift
// BAD: session stays alive in background, wastes resources
class BadViewModel {
    var session: PaymentCardReaderSession? // never released
}

// GOOD: nil out session on background, recreate on foreground
class GoodViewModel {
    var session: PaymentCardReaderSession?
    
    func handleBackground() {
        session = nil
    }
    
    func handleForeground() async throws {
        session = try await PaymentCardReaderSession(reader: reader, token: token)
        try await session?.prepare()
    }
}
```

### 3. Not Handling Cancellation

```swift
// Always handle the cancelled case gracefully
do {
    let result = try await session.readPaymentCard(request)
} catch let error as PaymentCardReaderSession.ReadError where error == .cancelled {
    // User cancelled — don't show error, just return to amount input
    return
} catch {
    // Actual error — show to user
}
```

### 4. Caching Tokens Too Long

PSP tokens have expiry times. Don't cache indefinitely:
```swift
// BAD
let token = savedToken // Might be expired

// GOOD
let token = try await tokenManager.getValidToken()
```

### 5. Testing on Beta iOS

Tap to Pay does **not** work on iOS beta releases. Always test on stable releases.

### 6. Multiple Simultaneous Sessions

Only one reader session can be active at a time across the entire device. Even other apps using Tap to Pay will block your session.
