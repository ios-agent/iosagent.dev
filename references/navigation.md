# CarPlay Navigation Apps

Navigation apps provide turn-by-turn directions on the CarPlay display. They use `CPMapTemplate` and `CPNavigationSession` for the core navigation experience.

## Requirements

- Entitlement: `com.apple.developer.carplay-maps`
- iOS 14.0+

## Map Template Setup

### Basic Configuration

```swift
import CarPlay
import MapKit

class CarPlaySceneDelegate: UIResponder, CPTemplateApplicationSceneDelegate {
    var interfaceController: CPInterfaceController?
    var mapTemplate: CPMapTemplate?
    var mapView: MKMapView?

    func templateApplicationScene(
        _ templateApplicationScene: CPTemplateApplicationScene,
        didConnect interfaceController: CPInterfaceController
    ) {
        self.interfaceController = interfaceController

        // Create map template
        let mapTemplate = CPMapTemplate()
        mapTemplate.mapDelegate = self
        self.mapTemplate = mapTemplate

        // Create map view for CarPlay window
        let mapView = MKMapView()
        mapView.showsUserLocation = true
        self.mapView = mapView

        templateApplicationScene.carWindow.rootViewController = MapViewController(mapView: mapView)

        interfaceController.setRootTemplate(mapTemplate, animated: true)
    }
}
```

### Map Template Delegate

```swift
extension CarPlaySceneDelegate: CPMapTemplateDelegate {
    func mapTemplate(
        _ mapTemplate: CPMapTemplate,
        panBeganWith direction: CPMapTemplate.PanDirection
    ) {
        // User started panning
    }

    func mapTemplate(
        _ mapTemplate: CPMapTemplate,
        panEndedWith direction: CPMapTemplate.PanDirection
    ) {
        // User stopped panning
    }

    func mapTemplate(
        _ mapTemplate: CPMapTemplate,
        panWith direction: CPMapTemplate.PanDirection
    ) {
        // Handle continuous pan
        let scrollAmount: CGFloat = 50

        var offset = CGPoint.zero
        switch direction {
        case .up: offset.y = -scrollAmount
        case .down: offset.y = scrollAmount
        case .left: offset.x = -scrollAmount
        case .right: offset.x = scrollAmount
        @unknown default: break
        }

        // Apply offset to map
    }

    func mapTemplate(
        _ mapTemplate: CPMapTemplate,
        selectedPreviewFor trip: CPTrip,
        using routeChoice: CPRouteChoice
    ) {
        // User selected a route preview
    }

    func mapTemplate(
        _ mapTemplate: CPMapTemplate,
        startedTrip trip: CPTrip,
        using routeChoice: CPRouteChoice
    ) {
        // Start navigation
        startNavigation(for: trip, with: routeChoice)
    }

    func mapTemplateDidCancelNavigation(_ mapTemplate: CPMapTemplate) {
        // User cancelled navigation
        endNavigation()
    }
}
```

## Navigation Session

### Starting Navigation

```swift
var navigationSession: CPNavigationSession?

func startNavigation(for trip: CPTrip, with routeChoice: CPRouteChoice) {
    // Start the navigation session
    navigationSession = mapTemplate?.startNavigationSession(for: trip)
    navigationSession?.pauseTrip(for: .loading, description: "Calculating route...")

    // Begin providing turn-by-turn instructions
    calculateRoute(for: trip) { maneuvers in
        self.navigationSession?.resumeTrip()
        self.updateManeuvers(maneuvers)
    }
}
```

### Creating Trips

```swift
func createTrip(to destination: CLLocationCoordinate2D) -> CPTrip {
    // Create origin (current location)
    let originItem = MKMapItem.forCurrentLocation()

    // Create destination
    let destinationPlacemark = MKPlacemark(coordinate: destination)
    let destinationItem = MKMapItem(placemark: destinationPlacemark)
    destinationItem.name = "Destination"

    // Create route choices
    let fastestRoute = CPRouteChoice(
        summaryVariants: ["Fastest Route"],
        additionalInformationVariants: ["Via Highway"],
        selectionSummaryVariants: ["25 min"]
    )

    let shortestRoute = CPRouteChoice(
        summaryVariants: ["Shortest Route"],
        additionalInformationVariants: ["Via Local Roads"],
        selectionSummaryVariants: ["30 min"]
    )

    // Create trip
    let trip = CPTrip(
        origin: originItem,
        destination: destinationItem,
        routeChoices: [fastestRoute, shortestRoute]
    )

    return trip
}
```

### Preview and Start Trip

