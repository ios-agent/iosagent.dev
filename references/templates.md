# CarPlay Templates

CarPlay uses a template-based UI system to ensure consistent, driver-safe interfaces. All CarPlay apps must use these system-provided templates.

## Template Overview

### Base Class
All templates inherit from `CPTemplate`:

```swift
class CPTemplate : NSObject
```

### Template Stack
Templates are managed in a navigation stack via `CPInterfaceController`:

```swift
// Push a template onto the stack
interfaceController.pushTemplate(template, animated: true)

// Pop the current template
interfaceController.popTemplate(animated: true)

// Pop to root
interfaceController.popToRootTemplate(animated: true)

// Set root template
interfaceController.setRootTemplate(template, animated: true)
```

## List Templates

### CPListTemplate
The most common template for displaying scrollable lists.

```swift
let item1 = CPListItem(text: "Song 1", detailText: "Artist Name")
item1.handler = { item, completion in
    // Handle selection
    completion()
}

let item2 = CPListItem(text: "Song 2", detailText: "Artist Name")
item2.accessoryType = .disclosureIndicator

let section = CPListSection(items: [item1, item2], header: "Now Playing")

let listTemplate = CPListTemplate(title: "Music", sections: [section])
listTemplate.emptyViewTitleVariants = ["No Music"]
listTemplate.emptyViewSubtitleVariants = ["Add music to your library"]
```

### CPListItem Types
```swift
// Basic item
let basic = CPListItem(text: "Title", detailText: "Subtitle")

// With image
let withImage = CPListItem(
    text: "Title",
    detailText: "Subtitle",
    image: UIImage(systemName: "music.note")
)

// With accessory
let withAccessory = CPListItem(text: "Title", detailText: nil)
withAccessory.accessoryType = .disclosureIndicator // or .cloud

// Image row item (for album art grids)
let imageRow = CPListImageRowItem(
    text: "Recently Played",
    images: [image1, image2, image3]
)
```

## Tab Bar Template

### CPTabBarTemplate
For apps with multiple sections:

```swift
let musicTemplate = CPListTemplate(title: "Music", sections: musicSections)
musicTemplate.tabImage = UIImage(systemName: "music.note")

let podcastTemplate = CPListTemplate(title: "Podcasts", sections: podcastSections)
podcastTemplate.tabImage = UIImage(systemName: "mic")

let tabBarTemplate = CPTabBarTemplate(templates: [musicTemplate, podcastTemplate])
tabBarTemplate.delegate = self

interfaceController.setRootTemplate(tabBarTemplate, animated: true)
```

### Tab Bar Delegate
```swift
extension CarPlaySceneDelegate: CPTabBarTemplateDelegate {
    func tabBarTemplate(
        _ tabBarTemplate: CPTabBarTemplate,
        didSelect selectedTemplate: CPTemplate
    ) {
        // Handle tab selection
    }
}
```

## Grid Template

### CPGridTemplate
For displaying items in a grid layout:

```swift
let button1 = CPGridButton(
    titleVariants: ["Favorites"],
    image: UIImage(systemName: "heart.fill")!
) { button in
    // Handle tap
}

let button2 = CPGridButton(
    titleVariants: ["Recents"],
    image: UIImage(systemName: "clock")!
) { button in
    // Handle tap
}

let gridTemplate = CPGridTemplate(
    title: "Quick Access",
    gridButtons: [button1, button2]
)
```

## Information Template

### CPInformationTemplate
For displaying static information:

```swift
let items = [
    CPInformationItem(title: "Address", detail: "123 Main St"),
    CPInformationItem(title: "Phone", detail: "(555) 123-4567"),
    CPInformationItem(title: "Hours", detail: "9 AM - 5 PM")
]

let actions = [
    CPTextButton(title: "Call", textStyle: .normal) { button in
        // Handle call
    },
    CPTextButton(title: "Directions", textStyle: .normal) { button in
        // Handle directions
    }
]

let infoTemplate = CPInformationTemplate(
    title: "Store Info",
    layout: .leading,
    items: items,
    actions: actions
)
```

## Alert Templates

### CPAlertTemplate
```swift
let alertTemplate = CPAlertTemplate(
    titleVariants: ["Confirm Action"],
    actions: [
        CPAlertAction(title: "Confirm", style: .default) { action in
            // Handle confirm
        },
        CPAlertAction(title: "Cancel", style: .cancel) { action in
            // Handle cancel
        }
    ]
)

interfaceController.presentTemplate(alertTemplate, animated: true)
```

### CPActionSheetTemplate
```swift
let actionSheet = CPActionSheetTemplate(
    title: "Options",
    message: "Choose an action",
    actions: [
        CPAlertAction(title: "Share", style: .default) { _ in },
        CPAlertAction(title: "Delete", style: .destructive) { _ in },
        CPAlertAction(title: "Cancel", style: .cancel) { _ in }
    ]
)
```

## Now Playing Template

### CPNowPlayingTemplate
Singleton template for audio playback (see [Audio](audio.md) for details):

```swift
let nowPlaying = CPNowPlayingTemplate.shared
nowPlaying.isUpNextButtonEnabled = true
nowPlaying.isAlbumArtistButtonEnabled = true
```

## Map Template

### CPMapTemplate
For navigation apps (see [Navigation](navigation.md) for details):

```swift
let mapTemplate = CPMapTemplate()
mapTemplate.mapDelegate = self
mapTemplate.automaticallyHidesNavigationBar = true
```

## Point of Interest Template

### CPPointOfInterestTemplate
For location browsing (see [POI](poi.md) for details):

```swift
let poiTemplate = CPPointOfInterestTemplate(
    title: "Nearby",
    pointsOfInterest: pois,
    selectedIndex: NSNotFound
)
```

## Voice Control Template

### CPVoiceControlTemplate
For voice input states:

```swift
let voiceTemplate = CPVoiceControlTemplate(
    voiceControlStates: [
        CPVoiceControlState(
            identifier: "listening",
            titleVariants: ["Listening..."],
            image: UIImage(systemName: "mic.fill")
        ),
        CPVoiceControlState(
            identifier: "processing",
            titleVariants: ["Processing..."],
            image: UIImage(systemName: "waveform")
        )
    ]
)
```

## Template Limits

CarPlay enforces limits to ensure driver safety:

| Element | Limit |
|---------|-------|
| List sections | 5-10 (varies by template) |
| List items per section | ~100 (varies) |
| Tab bar tabs | 4-5 |
| Grid buttons | 8 |
| Template stack depth | 5 |

## Best Practices

1. **Keep it simple** - Minimize the number of items and hierarchy depth
2. **Use images wisely** - Icons should be recognizable at a glance
3. **Handle loading states** - Show appropriate empty states while loading
4. **Update dynamically** - Use `updateSections()` for live updates
5. **Support accessibility** - Ensure VoiceOver compatibility
