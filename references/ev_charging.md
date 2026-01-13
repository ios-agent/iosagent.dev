# CarPlay EV Charging Apps

EV Charging apps help electric vehicle owners find, navigate to, and use charging stations. They integrate with CarPlay's POI system and can provide real-time availability and payment functionality.

## Requirements

- Entitlement: `com.apple.developer.carplay-charging`
- iOS 14.0+

## Charging Station Template

### Basic Setup

```swift
import CarPlay
import CoreLocation

class CarPlaySceneDelegate: UIResponder, CPTemplateApplicationSceneDelegate {
    var interfaceController: CPInterfaceController?
    var chargingTemplate: CPPointOfInterestTemplate?

    func templateApplicationScene(
        _ templateApplicationScene: CPTemplateApplicationScene,
        didConnect interfaceController: CPInterfaceController
    ) {
        self.interfaceController = interfaceController

        let template = createChargingTemplate()
        self.chargingTemplate = template
        interfaceController.setRootTemplate(template, animated: true)
    }

    func createChargingTemplate() -> CPPointOfInterestTemplate {
        let stations = loadNearbyChargingStations()
        let pois = stations.map { createChargingPOI(for: $0) }

        let template = CPPointOfInterestTemplate(
            title: "Charging",
            pointsOfInterest: pois,
            selectedIndex: NSNotFound
        )
        template.pointOfInterestDelegate = self

        return template
    }
}
```

### Creating Charging Station POIs

```swift
struct ChargingStation {
    let id: String
    let name: String
    let network: String
    let address: String
    let coordinate: CLLocationCoordinate2D
    let connectors: [Connector]
    let availablePorts: Int
    let totalPorts: Int
    let pricing: String
    let amenities: [String]
    let distance: Double
}

struct Connector {
    let type: ConnectorType
    let power: Double // kW
    let available: Bool
    let price: String
}

enum ConnectorType: String {
    case ccs = "CCS"
    case chademo = "CHAdeMO"
    case teslasc = "Tesla Supercharger"
    case j1772 = "J1772"
    case nacs = "NACS"
}

func createChargingPOI(for station: ChargingStation) -> CPPointOfInterest {
    let mapItem = MKMapItem(
        placemark: MKPlacemark(coordinate: station.coordinate)
    )
    mapItem.name = station.name

    let availabilityText = "\(station.availablePorts)/\(station.totalPorts) available"
    let connectorTypes = station.connectors
        .map { $0.type.rawValue }
        .joined(separator: ", ")

    let poi = CPPointOfInterest(
        location: mapItem,
        title: station.name,
        subtitle: availabilityText,
        summary: station.network,
        detailTitle: station.name,
        detailSubtitle: station.address,
        detailSummary: """
        \(availabilityText)
        Connectors: \(connectorTypes)
        \(station.pricing)
        """,
        pinImage: createPinImage(for: station)
    )

    // Primary action - Start charging
    poi.primaryButton = CPTextButton(
        title: "Start Charging",
        textStyle: .normal
    ) { [weak self] button in
        self?.startChargingFlow(at: station)
    }

    // Secondary action - Directions
    poi.secondaryButton = CPTextButton(
        title: "Directions",
        textStyle: .normal
    ) { [weak self] button in
        self?.navigateTo(station)
    }

    return poi
}

func createPinImage(for station: ChargingStation) -> UIImage? {
    let config = UIImage.SymbolConfiguration(pointSize: 24)

    if station.availablePorts > 0 {
        return UIImage(systemName: "bolt.car.fill", withConfiguration: config)?
            .withTintColor(.systemGreen, renderingMode: .alwaysOriginal)
    } else {
        return UIImage(systemName: "bolt.car", withConfiguration: config)?
            .withTintColor(.systemGray, renderingMode: .alwaysOriginal)
    }
}
```

## Station Details

### Detailed Station View

```swift
func showStationDetails(_ station: ChargingStation) {
    var items = [CPInformationItem]()

    // Address
    items.append(CPInformationItem(title: "Address", detail: station.address))

    // Network
    items.append(CPInformationItem(title: "Network", detail: station.network))

    // Availability
    items.append(CPInformationItem(
        title: "Availability",
        detail: "\(station.availablePorts) of \(station.totalPorts) ports available"
    ))

    // Connectors
    for connector in station.connectors {
        let status = connector.available ? "Available" : "In Use"
        items.append(CPInformationItem(
            title: "\(connector.type.rawValue) (\(Int(connector.power))kW)",
            detail: "\(status) - \(connector.price)"
        ))
    }

    // Amenities
    if !station.amenities.isEmpty {
        items.append(CPInformationItem(
            title: "Amenities",
            detail: station.amenities.joined(separator: ", ")
        ))
    }

    let actions = [
        CPTextButton(title: "Start Charging", textStyle: .confirm) { _ in
            self.startChargingFlow(at: station)
        },
        CPTextButton(title: "Directions", textStyle: .normal) { _ in
            self.navigateTo(station)
        }
    ]

    let template = CPInformationTemplate(
        title: station.name,
        layout: .leading,
        items: items,
        actions: actions
    )

    interfaceController?.pushTemplate(template, animated: true)
}
```

## Charging Flow

### Start Charging Session

