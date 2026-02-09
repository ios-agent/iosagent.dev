# View Modifiers

SwiftUI view modifiers that can be applied to views to customize their appearance, behavior, and accessibility.

## Quick Reference

- **Presentation**: `sheet()`, `fullScreenCover()`, `popover()`
- **Navigation**: `navigationTitle()`, `navigationBarTitleDisplayMode()`
- **Layout**: `frame()`, `padding()`, `offset()`
- **Styling**: `fontWeight()`, `cornerRadius()`, `shadow()`
- **Interaction**: `onTapGesture()`, `disabled()`, `opacity()`
- **Accessibility**: 
- **Animations**: `animation()`, `transition()`, `matchedGeometryEffect()`
- **Visual Effects**: `glassEffect()`, `blur()`, `brightness()`, `contrast()`, `saturation()`, `grayscale()`
- **Transforms**: `rotationEffect()`, `scaleEffect()`, `aspectRatio()`

---

## Presentation

### sheet(isPresented:onDismiss:content:)

SwiftUI
View
sheet(isPresented:onDismiss:content:)
Instance Method
sheet(isPresented:onDismiss:content:)
Presents a sheet when a binding to a Boolean value that you provide is true.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
nonisolated
func sheet<Content>(
    isPresented: Binding<Bool>,
    onDismiss: (() -> Void)? = nil,
    @ViewBuilder content: @escaping () -> Content
) -> some View where Content : View

Parameters
isPresented

A binding to a Boolean value that determines whether to present the sheet that you create in the modifier’s content closure.

onDismiss

The closure to execute when dismissing the sheet.

content

A closure that returns the content of the sheet.

Discussion

Use this method when you want to present a modal view to the user when a Boolean value you provide is true. The example below displays a modal view of the mockup for a software license agreement when the user toggles the isShowingSheet variable by clicking or tapping on the “Show License Agreement” button:

