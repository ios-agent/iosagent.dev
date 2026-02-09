# Controls

SwiftUI controls documentation.

---

## Button

SwiftUI
Button
Structure
Button
A control that initiates an action.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
struct Button<Label> where Label : View
Mentioned in
Building and customizing the menu bar with SwiftUI
Configuring views
Managing search interface activation
Populating SwiftUI menus with adaptive controls
Overview

You create a button by providing an action and a label. The action is either a method or closure property that does something when a user clicks or taps the button. The label is a view that describes the button’s action — for example, by showing text, an icon, or both.

The label of a button can be any kind of view, such as a Text view for text-only labels:

Button(action: signIn) {
    Text("Sign In")
}


Or a Label view, for buttons with both a title and an icon:

Button(action: signIn) {
    Label("Sign In", systemImage: "arrow.up")
}


For those common cases, you can also use the convenience initializers that take a title string or LocalizedStringKey as their first parameter, and optionally a system image name or ImageResource as their second parameter, instead of a trailing closure:

Button("Sign In", systemImage: "arrow.up", action: signIn)


Prefer to use these convenience initializers, or a Label view, when providing both a title and an icon. This allows the button to dynamically adapt its appearance to render its title and icon correctly in containers such as toolbars and menus. For example, on iOS, buttons only display their icons by default when placed in toolbars, but show both a leading title and trailing icon in menus. Defining labels this way also helps with accessibility — for example, applying the labelStyle(_:) modifier with an iconOnly style to the button will cause it to only visually display its icon, but still use its title to describe the button in accessibility modes like VoiceOver:

Button("Sign In", systemImage: "arrow.up", action: signIn)
    .labelStyle(.iconOnly)


Avoid labels that only use images or exclusively visual components without an accessibility label.

How the user activates the button varies by platform:

In iOS and watchOS, the user taps the button.

In macOS, the user clicks the button.

In tvOS, the user presses “select” on an external remote, like the Siri Remote, while focusing on the button.

The appearance of the button depends on factors like where you place it, whether you assign it a role, and how you style it.

Adding buttons to containers

Use buttons for any user interface element that initiates an action. Buttons automatically adapt their visual style to match the expected style within these different containers and contexts. For example, to create a List cell that initiates an action when selected by the user, add a button to the list’s content:

List {
    // Cells that show all the current folders.
    ForEach(folders) { folder in
        Text(folder.title)
    }


    // A cell that, when selected, adds a new folder.
    Button(action: addItem) {
        Label("Add Folder", systemImage: "folder.badge.plus")
    }
}


Similarly, to create a context menu item that initiates an action, add a button to the contextMenu(_:) modifier’s content closure:

.contextMenu {
    Button("Cut", action: cut)
    Button("Copy", action: copy)
    Button("Paste", action: paste)
}


This pattern extends to most other container views in SwiftUI that have customizable, interactive content, like Form instances.

Assigning a role

You can optionally initialize a button with a ButtonRole that characterizes the button’s purpose. For example, you can create a destructive button for a deletion action:

 Button("Delete", role: .destructive, action: delete)


The system uses the button’s role to style the button appropriately in every context. For example, a destructive button in a contextual menu appears with a red foreground color:

If you don’t specify a role for a button, the system applies an appropriate default appearance.

Styling buttons

**Examples:**

```swift
struct Button<Label> where Label : View
```

```swift
struct Button<Label> where Label : View
```

```swift
Button(action: signIn) {
    Text("Sign In")
}
```

```swift
Button(action: signIn) {
    Text("Sign In")
}
```

