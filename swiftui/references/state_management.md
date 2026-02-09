# State Management

SwiftUI state management documentation.

---

## State

SwiftUI
State
Structure
State
A property wrapper type that can read and write a value managed by SwiftUI.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
@frozen @propertyWrapper
struct State<Value>
Mentioned in
Managing user interface state
Performing a search operation
Understanding the navigation stack
Overview

Use state as the single source of truth for a given value type that you store in a view hierarchy. Create a state value in an App, Scene, or View by applying the @State attribute to a property declaration and providing an initial value. Declare state as private to prevent setting it in a memberwise initializer, which can conflict with the storage management that SwiftUI provides:

struct PlayButton: View {
    @State private var isPlaying: Bool = false // Create the state.


    var body: some View {
        Button(isPlaying ? "Pause" : "Play") { // Read the state.
            isPlaying.toggle() // Write the state.
        }
    }
}


SwiftUI manages the property’s storage. When the value changes, SwiftUI updates the parts of the view hierarchy that depend on the value. To access a state’s underlying value, you use its wrappedValue property. However, as a shortcut Swift enables you to access the wrapped value by referring directly to the state instance. The above example reads and writes the isPlaying state property’s wrapped value by referring to the property directly.

Declare state as private in the highest view in the view hierarchy that needs access to the value. Then share the state with any subviews that also need access, either directly for read-only access, or as a binding for read-write access. You can safely mutate state properties from any thread.

Share state with subviews

If you pass a state property to a subview, SwiftUI updates the subview any time the value changes in the container view, but the subview can’t modify the value. To enable the subview to modify the state’s stored value, pass a Binding instead.

For example, you can remove the isPlaying state from the play button in the above example, and instead make the button take a binding:

struct PlayButton: View {
    @Binding var isPlaying: Bool // Play button now receives a binding.


    var body: some View {
        Button(isPlaying ? "Pause" : "Play") {
            isPlaying.toggle()
        }
    }
}


Then you can define a player view that declares the state and creates a binding to the state. Get the binding to the state value by accessing the state’s projectedValue, which you get by prefixing the property name with a dollar sign ($):

struct PlayerView: View {
    @State private var isPlaying: Bool = false // Create the state here now.


    var body: some View {
        VStack {
            PlayButton(isPlaying: $isPlaying) // Pass a binding.


            // ...
        }
    }
}


Like you do for a StateObject, declare State as private to prevent setting it in a memberwise initializer, which can conflict with the storage management that SwiftUI provides. Unlike a state object, always initialize state by providing a default value in the state’s declaration, as in the above examples. Use state only for storage that’s local to a view and its subviews.

Store observable objects

You can also store observable objects that you create with the Observable() macro in State; for example:

@Observable
class Library {
    var name = "My library of books"
    // ...
}


struct ContentView: View {
    @State private var library = Library()


    var body: some View {
        LibraryView(library: library)
    }
}


A State property always instantiates its default value when SwiftUI instantiates the view. For this reason, avoid side effects and performance-intensive work when initializing the default value. For example, if a view updates frequently, allocating a new default object each time the view initializes can become expensive. Instead, you can defer the creation of the object using the task(priority:_:) modifier, which is called only once when the view first appears:

