# ProximityReader API Reference

Complete reference for all types in the ProximityReader framework.

## Table of Contents

1. [Payment Card Reader](#payment-card-reader)
2. [Payment Requests & Results](#payment-requests--results)
3. [Store and Forward](#store-and-forward)
4. [Loyalty / VAS](#loyalty--vas)
5. [Mobile Document Reader](#mobile-document-reader)
6. [Mobile Document Requests](#mobile-document-requests)
7. [Merchant Discovery](#merchant-discovery)
8. [Errors](#errors)

---

## Payment Card Reader

### `class PaymentCardReader`

Configures Tap to Pay on iPhone on the current device.

```swift
class PaymentCardReader {
    // Nested Types
    struct Token {
        let rawValue: String
        init(rawValue: String)
    }
    
    // Initialization
    init()
    
    // Account Management
    func isAccountLinked(using token: Token) async throws -> Bool
    func linkAccount(using token: Token) async throws
    
    // Device Capability
    static var isSupported: Bool { get }
    
    // Reader Identification
    var readerIdentifier: String { get async throws }
}
```

**Usage notes:**
- `isSupported` — Check before attempting any reader operations. Returns `false` on unsupported devices (pre-iPhone XS) or missing entitlements.
- `linkAccount(using:)` — Presents a system sheet for the merchant to accept Tap to Pay T&Cs. Only needed once per device/merchant.
- `isAccountLinked(using:)` — Quick check to see if the account setup has been completed.

### `class PaymentCardReaderSession`

Manages a payment card reading session.

```swift
class PaymentCardReaderSession {
    // Initialization
    init(reader: PaymentCardReader, token: PaymentCardReader.Token) async throws
    
    // Session Lifecycle
    func prepare() async throws
    func cancelRead() async throws
    
    // Reading Cards
    func readPaymentCard(_ request: PaymentCardTransactionRequest) async throws -> PaymentCardReadResult
    func readPaymentCard(_ request: PaymentCardTransactionRequest, vasRequest: VASRequest) async throws -> PaymentCardReadResult
    func readPaymentCard(_ request: PaymentCardVerificationRequest) async throws -> PaymentCardReadResult
    func readPaymentCard(_ request: PaymentCardVerificationRequest, vasRequest: VASRequest) async throws -> PaymentCardReadResult
    
    // Events
    var events: AsyncStream<PaymentCardReaderSession.Event> { get }
    
    // Nested Types
    enum Event {
        case updateProgress(Int)           // 0-100
        case notReady
        case ready
        case readNotCompleted
        case readCompleted
        case readRetry
        case removeCard
        case readCancelled
    }
    
    enum ReadError: Error {
        case cancelled
        case invalidAmount
        case notReady
        case readNotAllowed
        case deviceBanned
        case networkError
        case pinEntryTimeout
        case pinEntryFailed
        case readFromBackgroundError
    }
}
```

**Usage notes:**
- `prepare()` — Must be called before `readPaymentCard()`. Also call after backgrounding and after each transaction.
- `events` — AsyncStream for UI updates (progress, read state). Use in SwiftUI with `.task { for await event in session.events { ... } }`.
- `cancelRead()` — Cancels an in-progress card read.

---

## Payment Requests & Results

### `struct PaymentCardTransactionRequest`

```swift
struct PaymentCardTransactionRequest {
    let amount: Decimal
    let currencyCode: String
    let type: TransactionType
    
    enum TransactionType {
        case purchase
        case refund
    }
    
    init(amount: Decimal, currencyCode: String, type: TransactionType)
}
```

**Notes:**
- `amount` must be positive (> 0)
- `currencyCode` uses ISO 4217 (e.g. "USD", "EUR", "GBP")
- For refunds, use `.refund` type with the refund amount

### `struct PaymentCardVerificationRequest`

```swift
struct PaymentCardVerificationRequest {
    let currencyCode: String
    
    init(currencyCode: String)
}
```

Used to verify card details without charging (e.g. card-on-file enrollment).

### `struct PaymentCardReadResult`

```swift
struct PaymentCardReadResult {
    let paymentCardData: String?           // Encrypted card data for PSP
    let generalCardData: String?           // General card metadata
    let vasReadResult: VASReadResult?      // Loyalty data (if VAS request included)
}
```

**Notes:**
- `paymentCardData` is encrypted and must be sent to your PSP for decryption/processing
- The app never has access to raw card numbers or sensitive data

---

## Store and Forward

For offline/intermittent connectivity scenarios. Transactions are stored securely on device and batched for later submission.

### `class StoreAndForwardPaymentCardReaderSession`

```swift
class StoreAndForwardPaymentCardReaderSession {
    init(reader: PaymentCardReader, token: PaymentCardReader.Token) async throws
    
    func prepare() async throws
    func cancelRead() async throws
    
    func readPaymentCard(_ request: PaymentCardTransactionRequest) async throws -> PaymentCardReadResult
    func readPaymentCard(_ request: PaymentCardTransactionRequest, vasRequest: VASRequest) async throws -> PaymentCardReadResult
    
    var events: AsyncStream<PaymentCardReaderSession.Event> { get }
}
```

### `struct PaymentCardReaderStore`

```swift
struct PaymentCardReaderStore {
    init()
    
    func allBatches() async throws -> [StoreAndForwardBatch]
    func delete(using token: StoreAndForwardBatchDeletionToken) async throws
    
    var status: StoreAndForwardStatus { get async throws }
}
```

### `struct StoreAndForwardBatch`

```swift
struct StoreAndForwardBatch {
    let data: Data                                    // Encrypted batch to send to PSP
    let deletionToken: StoreAndForwardBatchDeletionToken
    let creationDate: Date
    let transactionCount: Int
}
```

### `struct StoreAndForwardStatus`

```swift
struct StoreAndForwardStatus {
    let isEnabled: Bool
    let batchCount: Int
    let totalTransactionCount: Int
}
```

---

## Loyalty / VAS

Value Added Services — read NFC loyalty/discount passes from Apple Wallet.

### `class VASRequest`

```swift
class VASRequest {
    let merchantIdentifier: String
    let localizedDescription: String
    
    init(merchantIdentifier: String, localizedDescription: String)
}
```

**Notes:**
- `merchantIdentifier` matches the pass type identifier in your loyalty pass (e.g. `pass.com.example.loyalty`)
- Can be used standalone with a verification request or combined with a transaction

### `struct VASReadResult`

```swift
struct VASReadResult {
    let entries: [VASReadResult.Entry]
    
    struct Entry {
        let identifier: String
        let data: Data?
        let status: Status
        
        enum Status {
            case success
            case dataNotFound
            case dataNotTransferred
            case incorrectCredentials
        }
    }
}
```

---

## Mobile Document Reader

### `class MobileDocumentReader`

```swift
class MobileDocumentReader {
    init()
    
    static var isSupported: Bool { get }
    var readerIdentifier: String { get async throws }
}
```

### `class MobileDocumentReaderSession`

```swift
class MobileDocumentReaderSession {
    init(reader: MobileDocumentReader, readerToken: Data) async throws
    
    func prepare() async throws
    
    func readDocument<T: MobileDocumentRequest>(_ request: T) async throws -> T.Result
    
    var events: AsyncStream<MobileDocumentReaderSession.Event> { get }
}
```

---

## Mobile Document Requests

All document requests conform to `MobileDocumentRequest`. There are three patterns:

| Pattern | Description | Use Case |
|---------|-------------|----------|
| **Display** | Shows results on-screen for visual inspection | Age verification at a venue |
| **Data** | Returns validated, structured elements | Backend processing |
| **RawData** | Returns raw CBOR response data | Custom processing pipelines |

### Driver's License Requests

```swift
struct MobileDriversLicenseDisplayRequest: MobileDocumentRequest {
    let retainedElements: [Element]
    init(retainedElements: [Element])
    
    enum Element {
        case givenName, familyName, dateOfBirth, portrait
        case ageOver18, ageOver21
        case documentNumber, issuingAuthority, expiryDate
        case drivingPrivileges, address, issuingCountry
        // ... additional elements
    }
}

struct MobileDriversLicenseDataRequest: MobileDocumentDataRequest { ... }
struct MobileDriversLicenseRawDataRequest: MobileDocumentRawDataRequest { ... }
```

### National ID Card Requests

```swift
struct MobileNationalIDCardDisplayRequest: MobileDocumentRequest { ... }
struct MobileNationalIDCardDataRequest: MobileDocumentDataRequest { ... }
struct MobileNationalIDCardRawDataRequest: MobileDocumentRawDataRequest { ... }
```

### Photo ID Requests

```swift
struct MobilePhotoIDDataRequest: MobileDocumentDataRequest { ... }
struct MobilePhotoIDRawDataRequest: MobileDocumentRawDataRequest { ... }
```

### Generic Document Requests

```swift
struct MobileDocumentDisplayRequest: MobileDocumentRequest { ... }
struct MobileDocumentAnyOfDataRequest: MobileDocumentDataRequest { ... }
struct MobileDocumentAnyOfRawDataRequest: MobileDocumentRawDataRequest { ... }
```

### Protocols

```swift
protocol MobileDocumentRequest {
    associatedtype Result
    // All document requests conform to this
}

protocol MobileDocumentDataRequest: MobileDocumentRequest {
    // Returns validated document elements
}

protocol MobileDocumentRawDataRequest: MobileDocumentRequest {
    // Returns raw response data (CBOR)
}
```

---

## Merchant Discovery

### `class ProximityReaderDiscovery`

```swift
class ProximityReaderDiscovery {
    init()
    func present() async throws
}
```

Apple-provided UI that educates merchants about Tap to Pay on iPhone. Content is automatically localized and kept up-to-date by Apple. Available iOS 18+.

---

## Errors

### `enum PaymentCardReaderError`

```swift
enum PaymentCardReaderError: Error {
    case notAllowed              // Missing entitlement
    case unsupported             // Device doesn't support Tap to Pay
    case networkError            // Connectivity issue
    case networkAuthenticationError
    case invalidReaderToken(_:)  // Invalid/expired PSP token
    case readerBusy              // Another session is active
    case readerMemoryFull        // Too many S&F transactions stored
    case accountNotLinked        // linkAccount() not called
    case accountAlreadyLinked
    case accountLinkingFailed
    case accountLinkingCancelled
    case accountLinkingRequiresUpdate
    case merchantBlocked
    case invalidMerchant
    case passcodeDisabled        // Device has no passcode set
    case backgrounded            // App was backgrounded
    case osVersionNotSupported
    case modelNotSupported
    case unknown
}
```

### `enum MobileDocumentReaderError`

```swift
enum MobileDocumentReaderError: Error {
    case notAllowed
    case unsupported
    case networkError
    case invalidReaderToken
    case readerBusy
    case sessionNotReady
    case documentRequestFailed
    case documentRequestCancelled
    case unknown
}
```
