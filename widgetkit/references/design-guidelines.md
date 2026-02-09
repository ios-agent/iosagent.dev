# Widget Design Guidelines (HIG)

## Table of Contents
1. [Core Principles](#core-principles)
2. [Content Strategy](#content-strategy)
3. [Layout & Margins](#layout--margins)
4. [Typography](#typography)
5. [Color & Imagery](#color--imagery)
6. [Rendering Modes](#rendering-modes)
7. [Interactivity Guidelines](#interactivity-guidelines)
8. [Animations](#animations)

---

## Core Principles

### Glanceability
- **Quick access to essential info**: Design for 2-3 second viewing
- **Prioritize dynamic content**: Information that changes throughout the day
- **Avoid app-like complexity**: Reserve detailed interactions for your app

### Value Proposition
- Choose ideas that relate to your app's main purpose
- Provide content users would find useful to see at a glance
- Don't replicate your app icon - offer real value

### Personalization
- Let people configure widgets when it adds value
- Automatically display relevant content when possible
- Balance customization with simplicity

---

## Content Strategy

### What to Display
✅ **Good content**:
- Timely, personally relevant information
- Dynamic data that changes throughout the day
- Quick actions users perform frequently
- Progress indicators and countdowns

❌ **Avoid**:
- Static content that never changes
- Sparse layouts that seem unnecessary
- Overly dense, cluttered information
- Content unrelated to widget's purpose

### Size Considerations
| Size | Content Strategy |
|------|------------------|
| Small | Single piece of information, one tap target |
| Medium | Multiple data points, 2-3 interactive elements |
| Large | Rich content, detailed visualizations |
| Extra Large | Dashboard-style, comprehensive views |

---

## Layout & Margins

### Standard Margins
- **Default**: 16pt margins for most widgets
- **Tight**: 11pt for content groupings, buttons, background shapes
- **Lock Screen/StandBy**: Smaller margins automatically applied

### Corner Radius
```swift
// Use ContainerRelativeShape to match widget corners
RoundedRectangle(cornerRadius: 0)
    .fill(.blue)
    .clipShape(ContainerRelativeShape())
```

### Padding
```swift
VStack {
    Content()
}
.padding()  // Standard padding
.padding(.horizontal, 16)  // Custom horizontal
.padding(11)  // Tighter padding
```

---

## Typography

### System Font Preference
- Use SF Pro for consistency across platforms
- System font adapts to user's accessibility settings
- Custom fonts sparingly (large text only)

### Minimum Sizes
- **Body text**: 11pt minimum
- **Captions**: 11pt minimum
- **Avoid**: Smaller than 11pt is hard to read

### Text Styles
```swift
Text("Title")
    .font(.headline)

Text("Body content")
    .font(.subheadline)

Text("Caption")
    .font(.caption)
    .foregroundStyle(.secondary)
```

### Date/Time Display
```swift
// Auto-updating relative time
Text(date, style: .relative)  // "2 hours ago"
Text(date, style: .timer)     // "2:45:30"
Text(date, style: .offset)    // "+2 hours"
Text(date, style: .time)      // "3:45 PM"
Text(date, style: .date)      // "January 15"
```

---

## Color & Imagery

### Color Guidelines
- Enhance appearance without competing with content
- Support both light and dark appearances
- Convey meaning without relying solely on color
- Use semantic colors when possible

```swift
// Semantic colors adapt to appearance
Text("Primary")
    .foregroundStyle(.primary)
Text("Secondary")
    .foregroundStyle(.secondary)

// Background
.background(.background)
.background(.fill)
```

### Image Handling
- Full-color images are desaturated in tinted/vibrant modes
- Use `widgetAccentable()` for images that should tint
- Keep images smaller than widget size in tinted mode
- Reserve full-color for media content (album art, etc.)

```swift
Image("albumArt")
    .resizable()
    .widgetAccentedRenderingMode(.fullColor)  // Keep full color

Image(systemName: "star.fill")
    .widgetAccentable()  // Tint with accent color
```

---

## Rendering Modes

### Full-Color Mode
- Preserve original colors
- Support light/dark variants in asset catalog
- Use semantic system colors

### Accented Mode
```swift
@Environment(\.widgetRenderingMode) var renderingMode

var body: some View {
    if renderingMode == .accented {
        // Simplified design for tinted appearance
        AccentedView()
    } else {
        FullColorView()
    }
}
```

#### Accent Groups
```swift
// Content in accent group gets accent color
VStack {
    Image(systemName: "star.fill")
        .widgetAccentable()
    Text("Accent Text")
        .widgetAccentable()
}
```

### Vibrant Mode (Lock Screen)
- Content automatically desaturated
- Add vibrancy effect over background
- Test readability against various wallpapers

---

## Interactivity Guidelines

### Tap Targets
- Make tap targets large enough for confident interaction
- Avoid accidental taps on wrong elements
- Small widgets: single tap target only

### Deep Linking
- Open app at the relevant location
- Don't make users navigate to find related content
- Preserve context from widget interaction

### Buttons & Toggles
- Offer simple, relevant functionality
- Reserve complexity for the app
- Keep actions directly related to widget content

```swift
// Good: Related action
Button(intent: CompleteTaskIntent()) {
    Image(systemName: "checkmark.circle")
}

// Avoid: Too complex for widget
Button(intent: EditTaskDetailsIntent()) {
    Text("Edit Details...")
}
```

---

## Animations

### Content Transitions
- Use animations to highlight data updates
- Maximum duration: 2 seconds
- Standard SwiftUI transitions work

```swift
Text(value)
    .contentTransition(.numericText())
    .animation(.smooth, value: value)

// Custom transitions
.transition(.push(from: .bottom))
.transition(.opacity)
```

### Update Animations
```swift
struct AnimatedWidgetView: View {
    let entry: Entry
    
    var body: some View {
        VStack {
            Text(entry.value)
                .contentTransition(.numericText(value: entry.value))
        }
        .animation(.default, value: entry.value)
    }
}
```

---

## Platform-Specific Design

### StandBy (iPhone)
- Widget appears scaled up
- Remove background colors (black background)
- Low-light: monochromatic red tint
- Prioritize large, readable text

### Lock Screen
- Vibrant rendering mode
- Test against various wallpapers
- Accessory widgets: extremely limited space

### visionOS
- 3D objects on surfaces
- Paper or glass treatment styles
- Design for viewing at distance
- Support simplified threshold

### watchOS
- Use colorful backgrounds with meaning
- Optimize for quick glances
- Consider complication slots
