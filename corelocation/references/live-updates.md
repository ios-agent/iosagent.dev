# Live Updates & Async/Await Patterns

## CLLocationUpdate (iOS 17+)

The modern way to receive location updates using Swift concurrency.

### Starting Live Updates

```swift
// Default configuration
let updates = CLLocationUpdate.liveUpdates()

// With activity type for power optimization
let updates = CLLocationUpdate.liveUpdates(.automotiveNavigation)
let updates = CLLocationUpdate.liveUpdates(.otherNavigation)
let updates = CLLocationUpdate.liveUpdates(.fitness)
let updates = CLLocationUpdate.liveUpdates(.airborne)
```

### Processing Updates

```swift
for try await update in CLLocationUpdate.liveUpdates() {
    // Check for location data
    if let location = update.location {
        let lat = location.coordinate.latitude
        let lon = location.coordinate.longitude
        let accuracy = location.horizontalAccuracy
        let altitude = location.altitude
        let speed = location.speed
        let course = location.course
    }

    // Check diagnostic properties
    if update.authorizationDenied {
        // User denied location access
    }
    if update.authorizationDeniedGlobally {
        // Location services are disabled system-wide
    }
    if update.authorizationRequestInProgress {
        // Authorization dialog is currently showing
    }
    if update.insufficientlyInUse {
        // App lacks sufficient "in use" state for updates
    }
    if update.locationUnavailable {
        // Location data is temporarily unavailable
    }
    if update.accuracyLimited {
        // User granted only reduced accuracy
    }
    if update.isStationary {
        // Device is stationary
    }
}
```

### CLLocationUpdate Properties Reference

| Property | Type | Description |
|----------|------|-------------|
| `location` | `CLLocation?` | Current location, nil if unavailable |
| `isStationary` | `Bool` | Device is stationary |
| `authorizationDenied` | `Bool` | Authorization explicitly denied |
| `authorizationDeniedGlobally` | `Bool` | Location services disabled globally |
| `authorizationRequestInProgress` | `Bool` | Auth dialog is showing |
| `authorizationRestricted` | `Bool` | Authorization restricted (e.g., parental controls) |
| `insufficientlyInUse` | `Bool` | App not sufficiently "in use" |
| `locationUnavailable` | `Bool` | Location temporarily unavailable |
| `accuracyLimited` | `Bool` | Reduced accuracy granted |
| `serviceSessionRequired` | `Bool` | CLServiceSession needed |
| `stationary` | `Bool` | Alias for isStationary |

### CLLocationUpdate.Updates

The `CLLocationUpdate.Updates` type is the `AsyncSequence` returned by `liveUpdates()`.
It conforms to `AsyncSequence` where `Element` is `CLLocationUpdate`.

## SwiftUI Full Integration Pattern

This is the recommended pattern for SwiftUI apps using live updates with
background support:

### 1. Shared Location Handler

```swift
import CoreLocation

@MainActor
class LocationsHandler: ObservableObject {
    static let shared = LocationsHandler()
    private let manager: CLLocationManager
    private var background: CLBackgroundActivitySession?

    @Published var lastLocation = CLLocation()
    @Published var isStationary = false
    @Published var count = 0

    @Published var updatesStarted: Bool = UserDefaults.standard.bool(forKey: "liveUpdatesStarted") {
        didSet { UserDefaults.standard.set(updatesStarted, forKey: "liveUpdatesStarted") }
    }

    @Published var backgroundActivity: Bool = UserDefaults.standard.bool(forKey: "BGActivitySessionStarted") {
        didSet {
            backgroundActivity
                ? (self.background = CLBackgroundActivitySession())
                : self.background?.invalidate()
            UserDefaults.standard.set(backgroundActivity, forKey: "BGActivitySessionStarted")
        }
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
                        self.count += 1
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

### 2. AppDelegate for Background Resume

```swift
import UIKit

class AppDelegate: NSObject, UIApplicationDelegate, ObservableObject {
    func application(
        _ application: UIApplication,
        didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]? = nil
    ) -> Bool {
        let handler = LocationsHandler.shared

        // Resume updates after background launch
        if handler.updatesStarted {
            handler.startLocationUpdates()
        }
        // Reinstate background session
        if handler.backgroundActivity {
            handler.backgroundActivity = true
        }
        return true
    }
}
```

### 3. App Entry Point

```swift
@main
struct MyApp: App {
    @UIApplicationDelegateAdaptor private var appDelegate: AppDelegate

    var body: some Scene {
        WindowGroup {
            ContentView()
        }
    }
}
```

The AppDelegate is critical for background resumption. When the system relaunches
the app after suspension or crash, `didFinishLaunchingWithOptions` restores the
location update and background activity session state.

## CLBackgroundActivitySession

Maintains a visual indicator (blue status bar pill on iOS) showing that
the app is using location in the background.

```swift
// Start a background activity session
let session = CLBackgroundActivitySession()

// End the session
session.invalidate()
```

The session keeps the app in a state where it can receive location updates
in the background. Persist the session state (e.g., via UserDefaults) so it
can be restored after app relaunch.

## Adopting Live Updates: Migration Guide

### Before (Delegate-based)

```swift
class LocationTracker: NSObject, CLLocationManagerDelegate {
    let manager = CLLocationManager()

    func start() {
        manager.delegate = self
        manager.requestWhenInUseAuthorization()
        manager.startUpdatingLocation()
    }

    func locationManager(_ manager: CLLocationManager, didUpdateLocations locations: [CLLocation]) {
        guard let location = locations.last else { return }
        // Process location
    }

    func locationManager(_ manager: CLLocationManager, didFailWithError error: Error) {
        // Handle error
    }
}
```

### After (Async/await)

```swift
class LocationTracker {
    func start() async throws {
        for try await update in CLLocationUpdate.liveUpdates() {
            if let location = update.location {
                // Process location
            }
        }
    }
}
```

The async version is simpler, eliminates the delegate, and provides
inline diagnostic properties for authorization and availability issues.
