---
name: apple-corelocation
description: >
  Reference skill for Apple's CoreLocation framework in Swift/SwiftUI.
  Use this skill whenever the user works with location services, GPS,
  geofencing, beacon ranging, geocoding, compass headings, or any
  CLLocationManager-related code on iOS, macOS, watchOS, or visionOS.
  Trigger on mentions of: CoreLocation, CLLocationManager, CLLocation,
  location permissions, geofencing, CLMonitor, iBeacon, CLGeocoder,
  reverse geocoding, background location updates, "When In Use" / "Always"
  authorization, CLLocationUpdate, live updates, significant location changes,
  or any location-related Info.plist keys like NSLocationWhenInUseUsageDescription.
---

# Apple CoreLocation Skill

Use this skill to write correct, modern CoreLocation code. CoreLocation provides
services for geographic location, altitude, orientation, and proximity to iBeacons.
It uses Wi-Fi, GPS, Bluetooth, magnetometer, barometer, and cellular hardware.

## When to Read Reference Files

This SKILL.md contains the essential patterns and quick-reference API surface.
For deeper implementation details, read the appropriate reference file:

| Topic | Reference File | When to Read |
|-------|---------------|--------------|
| Live Updates & async/await patterns | `references/live-updates.md` | SwiftUI apps, async location streams, background activity sessions |
| Authorization & Permissions | `references/authorization.md` | Permission flows, Info.plist keys, authorization status handling |
| Region Monitoring & CLMonitor | `references/monitoring.md` | Geofencing, condition monitoring, circular regions |
| Geocoding | `references/geocoding.md` | Address ↔ coordinate conversion, reverse geocoding, CLPlacemark |
| iBeacon & Compass | `references/beacon-compass.md` | Beacon ranging, heading updates, magnetometer |
| Background Location | `references/background.md` | Background updates, CLBackgroundActivitySession, power optimization |
| CLLocationManager API | `references/location-manager.md` | Full property/method reference for CLLocationManager |

## Modern CoreLocation (iOS 17+): Prefer Async/Await

Since iOS 17, CoreLocation supports Swift concurrency. Prefer the modern async API
over the legacy delegate-based approach for new projects.

### Getting Live Location Updates (Recommended Pattern)

```swift
import CoreLocation

let updates = CLLocationUpdate.liveUpdates()

for try await update in updates {
    if let location = update.location {
        // Process location
        print("Lat: \(location.coordinate.latitude), Lon: \(location.coordinate.longitude)")
    }
    if update.authorizationDenied {
        // Handle denied authorization
    }
    if update.authorizationRequestInProgress {
        // System is showing the authorization dialog
    }
}
```

The system automatically prompts for authorization when iteration begins if
status is `.notDetermined`. No explicit `requestWhenInUseAuthorization()` call
is needed with this pattern, but you may still call it for controlled timing.

### Live Updates with Accuracy Configuration

```swift
// High accuracy (GPS, more power)
let updates = CLLocationUpdate.liveUpdates(.default)

// Power-efficient options
let updates = CLLocationUpdate.liveUpdates(.automotiveNavigation)
let updates = CLLocationUpdate.liveUpdates(.otherNavigation)
let updates = CLLocationUpdate.liveUpdates(.fitness)
let updates = CLLocationUpdate.liveUpdates(.airborne)
```

### CLLocationUpdate Properties

- `location: CLLocation?` — The location, or nil if unavailable
- `isStationary: Bool` — Whether the device is stationary
- `authorizationDenied: Bool` — Authorization was denied
- `authorizationDeniedGlobally: Bool` — Location services disabled system-wide
- `authorizationRequestInProgress: Bool` — Auth dialog is being shown
- `insufficientlyInUse: Bool` — App lacks sufficient "in use" state
- `locationUnavailable: Bool` — Location data temporarily unavailable
- `accuracyLimited: Bool` — Accuracy authorization is reduced

## SwiftUI Integration Pattern

```swift
@MainActor
class LocationsHandler: ObservableObject {
    static let shared = LocationsHandler()
    private let manager: CLLocationManager
    private var background: CLBackgroundActivitySession?

    @Published var lastLocation = CLLocation()
    @Published var isStationary = false

    @Published var updatesStarted: Bool = UserDefaults.standard.bool(forKey: "liveUpdatesStarted") {
        didSet { UserDefaults.standard.set(updatesStarted, forKey: "liveUpdatesStarted") }
    }

    private init() {
        self.manager = CLLocationManager()
    }

    func startLocationUpdates() {
        if self.manager.authorizationStatus == .notDetermined {
            self.manager.requestWhenInUseAuthorization()
        }
        Task {
            do {
                self.updatesStarted = true
                let updates = CLLocationUpdate.liveUpdates()
                for try await update in updates {
                    if !self.updatesStarted { break }
                    if let loc = update.location {
                        self.lastLocation = loc
                        self.isStationary = update.isStationary
                    }
                }
            } catch {
                print("Could not start location updates")
            }
        }
    }

    func stopLocationUpdates() {
        self.updatesStarted = false
    }
}
```

## Authorization Quick Reference

### Info.plist Keys (Required)

