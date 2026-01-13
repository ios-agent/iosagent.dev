# CarPlay Claude Skill

A comprehensive reference documentation skill for Apple CarPlay development. This skill helps developers build CarPlay-enabled iOS apps with navigation, audio, communication, and other automotive experiences.

## What This Skill Covers

- **CarPlay App Development**: Building CarPlay-compatible iOS applications
- **CPTemplateApplicationScene**: Managing the CarPlay app lifecycle
- **Templates & UI**: Working with CPTemplate types for CarPlay interfaces
- **Navigation Apps**: Implementing turn-by-turn navigation with CPNavigationSession
- **Audio Apps**: Building audio streaming apps with CPNowPlayingTemplate
- **Communication Apps**: Handling messaging and calling with CPMessageListItem
- **EV Charging Apps**: Supporting electric vehicle charging workflows
- **Quick Food Ordering**: Implementing food ordering experiences
- **Fueling Apps**: Building fuel payment integrations

## Requirements

- **Xcode**: 15.0 or later
- **iOS**: 14.0+ (CarPlay framework), iOS 17+ for latest features
- **Entitlements**: CarPlay entitlement from Apple Developer Program
- **Device**: iPhone with CarPlay support or CarPlay Simulator

## Core Implementation Pattern

CarPlay apps follow a template-based architecture:

```swift
import CarPlay

class CarPlaySceneDelegate: UIResponder, CPTemplateApplicationSceneDelegate {
    var interfaceController: CPInterfaceController?

    func templateApplicationScene(
        _ templateApplicationScene: CPTemplateApplicationScene,
        didConnect interfaceController: CPInterfaceController
    ) {
        self.interfaceController = interfaceController

        let template = CPListTemplate(
            title: "My App",
            sections: [/* sections */]
        )
        interfaceController.setRootTemplate(template, animated: true)
    }
}
```

## Documentation Structure

| File | Description |
|------|-------------|
| [Getting Started](references/getting_started.md) | Project setup and CarPlay entitlements |
| [Templates](references/templates.md) | All CPTemplate types and usage |
| [Navigation](references/navigation.md) | Turn-by-turn navigation implementation |
| [Audio](references/audio.md) | Audio and media playback apps |
| [Communication](references/communication.md) | Messaging and calling integration |
| [Point of Interest](references/poi.md) | POI and location-based features |
| [EV Charging](references/ev_charging.md) | Electric vehicle charging apps |
| [API Reference](references/api_reference.md) | Complete CarPlay API documentation |
| [Best Practices](references/best_practices.md) | Design guidelines and optimization |

## Key Features

- **Privacy**: All processing happens on-device
- **Template-Based UI**: Consistent, driver-safe interfaces
- **Siri Integration**: Voice-first interaction support
- **Real-Time Updates**: Dynamic content and navigation updates
- **Multi-Screen**: Seamless iPhone and CarPlay coordination

## Install as a Claude Code Skill

This skill is available in the Claude Code marketplace. To install it:

```
/plugin marketplace add Eyadkelleh/carplay_claude_skill
```

Then install the skill:

```
/plugin install carplay@carplay-marketplace
```

Once installed, Claude Code will automatically suggest this skill when you're working with CarPlay development.

## When to Use This Skill

This skill is automatically suggested when working with:
- CarPlay framework and APIs
- CPTemplate implementations
- Navigation and mapping features
- Automotive app development
- In-car entertainment apps

## License

MIT License - See [LICENSE](LICENSE) for details.
