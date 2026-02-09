# Gestures

SwiftUI gestures documentation.

---

## DragGesture

SwiftUI
DragGesture
Structure
DragGesture
A dragging motion that invokes an action as the drag-event sequence changes.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
visionOS 1.0+
watchOS 6.0+
struct DragGesture
Mentioned in
Composing SwiftUI gestures
Overview

To recognize a drag gesture on a view, create and configure the gesture, and then add it to the view using the gesture(_:including:) modifier.

Add a drag gesture to a Circle and change its color while the user performs the drag gesture:

struct DragGestureView: View {
    @State private var isDragging = false


    var drag: some Gesture {
        DragGesture()
            .onChanged { _ in self.isDragging = true }
            .onEnded { _ in self.isDragging = false }
    }


    var body: some View {
        Circle()
            .fill(self.isDragging ? Color.red : Color.blue)
            .frame(width: 100, height: 100, alignment: .center)
            .gesture(drag)
    }
}

Topics
Creating a drag gesture
init(minimumDistance: CGFloat, coordinateSpace: some CoordinateSpaceProtocol)
Creates a dragging gesture with the minimum dragging distance before the gesture succeeds and the coordinate space of the gesture’s location.
var minimumDistance: CGFloat
The minimum dragging distance before the gesture succeeds.
var coordinateSpace: CoordinateSpace
The coordinate space in which to receive location values.
Deprecated initializers
init(minimumDistance: CGFloat, coordinateSpace: CoordinateSpace)
Creates a dragging gesture with the minimum dragging distance before the gesture succeeds and the coordinate space of the gesture’s location.
Deprecated
Structures
struct Value
The attributes of a drag gesture.
Initializers
init(minimumDistance: CGFloat, coordinateSpace3D: some CoordinateSpace3D)
Creates a dragging gesture with the minimum dragging distance before the gesture succeeds and the coordinate space of the gesture’s location.
init(minimumDistance:coordinateSpace:)
Creates a dragging gesture with the minimum dragging distance before the gesture succeeds and the coordinate space of the gesture’s location.
Relationships
Conforms To
Gesture
See Also
Recognizing gestures that change over time
func gesture(_:)
Attaches an NSGestureRecognizerRepresentable to the view.
func gesture<T>(T, isEnabled: Bool) -> some View
Attaches a gesture to the view with a lower precedence than gestures defined by the view.
func gesture<T>(T, name: String, isEnabled: Bool) -> some View
Attaches a gesture to the view with a lower precedence than gestures defined by the view.
func gesture<T>(T, including: GestureMask) -> some View
Attaches a gesture to the view with a lower precedence than gestures defined by the view.
struct WindowDragGesture
A gesture that recognizes the motion of and handles dragging a window.
struct MagnifyGesture
A gesture that recognizes a magnification motion and tracks the amount of magnification.
struct RotateGesture
A gesture that recognizes a rotation motion and tracks the angle of the rotation.
struct RotateGesture3D
A gesture that recognizes 3D rotation motion and tracks the angle and axis of the rotation.
struct GestureMask
Options that control how adding a gesture to a view affects other gestures recognized by the view and its subviews.

**Examples:**

```swift
struct DragGesture
```

```swift
struct DragGesture
```

```swift
struct DragGestureView: View {
    @State private var isDragging = false


    var drag: some Gesture {
        DragGesture()
            .onChanged { _ in self.isDragging = true }
            .onEnded { _ in self.isDragging = false }
    }


    var body: some View {
        Circle()
            .fill(self.isDragging ? Color.red : Color.blue)
            .frame(width: 100, height: 100, alignment: .center)
            .gesture(drag)
    }
}
```

```swift
struct DragGestureView: View {
    @State private var isDragging = false


    var drag: some Gesture {
        DragGesture()
            .onChanged { _ in self.isDragging = true }
            .onEnded { _ in self.isDragging = false }
    }


    var body: some View {
        Circle()
            .fill(self.isDragging ? Color.red : Color.blue)
            .frame(width: 100, height: 100, alignment: .center)
            .gesture(drag)
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/draggesture)

---

## TapGesture

SwiftUI
TapGesture
Structure
TapGesture
A gesture that recognizes one or more taps.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 16.0+
visionOS 1.0+
watchOS 6.0+
struct TapGesture
Overview

To recognize a tap gesture on a view, create and configure the gesture, and then add it to the view using the gesture(_:including:) modifier. The following code adds a tap gesture to a Circle that toggles the color of the circle:

struct TapGestureView: View {
    @State private var tapped = false


    var tap: some Gesture {
        TapGesture(count: 1)
            .onEnded { _ in self.tapped = !self.tapped }
    }


    var body: some View {
        Circle()
            .fill(self.tapped ? Color.blue : Color.red)
            .frame(width: 100, height: 100, alignment: .center)
            .gesture(tap)
    }
}

Topics
Creating a tap gesture
init(count: Int)
Creates a tap gesture with the number of required taps.
var count: Int
The required number of tap events.
Relationships
Conforms To
Gesture
See Also
Recognizing tap gestures
func onTapGesture(count: Int, perform: () -> Void) -> some View
Adds an action to perform when this view recognizes a tap gesture.
func onTapGesture(count:coordinateSpace:perform:)
Adds an action to perform when this view recognizes a tap gesture, and provides the action with the location of the interaction.
struct SpatialTapGesture
A gesture that recognizes one or more taps and reports their location.

**Examples:**

```swift
struct TapGesture
```

```swift
struct TapGesture
```

```swift
struct TapGestureView: View {
    @State private var tapped = false


