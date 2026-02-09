# Siri Shortcuts Reference

## Table of Contents
1. [Donating Shortcuts](#donating-shortcuts)
2. [Shortcut Suggestions](#shortcut-suggestions)
3. [Add to Siri Button](#add-to-siri-button)
4. [Relevant Shortcuts](#relevant-shortcuts)
5. [Deleting Shortcuts](#deleting-shortcuts)
6. [NSUserActivity Shortcuts](#nsuseractivity-shortcuts)

---

## Donating Shortcuts

Donate shortcuts after user actions to help Siri learn patterns.

### Basic Donation

```swift
import Intents

func donateShortcut(for order: Order) {
    // Create intent with user's choices
    let intent = OrderSoupIntent()
    intent.soup = Soup(identifier: order.soupID, display: order.soupName)
    intent.quantity = NSNumber(value: order.quantity)
    
    // Set suggested phrase
    intent.suggestedInvocationPhrase = "Order my usual soup"
    
    // Create interaction
    let interaction = INInteraction(intent: intent, response: nil)
    interaction.identifier = order.id.uuidString
    
    // Donate
    interaction.donate { error in
        if let error = error {
            print("Donation failed: \(error.localizedDescription)")
        } else {
            print("Successfully donated interaction")
        }
    }
}
```

### Donation Best Practices

- **Donate after each action**: Helps Siri learn frequency
- **Use consistent identifiers**: Enables deletion later
- **Include suggested phrases**: Helps users discover shortcuts
- **Don't over-donate**: Only meaningful user actions

---

## Shortcut Suggestions

Proactively suggest shortcuts to users.

```swift
import Intents

func updateShortcutSuggestions() {
    var suggestions: [INShortcut] = []
    
    // Suggest based on user history
    for favoriteOrder in user.favoriteOrders {
        let intent = OrderSoupIntent()
        intent.soup = favoriteOrder.soup
        intent.quantity = favoriteOrder.quantity
        intent.suggestedInvocationPhrase = "Order \(favoriteOrder.name)"
        
        if let shortcut = INShortcut(intent: intent) {
            suggestions.append(shortcut)
        }
    }
    
    // Set suggestions (replaces previous list)
    INVoiceShortcutCenter.shared.setShortcutSuggestions(suggestions)
}
```

### Clear Suggestions

```swift
// Remove all suggestions
INVoiceShortcutCenter.shared.setShortcutSuggestions([])
```

---

## Add to Siri Button

Let users add voice shortcuts from your app.

### Using INUIAddVoiceShortcutButton

```swift
import IntentsUI

class OrderDetailViewController: UIViewController, INUIAddVoiceShortcutButtonDelegate {
    
    func setupAddToSiriButton(for order: Order) {
        let intent = OrderSoupIntent()
        intent.soup = order.soup
        intent.suggestedInvocationPhrase = "Order my \(order.soupName)"
        
        let button = INUIAddVoiceShortcutButton(style: .whiteOutline)
        button.shortcut = INShortcut(intent: intent)
        button.delegate = self
        
        view.addSubview(button)
    }
    
    // MARK: - INUIAddVoiceShortcutButtonDelegate
    
    func present(_ addVoiceShortcutViewController: INUIAddVoiceShortcutViewController,
                 for addVoiceShortcutButton: INUIAddVoiceShortcutButton) {
        addVoiceShortcutViewController.delegate = self
        present(addVoiceShortcutViewController, animated: true)
    }
    
    func present(_ editVoiceShortcutViewController: INUIEditVoiceShortcutViewController,
                 for addVoiceShortcutButton: INUIAddVoiceShortcutButton) {
        editVoiceShortcutViewController.delegate = self
        present(editVoiceShortcutViewController, animated: true)
    }
}

// MARK: - INUIAddVoiceShortcutViewControllerDelegate
extension OrderDetailViewController: INUIAddVoiceShortcutViewControllerDelegate {
    func addVoiceShortcutViewController(_ controller: INUIAddVoiceShortcutViewController,
                                        didFinishWith voiceShortcut: INVoiceShortcut?,
                                        error: Error?) {
        controller.dismiss(animated: true)
    }
    
    func addVoiceShortcutViewControllerDidCancel(_ controller: INUIAddVoiceShortcutViewController) {
        controller.dismiss(animated: true)
    }
}
```

### Button Styles

```swift
INUIAddVoiceShortcutButton(style: .white)        // White background
INUIAddVoiceShortcutButton(style: .whiteOutline) // White outline
INUIAddVoiceShortcutButton(style: .black)        // Black background
INUIAddVoiceShortcutButton(style: .blackOutline) // Black outline
INUIAddVoiceShortcutButton(style: .automatic)    // Adapts to context
INUIAddVoiceShortcutButton(style: .automaticOutline)
```

---

## Relevant Shortcuts

Suggest shortcuts based on time, location, or situation (watchOS Siri face).

```swift
import Intents

func setRelevantShortcuts() {
    var relevantShortcuts: [INRelevantShortcut] = []
    
    // Morning coffee shortcut
    let coffeeIntent = OrderSoupIntent()
    coffeeIntent.soup = Soup(identifier: "coffee", display: "Morning Coffee")
    
    if let shortcut = INShortcut(intent: coffeeIntent) {
        let relevantShortcut = INRelevantShortcut(shortcut: shortcut)
        relevantShortcut.shortcutRole = .action
        
        // Show in morning
        let morningProvider = INDailyRoutineRelevanceProvider(situation: .morning)
        relevantShortcut.relevanceProviders = [morningProvider]
        
        relevantShortcuts.append(relevantShortcut)
    }
    
    // Gym workout shortcut
    let workoutIntent = INStartWorkoutIntent()
    if let shortcut = INShortcut(intent: workoutIntent) {
        let relevantShortcut = INRelevantShortcut(shortcut: shortcut)
        relevantShortcut.shortcutRole = .action
        
        // Show when at gym
        let gymLocation = CLLocationCoordinate2D(latitude: 37.33, longitude: -122.01)
        let region = CLCircularRegion(center: gymLocation, radius: 100, identifier: "gym")
        let locationProvider = INLocationRelevanceProvider(region: region)
        relevantShortcut.relevanceProviders = [locationProvider]
        
        relevantShortcuts.append(relevantShortcut)
    }
    
    // Set all relevant shortcuts
    INRelevantShortcutStore.default.setRelevantShortcuts(relevantShortcuts) { error in
        if let error = error {
            print("Failed to set relevant shortcuts: \(error)")
        }
    }
}
```

### Relevance Providers

| Provider | Triggers When |
|----------|---------------|
| `INDailyRoutineRelevanceProvider` | Morning, evening, commute, workout, etc. |
| `INLocationRelevanceProvider` | User enters/exits region |
| `INDateRelevanceProvider` | Specific date/time range |

---

## Deleting Shortcuts

### Delete by Identifier

```swift
// Delete specific interactions
INInteraction.delete(with: ["order-123", "order-456"]) { error in
    if let error = error {
        print("Delete failed: \(error)")
    }
}
```

### Delete by Group Identifier

```swift
// When donating, set group identifier
interaction.groupIdentifier = "soup-orders"

// Later, delete entire group
INInteraction.delete(with: "soup-orders") { error in }
```

### Delete All

```swift
// Delete all interactions from your app
INInteraction.deleteAll { error in }
```

---

## NSUserActivity Shortcuts

Alternative to intents for simpler use cases.

### Donate Activity

```swift
let activity = NSUserActivity(activityType: "com.app.viewMenu")
activity.title = "View Soup Menu"
activity.isEligibleForSearch = true
activity.isEligibleForPrediction = true
activity.suggestedInvocationPhrase = "Show soup menu"
activity.persistentIdentifier = "view-menu"

// Make current to donate
activity.becomeCurrent()
```

### Handle Activity

```swift
// SwiftUI
.onContinueUserActivity("com.app.viewMenu") { activity in
    navigateToMenu()
}

// UIKit
func application(_ application: UIApplication,
                 continue userActivity: NSUserActivity,
                 restorationHandler: @escaping ([UIUserActivityRestoring]?) -> Void) -> Bool {
    if userActivity.activityType == "com.app.viewMenu" {
        navigateToMenu()
        return true
    }
    return false
}
```

### Delete Activity

```swift
NSUserActivity.deleteSavedUserActivities(withPersistentIdentifiers: ["view-menu"]) {
    print("Deleted activity")
}
```
