# Widget Dimensions Reference

All dimensions in points (pt).

---

## iOS Widget Dimensions

| Screen Size (pt) | Small | Medium | Large | Circular | Rectangular | Inline |
|------------------|-------|--------|-------|----------|-------------|--------|
| 430×932 | 170×170 | 364×170 | 364×382 | 76×76 | 172×76 | 257×26 |
| 428×926 | 170×170 | 364×170 | 364×382 | 76×76 | 172×76 | 257×26 |
| 414×896 | 169×169 | 360×169 | 360×379 | 76×76 | 160×72 | 248×26 |
| 414×736 | 159×159 | 348×157 | 348×357 | 76×76 | 170×76 | 248×26 |
| 393×852 | 158×158 | 338×158 | 338×354 | 72×72 | 160×72 | 234×26 |
| 390×844 | 158×158 | 338×158 | 338×354 | 72×72 | 160×72 | 234×26 |
| 375×812 | 155×155 | 329×155 | 329×345 | 72×72 | 157×72 | 225×26 |
| 375×667 | 148×148 | 321×148 | 321×324 | 68×68 | 153×68 | 225×26 |
| 360×780 | 155×155 | 329×155 | 329×345 | 72×72 | 157×72 | 225×26 |
| 320×568 | 141×141 | 292×141 | 292×311 | N/A | N/A | N/A |

### Device Reference
- **430×932**: iPhone 16 Pro Max, 15 Pro Max, 14 Pro Max
- **428×926**: iPhone 14 Plus, 13 Pro Max, 12 Pro Max
- **414×896**: iPhone 11 Pro Max, XS Max, 11, XR
- **414×736**: iPhone 8 Plus, 7 Plus, 6s Plus
- **393×852**: iPhone 16, 15, 15 Pro, 14 Pro
- **390×844**: iPhone 14, 13, 13 Pro, 12, 12 Pro
- **375×812**: iPhone 13 mini, 12 mini, 11 Pro, XS, X
- **375×667**: iPhone SE (2nd/3rd gen), 8, 7, 6s
- **360×780**: iPhone 16e
- **320×568**: iPhone SE (1st gen), 5s

---

## iPadOS Widget Dimensions

| Screen Size (pt) | Target | Small | Medium | Large | Extra Large |
|------------------|--------|-------|--------|-------|-------------|
| 768×1024 | Canvas | 141×141 | 305.5×141 | 305.5×305.5 | 634.5×305.5 |
| | Device | 120×120 | 260×120 | 260×260 | 540×260 |
| 744×1133 | Canvas | 141×141 | 305.5×141 | 305.5×305.5 | 634.5×305.5 |
| | Device | 120×120 | 260×120 | 260×260 | 540×260 |
| 810×1080 | Canvas | 146×146 | 320.5×146 | 320.5×320.5 | 669×320.5 |
| | Device | 124×124 | 272×124 | 272×272 | 568×272 |
| 820×1180 | Canvas | 155×155 | 342×155 | 342×342 | 715.5×342 |
| | Device | 136×136 | 300×136 | 300×300 | 628×300 |
| 834×1112 | Canvas | 150×150 | 327.5×150 | 327.5×327.5 | 682×327.5 |
| | Device | 132×132 | 288×132 | 288×288 | 600×288 |
| 834×1194 | Canvas | 155×155 | 342×155 | 342×342 | 715.5×342 |
| | Device | 136×136 | 300×136 | 300×300 | 628×300 |
| 954×1373* | Canvas | 162×162 | 350×162 | 350×350 | 726×350 |
| | Device | 162×162 | 350×162 | 350×350 | 726×350 |
| 970×1389* | Canvas | 162×162 | 350×162 | 350×350 | 726×350 |
| | Device | 162×162 | 350×162 | 350×350 | 726×350 |
| 1024×1366 | Canvas | 170×170 | 378.5×170 | 378.5×378.5 | 795×378.5 |
| | Device | 160×160 | 356×160 | 356×356 | 748×356 |
| 1192×1590* | Canvas | 188×188 | 412×188 | 412×412 | 860×412 |
| | Device | 188×188 | 412×188 | 412×412 | 860×412 |

\* When Display Zoom is set to "More Space"

### iPad Device Reference
- **768×1024**: iPad mini (6th gen)
- **810×1080**: iPad (9th gen)
- **820×1180**: iPad (10th gen)
- **834×1112**: iPad Air (3rd gen), iPad Pro 10.5"
- **834×1194**: iPad Air (4th/5th gen), iPad Pro 11"
- **1024×1366**: iPad Pro 12.9"

---

## visionOS Widget Dimensions

| Widget Size | Points (pt) | Physical (mm @ 100%) |
|-------------|-------------|----------------------|
| Small | 158×158 | 268×268 |
| Medium | 338×158 | 574×268 |
| Large | 338×354 | 574×600 |
| Extra Large | 450×338 | 763×574 |
| Extra Large Portrait | 338×450 | 574×763 |

**Note**: Users can scale widgets 75%–125% in visionOS.

---

## watchOS Widget Dimensions

### Smart Stack Widget Sizes

| Apple Watch Size | Widget Size (pt) |
|------------------|------------------|
| 40mm | 152×69.5 |
| 41mm | 165×72.5 |
| 44mm | 173×76.5 |
| 45mm | 184×80.5 |
| 49mm (Ultra) | 191×81.5 |

### Complication Sizes by Watch Face

Complication sizes vary by watch face. Use SwiftUI's automatic sizing:

```swift
struct ComplicationView: View {
    @Environment(\.widgetFamily) var family
    
    var body: some View {
        switch family {
        case .accessoryCircular:
            // Circular gauge or icon
            Gauge(value: 0.7) {
                Image(systemName: "heart.fill")
            }
            .gaugeStyle(.accessoryCircularCapacity)
            
        case .accessoryRectangular:
            // 2-3 lines of content
            VStack(alignment: .leading) {
                Text("Title")
                Text("Subtitle").font(.caption)
            }
            
        case .accessoryInline:
            // Single line
            Label("Status", systemImage: "star")
            
        case .accessoryCorner:
            // Corner placement
            Text("99")
                .widgetCurvesContent()
                
        default:
            EmptyView()
        }
    }
}
```

---

## Using Dimensions in Code

### Get Runtime Size
```swift
struct MyWidgetView: View {
    @Environment(\.widgetFamily) var family
    
    var body: some View {
        GeometryReader { geometry in
            // geometry.size contains actual widget size
            Content()
                .frame(width: geometry.size.width, height: geometry.size.height)
        }
    }
}
```

### Context Display Size
```swift
struct Provider: TimelineProvider {
    func getTimeline(in context: Context, completion: @escaping (Timeline<Entry>) -> Void) {
        let displaySize = context.displaySize
        // Use displaySize.width and displaySize.height
    }
}
```

### Responsive Layouts
```swift
struct AdaptiveContent: View {
    @Environment(\.widgetFamily) var family
    
    var body: some View {
        switch family {
        case .systemSmall:
            CompactLayout()
        case .systemMedium:
            HorizontalLayout()
        case .systemLarge, .systemExtraLarge:
            GridLayout()
        default:
            CompactLayout()
        }
    }
}
```

---

## Design Recommendations

### Margins
- **Standard**: 16pt
- **Tight**: 11pt (for groupings/buttons)
- **Lock Screen**: System applies smaller margins automatically

### Touch Targets
- **Minimum**: 44×44pt for interactive elements
- **Recommended**: Larger for better accessibility

### Font Sizes
- **Minimum readable**: 11pt
- **Headlines**: 17-20pt
- **Body**: 13-15pt
