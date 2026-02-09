# Data Flow

SwiftUI data flow documentation.

---

## PreferenceKey

SwiftUI
PreferenceKey
Protocol
PreferenceKey
A named value produced by a view.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
protocol PreferenceKey
Overview

A view with multiple children automatically combines its values for a given preference into a single value visible to its ancestors.

Topics
Getting the default value
static var defaultValue: Self.Value
The default value of the preference.

Required Default implementation provided.

associatedtype Value
The type of value produced by this preference.

Required

Combining preferences
static func reduce(value: inout Self.Value, nextValue: () -> Self.Value)
Combines a sequence of values by modifying the previously-accumulated value with the result of a closure that provides the next value.

Required

Relationships
Conforming Types
PreferredColorSchemeKey
Text.LayoutKey

**Examples:**

```swift
protocol PreferenceKey
```

```swift
protocol PreferenceKey
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/preferencekey)

---

## FocusedSceneValue (Failed)

Error: Page.goto: Timeout 30000ms exceeded.
Call log:
  - navigating to "https://developer.apple.com/documentation/swiftui/focusedscenevalue", waiting until "networkidle"


[View Official Documentation](https://developer.apple.com/documentation/swiftui/focusedscenevalue)

---

