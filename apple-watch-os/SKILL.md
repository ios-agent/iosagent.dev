---
name: apple-watch-os
description: Expert guidance for building watchOS apps with SwiftUI, WidgetKit complications, notifications, Siri/App Intents, HealthKit, and WatchKit runtime management. Use this skill whenever the user asks about Apple Watch development, watchOS features, complications, watch faces, Smart Stack, Always On, double-tap, Action button (Ultra), background sessions, Extended Runtime Sessions, independent watch apps, or watchOS-specific APIs. Trigger for ClockKit to WidgetKit migration, watchOS UI patterns, multiple watch sizes, and accessibility. Also use for SwiftUI questions in a watchOS context.
---

# watchOS Apps Skill

Design before you code — watchOS requires more planning than coding. Keep interactions brief: a few taps, then wrist down.

## Architecture

| Layer | Technology | Purpose |
|-------|-----------|---------|
| Main app | SwiftUI + WatchKit | Navigation, direct interaction |
| Complications | WidgetKit | Watch face data + app launch |
| Smart Stack | WidgetKit | Swipe-up widget feed |
| Notifications | UserNotifications | Alerts + actions |
| Voice | App Intents / SiriKit | Siri + Shortcuts |
| Health | HealthKit | Sensors, workouts |
| Background | WKExtensionDelegate | Refresh, network, BLE |

## 1. App Lifecycle
- Independent app: no iOS companion required
- `@main` + `App` protocol; `WKApplicationDelegateAdaptor` for delegate
- Navigation (watchOS 10): `NavigationStack`, `TabView(.verticalPage)`
- Background: `WKExtensionDelegate.handle(_:)` + `WKBackgroundTask`

## 2. Complications (WidgetKit)
- Families: `.accessoryCircular`, `.accessoryRectangular`, `.accessoryInline`, `.accessoryCorner`
- Pattern: `TimelineProvider` -> `TimelineEntry` -> SwiftUI View
- Reload: `WidgetCenter.shared.reloadTimelines(ofKind:)`
- Smart Stack: `widgetRelevances(_:)` API
- Migration: replace `CLKComplicationDataSource` with WidgetKit timeline

## 3. Always On Display
- `TimelineView(.periodic(...))` for live updates
- `.isLuminanceReduced` env value to adapt UI
- Reduce animations/brightness in AOD state

## 4. Notifications
- Short-look: auto-generated (non-customizable)
- Long-look: `WKUserNotificationHostingController`; customize sash colors
- Action buttons: `UNNotificationCategory` + `UNNotificationAction`
- Interactive: controls in content area without launching app
- Text input suggestions: override `suggestionsForResponseToAction(withIdentifier:for:inputLanguage:)`
- Foreground actions run where tapped; background actions run on notification's target device

## 5. Gestures
- Double Tap (Series 9+, Ultra 2): `.handGestureShortcut(.primaryAction)` — one per scene
- Priority: primary action > scroll view > vertical tabs
- Action Button (Ultra): AppIntent via `ActionButtonArticle`

## 6. App Intents & Siri
- `AppIntents`: preferred for Siri, Shortcuts, Action button, Spotlight
- `SiriKit`: domain-based interactions only (messaging, media)
- Conform to `AppIntent`, implement `perform()`, use `@Parameter`

## 7. HealthKit
- Auth: `HKHealthStore().requestAuthorization(toShare:read:)`
- Workouts: `HKWorkoutSession` + `HKLiveWorkoutBuilder`
- Queries: `HKSampleQuery`, `HKStatisticsQuery`, `HKAnchoredObjectQuery`
- Extended Runtime Session needed for sustained workout tracking

## 8. Background & Runtime
- Background App Refresh: system-scheduled, limited budget
- `WKExtendedRuntimeSession`: workouts, mindfulness, location tracking
- Background `URLSession`: survives app close; prefer small payloads
- Complete tasks with `setTaskCompletedWithSnapshot(_:)`

## 9. Networking
- Foreground: `URLSession.shared` or ephemeral
- Background: `URLSessionConfiguration.backgroundSessionConfiguration("id")` + delegate

## 10. Auth, Sizes, A11y, Testing
- Auth: Sign in with Apple or PassKit (no password entry)
- Sizes: 40/41/44/45/49mm — use `.containerRelativeFrame()`, avoid fixed pixels
- Accessibility: `accessibilityLabel/hint/value`, `.accessibilityElement(children:.combine)`
- Testing: add `watchOS Unit/UI Testing Bundle` target, `@testable import`

## watchOS 10 Changes
- Vertical `TabView` navigation is standard (no `NavigationSplitView`)
- Smart Stack replaces Dock for widgets
- WidgetKit powers Lock Screen complications AND Smart Stack

## Common Patterns

```swift
// Double tap
Button("Action") { go() }.handGestureShortcut(.primaryAction)

// WidgetKit complication
struct W: Widget {
    var body: some WidgetConfiguration {
        StaticConfiguration(kind: "id", provider: P()) { e in V(entry: e) }
        .supportedFamilies([.accessoryCircular, .accessoryRectangular])
    }
}

// Extended runtime
let s = WKExtendedRuntimeSession(); s.delegate = self; s.start()

// Background URLSession
let cfg = URLSessionConfiguration.backgroundSessionConfiguration("com.app.bg")
URLSession(configuration: cfg, delegate: self, delegateQueue: nil)
    .downloadTask(with: url).resume()

// Always On
@Environment(\.isLuminanceReduced) var dim
```

## Reference
For full API docs, notification forwarding details, ClockKit migration, HealthKit patterns:
read `references/watchos-reference.md` bundled with this skill.
