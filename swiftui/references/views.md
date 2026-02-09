# Views

SwiftUI views documentation.

---

## View

SwiftUI
View
Protocol
View
A type that represents part of your app’s user interface and provides modifiers that you use to configure views.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
@MainActor @preconcurrency
protocol View
Mentioned in
Declaring a custom view
Configuring views
Reducing view modifier maintenance
Displaying data in lists
Migrating to the SwiftUI life cycle
Overview

You create custom views by declaring types that conform to the View protocol. Implement the required body computed property to provide the content for your custom view.

struct MyView: View {
    var body: some View {
        Text("Hello, World!")
    }
}


Assemble the view’s body by combining one or more of the built-in views provided by SwiftUI, like the Text instance in the example above, plus other custom views that you define, into a hierarchy of views. For more information about creating custom views, see Declaring a custom view.

The View protocol provides a set of modifiers — protocol methods with default implementations — that you use to configure views in the layout of your app. Modifiers work by wrapping the view instance on which you call them in another view with the specified characteristics, as described in Configuring views. For example, adding the opacity(_:) modifier to a text view returns a new view with some amount of transparency:

Text("Hello, World!")
    .opacity(0.5) // Display partially transparent text.


The complete list of default modifiers provides a large set of controls for managing views. For example, you can fine tune Layout modifiers, add Accessibility modifiers information, and respond to Input and event modifiers. You can also collect groups of default modifiers into new, custom view modifiers for easy reuse.

A type conforming to this protocol inherits @preconcurrency @MainActor isolation from the protocol if the conformance is declared in its original declaration. Isolation to the main actor is the default, but it’s not required. Declare the conformance in an extension to opt-out the isolation.

Topics
Implementing a custom view
var body: Self.Body
The content and behavior of the view.

Required Default implementations provided.

associatedtype Body : View
The type of view representing the body of this view.

Required

func modifier<T>(T) -> ModifiedContent<Self, T>
Applies a modifier to a view and returns a new view.
Previews in Xcode
Generate dynamic, interactive previews of your custom views.
Configuring view elements
Accessibility modifiers
Make your SwiftUI apps accessible to everyone, including people with disabilities.
Appearance modifiers
Configure a view’s foreground and background styles, controls, and visibility.
Text and symbol modifiers
Manage the rendering, selection, and entry of text in your view.
Auxiliary view modifiers
Add and configure supporting views, like toolbars and context menus.
Chart view modifiers
Configure charts that you declare with Swift Charts.
Drawing views
Style modifiers
Apply built-in styles to different types of views.
Layout modifiers
Tell a view how to arrange itself within a view hierarchy by adjusting its size, position, alignment, padding, and so on.
Graphics and rendering modifiers
Affect the way the system draws a view, for example by scaling or masking a view, or by applying graphical effects.
Providing interactivity
Input and event modifiers
Supply actions for a view to perform in response to user input and system events.
Search modifiers
Enable people to search for content in your app.
Presentation modifiers
Define additional views for the view to present under specified conditions.
State modifiers
Access storage and provide child views with configuration data.
Deprecated modifiers
Deprecated modifiers
Review unsupported modifiers and their replacements.
Instance Methods
func accessibilityActions<Content>(category: AccessibilityActionCategory, () -> Content) -> some View
Adds multiple accessibility actions to the view with a specific category. Actions allow assistive technologies, such as VoiceOver, to interact with the view by invoking the action and are grouped by their category. When multiple action modifiers with an equal category are applied to the view, the actions are combined together.
func accessibilityDefaultFocus<Value>(AccessibilityFocusState<Value>.Binding, Value) -> some View
Defines a region in which default accessibility focus is evaluated by assigning a value to a given accessibility focus state binding.
func accessibilityScrollStatus(_:isEnabled:)
Changes the announcement provided by accessibility technologies when a user scrolls a scroll view within this view.
func addOrderToWalletButtonStyle(AddOrderToWalletButtonStyle) -> some View
Sets the button’s style.
func addPassToWalletButtonStyle(AddPassToWalletButtonStyle) -> some View
Sets the style to be used by the button. (see PKAddPassButtonStyle).

**Examples:**

```swift
@MainActor @preconcurrency
protocol View
```

```swift
@MainActor @preconcurrency
protocol View
```

```swift
struct MyView: View {
    var body: some View {
        Text("Hello, World!")
    }
}
```

```swift
struct MyView: View {
    var body: some View {
        Text("Hello, World!")
    }
}
```

```swift
Text("Hello, World!")
    .opacity(0.5) // Display partially transparent text.
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/view)

---

## Text

SwiftUI
Text
Structure
Text
A view that displays one or more lines of read-only text.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
@frozen
struct Text
Mentioned in
Configuring views
Building layouts with stack views
Declaring a custom view
Laying out a simple view
Displaying data in lists
Overview

A text view draws a string in your app’s user interface using a body font that’s appropriate for the current platform. You can choose a different standard font, like title or caption, using the font(_:) view modifier.

Text("Hamlet")
    .font(.title)


If you need finer control over the styling of the text, you can use the same modifier to configure a system font or choose a custom font. You can also apply view modifiers like bold() or italic() to further adjust the formatting.

Text("by William Shakespeare")
    .font(.system(size: 12, weight: .light, design: .serif))
    .italic()


To apply styling within specific portions of the text, you can create the text view from an AttributedString, which in turn allows you to use Markdown to style runs of text. You can mix string attributes and SwiftUI modifiers, with the string attributes taking priority.

let attributedString = try! AttributedString(
    markdown: "_Hamlet_ by William Shakespeare")


var body: some View {
    Text(attributedString)
        .font(.system(size: 12, weight: .light, design: .serif))
}


A text view always uses exactly the amount of space it needs to display its rendered contents, but you can affect the view’s layout. For example, you can use the frame(width:height:alignment:) modifier to propose specific dimensions to the view. If the view accepts the proposal but the text doesn’t fit into the available space, the view uses a combination of wrapping, tightening, scaling, and truncation to make it fit. With a width of 100 points but no constraint on the height, a text view might wrap a long string:

Text("To be, or not to be, that is the question:")
    .frame(width: 100)


Use modifiers like lineLimit(_:), allowsTightening(_:), minimumScaleFactor(_:), and truncationMode(_:) to configure how the view handles space constraints. For example, combining a fixed width and a line limit of 1 results in truncation for text that doesn’t fit in that space:

Text("Brevity is the soul of wit.")
    .frame(width: 100)
    .lineLimit(1)


Localizing strings

If you initialize a text view with a string literal, the view uses the init(_:tableName:bundle:comment:) initializer, which interprets the string as a localization key and searches for the key in the table you specify, or in the default table if you don’t specify one.

Text("pencil") // Searches the default table in the main bundle.


For an app localized in both English and Spanish, the above view displays “pencil” and “lápiz” for English and Spanish users, respectively. If the view can’t perform localization, it displays the key instead. For example, if the same app lacks Danish localization, the view displays “pencil” for users in that locale. Similarly, an app that lacks any localization information displays “pencil” in any locale.

To explicitly bypass localization for a string literal, use the init(verbatim:) initializer.

Text(verbatim: "pencil") // Displays the string "pencil" in any locale.


If you initialize a text view with a variable value, the view uses the init(_:) initializer, which doesn’t localize the string. However, you can request localization by creating a LocalizedStringKey instance first, which triggers the init(_:tableName:bundle:comment:) initializer instead:

// Don't localize a string variable...
Text(writingImplement)


// ...unless you explicitly convert it to a localized string key.
Text(LocalizedStringKey(writingImplement))


When localizing a string variable, you can use the default table by omitting the optional initialization parameters — as in the above example — just like you might for a string literal.

When composing a complex string, where there is a need to assemble multiple pieces of text, use string interpolation:

let name: String = //…
Text("Hello, \(name)")


This would look up the "Hello, %@" localization key in the localized string file and replace the format specifier %@ with the value of name before rendering the text on screen.

Using string interpolation ensures that the text in your app can be localized correctly in all locales, especially in right-to-left languages.

If you desire to style only parts of interpolated text while ensuring that the content can still be localized correctly, interpolate Text or AttributedString:

let name = Text(person.name).bold()
Text("Hello, \(name)")

**Examples:**

```swift
@frozen
struct Text
```

```swift
@frozen
struct Text
```

```swift
Text("Hamlet")
    .font(.title)
```

```swift
Text("Hamlet")
    .font(.title)
```

```swift
Text("by William Shakespeare")
    .font(.system(size: 12, weight: .light, design: .serif))
    .italic()
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/text)

---

## Image

SwiftUI
Image
Structure
Image
A view that displays an image.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
@frozen
struct Image
Mentioned in
Building layouts with stack views
Configuring views
Creating performant scrollable stacks
Displaying data in lists
Fitting images into available space
Overview

Use an Image instance when you want to add images to your SwiftUI app. You can create images from many sources:

Image files in your app’s asset library or bundle. Supported types include PNG, JPEG, HEIC, and more.

Instances of platform-specific image types, like UIImage and NSImage.

A bitmap stored in a Core Graphics CGImage instance.

System graphics from the SF Symbols set.

The following example shows how to load an image from the app’s asset library or bundle and scale it to fit within its container:

Image("Landscape_4")
    .resizable()
    .aspectRatio(contentMode: .fit)
Text("Water wheel")


You can use methods on the Image type as well as standard view modifiers to adjust the size of the image to fit your app’s interface. Here, the Image type’s resizable(capInsets:resizingMode:) method scales the image to fit the current view. Then, the aspectRatio(_:contentMode:) view modifier adjusts this resizing behavior to maintain the image’s original aspect ratio, rather than scaling the x- and y-axes independently to fill all four sides of the view. The article Fitting images into available space shows how to apply scaling, clipping, and tiling to Image instances of different sizes.

An Image is a late-binding token; the system resolves its actual value only when it’s about to use the image in an environment.

Making images accessible

