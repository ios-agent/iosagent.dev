# CarPlay Development Reference Index

Welcome to the CarPlay development reference documentation. This guide covers everything you need to build CarPlay-enabled iOS applications.

## Documentation Overview

### Getting Started
- [Getting Started](getting_started.md) - Project setup, entitlements, and first CarPlay app

### Core Concepts
- [Templates](templates.md) - Understanding CarPlay's template-based UI system
- [API Reference](api_reference.md) - Complete CarPlay framework API documentation

### App Categories
- [Navigation](navigation.md) - Turn-by-turn navigation apps
- [Audio](audio.md) - Music and podcast streaming apps
- [Communication](communication.md) - Messaging and calling apps
- [Point of Interest](poi.md) - Location-based discovery apps
- [EV Charging](ev_charging.md) - Electric vehicle charging apps

### Advanced Topics
- [Best Practices](best_practices.md) - Design guidelines and optimization tips

## Quick Reference

### Supported App Categories
| Category | Primary Template | Entitlement |
|----------|-----------------|-------------|
| Navigation | CPMapTemplate | `com.apple.developer.carplay-maps` |
| Audio | CPNowPlayingTemplate | `com.apple.developer.carplay-audio` |
| Communication | CPListTemplate | `com.apple.developer.carplay-communication` |
| EV Charging | CPPointOfInterestTemplate | `com.apple.developer.carplay-charging` |
| Parking | CPPointOfInterestTemplate | `com.apple.developer.carplay-parking` |
| Quick Food Ordering | CPListTemplate | `com.apple.developer.carplay-quick-ordering` |

### Key Classes
- `CPTemplateApplicationSceneDelegate` - Main entry point for CarPlay apps
- `CPInterfaceController` - Manages template stack and navigation
- `CPTemplate` - Base class for all CarPlay templates
- `CPListItem` - Individual list row items

## Framework Import

```swift
import CarPlay
```

## Minimum Requirements
- iOS 14.0+ (base CarPlay support)
- iOS 17.0+ (latest features)
- CarPlay entitlement from Apple Developer Program
