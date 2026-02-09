# Layout

SwiftUI layout documentation.

---

## VStack

SwiftUI
VStack
Structure
VStack
A view that arranges its subviews in a vertical line.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
@frozen
struct VStack<Content> where Content : View
Mentioned in
Building layouts with stack views
Creating performant scrollable stacks
Adding a background to your view
Inspecting view layout
Picking container views for your content
Overview

Unlike LazyVStack, which only renders the views when your app needs to display them, a VStack renders the views all at once, regardless of whether they are on- or offscreen. Use the regular VStack when you have a small number of subviews or don’t want the delayed rendering behavior of the “lazy” version.

The following example shows a simple vertical stack of 10 text views:

var body: some View {
    VStack(
        alignment: .leading,
        spacing: 10
    ) {
        ForEach(
            1...10,
            id: \.self
        ) {
            Text("Item \($0)")
        }
    }
}


Note

If you need a vertical stack that conforms to the Layout protocol, like when you want to create a conditional layout using AnyLayout, use VStackLayout instead.

Topics
Creating a stack
init(alignment: HorizontalAlignment, spacing: CGFloat?, content: () -> Content)
Creates an instance with the given spacing and horizontal alignment.
Relationships
Conforms To
View
See Also
Statically arranging views in one dimension
Building layouts with stack views
Compose complex layouts from primitive container views.
struct HStack
A view that arranges its subviews in a horizontal line.

**Examples:**

```swift
@frozen
struct VStack<Content> where Content : View
```

```swift
@frozen
struct VStack<Content> where Content : View
```

```swift
var body: some View {
    VStack(
        alignment: .leading,
        spacing: 10
    ) {
        ForEach(
            1...10,
            id: \.self
        ) {
            Text("Item \($0)")
        }
    }
}
```

