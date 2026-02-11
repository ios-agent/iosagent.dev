# Verifier API — Mobile Document & ID Reading

Complete guide for implementing Apple's Verifier API to read mobile driver's licenses, national ID cards, and other mobile documents using ProximityReader.

## Overview

The Verifier API allows your iPhone app to read and verify mobile documents (mDL — mobile driver's licenses, national ID cards) from another person's iPhone or Apple Watch, without any additional hardware. The holder presents their document via Apple Wallet, and your app reads the requested elements.

**Availability**: iOS 17.0+

## Prerequisites

1. **Entitlement**: Request the Verifier API entitlement from Apple (separate from Tap to Pay)
2. **Server component**: You must run a server that generates **reader tokens** (signed JWTs)
3. **Apple certificate**: Obtain a reader authentication certificate from Apple's developer portal
4. **Device**: iPhone XS or later running iOS 17+

## Architecture

```
┌──────────────┐     Reader Token      ┌──────────────┐
│  Your Server  │ ◄──────────────────► │   Your App    │
│  (JWT Signer) │                      │  (Verifier)   │
└──────┬───────┘                      └──────┬───────┘
       │                                      │ NFC/Proximity
       │  Apple Reader                        │
       │  Certificate                   ┌─────▼────────┐
       │                                │  Holder's    │
       └────────────────────────────── │  iPhone/Watch │
                                        │  (Wallet)     │
                                        └──────────────┘
```

## Server-Side: Generating Reader Tokens

Your server must generate a signed JWT that the app uses to initialize the reader session. The token tells Apple what data elements you're authorized to request.

### JWT Structure

```json
{
  "iss": "<your-team-id>",
  "iat": 1700000000,
  "exp": 1700003600,
  "sub": "<your-reader-identifier>",
  "aud": "https://verify.apple.com",
  "nonce": "<unique-request-nonce>",
  "requested_elements": {
    "org.iso.18013.5.1": {
      "given_name": true,
      "family_name": true,
      "date_of_birth": true,
      "portrait": true,
      "age_over_21": true
    }
  }
}
```

### Signing the Token

Sign the JWT with your Apple-issued reader authentication certificate using ES256 algorithm.

```python
# Server-side (Python example)
import jwt
import time

def generate_reader_token(private_key, team_id, reader_id):
    payload = {
        "iss": team_id,
        "iat": int(time.time()),
        "exp": int(time.time()) + 3600,
        "sub": reader_id,
        "aud": "https://verify.apple.com",
        "nonce": generate_unique_nonce(),
        "requested_elements": {
            "org.iso.18013.5.1": {
                "given_name": True,
                "family_name": True,
                "date_of_birth": True,
                "portrait": True,
                "age_over_21": True
            }
        }
    }
    return jwt.encode(payload, private_key, algorithm="ES256")
```

## Client-Side: Reading Documents

### Basic Flow

```swift
import ProximityReader

class IDVerificationManager {
    private let docReader = MobileDocumentReader()
    private var session: MobileDocumentReaderSession?
    
    // Step 1: Check device support
    func checkSupport() -> Bool {
        MobileDocumentReader.isSupported
    }
    
    // Step 2: Fetch reader token from your server
    func fetchReaderToken() async throws -> Data {
        let url = URL(string: "https://your-server.com/api/reader-token")!
        let (data, _) = try await URLSession.shared.data(from: url)
        return data
    }
    
    // Step 3: Create session and prepare
    func prepareSession() async throws {
        let token = try await fetchReaderToken()
        session = try await MobileDocumentReaderSession(
            reader: docReader,
            readerToken: token
        )
        try await session?.prepare()
    }
    
    // Step 4: Read a document
    func verifyDriversLicense() async throws {
        guard let session else { throw VerificationError.sessionNotReady }
        
        // Display request: shows results on screen for visual verification
        let displayRequest = MobileDriversLicenseDisplayRequest(
            retainedElements: [
                .givenName,
                .familyName,
                .portrait,
                .dateOfBirth,
                .ageOver21
            ]
        )
        
        try await session.readDocument(displayRequest)
        // System UI shows the verified document elements on screen
    }
    
    // Alternative: Get validated data back for processing
    func getDriversLicenseData() async throws -> some MobileDocumentDataRequest.Result {
        guard let session else { throw VerificationError.sessionNotReady }
        
        let dataRequest = MobileDriversLicenseDataRequest(
            retainedElements: [
                .givenName,
                .familyName,
                .dateOfBirth
            ]
        )
        
        return try await session.readDocument(dataRequest)
    }
}
```

### Request Types by Document

**Driver's License**:
- `MobileDriversLicenseDisplayRequest` — Visual inspection
- `MobileDriversLicenseDataRequest` — Validated data
- `MobileDriversLicenseRawDataRequest` — Raw CBOR data

**National ID Card**:
- `MobileNationalIDCardDisplayRequest`
- `MobileNationalIDCardDataRequest`
- `MobileNationalIDCardRawDataRequest`

**Photo ID**:
- `MobilePhotoIDDataRequest`
- `MobilePhotoIDRawDataRequest`

**Any Document** (accepts whichever the holder presents):
- `MobileDocumentAnyOfDataRequest`
- `MobileDocumentAnyOfRawDataRequest`
- `MobileDocumentDisplayRequest`

### Display vs Data vs RawData

| Type | Returns | Best For |
|------|---------|----------|
| **Display** | Shows UI on screen, no data returned to app | Bouncer checking age at a bar |
| **Data** | Validated, structured Swift types | Backend processing, compliance |
| **RawData** | Raw CBOR bytes | Custom parsing, third-party verification |

### Available Elements (ISO 18013-5)

```swift
// Common driver's license elements
.givenName          // First name
.familyName         // Last name
.dateOfBirth        // Full birth date
.portrait           // Photo
.ageOver18          // Boolean: is holder 18+?
.ageOver21          // Boolean: is holder 21+?
.documentNumber     // License number
.issuingAuthority   // Issuing state/authority
.expiryDate         // Document expiration
.drivingPrivileges  // License classes/endorsements
.address            // Residential address
.issuingCountry     // Country of issuance
.sex                // Sex as on document
.height             // Height
.weight             // Weight
.eyeColour          // Eye color
.hairColour         // Hair color
```

### Monitoring Session Events

```swift
func observeEvents() async {
    guard let session else { return }
    
    for await event in session.events {
        switch event {
        case .sessionReady:
            // Ready to scan
            updateUI(status: .ready)
        case .documentPresented:
            // Holder tapped their device
            updateUI(status: .reading)
        case .documentRead:
            // Successfully read
            updateUI(status: .complete)
        default:
            break
        }
    }
}
```

## Error Handling

```swift
do {
    try await session.readDocument(request)
} catch let error as MobileDocumentReaderError {
    switch error {
    case .notAllowed:
        // Missing Verifier API entitlement
        showError("This app is not authorized for ID verification.")
    case .unsupported:
        // Device doesn't support document reading
        showError("This device doesn't support mobile ID reading.")
    case .invalidReaderToken:
        // Server-generated token is invalid or expired
        // → Refresh the token from your server
        try await prepareSession()
    case .documentRequestCancelled:
        // Holder declined to share their document
        showError("The document holder cancelled the request.")
    case .networkError:
        showError("Network connection required for verification.")
    default:
        showError("An unexpected error occurred: \(error)")
    }
}
```

## Privacy & Compliance

- Only request elements you genuinely need (principle of minimal disclosure)
- Display requests show data on-screen but don't give your app access to it — ideal for age checks
- Data requests return actual values — ensure you have proper data handling policies
- The holder always sees what's being requested and must explicitly consent
- Apple does not have access to the verification data
- All communication is encrypted end-to-end via the Secure Element
- Retain data only as long as legally required

## Testing

- Use the `ProximityReaderStub` framework for Xcode simulator testing
- Real document reads require two physical devices (verifier + holder)
- Apple provides test mDL profiles for development — request via your developer account
