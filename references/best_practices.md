# CarPlay Best Practices

Design and development guidelines for creating safe, effective CarPlay applications.

## Driver Safety

### Minimize Distraction

```swift
// Good: Simple, glanceable information
let item = CPListItem(text: "Gas Station", detailText: "0.5 mi")

// Bad: Too much information
let item = CPListItem(
    text: "Shell Gas Station #1234",
    detailText: "0.5 miles away, Regular $3.45/gal, Premium $3.89/gal, Open 24 hours"
)
```

### Limit Interaction Depth

```swift
// Recommended: Maximum 3 levels deep
// Root -> Category -> Detail

// Avoid: Deep navigation hierarchies
// Root -> Category -> Subcategory -> Item -> Detail -> Action -> Confirmation
```

### Use Voice When Possible

```swift
// Integrate with Siri for hands-free operation
class IntentHandler: INExtension, INPlayMediaIntentHandling {
    func handle(intent: INPlayMediaIntent, completion: @escaping (INPlayMediaIntentResponse) -> Void) {
        // Handle voice commands
    }
}
```

## Template Usage

### Choose the Right Template

| Use Case | Template |
|----------|----------|
| Browse content | CPListTemplate |
| Multiple sections | CPTabBarTemplate |
| Quick actions | CPGridTemplate |
| Show information | CPInformationTemplate |
| Location browsing | CPPointOfInterestTemplate |
| Navigation | CPMapTemplate |
| Media playback | CPNowPlayingTemplate |
| Confirmations | CPAlertTemplate |

### Handle Empty States

```swift
let template = CPListTemplate(title: "Favorites", sections: [])
template.emptyViewTitleVariants = ["No Favorites"]
template.emptyViewSubtitleVariants = ["Add favorites from the app"]
```

### Update Content Dynamically

```swift
// Update sections without creating new template
func updatePlaylist(with songs: [Song]) {
    let items = songs.map { song in
        CPListItem(text: song.title, detailText: song.artist)
    }
    let section = CPListSection(items: items)
    listTemplate.updateSections([section])
}
```

## Performance

### Optimize Image Loading

```swift
// Pre-size images for CarPlay
func resizeForCarPlay(_ image: UIImage) -> UIImage {
    let maxSize = CGSize(width: 44, height: 44)
    let renderer = UIGraphicsImageRenderer(size: maxSize)
    return renderer.image { _ in
        image.draw(in: CGRect(origin: .zero, size: maxSize))
    }
}

// Use SF Symbols when possible
let icon = UIImage(systemName: "music.note")
```

### Cache Frequently Used Data

```swift
class CarPlayDataCache {
    static let shared = CarPlayDataCache()
    private var cache = NSCache<NSString, AnyObject>()

    func cachedImage(for key: String) -> UIImage? {
        return cache.object(forKey: key as NSString) as? UIImage
    }

    func cacheImage(_ image: UIImage, for key: String) {
        cache.setObject(image, forKey: key as NSString)
    }
}
```

### Load Content Asynchronously

```swift
func loadContent() {
    // Show loading state
    let loadingSection = CPListSection(items: [
        CPListItem(text: "Loading...", detailText: nil)
    ])
    listTemplate.updateSections([loadingSection])

    // Load in background
    DispatchQueue.global().async {
        let content = self.fetchContent()

        DispatchQueue.main.async {
            self.updateUI(with: content)
        }
    }
}
```

## Connection Handling

### Handle Connect/Disconnect Gracefully

```swift
class CarPlaySceneDelegate: UIResponder, CPTemplateApplicationSceneDelegate {
    private var isCarPlayConnected = false

    func templateApplicationScene(
        _ templateApplicationScene: CPTemplateApplicationScene,
        didConnect interfaceController: CPInterfaceController
    ) {
        isCarPlayConnected = true
        NotificationCenter.default.post(name: .carPlayConnected, object: nil)

        // Restore previous state if available
        restoreState()
    }

    func templateApplicationScene(
        _ templateApplicationScene: CPTemplateApplicationScene,
        didDisconnect interfaceController: CPInterfaceController
    ) {
        isCarPlayConnected = false
        NotificationCenter.default.post(name: .carPlayDisconnected, object: nil)

        // Save state for later
        saveState()
    }
}
```

### Coordinate with iPhone App

```swift
// Share state between iPhone and CarPlay
class SharedState: ObservableObject {
    static let shared = SharedState()

    @Published var currentTrack: Track?
    @Published var isPlaying: Bool = false

    func play(_ track: Track) {
        currentTrack = track
        isPlaying = true
        // Notify both interfaces
    }
}
```

## Accessibility

### Support VoiceOver

```swift
// Provide meaningful accessibility labels
let item = CPListItem(text: "Now Playing", detailText: "Song Title")
item.accessibilityLabel = "Now Playing: Song Title by Artist Name"
item.accessibilityHint = "Double tap to view playback controls"
```

### Support Dynamic Type

```swift
// Use system fonts that respect accessibility settings
// CarPlay handles this automatically for template content
```

## Testing

### Use CarPlay Simulator

1. Open Xcode
2. Window > Devices and Simulators
3. Select simulator > Features > CarPlay

### Test Scenarios

```swift
// Test checklist:
// - [ ] App launches correctly in CarPlay
// - [ ] All templates display properly
// - [ ] Navigation works at all levels
// - [ ] Content updates reflect in real-time
// - [ ] Handle connection/disconnection
// - [ ] Audio continues when switching apps
// - [ ] Siri commands work correctly
// - [ ] Light and dark mode both work
// - [ ] Performance is smooth
// - [ ] Memory usage is reasonable
```

### Test with Different Display Sizes

CarPlay displays vary in size and resolution. Test with:
- Small displays (6-7 inch)
- Medium displays (8-10 inch)
- Large displays (11+ inch)

## Common Mistakes

### Don't Block the Main Thread

```swift
// Bad
func loadContent() {
    let data = slowNetworkRequest() // Blocks UI
    updateUI(with: data)
}

// Good
func loadContent() {
    Task {
        let data = await slowNetworkRequest()
        await MainActor.run {
            updateUI(with: data)
        }
    }
}
```

### Don't Ignore Template Limits

```swift
// CarPlay enforces limits - respect them
let maxItems = 100 // Approximate limit
let items = allItems.prefix(maxItems).map { /* ... */ }
```

### Don't Forget Error Handling

```swift
func pushTemplate(_ template: CPTemplate) {
    interfaceController?.pushTemplate(template, animated: true) { success, error in
        if let error = error {
            print("Failed to push template: \(error)")
            // Handle gracefully
        }
    }
}
```

### Don't Mix Navigation Patterns

```swift
// Pick one navigation pattern and stick with it
// Either use tabs OR hierarchical navigation, not both randomly
```

## Human Interface Guidelines

Apple's CarPlay HIG emphasizes:

1. **Glanceability** - Information readable in under 2 seconds
2. **Simplicity** - Minimal options per screen
3. **Voice-first** - Prioritize Siri integration
4. **Consistency** - Follow platform conventions
5. **Responsiveness** - Immediate feedback for actions

## Resources

- [Apple CarPlay Developer Documentation](https://developer.apple.com/carplay/)
- [CarPlay Human Interface Guidelines](https://developer.apple.com/design/human-interface-guidelines/carplay)
- [WWDC CarPlay Sessions](https://developer.apple.com/videos/)
- [CarPlay Entitlement Request](https://developer.apple.com/contact/carplay/)
