# Widget Interactivity Reference

## Table of Contents
1. [Deep Links](#deep-links)
2. [Buttons with App Intents](#buttons-with-app-intents)
3. [Toggles](#toggles)
4. [Configurable Widgets](#configurable-widgets)
5. [App Intent Examples](#app-intent-examples)

---

## Deep Links

### Single Widget Link
```swift
struct MyWidgetView: View {
    var body: some View {
        VStack {
            Text("Tap to open")
        }
        .widgetURL(URL(string: "myapp://detail/123")!)
    }
}
```

### Multiple Links (Medium/Large widgets)
```swift
struct MyWidgetView: View {
    var body: some View {
        VStack {
            Link(destination: URL(string: "myapp://item/1")!) {
                ItemRow(item: item1)
            }
            Link(destination: URL(string: "myapp://item/2")!) {
                ItemRow(item: item2)
            }
        }
    }
}
```

### Handle in App
```swift
// SwiftUI App
@main
struct MyApp: App {
    var body: some Scene {
        WindowGroup {
            ContentView()
                .onOpenURL { url in
                    handleWidgetURL(url)
                }
        }
    }
}

// UIKit AppDelegate
func application(_ app: UIApplication, open url: URL, options: [UIApplication.OpenURLOptionsKey : Any] = [:]) -> Bool {
    handleWidgetURL(url)
    return true
}
```

---

## Buttons with App Intents

### Define App Intent
```swift
import AppIntents

struct RefreshDataIntent: AppIntent {
    static var title: LocalizedStringResource = "Refresh Data"
    static var description = IntentDescription("Refreshes the widget data")
    
    func perform() async throws -> some IntentResult {
        // Perform action
        await DataManager.shared.refresh()
        return .result()
    }
}
```

### Use in Widget
```swift
struct MyWidgetView: View {
    var body: some View {
        VStack {
            Text("Current Value: \(value)")
            
            Button(intent: RefreshDataIntent()) {
                Label("Refresh", systemImage: "arrow.clockwise")
            }
            .buttonStyle(.bordered)
        }
    }
}
```

### Button with Parameters
```swift
struct IncrementIntent: AppIntent {
    static var title: LocalizedStringResource = "Increment"
    
    @Parameter(title: "Amount")
    var amount: Int
    
    init() { self.amount = 1 }
    init(amount: Int) { self.amount = amount }
    
    func perform() async throws -> some IntentResult {
        Counter.shared.value += amount
        return .result()
    }
}

// In widget view
Button(intent: IncrementIntent(amount: 5)) {
    Text("+5")
}
```

---

## Toggles

### Define Toggle Intent
```swift
struct ToggleFeatureIntent: AppIntent {
    static var title: LocalizedStringResource = "Toggle Feature"
    
    @Parameter(title: "Enabled")
    var isEnabled: Bool
    
    func perform() async throws -> some IntentResult {
        Settings.shared.featureEnabled = isEnabled
        return .result()
    }
}
```

### Use Toggle in Widget
```swift
struct MyWidgetView: View {
    @AppStorage("featureEnabled", store: UserDefaults(suiteName: "group.app"))
    var isEnabled: Bool = false
    
    var body: some View {
        Toggle(isOn: isEnabled, intent: ToggleFeatureIntent(isEnabled: !isEnabled)) {
            Label("Enable Feature", systemImage: "star")
        }
        .toggleStyle(.switch)
    }
}
```

---

## Configurable Widgets

### Configuration Intent
```swift
import AppIntents

struct SelectCityIntent: WidgetConfigurationIntent {
    static var title: LocalizedStringResource = "Select City"
    static var description = IntentDescription("Choose the city to display")
    
    @Parameter(title: "City")
    var city: CityEntity?
}

// Entity for selection
struct CityEntity: AppEntity {
    static var typeDisplayRepresentation = TypeDisplayRepresentation(name: "City")
    static var defaultQuery = CityQuery()
    
    var id: String
    var name: String
    
    var displayRepresentation: DisplayRepresentation {
        DisplayRepresentation(title: "\(name)")
    }
}

struct CityQuery: EntityQuery {
    func entities(for identifiers: [String]) async throws -> [CityEntity] {
        // Return entities matching identifiers
    }
    
    func suggestedEntities() async throws -> [CityEntity] {
        // Return suggested options
        [
            CityEntity(id: "nyc", name: "New York"),
            CityEntity(id: "la", name: "Los Angeles"),
            CityEntity(id: "sf", name: "San Francisco")
        ]
    }
}
```

### Use AppIntentConfiguration
```swift
struct ConfigurableWidget: Widget {
    var body: some WidgetConfiguration {
        AppIntentConfiguration(
            kind: "com.app.configurable",
            intent: SelectCityIntent.self,
            provider: ConfigProvider()
        ) { entry in
            ConfigurableWidgetView(entry: entry)
        }
        .configurationDisplayName("City Weather")
        .description("Shows weather for selected city")
    }
}

struct ConfigProvider: AppIntentTimelineProvider {
    func timeline(for configuration: SelectCityIntent, in context: Context) async -> Timeline<Entry> {
        let city = configuration.city ?? CityEntity(id: "default", name: "Default")
        let weather = await fetchWeather(for: city)
        let entry = Entry(date: .now, weather: weather)
        return Timeline(entries: [entry], policy: .after(.now.addingTimeInterval(3600)))
    }
}
```

---

## App Intent Examples

### Complete Task Intent
```swift
struct CompleteTaskIntent: AppIntent {
    static var title: LocalizedStringResource = "Complete Task"
    
    @Parameter(title: "Task ID")
    var taskID: String
    
    init() {}
    init(taskID: String) { self.taskID = taskID }
    
    func perform() async throws -> some IntentResult {
        try await TaskManager.shared.complete(taskID: taskID)
        // Refresh widget after action
        WidgetCenter.shared.reloadTimelines(ofKind: "com.app.tasks")
        return .result()
    }
}

// Usage in widget
ForEach(tasks) { task in
    HStack {
        Button(intent: CompleteTaskIntent(taskID: task.id)) {
            Image(systemName: task.isComplete ? "checkmark.circle.fill" : "circle")
        }
        Text(task.title)
    }
}
```

### Intent with Confirmation
```swift
struct DeleteItemIntent: AppIntent {
    static var title: LocalizedStringResource = "Delete Item"
    
    @Parameter(title: "Item")
    var item: ItemEntity
    
    static var isDiscoverable: Bool { false }
    
    func perform() async throws -> some IntentResult & ReturnsValue<Bool> {
        try await ItemStore.shared.delete(item)
        return .result(value: true)
    }
}
```

---

## Interactive Constraints

- **Small widgets**: Single tap target only (use `widgetURL`)
- **Medium/Large**: Multiple `Button`, `Toggle`, `Link` allowed
- **Accessory widgets**: Limited interactivity, prefer `widgetURL`
- **Actions must be fast**: Long-running tasks → start in app
- **Refresh after action**: Call `WidgetCenter.shared.reloadTimelines` after state changes
