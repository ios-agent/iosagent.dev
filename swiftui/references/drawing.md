# Drawing

SwiftUI drawing documentation.

---

## Path

SwiftUI
Path
Structure
Path
The outline of a 2D shape.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
@frozen
struct Path
Topics
Creating a path
init()
Creates an empty path.
init(_:)
Creates an empty path, then executes a closure to add its initial elements.
init(ellipseIn: CGRect)
Creates a path as an ellipse within the given rectangle.
init(roundedRect: CGRect, cornerRadius: CGFloat, style: RoundedCornerStyle)
Creates a path containing a rounded rectangle.
init(roundedRect: CGRect, cornerSize: CGSize, style: RoundedCornerStyle)
Creates a path containing a rounded rectangle.
init(roundedRect: CGRect, cornerRadii: RectangleCornerRadii, style: RoundedCornerStyle)
Creates a path as the given rounded rectangle, which may have uneven corner radii.
Getting the path’s characteristics
var boundingRect: CGRect
A rectangle containing all path segments.
var cgPath: CGPath
An immutable path representing the elements in the path.
func contains(CGPoint, eoFill: Bool) -> Bool
Returns true if the path contains a specified point.
var currentPoint: CGPoint?
Returns the last point in the path, or nil if the path contains no points.
var description: String
A description of the path that may be used to recreate the path via init?(_:).
var isEmpty: Bool
A Boolean value indicating whether the path contains zero elements.
Drawing a path
func move(to: CGPoint)
Begins a new subpath at the specified point.
func addArc(center: CGPoint, radius: CGFloat, startAngle: Angle, endAngle: Angle, clockwise: Bool, transform: CGAffineTransform)
Adds an arc of a circle to the path, specified with a radius and angles.
func addArc(tangent1End: CGPoint, tangent2End: CGPoint, radius: CGFloat, transform: CGAffineTransform)
Adds an arc of a circle to the path, specified with a radius and two tangent lines.
func addCurve(to: CGPoint, control1: CGPoint, control2: CGPoint)
Adds a cubic Bézier curve to the path, with the specified end point and control points.
func addEllipse(in: CGRect, transform: CGAffineTransform)
Adds an ellipse that fits inside the specified rectangle to the path.
func addLine(to: CGPoint)
Appends a straight line segment from the current point to the specified point.
func addLines([CGPoint])
Adds a sequence of connected straight-line segments to the path.
func addPath(Path, transform: CGAffineTransform)
Appends another path value to this path.
func addQuadCurve(to: CGPoint, control: CGPoint)
Adds a quadratic Bézier curve to the path, with the specified end point and control point.
func addRect(CGRect, transform: CGAffineTransform)
Adds a rectangular subpath to the path.
func addRects([CGRect], transform: CGAffineTransform)
Adds a set of rectangular subpaths to the path.
func addRelativeArc(center: CGPoint, radius: CGFloat, startAngle: Angle, delta: Angle, transform: CGAffineTransform)
Adds an arc of a circle to the path, specified with a radius and a difference in angle.
func addRoundedRect(in: CGRect, cornerSize: CGSize, style: RoundedCornerStyle, transform: CGAffineTransform)
Adds a rounded rectangle to the path.
func closeSubpath()
Closes and completes the current subpath.
Transforming the path
func applying(CGAffineTransform) -> Path
Returns a path constructed by applying the transform to all points of the path.
func offsetBy(dx: CGFloat, dy: CGFloat) -> Path
Returns a path constructed by translating all its points.
func trimmedPath(from: CGFloat, to: CGFloat) -> Path
Returns a partial copy of the path.
Performing operations on the path
func addRoundedRect(in: CGRect, cornerSize: CGSize, style: RoundedCornerStyle, transform: CGAffineTransform)
Adds a rounded rectangle to the path.
func intersection(Path, eoFill: Bool) -> Path
Returns a new path with filled regions common to both paths.
func lineIntersection(Path, eoFill: Bool) -> Path
Returns a new path with a line from this path that overlaps the filled regions of the given path.
func lineSubtraction(Path, eoFill: Bool) -> Path
Returns a new path with a line from this path that does not overlap the filled region of the given path.
func normalized(eoFill: Bool) -> Path
Returns a new weakly-simple copy of this path.
func subtracting(Path, eoFill: Bool) -> Path
Returns a new path with filled regions from this path that are not in the given path.
func symmetricDifference(Path, eoFill: Bool) -> Path
Returns a new path with filled regions either from this path or the given path, but not in both.
func union(Path, eoFill: Bool) -> Path
Returns a new path with filled regions in either this path or the given path.
Operating over path elements
func forEach((Path.Element) -> Void)
Calls body with each element in the path.
enum Element
An element of a path.
Applying a style