To use an image as a control, use one of the initializers that takes a label parameter. This allows the system’s accessibility frameworks to use the label as the name of the control for users who use features like VoiceOver. For images that are only present for aesthetic reasons, use an initializer with the decorative parameter; the accessibility systems ignore these images.

Topics
Creating an image
init(String, bundle: Bundle?)
Creates a labeled image that you can use as content for controls.
init(String, variableValue: Double?, bundle: Bundle?)
Creates a labeled image that you can use as content for controls, with a variable value.
init(ImageResource)
Initialize an Image with an image resource.
Creating an image for use as a control
init(String, bundle: Bundle?, label: Text)
Creates a labeled image that you can use as content for controls, with the specified label.
init(String, variableValue: Double?, bundle: Bundle?, label: Text)
Creates a labeled image that you can use as content for controls, with the specified label and variable value.
init(CGImage, scale: CGFloat, orientation: Image.Orientation, label: Text)
Creates a labeled image based on a Core Graphics image instance, usable as content for controls.
Creating an image for decorative use
init(decorative: String, bundle: Bundle?)
Creates an unlabeled, decorative image.
init(decorative: String, variableValue: Double?, bundle: Bundle?)
Creates an unlabeled, decorative image, with a variable value.
init(decorative: CGImage, scale: CGFloat, orientation: Image.Orientation)
Creates an unlabeled, decorative image based on a Core Graphics image instance.
Creating a system symbol image
init(systemName: String)
Creates a system symbol image.
init(systemName: String, variableValue: Double?)
Creates a system symbol image with a variable value.
Creating an image from another image
init(uiImage: UIImage)
Creates a SwiftUI image from a UIKit image instance.
init(nsImage: NSImage)
Creates a SwiftUI image from an AppKit image instance.
Creating an image from drawing instructions
init(size: CGSize, label: Text?, opaque: Bool, colorMode: ColorRenderingMode, renderer: (inout GraphicsContext) -> Void)
Initializes an image of the given size, with contents provided by a custom rendering closure.
Resizing images
func resizable(capInsets: EdgeInsets, resizingMode: Image.ResizingMode) -> Image
Sets the mode by which SwiftUI resizes an image to fit its space.
Specifying rendering behavior
func antialiased(Bool) -> Image
Specifies whether SwiftUI applies antialiasing when rendering the image.
func symbolRenderingMode(SymbolRenderingMode?) -> Image
Sets the rendering mode for symbol images within this view.
func renderingMode(Image.TemplateRenderingMode?) -> Image
Indicates whether SwiftUI renders an image as-is, or by using a different mode.
func interpolation(Image.Interpolation) -> Image
Specifies the current level of quality for rendering an image that requires interpolation.
enum TemplateRenderingMode
A type that indicates how SwiftUI renders images.
enum Interpolation
The level of quality for rendering an image that requires interpolation, such as a scaled image.
Specifying dynamic range

**Examples:**

```swift
@frozen
struct Image
```

```swift
@frozen
struct Image
```

```swift
Image("Landscape_4")
    .resizable()
    .aspectRatio(contentMode: .fit)
Text("Water wheel")
```

```swift
Image("Landscape_4")
    .resizable()
    .aspectRatio(contentMode: .fit)
Text("Water wheel")
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/image)

---

## Label

SwiftUI
Label
Structure
Label
A standard label for user interface items, consisting of an icon with a title.
iOS 14.0+
iPadOS 14.0+
Mac Catalyst 14.0+
macOS 11.0+
tvOS 14.0+
visionOS 1.0+
watchOS 7.0+
struct Label<Title, Icon> where Title : View, Icon : View
Mentioned in
Performing a search operation
Populating SwiftUI menus with adaptive controls
Preparing views for localization
Overview

One of the most common and recognizable user interface components is the combination of an icon and a label. This idiom appears across many kinds of apps and shows up in collections, lists, menus of action items, and disclosable lists, just to name a few.

You create a label, in its simplest form, by providing a title and the name of an image, such as an icon from the SF Symbols collection:

Label("Lightning", systemImage: "bolt.fill")


You can also apply styles to labels in several ways. In the case of dynamic changes to the view after device rotation or change to a window size you might want to show only the text portion of the label using the titleOnly label style:

Label("Lightning", systemImage: "bolt.fill")
    .labelStyle(.titleOnly)


Conversely, there’s also an icon-only label style:

Label("Lightning", systemImage: "bolt.fill")
    .labelStyle(.iconOnly)


Some containers might apply a different default label style, such as only showing icons within toolbars on macOS and iOS. To opt in to showing both the title and the icon, you can apply the titleAndIcon label style:

Label("Lightning", systemImage: "bolt.fill")
    .labelStyle(.titleAndIcon)


You can also create a customized label style by modifying an existing style; this example adds a red border to the default label style:

struct RedBorderedLabelStyle: LabelStyle {
    func makeBody(configuration: Configuration) -> some View {
        Label(configuration)
            .border(Color.red)
    }
}


For more extensive customization or to create a completely new label style, you’ll need to adopt the LabelStyle protocol and implement a LabelStyleConfiguration for the new style.

To apply a common label style to a group of labels, apply the style to the view hierarchy that contains the labels:

VStack {
    Label("Rain", systemImage: "cloud.rain")
    Label("Snow", systemImage: "snow")
    Label("Sun", systemImage: "sun.max")
}
.labelStyle(.iconOnly)


It’s also possible to make labels using views to compose the label’s icon programmatically, rather than using a pre-made image. In this example, the icon portion of the label uses a filled Circle overlaid with the user’s initials:

Label {
    Text(person.fullName)
        .font(.body)
        .foregroundColor(.primary)
    Text(person.title)
        .font(.subheadline)
        .foregroundColor(.secondary)
} icon: {
    Circle()
        .fill(person.profileColor)
        .frame(width: 44, height: 44, alignment: .center)
        .overlay(Text(person.initials))
}

Topics
Creating a label
init(_:image:)
Creates a label with an icon image and a title generated from a localized string.
init(_:systemImage:)
Creates a label with a system icon image and a title generated from a localized string.
init(title: () -> Title, icon: () -> Icon)
Creates a label with a custom title and icon.
init(_:)
Creates a label representing a family activity application.
init(_:image:)
Creates a label with an icon image and a title generated from a localized string.
Relationships
Conforms To
View
See Also
Displaying text
struct Text

**Examples:**

```swift
struct Label<Title, Icon> where Title : View, Icon : View
```

```swift
struct Label<Title, Icon> where Title : View, Icon : View
```

```swift
Label("Lightning", systemImage: "bolt.fill")
```

```swift
Label("Lightning", systemImage: "bolt.fill")
```

```swift
Label("Lightning", systemImage: "bolt.fill")
    .labelStyle(.titleOnly)
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/label)

---

## ScrollView

SwiftUI
ScrollView
Structure
ScrollView
A scrollable view.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
struct ScrollView<Content> where Content : View
Mentioned in
Picking container views for your content
Creating performant scrollable stacks
Grouping data with lazy stack views
Overview

The scroll view displays its content within the scrollable content region. As the user performs platform-appropriate scroll gestures, the scroll view adjusts what portion of the underlying content is visible. ScrollView can scroll horizontally, vertically, or both, but does not provide zooming functionality.

In the following example, a ScrollView allows the user to scroll through a VStack containing 100 Text views. The image after the listing shows the scroll view’s temporarily visible scrollbar at the right; you can disable it with the showsIndicators parameter of the ScrollView initializer.

var body: some View {
    ScrollView {
        VStack(alignment: .leading) {
            ForEach(0..<100) {
                Text("Row \($0)")
            }
        }
    }
}


Controlling Scroll Position

You can influence where a scroll view is initially scrolled by using the defaultScrollAnchor(_:) view modifier.

Provide a value of `UnitPoint/center`` to have the scroll view start in the center of its content when a scroll view is scrollable in both axes.

ScrollView([.horizontal, .vertical]) {
    // initially centered content
}
.defaultScrollAnchor(.center)


Or provide an alignment of `UnitPoint/bottom`` to have the scroll view start at the bottom of its content when a scroll view is scrollable in its vertical axes.

ScrollView {
    // initially bottom aligned content
}
.defaultScrollAnchor(.bottom)


After the scroll view initially renders, the user may scroll the content of the scroll view.

To perform programmatic scrolling, wrap one or more scroll views with a ScrollViewReader.

Topics
Creating a scroll view
init(Axis.Set, showsIndicators: Bool, content: () -> Content)
Creates a new instance that’s scrollable in the direction of the given axis and can show indicators while scrolling.
Deprecated
init(Axis.Set, content: () -> Content)
Creates a new instance that’s scrollable in the direction of the given axis and can show indicators while scrolling.
Configuring a scroll view
var content: Content
The scroll view’s content.
var axes: Axis.Set
The scrollable axes of the scroll view.
var showsIndicators: Bool
A value that indicates whether the scroll view displays the scrollable component of the content offset, in a way that’s suitable for the platform.
Supporting types
var body: some View
The content and behavior of the scroll view.
Relationships
Conforms To
View
See Also
Creating a scroll view
struct ScrollViewReader
A view that provides programmatic scrolling, by working with a proxy to scroll to known child views.
struct ScrollViewProxy
A proxy value that supports programmatic scrolling of the scrollable views within a view hierarchy.

**Examples:**

```swift
struct ScrollView<Content> where Content : View
```

```swift
struct ScrollView<Content> where Content : View
```

```swift
var body: some View {
    ScrollView {
        VStack(alignment: .leading) {
            ForEach(0..<100) {
                Text("Row \($0)")
            }
        }
    }
}
```

```swift
var body: some View {
    ScrollView {
        VStack(alignment: .leading) {
            ForEach(0..<100) {
                Text("Row \($0)")
            }
        }
    }
}
```

