# CarPlay Development Skill

## Description
CarPlay app development: Building iOS apps with CarPlay integration for automotive experiences including navigation, audio, communication, and utility apps.

## Platforms
- iOS 14.0+
- iOS 17.0+ (latest CarPlay features)

## When to Use
Use this skill when:
- Building CarPlay-enabled iOS applications
- Implementing CPTemplateApplicationScene lifecycle
- Working with CarPlay templates (CPListTemplate, CPGridTemplate, etc.)
- Creating navigation apps with CPNavigationSession
- Building audio/media playback apps
- Implementing communication features (messaging, calling)
- Developing EV charging, fueling, or food ordering apps
- Designing driver-safe interfaces

## Key Components

### App Architecture
- `CPTemplateApplicationSceneDelegate` - CarPlay scene lifecycle
- `CPInterfaceController` - Template management and navigation
- `CPWindow` - CarPlay display window

### Templates
- `CPTabBarTemplate` - Tab-based navigation
- `CPListTemplate` - Scrollable lists
- `CPGridTemplate` - Grid layouts
- `CPInformationTemplate` - Information display
- `CPPointOfInterestTemplate` - Location browsing
- `CPMapTemplate` - Map-based navigation
- `CPNowPlayingTemplate` - Media playback controls
- `CPActionSheetTemplate` - Action sheets
- `CPAlertTemplate` - Alerts and confirmations
- `CPVoiceControlTemplate` - Voice input

### Navigation
- `CPNavigationSession` - Active navigation management
- `CPTrip` - Route information
- `CPManeuver` - Turn-by-turn instructions
- `CPRouteChoice` - Route alternatives
- `CPTravelEstimates` - ETA and distance

### Audio & Media
- `CPNowPlayingTemplate` - Now playing interface
- `CPListImageRowItem` - Album art rows
- `CPContentStyle` - Visual styling

### Communication
- `CPMessageListItem` - Message display
- `CPContact` - Contact information
- `CPCallController` - Call management

### Points of Interest
- `CPPointOfInterest` - Location data
- `CPPointOfInterestTemplate` - POI browsing

## Best Practices
- Always check CarPlay availability before presenting templates
- Use appropriate template types for your app category
- Follow Apple Human Interface Guidelines for CarPlay
- Minimize driver distraction with simple, glanceable interfaces
- Support both light and dark appearances
- Handle connection/disconnection gracefully
- Use Siri for voice-first interactions
- Test thoroughly in CarPlay Simulator

## Code Examples

### Basic CarPlay Scene Setup
```swift
import CarPlay

class CarPlaySceneDelegate: UIResponder, CPTemplateApplicationSceneDelegate {
    var interfaceController: CPInterfaceController?

    func templateApplicationScene(
        _ templateApplicationScene: CPTemplateApplicationScene,
        didConnect interfaceController: CPInterfaceController
    ) {
        self.interfaceController = interfaceController

        let item = CPListItem(text: "Item", detailText: "Details")
        let section = CPListSection(items: [item])
        let listTemplate = CPListTemplate(title: "Home", sections: [section])

        interfaceController.setRootTemplate(listTemplate, animated: true)
    }

    func templateApplicationScene(
        _ templateApplicationScene: CPTemplateApplicationScene,
        didDisconnect interfaceController: CPInterfaceController
    ) {
        self.interfaceController = nil
    }
}
```

### Navigation App Template
```swift
let mapTemplate = CPMapTemplate()
mapTemplate.guidanceBackgroundColor = .systemBlue
mapTemplate.mapDelegate = self

// Start navigation
let trip = CPTrip(origin: originItem, destination: destItem, routeChoices: routes)
mapTemplate.startNavigationSession(for: trip)
```

### Audio App Template
```swift
let nowPlayingTemplate = CPNowPlayingTemplate.shared
nowPlayingTemplate.updateNowPlayingButtons([
    CPNowPlayingShuffleButton(handler: { _ in /* shuffle */ }),
    CPNowPlayingRepeatButton(handler: { _ in /* repeat */ })
])
interfaceController.pushTemplate(nowPlayingTemplate, animated: true)
```

## References
- [references/getting_started.md](references/getting_started.md) - Setup and configuration
- [references/templates.md](references/templates.md) - Template types guide
- [references/navigation.md](references/navigation.md) - Navigation implementation
- [references/audio.md](references/audio.md) - Audio app development
- [references/communication.md](references/communication.md) - Messaging and calls
- [references/poi.md](references/poi.md) - Points of interest
- [references/ev_charging.md](references/ev_charging.md) - EV charging apps
- [references/api_reference.md](references/api_reference.md) - Full API reference
- [references/best_practices.md](references/best_practices.md) - Guidelines and tips
