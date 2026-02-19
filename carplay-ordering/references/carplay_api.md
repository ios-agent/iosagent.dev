# CarPlay Framework API Reference

Quick reference for the key CarPlay classes used in quick-ordering apps.

## Template Classes

| Class | Purpose | Docs |
|-------|---------|------|
| `CPInterfaceController` | Root controller managing template stack | [Link](https://developer.apple.com/documentation/carplay/cpinterfacecontroller) |
| `CPTabBarTemplate` | Tab-based navigation container | [Link](https://developer.apple.com/documentation/carplay/cptabbartemplate) |
| `CPPointOfInterestTemplate` | Map with selectable POIs (max 12) | [Link](https://developer.apple.com/documentation/carplay/cppointofinteresttemplate) |
| `CPListTemplate` | Scrollable list of items | [Link](https://developer.apple.com/documentation/carplay/cplisttemplate) |
| `CPInformationTemplate` | Info display for orders/locations | [Link](https://developer.apple.com/documentation/carplay/cpinformationtemplate) |
| `CPAlertTemplate` | Modal alert dialogs | [Link](https://developer.apple.com/documentation/carplay/cpalerttemplate) |

## UI Elements

| Class | Purpose | Docs |
|-------|---------|------|
| `CPTextButton` | Text-styled action button | [Link](https://developer.apple.com/documentation/carplay/cptextbutton) |
| `CPAlertAction` | Button inside alert templates | [Link](https://developer.apple.com/documentation/carplay/cpalertaction) |
| `CPPointOfInterest` | Single POI on map | [Link](https://developer.apple.com/documentation/carplay/cppointofinterest) |
| `CPListItem` | Single row in a list template | [Link](https://developer.apple.com/documentation/carplay/cplistitem) |

## Delegates & Protocols

| Protocol | Purpose |
|----------|---------|
| `CPTemplateApplicationSceneDelegate` | CarPlay scene connection/disconnection |
| `CPInterfaceControllerDelegate` | Template stack changes |
| `CPPointOfInterestTemplateDelegate` | Map region changes, POI selection |
| `CPSessionConfigurationDelegate` | Content style changes (dark/light) |

## Scene Configuration (Info.plist)

For a CarPlay quick-ordering app, add to your `Info.plist`:

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

## Live Activity Integration

| Class/Protocol | Purpose | Docs |
|---------------|---------|------|
| `Activity` | Live Activity instance | [Link](https://developer.apple.com/documentation/activitykit/activity) |
| `ActivityAttributes` | Static data for the activity | [Link](https://developer.apple.com/documentation/activitykit/activityattributes) |
| `WidgetCenter` | Reload widget timelines | [Link](https://developer.apple.com/documentation/widgetkit/widgetcenter) |

## Useful Links

- [CarPlay Framework Overview](https://developer.apple.com/documentation/carplay)
- [Request CarPlay Entitlement](https://developer.apple.com/contact/carplay)
- [Sample Project: Quick-Ordering App](https://docs-assets.developer.apple.com/published/51654e33d2be/IntegratingCarPlayWithYourQuickOrderingApp.zip)
- [Human Interface Guidelines: CarPlay](https://developer.apple.com/design/human-interface-guidelines/carplay)
