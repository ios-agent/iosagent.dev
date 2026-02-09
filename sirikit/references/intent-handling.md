# Intent Handling Reference

## Table of Contents
1. [Intent Handler Setup](#intent-handler-setup)
2. [Resolution Phase](#resolution-phase)
3. [Confirmation Phase](#confirmation-phase)
4. [Handling Phase](#handling-phase)
5. [Resolution Results](#resolution-results)

---

## Intent Handler Setup

### Extension Principal Class

```swift
import Intents

class IntentHandler: INExtension {
    override func handler(for intent: INIntent) -> Any {
        // Route to appropriate handler based on intent type
        switch intent {
        case is OrderSoupIntent:
            return OrderSoupIntentHandler()
        case is INSendMessageIntent:
            return MessageIntentHandler()
        default:
            fatalError("Unhandled intent type: \(intent)")
        }
    }
}
```

### Protocol Conformance
Each intent has a generated handling protocol:

```swift
// For custom OrderSoupIntent
class OrderSoupIntentHandler: NSObject, OrderSoupIntentHandling {
    // Implement resolve, confirm, handle methods
}

// For system INSendMessageIntent
class MessageHandler: NSObject, INSendMessageIntentHandling {
    // Implement protocol methods
}
```

---

## Resolution Phase

Validate each parameter before execution. Called for each user-facing parameter.

### Resolution Method Pattern

```swift
func resolveSoup(for intent: OrderSoupIntent) async -> SoupResolutionResult {
    guard let soup = intent.soup else {
        return .needsValue()
    }
    
    if !isAvailable(soup) {
        return .unsupported(forReason: .outOfStock)
    }
    
    return .success(with: soup)
}

func resolveQuantity(for intent: OrderSoupIntent) async -> INIntegerResolutionResult {
    let quantity = intent.quantity ?? 1
    
    if quantity < 1 {
        return .unsupported(forReason: .negativeNumbersNotSupported)
    }
    
    if quantity > 10 {
        return .confirmationRequired(with: quantity)
    }
    
    return .success(with: quantity)
}
```

### Disambiguation Example

```swift
func resolveRecipient(for intent: INSendMessageIntent) async -> INPersonResolutionResult {
    guard let recipients = intent.recipients, !recipients.isEmpty else {
        return .needsValue()
    }
    
    let person = recipients[0]
    let matches = findContacts(matching: person.displayName)
    
    switch matches.count {
    case 0:
        return .unsupported()
    case 1:
        return .success(with: matches[0])
    default:
        // Present choices to user
        return .disambiguation(with: matches)
    }
}
```

---

## Confirmation Phase

Final validation before executing. Verify services are ready.

```swift
func confirm(intent: OrderSoupIntent) async -> OrderSoupIntentResponse {
    // Check if service is available
    guard StoreService.shared.isOpen else {
        return OrderSoupIntentResponse(code: .failureStoreClosed, userActivity: nil)
    }
    
    // Check user account
    guard UserManager.shared.isSignedIn else {
        return OrderSoupIntentResponse(code: .failureRequiresLogin, userActivity: nil)
    }
    
    // Ready to proceed
    return OrderSoupIntentResponse(code: .ready, userActivity: nil)
}
```

### Confirmation Response Codes

| Code | Use When |
|------|----------|
| `.ready` | All prerequisites met, ready to handle |
| `.inProgress` | Already processing (avoid duplicate) |
| `.failure` | Cannot proceed (generic) |
| `.failureRequiresLogin` | User authentication needed |
| Custom codes | Define in intent definition |

---

## Handling Phase

Execute the action and return result.

```swift
func handle(intent: OrderSoupIntent) async -> OrderSoupIntentResponse {
    guard let soup = intent.soup else {
        return OrderSoupIntentResponse(code: .failure, userActivity: nil)
    }
    
    do {
        let order = try await OrderService.shared.placeOrder(
            soup: soup,
            quantity: intent.quantity ?? 1
        )
        
        // Success with details for Siri to speak
        let response = OrderSoupIntentResponse(code: .success, userActivity: nil)
        response.orderNumber = order.number
        response.estimatedTime = order.estimatedTime
        return response
        
    } catch {
        return OrderSoupIntentResponse(code: .failure, userActivity: nil)
    }
}
```

### Launch App for Complex Tasks

```swift
func handle(intent: OrderSoupIntent) async -> OrderSoupIntentResponse {
    // Create activity to continue in app
    let activity = NSUserActivity(activityType: "com.app.orderSoup")
    activity.userInfo = ["soupID": intent.soup?.identifier ?? ""]
    
    // Tell Siri to launch app
    return OrderSoupIntentResponse(code: .continueInApp, userActivity: activity)
}
```

---

## Resolution Results

### Common Resolution Types

| Result | Method | Use When |
|--------|--------|----------|
| Success | `.success(with:)` | Value is valid |
| Needs Value | `.needsValue()` | Parameter required but missing |
| Disambiguation | `.disambiguation(with:)` | Multiple matches, user must choose |
| Confirmation Required | `.confirmationRequired(with:)` | Confident but want user confirmation |
| Not Required | `.notRequired()` | Parameter not needed for this flow |
| Unsupported | `.unsupported()` | Value cannot be used |

### Type-Specific Resolution Classes

```swift
// Strings
INStringResolutionResult.success(with: "value")

// Integers
INIntegerResolutionResult.success(with: 5)

// People
INPersonResolutionResult.disambiguation(with: contacts)

// Placemarks
INPlacemarkResolutionResult.success(with: placemark)

// Currency
INCurrencyAmountResolutionResult.success(with: amount)

// Custom enums (generated)
SoupTypeResolutionResult.success(with: .tomatoBisque)
```

### Unsupported with Reason

```swift
// Define reasons in intent definition file
func resolveQuantity(for intent: OrderSoupIntent) async -> INIntegerResolutionResult {
    if intent.quantity ?? 0 > 100 {
        return .unsupported(forReason: .greaterThanMaximumValue)
    }
    return .success(with: intent.quantity ?? 1)
}
```

---

## Async vs Completion Handler

### Modern Async/Await (iOS 15+)
```swift
func handle(intent: OrderSoupIntent) async -> OrderSoupIntentResponse {
    let result = await OrderService.shared.placeOrder(intent.soup!)
    return OrderSoupIntentResponse(code: .success, userActivity: nil)
}
```

### Completion Handler (Legacy)
```swift
func handle(intent: OrderSoupIntent, completion: @escaping (OrderSoupIntentResponse) -> Void) {
    OrderService.shared.placeOrder(intent.soup!) { result in
        completion(OrderSoupIntentResponse(code: .success, userActivity: nil))
    }
}
```
