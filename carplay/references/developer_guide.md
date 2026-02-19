# Developer Guide

Comprehensive guide for building CarPlay apps, covering all app categories, navigation implementation, testing configurations, and publishing requirements. Based on the CarPlay Developer Guide (February 2026).


---

# CarPlay App Categories

CarPlay supports ten app categories. Each requires a specific entitlement from Apple and has defined template and interaction constraints.

## Audio Apps

- **Entitlement:** `com.apple.developer.carplay-audio`
- **Minimum iOS:** 12.0
- **Template Depth Limit:** 5
- **Requirements:** Must use `MPNowPlayingInfoCenter` and `MPRemoteCommandCenter`. Root template must be `CPTabBarTemplate` (max 4 tabs) or `CPListTemplate`. Audio output is mandatory.
- **Supported Templates:** List, Tab Bar, Grid, Alert, Action Sheet, Now Playing, Search

## Communication Apps

- **Entitlement:** `com.apple.developer.carplay-communication`
- **Minimum iOS:** 12.0
- **Template Depth Limit:** 5
- **Requirements:** Must integrate with CallKit and SiriKit. Message list uses `CPMessageListItem`. VoIP calls must register with `CXProvider`.
- **Supported Templates:** List, Tab Bar, Grid, Contact, Alert, Action Sheet, Voice Control, Search

## Navigation Apps

- **Entitlement:** `com.apple.developer.carplay-maps`
- **Minimum iOS:** 12.0
- **Template Depth Limit:** 5
- **Requirements:** Must draw map content using `CPMapTemplate`. Must provide real-time turn-by-turn guidance with `CPNavigationSession`. Optionally supports Dashboard (iOS 13.4+) and Instrument Cluster (iOS 15.4+) scenes.
- **Supported Templates:** Map, List, Tab Bar, Grid, Search, Voice Control, Alert, Action Sheet, Point of Interest, Information

## Parking Apps

- **Entitlement:** `com.apple.developer.carplay-parking`
- **Minimum iOS:** 14.0
- **Template Depth Limit:** 5
- **Requirements:** Help users find, reserve, or pay for parking. Must provide location-relevant results.
- **Supported Templates:** List, Tab Bar, Grid, Alert, Action Sheet, Information, Point of Interest, Search

## EV Charging Apps

- **Entitlement:** `com.apple.developer.carplay-charging`
- **Minimum iOS:** 14.0
- **Template Depth Limit:** 5
- **Requirements:** Help users locate and manage EV charging stations. Must provide station availability status.
- **Supported Templates:** List, Tab Bar, Grid, Alert, Action Sheet, Information, Point of Interest, Search

## Quick Food Ordering Apps

- **Entitlement:** `com.apple.developer.carplay-quick-ordering`
- **Minimum iOS:** 14.0
- **Template Depth Limit:** 3
- **Requirements:** Streamlined food/drink ordering with pickup. Keep menus short and pre-populate favorites or recent orders where possible. Limit browsing depth.
- **Supported Templates:** List, Tab Bar, Grid, Alert, Action Sheet, Information, Search

## Fueling Apps

- **Entitlement:** `com.apple.developer.carplay-fueling`
- **Minimum iOS:** 16.0
- **Template Depth Limit:** 3
- **Requirements:** Help users locate gas stations, start/stop fuel pumps, and pay for fuel. Must provide station locations.
- **Supported Templates:** List, Tab Bar, Grid, Alert, Action Sheet, Information, Point of Interest, Search

## Driving Task Apps

- **Entitlement:** `com.apple.developer.carplay-driving-task`
- **Minimum iOS:** 16.0
- **Template Depth Limit:** 3
- **Requirements:** Assist with tasks done while driving (road conditions, tolls, driving accessories). Must not duplicate navigation functionality.
- **Supported Templates:** List, Tab Bar, Grid, Alert, Action Sheet, Information, Point of Interest, Search

## Public Safety Apps

