# Communication

Communication-related classes for messaging and VoIP apps in CarPlay.


---

# CPMessageComposeBarButton

**Technology:** CarPlay
**Type:** class
**Platforms:** iOS 14.0, iPadOS 14.0, Mac Catalyst 14.0

## Overview
A button that activates Siri and initiates the compose message flow.

## API Reference

### Creating a Message Compose Bar Button
• **init()** - Creates a message compose button with a system-provided image.
• **init(image:)** - Creates a message compose button that displays a custom image.


---

# CPMessageGridItemConfiguration

**Technology:** CarPlay
**Type:** class
**Platforms:** iOS 26.0, iPadOS 26.0, Mac Catalyst 26.0

## Overview


## API Reference

### Initializers
• **init(conversationIdentifier:unread:)** - Initialize a @c CPMessageGridItemConfiguration for use in a @c CPListTemplate.

### Instance Properties
• **conversationIdentifier** -
• **isUnread** -


---

# CPMessageListItemLeadingConfiguration

**Technology:** CarPlay
**Type:** class
**Platforms:** iOS 14.0, iPadOS 14.0, Mac Catalyst 14.0

## Overview
An object that describes the appearance of a message list item's leading region.

## API Reference

### Creating a Configuration
• **init(leadingItem:leadingImage:unread:)** - Creates a leading configuration that contains an item and an image.
• **CPMaximumMessageItemImageSize** - The maximum size of a message list item's image.

### Getting the Leading Item
• **leadingItem** - The configuration's item.
• **CPMessageLeadingItem** - The accessories that a message list item can display in its leading region.

### Getting the Configuration's State
• **leadingImage** - The configuration's image.
• **isUnread** - A Boolean value that determines whether the message list item displays an unread indicator.


---

# CPMessageListItemTrailingConfiguration

**Technology:** CarPlay
**Type:** class
**Platforms:** iOS 14.0, iPadOS 14.0, Mac Catalyst 14.0

## Overview
An object that describes the appearance of a message list item's trailing region.

## API Reference

### Creating a Configuration
• **init(trailingItem:trailingImage:)** - Creates a trailing configuration that contains an item and an image.
• **CPMaximumMessageItemImageSize** - The maximum size of a message list item's image.

### Getting the Trailing Item
• **trailingItem** - The configuration's item.
• **CPMessageTrailingItem** - The accessories that a message list item can display in its trailing region.

### Getting the Trailing Image
• **trailingImage** - The configuration's image.


---

# CPMaximumMessageItemLeadingDetailTextImageSize

**Technology:** CarPlay
**Type:** var
**Platforms:** iOS 12.0, iPadOS 12.0, Mac Catalyst 14.0

## Overview
Maximum size of an image for the detailed text leading image.