```swift
ScrollView([.horizontal, .vertical]) {
    // initially centered content
}
.defaultScrollAnchor(.center)
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/scrollview)

---

## Color

SwiftUI
Color
Structure
Color
A representation of a color that adapts to a given context.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
@frozen
struct Color
Mentioned in
Laying out a simple view
Overview

You can create a color in one of several ways:

Load a color from an Asset Catalog:

let aqua = Color("aqua") // Looks in your app's main bundle by default.


Specify component values, like red, green, and blue; hue, saturation, and brightness; or white level:

let skyBlue = Color(red: 0.4627, green: 0.8392, blue: 1.0)
let lemonYellow = Color(hue: 0.1639, saturation: 1, brightness: 1)
let steelGray = Color(white: 0.4745)


Create a color instance from another color, like a UIColor or an NSColor:

#if os(iOS)
let linkColor = Color(uiColor: .link)
#elseif os(macOS)
let linkColor = Color(nsColor: .linkColor)
#endif


Use one of a palette of predefined colors, like black, green, and purple.

Some view modifiers can take a color as an argument. For example, foregroundStyle(_:) uses the color you provide to set the foreground color for view elements, like text or SF Symbols:

Image(systemName: "leaf.fill")
    .foregroundStyle(Color.green)


Because SwiftUI treats colors as View instances, you can also directly add them to a view hierarchy. For example, you can layer a rectangle beneath a sun image using colors defined above:

ZStack {
    skyBlue
    Image(systemName: "sun.max.fill")
        .foregroundStyle(lemonYellow)
}
.frame(width: 200, height: 100)


A color used as a view expands to fill all the space it’s given, as defined by the frame of the enclosing ZStack in the above example:

SwiftUI only resolves a color to a concrete value just before using it in a given environment. This enables a context-dependent appearance for system defined colors, or those that you load from an Asset Catalog. For example, a color can have distinct light and dark variants that the system chooses from at render time.

Topics
Creating a color
init(String, bundle: Bundle?)
Creates a color from a color set that you indicate by name.
init(_:)
Creates a constant color with the values specified by the resolved color.
func resolve(in: EnvironmentValues) -> Color.Resolved
Evaluates this color to a resolved color given the current context.
Creating a color from component values
init(hue: Double, saturation: Double, brightness: Double, opacity: Double)
Creates a constant color from hue, saturation, and brightness values.
init(Color.RGBColorSpace, white: Double, opacity: Double)
Creates a constant grayscale color.
init(Color.RGBColorSpace, red: Double, green: Double, blue: Double, opacity: Double)
Creates a constant color from red, green, and blue component values.
enum RGBColorSpace
A profile that specifies how to interpret a color value for display.
Creating a color from another color
init(uiColor: UIColor)
Creates a color from a UIKit color.
init(nsColor: NSColor)
Creates a color from an AppKit color.
init(cgColor: CGColor)
Creates a color from a Core Graphics color.
Getting standard colors
static let black: Color
A black color suitable for use in UI elements.
static let blue: Color
A context-dependent blue color suitable for use in UI elements.
static let brown: Color
A context-dependent brown color suitable for use in UI elements.
static let clear: Color
A clear color suitable for use in UI elements.
static let cyan: Color
A context-dependent cyan color suitable for use in UI elements.
static let gray: Color
A context-dependent gray color suitable for use in UI elements.

**Examples:**

```swift
@frozen
struct Color
```

```swift
@frozen
struct Color
```

```swift
let aqua = Color("aqua") // Looks in your app's main bundle by default.
```

```swift
let aqua = Color("aqua") // Looks in your app's main bundle by default.
```

```swift
let skyBlue = Color(red: 0.4627, green: 0.8392, blue: 1.0)
let lemonYellow = Color(hue: 0.1639, saturation: 1, brightness: 1)
let steelGray = Color(white: 0.4745)
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/color)

---

## Shape

SwiftUI
Shape
Protocol
Shape
A 2D shape that you can use when drawing a view.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
protocol Shape : Sendable, Animatable, View, _RemoveGlobalActorIsolation
Overview

Shapes without an explicit fill or stroke get a default fill based on the foreground color.

You can define shapes in relation to an implicit frame of reference, such as the natural size of the view that contains it. Alternatively, you can define shapes in terms of absolute coordinates.

Topics
Getting standard shapes
static var buttonBorder: ButtonBorderShape
A shape that defers to the environment to determine the resolved button border shape.
static var capsule: Capsule
A capsule shape aligned inside the frame of the view containing it.
static func capsule(style: RoundedCornerStyle) -> Self
A capsule shape aligned inside the frame of the view containing it.
static var circle: Circle
A circle centered on the frame of the view containing it.
static var containerRelative: ContainerRelativeShape
A shape that is replaced by an inset version of the current container shape. If no container shape was defined, is replaced by a rectangle.
static var ellipse: Ellipse
An ellipse aligned inside the frame of the view containing it.
static var rect: Rectangle
A rectangular shape aligned inside the frame of the view containing it.
static func rect(cornerRadii: RectangleCornerRadii, style: RoundedCornerStyle) -> Self
A rectangular shape with rounded corners with different values, aligned inside the frame of the view containing it.
static func rect(cornerRadius: CGFloat, style: RoundedCornerStyle) -> Self
A rectangular shape with rounded corners, aligned inside the frame of the view containing it.
static func rect(cornerSize: CGSize, style: RoundedCornerStyle) -> Self
A rectangular shape with rounded corners, aligned inside the frame of the view containing it.
static func rect(topLeadingRadius: CGFloat, bottomLeadingRadius: CGFloat, bottomTrailingRadius: CGFloat, topTrailingRadius: CGFloat, style: RoundedCornerStyle) -> Self
A rectangular shape with rounded corners with different values, aligned inside the frame of the view containing it.
Defining a shape’s size and path
func sizeThatFits(ProposedViewSize) -> CGSize
Returns the size of the view that will render the shape, given a proposed size.

Required Default implementation provided.

func path(in: CGRect) -> Path
Describes this shape as a path within a rectangular frame of reference.

Required

Transforming a shape
func trim(from: CGFloat, to: CGFloat) -> some Shape
Trims this shape by a fractional amount based on its representation as a path.
func transform(CGAffineTransform) -> TransformedShape<Self>
Applies an affine transform to this shape.
func size(CGSize) -> some Shape
Returns a new version of self representing the same shape, but that will ask it to create its path from a rect of size. This does not affect the layout properties of any views created from the shape (e.g. by filling it).
func size(width: CGFloat, height: CGFloat) -> some Shape
Returns a new version of self representing the same shape, but that will ask it to create its path from a rect of size (width, height). This does not affect the layout properties of any views created from the shape (e.g. by filling it).
func scale(CGFloat, anchor: UnitPoint) -> ScaledShape<Self>
Scales this shape without changing its bounding frame.
func scale(x: CGFloat, y: CGFloat, anchor: UnitPoint) -> ScaledShape<Self>
Scales this shape without changing its bounding frame.
func rotation(Angle, anchor: UnitPoint) -> RotatedShape<Self>
Rotates this shape around an anchor point at the angle you specify.
func offset(_:)
Changes the relative position of this shape using the specified point.
func offset(x: CGFloat, y: CGFloat) -> OffsetShape<Self>
Changes the relative position of this shape using the specified point.
Setting the stroke characteristics
func stroke<S>(S, lineWidth: CGFloat) -> some View
Traces the outline of this shape with a color or gradient.
func stroke<S>(S, lineWidth: CGFloat, antialiased: Bool) -> StrokeShapeView<Self, S, EmptyView>
Traces the outline of this shape with a color or gradient.
func stroke(lineWidth: CGFloat) -> some Shape
Returns a new shape that is a stroked copy of self with line-width defined by lineWidth and all other properties of StrokeStyle having their default values.
func stroke<S>(S, style: StrokeStyle) -> some View
Traces the outline of this shape with a color or gradient.
func stroke<S>(S, style: StrokeStyle, antialiased: Bool) -> StrokeShapeView<Self, S, EmptyView>
Traces the outline of this shape with a color or gradient.
func stroke(style: StrokeStyle) -> some Shape
Returns a new shape that is a stroked copy of self, using the contents of style to define the stroke characteristics.
Filling a shape
func fill(_:style:)
Fills this shape with a color or gradient.
func fill(style: FillStyle) -> some View
Fills this shape with the foreground color.
Setting the role
static var role: ShapeRole
An indication of how to style a shape.

Required Default implementation provided.

Indicating a layout direction
var layoutDirectionBehavior: LayoutDirectionBehavior
Returns the behavior this shape should use for different layout directions.

**Examples:**

```swift
protocol Shape : Sendable, Animatable, View, _RemoveGlobalActorIsolation
```

```swift
protocol Shape : Sendable, Animatable, View, _RemoveGlobalActorIsolation
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/shape)

---

## Rectangle

SwiftUI
Rectangle
Structure
Rectangle
A rectangular shape aligned inside the frame of the view containing it.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
@frozen
struct Rectangle
Topics
Creating a rectangle
init()
Creates a new rectangle shape.
Relationships
Conforms To
Animatable
BitwiseCopyable
Copyable
InsettableShape
RoundedRectangularShape
Sendable
SendableMetatype
Shape
View
See Also
Creating rectangular shapes
struct RoundedRectangle
A rectangular shape with rounded corners, aligned inside the frame of the view containing it.
enum RoundedCornerStyle
Defines the shape of a rounded rectangle’s corners.
protocol RoundedRectangularShape
A protocol of InsettableShape that describes a rounded rectangular shape.
struct RoundedRectangularShapeCorners
A type describing the corner styles of a RoundedRectangularShape.
struct UnevenRoundedRectangle
A rectangular shape with rounded corners with different values, aligned inside the frame of the view containing it.
struct RectangleCornerRadii
Describes the corner radius values of a rounded rectangle with uneven corners.
struct RectangleCornerInsets
The inset sizes for the corners of a rectangle.
struct ConcentricRectangle
A shape that is replaced by a concentric version of the current container shape. If the container shape is a rectangle derived shape with four corners, this shape could choose to respect corners individually.

**Examples:**

```swift
@frozen
struct Rectangle
```

```swift
@frozen
struct Rectangle
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/rectangle)

