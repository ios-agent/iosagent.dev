# iBeacon & Compass Headings Reference

## iBeacon Ranging

### CLBeacon Properties

| Property | Type | Description |
|----------|------|-------------|
| `uuid` | `UUID` | The beacon's proximity UUID |
| `major` | `NSNumber` | The beacon's major value |
| `minor` | `NSNumber` | The beacon's minor value |
| `proximity` | `CLProximity` | Relative distance to the beacon |
| `accuracy` | `CLLocationAccuracy` | Estimated distance in meters (negative = unknown) |
| `rssi` | `Int` | Received signal strength in decibels |

### CLProximity Values

| Value | Meaning |
|-------|---------|
| `.unknown` | Proximity could not be determined |
| `.immediate` | Very close (within a few centimeters) |
| `.near` | Within a few meters |
| `.far` | Greater than 10 meters away |

### Ranging with CLMonitor (iOS 17+)

```swift
let monitor = await CLMonitor("beacon-monitor")

let condition = CLMonitor.BeaconIdentityCondition(
    uuid: UUID(uuidString: "E2C56DB5-DFFB-48D2-B060-D0F5A71096E0")!,
    major: 1,
    minor: 100
)
await monitor.add(condition, identifier: "my-beacon")

for try await event in await monitor.events {
    if event.state == .satisfied {
        // Beacon is in range
    }
}
```

### Legacy Beacon Ranging (Delegate-based)

```swift
// Create constraint
let constraint = CLBeaconIdentityConstraint(
    uuid: UUID(uuidString: "E2C56DB5-DFFB-48D2-B060-D0F5A71096E0")!
)

// Start ranging
manager.startRangingBeacons(satisfying: constraint)

// Delegate callback
func locationManager(
    _ manager: CLLocationManager,
    didRange beacons: [CLBeacon],
    satisfying constraint: CLBeaconIdentityConstraint
) {
    for beacon in beacons {
        print("UUID: \(beacon.uuid)")
        print("Major: \(beacon.major), Minor: \(beacon.minor)")
        print("Proximity: \(beacon.proximity.rawValue)")
        print("Accuracy: \(beacon.accuracy) meters")
        print("RSSI: \(beacon.rssi) dBm")
    }
}

// Stop ranging
manager.stopRangingBeacons(satisfying: constraint)
```

### CLBeaconIdentityConstraint

Used to match beacons by their identity:

```swift
// Match all beacons with this UUID
let constraint = CLBeaconIdentityConstraint(uuid: myUUID)

// Match beacons with specific major
let constraint = CLBeaconIdentityConstraint(uuid: myUUID, major: 1)

// Match specific beacon
let constraint = CLBeaconIdentityConstraint(uuid: myUUID, major: 1, minor: 100)
```

### CLBeaconRegion (Legacy)

```swift
let region = CLBeaconRegion(
    beaconIdentityConstraint: constraint,
    identifier: "my-beacon-region"
)
region.notifyEntryStateOnDisplay = true
```

### Turning a Device into an iBeacon

```swift
import CoreBluetooth

let peripheralManager = CBPeripheralManager()

// Create beacon region
let constraint = CLBeaconIdentityConstraint(
    uuid: UUID(uuidString: "E2C56DB5-DFFB-48D2-B060-D0F5A71096E0")!,
    major: 1,
    minor: 100
)
let region = CLBeaconRegion(beaconIdentityConstraint: constraint, identifier: "my-beacon")

// Get peripheral data
let peripheralData = region.peripheralData(withMeasuredPower: nil) as? [String: Any]

// Start advertising
peripheralManager.startAdvertising(peripheralData)
```

### Beacon Availability Check

```swift
if CLLocationManager.isRangingAvailable() {
    // Beacon ranging is supported
}
```

## Compass Headings

### CLHeading Properties

| Property | Type | Description |
|----------|------|-------------|
| `magneticHeading` | `CLLocationDirection` | Heading relative to magnetic north (0–359.9°) |
| `trueHeading` | `CLLocationDirection` | Heading relative to true north (0–359.9°); negative if invalid |
| `headingAccuracy` | `CLLocationDirection` | Maximum deviation in degrees; negative if invalid |
| `x` | `CLHeadingComponentValue` | Raw magnetometer X-axis value (microteslas) |
| `y` | `CLHeadingComponentValue` | Raw magnetometer Y-axis value (microteslas) |
| `z` | `CLHeadingComponentValue` | Raw magnetometer Z-axis value (microteslas) |
| `timestamp` | `Date` | Time the heading was determined |

### Starting Heading Updates

```swift
// Check availability first
guard CLLocationManager.headingAvailable() else {
    print("Heading not available on this device")
    return
}

let manager = CLLocationManager()
manager.delegate = self

// Optional: Set the minimum angle change to report
manager.headingFilter = 5  // degrees (kCLHeadingFilterNone for all changes)

// Optional: Set which device orientation represents "up"
manager.headingOrientation = .portrait

manager.startUpdatingHeading()
```

### Receiving Heading Updates

```swift
func locationManager(_ manager: CLLocationManager, didUpdateHeading newHeading: CLHeading) {
    // True heading requires location data to compute
    if newHeading.headingAccuracy >= 0 {
        let heading = newHeading.trueHeading  // Relative to true north
        let magnetic = newHeading.magneticHeading  // Relative to magnetic north
        print("True heading: \(heading)°, Magnetic: \(magnetic)°")
    }
}
```

### Stopping Heading Updates

```swift
manager.stopUpdatingHeading()
```

### Heading Filter

```swift
// Report every change
manager.headingFilter = kCLHeadingFilterNone

// Report only changes > 10 degrees
manager.headingFilter = 10
```

### Compass Calibration

The system may display a compass calibration alert. You can control this:

```swift
func locationManagerShouldDisplayHeadingCalibration(_ manager: CLLocationManager) -> Bool {
    return true  // Show the calibration UI when needed
}
```

### Important Notes

- `trueHeading` requires an active location fix to compute the magnetic
  declination. If no location is available, it returns a negative value.
- Heading data is not available on all devices. Always check
  `CLLocationManager.headingAvailable()`.
- For navigation, combine heading with course information from
  `CLLocation.course` for better results.