struct ContentView: View {
    @State private var library: Library?

**Examples:**

```swift
@frozen @propertyWrapper
struct State<Value>
```

```swift
@frozen @propertyWrapper
struct State<Value>
```

```swift
struct PlayButton: View {
    @State private var isPlaying: Bool = false // Create the state.


    var body: some View {
        Button(isPlaying ? "Pause" : "Play") { // Read the state.
            isPlaying.toggle() // Write the state.
        }
    }
}
```

```swift
struct PlayButton: View {
    @State private var isPlaying: Bool = false // Create the state.


    var body: some View {
        Button(isPlaying ? "Pause" : "Play") { // Read the state.
            isPlaying.toggle() // Write the state.
        }
    }
}
```

```swift
struct PlayButton: View {
    @Binding var isPlaying: Bool // Play button now receives a binding.


    var body: some View {
        Button(isPlaying ? "Pause" : "Play") {
            isPlaying.toggle()
        }
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/state)

---

## Binding

SwiftUI
Binding
Structure
Binding
A property wrapper type that can read and write a value owned by a source of truth.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
@frozen @propertyWrapper @dynamicMemberLookup
struct Binding<Value>
Mentioned in
Performing a search operation
Understanding the navigation stack
Adding a search interface to your app
Managing user interface state
Managing search interface activation
Overview

Use a binding to create a two-way connection between a property that stores data, and a view that displays and changes the data. A binding connects a property to a source of truth stored elsewhere, instead of storing data directly. For example, a button that toggles between play and pause can create a binding to a property of its parent view using the Binding property wrapper.

struct PlayButton: View {
    @Binding var isPlaying: Bool


    var body: some View {
        Button(isPlaying ? "Pause" : "Play") {
            isPlaying.toggle()
        }
    }
}


The parent view declares a property to hold the playing state, using the State property wrapper to indicate that this property is the value’s source of truth.

struct PlayerView: View {
    var episode: Episode
    @State private var isPlaying: Bool = false


    var body: some View {
        VStack {
            Text(episode.title)
                .foregroundStyle(isPlaying ? .primary : .secondary)
            PlayButton(isPlaying: $isPlaying) // Pass a binding.
        }
    }
}


When PlayerView initializes PlayButton, it passes a binding of its state property into the button’s binding property. Applying the $ prefix to a property wrapped value returns its projectedValue, which for a state property wrapper returns a binding to the value.

Whenever the user taps the PlayButton, the PlayerView updates its isPlaying state.

A binding conforms to Sendable only if its wrapped value type also conforms to Sendable. It is always safe to pass a sendable binding between different concurrency domains. However, reading from or writing to a binding’s wrapped value from a different concurrency domain may or may not be safe, depending on how the binding was created. SwiftUI will issue a warning at runtime if it detects a binding being used in a way that may compromise data safety.

Note

To create bindings to properties of a type that conforms to the Observable protocol, use the Bindable property wrapper. For more information, see Migrating from the Observable Object protocol to the Observable macro.

Topics
Creating a binding
init(_:)
Creates a binding by projecting the base value to a hashable value.
init(projectedValue: Binding<Value>)
Creates a binding from the value of another binding.
init(get:set:)
Creates a binding with closures that read and write the binding value.
static func constant(Value) -> Binding<Value>
Creates a binding with an immutable value.
Getting the value
var wrappedValue: Value
The underlying value referenced by the binding variable.
var projectedValue: Binding<Value>
A projection of the binding value that returns a binding.
subscript<Subject>(dynamicMember _: WritableKeyPath<Value, Subject>) -> Binding<Subject>
Returns a binding to the resulting value of a given key path.
Managing changes
var id: Value.ID
The stable identity of the entity associated with this instance, corresponding to the id of the binding’s wrapped value.
func animation(Animation?) -> Binding<Value>
Specifies an animation to perform when the binding value changes.
func transaction(Transaction) -> Binding<Value>
Specifies a transaction for the binding.
var transaction: Transaction
The binding’s transaction.
Subscripts
subscript(_:)
Default Implementations
Identifiable Implementations
Relationships
Conforms To
BidirectionalCollection
Collection
Copyable
DynamicProperty
Conforms when Value conforms to Copyable and Escapable.

**Examples:**

```swift
@frozen @propertyWrapper @dynamicMemberLookup
struct Binding<Value>
```

```swift
@frozen @propertyWrapper @dynamicMemberLookup
struct Binding<Value>
```

```swift
struct PlayButton: View {
    @Binding var isPlaying: Bool


    var body: some View {
        Button(isPlaying ? "Pause" : "Play") {
            isPlaying.toggle()
        }
    }
}
```

```swift
struct PlayButton: View {
    @Binding var isPlaying: Bool


    var body: some View {
        Button(isPlaying ? "Pause" : "Play") {
            isPlaying.toggle()
        }
    }
}
```

```swift
struct PlayerView: View {
    var episode: Episode
    @State private var isPlaying: Bool = false


