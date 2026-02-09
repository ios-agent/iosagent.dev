# Custom Intents Reference

## Table of Contents
1. [Intent Definition File](#intent-definition-file)
2. [Defining Intents](#defining-intents)
3. [Parameters](#parameters)
4. [Custom Types](#custom-types)
5. [Responses](#responses)
6. [Code Generation](#code-generation)

---

## Intent Definition File

### Create Definition File
1. File → New → File → SiriKit Intent Definition File
2. Name: `Intents.intentdefinition`
3. Add to both app and extension targets

### File Structure
```
Intents.intentdefinition
├── Intents
│   ├── OrderSoupIntent
│   └── CheckOrderStatusIntent
├── Types
│   ├── Soup (Custom Enum)
│   └── OrderDetails (Custom Type)
└── Enumerations
    └── OrderType
```

---

## Defining Intents

### Intent Properties

| Property | Description |
|----------|-------------|
| **Name** | VerbNoun format (e.g., `OrderSoup`) |
| **Category** | Determines default Siri dialog |
| **Title** | Human-readable display name |
| **Description** | What the intent does |
| **Confirmation** | Require user confirmation before handling |

### Categories

| Category | Best For |
|----------|----------|
| `Order` | Purchasing, ordering items |
| `Do` | Generic actions |
| `Search` | Finding information |
| `Send` | Sending messages, files |
| `Create` | Creating new items |
| `Open` | Opening app features |

### Configurable Intent

Enable "Intent is user-configurable" to allow:
- Editing in Shortcuts app
- Interactive Siri dialogs
- Multi-step shortcut inclusion

---

## Parameters

### Parameter Configuration

| Setting | Description |
|---------|-------------|
| **Display Name** | Shown in Siri/Shortcuts |
| **Type** | Data type (system or custom) |
| **User-facing** | Can user see/edit this parameter |
| **Prompt** | What Siri says when asking for value |
| **Default Value** | Pre-filled value |
| **Supports multiple values** | Array of values |

### System Parameter Types

```
String          Integer         Double          Boolean
URL             Person          Placemark       DateComponents
CurrencyAmount  File            Location        PaymentMethod
```

### Parameter Relationships

Set parent-child relationships:

```
orderType (parent)
├── pickup → storeLocation (shown if pickup)
└── delivery → deliveryAddress (shown if delivery)
```

Configuration:
1. Select child parameter
2. Expand "Relationship" section
3. Set Parent Parameter
4. Set "Show If Parent" condition

### Input Options

| Option | Description |
|--------|-------------|
| **Siri can ask for value** | Enable voice input |
| **Users can edit value** | Allow editing in Shortcuts |
| **Users can provide value** | Accept as shortcut input |
| **Options are provided dynamically** | Call code for options |

---

## Custom Types

### Custom Enum

```
// In Intent Definition
Enum: SoupSize
├── small (Display: "Small")
├── medium (Display: "Medium")  
└── large (Display: "Large")
```

Generated code:
```swift
@objc public enum SoupSize: Int {
    case unknown = 0
    case small = 1
    case medium = 2
    case large = 3
}
```

### Custom Object Type

```
// In Intent Definition
Type: Soup
├── identifier: String (required)
├── displayString: String
├── subtitleString: String?
├── image: INImage?
```

Generated code:
```swift
@objc(Soup)
public class Soup: INObject {
    @NSManaged public var identifier: String?
    @NSManaged public var displayString: String?
    // ...
}
```

### Dynamic Options Provider

```swift
// Provide options at runtime
class SoupOptionsProvider: NSObject, SoupOptionsProviding {
    func provideSoupOptions(for intent: OrderSoupIntent,
                           with completion: @escaping ([Soup]?, Error?) -> Void) {
        let soups = MenuService.shared.availableSoups.map { item in
            Soup(identifier: item.id, display: item.name)
        }
        completion(soups, nil)
    }
}
```

---

## Responses

### Response Template

Define in Intent Definition:

```
Code: success
├── Dialog: "Your ${soup} is ordered!"
├── Voice-only Dialog: "I've ordered your ${soup}."
└── Properties:
    ├── orderNumber: String
    └── estimatedTime: DateComponents
```

### Response Codes

| Code | Purpose |
|------|---------|
| `success` | Action completed successfully |
| `failure` | Generic failure |
| `ready` | Confirmation passed, ready to handle |
| `inProgress` | Already processing |
| `continueInApp` | Launch app to complete |
| Custom codes | Define specific failure reasons |

### Response Properties

Add properties for:
- Siri dialog parameters (`${propertyName}`)
- Shortcut output values
- Data to pass to app

### Generated Response Class

```swift
@objc(OrderSoupIntentResponse)
public class OrderSoupIntentResponse: INIntentResponse {
    @NSManaged public var orderNumber: String?
    @NSManaged public var estimatedTime: DateComponents?
    
    public static func success(orderNumber: String) -> OrderSoupIntentResponse {
        let response = OrderSoupIntentResponse(code: .success, userActivity: nil)
        response.orderNumber = orderNumber
        return response
    }
}
```

---

## Code Generation

### Target Membership

| Target | Intent Classes Setting |
|--------|------------------------|
| Shared Framework | Intent Classes |
| Main App | No Generated Classes |
| Intents Extension | No Generated Classes |

This avoids duplicate symbol errors.

### Generated Files

For `OrderSoupIntent`:

```swift
// OrderSoupIntent.swift
@objc(OrderSoupIntent)
public class OrderSoupIntent: INIntent {
    @NSManaged public var soup: Soup?
    @NSManaged public var quantity: NSNumber?
}

// OrderSoupIntentHandling.swift
@objc(OrderSoupIntentHandling)
public protocol OrderSoupIntentHandling {
    func resolveSoup(for intent: OrderSoupIntent) async -> SoupResolutionResult
    func confirm(intent: OrderSoupIntent) async -> OrderSoupIntentResponse
    func handle(intent: OrderSoupIntent) async -> OrderSoupIntentResponse
}

// OrderSoupIntentResponse.swift
@objc(OrderSoupIntentResponse)
public class OrderSoupIntentResponse: INIntentResponse { }
```

### Accessing Generated Code

```swift
import Intents

// Use generated classes
let intent = OrderSoupIntent()
intent.soup = Soup(identifier: "tomato", display: "Tomato Soup")
intent.quantity = 2
```