```swift
func startChargingFlow(at station: ChargingStation) {
    // Show connector selection
    let connectorItems = station.connectors.filter { $0.available }.map { connector in
        CPListItem(
            text: connector.type.rawValue,
            detailText: "\(Int(connector.power))kW - \(connector.price)"
        )
    }

    for (index, item) in connectorItems.enumerated() {
        item.handler = { [weak self] _, completion in
            let connector = station.connectors.filter { $0.available }[index]
            self?.selectConnector(connector, at: station)
            completion()
        }
    }

    let section = CPListSection(items: connectorItems, header: "Select Connector")
    let template = CPListTemplate(title: "Choose Connector", sections: [section])

    interfaceController?.pushTemplate(template, animated: true)
}

func selectConnector(_ connector: Connector, at station: ChargingStation) {
    // Show confirmation
    let alert = CPAlertTemplate(
        titleVariants: ["Start charging?"],
        actions: [
            CPAlertAction(title: "Start", style: .default) { [weak self] _ in
                self?.beginCharging(connector: connector, station: station)
            },
            CPAlertAction(title: "Cancel", style: .cancel) { [weak self] _ in
                self?.interfaceController?.dismissTemplate(animated: true)
            }
        ]
    )

    interfaceController?.presentTemplate(alert, animated: true)
}
```

### Active Charging Session

```swift
func beginCharging(connector: Connector, station: ChargingStation) {
    // Dismiss selection UI
    interfaceController?.popToRootTemplate(animated: true)

    // Start session with backend
    ChargingService.shared.startSession(
        stationId: station.id,
        connectorType: connector.type
    ) { [weak self] session in
        self?.showActiveChargingSession(session)
    }
}

func showActiveChargingSession(_ session: ChargingSession) {
    let items = [
        CPInformationItem(title: "Status", detail: "Charging"),
        CPInformationItem(title: "Energy Delivered", detail: "\(session.energyDelivered) kWh"),
        CPInformationItem(title: "Current Power", detail: "\(session.currentPower) kW"),
        CPInformationItem(title: "Time Elapsed", detail: session.formattedDuration),
        CPInformationItem(title: "Estimated Cost", detail: session.estimatedCost)
    ]

    let actions = [
        CPTextButton(title: "Stop Charging", textStyle: .cancel) { [weak self] _ in
            self?.stopCharging(session)
        }
    ]

    let template = CPInformationTemplate(
        title: "Charging Session",
        layout: .leading,
        items: items,
        actions: actions
    )

    interfaceController?.setRootTemplate(template, animated: true)

    // Start polling for updates
    startSessionUpdates(session)
}

func startSessionUpdates(_ session: ChargingSession) {
    Timer.scheduledTimer(withTimeInterval: 10, repeats: true) { [weak self] timer in
        ChargingService.shared.getSessionStatus(session.id) { updatedSession in
            if updatedSession.status == .completed {
                timer.invalidate()
                self?.showChargingComplete(updatedSession)
            } else {
                self?.updateChargingUI(updatedSession)
            }
        }
    }
}
```

### Charging Complete

```swift
func showChargingComplete(_ session: ChargingSession) {
    let items = [
        CPInformationItem(title: "Status", detail: "Complete"),
        CPInformationItem(title: "Total Energy", detail: "\(session.energyDelivered) kWh"),
        CPInformationItem(title: "Duration", detail: session.formattedDuration),
        CPInformationItem(title: "Total Cost", detail: session.totalCost)
    ]

    let actions = [
        CPTextButton(title: "Done", textStyle: .confirm) { [weak self] _ in
            self?.returnToStationList()
        }
    ]

    let template = CPInformationTemplate(
        title: "Charging Complete",
        layout: .leading,
        items: items,
        actions: actions
    )

    interfaceController?.setRootTemplate(template, animated: true)
}
```

## Filtering and Search

### Filter by Connector Type

```swift
func createFilterTemplate() -> CPListTemplate {
    let filters: [ConnectorType] = [.ccs, .chademo, .nacs, .j1772]

    let items = filters.map { type in
        let item = CPListItem(text: type.rawValue, detailText: nil)
        item.handler = { [weak self] _, completion in
            self?.filterStations(by: type)
            completion()
        }
        return item
    }

    let section = CPListSection(items: items, header: "Connector Type")
    return CPListTemplate(title: "Filter", sections: [section])
}

func filterStations(by connectorType: ConnectorType) {
    let filtered = allStations.filter { station in
        station.connectors.contains { $0.type == connectorType }
    }

    let pois = filtered.map { createChargingPOI(for: $0) }
    chargingTemplate?.setPointsOfInterest(pois, selectedIndex: NSNotFound)

    interfaceController?.popTemplate(animated: true)
}
```

## Real-Time Updates

### WebSocket for Live Availability

```swift
class StationAvailabilityService {
    func subscribeToUpdates(completion: @escaping ([ChargingStation]) -> Void) {
        // Connect to real-time service
        // Update availability as chargers become available/occupied
    }
}
```

## Best Practices

1. **Show real-time availability** - Update station status frequently
2. **Indicate connector compatibility** - Show which connectors work with user's vehicle
3. **Display pricing clearly** - Show per-kWh and time-based rates
4. **Provide charging estimates** - Estimate charge time based on vehicle
5. **Support session monitoring** - Show progress during charging
6. **Handle payment in-app** - Integrate payment for seamless experience
7. **Show amenities** - Display nearby services while charging
8. **Notify when complete** - Alert user when charging is done
