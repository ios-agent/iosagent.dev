# CLLocationManager API Reference

The central object for configuring, starting, and stopping Core Location services.

```swift
class CLLocationManager: NSObject
```

## Initialization

```swift
let manager = CLLocationManager()
manager.delegate = self  // CLLocationManagerDelegate
```

## Authorization Properties & Methods

| Member | Type | Description |
|--------|------|-------------|
| `authorizationStatus` | `CLAuthorizationStatus` | Current authorization status |
| `accuracyAuthorization` | `CLAccuracyAuthorization` | Full or reduced accuracy |
| `isAuthorizedForWidgetUpdates` | `Bool` | Widget eligibility |
| `requestWhenInUseAuthorization()` | Method | Request foreground access |
| `requestAlwaysAuthorization()` | Method | Request always access |
| `requestTemporaryFullAccuracyAuthorization(withPurposeKey:)` | Method | Request temp full accuracy |
| `requestTemporaryFullAccuracyAuthorization(withPurposeKey:completion:)` | Method | Same with completion handler |

## Service Availability (Type Methods)

| Method | Returns | Description |
|--------|---------|-------------|
| `locationServicesEnabled()` | `Bool` | Location services enabled globally |
| `headingAvailable()` | `Bool` | Heading data available on device |
| `significantLocationChangeMonitoringAvailable()` | `Bool` | Significant-change service available |
| `isMonitoringAvailable(for:)` | `Bool` | Region monitoring available |
| `isRangingAvailable()` | `Bool` | Beacon ranging available |

## Standard Location Service

```swift
// Configure
manager.desiredAccuracy = kCLLocationAccuracyBest
manager.distanceFilter = 10  // meters, or kCLDistanceFilterNone
manager.activityType = .fitness

// Start/stop
manager.startUpdatingLocation()
manager.stopUpdatingLocation()

// One-time request
manager.requestLocation()
```

### Desired Accuracy Constants

| Constant | Description |
|----------|-------------|
| `kCLLocationAccuracyBestForNavigation` | Highest precision, most power |
| `kCLLocationAccuracyBest` | Best available |
| `kCLLocationAccuracyNearestTenMeters` | ~10 meters |
| `kCLLocationAccuracyHundredMeters` | ~100 meters |
| `kCLLocationAccuracyKilometer` | ~1 km |
| `kCLLocationAccuracyThreeKilometers` | ~3 km |
| `kCLLocationAccuracyReduced` | Deliberately reduced |

### Distance Filter

```swift
manager.distanceFilter = kCLDistanceFilterNone  // All movement reported
manager.distanceFilter = 50  // Only report after 50 meter change
```

## Significant Location Changes

Low-power location monitoring using cell tower and Wi-Fi (no GPS):

```swift
manager.startMonitoringSignificantLocationChanges()
manager.stopMonitoringSignificantLocationChanges()
```

## Visits Service

Most power-efficient. Reports places the user visits:

```swift
manager.startMonitoringVisits()
manager.stopMonitoringVisits()
```

Delegate callback:
```swift
func locationManager(_ manager: CLLocationManager, didVisit visit: CLVisit) {
    print("Arrived: \(visit.arrivalDate)")
    print("Departed: \(visit.departureDate)")
    print("Coordinate: \(visit.coordinate)")
    print("Accuracy: \(visit.horizontalAccuracy)")
}
```

## Background Configuration

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `allowsBackgroundLocationUpdates` | `Bool` | `false` | Enable background updates |
| `showsBackgroundLocationIndicator` | `Bool` | `false` | Show blue status bar pill |
| `pausesLocationUpdatesAutomatically` | `Bool` | `true` (on supported) | Allow system to pause updates |
| `activityType` | `CLActivityType` | `.other` | Activity type hint for power optimization |

## Heading Updates

```swift
// Check availability
guard CLLocationManager.headingAvailable() else { return }

// Configure
manager.headingFilter = 5  // degrees, or kCLHeadingFilterNone
manager.headingOrientation = .portrait

// Start/stop
manager.startUpdatingHeading()
manager.stopUpdatingHeading()

// Dismiss calibration display
manager.dismissHeadingCalibrationDisplay()
```

## Region Monitoring (Legacy)

```swift
// Maximum monitoring distance
let maxDistance = manager.maximumRegionMonitoringDistance

// Start/stop monitoring
manager.startMonitoring(for: region)
manager.stopMonitoring(for: region)

// Currently monitored regions
let regions = manager.monitoredRegions

// Request state for a region
manager.requestState(for: region)
```

## Beacon Ranging

```swift
// Start/stop ranging
manager.startRangingBeacons(satisfying: constraint)
manager.stopRangingBeacons(satisfying: constraint)

// Currently ranged constraints
let constraints = manager.rangedBeaconConstraints
```

## CLLocationManagerDelegate

### Location Updates

```swift
func locationManager(_ manager: CLLocationManager, didUpdateLocations locations: [CLLocation]) {
    guard let location = locations.last else { return }
    // Process most recent location
}

func locationManager(_ manager: CLLocationManager, didFailWithError error: Error) {
    // Handle error
}
```

### Authorization

```swift
func locationManagerDidChangeAuthorization(_ manager: CLLocationManager) {
    switch manager.authorizationStatus {
    case .authorizedWhenInUse, .authorizedAlways:
        // Start services
    case .denied, .restricted:
        // Disable features
    case .notDetermined:
        // Waiting
    @unknown default:
        break
    }
}
```

### Heading