---

## Circle

SwiftUI
Circle
Structure
Circle
A circle centered on the frame of the view containing it.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
@frozen
struct Circle
Mentioned in
Laying out a simple view
Applying Liquid Glass to custom views
Overview

The circle’s radius equals half the length of the frame rectangle’s smallest edge.

Topics
Creating a circle
init()
Creates a new circle shape.
Relationships
Conforms To
Animatable
BitwiseCopyable
ChartSymbolShape
Copyable
InsettableShape
RoundedRectangularShape
Sendable
SendableMetatype
Shape
View
See Also
Creating circular shapes
struct Ellipse
An ellipse aligned inside the frame of the view containing it.
struct Capsule
A capsule shape aligned inside the frame of the view containing it.

**Examples:**

```swift
@frozen
struct Circle
```

```swift
@frozen
struct Circle
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/circle)

---

## RoundedRectangle

SwiftUI
RoundedRectangle
Structure
RoundedRectangle
A rectangular shape with rounded corners, aligned inside the frame of the view containing it.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
@frozen
struct RoundedRectangle
Topics
Creating a rounded rectangle
init(cornerRadius: CGFloat, style: RoundedCornerStyle)
Creates a new rounded rectangle shape.
init(cornerSize: CGSize, style: RoundedCornerStyle)
Creates a new rounded rectangle shape.
Getting the shape’s characteristics
var cornerSize: CGSize
The width and height of the rounded rectangle’s corners.
var style: RoundedCornerStyle
The style of corners drawn by the rounded rectangle.
Supporting types
var animatableData: CGSize.AnimatableData
The data to animate.
Relationships
Conforms To
Animatable
Copyable
InsettableShape
RoundedRectangularShape
Sendable
SendableMetatype
Shape
View
See Also
Creating rectangular shapes
struct Rectangle
A rectangular shape aligned inside the frame of the view containing it.
enum RoundedCornerStyle
Defines the shape of a rounded rectangle’s corners.
protocol RoundedRectangularShape
A protocol of InsettableShape that describes a rounded rectangular shape.
struct RoundedRectangularShapeCorners
A type describing the corner styles of a RoundedRectangularShape.
struct UnevenRoundedRectangle
A rectangular shape with rounded corners with different values, aligned inside the frame of the view containing it.
struct RectangleCornerRadii
Describes the corner radius values of a rounded rectangle with uneven corners.
struct RectangleCornerInsets
The inset sizes for the corners of a rectangle.
struct ConcentricRectangle
A shape that is replaced by a concentric version of the current container shape. If the container shape is a rectangle derived shape with four corners, this shape could choose to respect corners individually.

**Examples:**

```swift
@frozen
struct RoundedRectangle
```

```swift
@frozen
struct RoundedRectangle
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/roundedrectangle)

---

## Capsule

SwiftUI
Capsule
Structure
Capsule
A capsule shape aligned inside the frame of the view containing it.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
@frozen
struct Capsule
Mentioned in
Applying Liquid Glass to custom views
Overview

A capsule shape is equivalent to a rounded rectangle where the corner radius is chosen as half the length of the rectangle’s smallest edge.

Topics
Creating a capsule
init(style: RoundedCornerStyle)
Creates a new capsule shape.
Getting the shape’s characteristics
var style: RoundedCornerStyle
Relationships
Conforms To
Animatable
Copyable
InsettableShape
RoundedRectangularShape
Sendable
SendableMetatype
Shape
View
See Also
Creating circular shapes
struct Circle
A circle centered on the frame of the view containing it.
struct Ellipse
An ellipse aligned inside the frame of the view containing it.

**Examples:**

```swift
@frozen
struct Capsule
```

```swift
@frozen
struct Capsule
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/capsule)

---

## Ellipse

SwiftUI
Ellipse
Structure
Ellipse
An ellipse aligned inside the frame of the view containing it.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
@frozen
struct Ellipse
Topics
Creating an ellipse
init()
Creates a new ellipse shape.
Relationships
Conforms To
Animatable
BitwiseCopyable
Copyable
InsettableShape
Sendable
SendableMetatype
Shape
View
See Also
Creating circular shapes
struct Circle
A circle centered on the frame of the view containing it.
struct Capsule
A capsule shape aligned inside the frame of the view containing it.

**Examples:**

```swift
@frozen
struct Ellipse
```

```swift
@frozen
struct Ellipse
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/ellipse)

---

## TextField

SwiftUI
TextField
Structure
TextField
A control that displays an editable text interface.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
struct TextField<Label> where Label : View
Overview

You create a text field with a label and a binding to a value. If the value is a string, the text field updates this value continuously as the user types or otherwise edits the text in the field. For non-string types, it updates the value when the user commits their edits, such as by pressing the Return key.

The following example shows a text field to accept a username, and a Text view below it that shadows the continuously updated value of username. The Text view changes color as the user begins and ends editing. When the user submits their completed entry to the text field, the onSubmit(of:_:) modifier calls an internal validate(name:) method.

@State private var username: String = ""
@FocusState private var emailFieldIsFocused: Bool = false


var body: some View {
    TextField(
        "User name (email address)",
        text: $username
    )
    .focused($emailFieldIsFocused)
    .onSubmit {
        validate(name: username)
    }
    .textInputAutocapitalization(.never)
    .disableAutocorrection(true)
    .border(.secondary)


    Text(username)
        .foregroundColor(emailFieldIsFocused ? .red : .blue)
}


The bound value doesn’t have to be a string. By using a FormatStyle, you can bind the text field to a nonstring type, using the format style to convert the typed text into an instance of the bound type. The following example uses a PersonNameComponents.FormatStyle to convert the name typed in the text field to a PersonNameComponents instance. A Text view below the text field shows the debug description string of this instance.

@State private var nameComponents = PersonNameComponents()


var body: some View {
    TextField(
        "Proper name",
        value: $nameComponents,
        format: .name(style: .medium)
    )
    .onSubmit {
        validate(components: nameComponents)
    }
    .disableAutocorrection(true)
    .border(.secondary)
    Text(nameComponents.debugDescription)
}


Text field prompts

You can set an explicit prompt on the text field to guide users on what text they should provide. Each text field style determines where and when the text field uses a prompt and label. For example, a form on macOS always places the label at the leading edge of the field and uses a prompt, when available, as placeholder text within the field itself. In the same context on iOS, the text field uses either the prompt or label as placeholder text, depending on whether the initializer provided a prompt.

The following example shows a Form with two text fields, each of which provides a prompt to indicate that the field is required, and a view builder to provide a label:

Form {
    TextField(text: $username, prompt: Text("Required")) {
        Text("Username")
    }
    SecureField(text: $password, prompt: Text("Required")) {
        Text("Password")
    }
}


Styling text fields

SwiftUI provides a default text field style that reflects an appearance and behavior appropriate to the platform. The default style also takes the current context into consideration, like whether the text field is in a container that presents text fields with a special style. Beyond this, you can customize the appearance and interaction of text fields using the textFieldStyle(_:) modifier, passing in an instance of TextFieldStyle. The following example applies the roundedBorder style to both text fields within a VStack.

@State private var givenName: String = ""
@State private var familyName: String = ""


