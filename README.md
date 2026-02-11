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
| [ProximityReader](proximity-reader/SKILL.md) | Tap to Pay on iPhone, contactless payments, and ID verification |
| [Apple Wallet](apple-wallet/SKILL.md) | Wallet passes — boarding passes, tickets, coupons, loyalty cards, and NFC |
| [Metal](metal/SKILL.md) | GPU programming, shaders, render/compute pipelines, and Metal 4 |

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

**CarPlay**
```bash
npx skills add ios-agent/iosagent.dev --skill carplay
```

**SwiftUI**
```bash
npx skills add ios-agent/iosagent.dev --skill swiftui
```

**MapKit**
```bash
npx skills add ios-agent/iosagent.dev --skill mapkit
```

**SiriKit**
```bash
npx skills add ios-agent/iosagent.dev --skill sirikit
```

**WidgetKit**
```bash
npx skills add ios-agent/iosagent.dev --skill widgetkit
```

**Apple Foundation Models**
```bash
npx skills add ios-agent/iosagent.dev --skill apple-foundation-models
```

**Apple Wallet**
```bash
npx skills add ios-agent/iosagent.dev --skill apple-wallet
```

**Metal**
```bash
npx skills add ios-agent/iosagent.dev --skill metal
```

This works with **30+ AI coding agents** including Claude Code, GitHub Copilot, Cursor, Cline, and more. Browse all skills at [skills.sh](https://skills.sh).

### Via Claude Code Marketplace

Alternatively, install through the Claude Code marketplace:

```
/plugin marketplace add iosagent/iosagent.dev
```

Then install individual skills:

```
/plugin install carplay@iosagent
/plugin install swiftui@iosagent
/plugin install mapkit@iosagent
/plugin install sirikit@iosagent
/plugin install widgetkit@iosagent
/plugin install apple-foundation-models@iosagent
/plugin install proximity-reader@iosagent
/plugin install apple-wallet@iosagent
/plugin install metal@iosagent
```

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

### ProximityReader
Accept contactless payments on iPhone with Tap to Pay, read loyalty cards (VAS) from Apple Wallet, implement Store and Forward for offline scenarios, and verify mobile driver's licenses and IDs using the Verifier API.

### Apple Wallet
Create, sign, distribute, and update Apple Wallet passes including boarding passes, event tickets, coupons, store/loyalty cards, and generic passes. Covers pass.json structure, .pkpass bundles, NFC integration, barcode formats, push-based updates, and identity verification.

### Metal
Write, debug, and optimize Metal GPU code including shaders (MSL), render pipelines, compute pipelines, buffer/texture management, ray tracing, and Metal 4 APIs. Covers MetalKit, MetalFX, Metal Performance Shaders, and Apple Silicon optimization.

## When to Use These Skills

These skills are automatically suggested when working with:
- Apple platform frameworks (iOS, macOS, watchOS, tvOS, visionOS)
- Native app development with Swift/SwiftUI
- CarPlay, Siri, Widgets, Maps integration
- On-device AI with Apple Foundation Models
- Contactless payments, Tap to Pay, and ID verification with ProximityReader
- Apple Wallet passes, .pkpass bundles, NFC passes, and pass updates
- GPU programming, Metal shaders, compute/render pipelines, and graphics

## License

MIT License - See [LICENSE](LICENSE) for details.
