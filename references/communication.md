# CarPlay Communication Apps

Communication apps enable messaging and calling functionality in CarPlay. They integrate with Siri for voice-first interaction to minimize driver distraction.

## Requirements

- Entitlement: `com.apple.developer.carplay-communication`
- iOS 14.0+
- SiriKit integration for messaging/calling

## Message List

### Displaying Messages

```swift
import CarPlay

class CarPlaySceneDelegate: UIResponder, CPTemplateApplicationSceneDelegate {
    var interfaceController: CPInterfaceController?

    func templateApplicationScene(
        _ templateApplicationScene: CPTemplateApplicationScene,
        didConnect interfaceController: CPInterfaceController
    ) {
        self.interfaceController = interfaceController

        let messagesTemplate = createMessagesTemplate()
        interfaceController.setRootTemplate(messagesTemplate, animated: true)
    }

    func createMessagesTemplate() -> CPListTemplate {
        let conversations = loadConversations()

        let items = conversations.map { conversation -> CPMessageListItem in
            let item = CPMessageListItem(
                conversationIdentifier: conversation.id,
                text: conversation.lastMessage,
                leadingConfiguration: CPMessageListItemLeadingConfiguration(
                    leadingItem: .init(conversation.contact.name, style: .identifier),
                    unread: conversation.unreadCount > 0
                ),
                trailingConfiguration: CPMessageListItemTrailingConfiguration(
                    trailingItem: .init(timeString: conversation.timeString)
                ),
                detailText: conversation.contact.name,
                trailingText: conversation.timeString
            )

            return item
        }

        let section = CPListSection(items: items, header: "Messages")
        let template = CPListTemplate(title: "Messages", sections: [section])

        return template
    }
}
```

### Message Item Configuration

```swift
func createMessageItem(for conversation: Conversation) -> CPMessageListItem {
    // Leading configuration (avatar/identifier)
    let leadingConfig = CPMessageListItemLeadingConfiguration(
        leadingItem: .init(conversation.contact.name, style: .identifier),
        unread: conversation.hasUnread
    )

    // Trailing configuration (timestamp)
    let trailingConfig = CPMessageListItemTrailingConfiguration(
        trailingItem: .init(timeString: formatTime(conversation.lastMessageTime))
    )

    let item = CPMessageListItem(
        conversationIdentifier: conversation.id,
        text: conversation.lastMessage,
        leadingConfiguration: leadingConfig,
        trailingConfiguration: trailingConfig,
        detailText: nil,
        trailingText: nil
    )

    return item
}
```

## Contact Integration

### CPContact

```swift
func createContact(from contact: Contact) -> CPContact {
    let cpContact = CPContact(
        name: contact.fullName,
        image: contact.avatar
    )

    // Add phone actions
    let callAction = CPButton(
        title: "Call",
        handler: { button in
            self.initiateCall(to: contact)
        }
    )

    // Add message actions
    let messageAction = CPButton(
        title: "Message",
        handler: { button in
            self.composeMessage(to: contact)
        }
    )

    return cpContact
}
```

### Contact List

```swift
func createContactsTemplate() -> CPListTemplate {
    let contacts = loadContacts()

    let items = contacts.map { contact -> CPListItem in
        let item = CPListItem(
            text: contact.fullName,
            detailText: contact.phoneNumber,
            image: contact.avatar
        )
        item.accessoryType = .disclosureIndicator
        item.handler = { _, completion in
            self.showContactDetail(contact)
            completion()
        }
        return item
    }

    let section = CPListSection(items: items, header: "Contacts")
    return CPListTemplate(title: "Contacts", sections: [section])
}
```

## Siri Integration

### INSendMessageIntent

Communication apps must integrate with SiriKit for voice-controlled messaging:

```swift
import Intents

class IntentHandler: INExtension, INSendMessageIntentHandling {
    func handle(intent: INSendMessageIntent, completion: @escaping (INSendMessageIntentResponse) -> Void) {
        guard let recipients = intent.recipients,
              let content = intent.content else {
            completion(INSendMessageIntentResponse(code: .failure, userActivity: nil))
            return
        }

        // Send the message
        sendMessage(to: recipients, content: content) { success in
            let response = INSendMessageIntentResponse(
                code: success ? .success : .failure,
                userActivity: nil
            )
            completion(response)
        }
    }

    func resolveRecipients(
        for intent: INSendMessageIntent,
        with completion: @escaping ([INSendMessageRecipientResolutionResult]) -> Void
    ) {
        guard let recipients = intent.recipients else {
            completion([.needsValue()])
            return
        }

        let results = recipients.map { recipient -> INSendMessageRecipientResolutionResult in
            // Resolve recipient
            if let contact = findContact(matching: recipient) {
                return .success(with: contact)
            }
            return .unsupported()
        }

        completion(results)
    }
}
```

