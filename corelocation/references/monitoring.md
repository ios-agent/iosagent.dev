# Region Monitoring & CLMonitor Reference

## CLMonitor (iOS 17+)

`CLMonitor` is a Swift actor that monitors conditions and delivers events
via an `AsyncSequence`. It replaces the legacy delegate-based region monitoring.

### Creating a Monitor

```swift
// Create with a unique identifier
let monitor = await CLMonitor("myAppMonitor")
```

Use the same identifier when recreating the monitor after app relaunch
to restore previously registered conditions.

### Adding Conditions

```swift
// Circular geographic condition (geofence)
let condition = CLMonitor.CircularGeographicCondition(
    center: CLLocationCoordinate2D(latitude: 37.3349, longitude: -122.0090),
    radius: 200  // meters
)
await monitor.add(condition, identifier: "apple-park")

// Beacon identity condition
let beaconCondition = CLMonitor.BeaconIdentityCondition(
    uuid: UUID(uuidString: "E2C56DB5-DFFB-48D2-B060-D0F5A71096E0")!
)
await monitor.add(beaconCondition, identifier: "my-beacon")
```

### Removing Conditions

```swift
await monitor.remove("apple-park")
```

### Observing Events

```swift
for try await event in await monitor.events {
    switch event.state {
    case .satisfied:
        print("Condition satisfied: \(event.identifier)")
        // User entered the region or beacon is in range
    case .unsatisfied:
        print("Condition unsatisfied: \(event.identifier)")
        // User left the region or beacon out of range
    case .unknown:
        print("State unknown: \(event.identifier)")
    @unknown default:
        break
    }
}
```

### Event Properties

| Property | Type | Description |
|----------|------|-------------|
| `identifier` | `String` | The identifier of the monitored condition |
| `state` | `CLMonitor.Event.State` | `.satisfied`, `.unsatisfied`, or `.unknown` |
| `date` | `Date` | When the event occurred |
| `refinement` | varies | Additional detail (e.g., beacon proximity) |

### Event States

| State | Meaning |
|-------|---------|
| `.satisfied` | Condition is met (user is inside region / beacon in range) |
| `.unsatisfied` | Condition is not met (user is outside / beacon out of range) |
| `.unknown` | State cannot be determined |

## CLMonitor.CircularGeographicCondition

Defines a circular area for geofencing.

```swift
let condition = CLMonitor.CircularGeographicCondition(
    center: CLLocationCoordinate2D(latitude: 48.8566, longitude: 2.3522),
    radius: 500  // meters
)
```

Properties:
- `center: CLLocationCoordinate2D` — Center of the circular region
- `radius: CLLocationDistance` — Radius in meters

## CLMonitor.BeaconIdentityCondition

Monitors for iBeacon devices matching specified identity criteria.

```swift
// Match any beacon with this UUID
let condition = CLMonitor.BeaconIdentityCondition(
    uuid: UUID(uuidString: "E2C56DB5-DFFB-48D2-B060-D0F5A71096E0")!
)

// Match specific major value
let condition = CLMonitor.BeaconIdentityCondition(
    uuid: myUUID,
    major: 1
)

// Match specific major and minor values
let condition = CLMonitor.BeaconIdentityCondition(
    uuid: myUUID,
    major: 1,
    minor: 100
)
```

## Full Geofencing Example

```swift
import CoreLocation

class GeofenceManager {
    private var monitor: CLMonitor?

    func startMonitoring() async {
        monitor = await CLMonitor("geofence-monitor")

        // Add regions
        let homeCondition = CLMonitor.CircularGeographicCondition(
            center: CLLocationCoordinate2D(latitude: 50.9375, longitude: 6.9603),
            radius: 100
        )
        await monitor?.add(homeCondition, identifier: "home")

        let officeCondition = CLMonitor.CircularGeographicCondition(
            center: CLLocationCoordinate2D(latitude: 50.9413, longitude: 6.9583),
            radius: 200
        )
        await monitor?.add(officeCondition, identifier: "office")

        // Listen for events
        guard let monitor = monitor else { return }
        for try await event in await monitor.events {
            handleEvent(event)
        }
    }

    private func handleEvent(_ event: CLMonitor.Event) {
        switch event.state {
        case .satisfied:
            print("Arrived at \(event.identifier)")
        case .unsatisfied:
            print("Left \(event.identifier)")
        default:
            break
        }
    }
}
```

## Important Behavior Notes

- On iOS, the system monitors conditions and wakes the app when states change.
- On macOS, monitoring works only while the app is running and the system is awake.
- The system does NOT launch Mac apps for region notifications.
- If the app isn't running when a condition is satisfied on iOS, the system
  tries to launch it. Recreate the monitor with the same identifier on relaunch.
- Monitoring can only occur after the user unlocks the device after a reboot.
- The maximum monitoring distance is available via
  `CLLocationManager.maximumRegionMonitoringDistance`.
- An app can register up to 20 regions at a time (legacy API limit).

## Legacy Region Monitoring (Pre-iOS 17)

The legacy approach uses `CLLocationManager` delegates. This is deprecated
but still functional:

```swift
// Legacy approach — prefer CLMonitor on iOS 17+
let region = CLCircularRegion(
    center: coordinate,
    radius: 200,
    identifier: "coffee-shop"
)
region.notifyOnEntry = true
region.notifyOnExit = true
manager.startMonitoring(for: region)

// Delegate methods
func locationManager(_ manager: CLLocationManager, didEnterRegion region: CLRegion) { }
func locationManager(_ manager: CLLocationManager, didExitRegion region: CLRegion) { }
```

## CLRegion

Base class for monitored areas.

| Subclass | Purpose |
|----------|---------|
| `CLCircularRegion` | Geographic circular region (legacy) |
| `CLBeaconRegion` | Beacon identity region (legacy) |

Properties:
- `identifier: String` — Unique identifier
- `notifyOnEntry: Bool` — Notify when entering
- `notifyOnExit: Bool` — Notify when exiting
