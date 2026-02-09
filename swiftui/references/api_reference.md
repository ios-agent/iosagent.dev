# Api Reference

SwiftUI api reference documentation.

---

## Published (Failed)

Error: Page.goto: Timeout 30000ms exceeded.
Call log:
  - navigating to "https://developer.apple.com/documentation/swiftui/published", waiting until "networkidle"


[View Official Documentation](https://developer.apple.com/documentation/swiftui/published)

---

## Commands

SwiftUI
Commands
Protocol
Commands
Conforming types represent a group of related commands that can be exposed to the user via the main menu on macOS and key commands on iOS.
iOS 14.0+
iPadOS 14.0+
Mac Catalyst 14.0+
macOS 11.0+
visionOS 1.0+
@MainActor @preconcurrency
protocol Commands
Mentioned in
Building and customizing the menu bar with SwiftUI
Overview

A type conforming to this protocol inherits @preconcurrency @MainActor isolation from the protocol if the conformance is included in the type’s base declaration:

struct MyCustomType: Transition {
    // `@preconcurrency @MainActor` isolation by default
}


Isolation to the main actor is the default, but it’s not required. Declare the conformance in an extension to opt out of main actor isolation:

extension MyCustomType: Transition {
    // `nonisolated` by default
}

Topics
Implementing commands
var body: Self.Body
The contents of the command hierarchy.

Required

associatedtype Body : Commands
The type of commands that represents the body of this command hierarchy.

Required

Relationships
Conforming Types
CommandGroup
CommandMenu
EmptyCommands
Group
Conforms when Content conforms to Commands.
ImportFromDevicesCommands
InspectorCommands
SidebarCommands
TextEditingCommands
TextFormattingCommands
ToolbarCommands
See Also
Defining commands
func commands<Content>(content: () -> Content) -> some Scene
Adds commands to the scene.
func commandsRemoved() -> some Scene
Removes all commands defined by the modified scene.
func commandsReplaced<Content>(content: () -> Content) -> some Scene
Replaces all commands defined by the modified scene with the commands from the builder.
struct CommandMenu
Command menus are stand-alone, top-level containers for controls that perform related, app-specific commands.
struct CommandGroup
Groups of controls that you can add to existing command menus.
struct CommandsBuilder
Constructs command sets from multi-expression closures. Like ViewBuilder, it supports up to ten expressions in the closure body.
struct CommandGroupPlacement
The standard locations that you can place new command groups relative to.

**Examples:**

```swift
@MainActor @preconcurrency
protocol Commands
```

```swift
@MainActor @preconcurrency
protocol Commands
```

```swift
struct MyCustomType: Transition {
    // `@preconcurrency @MainActor` isolation by default
}
```

```swift
struct MyCustomType: Transition {
    // `@preconcurrency @MainActor` isolation by default
}
```

```swift
extension MyCustomType: Transition {
    // `nonisolated` by default
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/commands)

---

## MenuBarExtra

SwiftUI
MenuBarExtra
Structure
MenuBarExtra
A scene that renders itself as a persistent control in the system menu bar.
macOS 13.0+
struct MenuBarExtra<Label, Content> where Label : View, Content : View
Overview

Use a MenuBarExtra when you want to provide access to commonly used functionality, even when your app is not active.

@main
struct AppWithMenuBarExtra: App {
    @AppStorage("showMenuBarExtra") private var showMenuBarExtra = true


    var body: some Scene {
        WindowGroup {
            ContentView()
        }
        MenuBarExtra(
            "App Menu Bar Extra", systemImage: "star",
            isInserted: $showMenuBarExtra)
        {
            StatusMenu()
        }
    }
}


Or alternatively, to create a utility app that only shows in the menu bar.

@main
struct UtilityApp: App {
    var body: some Scene {
        MenuBarExtra("Utility App", systemImage: "hammer") {
            AppMenu()
        }
    }
}


An app that only shows in the menu bar will be automatically terminated if the user removes the extra from the menu bar.

For apps that only show in the menu bar, a common behavior is for the app to not display its icon in either the Dock or the application switcher. To enable this behavior, set the LSUIElement flag in your app’s Information Property List file to true.

For more complex or data rich menu bar extras, you can use the window style, which displays a popover-like window from the menu bar icon that contains standard controls. You define the layout and contents of those controls with the content that you provide:

MenuBarExtra("Utility App", systemImage: "hammer") {
    ScrollView {
        LazyVGrid(...)
    }
}
.menuBarExtraStyle(.window)

Topics
Creating a menu bar extra
init(_:content:)
Creates a menu bar extra with a key for a localized string to use as the label. The extra defines the primary scene of an App.
init(content: () -> Content, label: () -> Label)
Creates a menu bar extra that will be displayed in the system menu bar, and defines the primary scene of an App.
init(_:isInserted:content:)
Creates a menu bar extra with a key for a localized string to use as the label. The item will be displayed in the system menu bar when the specified binding is set to true. If the user removes the item from the menu bar, the binding will be set to false.
init(isInserted: Binding<Bool>, content: () -> Content, label: () -> Label)
Creates a menu bar extra. The item will be displayed in the system menu bar when the specified binding is set to true. If the user removes the item from the menu bar, the binding will be set to false.
Creating a menu bar extra with an image
init(_:image:content:)
Creates a menu bar extra with an image to use as the items label. The provided title will be used by the accessibility system.
init(_:image:isInserted:content:)
Creates a menu bar extra with an image to use as the items label. The provided title will be used by the accessibility system.
init(_:systemImage:content:)
Creates a menu bar extra with a system image to use as the items label. The provided title will be used by the accessibility system.
init(_:systemImage:isInserted:content:)
Creates a menu bar extra with a system image to use as the items label. The provided title will be used by the accessibility system.
Relationships
Conforms To
Scene
See Also
Creating a menu bar extra
func menuBarExtraStyle<S>(S) -> some Scene
Sets the style for menu bar extra created by this scene.
protocol MenuBarExtraStyle
A specification for the appearance and behavior of a menu bar extra scene.

**Examples:**

```swift
struct MenuBarExtra<Label, Content> where Label : View, Content : View
```

```swift
struct MenuBarExtra<Label, Content> where Label : View, Content : View
```

```swift
@main
struct AppWithMenuBarExtra: App {
    @AppStorage("showMenuBarExtra") private var showMenuBarExtra = true


    var body: some Scene {
        WindowGroup {
            ContentView()
        }
        MenuBarExtra(
            "App Menu Bar Extra", systemImage: "star",
            isInserted: $showMenuBarExtra)
        {
            StatusMenu()
        }
    }
}
```

```swift
@main
struct AppWithMenuBarExtra: App {
    @AppStorage("showMenuBarExtra") private var showMenuBarExtra = true


    var body: some Scene {
        WindowGroup {
            ContentView()
        }
        MenuBarExtra(
            "App Menu Bar Extra", systemImage: "star",
            isInserted: $showMenuBarExtra)
        {
            StatusMenu()
        }
    }
}
```

```swift
@main
struct UtilityApp: App {
    var body: some Scene {
        MenuBarExtra("Utility App", systemImage: "hammer") {
            AppMenu()
        }
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/menubarextra)

---

## Toolbar (Failed)

Error: Page.goto: Timeout 30000ms exceeded.
Call log:
  - navigating to "https://developer.apple.com/documentation/swiftui/toolbar", waiting until "networkidle"


[View Official Documentation](https://developer.apple.com/documentation/swiftui/toolbar)

---

## ToolbarItem

SwiftUI
ToolbarItem
Structure
ToolbarItem
A model that represents an item which can be placed in the toolbar or navigation bar.
iOS 14.0+
iPadOS 14.0+
Mac Catalyst 14.0+
macOS 11.0+
tvOS 14.0+
visionOS 1.0+
watchOS 7.0+
struct ToolbarItem<ID, Content> where Content : View
Topics
Creating a toolbar item
init(placement: ToolbarItemPlacement, content: () -> Content)
Creates a toolbar item with the specified placement and content.
init(id: String, placement: ToolbarItemPlacement, content: () -> Content)
Creates a toolbar item with the specified placement and content, which allows for user customization.
init(id: String, placement: ToolbarItemPlacement, showsByDefault: Bool, content: () -> Content)
Creates a toolbar item with the specified placement and content, which allows for user customization.
Deprecated
Relationships
Conforms To
Copyable
CustomizableToolbarContent
Conforms when ID is String and Content conforms to View.
Identifiable
ToolbarContent
See Also
Populating a toolbar
func toolbar(content:)
Populates the toolbar or navigation bar with the specified items.
struct ToolbarItemGroup
A model that represents a group of ToolbarItems which can be placed in the toolbar or navigation bar.
struct ToolbarItemPlacement
A structure that defines the placement of a toolbar item.
protocol ToolbarContent
Conforming types represent items that can be placed in various locations in a toolbar.
struct ToolbarContentBuilder
Constructs a toolbar item set from multi-expression closures.
struct ToolbarSpacer
A standard space item in toolbars.
struct DefaultToolbarItem
A toolbar item that represents a system component.

**Examples:**

```swift
struct ToolbarItem<ID, Content> where Content : View
```

```swift
struct ToolbarItem<ID, Content> where Content : View
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/toolbaritem)

---

## ToolbarItemGroup

SwiftUI
ToolbarItemGroup
Structure
ToolbarItemGroup
A model that represents a group of ToolbarItems which can be placed in the toolbar or navigation bar.
iOS 14.0+
iPadOS 14.0+
Mac Catalyst 14.0+
macOS 11.0+
tvOS 14.0+
visionOS 1.0+
watchOS 7.0+
struct ToolbarItemGroup<Content> where Content : View
Topics
Creating a toolbar item group
init(placement: ToolbarItemPlacement, content: () -> Content)
Creates a toolbar item group with a specified placement and content.
init<C, L>(placement: ToolbarItemPlacement, content: () -> C, label: () -> L)
Creates a toolbar item group with the specified placement, content, and a label describing that content.
Supporting types
struct LabeledToolbarItemGroupContent
A view that represents the view of a toolbar item group with a specified label.
Relationships
Conforms To
ToolbarContent
See Also
Populating a toolbar
func toolbar(content:)
Populates the toolbar or navigation bar with the specified items.
struct ToolbarItem
A model that represents an item which can be placed in the toolbar or navigation bar.
struct ToolbarItemPlacement
A structure that defines the placement of a toolbar item.
protocol ToolbarContent
Conforming types represent items that can be placed in various locations in a toolbar.
struct ToolbarContentBuilder
Constructs a toolbar item set from multi-expression closures.
struct ToolbarSpacer
A standard space item in toolbars.
struct DefaultToolbarItem
A toolbar item that represents a system component.

**Examples:**

```swift
struct ToolbarItemGroup<Content> where Content : View
```

```swift
struct ToolbarItemGroup<Content> where Content : View
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/toolbaritemgroup)

---

## Menu

SwiftUI
Menu
Structure
Menu
A control for presenting a menu of actions.
iOS 14.0+
iPadOS 14.0+
Mac Catalyst 14.0+
macOS 11.0+
tvOS 17.0+
visionOS 1.0+
struct Menu<Label, Content> where Label : View, Content : View
Mentioned in
Building and customizing the menu bar with SwiftUI
Populating SwiftUI menus with adaptive controls
Overview

The following example presents a menu of three buttons and a submenu, which contains three buttons of its own.

Menu("Actions") {
    Button("Duplicate", action: duplicate)
    Button("Rename", action: rename)
    Button("Delete…", action: delete)
    Menu("Copy") {
        Button("Copy", action: copy)
        Button("Copy Formatted", action: copyFormatted)
        Button("Copy Library Path", action: copyPath)
    }
}


You can create the menu’s title with a LocalizedStringKey, as seen in the previous example, or with a view builder that creates multiple views, such as an image and a text view:

Menu {
    Button("Open in Preview", action: openInPreview)
    Button("Save as PDF", action: saveAsPDF)
} label: {
    Label("PDF", systemImage: "doc.fill")
}


To support subtitles on menu items, initialize your Button with a view builder that creates multiple Text views where the first text represents the title and the second text represents the subtitle. The same approach applies to other controls such as Toggle:

Menu {
    Button(action: openInPreview) {
        Text("Open in Preview")
        Text("View the document in Preview")
    }
    Button(action: saveAsPDF) {
        Text("Save as PDF")
        Text("Export the document as a PDF file")
    }
} label: {
    Label("PDF", systemImage: "doc.fill")
}


Note

This behavior does not apply to buttons outside of a menu’s content.

Primary action

Menus can be created with a custom primary action. The primary action will be performed when the user taps or clicks on the body of the control, and the menu presentation will happen on a secondary gesture, such as on long press or on click of the menu indicator. The following example creates a menu that adds bookmarks, with advanced options that are presented in a menu.

Menu {
    Button(action: addCurrentTabToReadingList) {
        Label("Add to Reading List", systemImage: "eyeglasses")
    }
    Button(action: bookmarkAll) {
        Label("Add Bookmarks for All Tabs", systemImage: "book")
    }
    Button(action: show) {
        Label("Show All Bookmarks", systemImage: "books.vertical")
    }
} label: {
    Label("Add Bookmark", systemImage: "book")
} primaryAction: {
    addBookmark()
}

Styling menus

Use the menuStyle(_:) modifier to change the style of all menus in a view. The following example shows how to apply a custom style:

Menu("Editing") {
    Button("Set In Point", action: setInPoint)
    Button("Set Out Point", action: setOutPoint)
}
.menuStyle(EditingControlsMenuStyle())

Topics
Creating a menu from content
init(_:content:)
Creates a menu that generates its label from a localized string key.
init(content: () -> Content, label: () -> Label)
Creates a menu with a custom label.
init(_:image:content:)
Creates a menu that generates its label from a localized string key and image resource.
init(_:systemImage:content:)

**Examples:**

```swift
struct Menu<Label, Content> where Label : View, Content : View
```

```swift
struct Menu<Label, Content> where Label : View, Content : View
```

```swift
Menu("Actions") {
    Button("Duplicate", action: duplicate)
    Button("Rename", action: rename)
    Button("Delete…", action: delete)
    Menu("Copy") {
        Button("Copy", action: copy)
        Button("Copy Formatted", action: copyFormatted)
        Button("Copy Library Path", action: copyPath)
    }
}
```

```swift
Menu("Actions") {
    Button("Duplicate", action: duplicate)
    Button("Rename", action: rename)
    Button("Delete…", action: delete)
    Menu("Copy") {
        Button("Copy", action: copy)
        Button("Copy Formatted", action: copyFormatted)
        Button("Copy Library Path", action: copyPath)
    }
}
```

```swift
Menu {
    Button("Open in Preview", action: openInPreview)
    Button("Save as PDF", action: saveAsPDF)
} label: {
    Label("PDF", systemImage: "doc.fill")
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/menu)

---

## Form

SwiftUI
Form
Structure
Form
A container for grouping controls used for data entry, such as in settings or inspectors.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
struct Form<Content> where Content : View
Mentioned in
Picking container views for your content
Grouping data with lazy stack views
Overview

SwiftUI applies platform-appropriate styling to views contained inside a form, to group them together. Form-specific styling applies to things like buttons, toggles, labels, lists, and more. Keep in mind that these stylings may be platform-specific. For example, forms appear as grouped lists on iOS, and as aligned vertical stacks on macOS.

The following example shows a simple data entry form on iOS, grouped into two sections. The supporting types (NotifyMeAboutType and ProfileImageSize) and state variables (notifyMeAbout, profileImageSize, playNotificationSounds, and sendReadReceipts) are omitted for simplicity.

var body: some View {
    NavigationView {
        Form {
            Section(header: Text("Notifications")) {
                Picker("Notify Me About", selection: $notifyMeAbout) {
                    Text("Direct Messages").tag(NotifyMeAboutType.directMessages)
                    Text("Mentions").tag(NotifyMeAboutType.mentions)
                    Text("Anything").tag(NotifyMeAboutType.anything)
                }
                Toggle("Play notification sounds", isOn: $playNotificationSounds)
                Toggle("Send read receipts", isOn: $sendReadReceipts)
            }
            Section(header: Text("User Profiles")) {
                Picker("Profile Image Size", selection: $profileImageSize) {
                    Text("Large").tag(ProfileImageSize.large)
                    Text("Medium").tag(ProfileImageSize.medium)
                    Text("Small").tag(ProfileImageSize.small)
                }
                Button("Clear Image Cache") {}
            }
        }
    }
}


On macOS, a similar form renders as a vertical stack. To adhere to macOS platform conventions, this version doesn’t use sections, and uses colons at the end of its labels. It also sets the picker to use the inline style, which produces radio buttons on macOS.

var body: some View {
    Spacer()
    HStack {
        Spacer()
        Form {
            Picker("Notify Me About:", selection: $notifyMeAbout) {
                Text("Direct Messages").tag(NotifyMeAboutType.directMessages)
                Text("Mentions").tag(NotifyMeAboutType.mentions)
                Text("Anything").tag(NotifyMeAboutType.anything)
            }
            Toggle("Play notification sounds", isOn: $playNotificationSounds)
            Toggle("Send read receipts", isOn: $sendReadReceipts)


            Picker("Profile Image Size:", selection: $profileImageSize) {
                Text("Large").tag(ProfileImageSize.large)
                Text("Medium").tag(ProfileImageSize.medium)
                Text("Small").tag(ProfileImageSize.small)
            }
            .pickerStyle(.inline)


            Button("Clear Image Cache") {}
        }
        Spacer()
    }
    Spacer()
}


Topics
Creating a form
init(content: () -> Content)
Creates a form with the provided content.
Creating a form from a configuration
init(FormStyleConfiguration)
Creates a form based on a form style configuration.
Relationships
Conforms To
View
See Also
Grouping inputs
func formStyle<S>(S) -> some View
Sets the style for forms in a view hierarchy.
struct LabeledContent
A container for attaching a label to a value-bearing view.
func labeledContentStyle<S>(S) -> some View
Sets a style for labeled content.

**Examples:**

```swift
struct Form<Content> where Content : View
```

```swift
struct Form<Content> where Content : View
```

```swift
var body: some View {
    NavigationView {
        Form {
            Section(header: Text("Notifications")) {
                Picker("Notify Me About", selection: $notifyMeAbout) {
                    Text("Direct Messages").tag(NotifyMeAboutType.directMessages)
                    Text("Mentions").tag(NotifyMeAboutType.mentions)
                    Text("Anything").tag(NotifyMeAboutType.anything)
                }
                Toggle("Play notification sounds", isOn: $playNotificationSounds)
                Toggle("Send read receipts", isOn: $sendReadReceipts)
            }
            Section(header: Text("User Profiles")) {
                Picker("Profile Image Size", selection: $profileImageSize) {
                    Text("Large").tag(ProfileImageSize.large)
                    Text("Medium").tag(ProfileImageSize.medium)
                    Text("Small").tag(ProfileImageSize.small)
                }
                Button("Clear Image Cache") {}
            }
        }
    }
}
```

```swift
var body: some View {
    NavigationView {
        Form {
            Section(header: Text("Notifications")) {
                Picker("Notify Me About", selection: $notifyMeAbout) {
                    Text("Direct Messages").tag(NotifyMeAboutType.directMessages)
                    Text("Mentions").tag(NotifyMeAboutType.mentions)
                    Text("Anything").tag(NotifyMeAboutType.anything)
                }
                Toggle("Play notification sounds", isOn: $playNotificationSounds)
                Toggle("Send read receipts", isOn: $sendReadReceipts)
            }
            Section(header: Text("User Profiles")) {
                Picker("Profile Image Size", selection: $profileImageSize) {
                    Text("Large").tag(ProfileImageSize.large)
                    Text("Medium").tag(ProfileImageSize.medium)
                    Text("Small").tag(ProfileImageSize.small)
                }
                Button("Clear Image Cache") {}
            }
        }
    }
}
```

```swift
var body: some View {
    Spacer()
    HStack {
        Spacer()
        Form {
            Picker("Notify Me About:", selection: $notifyMeAbout) {
                Text("Direct Messages").tag(NotifyMeAboutType.directMessages)
                Text("Mentions").tag(NotifyMeAboutType.mentions)
                Text("Anything").tag(NotifyMeAboutType.anything)
            }
            Toggle("Play notification sounds", isOn: $playNotificationSounds)
            Toggle("Send read receipts", isOn: $sendReadReceipts)


            Picker("Profile Image Size:", selection: $profileImageSize) {
                Text("Large").tag(ProfileImageSize.large)
                Text("Medium").tag(ProfileImageSize.medium)
                Text("Small").tag(ProfileImageSize.small)
            }
            .pickerStyle(.inline)


            Button("Clear Image Cache") {}
        }
        Spacer()
    }
    Spacer()
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/form)

---

## Section

SwiftUI
Section
Structure
Section
A container view that you can use to add hierarchy within certain views.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
struct Section<Parent, Content, Footer>
Mentioned in
Grouping data with lazy stack views
Displaying data in lists
Populating SwiftUI menus with adaptive controls
Suggesting search terms
Overview

Use Section instances in views like List, Picker, and Form to organize content into separate sections. Each section has custom content that you provide on a per-instance basis. You can also provide headers and footers for each section.

Collapsible sections

Create sections that expand and collapse by using an initializer that accepts an isExpanded binding. A collapsible section in a List that uses the sidebar style shows a disclosure indicator next to the section’s header. Tapping on the disclosure indicator toggles the appearance of the section’s content.

Note

Not all contexts provide a default control to trigger collapse or expansion.

Topics
Creating a section
init(content:)
Creates a section with the provided section content.
init(_:content:)
Creates a section with the provided section content.
Adding headers and footers
init(content:header:)
Creates a section with a header and the provided section content.
init(content: () -> Content, footer: () -> Footer)
Creates a section with a footer and the provided section content.
init(content: () -> Content, header: () -> Parent, footer: () -> Footer)
Creates a section with a header, footer, and the provided section content.
Controlling collapsibility
init(_:isExpanded:content:)
Creates a section with the provided section content.
init(isExpanded:content:header:)
Creates a section with a header, the provided section content, and a binding representing the section’s expansion state.
Deprecated symbols
init(header: Parent, content: () -> Content)
Creates a section with a header and the provided section content.
Deprecated
init(footer: Footer, content: () -> Content)
Creates a section with a footer and the provided section content.
Deprecated
init(header: Parent, footer: Footer, content: () -> Content)
Creates a section with a header, footer, and the provided section content.
Deprecated
func collapsible(Bool) -> some View
Sets whether a section can be collapsed by the user.
Deprecated
Relationships
Conforms To
Copyable
TableRowContent
Conforms when Parent conforms to TableRowContent, Content conforms to TableRowContent, and Footer conforms to TableRowContent.
View
Conforms when Parent conforms to View, Content conforms to View, and Footer conforms to View.
See Also
Organizing views into sections
struct SectionCollection
An opaque collection representing the sections of view.
struct SectionConfiguration
Specifies the contents of a section.

**Examples:**

```swift
struct Section<Parent, Content, Footer>
```

```swift
struct Section<Parent, Content, Footer>
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/section)

---

## GroupBox

SwiftUI
GroupBox
Structure
GroupBox
A stylized view, with an optional label, that visually collects a logical grouping of content.
iOS 14.0+
iPadOS 14.0+
Mac Catalyst 14.0+
macOS 10.15+
visionOS 1.0+
struct GroupBox<Label, Content> where Label : View, Content : View
Overview

Use a group box when you want to visually distinguish a portion of your user interface with an optional title for the boxed content.

The following example sets up a GroupBox with the label “End-User Agreement”, and a long agreementText string in a Text view wrapped by a ScrollView. The box also contains a Toggle for the user to interact with after reading the text.

var body: some View {
    GroupBox(label:
        Label("End-User Agreement", systemImage: "building.columns")
    ) {
        ScrollView(.vertical, showsIndicators: true) {
            Text(agreementText)
                .font(.footnote)
        }
        .frame(height: 100)
        Toggle(isOn: $userAgreed) {
            Text("I agree to the above terms")
        }
    }
}


Topics
Creating a group box
init(content: () -> Content)
Creates an unlabeled group box with the provided view content.
init(content: () -> Content, label: () -> Label)
Creates a group box with the provided label and view content.
init(_:content:)
Creates a group box with the provided view content and title.
Creating a group box from a configuration
init(GroupBoxStyleConfiguration)
Creates a group box based on a style configuration.
Deprecated initializers
init(label: Label, content: () -> Content)
Deprecated
Relationships
Conforms To
View
See Also
Grouping views into a box
func groupBoxStyle<S>(S) -> some View
Sets the style for group boxes within this view.

**Examples:**

```swift
struct GroupBox<Label, Content> where Label : View, Content : View
```

```swift
struct GroupBox<Label, Content> where Label : View, Content : View
```

```swift
var body: some View {
    GroupBox(label:
        Label("End-User Agreement", systemImage: "building.columns")
    ) {
        ScrollView(.vertical, showsIndicators: true) {
            Text(agreementText)
                .font(.footnote)
        }
        .frame(height: 100)
        Toggle(isOn: $userAgreed) {
            Text("I agree to the above terms")
        }
    }
}
```

```swift
var body: some View {
    GroupBox(label:
        Label("End-User Agreement", systemImage: "building.columns")
    ) {
        ScrollView(.vertical, showsIndicators: true) {
            Text(agreementText)
                .font(.footnote)
        }
        .frame(height: 100)
        Toggle(isOn: $userAgreed) {
            Text("I agree to the above terms")
        }
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/groupbox)

---

## DisclosureGroup

SwiftUI
DisclosureGroup
Structure
DisclosureGroup
A view that shows or hides another content view, based on the state of a disclosure control.
iOS 14.0+
iPadOS 14.0+
Mac Catalyst 14.0+
macOS 11.0+
visionOS 1.0+
struct DisclosureGroup<Label, Content> where Label : View, Content : View
Mentioned in
Displaying data in lists
Overview

A disclosure group view consists of a label to identify the contents, and a control to show and hide the contents. Showing the contents puts the disclosure group into the “expanded” state, and hiding them makes the disclosure group “collapsed”.

In the following example, a disclosure group contains two toggles and an embedded disclosure group. The top level disclosure group exposes its expanded state with the bound property, topLevelExpanded. By expanding the disclosure group, the user can use the toggles to update the state of the toggleStates structure.

struct ToggleStates {
    var oneIsOn: Bool = false
    var twoIsOn: Bool = true
}
@State private var toggleStates = ToggleStates()
@State private var topExpanded: Bool = true


var body: some View {
    DisclosureGroup("Items", isExpanded: $topExpanded) {
        Toggle("Toggle 1", isOn: $toggleStates.oneIsOn)
        Toggle("Toggle 2", isOn: $toggleStates.twoIsOn)
        DisclosureGroup("Sub-items") {
            Text("Sub-item 1")
        }
    }
}

Topics
Creating a disclosure group
init(_:content:)
Creates a disclosure group, using a provided localized string key to create a text view for the label.
init(content: () -> Content, label: () -> Label)
Creates a disclosure group with the given label and content views.
init(_:isExpanded:content:)
Creates a disclosure group, using a provided localized string key to create a text view for the label, and a binding to the expansion state (expanded or collapsed).
init(isExpanded: Binding<Bool>, content: () -> Content, label: () -> Label)
Creates a disclosure group with the given label and content views, and a binding to the expansion state (expanded or collapsed).
Relationships
Conforms To
View
See Also
Disclosing information progressively
struct OutlineGroup
A structure that computes views and disclosure groups on demand from an underlying collection of tree-structured, identified data.
func disclosureGroupStyle<S>(S) -> some View
Sets the style for disclosure groups within this view.

**Examples:**

```swift
struct DisclosureGroup<Label, Content> where Label : View, Content : View
```

```swift
struct DisclosureGroup<Label, Content> where Label : View, Content : View
```

```swift
struct ToggleStates {
    var oneIsOn: Bool = false
    var twoIsOn: Bool = true
}
@State private var toggleStates = ToggleStates()
@State private var topExpanded: Bool = true


var body: some View {
    DisclosureGroup("Items", isExpanded: $topExpanded) {
        Toggle("Toggle 1", isOn: $toggleStates.oneIsOn)
        Toggle("Toggle 2", isOn: $toggleStates.twoIsOn)
        DisclosureGroup("Sub-items") {
            Text("Sub-item 1")
        }
    }
}
```

```swift
struct ToggleStates {
    var oneIsOn: Bool = false
    var twoIsOn: Bool = true
}
@State private var toggleStates = ToggleStates()
@State private var topExpanded: Bool = true


var body: some View {
    DisclosureGroup("Items", isExpanded: $topExpanded) {
        Toggle("Toggle 1", isOn: $toggleStates.oneIsOn)
        Toggle("Toggle 2", isOn: $toggleStates.twoIsOn)
        DisclosureGroup("Sub-items") {
            Text("Sub-item 1")
        }
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/disclosuregroup)

---

## OutlineGroup

SwiftUI
OutlineGroup
Structure
OutlineGroup
A structure that computes views and disclosure groups on demand from an underlying collection of tree-structured, identified data.
iOS 14.0+
iPadOS 14.0+
Mac Catalyst 14.0+
macOS 11.0+
visionOS 1.0+
struct OutlineGroup<Data, ID, Parent, Leaf, Subgroup> where Data : RandomAccessCollection, ID : Hashable
Mentioned in
Displaying data in lists
Overview

Use an outline group when you need a view that can represent a hierarchy of data by using disclosure views. This allows the user to navigate the tree structure by using the disclosure views to expand and collapse branches.

In the following example, a tree structure of FileItem data offers a simplified view of a file system. Passing the root of this tree and the key path of its children allows you to quickly create a visual representation of the file system.

struct FileItem: Hashable, Identifiable, CustomStringConvertible {
    var id: Self { self }
    var name: String
    var children: [FileItem]? = nil
    var description: String {
        switch children {
        case nil:
            return "📄 \(name)"
        case .some(let children):
            return children.isEmpty ? "📂 \(name)" : "📁 \(name)"
        }
    }
}


let data =
  FileItem(name: "users", children:
    [FileItem(name: "user1234", children:
      [FileItem(name: "Photos", children:
        [FileItem(name: "photo001.jpg"),
         FileItem(name: "photo002.jpg")]),
       FileItem(name: "Movies", children:
         [FileItem(name: "movie001.mp4")]),
          FileItem(name: "Documents", children: [])
      ]),
     FileItem(name: "newuser", children:
       [FileItem(name: "Documents", children: [])
       ])
    ])


OutlineGroup(data, children: \.children) { item in
    Text("\(item.description)")
}

Type parameters

Five generic type constraints define a specific OutlineGroup instance:

Data: The type of a collection containing the children of an element in the tree-shaped data.

ID: The type of the identifier for an element.

Parent: The type of the visual representation of an element whose children property is non-nil

Leaf: The type of the visual representation of an element whose children property is nil.

Subgroup: A type of a view that groups a parent view and a view representing its children, typically with some mechanism for showing and hiding the children

Topics
Creating an outline group
init(_:children:)
Creates an outline group from a collection of root data elements and a key path to element’s children.
init(_:children:content:)
Creates an outline group from a binding to a collection of root data elements and a key path to its children.
init(_:id:children:content:)
Creates an outline group from a binding to a collection of root data elements, the key path to a data element’s identifier, and a key path to its children.
Supporting types
struct OutlineSubgroupChildren
A type-erased view representing the children in an outline subgroup.
Relationships
Conforms To
Copyable
TableRowContent
Conforms when Data conforms to RandomAccessCollection, ID is Data.Element.ID, Parent conforms to TableRowContent, Parent is Leaf, Leaf is Subgroup, and Data.Element is Parent.TableRowValue.
View
Conforms when Data conforms to RandomAccessCollection, ID conforms to Hashable, Parent conforms to View, Leaf conforms to View, and Subgroup conforms to View.
See Also
Disclosing information progressively
struct DisclosureGroup
A view that shows or hides another content view, based on the state of a disclosure control.
func disclosureGroupStyle<S>(S) -> some View
Sets the style for disclosure groups within this view.

**Examples:**

```swift
struct OutlineGroup<Data, ID, Parent, Leaf, Subgroup> where Data : RandomAccessCollection, ID : Hashable
```

```swift
struct OutlineGroup<Data, ID, Parent, Leaf, Subgroup> where Data : RandomAccessCollection, ID : Hashable
```

```swift
RandomAccessCollection
```

```swift
struct FileItem: Hashable, Identifiable, CustomStringConvertible {
    var id: Self { self }
    var name: String
    var children: [FileItem]? = nil
    var description: String {
        switch children {
        case nil:
            return "📄 \(name)"
        case .some(let children):
            return children.isEmpty ? "📂 \(name)" : "📁 \(name)"
        }
    }
}


let data =
  FileItem(name: "users", children:
    [FileItem(name: "user1234", children:
      [FileItem(name: "Photos", children:
        [FileItem(name: "photo001.jpg"),
         FileItem(name: "photo002.jpg")]),
       FileItem(name: "Movies", children:
         [FileItem(name: "movie001.mp4")]),
          FileItem(name: "Documents", children: [])
      ]),
     FileItem(name: "newuser", children:
       [FileItem(name: "Documents", children: [])
       ])
    ])


OutlineGroup(data, children: \.children) { item in
    Text("\(item.description)")
}
```

```swift
struct FileItem: Hashable, Identifiable, CustomStringConvertible {
    var id: Self { self }
    var name: String
    var children: [FileItem]? = nil
    var description: String {
        switch children {
        case nil:
            return "📄 \(name)"
        case .some(let children):
            return children.isEmpty ? "📂 \(name)" : "📁 \(name)"
        }
    }
}


let data =
  FileItem(name: "users", children:
    [FileItem(name: "user1234", children:
      [FileItem(name: "Photos", children:
        [FileItem(name: "photo001.jpg"),
         FileItem(name: "photo002.jpg")]),
       FileItem(name: "Movies", children:
         [FileItem(name: "movie001.mp4")]),
          FileItem(name: "Documents", children: [])
      ]),
     FileItem(name: "newuser", children:
       [FileItem(name: "Documents", children: [])
       ])
    ])


OutlineGroup(data, children: \.children) { item in
    Text("\(item.description)")
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/outlinegroup)

---