```swift
Button(action: signIn) {
    Label("Sign In", systemImage: "arrow.up")
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/button)

---

## SecureField

SwiftUI
SecureField
Structure
SecureField
A control into which people securely enter private text.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
struct SecureField<Label> where Label : View
Overview

Use a secure field when you want the behavior of a TextField, but you want to hide the field’s text. Typically, you use this for entering passwords and other sensitive information, as the second field in the following screenshot demonstrates:

macOS
iOS

The field:

Displays one dot for each character someone types.

Hides the dots when someone takes a screenshot in iOS.

Prevents anyone from cutting or copying the field’s contents.

Displays an indicator when Caps Lock is enabled.

Bind to a string

A secure field binds to a string value and updates the string on every keystroke or other edit, so you can read its value at any time from elsewhere in your code. The following code shows how to create the above interface, with the secure field bound to a password string:

@State private var username: String = ""
@State private var password: String = ""


var body: some View {
    VStack {
        TextField("Username", text: $username)
            .autocorrectionDisabled(true)
            #if !os(macOS)
            .textInputAutocapitalization(.never)
            #endif


        SecureField("Password", text: $password)
            .onSubmit {
                handleLogin(username: username, password: password)
            }
    }
    .textFieldStyle(.roundedBorder)
}


The field in the above example has an onSubmit(of:_:) modifier that sends the username and password strings to a custom handleLogin(username:password:) method if someone presses the Return key while the secure field has focus. You can alternatively provide another mechanism — like a button — to do the same thing.

Guide people with a prompt

In addition to the string or view that you provide as a label, you can also provide a Text view prompt to help guide someone who uses the field, as the following Form does:

Form {
    TextField(text: $username, prompt: Text("Required")) {
        Text("Username")
    }
    .autocorrectionDisabled(true)
    #if !os(macOS)
    .textInputAutocapitalization(.never)
    #endif


    SecureField(text: $password, prompt: Text("Required")) {
        Text("Password")
    }
}


The system uses the label and prompt in different ways depending on the context. For example, a form in macOS places the label against the leading edge of the field and uses the prompt as placeholder text inside the field. The same form in iOS also uses the prompt as placeholder text, but doesn’t display the label:

macOS
iOS

If you remove the prompt from the previous example, the field keeps the label on the leading edge and omits the placeholder text in macOS, but displays the label as a placeholder in iOS:

macOS
iOS

Topics
Creating a secure text field
init(_:text:)
Creates a secure field with a prompt generated from a Text.
init(_:text:prompt:)
Creates a secure field with a prompt generated from a Text.
init(text: Binding<String>, prompt: Text?, label: () -> Label)
Creates a secure field with a prompt generated from a Text.
Deprecated initializers
init(_:text:onCommit:)
Creates an instance.
Deprecated

**Examples:**

```swift
struct SecureField<Label> where Label : View
```

```swift
struct SecureField<Label> where Label : View
```

```swift
@State private var username: String = ""
@State private var password: String = ""


var body: some View {
    VStack {
        TextField("Username", text: $username)
            .autocorrectionDisabled(true)
            #if !os(macOS)
            .textInputAutocapitalization(.never)
            #endif


        SecureField("Password", text: $password)
            .onSubmit {
                handleLogin(username: username, password: password)
            }
    }
    .textFieldStyle(.roundedBorder)
}
```

```swift
@State private var username: String = ""
@State private var password: String = ""


