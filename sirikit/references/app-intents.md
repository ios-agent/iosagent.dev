# App Intents Migration Reference

## Table of Contents
1. [Overview](#overview)
2. [Key Differences](#key-differences)
3. [Migration Steps](#migration-steps)
4. [App Intent Structure](#app-intent-structure)
5. [App Entities](#app-entities)
6. [App Shortcuts](#app-shortcuts)
7. [Coexistence Strategy](#coexistence-strategy)

---

## Overview

App Intents (iOS 16+) is the modern replacement for SiriKit custom intents.

### Benefits
- Swift-native, no code generation
- No separate extension required
- Better Shortcuts integration
- Focus Filters support
- Simpler architecture

### When to Migrate
- New apps: Use App Intents directly
- Existing apps: Migrate incrementally
- System intents: Still use SiriKit (messaging, calling, etc.)

---

## Key Differences

| Feature | SiriKit (Custom Intents) | App Intents |
|---------|--------------------------|-------------|
| Definition | `.intentdefinition` file | Swift code |
| Code generation | Xcode generates classes | Write directly |
| Extension | Requires Intents extension | Runs in app process |
| Async pattern | Completion handlers | async/await native |
| Entity queries | Manual implementation | `EntityQuery` protocol |
| Shortcuts | Manual donation | `AppShortcutsProvider` |

---

## Migration Steps

### 1. Create App Intent

**Before (SiriKit)**:
```swift
// Generated from .intentdefinition
@objc(OrderSoupIntent)
public class OrderSoupIntent: INIntent {
    @NSManaged public var soup: Soup?
    @NSManaged public var quantity: NSNumber?
}
```

**After (App Intents)**:
```swift
import AppIntents

struct OrderSoupIntent: AppIntent {
    static var title: LocalizedStringResource = "Order Soup"
    static var description = IntentDescription("Order your favorite soup")
    
    @Parameter(title: "Soup")
    var soup: SoupEntity
    
    @Parameter(title: "Quantity", default: 1)
    var quantity: Int
    
    func perform() async throws -> some IntentResult {
        let order = try await OrderService.shared.place(soup: soup, quantity: quantity)
        return .result(dialog: "Your \(soup.name) is ordered!")
    }
}
```

### 2. Create App Entity

**Before (SiriKit)**:
```swift
// Generated INObject subclass
@objc(Soup)
public class Soup: INObject {
    @NSManaged public var identifier: String?
    @NSManaged public var displayString: String?
}
```

**After (App Intents)**:
```swift
import AppIntents

struct SoupEntity: AppEntity {
    static var typeDisplayRepresentation = TypeDisplayRepresentation(name: "Soup")
    static var defaultQuery = SoupQuery()
    
    var id: String
    var name: String
    var price: Decimal
    
    var displayRepresentation: DisplayRepresentation {
        DisplayRepresentation(title: "\(name)", subtitle: "$\(price)")
    }
}
```

### 3. Create Entity Query

```swift
struct SoupQuery: EntityQuery {
    func entities(for identifiers: [String]) async throws -> [SoupEntity] {
        return MenuService.shared.soups.filter { identifiers.contains($0.id) }
    }
    
    func suggestedEntities() async throws -> [SoupEntity] {
        return Array(MenuService.shared.soups.prefix(5))
    }
}
```

### 4. Provide App Shortcuts

```swift
struct SoupShortcuts: AppShortcutsProvider {
    static var appShortcuts: [AppShortcut] {
        AppShortcut(
            intent: OrderSoupIntent(),
            phrases: [
                "Order soup from \(.applicationName)",
                "Get me soup from \(.applicationName)"
            ],
            shortTitle: "Order Soup",
            systemImageName: "cup.and.saucer"
        )
    }
}
```

---

## App Intent Structure

### Basic Intent

```swift
struct MyIntent: AppIntent {
    // Required: Title for Shortcuts
    static var title: LocalizedStringResource = "My Action"
    
    // Optional: Description
    static var description = IntentDescription("Does something useful")
    
    // Optional: Open app when run
    static var openAppWhenRun: Bool = false
    
    // Parameters
    @Parameter(title: "Input")
    var input: String
    
    // Perform action
    func perform() async throws -> some IntentResult {
        // Do work
        return .result()
    }
}
```

### Intent with Dialog Result

```swift
func perform() async throws -> some IntentResult & ProvidesDialog {
    return .result(dialog: "Action completed!")
}
```

### Intent with Return Value

```swift
func perform() async throws -> some IntentResult & ReturnsValue<String> {
    let result = await doWork()
    return .result(value: result)
}
```

### Intent that Opens App

```swift
struct OpenFeatureIntent: AppIntent {
    static var title: LocalizedStringResource = "Open Feature"
    static var openAppWhenRun: Bool = true
    
    func perform() async throws -> some IntentResult {
        // App will open, configure state
        NavigationState.shared.destination = .feature
        return .result()
    }
}
```

---

## App Entities

### Full Entity Example

```swift
struct SoupEntity: AppEntity, Identifiable {
    // Required
    static var typeDisplayRepresentation = TypeDisplayRepresentation(
        name: "Soup",
        numericFormat: "\(placeholder: .int) soups"
    )
    
    static var defaultQuery = SoupQuery()
    
    // Properties
    var id: String
    var name: String
    var price: Decimal
    var isAvailable: Bool
    
    // Display
    var displayRepresentation: DisplayRepresentation {
        DisplayRepresentation(
            title: "\(name)",
            subtitle: isAvailable ? "$\(price)" : "Sold Out",
            image: .init(systemName: isAvailable ? "cup.and.saucer.fill" : "cup.and.saucer")
        )
    }
}
```

### Entity Query with Search

```swift
struct SoupQuery: EntityStringQuery {
    func entities(for identifiers: [String]) async throws -> [SoupEntity] {
        MenuService.shared.soups.filter { identifiers.contains($0.id) }
    }
    
    func entities(matching string: String) async throws -> [SoupEntity] {
        MenuService.shared.soups.filter { 
            $0.name.localizedCaseInsensitiveContains(string)
        }
    }
    
    func suggestedEntities() async throws -> [SoupEntity] {
        MenuService.shared.featuredSoups
    }
}
```

---

## App Shortcuts

### Shortcuts Provider

```swift
struct MyAppShortcuts: AppShortcutsProvider {
    static var appShortcuts: [AppShortcut] {
        AppShortcut(
            intent: OrderSoupIntent(),
            phrases: [
                "Order \(\.$soup) from \(.applicationName)",
                "Get soup from \(.applicationName)"
            ],
            shortTitle: "Order Soup",
            systemImageName: "cup.and.saucer"
        )
        
        AppShortcut(
            intent: CheckOrderIntent(),
            phrases: ["Check my order in \(.applicationName)"],
            shortTitle: "Check Order",
            systemImageName: "list.bullet"
        )
    }
}
```

### Phrase Variables

```swift
// Reference parameters in phrases
"Order \(\.$soup) from \(.applicationName)"

// Application name placeholder
\(.applicationName)

// Parameter placeholders
\(\.$parameterName)
```

---

## Coexistence Strategy

### Support Both During Migration

```swift
// Old SiriKit handler still works
class IntentHandler: INExtension {
    override func handler(for intent: INIntent) -> Any {
        if intent is OrderSoupIntent {
            return OrderSoupHandler()
        }
        return self
    }
}

// New App Intent also available
struct OrderSoupAppIntent: AppIntent {
    // Modern implementation
}
```

### Migrate Donations

```swift
// Old: SiriKit donation
let interaction = INInteraction(intent: oldIntent, response: nil)
interaction.donate { _ in }

// New: App Intents (automatic via AppShortcutsProvider)
// Or manual:
try await OrderSoupIntent().donate()
```

### Update Info.plist

When fully migrated, remove SiriKit intent declarations:

```xml
<!-- Remove when migrated -->
<key>IntentsSupported</key>
<array>
    <string>OrderSoupIntent</string>
</array>
```

---

## Best Practices

1. **Migrate incrementally**: One intent at a time
2. **Test thoroughly**: Voice, Shortcuts app, Spotlight
3. **Keep SiriKit for system intents**: Messaging, calling still require it
4. **Use descriptive titles**: They appear in Shortcuts
5. **Provide suggested entities**: Better user experience
6. **Localize everything**: `LocalizedStringResource` for all text
