# Platform-Specific Widget Guide

## Table of Contents
1. [Platform Feature Matrix](#platform-feature-matrix)
2. [iOS / iPadOS](#ios--ipados)
3. [watchOS](#watchos)
4. [macOS](#macos)
5. [visionOS](#visionos)
6. [CarPlay](#carplay)

---

## Platform Feature Matrix

| Feature | iPhone | iPad | Apple Watch | Mac | Vision Pro |
|---------|--------|------|-------------|-----|------------|
| System Small | ✅ | ✅ | ❌ | ✅ | ✅ |
| System Medium | ✅ | ✅ | ❌ | ✅ | ✅ |
| System Large | ✅ | ✅ | ❌ | ✅ | ✅ |
| System Extra Large | ❌ | ✅ | ❌ | ✅ | ✅ |
| Extra Large Portrait | ❌ | ❌ | ❌ | ❌ | ✅ |
| Accessory Circular | ✅ | ✅ | ✅ | ❌ | ❌ |
| Accessory Rectangular | ✅ | ✅ | ✅ | ❌ | ❌ |
| Accessory Inline | ✅ | ✅ | ✅ | ❌ | ❌ |
| Accessory Corner | ❌ | ❌ | ✅ | ❌ | ❌ |
| Live Activities | ✅ | ✅ | Mirror | Mirror | ❌ |
| Controls | ✅ | ✅ | ✅ | ✅ | ❌ |

---

## iOS / iPadOS

### Locations
- **Home Screen**: System widgets (small, medium, large, extra large on iPad)
- **Today View**: System widgets
- **Lock Screen**: Accessory widgets (circular, rectangular, inline)
- **StandBy** (iPhone): System widgets scaled up, horizontal orientation

### StandBy Mode
```swift
@Environment(\.isLuminanceReduced) var isLuminanceReduced

var body: some View {
    VStack {
        // Content
    }
    .foregroundStyle(isLuminanceReduced ? .red : .primary)
}
```

**StandBy considerations**:
- Widget scales up significantly
- Black background (remove custom backgrounds)
- Low-light: red monochrome tint
- Optimize for viewing from distance

### Lock Screen Widgets
```swift
struct MyWidget: Widget {
    var body: some WidgetConfiguration {
        StaticConfiguration(kind: "lockscreen", provider: Provider()) { entry in
            LockScreenView(entry: entry)
        }
        .supportedFamilies([.accessoryCircular, .accessoryRectangular, .accessoryInline])
    }
}
```

### Conditional Platform Code
```swift
#if os(iOS)
.supportedFamilies([.systemSmall, .systemMedium, .accessoryCircular])
#endif
```

---

## watchOS

### Widget Extension Requirements
- Create separate watchOS widget extension target
- Use `accessory` families for complications
- Widgets appear in Smart Stack

### Watch Complications
```swift
struct ComplicationWidget: Widget {
    var body: some WidgetConfiguration {
        StaticConfiguration(kind: "watchComplication", provider: Provider()) { entry in
            ComplicationView(entry: entry)
        }
        .supportedFamilies([
            .accessoryCircular,
            .accessoryRectangular,
            .accessoryInline,
            .accessoryCorner  // watchOS only
        ])
    }
}
```

### Accessory Corner (watchOS only)
```swift
struct CornerView: View {
    var body: some View {
        ZStack {
            AccessoryWidgetBackground()
            Image(systemName: "star.fill")
        }
        .widgetLabel {
            Text("Label")
        }
    }
}
```

### Smart Stack Relevance
```swift
struct Entry: TimelineEntry {
    let date: Date
    
    var relevance: TimelineEntryRelevance? {
        // Score 0-1, higher = more relevant
        TimelineEntryRelevance(score: 0.8, duration: 3600)
    }
}
```

### RelevanceKit (watchOS)
```swift
import RelevanceKit

// Provide context clues for Smart Stack
func relevantContext() -> some RelevantContext {
    RelevantIntentContext(intent: MyIntent())
}
```

---

## macOS

### Locations
- Desktop
- Notification Center

### Mac-Specific Considerations
```swift
#if os(macOS)
struct MacWidgetView: View {
    @Environment(\.colorScheme) var colorScheme
    
    var body: some View {
        // macOS uses vibrant rendering on desktop
        VStack {
            Content()
        }
        .background(.regularMaterial)
    }
}
#endif
```

### iPhone Widgets on Mac
- iOS widgets can appear on Mac via Continuity
- Controlled by `NSFileProtectionComplete` entitlement
- May be scaled differently

---

## visionOS

### Spatial Widget Design
```swift
struct VisionOSWidget: Widget {
    var body: some WidgetConfiguration {
        StaticConfiguration(kind: "spatial", provider: Provider()) { entry in
            SpatialWidgetView(entry: entry)
        }
        .supportedFamilies([
            .systemSmall,
            .systemMedium,
            .systemLarge,
            .systemExtraLarge
        ])
    }
}
```

### Distance Thresholds
```swift
@Environment(\.widgetContentMargins) var margins

var body: some View {
    // Adapt layout based on viewing distance
    // simplified: viewed from far away
    // default: viewed nearby
}
```

### Mounting Styles
- **Elevated**: Default, sits on surface with shadow
- **Recessed**: Content appears set into surface (vertical only)

### Treatment Styles
- **Paper**: Print-like, responds to ambient lighting
- **Glass**: Layered, foreground stays bright

```swift
// In widget configuration
.contentMarginsDisabled()
.containerBackground(for: .widget) {
    // Custom background
}
```

### visionOS Best Practices
- Support both simplified and default thresholds
- Use high-resolution assets
- Test with system color palettes
- Consider real-world placement context

---

## CarPlay

### CarPlay Widget Support
- System small widgets only
- Full-color rendering with background removed
- Scaled up for in-car viewing

```swift
struct CarPlayWidget: Widget {
    var body: some WidgetConfiguration {
        StaticConfiguration(kind: "carplay", provider: Provider()) { entry in
            CarPlayView(entry: entry)
        }
        .supportedFamilies([.systemSmall])
        // CarPlay automatically supported for small widgets
    }
}
```

### CarPlay Design
- Large, clear typography
- High contrast
- Minimal interaction (tap to launch app)
- No background (removed automatically)

---

## Cross-Platform Widget Bundle

```swift
@main
struct MyWidgets: WidgetBundle {
    var body: some Widget {
        // iOS/iPadOS widgets
        HomeScreenWidget()
        LockScreenWidget()
        
        #if os(watchOS)
        WatchComplicationWidget()
        #endif
        
        #if os(iOS)
        LiveActivityWidget()
        #endif
    }
}
```

---

## Platform Detection

```swift
struct AdaptiveWidgetView: View {
    @Environment(\.widgetFamily) var family
    
    var body: some View {
        #if os(watchOS)
        WatchView(family: family)
        #elseif os(iOS)
        if family.isAccessory {
            AccessoryView()
        } else {
            SystemView()
        }
        #elseif os(macOS)
        MacView()
        #elseif os(visionOS)
        SpatialView()
        #endif
    }
}

extension WidgetFamily {
    var isAccessory: Bool {
        switch self {
        case .accessoryCircular, .accessoryRectangular, .accessoryInline, .accessoryCorner:
            return true
        default:
            return false
        }
    }
}
```