```swift
func locationManager(_ manager: CLLocationManager, didUpdateHeading newHeading: CLHeading) { }
func locationManagerShouldDisplayHeadingCalibration(_ manager: CLLocationManager) -> Bool { true }
```

### Region Monitoring (Legacy)

```swift
func locationManager(_ manager: CLLocationManager, didEnterRegion region: CLRegion) { }
func locationManager(_ manager: CLLocationManager, didExitRegion region: CLRegion) { }
func locationManager(_ manager: CLLocationManager, didDetermineState state: CLRegionState, for region: CLRegion) { }
func locationManager(_ manager: CLLocationManager, monitoringDidFailFor region: CLRegion?, withError error: Error) { }
```

### Beacon Ranging

```swift
func locationManager(_ manager: CLLocationManager, didRange beacons: [CLBeacon], satisfying constraint: CLBeaconIdentityConstraint) { }
func locationManager(_ manager: CLLocationManager, didFailRangingFor constraint: CLBeaconIdentityConstraint, error: Error) { }
```

### Pausing

```swift
func locationManagerDidPauseLocationUpdates(_ manager: CLLocationManager) { }
func locationManagerDidResumeLocationUpdates(_ manager: CLLocationManager) { }
```

### Visits

```swift
func locationManager(_ manager: CLLocationManager, didVisit visit: CLVisit) { }
```

## CLLocation

The latitude, longitude, and course information reported by the system.

### Properties

| Property | Type | Description |
|----------|------|-------------|
| `coordinate` | `CLLocationCoordinate2D` | Lat/lon (WGS 84) |
| `altitude` | `CLLocationDistance` | Meters above sea level |
| `ellipsoidalAltitude` | `CLLocationDistance` | Height above WGS 84 ellipsoid |
| `horizontalAccuracy` | `CLLocationAccuracy` | Accuracy in meters (negative = invalid) |
| `verticalAccuracy` | `CLLocationAccuracy` | Altitude accuracy in meters |
| `speed` | `CLLocationSpeed` | Meters per second |
| `speedAccuracy` | `CLLocationSpeedAccuracy` | Speed accuracy in m/s |
| `course` | `CLLocationDirection` | Degrees from true north (0–359.9) |
| `courseAccuracy` | `CLLocationDirectionAccuracy` | Course accuracy in degrees |
| `timestamp` | `Date` | When determined |
| `floor` | `CLFloor?` | Building floor (if available) |
| `sourceInformation` | `CLLocationSourceInformation?` | Source info |

### Creating CLLocation

```swift
// Simple
let location = CLLocation(latitude: 37.33, longitude: -122.03)

// Full
let location = CLLocation(
    coordinate: CLLocationCoordinate2D(latitude: 37.33, longitude: -122.03),
    altitude: 72.0,
    horizontalAccuracy: 10.0,
    verticalAccuracy: 5.0,
    course: 180.0,
    courseAccuracy: 10.0,
    speed: 1.5,
    speedAccuracy: 0.5,
    timestamp: Date()
)
```

### Distance Calculation

```swift
let distance = location1.distance(from: location2)  // meters
```

## CLLocationCoordinate2D

```swift
// Create
let coord = CLLocationCoordinate2D(latitude: 37.33, longitude: -122.03)

// Validate
let isValid = CLLocationCoordinate2DIsValid(coord)
let invalid = kCLLocationCoordinate2DInvalid  // Sentinel value

// Access
let lat = coord.latitude   // CLLocationDegrees (Double)
let lon = coord.longitude  // CLLocationDegrees (Double)
```

## CLVisit

Information about a user's visit to a location:

| Property | Type | Description |
|----------|------|-------------|
| `coordinate` | `CLLocationCoordinate2D` | Where the visit occurred |
| `horizontalAccuracy` | `CLLocationAccuracy` | Accuracy of coordinate |
| `arrivalDate` | `Date` | When user arrived |
| `departureDate` | `Date` | When user departed |

## CLError Codes

| Code | Description |
|------|-------------|
| `.locationUnknown` | Location could not be determined |
| `.denied` | User denied authorization |
| `.promptDeclined` | User dismissed the authorization prompt |
| `.network` | Network unavailable |
| `.headingFailure` | Heading could not be determined |
| `.regionMonitoringDenied` | Region monitoring denied |
| `.regionMonitoringFailure` | Region monitoring failed |
| `.regionMonitoringSetupDelayed` | Region monitoring setup delayed |
| `.regionMonitoringResponseDelayed` | Region monitoring response delayed |
| `.geocodeCanceled` | Geocode request was cancelled |
| `.geocodeFoundNoResult` | No geocoding result found |
| `.geocodeFoundPartialResult` | Partial geocoding result |
| `.rangingUnavailable` | Ranging not available |
| `.rangingFailure` | Ranging failed |

## Type Aliases

| Alias | Actual Type | Description |
|-------|-------------|-------------|
| `CLLocationDegrees` | `Double` | Latitude or longitude value |
| `CLLocationAccuracy` | `Double` | Accuracy in meters |
| `CLLocationSpeed` | `Double` | Speed in meters/second |
| `CLLocationSpeedAccuracy` | `Double` | Speed accuracy in m/s |
| `CLLocationDirection` | `Double` | Direction in degrees |
| `CLLocationDirectionAccuracy` | `Double` | Direction accuracy in degrees |
| `CLLocationDistance` | `Double` | Distance in meters |
| `CLLocationDistanceMax` | `CLLocationDistance` | Maximum distance value |
