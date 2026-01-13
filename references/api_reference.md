# CarPlay API Reference

Complete reference for the CarPlay framework APIs.

## Core Classes

### CPTemplateApplicationSceneDelegate

The main delegate for CarPlay scene lifecycle events.

```swift
protocol CPTemplateApplicationSceneDelegate : UISceneDelegate {
    // Required
    func templateApplicationScene(
        _ templateApplicationScene: CPTemplateApplicationScene,
        didConnect interfaceController: CPInterfaceController
    )

    func templateApplicationScene(
        _ templateApplicationScene: CPTemplateApplicationScene,
        didDisconnect interfaceController: CPInterfaceController
    )

    // Optional
    func templateApplicationScene(
        _ templateApplicationScene: CPTemplateApplicationScene,
        didSelect navigationAlert: CPNavigationAlert
    )

    func templateApplicationScene(
        _ templateApplicationScene: CPTemplateApplicationScene,
        didSelect maneuver: CPManeuver
    )
}
```

### CPInterfaceController

Manages the template stack and navigation.

```swift
class CPInterfaceController : NSObject {
    // Template Management
    func setRootTemplate(_ rootTemplate: CPTemplate, animated: Bool, completion: ((Bool, Error?) -> Void)?)
    func pushTemplate(_ templateToPush: CPTemplate, animated: Bool, completion: ((Bool, Error?) -> Void)?)
    func popTemplate(animated: Bool, completion: ((Bool, Error?) -> Void)?)
    func popToRootTemplate(animated: Bool, completion: ((Bool, Error?) -> Void)?)
    func popToTemplate(_ targetTemplate: CPTemplate, animated: Bool, completion: ((Bool, Error?) -> Void)?)

    // Modal Presentation
    func presentTemplate(_ templateToPresent: CPTemplate, animated: Bool, completion: ((Bool, Error?) -> Void)?)
    func dismissTemplate(animated: Bool, completion: ((Bool, Error?) -> Void)?)

    // Properties
    var delegate: CPInterfaceControllerDelegate?
    var rootTemplate: CPTemplate?
    var topTemplate: CPTemplate?
    var templates: [CPTemplate]
    var presentedTemplate: CPTemplate?
    var carTraitCollection: UITraitCollection
}
```

### CPTemplateApplicationScene

The scene object for CarPlay.

```swift
class CPTemplateApplicationScene : UIScene {
    var interfaceController: CPInterfaceController
    var carWindow: CPWindow
    var contentStyle: CPContentStyle
}
```

### CPWindow

The window for CarPlay display content.

```swift
class CPWindow : UIWindow {
    var rootViewController: UIViewController?
    var templateApplicationScene: CPTemplateApplicationScene?
}
```

## Templates

### CPTemplate (Base Class)

```swift
class CPTemplate : NSObject {
    var userInfo: Any?
    var tabTitle: String?
    var tabImage: UIImage?
    var tabSystemItem: UITabBarItem.SystemItem?
    var showsTabBadge: Bool
}
```

### CPListTemplate

```swift
class CPListTemplate : CPTemplate {
    init(title: String?, sections: [CPListSection])
    init(title: String?, sections: [CPListSection], assistantCellConfiguration: CPAssistantCellConfiguration?)

    var sections: [CPListSection]
    var title: String?
    var emptyViewTitleVariants: [String]
    var emptyViewSubtitleVariants: [String]

    func updateSections(_ sections: [CPListSection])
}
```

### CPListSection

```swift
class CPListSection : NSObject {
    init(items: [CPListItem])
    init(items: [CPListItem], header: String?, sectionIndexTitle: String?)

    var items: [CPListItem]
    var header: String?
    var sectionIndexTitle: String?
}
```

### CPListItem

```swift
class CPListItem : NSObject, CPSelectableListItem {
    init(text: String?, detailText: String?)
    init(text: String?, detailText: String?, image: UIImage?)
    init(text: String?, detailText: String?, image: UIImage?, accessoryImage: UIImage?, accessoryType: CPListItemAccessoryType)

    var text: String?
    var detailText: String?
    var image: UIImage?
    var accessoryImage: UIImage?
    var accessoryType: CPListItemAccessoryType
    var isEnabled: Bool
    var handler: CPSelectableListItemHandler?

    func setImage(_ image: UIImage?)
    func setDetailText(_ detailText: String?)
}

enum CPListItemAccessoryType {
    case none
    case disclosureIndicator
    case cloud
}
```

### CPListImageRowItem