- **Entitlement:** `com.apple.developer.carplay-public-safety`
- **Minimum iOS:** 14.0
- **Template Depth Limit:** 3
- **Requirements:** Provide real-time public safety information such as road hazards, speed cameras, or emergency alerts.
- **Supported Templates:** List, Tab Bar, Grid, Alert, Action Sheet, Information, Point of Interest, Search

## Voice-Based Conversational Apps (iOS 26.4+)

- **Entitlement:** `com.apple.developer.carplay-voice-based-conversation`
- **Minimum iOS:** 26.4
- **Template Depth Limit:** 3
- **Requirements:** Primarily voice-driven interaction (AI assistants, voice-based search). Must use `CPVoiceControlTemplate` as the primary interface. Action buttons and nav bar buttons available for supplemental controls. Minimal visual UI — the driver interacts through speech.
- **Supported Templates:** Voice Control, List, Alert, Action Sheet


---

# Build a CarPlay App

## Scene Manifest

Configure your app's `Info.plist` with the CarPlay scene configuration:

```xml
<key>UIApplicationSceneManifest</key>
<dict>
    <key>UISceneConfigurations</key>
    <dict>
        <key>CPTemplateApplicationSceneSessionRoleApplication</key>
        <array>
            <dict>
                <key>UISceneClassName</key>
                <string>CPTemplateApplicationScene</string>
                <key>UISceneConfigurationName</key>
                <string>CarPlay</string>
                <key>UISceneDelegateClassName</key>
                <string>$(PRODUCT_MODULE_NAME).CarPlaySceneDelegate</string>
            </dict>
        </array>
    </dict>
</dict>
```

## Startup Code

```swift
import CarPlay

class CarPlaySceneDelegate: UIResponder, CPTemplateApplicationSceneDelegate {
    var interfaceController: CPInterfaceController?

    func templateApplicationScene(
        _ templateApplicationScene: CPTemplateApplicationScene,
        didConnect interfaceController: CPInterfaceController
    ) {
        self.interfaceController = interfaceController

        let items = recentItems().map { item in
            let listItem = CPListItem(text: item.title, detailText: item.subtitle)
            listItem.handler = { _, completion in
                self.select(item)
                completion()
            }
            return listItem
        }

        let section = CPListSection(items: items)
        let listTemplate = CPListTemplate(title: "My App", sections: [section])
        interfaceController.setRootTemplate(listTemplate, animated: false)
    }

    func templateApplicationScene(
        _ templateApplicationScene: CPTemplateApplicationScene,
        didDisconnectInterfaceController interfaceController: CPInterfaceController
    ) {
        self.interfaceController = nil
    }
}
```

## Now Playing Integration

Audio apps must configure `MPNowPlayingInfoCenter` and `MPRemoteCommandCenter`:

```swift
import MediaPlayer

func configureNowPlaying(title: String, artist: String, artwork: UIImage) {
    var info = [String: Any]()
    info[MPMediaItemPropertyTitle] = title
    info[MPMediaItemPropertyArtist] = artist
    info[MPMediaItemPropertyArtwork] = MPMediaItemArtwork(boundsSize: artwork.size) { _ in artwork }
    info[MPNowPlayingInfoPropertyElapsedPlaybackTime] = player.currentTime
    info[MPMediaItemPropertyPlaybackDuration] = player.duration
    MPNowPlayingInfoCenter.default().nowPlayingInfo = info
}
```


---

# Build a CarPlay Navigation App

Navigation apps require additional scene configurations for Dashboard and Instrument Cluster.

## Scene Manifest (Navigation)

