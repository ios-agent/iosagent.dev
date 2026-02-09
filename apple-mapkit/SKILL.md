---
name: apple-mapkit
description: "Help developers integrate Apple MapKit into iOS/macOS apps. Use this skill when users ask to add a map to their app, display maps, show user location on a map, add markers/pins/annotations, implement map clustering, get directions/routing between locations, search for places/points of interest, implement MapKit features, work with MKMapView, SwiftUI Map, MKAnnotation, MKOverlay, MKDirections, MKLocalSearch, or any MapKit-related development task."
---

# Apple MapKit Integration

Help developers integrate MapKit into iOS/macOS/visionOS apps using SwiftUI or UIKit.

## Quick Reference

- **Full API documentation**: See `references/MapKit.md` for complete MapKit API details
- **Default to SwiftUI** for new projects (iOS 17+), offer UIKit for older targets or specific needs

## Common Workflows

### 1. Display a Basic Map

**SwiftUI (iOS 17+)**
```swift
import MapKit
import SwiftUI

struct ContentView: View {
    var body: some View {
        Map()
    }
}
```

**SwiftUI with initial position**
```swift
struct ContentView: View {
    @State private var position: MapCameraPosition = .region(
        MKCoordinateRegion(
            center: CLLocationCoordinate2D(latitude: 37.7749, longitude: -122.4194),
            span: MKCoordinateSpan(latitudeDelta: 0.1, longitudeDelta: 0.1)
        )
    )
    
    var body: some View {
        Map(position: $position)
    }
}
```

**UIKit**
```swift
import MapKit
import UIKit

class MapViewController: UIViewController {
    private let mapView = MKMapView()
    
    override func viewDidLoad() {
        super.viewDidLoad()
        mapView.frame = view.bounds
        mapView.autoresizingMask = [.flexibleWidth, .flexibleHeight]
        view.addSubview(mapView)
        
        let region = MKCoordinateRegion(
            center: CLLocationCoordinate2D(latitude: 37.7749, longitude: -122.4194),
            span: MKCoordinateSpan(latitudeDelta: 0.1, longitudeDelta: 0.1)
        )
        mapView.setRegion(region, animated: false)
    }
}
```

### 2. Show User Location

**Required**: Add `NSLocationWhenInUseUsageDescription` to Info.plist

**SwiftUI (iOS 17+)**
```swift
import CoreLocation
import MapKit
import SwiftUI

struct ContentView: View {
    @State private var position: MapCameraPosition = .userLocation(fallback: .automatic)
    
    var body: some View {
        Map(position: $position) {
            UserAnnotation()
        }
        .mapControls {
            MapUserLocationButton()
            MapCompass()
        }
    }
}
```

**UIKit**
```swift
class MapViewController: UIViewController, CLLocationManagerDelegate {
    private let mapView = MKMapView()
    private let locationManager = CLLocationManager()
    
    override func viewDidLoad() {
        super.viewDidLoad()
        setupMapView()
        locationManager.delegate = self
        locationManager.requestWhenInUseAuthorization()
    }
    
    func locationManagerDidChangeAuthorization(_ manager: CLLocationManager) {
        if manager.authorizationStatus == .authorizedWhenInUse {
            mapView.showsUserLocation = true
            mapView.userTrackingMode = .follow
        }
    }
}
```

### 3. Add Annotations/Markers

**SwiftUI (iOS 17+)**
```swift
struct Place: Identifiable {
    let id = UUID()
    let name: String
    let coordinate: CLLocationCoordinate2D
}

struct ContentView: View {
    let places = [
        Place(name: "San Francisco", coordinate: CLLocationCoordinate2D(latitude: 37.7749, longitude: -122.4194)),
        Place(name: "Oakland", coordinate: CLLocationCoordinate2D(latitude: 37.8044, longitude: -122.2712))
    ]
    
    var body: some View {
        Map {
            ForEach(places) { place in
                Marker(place.name, coordinate: place.coordinate)
            }
        }
    }
}
```

**Custom annotation content**
```swift
Map {
    ForEach(places) { place in
        Annotation(place.name, coordinate: place.coordinate) {
            VStack {
                Image(systemName: "mappin.circle.fill")
                    .font(.title)
                    .foregroundStyle(.red)
                Text(place.name)
                    .font(.caption)
            }
        }
    }
}
```

