# Navigation

SwiftUI navigation documentation.

---

## Link

SwiftUI
Link
Structure
Link
A control for navigating to a URL.
iOS 14.0+
iPadOS 14.0+
Mac Catalyst 14.0+
macOS 11.0+
tvOS 14.0+
visionOS 1.0+
watchOS 7.0+
@MainActor @preconcurrency
struct Link<Label> where Label : View
Overview

Create a link by providing a destination URL and a title. The title tells the user the purpose of the link, and can be a string, a title key that produces a localized string, or a view that acts as a label. The example below creates a link to example.com and displays the title string as a link-styled view:

Link("View Our Terms of Service",
      destination: URL(string: "https://www.example.com/TOS.html")!)


When a user taps or clicks a Link, the default behavior depends on the contents of the URL. For example, SwiftUI opens a Universal Link in the associated app if possible, or in the user’s default web browser if not. Alternatively, you can override the default behavior by setting the openURL environment value with a custom OpenURLAction:

Link("Visit Our Site", destination: URL(string: "https://www.example.com")!)
    .environment(\.openURL, OpenURLAction { url in
        print("Open \(url)")
        return .handled
    })


As with other views, you can style links using standard view modifiers depending on the view type of the link’s label. For example, a Text label could be modified with a custom font(_:) or foregroundColor(_:) to customize the appearance of the link in your app’s UI.

Topics
Creating a link
init(_:destination:)
Creates a control, consisting of a URL and a title key, used to navigate to a URL.
init(destination: URL, label: () -> Label)
Creates a control, consisting of a URL and a label, used to navigate to the given URL.
Relationships
Conforms To
View
See Also
Linking to other content
struct ShareLink
A view that controls a sharing presentation.
struct SharePreview
A representation of a type to display in a share preview.
struct TextFieldLink
A control that requests text input from the user when pressed.
struct HelpLink
A button with a standard appearance that opens app-specific help documentation.

**Examples:**

```swift
@MainActor @preconcurrency
struct Link<Label> where Label : View
```

```swift
@MainActor @preconcurrency
struct Link<Label> where Label : View
```

```swift
Link("View Our Terms of Service",
      destination: URL(string: "https://www.example.com/TOS.html")!)
```

```swift
Link("View Our Terms of Service",
      destination: URL(string: "https://www.example.com/TOS.html")!)
```

```swift
Link("Visit Our Site", destination: URL(string: "https://www.example.com")!)
    .environment(\.openURL, OpenURLAction { url in
        print("Open \(url)")
        return .handled
    })
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/link)

---

## NavigationLink

SwiftUI
NavigationLink
Structure
NavigationLink
A view that controls a navigation presentation.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
struct NavigationLink<Label, Destination> where Label : View, Destination : View
Mentioned in
Migrating to new navigation types
Displaying data in lists
Understanding the navigation stack
Overview

People click or tap a navigation link to present a view inside a NavigationStack or NavigationSplitView. You control the visual appearance of the link by providing view content in the link’s label closure. For example, you can use a Label to display a link:

NavigationLink {
    FolderDetail(id: workFolder.id)
} label: {
    Label("Work Folder", systemImage: "folder")
}


For a link composed only of text, you can use one of the convenience initializers that takes a string and creates a Text view for you:

NavigationLink("Work Folder") {
    FolderDetail(id: workFolder.id)
}

Link to a destination view

You can perform navigation by initializing a link with a destination view that you provide in the destination closure. For example, consider a ColorDetail view that fills itself with a color:

struct ColorDetail: View {
    var color: Color


    var body: some View {
        color.navigationTitle(color.description)
    }
}


The following NavigationStack presents three links to color detail views:

NavigationStack {
    List {
        NavigationLink("Mint") { ColorDetail(color: .mint) }
        NavigationLink("Pink") { ColorDetail(color: .pink) }
        NavigationLink("Teal") { ColorDetail(color: .teal) }
    }
    .navigationTitle("Colors")
}

Create a presentation link

Alternatively, you can use a navigation link to perform navigation based on a presented data value. To support this, use the navigationDestination(for:destination:) view modifier inside a navigation stack to associate a view with a kind of data, and then present a value of that data type from a navigation link. The following example reimplements the previous example as a series of presentation links:

NavigationStack {
    List {
        NavigationLink("Mint", value: Color.mint)
        NavigationLink("Pink", value: Color.pink)
        NavigationLink("Teal", value: Color.teal)
    }
    .navigationDestination(for: Color.self) { color in
        ColorDetail(color: color)
    }
    .navigationTitle("Colors")
}


Separating the view from the data facilitates programmatic navigation because you can manage navigation state by recording the presented data.

Control a presentation link programmatically

To navigate programmatically, introduce a state variable that tracks the items on a stack. For example, you can create an array of colors to store the stack state from the previous example, and initialize it as an empty array to start with an empty stack:

@State private var colors: [Color] = []


Then pass a Binding to the state to the navigation stack:

NavigationStack(path: $colors) {
    // ...
}


You can use the array to observe the current state of the stack. You can also modify the array to change the contents of the stack. For example, you can programmatically add blue to the array, and navigation to a new color detail view using the following method:

func showBlue() {
    colors.append(.blue)
}

Coordinate with a list


**Examples:**

```swift
struct NavigationLink<Label, Destination> where Label : View, Destination : View
```

```swift
struct NavigationLink<Label, Destination> where Label : View, Destination : View
```

```swift
NavigationLink {
    FolderDetail(id: workFolder.id)
} label: {
    Label("Work Folder", systemImage: "folder")
}
```

```swift
NavigationLink {
    FolderDetail(id: workFolder.id)
} label: {
    Label("Work Folder", systemImage: "folder")
}
```

```swift
NavigationLink("Work Folder") {
    FolderDetail(id: workFolder.id)
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/navigationlink)

