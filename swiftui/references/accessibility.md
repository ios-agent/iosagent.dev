# Accessibility

SwiftUI accessibility documentation.

---

## AccessibilityTraits

SwiftUI
AccessibilityTraits
Structure
AccessibilityTraits
A set of accessibility traits that describe how an element behaves.
iOS 13.0+
iPadOS 13.0+
Mac Catalyst 13.0+
macOS 10.15+
tvOS 13.0+
visionOS 1.0+
watchOS 6.0+
struct AccessibilityTraits
Topics
Getting traits
static let allowsDirectInteraction: AccessibilityTraits
The accessibility element allows direct touch interaction for VoiceOver users.
static let causesPageTurn: AccessibilityTraits
The accessibility element causes an automatic page turn when VoiceOver finishes reading the text within it.
static let isButton: AccessibilityTraits
The accessibility element is a button.
static let isHeader: AccessibilityTraits
The accessibility element is a header that divides content into sections, like the title of a navigation bar.
static let isImage: AccessibilityTraits
The accessibility element is an image.
static let isKeyboardKey: AccessibilityTraits
The accessibility element behaves as a keyboard key.
static let isLink: AccessibilityTraits
The accessibility element is a link.
static let isModal: AccessibilityTraits
The accessibility element is modal.
static let isSearchField: AccessibilityTraits
The accessibility element is a search field.
static let isSelected: AccessibilityTraits
The accessibility element is currently selected.
static let isStaticText: AccessibilityTraits
The accessibility element is a static text that cannot be modified by the user.
static let isSummaryElement: AccessibilityTraits
The accessibility element provides summary information when the application starts.
static let isToggle: AccessibilityTraits
The accessibility element is a toggle.
static let playsSound: AccessibilityTraits
The accessibility element plays its own sound when activated.
static let startsMediaSession: AccessibilityTraits
The accessibility element starts a media session when it is activated.
static let updatesFrequently: AccessibilityTraits
The accessibility element frequently updates its label or value.
Type Properties
static let isTabBar: AccessibilityTraits
The accessibility element is a tab bar.
Relationships
Conforms To
Equatable
ExpressibleByArrayLiteral
Sendable
SendableMetatype
SetAlgebra
See Also
Assigning traits to content
func accessibilityAddTraits(AccessibilityTraits) -> ModifiedContent<Self, AccessibilityAttachmentModifier>
Adds the given traits to the view.
func accessibilityRemoveTraits(AccessibilityTraits) -> ModifiedContent<Self, AccessibilityAttachmentModifier>
Removes the given traits from this view.

**Examples:**

```swift
struct AccessibilityTraits
```

```swift
struct AccessibilityTraits
```

[View Official Documentation](https://developer.apple.com/documentation/swiftui/accessibilitytraits)

---