    var body: some View {
        VStack {
            Text(episode.title)
                .foregroundStyle(isPlaying ? .primary : .secondary)
            PlayButton(isPlaying: $isPlaying) // Pass a binding.
        }
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/binding)

---

## ObservableObject (Failed)

Error: Page.goto: Timeout 30000ms exceeded.
Call log:
  - navigating to "https://developer.apple.com/documentation/swiftui/observableobject", waiting until "networkidle"


[View Official Documentation](https://developer.apple.com/documentation/swiftui/observableobject)

---

## StateObject

SwiftUI
StateObject
Structure
StateObject
A property wrapper type that instantiates an observable object.
iOS 14.0+
iPadOS 14.0+
Mac Catalyst 14.0+
macOS 11.0+
tvOS 14.0+
visionOS 1.0+
watchOS 7.0+
@MainActor @frozen @propertyWrapper @preconcurrency
struct StateObject<ObjectType> where ObjectType : ObservableObject
Overview

Use a state object as the single source of truth for a reference type that you store in a view hierarchy. Create a state object in an App, Scene, or View by applying the @StateObject attribute to a property declaration and providing an initial value that conforms to the ObservableObject protocol. Declare state objects as private to prevent setting them from a memberwise initializer, which can conflict with the storage management that SwiftUI provides:

class DataModel: ObservableObject {
    @Published var name = "Some Name"
    @Published var isEnabled = false
}


struct MyView: View {
    @StateObject private var model = DataModel() // Create the state object.


    var body: some View {
        Text(model.name) // Updates when the data model changes.
        MySubView()
            .environmentObject(model)
    }
}


SwiftUI creates a new instance of the model object only once during the lifetime of the container that declares the state object. For example, SwiftUI doesn’t create a new instance if a view’s inputs change, but does create a new instance if the identity of a view changes. When published properties of the observable object change, SwiftUI updates any view that depends on those properties, like the Text view in the above example.

Note

If you need to store a value type, like a structure, string, or integer, use the State property wrapper instead. Also use State if you need to store a reference type that conforms to the Observable() protocol. To learn more about Observation in SwiftUI, see Managing model data in your app.

Share state objects with subviews

You can pass a state object into a subview through a property that has the ObservedObject attribute. Alternatively, add the object to the environment of a view hierarchy by applying the environmentObject(_:) modifier to a view, like MySubView in the above code. You can then read the object inside MySubView or any of its descendants using the EnvironmentObject attribute:

struct MySubView: View {
    @EnvironmentObject var model: DataModel


    var body: some View {
        Toggle("Enabled", isOn: $model.isEnabled)
    }
}


Get a Binding to the state object’s properties using the dollar sign ($) operator. Use a binding when you want to create a two-way connection. In the above code, the Toggle controls the model’s isEnabled value through a binding.

Initialize state objects using external data

When a state object’s initial state depends on data that comes from outside its container, you can call the object’s initializer explicitly from within its container’s initializer. For example, suppose the data model from the previous example takes a name input during initialization and you want to use a value for that name that comes from outside the view. You can do this with a call to the state object’s initializer inside an explicit initializer that you create for the view:

struct MyInitializableView: View {
    @StateObject private var model: DataModel


    init(name: String) {
        // SwiftUI ensures that the following initialization uses the
        // closure only once during the lifetime of the view, so
        // later changes to the view's name input have no effect.
        _model = StateObject(wrappedValue: DataModel(name: name))
    }


    var body: some View {
        VStack {
            Text("Name: \(model.name)")
        }
    }
}


Use caution when doing this. SwiftUI only initializes a state object the first time you call its initializer in a given view. This ensures that the object provides stable storage even as the view’s inputs change. However, it might result in unexpected behavior or unwanted side effects if you explicitly initialize the state object.

In the above example, if the name input to MyInitializableView changes, SwiftUI reruns the view’s initializer with the new value. However, SwiftUI runs the autoclosure that you provide to the state object’s initializer only the first time you call the state object’s initializer, so the model’s stored name value doesn’t change.

Explicit state object initialization works well when the external data that the object depends on doesn’t change for a given instance of the object’s container. For example, you can create two views with different constant names:

var body: some View {
    VStack {
        MyInitializableView(name: "Ravi")
        MyInitializableView(name: "Maria")
    }
}


Important

Even for a configurable state object, you still declare it as private. This ensures that you can’t accidentally set the parameter through a memberwise initializer of the view, because doing so can conflict with the framework’s storage management and produce unexpected results.


**Examples:**

```swift
@MainActor @frozen @propertyWrapper @preconcurrency
struct StateObject<ObjectType> where ObjectType : ObservableObject
```

```swift
@MainActor @frozen @propertyWrapper @preconcurrency
struct StateObject<ObjectType> where ObjectType : ObservableObject
```

```swift
ObservableObject
```

```swift
class DataModel: ObservableObject {
    @Published var name = "Some Name"
    @Published var isEnabled = false
}


struct MyView: View {
    @StateObject private var model = DataModel() // Create the state object.


    var body: some View {
        Text(model.name) // Updates when the data model changes.
        MySubView()
            .environmentObject(model)
    }
}
```

```swift
class DataModel: ObservableObject {
    @Published var name = "Some Name"
    @Published var isEnabled = false
}


struct MyView: View {
    @StateObject private var model = DataModel() // Create the state object.


    var body: some View {
        Text(model.name) // Updates when the data model changes.
        MySubView()
            .environmentObject(model)
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/stateobject)

---

## ObservedObject

SwiftUI
ObservedObject
Structure
ObservedObject
A property wrapper type that subscribes to an observable object and invalidates a view whenever the observable object changes.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
@MainActor @propertyWrapper @preconcurrency @frozen
struct ObservedObject<ObjectType> where ObjectType : ObservableObject
Overview

Add the @ObservedObject attribute to a parameter of a SwiftUI View when the input is an ObservableObject and you want the view to update when the object’s published properties change. You typically do this to pass a StateObject into a subview.

The following example defines a data model as an observable object, instantiates the model in a view as a state object, and then passes the instance to a subview as an observed object:

class DataModel: ObservableObject {
    @Published var name = "Some Name"
    @Published var isEnabled = false
}


struct MyView: View {
    @StateObject private var model = DataModel()


    var body: some View {
        Text(model.name)
        MySubView(model: model)
    }
}


struct MySubView: View {
    @ObservedObject var model: DataModel


    var body: some View {
        Toggle("Enabled", isOn: $model.isEnabled)
    }
}


When any published property of the observable object changes, SwiftUI updates any view that depends on the object. Subviews can also make updates to the model properties, like the Toggle in the above example, that propagate to other observers throughout the view hierarchy.

Don’t specify a default or initial value for the observed object. Use the attribute only for a property that acts as an input for a view, as in the above example.

Note

Don’t wrap objects conforming to the Observable protocol with @ObservedObject. SwiftUI automatically tracks dependencies to Observable objects used within body and updates dependent views when their data changes. Attempting to wrap an Observable object with @ObservedObject may cause a compiler error, because it requires that its wrapped object to conform to the ObservableObject protocol.

If the view needs a binding to a property of an Observable object in its body, wrap the object with the Bindable property wrapper instead; for example, @Bindable var model: DataModel. For more information, see Managing model data in your app.

Topics
Creating an observed object
init(wrappedValue: ObjectType)
Creates an observed object with an initial wrapped value.
init(initialValue: ObjectType)
Creates an observed object with an initial value.
Getting the value
var wrappedValue: ObjectType
The underlying value that the observed object references.
var projectedValue: ObservedObject<ObjectType>.Wrapper
A projection of the observed object that creates bindings to its properties.
struct Wrapper
A wrapper of the underlying observable object that can create bindings to its properties.
Relationships
Conforms To
DynamicProperty
Sendable
SendableMetatype
See Also
Creating model data
Managing model data in your app
Create connections between your app’s data model and views.
Migrating from the Observable Object protocol to the Observable macro
Update your existing app to leverage the benefits of Observation in Swift.
macro Observable()
Defines and implements conformance of the Observable protocol.
Monitoring data changes in your app
Show changes to data in your app’s user interface by using observable objects.
struct StateObject
A property wrapper type that instantiates an observable object.
protocol ObservableObject
A type of object with a publisher that emits before the object has changed.

**Examples:**

```swift
@MainActor @propertyWrapper @preconcurrency @frozen
struct ObservedObject<ObjectType> where ObjectType : ObservableObject
```

```swift
@MainActor @propertyWrapper @preconcurrency @frozen
struct ObservedObject<ObjectType> where ObjectType : ObservableObject
```

```swift
ObservableObject
```

```swift
class DataModel: ObservableObject {
    @Published var name = "Some Name"
    @Published var isEnabled = false
}


struct MyView: View {
    @StateObject private var model = DataModel()


    var body: some View {
        Text(model.name)
        MySubView(model: model)
    }
}


struct MySubView: View {
    @ObservedObject var model: DataModel


    var body: some View {
        Toggle("Enabled", isOn: $model.isEnabled)
    }
}
```

```swift
class DataModel: ObservableObject {
    @Published var name = "Some Name"
    @Published var isEnabled = false
}


struct MyView: View {
    @StateObject private var model = DataModel()


    var body: some View {
        Text(model.name)
        MySubView(model: model)
    }
}


struct MySubView: View {
    @ObservedObject var model: DataModel


    var body: some View {
        Toggle("Enabled", isOn: $model.isEnabled)
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/observedobject)

---

## EnvironmentObject

SwiftUI
EnvironmentObject
Structure
EnvironmentObject
A property wrapper type for an observable object that a parent or ancestor view supplies.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
@MainActor @frozen @propertyWrapper @preconcurrency
struct EnvironmentObject<ObjectType> where ObjectType : ObservableObject
Overview

An environment object invalidates the current view whenever the observable object that conforms to ObservableObject changes. If you declare a property as an environment object, be sure to set a corresponding model object on an ancestor view by calling its environmentObject(_:) modifier.

Note

If your observable object conforms to the Observable protocol, use Environment instead of EnvironmentObject and set the model object in an ancestor view by calling its environment(_:) or environment(_:_:) modifiers.

Topics
Creating an environment object
init()
Creates an environment object.
Getting the value
var wrappedValue: ObjectType
The underlying value referenced by the environment object.
var projectedValue: EnvironmentObject<ObjectType>.Wrapper
A projection of the environment object that creates bindings to its properties using dynamic member lookup.
struct Wrapper
A wrapper of the underlying environment object that can create bindings to its properties using dynamic member lookup.
Relationships
Conforms To
DynamicProperty
Sendable
SendableMetatype
See Also
Distributing model data throughout your app
func environmentObject<T>(T) -> some View
Supplies an observable object to a view’s hierarchy.
func environmentObject<T>(T) -> some Scene
Supplies an ObservableObject to a view subhierarchy.

**Examples:**

```swift
@MainActor @frozen @propertyWrapper @preconcurrency
struct EnvironmentObject<ObjectType> where ObjectType : ObservableObject
```

```swift
@MainActor @frozen @propertyWrapper @preconcurrency
struct EnvironmentObject<ObjectType> where ObjectType : ObservableObject
```

```swift
ObservableObject
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/environmentobject)

---

## Environment

SwiftUI
Environment
Structure
Environment
A property wrapper that reads a value from a view’s environment.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
@frozen @propertyWrapper
struct Environment<Value>
Mentioned in
Building and customizing the menu bar with SwiftUI
Managing search interface activation
Migrating to the SwiftUI life cycle
Overview

Use the Environment property wrapper to read a value stored in a view’s environment. Indicate the value to read using an EnvironmentValues key path in the property declaration. For example, you can create a property that reads the color scheme of the current view using the key path of the colorScheme property:

@Environment(\.colorScheme) var colorScheme: ColorScheme


You can condition a view’s content on the associated value, which you read from the declared property’s wrappedValue. As with any property wrapper, you access the wrapped value by directly referring to the property:

if colorScheme == .dark { // Checks the wrapped value.
    DarkContent()
} else {
    LightContent()
}


If the value changes, SwiftUI updates any parts of your view that depend on the value. For example, that might happen in the above example if the user changes the Appearance settings.

You can use this property wrapper to read — but not set — an environment value. SwiftUI updates some environment values automatically based on system settings and provides reasonable defaults for others. You can override some of these, as well as set custom environment values that you define, using the environment(_:_:) view modifier.

For the complete list of environment values SwiftUI provides, see the properties of the EnvironmentValues structure. For information about creating custom environment values, see the Entry() macro.

Get an observable object

You can also use Environment to get an observable object from a view’s environment. The observable object must conform to the Observable protocol, and your app must set the object in the environment using the object itself or a key path.

To set the object in the environment using the object itself, use the environment(_:) modifier:

@Observable
class Library {
    var books: [Book] = [Book(), Book(), Book()]


    var availableBooksCount: Int {
        books.filter(\.isAvailable).count
    }
}


@main
struct BookReaderApp: App {
    @State private var library = Library()


    var body: some Scene {
        WindowGroup {
            LibraryView()
                .environment(library)
        }
    }
}


To get the observable object using its type, create a property and provide the Environment property wrapper the object’s type:

struct LibraryView: View {
    @Environment(Library.self) private var library


    var body: some View {
        // ...
    }
}


By default, reading an object from the environment returns a non-optional object when using the object type as the key. This default behavior assumes that a view in the current hierarchy previously stored a non-optional instance of the type using the environment(_:) modifier. If a view attempts to retrieve an object using its type and that object isn’t in the environment, SwiftUI throws an exception.

In cases where there is no guarantee that an object is in the environment, retrieve an optional version of the object as shown in the following code. If the object isn’t available the environment, SwiftUI returns nil instead of throwing an exception.

@Environment(Library.self) private var library: Library?

Get an observable object using a key path

To set the object with a key path, use the environment(_:_:) modifier:

@Observable
class Library {
    var books: [Book] = [Book(), Book(), Book()]


    var availableBooksCount: Int {
        books.filter(\.isAvailable).count

**Examples:**

```swift
@frozen @propertyWrapper
struct Environment<Value>
```

```swift
@frozen @propertyWrapper
struct Environment<Value>
```

```swift
@Environment(\.colorScheme) var colorScheme: ColorScheme
```

```swift
@Environment(\.colorScheme) var colorScheme: ColorScheme
```

```swift
if colorScheme == .dark { // Checks the wrapped value.
    DarkContent()
} else {
    LightContent()
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/environment)

---

## SceneStorage

SwiftUI
SceneStorage
Structure
SceneStorage
A property wrapper type that reads and writes to persisted, per-scene storage.
iOS 14.0+
iPadOS 14.0+
Mac Catalyst 14.0+
macOS 11.0+
tvOS 14.0+
visionOS 1.0+
watchOS 7.0+
@frozen @propertyWrapper
struct SceneStorage<Value>
Overview

You use SceneStorage when you need automatic state restoration of the value. SceneStorage works very similar to State, except its initial value is restored by the system if it was previously saved, and the value is shared with other SceneStorage variables in the same scene.

The system manages the saving and restoring of SceneStorage on your behalf. The underlying data that backs SceneStorage is not available to you, so you must access it via the SceneStorage property wrapper. The system makes no guarantees as to when and how often the data will be persisted.

Each Scene has its own notion of SceneStorage, so data is not shared between scenes.

Ensure that the data you use with SceneStorage is lightweight. Data of a large size, such as model data, should not be stored in SceneStorage, as poor performance may result.

If the Scene is explicitly destroyed (e.g. the switcher snapshot is destroyed on iPadOS or the window is closed on macOS), the data is also destroyed. Do not use SceneStorage with sensitive data.

Topics
Storing a value
init(wrappedValue:_:)
Creates a property that can save and restore an integer, transforming it to a RawRepresentable data type.
init(_:)
Creates a property that can save and restore an Optional boolean.
Getting the value
var wrappedValue: Value
The underlying value referenced by the state variable.
var projectedValue: Binding<Value>
A binding to the state value.
Initializers
init(wrappedValue: Value, String, store: UserDefaults?)
Creates a property that can save and restore tab sidebar customizations.
Relationships
Conforms To
DynamicProperty
Sendable
SendableMetatype
See Also
Saving state across app launches
Restoring your app’s state with SwiftUI
Provide app continuity for users by preserving their current activities.
func defaultAppStorage(UserDefaults) -> some View
The default store used by AppStorage contained within the view.
struct AppStorage
A property wrapper type that reflects a value from UserDefaults and invalidates a view on a change in value in that user default.

**Examples:**

```swift
@frozen @propertyWrapper
struct SceneStorage<Value>
```

```swift
@frozen @propertyWrapper
struct SceneStorage<Value>
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/scenestorage)

---

## FocusState

SwiftUI
FocusState
Structure
FocusState
A property wrapper type that can read and write a value that SwiftUI updates as the placement of focus within the scene changes.
iOS 15.0+
iPadOS 15.0+
Mac Catalyst 15.0+
macOS 12.0+
tvOS 15.0+
visionOS 1.0+
watchOS 8.0+
@frozen @propertyWrapper
struct FocusState<Value> where Value : Hashable
Overview

Use this property wrapper in conjunction with focused(_:equals:) and focused(_:) to describe views whose appearance and contents relate to the location of focus in the scene. When focus enters the modified view, the wrapped value of this property updates to match a given prototype value. Similarly, when focus leaves, the wrapped value of this property resets to nil or false. Setting the property’s value programmatically has the reverse effect, causing focus to move to the view associated with the updated value.

In the following example of a simple login screen, when the user presses the Sign In button and one of the fields is still empty, focus moves to that field. Otherwise, the sign-in process proceeds.

struct LoginForm {
    enum Field: Hashable {
        case username
        case password
    }


    @State private var username = ""
    @State private var password = ""
    @FocusState private var focusedField: Field?


    var body: some View {
        Form {
            TextField("Username", text: $username)
                .focused($focusedField, equals: .username)


            SecureField("Password", text: $password)
                .focused($focusedField, equals: .password)


            Button("Sign In") {
                if username.isEmpty {
                    focusedField = .username
                } else if password.isEmpty {
                    focusedField = .password
                } else {
                    handleLogin(username, password)
                }
            }
        }
    }
}


To allow for cases where focus is completely absent from a view tree, the wrapped value must be either an optional or a Boolean. Set the focus binding to false or nil as appropriate to remove focus from all bound fields. You can also use this to remove focus from a TextField and thereby dismiss the keyboard.

Avoid ambiguous focus bindings

The same view can have multiple focus bindings. In the following example, setting focusedField to either name or fullName causes the field to receive focus:

struct ContentView: View {
    enum Field: Hashable {
        case name
        case fullName
    }
    @FocusState private var focusedField: Field?


    var body: some View {
        TextField("Full Name", ...)
            .focused($focusedField, equals: .name)
            .focused($focusedField, equals: .fullName)
    }
}


On the other hand, binding the same value to two views is ambiguous. In the following example, two separate fields bind focus to the name value:

struct ContentView: View {
    enum Field: Hashable {
        case name
        case fullName
    }
    @FocusState private var focusedField: Field?


    var body: some View {
        TextField("Name", ...)
            .focused($focusedField, equals: .name)
        TextField("Full Name", ...)
            .focused($focusedField, equals: .name) // incorrect re-use of .name
    }
}


If the user moves focus to either field, the focusedField binding updates to name. However, if the app programmatically sets the value to name, SwiftUI chooses the first candidate, which in this case is the “Name” field. SwiftUI also emits a runtime warning in this case, since the repeated binding is likely a programmer error.

Nest focusable views

**Examples:**

```swift
@frozen @propertyWrapper
struct FocusState<Value> where Value : Hashable
```

```swift
@frozen @propertyWrapper
struct FocusState<Value> where Value : Hashable
```

```swift
struct LoginForm {
    enum Field: Hashable {
        case username
        case password
    }


    @State private var username = ""
    @State private var password = ""
    @FocusState private var focusedField: Field?


    var body: some View {
        Form {
            TextField("Username", text: $username)
                .focused($focusedField, equals: .username)


            SecureField("Password", text: $password)
                .focused($focusedField, equals: .password)


            Button("Sign In") {
                if username.isEmpty {
                    focusedField = .username
                } else if password.isEmpty {
                    focusedField = .password
                } else {
                    handleLogin(username, password)
                }
            }
        }
    }
}
```

```swift
struct LoginForm {
    enum Field: Hashable {
        case username
        case password
    }


    @State private var username = ""
    @State private var password = ""
    @FocusState private var focusedField: Field?


    var body: some View {
        Form {
            TextField("Username", text: $username)
                .focused($focusedField, equals: .username)


            SecureField("Password", text: $password)
                .focused($focusedField, equals: .password)


            Button("Sign In") {
                if username.isEmpty {
                    focusedField = .username
                } else if password.isEmpty {
                    focusedField = .password
                } else {
                    handleLogin(username, password)
                }
            }
        }
    }
}
```

```swift
struct ContentView: View {
    enum Field: Hashable {
        case name
        case fullName
    }
    @FocusState private var focusedField: Field?


    var body: some View {
        TextField("Full Name", ...)
            .focused($focusedField, equals: .name)
            .focused($focusedField, equals: .fullName)
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/focusstate)

---

## Observable (Failed)

Error: Page.goto: Timeout 30000ms exceeded.
Call log:
  - navigating to "https://developer.apple.com/documentation/swiftui/observable", waiting until "networkidle"


[View Official Documentation](https://developer.apple.com/documentation/swiftui/observable)

---