**UIKit**
```swift
class PlaceAnnotation: NSObject, MKAnnotation {
    let title: String?
    let coordinate: CLLocationCoordinate2D
    
    init(title: String, coordinate: CLLocationCoordinate2D) {
        self.title = title
        self.coordinate = coordinate
    }
}

// In view controller:
let annotation = PlaceAnnotation(
    title: "San Francisco",
    coordinate: CLLocationCoordinate2D(latitude: 37.7749, longitude: -122.4194)
)
mapView.addAnnotation(annotation)
```

### 4. Marker/Annotation Clustering

**SwiftUI (iOS 17+)** — Use `MapContentBuilder` with `.annotationTitles(.hidden)` for clustering behavior, or use `MKClusterAnnotation` in UIKit.

**UIKit with clustering**
```swift
class ClusterableAnnotation: NSObject, MKAnnotation {
    let coordinate: CLLocationCoordinate2D
    let title: String?
    
    init(coordinate: CLLocationCoordinate2D, title: String?) {
        self.coordinate = coordinate
        self.title = title
    }
}

class MapViewController: UIViewController, MKMapViewDelegate {
    private let mapView = MKMapView()
    
    override func viewDidLoad() {
        super.viewDidLoad()
        mapView.delegate = self
        mapView.register(MKMarkerAnnotationView.self, forAnnotationViewWithReuseIdentifier: MKMapViewDefaultAnnotationViewReuseIdentifier)
        mapView.register(MKMarkerAnnotationView.self, forAnnotationViewWithReuseIdentifier: MKMapViewDefaultClusterAnnotationViewReuseIdentifier)
    }
    
    func mapView(_ mapView: MKMapView, viewFor annotation: MKAnnotation) -> MKAnnotationView? {
        guard !(annotation is MKUserLocation) else { return nil }
        
        if let cluster = annotation as? MKClusterAnnotation {
            let view = mapView.dequeueReusableAnnotationView(withIdentifier: MKMapViewDefaultClusterAnnotationViewReuseIdentifier, for: annotation) as! MKMarkerAnnotationView
            view.markerTintColor = .blue
            view.glyphText = "\(cluster.memberAnnotations.count)"
            return view
        }
        
        let view = mapView.dequeueReusableAnnotationView(withIdentifier: MKMapViewDefaultAnnotationViewReuseIdentifier, for: annotation) as! MKMarkerAnnotationView
        view.clusteringIdentifier = "places" // Enable clustering
        view.markerTintColor = .red
        return view
    }
}
```

### 5. Directions and Routing

**SwiftUI (iOS 17+)**
```swift
struct DirectionsView: View {
    @State private var route: MKRoute?
    @State private var position: MapCameraPosition = .automatic
    
    let start = CLLocationCoordinate2D(latitude: 37.7749, longitude: -122.4194)
    let end = CLLocationCoordinate2D(latitude: 37.8044, longitude: -122.2712)
    
    var body: some View {
        Map(position: $position) {
            Marker("Start", coordinate: start)
            Marker("End", coordinate: end)
            if let route {
                MapPolyline(route.polyline)
                    .stroke(.blue, lineWidth: 5)
            }
        }
        .task {
            await calculateRoute()
        }
    }
    
    func calculateRoute() async {
        let request = MKDirections.Request()
        request.source = MKMapItem(placemark: MKPlacemark(coordinate: start))
        request.destination = MKMapItem(placemark: MKPlacemark(coordinate: end))
        request.transportType = .automobile
        
        let directions = MKDirections(request: request)
        if let response = try? await directions.calculate() {
            route = response.routes.first
        }
    }
}
```

