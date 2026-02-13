# Geocoding Reference

## CLGeocoder

Converts between geographic coordinates and human-readable place names.
Uses Apple servers for the conversion. Requests are rate-limited.

### Reverse Geocoding (Coordinate → Address)

```swift
let geocoder = CLGeocoder()

// Async/completion handler pattern
geocoder.reverseGeocodeLocation(location) { placemarks, error in
    guard error == nil, let placemark = placemarks?.first else {
        print("Geocoding failed: \(error?.localizedDescription ?? "unknown error")")
        return
    }

    print(placemark.name ?? "")           // e.g., "Apple Park"
    print(placemark.thoroughfare ?? "")   // e.g., "Apple Park Way"
    print(placemark.subThoroughfare ?? "")// e.g., "1"
    print(placemark.locality ?? "")       // e.g., "Cupertino"
    print(placemark.administrativeArea ?? "") // e.g., "CA"
    print(placemark.postalCode ?? "")     // e.g., "95014"
    print(placemark.country ?? "")        // e.g., "United States"
    print(placemark.isoCountryCode ?? "") // e.g., "US"
}
```

### Forward Geocoding (Address → Coordinate)

```swift
let geocoder = CLGeocoder()

geocoder.geocodeAddressString("1 Apple Park Way, Cupertino, CA") { placemarks, error in
    guard error == nil, let placemark = placemarks?.first else {
        print("Geocoding failed: \(error?.localizedDescription ?? "unknown error")")
        return
    }

    if let location = placemark.location {
        print("Lat: \(location.coordinate.latitude)")
        print("Lon: \(location.coordinate.longitude)")
    }
}
```

### Forward Geocoding with Region Hint

Providing a region biases results toward that area:

```swift
let region = CLCircularRegion(
    center: CLLocationCoordinate2D(latitude: 37.33, longitude: -122.03),
    radius: 50000,
    identifier: "search"
)

geocoder.geocodeAddressString("Main Street", in: region) { placemarks, error in
    // Results biased toward the Bay Area
}
```

### Cancelling a Request

```swift
geocoder.cancelGeocode()
```

Only one geocode request can be active at a time per `CLGeocoder` instance.

## CLPlacemark Properties

| Property | Type | Description |
|----------|------|-------------|
| `name` | `String?` | Name of the placemark |
| `thoroughfare` | `String?` | Street name |
| `subThoroughfare` | `String?` | Street number |
| `locality` | `String?` | City |
| `subLocality` | `String?` | Neighborhood |
| `administrativeArea` | `String?` | State/province |
| `subAdministrativeArea` | `String?` | County |
| `postalCode` | `String?` | ZIP/postal code |
| `country` | `String?` | Country name |
| `isoCountryCode` | `String?` | ISO country code |
| `location` | `CLLocation?` | The geographic location |
| `region` | `CLRegion?` | Geographic region associated with the placemark |
| `timeZone` | `TimeZone?` | Time zone of the placemark |
| `inlandWater` | `String?` | Name of inland water body |
| `ocean` | `String?` | Name of ocean |
| `areasOfInterest` | `[String]?` | Relevant areas of interest |

## Best Practices

- **Cache results**: Geocoder requests go to Apple servers. Cache placemarks
  to avoid unnecessary network calls.
- **Rate limiting**: Do NOT geocode on every location update. Throttle requests.
  The system will return errors if you exceed the rate limit.
- **One request at a time**: Each `CLGeocoder` instance can handle only one
  request at a time. Create multiple instances if needed.
- **Multiple results**: Forward geocoding may return multiple placemarks.
  Disambiguate by providing more specific address strings or region hints.
- **Error handling**: Always handle errors. Common failure reasons include
  no network, rate limiting, and invalid/ambiguous addresses.

## Error Handling

```swift
geocoder.reverseGeocodeLocation(location) { placemarks, error in
    if let error = error as? CLError {
        switch error.code {
        case .geocodeCanceled:
            print("Geocoding was cancelled")
        case .geocodeFoundNoResult:
            print("No result found for this location")
        case .geocodeFoundPartialResult:
            print("Partial result — some data may be missing")
        case .network:
            print("Network error")
        default:
            print("Geocoding error: \(error.localizedDescription)")
        }
        return
    }
    // Process placemarks...
}
```

## Async/Await Geocoding (iOS 16.4+)

```swift
do {
    let placemarks = try await geocoder.reverseGeocodeLocation(location)
    if let placemark = placemarks.first {
        print(placemark.locality ?? "Unknown")
    }
} catch {
    print("Geocoding failed: \(error)")
}
```