```swift
class CPListImageRowItem : NSObject, CPSelectableListItem {
    init(text: String, images: [UIImage])

    var text: String
    var images: [UIImage]
    var listImageRowHandler: CPListImageRowItemHandler?
    var handler: CPSelectableListItemHandler?
}
```

### CPTabBarTemplate

```swift
class CPTabBarTemplate : CPTemplate {
    init(templates: [CPTemplate])

    var templates: [CPTemplate]
    var selectedTemplate: CPTemplate?
    var delegate: CPTabBarTemplateDelegate?

    func updateTemplates(_ newTemplates: [CPTemplate])
}

protocol CPTabBarTemplateDelegate {
    func tabBarTemplate(_ tabBarTemplate: CPTabBarTemplate, didSelect selectedTemplate: CPTemplate)
}
```

### CPGridTemplate

```swift
class CPGridTemplate : CPTemplate {
    init(title: String?, gridButtons: [CPGridButton])

    var title: String?
    var gridButtons: [CPGridButton]

    func updateGridButtons(_ gridButtons: [CPGridButton])
}
```

### CPGridButton

```swift
class CPGridButton : NSObject {
    init(titleVariants: [String], image: UIImage, handler: CPGridButtonHandler)

    var titleVariants: [String]
    var image: UIImage
    var isEnabled: Bool
}
```

### CPInformationTemplate

```swift
class CPInformationTemplate : CPTemplate {
    init(title: String, layout: CPInformationTemplateLayout, items: [CPInformationItem], actions: [CPTextButton])

    var title: String
    var layout: CPInformationTemplateLayout
    var items: [CPInformationItem]
    var actions: [CPTextButton]
}

enum CPInformationTemplateLayout {
    case leading
    case twoColumn
}
```

### CPInformationItem

```swift
class CPInformationItem : NSObject {
    init(title: String?, detail: String?)

    var title: String?
    var detail: String?
}
```

### CPAlertTemplate

```swift
class CPAlertTemplate : CPTemplate {
    init(titleVariants: [String], actions: [CPAlertAction])

    var titleVariants: [String]
    var actions: [CPAlertAction]
}
```

### CPAlertAction

```swift
class CPAlertAction : NSObject {
    init(title: String, style: CPAlertActionStyle, handler: CPAlertActionHandler)

    var title: String
    var style: CPAlertActionStyle
}

enum CPAlertActionStyle {
    case `default`
    case cancel
    case destructive
}
```

### CPActionSheetTemplate

```swift
class CPActionSheetTemplate : CPTemplate {
    init(title: String?, message: String?, actions: [CPAlertAction])

    var title: String?
    var message: String?
    var actions: [CPAlertAction]
}
```

### CPMapTemplate

```swift
class CPMapTemplate : CPTemplate {
    var mapDelegate: CPMapTemplateDelegate?
    var mapButtons: [CPMapButton]
    var leadingNavigationBarButtons: [CPBarButton]
    var trailingNavigationBarButtons: [CPBarButton]
    var automaticallyHidesNavigationBar: Bool
    var hidesButtonsWithNavigationBar: Bool
    var guidanceBackgroundColor: UIColor
    var tripEstimateStyle: CPTripEstimateStyle
    var currentNavigationAlert: CPNavigationAlert?

    func showTripPreviews(_ tripPreviews: [CPTrip], textConfiguration: CPTripPreviewTextConfiguration?)
    func hideTripPreviews()
    func startNavigationSession(for trip: CPTrip) -> CPNavigationSession
    func showPanningInterface(animated: Bool)
    func dismissPanningInterface(animated: Bool)
    func present(navigationAlert: CPNavigationAlert, animated: Bool)
    func dismissNavigationAlert(animated: Bool, completion: ((Bool) -> Void)?)
}
```

### CPPointOfInterestTemplate

```swift
class CPPointOfInterestTemplate : CPTemplate {
    init(title: String, pointsOfInterest: [CPPointOfInterest], selectedIndex: Int)

    var title: String
    var pointsOfInterest: [CPPointOfInterest]
    var selectedIndex: Int
    var pointOfInterestDelegate: CPPointOfInterestTemplateDelegate?

    func setPointsOfInterest(_ pointsOfInterest: [CPPointOfInterest], selectedIndex: Int)
}
```

### CPPointOfInterest

```swift
class CPPointOfInterest : NSObject {
    init(location: MKMapItem, title: String, subtitle: String?, summary: String?, detailTitle: String?, detailSubtitle: String?, detailSummary: String?, pinImage: UIImage?)

    var location: MKMapItem
    var title: String
    var subtitle: String?
    var summary: String?
    var detailTitle: String?
    var detailSubtitle: String?
    var detailSummary: String?
    var pinImage: UIImage?
    var primaryButton: CPTextButton?
    var secondaryButton: CPTextButton?
}
```