**Examples:**

```swift
@frozen
struct Path
```

```swift
@frozen
struct Path
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/path)

---

## GeometryReader

SwiftUI
GeometryReader
Structure
GeometryReader
A container view that defines its content as a function of its own size and coordinate space.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
@frozen
struct GeometryReader<Content> where Content : View
Overview

This view returns a flexible preferred size to its parent layout.

Topics
Creating a geometry reader
init(content: (GeometryProxy) -> Content)
var content: (GeometryProxy) -> Content
Relationships
Conforms To
View
See Also
Measuring a view
struct GeometryReader3D
A container view that defines its content as a function of its own size and coordinate space.
struct GeometryProxy
A proxy for access to the size and coordinate space (for anchor resolution) of the container view.
struct GeometryProxy3D
A proxy for access to the size and coordinate space of the container view.
func coordinateSpace(NamedCoordinateSpace) -> some View
Assigns a name to the view’s coordinate space, so other code can operate on dimensions like points and sizes relative to the named space.
enum CoordinateSpace
A resolved coordinate space created by the coordinate space protocol.
protocol CoordinateSpaceProtocol
A frame of reference within the layout system.
struct PhysicalMetric
Provides access to a value in points that corresponds to the specified physical measurement.
struct PhysicalMetricsConverter
A physical metrics converter provides conversion between point values and their extent in 3D space, in the form of physical length measurements.

**Examples:**

```swift
@frozen
struct GeometryReader<Content> where Content : View
```

```swift
@frozen
struct GeometryReader<Content> where Content : View
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/geometryreader)

---

## GeometryProxy

SwiftUI
GeometryProxy
Structure
GeometryProxy
A proxy for access to the size and coordinate space (for anchor resolution) of the container view.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
struct GeometryProxy
Topics
Accessing geometry characteristics
func bounds(of: NamedCoordinateSpace) -> CGRect?
Returns the given coordinate space’s bounds rectangle, converted to the local coordinate space.
func frame(in:)
Returns the container view’s bounds rectangle, converted to a defined coordinate space.
var size: CGSize
The size of the container view.
var safeAreaInsets: EdgeInsets
The safe area inset of the container view.
subscript<T>(Anchor<T>) -> T
Resolves the value of an anchor to the container view.
func transform(in: some CoordinateSpaceProtocol) -> AffineTransform3D?
The container view’s 3D transform converted to a defined coordinate space.
Instance Properties
var containerCornerInsets: RectangleCornerInsets
Returns the corner insets of the container view. Use this value to adjust the geometry of a view based on the overlapping corner insets of the container view. Corner insets may include pieces of system UI as well as the corner radii for windows and presentations.
See Also
Measuring a view
struct GeometryReader
A container view that defines its content as a function of its own size and coordinate space.
struct GeometryReader3D
A container view that defines its content as a function of its own size and coordinate space.
struct GeometryProxy3D
A proxy for access to the size and coordinate space of the container view.
func coordinateSpace(NamedCoordinateSpace) -> some View
Assigns a name to the view’s coordinate space, so other code can operate on dimensions like points and sizes relative to the named space.
enum CoordinateSpace
A resolved coordinate space created by the coordinate space protocol.
protocol CoordinateSpaceProtocol
A frame of reference within the layout system.
struct PhysicalMetric
Provides access to a value in points that corresponds to the specified physical measurement.
struct PhysicalMetricsConverter
A physical metrics converter provides conversion between point values and their extent in 3D space, in the form of physical length measurements.