```xml
<key>UIApplicationSceneManifest</key>
<dict>
    <key>UISceneConfigurations</key>
    <dict>
        <key>CPTemplateApplicationSceneSessionRoleApplication</key>
        <array>
            <dict>
                <key>UISceneClassName</key>
                <string>CPTemplateApplicationScene</string>
                <key>UISceneConfigurationName</key>
                <string>CarPlay</string>
                <key>UISceneDelegateClassName</key>
                <string>$(PRODUCT_MODULE_NAME).CarPlaySceneDelegate</string>
            </dict>
        </array>
        <key>CPTemplateApplicationDashboardSceneSessionRoleApplication</key>
        <array>
            <dict>
                <key>UISceneClassName</key>
                <string>CPTemplateApplicationDashboardScene</string>
                <key>UISceneConfigurationName</key>
                <string>CarPlay-Dashboard</string>
                <key>UISceneDelegateClassName</key>
                <string>$(PRODUCT_MODULE_NAME).DashboardSceneDelegate</string>
            </dict>
        </array>
        <key>CPTemplateApplicationInstrumentClusterSceneSessionRoleApplication</key>
        <array>
            <dict>
                <key>UISceneClassName</key>
                <string>CPTemplateApplicationInstrumentClusterScene</string>
                <key>UISceneConfigurationName</key>
                <string>CarPlay-InstrumentCluster</string>
                <key>UISceneDelegateClassName</key>
                <string>$(PRODUCT_MODULE_NAME).InstrumentClusterSceneDelegate</string>
            </dict>
        </array>
    </dict>
</dict>
```

## Map Template and Base View

Navigation apps draw their own map content in a `UIView` provided by the CarPlay window:

```swift
func templateApplicationScene(
    _ templateApplicationScene: CPTemplateApplicationScene,
    didConnect interfaceController: CPInterfaceController,
    to window: CPWindow
) {
    self.interfaceController = interfaceController

    let mapViewController = MapViewController()
    window.rootViewController = mapViewController

    let mapTemplate = CPMapTemplate()
    mapTemplate.mapDelegate = self
    interfaceController.setRootTemplate(mapTemplate, animated: false)
}
```

## Route Guidance Lifecycle

1. Show trip previews with `showTripPreviews(_:textConfiguration:)`
2. User selects a route — delegate receives `mapTemplate(_:startedTrip:using:)`
3. Start navigation session: `mapTemplate.startNavigationSession(for:)`
4. Provide maneuvers via `navigationSession.upcomingManeuvers`
5. Update travel estimates with `navigationSession.updateEstimates(_:for:)`
6. Finish with `navigationSession.finishTrip()` or cancel with `navigationSession.cancelTrip()`

## Maneuver State Lifecycle

Maneuver states cycle through:

```
continue → initial → prepare → execute → continue
```

- **continue** — Default state; no imminent maneuver
- **initial** — Maneuver upcoming (far distance)
- **prepare** — Approaching the maneuver (medium distance)
- **execute** — Perform the maneuver now (at the turn)

Set via `navigationSession.maneuverState`.

## CPManeuverType Values

The `maneuverType` property on `CPManeuver` accepts the following values:

| Maneuver Type | Description |
|---|---|
| `.noTurn` | Continue straight |
| `.leftTurn` | Turn left |
| `.rightTurn` | Turn right |
| `.straightAhead` | Proceed straight ahead |
| `.uTurn` | Make a U-turn |
| `.followRoad` | Follow the current road |
| `.enterRoundabout` | Enter a roundabout |
| `.exitRoundabout` | Exit a roundabout |
| `.offRamp` | Take an off-ramp |
| `.onRamp` | Take an on-ramp |
| `.arriveEndOfRoute` | Arrive at the destination |
| `.startRoute` | Begin the route |
| `.arriveAtDestination` | Final arrival at destination |
| `.keepLeft` | Keep left |
| `.keepRight` | Keep right |
| `.enter` | Enter (e.g., highway) |
| `.exit` | Exit (e.g., highway) |
| `.merge` | Merge into traffic |
| `.toManeuverSharpLeft` | Sharp left turn |
| `.toManeuverSharpRight` | Sharp right turn |
| `.toManeuverSlightLeft` | Slight left turn |
| `.toManeuverSlightRight` | Slight right turn |
| `.changeRoad` | Road name change |
| `.changeHighway` | Highway change |
| `.changeHighwayLeft` | Change highway (take left) |
| `.changeHighwayRight` | Change highway (take right) |
| `.turnAtEnd` | Turn at the end of the road |
| `.arrivedAtDestinationLeft` | Destination on the left |
| `.arrivedAtDestinationRight` | Destination on the right |
| `.panRoute` | Pan route overview |
| `.trafficJamLeft` | Traffic jam ahead, keep left |
| `.trafficJamRight` | Traffic jam ahead, keep right |
| `.ferryBoat` | Board a ferry |
| `.pedestrian` | Pedestrian path |
| `.tollGate` | Pass through a toll gate |
| `.serviceArea` | Service area available |
| `.chargingStation` | Charging station available |
| `.parking` | Parking available |
| `.restArea` | Rest area available |