### CPNowPlayingTemplate

```swift
class CPNowPlayingTemplate : CPTemplate {
    static var shared: CPNowPlayingTemplate

    var isUpNextButtonEnabled: Bool
    var upNextButtonTitle: String
    var isAlbumArtistButtonEnabled: Bool
    var nowPlayingButtons: [CPNowPlayingButton]

    func updateNowPlayingButtons(_ nowPlayingButtons: [CPNowPlayingButton])
    func add(_ observer: CPNowPlayingTemplateObserver)
    func remove(_ observer: CPNowPlayingTemplateObserver)
}
```

### CPVoiceControlTemplate

```swift
class CPVoiceControlTemplate : CPTemplate {
    init(voiceControlStates: [CPVoiceControlState])

    var voiceControlStates: [CPVoiceControlState]

    func activateVoiceControlState(_ identifier: String)
}
```

## Navigation

### CPNavigationSession

```swift
class CPNavigationSession : NSObject {
    var upcomingManeuvers: [CPManeuver]
    var trip: CPTrip

    func pauseTrip(for reason: CPTripPauseReason, description: String?)
    func resumeTrip()
    func finishTrip()
    func cancelTrip()
    func updateEstimates(_ estimates: CPTravelEstimates, for maneuver: CPManeuver)
}
```

### CPTrip

```swift
class CPTrip : NSObject {
    init(origin: MKMapItem, destination: MKMapItem, routeChoices: [CPRouteChoice])

    var origin: MKMapItem
    var destination: MKMapItem
    var routeChoices: [CPRouteChoice]
}
```

### CPRouteChoice

```swift
class CPRouteChoice : NSObject {
    init(summaryVariants: [String], additionalInformationVariants: [String], selectionSummaryVariants: [String])

    var summaryVariants: [String]
    var additionalInformationVariants: [String]
    var selectionSummaryVariants: [String]
}
```

### CPManeuver

```swift
class CPManeuver : NSObject {
    var instructionVariants: [String]
    var initialTravelEstimates: CPTravelEstimates?
    var symbolImage: UIImage?
    var junctionImage: UIImage?
    var dashboardInstructionVariants: [String]
    var dashboardJunctionImage: UIImage?
    var dashboardSymbolImage: UIImage?
    var notificationInstructionVariants: [String]
    var notificationSymbolImage: UIImage?
}
```

### CPTravelEstimates

```swift
class CPTravelEstimates : NSObject {
    init(distanceRemaining: Measurement<UnitLength>, timeRemaining: TimeInterval)

    var distanceRemaining: Measurement<UnitLength>
    var timeRemaining: TimeInterval
}
```

## Buttons

### CPBarButton

```swift
class CPBarButton : NSObject {
    init(title: String, handler: CPBarButtonHandler?)
    init(image: UIImage, handler: CPBarButtonHandler?)

    var title: String?
    var image: UIImage?
    var isEnabled: Bool
    var buttonStyle: CPBarButtonStyle
}
```

### CPMapButton

```swift
class CPMapButton : NSObject {
    init(handler: CPMapButtonHandler?)

    var image: UIImage?
    var focusedImage: UIImage?
    var isEnabled: Bool
    var isHidden: Bool
}
```

### CPTextButton

```swift
class CPTextButton : NSObject {
    init(title: String, textStyle: CPTextButtonStyle, handler: CPTextButtonHandler?)

    var title: String
    var textStyle: CPTextButtonStyle
}

enum CPTextButtonStyle {
    case normal
    case cancel
    case confirm
}
```

## Constants and Enums

### CPContentStyle

```swift
enum CPContentStyle {
    case light
    case dark
}
```

### CPTripPauseReason

```swift
enum CPTripPauseReason {
    case arrivalAtDestination
    case loading
    case locating
    case rerouting
    case proceedToRoute
}
```

### CPLimitableUserInterface

```swift
protocol CPLimitableUserInterface {
    var contentLimitingLevel: CPContentLimitingLevel { get }
}

enum CPContentLimitingLevel {
    case notLimited
    case limited
}
```

## Best Practices

1. **Check availability** before using CarPlay APIs
2. **Handle all delegate methods** for robust behavior
3. **Use completion handlers** to track template transitions
4. **Respect content limits** for driver safety
5. **Test on actual hardware** in addition to simulator
