# Platform Specific

SwiftUI platform specific documentation.

---

## ImmersiveSpace

SwiftUI
ImmersiveSpace
Structure
ImmersiveSpace
A scene that presents its content in an unbounded space.
visionOS 1.0+
struct ImmersiveSpace<Content, Data> where Content : ImmersiveSpaceContent, Data : Decodable, Data : Encodable, Data : Hashable
Overview

Use an immersive space as a container for a view hierarchy that your app presents. The hierarchy that you declare as the immersive space’s content serves as a template for it:

@main
struct SolarSystemApp: App {
    var body: some Scene {
        ImmersiveSpace {
            SolarSystem()
        }
    }
}


If you want to create a bounded scene instead, use one of the types that creates a window or a volume, like WindowGroup or DocumentGroup.

Style the immersive space

By default, immersive spaces use the mixed style which places virtual content in a person’s surroundings. You can select a different style for the immersive space by adding the immersionStyle(selection:in:) scene modifier to the scene. For example, you can completely control the visual experience using the full immersion style:

@main
struct SolarSystemApp: App {
    @State private var style: ImmersionStyle = .full


    var body: some Scene {
        ImmersiveSpace {
            SolarSystem()
        }
        .immersionStyle(selection: $style, in: .full)
    }
}


You can change the immersion style after presenting the immersive space by changing the modifier’s selection input, although you can only use one of the values that you specify in the modifier’s second parameter. For any style of immersion, the other parts of your app’s interface — namely its windows — remain visible. However, the immersion style affects how windows interact with virtual objects in the environment:

For the mixed style, a virtual object obscures part or all of a window that’s behind the object. Similarly, a window obscures a virtual object that’s behind the window.

For other styles, windows always render in front of virtual content, no matter how someone positions the window or the content. This helps people to avoid losing track of windows behind virtual content when passthrough is partially or completely off.

Open an immersive space

You can programmatically open an immersive space by giving it an identifier. For example, you can label the solar system view from the previous example:

ImmersiveSpace(id: "solarSystem") {
    SolarSystem()
}


Elsewhere in your code, you use the openImmersiveSpace environment value to get the instance of the OpenImmersiveSpaceAction structure for a given Environment. You call the instance directly — for example, from a button’s closure, like in the following code — using the identifier:

struct NewSolarSystemImmersiveSpace: View {
    var solarSystem: SolarSystem
    @Environment(\.openImmersiveSpace) private var openImmersiveSpace


    var body: some View {
        Button("Present Solar System") {
            Task {
                await openImmersiveSpace(id: "solarSystem")
            }
        }
    }
}


Mark the call to the action with await because it executes asynchronously. When your app opens an immersive space, the system hides all other visible apps. The system allows only one immersive space to be open at a time. Be sure to close the open immersive space before opening another one.

Dismiss an immersive space

You can dismiss an immersive space by calling the dismissImmersiveSpace action from the environment. For example, you can define a button that dismisses an immersive space:

struct DismissImmersiveSpaceButton: View {
    @Environment(\.dismissImmersiveSpace)
    private var dismissImmersiveSpace


    var body: some View {
        Button("Close Solar System") {
            Task {
                await dismissImmersiveSpace()
            }
        }
    }
}


The dismiss action runs asynchronously, like the open action. You don’t need to specify an identifier when dismissing an immersive space because there can only be one immersive space open at a time.

Present an immersive space at launch

When an app launches, it opens an instance of the first scene that’s listed in the app’s body. However, to open an immersive space at launch, you need to provide additional configuration information in your app’s Info.plist file. In particular, set the UIApplicationPreferredDefaultSceneSessionRole key in the scene manifest to the value UISceneSessionRoleImmersiveSpaceApplication.


**Examples:**

```swift
struct ImmersiveSpace<Content, Data> where Content : ImmersiveSpaceContent, Data : Decodable, Data : Encodable, Data : Hashable
```

```swift
struct ImmersiveSpace<Content, Data> where Content : ImmersiveSpaceContent, Data : Decodable, Data : Encodable, Data : Hashable
```

```swift
ImmersiveSpaceContent
```

```swift
@main
struct SolarSystemApp: App {
    var body: some Scene {
        ImmersiveSpace {
            SolarSystem()
        }
    }
}
```

```swift
@main
struct SolarSystemApp: App {
    var body: some Scene {
        ImmersiveSpace {
            SolarSystem()
        }
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/immersivespace)

---