## CPJunctionType Values

| Junction Type | Description |
|---|---|
| `.intersection` | Standard intersection |
| `.roundabout` | Roundabout junction |

## CPTrafficSide Values

| Traffic Side | Description |
|---|---|
| `.right` | Traffic drives on the right side of the road |
| `.left` | Traffic drives on the left side of the road |

## Lane Guidance

Provide lane-level guidance using `CPLane` and `CPLaneGuidance`:

```swift
let lane = CPLane()
lane.primaryAngle = 0  // straight
lane.secondaryAngles = [NSNumber(value: Float.pi / 2)]  // also goes right
lane.status = .preferred

let laneGuidance = CPLaneGuidance()
laneGuidance.lanes = [lane]
laneGuidance.instructionVariants = ["Use the left lane"]

maneuver.linkedLaneGuidance = laneGuidance
```

## Voice Prompts

Navigation apps provide audio guidance via `AVAudioSession`:

```swift
import AVFoundation

func speakManeuver(_ text: String, promptStyle: CPManeuverDisplayStyle) {
    // Configure audio session for navigation prompts
    let session = AVAudioSession.sharedInstance()
    try? session.setCategory(.playback, mode: .voicePrompt, options: [.duckOthers, .interruptSpokenAudioAndMixWithOthers])
    try? session.setActive(true)

    let utterance = AVSpeechUtterance(string: text)
    synthesizer.speak(utterance)
}
```

Prompt styles control how much speech guidance to provide:
- **None** — No voice prompt
- **Short** — Abbreviated instruction (e.g., "Turn right")
- **Normal** — Full instruction (e.g., "In 500 meters, turn right onto Main Street")

## Multitouch Navigation (iOS 26+)

iOS 26 enables multitouch interaction on the CarPlay map template. Users can pinch to zoom and use two-finger gestures. The system notifies your delegate:

```swift
func mapTemplate(_ mapTemplate: CPMapTemplate,
                 panWith direction: CPMapTemplate.PanDirection) {
    // Handle directional pan
}
```

## Re-route (iOS 17.4+)

When the driver deviates from the planned route, resume with:

```swift
navigationSession.resumeTrip(for: trip, with: updatedRouteChoice)
```

## Second Map in Dashboard / Instrument Cluster

Navigation apps can display a secondary map in the Dashboard and Instrument Cluster scenes. Implement the respective scene delegates and draw map content in the provided `UIWindow`.

## Navigation Metadata for HUD (iOS 17.4+)

Vehicles with heads-up displays or instrument clusters can receive metadata from your navigation session. Implement the metadata delegate:

```swift
func mapTemplateShouldProvideNavigationMetadata(
    _ mapTemplate: CPMapTemplate
) -> Bool {
    return true
}
```

When returning `true`, the system forwards maneuver data, lane guidance, and travel estimates to the vehicle's HUD and instrument cluster.


---

# Test Configurations

## CarPlay Simulator (Xcode)

Test CarPlay in the iOS Simulator:
1. Build and run on an iOS Simulator
2. In the Simulator menu: **I/O > External Displays > CarPlay**

## CarPlay Simulator (Standalone Mac App)

Apple provides a standalone CarPlay Simulator as part of **Additional Tools for Xcode** (download from developer.apple.com). This enables testing on a physical device without a CarPlay-compatible vehicle.

