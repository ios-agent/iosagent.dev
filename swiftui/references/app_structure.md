# App Structure

SwiftUI app structure documentation.

---

## Scene

SwiftUI
Scene
Protocol
Scene
A part of an app’s user interface with a life cycle managed by the system.
iOS 14.0+
iPadOS 14.0+
Mac Catalyst 14.0+
macOS 11.0+
tvOS 14.0+
visionOS 1.0+
watchOS 7.0+
@MainActor @preconcurrency
protocol Scene
Mentioned in
Building and customizing the menu bar with SwiftUI
Migrating to the SwiftUI life cycle
Overview

You create an App by combining one or more instances that conform to the Scene protocol in the app’s body. You can use the built-in scenes that SwiftUI provides, like WindowGroup, along with custom scenes that you compose from other scenes. To create a custom scene, declare a type that conforms to the Scene protocol. Implement the required body computed property and provide the content for your custom scene:

struct MyScene: Scene {
    var body: some Scene {
        WindowGroup {
            MyRootView()
        }
    }
}


A scene acts as a container for a view hierarchy that you want to display to the user. The system decides when and how to present the view hierarchy in the user interface in a way that’s platform-appropriate and dependent on the current state of the app. For example, for the window group shown above, the system lets the user create or remove windows that contain MyRootView on platforms like macOS and iPadOS. On other platforms, the same view hierarchy might consume the entire display when active.

Read the scenePhase environment value from within a scene or one of its views to check whether a scene is active or in some other state. You can create a property that contains the scene phase, which is one of the values in the ScenePhase enumeration, using the Environment attribute:

struct MyScene: Scene {
    @Environment(\.scenePhase) private var scenePhase


    // ...
}


The Scene protocol provides scene modifiers, defined as protocol methods with default implementations, that you use to configure a scene. For example, you can use the onChange(of:perform:) modifier to trigger an action when a value changes. The following code empties a cache when all of the scenes in the window group have moved to the background:

struct MyScene: Scene {
    @Environment(\.scenePhase) private var scenePhase
    @StateObject private var cache = DataCache()