```swift
var body: some View {
    VStack(
        alignment: .leading,
        spacing: 10
    ) {
        ForEach(
            1...10,
            id: \.self
        ) {
            Text("Item \($0)")
        }
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/vstack)

---

## HStack

SwiftUI
HStack
Structure
HStack
A view that arranges its subviews in a horizontal line.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
@frozen
struct HStack<Content> where Content : View
Mentioned in
Building layouts with stack views
Creating performant scrollable stacks
Laying out a simple view
Aligning views across stacks
Aligning views within a stack
Overview

Unlike LazyHStack, which only renders the views when your app needs to display them onscreen, an HStack renders the views all at once, regardless of whether they are on- or offscreen. Use the regular HStack when you have a small number of subviews or don’t want the delayed rendering behavior of the “lazy” version.

The following example shows a simple horizontal stack of five text views:

var body: some View {
    HStack(
        alignment: .top,
        spacing: 10
    ) {
        ForEach(
            1...5,
            id: \.self
        ) {
            Text("Item \($0)")
        }
    }
}


Note

If you need a horizontal stack that conforms to the Layout protocol, like when you want to create a conditional layout using AnyLayout, use HStackLayout instead.

Topics
Creating a stack
init(alignment: VerticalAlignment, spacing: CGFloat?, content: () -> Content)
Creates a horizontal stack with the given spacing and vertical alignment.
Relationships
Conforms To
View
See Also
Statically arranging views in one dimension
Building layouts with stack views
Compose complex layouts from primitive container views.
struct VStack
A view that arranges its subviews in a vertical line.

**Examples:**

```swift
@frozen
struct HStack<Content> where Content : View
```

```swift
@frozen
struct HStack<Content> where Content : View
```

```swift
var body: some View {
    HStack(
        alignment: .top,
        spacing: 10
    ) {
        ForEach(
            1...5,
            id: \.self
        ) {
            Text("Item \($0)")
        }
    }
}
```

```swift
var body: some View {
    HStack(
        alignment: .top,
        spacing: 10
    ) {
        ForEach(
            1...5,
            id: \.self
        ) {
            Text("Item \($0)")
        }
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/hstack)

---

## ZStack

SwiftUI
ZStack
Structure
ZStack
A view that overlays its subviews, aligning them in both axes.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
@frozen
struct ZStack<Content> where Content : View
Mentioned in
Building layouts with stack views
Laying out a simple view
Adding a background to your view
Aligning views within a stack
Creating performant scrollable stacks
Overview

The ZStack assigns each successive subview a higher z-axis value than the one before it, meaning later subviews appear “on top” of earlier ones.

The following example creates a ZStack of 100 x 100 point Rectangle views filled with one of six colors, offsetting each successive subview by 10 points so they don’t completely overlap:

let colors: [Color] =
    [.red, .orange, .yellow, .green, .blue, .purple]


var body: some View {
    ZStack {
        ForEach(0..<colors.count) {
            Rectangle()
                .fill(colors[$0])
                .frame(width: 100, height: 100)
                .offset(x: CGFloat($0) * 10.0,
                        y: CGFloat($0) * 10.0)
        }
    }
}


The ZStack uses an Alignment to set the x- and y-axis coordinates of each subview, defaulting to a center alignment. In the following example, the ZStack uses a bottomLeading alignment to lay out two subviews, a red 100 x 50 point rectangle below, and a blue 50 x 100 point rectangle on top. Because of the alignment value, both rectangles share a bottom-left corner with the ZStack (in locales where left is the leading side).

var body: some View {
    ZStack(alignment: .bottomLeading) {
        Rectangle()
            .fill(Color.red)
            .frame(width: 100, height: 50)
        Rectangle()
            .fill(Color.blue)
            .frame(width:50, height: 100)
    }
    .border(Color.green, width: 1)
}


Note

If you need a version of this stack that conforms to the Layout protocol, like when you want to create a conditional layout using AnyLayout, use ZStackLayout instead.

Topics
Creating a stack
init(alignment: Alignment, content: () -> Content)
Creates an instance with the given alignment.
Supporting symbols
struct ZStackContent3D
A type that adds spacing to a ZStack.
Initializers
init<V>(alignment: Alignment, spacing: CGFloat?, content: () -> V)
Creates an instance with the given spacing and alignment.
Relationships
Conforms To
View
See Also
Layering views
Adding a background to your view
Compose a background behind your view and extend it beyond the safe area insets.
func zIndex(Double) -> some View
Controls the display order of overlapping views.
func background<V>(alignment: Alignment, content: () -> V) -> some View
Layers the views that you specify behind this view.
func background<S>(S, ignoresSafeAreaEdges: Edge.Set) -> some View
Sets the view’s background to a style.
func background(ignoresSafeAreaEdges: Edge.Set) -> some View
Sets the view’s background to the default background style.
func background(_:in:fillStyle:)
Sets the view’s background to an insettable shape filled with a style.
func background(in:fillStyle:)
Sets the view’s background to an insettable shape filled with the default background style.
func overlay<V>(alignment: Alignment, content: () -> V) -> some View
Layers the views that you specify in front of this view.
func overlay<S>(S, ignoresSafeAreaEdges: Edge.Set) -> some View
Layers the specified style in front of this view.
func overlay<S, T>(S, in: T, fillStyle: FillStyle) -> some View
Layers a shape that you specify in front of this view.
var backgroundMaterial: Material?
The material underneath the current view.
func containerBackground<S>(S, for: ContainerBackgroundPlacement) -> some View

**Examples:**

```swift
@frozen
struct ZStack<Content> where Content : View
```

```swift
@frozen
struct ZStack<Content> where Content : View
```

```swift
let colors: [Color] =
    [.red, .orange, .yellow, .green, .blue, .purple]


var body: some View {
    ZStack {
        ForEach(0..<colors.count) {
            Rectangle()
                .fill(colors[$0])
                .frame(width: 100, height: 100)
                .offset(x: CGFloat($0) * 10.0,
                        y: CGFloat($0) * 10.0)
        }
    }
}
```

```swift
let colors: [Color] =
    [.red, .orange, .yellow, .green, .blue, .purple]


var body: some View {
    ZStack {
        ForEach(0..<colors.count) {
            Rectangle()
                .fill(colors[$0])
                .frame(width: 100, height: 100)
                .offset(x: CGFloat($0) * 10.0,
                        y: CGFloat($0) * 10.0)
        }
    }
}
```

```swift
var body: some View {
    ZStack(alignment: .bottomLeading) {
        Rectangle()
            .fill(Color.red)
            .frame(width: 100, height: 50)
        Rectangle()
            .fill(Color.blue)
            .frame(width:50, height: 100)
    }
    .border(Color.green, width: 1)
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/zstack)

---

## List

SwiftUI
List
Structure
List
A container that presents rows of data arranged in a single column, optionally providing the ability to select one or more members.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
@MainActor @preconcurrency
struct List<SelectionValue, Content> where SelectionValue : Hashable, Content : View
Mentioned in
Picking container views for your content
Displaying data in lists
Grouping data with lazy stack views
Making a view into a drag source
Migrating to new navigation types
Overview

In its simplest form, a List creates its contents statically, as shown in the following example:

var body: some View {
    List {
        Text("A List Item")
        Text("A Second List Item")
        Text("A Third List Item")
    }
}


More commonly, you create lists dynamically from an underlying collection of data. The following example shows how to create a simple list from an array of an Ocean type which conforms to Identifiable:

struct Ocean: Identifiable {
    let name: String
    let id = UUID()
}


private var oceans = [
    Ocean(name: "Pacific"),
    Ocean(name: "Atlantic"),
    Ocean(name: "Indian"),
    Ocean(name: "Southern"),
    Ocean(name: "Arctic")
]


var body: some View {
    List(oceans) {
        Text($0.name)
    }
}


Supporting selection in lists

To make members of a list selectable, provide a binding to a selection variable. Binding to a single instance of the list data’s Identifiable.ID type creates a single-selection list. Binding to a Set creates a list that supports multiple selections. The following example shows how to add multiselect to the previous example:

struct Ocean: Identifiable, Hashable {
    let name: String
    let id = UUID()
}


private var oceans = [
    Ocean(name: "Pacific"),
    Ocean(name: "Atlantic"),
    Ocean(name: "Indian"),
    Ocean(name: "Southern"),
    Ocean(name: "Arctic")
]


@State private var multiSelection = Set<UUID>()


var body: some View {
    NavigationView {
        List(oceans, selection: $multiSelection) {
            Text($0.name)
        }
        .navigationTitle("Oceans")
        .toolbar { EditButton() }
    }
    Text("\(multiSelection.count) selections")
}


When people make a single selection by tapping or clicking, the selected cell changes its appearance to indicate the selection. To enable multiple selections with tap gestures, put the list into edit mode by either modifying the editMode value, or adding an EditButton to your app’s interface. When you put the list into edit mode, the list shows a circle next to each list item. The circle contains a checkmark when the user selects the associated item. The example above uses an Edit button, which changes its title to Done while in edit mode:

People can make multiple selections without needing to enter edit mode on devices that have a keyboard and mouse or trackpad, like Mac and iPad.

Refreshing the list content

To make the content of the list refreshable using the standard refresh control, use the refreshable(action:) modifier.

The following example shows how to add a standard refresh control to a list. When the user drags the top of the list downward, SwiftUI reveals the refresh control and executes the specified action. Use an await expression inside the action closure to refresh your data. The refresh indicator remains visible for the duration of the awaited operation.

**Examples:**

```swift
@MainActor @preconcurrency
struct List<SelectionValue, Content> where SelectionValue : Hashable, Content : View
```

```swift
@MainActor @preconcurrency
struct List<SelectionValue, Content> where SelectionValue : Hashable, Content : View
```

```swift
var body: some View {
    List {
        Text("A List Item")
        Text("A Second List Item")
        Text("A Third List Item")
    }
}
```

```swift
var body: some View {
    List {
        Text("A List Item")
        Text("A Second List Item")
        Text("A Third List Item")
    }
}
```

```swift
struct Ocean: Identifiable {
    let name: String
    let id = UUID()
}


private var oceans = [
    Ocean(name: "Pacific"),
    Ocean(name: "Atlantic"),
    Ocean(name: "Indian"),
    Ocean(name: "Southern"),
    Ocean(name: "Arctic")
]


var body: some View {
    List(oceans) {
        Text($0.name)
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/list)

---

## ForEach

SwiftUI
ForEach
Structure
ForEach
A structure that computes views on demand from an underlying collection of identified data.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
struct ForEach<Data, ID, Content> where Data : RandomAccessCollection, ID : Hashable
Mentioned in
Creating performant scrollable stacks
Displaying data in lists
Grouping data with lazy stack views
Picking container views for your content
Overview

Use ForEach to provide views based on a RandomAccessCollection of some data type. Either the collection’s elements must conform to Identifiable or you need to provide an id parameter to the ForEach initializer.

The following example creates a NamedFont type that conforms to Identifiable, and an array of this type called namedFonts. A ForEach instance iterates over the array, producing new Text instances that display examples of each SwiftUI Font style provided in the array.

private struct NamedFont: Identifiable {
    let name: String
    let font: Font
    var id: String { name }
}


private let namedFonts: [NamedFont] = [
    NamedFont(name: "Large Title", font: .largeTitle),
    NamedFont(name: "Title", font: .title),
    NamedFont(name: "Headline", font: .headline),
    NamedFont(name: "Body", font: .body),
    NamedFont(name: "Caption", font: .caption)
]


var body: some View {
    ForEach(namedFonts) { namedFont in
        Text(namedFont.name)
            .font(namedFont.font)
    }
}


Some containers like List or LazyVStack will query the elements within a for each lazily. To obtain maximal performance, ensure that the view created from each element in the collection represents a constant number of views.

For example, the following view uses an if statement which means each element of the collection can represent either 1 or 0 views, a non-constant number.

ForEach(namedFonts) { namedFont in
    if namedFont.name.count != 2 {
        Text(namedFont.name)
    }
}


You can make the above view represent a constant number of views by wrapping the condition in a VStack, an HStack, or a ZStack.

ForEach(namedFonts) { namedFont in
    VStack {
        if namedFont.name.count != 2 {
            Text(namedFont.name)
        }
    }
}


When enabling the following launch argument, SwiftUI will log when it encounters a view that produces a non-constant number of views in these containers:

-LogForEachSlowPath YES

Topics
Creating a collection
init(Data)
Creates an instance that uniquely identifies and creates table rows across updates based on the identity of the underlying data.
init(_:content:)
Creates an instance that uniquely identifies and creates map content across updates based on the identity of the underlying data.
init(_:id:content:)
Creates an instance that uniquely identifies and creates map content across updates based on the provided key path to the underlying data’s identifier.
Creating an editable collection
init<C, R>(Binding<C>, editActions: EditActions<C>, content: (Binding<C.Element>) -> R)
Creates an instance that uniquely identifies and creates views across updates based on the identity of the underlying data.
init<C, R>(Binding<C>, id: KeyPath<C.Element, ID>, editActions: EditActions<C>, content: (Binding<C.Element>) -> R)
Creates an instance that uniquely identifies and creates views across updates based on the identity of the underlying data.
Accessing content
var content: (Data.Element) -> Content
A function to create content on demand using the underlying data.
var data: Data
The collection of underlying identified data that SwiftUI uses to create views dynamically.
Initializers
init<V>(sections: V, content: (SectionConfiguration) -> Content)
Creates an instance that uniquely identifies and creates views across updates based on the sections of a given view.
init<V>(subviews: V, content: (Subview) -> Content)
Creates an instance that uniquely identifies and creates views across updates based on the subviews of a given view.
Relationships
Conforms To
AccessibilityRotorContent

**Examples:**

```swift
struct ForEach<Data, ID, Content> where Data : RandomAccessCollection, ID : Hashable
```

```swift
struct ForEach<Data, ID, Content> where Data : RandomAccessCollection, ID : Hashable
```

```swift
RandomAccessCollection
```

```swift
private struct NamedFont: Identifiable {
    let name: String
    let font: Font
    var id: String { name }
}


private let namedFonts: [NamedFont] = [
    NamedFont(name: "Large Title", font: .largeTitle),
    NamedFont(name: "Title", font: .title),
    NamedFont(name: "Headline", font: .headline),
    NamedFont(name: "Body", font: .body),
    NamedFont(name: "Caption", font: .caption)
]


var body: some View {
    ForEach(namedFonts) { namedFont in
        Text(namedFont.name)
            .font(namedFont.font)
    }
}
```

```swift
private struct NamedFont: Identifiable {
    let name: String
    let font: Font
    var id: String { name }
}


private let namedFonts: [NamedFont] = [
    NamedFont(name: "Large Title", font: .largeTitle),
    NamedFont(name: "Title", font: .title),
    NamedFont(name: "Headline", font: .headline),
    NamedFont(name: "Body", font: .body),
    NamedFont(name: "Caption", font: .caption)
]


var body: some View {
    ForEach(namedFonts) { namedFont in
        Text(namedFont.name)
            .font(namedFont.font)
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/foreach)

---

## LazyVStack

SwiftUI
LazyVStack
Structure
LazyVStack
A view that arranges its children in a line that grows vertically, creating items only as needed.
iOS 14.0+
iPadOS 14.0+
Mac Catalyst 14.0+
macOS 11.0+
tvOS 14.0+
visionOS 1.0+
watchOS 7.0+
struct LazyVStack<Content> where Content : View
Mentioned in
Grouping data with lazy stack views
Picking container views for your content
Creating performant scrollable stacks
Displaying data in lists
Overview

The stack is “lazy,” in that the stack view doesn’t create items until it needs to render them onscreen.

In the following example, a ScrollView contains a LazyVStack that consists of a vertical row of text views. The stack aligns to the leading edge of the scroll view, and uses default spacing between the text views.

ScrollView {
    LazyVStack(alignment: .leading) {
        ForEach(1...100, id: \.self) {
            Text("Row \($0)")
        }
    }
}

Topics
Creating a lazy-loading vertical stack
init(alignment: HorizontalAlignment, spacing: CGFloat?, pinnedViews: PinnedScrollableViews, content: () -> Content)
Creates a lazy vertical stack view with the given spacing, vertical alignment, pinning behavior, and content.
Relationships
Conforms To
View
See Also
Dynamically arranging views in one dimension
Grouping data with lazy stack views
Split content into logical sections inside lazy stack views.
Creating performant scrollable stacks
Display large numbers of repeated views efficiently with scroll views, stack views, and lazy stacks.
struct LazyHStack
A view that arranges its children in a line that grows horizontally, creating items only as needed.
struct PinnedScrollableViews
A set of view types that may be pinned to the bounds of a scroll view.

**Examples:**

```swift
struct LazyVStack<Content> where Content : View
```

```swift
struct LazyVStack<Content> where Content : View
```

```swift
ScrollView {
    LazyVStack(alignment: .leading) {
        ForEach(1...100, id: \.self) {
            Text("Row \($0)")
        }
    }
}
```

```swift
ScrollView {
    LazyVStack(alignment: .leading) {
        ForEach(1...100, id: \.self) {
            Text("Row \($0)")
        }
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/lazyvstack)

---

## LazyHStack

SwiftUI
LazyHStack
Structure
LazyHStack
A view that arranges its children in a line that grows horizontally, creating items only as needed.
iOS 14.0+
iPadOS 14.0+
Mac Catalyst 14.0+
macOS 11.0+
tvOS 14.0+
visionOS 1.0+
watchOS 7.0+
struct LazyHStack<Content> where Content : View
Mentioned in
Creating performant scrollable stacks
Grouping data with lazy stack views
Picking container views for your content
Overview

The stack is “lazy,” in that the stack view doesn’t create items until it needs to render them onscreen.

In the following example, a ScrollView contains a LazyHStack that consists of a horizontal row of text views. The stack aligns to the top of the scroll view and uses 10-point spacing between each text view.

ScrollView(.horizontal) {
    LazyHStack(alignment: .top, spacing: 10) {
        ForEach(1...100, id: \.self) {
            Text("Column \($0)")
        }
    }
}

Topics
Creating a lazy-loading horizontal stack
init(alignment: VerticalAlignment, spacing: CGFloat?, pinnedViews: PinnedScrollableViews, content: () -> Content)
Creates a lazy horizontal stack view with the given spacing, vertical alignment, pinning behavior, and content.
Relationships
Conforms To
View
See Also
Dynamically arranging views in one dimension
Grouping data with lazy stack views
Split content into logical sections inside lazy stack views.
Creating performant scrollable stacks
Display large numbers of repeated views efficiently with scroll views, stack views, and lazy stacks.
struct LazyVStack
A view that arranges its children in a line that grows vertically, creating items only as needed.
struct PinnedScrollableViews
A set of view types that may be pinned to the bounds of a scroll view.

**Examples:**

```swift
struct LazyHStack<Content> where Content : View
```

```swift
struct LazyHStack<Content> where Content : View
```

```swift
ScrollView(.horizontal) {
    LazyHStack(alignment: .top, spacing: 10) {
        ForEach(1...100, id: \.self) {
            Text("Column \($0)")
        }
    }
}
```

```swift
ScrollView(.horizontal) {
    LazyHStack(alignment: .top, spacing: 10) {
        ForEach(1...100, id: \.self) {
            Text("Column \($0)")
        }
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/lazyhstack)

---

## LazyVGrid

SwiftUI
LazyVGrid
Structure
LazyVGrid
A container view that arranges its child views in a grid that grows vertically, creating items only as needed.
iOS 14.0+
iPadOS 14.0+
Mac Catalyst 14.0+
macOS 11.0+
tvOS 14.0+
visionOS 1.0+
watchOS 7.0+
struct LazyVGrid<Content> where Content : View
Mentioned in
Picking container views for your content
Overview

Use a lazy vertical grid when you want to display a large, vertically scrollable collection of views arranged in a two dimensional layout. The first view that you provide to the grid’s content closure appears in the top row of the column that’s on the grid’s leading edge. Additional views occupy successive cells in the grid, filling the first row from leading to trailing edges, then the second row, and so on. The number of rows can grow unbounded, but you specify the number of columns by providing a corresponding number of GridItem instances to the grid’s initializer.

The grid in the following example defines two columns and uses a ForEach structure to repeatedly generate a pair of Text views for the columns in each row:

struct VerticalSmileys: View {
    let columns = [GridItem(.flexible()), GridItem(.flexible())]


    var body: some View {
         ScrollView {
             LazyVGrid(columns: columns) {
                 ForEach(0x1f600...0x1f679, id: \.self) { value in
                     Text(String(format: "%x", value))
                     Text(emoji(value))
                         .font(.largeTitle)
                 }
             }
         }
    }


    private func emoji(_ value: Int) -> String {
        guard let scalar = UnicodeScalar(value) else { return "?" }
        return String(Character(scalar))
    }
}


For each row in the grid, the first column shows a Unicode code point from the “Smileys” group, and the second shows its corresponding emoji:

You can achieve a similar layout using a Grid container. Unlike a lazy grid, which creates child views only when SwiftUI needs to display them, a regular grid creates all of its child views right away. This enables the grid to provide better support for cell spacing and alignment. Only use a lazy grid if profiling your app shows that a Grid view performs poorly because it tries to load too many views at once.

Topics
Creating a vertical grid
init(columns: [GridItem], alignment: HorizontalAlignment, spacing: CGFloat?, pinnedViews: PinnedScrollableViews, content: () -> Content)
Creates a grid that grows vertically.
Relationships
Conforms To
View
See Also
Dynamically arranging views in two dimensions
struct LazyHGrid
A container view that arranges its child views in a grid that grows horizontally, creating items only as needed.
struct GridItem
A description of a row or a column in a lazy grid.

**Examples:**

```swift
struct LazyVGrid<Content> where Content : View
```

```swift
struct LazyVGrid<Content> where Content : View
```

```swift
struct VerticalSmileys: View {
    let columns = [GridItem(.flexible()), GridItem(.flexible())]


    var body: some View {
         ScrollView {
             LazyVGrid(columns: columns) {
                 ForEach(0x1f600...0x1f679, id: \.self) { value in
                     Text(String(format: "%x", value))
                     Text(emoji(value))
                         .font(.largeTitle)
                 }
             }
         }
    }


    private func emoji(_ value: Int) -> String {
        guard let scalar = UnicodeScalar(value) else { return "?" }
        return String(Character(scalar))
    }
}
```

```swift
struct VerticalSmileys: View {
    let columns = [GridItem(.flexible()), GridItem(.flexible())]


    var body: some View {
         ScrollView {
             LazyVGrid(columns: columns) {
                 ForEach(0x1f600...0x1f679, id: \.self) { value in
                     Text(String(format: "%x", value))
                     Text(emoji(value))
                         .font(.largeTitle)
                 }
             }
         }
    }


    private func emoji(_ value: Int) -> String {
        guard let scalar = UnicodeScalar(value) else { return "?" }
        return String(Character(scalar))
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/lazyvgrid)

---

## LazyHGrid

SwiftUI
LazyHGrid
Structure
LazyHGrid
A container view that arranges its child views in a grid that grows horizontally, creating items only as needed.
iOS 14.0+
iPadOS 14.0+
Mac Catalyst 14.0+
macOS 11.0+
tvOS 14.0+
visionOS 1.0+
watchOS 7.0+
struct LazyHGrid<Content> where Content : View
Mentioned in
Picking container views for your content
Overview

Use a lazy horizontal grid when you want to display a large, horizontally scrollable collection of views arranged in a two dimensional layout. The first view that you provide to the grid’s content closure appears in the top row of the column that’s on the grid’s leading edge. Additional views occupy successive cells in the grid, filling the first column from top to bottom, then the second column, and so on. The number of columns can grow unbounded, but you specify the number of rows by providing a corresponding number of GridItem instances to the grid’s initializer.

The grid in the following example defines two rows and uses a ForEach structure to repeatedly generate a pair of Text views for the rows in each column:

struct HorizontalSmileys: View {
    let rows = [GridItem(.fixed(30)), GridItem(.fixed(30))]


    var body: some View {
        ScrollView(.horizontal) {
            LazyHGrid(rows: rows) {
                ForEach(0x1f600...0x1f679, id: \.self) { value in
                    Text(String(format: "%x", value))
                    Text(emoji(value))
                        .font(.largeTitle)
                }
            }
        }
    }


    private func emoji(_ value: Int) -> String {
        guard let scalar = UnicodeScalar(value) else { return "?" }
        return String(Character(scalar))
    }
}


For each column in the grid, the top row shows a Unicode code point from the “Smileys” group, and the bottom shows its corresponding emoji:

You can achieve a similar layout using a Grid container. Unlike a lazy grid, which creates child views only when SwiftUI needs to display them, a regular grid creates all of its child views right away. This enables the grid to provide better support for cell spacing and alignment. Only use a lazy grid if profiling your app shows that a Grid view performs poorly because it tries to load too many views at once.

Topics
Creating a horizontal grid
init(rows: [GridItem], alignment: VerticalAlignment, spacing: CGFloat?, pinnedViews: PinnedScrollableViews, content: () -> Content)
Creates a grid that grows horizontally.
Relationships
Conforms To
View
See Also
Dynamically arranging views in two dimensions
struct LazyVGrid
A container view that arranges its child views in a grid that grows vertically, creating items only as needed.
struct GridItem
A description of a row or a column in a lazy grid.

**Examples:**

```swift
struct LazyHGrid<Content> where Content : View
```

```swift
struct LazyHGrid<Content> where Content : View
```

```swift
struct HorizontalSmileys: View {
    let rows = [GridItem(.fixed(30)), GridItem(.fixed(30))]


    var body: some View {
        ScrollView(.horizontal) {
            LazyHGrid(rows: rows) {
                ForEach(0x1f600...0x1f679, id: \.self) { value in
                    Text(String(format: "%x", value))
                    Text(emoji(value))
                        .font(.largeTitle)
                }
            }
        }
    }


    private func emoji(_ value: Int) -> String {
        guard let scalar = UnicodeScalar(value) else { return "?" }
        return String(Character(scalar))
    }
}
```

```swift
struct HorizontalSmileys: View {
    let rows = [GridItem(.fixed(30)), GridItem(.fixed(30))]


    var body: some View {
        ScrollView(.horizontal) {
            LazyHGrid(rows: rows) {
                ForEach(0x1f600...0x1f679, id: \.self) { value in
                    Text(String(format: "%x", value))
                    Text(emoji(value))
                        .font(.largeTitle)
                }
            }
        }
    }


    private func emoji(_ value: Int) -> String {
        guard let scalar = UnicodeScalar(value) else { return "?" }
        return String(Character(scalar))
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/lazyhgrid)

---

## Grid

SwiftUI
Grid
Structure
Grid
A container view that arranges other views in a two dimensional layout.
iOS 16.0+
iPadOS 16.0+
Mac Catalyst 16.0+
macOS 13.0+
tvOS 16.0+
visionOS 1.0+
watchOS 9.0+
@frozen
struct Grid<Content> where Content : View
Overview

Create a two dimensional layout by initializing a Grid with a collection of GridRow structures. The first view in each grid row appears in the grid’s first column, the second view in the second column, and so on. The following example creates a grid with two rows and two columns:

Grid {
    GridRow {
        Text("Hello")
        Image(systemName: "globe")
    }
    GridRow {
        Image(systemName: "hand.wave")
        Text("World")
    }
}


A grid and its rows behave something like a collection of HStack instances wrapped in a VStack. However, the grid handles row and column creation as a single operation, which applies alignment and spacing to cells, rather than first to rows and then to a column of unrelated rows. The grid produced by the example above demonstrates this:

Note

If you need a grid that conforms to the Layout protocol, like when you want to create a conditional layout using AnyLayout, use GridLayout instead.

Multicolumn cells

If you provide a view rather than a GridRow as an element in the grid’s content, the grid uses the view to create a row that spans all of the grid’s columns. For example, you can add a Divider between the rows of the previous example:

Grid {
    GridRow {
        Text("Hello")
        Image(systemName: "globe")
    }
    Divider()
    GridRow {
        Image(systemName: "hand.wave")
        Text("World")
    }
}


Because a divider takes as much horizontal space as its parent offers, the entire grid widens to fill the width offered by its parent view.

To prevent a flexible view from taking more space on a given axis than the other cells in a row or column require, add the gridCellUnsizedAxes(_:) view modifier to the view:

Divider()
    .gridCellUnsizedAxes(.horizontal)


This restores the grid to the width that the text and images require:

To make a cell span a specific number of columns rather than the whole grid, use the gridCellColumns(_:) modifier on a view that’s contained inside a GridRow.

Column count

The grid’s column count grows to handle the row with the largest number of columns. If you create rows with different numbers of columns, the grid adds empty cells to the trailing edge of rows that have fewer columns. The example below creates three rows with different column counts:

Grid {
    GridRow {
        Text("Row 1")
        ForEach(0..<2) { _ in Color.red }
    }
    GridRow {
        Text("Row 2")
        ForEach(0..<5) { _ in Color.green }
    }
    GridRow {
        Text("Row 3")
        ForEach(0..<4) { _ in Color.blue }
    }
}


The resulting grid has as many columns as the widest row, adding empty cells to rows that don’t specify enough views:

The grid sets the width of all the cells in a column to match the needs of column’s widest cell. In the example above, the width of the first column depends on the width of the widest Text view that the column contains. The other columns, which contain flexible Color views, share the remaining horizontal space offered by the grid’s parent view equally.

Similarly, the tallest cell in a row sets the height of the entire row. The cells in the first column of the grid above need only the height required for each string, but the Color cells expand to equally share the total height available to the grid. As a result, the color cells determine the row heights.

Cell spacing and alignment

You can control the spacing between cells in both the horizontal and vertical dimensions and set a default alignment for the content in all the grid cells when you initialize the grid using the init(alignment:horizontalSpacing:verticalSpacing:content:) initializer. Consider a modified version of the previous example:

Grid(alignment: .bottom, horizontalSpacing: 1, verticalSpacing: 1) {
    // ...
}



**Examples:**

```swift
@frozen
struct Grid<Content> where Content : View
```

```swift
@frozen
struct Grid<Content> where Content : View
```

```swift
Grid {
    GridRow {
        Text("Hello")
        Image(systemName: "globe")
    }
    GridRow {
        Image(systemName: "hand.wave")
        Text("World")
    }
}
```

```swift
Grid {
    GridRow {
        Text("Hello")
        Image(systemName: "globe")
    }
    GridRow {
        Image(systemName: "hand.wave")
        Text("World")
    }
}
```

```swift
Grid {
    GridRow {
        Text("Hello")
        Image(systemName: "globe")
    }
    Divider()
    GridRow {
        Image(systemName: "hand.wave")
        Text("World")
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/grid)

---

## GridRow

SwiftUI
GridRow
Structure
GridRow
A horizontal row in a two dimensional grid container.
iOS 16.0+
iPadOS 16.0+
Mac Catalyst 16.0+
macOS 13.0+
tvOS 16.0+
visionOS 1.0+
watchOS 9.0+
@frozen
struct GridRow<Content> where Content : View
Overview

Use one or more GridRow instances to define the rows of a Grid container. The child views inside the row define successive grid cells. You can add rows to the grid explicitly, or use the ForEach structure to generate multiple rows. Similarly, you can add cells to the row explicitly or you can use ForEach to generate multiple cells inside the row. The following example mixes these strategies:

Grid {
    GridRow {
        Color.clear
            .gridCellUnsizedAxes([.horizontal, .vertical])
        ForEach(1..<4) { column in
            Text("C\(column)")
        }
    }
    ForEach(1..<4) { row in
        GridRow {
            Text("R\(row)")
            ForEach(1..<4) { _ in
                Circle().foregroundStyle(.mint)
            }
        }
    }
}


The grid in the example above has an explicit first row and three generated rows. Similarly, each row has an explicit first cell and three generated cells:

To create an empty cell, use something invisible, like the clear color that appears in the first column of the first row in the example above. However, if you use a flexible view like a Color or a Spacer, you might also need to add the gridCellUnsizedAxes(_:) modifier to prevent the view from taking up more space than the other cells in the row or column need.

Important

You can’t use EmptyView to create a blank cell because that resolves to the absence of a view and doesn’t generate a cell.

By default, the cells in the row use the Alignment that you define when you initialize the Grid. However, you can override the vertical alignment for the cells in a row by providing a VerticalAlignment value to the row’s init(alignment:content:) initializer.

If you apply a view modifier to a row, the row applies the modifier to all of the cells, similar to how a Group behaves. For example, if you apply the border(_:width:) modifier to a row, SwiftUI draws a border on each cell in the row rather than around the row.

Topics
Creating a grid row
init(alignment: VerticalAlignment?, content: () -> Content)
Creates a horizontal row of child views in a grid.
Relationships
Conforms To
Copyable
View
Conforms when Content conforms to View.
See Also
Statically arranging views in two dimensions
struct Grid
A container view that arranges other views in a two dimensional layout.
func gridCellColumns(Int) -> some View
Tells a view that acts as a cell in a grid to span the specified number of columns.
func gridCellAnchor(UnitPoint) -> some View
Specifies a custom alignment anchor for a view that acts as a grid cell.
func gridCellUnsizedAxes(Axis.Set) -> some View
Asks grid layouts not to offer the view extra size in the specified axes.
func gridColumnAlignment(HorizontalAlignment) -> some View
Overrides the default horizontal alignment of the grid column that the view appears in.

**Examples:**

```swift
@frozen
struct GridRow<Content> where Content : View
```

```swift
@frozen
struct GridRow<Content> where Content : View
```

```swift
Grid {
    GridRow {
        Color.clear
            .gridCellUnsizedAxes([.horizontal, .vertical])
        ForEach(1..<4) { column in
            Text("C\(column)")
        }
    }
    ForEach(1..<4) { row in
        GridRow {
            Text("R\(row)")
            ForEach(1..<4) { _ in
                Circle().foregroundStyle(.mint)
            }
        }
    }
}
```

```swift
Grid {
    GridRow {
        Color.clear
            .gridCellUnsizedAxes([.horizontal, .vertical])
        ForEach(1..<4) { column in
            Text("C\(column)")
        }
    }
    ForEach(1..<4) { row in
        GridRow {
            Text("R\(row)")
            ForEach(1..<4) { _ in
                Circle().foregroundStyle(.mint)
            }
        }
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/gridrow)

---

## Spacer

SwiftUI
Spacer
Structure
Spacer
A flexible space that expands along the major axis of its containing stack layout, or on both axes if not contained in a stack.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
@frozen
struct Spacer
Mentioned in
Building layouts with stack views
Adding a background to your view
Picking container views for your content
Overview

A spacer creates an adaptive view with no content that expands as much as it can. For example, when placed within an HStack, a spacer expands horizontally as much as the stack allows, moving sibling views out of the way, within the limits of the stack’s size. SwiftUI sizes a stack that doesn’t contain a spacer up to the combined ideal widths of the content of the stack’s child views.

The following example provides a simple checklist row to illustrate how you can use a spacer:

struct ChecklistRow: View {
    let name: String


    var body: some View {
        HStack {
            Image(systemName: "checkmark")
            Text(name)
        }
        .border(Color.blue)
    }
}


Adding a spacer before the image creates an adaptive view with no content that expands to push the image and text to the right side of the stack. The stack also now expands to take as much space as the parent view allows, shown by the blue border that indicates the boundary of the stack:

struct ChecklistRow: View {
    let name: String


    var body: some View {
        HStack {
            Spacer()
            Image(systemName: "checkmark")
            Text(name)
        }
        .border(Color.blue)
    }
}


Moving the spacer between the image and the name pushes those elements to the left and right sides of the HStack, respectively. Because the stack contains the spacer, it expands to take as much horizontal space as the parent view allows; the blue border indicates its size:

struct ChecklistRow: View {
    let name: String


    var body: some View {
        HStack {
            Image(systemName: "checkmark")
            Spacer()
            Text(name)
        }
        .border(Color.blue)
    }
}


Adding two spacer views on the outside of the stack leaves the image and text together, while the stack expands to take as much horizontal space as the parent view allows:

struct ChecklistRow: View {
    let name: String


    var body: some View {
        HStack {
            Spacer()
            Image(systemName: "checkmark")
            Text(name)
            Spacer()
        }
        .border(Color.blue)
    }
}


Topics
Creating a spacer
init(minLength: CGFloat?)
var minLength: CGFloat?
The minimum length this spacer can be shrunk to, along the axis or axes of expansion.
Relationships
Conforms To
BitwiseCopyable
Copyable
Sendable

**Examples:**

```swift
@frozen
struct Spacer
```

```swift
@frozen
struct Spacer
```

```swift
struct ChecklistRow: View {
    let name: String


    var body: some View {
        HStack {
            Image(systemName: "checkmark")
            Text(name)
        }
        .border(Color.blue)
    }
}
```

```swift
struct ChecklistRow: View {
    let name: String


    var body: some View {
        HStack {
            Image(systemName: "checkmark")
            Text(name)
        }
        .border(Color.blue)
    }
}
```

```swift
struct ChecklistRow: View {
    let name: String


    var body: some View {
        HStack {
            Spacer()
            Image(systemName: "checkmark")
            Text(name)
        }
        .border(Color.blue)
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/spacer)

---

## Divider

SwiftUI
Divider
Structure
Divider
A visual element that can be used to separate other content.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
struct Divider
Mentioned in
Building layouts with stack views
Populating SwiftUI menus with adaptive controls
Overview

When contained in a stack, the divider extends across the minor axis of the stack, or horizontally when not in a stack.

Topics
Creating a divider
init()
Relationships
Conforms To
View
See Also
Separators
struct Spacer
A flexible space that expands along the major axis of its containing stack layout, or on both axes if not contained in a stack.

**Examples:**

```swift
struct Divider
```

```swift
struct Divider
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/divider)

---

## NavigationStack

SwiftUI
NavigationStack
Structure
NavigationStack
A view that displays a root view and enables you to present additional views over the root view.
iOS 16.0+
iPadOS 16.0+
Mac Catalyst 16.0+
macOS 13.0+
tvOS 16.0+
visionOS 1.0+
watchOS 9.0+
@MainActor @preconcurrency
struct NavigationStack<Data, Root> where Root : View
Mentioned in
Migrating to new navigation types
Adding a search interface to your app
Understanding the navigation stack
Overview

Use a navigation stack to present a stack of views over a root view. People can add views to the top of the stack by clicking or tapping a NavigationLink, and remove views using built-in, platform-appropriate controls, like a Back button or a swipe gesture. The stack always displays the most recently added view that hasn’t been removed, and doesn’t allow the root view to be removed.

To create navigation links, associate a view with a data type by adding a navigationDestination(for:destination:) modifier inside the stack’s view hierarchy. Then initialize a NavigationLink that presents an instance of the same kind of data. The following stack displays a ParkDetails view for navigation links that present data of type Park:

NavigationStack {
    List(parks) { park in
        NavigationLink(park.name, value: park)
    }
    .navigationDestination(for: Park.self) { park in
        ParkDetails(park: park)
    }
}


In this example, the List acts as the root view and is always present. Selecting a navigation link from the list adds a ParkDetails view to the stack, so that it covers the list. Navigating back removes the detail view and reveals the list again. The system disables backward navigation controls when the stack is empty and the root view, namely the list, is visible.

Manage navigation state

By default, a navigation stack manages state to keep track of the views on the stack. However, your code can share control of the state by initializing the stack with a binding to a collection of data values that you create. The stack adds items to the collection as it adds views to the stack and removes items when it removes views. For example, you can create a State property to manage the navigation for the park detail view:

@State private var presentedParks: [Park] = []


Initializing the state as an empty array indicates a stack with no views. Provide a Binding to this state property using the dollar sign ($) prefix when you create a stack using the init(path:root:) initializer:

NavigationStack(path: $presentedParks) {
    List(parks) { park in
        NavigationLink(park.name, value: park)
    }
    .navigationDestination(for: Park.self) { park in
        ParkDetails(park: park)
    }
}


Like before, when someone taps or clicks the navigation link for a park, the stack displays the ParkDetails view using the associated park data. However, now the stack also puts the park data in the presentedParks array. Your code can observe this array to read the current stack state. It can also modify the array to change the views on the stack. For example, you can create a method that configures the stack with a specific set of parks:

func showParks() {
    presentedParks = [Park("Yosemite"), Park("Sequoia")]
}


The showParks method replaces the stack’s display with a view that shows details for Sequoia, the last item in the new presentedParks array. Navigating back from that view removes Sequoia from the array, which reveals a view that shows details for Yosemite. Use a path to support deep links, state restoration, or other kinds of programmatic navigation.

Navigate to different view types

To create a stack that can present more than one kind of view, you can add multiple navigationDestination(for:destination:) modifiers inside the stack’s view hierarchy, with each modifier presenting a different data type. The stack matches navigation links with navigation destinations based on their respective data types.

To create a path for programmatic navigation that contains more than one kind of data, you can use a NavigationPath instance as the path.

Topics
Creating a navigation stack
init(root: () -> Root)
Creates a navigation stack that manages its own navigation state.
Creating a navigation stack with a path
init(path:root:)
Creates a navigation stack with homogeneous navigation state that you can control.
Relationships
Conforms To
View
See Also
Stacking views in one column
struct NavigationPath
A type-erased list of data representing the content of a navigation stack.
func navigationDestination<D, C>(for: D.Type, destination: (D) -> C) -> some View
Associates a destination view with a presented data type for use within a navigation stack.
func navigationDestination<V>(isPresented: Binding<Bool>, destination: () -> V) -> some View
Associates a destination view with a binding that can be used to push the view onto a NavigationStack.
func navigationDestination<D, C>(item: Binding<Optional<D>>, destination: (D) -> C) -> some View
Associates a destination view with a bound value for use within a navigation stack or navigation split view

**Examples:**

```swift
@MainActor @preconcurrency
struct NavigationStack<Data, Root> where Root : View
```

```swift
@MainActor @preconcurrency
struct NavigationStack<Data, Root> where Root : View
```

```swift
NavigationStack {
    List(parks) { park in
        NavigationLink(park.name, value: park)
    }
    .navigationDestination(for: Park.self) { park in
        ParkDetails(park: park)
    }
}
```

```swift
NavigationStack {
    List(parks) { park in
        NavigationLink(park.name, value: park)
    }
    .navigationDestination(for: Park.self) { park in
        ParkDetails(park: park)
    }
}
```

```swift
@State private var presentedParks: [Park] = []
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/navigationstack)

---