## Enable Extra Options

```bash
defaults write com.apple.iphonesimulator CarPlayExtraOptions -bool YES
```

This enables additional configuration options in the CarPlay Simulator, including screen size selection and cluster display settings.

## Navigation Screen Sizes

The following screen configurations are used for testing navigation apps:

| Screen Size | Scale | Description |
|---|---|---|
| 748 × 456 | @2x | Compact width |
| 800 × 480 | @2x | Standard width |
| 828 × 1792 | @2x | Tall display |
| 900 × 600 | @2x | Wide display |
| 960 × 540 | @2x | 16:9 standard |
| 1024 × 600 | @2x | Wide format |
| 1080 × 600 | @2x | Extra wide |
| 1184 × 736 | @2x | HD wide |
| 1280 × 720 | @2x | 720p |
| 1600 × 828 | @2x | Ultra wide |
| 900 × 1200 | @3x | Portrait tall (@3x) |

## Instrument Cluster Configurations

Test instrument cluster rendering at multiple sizes. The simulator provides cluster display options when `CarPlayExtraOptions` is enabled.


---

# Template Enhancements

## List Template (iOS 26)

iOS 26 introduces element styles, message items, and pinned elements for `CPListTemplate`:

- **Element Styles:** `CPListImageRowItem` gains an `elementStyle` property with 5 visual styles for customizing image grid appearance.
- **Message Item:** `CPMessageListItem` can now be used within standard list templates alongside other item types.
- **Pinned Elements:** List sections can pin items to the top or bottom for persistent visibility during scrolling.

## Voice Control (iOS 26.4)

`CPVoiceControlTemplate` gains two new capabilities for voice-based conversational apps:

- **Action Buttons:** Add interactive buttons below the voice visualization. Use for quick-action commands (e.g., "Play Music", "Read Messages").
- **Navigation Bar Buttons:** Add leading/trailing bar buttons to the voice control template's navigation bar for additional controls.

## Point of Interest (iOS 16)

- **`selectedPinImage`:** Customize the pin image displayed when a point of interest is selected on the map.

## Information Template (iOS 16)

- **Leading/Trailing Navigation Bar Buttons:** `CPInformationTemplate` supports `CPBarButton` items in the navigation bar for additional actions.

## Now Playing — Sports Mode

Sports mode (`CPNowPlayingModeSports`) supports content items for detailed game information:
- Team logos (image or initials)
- Event scores and standings
- Game clock (countdown timer)
- Event status text array (e.g., quarter, down, field position)
- Possession indicators
- Background artwork


---

# Publishing Checklist

Before submitting your CarPlay app to App Store Review:

1. **Entitlement approved** — Confirm you have received the correct CarPlay entitlement from Apple for your app category
2. **Entitlement in project** — Add the entitlement to your Xcode project's entitlements file
3. **Scene delegate implemented** — `CPTemplateApplicationSceneDelegate` is properly configured
4. **Info.plist configured** — Scene manifest includes the correct `CPTemplateApplicationSceneSessionRoleApplication` configuration
5. **Template depth limits** — Verify your app does not exceed the template depth limit for its category (3 or 5)
6. **Item count limits** — Respect maximum item counts for all templates (lists, grids, tabs)
7. **Image assets sized correctly** — All images match the recommended sizes for CarPlay templates (see Assets Size Guide in SKILL.md)
8. **Day/night mode tested** — App renders correctly in both light and dark appearance
9. **Multiple screen sizes tested** — Test across at least 3 different CarPlay display sizes in the simulator
10. **No distracting content** — No video playback, complex animations, advertising, or content requiring extended reading while driving


---

# Deprecated Entitlements

| Old Entitlement Key | Replacement | Notes |
|---|---|---|
| `com.apple.developer.carplay-quick-food` | `com.apple.developer.carplay-quick-ordering` | Renamed to reflect broader ordering scope (food and drinks). Update existing provisioning profiles. |
