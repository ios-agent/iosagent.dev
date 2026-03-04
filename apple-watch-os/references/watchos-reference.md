# watchOS Reference

Source: developer.apple.com/documentation/watchos-apps

## App Architecture
- Independent app: no iOS companion needed
- `@main struct MyApp: App` entry point
- Background via `WKExtensionDelegate.handle(_:)`

## Always On Display
- `.isLuminanceReduced` environment value
- `TimelineView(.periodic(...))` for live updates
- Reduce animations and brightness in AOD state

## Double Tap (Series 9+, Ultra 2)
- `.handGestureShortcut(.primaryAction)` on any button/toggle/link
- One primary action per scene
- Priority: primary action > scroll view > vertical tabs

## Notifications
### Short-Look
Auto-generated: app icon + title. Not customizable.

### Long-Look (WKUserNotificationHostingController)
- Customize: `sashColor`, `titleColor`, `subtitleColor`, `wantsSashBlur`
- Register actions: `UNNotificationCategory` + `UNNotificationAction`
- `content.categoryIdentifier = "CATEGORY_ID"` for local
- `"category": "CATEGORY_ID"` in payload for remote
- Text input: override `suggestionsForResponseToAction(withIdentifier:for:inputLanguage:)`
- Foreground actions run where tapped; background actions on notification's target device

### Action Identifiers
| Tapped | actionIdentifier |
|--------|-----------------|
| Action button | Button's identifier |
| Dismiss | UNNotificationDismissActionIdentifier |
| Elsewhere | UNNotificationDefaultActionIdentifier |

## WidgetKit Complications
```swift
struct MyWidget: Widget {
    var body: some WidgetConfiguration {
        StaticConfiguration(kind: "id", provider: Provider()) { entry in
            EntryView(entry: entry)
        }
        .supportedFamilies([.accessoryCircular, .accessoryRectangular,
                            .accessoryInline, .accessoryCorner])
    }
}
```
Reload: `WidgetCenter.shared.reloadTimelines(ofKind:)`
Smart Stack: `widgetRelevances(_:)` with `RelevantContext`

## Background Tasks
```swift
func handle(_ tasks: Set<WKRefreshBackgroundTask>) {
    for task in tasks {
        switch task {
        case let t as WKApplicationRefreshBackgroundTask:
            // fetch data, schedule next
            t.setTaskCompletedWithSnapshot(false)
        case let t as WKURLSessionRefreshBackgroundTask:
            // handle background URLSession response
            t.setTaskCompletedWithSnapshot(false)
        default:
            task.setTaskCompletedWithSnapshot(false)
        }
    }
}
```
Schedule: `WKExtension.shared().scheduleBackgroundRefresh(withPreferredDate:userInfo:completionHandler:)`

## Extended Runtime Sessions
```swift
let session = WKExtendedRuntimeSession()
session.delegate = self
session.start()
// Types: .workout, .mindfulness, .smartAlarm, .selfCare, .heartRateMonitor
```

## Background URLSession
```swift
let config = URLSessionConfiguration.backgroundSessionConfiguration("com.app.bg")
let session = URLSession(configuration: config, delegate: self, delegateQueue: nil)
session.downloadTask(with: url).resume()
// Background session persists if app closes; prefer small payloads; may be deferred
```

## HealthKit
```swift
// Auth
try await HKHealthStore().requestAuthorization(toShare: types, read: types)

// Workout
let config = HKWorkoutConfiguration()
config.activityType = .running
let session = try HKWorkoutSession(healthStore: store, configuration: config)
let builder = session.associatedWorkoutBuilder()

// Queries
HKSampleQuery, HKStatisticsQuery, HKAnchoredObjectQuery
```

## App Intents
```swift
struct MyIntent: AppIntent {
    static var title: LocalizedStringResource = "Do Thing"
    @Parameter(title: "Value") var value: Int
    func perform() async throws -> some IntentResult {
        // do work
        return .result()
    }
}
```

## Multiple Watch Sizes
- 40mm: 162x197pt, 41mm: 176x215pt, 44mm: 184x224pt
- 45mm: 198x242pt, 49mm Ultra: 205x251pt
- Use `.containerRelativeFrame()` and `GeometryReader` for adaptive layouts

## Testing
```
New Target > watchOS > watchOS Unit Testing Bundle
@testable import YourWatchExtension
Scheme: [Project] WatchKit ExtensionTests
```

## watchOS 10 Navigation
```swift
// Vertical paged TabView (new standard)
TabView {
    HomeView().tabItem { Label("Home", systemImage: "house") }
    StatsView().tabItem { Label("Stats", systemImage: "chart.bar") }
}
.tabViewStyle(.verticalPage)

// NavigationStack still works
NavigationStack {
    List(items) { item in
        NavigationLink(item.title, value: item)
    }
    .navigationDestination(for: Item.self) { DetailView(item: $0) }
}
```
Note: `NavigationSplitView` is NOT available on watchOS.