---

## NavigationPath

SwiftUI
NavigationPath
Structure
NavigationPath
A type-erased list of data representing the content of a navigation stack.
iOS 16.0+
iPadOS 16.0+
Mac Catalyst 16.0+
macOS 13.0+
tvOS 16.0+
visionOS 1.0+
watchOS 9.0+
struct NavigationPath
Mentioned in
Migrating to new navigation types
Understanding the navigation stack
Overview

You can manage the state of a NavigationStack by initializing the stack with a binding to a collection of data. The stack stores data items in the collection for each view on the stack. You also can read and write the collection to observe and alter the stack’s state.

When a stack displays views that rely on only one kind of data, you can use a standard collection, like an array, to hold the data. If you need to present different kinds of data in a single stack, use a navigation path instead. The path uses type erasure so you can manage a collection of heterogeneous elements. The path also provides the usual collection controls for adding, counting, and removing data elements.

Serialize the path

When the values you present on the navigation stack conform to the Codable protocol, you can use the path’s codable property to get a serializable representation of the path. Use that representation to save and restore the contents of the stack. For example, you can define an ObservableObject that handles serializing and deserializing the path:

class MyModelObject: ObservableObject {
    @Published var path: NavigationPath


    static func readSerializedData() -> Data? {
        // Read data representing the path from app's persistent storage.
    }


    static func writeSerializedData(_ data: Data) {
        // Write data representing the path to app's persistent storage.
    }


    init() {
        if let data = Self.readSerializedData() {
            do {
                let representation = try JSONDecoder().decode(
                    NavigationPath.CodableRepresentation.self,
                    from: data)
                self.path = NavigationPath(representation)
            } catch {
                self.path = NavigationPath()
            }
        } else {
            self.path = NavigationPath()
        }
    }


    func save() {
        guard let representation = path.codable else { return }
        do {
            let encoder = JSONEncoder()
            let data = try encoder.encode(representation)
            Self.writeSerializedData(data)
        } catch {
            // Handle error.
        }
    }
}


Then, using that object in your view, you can save the state of the navigation path when the Scene enters the ScenePhase.background state:

@StateObject private var pathState = MyModelObject()
@Environment(\.scenePhase) private var scenePhase


var body: some View {
    NavigationStack(path: $pathState.path) {
        // Add a root view here.
    }
    .onChange(of: scenePhase) { phase in
        if phase == .background {
            pathState.save()
        }
    }
}

Topics
Creating a navigation path
init()
Creates a new, empty navigation path.
init(_:)
Creates a new navigation path from a serializable version.
Managing path contents
var isEmpty: Bool
A Boolean that indicates whether this path is empty.
var count: Int
The number of elements in this path.
func append(_:)
Appends a new codable value to the end of this path.
func removeLast(Int)

**Examples:**

```swift
struct NavigationPath
```

```swift
struct NavigationPath
```