    var tap: some Gesture {
        TapGesture(count: 1)
            .onEnded { _ in self.tapped = !self.tapped }
    }


    var body: some View {
        Circle()
            .fill(self.tapped ? Color.blue : Color.red)
            .frame(width: 100, height: 100, alignment: .center)
            .gesture(tap)
    }
}
```

```swift
struct TapGestureView: View {
    @State private var tapped = false


    var tap: some Gesture {
        TapGesture(count: 1)
            .onEnded { _ in self.tapped = !self.tapped }
    }


    var body: some View {
        Circle()
            .fill(self.tapped ? Color.blue : Color.red)
            .frame(width: 100, height: 100, alignment: .center)
            .gesture(tap)
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/tapgesture)

---

## LongPressGesture

SwiftUI
LongPressGesture
Structure
LongPressGesture
A gesture that succeeds when the user performs a long press.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 14.0+
visionOS 1.0+
watchOS 6.0+
struct LongPressGesture
Mentioned in
Adding interactivity with gestures
Composing SwiftUI gestures
Overview

To recognize a long-press gesture on a view, create and configure the gesture, then add it to the view using the gesture(_:including:) modifier.

Add a long-press gesture to a Circle to animate its color from blue to red, and then change it to green when the gesture ends:

struct LongPressGestureView: View {
    @GestureState private var isDetectingLongPress = false
    @State private var completedLongPress = false


    var longPress: some Gesture {
        LongPressGesture(minimumDuration: 3)
            .updating($isDetectingLongPress) { currentState, gestureState,
                    transaction in
                gestureState = currentState
                transaction.animation = Animation.easeIn(duration: 2.0)
            }
            .onEnded { finished in
                self.completedLongPress = finished
            }
    }


    var body: some View {
        Circle()
            .fill(self.isDetectingLongPress ?
                Color.red :
                (self.completedLongPress ? Color.green : Color.blue))
            .frame(width: 100, height: 100, alignment: .center)
            .gesture(longPress)
    }
}

Topics
Creating a long press gesture
init(minimumDuration: Double)
Creates a long-press gesture with a minimum duration
init(minimumDuration: Double, maximumDistance: CGFloat)
Creates a long-press gesture with a minimum duration and a maximum distance that the interaction can move before the gesture fails.
var minimumDuration: Double
The minimum duration of the long press that must elapse before the gesture succeeds.
var maximumDistance: CGFloat
The maximum distance that the long press can move before the gesture fails.
Relationships
Conforms To
Gesture
See Also
Recognizing long press gestures
func onLongPressGesture(minimumDuration: Double, maximumDistance: CGFloat, perform: () -> Void, onPressingChanged: ((Bool) -> Void)?) -> some View
Adds an action to perform when this view recognizes a long press gesture.
func onLongPressGesture(minimumDuration: Double, perform: () -> Void, onPressingChanged: ((Bool) -> Void)?) -> some View
Adds an action to perform when this view recognizes a long press gesture.
func onLongTouchGesture(minimumDuration: Double, perform: () -> Void, onTouchingChanged: ((Bool) -> Void)?) -> some View
Adds an action to perform when this view recognizes a remote long touch gesture. A long touch gesture is when the finger is on the remote touch surface without actually pressing.

**Examples:**

```swift
struct LongPressGesture
```

```swift
struct LongPressGesture
```

```swift
struct LongPressGestureView: View {
    @GestureState private var isDetectingLongPress = false
    @State private var completedLongPress = false


    var longPress: some Gesture {
        LongPressGesture(minimumDuration: 3)
            .updating($isDetectingLongPress) { currentState, gestureState,
                    transaction in
                gestureState = currentState
                transaction.animation = Animation.easeIn(duration: 2.0)
            }
            .onEnded { finished in
                self.completedLongPress = finished
            }
    }


    var body: some View {
        Circle()
            .fill(self.isDetectingLongPress ?
                Color.red :
                (self.completedLongPress ? Color.green : Color.blue))
            .frame(width: 100, height: 100, alignment: .center)
            .gesture(longPress)
    }
}
```

```swift
struct LongPressGestureView: View {
    @GestureState private var isDetectingLongPress = false
    @State private var completedLongPress = false


    var longPress: some Gesture {
        LongPressGesture(minimumDuration: 3)
            .updating($isDetectingLongPress) { currentState, gestureState,
                    transaction in
                gestureState = currentState
                transaction.animation = Animation.easeIn(duration: 2.0)
            }
            .onEnded { finished in
                self.completedLongPress = finished
            }
    }


    var body: some View {
        Circle()
            .fill(self.isDetectingLongPress ?
                Color.red :
                (self.completedLongPress ? Color.green : Color.blue))
            .frame(width: 100, height: 100, alignment: .center)
            .gesture(longPress)
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/longpressgesture)

---

## MagnificationGesture

SwiftUI
MagnificationGesture
Deprecated
Structure
MagnificationGesture
A gesture that recognizes a magnification motion and tracks the amount of magnification.
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
struct MagnificationGesture

Deprecated

Use MagnifyGesture instead.

Topics
Creating the gesture
init(minimumScaleDelta: CGFloat)
Creates a magnification gesture with a given minimum delta for the gesture to start.
var minimumScaleDelta: CGFloat
The minimum required delta before the gesture starts.
Relationships
Conforms To
Gesture
See Also
Deprecated gestures
struct RotationGesture
A gesture that recognizes a rotation motion and tracks the angle of the rotation.
Deprecated

**Examples:**

```swift
struct MagnificationGesture
```

```swift
struct MagnificationGesture
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/magnificationgesture)