**UIKit**
```swift
func calculateAndDisplayRoute(from source: CLLocationCoordinate2D, to destination: CLLocationCoordinate2D) {
    let request = MKDirections.Request()
    request.source = MKMapItem(placemark: MKPlacemark(coordinate: source))
    request.destination = MKMapItem(placemark: MKPlacemark(coordinate: destination))
    request.transportType = .automobile
    
    let directions = MKDirections(request: request)
    directions.calculate { [weak self] response, error in
        guard let route = response?.routes.first else { return }
        self?.mapView.addOverlay(route.polyline)
        self?.mapView.setVisibleMapRect(route.polyline.boundingMapRect, edgePadding: UIEdgeInsets(top: 50, left: 50, bottom: 50, right: 50), animated: true)
    }
}

// MKMapViewDelegate
func mapView(_ mapView: MKMapView, rendererFor overlay: MKOverlay) -> MKOverlayRenderer {
    if let polyline = overlay as? MKPolyline {
        let renderer = MKPolylineRenderer(polyline: polyline)
        renderer.strokeColor = .systemBlue
        renderer.lineWidth = 5
        return renderer
    }
    return MKOverlayRenderer(overlay: overlay)
}
```

### 6. Local Search (Find Places)

```swift
func searchForPlaces(query: String, region: MKCoordinateRegion) async -> [MKMapItem] {
    let request = MKLocalSearch.Request()
    request.naturalLanguageQuery = query
    request.region = region
    
    let search = MKLocalSearch(request: request)
    if let response = try? await search.start() {
        return response.mapItems
    }
    return []
}

// Usage
let results = await searchForPlaces(query: "coffee", region: mapView.region)
for item in results {
    print("\(item.name ?? "") - \(item.placemark.coordinate)")
}
```

**Search completions (autocomplete)**
```swift
class SearchCompleter: NSObject, ObservableObject, MKLocalSearchCompleterDelegate {
    @Published var results: [MKLocalSearchCompletion] = []
    private let completer = MKLocalSearchCompleter()
    
    override init() {
        super.init()
        completer.delegate = self
        completer.resultTypes = [.address, .pointOfInterest]
    }
    
    func search(query: String) {
        completer.queryFragment = query
    }
    
    func completerDidUpdateResults(_ completer: MKLocalSearchCompleter) {
        results = completer.results
    }
}
```

### 7. Map Overlays (Polylines, Polygons, Circles)

**SwiftUI (iOS 17+)**
```swift
Map {
    // Polyline
    MapPolyline(coordinates: [
        CLLocationCoordinate2D(latitude: 37.7749, longitude: -122.4194),
        CLLocationCoordinate2D(latitude: 37.8044, longitude: -122.2712)
    ])
    .stroke(.blue, lineWidth: 3)
    
    // Circle
    MapCircle(center: CLLocationCoordinate2D(latitude: 37.7749, longitude: -122.4194), radius: 1000)
        .foregroundStyle(.blue.opacity(0.3))
        .stroke(.blue, lineWidth: 2)
    
    // Polygon
    MapPolygon(coordinates: [
        CLLocationCoordinate2D(latitude: 37.77, longitude: -122.42),
        CLLocationCoordinate2D(latitude: 37.78, longitude: -122.40),
        CLLocationCoordinate2D(latitude: 37.76, longitude: -122.40)
    ])
    .foregroundStyle(.green.opacity(0.3))
    .stroke(.green, lineWidth: 2)
}
```

### 8. Map Configuration

**SwiftUI**
```swift
Map {
    // content
}
.mapStyle(.standard) // .imagery, .hybrid, .standard(elevation: .realistic)
.mapControls {
    MapUserLocationButton()
    MapCompass()
    MapScaleView()
    MapPitchToggle()
}
```

**UIKit**
```swift
mapView.mapType = .standard // .satellite, .hybrid, .satelliteFlyover, .hybridFlyover
mapView.showsCompass = true
mapView.showsScale = true
mapView.isZoomEnabled = true
mapView.isScrollEnabled = true
mapView.isPitchEnabled = true
mapView.isRotateEnabled = true
```

## Key Considerations

1. **Privacy**: Always add location usage descriptions to Info.plist
2. **Maps capability**: Enable in Xcode under Signing & Capabilities for directions
3. **iOS version**: SwiftUI Map API significantly improved in iOS 17; use UIKit for older targets
4. **Clustering**: Set `clusteringIdentifier` on annotation views (UIKit) to enable automatic clustering
5. **Performance**: For many annotations (1000+), consider clustering or custom tile overlays

## When to Consult Full Reference

Search `references/MapKit.md` for:
- Complete API signatures and parameters
- LookAround implementation details
- MKMapItem and place details
- GeoJSON decoding
- Indoor mapping (IMDF)
- Point of interest categories and filtering
- Snapshot generation
- All MKMapViewDelegate methods
