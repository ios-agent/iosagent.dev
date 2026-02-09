# Animations

SwiftUI animations documentation.

---

## Animation

SwiftUI
Animation
Structure
Animation
The way a view changes over time to create a smooth visual transition from one state to another.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
@frozen
struct Animation
Mentioned in
Unifying your app’s animations
Overview

An Animation provides a visual transition of a view when a state value changes from one value to another. The characteristics of this transition vary according to the animation type. For instance, a linear animation provides a mechanical feel to the animation because its speed is consistent from start to finish. In contrast, an animation that uses easing, like easeOut, offers a more natural feel by varying the acceleration of the animation.

To apply an animation to a view, add the animation(_:value:) modifier, and specify both an animation type and the value to animate. For instance, the Circle view in the following code performs an easeIn animation each time the state variable scale changes:

struct ContentView: View {
    @State private var scale = 0.5


    var body: some View {
        VStack {
            Circle()
                .scaleEffect(scale)
                .animation(.easeIn, value: scale)
            HStack {
                Button("+") { scale += 0.1 }
                Button("-") { scale -= 0.1 }
            }
        }
        .padding()
    }

Play

When the value of scale changes, the modifier scaleEffect(_:anchor:) resizes Circle according to the new value. SwiftUI can animate the transition between sizes because Circle conforms to the Shape protocol. Shapes in SwiftUI conform to the Animatable protocol, which describes how to animate a property of a view.

In addition to adding an animation to a view, you can also configure the animation by applying animation modifiers to the animation type. For example, you can:

Delay the start of the animation by using the delay(_:) modifier.

Repeat the animation by using the repeatCount(_:autoreverses:) or repeatForever(autoreverses:) modifiers.

Change the speed of the animation by using the speed(_:) modifier.

For example, the Circle view in the following code repeats the easeIn animation three times by using the repeatCount(_:autoreverses:) modifier:

struct ContentView: View {
    @State private var scale = 0.5


    var body: some View {
        VStack {
            Circle()
                .scaleEffect(scale)
                .animation(.easeIn.repeatCount(3), value: scale)
            HStack {
                Button("+") { scale += 0.1 }
                Button("-") { scale -= 0.1 }
            }
        }
        .padding()
    }
}

Play

A view can also perform an animation when a binding value changes. To specify the animation type on a binding, call its animation(_:) method. For example, the view in the following code performs a linear animation, moving the box truck between the leading and trailing edges of the view. The truck moves each time a person clicks the Toggle control, which changes the value of the $isTrailing binding.

struct ContentView: View {
    @State private var isTrailing = false


