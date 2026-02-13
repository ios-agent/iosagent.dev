# Authorization & Permissions Reference

## Authorization Flow Overview

Location data is sensitive. The system prevents apps from using location data
until explicitly authorized. Authorization happens once; the system stores the
result and doesn't prompt again (users change it in Settings).

Best practice: Request authorization only when the user engages a feature that
needs location. Requesting at launch reduces the chance the user grants access.

## Access Levels

### When In Use (Preferred)
- Location updates only while app is in foreground
- Better privacy and battery implications
- On iOS: foreground + brief transition to background
- On macOS: functionally equivalent to Always
- On visionOS: while user is looking at app
- On watchOS: when complication is on current watch face

### Always
- Location updates at any time
- System can launch app for significant-change, visits, region monitoring
- Not available on tvOS or visionOS
- Request only when necessary (time-sensitive automated responses)

### Capability Comparison

| Capability | When In Use | Always |
|------------|-------------|--------|
| Supported platforms | All | All except tvOS, visionOS |
| Supported services | All | All |
| Auto-launches terminated app | No | Yes (significant change, visits, region monitoring) |

## Info.plist Keys

### Required Keys

| Key | Required When |
|-----|--------------|
| `NSLocationWhenInUseUsageDescription` | App requests When In Use OR Always |
| `NSLocationAlwaysAndWhenInUseUsageDescription` | App requests Always authorization |

### Optional Keys

| Key | Purpose |
|-----|---------|
| `NSLocationUsageDescription` | macOS-only usage description |
| `NSLocationDefaultAccuracyReduced` | Default to reduced accuracy |
| `NSLocationAlwaysUsageDescription` | Legacy key (deprecated, use AlwaysAndWhenInUse) |

### Example Info.plist entries

```xml
<key>NSLocationWhenInUseUsageDescription</key>
<string>We need your location to show nearby charging stations.</string>

<key>NSLocationAlwaysAndWhenInUseUsageDescription</key>
<string>We need your location to notify you when you're near a charging station.</string>
```

## Requesting Authorization

### Standard Flow

```swift
let manager = CLLocationManager()

// Step 1: Check current status
switch manager.authorizationStatus {
case .notDetermined:
    // Request When In Use first
    manager.requestWhenInUseAuthorization()
case .authorizedWhenInUse:
    // Optionally request Always later
    manager.requestAlwaysAuthorization()
case .authorizedAlways:
    // Full access granted
    break
case .denied:
    // Direct user to Settings
    break
case .restricted:
    // Cannot change (parental controls, etc.)
    break
@unknown default:
    break
}
```

### Modern Async Flow (iOS 17+)

With live updates, authorization is requested automatically when you start
iterating the async stream, if status is `.notDetermined`:

```swift
let stream = CLLocationUpdate.liveUpdates()
for try await update in stream {
    if update.authorizationDenied {
        // Handle denied
    } else if update.authorizationRequestInProgress {
        // Dialog is showing
    } else if let location = update.location {
        // Process location
    }
}
```

### Temporary Full Accuracy

When the user has granted reduced accuracy, request temporary full accuracy:

```swift
// Requires a key in Info.plist under NSLocationTemporaryUsageDescriptionDictionary
manager.requestTemporaryFullAccuracyAuthorization(withPurposeKey: "DirectionsKey") { error in
    if error == nil {
        // Full accuracy temporarily granted
    }
}
```

## CLAuthorizationStatus Values

| Status | Value | Description |
|--------|-------|-------------|
| `.notDetermined` | 0 | User hasn't been asked |
| `.restricted` | 1 | Access restricted (parental controls, MDM) |
| `.denied` | 2 | User explicitly denied |
| `.authorizedAlways` | 3 | Always access granted |
| `.authorizedWhenInUse` | 4 | When In Use access granted |

## CLAccuracyAuthorization Values

| Value | Description |
|-------|-------------|
| `.fullAccuracy` | Full precision location data |
| `.reducedAccuracy` | Approximate location only (~5km radius); region monitoring and beacon ranging unavailable |

## Monitoring Authorization Changes

### Delegate-based

```swift
func locationManagerDidChangeAuthorization(_ manager: CLLocationManager) {
    switch manager.authorizationStatus {
    case .authorizedWhenInUse, .authorizedAlways:
        manager.startUpdatingLocation()
    case .denied, .restricted:
        // Disable location features
    case .notDetermined:
        // Waiting for user response
    @unknown default:
        break
    }

    // Also check accuracy
    switch manager.accuracyAuthorization {
    case .fullAccuracy:
        // Can use precise location
    case .reducedAccuracy:
        // Limited to approximate location
    @unknown default:
        break
    }
}
```

## CLServiceSession

Use `CLServiceSession` when your app always needs authorization. It provides
a single opportunity to upgrade from "When In Use" to "Always".

```swift
// Request Always authorization through a service session
let session = CLServiceSession(authorization: .always)

// With full accuracy purpose key
let session = CLServiceSession(
    authorization: .always,
    fullAccuracyPurposeKey: "NavigationKey"
)

// Monitor diagnostics
for try await diagnostic in session.diagnostics {
    // Check session status
}

// End the session
session.invalidate()
```

### AuthorizationRequirement enum

| Value | Description |
|-------|-------------|
| `.whenInUse` | Requires When In Use authorization |
| `.always` | Requires Always authorization |

## Suspending Authorization Requests

Defer the authorization dialog until your app is ready. Useful when you need
to show an onboarding screen first.

The system automatically shows the dialog when you start location services.
To defer it, don't start services until you're ready for the dialog.

## Widget Authorization

```swift
if manager.isAuthorizedForWidgetUpdates {
    // Widget can receive location updates
}
```

Widgets are eligible for location updates when the app has When In Use or
Always authorization.
