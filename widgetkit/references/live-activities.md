# Live Activities Reference

## Table of Contents
1. [Overview](#overview)
2. [Activity Attributes](#activity-attributes)
3. [Activity Configuration](#activity-configuration)
4. [Starting Activities](#starting-activities)
5. [Updating Activities](#updating-activities)
6. [Ending Activities](#ending-activities)
7. [Dynamic Island Presentations](#dynamic-island-presentations)
8. [Push Notifications](#push-notifications)

---

## Overview

Live Activities display real-time information on the Lock Screen and Dynamic Island (iPhone 14 Pro+). They require:
- `ActivityKit` framework for lifecycle management
- `ActivityConfiguration` in widget extension for UI
- `ActivityAttributes` to define static and dynamic content

**Platforms**: iPhone, iPad (iOS 16.1+), mirrored to Apple Watch and Mac

---

## Activity Attributes

```swift
import ActivityKit

struct DeliveryActivityAttributes: ActivityAttributes {
    // Static data - set when starting, never changes
    let orderNumber: String
    let restaurantName: String
    
    // Dynamic content state - updates during activity
    struct ContentState: Codable, Hashable {
        let status: DeliveryStatus
        let estimatedDelivery: Date
        let driverName: String?
    }
}

enum DeliveryStatus: String, Codable {
    case preparing, pickedUp, onTheWay, delivered
}
```

---

## Activity Configuration

```swift
struct DeliveryActivityWidget: Widget {
    var body: some WidgetConfiguration {
        ActivityConfiguration(for: DeliveryActivityAttributes.self) { context in
            // Lock Screen presentation
            LockScreenView(context: context)
        } dynamicIsland: { context in
            DynamicIsland {
                // Expanded regions
                DynamicIslandExpandedRegion(.leading) {
                    Label(context.attributes.restaurantName, systemImage: "bag")
                }
                DynamicIslandExpandedRegion(.trailing) {
                    Text(context.state.estimatedDelivery, style: .timer)
                }
                DynamicIslandExpandedRegion(.bottom) {
                    ProgressView(value: progress(for: context.state.status))
                }
                DynamicIslandExpandedRegion(.center) {
                    Text(context.state.status.displayName)
                }
            } compactLeading: {
                Image(systemName: "bag.fill")
            } compactTrailing: {
                Text(context.state.estimatedDelivery, style: .timer)
            } minimal: {
                Image(systemName: "bag.fill")
            }
        }
    }
}
```

---

## Starting Activities

```swift
import ActivityKit

func startDeliveryActivity(order: Order) async throws -> Activity<DeliveryActivityAttributes>? {
    // Check if Live Activities are enabled
    guard ActivityAuthorizationInfo().areActivitiesEnabled else {
        return nil
    }
    
    let attributes = DeliveryActivityAttributes(
        orderNumber: order.id,
        restaurantName: order.restaurant
    )
    
    let initialState = DeliveryActivityAttributes.ContentState(
        status: .preparing,
        estimatedDelivery: order.estimatedTime,
        driverName: nil
    )
    
    let content = ActivityContent(state: initialState, staleDate: nil)
    
    do {
        let activity = try Activity.request(
            attributes: attributes,
            content: content,
            pushType: .token  // Enable push updates
        )
        
        // Store activity ID for later updates
        storeActivityID(activity.id)
        
        // Get push token if using push updates
        for await token in activity.pushTokenUpdates {
            sendTokenToServer(token)
        }
        
        return activity
    } catch {
        print("Failed to start activity: \(error)")
        return nil
    }
}
```

---

## Updating Activities

### From App
```swift
func updateDeliveryStatus(activityID: String, newStatus: DeliveryStatus, driver: String?) async {
    let newState = DeliveryActivityAttributes.ContentState(
        status: newStatus,
        estimatedDelivery: calculateNewETA(),
        driverName: driver
    )
    
    let content = ActivityContent(state: newState, staleDate: nil)
    
    // Update by ID
    for activity in Activity<DeliveryActivityAttributes>.activities {
        if activity.id == activityID {
            await activity.update(content)
        }
    }
}
```

### With Alert
```swift
let alertConfig = AlertConfiguration(
    title: "Driver Assigned!",
    body: "\(driverName) is picking up your order",
    sound: .default
)

await activity.update(content, alertConfiguration: alertConfig)
```

---

## Ending Activities

```swift
func endDeliveryActivity(activityID: String, finalStatus: DeliveryStatus) async {
    let finalState = DeliveryActivityAttributes.ContentState(
        status: finalStatus,
        estimatedDelivery: Date(),
        driverName: nil
    )
    
    let finalContent = ActivityContent(state: finalState, staleDate: nil)
    
    for activity in Activity<DeliveryActivityAttributes>.activities {
        if activity.id == activityID {
            await activity.end(
                finalContent,
                dismissalPolicy: .after(.now + 3600)  // Keep on Lock Screen for 1 hour
            )
        }
    }
}

// Dismissal policies
.immediate           // Remove immediately
.default             // System decides (usually 4 hours)
.after(Date)         // Keep until specified time (max 4 hours)
```

---

## Dynamic Island Presentations

### Expanded View Regions
```swift
DynamicIsland {
    DynamicIslandExpandedRegion(.leading) {
        // Left side content
    }
    DynamicIslandExpandedRegion(.trailing) {
        // Right side content
    }
    DynamicIslandExpandedRegion(.center) {
        // Center content (below notch)
    }
    DynamicIslandExpandedRegion(.bottom) {
        // Bottom content (main area)
    }
}
```

### Compact View
```swift
compactLeading: {
    // Small icon/indicator on left
    Image(systemName: "car.fill")
}
compactTrailing: {
    // Small info on right (timer, count, etc.)
    Text(eta, style: .timer)
}
```

### Minimal View
```swift
minimal: {
    // Single icon when multiple activities exist
    Image(systemName: "bag.fill")
}
```

---

## Push Notifications

### APNs Payload
```json
{
    "aps": {
        "timestamp": 1234567890,
        "event": "update",
        "content-state": {
            "status": "onTheWay",
            "estimatedDelivery": "2024-01-15T14:30:00Z",
            "driverName": "John"
        },
        "alert": {
            "title": "Order Update",
            "body": "Your driver is on the way!"
        }
    }
}
```

### Event Types
- `"update"` - Update content state
- `"end"` - End the activity

### End via Push
```json
{
    "aps": {
        "timestamp": 1234567890,
        "event": "end",
        "dismissal-date": 1234571490,
        "content-state": {
            "status": "delivered",
            "estimatedDelivery": "2024-01-15T14:25:00Z",
            "driverName": "John"
        }
    }
}
```

---

## Lock Screen View

```swift
struct LockScreenView: View {
    let context: ActivityViewContext<DeliveryActivityAttributes>
    
    var body: some View {
        HStack {
            VStack(alignment: .leading) {
                Text(context.attributes.restaurantName)
                    .font(.headline)
                Text("Order #\(context.attributes.orderNumber)")
                    .font(.caption)
            }
            Spacer()
            VStack(alignment: .trailing) {
                Text(context.state.status.displayName)
                    .font(.subheadline)
                Text(context.state.estimatedDelivery, style: .timer)
                    .font(.title2)
            }
        }
        .padding()
        .activityBackgroundTint(.blue.opacity(0.2))
    }
}
```

---

## Best Practices

- **Start sparingly**: Only for events users actively track
- **Update meaningfully**: Avoid frequent minor updates
- **End promptly**: Don't keep stale activities
- **Design for glanceability**: Key info visible at a glance
- **Support all presentations**: Lock Screen, expanded, compact, minimal
- **Test on device**: Simulator has limitations for Dynamic Island