    var body: some View {
       VStack(alignment: isTrailing ? .trailing : .leading) {
            Image(systemName: "box.truck")
                .font(.system(size: 64))


            Toggle("Move to trailing edge",
                   isOn: $isTrailing.animation(.linear))
        }
    }
}

Play
Topics
Getting the default animation
static let `default`: Animation
A default animation instance.
Getting linear animations
static var linear: Animation
An animation that moves at a constant speed.
static func linear(duration: TimeInterval) -> Animation

**Examples:**

```swift
@frozen
struct Animation
```

```swift
@frozen
struct Animation
```

```swift
struct ContentView: View {
    @State private var scale = 0.5


    var body: some View {
        VStack {
            Circle()
                .scaleEffect(scale)
                .animation(.easeIn, value: scale)
            HStack {
                Button("+") { scale += 0.1 }
                Button("-") { scale -= 0.1 }
            }
        }
        .padding()
    }
```

```swift
struct ContentView: View {
    @State private var scale = 0.5


    var body: some View {
        VStack {
            Circle()
                .scaleEffect(scale)
                .animation(.easeIn, value: scale)
            HStack {
                Button("+") { scale += 0.1 }
                Button("-") { scale -= 0.1 }
            }
        }
        .padding()
    }
```

```swift
struct ContentView: View {
    @State private var scale = 0.5


    var body: some View {
        VStack {
            Circle()
                .scaleEffect(scale)
                .animation(.easeIn.repeatCount(3), value: scale)
            HStack {
                Button("+") { scale += 0.1 }
                Button("-") { scale -= 0.1 }
            }
        }
        .padding()
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/animation)

---

## Transition

SwiftUI
Transition
Protocol
Transition
A description of view changes to apply when a view is added to and removed from the view hierarchy.
iOS 17.0+
iPadOS 17.0+
Mac Catalyst 17.0+
macOS 14.0+
tvOS 17.0+
visionOS 1.0+
watchOS 10.0+
@MainActor @preconcurrency
protocol Transition
Overview

A transition should generally be made by applying one or more modifiers to the content. For symmetric transitions, the isIdentity property on phase can be used to change the properties of modifiers. For asymmetric transitions, the phase itself can be used to change those properties. Transitions should not use any identity-affecting changes like .id, if, and switch on the content, since doing so would reset the state of the view they’re applied to, causing wasted work and potentially surprising behavior when it appears and disappears.

The following code defines a transition that can be used to change the opacity and rotation when a view appears and disappears.

struct RotatingFadeTransition: Transition {
    func body(content: Content, phase: TransitionPhase) -> some View {
        content
          .opacity(phase.isIdentity ? 1.0 : 0.0)
          .rotationEffect(phase.rotation)
    }
}
extension TransitionPhase {
    fileprivate var rotation: Angle {
        switch self {
        case .willAppear: return .degrees(30)
        case .identity: return .zero
        case .didDisappear: return .degrees(-30)
        }
    }
}


A type conforming to this protocol inherits @preconcurrency @MainActor isolation from the protocol if the conformance is included in the type’s base declaration:

struct MyCustomType: Transition {
    // `@preconcurrency @MainActor` isolation by default
}


Isolation to the main actor is the default, but it’s not required. Declare the conformance in an extension to opt out of main actor isolation:

extension MyCustomType: Transition {
    // `nonisolated` by default
}


See Also: TransitionPhase

See Also: AnyTransition

Topics
Getting built-in transitions
static var blurReplace: BlurReplaceTransition
A transition that animates the insertion or removal of a view by combining blurring and scaling effects.
static func blurReplace(BlurReplaceTransition.Configuration) -> Self
A transition that animates the insertion or removal of a view by combining blurring and scaling effects.
static var identity: IdentityTransition
A transition that returns the input view, unmodified, as the output view.
static func move(edge: Edge) -> Self
Returns a transition that moves the view away, towards the specified edge of the view.
static func offset(CGSize) -> Self
Returns a transition that offset the view by the specified amount.
static func offset(x: CGFloat, y: CGFloat) -> Self
Returns a transition that offset the view by the specified x and y values.
static var opacity: OpacityTransition
A transition from transparent to opaque on insertion, and from opaque to transparent on removal.
static func push(from: Edge) -> Self
Creates a transition that when added to a view will animate the view’s insertion by moving it in from the specified edge while fading it in, and animate its removal by moving it out towards the opposite edge and fading it out.
static var scale: ScaleTransition
Returns a transition that scales the view.
static func scale(Double, anchor: UnitPoint) -> Self
Returns a transition that scales the view by the specified amount.
static var slide: SlideTransition
A transition that inserts by moving in from the leading edge, and removes by moving out towards the trailing edge.
static var symbolEffect: SymbolEffectTransition
A transition that applies the default symbol effect transition to symbol images within the inserted or removed view hierarchy. Other views are unaffected by this transition.
static func symbolEffect<T>(T, options: SymbolEffectOptions) -> SymbolEffectTransition
Creates a transition that applies the provided effect to symbol images within the inserted or removed view hierarchy. Other views are unaffected by this transition.
Configuring a transition
func animation(Animation?) -> some Transition
Attaches an animation to this transition.
static var properties: TransitionProperties
Returns the properties this transition type has.

Required Default implementation provided.

Using a transition
func apply<V>(content: V, phase: TransitionPhase) -> some View
func combined<T>(with: T) -> some Transition
Creating a custom transition
func body(content: Self.Content, phase: TransitionPhase) -> Self.Body
Gets the current body of the caller.

Required

**Examples:**

```swift
@MainActor @preconcurrency
protocol Transition
```

```swift
@MainActor @preconcurrency
protocol Transition
```

```swift
struct RotatingFadeTransition: Transition {
    func body(content: Content, phase: TransitionPhase) -> some View {
        content
          .opacity(phase.isIdentity ? 1.0 : 0.0)
          .rotationEffect(phase.rotation)
    }
}
extension TransitionPhase {
    fileprivate var rotation: Angle {
        switch self {
        case .willAppear: return .degrees(30)
        case .identity: return .zero
        case .didDisappear: return .degrees(-30)
        }
    }
}
```

```swift
struct RotatingFadeTransition: Transition {
    func body(content: Content, phase: TransitionPhase) -> some View {
        content
          .opacity(phase.isIdentity ? 1.0 : 0.0)
          .rotationEffect(phase.rotation)
    }
}
extension TransitionPhase {
    fileprivate var rotation: Angle {
        switch self {
        case .willAppear: return .degrees(30)
        case .identity: return .zero
        case .didDisappear: return .degrees(-30)
        }
    }
}
```

```swift
struct MyCustomType: Transition {
    // `@preconcurrency @MainActor` isolation by default
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/transition)

---

## AnyTransition

SwiftUI
AnyTransition
Structure
AnyTransition
A type-erased transition.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
@frozen
struct AnyTransition
Overview

See Also: Transition

Topics
Getting built-in transitions
static var identity: AnyTransition
A transition that returns the input view, unmodified, as the output view.
static func move(edge: Edge) -> AnyTransition
Returns a transition that moves the view away, towards the specified edge of the view.
static func offset(CGSize) -> AnyTransition
static func offset(x: CGFloat, y: CGFloat) -> AnyTransition
static let opacity: AnyTransition
A transition from transparent to opaque on insertion, and from opaque to transparent on removal.
static func push(from: Edge) -> AnyTransition
Creates a transition that when added to a view will animate the view’s insertion by moving it in from the specified edge while fading it in, and animate its removal by moving it out towards the opposite edge and fading it out.
static var scale: AnyTransition
Returns a transition that scales the view.
static func scale(scale: CGFloat, anchor: UnitPoint) -> AnyTransition
Returns a transition that scales the view by the specified amount.
static var slide: AnyTransition
A transition that inserts by moving in from the leading edge, and removes by moving out towards the trailing edge.
Combining and configuring transitions
func animation(Animation?) -> AnyTransition
Attaches an animation to this transition.
static func asymmetric(insertion: AnyTransition, removal: AnyTransition) -> AnyTransition
Provides a composite transition that uses a different transition for insertion versus removal.
func combined(with: AnyTransition) -> AnyTransition
Combines this transition with another, returning a new transition that is the result of both transitions being applied.
Creating a custom transition
init<T>(T)
Create an instance that type-erases transition.
static func modifier<E>(active: E, identity: E) -> AnyTransition
Returns a transition defined between an active modifier and an identity modifier.
See Also
Defining transitions
func transition(_:)
Associates a transition with the view.
protocol Transition
A description of view changes to apply when a view is added to and removed from the view hierarchy.
struct TransitionProperties
The properties a Transition can have.
enum TransitionPhase
An indication of which the current stage of a transition.
struct AsymmetricTransition
A composite Transition that uses a different transition for insertion versus removal.
func contentTransition(ContentTransition) -> some View
Modifies the view to use a given transition as its method of animating changes to the contents of its views.
var contentTransition: ContentTransition
The current method of animating the contents of views.
var contentTransitionAddsDrawingGroup: Bool
A Boolean value that controls whether views that render content transitions use GPU-accelerated rendering.
struct ContentTransition
A kind of transition that applies to the content within a single view, rather than to the insertion or removal of a view.
struct PlaceholderContentView
A placeholder used to construct an inline modifier, transition, or other helper type.
func navigationTransition(some NavigationTransition) -> some View
Sets the navigation transition style for this view.
protocol NavigationTransition
A type that defines the transition to use when navigating to a view.
func matchedTransitionSource(id: some Hashable, in: Namespace.ID) -> some View
Identifies this view as the source of a navigation transition, such as a zoom transition.
func matchedTransitionSource(id: some Hashable, in: Namespace.ID, configuration: (EmptyMatchedTransitionSourceConfiguration) -> some MatchedTransitionSourceConfiguration) -> some View
Identifies this view as the source of a navigation transition, such as a zoom transition.
protocol MatchedTransitionSourceConfiguration
A configuration that defines the appearance of a matched transition source.

**Examples:**

```swift
@frozen
struct AnyTransition
```

```swift
@frozen
struct AnyTransition
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/anytransition)

---