    var body: some Scene {
        WindowGroup {
            MyRootView()
        }
        .onChange(of: scenePhase) { newScenePhase in
            if newScenePhase == .background {
                cache.empty()
            }
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

Topics
Creating a scene
var body: Self.Body
The content and behavior of the scene.

Required

associatedtype Body : Scene
The type of scene that represents the body of this scene.

Required

Watching for changes
func onChange(of:initial:_:)
Adds an action to perform when the given value changes.
func handlesExternalEvents(matching: Set<String>) -> some Scene
Specifies the external events for which SwiftUI opens a new instance of the modified scene.
Creating background tasks
func backgroundTask<D, R>(BackgroundTask<D, R>, action: (D) async -> R) -> some Scene
Runs the specified action when the system provides a background task.
Managing app storage
func defaultAppStorage(UserDefaults) -> some Scene
The default store used by AppStorage contained within the scene and its view content.
Setting commands
func commands<Content>(content: () -> Content) -> some Scene

**Examples:**

```swift
@MainActor @preconcurrency
protocol Scene
```

```swift
@MainActor @preconcurrency
protocol Scene
```

```swift
struct MyScene: Scene {
    var body: some Scene {
        WindowGroup {
            MyRootView()
        }
    }
}
```

```swift
struct MyScene: Scene {
    var body: some Scene {
        WindowGroup {
            MyRootView()
        }
    }
}
```

```swift
struct MyScene: Scene {
    @Environment(\.scenePhase) private var scenePhase


    // ...
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/scene)

---

## WindowGroup

SwiftUI
WindowGroup
Structure
WindowGroup
A scene that presents a group of identically structured windows.
iOS 14.0+
iPadOS 14.0+
Mac Catalyst 14.0+
macOS 11.0+
tvOS 14.0+
visionOS 1.0+
watchOS 7.0+
struct WindowGroup<Content> where Content : View
Mentioned in
Building and customizing the menu bar with SwiftUI
Overview

Use a WindowGroup as a container for a view hierarchy that your app presents. The hierarchy that you declare as the group’s content serves as a template for each window that the app creates from that group:

@main
struct Mail: App {
    var body: some Scene {
        WindowGroup {
            MailViewer() // Define a view hierarchy for the window.
        }
    }
}


SwiftUI takes care of certain platform-specific behaviors. For example, on platforms that support it, like macOS and iPadOS, people can open more than one window from the group simultaneously. In macOS, people can gather open windows together in a tabbed interface. Also in macOS, window groups automatically provide commands for standard window management.

Important

To enable an iPadOS app to simultaneously display multiple windows, be sure to include the UIApplicationSupportsMultipleScenes key with a value of true in the UIApplicationSceneManifest dictionary of your app’s Information Property List.

Every window in the group maintains independent state. For example, the system allocates new storage for any State or StateObject variables instantiated by the scene’s view hierarchy for each window that it creates.

For document-based apps, use DocumentGroup to define windows instead.

Open windows programmatically

If you initialize a window group with an identifier, a presentation type, or both, you can programmatically open a window from the group. For example, you can give the mail viewer scene from the previous example an identifier:

WindowGroup(id: "mail-viewer") { // Identify the window group.
    MailViewer()
}


Elsewhere in your code, you can use the openWindow action from the environment to create a new window from the group:

struct NewViewerButton: View {
    @Environment(\.openWindow) private var openWindow


    var body: some View {
        Button("Open new mail viewer") {
            openWindow(id: "mail-viewer") // Match the group's identifier.
        }
    }
}


Be sure to use unique strings for identifiers that you apply to window groups in your app.

Present data in a window

If you initialize a window group with a presentation type, you can pass data of that type to the window when you open it. For example, you can define a second window group for the Mail app that displays a specified message:

@main
struct Mail: App {
    var body: some Scene {
        WindowGroup {
            MailViewer(id: "mail-viewer")
        }


        // A window group that displays messages.
        WindowGroup(for: Message.ID.self) { $messageID in
            MessageDetail(messageID: messageID)
        }
    }
}


When you call the openWindow action with a value, SwiftUI finds the window group with the matching type and passes a binding to the value into the window group’s content closure. For example, you can define a button that opens a message by passing the message’s identifier:

struct NewMessageButton: View {
    var message: Message
    @Environment(\.openWindow) private var openWindow


    var body: some View {
        Button("Open message") {
            openWindow(value: message.id)
        }
    }
}


Be sure that the type you present conforms to both the Hashable and Codable protocols. Also, prefer lightweight data for the presentation value. For model values that conform to the Identifiable protocol, the value’s identifier works well as a presentation type, as the above example demonstrates.

**Examples:**

```swift
struct WindowGroup<Content> where Content : View
```

```swift
struct WindowGroup<Content> where Content : View
```

```swift
@main
struct Mail: App {
    var body: some Scene {
        WindowGroup {
            MailViewer() // Define a view hierarchy for the window.
        }
    }
}
```

```swift
@main
struct Mail: App {
    var body: some Scene {
        WindowGroup {
            MailViewer() // Define a view hierarchy for the window.
        }
    }
}
```

```swift
WindowGroup(id: "mail-viewer") { // Identify the window group.
    MailViewer()
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/windowgroup)

---

## DocumentGroup

SwiftUI
DocumentGroup
Structure
DocumentGroup
A scene that enables support for opening, creating, and saving documents.
iOS 14.0+
iPadOS 14.0+
Mac Catalyst 14.0+
macOS 11.0+
visionOS 1.0+
struct DocumentGroup<Document, Content> where Content : View
Mentioned in
Building and customizing the menu bar with SwiftUI
Overview

Use a DocumentGroup scene to tell SwiftUI what kinds of documents your app can open when you declare your app using the App protocol.

Initialize a document group scene by passing in the document model and a view capable of displaying the document type. The document types you supply to DocumentGroup must conform to FileDocument or ReferenceFileDocument. SwiftUI uses the model to add document support to your app. In macOS this includes document-based menu support, including the ability to open multiple documents. On iOS this includes a document browser that can navigate to the documents stored on the file system and multiwindow support:

@main
struct MyApp: App {
    var body: some Scene {
        DocumentGroup(newDocument: TextFile()) { configuration in
            ContentView(document: configuration.$document)
        }
    }
}


Any time the configuration changes, SwiftUI updates the contents with that new configuration, similar to other parameterized builders.

Viewing documents

If your app only needs to display but not modify a specific document type, you can use the file viewer document group scene. You supply the file type of the document, and a view that displays the document type that you provide:

@main
struct MyApp: App {
    var body: some Scene {
        DocumentGroup(viewing: MyImageFormatDocument.self) {
            MyImageFormatViewer(image: $0.document)
        }
    }
}

Supporting multiple document types

Your app can support multiple document types by adding additional document group scenes:

@main
struct MyApp: App {
    var body: some Scene {
        DocumentGroup(newDocument: TextFile()) { group in
            ContentView(document: group.$document)
        }
        DocumentGroup(viewing: MyImageFormatDocument.self) { group in
            MyImageFormatViewer(image: group.document)
        }
    }
}

Accessing the document’s URL

If your app needs to know the document’s URL, you can read it from the editor closure’s configuration parameter, along with the binding to the document. When you create a new document, the configuration’s fileURL property is nil. Every time it changes, it is passed over to the DocumentGroup builder in the updated configuration. This ensures that the view you define in the closure always knows the URL of the document it hosts.

@main
struct MyApp: App {
    var body: some Scene {
        DocumentGroup(newDocument: TextFile()) { configuration in
            ContentView(
                document: configuration.$document,
                fileURL: configuration.fileURL
            )
        }
    }
}


The URL can be used, for example, to present the file path of the file name in the user interface. Don’t access the document’s contents or metadata using the URL because that can conflict with the management of the file that SwiftUI performs. Instead, use the methods that FileDocument and ReferenceFileDocument provide to perform read and write operations.

Topics
Creating a document group
init(newDocument:editor:)
Creates a document group for creating and editing file documents.
init(viewing:viewer:)
Creates a document group capable of viewing file documents.
Editing a document backed by a persistent store
init(editing:contentType:editor:prepareDocument:)
Instantiates a document group for creating and editing documents that store a specific model type.
init(editing: UTType, migrationPlan: any SchemaMigrationPlan.Type, editor: () -> Content, prepareDocument: (ModelContext) -> Void)
Instantiates a document group for creating and editing documents described by the last Schema in the migration plan.
Viewing a document backed by a persistent store
init(viewing:contentType:viewer:)
Instantiates a document group for viewing documents that store a specific model type.
init(viewing: UTType, migrationPlan: any SchemaMigrationPlan.Type, viewer: () -> Content)
Instantiates a document group for viewing documents described by the last Schema in the migration plan.
Relationships
Conforms To
Scene
See Also
Creating a document

**Examples:**

```swift
struct DocumentGroup<Document, Content> where Content : View
```

```swift
struct DocumentGroup<Document, Content> where Content : View
```

```swift
@main
struct MyApp: App {
    var body: some Scene {
        DocumentGroup(newDocument: TextFile()) { configuration in
            ContentView(document: configuration.$document)
        }
    }
}
```

```swift
@main
struct MyApp: App {
    var body: some Scene {
        DocumentGroup(newDocument: TextFile()) { configuration in
            ContentView(document: configuration.$document)
        }
    }
}
```

```swift
@main
struct MyApp: App {
    var body: some Scene {
        DocumentGroup(viewing: MyImageFormatDocument.self) {
            MyImageFormatViewer(image: $0.document)
        }
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/documentgroup)

---

## Settings

SwiftUI
Settings
Structure
Settings
A scene that presents an interface for viewing and modifying an app’s settings.
macOS 11.0+
struct Settings<Content> where Content : View
Mentioned in
Building and customizing the menu bar with SwiftUI
Declaring a custom view
Overview

Use a settings scene to have SwiftUI manage views with controls for your app’s settings when you declare your app using the App protocol. When you use an App declaration for multiple platforms, compile the settings scene only in macOS:

@main
struct MyApp: App {
    var body: some Scene {
        WindowGroup {
            ContentView()
        }
        #if os(macOS)
        Settings {
            SettingsView()
        }
        #endif
    }
}


Passing a view as the argument to a settings scene in the App declaration causes SwiftUI to enable the app’s Settings menu item. SwiftUI manages displaying and removing the settings view when the user selects the Settings item from the application menu or the equivalent keyboard shortcut:

The contents of your settings view are controls that modify bindings to UserDefaults values that SwiftUI manages using the AppStorage property wrapper:

struct GeneralSettingsView: View {
    @AppStorage("showPreview") private var showPreview = true
    @AppStorage("fontSize") private var fontSize = 12.0


    var body: some View {
        Form {
            Toggle("Show Previews", isOn: $showPreview)
            Slider(value: $fontSize, in: 9...96) {
                Text("Font Size (\(fontSize, specifier: "%.0f") pts)")
            }
        }
    }
}


You can define your settings in a single view, or you can use a TabView to group settings into different collections:

struct SettingsView: View {
    var body: some View {
        TabView {
            Tab("General", systemImage: "gear") {
                GeneralSettingsView()
            }
            Tab("Advanced", systemImage: "star") {
                AdvancedSettingsView()
            }
        }
        .scenePadding()
        .frame(maxWidth: 350, minHeight: 100)
    }
}


Topics
Creating a settings scene
init(content: () -> Content)
Creates a scene that presents an interface for viewing and modifying an app’s preferences.
Relationships
Conforms To
Scene
See Also
Managing a settings window
struct SettingsLink
A view that opens the Settings scene defined by an app.
struct OpenSettingsAction
An action that presents the settings scene for an app.
var openSettings: OpenSettingsAction
A Settings presentation action stored in a view’s environment.

**Examples:**

```swift
struct Settings<Content> where Content : View
```

```swift
struct Settings<Content> where Content : View
```

```swift
@main
struct MyApp: App {
    var body: some Scene {
        WindowGroup {
            ContentView()
        }
        #if os(macOS)
        Settings {
            SettingsView()
        }
        #endif
    }
}
```

```swift
@main
struct MyApp: App {
    var body: some Scene {
        WindowGroup {
            ContentView()
        }
        #if os(macOS)
        Settings {
            SettingsView()
        }
        #endif
    }
}
```

```swift
struct GeneralSettingsView: View {
    @AppStorage("showPreview") private var showPreview = true
    @AppStorage("fontSize") private var fontSize = 12.0


    var body: some View {
        Form {
            Toggle("Show Previews", isOn: $showPreview)
            Slider(value: $fontSize, in: 9...96) {
                Text("Font Size (\(fontSize, specifier: "%.0f") pts)")
            }
        }
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/settings)

---