```swift
class MyModelObject: ObservableObject {
    @Published var path: NavigationPath


    static func readSerializedData() -> Data? {
        // Read data representing the path from app's persistent storage.
    }


    static func writeSerializedData(_ data: Data) {
        // Write data representing the path to app's persistent storage.
    }


    init() {
        if let data = Self.readSerializedData() {
            do {
                let representation = try JSONDecoder().decode(
                    NavigationPath.CodableRepresentation.self,
                    from: data)
                self.path = NavigationPath(representation)
            } catch {
                self.path = NavigationPath()
            }
        } else {
            self.path = NavigationPath()
        }
    }


    func save() {
        guard let representation = path.codable else { return }
        do {
            let encoder = JSONEncoder()
            let data = try encoder.encode(representation)
            Self.writeSerializedData(data)
        } catch {
            // Handle error.
        }
    }
}
```

```swift
class MyModelObject: ObservableObject {
    @Published var path: NavigationPath


    static func readSerializedData() -> Data? {
        // Read data representing the path from app's persistent storage.
    }


    static func writeSerializedData(_ data: Data) {
        // Write data representing the path to app's persistent storage.
    }


    init() {
        if let data = Self.readSerializedData() {
            do {
                let representation = try JSONDecoder().decode(
                    NavigationPath.CodableRepresentation.self,
                    from: data)
                self.path = NavigationPath(representation)
            } catch {
                self.path = NavigationPath()
            }
        } else {
            self.path = NavigationPath()
        }
    }


    func save() {
        guard let representation = path.codable else { return }
        do {
            let encoder = JSONEncoder()
            let data = try encoder.encode(representation)
            Self.writeSerializedData(data)
        } catch {
            // Handle error.
        }
    }
}
```

