<!--
Downloaded via https://llm.codes by @steipete on January 28, 2026 at 05:30 PM
Source URL: https://developer.apple.com/documentation/MapKit
Total pages processed: 497
URLs filtered: Yes
Content de-duplicated: Yes
Availability strings filtered: Yes
Code blocks only: No
-->

# https://developer.apple.com/documentation/MapKit

Framework

# MapKit

Display map or satellite imagery within your app, call out points of interest, and determine placemark information for map coordinates.

## Overview

Use MapKit to give your app a sense of place with maps and location information. You can use the MapKit framework to:

- Embed maps directly into your app’s windows and views.

- Add annotations and overlays to a map to call out points of interest.

- Add LookAround capabilities to enable users to explore locations at street level.

- Respond to user interactions with well known points of interest, geographical features, and boundaries.

- Provide text completion to make it easy for users to search for a destination or point of interest.

## Topics

### The MapKit APIs

MapKit for SwiftUI allows you to build map-centric views and apps across Apple platforms. You can design expressive and highly interactive Maps with minimal code by composing views, using ViewBuilders and view modifiers.

Adopting unified Maps URLs

Access Maps URLs and options for displaying Maps information across Apple platforms.

### Articles

MapKit classes, protocols, and entitlements that are no longer supported.

Preparing your app to be the default navigation app

Configure your navigation app so people can set it as the default on their devices.

### Structures

`struct AnyMapContent`

A type-erased map content.

## See Also

### Related Documentation

Location and Maps Programming Guide

MapKit JS

Embed interactive Apple Maps on your website, annotate points of interest, and perform georelated searches.

Apple Maps Server API

Reduce API calls and conserve device power by streamlining your app’s georelated searches.

---

# https://developer.apple.com/documentation/mapkit/mapkit-for-appkit-and-uikit

Collection

- MapKit
- MapKit for AppKit and UIKit

API Collection

# MapKit for AppKit and UIKit

## Topics

### Essentials

Enabling Maps capability in Xcode

Configure your routing app to support providing directions.

Identifying unique locations with Place IDs

Obtain information about a point of interest that persists over its lifetime.

`class MKMapView`

An embeddable map interface, similar to the one that the Maps app provides.

`class MKMapItem`

A point of interest on the map.

### Map coordinates

`struct MKCoordinateRegion`

A rectangular geographic region that centers around a specific latitude and longitude.

`struct MKCoordinateSpan`

The width and height of a map region.

`struct MKMapRect`

A rectangular area on a two-dimensional map projection.

`struct MKMapPoint`

A point on a two-dimensional map projection.

`struct MKMapSize`

Width and height information on a two-dimensional map projection.

`class MKDistanceFormatter`

A utility object that converts between a geographic distance and a string-based expression of that distance.

### Map customization

`class MKMapCamera`

A virtual camera for defining the appearance of the map.

`class MKCompassButton`

A specialized view that displays the compass heading for its associated map.

`class MKScaleView`

A specialized view that displays the scale information for its associated map.

`class MKZoomControl`

A specialized view that displays and controls the zoom level of the map view.

`class MKPitchControl`

A specialized view that displays and controls the pitch angle of the map view.

`class MKUserTrackingButton`

A specialized button that allows the user to toggle whether the map tracks to the heading the user is facing.

`class MKUserTrackingBarButtonItem`

A specialized bar button item that allows the user to toggle whether the map tracks to the heading the user is facing.

### Annotations and overlays

Create annotations to add indicators and additional details for specific locations on a map.

Create overlays to highlight geographic regions or paths.

### Directions

`class MKDirections`

A utility object that computes directions and travel-time information based on the route information you provide.

`class Request`

The start and end points of a route, along with the planned mode of transportation.

`class Response`

The route information that Apple servers return in response to your request for directions.

`class ETAResponse`

The travel-time information that Apple servers return.

`class MKRoute`

A single route between a requested start and end point.

`class Step`

One portion of an overall route.

### Geographical features

Displaying an Indoor Map

Use the Indoor Mapping Data Format (IMDF) to show an indoor map with custom overlays and points of interest.

`class MKGeoJSONDecoder`

An object that decodes GeoJSON objects into MapKit types.

`class MKGeoJSONFeature`

The decoded representation of a GeoJSON feature.

`protocol MKGeoJSONObject`

Objects that the GeoJSON decoder can return.

### Local search

Interacting with nearby points of interest

Provide automatic search completions for a partial search query, search the map for relevant locations nearby, and retrieve details for selected points of interest.

`enum MKLocalSearchRegionPriority`

A value that indicates the importance of the configured region.

`struct ResultType`

Options that indicate types of search results.

`class MKLocalSearch`

A utility object for initiating map-based searches and processing the results.

`struct Options`

A structure that contains options for filtering results in a search.

`class MKAddressFilter`

An object that filters which address options to include or exclude in search results.

Options that indicate types of search completions.

`class MKLocalSearchCompleter`

A utility object for generating a list of completion strings based on a partial search string that you provide.

`class MKLocalSearchCompletion`

A fully formed string that completes a partial string.

`class MKLocalPointsOfInterestRequest`

A structured request to use when searching for points of interest.

### Exploring at street level

`class MKLookAroundScene`

A utility class that encapsulates information the framework requires to retrieve and display a specific Look Around location’s imagery.

`class MKLookAroundSceneRequest`

A class you use to request a LookAround scene at the location you specify.

`class MKLookAroundViewController`

A class that manages the presentation and display of a LookAround view.

`class MKLookAroundSnapshotter`

A utility class that you use to create a static image from a LookAround scene.

### Place information

`protocol MKMapItemDetailViewControllerDelegate`

The methods that you use to receive events from an associated map view controller.

`class MKMapItemDetailViewController`

An object that displays detailed information about a map item.

`class MapItemDetailPresentationStyle`

The type of map item detail accessory presentation to use.

`class MKSelectionAccessory`

The type of accessory to display for a selected annotation.

`enum CalloutStyle`

The style to use for a map item detail callout presentation.

### Points of interest

`class MKMapFeatureAnnotation`

A class that describes an annotation element on the map’s display such as a point of interest, territorial boundary, or physical feature.

`struct MKMapFeatureOptions`

A structure you use to tell the map which kinds of features users can interact with.

`class MKMapItemRequest`

A utility class you use to request additional information about a map feature.

`class MKIconStyle`

A class you use to customize the annotation view icon of a point of interest (POI) on the map.

`class MKPointOfInterestFilter`

A filter that includes or excludes point of interest categories from a map view, local search, or local search completer.

`struct MKPointOfInterestCategory`

A point of interest category.

### Static map snapshots

`class MKMapSnapshotter`

A utility class for capturing a map and its content into an image.

`class Snapshot`

An image that a snapshotter object generates.

### Reference

The functions of the MapKit framework provide convenient ways to package map-related data structures.

### Errors

`let MKErrorDomain: String`

The error domain for MapKit.

`struct MKError`

Error constants for the MapKit framework.

`enum Code`

### Deprecated

Map protocols and view modifiers that are no longer supported.

## See Also

### The MapKit APIs

MapKit for SwiftUI allows you to build map-centric views and apps across Apple platforms. You can design expressive and highly interactive Maps with minimal code by composing views, using ViewBuilders and view modifiers.

Adopting unified Maps URLs

Access Maps URLs and options for displaying Maps information across Apple platforms.

---

# https://developer.apple.com/documentation/mapkit/mapkit-for-swiftui

Collection

- MapKit
- MapKit for SwiftUI

API Collection

# MapKit for SwiftUI

MapKit for SwiftUI allows you to build map-centric views and apps across Apple platforms. You can design expressive and highly interactive Maps with minimal code by composing views, using ViewBuilders and view modifiers.

## Overview

Like MapKit for AppKit and UIKit, MapKit for SwiftUI allows you to take advantage of map styles ranging from satellite imagery to rich, 3D perspective imagery to present vivid maps. Using `MapContentBuilder` you can configure your maps to show `Marker` and `Annotation` views, or — for more specialized content — you can design your own SwiftUI views to place on the map. To add even more interactivity, MapKit for SwiftUI supports overlays to highlight areas on the map, enabling you to animate paths and directions using `MapPolyline`, or make it easy for people to dig deeper into on the ground details with tappable points of interest. People who use your app can also explore at street level using `LookAroundPreview` and Look Around viewer.

## Topics

Searching, displaying, and navigating to places

Convert place information between coordinates and user-friendly place names, get cycling directions, and conveniently display formatted addresses.

### Essentials

`struct Map`

A view that displays an embedded map interface.

`struct MapStyle`

A style that you can apply to a map.

### Annotations and overlays

`struct Annotation`

A customizable annotation used to indicate a location on a map.

`struct MapCircle`

A circular overlay with a configurable radius that you center on a geographic coordinate.

`struct MapPolygon`

A closed polygon overlay.

`struct MapPolyline`

An open polygon overlay consisting of one or more connected line segments.

`struct Marker`

A balloon-shaped annotation that marks a map location.

`struct UserAnnotation`

Displays the person’s current location on the map.

### Map controls

`struct MapCompass`

A view that reflects the current orientation of the associated map.

`struct MapLocationCompass`

A view that displays a combined user location button and map compass.

`struct MapPitchSlider`

A slider control that allows a person to change the pitch of the map.

`struct MapPitchToggle`

A button that sets the pitch of the associated map.

`struct MapScaleView`

Displays a legend with distance information for the associated map.

`struct MapUserLocationButton`

A button that sets the framing of the associated map to the user location.

`struct MapZoomStepper`

Buttons a person uses to adjust the zoom level of the map.

### Exploring at street level

`struct LookAroundPreview`

A view that provides a Look Around preview for a specific geographic location.

### Map features

`struct MapFeature`

A tappable map feature.

`struct MapSelection`

A value representing a selected feature on a map.

`protocol MapSelectable`

### Map customization

`struct MapCamera`

Defines a virtual viewpoint above the map surface.

`struct MapCameraBounds`

Defines an optional boundary of an area within which the map’s center needs to remain.

`struct MapCameraPosition`

A structure that describes how to position the map’s camera within the map.

`struct MapCameraUpdateContext`

A structure that defines additional information about the map camera.

`struct MapCameraUpdateFrequency`

A structure that describes when the map camera updates.

### Place information

`struct MapItemDetailSelectionAccessoryStyle`

The map item detail selection accessory style.

Specifies the selection accessory to display for the selected map item content.

Presents the accessory as an annotation callout on the map.

### Geocoding

`class MKGeocodingRequest`

A class that looks up a geographic coordinate using the provided string.

`class MKReverseGeocodingRequest`

A class that looks up address strings for the provided geographic coordinates.

### Representing places and addresses

`class MKMapItem`

A point of interest on the map.

`class MKAddress`

A class that contains a full address, and, optionally, a short address.

`class MKAddressRepresentations`

A class that provides formatted address strings.

GeoToolbox

Determine place descriptor information for map coordinates.

### Points of interest

`struct PointOfInterestCategories`

A structure you use to define points of interest to include or exclude on a map.

### Protocols

`protocol DynamicMapContent`

A  type of view that generates views from an underlying collection of data.

`protocol MapContent`

A protocol used to construct map content such as controls, markers, and annotations.

`struct MapContentBuilder`

A result builder that creates map content from closures you provide.

`struct MapContentView`

A view that contains content that displays on a map at a specific position, and that responds to specific interactions you specify.

### Structures

`struct DefaultUserAnnotationContent`

A structure that represents the view to show at the user’s location on the map.

`struct EmptyMapContent`

A map content element that doesn’t contain any content.

`struct MapProxy`

A proxy for accessing sizing information about a given map view.

`struct MapReader`

A container view that defines its contents as a function of information about the first contained map.

`struct TupleMapContent`

A view created from a Swift tuple of map content values.

`struct MapSelectableContentView`

## See Also

### The MapKit APIs

Adopting unified Maps URLs

Access Maps URLs and options for displaying Maps information across Apple platforms.

---

# https://developer.apple.com/documentation/mapkit/unified-map-urls

- MapKit
- Adopting unified Maps URLs

Article

# Adopting unified Maps URLs

Access Maps URLs and options for displaying Maps information across Apple platforms.

## Overview

In iOS 18.4 and later, macOS 15.4 and later, and watchOS 11.4 and later, the Maps platform provides a new, unified collection of URLs that offers the same functionality on all devices. Use the Maps path components to control aspects of the Maps display, ranging from the presentation of a simple map centered on a location you provide, to finding specific points of interest (POIs) and providing complex multistop driving, walking, or transit directions.

## Frame the map display

Use the `/frame` path component and `query` parameters to control aspects of the map’s framing and representation. This component allows you to set a map’s orientation, style, visible area (the map’s span), and other perspective controls, as described in the table below.

| Parameter | Description |
| --- | --- |
| `center` | Frames the map on a specific center described by comma-separated coordinate pair, such as `40.773957,-73.970974`. |
| `span` | Specifies the size of the area around the center point of the search in degrees of longitude and latitude, for example `0.05,0.05`, which is approximately one km for these examples. For more information on what these distances mean at different latitudes, see `init(latitudeDelta:longitudeDelta:)`. |
| `mode` | Sets the map’s mode to optionally allow location tracking: values can be `follow` or `follow-with-heading`, or `none`. |
| `heading` | Sets the direction toward which the map orients. |
| `pitch` | Sets the the vertical angle the map is oriented to. |
| `distance` | Sets the apparent distance from the viewer to the map surface; this parameter also affects the map’s `span`. |
| `map` | Sets the type of map to display: values can be `explore`, `driving`, `transit`, `satellite`, or `hybrid`. |

The following `/frame` path component examples demonstrate different kinds of map framing, along with details, where necessary, on how specific parameters affect what the map displays.

- Center the map at specific coordinate —

- Set map mode to transit and center map at specific coordinate —

- Set the map mode to `explore` and set user tracking to `follow` —

- Set map mode to `explore`; this setting cause the map to focus on a specified coordinate, and sets the map camera attributes —

- Set the map mode to `explore`, and set location tracking mode to `follow` — If you’re setting tracking mode and camera properties, the tracking mode takes precedence. Setting camera properties requires a center coordinate.

- Center the map at a specific coordinate and frame the map to the specified span —  It’s also possible to frame the map using the `distance` parameter, for example,

- Set the map mode to `explore`, which centers the map at a specified coordinate, and sets the map camera elevation, heading, and angle; in this example, facing East (90˚), a distance of 1 km, and a map pitch of 15˚ —

- Center the map at a specific coordinate and set the camera `distance` —

- Center the map at a specific coordinate and set the camera to the specified properties — If you provide both the `span` and `camera` properties, the `camera` properties take precedence, since they’re more specific than a `span`.

## Perform general searches

You can use the `/search` path component to search for specific kinds of locations using several `query` parameters.

| Parameter | Description |
| --- | --- |
| `center` | Searches the map starting at a specific center point described by a comma-separated coordinate pair, such as `40.773957,-73.970974`. |
| `query` | A search string. This parameter can be a general point of interest (POI) such as `pizza`, or a specific location such as an address string, such as `1000 Fifth Avenue, NY, NY`, or a city name such as `San Francisco`. For a list of POIs, see `MKPointOfInterestCategory`. |
| `span` | A span that specifies the size of the area around the center point of the search in degrees of longitude and latitude, for example `0.05,0.05` which is approximately 1 km for these examples. For more information on what these distances mean at different latitudes, see `init(latitudeDelta:longitudeDelta:)`. |

The following `/search` path component examples demonstrate how to use the `search` path component to find `pizza`, one of Maps’ POI identifiers, using different kinds of location and distance descriptions.

- Show results for `pizza` around a person’s location: The default center point is a person’s location.

- Show results for `pizza` centered on Trafalgar Square in London, United Kingdom —

- Show results for `pizza` within approximately 1 km around Washington Square Park in New York City —

## Show the place card of a POI

Using the `/place` path component enables you to specify a place card that shows useful details about points of interest on the map. Use the parameters in the following table to specify a POI and optionally the place card name and map type.

| Parameter | Description |
| --- | --- |
| `coordinate` | The latitude and longitude of the location, as a comma-separated pair of floating point values that represent latitude and longitude. |
| `address` | The address of the location, such as “1000 Fifth Ave, New York, NY”. |
| `place-id` | A Place ID is a unique identifier for a POI, such as `I521E602783BA9605`, The Metropolitan Museum of Art at 1000 Fifth Avenue, New York, NY 10028, United States; for more information on Place IDs, see Identifying unique locations with Place IDs. |
| `map` | The type of map to display. Maps supports `explore`, `driving`, `transit`, `satellite`, or `hybrid` as the map type. |

The following examples demonstrate different place card details along with details, where necessary, on how specific parameters affect what the maps displays.

- Show the address 1000 Fifth Ave, NY, NY, which is located at the specified coordinate and associated POIs near this address —

- Show 1000 Fifth Ave, NY, NY, 10028 using an address string and display associated POIs near this address:

- Show the place at PlaceID `IF149E70A3B3C4CB2` — American Museum of Natural History, 200 Central Park W, New York, NY 10024, United States — To find a specific Place ID, you can use `MKMapItem` in AppKit and UIKit, `Place` in MapKitJS, or see Place ID Lookup.

- Show a place card at the specified coordinate with custom name you provide — You can use this parameter when dropping a pin if you need to display a custom name for the place card.

- Show a person’s current location — This parameter requires that a person has given permission for Maps to display their location.

- Show the location of a person’s parked car — This parameter requires that a person has given Maps permission to record the place they parked.

## Explore the environment using Look Around

Use the `/look-around` path component and one of the following parameters to specify the initial location to start a session using Look Around.

| Parameter | Description |
| --- | --- |
| `coordinate` | The latitude and longitude of the location as a comma-separated pair of floating point values that represent latitude and longitude. |
| `address` | The address of the location. This parameter is an address string, such as “1000 Fifth Avenue, New York, NY 10028”. |
| `place-id` | A Place ID, which is a unique identifier for a point of interest, such as `I521E602783BA9605`, The Metropolitan Museum of Art at 1000 Fifth Avenue, New York, NY 10028, United States; for more information on Place IDs, see Identifying unique locations with Place IDs. |

The following examples demonstrate Look Around experiences in different cities:

- The San Francisco Ferry Building —

- The New York Stock Exchange, New York City, United States —

- The Tower of London, London, United Kingdom —

- The Eiffel Tower, Paris, France —

## Request directions

Use the `/directions` path component and following query parameters in several combinations to request directions.

| Parameters | Description | Values | Notes |
| --- | --- | --- | --- |
| `source` | The starting point of the navigation route | Specify an address, coordinate, or a place name | |
| `source-place-id` | An optional place identifier for the source parameter | A Place ID | Specifying a `source-place-id` also requires the `source` parameter |
| `destination` | The ending destination of the navigation route | Specify an address, coordinate, or a place name | |
| `destination-place-id` | An optional place identifier for the destination parameter | A Place ID | Specifying a `destination-place-id` also requires the `destination` parameter |
| `waypoint` | This parameter describes destinations in between the `source` and `destination` you can use for multistop routing | Specify an address, coordinate, or a place name | You can specify multiple waypoints by repeating the `waypoint` parameter |
| `waypoint-place-id` | An optional place identifier for the waypoint parameter | A Place ID, which is a unique identifier for a point of interest, such as `I521E602783BA9605`, The Metropolitan Museum of Art at 1000 Fifth Avenue, New York, NY 10028, United States; for more information on Place IDs, see Identifying unique locations with Place IDs | |
| `mode` | The transportation mode | You can specify one of `driving`, `walking`, `transit`, or `cycling` | |
| `avoid` | The route preferences are specific to the transportation mode | You can specify `tolls`, `highways`, `busy-roads`, or `stairs` | Specify multiple options by using a comma (,) as the delimiter |
| `transit-preferences` | The preferred method of travel for transit | Available modes are `bus`, `subway`, `commuter`, or `ferry` | Specify multiple options by using the comma (,) as the delimiter |
| `start` | Starts navigation after the delay in seconds that you specify | An integer that indicates the number of seconds to delay | |

You can use the query parameters to the `directions` path in a large number of combinations to control how Maps displays directions. Limitations on the combinators or side effect that they may have are listed in the table above.

- Show driving directions from a person’s current location to San Francisco City Hall:

- Show the step-by-step walking directions from the San Franciso Ferry Building to San Francisco City Hall:

- Show multistop driving directions to The San Francisco Ferry Building and San Francisco City Hall — You can specify multiple `waypoint` parameters for different waypoints.

- Show multistop driving directions, in New York City, from Riverside Park to The American Museum of Natural History, The Metropolitan Museum of Art, and The New York Public Library —

- Show transit directions from the New York Public Library to the American Museum of Natural History in New York City — Leaving off the `source` instructs Maps to display directions using public transit to the specified destination from a person’s current location, which might not be practical depending on a person’s location.

- Show driving directions from The American Museum of Natural History in New York City to Jones Beach State Park on Long Island, New York, avoiding tolls, if possible —

- Show driving directions to 941 Alamo Dr, in San Francisco, CA avoiding tolls and highways, if possible — You can use ‘,’ as a separator to specify multiple `avoid` options.

- Show walking directions from, a person’s current location to 1 La Avanzada St, San Francisco, CA avoiding highways, hills, stairs, and busy roads, if possible — The `avoid` options are only applicable to their respective transportation modes.

- Show transit directions from a person’s current location to Sausalito, preferring bus and ferry — Leaving off the `source` instructs Maps to display directions using public transit to the specified destination from a person’s current location, which might not be practical depending on their location.

## Find guides and curated places

Using the `/guides` path component, you can ask Maps to provide details about place guides and curated collections using the following URL:

## Report a problem

If you find an issue with Apple Maps, you can report a problem using the `/report-a-problem path` component, followed by any of the following parameters:

| Parameters | Description | Values |
| --- | --- | --- |
| `coordinate` | The latitude and longitude of the location | A comma-separated pair of floating point values that represent latitude and longitude |
| `address` | The address of the location | An address string, such as 1000 Fifth Avenue |
| `place-id` | The unique Place ID for a point of interest; for example, the place ID `I8CAD8EFA77AA3D42` represents Bethesda Terrace in New York City’s Central Park | For more information on Place IDs, see Identifying unique locations with Place IDs |

### Example problem reports

You can report a problem using the same kinds of location descriptors the other queries use. The following examples show how to report a problem using a coordinate, an address, or a Place ID.

- Report a problem at the coordinate `40.753035,-73.981846` (The New York Public Library at 42nd St & 5th Ave in New York City) -

- Report a problem at the address 1000 Fifth Avenue, New York, NY 10028 United States —

- Report a problem at Place ID `IBE1F65094A7A13B1`, the San Francisco Ferry Building —

When you open the `report-a-problem` URL, Maps opens a problem report sheet to ask a person for more detail on the nature of the problem, which Apple uses to investigate the report.

## Retrieve a full Maps URL from a shortened URL

When people share a map URL from Maps, this system creates a shortened version that’s more efficient to send in the app, for example, Messages or Mail. If you need to recover the full URL, follow these steps:

1. Check to see if the URL is a shortened Apple Maps URL; the host portion of an Apple shortened Maps URLs always end in `maps.apple` (no `.com`).

2. Attempt to access the URL programmatically, the full Apple Maps URL is accessible from the `HTTP 301` redirect response that the `maps.apple` server returns.

## See Also

### The MapKit APIs

MapKit for SwiftUI allows you to build map-centric views and apps across Apple platforms. You can design expressive and highly interactive Maps with minimal code by composing views, using ViewBuilders and view modifiers.

---

# https://developer.apple.com/documentation/mapkit/mapkit_for_appkit_and_uikit-deprecated-symbols

Collection

- MapKit
- Deprecated Symbols

API Collection

# Deprecated Symbols

MapKit classes, protocols, and entitlements that are no longer supported.

## Topics

### Classes

`class MKCircleView`

Provides the visual representation for an `MKCircle` annotation object.

Deprecated

`class MKOverlayView`

Defines the basic behavior associated with all overlay views.

`class MKOverlayPathView`

Represents a generic overlay that draws its contents using a Core Graphics path data type.

`class MKPolygonView`

Provides the visual representation for an `MKPolygon` annotation object.

`class MKPolylineView`

Provides the visual representation for an `MKPolyline` annotation object.

`class MKPinAnnotationView`

An annotation view that displays a pin image on the map.

### Properties

`var filterType: MKLocalSearchCompleter.FilterType`

The filter options for the search results.

`var pinColor: MKPinAnnotationColor`

The color of the pin head.

`var showsPointsOfInterest: Bool`

A Boolean value that indicates whether the map displays point-of-interest information.

`var mapType: MKMapType`

The map’s visual style.

### Methods

Returns the view associated with the overlay object, if any.

[`func mapView(MKMapView, didAddOverlayViews: [Any])`](https://developer.apple.com/documentation/mapkit/mkmapviewdelegate/mapview(_:didaddoverlayviews:))

Tells the delegate when the map adds one or more overlay views to the map.

Asks the delegate for the overlay view to use when displaying the specified overlay object.

### Protocols

`struct MapPin`

A pin-shaped annotation used to indicate a location on a map.

### Enumerations

`enum FilterType`

Constants indicating the types of search completions to return.

`enum MKMapType`

The type of map to display.

`enum MKPinAnnotationColor`

The supported colors for pin annotations.

### Entitlements

`Maps Entitlement`

A Boolean value that indicates whether the app may provide directions beyond what Maps supports, such as subway routes, hiking trails, and bike paths.

---

# https://developer.apple.com/documentation/mapkit/preparing-your-app-to-be-the-default-navigation-app

- MapKit
- Preparing your app to be the default navigation app

Article

# Preparing your app to be the default navigation app

Configure your navigation app so people can set it as the default on their devices.

## Overview

In iOS and iPadOS 18.4 and later in the European Union (EU), and in iOS 26.2 and later in Japan, a person may select an app other than the Maps app to provide navigation instructions. If your app provides navigation services and you want it to optionally become the default navigation app, there are several steps you need to take.

## Add the Default Navigation App entitlement

In Xcode, add the `com.apple.developer.navigation-app` entitlement to the `.entitlements` file for your app’s project. For instructions on how to add this entitlement, see `Default Navigation`.

## Adopt the geonavigation URL scheme

To provide navigation capabilities in your app, you need to adopt the `geo-navigation://` URL scheme. This scheme accepts the following types of navigation queries:

| Action | Parameters | Description | Values |
| --- | --- | --- | --- |
| /directions | source | Define the origination point of the navigation route | An address, coordinate, or place-name |
| /directions | destination | Define the final destination of the navigation route | An address, coordinate, or place-name |
| /directions | waypoint | Add places between the source and the destination to use for multistop routing | An address, coordinate, or place-name |
| /place | coordinate | Display a place for a given latitude and longitude at the provided location | A comma-separated pair of floating-point values that represent latitude and longitude |
| /place | address | Display a place at a specified address | An address string, such as `1 Dr Carlton B Goodlett Pl San Francisco, CA 94102` (San Francisco City Hall) |

You can use several of these parameters in combination to provide a number of action types, including:

- Providing the source and destination for a route.

- Providing the source, the destination, and one or more waypoints between the starting point and the final destination. You can provide these as strings that represent an address, a place-name, or a comma-separated pair of floating-point values for the latitude and longitude of the location as coordinates on the map.

## Add the geonavigation URL type support and URL scheme

Use the following steps to add the `geo-navigation` support to your app’s `Info.plist` file:

1. In your app’s Xcode project, select the `Info.plist` file in the Project navigator.

2. Expand the information property list by clicking its disclosure triangle to display the resources that the `Info.plist` file contains.

3. Open the URL Types array (or add a URL Types array, if necessary, by creating an entry and selecting URL Types from the pop-up menu).

4. Add a URL Schemes array to the URL Types array.

5. Add a string for the URL Schemes array and set its value to `geo-navigation`.

Before your app can open incoming `geo-navigation:` URLs, it needs to support this scheme as a custom URL scheme. To add this support, see Defining a custom URL scheme for your app.

## Prepare your app for submission to App Store Connect

To submit your app to App Store Connect, it needs to meet the following criteria:

- The `com.apple.developer.navigation-app` entitlement is in your app’s `.entitlements` file, and has a value of `true`.

- Your app is able to handle the `geo-navigation://` URL schema.

- The `Info.plist` file has the `UIBackgroundModes` property array and contains an entry with the string `location`.

---

# https://developer.apple.com/documentation/mapkit/anymapcontent

- MapKit
- AnyMapContent

Structure

# AnyMapContent

A type-erased map content.

MapKitSwiftUIMac Catalyst

@MainActor @preconcurrency
struct AnyMapContent

## Overview

An `AnyMapContent` allows changing the type of content used in a given map view.

## Topics

### Initializers

Create an instance that type-erases `base`.

## Relationships

### Conforms To

- `MapContent`
- `Sendable`
- `SendableMetatype`

---

# https://developer.apple.com/documentation/mapkit/mapkit-for-appkit-and-uikit)



---

# https://developer.apple.com/documentation/mapkit/mapkit-for-swiftui)



---

# https://developer.apple.com/documentation/mapkit/unified-map-urls)



---

# https://developer.apple.com/documentation/mapkit/mapkit_for_appkit_and_uikit-deprecated-symbols)

# The page you're looking for can't be found.

Search developer.apple.comSearch Icon

---

# https://developer.apple.com/documentation/mapkit/preparing-your-app-to-be-the-default-navigation-app)

# The page you're looking for can't be found.

Search developer.apple.comSearch Icon

---

# https://developer.apple.com/documentation/mapkit/anymapcontent)



---

# https://developer.apple.com/documentation/mapkit

Framework

# MapKit

Display map or satellite imagery within your app, call out points of interest, and determine placemark information for map coordinates.

## Overview

Use MapKit to give your app a sense of place with maps and location information. You can use the MapKit framework to:

- Embed maps directly into your app’s windows and views.

- Add annotations and overlays to a map to call out points of interest.

- Add LookAround capabilities to enable users to explore locations at street level.

- Respond to user interactions with well known points of interest, geographical features, and boundaries.

- Provide text completion to make it easy for users to search for a destination or point of interest.

## Topics

### The MapKit APIs

MapKit for SwiftUI allows you to build map-centric views and apps across Apple platforms. You can design expressive and highly interactive Maps with minimal code by composing views, using ViewBuilders and view modifiers.

Adopting unified Maps URLs

Access Maps URLs and options for displaying Maps information across Apple platforms.

### Articles

MapKit classes, protocols, and entitlements that are no longer supported.

Preparing your app to be the default navigation app

Configure your navigation app so people can set it as the default on their devices.

### Structures

`struct AnyMapContent`

A type-erased map content.

## See Also

### Related Documentation

Location and Maps Programming Guide

MapKit JS

Embed interactive Apple Maps on your website, annotate points of interest, and perform georelated searches.

Apple Maps Server API

Reduce API calls and conserve device power by streamlining your app’s georelated searches.

---

# https://developer.apple.com/documentation/mapkit/enabling-maps-capability-in-xcode

- MapKit
- MapKit for AppKit and UIKit
- Enabling Maps capability in Xcode

Article

# Enabling Maps capability in Xcode

Configure your routing app to support providing directions.

## Overview

A routing app, an iOS app that provides point-to-point directions, requires Maps capability to make those directions available to Maps and other apps. Maps capability allows an app to provide specific directions beyond what the Maps app supports, including subway routes, hiking trails, and bike paths. Use Xcode to enable Maps capability and select the supported modes.

### Add Maps Capability to Your Project

1. Open your project with Xcode. In the Project navigator, select your project.

2. Choose the target for the app in the Targets section of the outline view.

3. Click the Signing & Capabilities tab in the project editor.

4. In the toolbar, click the Library button (+) to open the Capabilities library and select Maps capability.

5. Select one or more routing modes using the checkboxes displayed under the Maps capability.

The screenshot below shows the Maps capability:

For more information on enabling capabilities in your app, see Adding capabilities to your app. For more information on providing directions in your app, see `MKDirections`.

## See Also

### Essentials

Identifying unique locations with Place IDs

Obtain information about a point of interest that persists over its lifetime.

`class MKMapView`

An embeddable map interface, similar to the one that the Maps app provides.

`class MKMapItem`

A point of interest on the map.

---

# https://developer.apple.com/documentation/mapkit/identifying-unique-locations-with-place-ids

- MapKit
- MapKit for AppKit and UIKit
- Identifying unique locations with Place IDs

Article

# Identifying unique locations with Place IDs

Obtain information about a point of interest that persists over its lifetime.

## Overview

MapKit for AppKit and UIKit, MapKit JS, and Apple Maps Server API provide a way for you to store and share references to places that matter to your application: the Place ID. A Place ID is an opaque string that semantically represents references to points of interest in the world, rather than particular coordinates or addresses.

A Place ID is a great feature for referencing a place’s information, even after that place’s information changes. Place IDs are also useful for displaying a place on a map. Use Place IDs to maintain unique collections of places that are important to your app.

### Obtain a Place ID

You obtain a Place ID by using Geocoder Lookup, Search, Search Autocomplete, Point-of-Interest Search, or choosing a place from Maps. You can also use a Place ID as a primary key or as part of a composite key in a database, or share Place IDs with other apps.

`MKMapItem` in MapKit for AppKit and UIKit, `Place` in MapKit JS, and `Place` objects in Apple Maps Server API include Place IDs that you can read and store. Additionally, you can obtain Place IDs for specific points of interest interactively from Place ID Lookup.

### Look up referenced place information

All MapKit platforms support using a Place ID to obtain the referenced place’s latest information, whether by issuing an `MKMapItemRequest` in MapKit for AppKit and UIKit, a `PlaceLookup` in MapKit JS, or a `Search for places using mulitple identifiers` request in Apple Maps Server API. These always return the most recent information for the place that the Place ID refers to, even if that information changed since you originally obtained it. You don’t have to track these changes or even update the stored Place ID.

A once-valid Place ID might fail to resolve from a lookup. However, this only happens when the referred place is no longer pertinent to Apple Maps. For instance, lookup failure might occur if a place has long been closed or simply no longer exists in the world in any meaningful way.

### Display a referenced place

Use Place IDs to display annotations with `MKMapItemAnnotation` from MapKit for AppKit and UIKit or doc://com.apple.documentation/documentation/mapkitjs/mapkit.placeannotation from MapKit JS. You can also use Place IDs to show more detailed selection accessories, such as popups that automatically display a place’s name, address, hours, and more, with `MKSelectionAccessory` from MapKit for AppKit and UIKit and `PlaceSelectionAccessory` from MapKit JS.

### Maintain a unique collection of places

Although Place IDs themselves are unique, they might not uniquely refer to a place. Multiple different Place IDs might refer to the same place. Because of this, storing collections of Place IDs, where each Place ID refers to a unique place (for example, a user’s favorite place list that shouldn’t contain the same place twice) is more complicated than simply making sure that each ID is bitwise-unique with every other ID in the set.

To aid with this task, place objects don’t just contain a Place ID in `identifier`. They also contain a set of alternate Place IDs. For MapKit for AppKit and UIKit it’s `alternateIdentifiers`, and for MapKit JS it’s `alternateIds`. This list is a nonexhaustive set of alternate Place IDs referring to the place.

This list is critical in maintaining a set of Place IDs that refer to unique places. When adding a new Place ID to an existing set of Place IDs meant to refer to unique places, consult the list of alternate Place IDs for the new Place ID. If your set already contains any of the alternate Place IDs, don’t add the new Place ID to the set because it would be a duplicate.

The procedure of checking for the presence of alternate Place IDs before insertion into an existing set works to minimize duplicate references. However, in rare cases, because alternate Place ID lists aren’t exhaustive, duplicates might occasionally occur. Ensure that your set of Place IDs doesn’t contain two Place IDs that refer to the same place by performing the following steps:

1. Create an empty set of Place IDs. This is the temporary set.

2. For each Place ID, look up its alternate IDs and check if the temporary set contains either the Place ID itself or any of its alternates. If the existing set already contains any of those IDs, remove the Place ID from the existing set, as it’s a duplicate. Otherwise, add the Place ID and all alternates to the temporary set.

After you’ve completed the above steps, delete the temporary set you used to ensure that there were no duplicates amongst Place IDs and their alternates. The existing set now has all duplicates removed.

To maintain performance, use these steps to perform de-duplication on a periodic basis. Alternatively, use Apple Maps Server API’s `Obtain a list of alternate place identifiers` for an efficient way of performing de-duplication.

## See Also

### Essentials

Enabling Maps capability in Xcode

Configure your routing app to support providing directions.

`class MKMapView`

An embeddable map interface, similar to the one that the Maps app provides.

`class MKMapItem`

A point of interest on the map.

---

# https://developer.apple.com/documentation/mapkit/mkmapview

- MapKit
- MKMapView

Class

# MKMapView

An embeddable map interface, similar to the one that the Maps app provides.

@MainActor
class MKMapView

## Overview

Use this class as-is to display map information and to manipulate the map contents from your app. The map view supports several display styles, including the `MKStandardMapConfiguration` that provides rich 2D and 3D presentations, an `MKHybridMapConfiguration` that provides a hybrid satellite map presentation, and `MKImageryMapConfiguration` that provides an imagery-based map presentation. Each of these map configurations support customization properties that refine specific elements of the map’s presentation.

You can center the map on specific coordinates, specify the size of the area you want to display, and annotate the map with custom information. When you initialize a map view, you specify the initial region for that map to display by setting the `region` property of the map. MapKit defines a region by a center point and a horizontal and vertical distance, referred to as the _span_. The _span_ defines how much of the map is visible, and is also how you set the zoom level. For example, specifying a large span results in the user seeing a wide geographical area at a low zoom level, whereas specifying a small span results in a more narrow geographical area and a higher zoom level.

In addition to setting the span programmatically, the `MKMapView` class supports many standard interactions for changing the position and zoom level of the map. In particular, map views support flick and pinch gestures for scrolling around the map and zooming in and out. The map view enables support for these gestures by default. You can enable and disable them using the `isScrollEnabled` and `isZoomEnabled` properties.

You can also use projected map coordinates instead of regions to specify some values. When you project the curved surface of the globe onto a flat surface, you get a two-dimensional version of a map where longitude lines appear to be parallel. To specify locations and distances, you use the `MKMapPoint`, `MKMapSize`, and `MKMapRect` data types.

Don’t subclass the `MKMapView` class itself. You can get information about the map view’s behavior by providing a delegate object. The map view calls the methods of your custom delegate to let it know about changes in the map status and to coordinate the display of custom annotations. The delegate object can be any object in your app as long as it conforms to the `MKMapViewDelegate` protocol. For more information about implementing the delegate object, see `MKMapViewDelegate`.

In macOS 10.14 and later, you can apply a light or dark appearance to your maps by modifying the `appearance` property of your map view (or one of its ancestor views). Even if you specify a custom appearance, users can use the Maps app to force all maps to adopt a light appearance. Use the map view’s `effectiveAppearance` property to determine the actual appearance of your map. For information about how to set view appearances, see Choosing a Specific Appearance for Your macOS App.

### Annotating the map

The `MKMapView` class supports the ability to annotate the map with custom information. Because a map may have large numbers of annotations, map views differentiate between the annotation objects MapKit uses to manage the annotation data and the view objects for presenting that data on the map.

An _annotation object_ is any object that conforms to the `MKAnnotation` protocol. Typically, you implement annotation objects using existing classes in your app’s data model. This allows you to manipulate the annotation data directly, but still make it available to the map view. Each annotation object contains information about the annotation’s location on the map, along with descriptive information that the map can display in a callout.

An _annotation view_,\_ \_which is an instance of the `MKAnnotationView` class, handles the presentation of annotation objects on the screen. An annotation view is responsible for presenting the annotation data in a way that makes sense. For example, the Maps app uses a marker icon to denote specific points of interest on a map. The MapKit framework offers the `MKMarkerAnnotationView` class for similar annotations in your own apps. You can also create annotation views that cover larger portions of the map.

Because the map view needs annotation views only when they’re onscreen, the `MKMapView` class provides a mechanism for queueing annotation views that aren’t in use. The map view detaches annotation views with a reuse identifier and queues them internally when they move offscreen. This feature improves memory use by keeping only a small number of annotation views in memory at once, and by recycling the views you do have. It also improves scrolling performance by alleviating the need to create new views while the map is scrolling.

When configuring your map interface, be sure to add all of your annotation objects right away. The map view uses the coordinate data in each annotation object to determine when the corresponding annotation view needs to appear onscreen. When an annotation moves onscreen, the map view asks its delegate to create a corresponding annotation view. If your app has different types of annotations, it can define different annotation view classes to represent each type.

### Adding overlays to the map

You can use overlays to layer content over a wide portion of the map. An _overlay_ object is any object that conforms to the `MKOverlay` protocol. An overlay object is a data object that contains the points that specify the shape and size of the overlay and its location on the map. Overlays can represent shapes like circles, rectangles, multisegment lines, and simple or complex polygons. You can also define your own custom overlays to represent other shapes.

_Overlay renderer_ objects, which are instances of the `MKOverlayRenderer` class, handle the presentation of an overlay. The job of the renderer is to draw the overlay’s content onto the screen when the map view requests it. For example, if you have a simple overlay that represents a bus route, you can use a polyline renderer to draw the line segments that trace the route of the bus. You can also define a custom renderer that draws both the bus route and icons at the location of each bus stop. When specifying overlays, you can add them to specific levels of the map, which tells the map view to render them above or below other types of map content.

When configuring your map interface, you can add overlay objects at any time. The map view uses the data in each overlay object to determine when the corresponding overlay view needs to appear onscreen. When an overlay moves onscreen, the map view asks its delegate to create a corresponding overlay renderer.

### Adding points of interest to the map

In iOS16 and macOS 13, and later, you can configure the map view to allow people to interact with a wide variety of points of interest (POIs) the map displays. These are instances of the `MKMapFeatureAnnotation` class, and cover a wide variety of elements visible on the map, including:

- Points of interest, such as museums, cafes, parks, and schools.

- Territorial boundaries, such as national borders, state boundaries, and neighborhoods.

- Features on the Earth’s surface, such as mountain ranges, rivers, and ocean basins.

You can control which features a person can interact with by configuring one of the `MKMapConfiguration` subclasses that defines the map’s presentation. Create an `MKMapConfiguration` with a set of `MKMapFeatureOptions` that describe the categories of POIs the map responds to. To further refine the specific kinds of points of interest the map display presents, use an `MKPointOfInterestFilter`.

When a person interacts with a specific POI, the framework calls your delegate object with one of the `MKMapViewDelegate` protocol methods, depending on whether the person selects or deselects a specific POI. These methods give your app a chance to respond to the selection or deselection of an element. Depending on the kind of element, you can decide whether you want to customize the display characteristics in the case of a POI, or in the case of territories or geographic map features, you can create custom interactions to display information.

### Adding Look Around views to the map

iOS16 and macOS 13, and later, support the inclusion of a Look Around view within the map view. Look Around allows people to explore the environment at street level. You request a Look Around view by creating an `MKLookAroundSceneRequest` with either an `MKMapItem` or a `CLLocationCoordinate2D`, and if there’s Look Around imagery available for the specified location, the framework returns an `MKLookAroundScene` for you to display using an `MKLookAroundViewController`.

## Topics

### Configuring the map appearance

`var preferredConfiguration: MKMapConfiguration`

The characteristics of the map view, including the map type and features the map displays.

`var pitchButtonVisibility: MKFeatureVisibility`

A value that indicates whether the map’s pitch button is visible.

`var showsUserTrackingButton: Bool`

A Boolean value that indicates whether the map displays the user tracking button.

`class MKMapConfiguration`

An abstract class that represents the shared elements of map configurations.

`class MKStandardMapConfiguration`

The class that represents the default map presentation, which is a street map that shows the position of all roads and some road names.

`class MKHybridMapConfiguration`

The class that represents a satellite image of the area with road and road name information layers on top.

`class MKImageryMapConfiguration`

The class that represents an imagery-based map presentation, such as one using satellite imagery.

### Customizing the map view behavior

`var delegate: (any MKMapViewDelegate)?`

The receiver’s delegate.

`protocol MKMapViewDelegate`

Optional methods that you use to receive map-related update messages.

### Accessing map properties

`enum MKMapType`

The type of map to display.

Deprecated

`var isZoomEnabled: Bool`

A Boolean value that determines whether the user may use pinch gestures to zoom in and out of the map.

`var isScrollEnabled: Bool`

A Boolean value that determines whether the user may scroll around the map.

`var isPitchEnabled: Bool`

A Boolean value that indicates whether the map uses the camera’s pitch information.

`var isRotateEnabled: Bool`

A Boolean value that indicates whether the map uses the camera’s heading information.

`var mapType: MKMapType`

The type of data the map view displays.

### Manipulating the visible portion of the map

`var region: MKCoordinateRegion`

The area the map view displays.

`func setRegion(MKCoordinateRegion, animated: Bool)`

Changes the currently visible region, and optionally animates the change.

`var centerCoordinate: CLLocationCoordinate2D`

The map coordinate at the center of the map view.

`func setCenter(CLLocationCoordinate2D, animated: Bool)`

Changes the center coordinate of the map, and optionally animates the change.

[`func showAnnotations([any MKAnnotation], animated: Bool)`](https://developer.apple.com/documentation/mapkit/mkmapview/showannotations(_:animated:))

Sets the visible region so that the map displays the specified annotations.

`var visibleMapRect: MKMapRect`

The area visible in the map view.

`func setVisibleMapRect(MKMapRect, animated: Bool)`

Changes the currently visible portion of the map, and optionally animates the change.

`func setVisibleMapRect(MKMapRect, edgePadding: UIEdgeInsets, animated: Bool)`

Changes the currently visible portion of the map, allowing you to specify additional space around the edges.

### Constraining the map view

`func setCameraBoundary(MKMapView.CameraBoundary?, animated: Bool)`

Sets the camera boundary for the map view, specifying whether to use animation.

`var cameraBoundary: MKMapView.CameraBoundary?`

The boundary of the area within which the map view’s center needs to remain.

`func setCameraZoomRange(MKMapView.CameraZoomRange?, animated: Bool)`

Sets the camera zoom range for the map view, specifying whether to use animation.

`var cameraZoomRange: MKMapView.CameraZoomRange!`

The zoom range to apply to the map view.

`class CameraBoundary`

A boundary of an area within which the map’s center needs to remain.

`class CameraZoomRange`

A camera zoom range that limits the distances to which the user can zoom.

### Configuring the map display

`func setCamera(MKMapCamera, animated: Bool)`

Changes the camera to use for determining the map’s viewing parameters, and optionally animates the change.

`var camera: MKMapCamera`

The camera to use for determining the appearance of the map.

`var showsCompass: Bool`

A Boolean value that indicates whether the map displays a compass control.

`var showsPitchControl: Bool`

A Boolean value that indicates whether the map displays the pitch control.

`var showsScale: Bool`

A Boolean value that indicates whether the map shows scale information.

`var showsZoomControls: Bool`

A Boolean value that indicates whether the map displays zoom controls.

`var showsBuildings: Bool`

A Boolean value that indicates whether the map displays extruded building information on supported map types.

`var showsPointsOfInterest: Bool`

A Boolean value that indicates whether the map displays point-of-interest information.

`var pointOfInterestFilter: MKPointOfInterestFilter?`

The filter to use for determining the points of interest that appear on the map.

`var showsTraffic: Bool`

A Boolean value that indicates whether the map displays traffic information.

### Displaying the user’s location

Converting a user’s location to a descriptive placemark

Transform the user’s location that displays on a map into an informative textual description by reverse geocoding.

`var showsUserLocation: Bool`

A Boolean value that indicates whether the map tries to display the user’s location.

`var isUserLocationVisible: Bool`

A Boolean value that indicates whether the user’s location is visible in the map view.

`var userLocation: MKUserLocation`

The annotation object that represents the user’s location.

`var userTrackingMode: MKUserTrackingMode`

The mode to use for tracking the user’s location.

`func setUserTrackingMode(MKUserTrackingMode, animated: Bool)`

Sets the mode to use for tracking the user’s location, with optional animation.

`enum MKUserTrackingMode`

The mode to use for tracking the user’s location on the map.

### Annotating the map

[`var annotations: [any MKAnnotation]`](https://developer.apple.com/documentation/mapkit/mkmapview/annotations)

The annotations associated with the map view.

`func addAnnotation(any MKAnnotation)`

Adds the specified annotation to the map view.

[`func addAnnotations([any MKAnnotation])`](https://developer.apple.com/documentation/mapkit/mkmapview/addannotations(_:))

Adds an array of annotation objects to the map view.

`func removeAnnotation(any MKAnnotation)`

Removes the specified annotation object from the map view.

[`func removeAnnotations([any MKAnnotation])`](https://developer.apple.com/documentation/mapkit/mkmapview/removeannotations(_:))

Removes an array of annotation objects from the map view.

Returns the annotation objects within the specified map rectangle.

### Managing annotation selections

`var annotationVisibleRect: CGRect`

The visible rectangle where the map is displaying annotation views.

[`var selectedAnnotations: [any MKAnnotation]`](https://developer.apple.com/documentation/mapkit/mkmapview/selectedannotations)

The selected annotations.

`func selectAnnotation(any MKAnnotation, animated: Bool)`

Selects the specified annotation and displays a callout view for it.

`func deselectAnnotation((any MKAnnotation)?, animated: Bool)`

Deselects the specified annotation and hides its callout view.

### Creating annotation views

`func register(AnyClass?, forAnnotationViewWithReuseIdentifier: String)`

Registers an annotation view class that the map can create automatically.

Returns a reusable annotation view using the specified identifier with a specified existing annotation view, if possible.

Returns a reusable annotation view using its identifier.

Returns the annotation view associated with the specified annotation object, if any.

`let MKMapViewDefaultAnnotationViewReuseIdentifier: String`

The default reuse identifier for your map’s annotation views.

`let MKMapViewDefaultClusterAnnotationViewReuseIdentifier: String`

The default reuse identifier for the annotation view representing a cluster of annotations.

### Accessing overlays

[`var overlays: [any MKOverlay]`](https://developer.apple.com/documentation/mapkit/mkmapview/overlays)

The overlay objects associated with the map view.

Returns overlay objects in the specified level of the map.

Returns the renderer object for drawing the contents of the specified overlay object.

`enum MKOverlayLevel`

Constants that indicate the position of overlays relative to other content.

Returns the view associated with the overlay object, if any.

### Adding and inserting overlays

`func addOverlay(any MKOverlay, level: MKOverlayLevel)`

Adds the overlay object to the map at the specified level.

[`func addOverlays([any MKOverlay], level: MKOverlayLevel)`](https://developer.apple.com/documentation/mapkit/mkmapview/addoverlays(_:level:))

Adds an array of overlay objects to the map at the specified level.

`func addOverlay(any MKOverlay)`

Adds a single overlay object to the map.

[`func addOverlays([any MKOverlay])`](https://developer.apple.com/documentation/mapkit/mkmapview/addoverlays(_:))

Adds an array of overlay objects to the map.

`func insertOverlay(any MKOverlay, at: Int, level: MKOverlayLevel)`

Inserts an overlay object into the level at the specified index.

`func insertOverlay(any MKOverlay, at: Int)`

Inserts an overlay object into the list associated with the map.

`func insertOverlay(any MKOverlay, above: any MKOverlay)`

Inserts one overlay object above another.

`func insertOverlay(any MKOverlay, below: any MKOverlay)`

Inserts one overlay object below another.

`func exchangeOverlay(any MKOverlay, with: any MKOverlay)`

Exchanges the positions of two overlay objects.

`func exchangeOverlay(at: Int, withOverlayAt: Int)`

Exchanges the position of two overlay objects at the specified index.

### Removing overlays

`func removeOverlay(any MKOverlay)`

Removes a single overlay object from the map.

[`func removeOverlays([any MKOverlay])`](https://developer.apple.com/documentation/mapkit/mkmapview/removeoverlays(_:))

Removes one or more overlay objects from the map.

### Converting map coordinates

Converts a map coordinate to a point in the specified view.

Converts a point in the specified view’s coordinate system to a map coordinate.

Converts a map region to a rectangle in the specified view.

Converts a rectangle in the specified view’s coordinate system to a map region.

### Adjusting map regions and rectangles

Adjusts the aspect ratio of the specified region to ensure that it fits in the map view’s frame.

Returns a centered map rectangle with the same aspect ratio as the map view’s frame.

Returns a centered, inset map rectangle with the same aspect ratio as the map view’s frame.

### Instance Properties

`var selectableMapFeatures: MKMapFeatureOptions`

The property that describes which selectable features the map responds to.

## Relationships

### Inherits From

- `NSView`
- `UIView`

### Conforms To

- `CALayerDelegate`
- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSAccessibilityElementProtocol`
- `NSAccessibilityProtocol`
- `NSAnimatablePropertyContainer`
- `NSAppearanceCustomization`
- `NSCoding`
- `NSDraggingDestination`
- `NSObjectProtocol`
- `NSStandardKeyBindingResponding`
- `NSTouchBarProvider`
- `NSUserActivityRestoring`
- `NSUserInterfaceItemIdentification`
- `Sendable`
- `SendableMetatype`
- `UIAccessibilityIdentification`
- `UIActivityItemsConfigurationProviding`
- `UIAppearance`
- `UIAppearanceContainer`
- `UICoordinateSpace`
- `UIDynamicItem`
- `UIFocusEnvironment`
- `UIFocusItem`
- `UIFocusItemContainer`
- `UILargeContentViewerItem`
- `UIPasteConfigurationSupporting`
- `UIPopoverPresentationControllerSourceItem`
- `UIResponderStandardEditActions`
- `UITraitChangeObservable`
- `UITraitEnvironment`
- `UIUserActivityRestoring`

## See Also

### Essentials

Enabling Maps capability in Xcode

Configure your routing app to support providing directions.

Identifying unique locations with Place IDs

Obtain information about a point of interest that persists over its lifetime.

`class MKMapItem`

A point of interest on the map.

---

# https://developer.apple.com/documentation/mapkit/mkmapitem

- MapKit
- MKMapItem

Class

# MKMapItem

A point of interest on the map.

class MKMapItem

## Mentioned in

Identifying unique locations with Place IDs

## Overview

A map item includes a geographic location and any interesting data that might apply to that location, such as the address at that location and the name of a business at that address. You can also create a special `MKMapItem` object representing the user’s location.

Use this class to do the following:

- Share map-related data with the Maps app.

- Handle requests for directions that originate from the Maps app.

To display information in the Maps app, create an `MKMapItem` object with the information you want to display and call the `openMaps(with:launchOptions:)` method. The Maps app displays that location on the map and shows the information you provide.

If you implement a routing app, the Maps app provides two `MKMapItem` objects representing the start and end points. Use the information in those two objects to plot the route and generate directions.

## Topics

### Creating map items

`init(placemark: MKPlacemark)`

Creates and returns a map item object using the specified placemark object.

Deprecated

Creates and returns a singleton map item object representing the user’s location.

### Accessing the map item attributes

`class Identifier`

A unique identifier for a place.

A set of alternative identifiers for a place.

`var identifier: MKMapItem.Identifier?`

`var isCurrentLocation: Bool`

A Boolean value that indicates whether the map item represents the user’s location.

`var name: String?`

The descriptive name associated with the map item.

`var placemark: MKPlacemark`

The placemark object containing the location information.

`var pointOfInterestCategory: MKPointOfInterestCategory?`

The point-of-interest category for the map item.

`var phoneNumber: String?`

The phone number associated with a business at the specified location.

`var timeZone: TimeZone?`

The time zone of the specified location.

`var url: URL?`

The URL associated with the specified location.

### Launching the Maps app

Opens the Maps app and displays the specified map items.

Opens the Maps app using the specified map items and options.

Opens the Maps app from a particular scene using the specified map items and options.

Opens the Maps app and displays the map item.

Opens the Maps app from a particular scene using the specified options.

### Serializing a map item

`let MKMapItemTypeIdentifier: String`

A constant that indicates the type of a serialized map item.

### Opening items at launch time

Launch options to specify when opening map items in the Maps app.

Strings that represent the possible values of the launch options direction mode key.

### Initializers

`init?(coder: NSCoder)`

`init(location: CLLocation, address: MKAddress?)`

Creates and returns a map item object using the specified location and address objects.

### Instance Properties

`var address: MKAddress?`

The address object.

`var addressRepresentations: MKAddressRepresentations?`

The address representations object that contains various address representations useful for display purposes.

`var location: CLLocation`

The location object.

## Relationships

### Inherits From

- `NSObject`

### Conforms To

- `CVarArg`
- `Copyable`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSCoding`
- `NSItemProviderReading`
- `NSItemProviderWriting`
- `NSObjectProtocol`
- `NSSecureCoding`

## See Also

### Essentials

Enabling Maps capability in Xcode

Configure your routing app to support providing directions.

Obtain information about a point of interest that persists over its lifetime.

`class MKMapView`

An embeddable map interface, similar to the one that the Maps app provides.

---

# https://developer.apple.com/documentation/mapkit/mkcoordinateregion

- MapKit
- MKCoordinateRegion

Structure

# MKCoordinateRegion

A rectangular geographic region that centers around a specific latitude and longitude.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

struct MKCoordinateRegion

## Topics

### Creating a region

`init()`

Creates a coordinate region.

`init(center: CLLocationCoordinate2D, latitudinalMeters: CLLocationDistance, longitudinalMeters: CLLocationDistance)`

Creates a new coordinate region from the specified coordinate and distance values.

`init(MKMapRect)`

Returns the region that corresponds to the specified map rectangle.

`init(center: CLLocationCoordinate2D, span: MKCoordinateSpan)`

Creates a coordinate region with a span around the specified center coordinate.

### Getting the region coordinates

`var center: CLLocationCoordinate2D`

The center point of the region.

`var span: MKCoordinateSpan`

The horizontal and vertical span representing the amount of map to display.

## Relationships

### Conforms To

- `BitwiseCopyable`
- `Sendable`

## See Also

### Map coordinates

`struct MKCoordinateSpan`

The width and height of a map region.

`struct MKMapRect`

A rectangular area on a two-dimensional map projection.

`struct MKMapPoint`

A point on a two-dimensional map projection.

`struct MKMapSize`

Width and height information on a two-dimensional map projection.

`class MKDistanceFormatter`

A utility object that converts between a geographic distance and a string-based expression of that distance.

---

# https://developer.apple.com/documentation/mapkit/mkcoordinatespan

- MapKit
- MKCoordinateSpan

Structure

# MKCoordinateSpan

The width and height of a map region.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

struct MKCoordinateSpan

## Overview

You use the delta values in this structure to indicate the desired zoom level of the map, with smaller delta values corresponding to a higher zoom level.

## Topics

### Creating a coordinate span

`init()`

Creates a coordinate span that represents a width and height on a map.

`init(latitudeDelta: CLLocationDegrees, longitudeDelta: CLLocationDegrees)`

Creates a new `MKCoordinateSpan` from the specified values.

### Getting the span coordinates

`var latitudeDelta: CLLocationDegrees`

The amount of north-to-south distance (measured in degrees) to display on the map.

`var longitudeDelta: CLLocationDegrees`

The amount of east-to-west distance (measured in degrees) to display for the map region.

## Relationships

### Conforms To

- `BitwiseCopyable`
- `Copyable`
- `Sendable`

## See Also

### Map coordinates

`struct MKCoordinateRegion`

A rectangular geographic region that centers around a specific latitude and longitude.

`struct MKMapRect`

A rectangular area on a two-dimensional map projection.

`struct MKMapPoint`

A point on a two-dimensional map projection.

`struct MKMapSize`

Width and height information on a two-dimensional map projection.

`class MKDistanceFormatter`

A utility object that converts between a geographic distance and a string-based expression of that distance.

---

# https://developer.apple.com/documentation/mapkit/mkmaprect

- MapKit
- MKMapRect

Structure

# MKMapRect

A rectangular area on a two-dimensional map projection.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

struct MKMapRect

## Overview

If you project the curved surface of the globe onto a flat surface, what you get is a two-dimensional version of a map where longitude lines appear to be parallel. Such maps are often used to show the entire surface of the globe all at once. An `MKMapRect` data structure represents a rectangular area as seen on this two-dimensional map.

## Topics

### Creating a map rectangle

`init()`

Creates the rectangle with an empty region.

`init(origin: MKMapPoint, size: MKMapSize)`

Creates the map rectangle with the specified point and size.

`init(x: Double, y: Double, width: Double, height: Double)`

Creates a new map rectangle structure from the specified values.

`init(MKMapRect)`

Returns the region that corresponds to the specified map rectangle.

### Getting standard map rectangles

`static let null: MKMapRect`

The null map rectangle.

`static let world: MKMapRect`

The map rectangle that represents the world in the two-dimensional map projection.

### Getting the rectangle coordinates

`var origin: MKMapPoint`

The origin point of the rectangle.

`var size: MKMapSize`

The width and height of the rectangle, starting from the origin point.

### Getting the boundaries

`var minX: Double`

Returns the minimum x-axis value of the specified rectangle.

`var minY: Double`

Returns the minimum y-axis value of the specified rectangle.

`var midX: Double`

Returns the mid-point along the x-axis of the specified rectangle.

`var midY: Double`

Returns the mid-point along the y-axis of the specified rectangle.

`var maxX: Double`

Returns the maximum x-axis value of the specified rectangle.

`var maxY: Double`

Returns the maximum y-axis value of the specified rectangle.

`var width: Double`

Returns the width of the map rectangle.

`var height: Double`

Returns the height of the map rectangle.

### Comparing rectangles

`var isNull: Bool`

A Boolean value that indicates whether the specified rectangle is null.

Returns a Boolean value that indicates whether two map rectangles are equal.

`var isEmpty: Bool`

A Boolean value that indicates whether the specified rectangle has no area.

`var spans180thMeridian: Bool`

A Boolean value that indicates whether the specified map rectangle crosses the 180th meridian.

`var remainder: MKMapRect`

A rectangle that represents the normalized portion of the specified rectangle that lies outside the world map boundaries.

### Intersecting the rectangle

Returns a Boolean value that indicates whether the specified map point lies within the rectangle.

Returns a Boolean value that indicates whether one rectangle contains another.

Returns a Boolean value that indicates whether two rectangles intersect each other.

### Modifying the rectangle

Returns a rectangle that represents the union of two rectangles.

Returns the rectangle that represents the intersection of two rectangles.

Returns the specified rectangle with an inset by the specified amounts.

Returns a rectangle with an origin point that shifts by the specified amount.

Divides the specified rectangle into two smaller rectangles.

### Getting a description of the rectangle

Returns a formatted string for the specified map rectangle.

## Relationships

### Conforms To

- `BitwiseCopyable`
- `Sendable`

## See Also

### Map coordinates

`struct MKCoordinateRegion`

A rectangular geographic region that centers around a specific latitude and longitude.

`struct MKCoordinateSpan`

The width and height of a map region.

`struct MKMapPoint`

A point on a two-dimensional map projection.

`struct MKMapSize`

Width and height information on a two-dimensional map projection.

`class MKDistanceFormatter`

A utility object that converts between a geographic distance and a string-based expression of that distance.

---

# https://developer.apple.com/documentation/mapkit/mkmappoint

- MapKit
- MKMapPoint

Structure

# MKMapPoint

A point on a two-dimensional map projection.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

struct MKMapPoint

## Overview

If you project the curved surface of the globe onto a flat surface, you get a two-dimensional version of a map where longitude lines appear to be parallel. An `MKMapPoint` data structure represents a point on this two-dimensional map.

The underlying units that MapKit uses to draw the contents of an `MKMapView` define the actual units of a map point, but you don’t need to worry about these units directly. You use map points primarily to simplify computations that are complex to do using coordinate values on a curved surface. By converting to map points, you can perform those calculations on a flat surface, which is generally much simpler, and then convert back as necessary. You can map between coordinate values and map points using the `init(_:)` and `coordinate` functions.

When saving map-related data to a file, save coordinate values (latitude and longitude) rather than map points.

## Topics

### Creating a map point

`init()`

Creates a map point at an unspecified point.

`init(x: Double, y: Double)`

Creates a new map point structure from the specified values.

`init(CLLocationCoordinate2D)`

Creates the map point data structure that corresponds to the specified coordinate.

### Getting the point coordinates

`var x: Double`

The location of the point along the x-axis of the map.

`var y: Double`

The location of the point along the y-axis of the map.

`var coordinate: CLLocationCoordinate2D`

A 2D coordinate that corresponds to the latitude and longitude of the specified map point.

### Comparing map points

Returns a Boolean value that indicates whether two map points are equal.

### Getting the distance between points

Returns the number of meters between two map points.

Returns the distance that one map point spans at the specified latitude.

Returns the number of map points that represent one meter at the specified latitude.

### Getting a description of the point

Returns a formatted string for the specified map point.

## Relationships

### Conforms To

- `BitwiseCopyable`
- `Sendable`

## See Also

### Map coordinates

`struct MKCoordinateRegion`

A rectangular geographic region that centers around a specific latitude and longitude.

`struct MKCoordinateSpan`

The width and height of a map region.

`struct MKMapRect`

A rectangular area on a two-dimensional map projection.

`struct MKMapSize`

Width and height information on a two-dimensional map projection.

`class MKDistanceFormatter`

A utility object that converts between a geographic distance and a string-based expression of that distance.

---

# https://developer.apple.com/documentation/mapkit/mkmapsize

- MapKit
- MKMapSize

Structure

# MKMapSize

Width and height information on a two-dimensional map projection.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

struct MKMapSize

## Overview

If you project the curved surface of the globe onto a flat surface, what you get is a two-dimensional version of a map where longitude lines appear to be parallel. Such maps are often used to show the entire surface of the globe all at once. An `MKMapSize` data structure represents a horizontal and vertical distance as measured on this two-dimensional map.

## Topics

### Creating a map size

`init()`

Creates a map size that represents an empty area on a two-dimensional projection of a map.

`init(width: Double, height: Double)`

Creates a map size that represents an area on a two-dimensional projection of a map with the specified width and height.

### Getting standard map sizes

`static let world: MKMapSize`

The width and height, in map points, of the world in a two-dimensional map projection.

### Getting the width and height

`var height: Double`

The height of the specified area, measured in map points.

`var width: Double`

The width of the specified area, measured in map points.

### Comparing map sizes

Returns a Boolean value that indicates whether two map sizes are equal.

### Getting a description of the size

Returns a formatted string for the specified map size.

## Relationships

### Conforms To

- `BitwiseCopyable`
- `Sendable`

## See Also

### Map coordinates

`struct MKCoordinateRegion`

A rectangular geographic region that centers around a specific latitude and longitude.

`struct MKCoordinateSpan`

The width and height of a map region.

`struct MKMapRect`

A rectangular area on a two-dimensional map projection.

`struct MKMapPoint`

A point on a two-dimensional map projection.

`class MKDistanceFormatter`

A utility object that converts between a geographic distance and a string-based expression of that distance.

---

# https://developer.apple.com/documentation/mapkit/mkdistanceformatter

- MapKit
- MKDistanceFormatter

Class

# MKDistanceFormatter

A utility object that converts between a geographic distance and a string-based expression of that distance.

class MKDistanceFormatter

## Overview

Use a distance formatter to display distances to the user or to parse user-specified text to obtain a numerical value for a distance. When formatting strings containing distances, a distance formatter object takes into account the user’s locale and language settings. You can also specify a custom locale or custom units for any distances that you format.

## Topics

### Converting distances

Creates a string representation of the specified distance.

Returns the distance value parsed from the specified string.

### Specifying the format

`var locale: Locale!`

The locale to use when formatting strings.

`var units: MKDistanceFormatter.Units`

The measuring system — imperial or metric — to use for units.

`enum Units`

Constants that reflect the type of units to use in the string.

`var unitStyle: MKDistanceFormatter.DistanceUnitStyle`

The preferred style for units.

`enum DistanceUnitStyle`

Constants that indicate the format style to use for strings.

## Relationships

### Inherits From

- `Formatter`

### Conforms To

- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSCoding`
- `NSCopying`
- `NSObjectProtocol`

## See Also

### Map coordinates

`struct MKCoordinateRegion`

A rectangular geographic region that centers around a specific latitude and longitude.

`struct MKCoordinateSpan`

The width and height of a map region.

`struct MKMapRect`

A rectangular area on a two-dimensional map projection.

`struct MKMapPoint`

A point on a two-dimensional map projection.

`struct MKMapSize`

Width and height information on a two-dimensional map projection.

---

# https://developer.apple.com/documentation/mapkit/mkmapcamera

- MapKit
- MKMapCamera

Class

# MKMapCamera

A virtual camera for defining the appearance of the map.

class MKMapCamera

## Overview

A camera object defines a virtual viewpoint above the map surface and affects how MapKit presents the map to the user. You use a camera object to specify the location of the camera on the map, the compass heading indicating the camera’s viewing direction, the pitch of the camera relative to the map perpendicular, and the camera’s altitude above the map. These factors create a map view with a three-dimensional perspective.

After creating an instance of this class, configure it with the desired attributes and assign it to your map view. When you assign a camera to your map view, MapKit centers the map using the value in your camera object’s `centerCoordinate` property, updating the map’s own region information in the process. The map also takes the camera’s pitch and altitude into account when calculating the visible region, ensuring that the region encompasses the visible content on the map.

## Topics

### Getting a camera object

`convenience init(lookingAtCenter: CLLocationCoordinate2D, fromEyeCoordinate: CLLocationCoordinate2D, eyeAltitude: CLLocationDistance)`

Returns a new camera object using the specified viewing angle information.

`convenience init(lookingAtCenter: CLLocationCoordinate2D, fromDistance: CLLocationDistance, pitch: CGFloat, heading: CLLocationDirection)`

Returns a new camera object using the specified distance, pitch, and heading information.

`convenience init(lookingAt: MKMapItem, forViewSize: CGSize, allowPitch: Bool)`

Returns a new camera object using the specified map item, view size, and pitch.

### Configuring the viewing angle

`var centerCoordinate: CLLocationCoordinate2D`

The map coordinate at the center of the map view.

`var heading: CLLocationDirection`

The heading of the camera (in degrees) relative to true north.

`var centerCoordinateDistance: CLLocationDistance`

The distance from the center point of the map to the camera, in meters.

`var pitch: CGFloat`

The viewing angle of the camera, in degrees.

`var altitude: CLLocationDistance`

The altitude above the ground, in meters.

Deprecated

## Relationships

### Inherits From

- `NSObject`

### Conforms To

- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSCoding`
- `NSCopying`
- `NSObjectProtocol`
- `NSSecureCoding`

## See Also

### Map customization

`class MKCompassButton`

A specialized view that displays the compass heading for its associated map.

`class MKScaleView`

A specialized view that displays the scale information for its associated map.

`class MKZoomControl`

A specialized view that displays and controls the zoom level of the map view.

`class MKPitchControl`

A specialized view that displays and controls the pitch angle of the map view.

`class MKUserTrackingButton`

A specialized button that allows the user to toggle whether the map tracks to the heading the user is facing.

`class MKUserTrackingBarButtonItem`

A specialized bar button item that allows the user to toggle whether the map tracks to the heading the user is facing.

---

# https://developer.apple.com/documentation/mapkit/mkcompassbutton

- MapKit
- MKCompassButton

Class

# MKCompassButton

A specialized view that displays the compass heading for its associated map.

@MainActor
class MKCompassButton

## Overview

Use this class when you want to incorporate a standard compass button into your own view hierarchy. A compass button reflects the current orientation of its associated map view. Tapping the compass button reorients the map so that due north is at the top of the map view.

## Topics

### Creating a compass button

`convenience init(mapView: MKMapView?)`

Creates a compass button and associates it with the specified map view.

### Getting the compass attributes

`var mapView: MKMapView?`

The map view that provides the heading information for the compass button.

`var compassVisibility: MKFeatureVisibility`

The visibility of the compass button.

`enum MKFeatureVisibility`

Constants that indicate the visibility of different map features.

## Relationships

### Inherits From

- `NSView`
- `UIView`

### Conforms To

- `CALayerDelegate`
- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSAccessibilityElementProtocol`
- `NSAccessibilityProtocol`
- `NSAnimatablePropertyContainer`
- `NSAppearanceCustomization`
- `NSCoding`
- `NSDraggingDestination`
- `NSObjectProtocol`
- `NSStandardKeyBindingResponding`
- `NSTouchBarProvider`
- `NSUserActivityRestoring`
- `NSUserInterfaceItemIdentification`
- `Sendable`
- `SendableMetatype`
- `UIAccessibilityIdentification`
- `UIActivityItemsConfigurationProviding`
- `UIAppearance`
- `UIAppearanceContainer`
- `UICoordinateSpace`
- `UIDynamicItem`
- `UIFocusEnvironment`
- `UIFocusItem`
- `UIFocusItemContainer`
- `UILargeContentViewerItem`
- `UIPasteConfigurationSupporting`
- `UIPopoverPresentationControllerSourceItem`
- `UIResponderStandardEditActions`
- `UITraitChangeObservable`
- `UITraitEnvironment`
- `UIUserActivityRestoring`

## See Also

### Map customization

`class MKMapCamera`

A virtual camera for defining the appearance of the map.

`class MKScaleView`

A specialized view that displays the scale information for its associated map.

`class MKZoomControl`

A specialized view that displays and controls the zoom level of the map view.

`class MKPitchControl`

A specialized view that displays and controls the pitch angle of the map view.

`class MKUserTrackingButton`

A specialized button that allows the user to toggle whether the map tracks to the heading the user is facing.

`class MKUserTrackingBarButtonItem`

A specialized bar button item that allows the user to toggle whether the map tracks to the heading the user is facing.

---

# https://developer.apple.com/documentation/mapkit/mkscaleview

- MapKit
- MKScaleView

Class

# MKScaleView

A specialized view that displays the scale information for its associated map.

@MainActor
class MKScaleView

## Overview

Use this class when you want to incorporate a standard scale view into your own view hierarchy. A scale view displays a legend with distance information for its associated map view. As the map region changes, the scale view updates automatically to reflect any changes in scale.

## Topics

### Creating a scale view

`convenience init(mapView: MKMapView?)`

Creates a scale view and associates it with the specified map view.

### Getting the scale view attributes

`var mapView: MKMapView?`

The map view that provides the scale information to the scale view.

`var scaleVisibility: MKFeatureVisibility`

The visibility of the scale view.

`var legendAlignment: MKScaleView.Alignment`

The alignment of the distance information in the scale view.

`enum Alignment`

Constants that indicate how the framework should align measurements.

## Relationships

### Inherits From

- `UIView`

### Conforms To

- `CALayerDelegate`
- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSCoding`
- `NSObjectProtocol`
- `NSTouchBarProvider`
- `Sendable`
- `SendableMetatype`
- `UIAccessibilityIdentification`
- `UIActivityItemsConfigurationProviding`
- `UIAppearance`
- `UIAppearanceContainer`
- `UICoordinateSpace`
- `UIDynamicItem`
- `UIFocusEnvironment`
- `UIFocusItem`
- `UIFocusItemContainer`
- `UILargeContentViewerItem`
- `UIPasteConfigurationSupporting`
- `UIPopoverPresentationControllerSourceItem`
- `UIResponderStandardEditActions`
- `UITraitChangeObservable`
- `UITraitEnvironment`
- `UIUserActivityRestoring`

## See Also

### Map customization

`class MKMapCamera`

A virtual camera for defining the appearance of the map.

`class MKCompassButton`

A specialized view that displays the compass heading for its associated map.

`class MKZoomControl`

A specialized view that displays and controls the zoom level of the map view.

`class MKPitchControl`

A specialized view that displays and controls the pitch angle of the map view.

`class MKUserTrackingButton`

A specialized button that allows the user to toggle whether the map tracks to the heading the user is facing.

`class MKUserTrackingBarButtonItem`

A specialized bar button item that allows the user to toggle whether the map tracks to the heading the user is facing.

---

# https://developer.apple.com/documentation/mapkit/mkzoomcontrol

- MapKit
- MKZoomControl

Class

# MKZoomControl

A specialized view that displays and controls the zoom level of the map view.

@MainActor
class MKZoomControl

## Overview

Use this class when you want to incorporate a standard, fixed-size zoom control into your own view hierarchy. A zoom control enables the user to change the zoom level of its associated map view.

## Topics

### Creating a zoom control

`convenience init(mapView: MKMapView?)`

Creates a zoom control and associates it with the specified map view.

### Accessing the map view

`var mapView: MKMapView?`

The map view associated with this control.

## Relationships

### Inherits From

- `NSView`
- `UIView`

### Conforms To

- `CALayerDelegate`
- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSAccessibilityElementProtocol`
- `NSAccessibilityProtocol`
- `NSAnimatablePropertyContainer`
- `NSAppearanceCustomization`
- `NSCoding`
- `NSDraggingDestination`
- `NSObjectProtocol`
- `NSStandardKeyBindingResponding`
- `NSTouchBarProvider`
- `NSUserActivityRestoring`
- `NSUserInterfaceItemIdentification`
- `Sendable`
- `SendableMetatype`
- `UIAccessibilityIdentification`
- `UIActivityItemsConfigurationProviding`
- `UIAppearance`
- `UIAppearanceContainer`
- `UICoordinateSpace`
- `UIDynamicItem`
- `UIFocusEnvironment`
- `UIFocusItem`
- `UIFocusItemContainer`
- `UILargeContentViewerItem`
- `UIPasteConfigurationSupporting`
- `UIPopoverPresentationControllerSourceItem`
- `UIResponderStandardEditActions`
- `UITraitChangeObservable`
- `UITraitEnvironment`
- `UIUserActivityRestoring`

## See Also

### Map customization

`class MKMapCamera`

A virtual camera for defining the appearance of the map.

`class MKCompassButton`

A specialized view that displays the compass heading for its associated map.

`class MKScaleView`

A specialized view that displays the scale information for its associated map.

`class MKPitchControl`

A specialized view that displays and controls the pitch angle of the map view.

`class MKUserTrackingButton`

A specialized button that allows the user to toggle whether the map tracks to the heading the user is facing.

`class MKUserTrackingBarButtonItem`

A specialized bar button item that allows the user to toggle whether the map tracks to the heading the user is facing.

---

# https://developer.apple.com/documentation/mapkit/mkpitchcontrol

- MapKit
- MKPitchControl

Class

# MKPitchControl

A specialized view that displays and controls the pitch angle of the map view.

@MainActor
class MKPitchControl

## Overview

Use this class when you want to incorporate a standard, fixed-size pitch control into your own view hierarchy. A pitch control allows the user to change the pitch angle of its associated map view.

## Topics

### Creating a pitch control

`convenience init(mapView: MKMapView?)`

Creates a pitch control and associates it with the specified map view.

### Accessing the map view

`var mapView: MKMapView?`

The map view associated with this control.

## Relationships

### Inherits From

- `NSView`
- `UIView`

### Conforms To

- `CALayerDelegate`
- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSAccessibilityElementProtocol`
- `NSAccessibilityProtocol`
- `NSAnimatablePropertyContainer`
- `NSAppearanceCustomization`
- `NSCoding`
- `NSDraggingDestination`
- `NSObjectProtocol`
- `NSStandardKeyBindingResponding`
- `NSTouchBarProvider`
- `NSUserActivityRestoring`
- `NSUserInterfaceItemIdentification`
- `Sendable`
- `SendableMetatype`
- `UIAccessibilityIdentification`
- `UIActivityItemsConfigurationProviding`
- `UIAppearance`
- `UIAppearanceContainer`
- `UICoordinateSpace`
- `UIDynamicItem`
- `UIFocusEnvironment`
- `UIFocusItem`
- `UIFocusItemContainer`
- `UILargeContentViewerItem`
- `UIPasteConfigurationSupporting`
- `UIPopoverPresentationControllerSourceItem`
- `UIResponderStandardEditActions`
- `UITraitChangeObservable`
- `UITraitEnvironment`
- `UIUserActivityRestoring`

## See Also

### Map customization

`class MKMapCamera`

A virtual camera for defining the appearance of the map.

`class MKCompassButton`

A specialized view that displays the compass heading for its associated map.

`class MKScaleView`

A specialized view that displays the scale information for its associated map.

`class MKZoomControl`

A specialized view that displays and controls the zoom level of the map view.

`class MKUserTrackingButton`

A specialized button that allows the user to toggle whether the map tracks to the heading the user is facing.

`class MKUserTrackingBarButtonItem`

A specialized bar button item that allows the user to toggle whether the map tracks to the heading the user is facing.

---

# https://developer.apple.com/documentation/mapkit/mkusertrackingbutton

- MapKit
- MKUserTrackingButton

Class

# MKUserTrackingButton

A specialized button that allows the user to toggle whether the map tracks to the heading the user is facing.

@MainActor
class MKUserTrackingButton

## Overview

Use this class when you need a standard button that you can incorporate into your view hierarchy. Tapping the button lets the user toggles between modes for displaying the map with and without the current heading applied. The button also reflects the current user tracking mode if set elsewhere.

## Topics

### Creating a user tracking button

`convenience init(mapView: MKMapView?)`

Initializes the button with the map view that it should control.

### Getting the parent map

`var mapView: MKMapView?`

The map view associated with the button.

## Relationships

### Inherits From

- `UIView`

### Conforms To

- `CALayerDelegate`
- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSCoding`
- `NSObjectProtocol`
- `NSTouchBarProvider`
- `Sendable`
- `SendableMetatype`
- `UIAccessibilityIdentification`
- `UIActivityItemsConfigurationProviding`
- `UIAppearance`
- `UIAppearanceContainer`
- `UICoordinateSpace`
- `UIDynamicItem`
- `UIFocusEnvironment`
- `UIFocusItem`
- `UIFocusItemContainer`
- `UILargeContentViewerItem`
- `UIPasteConfigurationSupporting`
- `UIPopoverPresentationControllerSourceItem`
- `UIResponderStandardEditActions`
- `UITraitChangeObservable`
- `UITraitEnvironment`
- `UIUserActivityRestoring`

## See Also

### Map customization

`class MKMapCamera`

A virtual camera for defining the appearance of the map.

`class MKCompassButton`

A specialized view that displays the compass heading for its associated map.

`class MKScaleView`

A specialized view that displays the scale information for its associated map.

`class MKZoomControl`

A specialized view that displays and controls the zoom level of the map view.

`class MKPitchControl`

A specialized view that displays and controls the pitch angle of the map view.

`class MKUserTrackingBarButtonItem`

A specialized bar button item that allows the user to toggle whether the map tracks to the heading the user is facing.

---

# https://developer.apple.com/documentation/mapkit/mkusertrackingbarbuttonitem

- MapKit
- MKUserTrackingBarButtonItem

Class

# MKUserTrackingBarButtonItem

A specialized bar button item that allows the user to toggle whether the map tracks to the heading the user is facing.

@MainActor
class MKUserTrackingBarButtonItem

## Overview

Tapping the button lets the user toggles between modes for displaying the map with and without the current heading applied. The button also reflects the current user tracking mode if set elsewhere. This bar button item is associated to a single map view.

## Topics

### Creating a user tracking bar button item

`init(mapView: MKMapView?)`

Initializes a newly created bar button item with the specified map view.

### Accessing the owning map

`var mapView: MKMapView?`

The map view associated with this bar button item.

## Relationships

### Inherits From

- `UIBarButtonItem`

### Conforms To

- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSCoding`
- `NSObjectProtocol`
- `UIAccessibilityIdentification`
- `UIAppearance`
- `UIPopoverPresentationControllerSourceItem`
- `UISpringLoadedInteractionSupporting`

## See Also

### Map customization

`class MKMapCamera`

A virtual camera for defining the appearance of the map.

`class MKCompassButton`

A specialized view that displays the compass heading for its associated map.

`class MKScaleView`

A specialized view that displays the scale information for its associated map.

`class MKZoomControl`

A specialized view that displays and controls the zoom level of the map view.

`class MKPitchControl`

A specialized view that displays and controls the pitch angle of the map view.

`class MKUserTrackingButton`

A specialized button that allows the user to toggle whether the map tracks to the heading the user is facing.

---

# https://developer.apple.com/documentation/mapkit/mapkit-annotations

Collection

- MapKit
- MapKit for AppKit and UIKit
- MapKit annotations

API Collection

# MapKit annotations

Create annotations to add indicators and additional details for specific locations on a map.

## Topics

### Location annotations

Annotating a Map with Custom Data

Annotate a map with location-specific data using default and customized annotation views and callouts.

`class MKPointAnnotation`

A string-based piece of location-specific data that you apply to a specific point on a map.

`class MKMapItemAnnotation`

An annotation that represents a map item

`class MKMarkerAnnotationView`

An annotation view that displays a balloon-shaped marker at the designated location.

`class MKPinAnnotationView`

An annotation view that displays a pin image on the map.

Deprecated

### Grouped annotations

Decluttering a Map with MapKit Annotation Clustering

Enhance the readability of a map by replacing overlapping annotations with a clustering annotation view.

`class MKClusterAnnotation`

An annotation that groups two or more distinct annotations into a single entity.

### User location

Converting a user’s location to a descriptive placemark

Transform the user’s location that displays on a map into an informative textual description by reverse geocoding.

`class MKUserLocation`

An annotation that reflects the user’s location on the map.

`class MKUserLocationView`

A configurable annotation that shows the user’s location using the default MapKit style.

### Annotations in SwiftUI

`struct MapMarker`

A balloon-shaped annotation used to indicate the location on a map.

`struct MapPin`

A pin-shaped annotation used to indicate a location on a map.

`struct MapAnnotation`

A customizable annotation that marks a map location.

`protocol MapAnnotationProtocol`

A protocol that represents the possible return types of annotations.

### Shared behavior

`class MKPlacemark`

A user-friendly description of a location on the map.

`protocol MKAnnotation`

An interface for associating your content with a specific map location.

`class MKAnnotationView`

The visual representation of one of your annotation objects.

## See Also

### Annotations and overlays

Create overlays to highlight geographic regions or paths.

---

# https://developer.apple.com/documentation/mapkit/mapkit-overlays

Collection

- MapKit
- MapKit for AppKit and UIKit
- MapKit overlays

API Collection

# MapKit overlays

Create overlays to highlight geographic regions or paths.

## Topics

### Samples

Displaying overlays on a map

Add regions of layered content to a map view.

Displaying an updating path of a user’s location history

Continually update a MapKit overlay displaying the path a user travels.

### Circular overlays

`class MKCircle`

A circular overlay with a configurable radius that you center on a geographic coordinate.

`class MKCircleRenderer`

The visual representation of a circular overlay.

### Custom shape overlays

`class MKPolygon`

A closed polygon overlay.

`class MKPolygonRenderer`

The visual representation of a single polygon overlay.

`class MKMultiPolygon`

A collection of multiple closed polygon overlays.

`class MKMultiPolygonRenderer`

The visual representation of multiple polygon overlays.

`class MKOverlayPathRenderer`

The visual representation of a path-based overlay.

### Multiple segment lines

`class MKPolyline`

An open polygon overlay consisting of one or more connected line segments.

`class MKGeodesicPolyline`

An open polygon overlay consisting of line segments that follow the contours of the Earth to create the shortest path between the specified points.

`class MKMultiPolyline`

A collection of multipolyline shapes, each consisting of one or more connected line segments.

`class MKPolylineRenderer`

A visual representation of any polyline overlay object.

`class MKMultiPolylineRenderer`

A visual representation of multiple polyline overlay objects.

`class MKGradientPolylineRenderer`

A visual representation of any polyline overlay object with a gradient.

### Tiled image overlays

`class MKTileOverlay`

An overlay that covers an area of the map with tiles of bitmap images.

`class MKTileOverlayRenderer`

The renderer for a tile overlay that handles the drawing of bitmap images on the map surface.

### Shared behavior

`protocol MKOverlay`

An interface for associating content with a specific map region.

`class MKOverlayRenderer`

The shared infrastructure for drawing overlays on the map surface.

`class MKShape`

An abstract class that defines the basic properties for all shape-based overlay objects.

`class MKMultiPoint`

An abstract class that defines the common behavior that open and closed polygon overlays share.

`class MKPlacemark`

A user-friendly description of a location on the map.

Deprecated

## See Also

### Annotations and overlays

Create annotations to add indicators and additional details for specific locations on a map.

---

# https://developer.apple.com/documentation/mapkit/mkdirections

- MapKit
- MKDirections

Class

# MKDirections

A utility object that computes directions and travel-time information based on the route information you provide.

class MKDirections

## Mentioned in

Enabling Maps capability in Xcode

## Overview

You use an `MKDirections` object to ask the Apple servers to provide walking or driving directions for a route, which you specify using an `MKDirections.Request` object. After making a request, MapKit delivers the results asynchronously to the completion handler that you provide. You can also get the estimated travel time for the route.

Each `MKDirections` object handles a single request for directions, although you can cancel and restart that request as needed. You can create multiple instances of this class and process different route requests at the same time, but make requests only when you plan to present the corresponding route information to the user. Apps may receive an `MKError.Code.loadingThrottled` error if the device makes too many requests in too short a time period.

## Topics

### Creating a directions object

`init(request: MKDirections.Request)`

Creates and returns a directions object using the specified request.

`class Request`

The start and end points of a route, along with the planned mode of transportation.

`enum RoutePreference`

Options that modify how the framework selects routes when calculating directions.

### Getting the directions

Begins calculating the requested route information asynchronously.

`typealias DirectionsHandler`

The block to use for processing the requested route information.

`class Response`

The route information that Apple servers return in response to your request for directions.

### Getting the ETA

Begins calculating the requested travel-time information asynchronously.

`typealias ETAHandler`

The block to use for processing travel-time information.

`class ETAResponse`

The travel-time information that Apple servers return.

### Managing the request

`func cancel()`

Cancels a pending request.

`var isCalculating: Bool`

A Boolean value that indicates whether a request is in process.

## Relationships

### Inherits From

- `NSObject`

### Conforms To

- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSObjectProtocol`

## See Also

### Directions

`class MKRoute`

A single route between a requested start and end point.

`class Step`

One portion of an overall route.

---

# https://developer.apple.com/documentation/mapkit/mkdirections/request

- MapKit
- MKDirections
- MKDirections.Request

Class

# MKDirections.Request

The start and end points of a route, along with the planned mode of transportation.

class Request

## Overview

You use an `MKDirections.Request` object when requesting or providing directions. If your app provides directions, use this class to decode the URL that the Maps app sends to you. If you need to request directions from Apple, pass an instance of this class to an `MKDirections` object. For example, an app that provides subway directions might request walking directions to and from relevant subway stations.

Prior to iOS 14, for apps that provide directions, you receive direction-related URLs in your app delegate’s `application(_:open:options:)` method. Upon receiving a URL, call the `isDirectionsRequest(_:)` method of this class to determine whether the URL relates to routing directions. If it does, create an instance of this class using the provided URL and extract the map items associated with the start and end points.

## Topics

### Creating a directions request object

Returns a Boolean value that indicates whether the specified URL contains a directions request.

`init(contentsOfURL: URL)`

Creates and returns a directions request object using the specified URL.

### Accessing the start and end points

`var source: MKMapItem?`

The starting point for routing directions.

`var destination: MKMapItem?`

The end point for routing directions.

### Specifying transportation options

`var transportType: MKDirectionsTransportType`

The type of conveyance that the directions apply to.

`var highwayPreference: MKDirections.RoutePreference`

The value that indicates whether the framework uses or avoids highways when providing directions.

`var tollPreference: MKDirections.RoutePreference`

The value that indicates whether the framework avoids routes that have tolls when providing directions.

`enum RoutePreference`

Options that modify how the framework selects routes when calculating directions.

`var requestsAlternateRoutes: Bool`

A Boolean value that indicates whether your app requests multiple routes when they’re available.

`var departureDate: Date?`

The departure date for the trip.

`var arrivalDate: Date?`

The arrival date for the trip.

### Constants

`struct MKDirectionsTransportType`

Constants that specify the type of conveyance to use.

### Launch options

`let MKLaunchOptionsCameraKey: String`

The virtual camera to use for viewing the map.

`let MKLaunchOptionsDirectionsModeCycling: String`

Cycling directions between the specified start and end points.

`let MKLaunchOptionsDirectionsModeDefault: String`

Directions that match the user’s preferred transportation type.

`let MKLaunchOptionsDirectionsModeDriving: String`

Driving directions between the specified start and end points.

`let MKLaunchOptionsDirectionsModeKey: String`

The mode of transportation.

`let MKLaunchOptionsDirectionsModeTransit: String`

Public transit directions between the specified start and end points.

`let MKLaunchOptionsDirectionsModeWalking: String`

Walking directions between the specified start and end points.

`let MKLaunchOptionsMapCenterKey: String`

The coordinate value on which to center the map.

`let MKLaunchOptionsMapSpanKey: String`

The amount of the map to display.

`let MKLaunchOptionsMapTypeKey: String`

The type of map (standard, satellite, or hybrid) to display.

`let MKLaunchOptionsShowsTrafficKey: String`

A Boolean value that indicates whether to display traffic information.

## Relationships

### Inherits From

- `NSObject`

### Conforms To

- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSObjectProtocol`

## See Also

### Directions

`class MKDirections`

A utility object that computes directions and travel-time information based on the route information you provide.

`class Response`

The route information that Apple servers return in response to your request for directions.

`class ETAResponse`

The travel-time information that Apple servers return.

`class MKRoute`

A single route between a requested start and end point.

`class Step`

One portion of an overall route.

---

# https://developer.apple.com/documentation/mapkit/mkdirections/response

- MapKit
- MKDirections
- MKDirections.Response

Class

# MKDirections.Response

The route information that Apple servers return in response to your request for directions.

class Response

## Overview

You don’t create instances of this class directly. Instead, you initiate a request for directions by calling the `calculate(completionHandler:)` method of an `MKDirections` object. The completion handler you pass to that method receives an `MKDirections.Response` object with the results.

## Topics

### Getting the end points

`var source: MKMapItem`

The start point of the route.

`var destination: MKMapItem`

The end point of the route.

### Getting the route information

[`var routes: [MKRoute]`](https://developer.apple.com/documentation/mapkit/mkdirections/response/routes)

An array of route objects representing the directions between the start and end points.

## Relationships

### Inherits From

- `NSObject`

### Conforms To

- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSObjectProtocol`

## See Also

### Directions

`class MKDirections`

A utility object that computes directions and travel-time information based on the route information you provide.

`class Request`

The start and end points of a route, along with the planned mode of transportation.

`class ETAResponse`

The travel-time information that Apple servers return.

`class MKRoute`

A single route between a requested start and end point.

`class Step`

One portion of an overall route.

---

# https://developer.apple.com/documentation/mapkit/mkdirections/etaresponse

- MapKit
- MKDirections
- MKDirections.ETAResponse

Class

# MKDirections.ETAResponse

The travel-time information that Apple servers return.

class ETAResponse

## Overview

You don’t create instances of this class directly. Instead, you initiate a request for the travel time by calling the `calculateETA(completionHandler:)` method of an `MKDirections` object. The completion handler you pass to that method receives an `MKDirections.ETAResponse` object with the results.

## Topics

### Getting the end points

`var source: MKMapItem`

The start point of the route.

`var destination: MKMapItem`

The end point of the route.

### Getting the travel information

`var expectedTravelTime: TimeInterval`

The expected travel time, in seconds.

`var expectedDepartureDate: Date`

The expected departure time.

`var expectedArrivalDate: Date`

The expected arrival time.

`var distance: CLLocationDistance`

The expected travel distance, in meters.

`var transportType: MKDirectionsTransportType`

The type of conveyance to use for determining the travel time.

## Relationships

### Inherits From

- `NSObject`

### Conforms To

- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSObjectProtocol`

## See Also

### Directions

`class MKDirections`

A utility object that computes directions and travel-time information based on the route information you provide.

`class Request`

The start and end points of a route, along with the planned mode of transportation.

`class Response`

The route information that Apple servers return in response to your request for directions.

`class MKRoute`

A single route between a requested start and end point.

`class Step`

One portion of an overall route.

---

# https://developer.apple.com/documentation/mapkit/mkroute

- MapKit
- MKRoute

Class

# MKRoute

A single route between a requested start and end point.

class MKRoute

## Overview

An `MKRoute` object defines the geometry for the route — that is, it contains line segments associated with specific map coordinates. A route object may also include other information, such as the name of the route, its distance, and the expected travel time.

You don’t create instances of this class directly. When you use an `MKDirections` object to request directions from Apple, the returned `MKDirections.Response` object contains the possible routes.

## Topics

### Getting the route geometry

`var polyline: MKPolyline`

The detailed route geometry.

[`var steps: [MKRoute.Step]`](https://developer.apple.com/documentation/mapkit/mkroute/steps)

The array of steps that create the overall route.

`class Step`

One portion of an overall route.

### Getting additional route details

`var name: String`

The assigned name for the route.

`var hasHighways: Bool`

A Boolean value that indicates whether the route contains highways.

`var hasTolls: Bool`

A Boolean value that indicates whether the route has tolls.

[`var advisoryNotices: [String]`](https://developer.apple.com/documentation/mapkit/mkroute/advisorynotices)

An array of advisory notice strings for the route.

`var distance: CLLocationDistance`

The route distance, in meters.

`var expectedTravelTime: TimeInterval`

The expected travel time, in seconds.

`var transportType: MKDirectionsTransportType`

The overall route transport type.

## Relationships

### Inherits From

- `NSObject`

### Conforms To

- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSObjectProtocol`

## See Also

### Directions

`class MKDirections`

A utility object that computes directions and travel-time information based on the route information you provide.

`class Request`

The start and end points of a route, along with the planned mode of transportation.

`class Response`

The route information that Apple servers return in response to your request for directions.

`class ETAResponse`

The travel-time information that Apple servers return.

---

# https://developer.apple.com/documentation/mapkit/mkroute/step

- MapKit
- MKRoute
- MKRoute.Step

Class

# MKRoute.Step

One portion of an overall route.

class Step

## Overview

Each `MKRoute.Step` object corresponds to a single instruction that the person needs to follow when navigating between two points. For example, a step might involve following a single road until continuing along the route requires a turn.

You don’t create instances of this class directly. An `MKRoute` object contains the `MKRoute.Step` objects associated with a route. For more information about requesting directions, see `MKDirections`.

## Topics

### Getting the step geometry

`var polyline: MKPolyline`

The detailed step geometry.

### Getting additional step details

`var instructions: String`

The written instructions for following the path that the step represents.

`var notice: String?`

Additional notices that apply to the step.

`var distance: CLLocationDistance`

The step distance, in meters.

`var transportType: MKDirectionsTransportType`

The transport type of the step.

## Relationships

### Inherits From

- `NSObject`

### Conforms To

- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSObjectProtocol`

## See Also

### Directions

`class MKDirections`

A utility object that computes directions and travel-time information based on the route information you provide.

`class Request`

The start and end points of a route, along with the planned mode of transportation.

`class Response`

The route information that Apple servers return in response to your request for directions.

`class ETAResponse`

The travel-time information that Apple servers return.

`class MKRoute`

A single route between a requested start and end point.

---

# https://developer.apple.com/documentation/mapkit/displaying-an-indoor-map

- MapKit
- MapKit for AppKit and UIKit
- Displaying an Indoor Map

Sample Code

# Displaying an Indoor Map

Use the Indoor Mapping Data Format (IMDF) to show an indoor map with custom overlays and points of interest.

Download

Xcode 16.0+

## Overview

The sample app demonstrates decoding, rendering, and styling of a small subset of the IMDF feature types and their properties. Use these examples to create your own indoor map with a style that’s consistent with your app’s design. You’ll need to handle feature categories that are specific to your venue, and configure the map style using your own colors, icons, and level picker.

## See Also

### Geographical features

`class MKGeoJSONDecoder`

An object that decodes GeoJSON objects into MapKit types.

`class MKGeoJSONFeature`

The decoded representation of a GeoJSON feature.

`protocol MKGeoJSONObject`

Objects that the GeoJSON decoder can return.

---

# https://developer.apple.com/documentation/mapkit/mkgeojsondecoder

- MapKit
- MKGeoJSONDecoder

Class

# MKGeoJSONDecoder

An object that decodes GeoJSON objects into MapKit types.

class MKGeoJSONDecoder

## Overview

The GeoJSON decoder returns objects that conform to the `MKGeoJSONObject` protocol.

## Topics

### Decoding GeoJSON objects

Decodes the provided data into native MapKit types that a map can display.

## Relationships

### Inherits From

- `NSObject`

### Conforms To

- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSObjectProtocol`

## See Also

### Geographical features

Displaying an Indoor Map

Use the Indoor Mapping Data Format (IMDF) to show an indoor map with custom overlays and points of interest.

`class MKGeoJSONFeature`

The decoded representation of a GeoJSON feature.

`protocol MKGeoJSONObject`

Objects that the GeoJSON decoder can return.

---

# https://developer.apple.com/documentation/mapkit/mkgeojsonfeature

- MapKit
- MKGeoJSONFeature

Class

# MKGeoJSONFeature

The decoded representation of a GeoJSON feature.

class MKGeoJSONFeature

## Overview

A feature is an object with associated geometry and optional properties in JSON that you define. MapKit exposes these optional properties, but treats them as opaque. `MKGeoJSONFeature` is one of the classes that the GeoJSON decoder ( `MKGeoJSONDecoder`) can return.

See the GeoJSON standards specification RFC 7946 for more information about `Feature` objects.

## Topics

### Feature properties

[`var geometry: [any MKShape & MKGeoJSONObject]`](https://developer.apple.com/documentation/mapkit/mkgeojsonfeature/geometry)

The shape or shapes associated with the GeoJSON feature.

`var identifier: String?`

An optional identifier the class returns as a string.

`var properties: Data?`

Optional serialized JSON data that corresponds to the properties key.

## Relationships

### Inherits From

- `NSObject`

### Conforms To

- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `MKGeoJSONObject`
- `NSObjectProtocol`

## See Also

### Geographical features

Displaying an Indoor Map

Use the Indoor Mapping Data Format (IMDF) to show an indoor map with custom overlays and points of interest.

`class MKGeoJSONDecoder`

An object that decodes GeoJSON objects into MapKit types.

`protocol MKGeoJSONObject`

Objects that the GeoJSON decoder can return.

---

# https://developer.apple.com/documentation/mapkit/mkgeojsonobject

- MapKit
- MKGeoJSONObject

Protocol

# MKGeoJSONObject

Objects that the GeoJSON decoder can return.

protocol MKGeoJSONObject : NSObjectProtocol

## Overview

Classes that conform to this protocol represent the types that the GeoJSON decoder can return.

There’s no reason to create your own classes that conform to this protocol; only MapKit can define classes that the GeoJSON decoder uses.

## Relationships

### Inherits From

- `NSObjectProtocol`

### Conforming Types

- `MKGeoJSONFeature`
- `MKGeodesicPolyline`
- `MKMultiPoint`
- `MKMultiPolygon`
- `MKMultiPolyline`
- `MKPointAnnotation`
- `MKPolygon`
- `MKPolyline`

## See Also

### Geographical features

Displaying an Indoor Map

Use the Indoor Mapping Data Format (IMDF) to show an indoor map with custom overlays and points of interest.

`class MKGeoJSONDecoder`

An object that decodes GeoJSON objects into MapKit types.

`class MKGeoJSONFeature`

The decoded representation of a GeoJSON feature.

---

# https://developer.apple.com/documentation/mapkit/interacting-with-nearby-points-of-interest

- MapKit
- MapKit for AppKit and UIKit
- Interacting with nearby points of interest

Sample Code

# Interacting with nearby points of interest

Provide automatic search completions for a partial search query, search the map for relevant locations nearby, and retrieve details for selected points of interest.

Download

Xcode 16.2+

## Overview

This sample code project demonstrates how to programmatically search for map-based addresses and points of interest using a natural language string, and how to get more information about points of interest that a person selects on the map. The search results center around the locations visible in the map view.

### Request search completions

`MKLocalSearchCompleter` retrieves autocomplete suggestions for a partial search query within a map region. A person can type “cof”, and a search completion suggests “coffee” as the query string. As the person types a query into a search bar, the sample app updates the query. In SwiftUI, the sample creates the search field using the `searchable(text:placement:prompt:)` modifier.

.searchable(text: $searchQuery, placement: .navigationBarDrawer(displayMode: .always), prompt: searchPrompt)

As someone types a query into a search bar, the sample app updates the `queryFragment` for the search completion through the `searchQuery` binding.

/// Ask for completion suggestions based on the query text.
func provideCompletionSuggestions(for query: String) {
/**
Configure the search to return completion results based only on the options in the app. For example,
someone can configure the app to exclude specific point-of-interest categories, or to only return results for addresses.
*/
searchCompleter?.resultTypes = mapConfiguration.resultType.completionResultType
searchCompleter?.regionPriority = mapConfiguration.regionPriority.localSearchRegionPriority
if mapConfiguration.resultType == .pointsOfInterest {
searchCompleter?.pointOfInterestFilter = mapConfiguration.pointOfInterestOptions.filter
} else if mapConfiguration.resultType == .addresses {
searchCompleter?.addressFilter = mapConfiguration.addressOptions.filter
}

searchCompleter?.region = mapConfiguration.region
searchCompleter?.queryFragment = query
}

### Receive completion results

Completion results represent fully formed query strings based on the query fragment someone types. The sample app uses completion results to populate UI elements to quickly fill in a search query. The app receives the latest completion results as an array of `MKLocalSearchCompletion` objects by adopting the `MKLocalSearchCompleterDelegate` protocol.

nonisolated func completerDidUpdateResults(_ completer: MKLocalSearchCompleter) {
Task { @MainActor in
/**
As a person types, new completion suggestions continuously to deliver the completion results to the UI, which the `SidebarView` stores in its `searchCompletions` property. The app displays the search suggestions with the `searchSuggestions(_:)` modifier, which takes a binding to the `searchCompletions` property.

.searchSuggestions {
// Treat each `MKMapItem` object as unique, using `\.self` for the identity. The `identifier` property of `MKMapItem`
// is an optional value, and the meaning of the identifier for `MKMapItem` doesn't have the same semantics as
// the `Identifable` protocol that `ForEach` requires.
ForEach($searchCompletions, id: \.self) { completion in
SearchCompletionItemView(completion: completion.wrappedValue)
.onTapGesture {
convertSearchCompletionToSearchResults(completion.wrappedValue)
}
}
}

### Highlight the relationship of a query fragment to the suggestion

Within the UI elements that represent each query result, the sample code uses the `titleHighlightRanges` on an `MKLocalSearchCompletion` to show how the query someone enters relates to the suggested result. For example, the following code applies a highlight with `NSAttributedString`:

let attributes = [NSAttributedString.Key.backgroundColor: UIColor(named: "suggestionHighlight")!]
let highlightedString = NSMutableAttributedString(string: text)

// Each `NSValue` wraps an `NSRange` that functions as a style attribute's range with `NSAttributedString`.
let ranges = rangeValues.map { $0.rangeValue }
for range in ranges {
highlightedString.addAttributes(attributes, range: range)
}

return highlightedString
}

### Search for map items

An `MKLocalSearch.Request` takes either an `MKLocalSearchCompletion` or a natural language query string, and returns an array of `MKMapItem` objects. Each `MKMapItem` represents a geographic location, like a specific address, that matches the search query. The sample code asynchronously retrieves the array of `MKMapItem` objects by calling `start(completionHandler:)` on `MKLocalSearch`.

let search = MKLocalSearch(request: request)
currentSearch = search
defer {
// After the search completes, the reference is no longer needed.
currentSearch = nil
}

var results: [MKMapItem]

do {
let response = try await search.start()
results = response.mapItems
} catch let error {
searchLogging.error("Search error: \(error.localizedDescription)")
results = []
}

### Allow someone to select points of interest on the map

If a person is exploring the map, they can get information for a point of interest by tapping it. To provide these interactions, the sample code enables selectable map features as follows:

// Use the standard map style, with an option to display specific point-of-interest categories.
.mapStyle(.standard(pointsOfInterest: mapModel.searchConfiguration.pointOfInterestOptions.categories))

// Only allow selection for points of interest, and disable selection of other labels, like city names.
.mapFeatureSelectionDisabled { feature in
feature.kind != MapFeature.FeatureKind.pointOfInterest
}

/*
The selection accessory allows people to tap on map features and get more detailed information, which displays
as either a sheet or a callout according to the `style` parameter. Along with the `selection` binding, this determines
which feature to display additional information for.

This modifier differs from the `mapItemDetailSelectionAccessory(:_) modifier, which enables the same selection
behaviors on annotations that the app adds to `Map` for search results.
*/
.mapFeatureSelectionAccessory(.automatic)

When someone taps a point of interest, the system presents the map item’s details, including information like a phone number, business hours, and buttons to start navigation to the location using Apple Maps. The system presents the information using the style that the `mapFeatureSelectionAccessory(_:)` modifier configures. The sample app uses the `automatic` style, but the `MapItemDetailSelectionAccessoryStyle` structure offers several other options.

### Persist and retrieve map items

If someone is exploring the map, they may want the app to store places they looked at so that they can come property, which the app stores in its `VisitedPlace` model using `SwiftData`.

guard let identifier = mapItem.identifier else { return }
let visit = VisitedPlace(id: identifier.rawValue)

When the app launches, it retrieves the history of visited locations from SwiftData. To get the `MKMapItem` from the previously stored identifier, the app creates an `MKMapItemRequest` with the stored identifier and calls `getMapItem(completionHandler:)`.

@MainActor

guard let identifier = MKMapItem.Identifier(rawValue: id) else { return nil }
let request = MKMapItemRequest(mapItemIdentifier: identifier)
var mapItem: MKMapItem? = nil
do {
mapItem = try await request.mapItem
} catch let error {
let logger = Logger(subsystem: Bundle.main.bundleIdentifier!, category: "Map Item Requests")
logger.error("Getting map item from identifier failed. Error: \(error.localizedDescription)")
}
return mapItem
}

## See Also

### Local search

`enum MKLocalSearchRegionPriority`

A value that indicates the importance of the configured region.

`struct ResultType`

Options that indicate types of search results.

`class MKLocalSearch`

A utility object for initiating map-based searches and processing the results.

`struct Options`

A structure that contains options for filtering results in a search.

`class MKAddressFilter`

An object that filters which address options to include or exclude in search results.

Options that indicate types of search completions.

`class MKLocalSearchCompleter`

A utility object for generating a list of completion strings based on a partial search string that you provide.

`class MKLocalSearchCompletion`

A fully formed string that completes a partial string.

`class MKLocalPointsOfInterestRequest`

A structured request to use when searching for points of interest.

---

# https://developer.apple.com/documentation/mapkit/mklocalsearchregionpriority

- MapKit
- MKLocalSearchRegionPriority

Enumeration

# MKLocalSearchRegionPriority

A value that indicates the importance of the configured region.

enum MKLocalSearchRegionPriority

## Topics

### Setting region priority

``case `default```

A value indicating that the results can originate from outside the specified region.

`case required`

A value indicating that no results can originate from outside the specified region.

### Initializers

`init?(rawValue: Int)`

## Relationships

### Conforms To

- `BitwiseCopyable`
- `Equatable`
- `Hashable`
- `RawRepresentable`
- `Sendable`
- `SendableMetatype`

## See Also

### Local search

Interacting with nearby points of interest

Provide automatic search completions for a partial search query, search the map for relevant locations nearby, and retrieve details for selected points of interest.

`struct ResultType`

Options that indicate types of search results.

`class MKLocalSearch`

A utility object for initiating map-based searches and processing the results.

`struct Options`

A structure that contains options for filtering results in a search.

`class MKAddressFilter`

An object that filters which address options to include or exclude in search results.

Options that indicate types of search completions.

`class MKLocalSearchCompleter`

A utility object for generating a list of completion strings based on a partial search string that you provide.

`class MKLocalSearchCompletion`

A fully formed string that completes a partial string.

`class MKLocalPointsOfInterestRequest`

A structured request to use when searching for points of interest.

---

# https://developer.apple.com/documentation/mapkit/mklocalsearch/resulttype

- MapKit
- MKLocalSearch
- MKLocalSearch.ResultType

Structure

# MKLocalSearch.ResultType

Options that indicate types of search results.

struct ResultType

## Overview

These options configure the types of search results you want to receive from `MKLocalSearch.Request`, including points of interest and addresses.

## Topics

### Creating the result type

`init(rawValue: UInt)`

Creates a search result type from the provided value.

### Specifying types of search results

`static var address: MKLocalSearch.ResultType`

A value that indicates that search results include addresses.

`static var pointOfInterest: MKLocalSearch.ResultType`

A value that indicates that search results include points of interest.

`static var physicalFeature: MKLocalSearch.ResultType`

A value that indicates that search results include physical features.

## Relationships

### Conforms To

- `BitwiseCopyable`
- `Equatable`
- `ExpressibleByArrayLiteral`
- `OptionSet`
- `RawRepresentable`
- `Sendable`
- `SendableMetatype`
- `SetAlgebra`

## See Also

### Local search

Interacting with nearby points of interest

Provide automatic search completions for a partial search query, search the map for relevant locations nearby, and retrieve details for selected points of interest.

`enum MKLocalSearchRegionPriority`

A value that indicates the importance of the configured region.

`class MKLocalSearch`

A utility object for initiating map-based searches and processing the results.

`struct Options`

A structure that contains options for filtering results in a search.

`class MKAddressFilter`

An object that filters which address options to include or exclude in search results.

`struct ResultType`

Options that indicate types of search completions.

`class MKLocalSearchCompleter`

A utility object for generating a list of completion strings based on a partial search string that you provide.

`class MKLocalSearchCompletion`

A fully formed string that completes a partial string.

`class MKLocalPointsOfInterestRequest`

A structured request to use when searching for points of interest.

---

# https://developer.apple.com/documentation/mapkit/mklocalsearch

- MapKit
- MKLocalSearch

Class

# MKLocalSearch

A utility object for initiating map-based searches and processing the results.

class MKLocalSearch

## Overview

Use an `MKLocalSearch` object to execute a single search request. You might use this class to search for addresses or points of interest on the map. Upon completion of the request, the object delivers the results to the completion handler that you provide.

## Topics

### Creating a search request

`init(request: MKLocalSearch.Request)`

Creates and returns a search object with the specified parameters.

`init(request: MKLocalPointsOfInterestRequest)`

Creates and returns a search object for fetching points of interest.

`class Request`

The parameters to use when searching for points of interest on the map.

`struct ResultType`

Options that indicate types of search results.

### Performing the search

Starts the search and delivers the results to the specified completion handler.

`typealias CompletionHandler`

A completion handler block for a search operation.

`var isSearching: Bool`

A Boolean value that indicates whether the search is in progress.

`func cancel()`

Cancels an in-progress search operation.

### Getting search results

`class Response`

The results from a map-based search.

## Relationships

### Inherits From

- `NSObject`

### Conforms To

- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSObjectProtocol`

## See Also

### Local search

Interacting with nearby points of interest

Provide automatic search completions for a partial search query, search the map for relevant locations nearby, and retrieve details for selected points of interest.

`enum MKLocalSearchRegionPriority`

A value that indicates the importance of the configured region.

`struct Options`

A structure that contains options for filtering results in a search.

`class MKAddressFilter`

An object that filters which address options to include or exclude in search results.

Options that indicate types of search completions.

`class MKLocalSearchCompleter`

A utility object for generating a list of completion strings based on a partial search string that you provide.

`class MKLocalSearchCompletion`

A fully formed string that completes a partial string.

`class MKLocalPointsOfInterestRequest`

A structured request to use when searching for points of interest.

---

# https://developer.apple.com/documentation/mapkit/mkaddressfilter/options

- MapKit
- MKAddressFilter
- MKAddressFilter.Options

Structure

# MKAddressFilter.Options

A structure that contains options for filtering results in a search.

struct Options

## Topics

### Creating a filter result

`init(rawValue: UInt)`

Creates a filter options object.

### Getting search filter options

`static var administrativeArea: MKAddressFilter.Options`

The primary administrative divisions of countries or regions.

`static var country: MKAddressFilter.Options`

Countries and regions.

`static var locality: MKAddressFilter.Options`

Local administrative divisions, postal cities, and populated places.

`static var postalCode: MKAddressFilter.Options`

An address code for mail sorting and delivery.

`static var subAdministrativeArea: MKAddressFilter.Options`

The secondary administrative divisions of countries or regions.

`static var subLocality: MKAddressFilter.Options`

Local administrative subdivisions, postal city subdistricts, and neighborhoods.

## Relationships

### Conforms To

- `BitwiseCopyable`
- `Equatable`
- `ExpressibleByArrayLiteral`
- `OptionSet`
- `RawRepresentable`
- `Sendable`
- `SendableMetatype`
- `SetAlgebra`

## See Also

### Local search

Interacting with nearby points of interest

Provide automatic search completions for a partial search query, search the map for relevant locations nearby, and retrieve details for selected points of interest.

`enum MKLocalSearchRegionPriority`

A value that indicates the importance of the configured region.

`struct ResultType`

Options that indicate types of search results.

`class MKLocalSearch`

A utility object for initiating map-based searches and processing the results.

`class MKAddressFilter`

An object that filters which address options to include or exclude in search results.

Options that indicate types of search completions.

`class MKLocalSearchCompleter`

A utility object for generating a list of completion strings based on a partial search string that you provide.

`class MKLocalSearchCompletion`

A fully formed string that completes a partial string.

`class MKLocalPointsOfInterestRequest`

A structured request to use when searching for points of interest.

---

# https://developer.apple.com/documentation/mapkit/mkaddressfilter

- MapKit
- MKAddressFilter

Class

# MKAddressFilter

An object that filters which address options to include or exclude in search results.

class MKAddressFilter

## Overview

Use this object to filter search results by criteria, such as country, region, and municipality. See `MKAddressFilter.Options` for more information.

## Topics

### Creating a filter

`init(excluding: MKAddressFilter.Options)`

Creates an address filter with options for excluding results in a search.

`init(including: MKAddressFilter.Options)`

Creates an address filter with options for including results in a search.

### Filtering results

`struct Options`

A structure that contains options for filtering results in a search.

`class var excludingAll: MKAddressFilter`

A list of categories to exclude from a search.

`class var includingAll: MKAddressFilter`

A list of categories to include in a search.

Indicates whether options are excluded from filtering.

Indicates whether options are included for filtering.

## Relationships

### Inherits From

- `NSObject`

### Conforms To

- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSCoding`
- `NSCopying`
- `NSObjectProtocol`
- `NSSecureCoding`

## See Also

### Local search

Interacting with nearby points of interest

Provide automatic search completions for a partial search query, search the map for relevant locations nearby, and retrieve details for selected points of interest.

`enum MKLocalSearchRegionPriority`

A value that indicates the importance of the configured region.

`struct ResultType`

Options that indicate types of search results.

`class MKLocalSearch`

A utility object for initiating map-based searches and processing the results.

Options that indicate types of search completions.

`class MKLocalSearchCompleter`

A utility object for generating a list of completion strings based on a partial search string that you provide.

`class MKLocalSearchCompletion`

A fully formed string that completes a partial string.

`class MKLocalPointsOfInterestRequest`

A structured request to use when searching for points of interest.

---

# https://developer.apple.com/documentation/mapkit/mklocalsearchcompleter/resulttype

- MapKit
- MKLocalSearchCompleter
- MKLocalSearchCompleter.ResultType

Structure

# MKLocalSearchCompleter.ResultType

Options that indicate types of search completions.

struct ResultType

## Topics

### Type properties

`static var address: MKLocalSearchCompleter.ResultType`

A value that indicates that the search completer includes address completions in the result.

`static var pointOfInterest: MKLocalSearchCompleter.ResultType`

A value that indicates that the search completer includes point-of-interest completions in the result.

`static var physicalFeature: MKLocalSearchCompleter.ResultType`

A value that indicates that the search completer includes physical feature completions in the result.

`static var query: MKLocalSearchCompleter.ResultType`

A value that indicates that the search completer includes query completions in the result.

### Initializers

`init(rawValue: UInt)`

Creates a direction transport type using a raw unsigned integer value.

## Relationships

### Conforms To

- `BitwiseCopyable`
- `Equatable`
- `ExpressibleByArrayLiteral`
- `OptionSet`
- `RawRepresentable`
- `Sendable`
- `SendableMetatype`
- `SetAlgebra`

## See Also

### Local search

Interacting with nearby points of interest

Provide automatic search completions for a partial search query, search the map for relevant locations nearby, and retrieve details for selected points of interest.

`enum MKLocalSearchRegionPriority`

A value that indicates the importance of the configured region.

`struct ResultType`

Options that indicate types of search results.

`class MKLocalSearch`

A utility object for initiating map-based searches and processing the results.

`struct Options`

A structure that contains options for filtering results in a search.

`class MKAddressFilter`

An object that filters which address options to include or exclude in search results.

`class MKLocalSearchCompleter`

A utility object for generating a list of completion strings based on a partial search string that you provide.

`class MKLocalSearchCompletion`

A fully formed string that completes a partial string.

`class MKLocalPointsOfInterestRequest`

A structured request to use when searching for points of interest.

---

# https://developer.apple.com/documentation/mapkit/mklocalsearchcompleter

- MapKit
- MKLocalSearchCompleter

Class

# MKLocalSearchCompleter

A utility object for generating a list of completion strings based on a partial search string that you provide.

class MKLocalSearchCompleter

## Overview

You use an `MKLocalSearchCompleter` object to retrieve auto-complete suggestions for your own map-based search controls. As the user types text, you feed the current text string into the search completer object, which delivers possible string completions that match locations or points of interest.

You create and configure `MKLocalSearchCompleter` objects yourself. You must always assign a delegate object to the search completer so that you can receive the search results that it generates. Specify a search region to restrict results to a designated area. The following code shows a simple example of a view controller that stores the `MKLocalSearchCompleter` object in a property. The view controller itself acts as the delegate for the completer and the view controller uses the region associated with an `MKMapView` object that’s part of the view controller’s interface. Completer objects are long-lived objects, so you can store strong references to them and reuse them later in your code.

Listing 1. Creating and configuring a search completer

override func viewDidLoad() {
super.viewDidLoad()

completer = MKLocalSearchCompleter()
completer.delegate = self

// Limit search results to the map view's current region.
completer.region = myMapView.region
}
- (void)viewDidLoad {
[super viewDidLoad];

self.completer = [[MKLocalSearchCompleter alloc] init];
self.completer.delegate = self;

// Limit search results to the map view's current region.
self.completer.region = self.myMapView.region;
}

Update the value of the completer’s `queryFragment` property to begin a search query. You can update this property in real time as the user types new characters into a text field because the completer object waits a short amount of time for the query string to stabilize. When modifications to the query string stop, the completer initiates a new search and returns the results to your delegate as an array of `MKLocalSearchCompletion` objects.

## Topics

### Receiving the search results

`var delegate: (any MKLocalSearchCompleterDelegate)?`

The object that receives the completion results.

`protocol MKLocalSearchCompleterDelegate`

Methods the delegate calls with search completion data.

### Specifying the query attributes

`var addressFilter: MKAddressFilter?`

A filter that lists which address options to include or exclude in search results.

`var queryFragment: String`

The search string that you want completions for.

`var region: MKCoordinateRegion`

The region that defines the geographic scope of the search.

`var regionPriority: MKLocalSearchRegionPriority`

A value that indicates the importance of the configured region.

`var resultTypes: MKLocalSearchCompleter.ResultType`

The types of search completions to include.

`var pointOfInterestFilter: MKPointOfInterestFilter?`

A filter that lists point of interest categories to include or exclude in the search.

`var filterType: MKLocalSearchCompleter.FilterType`

The filter options for the search results.

Deprecated

`enum FilterType`

Constants indicating the types of search completions to return.

`struct ResultType`

Options that indicate types of search completions.

### Canceling the query

`func cancel()`

Cancels an in-progress search operation.

`var isSearching: Bool`

A Boolean value that indicates whether a search operation is in progress.

### Getting the current query results

[`var results: [MKLocalSearchCompletion]`](https://developer.apple.com/documentation/mapkit/mklocalsearchcompleter/results)

The most recently received search completions.

## Relationships

### Inherits From

- `NSObject`

### Conforms To

- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSObjectProtocol`

## See Also

### Local search

Interacting with nearby points of interest

Provide automatic search completions for a partial search query, search the map for relevant locations nearby, and retrieve details for selected points of interest.

`enum MKLocalSearchRegionPriority`

Options that indicate types of search results.

`class MKLocalSearch`

A utility object for initiating map-based searches and processing the results.

`struct Options`

A structure that contains options for filtering results in a search.

`class MKAddressFilter`

An object that filters which address options to include or exclude in search results.

`class MKLocalSearchCompletion`

A fully formed string that completes a partial string.

`class MKLocalPointsOfInterestRequest`

A structured request to use when searching for points of interest.

---

# https://developer.apple.com/documentation/mapkit/mklocalsearchcompletion

- MapKit
- MKLocalSearchCompletion

Class

# MKLocalSearchCompletion

A fully formed string that completes a partial string.

class MKLocalSearchCompletion

## Overview

You don’t create instances of this class directly. Instead, you use an `MKLocalSearchCompleter` to initiate a search based on a set of partial search strings. That object stores any matches in its results property. Retrieve any `MKLocalSearchCompletion` objects from that property and display the search terms in your interface, or use one to initiate a search for content based on that search term.

When displaying text completions for a partial search term in your user interface, you might want to use a bold version of a font or add some other highlighting to the portion of the completion string that causes it to match the partial search term. To help you add this styling, the completion object includes highlight ranges for the title and subtitle strings.

## Topics

### Getting the search completions

`var title: String`

The title string associated with the point of interest.

`var subtitle: String`

The subtitle (if any) associated with the point of interest.

[`var titleHighlightRanges: [NSValue]`](https://developer.apple.com/documentation/mapkit/mklocalsearchcompletion/titlehighlightranges)

The ranges of characters to highlight in the title string.

[`var subtitleHighlightRanges: [NSValue]`](https://developer.apple.com/documentation/mapkit/mklocalsearchcompletion/subtitlehighlightranges)

The ranges of characters to highlight in the subtitle string.

## Relationships

### Inherits From

- `NSObject`

### Conforms To

- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSObjectProtocol`

## See Also

### Local search

Interacting with nearby points of interest

Provide automatic search completions for a partial search query, search the map for relevant locations nearby, and retrieve details for selected points of interest.

`enum MKLocalSearchRegionPriority`

A value that indicates the importance of the configured region.

`struct ResultType`

Options that indicate types of search results.

`class MKLocalSearch`

A utility object for initiating map-based searches and processing the results.

`struct Options`

A structure that contains options for filtering results in a search.

`class MKAddressFilter`

An object that filters which address options to include or exclude in search results.

Options that indicate types of search completions.

`class MKLocalSearchCompleter`

A utility object for generating a list of completion strings based on a partial search string that you provide.

`class MKLocalPointsOfInterestRequest`

A structured request to use when searching for points of interest.

---

# https://developer.apple.com/documentation/mapkit/mklocalpointsofinterestrequest

- MapKit
- MKLocalPointsOfInterestRequest

Class

# MKLocalPointsOfInterestRequest

A structured request to use when searching for points of interest.

class MKLocalPointsOfInterestRequest

## Overview

You create an `MKLocalPointsOfInterestRequest` to fetch points of interest within a rectangular bounding box or circular area.

To leverage the phone’s viewport to request points of interest, create a request with a rectangular bounding box using an `MKCoordinateRegion`. The request fetches points of interest within the rectangular region.

To retrieve points of interest nearby or “around the user,” create a request with a circular area defined by `CLLocationCoordinate2D` and a `CLLocationDistance` in meters. The fetch returns points of interest up to the maximum distance defined by `maxRadius`.

You may optionally specifying an `MKPointOfInterestFilter` describing categories to include or exclude. The default behavior of the fetch returns all points of interest.

## Topics

### Creating a point of interest request

`init(center: CLLocationCoordinate2D, radius: CLLocationDistance)`

Creates a points of interest search request centered on the provided coordinate with the provided radius.

`init(coordinateRegion: MKCoordinateRegion)`

Creates a points of interest search request based on existing region.

### Configuring the request parameters

`var region: MKCoordinateRegion`

The region of the bounding box of the request provided or the derived bounding box of the circle created by the radius.

`var coordinate: CLLocationCoordinate2D`

The center of the point of request as latitude and longitude.

`var radius: CLLocationDistance`

The distance provided in meters or the longest distance derived from the center point to the region’s bounding box.

`var pointOfInterestFilter: MKPointOfInterestFilter?`

A filter that lists points of interest categories to include or exclude.

### Getting the maximum radius

`class let maxRadius: CLLocationDistance`

The maximum distance respected for fetching points of interest from the center of the region.

## Relationships

### Inherits From

- `NSObject`

### Conforms To

- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSCopying`
- `NSObjectProtocol`

## See Also

### Local search

Interacting with nearby points of interest

Provide automatic search completions for a partial search query, search the map for relevant locations nearby, and retrieve details for selected points of interest.

`enum MKLocalSearchRegionPriority`

A value that indicates the importance of the configured region.

`struct ResultType`

Options that indicate types of search results.

`class MKLocalSearch`

A utility object for initiating map-based searches and processing the results.

`struct Options`

A structure that contains options for filtering results in a search.

`class MKAddressFilter`

An object that filters which address options to include or exclude in search results.

Options that indicate types of search completions.

`class MKLocalSearchCompleter`

A utility object for generating a list of completion strings based on a partial search string that you provide.

`class MKLocalSearchCompletion`

A fully formed string that completes a partial string.

---

# https://developer.apple.com/documentation/mapkit/mklookaroundscene

- MapKit
- MKLookAroundScene

Class

# MKLookAroundScene

A utility class that encapsulates information the framework requires to retrieve and display a specific Look Around location’s imagery.

class MKLookAroundScene

## Relationships

### Inherits From

- `NSObject`

### Conforms To

- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSCopying`
- `NSObjectProtocol`

## See Also

### Exploring at street level

`class MKLookAroundSceneRequest`

A class you use to request a LookAround scene at the location you specify.

`class MKLookAroundViewController`

A class that manages the presentation and display of a LookAround view.

`class MKLookAroundSnapshotter`

A utility class that you use to create a static image from a LookAround scene.

---

# https://developer.apple.com/documentation/mapkit/mklookaroundscenerequest

- MapKit
- MKLookAroundSceneRequest

Class

# MKLookAroundSceneRequest

A class you use to request a LookAround scene at the location you specify.

class MKLookAroundSceneRequest

## Topics

### Creating a LookAround scene

`init(coordinate: CLLocationCoordinate2D)`

Creates a LookAround scene at the specified coordinates.

`init(mapItem: MKMapItem)`

Creates a LookAround scene with the location described by the specified map item.

### Specifying the request’s location

`var coordinate: CLLocationCoordinate2D`

A coordinate value that describes the location of the LookAround scene.

`var mapItem: MKMapItem?`

A map item that describes the location of the LookAround scene.

### Starting and stopping scene requests

`func cancel()`

Cancels the pending scene request.

Requests a LookAround scene and calls the specified completion handler.

### Monitoring the progress of scene requests

`var isCancelled: Bool`

A Boolean value that indicates if the cancellation of a scene request was successful.

`var isLoading: Bool`

A Boolean value that indicates whether a scene request is loading.

## Relationships

### Inherits From

- `NSObject`

### Conforms To

- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSObjectProtocol`

## See Also

### Exploring at street level

`class MKLookAroundScene`

A utility class that encapsulates information the framework requires to retrieve and display a specific Look Around location’s imagery.

`class MKLookAroundViewController`

A class that manages the presentation and display of a LookAround view.

`class MKLookAroundSnapshotter`

A utility class that you use to create a static image from a LookAround scene.

---

# https://developer.apple.com/documentation/mapkit/mklookaroundviewcontroller

- MapKit
- MKLookAroundViewController

Class

# MKLookAroundViewController

A class that manages the presentation and display of a LookAround view.

@MainActor
class MKLookAroundViewController

## Topics

### Creating a LookAround controller

`init?(coder: NSCoder)`

Creates a new LookAround view controller object from a coder object provided by a storyboard or nib file.

`init(nibName: String?, bundle: Bundle?)`

Creates a new LookAround view controller from the specified nib and bundle.

`init(scene: MKLookAroundScene)`

Creates a new LookAround view controller with the specified scene.

### Customizing the LookAround display

`var isNavigationEnabled: Bool`

A Boolean value that indicates whether the map’s navigation controls are visible.

`var pointOfInterestFilter: MKPointOfInterestFilter?`

The filter used to determine the points of interest shown on the map.

`var showsRoadLabels: Bool`

A Boolean value that indicates whether the map display road labels.

`var badgePosition: MKLookAroundBadgePosition`

A value that indicates the badge’s position on the LookAround view.

`enum MKLookAroundBadgePosition`

Constants that control the position of badges on LookAround views.

### Interacting with the controller

`var delegate: (any MKLookAroundViewControllerDelegate)?`

An object you provide to receive events related to the user’s interaction with the LookAround view controller.

`protocol MKLookAroundViewControllerDelegate`

Methods you implement to respond to changes in the LookAround view controller.

### Accessing the scene

`var scene: MKLookAroundScene?`

The LookAround scene.

## Relationships

### Inherits From

- `NSViewController`
- `UIViewController`

### Conforms To

- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSCoding`
- `NSEditor`
- `NSExtensionRequestHandling`
- `NSObjectProtocol`
- `NSSecureCoding`
- `NSSeguePerforming`
- `NSStandardKeyBindingResponding`
- `NSTouchBarProvider`
- `NSUserActivityRestoring`
- `NSUserInterfaceItemIdentification`
- `Sendable`
- `SendableMetatype`
- `UIActivityItemsConfigurationProviding`
- `UIAppearanceContainer`
- `UIContentContainer`
- `UIFocusEnvironment`
- `UIPasteConfigurationSupporting`
- `UIResponderStandardEditActions`
- `UIStateRestoring`
- `UITraitChangeObservable`
- `UITraitEnvironment`
- `UIUserActivityRestoring`

## See Also

### Exploring at street level

`class MKLookAroundScene`

A utility class that encapsulates information the framework requires to retrieve and display a specific Look Around location’s imagery.

`class MKLookAroundSceneRequest`

A class you use to request a LookAround scene at the location you specify.

`class MKLookAroundSnapshotter`

A utility class that you use to create a static image from a LookAround scene.

---

# https://developer.apple.com/documentation/mapkit/mklookaroundsnapshotter

- MapKit
- MKLookAroundSnapshotter

Class

# MKLookAroundSnapshotter

A utility class that you use to create a static image from a LookAround scene.

class MKLookAroundSnapshotter

## Topics

### Creating a snapshotter object

`init(scene: MKLookAroundScene, options: MKLookAroundSnapshotter.Options)`

Create a new snapshotter object with the scene and options you specify.

### Starting and stopping a snapshot

`func cancel()`

Cancels an in-progress snapshot request.

Requests a new snapshot and calls the completion handler you provide.

### Monitoring the progress of a snaphot

`var isLoading: Bool`

A Boolean value that indicates whether the snapshot request is loading.

### Customizing the snapshot

`class Options`

Values you use to customize LookAround snapshots.

### Accessing snapshot imagery

`class Snapshot`

An object that contains a snapshot image.

## Relationships

### Inherits From

- `NSObject`

### Conforms To

- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSObjectProtocol`

## See Also

### Exploring at street level

`class MKLookAroundScene`

A utility class that encapsulates information the framework requires to retrieve and display a specific Look Around location’s imagery.

`class MKLookAroundSceneRequest`

A class you use to request a LookAround scene at the location you specify.

`class MKLookAroundViewController`

A class that manages the presentation and display of a LookAround view.

---

# https://developer.apple.com/documentation/mapkit/mkmapitemdetailviewcontrollerdelegate

- MapKit
- MKMapItemDetailViewControllerDelegate

Protocol

# MKMapItemDetailViewControllerDelegate

The methods that you use to receive events from an associated map view controller.

@MainActor
protocol MKMapItemDetailViewControllerDelegate : NSObjectProtocol

## Topics

### Instance Methods

`func mapItemDetailViewControllerDidFinish(MKMapItemDetailViewController)`

Informs the delegate when a person dismissed the view controller.

**Required**

## Relationships

### Inherits From

- `NSObjectProtocol`

## See Also

### Place information

`class MKMapItemDetailViewController`

An object that displays detailed information about a map item.

`class MapItemDetailPresentationStyle`

The type of map item detail accessory presentation to use.

`class MKSelectionAccessory`

The type of accessory to display for a selected annotation.

`enum CalloutStyle`

The style to use for a map item detail callout presentation.

---

# https://developer.apple.com/documentation/mapkit/mkmapitemdetailviewcontroller

- MapKit
- MKMapItemDetailViewController

Class

# MKMapItemDetailViewController

An object that displays detailed information about a map item.

@MainActor
class MKMapItemDetailViewController

## Overview

The view controller presents modally and displays place information such as addresses and phone numbers.

This class doesn’t support subclassing. The view hierarchy for this class is private and must not be modified.

## Topics

### Creating a map item detail view controller

`init(mapItem: MKMapItem?)`

Create a map item detail view controller.

`init(mapItem: MKMapItem?, displaysMap: Bool)`

Create a map item detail view controller

### Dismissing the map item detail interface

`var delegate: (any MKMapItemDetailViewControllerDelegate)?`

The map item detail view controller’s delegate.

### Getting and setting the map item

`var mapItem: MKMapItem?`

The map item to display.

## Relationships

### Inherits From

- `NSViewController`
- `UIViewController`

### Conforms To

- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSCoding`
- `NSEditor`
- `NSExtensionRequestHandling`
- `NSObjectProtocol`
- `NSSeguePerforming`
- `NSStandardKeyBindingResponding`
- `NSTouchBarProvider`
- `NSUserActivityRestoring`
- `NSUserInterfaceItemIdentification`
- `Sendable`
- `SendableMetatype`
- `UIActivityItemsConfigurationProviding`
- `UIAppearanceContainer`
- `UIContentContainer`
- `UIFocusEnvironment`
- `UIPasteConfigurationSupporting`
- `UIResponderStandardEditActions`
- `UIStateRestoring`
- `UITraitChangeObservable`
- `UITraitEnvironment`
- `UIUserActivityRestoring`

## See Also

### Place information

`protocol MKMapItemDetailViewControllerDelegate`

The methods that you use to receive events from an associated map view controller.

`class MapItemDetailPresentationStyle`

The type of map item detail accessory presentation to use.

`class MKSelectionAccessory`

The type of accessory to display for a selected annotation.

`enum CalloutStyle`

The style to use for a map item detail callout presentation.

---

# https://developer.apple.com/documentation/mapkit/mkselectionaccessory/mapitemdetailpresentationstyle

- MapKit
- MKSelectionAccessory
- MKSelectionAccessory.MapItemDetailPresentationStyle

Class

# MKSelectionAccessory.MapItemDetailPresentationStyle

The type of map item detail accessory presentation to use.

class MapItemDetailPresentationStyle

## Topics

### Creating a presentation style

An appropriate presentation style will be chosen automatically.

`class var callout: MKSelectionAccessory.MapItemDetailPresentationStyle`

Show map item detail as an annotation callout on the map.

Show map item detail as an annotation callout on the map

`class var openInMaps: MKSelectionAccessory.MapItemDetailPresentationStyle`

Display a small “Open in Apple Maps” link.

Show map item detail by presenting a sheet.

## Relationships

### Inherits From

- `NSObject`

### Conforms To

- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSObjectProtocol`

## See Also

### Place information

`protocol MKMapItemDetailViewControllerDelegate`

The methods that you use to receive events from an associated map view controller.

`class MKMapItemDetailViewController`

An object that displays detailed information about a map item.

`class MKSelectionAccessory`

The type of accessory to display for a selected annotation.

`enum CalloutStyle`

The style to use for a map item detail callout presentation.

---

# https://developer.apple.com/documentation/mapkit/mkselectionaccessory

- MapKit
- MKSelectionAccessory

Class

# MKSelectionAccessory

The type of accessory to display for a selected annotation.

class MKSelectionAccessory

## Mentioned in

Identifying unique locations with Place IDs

## Overview

Implement `mapView(_:selectionAccessoryFor:)` in your map view delegate to specify a selection accessory for annotation content.

## Topics

### Creating a selection accessory

Detailed information about a place

## Relationships

### Inherits From

- `NSObject`

### Conforms To

- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSObjectProtocol`

## See Also

### Place information

`protocol MKMapItemDetailViewControllerDelegate`

The methods that you use to receive events from an associated map view controller.

`class MKMapItemDetailViewController`

An object that displays detailed information about a map item.

`class MapItemDetailPresentationStyle`

The type of map item detail accessory presentation to use.

`enum CalloutStyle`

The style to use for a map item detail callout presentation.

---

# https://developer.apple.com/documentation/mapkit/mkselectionaccessory/mapitemdetailpresentationstyle/calloutstyle

- MapKit
- MKSelectionAccessory
- MKSelectionAccessory.MapItemDetailPresentationStyle
- MKSelectionAccessory.MapItemDetailPresentationStyle.CalloutStyle

Enumeration

# MKSelectionAccessory.MapItemDetailPresentationStyle.CalloutStyle

The style to use for a map item detail callout presentation.

enum CalloutStyle

## Overview

In Swift, use `MKSelectionAccessory.MapItemDetailPresentationStyle.CalloutStyle.full` for map views on iPadOS and macOS. Use a sheet presentation to display full detail place information on iOS.

In Objective-C, use `MKSelectionAccessory.MapItemDetailPresentationStyle.CalloutStyle.full` for map views on iPadOS and macOS. Use a sheet presentation to display full detail place information on iOS.

## Topics

### Enumeration Cases

`case automatic`

A value that allows the framework to choose an appropriate callout style automatically.

`case compact`

A compact, space-saving callout style.

`case full`

A rich, detailed callout style that is suitable for large map views.

### Initializers

`init?(rawValue: Int)`

## Relationships

### Conforms To

- `BitwiseCopyable`
- `Equatable`
- `Hashable`
- `RawRepresentable`
- `Sendable`
- `SendableMetatype`

## See Also

### Place information

`protocol MKMapItemDetailViewControllerDelegate`

The methods that you use to receive events from an associated map view controller.

`class MKMapItemDetailViewController`

An object that displays detailed information about a map item.

`class MapItemDetailPresentationStyle`

The type of map item detail accessory presentation to use.

`class MKSelectionAccessory`

The type of accessory to display for a selected annotation.

---

# https://developer.apple.com/documentation/mapkit/mkmapfeatureannotation

- MapKit
- MKMapFeatureAnnotation

Class

# MKMapFeatureAnnotation

A class that describes an annotation element on the map’s display such as a point of interest, territorial boundary, or physical feature.

class MKMapFeatureAnnotation

## Topics

### Customizing the annotation

`var featureType: MKMapFeatureAnnotation.FeatureType`

The type of map feature this annotation represents.

`enum FeatureType`

Values that describe the kinds of features visible on the map.

`var iconStyle: MKIconStyle?`

The icon style of a feature annotation.

`var pointOfInterestCategory: MKPointOfInterestCategory?`

The feature annotation’s point of interest category.

## Relationships

### Inherits From

- `NSObject`

### Conforms To

- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `MKAnnotation`
- `NSObjectProtocol`

## See Also

### Points of interest

Identifying unique locations with Place IDs

Obtain information about a point of interest that persists over its lifetime.

`struct MKMapFeatureOptions`

A structure you use to tell the map which kinds of features users can interact with.

`class MKMapItemRequest`

A utility class you use to request additional information about a map feature.

`class MKIconStyle`

A class you use to customize the annotation view icon of a point of interest (POI) on the map.

`class MKPointOfInterestFilter`

A filter that includes or excludes point of interest categories from a map view, local search, or local search completer.

`struct MKPointOfInterestCategory`

A point of interest category.

---

# https://developer.apple.com/documentation/mapkit/mkmapfeatureoptions

- MapKit
- MKMapFeatureOptions

Structure

# MKMapFeatureOptions

A structure you use to tell the map which kinds of features users can interact with.

struct MKMapFeatureOptions

## Topics

### Initializers

`init(rawValue: Int)`

Creates a new feature option structure with the specified value.

### Selecting interactive map features

`static var physicalFeatures: MKMapFeatureOptions`

The option that represents physical map features such as mountain ranges, rivers, and ocean basins.

`static var pointsOfInterest: MKMapFeatureOptions`

The option that represents points of interest such as museums, cafes, parks, or schools.

`static var territories: MKMapFeatureOptions`

The option that represents territorial boundaries such as a national border, a state boundary, or a neighborhood.

## Relationships

### Conforms To

- `BitwiseCopyable`
- `Equatable`
- `ExpressibleByArrayLiteral`
- `OptionSet`
- `RawRepresentable`
- `Sendable`
- `SendableMetatype`
- `SetAlgebra`

## See Also

### Points of interest

Identifying unique locations with Place IDs

Obtain information about a point of interest that persists over its lifetime.

`class MKMapFeatureAnnotation`

A class that describes an annotation element on the map’s display such as a point of interest, territorial boundary, or physical feature.

`class MKMapItemRequest`

A utility class you use to request additional information about a map feature.

`class MKIconStyle`

A class you use to customize the annotation view icon of a point of interest (POI) on the map.

`class MKPointOfInterestFilter`

A filter that includes or excludes point of interest categories from a map view, local search, or local search completer.

`struct MKPointOfInterestCategory`

A point of interest category.

---

# https://developer.apple.com/documentation/mapkit/mkmapitemrequest

- MapKit
- MKMapItemRequest

Class

# MKMapItemRequest

A utility class you use to request additional information about a map feature.

class MKMapItemRequest

## Mentioned in

Identifying unique locations with Place IDs

## Topics

### Creating a request

`convenience init(feature: MapFeature)`

Creates a new map item request with the specified map feature.

`init(mapItemIdentifier: MKMapItem.Identifier)`

Create a request with a map item identifier.

`init(mapFeatureAnnotation: MKMapFeatureAnnotation)`

Creates a new map item request with the specified feature annotation.

### Configuring the item request

`var mapFeature: MapFeature?`

The map feature.

`var mapFeatureAnnotation: MKMapFeatureAnnotation?`

The feature annotation.

`var mapItemIdentifier: MKMapItem.Identifier?`

The map item identifer.

`var feature: MapFeature`

Deprecated

`var featureAnnotation: MKMapFeatureAnnotation`

`var placeDescriptor: PlaceDescriptor?`

The place descriptor that contains information that’s helpful in uniquely identifying this place.

### Starting and stopping requests

`func cancel()`

Cancels an in-progress map item request.

Requests a map item and calls the provided completion handler.

### Checking the status of a request

`var isCancelled: Bool`

A Boolean value that indicates if the cancellation of the request was successful.

`var isLoading: Bool`

A Boolean value that indicates if the request is loading.

### Initializers

`convenience init(placeDescriptor: PlaceDescriptor)`

Creates a new map item request with the specified place descriptor

## Relationships

### Inherits From

- `NSObject`

### Conforms To

- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSObjectProtocol`

## See Also

### Points of interest

Obtain information about a point of interest that persists over its lifetime.

`class MKMapFeatureAnnotation`

A class that describes an annotation element on the map’s display such as a point of interest, territorial boundary, or physical feature.

`struct MKMapFeatureOptions`

A structure you use to tell the map which kinds of features users can interact with.

`class MKIconStyle`

A class you use to customize the annotation view icon of a point of interest (POI) on the map.

`class MKPointOfInterestFilter`

A filter that includes or excludes point of interest categories from a map view, local search, or local search completer.

`struct MKPointOfInterestCategory`

A point of interest category.

---

# https://developer.apple.com/documentation/mapkit/mkiconstyle

- MapKit
- MKIconStyle

Class

# MKIconStyle

A class you use to customize the annotation view icon of a point of interest (POI) on the map.

class MKIconStyle

## Topics

### Customizing the icon view

`var backgroundColor: UIColor`

The background color of the icon.

`var image: UIImage`

The icon image.

## Relationships

### Inherits From

- `NSObject`

### Conforms To

- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSObjectProtocol`

## See Also

### Points of interest

Identifying unique locations with Place IDs

Obtain information about a point of interest that persists over its lifetime.

`class MKMapFeatureAnnotation`

A class that describes an annotation element on the map’s display such as a point of interest, territorial boundary, or physical feature.

`struct MKMapFeatureOptions`

A structure you use to tell the map which kinds of features users can interact with.

`class MKMapItemRequest`

A utility class you use to request additional information about a map feature.

`class MKPointOfInterestFilter`

A filter that includes or excludes point of interest categories from a map view, local search, or local search completer.

`struct MKPointOfInterestCategory`

A point of interest category.

---

# https://developer.apple.com/documentation/mapkit/mkpointofinterestfilter

- MapKit
- MKPointOfInterestFilter

Class

# MKPointOfInterestFilter

A filter that includes or excludes point of interest categories from a map view, local search, or local search completer.

class MKPointOfInterestFilter

## Overview

You can apply a point of interest filter in a map view ( `pointOfInterestFilter`), a local search request ( `pointOfInterestFilter`), a search completer ( `pointOfInterestFilter`), and in snapshot options ( `pointOfInterestFilter`).

## Topics

### Creating filters

`class var excludingAll: MKPointOfInterestFilter`

A filter that excludes all point of interest categories.

`class var includingAll: MKPointOfInterestFilter`

A filter that includes all point of interest categories.

[`init(excluding: [MKPointOfInterestCategory])`](https://developer.apple.com/documentation/mapkit/mkpointofinterestfilter/init(excluding:))

Initialize the point of interest filter with a list of categories to exclude.

[`init(including: [MKPointOfInterestCategory])`](https://developer.apple.com/documentation/mapkit/mkpointofinterestfilter/init(including:))

Initialize the point of interest filter with a list of categories to include.

### Querying filter behavior

Returns a Boolean value indicating whether the filter excludes the point of interest category.

Returns a Boolean value indicating whether the filter includes the point of interest category.

## Relationships

### Inherits From

- `NSObject`

### Conforms To

- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSCoding`
- `NSCopying`
- `NSObjectProtocol`
- `NSSecureCoding`

## See Also

### Points of interest

Identifying unique locations with Place IDs

Obtain information about a point of interest that persists over its lifetime.

`class MKMapFeatureAnnotation`

A class that describes an annotation element on the map’s display such as a point of interest, territorial boundary, or physical feature.

`struct MKMapFeatureOptions`

A structure you use to tell the map which kinds of features users can interact with.

`class MKMapItemRequest`

A utility class you use to request additional information about a map feature.

`class MKIconStyle`

A class you use to customize the annotation view icon of a point of interest (POI) on the map.

`struct MKPointOfInterestCategory`

A point of interest category.

---

# https://developer.apple.com/documentation/mapkit/mkpointofinterestcategory

- MapKit
- MKPointOfInterestCategory

Structure

# MKPointOfInterestCategory

A point of interest category.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

struct MKPointOfInterestCategory

## Topics

### Category creation

`init(rawValue: String)`

Creates a point of interest category using the provided string.

### Arts and culture

`static let museum: MKPointOfInterestCategory`

The point of interest category for museums.

`static let musicVenue: MKPointOfInterestCategory`

The point of interest category for music venues.

`static let theater: MKPointOfInterestCategory`

The point of interest category for theaters.

### Education

`static let library: MKPointOfInterestCategory`

The point of interest category for libraries.

`static let planetarium: MKPointOfInterestCategory`

The point of interest category for planetariums.

`static let school: MKPointOfInterestCategory`

The point of interest category for schools.

`static let university: MKPointOfInterestCategory`

The point of interest category for universities.

### Entertainment

`static let movieTheater: MKPointOfInterestCategory`

The point of interest category for movie theaters.

`static let nightlife: MKPointOfInterestCategory`

The point of interest category for nightlife.

### Health and safety

`static let fireStation: MKPointOfInterestCategory`

The point of interest category for fire stations.

`static let hospital: MKPointOfInterestCategory`

The point of interest category for hospitals.

`static let pharmacy: MKPointOfInterestCategory`

The point of interest category for pharmacies.

`static let police: MKPointOfInterestCategory`

The point of interest category for police.

### Historical and cultural landmarks

`static let castle: MKPointOfInterestCategory`

The point of interest category for castles.

`static let fortress: MKPointOfInterestCategory`

The point of interest category for fortresses.

`static let landmark: MKPointOfInterestCategory`

The point of interest category for landmarks.

`static let nationalMonument: MKPointOfInterestCategory`

The point of interest category for national monuments.

### Food and drink

`static let bakery: MKPointOfInterestCategory`

The point of interest category for bakeries.

`static let brewery: MKPointOfInterestCategory`

The point of interest category for breweries.

`static let cafe: MKPointOfInterestCategory`

The point of interest category for cafes.

`static let distillery: MKPointOfInterestCategory`

The point of interest category for distilleries.

`static let foodMarket: MKPointOfInterestCategory`

The point of interest category for food markets, supermarkets, grocery stores, and convenience stores.

`static let restaurant: MKPointOfInterestCategory`

The point of interest category for restaurants.

`static let winery: MKPointOfInterestCategory`

The point of interest category for wineries.

### Personal services

`static let animalService: MKPointOfInterestCategory`

The point of interest category for animal services.

`static let atm: MKPointOfInterestCategory`

The point of interest category for ATM machines.

`static let automotiveRepair: MKPointOfInterestCategory`

The point of interest category for automotive repair services.

`static let bank: MKPointOfInterestCategory`

The point of interest category for banks.

`static let beauty: MKPointOfInterestCategory`

The point of interest category for beauty services.

`static let evCharger: MKPointOfInterestCategory`

The point of interest category for EV chargers.

`static let fitnessCenter: MKPointOfInterestCategory`

The point of interest category for fitness centers.

`static let laundry: MKPointOfInterestCategory`

The point of interest category for laundries.

`static let mailbox: MKPointOfInterestCategory`

The point of interest category for mailboxes.

`static let postOffice: MKPointOfInterestCategory`

The point of interest category for post offices.

`static let restroom: MKPointOfInterestCategory`

The point of interest category for restrooms.

`static let spa: MKPointOfInterestCategory`

The point of interest category for spa services.

`static let store: MKPointOfInterestCategory`

The point of interest category for stores.

### Parks and recreation

`static let amusementPark: MKPointOfInterestCategory`

The point of interest category for amusement parks.

`static let aquarium: MKPointOfInterestCategory`

The point of interest category for aquariums.

`static let beach: MKPointOfInterestCategory`

The point of interest category for beaches.

`static let campground: MKPointOfInterestCategory`

The point of interest category for campgrounds.

`static let fairground: MKPointOfInterestCategory`

The point of interest category for fairgrounds.

`static let marina: MKPointOfInterestCategory`

The point of interest category for marinas.

`static let nationalPark: MKPointOfInterestCategory`

The point of interest category for national parks.

`static let park: MKPointOfInterestCategory`

The point of interest category for parks.

`static let rvPark: MKPointOfInterestCategory`

The point of interest category for recreational vehicle parks.

`static let zoo: MKPointOfInterestCategory`

The point of interest category for zoos.

### Sports

`static let baseball: MKPointOfInterestCategory`

The point of interest category for baseball parks.

`static let basketball: MKPointOfInterestCategory`

The point of interest category for basketball courts.

`static let bowling: MKPointOfInterestCategory`

The point of interest category for bowling lanes.

`static let goKart: MKPointOfInterestCategory`

The point of interest category for go-kart services.

`static let golf: MKPointOfInterestCategory`

The point of interest category for golf courses.

`static let hiking: MKPointOfInterestCategory`

The point of interest category for hiking areas.

`static let miniGolf: MKPointOfInterestCategory`

The point of interest category for mini-golf areas.

`static let rockClimbing: MKPointOfInterestCategory`

The point of interest category for rock-climbing areas.

`static let skatePark: MKPointOfInterestCategory`

The point of interest category for skate parks.

`static let skating: MKPointOfInterestCategory`

The point of interest category for skating areas.

`static let skiing: MKPointOfInterestCategory`

The point of interest category for skiing areas.

`static let soccer: MKPointOfInterestCategory`

The point of interest category for soccer fields.

`static let stadium: MKPointOfInterestCategory`

The point of interest category for stadiums.

`static let tennis: MKPointOfInterestCategory`

The point of interest category for tennis courts.

`static let volleyball: MKPointOfInterestCategory`

The point of interest category for volleyball courts.

### Travel

`static let airport: MKPointOfInterestCategory`

The point of interest category for airports.

`static let carRental: MKPointOfInterestCategory`

The point of interest category for car rentals.

`static let conventionCenter: MKPointOfInterestCategory`

The point of interest category for convention centers.

`static let gasStation: MKPointOfInterestCategory`

The point of interest category for gas stations.

`static let hotel: MKPointOfInterestCategory`

The point of interest category for hotels.

`static let parking: MKPointOfInterestCategory`

The point of interest category for parking locations.

`static let publicTransport: MKPointOfInterestCategory`

The point of interest category for locations of public transportation.

### Water sports

`static let fishing: MKPointOfInterestCategory`

The point of interest category for fishing areas.

`static let kayaking: MKPointOfInterestCategory`

The point of interest category for kayaking areas.

`static let surfing: MKPointOfInterestCategory`

The point of interest category for surfing areas.

`static let swimming: MKPointOfInterestCategory`

The point of interest category for swimming areas.

## Relationships

### Conforms To

- `Equatable`
- `Hashable`
- `RawRepresentable`
- `Sendable`
- `SendableMetatype`

## See Also

### Points of interest

Identifying unique locations with Place IDs

Obtain information about a point of interest that persists over its lifetime.

`class MKMapFeatureAnnotation`

A class that describes an annotation element on the map’s display such as a point of interest, territorial boundary, or physical feature.

`struct MKMapFeatureOptions`

A structure you use to tell the map which kinds of features users can interact with.

`class MKMapItemRequest`

A utility class you use to request additional information about a map feature.

`class MKIconStyle`

A class you use to customize the annotation view icon of a point of interest (POI) on the map.

`class MKPointOfInterestFilter`

A filter that includes or excludes point of interest categories from a map view, local search, or local search completer.

---

# https://developer.apple.com/documentation/mapkit/mkmapsnapshotter

- MapKit
- MKMapSnapshotter

Class

# MKMapSnapshotter

A utility class for capturing a map and its content into an image.

class MKMapSnapshotter

## Overview

Use an `MKMapSnapshotter` object when you want to capture the system-provided map content, including the map tiles and imagery. The snapshotter object captures the best image possible by loading all of the available map tiles before capturing the image.

Configure a snapshotter object using an `MKMapSnapshotter.Options` object. The snapshot options specify the appearance of the map, including which portion of the map the snapshotter captures.

## Topics

### Creating a snapshotter object

`init(options: MKMapSnapshotter.Options)`

Creates and returns a snapshotter object based on the specified options.

`class Options`

The options the snapshotter initializer uses to create a snapshotter to capture map-based imagery.

### Generating a snapshot

Submits the request to create a snapshot and delivers the results to the specified block.

Submits the request to create a snapshot and executes the resulting block on the specified queue.

`typealias CompletionHandler`

A block that processes the results of a snapshot request.

`func cancel()`

Cancels the request to create a snapshot.

`var isLoading: Bool`

A Boolean value that indicates whether the snapshotter is generating an image.

### Snapshot output

`class Snapshot`

An image that a snapshotter object generates.

## Relationships

### Inherits From

- `NSObject`

### Conforms To

- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSObjectProtocol`

## See Also

### Static map snapshots

---

# https://developer.apple.com/documentation/mapkit/mkmapsnapshotter/snapshot

- MapKit
- MKMapSnapshotter
- MKMapSnapshotter.Snapshot

Class

# MKMapSnapshotter.Snapshot

An image that a snapshotter object generates.

class Snapshot

## Overview

You don’t create instances of this class directly. Instead, you use an `MKMapSnapshotter` object to capture the map contents asynchronously. An `MKMapSnapshotter.Snapshot` object contains the image that the snapshotter generates from the map contents.

Snapshot images don’t include any custom overlays or annotations that your app adds to the map view. If you want your annotations and overlays to appear on the final image, you need to draw them yourself. To position those items correctly on the image, use the `point(for:)` method of this class to translate the overlay or annotation coordinate value to an appropriate location inside the image’s coordinate space.

## Topics

### Getting the snapshot image

`var image: UIImage`

The image of the map’s content.

`var appearance: NSAppearance`

The visual style that MapKit uses when rendering the snapshot.

### Getting points on the image

Converts the specified map coordinate to a point in the coordinate space of the image.

### Getting appearance traits

`var traitCollection: UITraitCollection`

Traits to use when creating the snapshot.

## Relationships

### Inherits From

- `NSObject`

### Conforms To

- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSObjectProtocol`

## See Also

### Static map snapshots

`class MKMapSnapshotter`

A utility class for capturing a map and its content into an image.

---

# https://developer.apple.com/documentation/mapkit/mapkit-functions

Collection

- MapKit
- MapKit for AppKit and UIKit
- MapKit Functions

API Collection

# MapKit Functions

The functions of the MapKit framework provide convenient ways to package map-related data structures.

## Overview

## Topics

### Functions

`init(center: CLLocationCoordinate2D, latitudinalMeters: CLLocationDistance, longitudinalMeters: CLLocationDistance)`

Creates a new coordinate region from the specified coordinate and distance values.

`init(CLLocationCoordinate2D)`

Creates the map point data structure that corresponds to the specified coordinate.

## See Also

### Related Documentation

Location and Maps Programming Guide

---

# https://developer.apple.com/documentation/mapkit/mkerrordomain

- MapKit
- MKErrorDomain

Global Variable

# MKErrorDomain

The error domain for MapKit.

iOSiPadOSMac CatalystmacOSvisionOSwatchOS

let MKErrorDomain: String

## See Also

### Errors

`struct MKError`

Error constants for the MapKit framework.

`enum Code`

---

# https://developer.apple.com/documentation/mapkit/mkerror

- MapKit
- MKError

Structure

# MKError

Error constants for the MapKit framework.

struct MKError

## Topics

### Error codes

`static var decodingFailed: MKError.Code`

GeoJSON decoding failed.

`static var directionsNotFound: MKError.Code`

Directions to the specified location aren’t available.

`static var loadingThrottled: MKError.Code`

The data didn’t load because data throttling is in effect.

`static var placemarkNotFound: MKError.Code`

The framework couldn’t find the specified placemark.

`static var serverFailure: MKError.Code`

The map server was unable to return the desired information.

`static var unknown: MKError.Code`

An unknown error occurred.

`enum Code`

### Type Properties

`static var errorDomain: String`

The error domain.

## Relationships

### Conforms To

- `CustomNSError`
- `Equatable`
- `Error`
- `Hashable`
- `Sendable`
- `SendableMetatype`

## See Also

### Errors

`let MKErrorDomain: String`

The error domain for MapKit.

---

# https://developer.apple.com/documentation/mapkit/mkerror/code

- MapKit
- MKError
- MKError.Code

Enumeration

# MKError.Code

Error constants for the MapKit framework.

enum Code

## Topics

### Constants

`case decodingFailed`

GeoJSON decoding failed.

`case directionsNotFound`

The framework couldn’t find the specified directions.

`case loadingThrottled`

The data didn’t load because data throttling is in effect.

`case placemarkNotFound`

The specified placemark could not be found.

`case serverFailure`

The map server was unable to return the desired information.

`case unknown`

An unknown error occurred.

### Initializers

`init?(rawValue: UInt)`

## Relationships

### Conforms To

- `BitwiseCopyable`
- `Equatable`
- `Hashable`
- `RawRepresentable`
- `Sendable`
- `SendableMetatype`

## See Also

### Errors

`let MKErrorDomain: String`

The error domain for MapKit.

`struct MKError`

---

# https://developer.apple.com/documentation/mapkit/deprecated-symbols

Collection

- MapKit
- MapKit for AppKit and UIKit
- Deprecated Symbols

API Collection

# Deprecated Symbols

Map protocols and view modifiers that are no longer supported.

## Topics

### Initializers

Creates a map that displays a coordinate region and optionally configures available interactions, user location, and tracking behavior.

Deprecated

Creates a map that displays a coordinate region with annotations, and optionally configures available interactions, user location, and tracking behavior.

Creates a map that displays a map rectangle and optionally configures available interactions, user location, and tracking behavior.

Creates a map that displays a map rectangle with annotations, and optionally configures available interactions, user location, and tracking behavior.

### Structures

`struct MapAnnotation`

A customizable annotation that marks a map location.

`struct MapMarker`

A balloon-shaped annotation used to indicate the location on a map.

`struct MapPin`

A pin-shaped annotation used to indicate a location on a map.

### Enumerations

`enum MapUserTrackingMode`

The modes available for user tracking.

---

# https://developer.apple.com/documentation/mapkit/enabling-maps-capability-in-xcode)



---

# https://developer.apple.com/documentation/mapkit/identifying-unique-locations-with-place-ids)

# The page you're looking for can't be found.

Search developer.apple.comSearch Icon

---

# https://developer.apple.com/documentation/mapkit/mkmapview)



---

# https://developer.apple.com/documentation/mapkit/mkmapitem)



---

# https://developer.apple.com/documentation/mapkit/mkcoordinateregion)



---

# https://developer.apple.com/documentation/mapkit/mkcoordinatespan)



---

# https://developer.apple.com/documentation/mapkit/mkmaprect)



---

# https://developer.apple.com/documentation/mapkit/mkmappoint)



---

# https://developer.apple.com/documentation/mapkit/mkmapsize)



---

# https://developer.apple.com/documentation/mapkit/mkdistanceformatter)



---

# https://developer.apple.com/documentation/mapkit/mkmapcamera)



---

# https://developer.apple.com/documentation/mapkit/mkcompassbutton)



---

# https://developer.apple.com/documentation/mapkit/mkscaleview)



---

# https://developer.apple.com/documentation/mapkit/mkzoomcontrol)



---

# https://developer.apple.com/documentation/mapkit/mkpitchcontrol)



---

# https://developer.apple.com/documentation/mapkit/mkusertrackingbutton)



---

# https://developer.apple.com/documentation/mapkit/mkusertrackingbarbuttonitem)



---

# https://developer.apple.com/documentation/mapkit/mapkit-annotations)



---

# https://developer.apple.com/documentation/mapkit/mapkit-overlays)



---

# https://developer.apple.com/documentation/mapkit/mkdirections)



---

# https://developer.apple.com/documentation/mapkit/mkdirections/request)



---

# https://developer.apple.com/documentation/mapkit/mkdirections/response)



---

# https://developer.apple.com/documentation/mapkit/mkdirections/etaresponse)



---

# https://developer.apple.com/documentation/mapkit/mkroute)



---

# https://developer.apple.com/documentation/mapkit/mkroute/step)



---

# https://developer.apple.com/documentation/mapkit/displaying-an-indoor-map)



---

# https://developer.apple.com/documentation/mapkit/mkgeojsondecoder)



---

# https://developer.apple.com/documentation/mapkit/mkgeojsonfeature)



---

# https://developer.apple.com/documentation/mapkit/mkgeojsonobject)



---

# https://developer.apple.com/documentation/mapkit/interacting-with-nearby-points-of-interest)

# The page you're looking for can't be found.

Search developer.apple.comSearch Icon

---

# https://developer.apple.com/documentation/mapkit/mklocalsearchregionpriority)



---

# https://developer.apple.com/documentation/mapkit/mklocalsearch/resulttype)



---

# https://developer.apple.com/documentation/mapkit/mklocalsearch)



---

# https://developer.apple.com/documentation/mapkit/mkaddressfilter/options)



---

# https://developer.apple.com/documentation/mapkit/mkaddressfilter)



---

# https://developer.apple.com/documentation/mapkit/mklocalsearchcompleter/resulttype)



---

# https://developer.apple.com/documentation/mapkit/mklocalsearchcompleter)



---

# https://developer.apple.com/documentation/mapkit/mklocalsearchcompletion)



---

# https://developer.apple.com/documentation/mapkit/mklocalpointsofinterestrequest)



---

# https://developer.apple.com/documentation/mapkit/mklookaroundscene)



---

# https://developer.apple.com/documentation/mapkit/mklookaroundscenerequest)



---

# https://developer.apple.com/documentation/mapkit/mklookaroundviewcontroller)



---

# https://developer.apple.com/documentation/mapkit/mklookaroundsnapshotter)



---

# https://developer.apple.com/documentation/mapkit/mkmapitemdetailviewcontrollerdelegate)

# The page you're looking for can't be found.

Search developer.apple.comSearch Icon

---

# https://developer.apple.com/documentation/mapkit/mkmapitemdetailviewcontroller)



---

# https://developer.apple.com/documentation/mapkit/mkselectionaccessory/mapitemdetailpresentationstyle)

# The page you're looking for can't be found.

Search developer.apple.comSearch Icon

---

# https://developer.apple.com/documentation/mapkit/mkselectionaccessory)



---

# https://developer.apple.com/documentation/mapkit/mkselectionaccessory/mapitemdetailpresentationstyle/calloutstyle)

# The page you're looking for can't be found.

Search developer.apple.comSearch Icon

---

# https://developer.apple.com/documentation/mapkit/mkmapfeatureannotation)



---

# https://developer.apple.com/documentation/mapkit/mkmapfeatureoptions)



---

# https://developer.apple.com/documentation/mapkit/mkmapitemrequest)



---

# https://developer.apple.com/documentation/mapkit/mkiconstyle)



---

# https://developer.apple.com/documentation/mapkit/mkpointofinterestfilter)



---

# https://developer.apple.com/documentation/mapkit/mkpointofinterestcategory)



---

# https://developer.apple.com/documentation/mapkit/mkmapsnapshotter)



---

# https://developer.apple.com/documentation/mapkit/mkmapsnapshotter/snapshot)



---

# https://developer.apple.com/documentation/mapkit/mapkit-functions)



---

# https://developer.apple.com/documentation/mapkit/mkerrordomain)



---

# https://developer.apple.com/documentation/mapkit/mkerror)



---

# https://developer.apple.com/documentation/mapkit/mkerror/code)



---

# https://developer.apple.com/documentation/mapkit/deprecated-symbols)



---

# https://developer.apple.com/documentation/MapKit/MKCoordinateSpan/init(latitudeDelta:longitudeDelta:)

#app-main)

- MapKit
- MKCoordinateSpan
- init(latitudeDelta:longitudeDelta:)

Initializer

# init(latitudeDelta:longitudeDelta:)

Creates a new `MKCoordinateSpan` from the specified values.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

init(
latitudeDelta: CLLocationDegrees,
longitudeDelta: CLLocationDegrees
)

## Parameters

`latitudeDelta`

The amount of north-to-south distance (measured in degrees) to use for the span. Unlike longitudinal distances, which vary based on the latitude, one degree of latitude is approximately 111 kilometers (69 miles) at all times.

`longitudeDelta`

The amount of east-to-west distance (measured in degrees) to use for the span. The number of kilometers spanned by a longitude range varies based on the current latitude. For example, one degree of longitude spans a distance of approximately 111 kilometers (69 miles) at the equator but shrinks to 0 kilometers at the poles.

## Return Value

A span with the specified delta values.

## See Also

### Creating a coordinate span

`init()`

Creates a coordinate span that represents a width and height on a map.

---

# https://developer.apple.com/documentation/MapKit/MKPointOfInterestCategory

- MapKit
- MKPointOfInterestCategory

Structure

# MKPointOfInterestCategory

A point of interest category.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

struct MKPointOfInterestCategory

## Topics

### Category creation

`init(rawValue: String)`

Creates a point of interest category using the provided string.

### Arts and culture

`static let museum: MKPointOfInterestCategory`

The point of interest category for museums.

`static let musicVenue: MKPointOfInterestCategory`

The point of interest category for music venues.

`static let theater: MKPointOfInterestCategory`

The point of interest category for theaters.

### Education

`static let library: MKPointOfInterestCategory`

The point of interest category for libraries.

`static let planetarium: MKPointOfInterestCategory`

The point of interest category for planetariums.

`static let school: MKPointOfInterestCategory`

The point of interest category for schools.

`static let university: MKPointOfInterestCategory`

The point of interest category for universities.

### Entertainment

`static let movieTheater: MKPointOfInterestCategory`

The point of interest category for movie theaters.

`static let nightlife: MKPointOfInterestCategory`

The point of interest category for nightlife.

### Health and safety

`static let fireStation: MKPointOfInterestCategory`

The point of interest category for fire stations.

`static let hospital: MKPointOfInterestCategory`

The point of interest category for hospitals.

`static let pharmacy: MKPointOfInterestCategory`

The point of interest category for pharmacies.

`static let police: MKPointOfInterestCategory`

The point of interest category for police.

### Historical and cultural landmarks

`static let castle: MKPointOfInterestCategory`

The point of interest category for castles.

`static let fortress: MKPointOfInterestCategory`

The point of interest category for fortresses.

`static let landmark: MKPointOfInterestCategory`

The point of interest category for landmarks.

`static let nationalMonument: MKPointOfInterestCategory`

The point of interest category for national monuments.

### Food and drink

`static let bakery: MKPointOfInterestCategory`

The point of interest category for bakeries.

`static let brewery: MKPointOfInterestCategory`

The point of interest category for breweries.

`static let cafe: MKPointOfInterestCategory`

The point of interest category for cafes.

`static let distillery: MKPointOfInterestCategory`

The point of interest category for distilleries.

`static let foodMarket: MKPointOfInterestCategory`

The point of interest category for food markets, supermarkets, grocery stores, and convenience stores.

`static let restaurant: MKPointOfInterestCategory`

The point of interest category for restaurants.

`static let winery: MKPointOfInterestCategory`

The point of interest category for wineries.

### Personal services

`static let animalService: MKPointOfInterestCategory`

The point of interest category for animal services.

`static let atm: MKPointOfInterestCategory`

The point of interest category for ATM machines.

`static let automotiveRepair: MKPointOfInterestCategory`

The point of interest category for automotive repair services.

`static let bank: MKPointOfInterestCategory`

The point of interest category for banks.

`static let beauty: MKPointOfInterestCategory`

The point of interest category for beauty services.

`static let evCharger: MKPointOfInterestCategory`

The point of interest category for EV chargers.

`static let fitnessCenter: MKPointOfInterestCategory`

The point of interest category for fitness centers.

`static let laundry: MKPointOfInterestCategory`

The point of interest category for laundries.

`static let mailbox: MKPointOfInterestCategory`

The point of interest category for mailboxes.

`static let postOffice: MKPointOfInterestCategory`

The point of interest category for post offices.

`static let restroom: MKPointOfInterestCategory`

The point of interest category for restrooms.

`static let spa: MKPointOfInterestCategory`

The point of interest category for spa services.

`static let store: MKPointOfInterestCategory`

The point of interest category for stores.

### Parks and recreation

`static let amusementPark: MKPointOfInterestCategory`

The point of interest category for amusement parks.

`static let aquarium: MKPointOfInterestCategory`

The point of interest category for aquariums.

`static let beach: MKPointOfInterestCategory`

The point of interest category for beaches.

`static let campground: MKPointOfInterestCategory`

The point of interest category for campgrounds.

`static let fairground: MKPointOfInterestCategory`

The point of interest category for fairgrounds.

`static let marina: MKPointOfInterestCategory`

The point of interest category for marinas.

`static let nationalPark: MKPointOfInterestCategory`

The point of interest category for national parks.

`static let park: MKPointOfInterestCategory`

The point of interest category for parks.

`static let rvPark: MKPointOfInterestCategory`

The point of interest category for recreational vehicle parks.

`static let zoo: MKPointOfInterestCategory`

The point of interest category for zoos.

### Sports

`static let baseball: MKPointOfInterestCategory`

The point of interest category for baseball parks.

`static let basketball: MKPointOfInterestCategory`

The point of interest category for basketball courts.

`static let bowling: MKPointOfInterestCategory`

The point of interest category for bowling lanes.

`static let goKart: MKPointOfInterestCategory`

The point of interest category for go-kart services.

`static let golf: MKPointOfInterestCategory`

The point of interest category for golf courses.

`static let hiking: MKPointOfInterestCategory`

The point of interest category for hiking areas.

`static let miniGolf: MKPointOfInterestCategory`

The point of interest category for mini-golf areas.

`static let rockClimbing: MKPointOfInterestCategory`

The point of interest category for rock-climbing areas.

`static let skatePark: MKPointOfInterestCategory`

The point of interest category for skate parks.

`static let skating: MKPointOfInterestCategory`

The point of interest category for skating areas.

`static let skiing: MKPointOfInterestCategory`

The point of interest category for skiing areas.

`static let soccer: MKPointOfInterestCategory`

The point of interest category for soccer fields.

`static let stadium: MKPointOfInterestCategory`

The point of interest category for stadiums.

`static let tennis: MKPointOfInterestCategory`

The point of interest category for tennis courts.

`static let volleyball: MKPointOfInterestCategory`

The point of interest category for volleyball courts.

### Travel

`static let airport: MKPointOfInterestCategory`

The point of interest category for airports.

`static let carRental: MKPointOfInterestCategory`

The point of interest category for car rentals.

`static let conventionCenter: MKPointOfInterestCategory`

The point of interest category for convention centers.

`static let gasStation: MKPointOfInterestCategory`

The point of interest category for gas stations.

`static let hotel: MKPointOfInterestCategory`

The point of interest category for hotels.

`static let parking: MKPointOfInterestCategory`

The point of interest category for parking locations.

`static let publicTransport: MKPointOfInterestCategory`

The point of interest category for locations of public transportation.

### Water sports

`static let fishing: MKPointOfInterestCategory`

The point of interest category for fishing areas.

`static let kayaking: MKPointOfInterestCategory`

The point of interest category for kayaking areas.

`static let surfing: MKPointOfInterestCategory`

The point of interest category for surfing areas.

`static let swimming: MKPointOfInterestCategory`

The point of interest category for swimming areas.

## Relationships

### Conforms To

- `Equatable`
- `Hashable`
- `RawRepresentable`
- `Sendable`
- `SendableMetatype`

## See Also

### Points of interest

Identifying unique locations with Place IDs

Obtain information about a point of interest that persists over its lifetime.

`class MKMapFeatureAnnotation`

A class that describes an annotation element on the map’s display such as a point of interest, territorial boundary, or physical feature.

`struct MKMapFeatureOptions`

A structure you use to tell the map which kinds of features users can interact with.

`class MKMapItemRequest`

A utility class you use to request additional information about a map feature.

`class MKIconStyle`

A class you use to customize the annotation view icon of a point of interest (POI) on the map.

`class MKPointOfInterestFilter`

A filter that includes or excludes point of interest categories from a map view, local search, or local search completer.

---

# https://developer.apple.com/documentation/MapKit/identifying-unique-locations-with-place-ids

- MapKit
- MapKit for AppKit and UIKit
- Identifying unique locations with Place IDs

Article

# Identifying unique locations with Place IDs

Obtain information about a point of interest that persists over its lifetime.

## Overview

MapKit for AppKit and UIKit, MapKit JS, and Apple Maps Server API provide a way for you to store and share references to places that matter to your application: the Place ID. A Place ID is an opaque string that semantically represents references to points of interest in the world, rather than particular coordinates or addresses.

A Place ID is a great feature for referencing a place’s information, even after that place’s information changes. Place IDs are also useful for displaying a place on a map. Use Place IDs to maintain unique collections of places that are important to your app.

### Obtain a Place ID

You obtain a Place ID by using Geocoder Lookup, Search, Search Autocomplete, Point-of-Interest Search, or choosing a place from Maps. You can also use a Place ID as a primary key or as part of a composite key in a database, or share Place IDs with other apps.

`MKMapItem` in MapKit for AppKit and UIKit, `Place` in MapKit JS, and `Place` objects in Apple Maps Server API include Place IDs that you can read and store. Additionally, you can obtain Place IDs for specific points of interest interactively from Place ID Lookup.

### Look up referenced place information

All MapKit platforms support using a Place ID to obtain the referenced place’s latest information, whether by issuing an `MKMapItemRequest` in MapKit for AppKit and UIKit, a `PlaceLookup` in MapKit JS, or a `Search for places using mulitple identifiers` request in Apple Maps Server API. These always return the most recent information for the place that the Place ID refers to, even if that information changed since you originally obtained it. You don’t have to track these changes or even update the stored Place ID.

A once-valid Place ID might fail to resolve from a lookup. However, this only happens when the referred place is no longer pertinent to Apple Maps. For instance, lookup failure might occur if a place has long been closed or simply no longer exists in the world in any meaningful way.

### Display a referenced place

Use Place IDs to display annotations with `MKMapItemAnnotation` from MapKit for AppKit and UIKit or doc://com.apple.documentation/documentation/mapkitjs/mapkit.placeannotation from MapKit JS. You can also use Place IDs to show more detailed selection accessories, such as popups that automatically display a place’s name, address, hours, and more, with `MKSelectionAccessory` from MapKit for AppKit and UIKit and `PlaceSelectionAccessory` from MapKit JS.

### Maintain a unique collection of places

Although Place IDs themselves are unique, they might not uniquely refer to a place. Multiple different Place IDs might refer to the same place. Because of this, storing collections of Place IDs, where each Place ID refers to a unique place (for example, a user’s favorite place list that shouldn’t contain the same place twice) is more complicated than simply making sure that each ID is bitwise-unique with every other ID in the set.

To aid with this task, place objects don’t just contain a Place ID in `identifier`. They also contain a set of alternate Place IDs. For MapKit for AppKit and UIKit it’s `alternateIdentifiers`, and for MapKit JS it’s `alternateIds`. This list is a nonexhaustive set of alternate Place IDs referring to the place.

This list is critical in maintaining a set of Place IDs that refer to unique places. When adding a new Place ID to an existing set of Place IDs meant to refer to unique places, consult the list of alternate Place IDs for the new Place ID. If your set already contains any of the alternate Place IDs, don’t add the new Place ID to the set because it would be a duplicate.

The procedure of checking for the presence of alternate Place IDs before insertion into an existing set works to minimize duplicate references. However, in rare cases, because alternate Place ID lists aren’t exhaustive, duplicates might occasionally occur. Ensure that your set of Place IDs doesn’t contain two Place IDs that refer to the same place by performing the following steps:

1. Create an empty set of Place IDs. This is the temporary set.

2. For each Place ID, look up its alternate IDs and check if the temporary set contains either the Place ID itself or any of its alternates. If the existing set already contains any of those IDs, remove the Place ID from the existing set, as it’s a duplicate. Otherwise, add the Place ID and all alternates to the temporary set.

After you’ve completed the above steps, delete the temporary set you used to ensure that there were no duplicates amongst Place IDs and their alternates. The existing set now has all duplicates removed.

To maintain performance, use these steps to perform de-duplication on a periodic basis. Alternatively, use Apple Maps Server API’s `Obtain a list of alternate place identifiers` for an efficient way of performing de-duplication.

## See Also

### Essentials

Enabling Maps capability in Xcode

Configure your routing app to support providing directions.

`class MKMapView`

An embeddable map interface, similar to the one that the Maps app provides.

`class MKMapItem`

A point of interest on the map.

---

# https://developer.apple.com/documentation/MapKit/MKMapItem

- MapKit
- MKMapItem

Class

# MKMapItem

A point of interest on the map.

class MKMapItem

## Mentioned in

Identifying unique locations with Place IDs

## Overview

A map item includes a geographic location and any interesting data that might apply to that location, such as the address at that location and the name of a business at that address. You can also create a special `MKMapItem` object representing the user’s location.

Use this class to do the following:

- Share map-related data with the Maps app.

- Handle requests for directions that originate from the Maps app.

To display information in the Maps app, create an `MKMapItem` object with the information you want to display and call the `openMaps(with:launchOptions:)` method. The Maps app displays that location on the map and shows the information you provide.

If you implement a routing app, the Maps app provides two `MKMapItem` objects representing the start and end points. Use the information in those two objects to plot the route and generate directions.

## Topics

### Creating map items

`init(placemark: MKPlacemark)`

Creates and returns a map item object using the specified placemark object.

Deprecated

Creates and returns a singleton map item object representing the user’s location.

### Accessing the map item attributes

`class Identifier`

A unique identifier for a place.

A set of alternative identifiers for a place.

`var identifier: MKMapItem.Identifier?`

`var isCurrentLocation: Bool`

A Boolean value that indicates whether the map item represents the user’s location.

`var name: String?`

The descriptive name associated with the map item.

`var placemark: MKPlacemark`

The placemark object containing the location information.

`var pointOfInterestCategory: MKPointOfInterestCategory?`

The point-of-interest category for the map item.

`var phoneNumber: String?`

The phone number associated with a business at the specified location.

`var timeZone: TimeZone?`

The time zone of the specified location.

`var url: URL?`

The URL associated with the specified location.

### Launching the Maps app

Opens the Maps app and displays the specified map items.

Opens the Maps app using the specified map items and options.

Opens the Maps app from a particular scene using the specified map items and options.

Opens the Maps app and displays the map item.

Opens the Maps app from a particular scene using the specified options.

### Serializing a map item

`let MKMapItemTypeIdentifier: String`

A constant that indicates the type of a serialized map item.

### Opening items at launch time

Launch options to specify when opening map items in the Maps app.

Strings that represent the possible values of the launch options direction mode key.

### Initializers

`init?(coder: NSCoder)`

`init(location: CLLocation, address: MKAddress?)`

Creates and returns a map item object using the specified location and address objects.

### Instance Properties

`var address: MKAddress?`

The address object.

`var addressRepresentations: MKAddressRepresentations?`

The address representations object that contains various address representations useful for display purposes.

`var location: CLLocation`

The location object.

## Relationships

### Inherits From

- `NSObject`

### Conforms To

- `CVarArg`
- `Copyable`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSCoding`
- `NSItemProviderReading`
- `NSItemProviderWriting`
- `NSObjectProtocol`
- `NSSecureCoding`

## See Also

### Essentials

Enabling Maps capability in Xcode

Configure your routing app to support providing directions.

Obtain information about a point of interest that persists over its lifetime.

`class MKMapView`

An embeddable map interface, similar to the one that the Maps app provides.

---

# https://developer.apple.com/documentation/MapKit/MKCoordinateSpan/init(latitudeDelta:longitudeDelta:)).

).#app-main)

# The page you're looking for can't be found.

Search developer.apple.comSearch Icon

---

# https://developer.apple.com/documentation/MapKit/MKPointOfInterestCategory).



---

# https://developer.apple.com/documentation/MapKit/identifying-unique-locations-with-place-ids).

.#app-main)

# The page you're looking for can't be found.

Search developer.apple.comSearch Icon

---

# https://developer.apple.com/documentation/MapKit/MKMapItem)



---

# https://developer.apple.com/documentation/MapKit/identifying-unique-locations-with-place-ids)

# The page you're looking for can't be found.

Search developer.apple.comSearch Icon

---

# https://developer.apple.com/documentation/mapkit/mapcontentbuilder

- MapKit
- MapContentBuilder

Structure

# MapContentBuilder

A result builder that creates map content from closures you provide.

MapKitSwiftUIMac CatalystvisionOS

@resultBuilder
struct MapContentBuilder

## Overview

The `buildBlock(_:)` methods in this type create `MapContent` instances based on the number and types of sources you provide as parameters.

You don’t use this type directly. Instead, SwiftUI annotates the `content` parameter of the various `MapView` initializers with the `@MapContentBuilder` annotation, implicitly calling this builder for you.

## Topics

### Map content builders

Creates an empty map content block that contains no statements.

Creates a map content block that contains a single content result.

### Conditionally building map content

Compares content in a multistatement closure, resulting in use of the conditional content if the first argument you provide evaluates to  true.

Compares content in a multistatement closure, resulting in use of the conditional content if the second argument you provide evaluates to true.

Builds an expression within the map content builder.

Compares content in a multistatement closure, that produces an optional view that’s visible if the argument you provide evaluates to true.

Provides support for “if” statements with “available” macro clauses in multi-statement closures, producing conditional content for the “then” branch, such the conditionally-available branch.

## See Also

### Protocols

`protocol DynamicMapContent`

A  type of view that generates views from an underlying collection of data.

`protocol MapContent`

A protocol used to construct map content such as controls, markers, and annotations.

`struct MapContentView`

A view that contains content that displays on a map at a specific position, and that responds to specific interactions you specify.

---

# https://developer.apple.com/documentation/mapkit/marker

- MapKit
- Marker

Structure

# Marker

A balloon-shaped annotation that marks a map location.

MapKitSwiftUIMac CatalystvisionOS

@MainActor @preconcurrency

## Overview

Use this view to create marker instances in the closure you provide to the `content` parameter in the `Map` initializers.

## Topics

### Creating a marker

Creates a marker at the given location with the label you provide.

Creates a marker at the given location with the provided title and image resource to display as the balloon’s icon.

Creates a marker at the given location with the provided title and a system image the map displays as the balloon’s icon.

`init(LocalizedStringKey, coordinate: CLLocationCoordinate2D)`

Creates a marker at the given location with the localized string key you provide.

`init(LocalizedStringKey, image: String, coordinate: CLLocationCoordinate2D)`

Creates a marker at the given location with the provided localized title and image resource to display as the balloon’s icon.

`init(LocalizedStringKey, monogram: Text, coordinate: CLLocationCoordinate2D)`

Creates a marker at the given location with the provided title key and monogram.

Creates a marker at the given location with the provided title string and monogram.

`init(LocalizedStringKey, systemImage: String, coordinate: CLLocationCoordinate2D)`

Creates a marker at the given location with a localized title, and a system image the map displays as the balloon’s icon.

Creates a marker at the given location with the provided label.

`init(item: MKMapItem)`

Creates a marker for a given map item using a MapKit-provided label.

### Displaying place information

Specifies the selection accessory to display for the selected map item content.

### Initializers

`init(LocalizedStringResource, coordinate: CLLocationCoordinate2D)`

Creates a marker at the given location.

`init(LocalizedStringResource, image: String, coordinate: CLLocationCoordinate2D)`

Creates a marker at the given location with an image displayed as the balloon’s icon.

`init(LocalizedStringResource, monogram: Text, coordinate: CLLocationCoordinate2D)`

Creates a marker at the given location with a monogram displayed as the balloon’s icon.

`init(LocalizedStringResource, systemImage: String, coordinate: CLLocationCoordinate2D)`

Creates a marker at the given location with a system image displayed as the balloon’s icon.

## Relationships

### Conforms To

- `MapContent`
- `Sendable`
- `SendableMetatype`

## See Also

### Annotations and overlays

`struct Annotation`

A customizable annotation used to indicate a location on a map.

`struct MapCircle`

A circular overlay with a configurable radius that you center on a geographic coordinate.

`struct MapPolygon`

A closed polygon overlay.

`struct MapPolyline`

An open polygon overlay consisting of one or more connected line segments.

`struct UserAnnotation`

Displays the person’s current location on the map.

---

# https://developer.apple.com/documentation/mapkit/annotation

- MapKit
- Annotation

Structure

# Annotation

A customizable annotation used to indicate a location on a map.

MapKitSwiftUIMac CatalystvisionOS

@MainActor @preconcurrency

## Overview

Use this view to annotations in the closure you provide to the `content` parameter in the `Map` initializers.

## Topics

### Creating annotations

Creates an annotation that displays a view at a coordinate on the map.

Creates an annotation that displays a view at a coordinate on the map using a title key, coordinate, anchor location, and view you provide.

Creates an annotation that displays a view on the map using coordinates, anchor location, view, and label you provide.

### Displaying place information

Specifies the selection accessory to display for the selected map item content.

### Initializers

## Relationships

### Conforms To

- `MapContent`
- `Sendable`
- `SendableMetatype`

## See Also

### Annotations and overlays

`struct MapCircle`

A circular overlay with a configurable radius that you center on a geographic coordinate.

`struct MapPolygon`

A closed polygon overlay.

`struct MapPolyline`

An open polygon overlay consisting of one or more connected line segments.

`struct Marker`

A balloon-shaped annotation that marks a map location.

`struct UserAnnotation`

Displays the person’s current location on the map.

---

# https://developer.apple.com/documentation/mapkit/mappolyline

- MapKit
- MapPolyline

Structure

# MapPolyline

An open polygon overlay consisting of one or more connected line segments.

MapKitSwiftUIMac CatalystvisionOS

struct MapPolyline

## Overview

Use this view to create map polylines instances in the closure you provide to the `content` parameter in the `Map` initializers.

## Topics

### Creating a polyline

`init(MKPolyline)`

Creates a polyline from polyline you provide.

`init(MKRoute)`

Creates a polyline that traces the route you provide.

[`init(coordinates: [CLLocationCoordinate2D], contourStyle: MapPolyline.ContourStyle)`](https://developer.apple.com/documentation/mapkit/mappolyline/init(coordinates:contourstyle:))

Creates a polyline that traces a path between the given coordinates using the specifed contour style.

[`init(points: [MKMapPoint], contourStyle: MapPolyline.ContourStyle)`](https://developer.apple.com/documentation/mapkit/mappolyline/init(points:contourstyle:))

Creates a new polyline that traces a path between the provided points using the specifed contour style.

### Styling the polyline

`struct ContourStyle`

Values that define how MapKit styles lines to represent the contour of the Earth.

## Relationships

### Conforms To

- `Copyable`
- `MapContent`

## See Also

### Annotations and overlays

`struct Annotation`

A customizable annotation used to indicate a location on a map.

`struct MapCircle`

A circular overlay with a configurable radius that you center on a geographic coordinate.

`struct MapPolygon`

A closed polygon overlay.

`struct Marker`

A balloon-shaped annotation that marks a map location.

`struct UserAnnotation`

Displays the person’s current location on the map.

---

# https://developer.apple.com/documentation/mapkit/lookaroundpreview

- MapKit
- LookAroundPreview

Structure

# LookAroundPreview

A view that provides a Look Around preview for a specific geographic location.

MapKitSwiftUIMac CatalystvisionOS

@MainActor @preconcurrency
struct LookAroundPreview

## Overview

Use a `LookAroundPreview` to create preview imagery for a specific geographic location on the map that you can place in your view. In the following example, a travel recommendations app displays and styles a stack of Look Around previews it generates from an array of `ItineraryItem` structures that contain the location’s title and Look Around scene:

struct LookAroundPreviewsView: View {
let itinerary: [ItineraryItem]
var body: some View {
ScrollView {
LazyVStack {
ForEach(itinerary) { item in
LookAroundPreview(initialScene: item.lookAroundScene)
.frame(height: 128)
.overlay(alignment: .bottomTrailing) {
Text(item.title)
.font(.caption)
.foregroundColor(.white)
.padding()
}
}
}
}
}
}

To display a Look Around viewer a person can explore, apply a `lookAroundViewer` view modifier to a specific view, then add a control the user interacts with to display the Look Around viewer. In the following example, the `lookAroundViewer` view modifier observes a binding to Boolean value to determine whether to display the Look Around viewer.

var lookAroundScene: MKLookAroundScene?

@State private var isLookingAround: Bool = false

var body: some View {
MyInterestingView()
.lookAroundViewer(isPresented: $isLookingAround, initialScene: lookAroundScene)
.toolbar {
ToolbarItem {
Button(action: { lookingAround = true }) {
Image(systemName: "binoculars")
}
}
}
}

## Topics

### Creating a Look Around preview

`init(initialScene: MKLookAroundScene?, allowsNavigation: Bool, showsRoadLabels: Bool, pointsOfInterest: PointOfInterestCategories, badgePosition: MKLookAroundBadgePosition)`

Creates a Look Around preview with an initial scene, navigation, road label, points of interest, and badge position you specify.

Creates a Look Around preview with a binding to a scene, navigation, road label, points of interest, and badge position you specify.

## Relationships

### Conforms To

- `Sendable`
- `SendableMetatype`
- `View`

---

# https://developer.apple.com/documentation/mapkit/searching-displaying-and-navigating-to-places

- MapKit
- MapKit for SwiftUI
- Searching, displaying, and navigating to places

Sample Code

# Searching, displaying, and navigating to places

Convert place information between coordinates and user-friendly place names, get cycling directions, and conveniently display formatted addresses.

Download

Xcode 26.0+

## Overview

---

# https://developer.apple.com/documentation/mapkit/map

- MapKit
- Map

Structure

# Map

A view that displays an embedded map interface.

MapKitSwiftUIMac CatalystvisionOS

@MainActor @preconcurrency

## Overview

Use this SwiftUI view to display a `Map` with markers, annotations, and custom content you provide. You can configure the `Map` to optionally display the user’s location, track a location, and display various controls to allow them to interact with and control the map’s display. The following example displays a map of downtown San Francisco that shows different markers, and an annotation with custom view content at specific locations:

struct ContentView: View {
var body: some View {
Map {
Marker("San Francisco City Hall", coordinate: cityHallLocation)
.tint(.orange)
Marker("San Francisco Public Library", coordinate: publicLibraryLocation)
.tint(.blue)
Annotation("Diller Civic Center Playground", coordinate: playgroundLocation) {
ZStack {
RoundedRectangle(cornerRadius: 5)
.fill(Color.yellow)
Text("🛝")
.padding(5)
}
}
}
.mapControlVisibility(.hidden)
}
}

You create markers, annotations, and overlays using `MapContentBuilder` with any of several `MapContent` types including:

- `Annotation`

- `UserAnnotation`

- `Marker`

- `MapCircle`

- `MapPolygon`

- `MapPolyline`

You can also add a variety of controls to allow a person to interact with the map to change the map’s scale, display or hide the device’s current location, and so on:

- `MapCompass`

- `MapPitchButton`

- `MapPitchSlider`

- `MapScaleView`

- `MapUserLocationButton`

- `MapZoomStepper`

## Topics

### Creating a map

`init(bounds: MapCameraBounds?, interactionModes: MapInteractionModes, scope: Namespace.ID?)`

Creates a new, empty map with the bounds, interaction modes, and scope you provide.

Creates a new map with the bounds, interaction modes, scope, and content you provide.

Creates a new, empty map with the bounds, interaction modes, a binding to a map feature, and scope you provide.

Creates a new, empty map with the bounds, interaction modes, the selected map feature, and scope you provide.

Creates a new map with the bounds, interaction modes, selected map feature, scope, and map content you provide.

Creates a new map with the bounds, interaction modes, selected value, scope, and map content you provide.

`init(initialPosition: MapCameraPosition, bounds: MapCameraBounds?, interactionModes: MapInteractionModes, scope: Namespace.ID?)`

Creates a new, empty map with the initial camera position, bounds, interaction modes, and scope you provide.

Creates a new map with the initial camera position, bounds, interaction modes, scope, and map content you provide.

Creates a new, empty map with the initial camera position, bounds, interaction modes, selected map feature, and scope you provide.

Creates a new map with the initial camera position, bounds, interaction modes, selected map feature, scope, and content you provide.

Creates a new map with the initial camera position, bounds, interaction modes, scope, and content you provide.

Creates a new map with the initial camera position, bounds, interaction modes, selected feature, scope, and content you provide.

`struct MapInteractionModes`

Options that indicate the user interactions that the map responds to.

### Deprecated

Map protocols and view modifiers that are no longer supported.

### Displaying place information

Specifies the selection accessory to display for the selected map item content.

## Relationships

### Conforms To

- `Sendable`
- `SendableMetatype`
- `View`

## See Also

### Essentials

`struct MapStyle`

A style that you can apply to a map.

---

# https://developer.apple.com/documentation/mapkit/mapstyle

- MapKit
- MapStyle

Structure

# MapStyle

A style that you can apply to a map.

MapKitSwiftUIMac CatalystvisionOS

struct MapStyle

## Topics

### Creating map styles

Creates a hybrid map style that includes the elevation, point of interest, and traffic characteristics you specify.

Creates a map style based on satellite imagery with the elevation characteristics you specify.

Creates a standard map style that includes the elevation, point of interest, and traffic characteristics you specify.

`struct Elevation`

Values you use to determine whether a map renders elevation.

`struct StandardEmphasis`

Values that control how the framework emphasizes map features.

### Map styles

`static var hybrid: MapStyle`

A map style that represents a satellite image of the area, including the paths of roads with their names layered on top.

`static var imagery: MapStyle`

A map style that represents a satellite image of the area the map displays.

`static var standard: MapStyle`

A map style that represents the default map presentation, which is a street map that shows the position of all roads and some road names, depending upon the zoom level of the map.

## See Also

### Essentials

`struct Map`

A view that displays an embedded map interface.

---

# https://developer.apple.com/documentation/mapkit/mapcircle

- MapKit
- MapCircle

Structure

# MapCircle

A circular overlay with a configurable radius that you center on a geographic coordinate.

MapKitSwiftUIMac CatalystvisionOS

struct MapCircle

## Overview

Use this view to create circular overlays in the closure you provide to the `content` parameter in `Map` initializers.

## Topics

### Creating a map circle

`init(MKCircle)`

Creates a circle overlay from an existing map circle object.

`init(center: CLLocationCoordinate2D, radius: CLLocationDistance)`

Creates a circle with the center coordinate and radius you specify.

`init(mapRect: MKMapRect)`

Creates the largest possible circle centered within the given map rectangle.

## Relationships

### Conforms To

- `Copyable`
- `MapContent`

## See Also

### Annotations and overlays

`struct Annotation`

A customizable annotation used to indicate a location on a map.

`struct MapPolygon`

A closed polygon overlay.

`struct MapPolyline`

An open polygon overlay consisting of one or more connected line segments.

`struct Marker`

A balloon-shaped annotation that marks a map location.

`struct UserAnnotation`

Displays the person’s current location on the map.

---

# https://developer.apple.com/documentation/mapkit/mappolygon

- MapKit
- MapPolygon

Structure

# MapPolygon

A closed polygon overlay.

MapKitSwiftUIMac CatalystvisionOS

struct MapPolygon

## Overview

Use this view to create map polygons instances in the closure you provide to the `content` parameter in the `Map` initializers.

## Topics

### Creating a map polygon

[`init(coordinates: [CLLocationCoordinate2D])`](https://developer.apple.com/documentation/mapkit/mappolygon/init(coordinates:))

Creates a polygon from a list of coordinates you provide.

[`init(points: [MKMapPoint])`](https://developer.apple.com/documentation/mapkit/mappolygon/init(points:))

Creates a polygon from a list of map points.

`init(MKPolygon)`

Creates a polygon from the polygon you provide.

## Relationships

### Conforms To

- `Copyable`
- `MapContent`

## See Also

### Annotations and overlays

`struct Annotation`

A customizable annotation used to indicate a location on a map.

`struct MapCircle`

A circular overlay with a configurable radius that you center on a geographic coordinate.

`struct MapPolyline`

An open polygon overlay consisting of one or more connected line segments.

`struct Marker`

A balloon-shaped annotation that marks a map location.

`struct UserAnnotation`

Displays the person’s current location on the map.

---

# https://developer.apple.com/documentation/mapkit/userannotation

- MapKit
- UserAnnotation

Structure

# UserAnnotation

Displays the person’s current location on the map.

MapKitSwiftUIMac CatalystvisionOS

@MainActor @preconcurrency

## Overview

Displays the person’s current location using the system styled user location indicator.

## Topics

### Creating a user annotation

`init()`

Creates an annotation that displays the person’s current location.

`init(anchor: UnitPoint)`

Creates an annotation that displays the person’s current location using the system styled user location indicator with the specified anchor point.

Creates an annotation that displays a person’s current location using the system styled user location indicator with the specified anchor point using a custom view.

Create an annotation that displays the person’s current location of the user using a custom view.

### Information about a person’s location

`struct UserLocation`

A structure that contains Information about the person’s current location.

## Relationships

### Conforms To

- `MapContent`
- `Sendable`
- `SendableMetatype`

## See Also

### Annotations and overlays

`struct Annotation`

A customizable annotation used to indicate a location on a map.

`struct MapCircle`

A circular overlay with a configurable radius that you center on a geographic coordinate.

`struct MapPolygon`

A closed polygon overlay.

`struct MapPolyline`

An open polygon overlay consisting of one or more connected line segments.

`struct Marker`

A balloon-shaped annotation that marks a map location.

---

# https://developer.apple.com/documentation/mapkit/mapcompass

- MapKit
- MapCompass

Structure

# MapCompass

A view that reflects the current orientation of the associated map.

MapKitSwiftUIMac CatalystvisionOS

@MainActor @preconcurrency
struct MapCompass

## Overview

You can use `MapCompass` with a `Map` as a stand alone view, as shown in the following example:

struct CompassButtonTestView: View {
@Namespace var mapScope
var body: some View {
VStack {
Map(scope: mapScope)
MapCompass(scope: mapScope)
}
.mapScope(mapScope)
}
}

You can also use `MapCompass` with the `Map/mapControls(_:)`, modifier, as shown below:

Map()
.mapControls {
MapCompass()
}

Tapping the compass reorients the map so that North is at the top of the `Map` view.

## Topics

### Creating a map compass

`init(scope: Namespace.ID?)`

Creates a new map compass with the scope you specify.

## Relationships

### Conforms To

- `Sendable`
- `SendableMetatype`
- `View`

## See Also

### Map controls

`struct MapLocationCompass`

A view that displays a combined user location button and map compass.

`struct MapPitchSlider`

A slider control that allows a person to change the pitch of the map.

`struct MapPitchToggle`

A button that sets the pitch of the associated map.

`struct MapScaleView`

Displays a legend with distance information for the associated map.

`struct MapUserLocationButton`

A button that sets the framing of the associated map to the user location.

`struct MapZoomStepper`

Buttons a person uses to adjust the zoom level of the map.

---

# https://developer.apple.com/documentation/mapkit/maplocationcompass

- MapKit
- MapLocationCompass

Structure

# MapLocationCompass

A view that displays a combined user location button and map compass.

MapKitSwiftUI

@MainActor @preconcurrency
struct MapLocationCompass

## Overview

In watchOS 10 and later, this view displays a combined `MapUserLocationButton` and `MapCompass` control. When the map camera has a heading of zero (where north is up), this view shows the user location button. When the map camera is in a rotated state, it shows a compass.

Use `MapLocationCompass` in conjunction with `Map` as a standalone view, as shown in this example:

struct LocationCompassTestView: View {
@Namespace var mapScope

var body: some View {
VStack {
Map(scope: mapScope)
MapLocationCompass(scope: mapScope)
}
.mapScope(mapScope)
}
}

You can also use `MapLocationCompass` in conjunction with the `mapControls(_:)` modifier. For example:

Map()
.mapControls {
MapLocationCompass()
}

## Topics

### Creating a map loction compass

`init(scope: Namespace.ID?)`

Creates a new map location compass with the provided scope.

## Relationships

### Conforms To

- `Sendable`
- `SendableMetatype`
- `View`

## See Also

### Map controls

`struct MapCompass`

A view that reflects the current orientation of the associated map.

`struct MapPitchSlider`

A slider control that allows a person to change the pitch of the map.

`struct MapPitchToggle`

A button that sets the pitch of the associated map.

`struct MapScaleView`

Displays a legend with distance information for the associated map.

`struct MapUserLocationButton`

A button that sets the framing of the associated map to the user location.

`struct MapZoomStepper`

Buttons a person uses to adjust the zoom level of the map.

---

# https://developer.apple.com/documentation/mapkit/mappitchslider

- MapKit
- MapPitchSlider

Structure

# MapPitchSlider

A slider control that allows a person to change the pitch of the map.

MapKitSwiftUI

@MainActor @preconcurrency
struct MapPitchSlider

## Topics

### Creating a map pitch slider

`init(scope: Namespace.ID?)`

Creates a new map pitch slider with the scope you specify.

## Relationships

### Conforms To

- `Sendable`
- `SendableMetatype`
- `View`

## See Also

### Map controls

`struct MapCompass`

A view that reflects the current orientation of the associated map.

`struct MapLocationCompass`

A view that displays a combined user location button and map compass.

`struct MapPitchToggle`

A button that sets the pitch of the associated map.

`struct MapScaleView`

Displays a legend with distance information for the associated map.

`struct MapUserLocationButton`

A button that sets the framing of the associated map to the user location.

`struct MapZoomStepper`

Buttons a person uses to adjust the zoom level of the map.

---

# https://developer.apple.com/documentation/mapkit/mappitchtoggle

- MapKit
- MapPitchToggle

Structure

# MapPitchToggle

A button that sets the pitch of the associated map.

MapKitSwiftUIMac CatalystvisionOS

@MainActor @preconcurrency
struct MapPitchToggle

## Overview

The `MapPitchToggle` control sets the pitch of the associated map to a pleasing angle if flat, or returns the map to flat if pitched.

You can use this control in conjunction with `Map` as a standalone view, as this example shows:

struct MyMapView: View {
@Namespace var mapScope

var body: some View {
VStack {
Map(scope: mapScope)
MapPitchToggle(scope: mapScope)
}
.mapScope(mapScope)
}
}

Alternatively, use `MapPitchToggle` in conjunction with the `mapControls(_:)` modifier. For example:

Map()
.mapControls {
MapPitchToggle()
}

## Topics

### Creating a map pitch toggle

`init(scope: Namespace.ID?)`

Creates a new map pitch toggle control with the provided scope.

## Relationships

### Conforms To

- `Sendable`
- `SendableMetatype`
- `View`

## See Also

### Map controls

`struct MapCompass`

A view that reflects the current orientation of the associated map.

`struct MapLocationCompass`

A view that displays a combined user location button and map compass.

`struct MapPitchSlider`

A slider control that allows a person to change the pitch of the map.

`struct MapScaleView`

Displays a legend with distance information for the associated map.

`struct MapUserLocationButton`

A button that sets the framing of the associated map to the user location.

`struct MapZoomStepper`

Buttons a person uses to adjust the zoom level of the map.

---

# https://developer.apple.com/documentation/mapkit/mapscaleview

- MapKit
- MapScaleView

Structure

# MapScaleView

Displays a legend with distance information for the associated map.

MapKitSwiftUIMac CatalystvisionOS

@MainActor @preconcurrency
struct MapScaleView

## Overview

You can use this with `Map` as a standalone view, for example:

struct ScaleTestView: View {
@Namespace var mapScope

var body: some View {
VStack {
Map(scope: mapScope)
MapCompass(scope: mapScope)
}
.mapScope(mapScope)
}
}

The scale indicator grows and shrinks (although visually, its frame is static) based on the zoom level of the map. By default the leading edge remains anchored and the trailing edge moves as the scale changes. If the scale is trailing aligned, then it may be more visually appealing to anchor the `ScaleView` to the trailing edge

ZStack(alignment: .trailing) {
Map(mapScope)
MapScaleView(anchorEdge: .trailing, scope: mapScope)
}
.mapScope(mapScope)

You can also use `MapScaleView` with the `mapControls(_:)` modifier, as shown in this example:

Map()
.mapControls {
MapScaleView()
}

## Topics

### Creating a map scale view

`init(anchorEdge: HorizontalEdge, scope: Namespace.ID?)`

Creates a map scale view.

`init(alignment: HorizontalAlignment, scope: Namespace.ID?)`

Creates a scale view with the provided alignment and scope.

## Relationships

### Conforms To

- `Sendable`
- `SendableMetatype`
- `View`

## See Also

### Map controls

`struct MapCompass`

A view that reflects the current orientation of the associated map.

`struct MapLocationCompass`

A view that displays a combined user location button and map compass.

`struct MapPitchSlider`

A slider control that allows a person to change the pitch of the map.

`struct MapPitchToggle`

A button that sets the pitch of the associated map.

`struct MapUserLocationButton`

A button that sets the framing of the associated map to the user location.

`struct MapZoomStepper`

Buttons a person uses to adjust the zoom level of the map.

---

# https://developer.apple.com/documentation/mapkit/mapuserlocationbutton

- MapKit
- MapUserLocationButton

Structure

# MapUserLocationButton

A button that sets the framing of the associated map to the user location.

MapKitSwiftUIMac CatalystvisionOS

@MainActor @preconcurrency
struct MapUserLocationButton

## Overview

Use `MapUserLocationButton` in conjunction with `Map` as a stand alone view, as shown in this example:

struct LocationButtonTestView: View {
@Namespace var mapScope
var body: some View {
VStack {
Map(scope: mapScope)
MapUserLocationButton(scope: mapScope)
}
.mapScope(mapScope)
}
}

You can also use `MapUserLocationButton` in conjunction with the `Map/mapControls(_:)` modifier as shown in this example:

Map()
.mapControls {
MapUserLocationButton()
}

## Topics

### Creating a map user location button

`init(scope: Namespace.ID?)`

Creates a new user location button with the scope you specify.

## Relationships

### Conforms To

- `Sendable`
- `SendableMetatype`
- `View`

## See Also

### Map controls

`struct MapCompass`

A view that reflects the current orientation of the associated map.

`struct MapLocationCompass`

A view that displays a combined user location button and map compass.

`struct MapPitchSlider`

A slider control that allows a person to change the pitch of the map.

`struct MapPitchToggle`

A button that sets the pitch of the associated map.

`struct MapScaleView`

Displays a legend with distance information for the associated map.

`struct MapZoomStepper`

Buttons a person uses to adjust the zoom level of the map.

---

# https://developer.apple.com/documentation/mapkit/mapzoomstepper

- MapKit
- MapZoomStepper

Structure

# MapZoomStepper

Buttons a person uses to adjust the zoom level of the map.

MapKitSwiftUI

@MainActor @preconcurrency
struct MapZoomStepper

## Overview

You typically use `MapZoomStepper` with `Map` as a stand alone view, as shown in the following example:

struct ZoomStepperTestView: View {
@Namespace var mapScope
var body: some View {
VStack {
Map(scope: mapScope)
MapZoomStepper(scope: mapScope)
}
.mapScope(mapScope)
}
}

You can also use a MapZoomStepper in conjunction with the `Map/mapControls(_:)` modifier, as show in here:

Map()
.mapControls {
MapZoomStepper()
}

## Topics

### Creating a zoom stepper

`init(scope: Namespace.ID?)`

Creates a new zoom stepper with the scope you specify.

## Relationships

### Conforms To

- `Sendable`
- `SendableMetatype`
- `View`

## See Also

### Map controls

`struct MapCompass`

A view that reflects the current orientation of the associated map.

`struct MapLocationCompass`

A view that displays a combined user location button and map compass.

`struct MapPitchSlider`

A slider control that allows a person to change the pitch of the map.

`struct MapPitchToggle`

A button that sets the pitch of the associated map.

`struct MapScaleView`

Displays a legend with distance information for the associated map.

`struct MapUserLocationButton`

A button that sets the framing of the associated map to the user location.

---

# https://developer.apple.com/documentation/mapkit/mapfeature

- MapKit
- MapFeature

Structure

# MapFeature

A tappable map feature.

MapKitSwiftUIMac CatalystvisionOS

struct MapFeature

## Overview

Tappable map features can include single points of interest, such as hotels and restaurants, a territory, or a physical map feature such as an ocean, basin, river, or mountain range.

## Topics

### Accessing the feature’s properties

`var kind: MapFeature.FeatureKind`

The kind of feature represented by the map feature.

`struct FeatureKind`

The kind of feature represented by a map feature.

`var coordinate: CLLocationCoordinate2D`

The coordinate of the map feature.

`var title: String?`

The title of the map feature.

`var backgroundColor: Color?`

The background color associated with the map feature.

`var image: Image?`

An image associated with the map feature.

`var pointOfInterestCategory: MKPointOfInterestCategory?`

The point of interest category of the map feature.

## Relationships

### Conforms To

- `Copyable`
- `Equatable`
- `Hashable`

## See Also

### Map features

`struct MapSelection`

A value representing a selected feature on a map.

`protocol MapSelectable`

---

# https://developer.apple.com/documentation/mapkit/mapselection

- MapKit
- MapSelection

Structure

# MapSelection

A value representing a selected feature on a map.

MapKitSwiftUIMac Catalyst

## Topics

### Creating a map selection

`init(SelectionValue)`

Creates a map selection with a tag.

### Getting the properties

`var value: SelectionValue?`

The selection of the given tag value.

## Relationships

### Conforms To

- `Equatable`
- `Hashable`
- `MapSelectable`

## See Also

### Map features

`struct MapFeature`

A tappable map feature.

`protocol MapSelectable`

---

# https://developer.apple.com/documentation/mapkit/mapselectable

- MapKit
- MapSelectable

Protocol

# MapSelectable

MapKitSwiftUIMac CatalystvisionOS

protocol MapSelectable : Hashable

## Topics

### Initializers

`init(MapFeature?)`

**Required**

### Instance Properties

`var feature: MapFeature?`

## Relationships

### Inherits From

- `Equatable`
- `Hashable`

### Conforming Types

- `MapSelection`

## See Also

### Map features

`struct MapFeature`

A tappable map feature.

`struct MapSelection`

A value representing a selected feature on a map.

---

# https://developer.apple.com/documentation/mapkit/mapcamera

- MapKit
- MapCamera

Structure

# MapCamera

Defines a virtual viewpoint above the map surface.

MapKitSwiftUIMac CatalystvisionOS

struct MapCamera

## Overview

`MapCamera` allows you to specify the viewpoint of a `Map`, as well as affect how MapKit presents the map to the user.

To create a map view with a 3D perspective, `MapCamera` takes input from the camera and device:

- The location of the camera on the map.

- The compass heading to indicate the camera’s viewing direction.

- The pitch of the camera relative to the map perpendicular.

- The camera’s distance from the target point.

## Topics

### Creating a map camera

`init(MKMapCamera)`

Creates a map camera from the given MapKit camera object.

`init(centerCoordinate: CLLocationCoordinate2D, distance: Double, heading: Double, pitch: Double)`

Creates a camera using the specified distance, pitch, and heading information.

### Accessing the camera properties

`var centerCoordinate: CLLocationCoordinate2D`

The map coordinate at the center of the map view.

`var distance: Double`

The distance from the center point of the map to the camera, in meters.

`var heading: Double`

The heading of the camera, in degrees, relative to true North.

`var pitch: Double`

The viewing angle of the camera, in degrees.

## Relationships

### Conforms To

- `Equatable`

## See Also

### Map customization

`struct MapCameraBounds`

Defines an optional boundary of an area within which the map’s center needs to remain.

`struct MapCameraPosition`

A structure that describes how to position the map’s camera within the map.

`struct MapCameraUpdateContext`

A structure that defines additional information about the map camera.

`struct MapCameraUpdateFrequency`

A structure that describes when the map camera updates.

---

# https://developer.apple.com/documentation/mapkit/mapcamerabounds

- MapKit
- MapCameraBounds

Structure

# MapCameraBounds

Defines an optional boundary of an area within which the map’s center needs to remain.

MapKitSwiftUIMac CatalystvisionOS

struct MapCameraBounds

## Overview

Using the `MapCameraBounds` initializers you can also define an optional camera zoom range that limits the distances that a person can zoom the map camera to.

## Topics

### Creating a map camera bounds

`init(centerCoordinateBounds: MKCoordinateRegion, minimumDistance: Double?, maximumDistance: Double?)`

Creates a camera bounds with the specified region boundary and zoom ranges.

`init(centerCoordinateBounds: MKMapRect, minimumDistance: Double?, maximumDistance: Double?)`

Creates a camera bounds with the specified map rectangle boundary and zoom ranges.

`init(minimumDistance: Double?, maximumDistance: Double?)`

Creates a camera bounds with the zoom ranges you specify.

## See Also

### Map customization

`struct MapCamera`

Defines a virtual viewpoint above the map surface.

`struct MapCameraPosition`

A structure that describes how to position the map’s camera within the map.

`struct MapCameraUpdateContext`

A structure that defines additional information about the map camera.

`struct MapCameraUpdateFrequency`

A structure that describes when the map camera updates.

---

# https://developer.apple.com/documentation/mapkit/mapcameraposition

- MapKit
- MapCameraPosition

Structure

# MapCameraPosition

A structure that describes how to position the map’s camera within the map.

MapKitSwiftUIMac CatalystvisionOS

struct MapCameraPosition

## Overview

`MapCameraPosition` contains a variety of properties that you can use to control the semantic framings of the camera in relation to its position to the map, such as `automatic`, which frames the content of the map, and the `camera` property, which allows you to specify an explicit camera position.

When you pass `MapCameraPosition` as a binding to a map, the map adjusts its camera to frame the requested content, or to exactly match the camera `MapCameraPosition` specifies. If a person interacts with the `Map` in a way that moves the map, the map resets the position to a value that specifies `positionedByUser`.

## Topics

### Creating a camera position

Creates a new camera position from an existing map camera you provide.

Creates a new camera position centered on a map item and automatic pitch selection you provide.

Creates a new camera position with the map boundaries you provide.

Creates a new camera position the coordinate region you provide.

Creates a camera position with the specific fallback position and optionally follows the user’s heading.

### Information about camera position and framing

`static var automatic: MapCameraPosition`

The position that frames the map’s content.

`var allowsAutomaticPitch: Bool`

The setting that allows the map’s camera to automatically set the pitch when framing the item.

`var camera: MapCamera?`

A map camera that defines the camera positioning.

`var fallbackPosition: MapCameraPosition?`

The position to use if the framework hasn’t resolved the person’s location.

`var item: MKMapItem?`

The item the map is framing.

`var positionedByUser: Bool`

A Boolean value that indicates whether the person specified the camera position by interacting with the map.

`var rect: MKMapRect?`

The position that frames the given map rectangle.

`var region: MKCoordinateRegion?`

The coordinate region to frame.

### Accessing information about someone’s location

`var followsUserHeading: Bool`

A Boolean value that indicates whether the map is following someone’s heading.

`var followsUserLocation: Bool`

A Boolean value that indicates whether the map is following someone’s location.

## Relationships

### Conforms To

- `Equatable`

## See Also

### Map customization

`struct MapCamera`

Defines a virtual viewpoint above the map surface.

`struct MapCameraBounds`

Defines an optional boundary of an area within which the map’s center needs to remain.

`struct MapCameraUpdateContext`

A structure that defines additional information about the map camera.

`struct MapCameraUpdateFrequency`

A structure that describes when the map camera updates.

---

# https://developer.apple.com/documentation/mapkit/mapcameraupdatecontext

- MapKit
- MapCameraUpdateContext

Structure

# MapCameraUpdateContext

A structure that defines additional information about the map camera.

MapKitSwiftUIMac CatalystvisionOS

struct MapCameraUpdateContext

## Topics

### Accessing information about the camera

`let camera: MapCamera`

The current map camera.

`let rect: MKMapRect`

A map rectangle that approximates the view of the map’s camera.

`let region: MKCoordinateRegion`

A map region that approximates the view of the map’s camera.

## See Also

### Map customization

`struct MapCamera`

Defines a virtual viewpoint above the map surface.

`struct MapCameraBounds`

Defines an optional boundary of an area within which the map’s center needs to remain.

`struct MapCameraPosition`

A structure that describes how to position the map’s camera within the map.

`struct MapCameraUpdateFrequency`

A structure that describes when the map camera updates.

---

# https://developer.apple.com/documentation/mapkit/mapcameraupdatefrequency

- MapKit
- MapCameraUpdateFrequency

Structure

# MapCameraUpdateFrequency

A structure that describes when the map camera updates.

MapKitSwiftUIMac CatalystvisionOS

struct MapCameraUpdateFrequency

## Topics

### Timing of camera updates

`static var continuous: MapCameraUpdateFrequency`

A value that indicates that all camera updates are continuous, including while interactions are taking place.

`static var onEnd: MapCameraUpdateFrequency`

A value that indicates the camera updates when map interactions are complete.

## See Also

### Map customization

`struct MapCamera`

Defines a virtual viewpoint above the map surface.

`struct MapCameraBounds`

Defines an optional boundary of an area within which the map’s center needs to remain.

`struct MapCameraPosition`

A structure that describes how to position the map’s camera within the map.

`struct MapCameraUpdateContext`

A structure that defines additional information about the map camera.

---

# https://developer.apple.com/documentation/mapkit/mapitemdetailselectionaccessorystyle

- MapKit
- MapItemDetailSelectionAccessoryStyle

Structure

# MapItemDetailSelectionAccessoryStyle

The map item detail selection accessory style.

MapKitSwiftUIMac Catalyst

struct MapItemDetailSelectionAccessoryStyle

## Topics

### Accessory styles

`static var automatic: MapItemDetailSelectionAccessoryStyle`

A value that allows the framework to choose an appropriate callout style automatically.

`static var callout: MapItemDetailSelectionAccessoryStyle`

The accessory, shown as an annotation callout on the map.

`static var caption: MapItemDetailSelectionAccessoryStyle`

An “Open in Apple Maps” link below the content’s label.

`static var sheet: MapItemDetailSelectionAccessoryStyle`

The map item detail sheet.

### Callout styles

`struct CalloutStyle`

The style to use for callout content.

`static var automatic: MapItemDetailSelectionAccessoryStyle.CalloutStyle`

`static var compact: MapItemDetailSelectionAccessoryStyle.CalloutStyle`

A compact, space-saving callout style.

`static var full: MapItemDetailSelectionAccessoryStyle.CalloutStyle`

A rich, detailed callout style that is suitable for large map views.

### Type Methods

Presents the accessory as an annotation callout on the map.

## See Also

### Place information

Specifies the selection accessory to display for the selected map item content.

---

# https://developer.apple.com/documentation/mapkit/mapcontent/mapitemdetailselectionaccessory(_:)

#app-main)

- MapKit
- MapContent
- mapItemDetailSelectionAccessory(\_:)

Instance Method

# mapItemDetailSelectionAccessory(\_:)

Specifies the selection accessory to display for the selected map item content.

MapKitSwiftUIMac Catalyst

@MainActor @preconcurrency

## Parameters

`style`

The map item detail selection accessory style. If `nil`, no selection accessory appears.

## See Also

### Place information

`struct MapItemDetailSelectionAccessoryStyle`

The map item detail selection accessory style.

Presents the accessory as an annotation callout on the map.

---

# https://developer.apple.com/documentation/mapkit/mapitemdetailselectionaccessorystyle/callout(_:)

#app-main)

- MapKit
- MapItemDetailSelectionAccessoryStyle
- callout(\_:)

Type Method

# callout(\_:)

Presents the accessory as an annotation callout on the map.

MapKitSwiftUIMac Catalyst

## Parameters

`style`

The `MapItemDetailSelectionAccessoryStyle.CalloutStyle` to use.

## See Also

### Place information

`struct MapItemDetailSelectionAccessoryStyle`

The map item detail selection accessory style.

Specifies the selection accessory to display for the selected map item content.

---

# https://developer.apple.com/documentation/mapkit/mkgeocodingrequest

- MapKit
- MKGeocodingRequest

Class

# MKGeocodingRequest

A class that looks up a geographic coordinate using the provided string.

class MKGeocodingRequest

## Discussion

Use this class to look up the coordinate for an address string you provide, for example if you want to display the location in a map. This example shows how to use a `Task` modifier on a SwiftUI view to geocode an array of street addresses to the corresponding coordinates that MapKit returns in an array of `MKMapItem` objects.

struct MyGeocoderView: View {

let addressVisits = [\
"Bethesda Terrace, Central Park \n New York, NY 10023 \n United States",\
"Mill Creek Park Fountain, \n Kansas City, Missouri, \n United States",\
"Archibald Fountain, 110 Elizabeth St \n Sydney NSW 2000 \n Australia"\
]
@State var addressVisitMapItems: [MKMapItem] = []
var body: some View {
// SwiftUI body views
}
.onAppear {
Task {
var addressMapItems = MKMapItem
for address in addressVisits {
if let request = MKGeocodingRequest(addressString: address) {
do {
let mapitems = try await request.mapItems
if let mapitem = mapitems.first {
addressMppItems.append(mapitem)
}
} catch let error {
print("error: \(error)")
}
}
}
addressVisitMapItems = addressMapItems

// The `addressVisitMapItems` array contains `MKMapItem` items that provide information that describe
// the geographic coordinates, the specific address, and other rich data about the provided locations:
//
// "New York, NY 10023 United States" at (40.76821482, -73.98669500)
// "West 43rd St, Kansas City, MO 64111 United States" at (39.04979190, -94.59874170)
// "110 Elizabeth St Sydney NSW 2000 Australia" at (33.87171620, 151.21150870)
}
}

## Topics

### Creating a geocoding request object

`init?(addressString: String)`

Initializes a new geocoder request object with the provided address string.

### Getting the geocoder’s state

`var isLoading: Bool`

A Boolean value that indicates whether the current geocoding request is in a loading state.

`var isCancelled: Bool`

A Boolean value that indicates whether the current geocoding request is in a cancelled state.

### Controlling the geocoder’s operation

`func cancel()`

A function you call to cancel a geocoding request that’s in progress.

### Getting information about the geocoder

`var addressString: String`

The string used to initialize the geocoder.

Returns the map items relevant to the geocoded location.

`var preferredLocale: Locale?`

A value that indicates the default locale the geocoder should use when processing requests.

`var region: MKCoordinateRegion`

The geographic region for the framework to use as the bounds for the request; defaults to a region that covers the whole world.

## Relationships

### Inherits From

- `NSObject`

### Conforms To

- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSObjectProtocol`

## See Also

### Geocoding

`class MKReverseGeocodingRequest`

A class that looks up address strings for the provided geographic coordinates.

---

# https://developer.apple.com/documentation/mapkit/mkreversegeocodingrequest

- MapKit
- MKReverseGeocodingRequest

Class

# MKReverseGeocodingRequest

A class that looks up address strings for the provided geographic coordinates.

class MKReverseGeocodingRequest

## Discussion

Use this class to look up an address by a coordinate you provide. This example shows how to use a `Task` modifier on a SwiftUI view to reverse geocodes an array of coordinates to the corresponding addresses that MapKit returns in an array of `MKMapItem` objects.

struct MyReverseGeocoderView: View {

let fountainCoordinates = [\
CLLocation(latitude: 39.042617, longitude: -94.587526),\
CLLocation(latitude: 40.774313, longitude: -73.970835),\
CLLocation(latitude: -33.870986, longitude: 151.211786),\
CLLocation(latitude: 41.875790, longitude: -87.618953),\
]

// An array that holds resolved information about the fountains.
@State var fountains: [MKMapItem] = []

var body: some View {
// SwiftUI body views
}
.task {
var fountainMapItems = MKMapItem
for coordinate in fountainCoordinates {
if let request = MKReverseGeocodingRequest(location: coordinate) {
let mapitems = try? await request.mapItems
if let mapitem = mapitems?.first {
fountainMapItems.append(mapitem)
}
}
}
fountains = fountainMapItems
// The fountains `MKMapItems` array contains information describing
// details about the following places based on the provided coordinates:
//
// Mill Creek Park Fountain, Kansas City, Missouri
// Bethesda Terrace Fountain, Central Park, New York City
// Archibald Fountain, Sydney, Australia
// Buckingham Fountain, Chicago, Illinois
}
}

## Topics

### Creating a request object

`init?(location: CLLocation)`

Initializes a new reverse geocoder request object with the provided location.

### Getting the reverse geocoder’s state

`var isLoading: Bool`

A Boolean value that indicates whether the current reverse geocoding request is in a loading state.

`var isCancelled: Bool`

A Boolean value that indicates whether the current reverse geocoding request is in a cancelled state.

`var location: CLLocation`

The location provided to the initializer.

### Controlling the reverse geocoder’s operation

`func cancel()`

A method you call to cancel a reverse geocoding request that’s in progress.

### Getting information about map items and the reverse geocoder’s locale’

Returns the map items relevant to the reverse geocoded location.

`var preferredLocale: Locale?`

A value that indicates the preferred locale for the addresses the request returns, or `nil` if the framework should use the device locale.

## Relationships

### Inherits From

- `NSObject`

### Conforms To

- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSObjectProtocol`

## See Also

### Geocoding

`class MKGeocodingRequest`

A class that looks up a geographic coordinate using the provided string.

---

# https://developer.apple.com/documentation/mapkit/mkaddress

- MapKit
- MKAddress

Class

# MKAddress

A class that contains a full address, and, optionally, a short address.

class MKAddress

## Discussion

MapKit capabilities, such as Search and Reverse geocoding, populate the `MKAddress` of a `MKMapItem` with a full address, and a short address, if the framework has one.

When presenting a Place Card using an `MKMapItemDetailViewController` or a selection accessory on an annotation you created using an `MKMapItem`, MapKit uses the full address provided if you create the `MKMapitem` using `init(location:address:)`.

## Topics

### Creating an address

`init?(fullAddress: String, shortAddress: String?)`

Initializes a new address with a location’s full address using a string and a short address that provides an abbreviated form of the address such as a street address.

### Getting the full and short addresses

`var fullAddress: String`

A string that represents a place’s full address

`var shortAddress: String?`

A string that represents the short address of a location, such as it’s street address and city.

## Relationships

### Inherits From

- `NSObject`

### Conforms To

- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSObjectProtocol`

## See Also

### Representing places and addresses

`class MKMapItem`

A point of interest on the map.

`class MKAddressRepresentations`

A class that provides formatted address strings.

GeoToolbox

Determine place descriptor information for map coordinates.

---

# https://developer.apple.com/documentation/mapkit/mkaddressrepresentations

- MapKit
- MKAddressRepresentations

Class

# MKAddressRepresentations

A class that provides formatted address strings.

class MKAddressRepresentations

## Discussion

Use this class to obtain formatted address strings for a place’s full address, city, or region.

## Topics

### Getting parts of an address

`var cityName: String?`

The name of the city.

`var cityWithContext: String?`

The city name along with the country name, to provide additional disambiguating context.

`var regionName: String?`

The region name, such as “United States”.

`var region: Locale.Region?`

### Getting a full address and city name

Returns the the location’s full address, optionally including the country or on a single link without line breaks.

The city name and, optionally and if applicable, state and region to provide additional disambiguating context.

### Controlling the degree of disambiguation to include in an address representation

`enum ContextStyle`

Values that describe the degree of disambiguation context to include in an address representation.

## Relationships

### Inherits From

- `NSObject`

### Conforms To

- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSObjectProtocol`

## See Also

### Representing places and addresses

`class MKMapItem`

A point of interest on the map.

`class MKAddress`

A class that contains a full address, and, optionally, a short address.

GeoToolbox

Determine place descriptor information for map coordinates.

---

# https://developer.apple.com/documentation/mapkit/pointofinterestcategories

- MapKit
- PointOfInterestCategories

Structure

# PointOfInterestCategories

A structure you use to define points of interest to include or exclude on a map.

MapKitSwiftUIMac CatalystvisionOS

struct PointOfInterestCategories

## Topics

### Categories to include or exclude

`static var all: PointOfInterestCategories`

A list of all points of interest categories, both included and excluded.

`static var excludingAll: PointOfInterestCategories`

A list of point of interest categories to exclude from display on the map.

### Modifying the categories to include or exclude

Show all points of interest except those belonging to certain categories using the array you provide.

Show all points of interest except those belonging to certain categories using the list you provide.

Show only points of interest belonging to certain categories from the provided array.

Show only points of interest belonging to certain categories from the provided list.

## Relationships

### Conforms To

- `Copyable`
- `ExpressibleByArrayLiteral`

---

# https://developer.apple.com/documentation/mapkit/dynamicmapcontent

- MapKit
- DynamicMapContent

Protocol

# DynamicMapContent

A  type of view that generates views from an underlying collection of data.

MapKitSwiftUIMac CatalystvisionOS

protocol DynamicMapContent : MapContent

## Topics

### Accessing the data

`var data: Self.Data`

The collection of underlying data.

**Required**

### Associated types

`associatedtype Data : Collection`

The type represents the data this protocol contains.

## Relationships

### Inherits From

- `MapContent`

## See Also

### Protocols

`protocol MapContent`

A protocol used to construct map content such as controls, markers, and annotations.

`struct MapContentBuilder`

A result builder that creates map content from closures you provide.

`struct MapContentView`

A view that contains content that displays on a map at a specific position, and that responds to specific interactions you specify.

---

# https://developer.apple.com/documentation/mapkit/mapcontent

- MapKit
- MapContent

Protocol

# MapContent

A protocol used to construct map content such as controls, markers, and annotations.

MapKitSwiftUIMac CatalystvisionOS

@MainActor @preconcurrency
protocol MapContent

## Topics

### Accessing the view body

`var body: Self.Body`

The content and behavior of the view.

**Required**

### Supplying annotation titles

Sets the visibility of titles for markers and annotations.

Sets the visibility of subtitles for markers and annotations.

### Setting the content style

Specifies the shape style used to fill content in drawing map overlays.

The tint shape style to apply to map content.

### Setting stroke properties

Applies the given shape style to drawn map overlays using the line width you specify.

Applies the given shape style to drawn map overlays using the stroke style you specify.

Applies the given stoke drawn map overlays using the line width you specify.

Applies the given stroke style to drawn map overlays.

### Setting the overlay level

Specifies the position of overlays relative to other map content.

### Associated types

`associatedtype Body : MapContent`

### Displaying place information

Specifies the selection accessory to display for the selected map item content.

### Instance Methods

Sets the unique tag value of this piece of map content.

## Relationships

### Inherited By

- `DynamicMapContent`

### Conforming Types

- `Annotation`
- `AnyMapContent`
- `EmptyMapContent`
- `MapCircle`
- `MapPolygon`
- `MapPolyline`
- `Marker`
- `TupleMapContent`
- `UserAnnotation`

## See Also

### Protocols

`protocol DynamicMapContent`

A  type of view that generates views from an underlying collection of data.

`struct MapContentBuilder`

A result builder that creates map content from closures you provide.

`struct MapContentView`

A view that contains content that displays on a map at a specific position, and that responds to specific interactions you specify.

---

# https://developer.apple.com/documentation/mapkit/mapcontentview

- MapKit
- MapContentView

Structure

# MapContentView

A view that contains content that displays on a map at a specific position, and that responds to specific interactions you specify.

MapKitSwiftUIMac CatalystvisionOS

@MainActor @preconcurrency

## Relationships

### Conforms To

- `Sendable`
- `SendableMetatype`
- `View`

## See Also

### Protocols

`protocol DynamicMapContent`

A  type of view that generates views from an underlying collection of data.

`protocol MapContent`

A protocol used to construct map content such as controls, markers, and annotations.

`struct MapContentBuilder`

A result builder that creates map content from closures you provide.

---

# https://developer.apple.com/documentation/mapkit/defaultuserannotationcontent

- MapKit
- DefaultUserAnnotationContent

Structure

# DefaultUserAnnotationContent

A structure that represents the view to show at the user’s location on the map.

MapKitSwiftUIMac CatalystvisionOS

@MainActor @preconcurrency
struct DefaultUserAnnotationContent

## Overview

Don’t use this type directly. Instead, MapKit creates this type on your behalf.

## Relationships

### Conforms To

- `Sendable`
- `SendableMetatype`
- `View`

## See Also

### Structures

`struct EmptyMapContent`

A map content element that doesn’t contain any content.

`struct MapProxy`

A proxy for accessing sizing information about a given map view.

`struct MapReader`

A container view that defines its contents as a function of information about the first contained map.

`struct TupleMapContent`

A view created from a Swift tuple of map content values.

`struct MapSelectableContentView`

---

# https://developer.apple.com/documentation/mapkit/emptymapcontent

- MapKit
- EmptyMapContent

Structure

# EmptyMapContent

A map content element that doesn’t contain any content.

MapKitSwiftUIMac CatalystvisionOS

@MainActor @preconcurrency
struct EmptyMapContent

## Topics

### Creating an empty map content structure

`init()`

Creates an empty map content element.

## Relationships

### Conforms To

- `MapContent`
- `Sendable`
- `SendableMetatype`

## See Also

### Structures

`struct DefaultUserAnnotationContent`

A structure that represents the view to show at the user’s location on the map.

`struct MapProxy`

A proxy for accessing sizing information about a given map view.

`struct MapReader`

A container view that defines its contents as a function of information about the first contained map.

`struct TupleMapContent`

A view created from a Swift tuple of map content values.

`struct MapSelectableContentView`

---

# https://developer.apple.com/documentation/mapkit/mapproxy

- MapKit
- MapProxy

Structure

# MapProxy

A proxy for accessing sizing information about a given map view.

MapKitSwiftUIMac CatalystvisionOS

struct MapProxy

## Topics

### Creating a camera proxy

Creates a camera in the context of the map that frames the given coordinate region.

Creates a camera in the context of the map that frames the given map rectangle.

Creates a camera in the context of the map that frames the given map item.

### Converting between coordinate spaces

Converts a map coordinate to a point in the specified coordinate space.

Converts a point in the specified coordinate space to a map coordinate.

## See Also

### Structures

`struct DefaultUserAnnotationContent`

A structure that represents the view to show at the user’s location on the map.

`struct EmptyMapContent`

A map content element that doesn’t contain any content.

`struct MapReader`

A container view that defines its contents as a function of information about the first contained map.

`struct TupleMapContent`

A view created from a Swift tuple of map content values.

`struct MapSelectableContentView`

---

# https://developer.apple.com/documentation/mapkit/mapreader

- MapKit
- MapReader

Structure

# MapReader

A container view that defines its contents as a function of information about the first contained map.

MapKitSwiftUIMac CatalystvisionOS

@MainActor @preconcurrency

## Overview

The map reader’s content builder receives a `MapProxy` instance. You can use this instance to get the information you’ll need to convert between a `MapCamera` and a `MKMapRect` or `MKCoordinateRegion`.

## Topics

### Creating a map reader

Creates an instance that allows view content to reference information about a contained map.

## Relationships

### Conforms To

- `Sendable`
- `SendableMetatype`
- `View`

## See Also

### Structures

`struct DefaultUserAnnotationContent`

A structure that represents the view to show at the user’s location on the map.

`struct EmptyMapContent`

A map content element that doesn’t contain any content.

`struct MapProxy`

A proxy for accessing sizing information about a given map view.

`struct TupleMapContent`

A view created from a Swift tuple of map content values.

`struct MapSelectableContentView`

---

# https://developer.apple.com/documentation/mapkit/tuplemapcontent

- MapKit
- TupleMapContent

Structure

# TupleMapContent

A view created from a Swift tuple of map content values.

MapKitSwiftUIMac CatalystvisionOS

@MainActor @frozen @preconcurrency

## Topics

### Accessing the tuple value

`var value: T`

The contents of the tuple.

## Relationships

### Conforms To

- `MapContent`
- `Sendable`
- `SendableMetatype`

## See Also

### Structures

`struct DefaultUserAnnotationContent`

A structure that represents the view to show at the user’s location on the map.

`struct EmptyMapContent`

A map content element that doesn’t contain any content.

`struct MapProxy`

A proxy for accessing sizing information about a given map view.

`struct MapReader`

A container view that defines its contents as a function of information about the first contained map.

`struct MapSelectableContentView`

---

# https://developer.apple.com/documentation/mapkit/mapselectablecontentview

- MapKit
- MapSelectableContentView

Structure

# MapSelectableContentView

MapKitSwiftUIMac CatalystvisionOS

@MainActor @preconcurrency

## Relationships

### Conforms To

- `Sendable`
- `SendableMetatype`
- `View`

## See Also

### Structures

`struct DefaultUserAnnotationContent`

A structure that represents the view to show at the user’s location on the map.

`struct EmptyMapContent`

A map content element that doesn’t contain any content.

`struct MapProxy`

A proxy for accessing sizing information about a given map view.

`struct MapReader`

A container view that defines its contents as a function of information about the first contained map.

`struct TupleMapContent`

A view created from a Swift tuple of map content values.

---

# https://developer.apple.com/documentation/mapkit/mapcontentbuilder)



---

# https://developer.apple.com/documentation/mapkit/marker)



---

# https://developer.apple.com/documentation/mapkit/annotation)



---

# https://developer.apple.com/documentation/mapkit/mappolyline),



---

# https://developer.apple.com/documentation/mapkit/lookaroundpreview)



---

# https://developer.apple.com/documentation/mapkit/searching-displaying-and-navigating-to-places)

# The page you're looking for can't be found.

Search developer.apple.comSearch Icon

---

# https://developer.apple.com/documentation/mapkit/map)



---

# https://developer.apple.com/documentation/mapkit/mapstyle)



---

# https://developer.apple.com/documentation/mapkit/mapcircle)



---

# https://developer.apple.com/documentation/mapkit/mappolygon)



---

# https://developer.apple.com/documentation/mapkit/mappolyline)



---

# https://developer.apple.com/documentation/mapkit/userannotation)



---

# https://developer.apple.com/documentation/mapkit/mapcompass)



---

# https://developer.apple.com/documentation/mapkit/maplocationcompass)



---

# https://developer.apple.com/documentation/mapkit/mappitchslider)



---

# https://developer.apple.com/documentation/mapkit/mappitchtoggle)



---

# https://developer.apple.com/documentation/mapkit/mapscaleview)



---

# https://developer.apple.com/documentation/mapkit/mapuserlocationbutton)



---

# https://developer.apple.com/documentation/mapkit/mapzoomstepper)



---

# https://developer.apple.com/documentation/mapkit/mapfeature)



---

# https://developer.apple.com/documentation/mapkit/mapselection)



---

# https://developer.apple.com/documentation/mapkit/mapselectable)



---

# https://developer.apple.com/documentation/mapkit/mapcamera)



---

# https://developer.apple.com/documentation/mapkit/mapcamerabounds)



---

# https://developer.apple.com/documentation/mapkit/mapcameraposition)



---

# https://developer.apple.com/documentation/mapkit/mapcameraupdatecontext)



---

# https://developer.apple.com/documentation/mapkit/mapcameraupdatefrequency)



---

# https://developer.apple.com/documentation/mapkit/mapitemdetailselectionaccessorystyle)

# The page you're looking for can't be found.

Search developer.apple.comSearch Icon

---

# https://developer.apple.com/documentation/mapkit/mapcontent/mapitemdetailselectionaccessory(_:))

)#app-main)

# The page you're looking for can't be found.

Search developer.apple.comSearch Icon

---

# https://developer.apple.com/documentation/mapkit/mapitemdetailselectionaccessorystyle/callout(_:))

)#app-main)

# The page you're looking for can't be found.

Search developer.apple.comSearch Icon

---

# https://developer.apple.com/documentation/mapkit/mkgeocodingrequest)



---

# https://developer.apple.com/documentation/mapkit/mkreversegeocodingrequest)



---

# https://developer.apple.com/documentation/mapkit/mkaddress)



---

# https://developer.apple.com/documentation/mapkit/mkaddressrepresentations)



---

# https://developer.apple.com/documentation/mapkit/pointofinterestcategories)



---

# https://developer.apple.com/documentation/mapkit/dynamicmapcontent)



---

# https://developer.apple.com/documentation/mapkit/mapcontent)



---

# https://developer.apple.com/documentation/mapkit/mapcontentview)



---

# https://developer.apple.com/documentation/mapkit/defaultuserannotationcontent)



---

# https://developer.apple.com/documentation/mapkit/emptymapcontent)



---

# https://developer.apple.com/documentation/mapkit/mapproxy)



---

# https://developer.apple.com/documentation/mapkit/mapreader)



---

# https://developer.apple.com/documentation/mapkit/tuplemapcontent)



---

# https://developer.apple.com/documentation/mapkit/mapselectablecontentview)



---

# https://developer.apple.com/documentation/mapkit/mkcircleview

- MapKit
- MKCircleView Deprecated

Class

# MKCircleView

Provides the visual representation for an `MKCircle` annotation object.

iOS 4.0–13.0DeprecatediPadOS 4.0–13.0DeprecatedMac Catalyst 13.1–13.1Deprecated

@MainActor
class MKCircleView

## Overview

This view fills and strokes the circle represented by the annotation. You can change the color and other drawing attributes of the circle by modifying the properties inherited from the `MKOverlayPathView` class. This class is typically used as is and not subclassed.

Use of this class is discouraged in iOS 7 and later. Use the `MKCircleRenderer` class instead.

## Relationships

### Inherits From

- `MKOverlayPathView`

### Conforms To

- `CALayerDelegate`
- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSCoding`
- `NSObjectProtocol`
- `NSTouchBarProvider`
- `Sendable`
- `SendableMetatype`
- `UIAccessibilityIdentification`
- `UIActivityItemsConfigurationProviding`
- `UIAppearance`
- `UIAppearanceContainer`
- `UICoordinateSpace`
- `UIDynamicItem`
- `UIFocusEnvironment`
- `UIFocusItem`
- `UIFocusItemContainer`
- `UILargeContentViewerItem`
- `UIPasteConfigurationSupporting`
- `UIPopoverPresentationControllerSourceItem`
- `UIResponderStandardEditActions`
- `UITraitChangeObservable`
- `UITraitEnvironment`
- `UIUserActivityRestoring`

## See Also

### Classes

`class MKOverlayView`

Defines the basic behavior associated with all overlay views.

Deprecated

`class MKOverlayPathView`

Represents a generic overlay that draws its contents using a Core Graphics path data type.

`class MKPolygonView`

Provides the visual representation for an `MKPolygon` annotation object.

`class MKPolylineView`

Provides the visual representation for an `MKPolyline` annotation object.

`class MKPinAnnotationView`

An annotation view that displays a pin image on the map.

---

# https://developer.apple.com/documentation/mapkit/mkcircle

- MapKit
- MKCircle

Class

# MKCircle

A circular overlay with a configurable radius that you center on a geographic coordinate.

class MKCircle

## Overview

This class defines the portion of the map that the overlay covers. To draw the region, return an `MKCircleRenderer` object from the `mapView(_:rendererFor:)` method of your map view delegate.

## Topics

### Creating a circle overlay

`convenience init(center: CLLocationCoordinate2D, radius: CLLocationDistance)`

Creates and returns a circle object using the specified coordinate and radius.

`convenience init(mapRect: MKMapRect)`

Creates and returns a circle object that derives the circular area from the specified rectangle.

### Accessing the overlay’s attributes

`var coordinate: CLLocationCoordinate2D`

The center point of the circular area, specified as a latitude and longitude.

`var radius: CLLocationDistance`

The radius of the circular area, in meters.

`var boundingMapRect: MKMapRect`

The bounding rectangle of the circular area.

## Relationships

### Inherits From

- `MKShape`

### Conforms To

- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `MKAnnotation`
- `MKOverlay`
- `NSObjectProtocol`

## See Also

### Circular overlays

`class MKCircleRenderer`

The visual representation of a circular overlay.

---

# https://developer.apple.com/documentation/mapkit/mkoverlayview

- MapKit
- MKOverlayView Deprecated

Class

# MKOverlayView

Defines the basic behavior associated with all overlay views.

iOS 4.0–13.0DeprecatediPadOS 4.0–13.0DeprecatedMac Catalyst 13.1–13.1Deprecated

@MainActor
class MKOverlayView

## Overview

An overlay view provides the visual representation of an overlay object—that is, an object that conforms to the `MKOverlay` protocol. This class defines the drawing infrastructure used by the map view but does not do any actual drawing. Subclasses are expected to override the `drawMapRect:zoomScale:inContext:` method in order to draw the contents of the overlay view.

The Map Kit framework provides several concrete instances of overlay views. Specifically, it provides overlay views for each of the concrete overlay objects. You can use one of these existing overlay views or define your own subclass if you want to draw the overlay contents differently.

In iOS 7 and later, use the `MKOverlayRenderer` class to display overlays instead.

### Subclassing notes

You can subclass `MKOverlayView` to create overlays based on custom shapes and content. The only method subclasses are expected to override is the `drawMapRect:zoomScale:inContext:` method. However, if your class contains content that may not be ready for drawing right away, you should also override the `canDrawMapRect:zoomScale:` method and use it to report when your class is ready and able to draw.

The implementation of your `drawMapRect:zoomScale:inContext:` method must be safe to run from multiple threads simultaneously. To improve performance, the map view may tile overlays that are large enough and distribute the rendering of each tile to separate threads.

## Relationships

### Inherits From

- `UIView`

### Inherited By

- `MKOverlayPathView`

### Conforms To

- `CALayerDelegate`
- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSCoding`
- `NSObjectProtocol`
- `NSTouchBarProvider`
- `Sendable`
- `SendableMetatype`
- `UIAccessibilityIdentification`
- `UIActivityItemsConfigurationProviding`
- `UIAppearance`
- `UIAppearanceContainer`
- `UICoordinateSpace`
- `UIDynamicItem`
- `UIFocusEnvironment`
- `UIFocusItem`
- `UIFocusItemContainer`
- `UILargeContentViewerItem`
- `UIPasteConfigurationSupporting`
- `UIPopoverPresentationControllerSourceItem`
- `UIResponderStandardEditActions`
- `UITraitChangeObservable`
- `UITraitEnvironment`
- `UIUserActivityRestoring`

## See Also

### Classes

`class MKCircleView`

Provides the visual representation for an `MKCircle` annotation object.

Deprecated

`class MKOverlayPathView`

Represents a generic overlay that draws its contents using a Core Graphics path data type.

`class MKPolygonView`

Provides the visual representation for an `MKPolygon` annotation object.

`class MKPolylineView`

Provides the visual representation for an `MKPolyline` annotation object.

`class MKPinAnnotationView`

An annotation view that displays a pin image on the map.

---

# https://developer.apple.com/documentation/mapkit/mkoverlaypathview

- MapKit
- MKOverlayPathView Deprecated

Class

# MKOverlayPathView

Represents a generic overlay that draws its contents using a Core Graphics path data type.

iOS 4.0–13.0DeprecatediPadOS 4.0–13.0DeprecatedMac Catalyst 13.1–13.1Deprecated

@MainActor
class MKOverlayPathView

## Overview

You can use this class to implement simple path-based overlay views or subclass it to define additional drawing behaviors. The default drawing behavior of this class is to apply the object’s current fill attributes, fill the path, apply the current stroke attributes, and then stroke the path.

If you subclass, you should override the `createPath` method and use that method to build the appropriate path for the overlay. You can invalidate this path as needed and force the path to be recreated using whatever new data your subclass has obtained.

In iOS 7 and later, use the `MKOverlayPathRenderer` class to display path-based overlays instead.

## Relationships

### Inherits From

- `MKOverlayView`

### Inherited By

- `MKCircleView`
- `MKPolygonView`
- `MKPolylineView`

### Conforms To

- `CALayerDelegate`
- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSCoding`
- `NSObjectProtocol`
- `NSTouchBarProvider`
- `Sendable`
- `SendableMetatype`
- `UIAccessibilityIdentification`
- `UIActivityItemsConfigurationProviding`
- `UIAppearance`
- `UIAppearanceContainer`
- `UICoordinateSpace`
- `UIDynamicItem`
- `UIFocusEnvironment`
- `UIFocusItem`
- `UIFocusItemContainer`
- `UILargeContentViewerItem`
- `UIPasteConfigurationSupporting`
- `UIPopoverPresentationControllerSourceItem`
- `UIResponderStandardEditActions`
- `UITraitChangeObservable`
- `UITraitEnvironment`
- `UIUserActivityRestoring`

## See Also

### Classes

`class MKCircleView`

Provides the visual representation for an `MKCircle` annotation object.

Deprecated

`class MKOverlayView`

Defines the basic behavior associated with all overlay views.

`class MKPolygonView`

Provides the visual representation for an `MKPolygon` annotation object.

`class MKPolylineView`

Provides the visual representation for an `MKPolyline` annotation object.

`class MKPinAnnotationView`

An annotation view that displays a pin image on the map.

---

# https://developer.apple.com/documentation/mapkit/mkpolygonview

- MapKit
- MKPolygonView Deprecated

Class

# MKPolygonView

Provides the visual representation for an `MKPolygon` annotation object.

iOS 4.0–13.0DeprecatediPadOS 4.0–13.0DeprecatedMac Catalyst 13.1–13.1Deprecated

@MainActor
class MKPolygonView

## Overview

This view fills and strokes the area represented by the annotation. You can change the color and other drawing attributes of the polygon by modifying the properties inherited from the `MKOverlayPathView` class. This class is typically used as is and not subclassed.

In iOS 7 and later, use the `MKPolygonRenderer` class to display polygon overlays instead.

## Relationships

### Inherits From

- `MKOverlayPathView`

### Conforms To

- `CALayerDelegate`
- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSCoding`
- `NSObjectProtocol`
- `NSTouchBarProvider`
- `Sendable`
- `SendableMetatype`
- `UIAccessibilityIdentification`
- `UIActivityItemsConfigurationProviding`
- `UIAppearance`
- `UIAppearanceContainer`
- `UICoordinateSpace`
- `UIDynamicItem`
- `UIFocusEnvironment`
- `UIFocusItem`
- `UIFocusItemContainer`
- `UILargeContentViewerItem`
- `UIPasteConfigurationSupporting`
- `UIPopoverPresentationControllerSourceItem`
- `UIResponderStandardEditActions`
- `UITraitChangeObservable`
- `UITraitEnvironment`
- `UIUserActivityRestoring`

## See Also

### Classes

`class MKCircleView`

Provides the visual representation for an `MKCircle` annotation object.

Deprecated

`class MKOverlayView`

Defines the basic behavior associated with all overlay views.

`class MKOverlayPathView`

Represents a generic overlay that draws its contents using a Core Graphics path data type.

`class MKPolylineView`

Provides the visual representation for an `MKPolyline` annotation object.

`class MKPinAnnotationView`

An annotation view that displays a pin image on the map.

---

# https://developer.apple.com/documentation/mapkit/mkpolygon

- MapKit
- MKPolygon

Class

# MKPolygon

A closed polygon overlay.

class MKPolygon

## Overview

The points you add to this overlay connect end-to-end in the order you provide them. The first and last points connect to each other to create a closed shape.

When creating a polygon, you can mask out portions of the polygon by specifying one or more interior polygons. For the polygons you specify, this class uses the even-odd fill rule to determine the final occupied area. When applied to overlapping polygons, this rule can cause the framework to mask specific regions out and thereby remove them from the total occupied area. For more information about how fill rules apply to paths, see Paths in Quartz 2D Programming Guide.

## Topics

### Creating a polygon overlay

Creates and returns a polygon object from the specified set of map points.

Creates and returns a polygon object from the specified set of map points and interior polygons.

Creates and returns a polygon object from the specified set of coordinates.

Creates and returns a polygon object from the specified set of coordinates and interior polygons.

### Accessing the interior polygons

[`var interiorPolygons: [MKPolygon]?`](https://developer.apple.com/documentation/mapkit/mkpolygon/interiorpolygons)

The array of polygons that nest inside the enclosing polygon.

## Relationships

### Inherits From

- `MKMultiPoint`

### Conforms To

- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `MKAnnotation`
- `MKGeoJSONObject`
- `MKOverlay`
- `NSObjectProtocol`

## See Also

### Custom shape overlays

`class MKPolygonRenderer`

The visual representation of a single polygon overlay.

`class MKMultiPolygon`

A collection of multiple closed polygon overlays.

`class MKMultiPolygonRenderer`

The visual representation of multiple polygon overlays.

`class MKOverlayPathRenderer`

The visual representation of a path-based overlay.

---

# https://developer.apple.com/documentation/mapkit/mkpolylineview

- MapKit
- MKPolylineView Deprecated

Class

# MKPolylineView

Provides the visual representation for an `MKPolyline` annotation object.

iOS 4.0–13.0DeprecatediPadOS 4.0–13.0DeprecatedMac Catalyst 13.1–13.1Deprecated

@MainActor
class MKPolylineView

## Overview

This view strokes the path represented by the annotation. (This class does not fill the area enclosed by the path.) You can change the color and other drawing attributes of the path by modifying the properties inherited from the `MKOverlayPathView` class. This class is typically used as is and not subclassed.

In iOS 7 and later, use the `MKPolylineRenderer` class to display polyline overlays instead.

## Relationships

### Inherits From

- `MKOverlayPathView`

### Conforms To

- `CALayerDelegate`
- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSCoding`
- `NSObjectProtocol`
- `NSTouchBarProvider`
- `Sendable`
- `SendableMetatype`
- `UIAccessibilityIdentification`
- `UIActivityItemsConfigurationProviding`
- `UIAppearance`
- `UIAppearanceContainer`
- `UICoordinateSpace`
- `UIDynamicItem`
- `UIFocusEnvironment`
- `UIFocusItem`
- `UIFocusItemContainer`
- `UILargeContentViewerItem`
- `UIPasteConfigurationSupporting`
- `UIPopoverPresentationControllerSourceItem`
- `UIResponderStandardEditActions`
- `UITraitChangeObservable`
- `UITraitEnvironment`
- `UIUserActivityRestoring`

## See Also

### Classes

`class MKCircleView`

Provides the visual representation for an `MKCircle` annotation object.

Deprecated

`class MKOverlayView`

Defines the basic behavior associated with all overlay views.

`class MKOverlayPathView`

Represents a generic overlay that draws its contents using a Core Graphics path data type.

`class MKPolygonView`

Provides the visual representation for an `MKPolygon` annotation object.

`class MKPinAnnotationView`

An annotation view that displays a pin image on the map.

---

# https://developer.apple.com/documentation/mapkit/mkpolyline

- MapKit
- MKPolyline

Class

# MKPolyline

An open polygon overlay consisting of one or more connected line segments.

class MKPolyline

## Overview

The points connect end-to-end in the order that you provide them. The first and last points don’t automatically connect to each other.

## Topics

### Creating a polyline overlay

Creates a polyline object from the specified set of map points.

Creates a polyline object from the specified set of coordinates.

## Relationships

### Inherits From

- `MKMultiPoint`

### Inherited By

- `MKGeodesicPolyline`

### Conforms To

- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `MKAnnotation`
- `MKGeoJSONObject`
- `MKOverlay`
- `NSObjectProtocol`

## See Also

### Multiple segment lines

`class MKGeodesicPolyline`

An open polygon overlay consisting of line segments that follow the contours of the Earth to create the shortest path between the specified points.

`class MKMultiPolyline`

A collection of multipolyline shapes, each consisting of one or more connected line segments.

`class MKPolylineRenderer`

A visual representation of any polyline overlay object.

`class MKMultiPolylineRenderer`

A visual representation of multiple polyline overlay objects.

`class MKGradientPolylineRenderer`

A visual representation of any polyline overlay object with a gradient.

---

# https://developer.apple.com/documentation/mapkit/mkpinannotationview

- MapKit
- MKPinAnnotationView Deprecated

Class

# MKPinAnnotationView

An annotation view that displays a pin image on the map.

iOS 3.0–16.0DeprecatediPadOS 3.0–16.0DeprecatedMac Catalyst 13.1–16.0DeprecatedmacOS 10.9–13.0DeprecatedtvOS 9.2–16.0DeprecatedvisionOS 1.0–1.0Deprecated

@MainActor
class MKPinAnnotationView

## Overview

Return instances of this class from the `mapView(_:viewFor:)` method of your map view delegate when you want to display a pin for one of your annotations. The pins displayed by this view are the same ones found in the Maps application. You can specify the type of pin you want to display and whether you want the pin to be animated into place.

## Topics

### Getting Standard Pin Colors

Returns the standard color for red pins.

Returns the standard color for green pins.

Returns the standard color for purple pins.

`enum MKPinAnnotationColor`

The supported colors for pin annotations.

### Getting and Setting Attributes

`var pinTintColor: UIColor!`

The color of the pin head.

`var animatesDrop: Bool`

A Boolean value indicating whether the annotation view is animated onto the screen.

`var pinColor: MKPinAnnotationColor`

## Relationships

### Inherits From

- `MKAnnotationView`

### Conforms To

- `CALayerDelegate`
- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSAccessibilityElementProtocol`
- `NSAccessibilityProtocol`
- `NSAnimatablePropertyContainer`
- `NSAppearanceCustomization`
- `NSCoding`
- `NSDraggingDestination`
- `NSObjectProtocol`
- `NSStandardKeyBindingResponding`
- `NSTouchBarProvider`
- `NSUserActivityRestoring`
- `NSUserInterfaceItemIdentification`
- `Sendable`
- `SendableMetatype`
- `UIAccessibilityIdentification`
- `UIActivityItemsConfigurationProviding`
- `UIAppearance`
- `UIAppearanceContainer`
- `UICoordinateSpace`
- `UIDynamicItem`
- `UIFocusEnvironment`
- `UIFocusItem`
- `UIFocusItemContainer`
- `UILargeContentViewerItem`
- `UIPasteConfigurationSupporting`
- `UIPopoverPresentationControllerSourceItem`
- `UIResponderStandardEditActions`
- `UITraitChangeObservable`
- `UITraitEnvironment`
- `UIUserActivityRestoring`

## See Also

### Classes

`class MKCircleView`

Provides the visual representation for an `MKCircle` annotation object.

Deprecated

`class MKOverlayView`

Defines the basic behavior associated with all overlay views.

`class MKOverlayPathView`

Represents a generic overlay that draws its contents using a Core Graphics path data type.

`class MKPolygonView`

Provides the visual representation for an `MKPolygon` annotation object.

`class MKPolylineView`

Provides the visual representation for an `MKPolyline` annotation object.

---

# https://developer.apple.com/documentation/mapkit/mklocalsearchcompleter/filtertype-swift.property

- MapKit
- MKLocalSearchCompleter
- filterType Deprecated

Instance Property

# filterType

The filter options for the search results.

iOS 9.3–13.0DeprecatediPadOS 9.3–13.0DeprecatedMac Catalyst 13.1–13.1DeprecatedmacOS 10.11.4–10.15DeprecatedtvOS 9.2–13.0Deprecated

var filterType: MKLocalSearchCompleter.FilterType { get set }

## Discussion

Use this property to determine whether you want completions that represent points-of-interest or whether completions might yield additional relevant query strings.

## See Also

### Properties

`var pinColor: MKPinAnnotationColor`

The color of the pin head.

Deprecated

`var showsPointsOfInterest: Bool`

A Boolean value that indicates whether the map displays point-of-interest information.

`var mapType: MKMapType`

The map’s visual style.

---

# https://developer.apple.com/documentation/mapkit/mkpinannotationview/pincolor

- MapKit
- MKPinAnnotationView
- pinColor Deprecated

Instance Property

# pinColor

The color of the pin head.

iOS 3.0–9.0DeprecatediPadOS 3.0–9.0DeprecatedMac Catalyst 13.1–13.1DeprecatedmacOS 10.9–10.11Deprecated

@MainActor
var pinColor: MKPinAnnotationColor { get set }

## Discussion

The Maps application uses different pin colors for different types of map annotations. Your own map annotation should use the available pin colors in the same way. For a description of when to use each type of pin, see the constants of `MKPinAnnotationColor`.

## See Also

### Properties

`var filterType: MKLocalSearchCompleter.FilterType`

The filter options for the search results.

Deprecated

`var showsPointsOfInterest: Bool`

A Boolean value that indicates whether the map displays point-of-interest information.

`var mapType: MKMapType`

The map’s visual style.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/showspointsofinterest

- MapKit
- MKMapView
- showsPointsOfInterest Deprecated

Instance Property

# showsPointsOfInterest

A Boolean value that indicates whether the map displays point-of-interest information.

iOS 7.0–13.0DeprecatediPadOS 7.0–13.0DeprecatedMac Catalyst 13.1–13.1DeprecatedmacOS 10.9–10.15DeprecatedtvOS 9.2–13.0Deprecated

@MainActor
var showsPointsOfInterest: Bool { get set }

## Discussion

When this property is set to `true`, the map displays icons and labels for restaurants, schools, and other relevant points of interest. The `mapType` property must be set to `MKMapType.standard` or `MKMapType.hybrid` for points of interest to be displayed.The default value of this property is `true`.

## See Also

### Properties

`var filterType: MKLocalSearchCompleter.FilterType`

The filter options for the search results.

Deprecated

`var pinColor: MKPinAnnotationColor`

The color of the pin head.

`var showsPointsOfInterest: Bool`

`var mapType: MKMapType`

The map’s visual style.

---

# https://developer.apple.com/documentation/mapkit/mkmapsnapshotter/options/showspointsofinterest

- MapKit
- MKMapSnapshotter
- MKMapSnapshotter.Options
- showsPointsOfInterest Deprecated

Instance Property

# showsPointsOfInterest

A Boolean value that indicates whether the map displays point-of-interest information.

iOS 7.0–13.0DeprecatediPadOS 7.0–13.0DeprecatedMac Catalyst 13.1–13.1DeprecatedmacOS 10.9–10.15DeprecatedtvOS 9.2–13.0Deprecated

var showsPointsOfInterest: Bool { get set }

## Discussion

When this property is set to `true`, the map displays icons and labels for restaurants, schools, and other relevant points of interest. The default value of this property is `true`.

## See Also

### Properties

`var filterType: MKLocalSearchCompleter.FilterType`

The filter options for the search results.

Deprecated

`var pinColor: MKPinAnnotationColor`

The color of the pin head.

`var showsPointsOfInterest: Bool`

`var mapType: MKMapType`

The map’s visual style.

---

# https://developer.apple.com/documentation/mapkit/mkmapsnapshotter/options/maptype

- MapKit
- MKMapSnapshotter
- MKMapSnapshotter.Options
- mapType Deprecated

Instance Property

# mapType

The map’s visual style.

iOS 7.0–26.2DeprecatediPadOS 7.0–26.2DeprecatedmacOS 10.9–26.2DeprecatedvisionOS 1.0–26.2Deprecated

var mapType: MKMapType { get set }

## Discussion

The default value of this property is `MKMapType.standard`.

## See Also

### Properties

`var filterType: MKLocalSearchCompleter.FilterType`

The filter options for the search results.

Deprecated

`var pinColor: MKPinAnnotationColor`

The color of the pin head.

`var showsPointsOfInterest: Bool`

A Boolean value that indicates whether the map displays point-of-interest information.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/view(for:)-38z60

-38z60#app-main)

- MapKit
- MKMapView
- view(for:) Deprecated

Instance Method

# view(for:)

Returns the view associated with the overlay object, if any.

iOS 4.0–13.0DeprecatediPadOS 4.0–13.0DeprecatedMac Catalyst 13.1–13.1Deprecated

@MainActor

## Parameters

`overlay`

The overlay object whose view you want.

## Return Value

The view associated with the overlay object or `nil` if the overlay is not onscreen.

## See Also

### Methods

[`func mapView(MKMapView, didAddOverlayViews: [Any])`](https://developer.apple.com/documentation/mapkit/mkmapviewdelegate/mapview(_:didaddoverlayviews:))

Tells the delegate when the map adds one or more overlay views to the map.

Deprecated

Asks the delegate for the overlay view to use when displaying the specified overlay object.

---

# https://developer.apple.com/documentation/mapkit/mkmapviewdelegate/mapview(_:viewfor:)-6j267

-6j267#app-main)

- MapKit
- MKMapViewDelegate
- mapView(\_:viewFor:) Deprecated

Instance Method

# mapView(\_:viewFor:)

Asks the delegate for the overlay view to use when displaying the specified overlay object.

iOS 4.0–13.0DeprecatediPadOS 4.0–13.0DeprecatedMac Catalyst 13.1–13.1Deprecated

@MainActor
optional func mapView(
_ mapView: MKMapView,
viewFor overlay: any MKOverlay

## Parameters

`mapView`

The map view that requests the overlay view.

`overlay`

The object representing the overlay that the map view is about to display.

## Return Value

The view to use when presenting the specified overlay on the map. If you return `nil`, no view displays for the specified overlay object.

## See Also

### Methods

Returns the view associated with the overlay object, if any.

Deprecated

[`func mapView(MKMapView, didAddOverlayViews: [Any])`](https://developer.apple.com/documentation/mapkit/mkmapviewdelegate/mapview(_:didaddoverlayviews:))

Tells the delegate when the map adds one or more overlay views to the map.

---

# https://developer.apple.com/documentation/mapkit/mappin

- MapKit
- MapPin Deprecated

Structure

# MapPin

A pin-shaped annotation used to indicate a location on a map.

MapKitSwiftUIiOS 14.0–16.0DeprecatediPadOS 14.0–16.0DeprecatedMac CatalystmacOS 11.0–13.0DeprecatedtvOS 14.0–16.0DeprecatedvisionOSwatchOS 7.0–9.0Deprecated

struct MapPin

## Overview

Create a `Map` and display pin annotations by returning a view that conforms to `MapAnnotationProtocol`, such as `MapPin`, from the trailing closure of `init(coordinateRegion:interactionModes:showsUserLocation:userTrackingMode:annotationItems:annotationContent:)` or `init(mapRect:interactionModes:showsUserLocation:userTrackingMode:annotationItems:annotationContent:)`. Items you provide as a collection to the source annotations need to conform to `Identifiable`.

For example, the following code displays a map with a pin annotation:

struct IdentifiablePlace: Identifiable {
let id: UUID
let location: CLLocationCoordinate2D
init(id: UUID = UUID(), lat: Double, long: Double) {
self.id = id
self.location = CLLocationCoordinate2D(
latitude: lat,
longitude: long)
}
}

struct PinAnnotationMapView: View {
let place: IdentifiablePlace
@State var region: MKCoordinateRegion

var body: some View {
Map(coordinateRegion: $region,
annotationItems: [place])
{ place in
MapPin(coordinate: place.location,
tint: Color.purple)
}
}
}

## Topics

### Creating a map pin

`init(coordinate: CLLocationCoordinate2D, tint: Color?)`

Creates a map pin at the map location that you specify.

## Relationships

### Conforms To

- `MapAnnotationProtocol`

---

# https://developer.apple.com/documentation/mapkit/mklocalsearchcompleter/filtertype-swift.enum

- MapKit
- MKLocalSearchCompleter
- MKLocalSearchCompleter.FilterType Deprecated

Enumeration

# MKLocalSearchCompleter.FilterType

Constants indicating the types of search completions to return.

iOS 9.3–13.0DeprecatediPadOS 9.3–13.0DeprecatedMac Catalyst 13.1–13.1DeprecatedmacOS 10.11.4–10.15DeprecatedtvOS 9.2–13.0Deprecated

enum FilterType

## Topics

### Constants

`case locationsAndQueries`

Points of interest and query suggestions. Specify this value when you want both map-based points of interest and common query terms used to find locations. For example, the search string `cof` yields a completion for _coffee_.

`case locationsOnly`

Points of interest only. Specify this value when you want the search string to yield completions that correspond to a specific point-of-interest on the map.

### Initializers

`init?(rawValue: Int)`

## Relationships

### Conforms To

- `BitwiseCopyable`
- `Equatable`
- `Hashable`
- `RawRepresentable`
- `Sendable`
- `SendableMetatype`

## See Also

### Enumerations

`enum MKMapType`

The type of map to display.

Deprecated

`enum MKPinAnnotationColor`

The supported colors for pin annotations.

---

# https://developer.apple.com/documentation/mapkit/mkmaptype

- MapKit
- MKMapType Deprecated

Enumeration

# MKMapType

The type of map to display.

enum MKMapType

## Topics

### Constants

`case standard`

A street map that shows the position of all roads and some road names.

`case satellite`

Satellite imagery of the area.

`case hybrid`

A satellite image of the area with road and road name information layered on top.

`case satelliteFlyover`

A satellite image of the area with flyover data where available.

`case hybridFlyover`

A hybrid satellite image with flyover data where available.

`case mutedStandard`

A street map where MapKit emphasizes your data over the underlying map details.

### Initializers

`init?(rawValue: UInt)`

## Relationships

### Conforms To

- `BitwiseCopyable`
- `Equatable`
- `Hashable`
- `RawRepresentable`
- `Sendable`
- `SendableMetatype`

## See Also

### Enumerations

`enum FilterType`

Constants indicating the types of search completions to return.

Deprecated

`enum MKPinAnnotationColor`

The supported colors for pin annotations.

---

# https://developer.apple.com/documentation/mapkit/mkpinannotationcolor

- MapKit
- MKPinAnnotationColor Deprecated

Enumeration

# MKPinAnnotationColor

The supported colors for pin annotations.

iOS 3.0–9.0DeprecatediPadOS 3.0–9.0DeprecatedMac Catalyst 13.1–13.1DeprecatedmacOS 10.9–10.11Deprecated

enum MKPinAnnotationColor

## Topics

### Constants

`case red`

`case green`

`case purple`

### Initializers

`init?(rawValue: UInt)`

## Relationships

### Conforms To

- `BitwiseCopyable`
- `Equatable`
- `Hashable`
- `RawRepresentable`
- `Sendable`
- `SendableMetatype`

## See Also

### Enumerations

`enum FilterType`

Constants indicating the types of search completions to return.

Deprecated

`enum MKMapType`

The type of map to display.

---

# https://developer.apple.com/documentation/mapkit/mkcircleview)



---

# https://developer.apple.com/documentation/mapkit/mkcircle)



---

# https://developer.apple.com/documentation/mapkit/mkoverlayview)



---

# https://developer.apple.com/documentation/mapkit/mkoverlaypathview)



---

# https://developer.apple.com/documentation/mapkit/mkpolygonview)



---

# https://developer.apple.com/documentation/mapkit/mkpolygon)



---

# https://developer.apple.com/documentation/mapkit/mkpolylineview)



---

# https://developer.apple.com/documentation/mapkit/mkpolyline)



---

# https://developer.apple.com/documentation/mapkit/mkpinannotationview)



---

# https://developer.apple.com/documentation/mapkit/mklocalsearchcompleter/filtertype-swift.property)

# The page you're looking for can't be found.

Search developer.apple.comSearch Icon

---

# https://developer.apple.com/documentation/mapkit/mkpinannotationview/pincolor)



---

# https://developer.apple.com/documentation/mapkit/mkmapview/showspointsofinterest)



---

# https://developer.apple.com/documentation/mapkit/mkmapsnapshotter/options/showspointsofinterest)

# The page you're looking for can't be found.

Search developer.apple.comSearch Icon

---

# https://developer.apple.com/documentation/mapkit/mkmapsnapshotter/options/maptype)



---

# https://developer.apple.com/documentation/mapkit/mkmapview/view(for:)-38z60)



---

# https://developer.apple.com/documentation/mapkit/mkmapviewdelegate/mapview(_:didaddoverlayviews:))

)#app-main)

# The page you're looking for can't be found.

Search developer.apple.comSearch Icon

---

# https://developer.apple.com/documentation/mapkit/mkmapviewdelegate/mapview(_:viewfor:)-6j267)

-6j267)#app-main)

# The page you're looking for can't be found.

Search developer.apple.comSearch Icon

---

# https://developer.apple.com/documentation/mapkit/mappin)



---

# https://developer.apple.com/documentation/mapkit/mklocalsearchcompleter/filtertype-swift.enum)

# The page you're looking for can't be found.

Search developer.apple.comSearch Icon

---

# https://developer.apple.com/documentation/mapkit/mkmaptype)



---

# https://developer.apple.com/documentation/mapkit/mkpinannotationcolor)



---

# https://developer.apple.com/documentation/mapkit/anymapcontent/init(_:)

#app-main)

- MapKit
- AnyMapContent
- init(\_:)

Initializer

# init(\_:)

Create an instance that type-erases `base`.

MapKitSwiftUIMac Catalyst

@MainActor @preconcurrency

---

# https://developer.apple.com/documentation/mapkit/anymapcontent/init(_:))



---

# https://developer.apple.com/documentation/mapkit/mkcoordinatespan/init()

#app-main)

- MapKit
- MKCoordinateSpan
- init()

Initializer

# init()

Creates a coordinate span that represents a width and height on a map.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

init()

## See Also

### Creating a coordinate span

`init(latitudeDelta: CLLocationDegrees, longitudeDelta: CLLocationDegrees)`

Creates a new `MKCoordinateSpan` from the specified values.

---

# https://developer.apple.com/documentation/mapkit/mkcoordinatespan/init(latitudedelta:longitudedelta:)

#app-main)

- MapKit
- MKCoordinateSpan
- init(latitudeDelta:longitudeDelta:)

Initializer

# init(latitudeDelta:longitudeDelta:)

Creates a new `MKCoordinateSpan` from the specified values.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

init(
latitudeDelta: CLLocationDegrees,
longitudeDelta: CLLocationDegrees
)

## Parameters

`latitudeDelta`

The amount of north-to-south distance (measured in degrees) to use for the span. Unlike longitudinal distances, which vary based on the latitude, one degree of latitude is approximately 111 kilometers (69 miles) at all times.

`longitudeDelta`

The amount of east-to-west distance (measured in degrees) to use for the span. The number of kilometers spanned by a longitude range varies based on the current latitude. For example, one degree of longitude spans a distance of approximately 111 kilometers (69 miles) at the equator but shrinks to 0 kilometers at the poles.

## Return Value

A span with the specified delta values.

## See Also

### Creating a coordinate span

`init()`

Creates a coordinate span that represents a width and height on a map.

---

# https://developer.apple.com/documentation/mapkit/mkcoordinatespan/latitudedelta

- MapKit
- MKCoordinateSpan
- latitudeDelta

Instance Property

# latitudeDelta

The amount of north-to-south distance (measured in degrees) to display on the map.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

var latitudeDelta: CLLocationDegrees

## Discussion

Unlike longitudinal distances, which vary based on the latitude, one degree of latitude is always approximately 111 kilometers (69 miles).

## See Also

### Related Documentation

Location and Maps Programming Guide

### Getting the span coordinates

`var longitudeDelta: CLLocationDegrees`

The amount of east-to-west distance (measured in degrees) to display for the map region.

---

# https://developer.apple.com/documentation/mapkit/mkcoordinatespan/longitudedelta

- MapKit
- MKCoordinateSpan
- longitudeDelta

Instance Property

# longitudeDelta

The amount of east-to-west distance (measured in degrees) to display for the map region.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

var longitudeDelta: CLLocationDegrees

## Discussion

The number of kilometers spanned by a longitude range varies based on the current latitude. For example, one degree of longitude spans a distance of approximately 111 kilometers (69 miles) at the equator but shrinks to 0 kilometers at the poles.

## See Also

### Getting the span coordinates

`var latitudeDelta: CLLocationDegrees`

The amount of north-to-south distance (measured in degrees) to display on the map.

---

# https://developer.apple.com/documentation/mapkit/mkcoordinatespan/init())



---

# https://developer.apple.com/documentation/mapkit/mkcoordinatespan/init(latitudedelta:longitudedelta:))

)#app-main)

# The page you're looking for can't be found.

Search developer.apple.comSearch Icon

---

# https://developer.apple.com/documentation/mapkit/mkcoordinatespan/latitudedelta)



---

# https://developer.apple.com/documentation/mapkit/mkcoordinatespan/longitudedelta)



---

# https://developer.apple.com/documentation/mapkit/mkcoordinateregion/init()

#app-main)

- MapKit
- MKCoordinateRegion
- init()

Initializer

# init()

Creates a coordinate region.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

init()

## See Also

### Creating a region

`init(center: CLLocationCoordinate2D, latitudinalMeters: CLLocationDistance, longitudinalMeters: CLLocationDistance)`

Creates a new coordinate region from the specified coordinate and distance values.

`init(MKMapRect)`

Returns the region that corresponds to the specified map rectangle.

`init(center: CLLocationCoordinate2D, span: MKCoordinateSpan)`

Creates a coordinate region with a span around the specified center coordinate.

---

# https://developer.apple.com/documentation/mapkit/mkcoordinateregion/init(center:latitudinalmeters:longitudinalmeters:)

#app-main)

- MapKit
- MKCoordinateRegion
- init(center:latitudinalMeters:longitudinalMeters:)

Initializer

# init(center:latitudinalMeters:longitudinalMeters:)

Creates a new coordinate region from the specified coordinate and distance values.

iOSiPadOSMac CatalystmacOSvisionOSwatchOS

init(
center centerCoordinate: CLLocationCoordinate2D,
latitudinalMeters: CLLocationDistance,
longitudinalMeters: CLLocationDistance
)

## Parameters

`centerCoordinate`

The center point of the new coordinate region.

`latitudinalMeters`

The north-to-south span of the region (measured in meters) specified as the distance from the center point to the bounds along the north-to-south axis.

`longitudinalMeters`

The east-to-west span of the region (measured in meters) specified as the distance from the center point to the bounds along the east-to-west axis.

## Return Value

A region with the specified values.

## See Also

### Creating a region

`init()`

Creates a coordinate region.

`init(MKMapRect)`

Returns the region that corresponds to the specified map rectangle.

`init(center: CLLocationCoordinate2D, span: MKCoordinateSpan)`

Creates a coordinate region with a span around the specified center coordinate.

---

# https://developer.apple.com/documentation/mapkit/mkcoordinateregion/init(_:)

#app-main)

- MapKit
- MKCoordinateRegion
- init(\_:)

Initializer

# init(\_:)

Returns the region that corresponds to the specified map rectangle.

init(_ rect: MKMapRect)

## Parameters

`rect`

The map rectangle that corresponds to the desired region on a two-dimensional map projection.

## Return Value

The region structure specifying the latitude, longitude, and span values for the specified rectangle.

## See Also

### Creating a region

`init()`

Creates a coordinate region.

`init(center: CLLocationCoordinate2D, latitudinalMeters: CLLocationDistance, longitudinalMeters: CLLocationDistance)`

Creates a new coordinate region from the specified coordinate and distance values.

`init(center: CLLocationCoordinate2D, span: MKCoordinateSpan)`

Creates a coordinate region with a span around the specified center coordinate.

---

# https://developer.apple.com/documentation/mapkit/mkcoordinateregion/init(center:span:)

#app-main)

- MapKit
- MKCoordinateRegion
- init(center:span:)

Initializer

# init(center:span:)

Creates a coordinate region with a span around the specified center coordinate.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

init(
center: CLLocationCoordinate2D,
span: MKCoordinateSpan
)

## Parameters

`center`

The center of the coordinate region.

`span`

The span around the center of the coordinate region.

## See Also

### Creating a region

`init()`

Creates a coordinate region.

`init(center: CLLocationCoordinate2D, latitudinalMeters: CLLocationDistance, longitudinalMeters: CLLocationDistance)`

Creates a new coordinate region from the specified coordinate and distance values.

`init(MKMapRect)`

Returns the region that corresponds to the specified map rectangle.

---

# https://developer.apple.com/documentation/mapkit/mkcoordinateregion/center

- MapKit
- MKCoordinateRegion
- center

Instance Property

# center

The center point of the region.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

var center: CLLocationCoordinate2D

## See Also

### Getting the region coordinates

`var span: MKCoordinateSpan`

The horizontal and vertical span representing the amount of map to display.

---

# https://developer.apple.com/documentation/mapkit/mkcoordinateregion/span

- MapKit
- MKCoordinateRegion
- span

Instance Property

# span

The horizontal and vertical span representing the amount of map to display.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

var span: MKCoordinateSpan

## Discussion

The span also defines the current zoom level used by the map view object.

## See Also

### Getting the region coordinates

`var center: CLLocationCoordinate2D`

The center point of the region.

---

# https://developer.apple.com/documentation/mapkit/mkcoordinateregion/init())



---

# https://developer.apple.com/documentation/mapkit/mkcoordinateregion/init(center:latitudinalmeters:longitudinalmeters:))

)#app-main)

# The page you're looking for can't be found.

Search developer.apple.comSearch Icon

---

# https://developer.apple.com/documentation/mapkit/mkcoordinateregion/init(_:))



---

# https://developer.apple.com/documentation/mapkit/mkcoordinateregion/init(center:span:))

)#app-main)

# The page you're looking for can't be found.

Search developer.apple.comSearch Icon

---

# https://developer.apple.com/documentation/mapkit/mkcoordinateregion/center)



---

# https://developer.apple.com/documentation/mapkit/mkcoordinateregion/span)



---

# https://developer.apple.com/documentation/mapkit/mkdirections).



---

# https://developer.apple.com/documentation/mapkit/mkmapitem/openmaps(with:launchoptions:)

#app-main)

- MapKit
- MKMapItem
- openMaps(with:launchOptions:)

Type Method

# openMaps(with:launchOptions:)

Opens the Maps app and displays the specified map items.

class func openMaps(
with mapItems: [MKMapItem],
launchOptions: [String : Any]? = nil

## Parameters

`mapItems`

An array containing one or more `MKMapItem` objects representing the items you want to display on the map.

`launchOptions`

Additional information that the Maps app can use to configure the map display. For example, you can use the launch options to specify the visible map region, a 3D perspective, and the map type. For a list of keys you can put into this dictionary, see Launch options dictionary keys.

You may specify `nil` for this parameter.

## Return Value

`true` if the Maps app successfully opens the maps items, or `false` if there’s an error.

## Discussion

You use this method to pass one or more map items to the Maps app. For example, you might use this method to ask the Maps app to display location-based search results that your app generates. The Maps app displays pins at each location you specify and uses the contents of each map item object to display additional information.

If you specify the `MKLaunchOptionsDirectionsModeKey` option in the `launchOptions` dictionary, the `mapItems` array may have no more than two items in it. If the array contains one item, the Maps app generates directions from the user’s location to the location that the map item specifies. If the array contains two items, the Maps app generates directions from the location of the first item to the location of the second item in the array.

If you don’t include the `MKLaunchOptionsMapCenterKey` and `MKLaunchOptionsMapSpanKey` keys in your `launchOptions` dictionary, the Maps app constructs a region that encompasses the provided items. It uses this region to set the visible portion of the map.

## See Also

### Launching the Maps app

Opens the Maps app using the specified map items and options.

Opens the Maps app from a particular scene using the specified map items and options.

Opens the Maps app and displays the map item.

Opens the Maps app from a particular scene using the specified options.

---

# https://developer.apple.com/documentation/mapkit/mkmapitem/init(placemark:)

#app-main)

- MapKit
- MKMapItem
- init(placemark:) Deprecated

Initializer

# init(placemark:)

Creates and returns a map item object using the specified placemark object.

iOS 6.0–26.0DeprecatediPadOS 6.0–26.0DeprecatedMac Catalyst 13.1–26.0DeprecatedmacOS 10.9–26.0DeprecatedtvOS 9.2–26.0DeprecatedvisionOS 1.0–26.0DeprecatedwatchOS 2.0–26.0Deprecated

init(placemark: MKPlacemark)

## Parameters

`placemark`

The placemark object corresponding to the desired map location. This parameter can’t be `nil`.

## Return Value

An initialized map item object.

## Discussion

Use this method to create a map item for an existing placemark. Don’t use it to create a map item representing the user’s location. To do that, use the `forCurrentLocation()` method instead.

## See Also

### Creating map items

Creates and returns a singleton map item object representing the user’s location.

---

# https://developer.apple.com/documentation/mapkit/mkmapitem/forcurrentlocation()

#app-main)

- MapKit
- MKMapItem
- forCurrentLocation()

Type Method

# forCurrentLocation()

Creates and returns a singleton map item object representing the user’s location.

## Return Value

An `MKMapItem` object representing the user’s location.

## Discussion

For privacy reasons, and because the user’s location can change, the map item that this method returns doesn’t contain any coordinate data. When you need the actual location of the user, use the Core Location framework to retrieve it.

## See Also

### Related Documentation

Location and Maps Programming Guide

### Creating map items

`init(placemark: MKPlacemark)`

Creates and returns a map item object using the specified placemark object.

Deprecated

---

# https://developer.apple.com/documentation/mapkit/mkmapitem/identifier-swift.class

- MapKit
- MKMapItem
- MKMapItem.Identifier

Class

# MKMapItem.Identifier

A unique identifier for a place.

class Identifier

## Relationships

### Inherits From

- `NSObject`

### Conforms To

- `CVarArg`
- `Copyable`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Decodable`
- `Encodable`
- `Equatable`
- `Hashable`
- `NSCoding`
- `NSCopying`
- `NSObjectProtocol`
- `NSSecureCoding`
- `RawRepresentable`

## See Also

### Accessing the map item attributes

A set of alternative identifiers for a place.

`var identifier: MKMapItem.Identifier?`

`var isCurrentLocation: Bool`

A Boolean value that indicates whether the map item represents the user’s location.

`var name: String?`

The descriptive name associated with the map item.

`var placemark: MKPlacemark`

The placemark object containing the location information.

Deprecated

`var pointOfInterestCategory: MKPointOfInterestCategory?`

The point-of-interest category for the map item.

`var phoneNumber: String?`

The phone number associated with a business at the specified location.

`var timeZone: TimeZone?`

The time zone of the specified location.

`var url: URL?`

The URL associated with the specified location.

---

# https://developer.apple.com/documentation/mapkit/mkmapitem/alternateidentifiers

- MapKit
- MKMapItem
- alternateIdentifiers

Instance Property

# alternateIdentifiers

A set of alternative identifiers for a place.

## Mentioned in

Identifying unique locations with Place IDs

## Discussion

The identifier for a point of interest may change over time. This property provides a set of alternative identifiers for this map item.

## See Also

### Accessing the map item attributes

`class Identifier`

A unique identifier for a place.

`var identifier: MKMapItem.Identifier?`

`var isCurrentLocation: Bool`

A Boolean value that indicates whether the map item represents the user’s location.

`var name: String?`

The descriptive name associated with the map item.

`var placemark: MKPlacemark`

The placemark object containing the location information.

Deprecated

`var pointOfInterestCategory: MKPointOfInterestCategory?`

The point-of-interest category for the map item.

`var phoneNumber: String?`

The phone number associated with a business at the specified location.

`var timeZone: TimeZone?`

The time zone of the specified location.

`var url: URL?`

The URL associated with the specified location.

---

# https://developer.apple.com/documentation/mapkit/mkmapitem/identifier-swift.property

- MapKit
- MKMapItem
- identifier

Instance Property

# identifier

A unique identifier for a place.

var identifier: MKMapItem.Identifier? { get }

## Mentioned in

Identifying unique locations with Place IDs

## Discussion

An identifier uniquely identifies a place, such as a business or a landmark. You can persist an identifier and use it later to recall information about place.

## See Also

### Accessing the map item attributes

`class Identifier`

A set of alternative identifiers for a place.

`var isCurrentLocation: Bool`

A Boolean value that indicates whether the map item represents the user’s location.

`var name: String?`

The descriptive name associated with the map item.

`var placemark: MKPlacemark`

The placemark object containing the location information.

Deprecated

`var pointOfInterestCategory: MKPointOfInterestCategory?`

The point-of-interest category for the map item.

`var phoneNumber: String?`

The phone number associated with a business at the specified location.

`var timeZone: TimeZone?`

The time zone of the specified location.

`var url: URL?`

The URL associated with the specified location.

---

# https://developer.apple.com/documentation/mapkit/mkmapitem/iscurrentlocation

- MapKit
- MKMapItem
- isCurrentLocation

Instance Property

# isCurrentLocation

A Boolean value that indicates whether the map item represents the user’s location.

var isCurrentLocation: Bool { get }

## Discussion

If the value of this property is `true`, the map item represents the user’s location, and the value in the `placemark` property is `nil`.

## See Also

### Accessing the map item attributes

`class Identifier`

A unique identifier for a place.

A set of alternative identifiers for a place.

`var identifier: MKMapItem.Identifier?`

`var name: String?`

The descriptive name associated with the map item.

`var placemark: MKPlacemark`

The placemark object containing the location information.

Deprecated

`var pointOfInterestCategory: MKPointOfInterestCategory?`

The point-of-interest category for the map item.

`var phoneNumber: String?`

The phone number associated with a business at the specified location.

`var timeZone: TimeZone?`

The time zone of the specified location.

`var url: URL?`

The URL associated with the specified location.

---

# https://developer.apple.com/documentation/mapkit/mkmapitem/name

- MapKit
- MKMapItem
- name

Instance Property

# name

The descriptive name associated with the map item.

var name: String? { get set }

## Discussion

Use this property to specify the name associated with the location. For example, if there’s a business at the specified location, use this property to specify the name of the business.

If this map item represents the user’s location, the value in this property is a localized version of _Current Location_.

## See Also

### Accessing the map item attributes

`class Identifier`

A unique identifier for a place.

A set of alternative identifiers for a place.

`var identifier: MKMapItem.Identifier?`

`var isCurrentLocation: Bool`

A Boolean value that indicates whether the map item represents the user’s location.

`var placemark: MKPlacemark`

The placemark object containing the location information.

Deprecated

`var pointOfInterestCategory: MKPointOfInterestCategory?`

The point-of-interest category for the map item.

`var phoneNumber: String?`

The phone number associated with a business at the specified location.

`var timeZone: TimeZone?`

The time zone of the specified location.

`var url: URL?`

The URL associated with the specified location.

---

# https://developer.apple.com/documentation/mapkit/mkmapitem/placemark

- MapKit
- MKMapItem
- placemark Deprecated

Instance Property

# placemark

The placemark object containing the location information.

iOS 6.0–26.0DeprecatediPadOS 6.0–26.0DeprecatedMac Catalyst 13.1–26.0DeprecatedmacOS 10.9–26.0DeprecatedtvOS 9.2–26.0DeprecatedvisionOS 1.0–26.0DeprecatedwatchOS 2.0–26.0Deprecated

var placemark: MKPlacemark { get }

## Discussion

If you create the map item using the `forCurrentLocation()` method, the value of this property is `nil` and the `isCurrentLocation` property is `true`.

## See Also

### Accessing the map item attributes

`class Identifier`

A unique identifier for a place.

A set of alternative identifiers for a place.

`var identifier: MKMapItem.Identifier?`

`var isCurrentLocation: Bool`

A Boolean value that indicates whether the map item represents the user’s location.

`var name: String?`

The descriptive name associated with the map item.

`var pointOfInterestCategory: MKPointOfInterestCategory?`

The point-of-interest category for the map item.

`var phoneNumber: String?`

The phone number associated with a business at the specified location.

`var timeZone: TimeZone?`

The time zone of the specified location.

`var url: URL?`

The URL associated with the specified location.

---

# https://developer.apple.com/documentation/mapkit/mkmapitem/pointofinterestcategory

- MapKit
- MKMapItem
- pointOfInterestCategory

Instance Property

# pointOfInterestCategory

The point-of-interest category for the map item.

var pointOfInterestCategory: MKPointOfInterestCategory? { get set }

## Discussion

If the map item doesn’t correspond to a point of interest, or if the point of interest isn’t one of the known values in `MKPointOfInterestCategory`, `pointOfInterestCategory` is `nil`.

## See Also

### Accessing the map item attributes

`class Identifier`

A unique identifier for a place.

A set of alternative identifiers for a place.

`var identifier: MKMapItem.Identifier?`

`var isCurrentLocation: Bool`

A Boolean value that indicates whether the map item represents the user’s location.

`var name: String?`

The descriptive name associated with the map item.

`var placemark: MKPlacemark`

The placemark object containing the location information.

Deprecated

`var phoneNumber: String?`

The phone number associated with a business at the specified location.

`var timeZone: TimeZone?`

The time zone of the specified location.

`var url: URL?`

The URL associated with the specified location.

---

# https://developer.apple.com/documentation/mapkit/mkmapitem/phonenumber

- MapKit
- MKMapItem
- phoneNumber

Instance Property

# phoneNumber

The phone number associated with a business at the specified location.

var phoneNumber: String? { get set }

## Discussion

If there’s a relevant phone number associated with the location, such as for a business at the location, use this property to specify that value.

## See Also

### Accessing the map item attributes

`class Identifier`

A unique identifier for a place.

A set of alternative identifiers for a place.

`var identifier: MKMapItem.Identifier?`

`var isCurrentLocation: Bool`

A Boolean value that indicates whether the map item represents the user’s location.

`var name: String?`

The descriptive name associated with the map item.

`var placemark: MKPlacemark`

The placemark object containing the location information.

Deprecated

`var pointOfInterestCategory: MKPointOfInterestCategory?`

The point-of-interest category for the map item.

`var timeZone: TimeZone?`

The time zone of the specified location.

`var url: URL?`

The URL associated with the specified location.

---

# https://developer.apple.com/documentation/mapkit/mkmapitem/timezone

- MapKit
- MKMapItem
- timeZone

Instance Property

# timeZone

The time zone of the specified location.

var timeZone: TimeZone? { get set }

## Discussion

When you search for map items, MapKit populates this field with the time zone information as a convenience. You may also set the time zone for any map items you create.

## See Also

### Accessing the map item attributes

`class Identifier`

A unique identifier for a place.

A set of alternative identifiers for a place.

`var identifier: MKMapItem.Identifier?`

`var isCurrentLocation: Bool`

A Boolean value that indicates whether the map item represents the user’s location.

`var name: String?`

The descriptive name associated with the map item.

`var placemark: MKPlacemark`

The placemark object containing the location information.

Deprecated

`var pointOfInterestCategory: MKPointOfInterestCategory?`

The point-of-interest category for the map item.

`var phoneNumber: String?`

The phone number associated with a business at the specified location.

`var url: URL?`

The URL associated with the specified location.

---

# https://developer.apple.com/documentation/mapkit/mkmapitem/url

- MapKit
- MKMapItem
- url

Instance Property

# url

The URL associated with the specified location.

var url: URL? { get set }

## Discussion

If there’s a relevant URL associated with the location, such as for a business at the location, use this property to specify that value.

## See Also

### Accessing the map item attributes

`class Identifier`

A unique identifier for a place.

A set of alternative identifiers for a place.

`var identifier: MKMapItem.Identifier?`

`var isCurrentLocation: Bool`

A Boolean value that indicates whether the map item represents the user’s location.

`var name: String?`

The descriptive name associated with the map item.

`var placemark: MKPlacemark`

The placemark object containing the location information.

Deprecated

`var pointOfInterestCategory: MKPointOfInterestCategory?`

The point-of-interest category for the map item.

`var phoneNumber: String?`

The phone number associated with a business at the specified location.

`var timeZone: TimeZone?`

The time zone of the specified location.

---

# https://developer.apple.com/documentation/mapkit/mkmapitemtypeidentifier

- MapKit
- MKMapItemTypeIdentifier

Global Variable

# MKMapItemTypeIdentifier

A constant that indicates the type of a serialized map item.

let MKMapItemTypeIdentifier: String

---

# https://developer.apple.com/documentation/mapkit/launch-options-dictionary-keys

Collection

- MapKit
- MapKit for AppKit and UIKit
- MKMapItem
- Launch options dictionary keys

API Collection

# Launch options dictionary keys

Launch options to specify when opening map items in the Maps app.

## Overview

You specify these keys in the launch options dictionary for the `openMaps(with:launchOptions:)` or `openInMaps(launchOptions:)` method.

## Topics

### Launch options

`let MKLaunchOptionsDirectionsModeKey: String`

The mode of transportation.

`let MKLaunchOptionsMapTypeKey: String`

The type of map (standard, satellite, or hybrid) to display.

`let MKLaunchOptionsMapCenterKey: String`

The coordinate value on which to center the map.

`let MKLaunchOptionsMapSpanKey: String`

The amount of the map to display.

`let MKLaunchOptionsShowsTrafficKey: String`

A Boolean value that indicates whether to display traffic information.

`let MKLaunchOptionsCameraKey: String`

The virtual camera to use for viewing the map.

## See Also

### Opening items at launch time

Strings that represent the possible values of the launch options direction mode key.

---

# https://developer.apple.com/documentation/mapkit/directions-mode-values

Collection

- MapKit
- MapKit for AppKit and UIKit
- MKMapItem
- Directions mode values

API Collection

# Directions mode values

Strings that represent the possible values of the launch options direction mode key.

## Overview

For a list of possible values, see the `MKLaunchOptionsDirectionsModeKey` documentation.

## Topics

### Directions keys

`let MKLaunchOptionsDirectionsModeDriving: String`

Driving directions between the specified start and end points.

`let MKLaunchOptionsDirectionsModeWalking: String`

Walking directions between the specified start and end points.

`let MKLaunchOptionsDirectionsModeTransit: String`

Public transit directions between the specified start and end points.

`let MKLaunchOptionsDirectionsModeCycling: String`

Cycling directions between the specified start and end points.

`let MKLaunchOptionsDirectionsModeDefault: String`

Directions that match the user’s preferred transportation type.

## See Also

### Opening items at launch time

Launch options to specify when opening map items in the Maps app.

---

# https://developer.apple.com/documentation/mapkit/mkmapitem/init(coder:)

#app-main)

- MapKit
- MKMapItem
- init(coder:)

Initializer

# init(coder:)

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

init?(coder: NSCoder)

---

# https://developer.apple.com/documentation/mapkit/mkmapitem/init(location:address:)

#app-main)

- MapKit
- MKMapItem
- init(location:address:)

Initializer

# init(location:address:)

Creates and returns a map item object using the specified location and address objects.

init(
location: CLLocation,
address: MKAddress?
)

## Parameters

`location`

A `CLLocation`.

`address`

An `MKAddress`.

## Return Value

An initialized map item object.

## Discussion

Use this method to create a map item for a specific location. Don’t use it to create a map item representing the current location of someone’s device, instead use the \`\`\`MKMapItem/forCurrentLocation()\`\` method.

---

# https://developer.apple.com/documentation/mapkit/mkmapitem/address

- MapKit
- MKMapItem
- address

Instance Property

# address

The address object.

var address: MKAddress? { get }

---

# https://developer.apple.com/documentation/mapkit/mkmapitem/addressrepresentations

- MapKit
- MKMapItem
- addressRepresentations

Instance Property

# addressRepresentations

The address representations object that contains various address representations useful for display purposes.

var addressRepresentations: MKAddressRepresentations? { get }

---

# https://developer.apple.com/documentation/mapkit/mkmapitem/location

- MapKit
- MKMapItem
- location

Instance Property

# location

The location object.

var location: CLLocation { get }

---

# https://developer.apple.com/documentation/mapkit/mkmapitem/openmaps(with:launchoptions:))

)#app-main)

# The page you're looking for can't be found.

Search developer.apple.comSearch Icon

---

# https://developer.apple.com/documentation/mapkit/mkmapitem/init(placemark:))



---

# https://developer.apple.com/documentation/mapkit/mkmapitem/forcurrentlocation())



---

# https://developer.apple.com/documentation/mapkit/mkmapitem/identifier-swift.class)



---

# https://developer.apple.com/documentation/mapkit/mkmapitem/alternateidentifiers)



---

# https://developer.apple.com/documentation/mapkit/mkmapitem/identifier-swift.property)



---

# https://developer.apple.com/documentation/mapkit/mkmapitem/iscurrentlocation)



---

# https://developer.apple.com/documentation/mapkit/mkmapitem/name)



---

# https://developer.apple.com/documentation/mapkit/mkmapitem/placemark)



---

# https://developer.apple.com/documentation/mapkit/mkmapitem/pointofinterestcategory)



---

# https://developer.apple.com/documentation/mapkit/mkmapitem/phonenumber)



---

# https://developer.apple.com/documentation/mapkit/mkmapitem/timezone)



---

# https://developer.apple.com/documentation/mapkit/mkmapitem/url)



---

# https://developer.apple.com/documentation/mapkit/mkmapitem/openmaps(with:launchoptions:completionhandler:))

)#app-main)

# The page you're looking for can't be found.

Search developer.apple.comSearch Icon

---

# https://developer.apple.com/documentation/mapkit/mkmapitem/openmaps(with:launchoptions:from:completionhandler:))

)#app-main)

# The page you're looking for can't be found.

Search developer.apple.comSearch Icon

---

# https://developer.apple.com/documentation/mapkit/mkmapitem/openinmaps(launchoptions:))

)#app-main)

# The page you're looking for can't be found.

Search developer.apple.comSearch Icon

---

# https://developer.apple.com/documentation/mapkit/mkmapitem/openinmaps(launchoptions:completionhandler:))

)#app-main)

# The page you're looking for can't be found.

Search developer.apple.comSearch Icon

---

# https://developer.apple.com/documentation/mapkit/mkmapitem/openinmaps(launchoptions:from:completionhandler:))

)#app-main)

# The page you're looking for can't be found.

Search developer.apple.comSearch Icon

---

# https://developer.apple.com/documentation/mapkit/mkmapitemtypeidentifier)



---

# https://developer.apple.com/documentation/mapkit/launch-options-dictionary-keys)



---

# https://developer.apple.com/documentation/mapkit/directions-mode-values)



---

# https://developer.apple.com/documentation/mapkit/mkmapitem/init(coder:))



---

# https://developer.apple.com/documentation/mapkit/mkmapitem/init(location:address:))



---

# https://developer.apple.com/documentation/mapkit/mkmapitem/address)



---

# https://developer.apple.com/documentation/mapkit/mkmapitem/addressrepresentations)



---

# https://developer.apple.com/documentation/mapkit/mkmapitem/location)



---

# https://developer.apple.com/documentation/mapkit/mkstandardmapconfiguration

- MapKit
- MKStandardMapConfiguration

Class

# MKStandardMapConfiguration

The class that represents the default map presentation, which is a street map that shows the position of all roads and some road names.

class MKStandardMapConfiguration

## Topics

### Creating a standard map configuration

`init()`

Creates a new standard map configuration.

`convenience init(elevationStyle: MKMapConfiguration.ElevationStyle)`

Creates a new standard map configuration with the specified elevation style.

`convenience init(elevationStyle: MKMapConfiguration.ElevationStyle, emphasisStyle: MKStandardMapConfiguration.EmphasisStyle)`

Creates a standard map configuration with the specified elevation and emphasis styles.

`convenience init(emphasisStyle: MKStandardMapConfiguration.EmphasisStyle)`

Creates a standard map configuration with the specified emphasis style.

`enum ElevationStyle`

Values that control the map’s elevation style.

`enum EmphasisStyle`

Values that control how the framework emphasizes map features.

### Customizing the map display

`var emphasisStyle: MKStandardMapConfiguration.EmphasisStyle`

The value that indicates how the framework emphasizes map features.

`var pointOfInterestFilter: MKPointOfInterestFilter?`

The filter used to determine the points of interest shown on the map.

`var showsTraffic: Bool`

A Boolean value that controls whether the map displays traffic conditions.

## Relationships

### Inherits From

- `MKMapConfiguration`

### Conforms To

- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSCoding`
- `NSCopying`
- `NSObjectProtocol`
- `NSSecureCoding`

## See Also

### Configuring the map appearance

`var preferredConfiguration: MKMapConfiguration`

The characteristics of the map view, including the map type and features the map displays.

`var pitchButtonVisibility: MKFeatureVisibility`

A value that indicates whether the map’s pitch button is visible.

`var showsUserTrackingButton: Bool`

A Boolean value that indicates whether the map displays the user tracking button.

`class MKMapConfiguration`

An abstract class that represents the shared elements of map configurations.

`class MKHybridMapConfiguration`

The class that represents a satellite image of the area with road and road name information layers on top.

`class MKImageryMapConfiguration`

The class that represents an imagery-based map presentation, such as one using satellite imagery.

---

# https://developer.apple.com/documentation/mapkit/mkhybridmapconfiguration

- MapKit
- MKHybridMapConfiguration

Class

# MKHybridMapConfiguration

The class that represents a satellite image of the area with road and road name information layers on top.

class MKHybridMapConfiguration

## Topics

### Creating a hybrid map configuration

`init()`

Creates a new hybrid map configuration.

`convenience init(elevationStyle: MKMapConfiguration.ElevationStyle)`

Creates a new hybrid map configuration with the specified elevation style.

`enum ElevationStyle`

Values that control the map’s elevation style.

### Controlling what the map displays

`var pointOfInterestFilter: MKPointOfInterestFilter?`

The filter the framework uses to determine the points of interest to show on the map.

`var showsTraffic: Bool`

A Boolean value that indicates whether the maps shows traffic conditions.

## Relationships

### Inherits From

- `MKMapConfiguration`

### Conforms To

- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSCoding`
- `NSCopying`
- `NSObjectProtocol`
- `NSSecureCoding`

## See Also

### Configuring the map appearance

`var preferredConfiguration: MKMapConfiguration`

The characteristics of the map view, including the map type and features the map displays.

`var pitchButtonVisibility: MKFeatureVisibility`

A value that indicates whether the map’s pitch button is visible.

`var showsUserTrackingButton: Bool`

A Boolean value that indicates whether the map displays the user tracking button.

`class MKMapConfiguration`

An abstract class that represents the shared elements of map configurations.

`class MKStandardMapConfiguration`

The class that represents the default map presentation, which is a street map that shows the position of all roads and some road names.

`class MKImageryMapConfiguration`

The class that represents an imagery-based map presentation, such as one using satellite imagery.

---

# https://developer.apple.com/documentation/mapkit/mkimagerymapconfiguration

- MapKit
- MKImageryMapConfiguration

Class

# MKImageryMapConfiguration

The class that represents an imagery-based map presentation, such as one using satellite imagery.

class MKImageryMapConfiguration

## Topics

### Creating a map imagery configuration

`init()`

Creates a new imagery based map configuration.

`convenience init(elevationStyle: MKMapConfiguration.ElevationStyle)`

Creates a new imagery based map configuration with the specified elevation style.

## Relationships

### Inherits From

- `MKMapConfiguration`

### Conforms To

- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSCoding`
- `NSCopying`
- `NSObjectProtocol`
- `NSSecureCoding`

## See Also

### Configuring the map appearance

`var preferredConfiguration: MKMapConfiguration`

The characteristics of the map view, including the map type and features the map displays.

`var pitchButtonVisibility: MKFeatureVisibility`

A value that indicates whether the map’s pitch button is visible.

`var showsUserTrackingButton: Bool`

A Boolean value that indicates whether the map displays the user tracking button.

`class MKMapConfiguration`

An abstract class that represents the shared elements of map configurations.

`class MKStandardMapConfiguration`

The class that represents the default map presentation, which is a street map that shows the position of all roads and some road names.

`class MKHybridMapConfiguration`

The class that represents a satellite image of the area with road and road name information layers on top.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/region

- MapKit
- MKMapView
- region

Instance Property

# region

The area the map view displays.

@MainActor
var region: MKCoordinateRegion { get set }

## Discussion

The _region_ encompasses both the latitude and longitude center point of the map, and the span of coordinates to display. The span values provide an implicit zoom value for the map. The larger the displayed area, the lower the amount of zoom. Similarly, the smaller the displayed area, the greater the amount of zoom.

Changing only the center coordinate of the region can still cause the span to change implicitly. The span might change because the distances that a span represents change at different latitudes and longitudes, and the map view may need to adjust the span to account for the new location. If you want to change the center coordinate without changing the zoom level, use the `centerCoordinate` instead.

Changing the value of this property updates the map view immediately. When setting this property, the map may adjust the new region value so that it fits the visible area of the map precisely. This ensures that the value in this property reflects the visible portion of the map. However, it does mean that if you get the value of this property right after setting it, the returned value may not match the value you set. You can use the `regionThatFits(_:)` method to determine the region that the map sets.

If you want to animate the change in region, use the `setRegion(_:animated:)` method instead.

## See Also

### Manipulating the visible portion of the map

`func setRegion(MKCoordinateRegion, animated: Bool)`

Changes the currently visible region, and optionally animates the change.

`var centerCoordinate: CLLocationCoordinate2D`

The map coordinate at the center of the map view.

`func setCenter(CLLocationCoordinate2D, animated: Bool)`

Changes the center coordinate of the map, and optionally animates the change.

[`func showAnnotations([any MKAnnotation], animated: Bool)`](https://developer.apple.com/documentation/mapkit/mkmapview/showannotations(_:animated:))

Sets the visible region so that the map displays the specified annotations.

`var visibleMapRect: MKMapRect`

The area visible in the map view.

`func setVisibleMapRect(MKMapRect, animated: Bool)`

Changes the currently visible portion of the map, and optionally animates the change.

`func setVisibleMapRect(MKMapRect, edgePadding: UIEdgeInsets, animated: Bool)`

Changes the currently visible portion of the map, allowing you to specify additional space around the edges.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/isscrollenabled

- MapKit
- MKMapView
- isScrollEnabled

Instance Property

# isScrollEnabled

A Boolean value that determines whether the user may scroll around the map.

@MainActor
var isScrollEnabled: Bool { get set }

## Discussion

This property controls only user interactions with the map. If you set the value of this property to `false`, you may still change the map location programmatically by changing the value in the `region` property.

The default value of this property is `true`.

## See Also

### Accessing map properties

`enum MKMapType`

The type of map to display.

Deprecated

`var isZoomEnabled: Bool`

A Boolean value that determines whether the user may use pinch gestures to zoom in and out of the map.

`var isPitchEnabled: Bool`

A Boolean value that indicates whether the map uses the camera’s pitch information.

`var isRotateEnabled: Bool`

A Boolean value that indicates whether the map uses the camera’s heading information.

`var mapType: MKMapType`

The type of data the map view displays.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/iszoomenabled

- MapKit
- MKMapView
- isZoomEnabled

Instance Property

# isZoomEnabled

A Boolean value that determines whether the user may use pinch gestures to zoom in and out of the map.

@MainActor
var isZoomEnabled: Bool { get set }

## Discussion

This property controls only user interactions with the map. If you set the value of this property to `false`, you may still change the zoom level programmatically by changing the value in the `region` property.

The default value of this property is `true`.

## See Also

### Accessing map properties

`enum MKMapType`

The type of map to display.

Deprecated

`var isScrollEnabled: Bool`

A Boolean value that determines whether the user may scroll around the map.

`var isPitchEnabled: Bool`

A Boolean value that indicates whether the map uses the camera’s pitch information.

`var isRotateEnabled: Bool`

A Boolean value that indicates whether the map uses the camera’s heading information.

`var mapType: MKMapType`

The type of data the map view displays.

---

# https://developer.apple.com/documentation/mapkit/mkmapviewdelegate

- MapKit
- MKMapViewDelegate

Protocol

# MKMapViewDelegate

Optional methods that you use to receive map-related update messages.

iOSiPadOSMac CatalystmacOStvOSvisionOS

@MainActor
protocol MKMapViewDelegate : NSObjectProtocol

## Overview

Because many map operations require the `MKMapView` class to load data asynchronously, the map view calls these methods to notify your app when specific operations complete. The map view also uses these methods to request annotation and overlay views, and to manage interactions with those views.

Before releasing an `MKMapView` object that you set a delegate for, remember to set that object’s `delegate` property to `nil`. MapKit calls all of your delegate methods on the app’s main thread.

## Topics

### Responding to map position changes

`func mapView(MKMapView, regionWillChangeAnimated: Bool)`

Tells the delegate when the region the map view is displaying is about to change.

`func mapViewDidChangeVisibleRegion(MKMapView)`

Tells the delegate when the map view’s visible region changes.

`func mapView(MKMapView, regionDidChangeAnimated: Bool)`

Tells the delegate when the region the map view is displaying changes.

### Loading the map data

`func mapViewWillStartLoadingMap(MKMapView)`

Tells the delegate that the specified map view is about to retrieve some map data.

`func mapViewDidFinishLoadingMap(MKMapView)`

Tells the delegate when the specified map view successfully loads the needed map data.

`func mapViewDidFailLoadingMap(MKMapView, withError: any Error)`

Tells the delegate that the specified view is unable to load the map data.

`func mapViewWillStartRenderingMap(MKMapView)`

Tells the delegate that the map view is about to start rendering some of its tiles.

`func mapViewDidFinishRenderingMap(MKMapView, fullyRendered: Bool)`

Tells the delegate when the map view finishes rendering all visible tiles.

### Tracking the user’s location

`func mapViewWillStartLocatingUser(MKMapView)`

Tells the delegate that the map view is about to start tracking the user’s location.

`func mapViewDidStopLocatingUser(MKMapView)`

Tells the delegate when the map view stops tracking the user’s location.

`func mapView(MKMapView, didUpdate: MKUserLocation)`

Tells the delegate when the map view updates the user’s location.

`func mapView(MKMapView, didFailToLocateUserWithError: any Error)`

Tells the delegate when an attempt to locate the user’s location fails.

`func mapView(MKMapView, didChange: MKUserTrackingMode, animated: Bool)`

Tells the delegate when the user-tracking mode changes.

### Managing annotation views

Returns the view associated with the specified annotation object.

[`func mapView(MKMapView, didAdd: [MKAnnotationView])`](https://developer.apple.com/documentation/mapkit/mkmapviewdelegate/mapview(_:didadd:)-44xon)

Tells the delegate when the map view adds one or more annotation views to the map.

`func mapView(MKMapView, annotationView: MKAnnotationView, calloutAccessoryControlTapped: UIControl)`

Tells the delegate when the user taps one of the annotation view’s accessory buttons.

Asks the delegate to provide a cluster annotation object for the specified annotations.

### Dragging an annotation view

`func mapView(MKMapView, annotationView: MKAnnotationView, didChange: MKAnnotationView.DragState, fromOldState: MKAnnotationView.DragState)`

Tells the delegate when the drag state of one of its annotation views changes.

### Selecting annotations and annotations views

`func mapView(MKMapView, didSelect: MKAnnotationView)`

Tells the delegate when the user selects one or more of its annotation views.

`func mapView(MKMapView, didDeselect: MKAnnotationView)`

Tells the delegate when the user deselects one or more of its annotation views.

`func mapView(MKMapView, didDeselect: any MKAnnotation)`

Tells the delegate when the user deselects one or more annotations.

`func mapView(MKMapView, didSelect: any MKAnnotation)`

Tells the delegate when the user selects one or more annotations.

`var selectableMapFeatures: MKMapFeatureOptions`

The property that describes which selectable features the map responds to.

### Managing the display of overlays

Specifies the accessory to display for a selected annotation

Asks the delegate for a renderer object to use when drawing the specified overlay.

[`func mapView(MKMapView, didAdd: [MKOverlayRenderer])`](https://developer.apple.com/documentation/mapkit/mkmapviewdelegate/mapview(_:didadd:)-793gj)

Tells the delegate when the map view adds one or more renderer objects to the map.

Asks the delegate for the overlay view to use when displaying the specified overlay object.

Deprecated

[`func mapView(MKMapView, didAddOverlayViews: [Any])`](https://developer.apple.com/documentation/mapkit/mkmapviewdelegate/mapview(_:didaddoverlayviews:))

Tells the delegate when the map adds one or more overlay views to the map.

## Relationships

### Inherits From

- `NSObjectProtocol`

## See Also

### Customizing the map view behavior

`var delegate: (any MKMapViewDelegate)?`

The receiver’s delegate.

---

# https://developer.apple.com/documentation/mapkit/mkannotation

- MapKit
- MKAnnotation

Protocol

# MKAnnotation

An interface for associating your content with a specific map location.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

protocol MKAnnotation : NSObjectProtocol

## Overview

An object that adopts this protocol manages the data that you want to display on the map surface. It doesn’t provide the visual representation that the map displays. Instead, your map view’s delegate provides the `MKAnnotationView` objects necessary to display the content of your annotations. When you want to display content at a specific point on the map, add an annotation object to the map view. When the annotation’s `coordinate` is visible on the map, the map view asks its delegate to provide an appropriate view to display any content associated with the annotation. You implement the `mapView(_:viewFor:)` method of the delegate to provide that view.

An object that adopts this protocol needs to implement the `coordinate` property. The other methods of this protocol are optional.

## Topics

### Position attributes

`var coordinate: CLLocationCoordinate2D`

The center point (specified as a map coordinate) of the annotation.

**Required**

### Title attributes

`var title: String?`

The string containing the annotation’s title.

`var subtitle: String?`

The string containing the annotation’s subtitle.

## Relationships

### Inherits From

- `NSObjectProtocol`

### Inherited By

- `MKOverlay`

### Conforming Types

- `MKCircle`
- `MKClusterAnnotation`
- `MKGeodesicPolyline`
- `MKMapFeatureAnnotation`
- `MKMapItemAnnotation`
- `MKMultiPoint`
- `MKMultiPolygon`
- `MKMultiPolyline`
- `MKPlacemark`
- `MKPointAnnotation`
- `MKPolygon`
- `MKPolyline`
- `MKShape`
- `MKTileOverlay`
- `MKUserLocation`

## See Also

### Shared behavior

`class MKPlacemark`

A user-friendly description of a location on the map.

Deprecated

`class MKAnnotationView`

The visual representation of one of your annotation objects.

---

# https://developer.apple.com/documentation/mapkit/mkannotationview

- MapKit
- MKAnnotationView

Class

# MKAnnotationView

The visual representation of one of your annotation objects.

@MainActor
class MKAnnotationView

## Overview

_Annotation views_ are loosely coupled to a corresponding _annotation object_, which is an object that conforms to the `MKAnnotation` protocol. When an annotation’s coordinate point is in the map’s visible region, the map view asks its delegate to provide a corresponding annotation view. MapKit may recycle annotation views and put them into a reuse queue that the map view maintains.

The most efficient way to provide the content for an annotation view is to set its `image` property. The annotation view sizes itself automatically to the image you specify and draws that image for its contents. Because it’s a view, you can also override the `draw(_:)` method and draw your view’s content manually. If you choose to override `draw(_:)` directly and you don’t specify a custom image in the `image` property, the annotation view sets the width and height of the annotation view’s frame to `0` by default. Before the framework can draw your custom content, you need to set the width and height to nonzero values by modifying the view’s `frame` property. In general, if your content consists entirely of static images, it’s more efficient to set the `image` property and change it as necessary than to draw the images yourself.

Annotation views anchor to the map at the point that their associated annotation object specifies. Although they scroll with the map contents, annotation views reside in a separate display layer and don’t scale when the size of the visible map region changes.

Additionally, annotation views support the concept of a _selection state_, which determines whether the map displays the annotation view as unselected, selected, or selected and displaying a standard callout view. The user toggles between the selection states through interactions with the annotation view. In the unselected state, the map displays the annotation view, but doesn’t highlight it. In the selected state, the framework highlights the annotation, but doesn’t display the callout. Finally, the map view can display the annotation with both a highlight and a callout. The callout view displays additional information, such as a title string and controls for viewing more information. The annotation object provides the title information, but your annotation view is responsible for providing any custom controls. For more information, see the Subclassing notes section below.

### Reuse annotation views

The design of annotation views enables their reuse as the user (or your app) changes the visible map region. The reuse of annotation views provides significant performance improvements during scrolling by avoiding the creation of new view objects during this time-critical operation. For this reason, don’t tightly couple annotation views to the contents of their associated annotation. Instead, use the properties of an annotation view (or setter methods) to configure the view for a new annotation object.

Whenever you initialize a new annotation view, specify a reuse identifier for that view. When the framework no longer needs annotation views, the map view may put them into a reuse queue. As the framework adds new annotations to the map view, the delegate object can then dequeue and reconfigure an existing view (rather than create a new one) using the `dequeueReusableAnnotationView(withIdentifier:)` method of `MKMapView`.

### Subclassing notes

You can use the `MKAnnotationView` class as-is or subclass it to provide custom behavior as necessary. The `image` property of the class lets you set the appearance of the annotation view without subclassing directly. You might also create custom subclasses as a convenience and use them to put the annotation view in a known state.

There are no special requirements for subclassing `MKAnnotationView`. However, the following list includes some reasons you might want to subclass, and the methods to override to implement the desired behavior:

- To put the annotation view into a consistent state, provide a custom initialization method. Your custom initialization method then calls `init(annotation:reuseIdentifier:)` to initialize the superclass.

- To provide custom callout views, override the `leftCalloutAccessoryView` method and use it to return the views.

If you support draggable annotation views in iOS, your subclass is responsible for changing the value in the `dragState` property to appropriate values at key transition points in the drag operation. For more information, see the description of that property.

## Topics

### Creating and preparing an annotation view

`init(annotation: (any MKAnnotation)?, reuseIdentifier: String?)`

Creates and returns a new annotation view.

`init?(coder: NSCoder)`

Creates an annotation view using data from the specified unarchiver.

`func prepareForReuse()`

Calls this method when removing the view from the reuse queue.

`func prepareForDisplay()`

Notifies the annotation view that the map view is about to display it.

### Setting the priority for display

`var displayPriority: MKFeatureDisplayPriority`

The display priority of the annotation view.

`struct MKFeatureDisplayPriority`

Constants that indicates the display priority for annotations.

`var zPriority: MKAnnotationViewZPriority`

The relative importance of the annotation view when in an unselected state with respect to its ordering along the z-axis.

`var selectedZPriority: MKAnnotationViewZPriority`

The relative importance of the annotation view when in a selected state with respect to its ordering along the z-axis.

`struct MKAnnotationViewZPriority`

Constants that indicates the priority for ordering overlapping annotation views.

### Getting and setting attributes

`var isEnabled: Bool`

A Boolean value that indicates whether the annotation is in an enabled state.

`var image: UIImage?`

The image the annotation view displays.

`var isHighlighted: Bool`

A Boolean value that indicates whether the map view highlights the annotation view.

`var annotation: (any MKAnnotation)?`

The annotation object associated with the view.

`var centerOffset: CGPoint`

The offset (in points) at which to display the view.

`var calloutOffset: CGPoint`

The offset (in points) at which to place the callout.

`var reuseIdentifier: String?`

The string that identifies that the annotation view is reusable.

### Managing the selection state

`func setSelected(Bool, animated: Bool)`

Sets the selection state of the annotation view.

`var isSelected: Bool`

A Boolean value that indicates whether the annotation view is in a selected state.

### Managing callout views

`var accessoryOffset: CGPoint`

An offset that changes the accessory’s default anchor point.

`var canShowCallout: Bool`

A Boolean value that indicates whether the annotation view is able to display extra information in a callout.

`var leftCalloutAccessoryView: UIView?`

The view to display on the left side of the standard callout.

`var rightCalloutAccessoryView: UIView?`

The view to display on the right side of the standard callout.

`var detailCalloutAccessoryView: UIView?`

The detail accessory view to use in the standard callout.

`var leftCalloutOffset: CGPoint`

The offset in points from the middle-left of the annotation view.

`var rightCalloutOffset: CGPoint`

The offset in points from the middle-right of the annotation view.

### Supporting drag operations

`var isDraggable: Bool`

A Boolean value that indicates whether the annotation view is draggable.

`func setDragState(MKAnnotationView.DragState, animated: Bool)`

Sets the drag state for the annotation view.

`var dragState: MKAnnotationView.DragState`

The drag state of the annotation view.

### Managing collisions between annotation views

`var collisionMode: MKAnnotationView.CollisionMode`

The collision mode to use when interpreting the collision frame rectangle.

`enum CollisionMode`

Constants that indicates how to interpret the collision frame rectangle of an annotation view.

### Clustering annotation views

Decluttering a Map with MapKit Annotation Clustering

Enhance the readability of a map by replacing overlapping annotations with a clustering annotation view.

`var clusteringIdentifier: String?`

An identifier that determines whether the annotation view participates in clustering.

`var cluster: MKAnnotationView?`

The clustering annotation view that replaces the annotation view.

### Constants

`enum DragState`

Constants that indicate the drag state of an annotation view.

## Relationships

### Inherits From

- `NSView`
- `UIView`

### Inherited By

- `MKMarkerAnnotationView`
- `MKPinAnnotationView`
- `MKUserLocationView`

### Conforms To

- `CALayerDelegate`
- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSAccessibilityElementProtocol`
- `NSAccessibilityProtocol`
- `NSAnimatablePropertyContainer`
- `NSAppearanceCustomization`
- `NSCoding`
- `NSDraggingDestination`
- `NSObjectProtocol`
- `NSStandardKeyBindingResponding`
- `NSTouchBarProvider`
- `NSUserActivityRestoring`
- `NSUserInterfaceItemIdentification`
- `Sendable`
- `SendableMetatype`
- `UIAccessibilityIdentification`
- `UIActivityItemsConfigurationProviding`
- `UIAppearance`
- `UIAppearanceContainer`
- `UICoordinateSpace`
- `UIDynamicItem`
- `UIFocusEnvironment`
- `UIFocusItem`
- `UIFocusItemContainer`
- `UILargeContentViewerItem`
- `UIPasteConfigurationSupporting`
- `UIPopoverPresentationControllerSourceItem`
- `UIResponderStandardEditActions`
- `UITraitChangeObservable`
- `UITraitEnvironment`
- `UIUserActivityRestoring`

## See Also

### Shared behavior

`class MKPlacemark`

A user-friendly description of a location on the map.

Deprecated

`protocol MKAnnotation`

An interface for associating your content with a specific map location.

---

# https://developer.apple.com/documentation/mapkit/mkmarkerannotationview

- MapKit
- MKMarkerAnnotationView

Class

# MKMarkerAnnotationView

An annotation view that displays a balloon-shaped marker at the designated location.

@MainActor
class MKMarkerAnnotationView

## Overview

Return an instance of this class from the `mapView(_:viewFor:)` method of your map view delegate when you want to display the same types of markers used in the Maps app.

The default `displayPriority` for an instance of this class is `defaultLow`.

## Topics

### Setting the Marker Color

`var markerTintColor: UIColor?`

The background color of the marker balloon.

### Setting the Marker Content

`var glyphText: String?`

The text to display in the marker balloon.

`var glyphImage: UIImage?`

An image to display in the marker balloon.

`var glyphTintColor: UIColor?`

The color to apply to the glyph text or image.

`var selectedGlyphImage: UIImage?`

An image to display when the user selects the marker.

### Setting the Visibility

`var titleVisibility: MKFeatureVisibility`

The visibility of the title text rendered beneath the marker balloon.

`var subtitleVisibility: MKFeatureVisibility`

The visibility of the subtitle text rendered beneath the marker balloon.

`enum MKFeatureVisibility`

Constants that indicate the visibility of different map features.

### Animating the Marker onto the Screen

`var animatesWhenAdded: Bool`

A Boolean that indicates whether the marker animates into position onscreen.

## Relationships

### Inherits From

- `MKAnnotationView`

### Conforms To

- `CALayerDelegate`
- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSAccessibilityElementProtocol`
- `NSAccessibilityProtocol`
- `NSAnimatablePropertyContainer`
- `NSAppearanceCustomization`
- `NSCoding`
- `NSDraggingDestination`
- `NSObjectProtocol`
- `NSStandardKeyBindingResponding`
- `NSTouchBarProvider`
- `NSUserActivityRestoring`
- `NSUserInterfaceItemIdentification`
- `Sendable`
- `SendableMetatype`
- `UIAccessibilityIdentification`
- `UIActivityItemsConfigurationProviding`
- `UIAppearance`
- `UIAppearanceContainer`
- `UICoordinateSpace`
- `UIDynamicItem`
- `UIFocusEnvironment`
- `UIFocusItem`
- `UIFocusItemContainer`
- `UILargeContentViewerItem`
- `UIPasteConfigurationSupporting`
- `UIPopoverPresentationControllerSourceItem`
- `UIResponderStandardEditActions`
- `UITraitChangeObservable`
- `UITraitEnvironment`
- `UIUserActivityRestoring`

## See Also

### Location annotations

Annotating a Map with Custom Data

Annotate a map with location-specific data using default and customized annotation views and callouts.

`class MKPointAnnotation`

A string-based piece of location-specific data that you apply to a specific point on a map.

`class MKMapItemAnnotation`

An annotation that represents a map item

`class MKPinAnnotationView`

An annotation view that displays a pin image on the map.

Deprecated

---

# https://developer.apple.com/documentation/mapkit/mkoverlay

- MapKit
- MKOverlay

Protocol

# MKOverlay

An interface for associating content with a specific map region.

protocol MKOverlay : MKAnnotation

## Overview

_Overlay objects_ are data objects that define the geographic data to cover. MapKit defines several concrete classes that adopt this protocol and define standard shapes like rectangles, circles, and polygons. You might use overlays to define the geographic boundaries of a national park or trace a bus route along city streets. You add an overlay to your map view by calling its `addOverlay(_:)` method or any other map view method for adding overlays to the map. When the overlay’s region intersects the visible portion of the map, the map view calls the `mapView(_:rendererFor:)` method of its delegate to obtain the renderer object responsible for drawing the overlay.

If you add an overlay to a map view as an annotation, instead of adding it as an overlay, the map view treats your overlay as an annotation. Specifically, it displays your overlay only when its `coordinate` is in the visible map region, rather than displaying the overlay when any portion of its covered area is visible.

## Topics

### Describing the overlay geometry

`var coordinate: CLLocationCoordinate2D`

The approximate center point of the overlay area.

**Required**

`var boundingMapRect: MKMapRect`

The projected rectangle that encompasses the overlay.

### Determining map intersections

Returns a Boolean value that indicates whether the specified rectangle intersects the overlay’s shape.

### Optimizing map rendering

Returns a Boolean value that indicates whether the overlay content replaces the underlying map content.

## Relationships

### Inherits From

- `MKAnnotation`
- `NSObjectProtocol`

### Conforming Types

- `MKCircle`
- `MKGeodesicPolyline`
- `MKMultiPolygon`
- `MKMultiPolyline`
- `MKPolygon`
- `MKPolyline`
- `MKTileOverlay`

## See Also

### Shared behavior

`class MKOverlayRenderer`

The shared infrastructure for drawing overlays on the map surface.

`class MKShape`

An abstract class that defines the basic properties for all shape-based overlay objects.

`class MKMultiPoint`

An abstract class that defines the common behavior that open and closed polygon overlays share.

`class MKPlacemark`

A user-friendly description of a location on the map.

Deprecated

---

# https://developer.apple.com/documentation/mapkit/mkoverlayrenderer

- MapKit
- MKOverlayRenderer

Class

# MKOverlayRenderer

The shared infrastructure for drawing overlays on the map surface.

class MKOverlayRenderer

## Overview

An overlay renderer draws the visual representation of an overlay object — that is, an object that conforms to the `MKOverlay` protocol. This class defines the drawing infrastructure the map view uses. Subclasses need to override the `draw(_:zoomScale:in:)` method to draw the contents of the overlay.

The MapKit framework provides several concrete instances of overlay renderers. Specifically, it provides renderers for each of the concrete overlay objects. You can use one of these existing renderers or define your own subclasses if you want to draw the overlay contents differently.

You can subclass `MKOverlayRenderer` to create overlays based on custom shapes, content, or drawing techniques. The only method subclasses need to override is the `draw(_:zoomScale:in:)` method. However, if your class contains content that may not be ready for drawing right away, you need to also override the `canDraw(_:zoomScale:)` method and use it to report when your class is ready and able to draw.

The map view may tile large overlays and distribute the rendering of each tile to separate threads. Therefore, the implementation of your `draw(_:zoomScale:in:)` method needs to be safe to run from background threads and from multiple threads simultaneously.

## Topics

### Creating an overlay view

`init(overlay: any MKOverlay)`

Creates and returns the overlay renderer and associates it with the specified overlay object.

### Attributes of the overlay

`var overlay: any MKOverlay`

The overlay object containing the data for drawing.

`var alpha: CGFloat`

The amount of transparency to apply to the overlay.

`var contentScaleFactor: CGFloat`

The scale factor for drawing the overlay’s content.

`var blendMode: CGBlendMode`

The blend mode to apply to the overlay.

### Converting points on the map

Returns the point in the overlay renderer’s drawing area corresponding to the specified point on the map.

Returns the point on the map that corresponds to the specified point in the overlay renderer’s drawing area.

Returns the rectangle in the overlay renderer’s drawing area corresponding to the specified rectangle on the map.

Returns the rectangle on the map that corresponds to the specified rectangle in the overlay renderer’s drawing area.

### Drawing the overlay

Returns a Boolean value that indicates whether the overlay view is ready to draw its content.

`func draw(MKMapRect, zoomScale: MKZoomScale, in: CGContext)`

Draws the overlay’s contents at the specified location on the map.

`func setNeedsDisplay()`

Invalidates the entire contents of the overlay for all zoom scales.

`func setNeedsDisplay(MKMapRect)`

Invalidates the specified portion of the overlay at all zoom scales.

`func setNeedsDisplay(MKMapRect, zoomScale: MKZoomScale)`

Invalidates the specified portion of the overlay, but only at the specified zoom scale.

### Types

`typealias MKZoomScale`

A scale factor to use in conjunction with a map.

Returns the width (in screen points) of roads on a map at the specified zoom level.

## Relationships

### Inherits From

- `NSObject`

### Inherited By

- `MKOverlayPathRenderer`
- `MKTileOverlayRenderer`

### Conforms To

- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSObjectProtocol`

## See Also

### Shared behavior

`protocol MKOverlay`

An interface for associating content with a specific map region.

`class MKShape`

An abstract class that defines the basic properties for all shape-based overlay objects.

`class MKMultiPoint`

An abstract class that defines the common behavior that open and closed polygon overlays share.

`class MKPlacemark`

A user-friendly description of a location on the map.

Deprecated

---

# https://developer.apple.com/documentation/mapkit/mkmapconfiguration

- MapKit
- MKMapConfiguration

Class

# MKMapConfiguration

An abstract class that represents the shared elements of map configurations.

class MKMapConfiguration

## Topics

### Controlling the elevation style

`var elevationStyle: MKMapConfiguration.ElevationStyle`

The value that indicates the map’s elevation style.

`enum ElevationStyle`

Values that control the map’s elevation style.

## Relationships

### Inherits From

- `NSObject`

### Inherited By

- `MKHybridMapConfiguration`
- `MKImageryMapConfiguration`
- `MKStandardMapConfiguration`

### Conforms To

- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSCoding`
- `NSCopying`
- `NSObjectProtocol`
- `NSSecureCoding`

## See Also

### Configuring the map appearance

`var preferredConfiguration: MKMapConfiguration`

The characteristics of the map view, including the map type and features the map displays.

`var pitchButtonVisibility: MKFeatureVisibility`

A value that indicates whether the map’s pitch button is visible.

`var showsUserTrackingButton: Bool`

A Boolean value that indicates whether the map displays the user tracking button.

`class MKStandardMapConfiguration`

The class that represents the default map presentation, which is a street map that shows the position of all roads and some road names.

`class MKHybridMapConfiguration`

The class that represents a satellite image of the area with road and road name information layers on top.

`class MKImageryMapConfiguration`

The class that represents an imagery-based map presentation, such as one using satellite imagery.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/preferredconfiguration

- MapKit
- MKMapView
- preferredConfiguration

Instance Property

# preferredConfiguration

The characteristics of the map view, including the map type and features the map displays.

@NSCopying @MainActor
var preferredConfiguration: MKMapConfiguration { get set }

## See Also

### Configuring the map appearance

`var pitchButtonVisibility: MKFeatureVisibility`

A value that indicates whether the map’s pitch button is visible.

`var showsUserTrackingButton: Bool`

A Boolean value that indicates whether the map displays the user tracking button.

`class MKMapConfiguration`

An abstract class that represents the shared elements of map configurations.

`class MKStandardMapConfiguration`

The class that represents the default map presentation, which is a street map that shows the position of all roads and some road names.

`class MKHybridMapConfiguration`

The class that represents a satellite image of the area with road and road name information layers on top.

`class MKImageryMapConfiguration`

The class that represents an imagery-based map presentation, such as one using satellite imagery.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/pitchbuttonvisibility

- MapKit
- MKMapView
- pitchButtonVisibility

Instance Property

# pitchButtonVisibility

A value that indicates whether the map’s pitch button is visible.

@MainActor
var pitchButtonVisibility: MKFeatureVisibility { get set }

## Discussion

Use this button to display or hide a button that allows a person to set the map to a pleasing pitch or return the map to a flat appearance.

## See Also

### Configuring the map appearance

`var preferredConfiguration: MKMapConfiguration`

The characteristics of the map view, including the map type and features the map displays.

`var showsUserTrackingButton: Bool`

A Boolean value that indicates whether the map displays the user tracking button.

`class MKMapConfiguration`

An abstract class that represents the shared elements of map configurations.

`class MKStandardMapConfiguration`

The class that represents the default map presentation, which is a street map that shows the position of all roads and some road names.

`class MKHybridMapConfiguration`

The class that represents a satellite image of the area with road and road name information layers on top.

`class MKImageryMapConfiguration`

The class that represents an imagery-based map presentation, such as one using satellite imagery.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/showsusertrackingbutton

- MapKit
- MKMapView
- showsUserTrackingButton

Instance Property

# showsUserTrackingButton

A Boolean value that indicates whether the map displays the user tracking button.

@MainActor
var showsUserTrackingButton: Bool { get set }

## See Also

### Configuring the map appearance

`var preferredConfiguration: MKMapConfiguration`

The characteristics of the map view, including the map type and features the map displays.

`var pitchButtonVisibility: MKFeatureVisibility`

A value that indicates whether the map’s pitch button is visible.

`class MKMapConfiguration`

An abstract class that represents the shared elements of map configurations.

`class MKStandardMapConfiguration`

The class that represents the default map presentation, which is a street map that shows the position of all roads and some road names.

`class MKHybridMapConfiguration`

The class that represents a satellite image of the area with road and road name information layers on top.

`class MKImageryMapConfiguration`

The class that represents an imagery-based map presentation, such as one using satellite imagery.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/delegate

- MapKit
- MKMapView
- delegate

Instance Property

# delegate

The receiver’s delegate.

@IBOutlet @MainActor
weak var delegate: (any MKMapViewDelegate)? { get set }

## Discussion

A map view sends messages to its delegate regarding the loading of map data and changes in the portion of the map it displays. The delegate also manages the annotation views that highlight points of interest on the map.

The delegate needs to implement the methods of the `MKMapViewDelegate` protocol.

## See Also

### Customizing the map view behavior

`protocol MKMapViewDelegate`

Optional methods that you use to receive map-related update messages.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/ispitchenabled

- MapKit
- MKMapView
- isPitchEnabled

Instance Property

# isPitchEnabled

A Boolean value that indicates whether the map uses the camera’s pitch information.

@MainActor
var isPitchEnabled: Bool { get set }

## Discussion

When this property is `true` and the framework associates a valid camera with the map, the map view uses the camera’s pitch angle to tilt the plane of the map. When this property is `false`, the map ignores the camera’s pitch angle and the map displays as if the user is looking straight down onto it.

In an app, be sure to check the value of this property to determine whether a map can support 3D.

## See Also

### Accessing map properties

`enum MKMapType`

The type of map to display.

Deprecated

`var isZoomEnabled: Bool`

A Boolean value that determines whether the user may use pinch gestures to zoom in and out of the map.

`var isScrollEnabled: Bool`

A Boolean value that determines whether the user may scroll around the map.

`var isRotateEnabled: Bool`

A Boolean value that indicates whether the map uses the camera’s heading information.

`var mapType: MKMapType`

The type of data the map view displays.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/isrotateenabled

- MapKit
- MKMapView
- isRotateEnabled

Instance Property

# isRotateEnabled

A Boolean value that indicates whether the map uses the camera’s heading information.

@MainActor
var isRotateEnabled: Bool { get set }

## Discussion

When this property is `true` and the framework associates a valid camera with the map, the map uses the camera’s heading angle to rotate the plane of the map around its center point. When this property is `false`, the map view ignores the camera’s heading angle and the map orients so that the map view situates true north at the top.

## See Also

### Accessing map properties

`enum MKMapType`

The type of map to display.

Deprecated

`var isZoomEnabled: Bool`

A Boolean value that determines whether the user may use pinch gestures to zoom in and out of the map.

`var isScrollEnabled: Bool`

A Boolean value that determines whether the user may scroll around the map.

`var isPitchEnabled: Bool`

A Boolean value that indicates whether the map uses the camera’s pitch information.

`var mapType: MKMapType`

The type of data the map view displays.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/maptype

- MapKit
- MKMapView
- mapType Deprecated

Instance Property

# mapType

The type of data the map view displays.

iOS 3.0–26.2DeprecatediPadOS 3.0–26.2DeprecatedmacOS 10.9–26.2DeprecatedvisionOS 1.0–26.2Deprecated

@MainActor
var mapType: MKMapType { get set }

## Discussion

Changing the value in this property may cause the receiver to begin loading new map content. For example, changing from `MKMapType.standard` to `MKMapType.satellite` might cause it to begin loading the satellite imagery for the map. If the map needs new data, however, it loads asynchronously and MapKit sends appropriate messages to the receiver’s delegate indicating the status of the operation.

## See Also

### Related Documentation

Location and Maps Programming Guide

### Accessing map properties

`enum MKMapType`

The type of map to display.

Deprecated

`var isZoomEnabled: Bool`

A Boolean value that determines whether the user may use pinch gestures to zoom in and out of the map.

`var isScrollEnabled: Bool`

A Boolean value that determines whether the user may scroll around the map.

`var isPitchEnabled: Bool`

A Boolean value that indicates whether the map uses the camera’s pitch information.

`var isRotateEnabled: Bool`

A Boolean value that indicates whether the map uses the camera’s heading information.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/setregion(_:animated:)

#app-main)

- MapKit
- MKMapView
- setRegion(\_:animated:)

Instance Method

# setRegion(\_:animated:)

Changes the currently visible region, and optionally animates the change.

@MainActor
func setRegion(
_ region: MKCoordinateRegion,
animated: Bool
)

## Parameters

`region`

The new region to display in the map view.

`animated`

Specify `true` if you want the map view to animate the transition to the new region, or `false` if you want the map to center on the specified region immediately.

## Discussion

Changing just the center coordinate of the region can still cause the span values to change implicitly. The span values might change because the distances that a span repesents change at different latitudes and longitudes, and the map view may need to adjust the span to account for the new location. If you want to change the center coordinate without changing the zoom level, use the `setCenter(_:animated:)` instead.

When setting a new region, the map may adjust the value in the `region` parameter so that it fits the visible area of the map precisely. This adjustment ensures that the value in the `region` property reflects the visible portion of the map. However, it does mean that if you get the value of that property right after calling this method, the returned value may not match the value you set. You can use the `regionThatFits(_:)` method to determine the region that the map sets.

## See Also

### Manipulating the visible portion of the map

`var region: MKCoordinateRegion`

The area the map view displays.

`var centerCoordinate: CLLocationCoordinate2D`

The map coordinate at the center of the map view.

`func setCenter(CLLocationCoordinate2D, animated: Bool)`

Changes the center coordinate of the map, and optionally animates the change.

[`func showAnnotations([any MKAnnotation], animated: Bool)`](https://developer.apple.com/documentation/mapkit/mkmapview/showannotations(_:animated:))

Sets the visible region so that the map displays the specified annotations.

`var visibleMapRect: MKMapRect`

The area visible in the map view.

`func setVisibleMapRect(MKMapRect, animated: Bool)`

Changes the currently visible portion of the map, and optionally animates the change.

`func setVisibleMapRect(MKMapRect, edgePadding: UIEdgeInsets, animated: Bool)`

Changes the currently visible portion of the map, allowing you to specify additional space around the edges.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/centercoordinate

- MapKit
- MKMapView
- centerCoordinate

Instance Property

# centerCoordinate

The map coordinate at the center of the map view.

@MainActor
var centerCoordinate: CLLocationCoordinate2D { get set }

## Discussion

Changing the value in this property centers the map on the new coordinate without changing the current zoom level. It also updates the values in the `region` property to reflect the new center coordinate and the new span values needed to maintain the current zoom level.

Changing the value of this property updates the map view immediately. If you want to animate the change, use the `setCenter(_:animated:)` method instead.

## See Also

### Manipulating the visible portion of the map

`var region: MKCoordinateRegion`

The area the map view displays.

`func setRegion(MKCoordinateRegion, animated: Bool)`

Changes the currently visible region, and optionally animates the change.

`func setCenter(CLLocationCoordinate2D, animated: Bool)`

Changes the center coordinate of the map, and optionally animates the change.

[`func showAnnotations([any MKAnnotation], animated: Bool)`](https://developer.apple.com/documentation/mapkit/mkmapview/showannotations(_:animated:))

Sets the visible region so that the map displays the specified annotations.

`var visibleMapRect: MKMapRect`

The area visible in the map view.

`func setVisibleMapRect(MKMapRect, animated: Bool)`

Changes the currently visible portion of the map, and optionally animates the change.

`func setVisibleMapRect(MKMapRect, edgePadding: UIEdgeInsets, animated: Bool)`

Changes the currently visible portion of the map, allowing you to specify additional space around the edges.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/setcenter(_:animated:)

#app-main)

- MapKit
- MKMapView
- setCenter(\_:animated:)

Instance Method

# setCenter(\_:animated:)

Changes the center coordinate of the map, and optionally animates the change.

@MainActor
func setCenter(
_ coordinate: CLLocationCoordinate2D,
animated: Bool
)

## Parameters

`coordinate`

The new center coordinate for the map.

`animated`

Specify `true` if you want the map view to scroll to the new location or `false` if you want the map to display the new location immediately.

## Discussion

Changing the center coordinate centers the map on the new coordinate without changing the current zoom level. It also updates the value in the `region` property to reflect the new center coordinate and the new span values needed to maintain the current zoom level.

## See Also

### Manipulating the visible portion of the map

`var region: MKCoordinateRegion`

The area the map view displays.

`func setRegion(MKCoordinateRegion, animated: Bool)`

Changes the currently visible region, and optionally animates the change.

`var centerCoordinate: CLLocationCoordinate2D`

The map coordinate at the center of the map view.

[`func showAnnotations([any MKAnnotation], animated: Bool)`](https://developer.apple.com/documentation/mapkit/mkmapview/showannotations(_:animated:))

Sets the visible region so that the map displays the specified annotations.

`var visibleMapRect: MKMapRect`

The area visible in the map view.

`func setVisibleMapRect(MKMapRect, animated: Bool)`

Changes the currently visible portion of the map, and optionally animates the change.

`func setVisibleMapRect(MKMapRect, edgePadding: UIEdgeInsets, animated: Bool)`

Changes the currently visible portion of the map, allowing you to specify additional space around the edges.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/visiblemaprect

- MapKit
- MKMapView
- visibleMapRect

Instance Property

# visibleMapRect

The area visible in the map view.

@MainActor
var visibleMapRect: MKMapRect { get set }

## Discussion

This property represents the same basic information as the `region` property but specified as a map rectangle instead of a region.

Changing the value of this property updates the map view immediately. If you want to animate the change, use the `setVisibleMapRect(_:animated:)` method instead.

## See Also

### Manipulating the visible portion of the map

`var region: MKCoordinateRegion`

The area the map view displays.

`func setRegion(MKCoordinateRegion, animated: Bool)`

Changes the currently visible region, and optionally animates the change.

`var centerCoordinate: CLLocationCoordinate2D`

The map coordinate at the center of the map view.

`func setCenter(CLLocationCoordinate2D, animated: Bool)`

Changes the center coordinate of the map, and optionally animates the change.

[`func showAnnotations([any MKAnnotation], animated: Bool)`](https://developer.apple.com/documentation/mapkit/mkmapview/showannotations(_:animated:))

Sets the visible region so that the map displays the specified annotations.

`func setVisibleMapRect(MKMapRect, animated: Bool)`

Changes the currently visible portion of the map, and optionally animates the change.

`func setVisibleMapRect(MKMapRect, edgePadding: UIEdgeInsets, animated: Bool)`

Changes the currently visible portion of the map, allowing you to specify additional space around the edges.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/setvisiblemaprect(_:animated:)

#app-main)

- MapKit
- MKMapView
- setVisibleMapRect(\_:animated:)

Instance Method

# setVisibleMapRect(\_:animated:)

Changes the currently visible portion of the map, and optionally animates the change.

@MainActor
func setVisibleMapRect(
_ mapRect: MKMapRect,
animated animate: Bool
)

## Parameters

`mapRect`

The map rectangle to make visible in the map view.

`animate`

Specify `true` if you want the map view to animate the transition to the new map rectangle or `false` if you want the map to center on the specified rectangle immediately.

## See Also

### Manipulating the visible portion of the map

`var region: MKCoordinateRegion`

The area the map view displays.

`func setRegion(MKCoordinateRegion, animated: Bool)`

Changes the currently visible region, and optionally animates the change.

`var centerCoordinate: CLLocationCoordinate2D`

The map coordinate at the center of the map view.

`func setCenter(CLLocationCoordinate2D, animated: Bool)`

Changes the center coordinate of the map, and optionally animates the change.

[`func showAnnotations([any MKAnnotation], animated: Bool)`](https://developer.apple.com/documentation/mapkit/mkmapview/showannotations(_:animated:))

Sets the visible region so that the map displays the specified annotations.

`var visibleMapRect: MKMapRect`

The area visible in the map view.

`func setVisibleMapRect(MKMapRect, edgePadding: UIEdgeInsets, animated: Bool)`

Changes the currently visible portion of the map, allowing you to specify additional space around the edges.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/setvisiblemaprect(_:edgepadding:animated:)

#app-main)

- MapKit
- MKMapView
- setVisibleMapRect(\_:edgePadding:animated:)

Instance Method

# setVisibleMapRect(\_:edgePadding:animated:)

Changes the currently visible portion of the map, allowing you to specify additional space around the edges.

**iOS, iPadOS, Mac Catalyst, tvOS, visionOS**

@MainActor
func setVisibleMapRect(
_ mapRect: MKMapRect,
edgePadding insets: UIEdgeInsets,
animated animate: Bool
)

**macOS**

@MainActor
func setVisibleMapRect(
_ mapRect: MKMapRect,
edgePadding insets: NSEdgeInsets,
animated animate: Bool
)

## Parameters

`mapRect`

The map rectangle to make visible in the map view.

`insets`

The amount of additional space (measured in screen points) to make visible around the specified rectangle.

`animate`

Specify `true` if you want the map view to animate the transition to the new map rectangle or `false` if you want the map to center on the specified rectangle immediately.

## See Also

### Manipulating the visible portion of the map

`var region: MKCoordinateRegion`

The area the map view displays.

`func setRegion(MKCoordinateRegion, animated: Bool)`

Changes the currently visible region, and optionally animates the change.

`var centerCoordinate: CLLocationCoordinate2D`

The map coordinate at the center of the map view.

`func setCenter(CLLocationCoordinate2D, animated: Bool)`

Changes the center coordinate of the map, and optionally animates the change.

[`func showAnnotations([any MKAnnotation], animated: Bool)`](https://developer.apple.com/documentation/mapkit/mkmapview/showannotations(_:animated:))

Sets the visible region so that the map displays the specified annotations.

`var visibleMapRect: MKMapRect`

The area visible in the map view.

`func setVisibleMapRect(MKMapRect, animated: Bool)`

Changes the currently visible portion of the map, and optionally animates the change.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/setcameraboundary(_:animated:)

#app-main)

- MapKit
- MKMapView
- setCameraBoundary(\_:animated:)

Instance Method

# setCameraBoundary(\_:animated:)

Sets the camera boundary for the map view, specifying whether to use animation.

@MainActor
func setCameraBoundary(
_ cameraBoundary: MKMapView.CameraBoundary?,
animated: Bool
)

## Parameters

`cameraBoundary`

The new `MKMapView.CameraBoundary`.

`animated`

A Boolean value that indicates whether the framework animates the transition of the map view to the new boundary.

## See Also

### Constraining the map view

`var cameraBoundary: MKMapView.CameraBoundary?`

The boundary of the area within which the map view’s center needs to remain.

`func setCameraZoomRange(MKMapView.CameraZoomRange?, animated: Bool)`

Sets the camera zoom range for the map view, specifying whether to use animation.

`var cameraZoomRange: MKMapView.CameraZoomRange!`

The zoom range to apply to the map view.

`class CameraBoundary`

A boundary of an area within which the map’s center needs to remain.

`class CameraZoomRange`

A camera zoom range that limits the distances to which the user can zoom.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/cameraboundary-swift.property

- MapKit
- MKMapView
- cameraBoundary

Instance Property

# cameraBoundary

The boundary of the area within which the map view’s center needs to remain.

@NSCopying @MainActor
var cameraBoundary: MKMapView.CameraBoundary? { get set }

## See Also

### Constraining the map view

`func setCameraBoundary(MKMapView.CameraBoundary?, animated: Bool)`

Sets the camera boundary for the map view, specifying whether to use animation.

`func setCameraZoomRange(MKMapView.CameraZoomRange?, animated: Bool)`

Sets the camera zoom range for the map view, specifying whether to use animation.

`var cameraZoomRange: MKMapView.CameraZoomRange!`

The zoom range to apply to the map view.

`class CameraBoundary`

A boundary of an area within which the map’s center needs to remain.

`class CameraZoomRange`

A camera zoom range that limits the distances to which the user can zoom.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/setcamerazoomrange(_:animated:)



---

# https://developer.apple.com/documentation/mapkit/mkmapview/camerazoomrange-swift.property

- MapKit
- MKMapView
- cameraZoomRange

Instance Property

# cameraZoomRange

The zoom range to apply to the map view.

@NSCopying @MainActor
var cameraZoomRange: MKMapView.CameraZoomRange! { get set }

## See Also

### Constraining the map view

`func setCameraBoundary(MKMapView.CameraBoundary?, animated: Bool)`

Sets the camera boundary for the map view, specifying whether to use animation.

`var cameraBoundary: MKMapView.CameraBoundary?`

The boundary of the area within which the map view’s center needs to remain.

`func setCameraZoomRange(MKMapView.CameraZoomRange?, animated: Bool)`

Sets the camera zoom range for the map view, specifying whether to use animation.

`class CameraBoundary`

A boundary of an area within which the map’s center needs to remain.

`class CameraZoomRange`

A camera zoom range that limits the distances to which the user can zoom.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/cameraboundary-swift.class

- MapKit
- MKMapView
- MKMapView.CameraBoundary

Class

# MKMapView.CameraBoundary

A boundary of an area within which the map’s center needs to remain.

class CameraBoundary

## Overview

The constraints of the camera boundary restrict the center point of your map.

## Topics

### Creating a camera boundary

`init?(coder: NSCoder)`

Creates a camera boundary using the provided coder.

`init?(coordinateRegion: MKCoordinateRegion)`

Creates a camera boundary using the provided coordinate region.

`init?(mapRect: MKMapRect)`

Creates a camera boundary using the provided map rectangle.

### Accessing the boundary

`var mapRect: MKMapRect`

The map rectangle that describes the camera boundary.

`var region: MKCoordinateRegion`

The coordinate region that describes the camera boundary.

## Relationships

### Inherits From

- `NSObject`

### Conforms To

- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSCoding`
- `NSCopying`
- `NSObjectProtocol`
- `NSSecureCoding`

## See Also

### Constraining the map view

`func setCameraBoundary(MKMapView.CameraBoundary?, animated: Bool)`

Sets the camera boundary for the map view, specifying whether to use animation.

`var cameraBoundary: MKMapView.CameraBoundary?`

The boundary of the area within which the map view’s center needs to remain.

`func setCameraZoomRange(MKMapView.CameraZoomRange?, animated: Bool)`

Sets the camera zoom range for the map view, specifying whether to use animation.

`var cameraZoomRange: MKMapView.CameraZoomRange!`

The zoom range to apply to the map view.

`class CameraZoomRange`

A camera zoom range that limits the distances to which the user can zoom.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/camerazoomrange-swift.class

- MapKit
- MKMapView
- MKMapView.CameraZoomRange

Class

# MKMapView.CameraZoomRange

A camera zoom range that limits the distances to which the user can zoom.

class CameraZoomRange

## Overview

Create a camera zoom range to limit the distance to which the user can zoom. After you create the camera zoom range, you can apply it to multiple map views. If you don’t create a camera zoom range, your map view allows the user to zoom to MapKit’s capabilities.

## Topics

### Creating a camera zoom range

`init?(minCenterCoordinateDistance: CLLocationDistance, maxCenterCoordinateDistance: CLLocationDistance)`

Create a camera zoom range by specifying a minimum and maximum distance from your map view’s center coordinates, measured in meters.

`convenience init?(minCenterCoordinateDistance: CLLocationDistance)`

Create a camera zoom range by specifying the minimum distance from your map view’s center coordinate, measured in meters.

`convenience init?(maxCenterCoordinateDistance: CLLocationDistance)`

Create a camera zoom range by specifying the maximum distance from your map view’s center coordinate, measured in meters.

`let MKMapCameraZoomDefault: CLLocationDistance`

A constant value used to represent the default value for zooming in or out on a map.

### Accessing zoom range values

`var maxCenterCoordinateDistance: CLLocationDistance`

The maximum distance of the camera to the center of the map, measured in meters.

`var minCenterCoordinateDistance: CLLocationDistance`

The minimum distance of the camera to the center of the map, measured in meters.

## Relationships

### Inherits From

- `NSObject`

### Conforms To

- `CVarArg`
- `CustomDebugStringConvertible`
- `CustomStringConvertible`
- `Equatable`
- `Hashable`
- `NSCoding`
- `NSCopying`
- `NSObjectProtocol`
- `NSSecureCoding`

## See Also

### Constraining the map view

`func setCameraBoundary(MKMapView.CameraBoundary?, animated: Bool)`

Sets the camera boundary for the map view, specifying whether to use animation.

`var cameraBoundary: MKMapView.CameraBoundary?`

The boundary of the area within which the map view’s center needs to remain.

`func setCameraZoomRange(MKMapView.CameraZoomRange?, animated: Bool)`

Sets the camera zoom range for the map view, specifying whether to use animation.

`var cameraZoomRange: MKMapView.CameraZoomRange!`

The zoom range to apply to the map view.

`class CameraBoundary`

A boundary of an area within which the map’s center needs to remain.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/setcamera(_:animated:)

#app-main)

- MapKit
- MKMapView
- setCamera(\_:animated:)

Instance Method

# setCamera(\_:animated:)

Changes the camera to use for determining the map’s viewing parameters, and optionally animates the change.

@MainActor
func setCamera(
_ camera: MKMapCamera,
animated: Bool
)

## Parameters

`camera`

The camera object containing the viewing angle information. This parameter can’t be `nil`.

`animated`

Specify `true` if you want the map view to animate the change in viewing angle, or `false` if you want the map to reflect the changes without animations.

## See Also

### Configuring the map display

`var camera: MKMapCamera`

The camera to use for determining the appearance of the map.

`var showsCompass: Bool`

A Boolean value that indicates whether the map displays a compass control.

`var showsPitchControl: Bool`

A Boolean value that indicates whether the map displays the pitch control.

`var showsScale: Bool`

A Boolean value that indicates whether the map shows scale information.

`var showsZoomControls: Bool`

A Boolean value that indicates whether the map displays zoom controls.

`var showsBuildings: Bool`

A Boolean value that indicates whether the map displays extruded building information on supported map types.

Deprecated

`var showsPointsOfInterest: Bool`

A Boolean value that indicates whether the map displays point-of-interest information.

`var pointOfInterestFilter: MKPointOfInterestFilter?`

The filter to use for determining the points of interest that appear on the map.

`var showsTraffic: Bool`

A Boolean value that indicates whether the map displays traffic information.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/camera

- MapKit
- MKMapView
- camera

Instance Property

# camera

The camera to use for determining the appearance of the map.

@NSCopying @MainActor
var camera: MKMapCamera { get set }

## Discussion

A camera object defines a point above the map’s surface from which to view the map. Applying a camera to a map can have the effect of giving the map a 3D-like appearance. You can use a camera to rotate the map so that it orients to match the user’s heading or to apply a pitch angle to tilt the plane of the map. You can check the map’s `isPitchEnabled` property to determine whether the map can use pitch.

Assigning a new camera to this property updates the map immediately and without animating the change. If you want to animate changes in camera position, use the `setCamera(_:animated:)` method instead.

Don’t set this property to `nil`. To restore the map to a flat appearance, apply a camera with a pitch angle of `0`, which yields a camera looking straight down onto the map surface.

## See Also

### Configuring the map display

`func setCamera(MKMapCamera, animated: Bool)`

Changes the camera to use for determining the map’s viewing parameters, and optionally animates the change.

`var showsCompass: Bool`

A Boolean value that indicates whether the map displays a compass control.

`var showsPitchControl: Bool`

A Boolean value that indicates whether the map displays the pitch control.

`var showsScale: Bool`

A Boolean value that indicates whether the map shows scale information.

`var showsZoomControls: Bool`

A Boolean value that indicates whether the map displays zoom controls.

`var showsBuildings: Bool`

A Boolean value that indicates whether the map displays extruded building information on supported map types.

Deprecated

`var showsPointsOfInterest: Bool`

A Boolean value that indicates whether the map displays point-of-interest information.

`var pointOfInterestFilter: MKPointOfInterestFilter?`

The filter to use for determining the points of interest that appear on the map.

`var showsTraffic: Bool`

A Boolean value that indicates whether the map displays traffic information.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/showscompass

- MapKit
- MKMapView
- showsCompass

Instance Property

# showsCompass

A Boolean value that indicates whether the map displays a compass control.

@MainActor
var showsCompass: Bool { get set }

## Discussion

Use this property to show or hide a control that lets users change the heading orientation of the map.

## See Also

### Configuring the map display

`func setCamera(MKMapCamera, animated: Bool)`

Changes the camera to use for determining the map’s viewing parameters, and optionally animates the change.

`var camera: MKMapCamera`

The camera to use for determining the appearance of the map.

`var showsPitchControl: Bool`

A Boolean value that indicates whether the map displays the pitch control.

`var showsScale: Bool`

A Boolean value that indicates whether the map shows scale information.

`var showsZoomControls: Bool`

A Boolean value that indicates whether the map displays zoom controls.

`var showsBuildings: Bool`

A Boolean value that indicates whether the map displays extruded building information on supported map types.

Deprecated

`var showsPointsOfInterest: Bool`

A Boolean value that indicates whether the map displays point-of-interest information.

`var pointOfInterestFilter: MKPointOfInterestFilter?`

The filter to use for determining the points of interest that appear on the map.

`var showsTraffic: Bool`

A Boolean value that indicates whether the map displays traffic information.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/showspitchcontrol

- MapKit
- MKMapView
- showsPitchControl

Instance Property

# showsPitchControl

A Boolean value that indicates whether the map displays the pitch control.

@MainActor
var showsPitchControl: Bool { get set }

## See Also

### Configuring the map display

`func setCamera(MKMapCamera, animated: Bool)`

Changes the camera to use for determining the map’s viewing parameters, and optionally animates the change.

`var camera: MKMapCamera`

The camera to use for determining the appearance of the map.

`var showsCompass: Bool`

A Boolean value that indicates whether the map displays a compass control.

`var showsScale: Bool`

A Boolean value that indicates whether the map shows scale information.

`var showsZoomControls: Bool`

A Boolean value that indicates whether the map displays zoom controls.

`var showsBuildings: Bool`

A Boolean value that indicates whether the map displays extruded building information on supported map types.

Deprecated

`var showsPointsOfInterest: Bool`

A Boolean value that indicates whether the map displays point-of-interest information.

`var pointOfInterestFilter: MKPointOfInterestFilter?`

The filter to use for determining the points of interest that appear on the map.

`var showsTraffic: Bool`

A Boolean value that indicates whether the map displays traffic information.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/showsscale

- MapKit
- MKMapView
- showsScale

Instance Property

# showsScale

A Boolean value that indicates whether the map shows scale information.

@MainActor
var showsScale: Bool { get set }

## Discussion

The default value of this property is `false`.

## See Also

### Configuring the map display

`func setCamera(MKMapCamera, animated: Bool)`

Changes the camera to use for determining the map’s viewing parameters, and optionally animates the change.

`var camera: MKMapCamera`

The camera to use for determining the appearance of the map.

`var showsCompass: Bool`

A Boolean value that indicates whether the map displays a compass control.

`var showsPitchControl: Bool`

A Boolean value that indicates whether the map displays the pitch control.

`var showsZoomControls: Bool`

A Boolean value that indicates whether the map displays zoom controls.

`var showsBuildings: Bool`

A Boolean value that indicates whether the map displays extruded building information on supported map types.

Deprecated

`var showsPointsOfInterest: Bool`

A Boolean value that indicates whether the map displays point-of-interest information.

`var pointOfInterestFilter: MKPointOfInterestFilter?`

The filter to use for determining the points of interest that appear on the map.

`var showsTraffic: Bool`

A Boolean value that indicates whether the map displays traffic information.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/showszoomcontrols

- MapKit
- MKMapView
- showsZoomControls

Instance Property

# showsZoomControls

A Boolean value that indicates whether the map displays zoom controls.

@MainActor
var showsZoomControls: Bool { get set }

## Discussion

In macOS, use this property to show or hide the controls that let users change the zoom level of the map.

## See Also

### Configuring the map display

`func setCamera(MKMapCamera, animated: Bool)`

Changes the camera to use for determining the map’s viewing parameters, and optionally animates the change.

`var camera: MKMapCamera`

The camera to use for determining the appearance of the map.

`var showsCompass: Bool`

A Boolean value that indicates whether the map displays a compass control.

`var showsPitchControl: Bool`

A Boolean value that indicates whether the map displays the pitch control.

`var showsScale: Bool`

A Boolean value that indicates whether the map shows scale information.

`var showsBuildings: Bool`

A Boolean value that indicates whether the map displays extruded building information on supported map types.

Deprecated

`var showsPointsOfInterest: Bool`

A Boolean value that indicates whether the map displays point-of-interest information.

`var pointOfInterestFilter: MKPointOfInterestFilter?`

The filter to use for determining the points of interest that appear on the map.

`var showsTraffic: Bool`

A Boolean value that indicates whether the map displays traffic information.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/showsbuildings

- MapKit
- MKMapView
- showsBuildings Deprecated

Instance Property

# showsBuildings

A Boolean value that indicates whether the map displays extruded building information on supported map types.

iOS 7.0–26.2DeprecatediPadOS 7.0–26.2DeprecatedmacOS 10.9–26.2DeprecatedvisionOS 1.0–26.2Deprecated

@MainActor
var showsBuildings: Bool { get set }

## Discussion

When this property is `true` and the camera has a pitch angle greater than zero, the map extrudes buildings so that they extend above the map plane, creating a 3D effect. The default value of this property is `true`.

To display extruded buildings, set the `mapType` property to `MKMapType.standard` or `MKMapType.mutedStandard`.

## See Also

### Configuring the map display

`func setCamera(MKMapCamera, animated: Bool)`

Changes the camera to use for determining the map’s viewing parameters, and optionally animates the change.

`var camera: MKMapCamera`

The camera to use for determining the appearance of the map.

`var showsCompass: Bool`

A Boolean value that indicates whether the map displays a compass control.

`var showsPitchControl: Bool`

A Boolean value that indicates whether the map displays the pitch control.

`var showsScale: Bool`

A Boolean value that indicates whether the map shows scale information.

`var showsZoomControls: Bool`

A Boolean value that indicates whether the map displays zoom controls.

`var showsPointsOfInterest: Bool`

A Boolean value that indicates whether the map displays point-of-interest information.

Deprecated

`var pointOfInterestFilter: MKPointOfInterestFilter?`

The filter to use for determining the points of interest that appear on the map.

`var showsTraffic: Bool`

A Boolean value that indicates whether the map displays traffic information.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/pointofinterestfilter

- MapKit
- MKMapView
- pointOfInterestFilter Deprecated

Instance Property

# pointOfInterestFilter

The filter to use for determining the points of interest that appear on the map.

iOS 13.0–26.2DeprecatediPadOS 13.0–26.2DeprecatedmacOS 10.15–26.2DeprecatedvisionOS 1.0–26.2Deprecated

@NSCopying @MainActor
var pointOfInterestFilter: MKPointOfInterestFilter? { get set }

## See Also

### Configuring the map display

`func setCamera(MKMapCamera, animated: Bool)`

Changes the camera to use for determining the map’s viewing parameters, and optionally animates the change.

`var camera: MKMapCamera`

The camera to use for determining the appearance of the map.

`var showsCompass: Bool`

A Boolean value that indicates whether the map displays a compass control.

`var showsPitchControl: Bool`

A Boolean value that indicates whether the map displays the pitch control.

`var showsScale: Bool`

A Boolean value that indicates whether the map shows scale information.

`var showsZoomControls: Bool`

A Boolean value that indicates whether the map displays zoom controls.

`var showsBuildings: Bool`

A Boolean value that indicates whether the map displays extruded building information on supported map types.

Deprecated

`var showsPointsOfInterest: Bool`

A Boolean value that indicates whether the map displays point-of-interest information.

`var showsTraffic: Bool`

A Boolean value that indicates whether the map displays traffic information.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/showstraffic

- MapKit
- MKMapView
- showsTraffic Deprecated

Instance Property

# showsTraffic

A Boolean value that indicates whether the map displays traffic information.

iOS 9.0–26.2DeprecatediPadOS 9.0–26.2DeprecatedmacOS 10.11–26.2DeprecatedvisionOS 1.0–26.2Deprecated

@MainActor
var showsTraffic: Bool { get set }

## Discussion

The `mapType` property must be set to `MKMapType.standard` or `MKMapType.hybrid` for traffic information to be shown. The default value of this property is `false`.

## See Also

### Configuring the map display

`func setCamera(MKMapCamera, animated: Bool)`

Changes the camera to use for determining the map’s viewing parameters, and optionally animates the change.

`var camera: MKMapCamera`

The camera to use for determining the appearance of the map.

`var showsCompass: Bool`

A Boolean value that indicates whether the map displays a compass control.

`var showsPitchControl: Bool`

A Boolean value that indicates whether the map displays the pitch control.

`var showsScale: Bool`

A Boolean value that indicates whether the map shows scale information.

`var showsZoomControls: Bool`

A Boolean value that indicates whether the map displays zoom controls.

`var showsBuildings: Bool`

A Boolean value that indicates whether the map displays extruded building information on supported map types.

Deprecated

`var showsPointsOfInterest: Bool`

A Boolean value that indicates whether the map displays point-of-interest information.

`var pointOfInterestFilter: MKPointOfInterestFilter?`

The filter to use for determining the points of interest that appear on the map.

---

# https://developer.apple.com/documentation/mapkit/converting-a-user-s-location-to-a-descriptive-placemark



---

# https://developer.apple.com/documentation/mapkit/mkmapview/showsuserlocation

- MapKit
- MKMapView
- showsUserLocation

Instance Property

# showsUserLocation

A Boolean value that indicates whether the map tries to display the user’s location.

@MainActor
var showsUserLocation: Bool { get set }

## Mentioned in

Converting a user’s location to a descriptive placemark

## Discussion

This property doesn’t indicate whether the user’s location is actually visible on the map, only whether the map view tries to display it. Setting this property to `true` causes the map view to use the Core Location framework to find the user’s location and try to display it on the map. While this property is `true`, the map view continues to track the user’s location and update it periodically. The default value of this property is `false`.

Showing the user’s location doesn’t ensure that it’s visible on the map. The user might scroll the map to a different point, causing the location to be offscreen. To determine whether the user’s location displays on the map, use the `isUserLocationVisible` property.

## See Also

### Displaying the user’s location

Transform the user’s location that displays on a map into an informative textual description by reverse geocoding.

`var isUserLocationVisible: Bool`

A Boolean value that indicates whether the user’s location is visible in the map view.

`var userLocation: MKUserLocation`

The annotation object that represents the user’s location.

`var userTrackingMode: MKUserTrackingMode`

The mode to use for tracking the user’s location.

`func setUserTrackingMode(MKUserTrackingMode, animated: Bool)`

Sets the mode to use for tracking the user’s location, with optional animation.

`enum MKUserTrackingMode`

The mode to use for tracking the user’s location on the map.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/isuserlocationvisible

- MapKit
- MKMapView
- isUserLocationVisible

Instance Property

# isUserLocationVisible

A Boolean value that indicates whether the user’s location is visible in the map view.

@MainActor
var isUserLocationVisible: Bool { get }

## Discussion

When determining whether the user’s location is visible, this property factors in the horizontal accuracy of the location data. Specifically, if the rectangle that the user’s location represents, plus or minus the horizontal accuracy of that location, intersects the map’s visible rectangle, this property contains the value `true`. If that location rectangle doesn’t intersect the map’s visible rectangle, this property contains the value `false`.

When the user’s location is unknown, this property contains the value `false`.

## See Also

### Displaying the user’s location

Converting a user’s location to a descriptive placemark

Transform the user’s location that displays on a map into an informative textual description by reverse geocoding.

`var showsUserLocation: Bool`

A Boolean value that indicates whether the map tries to display the user’s location.

`var userLocation: MKUserLocation`

The annotation object that represents the user’s location.

`var userTrackingMode: MKUserTrackingMode`

The mode to use for tracking the user’s location.

`func setUserTrackingMode(MKUserTrackingMode, animated: Bool)`

Sets the mode to use for tracking the user’s location, with optional animation.

`enum MKUserTrackingMode`

The mode to use for tracking the user’s location on the map.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/userlocation

- MapKit
- MKMapView
- userLocation

Instance Property

# userLocation

The annotation object that represents the user’s location.

@MainActor
var userLocation: MKUserLocation { get }

## See Also

### Displaying the user’s location

Converting a user’s location to a descriptive placemark

Transform the user’s location that displays on a map into an informative textual description by reverse geocoding.

`var showsUserLocation: Bool`

A Boolean value that indicates whether the map tries to display the user’s location.

`var isUserLocationVisible: Bool`

A Boolean value that indicates whether the user’s location is visible in the map view.

`var userTrackingMode: MKUserTrackingMode`

The mode to use for tracking the user’s location.

`func setUserTrackingMode(MKUserTrackingMode, animated: Bool)`

Sets the mode to use for tracking the user’s location, with optional animation.

`enum MKUserTrackingMode`

The mode to use for tracking the user’s location on the map.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/usertrackingmode

- MapKit
- MKMapView
- userTrackingMode

Instance Property

# userTrackingMode

The mode to use for tracking the user’s location.

@MainActor
var userTrackingMode: MKUserTrackingMode { get set }

## Discussion

Setting the tracking mode to `MKUserTrackingMode.follow` or `MKUserTrackingMode.followWithHeading` causes the map view to center the map on that location and begin tracking the user’s location. If it’s zoomed out, the map view automatically zooms in on the user’s location, effectively changing the current visible region.

For possible values, see `MKUserTrackingMode`.

## See Also

### Displaying the user’s location

Converting a user’s location to a descriptive placemark

Transform the user’s location that displays on a map into an informative textual description by reverse geocoding.

`var showsUserLocation: Bool`

A Boolean value that indicates whether the map tries to display the user’s location.

`var isUserLocationVisible: Bool`

A Boolean value that indicates whether the user’s location is visible in the map view.

`var userLocation: MKUserLocation`

The annotation object that represents the user’s location.

`func setUserTrackingMode(MKUserTrackingMode, animated: Bool)`

Sets the mode to use for tracking the user’s location, with optional animation.

`enum MKUserTrackingMode`

The mode to use for tracking the user’s location on the map.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/setusertrackingmode(_:animated:)

#app-main)

- MapKit
- MKMapView
- setUserTrackingMode(\_:animated:)

Instance Method

# setUserTrackingMode(\_:animated:)

Sets the mode to use for tracking the user’s location, with optional animation.

@MainActor
func setUserTrackingMode(
_ mode: MKUserTrackingMode,
animated: Bool
)

## Parameters

`mode`

The mode for tracking the user’s location. `MKUserTrackingMode` describes the possible values.

`animated`

If `true`, the map animates the change from the current mode to the new mode; otherwise, it doesn’t. This parameter affects only tracking-mode changes. Changes to the user’s location or heading use animation.

## Discussion

Setting the tracking mode to `MKUserTrackingMode.follow` or `MKUserTrackingMode.followWithHeading` causes the map view to center the map on that location and begin tracking the user’s location. If it’s zoomed out, the map view automatically zooms in on the user’s location, effectively changing the current visible region.

## See Also

### Related Documentation

`func mapView(MKMapView, didChange: MKUserTrackingMode, animated: Bool)`

Tells the delegate when the user-tracking mode changes.

`func mapView(MKMapView, didUpdate: MKUserLocation)`

Tells the delegate when the map view updates the user’s location.

`var heading: CLHeading?`

The heading of the user’s location.

### Displaying the user’s location

Converting a user’s location to a descriptive placemark

Transform the user’s location that displays on a map into an informative textual description by reverse geocoding.

`var showsUserLocation: Bool`

A Boolean value that indicates whether the map tries to display the user’s location.

`var isUserLocationVisible: Bool`

A Boolean value that indicates whether the user’s location is visible in the map view.

`var userLocation: MKUserLocation`

The annotation object that represents the user’s location.

`var userTrackingMode: MKUserTrackingMode`

The mode to use for tracking the user’s location.

`enum MKUserTrackingMode`

The mode to use for tracking the user’s location on the map.

---

# https://developer.apple.com/documentation/mapkit/mkusertrackingmode

- MapKit
- MKUserTrackingMode

Enumeration

# MKUserTrackingMode

The mode to use for tracking the user’s location on the map.

enum MKUserTrackingMode

## Topics

### Constants

`case none`

The map doesn’t follow the user’s location.

`case follow`

The map follows the user location.

`case followWithHeading`

The map follows the user’s location and rotates when the heading changes.

### Initializers

`init?(rawValue: Int)`

## Relationships

### Conforms To

- `BitwiseCopyable`
- `Equatable`
- `Hashable`
- `RawRepresentable`
- `Sendable`
- `SendableMetatype`

## See Also

### Displaying the user’s location

Converting a user’s location to a descriptive placemark

Transform the user’s location that displays on a map into an informative textual description by reverse geocoding.

`var showsUserLocation: Bool`

A Boolean value that indicates whether the map tries to display the user’s location.

`var isUserLocationVisible: Bool`

A Boolean value that indicates whether the user’s location is visible in the map view.

`var userLocation: MKUserLocation`

The annotation object that represents the user’s location.

`var userTrackingMode: MKUserTrackingMode`

The mode to use for tracking the user’s location.

`func setUserTrackingMode(MKUserTrackingMode, animated: Bool)`

Sets the mode to use for tracking the user’s location, with optional animation.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/addannotation(_:)

#app-main)

- MapKit
- MKMapView
- addAnnotation(\_:)

Instance Method

# addAnnotation(\_:)

Adds the specified annotation to the map view.

@MainActor
func addAnnotation(_ annotation: any MKAnnotation)

## Parameters

`annotation`

The annotation object to add to the receiver. This object must conform to the `MKAnnotation` protocol. The map view retains the specified object.

## See Also

### Annotating the map

[`var annotations: [any MKAnnotation]`](https://developer.apple.com/documentation/mapkit/mkmapview/annotations)

The annotations associated with the map view.

[`func addAnnotations([any MKAnnotation])`](https://developer.apple.com/documentation/mapkit/mkmapview/addannotations(_:))

Adds an array of annotation objects to the map view.

`func removeAnnotation(any MKAnnotation)`

Removes the specified annotation object from the map view.

[`func removeAnnotations([any MKAnnotation])`](https://developer.apple.com/documentation/mapkit/mkmapview/removeannotations(_:))

Removes an array of annotation objects from the map view.

Returns the annotation objects within the specified map rectangle.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/removeannotation(_:)

#app-main)

- MapKit
- MKMapView
- removeAnnotation(\_:)

Instance Method

# removeAnnotation(\_:)

Removes the specified annotation object from the map view.

@MainActor
func removeAnnotation(_ annotation: any MKAnnotation)

## Parameters

`annotation`

The annotation object to remove. This object needs to conform to the `MKAnnotation` protocol.

## Discussion

If the annotation is associated with an annotation view, and that view has a reuse identifier, this method removes the annotation view and queues it internally for later reuse. You can retrieve queued annotation views (and associate them with new annotations) using the `dequeueReusableAnnotationView(withIdentifier:)` method.

Removing an annotation object disassociates it from the map view entirely, preventing the map view from displaying it on the map. Typically, you call this method only when you want to hide or delete a specified annotation.

## See Also

### Annotating the map

[`var annotations: [any MKAnnotation]`](https://developer.apple.com/documentation/mapkit/mkmapview/annotations)

The annotations associated with the map view.

`func addAnnotation(any MKAnnotation)`

Adds the specified annotation to the map view.

[`func addAnnotations([any MKAnnotation])`](https://developer.apple.com/documentation/mapkit/mkmapview/addannotations(_:))

Adds an array of annotation objects to the map view.

[`func removeAnnotations([any MKAnnotation])`](https://developer.apple.com/documentation/mapkit/mkmapview/removeannotations(_:))

Removes an array of annotation objects from the map view.

Returns the annotation objects within the specified map rectangle.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/annotations(in:)

#app-main)

- MapKit
- MKMapView
- annotations(in:)

Instance Method

# annotations(in:)

Returns the annotation objects within the specified map rectangle.

@MainActor

## Parameters

`mapRect`

The portion of the map that you want to search for annotations.

## Return Value

The set of annotation objects within `mapRect`.

## Discussion

This method offers a fast way to retrieve the annotation objects in a particular portion of the map. It’s much faster than doing a linear search of the objects in the `annotations` property yourself.

## See Also

### Annotating the map

[`var annotations: [any MKAnnotation]`](https://developer.apple.com/documentation/mapkit/mkmapview/annotations)

The annotations associated with the map view.

`func addAnnotation(any MKAnnotation)`

Adds the specified annotation to the map view.

[`func addAnnotations([any MKAnnotation])`](https://developer.apple.com/documentation/mapkit/mkmapview/addannotations(_:))

Adds an array of annotation objects to the map view.

`func removeAnnotation(any MKAnnotation)`

Removes the specified annotation object from the map view.

[`func removeAnnotations([any MKAnnotation])`](https://developer.apple.com/documentation/mapkit/mkmapview/removeannotations(_:))

Removes an array of annotation objects from the map view.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/annotationvisiblerect

- MapKit
- MKMapView
- annotationVisibleRect

Instance Property

# annotationVisibleRect

The visible rectangle where the map is displaying annotation views.

@MainActor
var annotationVisibleRect: CGRect { get }

## See Also

### Managing annotation selections

[`var selectedAnnotations: [any MKAnnotation]`](https://developer.apple.com/documentation/mapkit/mkmapview/selectedannotations)

The selected annotations.

`func selectAnnotation(any MKAnnotation, animated: Bool)`

Selects the specified annotation and displays a callout view for it.

`func deselectAnnotation((any MKAnnotation)?, animated: Bool)`

Deselects the specified annotation and hides its callout view.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/selectannotation(_:animated:)

#app-main)

- MapKit
- MKMapView
- selectAnnotation(\_:animated:)

Instance Method

# selectAnnotation(\_:animated:)

Selects the specified annotation and displays a callout view for it.

@MainActor
func selectAnnotation(
_ annotation: any MKAnnotation,
animated: Bool
)

## Parameters

`annotation`

The annotation object to select.

`animated`

If `true`, the map view animates the callout view into position.

## Discussion

If the specified annotation isn’t onscreen, and, therefore, doesn’t have an associated annotation view, this method has no effect.

## See Also

### Managing annotation selections

`var annotationVisibleRect: CGRect`

The visible rectangle where the map is displaying annotation views.

[`var selectedAnnotations: [any MKAnnotation]`](https://developer.apple.com/documentation/mapkit/mkmapview/selectedannotations)

The selected annotations.

`func deselectAnnotation((any MKAnnotation)?, animated: Bool)`

Deselects the specified annotation and hides its callout view.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/deselectannotation(_:animated:)

#app-main)

- MapKit
- MKMapView
- deselectAnnotation(\_:animated:)

Instance Method

# deselectAnnotation(\_:animated:)

Deselects the specified annotation and hides its callout view.

@MainActor
func deselectAnnotation(
_ annotation: (any MKAnnotation)?,
animated: Bool
)

## Parameters

`annotation`

The annotation object to deselect.

`animated`

If `true`, the map view animates the callout view offscreen.

## See Also

### Managing annotation selections

`var annotationVisibleRect: CGRect`

The visible rectangle where the map is displaying annotation views.

[`var selectedAnnotations: [any MKAnnotation]`](https://developer.apple.com/documentation/mapkit/mkmapview/selectedannotations)

The selected annotations.

`func selectAnnotation(any MKAnnotation, animated: Bool)`

Selects the specified annotation and displays a callout view for it.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/register(_:forannotationviewwithreuseidentifier:)

#app-main)

- MapKit
- MKMapView
- register(\_:forAnnotationViewWithReuseIdentifier:)

Instance Method

# register(\_:forAnnotationViewWithReuseIdentifier:)

Registers an annotation view class that the map can create automatically.

@MainActor
func register(
_ viewClass: AnyClass?,
forAnnotationViewWithReuseIdentifier identifier: String
)

## Parameters

`viewClass`

The class of an annotation view that you use in your map. The class needs to be a subclass of `MKAnnotationView`.

`identifier`

The reuse identifier to associate with the specified class. This parameter can’t be `nil` or an empty string.

## Discussion

Use this method to register one or more views that you use to display annotations on your map. Register your classes before adding any annotations to the map.

When you register an annotation view class using this method, the `dequeueReusableAnnotationView(withIdentifier:for:)` method uses the provided identifier to create the view that you register. It creates a new view only if an existing view isn’t available for reuse.

## See Also

### Creating annotation views

Returns a reusable annotation view using the specified identifier with a specified existing annotation view, if possible.

Returns a reusable annotation view using its identifier.

Returns the annotation view associated with the specified annotation object, if any.

`let MKMapViewDefaultAnnotationViewReuseIdentifier: String`

The default reuse identifier for your map’s annotation views.

`let MKMapViewDefaultClusterAnnotationViewReuseIdentifier: String`

The default reuse identifier for the annotation view representing a cluster of annotations.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/dequeuereusableannotationview(withidentifier:for:)

#app-main)

- MapKit
- MKMapView
- dequeueReusableAnnotationView(withIdentifier:for:)

Instance Method

# dequeueReusableAnnotationView(withIdentifier:for:)

Returns a reusable annotation view using the specified identifier with a specified existing annotation view, if possible.

@MainActor
func dequeueReusableAnnotationView(
withIdentifier identifier: String,
for annotation: any MKAnnotation

## Parameters

`identifier`

A string identifying the annotation view to create.

`annotation`

The annotation the map is displaying. This method automatically assigns this annotation object to the returned annotation view.

## Return Value

An annotation view with the specified identifier.

## Discussion

For performance reasons, be sure to reuse `MKAnnotationView` objects in your map views. As annotation views move offscreen, the map view moves them to an internally managed reuse queue. As new annotations move onscreen, and the map view prompts your code to provide a corresponding annotation view, use this method to dequeue an existing view. Dequeueing saves time and memory during performance-critical operations, such as scrolling.

If the map view can dequeue an existing view, this method tries to create one from the specified identifier. Before this can happen, you need to register an annotation view class using the `register(_:forAnnotationViewWithReuseIdentifier:)` method. If there’s no registered class with the appropriate identifier, this method throws an exception.

## See Also

### Creating annotation views

`func register(AnyClass?, forAnnotationViewWithReuseIdentifier: String)`

Registers an annotation view class that the map can create automatically.

Returns a reusable annotation view using its identifier.

Returns the annotation view associated with the specified annotation object, if any.

`let MKMapViewDefaultAnnotationViewReuseIdentifier: String`

The default reuse identifier for your map’s annotation views.

`let MKMapViewDefaultClusterAnnotationViewReuseIdentifier: String`

The default reuse identifier for the annotation view representing a cluster of annotations.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/dequeuereusableannotationview(withidentifier:)

#app-main)

- MapKit
- MKMapView
- dequeueReusableAnnotationView(withIdentifier:)

Instance Method

# dequeueReusableAnnotationView(withIdentifier:)

Returns a reusable annotation view using its identifier.

@MainActor

## Parameters

`identifier`

A string identifying the annotation view for the map view to reuse. This string is the same one you specify when initializing the annotation view using the `init(annotation:reuseIdentifier:)` method.

## Return Value

An annotation view with the specified identifier, or `nil` if no such object exists in the reuse queue.

## Discussion

For performance reasons, it’s best practice to reuse `MKAnnotationView` objects in your map views. As annotation views move offscreen, the map view moves them to an internally managed reuse queue. As new annotations move onscreen, and the map view prompts your code to provide a corresponding annotation view, attempt to dequeue an existing view before creating a new one. Dequeueing saves time and memory during performance-critical operations like scrolling.

## See Also

### Creating annotation views

`func register(AnyClass?, forAnnotationViewWithReuseIdentifier: String)`

Registers an annotation view class that the map can create automatically.

Returns a reusable annotation view using the specified identifier with a specified existing annotation view, if possible.

Returns the annotation view associated with the specified annotation object, if any.

`let MKMapViewDefaultAnnotationViewReuseIdentifier: String`

The default reuse identifier for your map’s annotation views.

`let MKMapViewDefaultClusterAnnotationViewReuseIdentifier: String`

The default reuse identifier for the annotation view representing a cluster of annotations.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/view(for:)-33w8k

-33w8k#app-main)

- MapKit
- MKMapView
- view(for:)

Instance Method

# view(for:)

Returns the annotation view associated with the specified annotation object, if any.

@MainActor

## Parameters

`annotation`

The annotation object whose view you want.

## Return Value

The annotation view or `nil` if the view has not yet been created. This method may also return `nil` if the annotation is not in the visible map region and therefore does not have an associated annotation view.

## See Also

### Creating annotation views

`func register(AnyClass?, forAnnotationViewWithReuseIdentifier: String)`

Registers an annotation view class that the map can create automatically.

Returns a reusable annotation view using the specified identifier with a specified existing annotation view, if possible.

Returns a reusable annotation view using its identifier.

`let MKMapViewDefaultAnnotationViewReuseIdentifier: String`

The default reuse identifier for your map’s annotation views.

`let MKMapViewDefaultClusterAnnotationViewReuseIdentifier: String`

The default reuse identifier for the annotation view representing a cluster of annotations.

---

# https://developer.apple.com/documentation/mapkit/mkmapviewdefaultannotationviewreuseidentifier

- MapKit
- MKMapViewDefaultAnnotationViewReuseIdentifier

Global Variable

# MKMapViewDefaultAnnotationViewReuseIdentifier

The default reuse identifier for your map’s annotation views.

let MKMapViewDefaultAnnotationViewReuseIdentifier: String

## Discussion

Use this constant to register a default annotation view. This map view uses this default annotation view when your map view’s delegate doesn’t implement the `mapView(_:viewFor:)` method, or when that method returns `nil`.

## See Also

### Creating annotation views

`func register(AnyClass?, forAnnotationViewWithReuseIdentifier: String)`

Registers an annotation view class that the map can create automatically.

Returns a reusable annotation view using the specified identifier with a specified existing annotation view, if possible.

Returns a reusable annotation view using its identifier.

Returns the annotation view associated with the specified annotation object, if any.

`let MKMapViewDefaultClusterAnnotationViewReuseIdentifier: String`

The default reuse identifier for the annotation view representing a cluster of annotations.

---

# https://developer.apple.com/documentation/mapkit/mkmapviewdefaultclusterannotationviewreuseidentifier

- MapKit
- MKMapViewDefaultClusterAnnotationViewReuseIdentifier

Global Variable

# MKMapViewDefaultClusterAnnotationViewReuseIdentifier

The default reuse identifier for the annotation view representing a cluster of annotations.

let MKMapViewDefaultClusterAnnotationViewReuseIdentifier: String

## Discussion

Use this constant to register a default annotation view to use for clusters of annotations. The map view uses this cluster annotation view when your map view’s delegate doesn’t implement the `mapView(_:viewFor:)` method, or when that method returns `nil`.

## See Also

### Creating annotation views

`func register(AnyClass?, forAnnotationViewWithReuseIdentifier: String)`

Registers an annotation view class that the map can create automatically.

Returns a reusable annotation view using the specified identifier with a specified existing annotation view, if possible.

Returns a reusable annotation view using its identifier.

Returns the annotation view associated with the specified annotation object, if any.

`let MKMapViewDefaultAnnotationViewReuseIdentifier: String`

The default reuse identifier for your map’s annotation views.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/renderer(for:)

#app-main)

- MapKit
- MKMapView
- renderer(for:)

Instance Method

# renderer(for:)

Returns the renderer object for drawing the contents of the specified overlay object.

@MainActor

## Parameters

`overlay`

The overlay object whose renderer you want.

## Return Value

The renderer object in use for the specified overlay or `nil` if the overlay is not onscreen.

## Discussion

This method returns the renderer object that your map delegate provided in its `mapView(_:rendererFor:)` method.

## See Also

### Accessing overlays

[`var overlays: [any MKOverlay]`](https://developer.apple.com/documentation/mapkit/mkmapview/overlays)

The overlay objects associated with the map view.

Returns overlay objects in the specified level of the map.

`enum MKOverlayLevel`

Constants that indicate the position of overlays relative to other content.

Returns the view associated with the overlay object, if any.

Deprecated

---

# https://developer.apple.com/documentation/mapkit/mkoverlaylevel

- MapKit
- MKOverlayLevel

Enumeration

# MKOverlayLevel

Constants that indicate the position of overlays relative to other content.

enum MKOverlayLevel

## Topics

### Constants

`case aboveRoads`

Place the overlay above roadways but below map labels, shields, or point-of-interest icons.

`case aboveLabels`

Place the overlay above map labels, shields, or point-of-interest icons but below annotations and 3D projections of buildings.

### Initializers

`init?(rawValue: Int)`

## Relationships

### Conforms To

- `BitwiseCopyable`
- `Equatable`
- `Hashable`
- `RawRepresentable`
- `Sendable`
- `SendableMetatype`

## See Also

### Accessing overlays

[`var overlays: [any MKOverlay]`](https://developer.apple.com/documentation/mapkit/mkmapview/overlays)

The overlay objects associated with the map view.

Returns overlay objects in the specified level of the map.

Returns the renderer object for drawing the contents of the specified overlay object.

Returns the view associated with the overlay object, if any.

Deprecated

---

# https://developer.apple.com/documentation/mapkit/mkmapview/addoverlay(_:level:)

#app-main)

- MapKit
- MKMapView
- addOverlay(\_:level:)

Instance Method

# addOverlay(\_:level:)

Adds the overlay object to the map at the specified level.

@MainActor
func addOverlay(
_ overlay: any MKOverlay,
level: MKOverlayLevel
)

## Parameters

`overlay`

The overlay object to add. This object needs to conform to the `MKOverlay` protocol.

`level`

The map level at which to place the overlay. For a list of possible values for this parameter, see `MKOverlayLevel`.

## Discussion

Positioning an overlay at a specific level places that overlay’s visual representation in front of or behind other map content such as map labels and point-of-interest icons.

This method adds the specified overlay to the end of the list of overlay objects at the given level. Adding an overlay also causes the map view to begin monitoring the area they represent. As soon as the bounding rectangle of the overlay intersects the visible portion of the map, the map view calls your delegate’s `mapView(_:rendererFor:)` method to get the renderer object to use when drawing the overlay.

To remove an overlay from a map, use the `removeOverlay(_:)` method.

## See Also

### Adding and inserting overlays

[`func addOverlays([any MKOverlay], level: MKOverlayLevel)`](https://developer.apple.com/documentation/mapkit/mkmapview/addoverlays(_:level:))

Adds an array of overlay objects to the map at the specified level.

`func addOverlay(any MKOverlay)`

Adds a single overlay object to the map.

[`func addOverlays([any MKOverlay])`](https://developer.apple.com/documentation/mapkit/mkmapview/addoverlays(_:))

Adds an array of overlay objects to the map.

`func insertOverlay(any MKOverlay, at: Int, level: MKOverlayLevel)`

Inserts an overlay object into the level at the specified index.

`func insertOverlay(any MKOverlay, at: Int)`

Inserts an overlay object into the list associated with the map.

`func insertOverlay(any MKOverlay, above: any MKOverlay)`

Inserts one overlay object above another.

`func insertOverlay(any MKOverlay, below: any MKOverlay)`

Inserts one overlay object below another.

`func exchangeOverlay(any MKOverlay, with: any MKOverlay)`

Exchanges the positions of two overlay objects.

`func exchangeOverlay(at: Int, withOverlayAt: Int)`

Exchanges the position of two overlay objects at the specified index.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/addoverlay(_:)

#app-main)

- MapKit
- MKMapView
- addOverlay(\_:)

Instance Method

# addOverlay(\_:)

Adds a single overlay object to the map.

@MainActor
func addOverlay(_ overlay: any MKOverlay)

## Parameters

`overlay`

The overlay object to add. This object needs to conform to the `MKOverlay` protocol.

## Discussion

The map view adds the specified object to the group of overlay objects in the `MKOverlayLevel.aboveLabels` level. Adding an overlay causes the map view to begin monitoring the area that the overlay represents. As soon as the bounding rectangle of an overlay intersects the visible portion of the map, the map view adds a corresponding overlay view to the map. Implement the `mapView(_:rendererFor:)` method of the map view’s delegate object to provide the overlay view.

To remove an overlay from a map, use the `removeOverlay(_:)` method.

## See Also

### Related Documentation

`func removeOverlay(any MKOverlay)`

Removes a single overlay object from the map.

[`func removeOverlays([any MKOverlay])`](https://developer.apple.com/documentation/mapkit/mkmapview/removeoverlays(_:))

Removes one or more overlay objects from the map.

### Adding and inserting overlays

`func addOverlay(any MKOverlay, level: MKOverlayLevel)`

Adds the overlay object to the map at the specified level.

[`func addOverlays([any MKOverlay], level: MKOverlayLevel)`](https://developer.apple.com/documentation/mapkit/mkmapview/addoverlays(_:level:))

Adds an array of overlay objects to the map at the specified level.

[`func addOverlays([any MKOverlay])`](https://developer.apple.com/documentation/mapkit/mkmapview/addoverlays(_:))

Adds an array of overlay objects to the map.

`func insertOverlay(any MKOverlay, at: Int, level: MKOverlayLevel)`

Inserts an overlay object into the level at the specified index.

`func insertOverlay(any MKOverlay, at: Int)`

Inserts an overlay object into the list associated with the map.

`func insertOverlay(any MKOverlay, above: any MKOverlay)`

Inserts one overlay object above another.

`func insertOverlay(any MKOverlay, below: any MKOverlay)`

Inserts one overlay object below another.

`func exchangeOverlay(any MKOverlay, with: any MKOverlay)`

Exchanges the positions of two overlay objects.

`func exchangeOverlay(at: Int, withOverlayAt: Int)`

Exchanges the position of two overlay objects at the specified index.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/insertoverlay(_:at:level:)

#app-main)

- MapKit
- MKMapView
- insertOverlay(\_:at:level:)

Instance Method

# insertOverlay(\_:at:level:)

Inserts an overlay object into the level at the specified index.

@MainActor
func insertOverlay(
_ overlay: any MKOverlay,
at index: Int,
level: MKOverlayLevel
)

## Parameters

`overlay`

The overlay object to insert.

`index`

The index at which to insert the overlay object. If this value is greater than the number of objects in the `overlays` property, this method appends the object to the end of the array.

`level`

The map level at which to place the overlay. For a list of possible values for this parameter, see `MKOverlayLevel`.

## Discussion

Inserting an overlay at a specific level places that overlay’s visual representation in front of or behind other map content such as map labels and point-of-interest icons.

## See Also

### Adding and inserting overlays

`func addOverlay(any MKOverlay, level: MKOverlayLevel)`

Adds the overlay object to the map at the specified level.

[`func addOverlays([any MKOverlay], level: MKOverlayLevel)`](https://developer.apple.com/documentation/mapkit/mkmapview/addoverlays(_:level:))

Adds an array of overlay objects to the map at the specified level.

`func addOverlay(any MKOverlay)`

Adds a single overlay object to the map.

[`func addOverlays([any MKOverlay])`](https://developer.apple.com/documentation/mapkit/mkmapview/addoverlays(_:))

Adds an array of overlay objects to the map.

`func insertOverlay(any MKOverlay, at: Int)`

Inserts an overlay object into the list associated with the map.

`func insertOverlay(any MKOverlay, above: any MKOverlay)`

Inserts one overlay object above another.

`func insertOverlay(any MKOverlay, below: any MKOverlay)`

Inserts one overlay object below another.

`func exchangeOverlay(any MKOverlay, with: any MKOverlay)`

Exchanges the positions of two overlay objects.

`func exchangeOverlay(at: Int, withOverlayAt: Int)`

Exchanges the position of two overlay objects at the specified index.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/insertoverlay(_:at:)

#app-main)

- MapKit
- MKMapView
- insertOverlay(\_:at:)

Instance Method

# insertOverlay(\_:at:)

Inserts an overlay object into the list associated with the map.

@MainActor
func insertOverlay(
_ overlay: any MKOverlay,
at index: Int
)

## Parameters

`overlay`

The overlay object to insert.

`index`

The index at which to insert the overlay object. If this value is greater than the number of objects in the `overlays` property, this method appends the object to the end of the array.

## Discussion

This method inserts the overlay into the `MKOverlayLevel.aboveLabels` level.

## See Also

### Adding and inserting overlays

`func addOverlay(any MKOverlay, level: MKOverlayLevel)`

Adds the overlay object to the map at the specified level.

[`func addOverlays([any MKOverlay], level: MKOverlayLevel)`](https://developer.apple.com/documentation/mapkit/mkmapview/addoverlays(_:level:))

Adds an array of overlay objects to the map at the specified level.

`func addOverlay(any MKOverlay)`

Adds a single overlay object to the map.

[`func addOverlays([any MKOverlay])`](https://developer.apple.com/documentation/mapkit/mkmapview/addoverlays(_:))

Adds an array of overlay objects to the map.

`func insertOverlay(any MKOverlay, at: Int, level: MKOverlayLevel)`

Inserts an overlay object into the level at the specified index.

`func insertOverlay(any MKOverlay, above: any MKOverlay)`

Inserts one overlay object above another.

`func insertOverlay(any MKOverlay, below: any MKOverlay)`

Inserts one overlay object below another.

`func exchangeOverlay(any MKOverlay, with: any MKOverlay)`

Exchanges the positions of two overlay objects.

`func exchangeOverlay(at: Int, withOverlayAt: Int)`

Exchanges the position of two overlay objects at the specified index.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/insertoverlay(_:above:)

#app-main)

- MapKit
- MKMapView
- insertOverlay(\_:above:)

Instance Method

# insertOverlay(\_:above:)

Inserts one overlay object above another.

@MainActor
func insertOverlay(
_ overlay: any MKOverlay,
above sibling: any MKOverlay
)

## Parameters

`overlay`

The overlay object to insert.

`sibling`

An existing object in the `overlays` array. This object needs to exist in the array and can’t be `nil`.

## Discussion

This method inserts the overlay into the `MKOverlayLevel.aboveLabels` level and positions it relative to the specified sibling. When displaying it, the map view displays the overlay’s contents above that of its sibling. If the sibling isn’t in the same map level, this method appends the overlay to the end of the list of overlays at the indicated level.

## See Also

### Adding and inserting overlays

`func addOverlay(any MKOverlay, level: MKOverlayLevel)`

Adds the overlay object to the map at the specified level.

[`func addOverlays([any MKOverlay], level: MKOverlayLevel)`](https://developer.apple.com/documentation/mapkit/mkmapview/addoverlays(_:level:))

Adds an array of overlay objects to the map at the specified level.

`func addOverlay(any MKOverlay)`

Adds a single overlay object to the map.

[`func addOverlays([any MKOverlay])`](https://developer.apple.com/documentation/mapkit/mkmapview/addoverlays(_:))

Adds an array of overlay objects to the map.

`func insertOverlay(any MKOverlay, at: Int, level: MKOverlayLevel)`

Inserts an overlay object into the level at the specified index.

`func insertOverlay(any MKOverlay, at: Int)`

Inserts an overlay object into the list associated with the map.

`func insertOverlay(any MKOverlay, below: any MKOverlay)`

Inserts one overlay object below another.

`func exchangeOverlay(any MKOverlay, with: any MKOverlay)`

Exchanges the positions of two overlay objects.

`func exchangeOverlay(at: Int, withOverlayAt: Int)`

Exchanges the position of two overlay objects at the specified index.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/insertoverlay(_:below:)

#app-main)

- MapKit
- MKMapView
- insertOverlay(\_:below:)

Instance Method

# insertOverlay(\_:below:)

Inserts one overlay object below another.

@MainActor
func insertOverlay(
_ overlay: any MKOverlay,
below sibling: any MKOverlay
)

## Parameters

`overlay`

The overlay object to insert.

`sibling`

An existing object in the `overlays` array. This object needs to exist in the array and can’t be `nil`.

## Discussion

This method inserts the overlay into the `MKOverlayLevel.aboveLabels` level and positions it relative to the specified sibling. When displaying it, the map view displays the overlay’s contents beneath that of its sibling. If the sibling isn’t in the same map level, this method appends the overlay to the end of the list of overlays at the indicated level.

## See Also

### Adding and inserting overlays

`func addOverlay(any MKOverlay, level: MKOverlayLevel)`

Adds the overlay object to the map at the specified level.

[`func addOverlays([any MKOverlay], level: MKOverlayLevel)`](https://developer.apple.com/documentation/mapkit/mkmapview/addoverlays(_:level:))

Adds an array of overlay objects to the map at the specified level.

`func addOverlay(any MKOverlay)`

Adds a single overlay object to the map.

[`func addOverlays([any MKOverlay])`](https://developer.apple.com/documentation/mapkit/mkmapview/addoverlays(_:))

Adds an array of overlay objects to the map.

`func insertOverlay(any MKOverlay, at: Int, level: MKOverlayLevel)`

Inserts an overlay object into the level at the specified index.

`func insertOverlay(any MKOverlay, at: Int)`

Inserts an overlay object into the list associated with the map.

`func insertOverlay(any MKOverlay, above: any MKOverlay)`

Inserts one overlay object above another.

`func exchangeOverlay(any MKOverlay, with: any MKOverlay)`

Exchanges the positions of two overlay objects.

`func exchangeOverlay(at: Int, withOverlayAt: Int)`

Exchanges the position of two overlay objects at the specified index.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/exchangeoverlay(_:with:)

#app-main)

- MapKit
- MKMapView
- exchangeOverlay(\_:with:)

Instance Method

# exchangeOverlay(\_:with:)

Exchanges the positions of two overlay objects.

@MainActor
func exchangeOverlay(
_ overlay1: any MKOverlay,
with overlay2: any MKOverlay
)

## Parameters

`overlay1`

The first overlay object.

`overlay2`

The second overlay object.

## Discussion

If the overlays are in the same map level, they exchange positions within that level’s array of overlay objects. If they’re in different map levels, the two objects also swap levels. Swapping the position of the overlays affects their visibility in the map view.

## See Also

### Adding and inserting overlays

`func addOverlay(any MKOverlay, level: MKOverlayLevel)`

Adds the overlay object to the map at the specified level.

[`func addOverlays([any MKOverlay], level: MKOverlayLevel)`](https://developer.apple.com/documentation/mapkit/mkmapview/addoverlays(_:level:))

Adds an array of overlay objects to the map at the specified level.

`func addOverlay(any MKOverlay)`

Adds a single overlay object to the map.

[`func addOverlays([any MKOverlay])`](https://developer.apple.com/documentation/mapkit/mkmapview/addoverlays(_:))

Adds an array of overlay objects to the map.

`func insertOverlay(any MKOverlay, at: Int, level: MKOverlayLevel)`

Inserts an overlay object into the level at the specified index.

`func insertOverlay(any MKOverlay, at: Int)`

Inserts an overlay object into the list associated with the map.

`func insertOverlay(any MKOverlay, above: any MKOverlay)`

Inserts one overlay object above another.

`func insertOverlay(any MKOverlay, below: any MKOverlay)`

Inserts one overlay object below another.

`func exchangeOverlay(at: Int, withOverlayAt: Int)`

Exchanges the position of two overlay objects at the specified index.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/exchangeoverlay(at:withoverlayat:)

#app-main)

- MapKit
- MKMapView
- exchangeOverlay(at:withOverlayAt:)

Instance Method

# exchangeOverlay(at:withOverlayAt:)

Exchanges the position of two overlay objects at the specified index.

@MainActor
func exchangeOverlay(
at index1: Int,
withOverlayAt index2: Int
)

## Parameters

`index1`

The index of an overlay in the `MKOverlayLevel.aboveLabels` map level.

`index2`

The index of another overlay in the `MKOverlayLevel.aboveLabels` map level.

## Discussion

If you need to exchange overlays in other map levels, use the `exchangeOverlay(_:with:)` method.

## See Also

### Adding and inserting overlays

`func addOverlay(any MKOverlay, level: MKOverlayLevel)`

Adds the overlay object to the map at the specified level.

[`func addOverlays([any MKOverlay], level: MKOverlayLevel)`](https://developer.apple.com/documentation/mapkit/mkmapview/addoverlays(_:level:))

Adds an array of overlay objects to the map at the specified level.

`func addOverlay(any MKOverlay)`

Adds a single overlay object to the map.

[`func addOverlays([any MKOverlay])`](https://developer.apple.com/documentation/mapkit/mkmapview/addoverlays(_:))

Adds an array of overlay objects to the map.

`func insertOverlay(any MKOverlay, at: Int, level: MKOverlayLevel)`

Inserts an overlay object into the level at the specified index.

`func insertOverlay(any MKOverlay, at: Int)`

Inserts an overlay object into the list associated with the map.

`func insertOverlay(any MKOverlay, above: any MKOverlay)`

Inserts one overlay object above another.

`func insertOverlay(any MKOverlay, below: any MKOverlay)`

Inserts one overlay object below another.

`func exchangeOverlay(any MKOverlay, with: any MKOverlay)`

Exchanges the positions of two overlay objects.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/removeoverlay(_:)

#app-main)

- MapKit
- MKMapView
- removeOverlay(\_:)

Instance Method

# removeOverlay(\_:)

Removes a single overlay object from the map.

@MainActor
func removeOverlay(_ overlay: any MKOverlay)

## Parameters

`overlay`

The overlay object to remove.

## Discussion

This method removes the overlay regardless of the level that it’s in. Removing an overlay also removes its corresponding renderer, if one is in use. If the specified overlay isn’t associated with the map view, this method does nothing.

## See Also

### Related Documentation

`func addOverlay(any MKOverlay)`

Adds a single overlay object to the map.

[`func addOverlays([any MKOverlay])`](https://developer.apple.com/documentation/mapkit/mkmapview/addoverlays(_:))

Adds an array of overlay objects to the map.

### Removing overlays

[`func removeOverlays([any MKOverlay])`](https://developer.apple.com/documentation/mapkit/mkmapview/removeoverlays(_:))

Removes one or more overlay objects from the map.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/convert(_:topointto:)

#app-main)

- MapKit
- MKMapView
- convert(\_:toPointTo:)

Instance Method

# convert(\_:toPointTo:)

Converts a map coordinate to a point in the specified view.

**iOS, iPadOS, Mac Catalyst, tvOS, visionOS**

@MainActor
func convert(
_ coordinate: CLLocationCoordinate2D,
toPointTo view: UIView?

**macOS**

@MainActor
func convert(
_ coordinate: CLLocationCoordinate2D,
toPointTo view: NSView?

## Parameters

`coordinate`

The map coordinate that you want to find the corresponding point for.

`view`

The view where you want to locate the specified map coordinate. If this parameter is `nil`, the method specifies the returned point in the window’s coordinate system. If `view` isn’t `nil`, the point belongs to the same window as the map view.

## Return Value

The point (in the appropriate view or window coordinate system) corresponding to the specified latitude and longitude value.

## See Also

### Converting map coordinates

Converts a point in the specified view’s coordinate system to a map coordinate.

Converts a map region to a rectangle in the specified view.

Converts a rectangle in the specified view’s coordinate system to a map region.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/convert(_:tocoordinatefrom:)

#app-main)

- MapKit
- MKMapView
- convert(\_:toCoordinateFrom:)

Instance Method

# convert(\_:toCoordinateFrom:)

Converts a point in the specified view’s coordinate system to a map coordinate.

**iOS, iPadOS, Mac Catalyst, tvOS, visionOS**

@MainActor
func convert(
_ point: CGPoint,
toCoordinateFrom view: UIView?

**macOS**

@MainActor
func convert(
_ point: CGPoint,
toCoordinateFrom view: NSView?

## Parameters

`point`

The point you want to convert.

`view`

The view that serves as the reference coordinate system for the `point` parameter.

## Return Value

The map coordinate at the specified point.

## See Also

### Converting map coordinates

Converts a map coordinate to a point in the specified view.

Converts a map region to a rectangle in the specified view.

Converts a rectangle in the specified view’s coordinate system to a map region.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/convert(_:torectto:)

#app-main)

- MapKit
- MKMapView
- convert(\_:toRectTo:)

Instance Method

# convert(\_:toRectTo:)

Converts a map region to a rectangle in the specified view.

**iOS, iPadOS, Mac Catalyst, tvOS, visionOS**

@MainActor
func convert(
_ region: MKCoordinateRegion,
toRectTo view: UIView?

**macOS**

@MainActor
func convert(
_ region: MKCoordinateRegion,
toRectTo view: NSView?

## Parameters

`region`

The map region that you want to find the corresponding view rectangle for.

`view`

The view where you want to locate the specified map region. If this parameter is `nil`, the method specifies the returned rectangle in the window’s coordinate system. If `view` isn’t `nil`, the rectangle belongs to the same window as the map view.

## Return Value

The rectangle corresponding to the specified map region.

## See Also

### Converting map coordinates

Converts a map coordinate to a point in the specified view.

Converts a point in the specified view’s coordinate system to a map coordinate.

Converts a rectangle in the specified view’s coordinate system to a map region.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/convert(_:toregionfrom:)



---

# https://developer.apple.com/documentation/mapkit/mkmapview/regionthatfits(_:)

#app-main)

- MapKit
- MKMapView
- regionThatFits(\_:)

Instance Method

# regionThatFits(\_:)

Adjusts the aspect ratio of the specified region to ensure that it fits in the map view’s frame.

@MainActor

## Parameters

`region`

The initial region whose span you want to adjust.

## Return Value

A region that is still centered on the same point of the map but whose span values are adjusted to fit in the map view’s frame.

## Discussion

You can use this method to normalize the region values before displaying them in the map. This method returns a new region that both contains the specified region and fits neatly inside the map view’s frame.

## See Also

### Adjusting map regions and rectangles

Returns a centered map rectangle with the same aspect ratio as the map view’s frame.

Returns a centered, inset map rectangle with the same aspect ratio as the map view’s frame.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/maprectthatfits(_:)

#app-main)

- MapKit
- MKMapView
- mapRectThatFits(\_:)

Instance Method

# mapRectThatFits(\_:)

Returns a centered map rectangle with the same aspect ratio as the map view’s frame.

@MainActor

## Parameters

`mapRect`

The initial map rectangle whose width and height you want to adjust to the view frame.

## Return Value

MapKit centers the map rectangle on the same point of the map, and adjusts the width and height to fit in the map view’s frame.

## Discussion

Returns a map rectangle with the same aspect ratio as the map view’s frame, centered at the same location as the specified map rectangle.

You can use this method to normalize map rectangle values before displaying the corresponding area. This method returns a new map rectangle that both contains the specified rectangle and fits neatly inside the map view’s frame.

## See Also

### Adjusting map regions and rectangles

Adjusts the aspect ratio of the specified region to ensure that it fits in the map view’s frame.

Returns a centered, inset map rectangle with the same aspect ratio as the map view’s frame.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/maprectthatfits(_:edgepadding:)

#app-main)

- MapKit
- MKMapView
- mapRectThatFits(\_:edgePadding:)

Instance Method

# mapRectThatFits(\_:edgePadding:)

Returns a centered, inset map rectangle with the same aspect ratio as the map view’s frame.

**iOS, iPadOS, Mac Catalyst, tvOS, visionOS**

@MainActor
func mapRectThatFits(
_ mapRect: MKMapRect,
edgePadding insets: UIEdgeInsets

**macOS**

@MainActor
func mapRectThatFits(
_ mapRect: MKMapRect,
edgePadding insets: NSEdgeInsets

## Parameters

`mapRect`

The initial map rectangle with the width and height you want to adjust.

`insets`

The distance (in screen points) by which to inset the returned rectangle from the actual boundaries of the map view’s frame.

## Return Value

MapKit centers the map rectangle on the same point of the map, and adjusts the width and height to fit in the map view’s frame, minus its inset values.

## See Also

### Adjusting map regions and rectangles

Adjusts the aspect ratio of the specified region to ensure that it fits in the map view’s frame.

Returns a centered map rectangle with the same aspect ratio as the map view’s frame.

---

# https://developer.apple.com/documentation/mapkit/mkmapview/selectablemapfeatures

- MapKit
- MKMapView
- selectableMapFeatures

Instance Property

# selectableMapFeatures

The property that describes which selectable features the map responds to.

@MainActor
var selectableMapFeatures: MKMapFeatureOptions { get set }

## See Also

### Selecting annotations and annotations views

`func mapView(MKMapView, didSelect: MKAnnotationView)`

Tells the delegate when the user selects one or more of its annotation views.

`func mapView(MKMapView, didDeselect: MKAnnotationView)`

Tells the delegate when the user deselects one or more of its annotation views.

`func mapView(MKMapView, didDeselect: any MKAnnotation)`

Tells the delegate when the user deselects one or more annotations.

`func mapView(MKMapView, didSelect: any MKAnnotation)`

Tells the delegate when the user selects one or more annotations.

---

# https://developer.apple.com/documentation/mapkit/mkstandardmapconfiguration)



---

# https://developer.apple.com/documentation/mapkit/mkhybridmapconfiguration)



---

# https://developer.apple.com/documentation/mapkit/mkimagerymapconfiguration)



---

# https://developer.apple.com/documentation/mapkit/mkmapview/region)



---

# https://developer.apple.com/documentation/mapkit/mkmapview/isscrollenabled)



---

# https://developer.apple.com/documentation/mapkit/mkmapview/iszoomenabled)



---

# https://developer.apple.com/documentation/mapkit/mkmappoint),



---

# https://developer.apple.com/documentation/mapkit/mkmapsize),



---

# https://developer.apple.com/documentation/mapkit/mkmapviewdelegate)



---

# https://developer.apple.com/documentation/mapkit/mkmapviewdelegate).



---

# https://developer.apple.com/documentation/mapkit/mkannotation)



---

# https://developer.apple.com/documentation/mapkit/mkannotationview)



---

# https://developer.apple.com/documentation/mapkit/mkmarkerannotationview)



---

# https://developer.apple.com/documentation/mapkit/mkoverlay)



---

# https://developer.apple.com/documentation/mapkit/mkoverlayrenderer)



---

# https://developer.apple.com/documentation/mapkit/mkmapconfiguration)



---

# https://developer.apple.com/documentation/mapkit/mkpointofinterestfilter).



---

# https://developer.apple.com/documentation/mapkit/mklookaroundviewcontroller).



---

# https://developer.apple.com/documentation/mapkit/mkmapview/preferredconfiguration)



---

# https://developer.apple.com/documentation/mapkit/mkmapview/pitchbuttonvisibility)



---

# https://developer.apple.com/documentation/mapkit/mkmapview/showsusertrackingbutton)



---

# https://developer.apple.com/documentation/mapkit/mkmapview/delegate)



---

# https://developer.apple.com/documentation/mapkit/mkmapview/ispitchenabled)



---

# https://developer.apple.com/documentation/mapkit/mkmapview/isrotateenabled)



---

# https://developer.apple.com/documentation/mapkit/mkmapview/maptype)



---

# https://developer.apple.com/documentation/mapkit/mkmapview/setregion(_:animated:))



---

# https://developer.apple.com/documentation/mapkit/mkmapview/centercoordinate)



---

# https://developer.apple.com/documentation/mapkit/mkmapview/setcenter(_:animated:))



---

# https://developer.apple.com/documentation/mapkit/mkmapview/showannotations(_:animated:))

)#app-main)

# The page you're looking for can't be found.

Search developer.apple.comSearch Icon

---

# https://developer.apple.com/documentation/mapkit/mkmapview/visiblemaprect)



---

# https://developer.apple.com/documentation/mapkit/mkmapview/setvisiblemaprect(_:animated:))

)#app-main)

# The page you're looking for can't be found.

Search developer.apple.comSearch Icon

---

# https://developer.apple.com/documentation/mapkit/mkmapview/setvisiblemaprect(_:edgepadding:animated:))

)#app-main)

# The page you're looking for can't be found.

Search developer.apple.comSearch Icon

---

# https://developer.apple.com/documentation/mapkit/mkmapview/setcameraboundary(_:animated:))

)#app-main)

# The page you're looking for can't be found.

Search developer.apple.comSearch Icon

---

# https://developer.apple.com/documentation/mapkit/mkmapview/cameraboundary-swift.property)

# The page you're looking for can't be found.

Search developer.apple.comSearch Icon

---

# https://developer.apple.com/documentation/mapkit/mkmapview/setcamerazoomrange(_:animated:))

)#app-main)

# The page you're looking for can't be found.

Search developer.apple.comSearch Icon

---

# https://developer.apple.com/documentation/mapkit/mkmapview/camerazoomrange-swift.property)

# The page you're looking for can't be found.

Search developer.apple.comSearch Icon

---

# https://developer.apple.com/documentation/mapkit/mkmapview/cameraboundary-swift.class)

# The page you're looking for can't be found.

Search developer.apple.comSearch Icon

---

# https://developer.apple.com/documentation/mapkit/mkmapview/camerazoomrange-swift.class)

# The page you're looking for can't be found.

Search developer.apple.comSearch Icon

---

# https://developer.apple.com/documentation/mapkit/mkmapview/setcamera(_:animated:))



---

# https://developer.apple.com/documentation/mapkit/mkmapview/camera)



---

# https://developer.apple.com/documentation/mapkit/mkmapview/showscompass)



---

# https://developer.apple.com/documentation/mapkit/mkmapview/showspitchcontrol)



---

# https://developer.apple.com/documentation/mapkit/mkmapview/showsscale)



---

# https://developer.apple.com/documentation/mapkit/mkmapview/showszoomcontrols)



---

# https://developer.apple.com/documentation/mapkit/mkmapview/showsbuildings)



---

# https://developer.apple.com/documentation/mapkit/mkmapview/pointofinterestfilter)



---

# https://developer.apple.com/documentation/mapkit/mkmapview/showstraffic)



---

# https://developer.apple.com/documentation/mapkit/converting-a-user-s-location-to-a-descriptive-placemark)

# The page you're looking for can't be found.

Search developer.apple.comSearch Icon

---

# https://developer.apple.com/documentation/mapkit/mkmapview/showsuserlocation)



---

# https://developer.apple.com/documentation/mapkit/mkmapview/isuserlocationvisible)



---

# https://developer.apple.com/documentation/mapkit/mkmapview/userlocation)



---

# https://developer.apple.com/documentation/mapkit/mklaunchoptionsdirectionsmodekey

- MapKit
- MKLaunchOptionsDirectionsModeKey

Global Variable

# MKLaunchOptionsDirectionsModeKey

The mode of transportation.

let MKLaunchOptionsDirectionsModeKey: String

## Discussion

The value of this key is an `NSString` corresponding to one of the values described in Directions mode values. You specify this key to tell the Maps app which mode of transport to use when generating directions.

## See Also

### Launch options

`let MKLaunchOptionsCameraKey: String`

The virtual camera to use for viewing the map.

`let MKLaunchOptionsDirectionsModeCycling: String`

Cycling directions between the specified start and end points.

`let MKLaunchOptionsDirectionsModeDefault: String`

Directions that match the user’s preferred transportation type.

`let MKLaunchOptionsDirectionsModeDriving: String`

Driving directions between the specified start and end points.

`let MKLaunchOptionsDirectionsModeTransit: String`

Public transit directions between the specified start and end points.

`let MKLaunchOptionsDirectionsModeWalking: String`

Walking directions between the specified start and end points.

`let MKLaunchOptionsMapCenterKey: String`

The coordinate value on which to center the map.

`let MKLaunchOptionsMapSpanKey: String`

The amount of the map to display.

`let MKLaunchOptionsMapTypeKey: String`

The type of map (standard, satellite, or hybrid) to display.

`let MKLaunchOptionsShowsTrafficKey: String`

A Boolean value that indicates whether to display traffic information.

---

# https://developer.apple.com/documentation/mapkit/mklaunchoptionsmapcenterkey

- MapKit
- MKLaunchOptionsMapCenterKey

Global Variable

# MKLaunchOptionsMapCenterKey

The coordinate value on which to center the map.

let MKLaunchOptionsMapCenterKey: String

## Discussion

The value of this key is an `NSValue` object that contains an encoded `CLLocationCoordinate2D` structure.

## See Also

### Launch options

`let MKLaunchOptionsCameraKey: String`

The virtual camera to use for viewing the map.

`let MKLaunchOptionsDirectionsModeCycling: String`

Cycling directions between the specified start and end points.

`let MKLaunchOptionsDirectionsModeDefault: String`

Directions that match the user’s preferred transportation type.

`let MKLaunchOptionsDirectionsModeDriving: String`

Driving directions between the specified start and end points.

`let MKLaunchOptionsDirectionsModeKey: String`

The mode of transportation.

`let MKLaunchOptionsDirectionsModeTransit: String`

Public transit directions between the specified start and end points.

`let MKLaunchOptionsDirectionsModeWalking: String`

Walking directions between the specified start and end points.

`let MKLaunchOptionsMapSpanKey: String`

The amount of the map to display.

`let MKLaunchOptionsMapTypeKey: String`

The type of map (standard, satellite, or hybrid) to display.

`let MKLaunchOptionsShowsTrafficKey: String`

A Boolean value that indicates whether to display traffic information.

---

# https://developer.apple.com/documentation/mapkit/mklaunchoptionsmapspankey

- MapKit
- MKLaunchOptionsMapSpanKey

Global Variable

# MKLaunchOptionsMapSpanKey

The amount of the map to display.

let MKLaunchOptionsMapSpanKey: String

## Discussion

The value of this key is an `NSValue` object that contains an encoded `MKCoordinateSpan` structure.

## See Also

### Launch options

`let MKLaunchOptionsCameraKey: String`

The virtual camera to use for viewing the map.

`let MKLaunchOptionsDirectionsModeCycling: String`

Cycling directions between the specified start and end points.

`let MKLaunchOptionsDirectionsModeDefault: String`

Directions that match the user’s preferred transportation type.

`let MKLaunchOptionsDirectionsModeDriving: String`

Driving directions between the specified start and end points.

`let MKLaunchOptionsDirectionsModeKey: String`

The mode of transportation.

`let MKLaunchOptionsDirectionsModeTransit: String`

Public transit directions between the specified start and end points.

`let MKLaunchOptionsDirectionsModeWalking: String`

Walking directions between the specified start and end points.

`let MKLaunchOptionsMapCenterKey: String`

The coordinate value on which to center the map.

`let MKLaunchOptionsMapTypeKey: String`

The type of map (standard, satellite, or hybrid) to display.

`let MKLaunchOptionsShowsTrafficKey: String`

A Boolean value that indicates whether to display traffic information.

---

# https://developer.apple.com/documentation/mapkit/launch-options-dictionary-keys).



---

# https://developer.apple.com/documentation/mapkit/mklaunchoptionscamerakey

- MapKit
- MKLaunchOptionsCameraKey

Global Variable

# MKLaunchOptionsCameraKey

The virtual camera to use for viewing the map.

let MKLaunchOptionsCameraKey: String

## Discussion

The value of this key is an `MKMapCamera` object that describes a virtual camera that can specify a 3D perspective for the map. If you don’t specify this key, the Maps app uses its current settings to define the appearance of the map.

## See Also

### Launch options

`let MKLaunchOptionsDirectionsModeCycling: String`

Cycling directions between the specified start and end points.

`let MKLaunchOptionsDirectionsModeDefault: String`

Directions that match the user’s preferred transportation type.

`let MKLaunchOptionsDirectionsModeDriving: String`

Driving directions between the specified start and end points.

`let MKLaunchOptionsDirectionsModeKey: String`

The mode of transportation.

`let MKLaunchOptionsDirectionsModeTransit: String`

Public transit directions between the specified start and end points.

`let MKLaunchOptionsDirectionsModeWalking: String`

Walking directions between the specified start and end points.

`let MKLaunchOptionsMapCenterKey: String`

The coordinate value on which to center the map.

`let MKLaunchOptionsMapSpanKey: String`

The amount of the map to display.

`let MKLaunchOptionsMapTypeKey: String`

The type of map (standard, satellite, or hybrid) to display.

`let MKLaunchOptionsShowsTrafficKey: String`

A Boolean value that indicates whether to display traffic information.

---

# https://developer.apple.com/documentation/mapkit/mklaunchoptionsdirectionsmodecycling

- MapKit
- MKLaunchOptionsDirectionsModeCycling

Global Variable

# MKLaunchOptionsDirectionsModeCycling

Cycling directions between the specified start and end points.

let MKLaunchOptionsDirectionsModeCycling: String

## Discussion

You can use this launch options key to open the Maps app directly in the mode that enables route planning that returns cycling directions, as shown in this example.

Button("Cycling Directions") {
selectedItem.openInMaps(
launchOptions: [MKLaunchOptionsDirectionsModeKey: MKLaunchOptionsDirectionsModeCycling]
)
}

## See Also

### Launch options

`let MKLaunchOptionsCameraKey: String`

The virtual camera to use for viewing the map.

`let MKLaunchOptionsDirectionsModeDefault: String`

Directions that match the user’s preferred transportation type.

`let MKLaunchOptionsDirectionsModeDriving: String`

Driving directions between the specified start and end points.

`let MKLaunchOptionsDirectionsModeKey: String`

The mode of transportation.

`let MKLaunchOptionsDirectionsModeTransit: String`

Public transit directions between the specified start and end points.

`let MKLaunchOptionsDirectionsModeWalking: String`

Walking directions between the specified start and end points.

`let MKLaunchOptionsMapCenterKey: String`

The coordinate value on which to center the map.

`let MKLaunchOptionsMapSpanKey: String`

The amount of the map to display.

`let MKLaunchOptionsMapTypeKey: String`

The type of map (standard, satellite, or hybrid) to display.

`let MKLaunchOptionsShowsTrafficKey: String`

A Boolean value that indicates whether to display traffic information.

---

# https://developer.apple.com/documentation/mapkit/mklaunchoptionsdirectionsmodedefault

- MapKit
- MKLaunchOptionsDirectionsModeDefault

Global Variable

# MKLaunchOptionsDirectionsModeDefault

Directions that match the user’s preferred transportation type.

let MKLaunchOptionsDirectionsModeDefault: String

## See Also

### Launch options

`let MKLaunchOptionsCameraKey: String`

The virtual camera to use for viewing the map.

`let MKLaunchOptionsDirectionsModeCycling: String`

Cycling directions between the specified start and end points.

`let MKLaunchOptionsDirectionsModeDriving: String`

Driving directions between the specified start and end points.

`let MKLaunchOptionsDirectionsModeKey: String`

The mode of transportation.

`let MKLaunchOptionsDirectionsModeTransit: String`

Public transit directions between the specified start and end points.

`let MKLaunchOptionsDirectionsModeWalking: String`

Walking directions between the specified start and end points.

`let MKLaunchOptionsMapCenterKey: String`

The coordinate value on which to center the map.

`let MKLaunchOptionsMapSpanKey: String`

The amount of the map to display.

`let MKLaunchOptionsMapTypeKey: String`

The type of map (standard, satellite, or hybrid) to display.

`let MKLaunchOptionsShowsTrafficKey: String`

A Boolean value that indicates whether to display traffic information.

---

# https://developer.apple.com/documentation/mapkit/mklaunchoptionsdirectionsmodedriving

- MapKit
- MKLaunchOptionsDirectionsModeDriving

Global Variable

# MKLaunchOptionsDirectionsModeDriving

Driving directions between the specified start and end points.

let MKLaunchOptionsDirectionsModeDriving: String

## See Also

### Launch options

`let MKLaunchOptionsCameraKey: String`

The virtual camera to use for viewing the map.

`let MKLaunchOptionsDirectionsModeCycling: String`

Cycling directions between the specified start and end points.

`let MKLaunchOptionsDirectionsModeDefault: String`

Directions that match the user’s preferred transportation type.

`let MKLaunchOptionsDirectionsModeKey: String`

The mode of transportation.

`let MKLaunchOptionsDirectionsModeTransit: String`

Public transit directions between the specified start and end points.

`let MKLaunchOptionsDirectionsModeWalking: String`

Walking directions between the specified start and end points.

`let MKLaunchOptionsMapCenterKey: String`

The coordinate value on which to center the map.

`let MKLaunchOptionsMapSpanKey: String`

The amount of the map to display.

`let MKLaunchOptionsMapTypeKey: String`

The type of map (standard, satellite, or hybrid) to display.

`let MKLaunchOptionsShowsTrafficKey: String`

A Boolean value that indicates whether to display traffic information.

---

# https://developer.apple.com/documentation/mapkit/mklaunchoptionsdirectionsmodetransit

- MapKit
- MKLaunchOptionsDirectionsModeTransit

Global Variable

# MKLaunchOptionsDirectionsModeTransit

Public transit directions between the specified start and end points.

let MKLaunchOptionsDirectionsModeTransit: String

## See Also

### Launch options

`let MKLaunchOptionsCameraKey: String`

The virtual camera to use for viewing the map.

`let MKLaunchOptionsDirectionsModeCycling: String`

Cycling directions between the specified start and end points.

`let MKLaunchOptionsDirectionsModeDefault: String`

Directions that match the user’s preferred transportation type.

`let MKLaunchOptionsDirectionsModeDriving: String`

Driving directions between the specified start and end points.

`let MKLaunchOptionsDirectionsModeKey: String`

The mode of transportation.

`let MKLaunchOptionsDirectionsModeWalking: String`

Walking directions between the specified start and end points.

`let MKLaunchOptionsMapCenterKey: String`

The coordinate value on which to center the map.

`let MKLaunchOptionsMapSpanKey: String`

The amount of the map to display.

`let MKLaunchOptionsMapTypeKey: String`

The type of map (standard, satellite, or hybrid) to display.

`let MKLaunchOptionsShowsTrafficKey: String`

A Boolean value that indicates whether to display traffic information.

---

# https://developer.apple.com/documentation/mapkit/mklaunchoptionsdirectionsmodewalking

- MapKit
- MKLaunchOptionsDirectionsModeWalking

Global Variable

# MKLaunchOptionsDirectionsModeWalking

Walking directions between the specified start and end points.

let MKLaunchOptionsDirectionsModeWalking: String

## See Also

### Launch options

`let MKLaunchOptionsCameraKey: String`

The virtual camera to use for viewing the map.

`let MKLaunchOptionsDirectionsModeCycling: String`

Cycling directions between the specified start and end points.

`let MKLaunchOptionsDirectionsModeDefault: String`

Directions that match the user’s preferred transportation type.

`let MKLaunchOptionsDirectionsModeDriving: String`

Driving directions between the specified start and end points.

`let MKLaunchOptionsDirectionsModeKey: String`

The mode of transportation.

`let MKLaunchOptionsDirectionsModeTransit: String`

Public transit directions between the specified start and end points.

`let MKLaunchOptionsMapCenterKey: String`

The coordinate value on which to center the map.

`let MKLaunchOptionsMapSpanKey: String`

The amount of the map to display.

`let MKLaunchOptionsMapTypeKey: String`

The type of map (standard, satellite, or hybrid) to display.

`let MKLaunchOptionsShowsTrafficKey: String`

A Boolean value that indicates whether to display traffic information.

---

# https://developer.apple.com/documentation/mapkit/mklaunchoptionsmaptypekey

- MapKit
- MKLaunchOptionsMapTypeKey

Global Variable

# MKLaunchOptionsMapTypeKey

The type of map (standard, satellite, or hybrid) to display.

let MKLaunchOptionsMapTypeKey: String

## Discussion

The value of this key is an `NSNumber` object whose value is an integer corresponding to an `MKMapType` value.

## See Also

### Launch options

`let MKLaunchOptionsCameraKey: String`

The virtual camera to use for viewing the map.

`let MKLaunchOptionsDirectionsModeCycling: String`

Cycling directions between the specified start and end points.

`let MKLaunchOptionsDirectionsModeDefault: String`

Directions that match the user’s preferred transportation type.

`let MKLaunchOptionsDirectionsModeDriving: String`

Driving directions between the specified start and end points.

`let MKLaunchOptionsDirectionsModeKey: String`

The mode of transportation.

`let MKLaunchOptionsDirectionsModeTransit: String`

Public transit directions between the specified start and end points.

`let MKLaunchOptionsDirectionsModeWalking: String`

Walking directions between the specified start and end points.

`let MKLaunchOptionsMapCenterKey: String`

The coordinate value on which to center the map.

`let MKLaunchOptionsMapSpanKey: String`

The amount of the map to display.

`let MKLaunchOptionsShowsTrafficKey: String`

A Boolean value that indicates whether to display traffic information.

---

# https://developer.apple.com/documentation/mapkit/mklaunchoptionsshowstraffickey

- MapKit
- MKLaunchOptionsShowsTrafficKey

Global Variable

# MKLaunchOptionsShowsTrafficKey

A Boolean value that indicates whether to display traffic information.

let MKLaunchOptionsShowsTrafficKey: String

## Discussion

The value of this key is an `NSNumber` object that contains a Boolean value. If you don’t specify this key, the Maps app uses its current settings to determine whether to display traffic.

## See Also

### Launch options

`let MKLaunchOptionsCameraKey: String`

The virtual camera to use for viewing the map.

`let MKLaunchOptionsDirectionsModeCycling: String`

Cycling directions between the specified start and end points.

`let MKLaunchOptionsDirectionsModeDefault: String`

Directions that match the user’s preferred transportation type.

`let MKLaunchOptionsDirectionsModeDriving: String`

Driving directions between the specified start and end points.

`let MKLaunchOptionsDirectionsModeKey: String`

The mode of transportation.

`let MKLaunchOptionsDirectionsModeTransit: String`

Public transit directions between the specified start and end points.

`let MKLaunchOptionsDirectionsModeWalking: String`

Walking directions between the specified start and end points.

`let MKLaunchOptionsMapCenterKey: String`

The coordinate value on which to center the map.

`let MKLaunchOptionsMapSpanKey: String`

The amount of the map to display.

`let MKLaunchOptionsMapTypeKey: String`

The type of map (standard, satellite, or hybrid) to display.

---

# https://developer.apple.com/documentation/mapkit/mklaunchoptionscamerakey)



---

# https://developer.apple.com/documentation/mapkit/mklaunchoptionsdirectionsmodecycling)

# The page you're looking for can't be found.

Search developer.apple.comSearch Icon

---

# https://developer.apple.com/documentation/mapkit/mklaunchoptionsdirectionsmodedefault)

# The page you're looking for can't be found.

Search developer.apple.comSearch Icon

---

# https://developer.apple.com/documentation/mapkit/mklaunchoptionsdirectionsmodedriving)

# The page you're looking for can't be found.

Search developer.apple.comSearch Icon

---

# https://developer.apple.com/documentation/mapkit/mklaunchoptionsdirectionsmodekey)



---

# https://developer.apple.com/documentation/mapkit/mklaunchoptionsdirectionsmodetransit)

# The page you're looking for can't be found.

Search developer.apple.comSearch Icon

---

# https://developer.apple.com/documentation/mapkit/mklaunchoptionsdirectionsmodewalking)

# The page you're looking for can't be found.

Search developer.apple.comSearch Icon

---

# https://developer.apple.com/documentation/mapkit/mklaunchoptionsmapspankey)



---

# https://developer.apple.com/documentation/mapkit/mklaunchoptionsmaptypekey)



---

# https://developer.apple.com/documentation/mapkit/mklaunchoptionsshowstraffickey)



---

# https://developer.apple.com/documentation/mapkit/directions-mode-values).



---

# https://developer.apple.com/documentation/mapkit/mklaunchoptionsmapcenterkey)



---

