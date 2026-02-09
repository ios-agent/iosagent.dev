# Timeline & Updates Reference

## Table of Contents
1. [Timeline Provider Protocol](#timeline-provider-protocol)
2. [Timeline Entry](#timeline-entry)
3. [Reload Policies](#reload-policies)
4. [Async Timeline Provider](#async-timeline-provider)
5. [Push Notification Updates](#push-notification-updates)
6. [Programmatic Refresh](#programmatic-refresh)

---

## Timeline Provider Protocol

```swift
protocol TimelineProvider {
    associatedtype Entry: TimelineEntry
    typealias Context = TimelineProviderContext
    
    // Return placeholder for widget gallery
    func placeholder(in context: Context) -> Entry
    
    // Return snapshot for gallery preview (isPreview: true) or quick display
    func getSnapshot(in context: Context, completion: @escaping (Entry) -> Void)
    
    // Return timeline with entries and reload policy
    func getTimeline(in context: Context, completion: @escaping (Timeline<Entry>) -> Void)
}
```

### Context Properties
```swift
struct TimelineProviderContext {
    let family: WidgetFamily           // Current widget size
    let isPreview: Bool                // True if rendering for gallery
    let displaySize: CGSize            // Actual display size in points
    let environmentVariants: [String]  // Environment variations
}
```

---

## Timeline Entry

```swift
protocol TimelineEntry {
    var date: Date { get }                    // Required: When to display
    var relevance: TimelineEntryRelevance? { get }  // Optional: Smart Stack priority
}

// Example with relevance
struct MyEntry: TimelineEntry {
    let date: Date
    let data: MyData
    
    var relevance: TimelineEntryRelevance? {
        // Higher score = more likely to show in Smart Stack
        TimelineEntryRelevance(score: data.importance, duration: 3600)
    }
}
```

---

## Reload Policies

```swift
enum TimelineReloadPolicy {
    case atEnd              // Request new timeline when last entry displays
    case after(Date)        // Request new timeline after specific date
    case never              // Don't request automatic reload
}

// Examples
Timeline(entries: entries, policy: .atEnd)
Timeline(entries: entries, policy: .after(Date().addingTimeInterval(3600)))
Timeline(entries: entries, policy: .never)
```

### Best Practices
- **Use `.after(Date)`** for predictable update schedules
- **Use `.atEnd`** when content changes unpredictably
- **Use `.never`** for static content, update via `WidgetCenter` or push

---

## Async Timeline Provider

```swift
// iOS 17+ async/await version
struct Provider: AppIntentTimelineProvider {
    func placeholder(in context: Context) -> Entry {
        Entry(date: .now)
    }
    
    func snapshot(for configuration: ConfigIntent, in context: Context) async -> Entry {
        await fetchCurrentEntry()
    }
    
    func timeline(for configuration: ConfigIntent, in context: Context) async -> Timeline<Entry> {
        let entries = await fetchEntries()
        return Timeline(entries: entries, policy: .atEnd)
    }
}
```

---

## Push Notification Updates

### Enable Background Mode
Add to widget extension's Info.plist:
```xml
<key>NSWidgetWantsLocation</key>
<false/>
<key>NSWidgetWantsContentUpdateNotifications</key>
<true/>
```

### Send Push Notification
```json
{
    "aps": {
        "content-available": 1
    }
}
```

### Handle in Extension
The system automatically calls `getTimeline` when push received.

---

## Programmatic Refresh

```swift
import WidgetKit

// Refresh specific widget
WidgetCenter.shared.reloadTimelines(ofKind: "com.app.mywidget")

// Refresh all widgets
WidgetCenter.shared.reloadAllTimelines()

// Get current widget configurations
WidgetCenter.shared.getCurrentConfigurations { result in
    switch result {
    case .success(let configs):
        for config in configs {
            print("Widget: \(config.kind), Family: \(config.family)")
        }
    case .failure(let error):
        print("Error: \(error)")
    }
}
```

### When to Refresh
- After user action in main app
- When background task completes
- After significant data change
- **Avoid**: Frequent refreshes drain battery budget

---

## Timeline Generation Patterns

### Multiple Future Entries
```swift
func getTimeline(in context: Context, completion: @escaping (Timeline<Entry>) -> Void) {
    var entries: [Entry] = []
    let currentDate = Date()
    
    // Generate entries for next 5 hours
    for hourOffset in 0..<5 {
        let entryDate = Calendar.current.date(byAdding: .hour, value: hourOffset, to: currentDate)!
        let entry = Entry(date: entryDate, data: dataForHour(hourOffset))
        entries.append(entry)
    }
    
    completion(Timeline(entries: entries, policy: .atEnd))
}
```

### Date-Based Content
```swift
// Show different content at specific times
let morningEntry = Entry(date: morningDate, greeting: "Good morning!")
let afternoonEntry = Entry(date: noonDate, greeting: "Good afternoon!")
let eveningEntry = Entry(date: eveningDate, greeting: "Good evening!")
```
