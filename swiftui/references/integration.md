# Integration

SwiftUI integration protocols for bridging UIKit and AppKit views into SwiftUI.

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
## WKInterfaceObjectRepresentable

SwiftUI
WKInterfaceObjectRepresentable
Protocol
WKInterfaceObjectRepresentable
A view that represents a WatchKit interface object.
watchOS 6.0+
@MainActor @preconcurrency
protocol WKInterfaceObjectRepresentable : View where Self.Body == Never
Overview

Use a WKInterfaceObjectRepresentable instance to create and manage a WKInterfaceObject in your SwiftUI interface. Adopt this protocol in one of your app’s custom instances, and use its methods to create, update, and tear down your interface object. The creation and update processes parallel the behavior of SwiftUI views, and you use them to configure your interface object with your app’s current state information. Use the teardown process to remove your interface object cleanly from your SwiftUI. For example, you might use the teardown process to notify other parts of your app that the interface object is disappearing.

To add your interface object into your SwiftUI interface, create your WKInterfaceObjectRepresentable instance and add it to your SwiftUI interface. The system calls the methods of your representable instance at appropriate times to create and update the interface object.

The system doesn’t automatically communicate changes occurring within your interface object to other parts of your SwiftUI interface. When you want your interface object to coordinate with other SwiftUI views, you must provide a Coordinator instance to facilitate those interactions. For example, you use a coordinator to forward target-action and delegate messages from your interface object to any SwiftUI views.

Topics
Creating and updating the interface object
func makeWKInterfaceObject(context: Self.Context) -> Self.WKInterfaceObjectType
Creates a WatchKit interface object and configures its initial state.

Required

func updateWKInterfaceObject(Self.WKInterfaceObjectType, context: Self.Context)
Updates the presented WatchKit interface object (and its coordinator) to the latest configuration.

Required

typealias Context
Cleaning up the interface object
static func dismantleWKInterfaceObject(Self.WKInterfaceObjectType, coordinator: Self.Coordinator)
Cleans up the presented WatchKit interface object (and its coordinator) in anticipation of their removal.

Required Default implementation provided.

Providing a custom coordinator object
func makeCoordinator() -> Self.Coordinator
Creates the custom instance that you use to communicate changes from your interface object to other parts of your SwiftUI interface.

Required Default implementation provided.

associatedtype Coordinator = Void
A type to coordinate with the WatchKit interface object.

Required

associatedtype WKInterfaceObjectType : WKInterfaceObject
The type of WatchKit interface object to be presented.

Required

Relationships
Inherits From
View
See Also
Adding WatchKit views to SwiftUI view hierarchies
struct WKInterfaceObjectRepresentableContext
Contextual information about the state of the system that you use to create and update your WatchKit interface object.

**Examples:**

```swift
@MainActor @preconcurrency
protocol WKInterfaceObjectRepresentable : View where Self.Body == Never
```

```swift
@MainActor @preconcurrency
protocol WKInterfaceObjectRepresentable : View where Self.Body == Never
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/wkinterfaceobjectrepresentable)