var body: some View {
    VStack {
        TextField(
            "Given Name",
            text: $givenName
        )
        .disableAutocorrection(true)
        TextField(
            "Family Name",
            text: $familyName
        )
        .disableAutocorrection(true)
    }
    .textFieldStyle(.roundedBorder)

**Examples:**

```swift
struct TextField<Label> where Label : View
```

```swift
struct TextField<Label> where Label : View
```

```swift
@State private var username: String = ""
@FocusState private var emailFieldIsFocused: Bool = false


var body: some View {
    TextField(
        "User name (email address)",
        text: $username
    )
    .focused($emailFieldIsFocused)
    .onSubmit {
        validate(name: username)
    }
    .textInputAutocapitalization(.never)
    .disableAutocorrection(true)
    .border(.secondary)


    Text(username)
        .foregroundColor(emailFieldIsFocused ? .red : .blue)
}
```

```swift
@State private var username: String = ""
@FocusState private var emailFieldIsFocused: Bool = false


var body: some View {
    TextField(
        "User name (email address)",
        text: $username
    )
    .focused($emailFieldIsFocused)
    .onSubmit {
        validate(name: username)
    }
    .textInputAutocapitalization(.never)
    .disableAutocorrection(true)
    .border(.secondary)


    Text(username)
        .foregroundColor(emailFieldIsFocused ? .red : .blue)
}
```

```swift
@State private var nameComponents = PersonNameComponents()


var body: some View {
    TextField(
        "Proper name",
        value: $nameComponents,
        format: .name(style: .medium)
    )
    .onSubmit {
        validate(components: nameComponents)
    }
    .disableAutocorrection(true)
    .border(.secondary)
    Text(nameComponents.debugDescription)
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/textfield)

---

## TextEditor

SwiftUI
TextEditor
Structure
TextEditor
A view that can display and edit long-form text.
iOS 14.0+
iPadOS 14.0+
Mac Catalyst 14.0+
macOS 11.0+
visionOS 1.0+
struct TextEditor
Overview

A text editor view allows you to display and edit multiline, scrollable text in your app’s user interface. By default, the text editor view styles the text using characteristics inherited from the environment, like font(_:), foregroundColor(_:), and multilineTextAlignment(_:).

You create a text editor by adding a TextEditor instance to the body of your view, and initialize it by passing in a Binding to a string variable in your app:

struct TextEditingView: View {
    @State private var fullText: String = "This is some editable text..."


    var body: some View {
        TextEditor(text: $fullText)
    }
}


To style the text, use the standard view modifiers to configure a system font, set a custom font, or change the color of the view’s text.

In this example, the view renders the editor’s text in gray with a custom font:

struct TextEditingView: View {
    @State private var fullText: String = "This is some editable text..."


    var body: some View {
        TextEditor(text: $fullText)
            .foregroundColor(Color.gray)
            .font(.custom("HelveticaNeue", size: 13))
    }
}


If you want to change the spacing or font scaling aspects of the text, you can use modifiers like lineLimit(_:), lineSpacing(_:), and minimumScaleFactor(_:) to configure how the view displays text depending on the space constraints. For example, here the lineSpacing(_:) modifier sets the spacing between lines to 5 points:

struct TextEditingView: View {
    @State private var fullText: String = "This is some editable text..."


    var body: some View {
        TextEditor(text: $fullText)
            .foregroundColor(Color.gray)
            .font(.custom("HelveticaNeue", size: 13))
            .lineSpacing(5)
    }
}

Topics
Creating a text editor
init(text: Binding<String>)
Creates a plain text editor.
Initializers
init(text:selection:)
Creates a styled text editor.
Relationships
Conforms To
View
See Also
Getting text input
Building rich SwiftUI text experiences
Build an editor for formatted text using SwiftUI text editor views and attributed strings.
struct TextField
A control that displays an editable text interface.
func textFieldStyle<S>(S) -> some View
Sets the style for text fields within this view.
struct SecureField
A control into which people securely enter private text.

**Examples:**

```swift
struct TextEditor
```

```swift
struct TextEditor
```

```swift
struct TextEditingView: View {
    @State private var fullText: String = "This is some editable text..."


    var body: some View {
        TextEditor(text: $fullText)
    }
}
```

```swift
struct TextEditingView: View {
    @State private var fullText: String = "This is some editable text..."


    var body: some View {
        TextEditor(text: $fullText)
    }
}
```

```swift
struct TextEditingView: View {
    @State private var fullText: String = "This is some editable text..."


    var body: some View {
        TextEditor(text: $fullText)
            .foregroundColor(Color.gray)
            .font(.custom("HelveticaNeue", size: 13))
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/texteditor)

---

## ColorPicker

SwiftUI
ColorPicker
Structure
ColorPicker
A control used to select a color from the system color picker UI.
iOS 14.0+
iPadOS 14.0+
Mac Catalyst 14.0+
macOS 11.0+
visionOS 1.0+
struct ColorPicker<Label> where Label : View
Overview

The color picker shows the currently selected color and displays the larger system color picker that allows people to select a new color.

By default color picker supports colors with opacity; to disable opacity support, set the supportsOpacity parameter to false. In this mode the color picker won’t show controls for adjusting the opacity of the selected color, and strips out opacity from any color set programmatically or selected from the user’s system favorites.

You use ColorPicker by embedding it inside a view hierarchy and initializing it with a title string and a Binding to a Color:

struct FormattingControls: View {
    @State private var bgColor =
        Color(.sRGB, red: 0.98, green: 0.9, blue: 0.2)


    var body: some View {
        VStack {
            ColorPicker("Alignment Guides", selection: $bgColor)
        }
    }
}

Topics
Creating a color picker
init(_:selection:supportsOpacity:)
Creates a color picker with a text label generated from a title string key.
init(selection:supportsOpacity:label:)
Creates an instance that selects a color.
Relationships
Conforms To
View

**Examples:**

```swift
struct ColorPicker<Label> where Label : View
```

```swift
struct ColorPicker<Label> where Label : View
```

```swift
struct FormattingControls: View {
    @State private var bgColor =
        Color(.sRGB, red: 0.98, green: 0.9, blue: 0.2)


    var body: some View {
        VStack {
            ColorPicker("Alignment Guides", selection: $bgColor)
        }
    }
}
```

```swift
struct FormattingControls: View {
    @State private var bgColor =
        Color(.sRGB, red: 0.98, green: 0.9, blue: 0.2)


    var body: some View {
        VStack {
            ColorPicker("Alignment Guides", selection: $bgColor)
        }
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/colorpicker)

---

## ProgressView

SwiftUI
ProgressView
Structure
ProgressView
A view that shows the progress toward completion of a task.
iOS 14.0+
iPadOS 14.0+
Mac Catalyst 14.0+
macOS 11.0+
tvOS 14.0+
visionOS 1.0+
watchOS 7.0+
struct ProgressView<Label, CurrentValueLabel> where Label : View, CurrentValueLabel : View
Mentioned in
Declaring a custom view
Overview

Use a progress view to show that a task is incomplete but advancing toward completion. A progress view can show both determinate (percentage complete) and indeterminate (progressing or not) types of progress.

Create a determinate progress view by initializing a ProgressView with a binding to a numeric value that indicates the progress, and a total value that represents completion of the task. By default, the progress is 0.0 and the total is 1.0.

The example below uses the state property progress to show progress in a determinate ProgressView. The progress view uses its default total of 1.0, and because progress starts with an initial value of 0.5, the progress view begins half-complete. A “More” button below the progress view allows people to increment the progress in increments of five percent:

struct LinearProgressDemoView: View {
    @State private var progress = 0.5


    var body: some View {
        VStack {
            ProgressView(value: progress)
            Button("More") { progress += 0.05 }
        }
    }
}


To create an indeterminate progress view, use an initializer that doesn’t take a progress value:

var body: some View {
    ProgressView()
}


You can also create a progress view that covers a closed range of Date values. As long as the current date is within the range, the progress view automatically updates, filling or depleting the progress view as it nears the end of the range. The following example shows a five-minute timer whose start time is that of the progress view’s initialization:

struct DateRelativeProgressDemoView: View {
    let workoutDateRange = Date()...Date().addingTimeInterval(5*60)


    var body: some View {
         ProgressView(timerInterval: workoutDateRange) {
             Text("Workout")
         }
    }
}


Styling progress views

You can customize the appearance and interaction of progress views by creating styles that conform to the ProgressViewStyle protocol. To set a specific style for all progress view instances within a view, use the progressViewStyle(_:) modifier. In the following example, a custom style adds a rounded pink border to all progress views within the enclosing VStack:

struct BorderedProgressViews: View {
    var body: some View {
        VStack {
            ProgressView(value: 0.25) { Text("25% progress") }
            ProgressView(value: 0.75) { Text("75% progress") }
        }
        .progressViewStyle(PinkBorderedProgressViewStyle())
    }
}


struct PinkBorderedProgressViewStyle: ProgressViewStyle {
    func makeBody(configuration: Configuration) -> some View {
        ProgressView(configuration)
            .padding(4)
            .border(.pink, width: 3)
            .cornerRadius(4)
    }
}


SwiftUI provides two built-in progress view styles, linear and circular, as well as an automatic style that defaults to the most appropriate style in the current context. The following example shows a circular progress view that starts at 60 percent completed.

struct CircularProgressDemoView: View {
    @State private var progress = 0.6


    var body: some View {
        VStack {
            ProgressView(value: progress)
                .progressViewStyle(.circular)
        }
    }
}


On platforms other than macOS, the circular style may appear as an indeterminate indicator instead.

Topics

**Examples:**

```swift
struct ProgressView<Label, CurrentValueLabel> where Label : View, CurrentValueLabel : View
```

```swift
struct ProgressView<Label, CurrentValueLabel> where Label : View, CurrentValueLabel : View
```

```swift
struct LinearProgressDemoView: View {
    @State private var progress = 0.5


    var body: some View {
        VStack {
            ProgressView(value: progress)
            Button("More") { progress += 0.05 }
        }
    }
}
```

```swift
struct LinearProgressDemoView: View {
    @State private var progress = 0.5


    var body: some View {
        VStack {
            ProgressView(value: progress)
            Button("More") { progress += 0.05 }
        }
    }
}
```

```swift
var body: some View {
    ProgressView()
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/progressview)

---

## TabView

SwiftUI
TabView
Structure
TabView
A view that switches between multiple child views using interactive user interface elements.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 7.0+
struct TabView<SelectionValue, Content> where SelectionValue : Hashable, Content : View
Overview

To create a user interface with tabs, place Tabs in a TabView. On iOS, you can also use one of the badge modifiers, like badge(_:), to assign a badge to each of the tabs.

The following example creates a tab view with three tabs, each presenting a custom child view. The first tab has a numeric badge and the third has a string badge.

TabView {
    Tab("Received", systemImage: "tray.and.arrow.down.fill") {
        ReceivedView()
    }
    .badge(2)


    Tab("Sent", systemImage: "tray.and.arrow.up.fill") {
        SentView()
    }


    Tab("Account", systemImage: "person.crop.circle.fill") {
        AccountView()
    }
    .badge("!")
}


To programmatically select different tabs, use the init(selection:content:) initializer. You can assign a selection value to each tab using a Tab initializer that takes a value. Each tab should have a unique selection value and all tabs should have the same selection value type. When people select a tab in the tab view, the tab view updates the selection binding to the value of the currently selected tab.

The following example creates a tab view that supports programatic selection and has 3 tabs.

TabView(selection: $selection) {
    Tab("Received", systemImage: "tray.and.arrow.down.fill", value: 0) {
        ReceivedView()
    }


    Tab("Sent", systemImage: "tray.and.arrow.up.fill", value: 1) {
        SentView()
    }


    Tab("Account", systemImage: "person.crop.circle.fill", value: 2) {
        AccountView()
    }
}


You can use the page style to display a tab view with multiple scrolling pages of content.

The following example uses a ForEach to create a scrolling tab view that shows the temperatures of various cities.

TabView {
    ForEach(cities) { city in
        TemperatureView(city)
    }
}
.tabViewStyle(.page)

Using tab sections

The sidebarAdaptable style supports declaring a secondary tab hierarchy by grouping tabs with a TabSection.

On iPadOS, tab sections appear in both the sidebar and the tab bar. On iOS and the horizontally compact size class on iPadOS, secondary tabs appear in the tab bar. When secondary tabs appear in the tab bar, the section header doesn’t appear in the tab bar. Consider limiting the number of tabs on iOS and the iPadOS horizontal compact size class so all tabs fit in the tab bar.

The following example has 5 tabs, three of which are grouped within a TabSection.

TabView {
    Tab("Requests", systemImage: "paperplane") {
        RequestsView()
    }


    Tab("Account", systemImage: "person.crop.circle.fill") {
        AccountView()
    }


    TabSection("Messages") {
        Tab("Received", systemImage: "tray.and.arrow.down.fill") {
            ReceivedView()
        }


        Tab("Sent", systemImage: "tray.and.arrow.up.fill") {
            SentView()
        }



**Examples:**

```swift
struct TabView<SelectionValue, Content> where SelectionValue : Hashable, Content : View
```

```swift
struct TabView<SelectionValue, Content> where SelectionValue : Hashable, Content : View
```

```swift
TabView {
    Tab("Received", systemImage: "tray.and.arrow.down.fill") {
        ReceivedView()
    }
    .badge(2)


    Tab("Sent", systemImage: "tray.and.arrow.up.fill") {
        SentView()
    }


    Tab("Account", systemImage: "person.crop.circle.fill") {
        AccountView()
    }
    .badge("!")
}
```

```swift
TabView {
    Tab("Received", systemImage: "tray.and.arrow.down.fill") {
        ReceivedView()
    }
    .badge(2)


    Tab("Sent", systemImage: "tray.and.arrow.up.fill") {
        SentView()
    }


    Tab("Account", systemImage: "person.crop.circle.fill") {
        AccountView()
    }
    .badge("!")
}
```

```swift
TabView(selection: $selection) {
    Tab("Received", systemImage: "tray.and.arrow.down.fill", value: 0) {
        ReceivedView()
    }


    Tab("Sent", systemImage: "tray.and.arrow.up.fill", value: 1) {
        SentView()
    }


    Tab("Account", systemImage: "person.crop.circle.fill", value: 2) {
        AccountView()
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/tabview)

---

## ViewModifier

SwiftUI
ViewModifier
Protocol
ViewModifier
A modifier that you apply to a view or another view modifier, producing a different version of the original value.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
@MainActor @preconcurrency
protocol ViewModifier
Mentioned in
Reducing view modifier maintenance
Overview

Adopt the ViewModifier protocol when you want to create a reusable modifier that you can apply to any view. The example below combines several modifiers to create a new modifier that you can use to create blue caption text surrounded by a rounded rectangle:

struct BorderedCaption: ViewModifier {
    func body(content: Content) -> some View {
        content
            .font(.caption2)
            .padding(10)
            .overlay(
                RoundedRectangle(cornerRadius: 15)
                    .stroke(lineWidth: 1)
            )
            .foregroundColor(Color.blue)
    }
}


You can apply modifier(_:) directly to a view, but a more common and idiomatic approach uses modifier(_:) to define an extension to View itself that incorporates the view modifier:

extension View {
    func borderedCaption() -> some View {
        modifier(BorderedCaption())
    }
}


You can then apply the bordered caption to any view, similar to this:

Image(systemName: "bus")
    .resizable()
    .frame(width:50, height:50)
Text("Downtown Bus")
    .borderedCaption()


A type conforming to this protocol inherits @preconcurrency @MainActor isolation from the protocol if the conformance is included in the type’s base declaration:

struct MyCustomType: Transition {
    // `@preconcurrency @MainActor` isolation by default
}


Isolation to the main actor is the default, but it’s not required. Declare the conformance in an extension to opt out of main actor isolation:

extension MyCustomType: Transition {
    // `nonisolated` by default
}

Topics
Creating a view modifier
func body(content: Self.Content) -> Self.Body
Gets the current body of the caller.

Required Default implementation provided.

associatedtype Body : View
The type of view representing the body.

Required

typealias Content
The content view type passed to body().
Adding animations to a view
func animation(Animation?) -> some ViewModifier
Returns a new version of the modifier that will apply animation to all animatable values within the modifier.
func concat<T>(T) -> ModifiedContent<Self, T>
Returns a new modifier that is the result of concatenating self with modifier.
Handling view taps and gestures
func transaction((inout Transaction) -> Void) -> some ViewModifier
Returns a new version of the modifier that will apply the transaction mutation function transform to all transactions within the modifier.
Relationships
Inherited By
AnimatableModifier
EnvironmentalModifier
GeometryEffect
Conforming Types
AccessibilityAttachmentModifier
EmptyModifier
LayoutRotationUnaryLayout
ManipulableModifier
ManipulableResponderModifier
ManipulableTransformBindingModifier
ManipulationGeometryModifier

**Examples:**

```swift
@MainActor @preconcurrency
protocol ViewModifier
```

```swift
@MainActor @preconcurrency
protocol ViewModifier
```

```swift
struct BorderedCaption: ViewModifier {
    func body(content: Content) -> some View {
        content
            .font(.caption2)
            .padding(10)
            .overlay(
                RoundedRectangle(cornerRadius: 15)
                    .stroke(lineWidth: 1)
            )
            .foregroundColor(Color.blue)
    }
}
```

```swift
struct BorderedCaption: ViewModifier {
    func body(content: Content) -> some View {
        content
            .font(.caption2)
            .padding(10)
            .overlay(
                RoundedRectangle(cornerRadius: 15)
                    .stroke(lineWidth: 1)
            )
            .foregroundColor(Color.blue)
    }
}
```

```swift
extension View {
    func borderedCaption() -> some View {
        modifier(BorderedCaption())
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/viewmodifier)

---

## TimelineView

SwiftUI
TimelineView
Structure
TimelineView
A view that updates according to a schedule that you provide.
iOS 15.0+
iPadOS 15.0+
Mac Catalyst 15.0+
macOS 12.0+
tvOS 15.0+
visionOS 1.0+
watchOS 8.0+
struct TimelineView<Schedule, Content> where Schedule : TimelineSchedule
Overview

A timeline view acts as a container with no appearance of its own. Instead, it redraws the content it contains at scheduled points in time. For example, you can update the face of an analog timer once per second:

TimelineView(.periodic(from: startDate, by: 1)) { context in
    AnalogTimerView(date: context.date)
}


The closure that creates the content receives an input of type TimelineView.Context that you can use to customize the content’s appearance. The context includes the date that triggered the update. In the example above, the timeline view sends that date to an analog timer that you create so the timer view knows how to draw the hands on its face.

The context also includes a cadence property that you can use to hide unnecessary detail. For example, you can use the cadence to decide when it’s appropriate to display the timer’s second hand:

TimelineView(.periodic(from: startDate, by: 1.0)) { context in
    AnalogTimerView(
        date: context.date,
        showSeconds: context.cadence <= .seconds)
}


The system might use a cadence that’s slower than the schedule’s update rate. For example, a view on watchOS might remain visible when the user lowers their wrist, but update less frequently, and thus require less detail.

You can define a custom schedule by creating a type that conforms to the TimelineSchedule protocol, or use one of the built-in schedule types:

Use an everyMinute schedule to update at the beginning of each minute.

Use a periodic(from:by:) schedule to update periodically with a custom start time and interval between updates.

Use an explicit(_:) schedule when you need a finite number, or irregular set of updates.

For a schedule containing only dates in the past, the timeline view shows the last date in the schedule. For a schedule containing only dates in the future, the timeline draws its content using the current date until the first scheduled date arrives.

Topics
Creating a timeline
init(Schedule, content: (TimelineViewDefaultContext) -> Content)
Creates a new timeline view that uses the given schedule.
struct Context
Information passed to a timeline view’s content callback.
Deprecated symbols
init(Schedule, content: (TimelineView<Schedule, Content>.Context) -> Content)
Creates a new timeline view that uses the given schedule.
Deprecated
Initializers
init(_:content:)
Creates a new timeline view that uses the given schedule.
Relationships
Conforms To
Copyable
View
Conforms when Schedule conforms to TimelineSchedule and Content conforms to View.
See Also
Updating a view on a schedule
Updating watchOS apps with timelines
Seamlessly schedule updates to your user interface, even while it’s inactive.
protocol TimelineSchedule
A type that provides a sequence of dates for use as a schedule.
typealias TimelineViewDefaultContext
Information passed to a timeline view’s content callback.

**Examples:**

```swift
struct TimelineView<Schedule, Content> where Schedule : TimelineSchedule
```

```swift
struct TimelineView<Schedule, Content> where Schedule : TimelineSchedule
```

```swift
TimelineSchedule
```

```swift
TimelineView(.periodic(from: startDate, by: 1)) { context in
    AnalogTimerView(date: context.date)
}
```

```swift
TimelineView(.periodic(from: startDate, by: 1)) { context in
    AnalogTimerView(date: context.date)
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/timelineview)

---

## ContextMenu

SwiftUI
ContextMenu
Deprecated
Structure
ContextMenu
A container for views that you present as menu items in a context menu.
iOS 13.0–26.2
Deprecated
iPadOS 13.0–26.2
Deprecated
Mac Catalyst 13.0–26.2
Deprecated
macOS 10.15–26.2
Deprecated
visionOS 1.0–26.2
Deprecated
watchOS 6.0–7.0
Deprecated
struct ContextMenu<MenuItems> where MenuItems : View

Deprecated

Use contextMenu(menuItems:) instead.

Overview

A context menu view allows you to present a situationally specific menu that enables taking actions relevant to the current task.

You can create a context menu by first defining a ContextMenu container with the controls that represent the actions people can take, and then using the contextMenu(_:) view modifier to apply the menu to a view.

The example below creates and applies a two item context menu container to a Text view. The Boolean value shouldShowMenu, which defaults to true, controls the availability of context menu:

private let menuItems = ContextMenu {
    Button {
        // Add this item to a list of favorites.
    } label: {
        Label("Add to Favorites", systemImage: "heart")
    }
    Button {
        // Open Maps and center it on this item.
    } label: {
        Label("Show in Maps", systemImage: "mappin")
    }
}


private struct ContextMenuMenuItems: View {
    @State private var shouldShowMenu = true


    var body: some View {
        Text("Turtle Rock")
            .contextMenu(shouldShowMenu ? menuItems : nil)
    }
}


Topics
Creating a context menu
init(menuItems: () -> MenuItems)
Creates a context menu.
See Also
Deprecated types
struct MenuButton
A button that displays a menu containing a list of choices when pressed.
Deprecated
typealias PullDownButton
Deprecated

**Examples:**

```swift
struct ContextMenu<MenuItems> where MenuItems : View
```

```swift
struct ContextMenu<MenuItems> where MenuItems : View
```

```swift
private let menuItems = ContextMenu {
    Button {
        // Add this item to a list of favorites.
    } label: {
        Label("Add to Favorites", systemImage: "heart")
    }
    Button {
        // Open Maps and center it on this item.
    } label: {
        Label("Show in Maps", systemImage: "mappin")
    }
}


private struct ContextMenuMenuItems: View {
    @State private var shouldShowMenu = true


    var body: some View {
        Text("Turtle Rock")
            .contextMenu(shouldShowMenu ? menuItems : nil)
    }
}
```

```swift
private let menuItems = ContextMenu {
    Button {
        // Add this item to a list of favorites.
    } label: {
        Label("Add to Favorites", systemImage: "heart")
    }
    Button {
        // Open Maps and center it on this item.
    } label: {
        Label("Show in Maps", systemImage: "mappin")
    }
}


private struct ContextMenuMenuItems: View {
    @State private var shouldShowMenu = true


    var body: some View {
        Text("Turtle Rock")
            .contextMenu(shouldShowMenu ? menuItems : nil)
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/contextmenu)

---

## UIViewRepresentable

SwiftUI
UIViewRepresentable
Protocol
UIViewRepresentable
A wrapper for a UIKit view that you use to integrate that view into your SwiftUI view hierarchy.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
tvOS 13.0+
visionOS 1.0+
@MainActor @preconcurrency
protocol UIViewRepresentable : View where Self.Body == Never
Overview

Use a UIViewRepresentable instance to create and manage a UIView object in your SwiftUI interface. Adopt this protocol in one of your app’s custom instances, and use its methods to create, update, and tear down your view. The creation and update processes parallel the behavior of SwiftUI views, and you use them to configure your view with your app’s current state information. Use the teardown process to remove your view cleanly from your SwiftUI. For example, you might use the teardown process to notify other objects that the view is disappearing.

To add your view into your SwiftUI interface, create your UIViewRepresentable instance and add it to your SwiftUI interface. The system calls the methods of your representable instance at appropriate times to create and update the view. The following example shows the inclusion of a custom MyRepresentedCustomView structure in the view hierarchy.

struct ContentView: View {
   var body: some View {
      VStack {
         Text("Global Sales")
         MyRepresentedCustomView()
      }
   }
}


The system doesn’t automatically communicate changes occurring within your view to other parts of your SwiftUI interface. When you want your view to coordinate with other SwiftUI views, you must provide a Coordinator instance to facilitate those interactions. For example, you use a coordinator to forward target-action and delegate messages from your view to any SwiftUI views.

Warning

SwiftUI fully controls the layout of the UIKit view’s center, bounds, frame, and transform properties. Don’t directly set these layout-related properties on the view managed by a UIViewRepresentable instance from your own code because that conflicts with SwiftUI and results in undefined behavior.

Topics
Creating and updating the view
func makeUIView(context: Self.Context) -> Self.UIViewType
Creates the view object and configures its initial state.

Required

func updateUIView(Self.UIViewType, context: Self.Context)
Updates the state of the specified view with new information from SwiftUI.

Required

typealias Context
associatedtype UIViewType : UIView
The type of view to present.

Required

Specifying a size
func sizeThatFits(ProposedViewSize, uiView: Self.UIViewType, context: Self.Context) -> CGSize?
Given a proposed size, returns the preferred size of the composite view.

Required Default implementation provided.

Cleaning up the view
static func dismantleUIView(Self.UIViewType, coordinator: Self.Coordinator)
Cleans up the presented UIKit view (and coordinator) in anticipation of their removal.

Required Default implementation provided.

Providing a custom coordinator object
func makeCoordinator() -> Self.Coordinator
Creates the custom instance that you use to communicate changes from your view to other parts of your SwiftUI interface.

Required Default implementation provided.

associatedtype Coordinator = Void
A type to coordinate with the view.

Required

Performing layout
typealias LayoutOptions
Relationships
Inherits From
View
See Also
Adding UIKit views to SwiftUI view hierarchies
struct UIViewRepresentableContext
Contextual information about the state of the system that you use to create and update your UIKit view.
protocol UIViewControllerRepresentable
A view that represents a UIKit view controller.
struct UIViewControllerRepresentableContext
Contextual information about the state of the system that you use to create and update your UIKit view controller.

**Examples:**

```swift
@MainActor @preconcurrency
protocol UIViewRepresentable : View where Self.Body == Never
```

```swift
@MainActor @preconcurrency
protocol UIViewRepresentable : View where Self.Body == Never
```

```swift
struct ContentView: View {
   var body: some View {
      VStack {
         Text("Global Sales")
         MyRepresentedCustomView()
      }
   }
}
```

```swift
struct ContentView: View {
   var body: some View {
      VStack {
         Text("Global Sales")
         MyRepresentedCustomView()
      }
   }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/uiviewrepresentable)

---

## UIViewControllerRepresentable

SwiftUI
UIViewControllerRepresentable
Protocol
UIViewControllerRepresentable
A view that represents a UIKit view controller.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
tvOS 13.0+
visionOS 1.0+
@MainActor @preconcurrency
protocol UIViewControllerRepresentable : View where Self.Body == Never
Overview

Use a UIViewControllerRepresentable instance to create and manage a UIViewController object in your SwiftUI interface. Adopt this protocol in one of your app’s custom instances, and use its methods to create, update, and tear down your view controller. The creation and update processes parallel the behavior of SwiftUI views, and you use them to configure your view controller with your app’s current state information. Use the teardown process to remove your view controller cleanly from your SwiftUI. For example, you might use the teardown process to notify other objects that the view controller is disappearing.

To add your view controller into your SwiftUI interface, create your UIViewControllerRepresentable instance and add it to your SwiftUI interface. The system calls the methods of your custom instance at appropriate times.

The system doesn’t automatically communicate changes occurring within your view controller to other parts of your SwiftUI interface. When you want your view controller to coordinate with other SwiftUI views, you must provide a Coordinator instance to facilitate those interactions. For example, you use a coordinator to forward target-action and delegate messages from your view controller to any SwiftUI views.

Warning

SwiftUI fully controls the layout of the UIKit view controller’s view using the view’s center, bounds, frame, and transform properties. Don’t directly set these layout-related properties on the view managed by a UIViewControllerRepresentable instance from your own code because that conflicts with SwiftUI and results in undefined behavior.

Topics
Creating and updating the view controller
func makeUIViewController(context: Self.Context) -> Self.UIViewControllerType
Creates the view controller object and configures its initial state.

Required

func updateUIViewController(Self.UIViewControllerType, context: Self.Context)
Updates the state of the specified view controller with new information from SwiftUI.

Required

typealias Context
associatedtype UIViewControllerType : UIViewController
The type of view controller to present.

Required

Specifying a size
func sizeThatFits(ProposedViewSize, uiViewController: Self.UIViewControllerType, context: Self.Context) -> CGSize?
Given a proposed size, returns the preferred size of the composite view.

Required Default implementation provided.

Cleaning up the view controller
static func dismantleUIViewController(Self.UIViewControllerType, coordinator: Self.Coordinator)
Cleans up the presented view controller (and coordinator) in anticipation of their removal.

Required Default implementation provided.

Providing a custom coordinator object
func makeCoordinator() -> Self.Coordinator
Creates the custom instance that you use to communicate changes from your view controller to other parts of your SwiftUI interface.

Required Default implementation provided.

associatedtype Coordinator = Void
A type to coordinate with the view controller.

Required

Performing layout
typealias LayoutOptions
Relationships
Inherits From
View
See Also
Adding UIKit views to SwiftUI view hierarchies
protocol UIViewRepresentable
A wrapper for a UIKit view that you use to integrate that view into your SwiftUI view hierarchy.
struct UIViewRepresentableContext
Contextual information about the state of the system that you use to create and update your UIKit view.
struct UIViewControllerRepresentableContext
Contextual information about the state of the system that you use to create and update your UIKit view controller.

**Examples:**

```swift
@MainActor @preconcurrency
protocol UIViewControllerRepresentable : View where Self.Body == Never
```

```swift
@MainActor @preconcurrency
protocol UIViewControllerRepresentable : View where Self.Body == Never
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/uiviewcontrollerrepresentable)

---

## NSViewRepresentable

SwiftUI
NSViewRepresentable
Protocol
NSViewRepresentable
A wrapper that you use to integrate an AppKit view into your SwiftUI view hierarchy.
macOS 10.15+
@MainActor @preconcurrency
protocol NSViewRepresentable : View where Self.Body == Never
Overview

Use an NSViewRepresentable instance to create and manage an NSView object in your SwiftUI interface. Adopt this protocol in one of your app’s custom instances, and use its methods to create, update, and tear down your view. The creation and update processes parallel the behavior of SwiftUI views, and you use them to configure your view with your app’s current state information. Use the teardown process to remove your view cleanly from your SwiftUI. For example, you might use the teardown process to notify other objects that the view is disappearing.

To add your view into your SwiftUI interface, create your NSViewRepresentable instance and add it to your SwiftUI interface. The system calls the methods of your representable instance at appropriate times to create and update the view. The following example shows the inclusion of a custom MyRepresentedCustomView struct in the view hierarchy.

struct ContentView: View {
   var body: some View {
      VStack {
         Text("Global Sales")
         MyRepresentedCustomView()
      }
   }
}


The system doesn’t automatically communicate changes occurring within your view controller to other parts of your SwiftUI interface. When you want your view controller to coordinate with other SwiftUI views, you must provide a Coordinator object to facilitate those interactions. For example, you use a coordinator to forward target-action and delegate messages from your view controller to any SwiftUI views.

Warning

SwiftUI fully controls the layout of the AppKit view using the view’s frame and bounds properties. Don’t directly set these layout-related properties on the view managed by an NSViewRepresentable instance from your own code because that conflicts with SwiftUI and results in undefined behavior.

Topics
Creating and updating the view
func makeNSView(context: Self.Context) -> Self.NSViewType
Creates the view object and configures its initial state.

Required

func updateNSView(Self.NSViewType, context: Self.Context)
Updates the state of the specified view with new information from SwiftUI.

Required

typealias Context
associatedtype NSViewType : NSView
The type of view to present.

Required

Specifying a size
func sizeThatFits(ProposedViewSize, nsView: Self.NSViewType, context: Self.Context) -> CGSize?
Given a proposed size, returns the preferred size of the composite view.

Required Default implementation provided.

Cleaning up the view
static func dismantleNSView(Self.NSViewType, coordinator: Self.Coordinator)
Cleans up the presented AppKit view (and coordinator) in anticipation of their removal.

Required Default implementation provided.

Providing a custom coordinator object
func makeCoordinator() -> Self.Coordinator
Creates the custom instance that you use to communicate changes from your view to other parts of your SwiftUI interface.

Required Default implementation provided.

associatedtype Coordinator = Void
A type to coordinate with the view.

Required

Performing layout
typealias LayoutOptions
Relationships
Inherits From
View
See Also
Adding AppKit views to SwiftUI view hierarchies
struct NSViewRepresentableContext
Contextual information about the state of the system that you use to create and update your AppKit view.
protocol NSViewControllerRepresentable
A wrapper that you use to integrate an AppKit view controller into your SwiftUI interface.
struct NSViewControllerRepresentableContext
Contextual information about the state of the system that you use to create and update your AppKit view controller.

**Examples:**

```swift
@MainActor @preconcurrency
protocol NSViewRepresentable : View where Self.Body == Never
```

```swift
@MainActor @preconcurrency
protocol NSViewRepresentable : View where Self.Body == Never
```

```swift
struct ContentView: View {
   var body: some View {
      VStack {
         Text("Global Sales")
         MyRepresentedCustomView()
      }
   }
}
```

```swift
struct ContentView: View {
   var body: some View {
      VStack {
         Text("Global Sales")
         MyRepresentedCustomView()
      }
   }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/nsviewrepresentable)

---

## NSViewControllerRepresentable

SwiftUI
NSViewControllerRepresentable
Protocol
NSViewControllerRepresentable
A wrapper that you use to integrate an AppKit view controller into your SwiftUI interface.
macOS 10.15+
@MainActor @preconcurrency
protocol NSViewControllerRepresentable : View where Self.Body == Never
Overview

Use an NSViewControllerRepresentable instance to create and manage an NSViewController object in your SwiftUI interface. Adopt this protocol in one of your app’s custom instances, and use its methods to create, update, and tear down your view controller. The creation and update processes parallel the behavior of SwiftUI views, and you use them to configure your view controller with your app’s current state information. Use the teardown process to remove your view controller cleanly from your SwiftUI. For example, you might use the teardown process to notify other objects that the view controller is disappearing.

To add your view controller into your SwiftUI interface, create your NSViewControllerRepresentable instance and add it to your SwiftUI interface. The system calls the methods of your custom instance at appropriate times.

The system doesn’t automatically communicate changes occurring within your view controller to other parts of your SwiftUI interface. When you want your view controller to coordinate with other SwiftUI views, you must provide a Coordinator instance to facilitate those interactions. For example, you use a coordinator to forward target-action and delegate messages from your view controller to any SwiftUI views.

Warning

SwiftUI fully controls the layout of the AppKit view controller’s view using the view’s frame and bounds properties. Don’t directly set these layout-related properties on the view managed by an NSViewControllerRepresentable instance from your own code because that conflicts with SwiftUI and results in undefined behavior.

Topics
Creating and updating the view controller
func makeNSViewController(context: Self.Context) -> Self.NSViewControllerType
Creates the view controller object and configures its initial state.

Required

func updateNSViewController(Self.NSViewControllerType, context: Self.Context)
Updates the state of the specified view controller with new information from SwiftUI.

Required

typealias Context
associatedtype NSViewControllerType : NSViewController
The type of view controller to present.

Required

Specifying a size
func sizeThatFits(ProposedViewSize, nsViewController: Self.NSViewControllerType, context: Self.Context) -> CGSize?
Given a proposed size, returns the preferred size of the composite view.

Required Default implementation provided.

Cleaning up the view controller
static func dismantleNSViewController(Self.NSViewControllerType, coordinator: Self.Coordinator)
Cleans up the presented view controller (and coordinator) in anticipation of its removal.

Required Default implementation provided.

Providing a custom coordinator object
func makeCoordinator() -> Self.Coordinator
Creates the custom object that you use to communicate changes from your view controller to other parts of your SwiftUI interface.

Required Default implementation provided.

associatedtype Coordinator = Void
A type to coordinate with the view controller.

Required

Performing layout
typealias LayoutOptions
Relationships
Inherits From
View
See Also
Adding AppKit views to SwiftUI view hierarchies
protocol NSViewRepresentable
A wrapper that you use to integrate an AppKit view into your SwiftUI view hierarchy.
struct NSViewRepresentableContext
Contextual information about the state of the system that you use to create and update your AppKit view.
struct NSViewControllerRepresentableContext
Contextual information about the state of the system that you use to create and update your AppKit view controller.

**Examples:**

```swift
@MainActor @preconcurrency
protocol NSViewControllerRepresentable : View where Self.Body == Never
```

```swift
@MainActor @preconcurrency
protocol NSViewControllerRepresentable : View where Self.Body == Never
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/nsviewcontrollerrepresentable)

---

## PreviewProvider

SwiftUI
PreviewProvider
Protocol
PreviewProvider
A type that produces view previews in Xcode.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
@MainActor @preconcurrency
protocol PreviewProvider : _PreviewProvider
Overview

Important

You can use this protocol to define a preview manually, but you typically use a preview macro like Preview(_:body:) instead.

You can create an Xcode preview by declaring a structure that conforms to the PreviewProvider protocol. Implement the required previews computed property, and return the view to display:

struct CircleImage_Previews: PreviewProvider {
    static var previews: some View {
        CircleImage()
    }
}


Xcode statically discovers preview providers in your project and generates previews for any providers currently open in the source editor. Xcode generates the preview using the current run destination as a hint for which device to display. For example, Xcode shows the following preview if you’ve selected an iOS target to run on the iPhone 12 Pro Max simulator:

When you create a new file (File > New > File) and choose the SwiftUI view template, Xcode automatically inserts a preview structure at the bottom of the file that you can configure. You can also create new preview structures in an existing SwiftUI view file by choosing Editor > Create Preview.

Customize the preview’s appearance by adding view modifiers, just like you do when building a custom View. This includes preview-specific modifiers that let you control aspects of the preview, like the device orientation:

struct CircleImage_Previews: PreviewProvider {
    static var previews: some View {
        CircleImage()
            .previewInterfaceOrientation(.landscapeLeft)
    }
}


For the complete list of preview customizations, see Previews in Xcode.

Xcode creates different previews for each view in your preview, so you can see variations side by side. For example, you might want to see a view’s light and dark appearances simultaneously:

struct CircleImage_Previews: PreviewProvider {
    static var previews: some View {
        CircleImage()
        CircleImage()
            .preferredColorScheme(.dark)
    }
}


Use a Group when you want to maintain different previews, but apply a single modifier to all of them:

struct CircleImage_Previews: PreviewProvider {
    static var previews: some View {
        Group {
            CircleImage()
            CircleImage()
                .preferredColorScheme(.dark)
        }
        .previewLayout(.sizeThatFits)
    }
}


Topics
Creating a preview
static var previews: Self.Previews
A collection of views to preview.

Required

associatedtype Previews : View
The type to preview.

Required

Specifying the platform
static var platform: PreviewPlatform?
The platform on which to run the provider.

Required Default implementation provided.

See Also
Defining a preview
macro Previewable()
Tag allowing a dynamic property to appear inline in a preview.
enum PreviewPlatform
Platforms that can run the preview.
func previewDisplayName(String?) -> some View
Sets a user visible name to show in the canvas for a preview.
protocol PreviewModifier
A type that defines an environment in which previews can appear.
struct PreviewModifierContent
The type-erased content of a preview.

**Examples:**

```swift
@MainActor @preconcurrency
protocol PreviewProvider : _PreviewProvider
```

```swift
@MainActor @preconcurrency
protocol PreviewProvider : _PreviewProvider
```

```swift
struct CircleImage_Previews: PreviewProvider {
    static var previews: some View {
        CircleImage()
    }
}
```

```swift
struct CircleImage_Previews: PreviewProvider {
    static var previews: some View {
        CircleImage()
    }
}
```

```swift
struct CircleImage_Previews: PreviewProvider {
    static var previews: some View {
        CircleImage()
            .previewInterfaceOrientation(.landscapeLeft)
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/previewprovider)

---

## AccessibilityLabel (Failed)

Error: Page.goto: Timeout 30000ms exceeded.
Call log:
  - navigating to "https://developer.apple.com/documentation/swiftui/accessibilitylabel", waiting until "networkidle"


[View Official Documentation](https://developer.apple.com/documentation/swiftui/accessibilitylabel)

---

## RealityView (Failed)

Error: Page.goto: Timeout 30000ms exceeded.
Call log:
  - navigating to "https://developer.apple.com/documentation/swiftui/realityview", waiting until "networkidle"


[View Official Documentation](https://developer.apple.com/documentation/swiftui/realityview)

---