---

## RotationGesture

SwiftUI
RotationGesture
Deprecated
Structure
RotationGesture
A gesture that recognizes a rotation motion and tracks the angle of the rotation.
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
struct RotationGesture

Deprecated

Use RotateGesture instead.

Topics
Creating the gesture
init(minimumAngleDelta: Angle)
Creates a rotation gesture with a minimum delta for the gesture to start.
var minimumAngleDelta: Angle
The minimum delta required before the gesture succeeds.
Relationships
Conforms To
Gesture
See Also
Deprecated gestures
struct MagnificationGesture
A gesture that recognizes a magnification motion and tracks the amount of magnification.
Deprecated

**Examples:**

```swift
struct RotationGesture
```

```swift
struct RotationGesture
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/rotationgesture)

---

## DigitalCrownRotationalSensitivity

SwiftUI
DigitalCrownRotationalSensitivity
Enumeration
DigitalCrownRotationalSensitivity
The amount of Digital Crown rotation needed to move between two integer numbers.
watchOS 6.0+
enum DigitalCrownRotationalSensitivity
Overview

You may need to experiment to find the level of sensitivity that works for your use case.

Topics
Getting sensitivity options
case low
Low sensitivity.
case medium
Medium sensitivity.
case high
High sensitivity.
Relationships
Conforms To
Copyable
Equatable
Hashable
Sendable
SendableMetatype
See Also
Interacting with the Digital Crown
func digitalCrownAccessory(Visibility) -> some View
Specifies the visibility of Digital Crown accessory Views on Apple Watch.
func digitalCrownAccessory<Content>(content: () -> Content) -> some View
Places an accessory View next to the Digital Crown on Apple Watch.
func digitalCrownRotation<V>(Binding<V>, from: V, through: V, sensitivity: DigitalCrownRotationalSensitivity, isContinuous: Bool, isHapticFeedbackEnabled: Bool, onChange: (DigitalCrownEvent) -> Void, onIdle: () -> Void) -> some View
Tracks Digital Crown rotations by updating the specified binding.
func digitalCrownRotation<V>(Binding<V>, onChange: (DigitalCrownEvent) -> Void, onIdle: () -> Void) -> some View
Tracks Digital Crown rotations by updating the specified binding.
func digitalCrownRotation(detent:from:through:by:sensitivity:isContinuous:isHapticFeedbackEnabled:onChange:onIdle:)
Tracks Digital Crown rotations by updating the specified binding.
func digitalCrownRotation<V>(Binding<V>) -> some View
Tracks Digital Crown rotations by updating the specified binding.
func digitalCrownRotation<V>(Binding<V>, from: V, through: V, by: V.Stride?, sensitivity: DigitalCrownRotationalSensitivity, isContinuous: Bool, isHapticFeedbackEnabled: Bool) -> some View
Tracks Digital Crown rotations by updating the specified binding.
struct DigitalCrownEvent
An event emitted when the user rotates the Digital Crown.

**Examples:**

```swift
enum DigitalCrownRotationalSensitivity
```

```swift
enum DigitalCrownRotationalSensitivity
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/digitalcrownrotationalsensitivity)

---