var body: some View {
    VStack {
        TextField("Username", text: $username)
            .autocorrectionDisabled(true)
            #if !os(macOS)
            .textInputAutocapitalization(.never)
            #endif


        SecureField("Password", text: $password)
            .onSubmit {
                handleLogin(username: username, password: password)
            }
    }
    .textFieldStyle(.roundedBorder)
}
```

```swift
Form {
    TextField(text: $username, prompt: Text("Required")) {
        Text("Username")
    }
    .autocorrectionDisabled(true)
    #if !os(macOS)
    .textInputAutocapitalization(.never)
    #endif


    SecureField(text: $password, prompt: Text("Required")) {
        Text("Password")
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/securefield)

---

## Toggle

SwiftUI
Toggle
Structure
Toggle
A control that toggles between on and off states.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
struct Toggle<Label> where Label : View
Mentioned in
Building and customizing the menu bar with SwiftUI
Declaring a custom view
Laying out a simple view
Populating SwiftUI menus with adaptive controls
Overview

You create a toggle by providing an isOn binding and a label. Bind isOn to a Boolean property that determines whether the toggle is on or off. Set the label to a view that visually describes the purpose of switching between toggle states. For example:

@State private var vibrateOnRing = false


var body: some View {
    Toggle(isOn: $vibrateOnRing) {
        Text("Vibrate on Ring")
    }
}


For the common case of Label based labels, you can use the convenience initializer that takes a title string (or localized string key) and the name of a system image:

@State private var vibrateOnRing = true


var body: some View {
    Toggle(
        "Vibrate on Ring",
        systemImage: "dot.radiowaves.left.and.right",
        isOn: $vibrateOnRing
    )
}


For text-only labels, you can use the convenience initializer that takes a title string (or localized string key) as its first parameter, instead of a trailing closure:

@State private var vibrateOnRing = true


var body: some View {
    Toggle("Vibrate on Ring", isOn: $vibrateOnRing)
}


For cases where adding a subtitle to the label is desired, use a view builder that creates multiple Text views where the first text represents the title and the second text represents the subtitle:

@State private var vibrateOnRing = false


var body: some View {
    Toggle(isOn: $vibrateOnRing) {
        Text("Vibrate on Ring")
        Text("Enable vibration when the phone rings")
    }
}


Note

This behavior does not apply to button.

Styling toggles

Toggles use a default style that varies based on both the platform and the context. For more information, read about the automatic toggle style.

You can customize the appearance and interaction of toggles by applying styles using the toggleStyle(_:) modifier. You can apply built-in styles, like switch, to either a toggle, or to a view hierarchy that contains toggles:

VStack {
    Toggle("Vibrate on Ring", isOn: $vibrateOnRing)
    Toggle("Vibrate on Silent", isOn: $vibrateOnSilent)
}
.toggleStyle(.switch)


You can also define custom styles by creating a type that conforms to the ToggleStyle protocol.

Topics
Creating a toggle
init(_:isOn:)
Creates a toggle that generates its label from a localized string key.
init(isOn: Binding<Bool>, label: () -> Label)
Creates a toggle that displays a custom label.
init(_:image:isOn:)
Creates a toggle that generates its label from a localized string key and image resource.
init(_:systemImage:isOn:)
Creates a toggle that generates its label from a localized string key and system image.
Creating a toggle for a collection
init(_:sources:isOn:)

**Examples:**

```swift
struct Toggle<Label> where Label : View
```

```swift
struct Toggle<Label> where Label : View
```

```swift
@State private var vibrateOnRing = false


var body: some View {
    Toggle(isOn: $vibrateOnRing) {
        Text("Vibrate on Ring")
    }
}
```

```swift
@State private var vibrateOnRing = false


var body: some View {
    Toggle(isOn: $vibrateOnRing) {
        Text("Vibrate on Ring")
    }
}
```

```swift
@State private var vibrateOnRing = true


var body: some View {
    Toggle(
        "Vibrate on Ring",
        systemImage: "dot.radiowaves.left.and.right",
        isOn: $vibrateOnRing
    )
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/toggle)

---

## Slider

SwiftUI
Slider
Structure
Slider
A control for selecting a value from a bounded linear range of values.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
visionOS 1.0+
watchOS 6.0+
struct Slider<Label, ValueLabel> where Label : View, ValueLabel : View
Mentioned in
Populating SwiftUI menus with adaptive controls
Overview

A slider consists of a “thumb” image that the user moves between two extremes of a linear “track”. The ends of the track represent the minimum and maximum possible values. As the user moves the thumb, the slider updates its bound value.

The following example shows a slider bound to the value speed. As the slider updates this value, a bound Text view shows the value updating. The onEditingChanged closure passed to the slider receives callbacks when the user drags the slider. The example uses this to change the color of the value text.

@State private var speed = 50.0
@State private var isEditing = false


var body: some View {
    VStack {
        Slider(
            value: $speed,
            in: 0...100,
            onEditingChanged: { editing in
                isEditing = editing
            }
        )
        Text("\(speed)")
            .foregroundColor(isEditing ? .red : .blue)
    }
}


You can also use a step parameter to provide incremental steps along the path of the slider. For example, if you have a slider with a range of 0 to 100, and you set the step value to 5, the slider’s increments would be 0, 5, 10, and so on. The following example shows this approach, and also adds optional minimum and maximum value labels.

@State private var speed = 50.0
@State private var isEditing = false


var body: some View {
    Slider(
        value: $speed,
        in: 0...100,
        step: 5
    ) {
        Text("Speed")
    } minimumValueLabel: {
        Text("0")
    } maximumValueLabel: {
        Text("100")
    } onEditingChanged: { editing in
        isEditing = editing
    }
    Text("\(speed)")
        .foregroundColor(isEditing ? .red : .blue)
}


The slider also uses the step to increase or decrease the value when a VoiceOver user adjusts the slider with voice commands.

Topics
Creating a slider
init<V>(value: Binding<V>, in: ClosedRange<V>, onEditingChanged: (Bool) -> Void)
Creates a slider to select a value from a given range.
init<V>(value: Binding<V>, in: ClosedRange<V>, step: V.Stride, onEditingChanged: (Bool) -> Void)
Creates a slider to select a value from a given range, subject to a step increment.
Creating a slider with labels
init<V>(value: Binding<V>, in: ClosedRange<V>, label: () -> Label, onEditingChanged: (Bool) -> Void)
Creates a slider to select a value from a given range, which displays the provided label.
init<V>(value: Binding<V>, in: ClosedRange<V>, step: V.Stride, label: () -> Label, onEditingChanged: (Bool) -> Void)
Creates a slider to select a value from a given range, subject to a step increment, which displays the provided label.
init<V>(value: Binding<V>, in: ClosedRange<V>, label: () -> Label, minimumValueLabel: () -> ValueLabel, maximumValueLabel: () -> ValueLabel, onEditingChanged: (Bool) -> Void)
Creates a slider to select a value from a given range, which displays the provided labels.
init<V>(value: Binding<V>, in: ClosedRange<V>, step: V.Stride, label: () -> Label, minimumValueLabel: () -> ValueLabel, maximumValueLabel: () -> ValueLabel, onEditingChanged: (Bool) -> Void)
Creates a slider to select a value from a given range, subject to a step increment, which displays the provided labels.
Adding ticks to a slider
struct SliderTick
A representation of a tick in a slider, with associated value and optional label.
struct SliderTickBuilder
A result builder that constructs SliderTicks for use when creating a Slider.
struct SliderTickContentForEach
A type of slider content that creates content by iterating over a collection.
struct TupleSliderTickContent
Slider content created from a Swift tuple of slider content.
protocol SliderTickContent
A type that provides content for a SliderTickBuilder.
Deprecated initializers
init<V>(value: Binding<V>, in: ClosedRange<V>, onEditingChanged: (Bool) -> Void, label: () -> Label)
Creates a slider to select a value from a given range, which displays the provided label.
Deprecated
init<V>(value: Binding<V>, in: ClosedRange<V>, step: V.Stride, onEditingChanged: (Bool) -> Void, label: () -> Label)
Creates a slider to select a value from a given range, subject to a step increment, which displays the provided label.
Deprecated
init<V>(value: Binding<V>, in: ClosedRange<V>, onEditingChanged: (Bool) -> Void, minimumValueLabel: ValueLabel, maximumValueLabel: ValueLabel, label: () -> Label)

**Examples:**

```swift
struct Slider<Label, ValueLabel> where Label : View, ValueLabel : View
```

```swift
struct Slider<Label, ValueLabel> where Label : View, ValueLabel : View
```

```swift
@State private var speed = 50.0
@State private var isEditing = false


var body: some View {
    VStack {
        Slider(
            value: $speed,
            in: 0...100,
            onEditingChanged: { editing in
                isEditing = editing
            }
        )
        Text("\(speed)")
            .foregroundColor(isEditing ? .red : .blue)
    }
}
```

```swift
@State private var speed = 50.0
@State private var isEditing = false


var body: some View {
    VStack {
        Slider(
            value: $speed,
            in: 0...100,
            onEditingChanged: { editing in
                isEditing = editing
            }
        )
        Text("\(speed)")
            .foregroundColor(isEditing ? .red : .blue)
    }
}
```

```swift
@State private var speed = 50.0
@State private var isEditing = false


var body: some View {
    Slider(
        value: $speed,
        in: 0...100,
        step: 5
    ) {
        Text("Speed")
    } minimumValueLabel: {
        Text("0")
    } maximumValueLabel: {
        Text("100")
    } onEditingChanged: { editing in
        isEditing = editing
    }
    Text("\(speed)")
        .foregroundColor(isEditing ? .red : .blue)
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/slider)

---

## Stepper

SwiftUI
Stepper
Structure
Stepper
A control that performs increment and decrement actions.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
visionOS 1.0+
watchOS 9.0+
struct Stepper<Label> where Label : View
Overview

Use a stepper control when you want the user to have granular control while incrementing or decrementing a value. For example, you can use a stepper to:

Change a value up or down by 1.

Operate strictly over a prescribed range.

Step by specific amounts over a stepper’s range of possible values.

The example below uses an array that holds a number of Color values, a local state variable, value, to set the control’s background color, and title label. When the user clicks or taps the stepper’s increment or decrement buttons, SwiftUI executes the relevant closure that updates value, wrapping the value to prevent overflow. SwiftUI then re-renders the view, updating the text and background color to match the current index:

struct StepperView: View {
    @State private var value = 0
    let colors: [Color] = [.orange, .red, .gray, .blue,
                           .green, .purple, .pink]


    func incrementStep() {
        value += 1
        if value >= colors.count { value = 0 }
    }


    func decrementStep() {
        value -= 1
        if value < 0 { value = colors.count - 1 }
    }


    var body: some View {
        Stepper {
            Text("Value: \(value) Color: \(colors[value].description)")
        } onIncrement: {
            incrementStep()
        } onDecrement: {
            decrementStep()
        }
        .padding(5)
        .background(colors[value])
    }
}


The following example shows a stepper that displays the effect of incrementing or decrementing a value with the step size of step with the bounds defined by range:

struct StepperView: View {
    @State private var value = 0
    let step = 5
    let range = 1...50


    var body: some View {
        Stepper(
            value: $value,
            in: range,
            step: step
        ) {
            Text("Current: \(value) in \(range.description) " +
                 "stepping by \(step)")
        }
        .padding(10)
    }
}


Topics
Creating a stepper
init<V>(value: Binding<V>, step: V.Stride, label: () -> Label, onEditingChanged: (Bool) -> Void)
Creates a stepper configured to increment or decrement a binding to a value using a step value you provide.
init<F>(value: Binding<F.FormatInput>, step: F.FormatInput.Stride, format: F, label: () -> Label, onEditingChanged: (Bool) -> Void)
Creates a stepper configured to increment or decrement a binding to a value using a step value you provide, displaying its value with an applied format style.
init(_:value:step:onEditingChanged:)
Creates a stepper with a title and configured to increment and decrement a binding to a value and step amount you provide.
init(_:value:step:format:onEditingChanged:)
Creates a stepper with a title key and configured to increment and decrement a binding to a value and step amount you provide, displaying its value with an applied format style.
Creating a stepper over a range
init<V>(value: Binding<V>, in: ClosedRange<V>, step: V.Stride, label: () -> Label, onEditingChanged: (Bool) -> Void)
Creates a stepper configured to increment or decrement a binding to a value using a step value and within a range of values you provide.
init<F>(value: Binding<F.FormatInput>, in: ClosedRange<F.FormatInput>, step: F.FormatInput.Stride, format: F, label: () -> Label, onEditingChanged: (Bool) -> Void)
Creates a stepper configured to increment or decrement a binding to a value using a step value and within a range of values you provide, displaying its value with an applied format style.
init(_:value:in:step:onEditingChanged:)
Creates a stepper instance that increments and decrements a binding to a value, by a step size and within a closed range that you provide.
init(_:value:in:step:format:onEditingChanged:)
Creates a stepper instance that increments and decrements a binding to a value, by a step size and within a closed range that you provide, displaying its value with an applied format style.
Creating a stepper with change behavior
init(label: () -> Label, onIncrement: (() -> Void)?, onDecrement: (() -> Void)?, onEditingChanged: (Bool) -> Void)
Creates a stepper instance that performs the closures you provide when the user increments or decrements the stepper.

**Examples:**

```swift
struct Stepper<Label> where Label : View
```

```swift
struct Stepper<Label> where Label : View
```

```swift
struct StepperView: View {
    @State private var value = 0
    let colors: [Color] = [.orange, .red, .gray, .blue,
                           .green, .purple, .pink]


    func incrementStep() {
        value += 1
        if value >= colors.count { value = 0 }
    }


    func decrementStep() {
        value -= 1
        if value < 0 { value = colors.count - 1 }
    }


    var body: some View {
        Stepper {
            Text("Value: \(value) Color: \(colors[value].description)")
        } onIncrement: {
            incrementStep()
        } onDecrement: {
            decrementStep()
        }
        .padding(5)
        .background(colors[value])
    }
}
```

```swift
struct StepperView: View {
    @State private var value = 0
    let colors: [Color] = [.orange, .red, .gray, .blue,
                           .green, .purple, .pink]


    func incrementStep() {
        value += 1
        if value >= colors.count { value = 0 }
    }


    func decrementStep() {
        value -= 1
        if value < 0 { value = colors.count - 1 }
    }


    var body: some View {
        Stepper {
            Text("Value: \(value) Color: \(colors[value].description)")
        } onIncrement: {
            incrementStep()
        } onDecrement: {
            decrementStep()
        }
        .padding(5)
        .background(colors[value])
    }
}
```

```swift
struct StepperView: View {
    @State private var value = 0
    let step = 5
    let range = 1...50


    var body: some View {
        Stepper(
            value: $value,
            in: range,
            step: step
        ) {
            Text("Current: \(value) in \(range.description) " +
                 "stepping by \(step)")
        }
        .padding(10)
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/stepper)

---

## Picker

SwiftUI
Picker
Structure
Picker
A control for selecting from a set of mutually exclusive values.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
struct Picker<Label, SelectionValue, Content> where Label : View, SelectionValue : Hashable, Content : View
Mentioned in
Picking container views for your content
Performing a search operation
Populating SwiftUI menus with adaptive controls
Scoping a search operation
Overview

You create a picker by providing a selection binding, a label, and the content for the picker to display. Set the selection parameter to a bound property that provides the value to display as the current selection. Set the label to a view that visually describes the purpose of selecting content in the picker, and then provide the content for the picker to display.

For example, consider an enumeration of ice cream flavors and a State variable to hold the selected flavor:

enum Flavor: String, CaseIterable, Identifiable {
    case chocolate, vanilla, strawberry
    var id: Self { self }
}


@State private var selectedFlavor: Flavor = .chocolate


You can create a picker to select among the values by providing a label, a binding to the current selection, and a collection of views for the picker’s content. Append a tag to each of these content views using the View/tag(_:) view modifier so that the type of each selection matches the type of the bound state variable:

List {
    Picker("Flavor", selection: $selectedFlavor) {
        Text("Chocolate").tag(Flavor.chocolate)
        Text("Vanilla").tag(Flavor.vanilla)
        Text("Strawberry").tag(Flavor.strawberry)
    }
}


If you provide a string label for the picker, as the example above does, the picker uses it to initialize a Text view as a label. Alternatively, you can use the init(selection:content:label:) initializer to compose the label from other views. The exact appearance of the picker depends on the context. If you use a picker in a List in iOS, it appears in a row with the label and selected value, and a chevron to indicate that you can tap the row to select a new value:

For cases where adding a subtitle to the label is desired, use a view builder that creates multiple Text views where the first text represents the title and the second text represents the subtitle:

List {
    Picker(selection: $selectedFlavor) {
        Text("Chocolate").tag(Flavor.chocolate)
        Text("Vanilla").tag(Flavor.vanilla)
        Text("Strawberry").tag(Flavor.strawberry)
    } label: {
        Text("Flavor")
        Text("Choose your favorite flavor")
    }
}

Iterating over a picker’s options

To provide selection values for the Picker without explicitly listing each option, you can create the picker with a ForEach:

Picker("Flavor", selection: $selectedFlavor) {
    ForEach(Flavor.allCases) { flavor in
        Text(flavor.rawValue.capitalized)
    }
}


ForEach automatically assigns a tag to the selection views using each option’s id. This is possible because Flavor conforms to the Identifiable protocol.

The example above relies on the fact that Flavor defines the type of its id parameter to exactly match the selection type. If that’s not the case, you need to override the tag. For example, consider a Topping type and a suggested topping for each flavor:

enum Topping: String, CaseIterable, Identifiable {
    case nuts, cookies, blueberries
    var id: Self { self }
}


extension Flavor {
    var suggestedTopping: Topping {
        switch self {
        case .chocolate: return .nuts
        case .vanilla: return .cookies
        case .strawberry: return .blueberries
        }
    }
}


@State private var suggestedTopping: Topping = .nuts


The following example shows a picker that’s bound to a Topping type, while the options are all Flavor instances. Each option uses the tag modifier to associate the suggested topping with the flavor it displays:

List {
    Picker("Flavor", selection: $suggestedTopping) {
        ForEach(Flavor.allCases) { flavor in
            Text(flavor.rawValue.capitalized)

**Examples:**

```swift
struct Picker<Label, SelectionValue, Content> where Label : View, SelectionValue : Hashable, Content : View
```

```swift
struct Picker<Label, SelectionValue, Content> where Label : View, SelectionValue : Hashable, Content : View
```

```swift
enum Flavor: String, CaseIterable, Identifiable {
    case chocolate, vanilla, strawberry
    var id: Self { self }
}


@State private var selectedFlavor: Flavor = .chocolate
```

```swift
enum Flavor: String, CaseIterable, Identifiable {
    case chocolate, vanilla, strawberry
    var id: Self { self }
}


@State private var selectedFlavor: Flavor = .chocolate
```

```swift
List {
    Picker("Flavor", selection: $selectedFlavor) {
        Text("Chocolate").tag(Flavor.chocolate)
        Text("Vanilla").tag(Flavor.vanilla)
        Text("Strawberry").tag(Flavor.strawberry)
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/picker)

---

## DatePicker

SwiftUI
DatePicker
Structure
DatePicker
A control for selecting an absolute date.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
visionOS 1.0+
watchOS 10.0+
struct DatePicker<Label> where Label : View
Mentioned in
Laying out a simple view
Overview

Use a DatePicker when you want to provide a view that allows the user to select a calendar date, and optionally a time. The view binds to a Date instance.

The following example creates a basic DatePicker, which appears on iOS as text representing the date. This example limits the display to only the calendar date, not the time. When the user taps or clicks the text, a calendar view animates in, from which the user can select a date. When the user dismisses the calendar view, the view updates the bound Date.

@State private var date = Date()


var body: some View {
    DatePicker(
        "Start Date",
        selection: $date,
        displayedComponents: [.date]
    )
}


For cases where adding a subtitle to the label is desired, use a view builder that creates multiple Text views where the first text represents the title and the second text represents the subtitle:

@State private var date = Date()


var body: some View {
    DatePicker(selection: $date) {
        Text("Start Date")
        Text("Select the starting date for the event")
    }
}


You can limit the DatePicker to specific ranges of dates, allowing selections only before or after a certain date, or between two dates. The following example shows a date-and-time picker that only permits selections within the year 2021 (in the UTC time zone).

@State private var date = Date()
let dateRange: ClosedRange<Date> = {
    let calendar = Calendar.current
    let startComponents = DateComponents(year: 2021, month: 1, day: 1)
    let endComponents = DateComponents(year: 2021, month: 12, day: 31, hour: 23, minute: 59, second: 59)
    return calendar.date(from:startComponents)!
        ...
        calendar.date(from:endComponents)!
}()


var body: some View {
    DatePicker(
        "Start Date",
         selection: $date,
         in: dateRange,
         displayedComponents: [.date, .hourAndMinute]
    )
}


Styling date pickers

To use a different style of date picker, use the datePickerStyle(_:) view modifier. The following example shows the graphical date picker style.

@State private var date = Date()


var body: some View {
    DatePicker(
        "Start Date",
        selection: $date,
        displayedComponents: [.date]
    )
    .datePickerStyle(.graphical)
}


Topics
Creating a date picker for any date
init(_:selection:displayedComponents:)
Creates an instance that selects a Date with an unbounded range.
init(selection: Binding<Date>, displayedComponents: DatePicker<Label>.Components, label: () -> Label)
Creates an instance that selects a Date with an unbounded range.
Creating a date picker for specific dates
init(_:selection:in:displayedComponents:)
Creates an instance that selects a Date in a closed range.
init(selection:in:displayedComponents:label:)
Creates an instance that selects a Date in a closed range.
Setting date picker components
typealias Components
struct DatePickerComponents
Relationships

**Examples:**

```swift
struct DatePicker<Label> where Label : View
```

```swift
struct DatePicker<Label> where Label : View
```

```swift
@State private var date = Date()


var body: some View {
    DatePicker(
        "Start Date",
        selection: $date,
        displayedComponents: [.date]
    )
}
```

```swift
@State private var date = Date()


var body: some View {
    DatePicker(
        "Start Date",
        selection: $date,
        displayedComponents: [.date]
    )
}
```

```swift
@State private var date = Date()


var body: some View {
    DatePicker(selection: $date) {
        Text("Start Date")
        Text("Select the starting date for the event")
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/datepicker)

---

## Gauge

SwiftUI
Gauge
Structure
Gauge
A view that shows a value within a range.
iOS 16.0+
iPadOS 16.0+
Mac Catalyst 16.0+
macOS 13.0+
visionOS 1.0+
watchOS 7.0+
struct Gauge<Label, CurrentValueLabel, BoundsLabel, MarkedValueLabels> where Label : View, CurrentValueLabel : View, BoundsLabel : View, MarkedValueLabels : View
Overview

A gauge is a view that shows a current level of a value in relation to a specified finite capacity, very much like a fuel gauge in an automobile. Gauge displays are configurable; they can show any combination of the gauge’s current value, the range the gauge can display, and a label describing the purpose of the gauge itself.

In its most basic form, a gauge displays a single value along the path of the gauge mapped into a range from 0 to 100 percent. The example below sets the gauge’s indicator to a position 40 percent along the gauge’s path:

struct SimpleGauge: View {
    @State private var batteryLevel = 0.4


    var body: some View {
        Gauge(value: batteryLevel) {
            Text("Battery Level")
        }
    }
}


You can make a gauge more descriptive by describing its purpose, showing its current value and its start and end values. This example shows the gauge variant that accepts a range and adds labels using multiple trailing closures describing the current value and the minimum and maximum values of the gauge:

struct LabeledGauge: View {
    @State private var current = 67.0
    @State private var minValue = 0.0
    @State private var maxValue = 170.0


    var body: some View {
        Gauge(value: current, in: minValue...maxValue) {
            Text("BPM")
        } currentValueLabel: {
            Text("\(Int(current))")
        } minimumValueLabel: {
            Text("\(Int(minValue))")
        } maximumValueLabel: {
            Text("\(Int(maxValue))")
        }
    }
}


As shown above, the default style for gauges is a linear, continuous bar with an indicator showing the current value, and optional labels describing the gauge’s purpose, current, minimum, and maximum values.

Note

Some visual presentations of Gauge don’t display all the labels required by the API. However, the accessibility system does use the label content and you should use these labels to fully describe the gauge for accessibility users.

To change the style of a gauge, use the gaugeStyle(_:) view modifier and supply an initializer for a specific gauge style. For example, to display the same gauge in a circular style, apply the circular style to the view:

struct LabeledGauge: View {
    @State private var current = 67.0
    @State private var minValue = 0.0
    @State private var maxValue = 170.0


    var body: some View {
        Gauge(value: current, in: minValue...maxValue) {
            Text("BPM")
        } currentValueLabel: {
            Text("\(Int(current))")
        } minimumValueLabel: {
            Text("\(Int(minValue))")
        } maximumValueLabel: {
            Text("\(Int(maxValue))")
        }
        .gaugeStyle(.circular)
    }
}


To style elements of a gauge’s presentation, you apply view modifiers to the elements that you want to change. In the example below, the current value, minimum and maximum value labels have custom colors:

struct StyledGauge: View {
    @State private var current = 67.0
    @State private var minValue = 50.0
    @State private var maxValue = 170.0


    var body: some View {
        Gauge(value: current, in: minValue...maxValue) {
            Image(systemName: "heart.fill")
                .foregroundColor(.red)
        } currentValueLabel: {
            Text("\(Int(current))")
                .foregroundColor(Color.green)
        } minimumValueLabel: {
            Text("\(Int(minValue))")
                .foregroundColor(Color.green)
        } maximumValueLabel: {

**Examples:**

```swift
struct Gauge<Label, CurrentValueLabel, BoundsLabel, MarkedValueLabels> where Label : View, CurrentValueLabel : View, BoundsLabel : View, MarkedValueLabels : View
```

```swift
struct Gauge<Label, CurrentValueLabel, BoundsLabel, MarkedValueLabels> where Label : View, CurrentValueLabel : View, BoundsLabel : View, MarkedValueLabels : View
```

```swift
struct SimpleGauge: View {
    @State private var batteryLevel = 0.4


    var body: some View {
        Gauge(value: batteryLevel) {
            Text("Battery Level")
        }
    }
}
```

```swift
struct SimpleGauge: View {
    @State private var batteryLevel = 0.4


    var body: some View {
        Gauge(value: batteryLevel) {
            Text("Battery Level")
        }
    }
}
```

```swift
struct LabeledGauge: View {
    @State private var current = 67.0
    @State private var minValue = 0.0
    @State private var maxValue = 170.0


    var body: some View {
        Gauge(value: current, in: minValue...maxValue) {
            Text("BPM")
        } currentValueLabel: {
            Text("\(Int(current))")
        } minimumValueLabel: {
            Text("\(Int(minValue))")
        } maximumValueLabel: {
            Text("\(Int(maxValue))")
        }
    }
}
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/gauge)

---

