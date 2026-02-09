# IntentsUI Reference

## Table of Contents
1. [Overview](#overview)
2. [Creating UI Extension](#creating-ui-extension)
3. [View Controller Configuration](#view-controller-configuration)
4. [Custom Interface](#custom-interface)
5. [Hiding Default Content](#hiding-default-content)

---

## Overview

IntentsUI allows customizing the Siri and Maps interface when displaying your intent responses.

### When to Use
- Display branded content
- Show rich visualizations
- Replace default Siri interface elements
- Add custom confirmation UI

### Architecture
```
┌─────────────────────────────────────────┐
│              Siri Interface              │
├─────────────────────────────────────────┤
│    Default Header (optional hide)        │
├─────────────────────────────────────────┤
│                                         │
│     Your Custom View Controller         │
│                                         │
├─────────────────────────────────────────┤
│    Default Footer (optional hide)        │
└─────────────────────────────────────────┘
```

---

## Creating UI Extension

### Add Extension Target
1. File → New → Target → Intents UI Extension
2. Name: `YourAppIntentsUI`
3. Language: Swift
4. Automatically added as embedded binary

### Generated Files
```
YourAppIntentsUI/
├── IntentViewController.swift
├── MainInterface.storyboard
└── Info.plist
```

### Info.plist Configuration

```xml
<key>NSExtension</key>
<dict>
    <key>NSExtensionAttributes</key>
    <dict>
        <key>IntentsSupported</key>
        <array>
            <string>OrderSoupIntent</string>
        </array>
    </dict>
    <key>NSExtensionMainStoryboard</key>
    <string>MainInterface</string>
    <key>NSExtensionPointIdentifier</key>
    <string>com.apple.intents-ui-service</string>
</dict>
```

---

## View Controller Configuration

### Basic View Controller

```swift
import IntentsUI

class IntentViewController: UIViewController, INUIHostedViewControlling {
    
    @IBOutlet weak var soupImageView: UIImageView!
    @IBOutlet weak var orderLabel: UILabel!
    @IBOutlet weak var priceLabel: UILabel!
    
    // MARK: - INUIHostedViewControlling
    
    func configureView(for parameters: Set<INParameter>,
                       of interaction: INInteraction,
                       interactiveBehavior: INUIInteractiveBehavior,
                       context: INUIHostedViewContext,
                       completion: @escaping (Bool, Set<INParameter>, CGSize) -> Void) {
        
        guard let intent = interaction.intent as? OrderSoupIntent else {
            completion(false, Set(), .zero)
            return
        }
        
        // Configure your UI
        if let soup = intent.soup {
            orderLabel.text = "Order: \(soup.displayString ?? "")"
            soupImageView.image = UIImage(named: soup.identifier ?? "default")
        }
        
        if let response = interaction.intentResponse as? OrderSoupIntentResponse {
            priceLabel.text = "Total: $\(response.totalPrice ?? 0)"
        }
        
        // Return desired size
        let size = CGSize(width: self.desiredSize.width, height: 200)
        completion(true, parameters, size)
    }
    
    var desiredSize: CGSize {
        let width = self.extensionContext?.hostedViewMaximumAllowedSize.width ?? 320
        return CGSize(width: width, height: 200)
    }
}
```

### Context Types

| Context | When Used |
|---------|-----------|
| `.siri` | Displayed in Siri interface |
| `.mapsCard` | Displayed in Maps card |
| `.lockScreen` | Displayed on Lock Screen |

```swift
func configureView(/* ... */, context: INUIHostedViewContext, /* ... */) {
    switch context {
    case .siri:
        configureForSiri()
    case .mapsCard:
        configureForMaps()
    default:
        break
    }
}
```

---

## Custom Interface

### Per-Parameter Customization

Customize specific parts of the interface:

```swift
func configureView(for parameters: Set<INParameter>,
                   of interaction: INInteraction,
                   /* ... */) {
    
    // Check which parameters to display
    for parameter in parameters {
        switch parameter.parameterKeyPath {
        case "soup":
            configureSoupView(interaction: interaction)
        case "quantity":
            configureQuantityView(interaction: interaction)
        default:
            break
        }
    }
    
    // Return parameters you're handling
    let handledParameters = parameters.filter { 
        ["soup", "quantity"].contains($0.parameterKeyPath)
    }
    completion(true, handledParameters, desiredSize)
}
```

### Interactive Behavior

```swift
func configureView(/* ... */,
                   interactiveBehavior: INUIInteractiveBehavior,
                   /* ... */) {
    
    switch interactiveBehavior {
    case .none:
        // Non-interactive display
        disableInteraction()
    case .nextView:
        // User can tap to continue
        enableTapToContinue()
    case .launch:
        // Tap launches app
        enableTapToLaunch()
    case .genericAction:
        // Generic interaction available
        enableGenericAction()
    @unknown default:
        break
    }
}
```

---

## Hiding Default Content

### INUIHostedViewSiriProviding Protocol

```swift
class IntentViewController: UIViewController, 
                            INUIHostedViewControlling,
                            INUIHostedViewSiriProviding {
    
    // Hide the default Siri confirmation view
    var displaysMessage: Bool {
        return false
    }
    
    // Hide the default payment transaction view
    var displaysPaymentTransaction: Bool {
        return false
    }
    
    // Hide the default map (for ride booking)
    var displaysMap: Bool {
        return false
    }
}
```

### What You Can Hide

| Property | Hides |
|----------|-------|
| `displaysMessage` | Default message/confirmation text |
| `displaysPaymentTransaction` | Payment details card |
| `displaysMap` | Map view in ride booking |

---

## Size Management

### Respecting Maximum Size

```swift
var desiredSize: CGSize {
    guard let maxSize = extensionContext?.hostedViewMaximumAllowedSize else {
        return CGSize(width: 320, height: 200)
    }
    
    // Don't exceed maximum
    let height = min(calculatedHeight, maxSize.height)
    return CGSize(width: maxSize.width, height: height)
}
```

### Dynamic Height

```swift
func configureView(/* ... */, completion: @escaping (Bool, Set<INParameter>, CGSize) -> Void) {
    // Update UI first
    updateLabels()
    
    // Calculate required height
    view.layoutIfNeeded()
    let fittingSize = view.systemLayoutSizeFitting(
        CGSize(width: desiredSize.width, height: UIView.layoutFittingCompressedSize.height),
        withHorizontalFittingPriority: .required,
        verticalFittingPriority: .fittingSizeLevel
    )
    
    completion(true, parameters, fittingSize)
}
```

---

## Storyboard vs Programmatic

### Using Storyboard (Default)
- Design in `MainInterface.storyboard`
- Connect outlets to `IntentViewController`
- Set in Info.plist: `NSExtensionMainStoryboard`

### Programmatic UI

```swift
// Info.plist - replace NSExtensionMainStoryboard with:
// NSExtensionPrincipalClass: $(PRODUCT_MODULE_NAME).IntentViewController

class IntentViewController: UIViewController, INUIHostedViewControlling {
    
    private lazy var stackView: UIStackView = {
        let stack = UIStackView()
        stack.axis = .vertical
        stack.spacing = 8
        return stack
    }()
    
    override func viewDidLoad() {
        super.viewDidLoad()
        setupUI()
    }
    
    private func setupUI() {
        view.addSubview(stackView)
        stackView.translatesAutoresizingMaskIntoConstraints = false
        NSLayoutConstraint.activate([
            stackView.leadingAnchor.constraint(equalTo: view.leadingAnchor, constant: 16),
            stackView.trailingAnchor.constraint(equalTo: view.trailingAnchor, constant: -16),
            stackView.topAnchor.constraint(equalTo: view.topAnchor, constant: 16),
            stackView.bottomAnchor.constraint(lessThanOrEqualTo: view.bottomAnchor, constant: -16)
        ])
    }
}
```