### INStartCallIntent

```swift
class CallIntentHandler: INExtension, INStartCallIntentHandling {
    func handle(intent: INStartCallIntent, completion: @escaping (INStartCallIntentResponse) -> Void) {
        guard let contacts = intent.contacts else {
            completion(INStartCallIntentResponse(code: .failure, userActivity: nil))
            return
        }

        // Initiate call
        startCall(to: contacts.first) { success in
            let response = INStartCallIntentResponse(
                code: success ? .success : .failure,
                userActivity: nil
            )
            completion(response)
        }
    }
}
```

## Call Management

### CPCallController (Deprecated)

Note: Direct call handling in CarPlay has been deprecated. Use CallKit instead:

```swift
import CallKit

class CallManager: NSObject, CXProviderDelegate {
    let provider: CXProvider
    let callController = CXCallController()

    override init() {
        let config = CXProviderConfiguration()
        config.supportsVideo = false
        config.supportedHandleTypes = [.phoneNumber]

        provider = CXProvider(configuration: config)
        super.init()
        provider.setDelegate(self, queue: nil)
    }

    func startCall(to phoneNumber: String) {
        let handle = CXHandle(type: .phoneNumber, value: phoneNumber)
        let callUUID = UUID()
        let startCallAction = CXStartCallAction(call: callUUID, handle: handle)

        let transaction = CXTransaction(action: startCallAction)
        callController.request(transaction) { error in
            if let error = error {
                print("Failed to start call: \(error)")
            }
        }
    }

    func provider(_ provider: CXProvider, perform action: CXStartCallAction) {
        // Configure audio session
        // Connect to VoIP service
        action.fulfill()
    }

    func provider(_ provider: CXProvider, perform action: CXAnswerCallAction) {
        // Answer incoming call
        action.fulfill()
    }

    func provider(_ provider: CXProvider, perform action: CXEndCallAction) {
        // End call
        action.fulfill()
    }
}
```

## Read Messages with Siri

### Handling Read Requests

```swift
class ReadMessageIntentHandler: INExtension, INSearchForMessagesIntentHandling {
    func handle(
        intent: INSearchForMessagesIntent,
        completion: @escaping (INSearchForMessagesIntentResponse) -> Void
    ) {
        let messages = searchMessages(matching: intent)

        let response = INSearchForMessagesIntentResponse(code: .success, userActivity: nil)
        response.messages = messages.map { message in
            INMessage(
                identifier: message.id,
                conversationIdentifier: message.conversationId,
                content: message.content,
                dateSent: message.date,
                sender: INPerson(
                    personHandle: INPersonHandle(value: message.sender.id, type: .unknown),
                    nameComponents: nil,
                    displayName: message.sender.name,
                    image: nil,
                    contactIdentifier: nil,
                    customIdentifier: nil
                ),
                recipients: nil,
                groupName: nil,
                messageType: .text
            )
        }

        completion(response)
    }
}
```

## Voice Dictation

### Handling Dictated Text

```swift
func handleVoiceDictation(text: String, for conversation: Conversation) {
    // Show confirmation
    let alert = CPAlertTemplate(
        titleVariants: ["Send message?"],
        actions: [
            CPAlertAction(title: "Send", style: .default) { _ in
                self.sendMessage(text, to: conversation)
                self.interfaceController?.dismissTemplate(animated: true)
            },
            CPAlertAction(title: "Cancel", style: .cancel) { _ in
                self.interfaceController?.dismissTemplate(animated: true)
            }
        ]
    )

    interfaceController?.presentTemplate(alert, animated: true)
}
```

## Best Practices

1. **Voice-first design** - Prioritize Siri integration over touch interaction
2. **Minimize reading** - Keep message previews short
3. **Quick replies** - Offer pre-composed response options
4. **Contact disambiguation** - Handle multiple contacts with same name
5. **Offline support** - Queue messages when offline
6. **Privacy** - Never display sensitive content automatically
7. **Audio feedback** - Use audio cues for message sent/received
8. **Test with Siri** - Ensure all voice commands work correctly
