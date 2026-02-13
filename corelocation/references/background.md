# Background Location Updates Reference

## When to Use Background Location

Use background updates ONLY when your app needs real-time location while
not in the foreground:

- Track precise path during hike or fitness workout
- Provide real-time navigation instructions
- Generate time-sensitive notifications
- Take immediate action on region entry/exit

## Setup Requirements (iOS/iPadOS/watchOS)

macOS does not need special setup — apps are not suspended in background.
visionOS does NOT support background location updates.

### Step 1: Add Background Mode Capability

In Xcode → Target → Signing & Capabilities → add "Background Modes":
- Check **Location updates**

This adds `UIBackgroundModes` with `location` to your Info.plist:

```xml
<key>UIBackgroundModes</key>
<array>
    <string>location</string>
</array>
```

### Step 2: Enable Background Updates in Code

```swift
let manager = CLLocationManager()
manager.allowsBackgroundLocationUpdates = true
manager.showsBackgroundLocationIndicator = true  // Blue status bar pill
```

### Step 3: Start a Background Activity Session

```swift
let backgroundSession = CLBackgroundActivitySession()
// Hold a reference to this — releasing it ends the session
```

### Step 4: Configure Power Optimization

```swift
manager.activityType = .fitness  // or .automotiveNavigation, .otherNavigation, etc.
manager.pausesLocationUpdatesAutomatically = true  // Save battery when stationary
```

## CLBackgroundActivitySession

Manages a visual indicator (blue pill on iOS status bar) that keeps your
app "in use" in the background, allowing continued location updates.

```swift
// Start session
let session = CLBackgroundActivitySession()

// End session
session.invalidate()
```

Persist session state via UserDefaults so you can restore it after app relaunch.

## Activity Types (`CLActivityType`)

Set `activityType` to help CoreLocation optimize power usage:

| Value | Use Case | Effect |
|-------|----------|--------|
| `.other` | Default | No specific optimization |
| `.automotiveNavigation` | Car navigation | Expects road-like movement |
| `.fitness` | Walking, running, cycling | Pedestrian-speed movement |
| `.otherNavigation` | Non-automotive navigation | General navigation |
| `.airborne` | Flying | High altitude, high speed |

## Automatic Pausing

When `pausesLocationUpdatesAutomatically = true`:

- CoreLocation pauses updates when location is unlikely to change
  (e.g., user stopped moving)
- Saves significant battery
- Your delegate receives `locationManagerDidPauseLocationUpdates(_:)`
- Your responsibility to restart when needed (use a `UNLocationNotificationTrigger`
  to alert the user)

```swift
func locationManagerDidPauseLocationUpdates(_ manager: CLLocationManager) {
    // Configure a local notification to prompt user to reopen app
    let trigger = UNLocationNotificationTrigger(
        region: CLCircularRegion(
            center: manager.location?.coordinate ?? CLLocationCoordinate2D(),
            radius: 100,
            identifier: "resume"
        ),
        repeats: false
    )
    // ... schedule notification with this trigger
}
```

## Full Background Location Pattern (SwiftUI)

```swift
@MainActor
class LocationsHandler: ObservableObject {
    static let shared = LocationsHandler()
    private let manager: CLLocationManager
    private var background: CLBackgroundActivitySession?

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
        if manager.authorizationStatus == .notDetermined {
            manager.requestWhenInUseAuthorization()
        }
        Task {
            updatesStarted = true
            let updates = CLLocationUpdate.liveUpdates(.fitness)
            for try await update in updates {
                if !updatesStarted { break }
                if let loc = update.location {
                    // Process location
                }
            }
        }
    }

    func stopLocationUpdates() {
        updatesStarted = false
    }
}
```

### AppDelegate for Background Resume

```swift
class AppDelegate: NSObject, UIApplicationDelegate, ObservableObject {
    func application(
        _ application: UIApplication,
        didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]? = nil
    ) -> Bool {
        let handler = LocationsHandler.shared
        if handler.updatesStarted {
            handler.startLocationUpdates()
        }
        if handler.backgroundActivity {
            handler.backgroundActivity = true
        }
        return true
    }
}
```

### App Entry Point

```swift
@main
struct MyApp: App {
    @UIApplicationDelegateAdaptor private var appDelegate: AppDelegate
    var body: some Scene {
        WindowGroup { ContentView() }
    }
}
```

## Location Push Service Extension

For location-sharing apps, CoreLocation supports a push-based approach
to query a user's location via push notification:

1. Add `com.apple.developer.location.push` entitlement
2. Create a Location Push Service Extension target
3. Implement `CLLocationPushServiceExtension`:

```swift
class LocationPushService: CLLocationPushServiceExtension {
    func didReceiveLocationPushPayload(
        _ payload: [String: Any],
        completion: @escaping () -> Void
    ) {
        // Start location updates
        let manager = CLLocationManager()
        manager.requestLocation()
        // Send location to server, then call completion
        completion()
    }
}
```

## Power Optimization Checklist

1. Choose the least power-hungry service for your needs
2. Set appropriate `activityType`
3. Enable `pausesLocationUpdatesAutomatically` when possible
4. Use `desiredAccuracy` wisely — don't request GPS if Wi-Fi accuracy suffices
5. Set `distanceFilter` to avoid unnecessary updates
6. Stop updates as soon as you no longer need them
7. Use `CLBackgroundActivitySession` only when truly needed
