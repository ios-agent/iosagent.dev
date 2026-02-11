# PassKit Technical Reference

## pass.json Structure

Every `.pkpass` bundle contains a `pass.json` file that defines the pass content and behavior.

### Minimal pass.json Example

```json
{
  "formatVersion": 1,
  "passTypeIdentifier": "pass.com.example.mypass",
  "serialNumber": "ABC123",
  "teamIdentifier": "ABCDE12345",
  "organizationName": "Example Corp",
  "description": "Example Event Ticket",
  "foregroundColor": "rgb(255, 255, 255)",
  "backgroundColor": "rgb(60, 65, 76)",
  "eventTicket": {
    "primaryFields": [
      {
        "key": "event",
        "label": "EVENT",
        "value": "Concert in the Park"
      }
    ],
    "secondaryFields": [
      {
        "key": "loc",
        "label": "LOCATION",
        "value": "Central Park"
      }
    ],
    "auxiliaryFields": [
      {
        "key": "date",
        "label": "DATE",
        "value": "2026-03-15T19:00:00Z",
        "dateStyle": "PKDateStyleMedium",
        "timeStyle": "PKDateStyleShort"
      }
    ]
  },
  "barcode": {
    "message": "ABC123",
    "format": "PKBarcodeFormatQR",
    "messageEncoding": "iso-8859-1"
  },
  "barcodes": [
    {
      "message": "ABC123",
      "format": "PKBarcodeFormatQR",
      "messageEncoding": "iso-8859-1"
    }
  ]
}
```

### Pass Style Keys

Each pass style uses a different top-level key in `pass.json`:

| Style | JSON Key |
|-------|----------|
| Boarding Pass | `boardingPass` |
| Coupon | `coupon` |
| Event Ticket | `eventTicket` |
| Store Card | `storeCard` |
| Generic Pass | `generic` |

### Field Types

Each style supports these field areas (content varies by style):

- **headerFields** — Top of the pass, always visible
- **primaryFields** — Main information area
- **secondaryFields** — Below primary, smaller text
- **auxiliaryFields** — Additional details
- **backFields** — Shown when user flips the pass over

### Barcode Formats

```
PKBarcodeFormatQR      — QR Code (most universal)
PKBarcodeFormatAztec   — Aztec (compact, used by airlines)
PKBarcodeFormatPDF417  — PDF417 (legacy systems)
```

Use the `barcodes` array (plural) for multiple fallback formats. The singular `barcode` key is
for backward compatibility with older iOS versions.

## .pkpass Bundle Structure

A `.pkpass` file is a ZIP archive with a specific structure:

```
MyPass.pkpass/
├── pass.json          — Pass definition (required)
├── manifest.json      — SHA-1 hashes of all files (required)
├── signature           — PKCS#7 detached signature (required)
├── icon.png           — Pass icon (required)
├── icon@2x.png        — Retina icon
├── icon@3x.png        — Super Retina icon
├── logo.png           — Logo displayed on pass
├── logo@2x.png
├── strip.png          — Strip image (coupon, event ticket, store card)
├── strip@2x.png
├── thumbnail.png      — Thumbnail (event ticket, generic)
├── thumbnail@2x.png
└── en.lproj/          — Localization folder
    └── pass.strings
```

## Relevance Configuration

Passes can appear automatically on the Lock Screen based on location and time.

### Location Relevance

```json
"locations": [
  {
    "latitude": 37.331,
    "longitude": -122.029,
    "relevantText": "Welcome to the store!"
  }
]
```

Up to 10 locations per pass. The system determines the appropriate radius based on the pass style.

### Time Relevance

```json
"relevantDate": "2026-03-15T19:00:00Z"
```

The relevance window depends on the pass style — a boarding pass shows earlier than an event ticket.

## Server-Side Update Flow

To push updates to passes:

1. **Register for push notifications** — When a pass is added, the device registers with your server
2. **Store device tokens** — Your server stores the push token for each device/pass combination
3. **Send push notification** — When pass data changes, send a push to registered devices
4. **Device fetches update** — Device calls your web service to get the updated pass
5. **Pass updates on device** — New pass data replaces the old version

### Required Web Service Endpoints

Your server must implement these REST endpoints:

| Endpoint | Method | Purpose |
|----------|--------|---------|
| `webServiceURL/v1/devices/{deviceLibraryIdentifier}/registrations/{passTypeIdentifier}` | POST | Register device for updates |
| `webServiceURL/v1/devices/{deviceLibraryIdentifier}/registrations/{passTypeIdentifier}/{serialNumber}` | DELETE | Unregister device |
| `webServiceURL/v1/devices/{deviceLibraryIdentifier}/registrations/{passTypeIdentifier}` | GET | Get serial numbers of updated passes |
| `webServiceURL/v1/passes/{passTypeIdentifier}/{serialNumber}` | GET | Get latest version of a pass |
| `webServiceURL/v1/log` | POST | Log error messages from devices |

### Authentication

Pass updates use an authentication token defined in `pass.json`:

```json
"authenticationToken": "your-secret-token-here",
"webServiceURL": "https://your-server.example.com"
```

The token must be at least 16 characters. Devices send it in the `Authorization` header.

## NFC Integration

For NFC-enabled passes, add the `nfc` key to `pass.json`:

```json
"nfc": {
  "message": "your-nfc-payload",
  "encryptionPublicKey": "your-public-key"
}
```

NFC passes require additional entitlements and Apple approval. For Apple Pay loyalty integration,
see the dedicated [loyalty passes documentation](https://developer.apple.com/wallet/loyalty-passes/).

## Signing Process (Command Line)

```bash
# 1. Create manifest.json with SHA-1 hashes of all files
openssl sha1 pass.json icon.png logo.png ... > manifest.json

# 2. Sign the manifest
openssl smime -binary -sign \
  -certfile AppleWWDRCA.pem \
  -signer PassCert.pem \
  -inkey PassKey.pem \
  -in manifest.json \
  -out signature \
  -outform DER

# 3. Package as .pkpass (ZIP)
zip -r MyPass.pkpass pass.json manifest.json signature icon.png logo.png ...
```

## Apple Developer Resources

- [PassKit Framework](https://developer.apple.com/documentation/passkit/)
- [WalletPasses Documentation](https://developer.apple.com/documentation/walletpasses/)
- [Human Interface Guidelines — Wallet](https://developer.apple.com/design/human-interface-guidelines/wallet/)
- [Add to Apple Wallet Guidelines](https://developer.apple.com/wallet/add-to-apple-wallet-guidelines/)
- [Loyalty Passes](https://developer.apple.com/wallet/loyalty-passes/)
- [Verify with Wallet](https://developer.apple.com/wallet/get-started-with-verify-with-wallet/)
- [ID Verifier](https://developer.apple.com/wallet/id-verifier/)
- [Certificates, Identifiers & Profiles](https://developer.apple.com/help/account/create-certificates/certificates-overview/)