**Examples:**

```swift
struct GeometryProxy
```

```swift
struct GeometryProxy
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/geometryproxy)

---

## Canvas

SwiftUI
Canvas
Structure
Canvas
A view type that supports immediate mode drawing.
iOS 15.0+
iPadOS 15.0+
Mac Catalyst 15.0+
macOS 12.0+
tvOS 15.0+
visionOS 1.0+
watchOS 8.0+
struct Canvas<Symbols> where Symbols : View
Overview

Use a canvas to draw rich and dynamic 2D graphics inside a SwiftUI view. The canvas passes a GraphicsContext to the closure that you use to perform immediate mode drawing operations. The canvas also passes a CGSize value that you can use to customize what you draw. For example, you can use the context’s stroke(_:with:lineWidth:) command to draw a Path instance:

Canvas { context, size in
    context.stroke(
        Path(ellipseIn: CGRect(origin: .zero, size: size)),
        with: .color(.green),
        lineWidth: 4)
}
.frame(width: 300, height: 200)
.border(Color.blue)


The example above draws the outline of an ellipse that exactly inscribes a canvas with a blue border:

In addition to outlined and filled paths, you can draw images, text, and complete SwiftUI views. To draw views, use the init(opaque:colorMode:rendersAsynchronously:renderer:symbols:) method to supply views that you can reference from inside the renderer. You can also add masks, apply filters, perform transforms, control blending, and more. For information about how to draw, see GraphicsContext.

A canvas doesn’t offer interactivity or accessibility for individual elements, including for views that you pass in as symbols. However, it might provide better performance for a complex drawing that involves dynamic data. Use a canvas to improve performance for a drawing that doesn’t primarily involve text or require interactive elements.

Topics
Creating a canvas
init(opaque: Bool, colorMode: ColorRenderingMode, rendersAsynchronously: Bool, renderer: (inout GraphicsContext, CGSize) -> Void)
Creates and configures a canvas.
init(opaque: Bool, colorMode: ColorRenderingMode, rendersAsynchronously: Bool, renderer: (inout GraphicsContext, CGSize) -> Void, symbols: () -> Symbols)
Creates and configures a canvas that you supply with renderable child views.
Managing opacity and color
var isOpaque: Bool
A Boolean that indicates whether the canvas is fully opaque.
var colorMode: ColorRenderingMode
The working color space and storage format of the canvas.
Referencing symbols
var symbols: Symbols
A view that provides child views that you can use in the drawing callback.
Rendering
var rendersAsynchronously: Bool
A Boolean that indicates whether the canvas can present its contents to its parent view asynchronously.
var renderer: (inout GraphicsContext, CGSize) -> Void
The drawing callback that you use to draw into the canvas.
Relationships
Conforms To
Copyable
View
Conforms when Symbols conforms to View.
See Also
Immediate mode drawing
Add rich graphics to your SwiftUI app
Make your apps stand out by adding background materials, vibrancy, custom graphics, and animations.
struct GraphicsContext
An immediate mode drawing destination, and its current state.

**Examples:**

```swift
struct Canvas<Symbols> where Symbols : View
```

```swift
struct Canvas<Symbols> where Symbols : View
```

```swift
Canvas { context, size in
    context.stroke(
        Path(ellipseIn: CGRect(origin: .zero, size: size)),
        with: .color(.green),
        lineWidth: 4)
}
.frame(width: 300, height: 200)
.border(Color.blue)
```

```swift
Canvas { context, size in
    context.stroke(
        Path(ellipseIn: CGRect(origin: .zero, size: size)),
        with: .color(.green),
        lineWidth: 4)
}
.frame(width: 300, height: 200)
.border(Color.blue)
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/canvas)

---

