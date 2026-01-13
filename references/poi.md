# CarPlay Point of Interest Apps

Point of Interest (POI) apps help users discover and navigate to locations like restaurants, gas stations, parking, and other destinations.

## Requirements

- Entitlement: One of the following based on app category:
  - `com.apple.developer.carplay-parking`
  - `com.apple.developer.carplay-charging`
  - `com.apple.developer.carplay-quick-ordering`
  - `com.apple.developer.carplay-fueling`
- iOS 14.0+

## POI Template

### Basic Setup

```swift
import CarPlay
import CoreLocation

class CarPlaySceneDelegate: UIResponder, CPTemplateApplicationSceneDelegate {
    var interfaceController: CPInterfaceController?

    func templateApplicationScene(
        _ templateApplicationScene: CPTemplateApplicationScene,
        didConnect interfaceController: CPInterfaceController
    ) {
        self.interfaceController = interfaceController

        let poiTemplate = createPOITemplate()
        interfaceController.setRootTemplate(poiTemplate, animated: true)
    }

    func createPOITemplate() -> CPPointOfInterestTemplate {
        let pois = loadNearbyLocations()

        let template = CPPointOfInterestTemplate(
            title: "Nearby",
            pointsOfInterest: pois,
            selectedIndex: NSNotFound
        )
        template.pointOfInterestDelegate = self

        return template
    }
}
```

### Creating Points of Interest

```swift
func createPOI(for location: Location) -> CPPointOfInterest {
    let mapItem = MKMapItem(
        placemark: MKPlacemark(coordinate: location.coordinate)
    )
    mapItem.name = location.name

    let poi = CPPointOfInterest(
        location: mapItem,
        title: location.name,
        subtitle: location.address,
        summary: location.description,
        detailTitle: location.name,
        detailSubtitle: location.formattedDistance,
        detailSummary: location.details,
        pinImage: UIImage(systemName: location.categoryIcon)
    )

    // Add action buttons
    poi.primaryButton = CPTextButton(
        title: "Directions",
        textStyle: .normal
    ) { button in
        self.getDirections(to: location)
    }

    poi.secondaryButton = CPTextButton(
        title: "Call",
        textStyle: .normal
    ) { button in
        self.call(location.phoneNumber)
    }

    return poi
}
```

### POI Template Delegate

```swift
extension CarPlaySceneDelegate: CPPointOfInterestTemplateDelegate {
    func pointOfInterestTemplate(
        _ pointOfInterestTemplate: CPPointOfInterestTemplate,
        didChangeMapRegion region: MKCoordinateRegion
    ) {
        // User moved the map - load new POIs for this region
        loadPOIs(in: region) { pois in
            pointOfInterestTemplate.setPointsOfInterest(pois, selectedIndex: NSNotFound)
        }
    }

    func pointOfInterestTemplate(
        _ pointOfInterestTemplate: CPPointOfInterestTemplate,
        didSelectPointOfInterest pointOfInterest: CPPointOfInterest
    ) {
        // User selected a POI - show details
    }
}
```

## Category-Specific Features

### Parking Apps

```swift
func createParkingPOI(for lot: ParkingLot) -> CPPointOfInterest {
    let poi = CPPointOfInterest(
        location: lot.mapItem,
        title: lot.name,
        subtitle: "\(lot.availableSpaces) spots available",
        summary: lot.pricePerHour,
        detailTitle: lot.name,
        detailSubtitle: "Available: \(lot.availableSpaces)/\(lot.totalSpaces)",
        detailSummary: """
        Rate: \(lot.pricePerHour)
        Hours: \(lot.hours)
        \(lot.amenities.joined(separator: ", "))
        """,
        pinImage: UIImage(systemName: "car.fill")
    )

    poi.primaryButton = CPTextButton(title: "Reserve", textStyle: .normal) { _ in
        self.reserveSpot(at: lot)
    }

    return poi
}
```

### EV Charging Apps

See [EV Charging](ev_charging.md) for detailed EV charging implementation.

### Food Ordering Apps