struct ShowLicenseAgreement: View {
    @State private var isShowingSheet = false
    var body: some View {
        Button(action: {
            isShowingSheet.toggle()
        }) {
            Text("Show License Agreement")
        }
        .sheet(isPresented: $isShowingSheet,
               onDismiss: didDismiss) {
            VStack {
                Text("License Agreement")
                    .font(.title)

**Examples:**

```swift
nonisolated
func sheet<Content>(
    isPresented: Binding<Bool>,
    onDismiss: (() -> Void)? = nil,
    @ViewBuilder content: @escaping () -> Content
) -> some View where Content : View
```

```swift
nonisolated
func sheet<Content>(
    isPresented: Binding<Bool>,
    onDismiss: (() -> Void)? = nil,
    @ViewBuilder content: @escaping () -> Content
) -> some View where Content : View
```

```swift
ViewBuilder
```

```swift
struct ShowLicenseAgreement: View {
    @State private var isShowingSheet = false
    var body: some View {
        Button(action: {
            isShowingSheet.toggle()
        }) {
            Text("Show License Agreement")
        }
        .sheet(isPresented: $isShowingSheet,
               onDismiss: didDismiss) {
            VStack {
                Text("License Agreement")
                    .font(.title)
                    .padding(50)
                Text("""
                        Terms and conditions go here.
                    """)
                    .padding(50)
                Button("Dismiss",
                       action: { isShowingSheet.toggle() })
            }
        }
    }


    func didDismiss() {
        // Handle the dismissing action.
    }
}
```

```swift
struct ShowLicenseAgreement: View {
    @State private var isShowingSheet = false
    var body: some View {
        Button(action: {
            isShowingSheet.toggle()
        }) {
            Text("Show License Agreement")
        }
        .sheet(isPresented: $isShowingSheet,
               onDismiss: didDismiss) {
            VStack {
                Text("License Agreement")
                    .font(.title)
                    .padding(50)
                Text("""
                        Terms and conditions go here.
                    """)
                    .padding(50)
                Button("Dismiss",
                       action: { isShowingSheet.toggle() })
            }
        }
    }


    func didDismiss() {
        // Handle the dismissing action.
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/view/sheet(ispresented:ondismiss:content:))

---

### fullScreenCover(isPresented:onDismiss:content:)

SwiftUI
View
fullScreenCover(isPresented:onDismiss:content:)
Instance Method
fullScreenCover(isPresented:onDismiss:content:)
Presents a modal view that covers as much of the screen as possible when binding to a Boolean value you provide is true.
iOS 14.0+
iPadOS 14.0+
Mac Catalyst 14.0+
tvOS 14.0+
visionOS 1.0+
watchOS 7.0+
nonisolated
func fullScreenCover<Content>(
    isPresented: Binding<Bool>,
    onDismiss: (() -> Void)? = nil,
    @ViewBuilder content: @escaping () -> Content
) -> some View where Content : View

Parameters
isPresented

A binding to a Boolean value that determines whether to present the sheet.

onDismiss

The closure to execute when dismissing the modal view.

content

A closure that returns the content of the modal view.

Discussion

Use this method to show a modal view that covers as much of the screen as possible. The example below displays a custom view when the user toggles the value of the isPresenting binding:

struct FullScreenCoverPresentedOnDismiss: View {
    @State private var isPresenting = false
    var body: some View {
        Button("Present Full-Screen Cover") {
            isPresenting.toggle()
        }
        .fullScreenCover(isPresented: $isPresenting,
                         onDismiss: didDismiss) {
            VStack {
                Text("A full-screen modal view.")
                    .font(.title)
                Text("Tap to Dismiss")
            }
            .onTapGesture {

**Examples:**

```swift
nonisolated
func fullScreenCover<Content>(
    isPresented: Binding<Bool>,
    onDismiss: (() -> Void)? = nil,
    @ViewBuilder content: @escaping () -> Content
) -> some View where Content : View
```

```swift
nonisolated
func fullScreenCover<Content>(
    isPresented: Binding<Bool>,
    onDismiss: (() -> Void)? = nil,
    @ViewBuilder content: @escaping () -> Content
) -> some View where Content : View
```

```swift
ViewBuilder
```

```swift
struct FullScreenCoverPresentedOnDismiss: View {
    @State private var isPresenting = false
    var body: some View {
        Button("Present Full-Screen Cover") {
            isPresenting.toggle()
        }
        .fullScreenCover(isPresented: $isPresenting,
                         onDismiss: didDismiss) {
            VStack {
                Text("A full-screen modal view.")
                    .font(.title)
                Text("Tap to Dismiss")
            }
            .onTapGesture {
                isPresenting.toggle()
            }
            .foregroundColor(.white)
            .frame(maxWidth: .infinity,
                   maxHeight: .infinity)
            .background(Color.blue)
            .ignoresSafeArea(edges: .all)
        }
    }


    func didDismiss() {
        // Handle the dismissing action.
    }
}
```

```swift
struct FullScreenCoverPresentedOnDismiss: View {
    @State private var isPresenting = false
    var body: some View {
        Button("Present Full-Screen Cover") {
            isPresenting.toggle()
        }
        .fullScreenCover(isPresented: $isPresenting,
                         onDismiss: didDismiss) {
            VStack {
                Text("A full-screen modal view.")
                    .font(.title)
                Text("Tap to Dismiss")
            }
            .onTapGesture {
                isPresenting.toggle()
            }
            .foregroundColor(.white)
            .frame(maxWidth: .infinity,
                   maxHeight: .infinity)
            .background(Color.blue)
            .ignoresSafeArea(edges: .all)
        }
    }


    func didDismiss() {
        // Handle the dismissing action.
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/view/fullscreencover(ispresented:ondismiss:content:))

---

### popover(isPresented:attachmentAnchor:arrowEdge:content:)

SwiftUI
View
popover(isPresented:attachmentAnchor:arrowEdge:content:)
Instance Method
popover(isPresented:attachmentAnchor:arrowEdge:content:)
Presents a popover when a given condition is true.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
visionOS 1.0+
nonisolated
func popover<Content>(
    isPresented: Binding<Bool>,
    attachmentAnchor: PopoverAttachmentAnchor = .rect(.bounds),
    arrowEdge: Edge? = nil,
    @ViewBuilder content: @escaping () -> Content
) -> some View where Content : View

Parameters
isPresented

A binding to a Boolean value that determines whether to present the popover content that you return from the modifier’s content closure.

attachmentAnchor

The positioning anchor that defines the attachment point of the popover. The default is bounds.

arrowEdge

The edge of the attachmentAnchor that defines the location of the popover’s arrow. The default is nil, which results in the system allowing any arrow edge.

content

A closure returning the content of the popover.

Discussion

Use this method to show a popover whose contents are a SwiftUI view that you provide when a bound Boolean variable is true. In the example below, a popover displays whenever the user toggles the isShowingPopover state variable by pressing the “Show Popover” button:

struct PopoverExample: View {
    @State private var isShowingPopover = false


    var body: some View {
        Button("Show Popover") {
            self.isShowingPopover = true
        }
        .popover(
            isPresented: $isShowingPopover, arrowEdge: .bottom

**Examples:**

```swift
nonisolated
func popover<Content>(
    isPresented: Binding<Bool>,
    attachmentAnchor: PopoverAttachmentAnchor = .rect(.bounds),
    arrowEdge: Edge? = nil,
    @ViewBuilder content: @escaping () -> Content
) -> some View where Content : View
```

```swift
nonisolated
func popover<Content>(
    isPresented: Binding<Bool>,
    attachmentAnchor: PopoverAttachmentAnchor = .rect(.bounds),
    arrowEdge: Edge? = nil,
    @ViewBuilder content: @escaping () -> Content
) -> some View where Content : View
```

```swift
PopoverAttachmentAnchor
```

```swift
ViewBuilder
```

```swift
struct PopoverExample: View {
    @State private var isShowingPopover = false


    var body: some View {
        Button("Show Popover") {
            self.isShowingPopover = true
        }
        .popover(
            isPresented: $isShowingPopover, arrowEdge: .bottom
        ) {
            Text("Popover Content")
                .padding()
        }
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/view/popover(ispresented:attachmentanchor:arrowedge:content:))

---

### alert (Failed to scrape)

Error: Page.goto: Timeout 30000ms exceeded.
Call log:
  - navigating to "https://developer.apple.com/documentation/swiftui/view/alert(_:ispresented:actions:)-16hrk", waiting until "networkidle"


[View Official Documentation](https://developer.apple.com/documentation/swiftui/view/alert(_:ispresented:actions:)-16hrk)

---

### confirmationDialog (Failed to scrape)

Error: Page.goto: Timeout 30000ms exceeded.
Call log:
  - navigating to "https://developer.apple.com/documentation/swiftui/view/confirmationdialog(_:ispresented:titlevisibility:actions:)-5scpa", waiting until "networkidle"


[View Official Documentation](https://developer.apple.com/documentation/swiftui/view/confirmationdialog(_:ispresented:titlevisibility:actions:)-5scpa)

---

## Navigation

### toolbar (Failed to scrape)

Error: Page.goto: Timeout 30000ms exceeded.
Call log:
  - navigating to "https://developer.apple.com/documentation/swiftui/view/toolbar(content:)-41w96", waiting until "networkidle"


[View Official Documentation](https://developer.apple.com/documentation/swiftui/view/toolbar(content:)-41w96)

---

### toolbarItem (Failed to scrape)

Error: Page.goto: Timeout 30000ms exceeded.
Call log:
  - navigating to "https://developer.apple.com/documentation/swiftui/view/toolbaritem(id:placement:showsbydefault:content:)", waiting until "networkidle"


[View Official Documentation](https://developer.apple.com/documentation/swiftui/view/toolbaritem(id:placement:showsbydefault:content:))

---

### navigationTitle(_:)

SwiftUI
View
navigationTitle(_:)
Instance Method
navigationTitle(_:)
Configures the view’s title for purposes of navigation, using a localized string.
iOS 14.0+
iPadOS 14.0+
Mac Catalyst 14.0+
macOS 11.0+
tvOS 14.0+
visionOS 1.0+
watchOS 7.0+
nonisolated
func navigationTitle(_ titleKey: LocalizedStringKey) -> some View

Show all declarations
Parameters
titleKey

The key to a localized string to display.

Discussion

A view’s navigation title is used to visually display the current navigation state of an interface. On iOS and watchOS, when a view is navigated to inside of a navigation view, that view’s title is displayed in the navigation bar. On iPadOS, the primary destination’s navigation title is reflected as the window’s title in the App Switcher. Similarly on macOS, the primary destination’s title is used as the window title in the titlebar, Windows menu and Mission Control.

Refer to the Configure your apps navigation titles article for more information on navigation title modifiers.

**Examples:**

```swift
nonisolated
func navigationTitle(_ titleKey: LocalizedStringKey) -> some View
```

```swift
nonisolated
func navigationTitle(_ titleKey: LocalizedStringKey) -> some View
```

```swift
LocalizedStringKey
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/view/navigationtitle(_:)-43srq)

---

### navigationBarTitleDisplayMode(_:)

SwiftUI
View
navigationBarTitleDisplayMode(_:)
Instance Method
navigationBarTitleDisplayMode(_:)
Configures the title display mode for this view.
iOS 14.0+
iPadOS 14.0+
Mac Catalyst 14.0+
visionOS 1.0+
watchOS 8.0+
nonisolated
func navigationBarTitleDisplayMode(_ displayMode: NavigationBarItem.TitleDisplayMode) -> some View

Parameters
displayMode

The style to use for displaying the title.

See Also
Configuring the navigation bar
func navigationBarBackButtonHidden(Bool) -> some View
Hides the navigation bar back button for the view.
struct NavigationBarItem
A configuration for a navigation bar that represents a view at the top of a navigation stack.

**Examples:**

```swift
nonisolated
func navigationBarTitleDisplayMode(_ displayMode: NavigationBarItem.TitleDisplayMode) -> some View
```

```swift
nonisolated
func navigationBarTitleDisplayMode(_ displayMode: NavigationBarItem.TitleDisplayMode) -> some View
```

```swift
NavigationBarItem
```

```swift
TitleDisplayMode
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/view/navigationbartitledisplaymode(_:))

---

## Layout

### frame(width:height:alignment:)

SwiftUI
View
frame(width:height:alignment:)
Instance Method
frame(width:height:alignment:)
Positions this view within an invisible frame with the specified size.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
nonisolated
func frame(
    width: CGFloat? = nil,
    height: CGFloat? = nil,
    alignment: Alignment = .center
) -> some View

Parameters
width

A fixed width for the resulting view. If width is nil, the resulting view assumes this view’s sizing behavior.

height

A fixed height for the resulting view. If height is nil, the resulting view assumes this view’s sizing behavior.

alignment

The alignment of this view inside the resulting frame. Note that most alignment values have no apparent effect when the size of the frame happens to match that of this view.

Return Value

A view with fixed dimensions of width and height, for the parameters that are non-nil.

Mentioned in
Building layouts with stack views
Configuring views
Laying out a simple view
Discussion

Use this method to specify a fixed size for a view’s width, height, or both. If you only specify one of the dimensions, the resulting view assumes this view’s sizing behavior in the other dimension.

For example, the following code lays out an ellipse in a fixed 200 by 100 frame. Because a shape always occupies the space offered to it by the layout system, the first ellipse is 200x100 points. The second ellipse is laid out in a frame with only a fixed height, so it occupies that height, and whatever width the layout system offers to its parent.

VStack {
    Ellipse()
        .fill(Color.purple)

**Examples:**

```swift
nonisolated
func frame(
    width: CGFloat? = nil,
    height: CGFloat? = nil,
    alignment: Alignment = .center
) -> some View
```

```swift
nonisolated
func frame(
    width: CGFloat? = nil,
    height: CGFloat? = nil,
    alignment: Alignment = .center
) -> some View
```

```swift
VStack {
    Ellipse()
        .fill(Color.purple)
        .frame(width: 200, height: 100)
    Ellipse()
        .fill(Color.blue)
        .frame(height: 100)
}
```

```swift
VStack {
    Ellipse()
        .fill(Color.purple)
        .frame(width: 200, height: 100)
    Ellipse()
        .fill(Color.blue)
        .frame(height: 100)
}
```

```swift
Text("Hello world!")
    .frame(width: 200, height: 30, alignment: .topLeading)
    .border(Color.gray)
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/view/frame(width:height:alignment:))

---

### padding(_:)

SwiftUI
View
padding(_:)
Instance Method
padding(_:)
Adds a specific padding amount to each edge of this view.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
nonisolated
func padding(_ length: CGFloat) -> some View

Show all declarations
Parameters
length

The amount, given in points, to pad this view on all edges.

Return Value

A view that’s padded by the amount you specify.

Discussion

Use this modifier to add padding all the way around a view.

VStack {
    Text("Text padded by 10 points on each edge.")
        .padding(10)
        .border(.gray)
    Text("Unpadded text for comparison.")
        .border(.yellow)
}


The order in which you apply modifiers matters. The example above applies the padding before applying the border to ensure that the border encompasses the padded region:

To independently control the amount of padding for each edge, use padding(_:). To pad a select set of edges by the same amount, use padding(_:_:).

**Examples:**

```swift
nonisolated
func padding(_ length: CGFloat) -> some View
```

```swift
nonisolated
func padding(_ length: CGFloat) -> some View
```

```swift
VStack {
    Text("Text padded by 10 points on each edge.")
        .padding(10)
        .border(.gray)
    Text("Unpadded text for comparison.")
        .border(.yellow)
}
```

```swift
VStack {
    Text("Text padded by 10 points on each edge.")
        .padding(10)
        .border(.gray)
    Text("Unpadded text for comparison.")
        .border(.yellow)
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/view/padding(_:)-68shk)

---

### background (Failed to scrape)

Error: Page.goto: Timeout 30000ms exceeded.
Call log:
  - navigating to "https://developer.apple.com/documentation/swiftui/view/background(alignment:content:)-89n7j", waiting until "networkidle"


[View Official Documentation](https://developer.apple.com/documentation/swiftui/view/background(alignment:content:)-89n7j)

---

### overlay (Failed to scrape)

Error: Page.goto: Timeout 30000ms exceeded.
Call log:
  - navigating to "https://developer.apple.com/documentation/swiftui/view/overlay(alignment:content:)-9ydux", waiting until "networkidle"


[View Official Documentation](https://developer.apple.com/documentation/swiftui/view/overlay(alignment:content:)-9ydux)

---

### offset(_:)

SwiftUI
View
offset(_:)
Instance Method
offset(_:)
Offset this view by the horizontal and vertical amount specified in the offset parameter.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
nonisolated
func offset(_ offset: CGSize) -> some View

Parameters
offset

The distance to offset this view.

Return Value

A view that offsets this view by offset.

Discussion

Use offset(_:) to shift the displayed contents by the amount specified in the offset parameter.

The original dimensions of the view aren’t changed by offsetting the contents; in the example below the gray border drawn by this view surrounds the original position of the text:

Text("Offset by passing CGSize()")
    .border(Color.green)
    .offset(CGSize(width: 20, height: 25))
    .border(Color.gray)


See Also
Adjusting a view’s position
Making fine adjustments to a view’s position
Shift the position of a view by applying the offset or position modifier.
func position(CGPoint) -> some View
Positions the center of this view at the specified point in its parent’s coordinate space.
func position(x: CGFloat, y: CGFloat) -> some View
Positions the center of this view at the specified coordinates in its parent’s coordinate space.
func offset(x: CGFloat, y: CGFloat) -> some View
Offset this view by the specified horizontal and vertical distances.
func offset(z: CGFloat) -> some View
Brings a view forward in Z by the provided distance in points.

**Examples:**

```swift
nonisolated
func offset(_ offset: CGSize) -> some View
```

```swift
nonisolated
func offset(_ offset: CGSize) -> some View
```

```swift
Text("Offset by passing CGSize()")
    .border(Color.green)
    .offset(CGSize(width: 20, height: 25))
    .border(Color.gray)
```

```swift
Text("Offset by passing CGSize()")
    .border(Color.green)
    .offset(CGSize(width: 20, height: 25))
    .border(Color.gray)
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/view/offset(_:))

---

## Styling

### foregroundStyle (Failed to scrape)

Error: Page.goto: Timeout 30000ms exceeded.
Call log:
  - navigating to "https://developer.apple.com/documentation/swiftui/view/foregroundstyle(_:)-7xm6o", waiting until "networkidle"


[View Official Documentation](https://developer.apple.com/documentation/swiftui/view/foregroundstyle(_:)-7xm6o)

---

### font (Failed to scrape)

Error: Page.goto: Timeout 30000ms exceeded.
Call log:
  - navigating to "https://developer.apple.com/documentation/swiftui/view/font(_:)", waiting until "networkidle"


[View Official Documentation](https://developer.apple.com/documentation/swiftui/view/font(_:))

---

### fontWeight(_:)

SwiftUI
View
fontWeight(_:)
Instance Method
fontWeight(_:)
Sets the font weight of the text in this view.
iOS 16.0+
iPadOS 16.0+
Mac Catalyst 16.0+
macOS 13.0+
tvOS 16.0+
visionOS 1.0+
watchOS 9.0+
nonisolated
func fontWeight(_ weight: Font.Weight?) -> some View

Parameters
weight

One of the available font weights. Providing nil removes the effect of any font weight modifier applied higher in the view hierarchy.

Return Value

A view that uses the font weight you specify.

See Also
Setting a font
Applying custom fonts to text
Add and use a font in your app that scales with Dynamic Type.
func font(Font?) -> some View
Sets the default font for text in this view.
func fontDesign(Font.Design?) -> some View
Sets the font design of the text in this view.
func fontWidth(Font.Width?) -> some View
Sets the font width of the text in this view.
var font: Font?
The default font of this environment.
struct Font
An environment-dependent font.

**Examples:**

```swift
nonisolated
func fontWeight(_ weight: Font.Weight?) -> some View
```

```swift
nonisolated
func fontWeight(_ weight: Font.Weight?) -> some View
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/view/fontweight(_:))

---

### cornerRadius(_:antialiased:)

SwiftUI
cornerRadius(_:antialiased:)
Deprecated
Instance Method
cornerRadius(_:antialiased:)
Clips this view to its bounding frame, with the specified corner radius.
iOS 13.0–26.2
Deprecated
iPadOS 13.0–26.2
Deprecated
Mac Catalyst 13.0–26.2
Deprecated
macOS 10.15–26.2
Deprecated
tvOS 13.0–26.2
Deprecated
visionOS 1.0–26.2
Deprecated
watchOS 6.0–26.2
Deprecated
nonisolated
func cornerRadius(
    _ radius: CGFloat,
    antialiased: Bool = true
) -> some View


Deprecated

Use clipShape(_:style:) or fill(style:) instead.

Parameters
radius

A CGFloat value that specifies the corner radius to use when clipping the view to its bounding frame.

antialiased

A Boolean value that indicates whether the rendering system applies smoothing to the edges of the clipping rectangle.

Return Value

A view that clips this view to its bounding frame with the specified corner radius.

Discussion

By default, a view’s bounding frame only affects its layout, so any content that extends beyond the edges of the frame remains visible. Use cornerRadius(_:antialiased:) to hide any content that extends beyond these edges while applying a corner radius.

The following code applies a corner radius of 25 to a text view:


**Examples:**

```swift
nonisolated
func cornerRadius(
    _ radius: CGFloat,
    antialiased: Bool = true
) -> some View
```

```swift
nonisolated
func cornerRadius(
    _ radius: CGFloat,
    antialiased: Bool = true
) -> some View
```

```swift
Text("Rounded Corners")
    .frame(width: 175, height: 75)
    .foregroundColor(Color.white)
    .background(Color.black)
    .cornerRadius(25)
```

```swift
Text("Rounded Corners")
    .frame(width: 175, height: 75)
    .foregroundColor(Color.white)
    .background(Color.black)
    .cornerRadius(25)
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/view/cornerradius(_:antialiased:))

---

### shadow(color:radius:x:y:)

SwiftUI
View
shadow(color:radius:x:y:)
Instance Method
shadow(color:radius:x:y:)
Adds a shadow to this view.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
nonisolated
func shadow(
    color: Color = Color(.sRGBLinear, white: 0, opacity: 0.33),
    radius: CGFloat,
    x: CGFloat = 0,
    y: CGFloat = 0
) -> some View

Parameters
color

The shadow’s color.

radius

A measure of how much to blur the shadow. Larger values result in more blur.

x

An amount to offset the shadow horizontally from the view.

y

An amount to offset the shadow vertically from the view.

Return Value

A view that adds a shadow to this view.

Discussion

Use this modifier to add a shadow of a specified color behind a view. You can offset the shadow from its view independently in the horizontal and vertical dimensions using the x and y parameters. You can also blur the edges of the shadow using the radius parameter. Use a radius of zero to create a sharp shadow. Larger radius values produce softer shadows.

The example below creates a grid of boxes with varying offsets and blur. Each box displays its radius and offset values for reference.

struct Shadow: View {
    let steps = [0, 5, 10]

**Examples:**

```swift
nonisolated
func shadow(
    color: Color = Color(.sRGBLinear, white: 0, opacity: 0.33),
    radius: CGFloat,
    x: CGFloat = 0,
    y: CGFloat = 0
) -> some View
```

```swift
nonisolated
func shadow(
    color: Color = Color(.sRGBLinear, white: 0, opacity: 0.33),
    radius: CGFloat,
    x: CGFloat = 0,
    y: CGFloat = 0
) -> some View
```

```swift
struct Shadow: View {
    let steps = [0, 5, 10]


    var body: some View {
        VStack(spacing: 50) {
            ForEach(steps, id: \.self) { offset in
                HStack(spacing: 50) {
                    ForEach(steps, id: \.self) { radius in
                        Color.blue
                            .shadow(
                                color: .primary,
                                radius: CGFloat(radius),
                                x: CGFloat(offset), y: CGFloat(offset))
                            .overlay {
                                VStack {
                                    Text("\(radius)")
                                    Text("(\(offset), \(offset))")
                                }
                            }
                    }
                }
            }
        }
    }
}
```

```swift
struct Shadow: View {
    let steps = [0, 5, 10]


    var body: some View {
        VStack(spacing: 50) {
            ForEach(steps, id: \.self) { offset in
                HStack(spacing: 50) {
                    ForEach(steps, id: \.self) { radius in
                        Color.blue
                            .shadow(
                                color: .primary,
                                radius: CGFloat(radius),
                                x: CGFloat(offset), y: CGFloat(offset))
                            .overlay {
                                VStack {
                                    Text("\(radius)")
                                    Text("(\(offset), \(offset))")
                                }
                            }
                    }
                }
            }
        }
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/view/shadow(color:radius:x:y:))

---

## Interaction

### onTapGesture(count:perform:)

SwiftUI
View
onTapGesture(count:perform:)
Instance Method
onTapGesture(count:perform:)
Adds an action to perform when this view recognizes a tap gesture.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 16.0+
visionOS 1.0+
watchOS 6.0+
nonisolated
func onTapGesture(
    count: Int = 1,
    perform action: @escaping () -> Void
) -> some View

Parameters
count

The number of taps or clicks required to trigger the action closure provided in action. Defaults to 1.

action

The action to perform.

Discussion

Use this method to perform the specified action when the user clicks or taps on the view or container count times.

Note

If you create a control that’s functionally equivalent to a Button, use ButtonStyle to create a customized button instead.

In the example below, the color of the heart images changes to a random color from the colors array whenever the user clicks or taps on the view twice:

struct TapGestureExample: View {
    let colors: [Color] = [.gray, .red, .orange, .yellow,
                           .green, .blue, .purple, .pink]
    @State private var fgColor: Color = .gray


    var body: some View {
        Image(systemName: "heart.fill")
            .resizable()
            .frame(width: 200, height: 200)
            .foregroundColor(fgColor)
            .onTapGesture(count: 2) {

**Examples:**

```swift
nonisolated
func onTapGesture(
    count: Int = 1,
    perform action: @escaping () -> Void
) -> some View
```

```swift
nonisolated
func onTapGesture(
    count: Int = 1,
    perform action: @escaping () -> Void
) -> some View
```

```swift
struct TapGestureExample: View {
    let colors: [Color] = [.gray, .red, .orange, .yellow,
                           .green, .blue, .purple, .pink]
    @State private var fgColor: Color = .gray


    var body: some View {
        Image(systemName: "heart.fill")
            .resizable()
            .frame(width: 200, height: 200)
            .foregroundColor(fgColor)
            .onTapGesture(count: 2) {
                fgColor = colors.randomElement()!
            }
    }
}
```

```swift
struct TapGestureExample: View {
    let colors: [Color] = [.gray, .red, .orange, .yellow,
                           .green, .blue, .purple, .pink]
    @State private var fgColor: Color = .gray


    var body: some View {
        Image(systemName: "heart.fill")
            .resizable()
            .frame(width: 200, height: 200)
            .foregroundColor(fgColor)
            .onTapGesture(count: 2) {
                fgColor = colors.randomElement()!
            }
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/view/ontapgesture(count:perform:))

---

### gesture (Failed to scrape)

Error: Page.goto: Timeout 30000ms exceeded.
Call log:
  - navigating to "https://developer.apple.com/documentation/swiftui/view/gesture(_:including:)-f20a", waiting until "networkidle"


[View Official Documentation](https://developer.apple.com/documentation/swiftui/view/gesture(_:including:)-f20a)

---

### disabled(_:)

SwiftUI
View
disabled(_:)
Instance Method
disabled(_:)
Adds a condition that controls whether users can interact with this view.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
nonisolated
func disabled(_ disabled: Bool) -> some View

Parameters
disabled

A Boolean value that determines whether users can interact with this view.

Return Value

A view that controls whether users can interact with this view.

Discussion

The higher views in a view hierarchy can override the value you set on this view. In the following example, the button isn’t interactive because the outer disabled(_:) modifier overrides the inner one:

HStack {
    Button(Text("Press")) {}
    .disabled(false)
}
.disabled(true)

See Also
Managing view interaction
var isEnabled: Bool
A Boolean value that indicates whether the view associated with this environment allows user interaction.
func interactionActivityTrackingTag(String) -> some View
Sets a tag that you use for tracking interactivity.
func invalidatableContent(Bool) -> some View
Mark the receiver as their content might be invalidated.

**Examples:**

```swift
nonisolated
func disabled(_ disabled: Bool) -> some View
```

```swift
nonisolated
func disabled(_ disabled: Bool) -> some View
```

```swift
HStack {
    Button(Text("Press")) {}
    .disabled(false)
}
.disabled(true)
```

```swift
HStack {
    Button(Text("Press")) {}
    .disabled(false)
}
.disabled(true)
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/view/disabled(_:))

---

### opacity(_:)

SwiftUI
View
opacity(_:)
Instance Method
opacity(_:)
Sets the transparency of this view.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
nonisolated
func opacity(_ opacity: Double) -> some View

Parameters
opacity

A value between 0 (fully transparent) and 1 (fully opaque).

Return Value

A view that sets the transparency of this view.

Discussion

Apply opacity to reveal views that are behind another view or to de-emphasize a view.

When applying the opacity(_:) modifier to a view that has already had its opacity transformed, the modifier multiplies the effect of the underlying opacity transformation.

The example below shows yellow and red rectangles configured to overlap. The top yellow rectangle has its opacity set to 50%, allowing the occluded portion of the bottom rectangle to be visible:

struct Opacity: View {
    var body: some View {
        VStack {
            Color.yellow.frame(width: 100, height: 100, alignment: .center)
                .zIndex(1)
                .opacity(0.5)


            Color.red.frame(width: 100, height: 100, alignment: .center)
                .padding(-40)
        }
    }
}


See Also
Hiding views

**Examples:**

```swift
nonisolated
func opacity(_ opacity: Double) -> some View
```

```swift
nonisolated
func opacity(_ opacity: Double) -> some View
```

```swift
struct Opacity: View {
    var body: some View {
        VStack {
            Color.yellow.frame(width: 100, height: 100, alignment: .center)
                .zIndex(1)
                .opacity(0.5)


            Color.red.frame(width: 100, height: 100, alignment: .center)
                .padding(-40)
        }
    }
}
```

```swift
struct Opacity: View {
    var body: some View {
        VStack {
            Color.yellow.frame(width: 100, height: 100, alignment: .center)
                .zIndex(1)
                .opacity(0.5)


            Color.red.frame(width: 100, height: 100, alignment: .center)
                .padding(-40)
        }
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/view/opacity(_:))

---

## Accessibility

### accessibilityLabel (Failed to scrape)

Error: Page.goto: Timeout 30000ms exceeded.
Call log:
  - navigating to "https://developer.apple.com/documentation/swiftui/view/accessibilitylabel(_:)-88xs4", waiting until "networkidle"


[View Official Documentation](https://developer.apple.com/documentation/swiftui/view/accessibilitylabel(_:)-88xs4)

---

### accessibilityHint (Failed to scrape)

Error: Page.goto: Timeout 30000ms exceeded.
Call log:
  - navigating to "https://developer.apple.com/documentation/swiftui/view/accessibilityhint(_:)-7gke9", waiting until "networkidle"


[View Official Documentation](https://developer.apple.com/documentation/swiftui/view/accessibilityhint(_:)-7gke9)

---

### accessibilityValue (Failed to scrape)

Error: Page.goto: Timeout 30000ms exceeded.
Call log:
  - navigating to "https://developer.apple.com/documentation/swiftui/view/accessibilityvalue(_:)-52vvd", waiting until "networkidle"


[View Official Documentation](https://developer.apple.com/documentation/swiftui/view/accessibilityvalue(_:)-52vvd)

---

## Animations

### animation(_:value:)

SwiftUI
View
animation(_:value:)
Instance Method
animation(_:value:)
Applies the given animation to this view when the specified value changes.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
nonisolated
func animation<V>(
    _ animation: Animation?,
    value: V
) -> some View where V : Equatable

Parameters
animation

The animation to apply. If animation is nil, the view doesn’t animate.

value

A value to monitor for changes.

Return Value

A view that applies animation to this view whenever value changes.

Mentioned in
Managing user interface state
See Also
Adding state-based animation to a view
func animation(_:)
Applies the given animation to this view when this view changes.
func animation<V>(Animation?, body: (PlaceholderContentView<Self>) -> V) -> some View
Applies the given animation to all animatable values within the body closure.

**Examples:**

```swift
nonisolated
func animation<V>(
    _ animation: Animation?,
    value: V
) -> some View where V : Equatable
```

```swift
nonisolated
func animation<V>(
    _ animation: Animation?,
    value: V
) -> some View where V : Equatable
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/view/animation(_:value:))

---

### transition(_:)

SwiftUI
View
transition(_:)
Instance Method
transition(_:)
Associates a transition with the view.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
nonisolated
func transition(_ t: AnyTransition) -> some View

Show all declarations
Discussion

When this view appears or disappears, the transition will be applied to it, allowing for animating it in and out.

The following code will conditionally show MyView, and when it appears or disappears, will use a slide transition to show it.

if isActive {
    MyView()
        .transition(.slide)
}
Button("Toggle") {
    withAnimation {
        isActive.toggle()
    }
}

See Also
Defining transitions
protocol Transition
A description of view changes to apply when a view is added to and removed from the view hierarchy.
struct TransitionProperties
The properties a Transition can have.
enum TransitionPhase
An indication of which the current stage of a transition.
struct AsymmetricTransition
A composite Transition that uses a different transition for insertion versus removal.
struct AnyTransition
A type-erased transition.
func contentTransition(ContentTransition) -> some View
Modifies the view to use a given transition as its method of animating changes to the contents of its views.
var contentTransition: ContentTransition
The current method of animating the contents of views.
var contentTransitionAddsDrawingGroup: Bool

**Examples:**

```swift
nonisolated
func transition(_ t: AnyTransition) -> some View
```

```swift
nonisolated
func transition(_ t: AnyTransition) -> some View
```

```swift
AnyTransition
```

```swift
if isActive {
    MyView()
        .transition(.slide)
}
Button("Toggle") {
    withAnimation {
        isActive.toggle()
    }
}
```

```swift
if isActive {
    MyView()
        .transition(.slide)
}
Button("Toggle") {
    withAnimation {
        isActive.toggle()
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/view/transition(_:))

---

### matchedGeometryEffect(id:in:properties:anchor:isSource:)

SwiftUI
View
matchedGeometryEffect(id:in:properties:anchor:isSource:)
Instance Method
matchedGeometryEffect(id:in:properties:anchor:isSource:)
Defines a group of views with synchronized geometry using an identifier and namespace that you provide.
iOS 14.0+
iPadOS 14.0+
Mac Catalyst 14.0+
macOS 11.0+
tvOS 14.0+
visionOS 1.0+
watchOS 7.0+
nonisolated
func matchedGeometryEffect<ID>(
    id: ID,
    in namespace: Namespace.ID,
    properties: MatchedGeometryProperties = .frame,
    anchor: UnitPoint = .center,
    isSource: Bool = true
) -> some View where ID : Hashable

Parameters
id

The identifier, often derived from the identifier of the data being displayed by the view.

namespace

The namespace in which defines the id. New namespaces are created by adding an @Namespace variable to a View type and reading its value in the view’s body method.

properties

The properties to copy from the source view.

anchor

The relative location in the view used to produce its shared position value.

isSource

True if the view should be used as the source of geometry for other views in the group.

Return Value

A new view that defines an entry in the global database of views synchronizing their geometry.

Discussion

This method sets the geometry of each view in the group from the inserted view with isSource = true (known as the “source” view), updating the values marked by properties.

**Examples:**

```swift
nonisolated
func matchedGeometryEffect<ID>(
    id: ID,
    in namespace: Namespace.ID,
    properties: MatchedGeometryProperties = .frame,
    anchor: UnitPoint = .center,
    isSource: Bool = true
) -> some View where ID : Hashable
```

```swift
nonisolated
func matchedGeometryEffect<ID>(
    id: ID,
    in namespace: Namespace.ID,
    properties: MatchedGeometryProperties = .frame,
    anchor: UnitPoint = .center,
    isSource: Bool = true
) -> some View where ID : Hashable
```

```swift
MatchedGeometryProperties
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/view/matchedgeometryeffect(id:in:properties:anchor:issource:))

---

## Visual Effects

### glassEffect(_:in:)

SwiftUI
View
glassEffect(_:in:)
Instance Method
glassEffect(_:in:)
Applies the Liquid Glass effect to a view.
iOS 26.0+
iPadOS 26.0+
Mac Catalyst 26.0+
macOS 26.0+
tvOS 26.0+
watchOS 26.0+
nonisolated
func glassEffect(
    _ glass: Glass = .regular,
    in shape: some Shape = DefaultGlassEffectShape()
) -> some View

Mentioned in
Applying Liquid Glass to custom views
Discussion

When you use this effect, the system:

Renders a shape anchored behind a view with the Liquid Glass material.

Applies the foreground effects of Liquid Glass over a view.

For example, to add this effect to a Text:

Text("Hello, World!")
    .font(.title)
    .padding()
    .glassEffect()


SwiftUI uses the regular variant by default along with a Capsule shape.

SwiftUI anchors the Liquid Glass to a view’s bounds. For the example above, the material fills the entirety of the Text frame, which includes the padding.

You typically use this modifier with a GlassEffectContainer to combine multiple Liquid Glass shapes into a single shape that can morph into one another.

See Also
Styling views with Liquid Glass
Applying Liquid Glass to custom views
Configure, combine, and morph views using Liquid Glass effects.
Landmarks: Building an app with Liquid Glass
Enhance your app experience with system-provided and custom Liquid Glass.
func interactive(Bool) -> Glass
Returns a copy of the structure configured to be interactive.

**Examples:**

```swift
nonisolated
func glassEffect(
    _ glass: Glass = .regular,
    in shape: some Shape = DefaultGlassEffectShape()
) -> some View
```

```swift
nonisolated
func glassEffect(
    _ glass: Glass = .regular,
    in shape: some Shape = DefaultGlassEffectShape()
) -> some View
```

```swift
Text("Hello, World!")
    .font(.title)
    .padding()
    .glassEffect()
```

```swift
Text("Hello, World!")
    .font(.title)
    .padding()
    .glassEffect()
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/view/glasseffect(_:in:))

---

### blur(radius:opaque:)

SwiftUI
View
blur(radius:opaque:)
Instance Method
blur(radius:opaque:)
Applies a Gaussian blur to this view.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
nonisolated
func blur(
    radius: CGFloat,
    opaque: Bool = false
) -> some View

Parameters
radius

The radial size of the blur. A blur is more diffuse when its radius is large.

opaque

A Boolean value that indicates whether the blur renderer permits transparency in the blur output. Set to true to create an opaque blur, or set to false to permit transparency.

Discussion

Use blur(radius:opaque:) to apply a gaussian blur effect to the rendering of this view.

The example below shows two Text views, the first with no blur effects, the second with blur(radius:opaque:) applied with the radius set to 2. The larger the radius, the more diffuse the effect.

struct Blur: View {
    var body: some View {
        VStack {
            Text("This is some text.")
                .padding()
            Text("This is some blurry text.")
                .blur(radius: 2.0)
        }
    }
}


See Also
Applying blur and shadows
func shadow(color: Color, radius: CGFloat, x: CGFloat, y: CGFloat) -> some View
Adds a shadow to this view.

**Examples:**

```swift
nonisolated
func blur(
    radius: CGFloat,
    opaque: Bool = false
) -> some View
```

```swift
nonisolated
func blur(
    radius: CGFloat,
    opaque: Bool = false
) -> some View
```

```swift
struct Blur: View {
    var body: some View {
        VStack {
            Text("This is some text.")
                .padding()
            Text("This is some blurry text.")
                .blur(radius: 2.0)
        }
    }
}
```

```swift
struct Blur: View {
    var body: some View {
        VStack {
            Text("This is some text.")
                .padding()
            Text("This is some blurry text.")
                .blur(radius: 2.0)
        }
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/view/blur(radius:opaque:))

---

### brightness(_:)

SwiftUI
View
brightness(_:)
Instance Method
brightness(_:)
Brightens this view by the specified amount.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
nonisolated
func brightness(_ amount: Double) -> some View

Parameters
amount

A value between 0 (no effect) and 1 (full white brightening) that represents the intensity of the brightness effect.

Return Value

A view that brightens this view by the specified amount.

Discussion

Use brightness(_:) to brighten the intensity of the colors in a view. The example below shows a series of red squares, with their brightness increasing from 0 (fully red) to 100% (white) in 20% increments.

struct Brightness: View {
    var body: some View {
        HStack {
            ForEach(0..<6) {
                Color.red.frame(width: 60, height: 60, alignment: .center)
                    .brightness(Double($0) * 0.2)
                    .overlay(Text("\(Double($0) * 0.2 * 100, specifier: "%.0f")%"),
                             alignment: .bottom)
                    .border(Color.gray)
            }
        }
    }
}


See Also
Transforming colors
func contrast(Double) -> some View
Sets the contrast and separation between similar colors in this view.
func colorInvert() -> some View
Inverts the colors in this view.

**Examples:**

```swift
nonisolated
func brightness(_ amount: Double) -> some View
```

```swift
nonisolated
func brightness(_ amount: Double) -> some View
```

```swift
struct Brightness: View {
    var body: some View {
        HStack {
            ForEach(0..<6) {
                Color.red.frame(width: 60, height: 60, alignment: .center)
                    .brightness(Double($0) * 0.2)
                    .overlay(Text("\(Double($0) * 0.2 * 100, specifier: "%.0f")%"),
                             alignment: .bottom)
                    .border(Color.gray)
            }
        }
    }
}
```

```swift
struct Brightness: View {
    var body: some View {
        HStack {
            ForEach(0..<6) {
                Color.red.frame(width: 60, height: 60, alignment: .center)
                    .brightness(Double($0) * 0.2)
                    .overlay(Text("\(Double($0) * 0.2 * 100, specifier: "%.0f")%"),
                             alignment: .bottom)
                    .border(Color.gray)
            }
        }
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/view/brightness(_:))

---

### contrast(_:)

SwiftUI
View
contrast(_:)
Instance Method
contrast(_:)
Sets the contrast and separation between similar colors in this view.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
nonisolated
func contrast(_ amount: Double) -> some View

Parameters
amount

The intensity of color contrast to apply. negative values invert colors in addition to applying contrast.

Return Value

A view that applies color contrast to this view.

Discussion

Apply contrast to a view to increase or decrease the separation between similar colors in the view.

In the example below, the contrast(_:) modifier is applied to a set of red squares each containing a contrasting green inner circle. At each step in the loop, the contrast(_:) modifier changes the contrast of the circle/square view in 20% increments. This ranges from -20% contrast (yielding inverted colors — turning the red square to pale-green and the green circle to mauve), to neutral-gray at 0%, to 100% contrast (bright-red square / bright-green circle). Applying negative contrast values, as shown in the -20% square, will apply contrast in addition to inverting colors.

struct CircleView: View {
    var body: some View {
        Circle()
            .fill(Color.green)
            .frame(width: 25, height: 25, alignment: .center)
    }
}


struct Contrast: View {
    var body: some View {
        HStack {
            ForEach(-1..<6) {
                Color.red.frame(width: 50, height: 50, alignment: .center)
                    .overlay(CircleView(), alignment: .center)
                    .contrast(Double($0) * 0.2)
                    .overlay(Text("\(Double($0) * 0.2 * 100, specifier: "%.0f")%")
                                 .font(.callout),
                             alignment: .bottom)

**Examples:**

```swift
nonisolated
func contrast(_ amount: Double) -> some View
```

```swift
nonisolated
func contrast(_ amount: Double) -> some View
```

```swift
struct CircleView: View {
    var body: some View {
        Circle()
            .fill(Color.green)
            .frame(width: 25, height: 25, alignment: .center)
    }
}


struct Contrast: View {
    var body: some View {
        HStack {
            ForEach(-1..<6) {
                Color.red.frame(width: 50, height: 50, alignment: .center)
                    .overlay(CircleView(), alignment: .center)
                    .contrast(Double($0) * 0.2)
                    .overlay(Text("\(Double($0) * 0.2 * 100, specifier: "%.0f")%")
                                 .font(.callout),
                             alignment: .bottom)
                    .border(Color.gray)
            }
        }
    }
}
```

```swift
struct CircleView: View {
    var body: some View {
        Circle()
            .fill(Color.green)
            .frame(width: 25, height: 25, alignment: .center)
    }
}


struct Contrast: View {
    var body: some View {
        HStack {
            ForEach(-1..<6) {
                Color.red.frame(width: 50, height: 50, alignment: .center)
                    .overlay(CircleView(), alignment: .center)
                    .contrast(Double($0) * 0.2)
                    .overlay(Text("\(Double($0) * 0.2 * 100, specifier: "%.0f")%")
                                 .font(.callout),
                             alignment: .bottom)
                    .border(Color.gray)
            }
        }
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/view/contrast(_:))

---

### saturation(_:)

SwiftUI
View
saturation(_:)
Instance Method
saturation(_:)
Adjusts the color saturation of this view.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
nonisolated
func saturation(_ amount: Double) -> some View

Parameters
amount

The amount of saturation to apply to this view.

Return Value

A view that adjusts the saturation of this view.

Discussion

Use color saturation to increase or decrease the intensity of colors in a view.

The example below shows a series of red squares with their saturation increasing from 0 (gray) to 100% (fully-red) in 20% increments:

struct Saturation: View {
    var body: some View {
        HStack {
            ForEach(0..<6) {
                Color.red.frame(width: 60, height: 60, alignment: .center)
                    .saturation(Double($0) * 0.2)
                    .overlay(Text("\(Double($0) * 0.2 * 100, specifier: "%.0f")%"),
                             alignment: .bottom)
                    .border(Color.gray)
            }
        }
    }
}


See Also

contrast(_:)


**Examples:**

```swift
nonisolated
func saturation(_ amount: Double) -> some View
```

```swift
nonisolated
func saturation(_ amount: Double) -> some View
```

```swift
struct Saturation: View {
    var body: some View {
        HStack {
            ForEach(0..<6) {
                Color.red.frame(width: 60, height: 60, alignment: .center)
                    .saturation(Double($0) * 0.2)
                    .overlay(Text("\(Double($0) * 0.2 * 100, specifier: "%.0f")%"),
                             alignment: .bottom)
                    .border(Color.gray)
            }
        }
    }
}
```

```swift
struct Saturation: View {
    var body: some View {
        HStack {
            ForEach(0..<6) {
                Color.red.frame(width: 60, height: 60, alignment: .center)
                    .saturation(Double($0) * 0.2)
                    .overlay(Text("\(Double($0) * 0.2 * 100, specifier: "%.0f")%"),
                             alignment: .bottom)
                    .border(Color.gray)
            }
        }
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/view/saturation(_:))

---

### grayscale(_:)

SwiftUI
View
grayscale(_:)
Instance Method
grayscale(_:)
Adds a grayscale effect to this view.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
nonisolated
func grayscale(_ amount: Double) -> some View

Parameters
amount

The intensity of grayscale to apply from 0.0 to less than 1.0. Values closer to 0.0 are more colorful, and values closer to 1.0 are less colorful.

Return Value

A view that adds a grayscale effect to this view.

Discussion

A grayscale effect reduces the intensity of colors in this view.

The example below shows a series of red squares with their grayscale effect increasing from 0 (reddest) to 99% (fully desaturated) in approximate 20% increments:

struct Saturation: View {
    var body: some View {
        HStack {
            ForEach(0..<6) {
                Color.red.frame(width: 60, height: 60, alignment: .center)
                    .grayscale(Double($0) * 0.1999)
                    .overlay(Text("\(Double($0) * 0.1999 * 100, specifier: "%.4f")%"),
                             alignment: .bottom)
                    .border(Color.gray)
            }
        }
    }
}


See Also
Transforming colors
func brightness(Double) -> some View
Brightens this view by the specified amount.

**Examples:**

```swift
nonisolated
func grayscale(_ amount: Double) -> some View
```

```swift
nonisolated
func grayscale(_ amount: Double) -> some View
```

```swift
struct Saturation: View {
    var body: some View {
        HStack {
            ForEach(0..<6) {
                Color.red.frame(width: 60, height: 60, alignment: .center)
                    .grayscale(Double($0) * 0.1999)
                    .overlay(Text("\(Double($0) * 0.1999 * 100, specifier: "%.4f")%"),
                             alignment: .bottom)
                    .border(Color.gray)
            }
        }
    }
}
```

```swift
struct Saturation: View {
    var body: some View {
        HStack {
            ForEach(0..<6) {
                Color.red.frame(width: 60, height: 60, alignment: .center)
                    .grayscale(Double($0) * 0.1999)
                    .overlay(Text("\(Double($0) * 0.1999 * 100, specifier: "%.4f")%"),
                             alignment: .bottom)
                    .border(Color.gray)
            }
        }
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/view/grayscale(_:))

---

## Transforms

### rotationEffect(_:anchor:)

SwiftUI
View
rotationEffect(_:anchor:)
Instance Method
rotationEffect(_:anchor:)
Rotates a view’s rendered output in two dimensions around the specified point.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
nonisolated
func rotationEffect(
    _ angle: Angle,
    anchor: UnitPoint = .center
) -> some View

Parameters
angle

The angle by which to rotate the view.

anchor

A unit point within the view about which to perform the rotation. The default value is center.

Return Value

A view with rotated content.

Discussion

This modifier rotates the view’s content around the axis that points out of the xy-plane. It has no effect on the view’s frame. The following code rotates text by 22˚ and then draws a border around the modified view to show that the frame remains unchanged by the rotation modifier:

Text("Rotation by passing an angle in degrees")
    .rotationEffect(.degrees(22))
    .border(Color.gray)


See Also
Scaling, rotating, or transforming a view
func scaledToFill() -> some View
Scales this view to fill its parent.
func scaledToFit() -> some View
Scales this view to fit its parent.
func scaleEffect(_:anchor:)
Scales this view’s rendered output by the given amount in both the horizontal and vertical directions, relative to an anchor point.
func scaleEffect(_:anchor:)

**Examples:**

```swift
nonisolated
func rotationEffect(
    _ angle: Angle,
    anchor: UnitPoint = .center
) -> some View
```

```swift
nonisolated
func rotationEffect(
    _ angle: Angle,
    anchor: UnitPoint = .center
) -> some View
```

```swift
Text("Rotation by passing an angle in degrees")
    .rotationEffect(.degrees(22))
    .border(Color.gray)
```

```swift
Text("Rotation by passing an angle in degrees")
    .rotationEffect(.degrees(22))
    .border(Color.gray)
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/view/rotationeffect(_:anchor:))

---

### scaleEffect(_:anchor:)

SwiftUI
View
scaleEffect(_:anchor:)
Instance Method
scaleEffect(_:anchor:)
Scales this view’s rendered output by the given amount in both the horizontal and vertical directions, relative to an anchor point.
iOS 13.0+
iPadOS 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
nonisolated
func scaleEffect(
    _ s: CGFloat,
    anchor: UnitPoint = .center
) -> ModifiedContent<Self, _UniformScaleEffect>
Show all declarations
Parameters
s

The amount to scale the view in the view in both the horizontal and vertical directions.

anchor

The anchor point with a default of center that indicates the starting position for the scale operation.

Discussion

Use scaleEffect(_:anchor:) to apply a horizontally and vertically scaling transform to a view.

Image(systemName: "envelope.badge.fill")
    .resizable()
    .frame(width: 100, height: 100, alignment: .center)
    .foregroundColor(Color.red)
    .scaleEffect(2, anchor: .leading)
    .border(Color.gray)


See Also
Scaling, rotating, or transforming a view
func scaledToFill() -> some View
Scales this view to fill its parent.
func scaledToFit() -> some View
Scales this view to fit its parent.
func scaleEffect(x: CGFloat, y: CGFloat, anchor: UnitPoint) -> some View
Scales this view’s rendered output by the given horizontal and vertical amounts, relative to an anchor point.
func scaleEffect(x: CGFloat, y: CGFloat, z: CGFloat, anchor: UnitPoint3D) -> some View
Scales this view by the specified horizontal, vertical, and depth factors, relative to an anchor point.
func aspectRatio(_:contentMode:)

**Examples:**

```swift
nonisolated
func scaleEffect(
    _ s: CGFloat,
    anchor: UnitPoint = .center
) -> ModifiedContent<Self, _UniformScaleEffect>
```

```swift
nonisolated
func scaleEffect(
    _ s: CGFloat,
    anchor: UnitPoint = .center
) -> ModifiedContent<Self, _UniformScaleEffect>
```

```swift
ModifiedContent
```

```swift
Image(systemName: "envelope.badge.fill")
    .resizable()
    .frame(width: 100, height: 100, alignment: .center)
    .foregroundColor(Color.red)
    .scaleEffect(2, anchor: .leading)
    .border(Color.gray)
```

```swift
Image(systemName: "envelope.badge.fill")
    .resizable()
    .frame(width: 100, height: 100, alignment: .center)
    .foregroundColor(Color.red)
    .scaleEffect(2, anchor: .leading)
    .border(Color.gray)
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/view/scaleeffect(_:anchor:))

---

### aspectRatio(_:contentMode:)

SwiftUI
View
aspectRatio(_:contentMode:)
Instance Method
aspectRatio(_:contentMode:)
Constrains this view’s dimensions to the specified aspect ratio.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
nonisolated
func aspectRatio(
    _ aspectRatio: CGFloat? = nil,
    contentMode: ContentMode
) -> some View

Show all declarations
Parameters
aspectRatio

The ratio of width to height to use for the resulting view. Use nil to maintain the current aspect ratio in the resulting view.

contentMode

A flag that indicates whether this view fits or fills the parent context.

Return Value

A view that constrains this view’s dimensions to the aspect ratio of the given size using contentMode as its scaling algorithm.

Mentioned in
Fitting images into available space
Discussion

Use aspectRatio(_:contentMode:) to constrain a view’s dimensions to an aspect ratio specified by a CGFloat using the specified content mode.

If this view is resizable, the resulting view will have aspectRatio as its aspect ratio. In this example, the purple ellipse has a 3:4 width-to-height ratio, and scales to fit its frame:

Ellipse()
    .fill(Color.purple)
    .aspectRatio(0.75, contentMode: .fit)
    .frame(width: 200, height: 200)
    .border(Color(white: 0.75))


See Also
Scaling, rotating, or transforming a view

**Examples:**

```swift
nonisolated
func aspectRatio(
    _ aspectRatio: CGFloat? = nil,
    contentMode: ContentMode
) -> some View
```

```swift
nonisolated
func aspectRatio(
    _ aspectRatio: CGFloat? = nil,
    contentMode: ContentMode
) -> some View
```

```swift
ContentMode
```

```swift
Ellipse()
    .fill(Color.purple)
    .aspectRatio(0.75, contentMode: .fit)
    .frame(width: 200, height: 200)
    .border(Color(white: 0.75))
```

```swift
Ellipse()
    .fill(Color.purple)
    .aspectRatio(0.75, contentMode: .fit)
    .frame(width: 200, height: 200)
    .border(Color(white: 0.75))
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/view/aspectratio(_:contentmode:))

---

