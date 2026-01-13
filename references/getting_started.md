# Getting Started with CarPlay Development

## Prerequisites

### Developer Requirements
1. Apple Developer Program membership
2. CarPlay entitlement approval from Apple
3. Xcode 15.0 or later

### Device Requirements
- iPhone with CarPlay support
- CarPlay-compatible vehicle or head unit
- Or use CarPlay Simulator in Xcode

## Project Setup

### 1. Request CarPlay Entitlement

Before you can build a CarPlay app, you must request the appropriate entitlement from Apple:

1. Go to [Apple Developer Portal](https://developer.apple.com)
2. Navigate to Certificates, Identifiers & Profiles
3. Select your App ID
4. Request CarPlay entitlement for your app category

### 2. Add Entitlement to Your App

Create or update your entitlements file:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>com.apple.developer.carplay-audio</key>
    <true/>
</dict>
</plist>
```

### 3. Configure Info.plist

Add the CarPlay scene configuration:

```xml
<key>UIApplicationSceneManifest</key>
<dict>
    <key>UIApplicationSupportsMultipleScenes</key>
    <true/>
    <key>UISceneConfigurations</key>
    <dict>
        <key>CPTemplateApplicationSceneSessionRoleApplication</key>
        <array>
            <dict>
                <key>UISceneClassName</key>
                <string>CPTemplateApplicationScene</string>
                <key>UISceneConfigurationName</key>
                <string>CarPlay</string>
                <key>UISceneDelegateClassName</key>
                <string>$(PRODUCT_MODULE_NAME).CarPlaySceneDelegate</string>
            </dict>
        </array>
    </dict>
</dict>
```

### 4. Create CarPlay Scene Delegate

```swift
import CarPlay

class CarPlaySceneDelegate: UIResponder, CPTemplateApplicationSceneDelegate {
    var interfaceController: CPInterfaceController?
    var carWindow: CPWindow?

    // Called when CarPlay connects
    func templateApplicationScene(
        _ templateApplicationScene: CPTemplateApplicationScene,
        didConnect interfaceController: CPInterfaceController
    ) {
        self.interfaceController = interfaceController
        self.carWindow = templateApplicationScene.carWindow

        // Set up your initial template
        let rootTemplate = createRootTemplate()
        interfaceController.setRootTemplate(rootTemplate, animated: true)
    }

    // Called when CarPlay disconnects
    func templateApplicationScene(
        _ templateApplicationScene: CPTemplateApplicationScene,
        didDisconnect interfaceController: CPInterfaceController
    ) {
        self.interfaceController = nil
        self.carWindow = nil
    }

    // Called when CarPlay scene becomes active
    func sceneDidBecomeActive(_ scene: UIScene) {
        // Resume activities
    }

    // Called when CarPlay scene resigns active
    func sceneWillResignActive(_ scene: UIScene) {
        // Pause activities
    }

    private func createRootTemplate() -> CPTemplate {
        let item = CPListItem(text: "Welcome", detailText: "Your CarPlay App")
        let section = CPListSection(items: [item])
        return CPListTemplate(title: "Home", sections: [section])
    }
}
```

## Testing with CarPlay Simulator

### Enable CarPlay Simulator
1. Open Xcode
2. Go to Xcode > Open Developer Tool > More Developer Tools
3. Download "Additional Tools for Xcode"
4. Launch CarPlay Simulator from Applications

### Connect to Simulator
1. Run your app on a simulator or device
2. Open CarPlay Simulator
3. Your app should appear in the CarPlay home screen

## App Categories and Entitlements

| App Type | Entitlement Key |
|----------|----------------|
| Audio | `com.apple.developer.carplay-audio` |
| Communication | `com.apple.developer.carplay-communication` |
| Navigation | `com.apple.developer.carplay-maps` |
| EV Charging | `com.apple.developer.carplay-charging` |
| Fueling | `com.apple.developer.carplay-fueling` |
| Parking | `com.apple.developer.carplay-parking` |
| Quick Food Ordering | `com.apple.developer.carplay-quick-ordering` |

## Next Steps

- [Templates](templates.md) - Learn about CarPlay UI templates
- [Best Practices](best_practices.md) - Design guidelines for driver safety