```swift
func createRestaurantPOI(for restaurant: Restaurant) -> CPPointOfInterest {
    let poi = CPPointOfInterest(
        location: restaurant.mapItem,
        title: restaurant.name,
        subtitle: "\(restaurant.rating) stars • \(restaurant.cuisine)",
        summary: restaurant.waitTime,
        detailTitle: restaurant.name,
        detailSubtitle: "\(restaurant.distance) away • \(restaurant.priceRange)",
        detailSummary: """
        Wait time: \(restaurant.waitTime)
        Open until: \(restaurant.closingTime)
        """,
        pinImage: UIImage(systemName: "fork.knife")
    )

    poi.primaryButton = CPTextButton(title: "Order", textStyle: .normal) { _ in
        self.startOrder(at: restaurant)
    }

    poi.secondaryButton = CPTextButton(title: "Menu", textStyle: .normal) { _ in
        self.showMenu(for: restaurant)
    }

    return poi
}
```

### Fueling Apps

```swift
func createGasStationPOI(for station: GasStation) -> CPPointOfInterest {
    let poi = CPPointOfInterest(
        location: station.mapItem,
        title: station.brand,
        subtitle: "$\(station.regularPrice)/gal",
        summary: station.address,
        detailTitle: station.brand,
        detailSubtitle: station.address,
        detailSummary: """
        Regular: $\(station.regularPrice)
        Premium: $\(station.premiumPrice)
        Diesel: $\(station.dieselPrice ?? "N/A")
        """,
        pinImage: UIImage(systemName: "fuelpump.fill")
    )

    poi.primaryButton = CPTextButton(title: "Pay", textStyle: .normal) { _ in
        self.startPayment(at: station)
    }

    return poi
}
```

## Location Updates

### Monitoring User Location

```swift
class LocationManager: NSObject, CLLocationManagerDelegate {
    let manager = CLLocationManager()
    var onLocationUpdate: ((CLLocation) -> Void)?

    func startUpdating() {
        manager.delegate = self
        manager.desiredAccuracy = kCLLocationAccuracyBest
        manager.requestWhenInUseAuthorization()
        manager.startUpdatingLocation()
    }

    func locationManager(
        _ manager: CLLocationManager,
        didUpdateLocations locations: [CLLocation]
    ) {
        guard let location = locations.last else { return }
        onLocationUpdate?(location)
    }
}
```

### Updating POIs Based on Location

```swift
func updatePOIsForCurrentLocation() {
    locationManager.onLocationUpdate = { [weak self] location in
        self?.loadNearbyPOIs(around: location.coordinate) { pois in
            self?.poiTemplate?.setPointsOfInterest(pois, selectedIndex: NSNotFound)
        }
    }
}
```

## Map Integration

### Showing POI on Map

```swift
func getDirections(to poi: CPPointOfInterest) {
    guard let location = poi.location else { return }

    // Open in Maps
    location.openInMaps(launchOptions: [
        MKLaunchOptionsDirectionsModeKey: MKLaunchOptionsDirectionsModeDriving
    ])
}
```

### Custom Map Annotations

```swift
func configurePinImage(for category: POICategory) -> UIImage? {
    switch category {
    case .parking:
        return UIImage(systemName: "p.circle.fill")
    case .charging:
        return UIImage(systemName: "bolt.car.fill")
    case .food:
        return UIImage(systemName: "fork.knife.circle.fill")
    case .fuel:
        return UIImage(systemName: "fuelpump.circle.fill")
    default:
        return UIImage(systemName: "mappin.circle.fill")
    }
}
```

## Search

### POI Search

```swift
func searchPOIs(query: String) {
    let request = MKLocalSearch.Request()
    request.naturalLanguageQuery = query
    request.region = currentMapRegion

    let search = MKLocalSearch(request: request)
    search.start { response, error in
        guard let items = response?.mapItems else { return }

        let pois = items.map { self.createPOI(from: $0) }
        self.poiTemplate?.setPointsOfInterest(pois, selectedIndex: NSNotFound)
    }
}
```

## Best Practices

1. **Show relevant information** - Display what drivers need at a glance
2. **Update availability** - Refresh real-time data (parking spots, wait times)
3. **Provide quick actions** - One-tap directions, calls, or orders
4. **Handle offline** - Cache recent POIs for offline access
5. **Respect location privacy** - Only request necessary location access
6. **Optimize images** - Use appropriate pin image sizes
7. **Sort by relevance** - Consider distance, ratings, and availability
8. **Test map interactions** - Verify pan and zoom behavior