```swift
func showTripPreview(trip: CPTrip) {
    let textConfig = CPTripPreviewTextConfiguration(
        startButtonTitle: "Go",
        additionalRoutesButtonTitle: "Routes",
        overviewButtonTitle: "Overview"
    )

    mapTemplate?.showTripPreviews([trip], textConfiguration: textConfig)
}
```

## Maneuvers

### Creating Maneuvers

```swift
func createManeuver(
    instruction: String,
    distance: CLLocationDistance,
    type: CPManeuver.ManeuverType
) -> CPManeuver {
    let maneuver = CPManeuver()
    maneuver.instructionVariants = [instruction]
    maneuver.initialTravelEstimates = CPTravelEstimates(
        distanceRemaining: Measurement(value: distance, unit: .meters),
        timeRemaining: distance / 15 // Rough estimate
    )

    // Set junction image if available
    if let symbolImage = UIImage(systemName: symbolForManeuverType(type)) {
        maneuver.symbolImage = symbolImage
    }

    return maneuver
}

func symbolForManeuverType(_ type: CPManeuver.ManeuverType) -> String {
    switch type {
    case .turnRight: return "arrow.turn.up.right"
    case .turnLeft: return "arrow.turn.up.left"
    case .straightAhead: return "arrow.up"
    case .uTurn: return "arrow.uturn.down"
    case .keepLeft: return "arrow.up.left"
    case .keepRight: return "arrow.up.right"
    default: return "arrow.up"
    }
}
```

### Updating Maneuvers

```swift
func updateManeuvers(_ maneuvers: [CPManeuver]) {
    guard let session = navigationSession else { return }

    // Update upcoming maneuvers (max 2)
    session.upcomingManeuvers = Array(maneuvers.prefix(2))
}

func updateTravelEstimates(
    distanceRemaining: CLLocationDistance,
    timeRemaining: TimeInterval
) {
    guard let session = navigationSession,
          let currentManeuver = session.upcomingManeuvers.first else { return }

    let estimates = CPTravelEstimates(
        distanceRemaining: Measurement(value: distanceRemaining, unit: .meters),
        timeRemaining: timeRemaining
    )

    session.updateEstimates(estimates, for: currentManeuver)
}
```

## Map Buttons

### Adding Navigation Buttons

```swift
func setupMapButtons() {
    let panButton = CPMapButton { button in
        self.mapTemplate?.showPanningInterface(animated: true)
    }
    panButton.image = UIImage(systemName: "arrow.up.and.down.and.arrow.left.and.right")

    let zoomInButton = CPMapButton { button in
        self.zoomIn()
    }
    zoomInButton.image = UIImage(systemName: "plus.magnifyingglass")

    let zoomOutButton = CPMapButton { button in
        self.zoomOut()
    }
    zoomOutButton.image = UIImage(systemName: "minus.magnifyingglass")

    let recenterButton = CPMapButton { button in
        self.recenterMap()
    }
    recenterButton.image = UIImage(systemName: "location.fill")

    mapTemplate?.mapButtons = [panButton, zoomInButton, zoomOutButton, recenterButton]
}
```

## Navigation Bar

### Customizing Navigation Bar

```swift
func setupNavigationBar() {
    let searchButton = CPBarButton(title: "Search") { button in
        self.showSearch()
    }

    let favoritesButton = CPBarButton(image: UIImage(systemName: "star.fill")) { button in
        self.showFavorites()
    }

    mapTemplate?.leadingNavigationBarButtons = [searchButton]
    mapTemplate?.trailingNavigationBarButtons = [favoritesButton]
}
```

## Speed Limit and Compass

### Display Speed Limit

```swift
// Show speed limit on map template
let speedLimit = CPSpeedLimit(
    speedLimit: Measurement(value: 65, unit: .milesPerHour)
)
mapTemplate?.currentSpeedLimit = speedLimit
```

### Compass and Navigation State

```swift
// Configure navigation state
mapTemplate?.hidesButtonsWithNavigationBar = false
mapTemplate?.automaticallyHidesNavigationBar = true
```

## Ending Navigation

```swift
func endNavigation() {
    navigationSession?.finishTrip()
    navigationSession = nil

    mapTemplate?.hideTripPreviews()
}
```

## Best Practices

1. **Always show current maneuver** - Keep drivers informed of next action
2. **Update estimates frequently** - Recalculate as traffic conditions change
3. **Support lane guidance** - Show lane information when available
4. **Handle re-routing** - Automatically recalculate when user goes off-route
5. **Provide audio cues** - Use AVSpeechSynthesizer for voice guidance
6. **Test thoroughly** - Use CarPlay Simulator with various scenarios