```swift
@StateObject private var pathState = MyModelObject()
@Environment(\.scenePhase) private var scenePhase


var body: some View {
    NavigationStack(path: $pathState.path) {
        // Add a root view here.
    }
    .onChange(of: scenePhase) { phase in
        if phase == .background {
            pathState.save()
        }
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/navigationpath)

---

## Sheet (Failed)

Error: Page.goto: Timeout 30000ms exceeded.
Call log:
  - navigating to "https://developer.apple.com/documentation/swiftui/sheet", waiting until "networkidle"


[View Official Documentation](https://developer.apple.com/documentation/swiftui/sheet)

---

## FullScreenCover (Failed)

Error: Page.goto: Timeout 30000ms exceeded.
Call log:
  - navigating to "https://developer.apple.com/documentation/swiftui/fullscreencover", waiting until "networkidle"


[View Official Documentation](https://developer.apple.com/documentation/swiftui/fullscreencover)

---

## Popover (Failed)

Error: Page.goto: Timeout 30000ms exceeded.
Call log:
  - navigating to "https://developer.apple.com/documentation/swiftui/popover", waiting until "networkidle"


[View Official Documentation](https://developer.apple.com/documentation/swiftui/popover)

---

## Alert

SwiftUI
Alert
Deprecated
Structure
Alert
A representation of an alert presentation.
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
struct Alert

Deprecated

Use a View modifier like alert(_:isPresented:presenting:actions:message:) instead.

Overview

Use an alert when you want the user to act in response to the state of the app or system. If you want the user to make a choice in response to their action, use an ActionSheet instead.

You show an alert by using the alert(isPresented:content:) view modifier to create an alert, which then appears whenever the bound isPresented value is true. The content closure you provide to this modifer produces a customized instance of the Alert type.

In the following example, a button presents a simple alert when tapped, by updating a local showAlert property that binds to the alert.

@State private var showAlert = false
var body: some View {
    Button("Tap to show alert") {
        showAlert = true
    }
    .alert(isPresented: $showAlert) {
        Alert(
            title: Text("Current Location Not Available"),
            message: Text("Your current location can’t be " +
                            "determined at this time.")
        )
    }
}


To customize the alert, add instances of the Alert.Button type, which provides standardized buttons for common tasks like canceling and performing destructive actions. The following example uses two buttons: a default button labeled “Try Again” that calls a saveWorkoutData method, and a “Delete” button that calls a destructive deleteWorkoutData method.

@State private var showAlert = false
var body: some View {
    Button("Tap to show alert") {
        showAlert = true
    }
    .alert(isPresented: $showAlert) {
        Alert(
            title: Text("Unable to Save Workout Data"),
            message: Text("The connection to the server was lost."),
            primaryButton: .default(
                Text("Try Again"),
                action: saveWorkoutData
            ),
            secondaryButton: .destructive(
                Text("Delete"),
                action: deleteWorkoutData
            )
        )
    }
}


The alert handles its own dismissal when the user taps one of the buttons in the alert, by setting the bound isPresented value back to false.

Topics
Creating an alert
init(title: Text, message: Text?, dismissButton: Alert.Button?)
Creates an alert with one button.
init(title: Text, message: Text?, primaryButton: Alert.Button, secondaryButton: Alert.Button)
Creates an alert with two buttons.
static func sideBySideButtons(title: Text, message: Text?, primaryButton: Alert.Button, secondaryButton: Alert.Button) -> Alert
Creates a side by side button alert.
Specifying the button type
struct Button
A button that represents an operation of an alert presentation.
See Also
Deprecated modal presentations
struct ActionSheet
A representation of an action sheet presentation.
Deprecated

**Examples:**

```swift
struct Alert
```

```swift
struct Alert
```

```swift
@State private var showAlert = false
var body: some View {
    Button("Tap to show alert") {
        showAlert = true
    }
    .alert(isPresented: $showAlert) {
        Alert(
            title: Text("Current Location Not Available"),
            message: Text("Your current location can’t be " +
                            "determined at this time.")
        )
    }
}
```

```swift
@State private var showAlert = false
var body: some View {
    Button("Tap to show alert") {
        showAlert = true
    }
    .alert(isPresented: $showAlert) {
        Alert(
            title: Text("Current Location Not Available"),
            message: Text("Your current location can’t be " +
                            "determined at this time.")
        )
    }
}
```

```swift
@State private var showAlert = false
var body: some View {
    Button("Tap to show alert") {
        showAlert = true
    }
    .alert(isPresented: $showAlert) {
        Alert(
            title: Text("Unable to Save Workout Data"),
            message: Text("The connection to the server was lost."),
            primaryButton: .default(
                Text("Try Again"),
                action: saveWorkoutData
            ),
            secondaryButton: .destructive(
                Text("Delete"),
                action: deleteWorkoutData
            )
        )
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/alert)

---

## ConfirmationDialog (Failed)

Error: Page.goto: Timeout 30000ms exceeded.
Call log:
  - navigating to "https://developer.apple.com/documentation/swiftui/confirmationdialog", waiting until "networkidle"


[View Official Documentation](https://developer.apple.com/documentation/swiftui/confirmationdialog)

---

## Table

SwiftUI
Table
Structure
Table
A container that presents rows of data arranged in one or more columns, optionally providing the ability to select one or more members.
iOS 16.0+
iPadOS 16.0+
Mac Catalyst 16.0+
macOS 12.0+
visionOS 1.0+
struct Table<Value, Rows, Columns> where Value == Rows.TableRowValue, Rows : TableRowContent, Columns : TableColumnContent, Rows.TableRowValue == Columns.TableRowValue
Overview

You commonly create tables from collections of data. The following example shows how to create a simple, three-column table from an array of Person instances that conform to the Identifiable protocol:

struct Person: Identifiable {
    let givenName: String
    let familyName: String
    let emailAddress: String
    let id = UUID()


    var fullName: String { givenName + " " + familyName }
}


@State private var people = [
    Person(givenName: "Juan", familyName: "Chavez", emailAddress: "juanchavez@icloud.com"),
    Person(givenName: "Mei", familyName: "Chen", emailAddress: "meichen@icloud.com"),
    Person(givenName: "Tom", familyName: "Clark", emailAddress: "tomclark@icloud.com"),
    Person(givenName: "Gita", familyName: "Kumar", emailAddress: "gitakumar@icloud.com")
]


struct PeopleTable: View {
    var body: some View {
        Table(people) {
            TableColumn("Given Name", value: \.givenName)
            TableColumn("Family Name", value: \.familyName)
            TableColumn("E-Mail Address", value: \.emailAddress)
        }
    }
}


If there are more rows than can fit in the available space, Table provides vertical scrolling automatically. On macOS, the table also provides horizontal scrolling if there are more columns than can fit in the width of the view. Scroll bars appear as needed on iOS; on macOS, the Table shows or hides scroll bars based on the “Show scroll bars” system preference.

Supporting selection in tables

To make rows of a table selectable, provide a binding to a selection variable. Binding to a single instance of the table data’s id type creates a single-selection table. Binding to a Set creates a table that supports multiple selections. The following example shows how to add multi-select to the previous example. A Text view below the table shows the number of items currently selected.

struct SelectableTable: View {
    @State private var selectedPeople = Set<Person.ID>()


    var body: some View {
        Table(people, selection: $selectedPeople) {
            TableColumn("Given Name", value: \.givenName)
            TableColumn("Family Name", value: \.familyName)
            TableColumn("E-Mail Address", value: \.emailAddress)
        }
        Text("\(selectedPeople.count) people selected")
    }
}

Supporting sorting in tables

To make the columns of a table sortable, provide a binding to an array of SortComparator instances. The table reflects the sorted state through its column headers, allowing sorting for any columns with key paths.

When the table sort descriptors update, re-sort the data collection that underlies the table; the table itself doesn’t perform a sort operation. You can watch for changes in the sort descriptors by using a onChange(of:perform:) modifier, and then sort the data in the modifier’s perform closure.

The following example shows how to add sorting capability to the previous example:

struct SortableTable: View {
    @State private var sortOrder = [KeyPathComparator(\Person.givenName)]


    var body: some View {
        Table(people, sortOrder: $sortOrder) {
            TableColumn("Given Name", value: \.givenName)
            TableColumn("Family Name", value: \.familyName)
            TableColumn("E-Mail address", value: \.emailAddress)
        }
        .onChange(of: sortOrder) { _, sortOrder in
            people.sort(using: sortOrder)
        }
    }
}

Building tables with static rows

To create a table from static rows, rather than the contents of a collection of data, you provide both the columns and the rows.

The following example shows a table that calculates prices from applying varying gratuities (“tips”) to a fixed set of prices. It creates the table with the init(of:columns:rows:) initializer, with the rows parameter providing the base price that each row uses for its calculations. Each column receives each price and performs its calculation, producing a Text to display the formatted result.

struct Purchase: Identifiable {
    let price: Decimal
    let id = UUID()
}


**Examples:**

```swift
struct Table<Value, Rows, Columns> where Value == Rows.TableRowValue, Rows : TableRowContent, Columns : TableColumnContent, Rows.TableRowValue == Columns.TableRowValue
```

```swift
struct Table<Value, Rows, Columns> where Value == Rows.TableRowValue, Rows : TableRowContent, Columns : TableColumnContent, Rows.TableRowValue == Columns.TableRowValue
```

```swift
TableRowValue
```

```swift
TableRowContent
```

```swift
TableColumnContent
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/table)

---

## TableColumn

SwiftUI
TableColumn
Structure
TableColumn
A column that displays a view for each row in a table.
iOS 16.0+
iPadOS 16.0+
Mac Catalyst 16.0+
macOS 12.0+
visionOS 1.0+
struct TableColumn<RowValue, Sort, Content, Label> where RowValue : Identifiable, Sort : SortComparator, Content : View, Label : View
Overview

You create a column with a label, content view, and optional key path. The table calls the content view builder with the value for each row in the table. The column uses a key path to map to a property of each row value, which sortable tables use to reflect the current sort order.

The following example creates a sortable column for a table with Person rows, displaying each person’s given name:

TableColumn("Given name", value: \.givenName) { person in
    Text(person.givenName)
}


For the common case of String properties, you can use the convenience initializer that doesn’t require an explicit content closure and displays that string verbatim as a Text view. This means you can write the previous example as:

TableColumn("Given name", value: \.givenName)

Topics
Creating an unsortable column
init(_:value:)
Creates an unsortable column that displays a string property with a text label.
init(_:content:)
Creates an unsortable column with a text label
Creating a sortable column
init(_:value:content:)
Creates a sortable column for Boolean values with a text label.
init(_:value:comparator:)
Creates a sortable column that displays a string property and has a text label.
init(_:value:comparator:content:)
Creates a sortable column with a text label.
init(_:sortUsing:content:)
Creates a sortable column with text label.
Setting the column width
func width(CGFloat?) -> TableColumn<RowValue, Sort, Content, Label>
Creates a fixed width table column that isn’t user resizable.
func width(min: CGFloat?, ideal: CGFloat?, max: CGFloat?) -> TableColumn<RowValue, Sort, Content, Label>
Creates a resizable table column with the provided constraints.
func width() -> TableColumn<RowValue, Sort, Content, Label>
Sets the column’s width.
Deprecated
Relationships
Conforms To
TableColumnContent
See Also
Creating columns
protocol TableColumnContent
A type used to represent columns within a table.
struct TableColumnAlignment
Describes the alignment of the content of a table column.
struct TableColumnBuilder
A result builder that creates table column content from closures.
struct TableColumnForEach
A structure that computes columns on demand from an underlying collection of identified data.

**Examples:**

```swift
struct TableColumn<RowValue, Sort, Content, Label> where RowValue : Identifiable, Sort : SortComparator, Content : View, Label : View
```

```swift
struct TableColumn<RowValue, Sort, Content, Label> where RowValue : Identifiable, Sort : SortComparator, Content : View, Label : View
```

```swift
Identifiable
```

```swift
SortComparator
```

```swift
TableColumn("Given name", value: \.givenName) { person in
    Text(person.givenName)
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/tablecolumn)

---

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

---