| Key | When to Use |
|-----|-------------|
| `NSLocationWhenInUseUsageDescription` | App uses location while in foreground |
| `NSLocationAlwaysAndWhenInUseUsageDescription` | App needs location in background too |
| `NSLocationDefaultAccuracyReduced` | Request reduced accuracy by default |

### Authorization Status Values (`CLAuthorizationStatus`)

| Value | Meaning |
|-------|---------|
| `.notDetermined` | User hasn't been asked yet |
| `.restricted` | App cannot use location (e.g., parental controls) |
| `.denied` | User explicitly denied |
| `.authorizedWhenInUse` | App can use location while in foreground |
| `.authorizedAlways` | App can use location at any time |

### Requesting Authorization

```swift
let manager = CLLocationManager()

// For foreground-only access
manager.requestWhenInUseAuthorization()

// For background access (after getting "When In Use" first)
manager.requestAlwaysAuthorization()

// For temporary full accuracy (when user granted reduced accuracy)
manager.requestTemporaryFullAccuracyAuthorization(withPurposeKey: "MyPurposeKey")
```

## Condition Monitoring with CLMonitor (iOS 17+)

```swift
let monitor = await CLMonitor("myMonitor")

// Add a circular geographic condition
await monitor.add(
    CLMonitor.CircularGeographicCondition(center: coordinate, radius: 200),
    identifier: "coffee-shop"
)

// Observe events
for try await event in await monitor.events {
    switch event.state {
    case .satisfied:
        print("Entered region: \(event.identifier)")
    case .unsatisfied:
        print("Exited region: \(event.identifier)")
    default:
        break
    }
}
```

## Geocoding Quick Reference

```swift
let geocoder = CLGeocoder()

// Reverse geocode: coordinate → address
geocoder.reverseGeocodeLocation(location) { placemarks, error in
    if let placemark = placemarks?.first {
        print(placemark.locality ?? "Unknown city")
    }
}

// Forward geocode: address → coordinate
geocoder.geocodeAddressString("1 Apple Park Way, Cupertino") { placemarks, error in
    if let location = placemarks?.first?.location {
        print(location.coordinate)
    }
}
```

## CLLocation Key Properties

| Property | Type | Description |
|----------|------|-------------|
| `coordinate` | `CLLocationCoordinate2D` | Latitude and longitude (WGS 84) |
| `altitude` | `CLLocationDistance` | Meters above sea level |
| `horizontalAccuracy` | `CLLocationAccuracy` | Accuracy in meters (negative = invalid) |
| `verticalAccuracy` | `CLLocationAccuracy` | Altitude accuracy in meters |
| `speed` | `CLLocationSpeed` | Meters per second |
| `course` | `CLLocationDirection` | Degrees relative to true north |
| `timestamp` | `Date` | When the location was determined |
| `floor` | `CLFloor?` | Floor of a building, if available |
| `sourceInformation` | `CLLocationSourceInformation?` | Info about the location source |

## Power Optimization Guidelines

Choose the most power-efficient service for your use case:

1. **Visits service** (`startMonitoringVisits()`) — Most power-efficient. Reports
   places visited and time spent. Good for: check-in apps, travel logs.

2. **Significant-change service** (`startMonitoringSignificantLocationChanges()`) —
   Low power, uses Wi-Fi/cellular only. Good for: approximate location tracking.

3. **Standard location service** (`startUpdatingLocation()`) — Configurable
   accuracy via `desiredAccuracy`. Good for: navigation, fitness tracking.

4. **Live updates** (`CLLocationUpdate.liveUpdates()`) — Modern async API with
   configurable activity types. Good for: any new project on iOS 17+.

### Desired Accuracy Constants

| Constant | Description |
|----------|-------------|
| `kCLLocationAccuracyBestForNavigation` | Highest precision, most power |
| `kCLLocationAccuracyBest` | Best available accuracy |
| `kCLLocationAccuracyNearestTenMeters` | Within ~10 meters |
| `kCLLocationAccuracyHundredMeters` | Within ~100 meters |
| `kCLLocationAccuracyKilometer` | Within ~1 km |
| `kCLLocationAccuracyThreeKilometers` | Within ~3 km |
| `kCLLocationAccuracyReduced` | Deliberately reduced accuracy |

## Platform Considerations

- **visionOS**: Location services are limited. Background updates are not supported.
  Region monitoring methods do nothing for compatible iPad/iPhone apps running in visionOS.
- **macOS**: Apps are not suspended in background, so no special background capability needed.
- **watchOS**: Supports background location with capability. Use `CLBackgroundActivitySession`.
- **Widgets**: Check `isAuthorizedForWidgetUpdates` for widget eligibility.

## Common Pitfalls

- Always check `horizontalAccuracy` — negative values mean the coordinate is invalid.
- Do not assume location is immediately available after starting services.
- Handle authorization changes gracefully; users can revoke at any time via Settings.
- Geocoder requests are rate-limited; cache results and do not geocode on every location update.
- The system can pause location updates automatically. Set `pausesLocationUpdatesAutomatically`
  and `activityType` to help CoreLocation make good decisions.
- For background updates on iOS: add the "Location updates" background mode capability
  AND set `allowsBackgroundLocationUpdates = true` on the location manager.
