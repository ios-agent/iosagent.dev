# iosagent.dev

A collection of comprehensive iOS/macOS development skills for AI coding agents. These skills help developers build apps using Apple's native frameworks including CarPlay, SwiftUI, MapKit, SiriKit, WidgetKit, and Apple Foundation Models.

## Available Skills

| Skill | Description |
|-------|-------------|
| [CarPlay](carplay/SKILL.md) | Building CarPlay-enabled apps for automotive experiences |
| [SwiftUI](swiftui/SKILL.md) | User interface framework for all Apple platforms |
| [MapKit](apple-mapkit/SKILL.md) | Maps, location, directions, and place search |
| [SiriKit](sirikit/SKILL.md) | Voice interactions, Shortcuts, and intelligent suggestions |
| [WidgetKit](widgetkit/SKILL.md) | Widgets, Live Activities, and watch complications |
| [Apple Foundation Models](apple-foundation-models/SKILL.md) | On-device AI and LLM capabilities |

## Requirements

- **Xcode**: 15.0 or later
- **iOS**: 14.0+ (varies by framework)
- **macOS**: 13.0+
- **Device**: Physical device or Simulator

## Installation

### Install All Skills

```bash
npx skills add ios-agent/iosagent.dev
```

### Install Individual Skills

```bash
npx skills add ios-agent/iosagent.dev --skill carplay
npx skills add ios-agent/iosagent.dev --skill swiftui
npx skills add ios-agent/iosagent.dev --skill mapkit
npx skills add ios-agent/iosagent.dev --skill sirikit
npx skills add ios-agent/iosagent.dev --skill widgetkit
npx skills add ios-agent/iosagent.dev --skill apple-foundation-models
```

This works with **30+ AI coding agents** including Claude Code, GitHub Copilot, Cursor, Cline, and more. Browse all skills at [skills.sh](https://skills.sh).

## Skills Overview

### CarPlay
Build CarPlay-enabled iOS apps with navigation, audio, communication, and utility experiences. Covers CPTemplateApplicationScene, all template types, navigation sessions, and more.

### SwiftUI
Complete SwiftUI framework documentation covering views, modifiers, layout, state management, animations, navigation, and data flow for iOS, macOS, watchOS, tvOS, and visionOS.

### MapKit
Integrate Apple Maps with annotations, directions, local search, overlays, and LookAround. Supports both SwiftUI Map (iOS 17+) and MKMapView.

### SiriKit
Implement Siri voice interactions, Shortcuts, custom intents, and App Intents. Covers all system intent domains and custom intent definition.

### WidgetKit
Create widgets, Live Activities, watch complications, and controls. Covers all widget families, timeline providers, interactivity, and rendering modes.

### Apple Foundation Models
Build with Apple's on-device AI using SystemLanguageModel, guided generation, tool calling, and prompting patterns for iOS 26+.

## When to Use These Skills

These skills are automatically suggested when working with:
- Apple platform frameworks (iOS, macOS, watchOS, tvOS, visionOS)
- Native app development with Swift/SwiftUI
- CarPlay, Siri, Widgets, Maps integration
- On-device AI with Apple Foundation Models

## License

MIT License - See [LICENSE](LICENSE) for details.
