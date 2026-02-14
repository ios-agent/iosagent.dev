<!--
Downloaded via https://llm.codes by @steipete on February 14, 2026 at 12:35 PM
Source URL: https://developer.apple.com/documentation/appclip
Total pages processed: 34
URLs filtered: No
Content de-duplicated: Yes
Availability strings filtered: No
Code blocks only: No
-->

# https://developer.apple.com/documentation/appclip

Framework

# App Clips

Create a lightweight, in-the-moment experience or demo version for your app that’s instantly available.

iOS 14.0+iPadOS 14.0+

## [Overview](https://developer.apple.com/documentation/appclip\#overview)

An _App Clip_ is a lightweight version of your app that offers access to some of the app’s functionality. For example, a donut shop’s app a person downloads and installs from the App Store may allow them to order donuts, save favorites, collect rewards, get special offers, and so on. The donut shop’s App Clip is instantly available – for example, when someone searches for “donuts” near the shop – without the need to install the full app. To ensure a fast launch experience and a fast order experience, the App Clip offers only the functionality to order donuts.

App Clips that conform to a set of constraints can be larger in size, making it possible to offer an App Clip that’s a demo version of your app. The larger demo size allows people to experience your app’s functionality without a purchase or subscription. For example, a game might offer an App Clip to play the first level, a fitness app might offer an App Clip with a free workout, and so on. When a person has finished the game’s first level or completed the free workout, the App Clip displays a prompt to install the full app.

### [Offer a great user experience](https://developer.apple.com/documentation/appclip\#Offer-a-great-user-experience)

App Clips provide a polished user experience that helps users solve a real-world task as quickly as possible or effortlessly try out a new app. Additionally, App Clips don’t appear on the Home screen, and users don’t manage them the way they manage full apps. Instead, the system removes an App Clip from a device after a period of inactivity, emphasizing the importance of a polished user experience.

### [Review App Clip creation](https://developer.apple.com/documentation/appclip\#Review-App-Clip-creation)

Limit the function of an App Clip to ensure a fast launch experience, protect user privacy, and preserve resources for in-the-moment experiences and demo versions of your app. Before you create an App Clip:

1. Review technology available to App Clips and constraints that ensure a good user experience.

2. Identify which of your app’s functionalities might make a great App Clip.

3. Learn how people discover and launch App Clips with _invocations_ and how you configure App Clip experiences and use invocation URLs to offer a great launch experience.

For more information, refer to [Choosing the right functionality for your App Clip](https://developer.apple.com/documentation/appclip/choosing-the-right-functionality-for-your-app-clip) and [Configuring App Clip experiences](https://developer.apple.com/documentation/appclip/configuring-the-launch-experience-of-your-app-clip).

When you’ve identified functionality for your App Clip and identified invocations:

- Make changes to your app’s Xcode project and your code; for example, add an App Clip target and share code between your App Clip and full app.

- Add code to respond to invocations and to handle invocation URLs.

- Create App Clip experiences in App Store Connect.

- Optionally, associate your App Clip with your website to support additional invocations and advanced App Clip experiences.

- Optionally, create App Clip Codes that offer the best experience for people to discover and launch your App Clip.

## [Topics](https://developer.apple.com/documentation/appclip\#topics)

### [Essentials](https://developer.apple.com/documentation/appclip\#Essentials)

[Choosing the right functionality for your App Clip](https://developer.apple.com/documentation/appclip/choosing-the-right-functionality-for-your-app-clip)

Review frameworks available to App Clips and identify functionality that makes a great App Clip.

[Configuring App Clip experiences](https://developer.apple.com/documentation/appclip/configuring-the-launch-experience-of-your-app-clip)

Review how people launch your App Clip with invocation URLs, default and demo links, and advanced App Clip experiences.

[App Clips updates](https://developer.apple.com/documentation/Updates/AppClips)

Learn about important changes in App Clips.

### [Creation](https://developer.apple.com/documentation/appclip\#Creation)

[Creating an App Clip with Xcode](https://developer.apple.com/documentation/appclip/creating-an-app-clip-with-xcode)

Add an App Clip target to your Xcode project and share code between the App Clip and its corresponding full app.

[Fruta: Building a feature-rich app with SwiftUI](https://developer.apple.com/documentation/appclip/fruta-building-a-feature-rich-app-with-swiftui)

Create a shared codebase to build a multiplatform app that offers widgets and an App Clip.

[`Parent Application Identifiers Entitlement`](https://developer.apple.com/documentation/BundleResources/Entitlements/com.apple.developer.parent-application-identifiers)

A list of parent application identifiers for an App Clip with exactly one entry.

[`com.apple.developer.associated-appclip-app-identifiers`](https://developer.apple.com/documentation/BundleResources/Entitlements/com.apple.developer.associated-appclip-app-identifiers)

A list of App Clip identifiers for an app with exactly one entry.

[`com.apple.developer.on-demand-install-capable`](https://developer.apple.com/documentation/BundleResources/Entitlements/com.apple.developer.on-demand-install-capable)

A Boolean value that indicates whether a bundle represents an App Clip.

### [Launch](https://developer.apple.com/documentation/appclip\#Launch)

[Responding to invocations](https://developer.apple.com/documentation/appclip/responding-to-invocations)

Add code to respond to invocations and offer a focused launch experience.

[Associating your App Clip with your website](https://developer.apple.com/documentation/appclip/associating-your-app-clip-with-your-website)

Enable the system to verify your App Clip to support invocations from your website and devices running iOS 16.3 or earlier.

[Supporting invocations from your website and the Messages app](https://developer.apple.com/documentation/appclip/supporting-invocations-from-your-website-and-the-messages-app)

Display a Smart App Banner and the App Clip card on your website that people tap to launch your App Clip, and add support for invocations from the Messages app.

[Confirming a person’s physical location](https://developer.apple.com/documentation/appclip/confirming-a-person-s-physical-location)

Add code to quickly confirm a person’s physical location while respecting their privacy.

[Launching another app’s App Clip from your app](https://developer.apple.com/documentation/appclip/launching-another-app-s-app-clip-from-your-app)

Enable people to launch another app’s App Clip from your app with App Clip links and offer a rich preview of it with the Link Presentation framework.

[`class APActivationPayload`](https://developer.apple.com/documentation/appclip/apactivationpayload)

Information that’s passed to an App Clip on launch.

[`NSAppClip`](https://developer.apple.com/documentation/BundleResources/Information-Property-List/NSAppClip)

A collection of keys that an App Clip uses to get additional capabilities.

### [App Clip Codes](https://developer.apple.com/documentation/appclip\#App-Clip-Codes)

Help users discover your App Clip by using an NFC-integrated or scan-only App Clip Code.

[Encoding a URL in an App Clip Code](https://developer.apple.com/documentation/appclip/encoding-a-url-in-an-app-clip-code)

Choose an invocation URL for your App Clip Code that you can encode efficiently.

[Preparing multiple App Clip Codes for production](https://developer.apple.com/documentation/appclip/preparing-multiple-app-clip-codes-for-production)

Prepare your App Clip Codes to send to a professional printing service.

[Interacting with App Clip Codes in AR](https://developer.apple.com/documentation/appclip/interacting-with-app-clip-codes-in-ar)

Display content and provide services in an AR experience with App Clip Codes.

### [App Clip to full app transition](https://developer.apple.com/documentation/appclip\#App-Clip-to-full-app-transition)

[Recommending your app to App Clip users](https://developer.apple.com/documentation/appclip/recommending-your-app-to-app-clip-users)

Display an overlay in your App Clip to recommend your app to users.

[Sharing data between your App Clip and your full app](https://developer.apple.com/documentation/appclip/sharing-data-between-your-app-clip-and-your-full-app)

Use CloudKit, Sign in with Apple, shared user defaults or containers, and the keychain to offer a smooth transition from your App Clip to your app.

### [Notifications](https://developer.apple.com/documentation/appclip\#Notifications)

[Enabling notifications in App Clips](https://developer.apple.com/documentation/appclip/enabling-notifications-in-app-clips)

Enable your App Clip to schedule and receive notifications for a short or extended time period.

### [Live Activities](https://developer.apple.com/documentation/appclip\#Live-Activities)

[Offering Live Activities with your App Clip](https://developer.apple.com/documentation/appclip/offering-live-activities-with-your-app-clip)

Add a widget extension to your App Clip target and use ActivityKit to display Live Activities on the Lock Screen and in the Dynamic Island.

### [Testing](https://developer.apple.com/documentation/appclip\#Testing)

[Testing the launch experience of your App Clip](https://developer.apple.com/documentation/appclip/testing-the-launch-experience-of-your-app-clip)

Debug App Clip invocations, test the launch experience, and verify the configuration of your released App Clip.

### [Distribution](https://developer.apple.com/documentation/appclip\#Distribution)

[Distributing your App Clip](https://developer.apple.com/documentation/appclip/distributing-your-app-clip)

Archive the full app for your App Clip, upload it to App Store Connect, and distribute it to testers or publish it on the App Store.

---

# https://developer.apple.com/documentation/appclip/responding-to-invocations

- [App Clips](https://developer.apple.com/documentation/appclip)
- Responding to invocations

Article

# Responding to invocations

Add code to respond to invocations and offer a focused launch experience.

## [Overview](https://developer.apple.com/documentation/appclip/responding-to-invocations\#overview)

A great launch experience that helps the user complete a task quickly is the key to a successful App Clip. Upon launch, your App Clip needs to be aware of the user’s context and update its UI accordingly. For example, an App Clip might provide functionality to order donuts from a local donut shop with multiple physical locations. Instead of making the user select a location before displaying the donut menu, the App Clip recognizes the user’s context and updates its UI accordingly. The user doesn’t have to select a location, and can complete their task — ordering donuts — with fewer taps.

To enable the App Clip to respond to the user’s context upon launch, the system makes the _invocation URL_ available to the App Clip. Configuring the launch experience of your App Clip and choosing invocation URLs are key tasks when creating an App Clip. However, configuring invocation URLs in App Store Connect isn’t enough to provide a streamlined launch experience. You also need to add code to your App Clip that handles the invocation URL and updates its UI.

### [Leveraging the invocation URL](https://developer.apple.com/documentation/appclip/responding-to-invocations\#Leveraging-the-invocation-URL)

Both the App Clip and the full app need to respond to the invocation URL and update their UI to help the user quickly complete their task at hand. Consider the example of a donut shop with multiple physical locations. The user shouldn’t have to select the location that matches their context before they can order pastries. Instead, the App Clip can make use of the invocation URL to update its UI to display the shop’s menu right away. For example, use an invocation URL with additional URL parameters that help the App Clip recognize the user’s context and update its UI:

1. If you don’t use the default App Clip link that App Store Connect generates for a default experience, add entries for each domain that launches the App Clip to the [`Associated Domains Entitlement`](https://developer.apple.com/documentation/BundleResources/Entitlements/com.apple.developer.associated-domains). For the example described above, you add `example.com`. You typically do this when you add an App Clip target to your Xcode project.

2. Use invocation URLs that contain additional parameters; for example, `https://example.com/location1`, `https://example.com/location2`, and so on.

3. On launch, respond to the URLs by persisting any unsaved data in case the user switches from one location to another. Then, update the UI to match the new location.

If you configure a generic URL, both your App Clip and your full app must always be able to handle the URL, even if you only intend to use it as a prefix for your actual invocation URLs. For example, you can register `https://example.com/` as part of an advanced App Store experience. For the actual invocations — such as in your App Clip Codes — you can use URLs like `https://example.com/location1` or `https://example.com/location2`. However, your App Clip and full app must also be able to handle `https://example.com`.

For additional information on associating your App Clip with your website and configuring experiences, refer to [Associating your App Clip with your website](https://developer.apple.com/documentation/appclip/associating-your-app-clip-with-your-website) and [Configuring App Clip experiences](https://developer.apple.com/documentation/appclip/configuring-the-launch-experience-of-your-app-clip).

### [Access the invocation URL](https://developer.apple.com/documentation/appclip/responding-to-invocations\#Access-the-invocation-URL)

To respond to an invocation, you need to access the invocation URL so your App Clip can tailor itself to the experience. To access the URL, query the [`NSUserActivity`](https://developer.apple.com/documentation/Foundation/NSUserActivity) object the system passes to the App Clip upon launch. If a user installs the full app, it replaces the App Clip, and the system launches it with each invocation. To offer the same functionality and provide an equivalent user experience as the App Clip, the full app also needs to handle all invocation URLs. In most cases, it makes sense to share the code that handles your URL between full app and App Clip, and also have the App Clip store state information in a shared container. This way, the full app can access any data stored by the App Clip, and, upon launch, take the user to the part of the app that best matches their context.

To access the [`NSUserActivity`](https://developer.apple.com/documentation/Foundation/NSUserActivity) object on launch:

- If you use the SwiftUI lifecycle, apply the [`onContinueUserActivity(_:perform:)`](https://developer.apple.com/documentation/SwiftUI/View/onContinueUserActivity(_:perform:)) modifier. For additional information on implementing lifecycle callbacks for your SwiftUI app, refer to [Restoring your app’s state with SwiftUI](https://developer.apple.com/documentation/SwiftUI/restoring-your-app-s-state-with-swiftui).

- If you use a scene-based lifecycle, implement the [`scene(_:willConnectTo:options:)`](https://developer.apple.com/documentation/UIKit/UISceneDelegate/scene(_:willConnectTo:options:)) and [`scene(_:willContinueUserActivityWithType:)`](https://developer.apple.com/documentation/UIKit/UISceneDelegate/scene(_:willContinueUserActivityWithType:)) callbacks. On the first launch, the system calls the [`scene(_:willConnectTo:options:)`](https://developer.apple.com/documentation/UIKit/UISceneDelegate/scene(_:willConnectTo:options:)) callback. If the app or App Clip is suspended in memory and the user launches it, the system calls [`scene(_:willContinueUserActivityWithType:)`](https://developer.apple.com/documentation/UIKit/UISceneDelegate/scene(_:willContinueUserActivityWithType:)).

- If you use the [`UIApplicationDelegate`](https://developer.apple.com/documentation/UIKit/UIApplicationDelegate) object to respond to lifecycle events, be sure to implement the [`application(_:continue:restorationHandler:)`](https://developer.apple.com/documentation/UIKit/UIApplicationDelegate/application(_:continue:restorationHandler:)) callback. Note that you don’t have access to the [`NSUserActivity`](https://developer.apple.com/documentation/Foundation/NSUserActivity) object in [`application(_:didFinishLaunchingWithOptions:)`](https://developer.apple.com/documentation/UIKit/UIApplicationDelegate/application(_:didFinishLaunchingWithOptions:)).

On launch, confirm that the invocation is of type [`NSUserActivityTypeBrowsingWeb`](https://developer.apple.com/documentation/Foundation/NSUserActivityTypeBrowsingWeb), then access the URL that the system passes to the App Clip. The following code shows a function that extracts components from the invocation URL:

func respondTo(_ activity: NSUserActivity?) {

// Guard against faulty data.
guard let activity, activity.activityType == NSUserActivityTypeBrowsingWeb else { return }
let incomingURL = activity.webpageURL
guard let components = NSURLComponents(url: incomingURL, resolvingAgainstBaseURL: true) else { return }

// Update the user interface based on URL components passed to the App Clip or full app.
}

For more information about responding to lifecycle events, refer to [Managing your app’s life cycle](https://developer.apple.com/documentation/UIKit/managing-your-app-s-life-cycle). For general information on handling links, refer to [Supporting universal links in your app](https://developer.apple.com/documentation/Xcode/supporting-universal-links-in-your-app).

To learn more about sharing data between the App Clip and the full app, refer to [Sharing data between your App Clip and your full app](https://developer.apple.com/documentation/appclip/sharing-data-between-your-app-clip-and-your-full-app).

### [Ensure your code handles all invocations](https://developer.apple.com/documentation/appclip/responding-to-invocations\#Ensure-your-code-handles-all-invocations)

A fast, consistent user experience that fits the user’s context is key to the App Clip user experience, and it’s why designing and configuring your App Clip experiences is so important. As a result, spending time to write resilient code, handling all possible invocation URLs, and testing the code is key. Make sure you guard against faulty data and handle the following scenarios:

- Invocations from the Maps app and location-based suggestions from Siri Suggestions use the URL you register for an App Clip experience as the invocation URL.

- Invocations from Messages app or your website use the site’s URL as the invocation URL.

- If a user returns to a previously launched App Clip from the App Library or Spotlight, the App Clip uses the invocation URL that it previously used to launch the App Clip.

- If a user returns to a previously launched App Clip from a notification or the App Switcher, the App Clip launches without an invocation URL. To address this case, save the state of your App Clip before the user leaves it, and restore the saved state if the invocation URL isn’t available upon launch.

For more information on verifying invocation URLs, refer to [Testing the launch experience of your App Clip](https://developer.apple.com/documentation/appclip/testing-the-launch-experience-of-your-app-clip).

## [See Also](https://developer.apple.com/documentation/appclip/responding-to-invocations\#see-also)

### [Launch](https://developer.apple.com/documentation/appclip/responding-to-invocations\#Launch)

[Associating your App Clip with your website](https://developer.apple.com/documentation/appclip/associating-your-app-clip-with-your-website)

Enable the system to verify your App Clip to support invocations from your website and devices running iOS 16.3 or earlier.

[Supporting invocations from your website and the Messages app](https://developer.apple.com/documentation/appclip/supporting-invocations-from-your-website-and-the-messages-app)

Display a Smart App Banner and the App Clip card on your website that people tap to launch your App Clip, and add support for invocations from the Messages app.

[Confirming a person’s physical location](https://developer.apple.com/documentation/appclip/confirming-a-person-s-physical-location)

Add code to quickly confirm a person’s physical location while respecting their privacy.

[Launching another app’s App Clip from your app](https://developer.apple.com/documentation/appclip/launching-another-app-s-app-clip-from-your-app)

Enable people to launch another app’s App Clip from your app with App Clip links and offer a rich preview of it with the Link Presentation framework.

[`class APActivationPayload`](https://developer.apple.com/documentation/appclip/apactivationpayload)

Information that’s passed to an App Clip on launch.

[`NSAppClip`](https://developer.apple.com/documentation/BundleResources/Information-Property-List/NSAppClip)

A collection of keys that an App Clip uses to get additional capabilities.

---

# https://developer.apple.com/documentation/appclip/configuring-the-launch-experience-of-your-app-clip

- [App Clips](https://developer.apple.com/documentation/appclip)
- Configuring App Clip experiences

Article

# Configuring App Clip experiences

Review how people launch your App Clip with invocation URLs, default and demo links, and advanced App Clip experiences.

## [Overview](https://developer.apple.com/documentation/appclip/configuring-the-launch-experience-of-your-app-clip\#overview)

People launch your App Clip by performing an _invocation_ — for example, by scanning an App Clip Code or tapping a Smart App Banner on a website. Upon launch, the App Clip receives an _invocation URL_ that determines what information appears on the App Clip card. To offer the best launch experience for a person’s current context, use the invocation URL on launch to update the UI of your App Clip.

To configure invocation URLs and the metadata that appears on the App Clip card, create the required _default App Clip experience_ in [App Store Connect](https://appstoreconnect.apple.com/login). For more advanced use cases — for example, to associate an App Clip with a physical location or to create an App Clip for multiple businesses — configure optional _advanced App Clip experiences_.

The actual configuration of your App Clip experiences typically happens when you upload the first build that contains an App Clip to App Store Connect. However, it’s important to understand how App Clip experiences work before you start developing your App Clip. Identify invocations and invocation URLs, and plan changes to your code before or in parallel with the implementation of your App Clip. Additionally, to support advanced App Clip experiences or iOS versions older than iOS 16.4, you need to make changes to your server to associate your App Clip with your website.

### [Review how people invoke an App Clip](https://developer.apple.com/documentation/appclip/configuring-the-launch-experience-of-your-app-clip\#Review-how-people-invoke-an-App-Clip)

People don’t search the App Store for an App Clip. They discover it when and where they need it, and launch the App Clip by performing one of the following invocations:

- Scanning an App Clip Code, NFC tag, or QR code at a physical location

- Tapping a location-based suggestion from Siri Suggestions

- Tapping a link in the Maps app

- Tapping a Smart App Banner on a website in Safari or an app that uses [`SFSafariViewController`](https://developer.apple.com/documentation/SafariServices/SFSafariViewController)

- Tapping the action button of an App Clip card that appears in Safari or an [`SFSafariViewController`](https://developer.apple.com/documentation/SafariServices/SFSafariViewController) (requires iOS 15 or later)

- Tapping a link that someone shares in the Messages app (as a text message only)

- Tapping an App Clip preview or link to an App Clip in another app (requires iOS 17 or later)

- Tapping a link to an App Clip in an email or on a website

With each invocation, the system verifies whether the invocation URL matches the invocation URL in App Store Connect. After it verifies the invocation, the system uses the invocation URL to determine which App Clip experience to use for launching your App Clip. It then uses the App Clip experience’s metadata to populate the App Clip card and passes the invocation URL to the App Clip.

### [Choose App Clip experiences you want to support](https://developer.apple.com/documentation/appclip/configuring-the-launch-experience-of-your-app-clip\#Choose-App-Clip-experiences-you-want-to-support)

No matter which invocation method you want to support, you need to create a default App Clip experience in [App Store Connect](https://appstoreconnect.apple.com/login). With a default App Clip experience, App Store Connect generates a default App Clip link that supports common invocations, without requiring any changes to your server. For some App Clips, this default experience and the default App Clip link may be enough to provide their functionality.

However, your App Clip might benefit from using a custom link for your default experience, or the generated App Clip demo link. Additionally, depending on the functionality your app and App Clip provide, you may need to configure advanced App Clip experiences in addition to the default App Clip experience.

The following table shows the invocations each experience and link type supports:

| Invocations and URL constraints | Default App Clip experience with default link | Default App Clip experience with an associated website | App Clip demo link | Advanced App Clip experience |
| --- | --- | --- | --- | --- |
| A Smart App Banner or the App Clip card on your website | No | Yes | No | Yes, if you associate your website with the App Clip. |
| A shared link to an App Clip in the Messages app | Yes | Yes | Yes, with a limited preview. | Yes, if you associate your website with the App Clip. |
| QR codes | Yes | Yes | Yes | Yes |
| NFC tags | Yes | Yes | Yes | Yes |
| App Clip Codes | No | No | Yes, if you use the short version of the demo link. | Yes |
| Maps | No | No | No | Yes |
| Spotlight search | Yes, excluding location-based Spotlight suggestions. | Yes, excluding location-based Spotlight suggestions. | Yes, excluding location-based Spotlight suggestions. | Yes |
| Another app that uses [Link Presentation](https://developer.apple.com/documentation/LinkPresentation) | Yes | Yes | Yes | Yes |
| Another app that uses [`Link`](https://developer.apple.com/documentation/SwiftUI/Link) or [`open(_:options:completionHandler:)`](https://developer.apple.com/documentation/UIKit/UIApplication/open(_:options:completionHandler:)) | Yes | Yes | Yes | No |
| Supports URL parameters | Yes | Yes | No | Yes |

If you don’t have a website for your app or don’t want to support invocations that require an associated website, configure the default experience and use the default link for your invocations. If you support iOS 16.3 and earlier or want to support additional invocations, including showing an App Clip card on your website, associate your website with your App Clip.

You can use the generated demo URL to offer a demo version of your app that launches from physical and digital experiences. Note that the demo URL doesn’t replace the default App Clip experience. It allows you to use the default App Clip experience, support digital and physical invocations, and create an App Clip with a larger uncompressed binary size. For more information, see [Keep your App Clip within size limitations](https://developer.apple.com/documentation/appclip/choosing-the-right-functionality-for-your-app-clip#Keep-your-App-Clip-within-size-limitations).

Configure an advanced App Clip experience if:

- You want your App Clip to support all possible invocations on devices that run iOS 16.3 and earlier.

- You want to display a Smart App Banner and an App Clip card on an additional website that uses a different subdomain or domain.

- You need to associate your App Clip with a physical location.

- You create an App Clip for multiple businesses to use.

### [Configure a default App Clip experience](https://developer.apple.com/documentation/appclip/configuring-the-launch-experience-of-your-app-clip\#Configure-a-default-App-Clip-experience)

An App Clip always requires a corresponding full app, and you submit your App Clip binary together with your full app’s binary to [App Store Connect](https://appstoreconnect.apple.com/login). After you’ve uploaded your full app to App Store Connect, configure a default App Clip experience. Navigate to the page for the app version that offers an App Clip, expand the App Clip section, and provide the following metadata for the App Clip card:

- A header image

- Copy for the App Clip card’s subtitle

- The call-to-action verb that appears on the Action button people tap to launch the App Clip

For your default App Clip experience, the invocation URL that’s available to the App Clip on launch can be:

- The default App Clip link that the system generates for you for your default App Clip experience

- The App Clip demo link that the system generates for you

- The URL of the website you associated with the App Clip and that displays the Smart App Banner and the App Clip card

### [Choose invocation URLs for your default experience](https://developer.apple.com/documentation/appclip/configuring-the-launch-experience-of-your-app-clip\#Choose-invocation-URLs-for-your-default-experience)

App Store Connect generates an App Clip demo link when you configure the default App Clip experience. With the demo link, you can offer an App Clip that’s a demo version of your app. Its uncompressed App Clip binary can be larger in size and supports all invocations, including physical invocations. However, App Clip demo links can’t contain URL parameters.

The default and demo App Clip links offer functionality without changes to your server. However, associating your App Clip with your website and making changes to your server comes with benefits: The website can display a Smart App Banner or the App Clip card. For example, a shop might associate its App Clip with its website on https://example.com. To launch the App Clip, the website displays a Smart App Banner at various locations, for example:

- `https://example.com/menu`

- `https://example.com/contact`

- `https://example.com/menu/breakfast`

- `https://example.com/menu/lunch`

The website also displays the App Clip card on `https://appclip.example.com/,` a dedicated page that promotes the App Clip. Upon launch, the App Clip receives the website’s URL as the invocation URL and displays the functionality in the App Clip that matches the URL — for example, the coffee shop’s lunch menu.

For additional information about associating your App Clip with your website, refer to [Associating your App Clip with your website](https://developer.apple.com/documentation/appclip/associating-your-app-clip-with-your-website).

### [Customize the App Clip card](https://developer.apple.com/documentation/appclip/configuring-the-launch-experience-of-your-app-clip\#Customize-the-App-Clip-card)

The App Clip card is the first thing people see when they discover your App Clip, which makes the App Clip card’s design especially important. To explore different imagery and text, and to test their appearance on your device, use local experiences as described in [Testing the launch experience of your App Clip](https://developer.apple.com/documentation/appclip/testing-the-launch-experience-of-your-app-clip).

An effective App Clip card matches a person’s context. For example, a business with multiple physical locations might display imagery that matches the person’s current location. Each physical location might correspond to a different image and text on the App Clip card. However, it’s not possible to programmatically change the content on the App Clip card. Instead, configure an advanced App Clip experience in App Store Connect for each context that needs its own App Clip card. You can choose text and imagery for each advanced App Clip experience.

You can also localize the text that appears on the App Clip card in App Store Connect. For more information on localization, refer to [Localize App Store Information](https://help.apple.com/app-store-connect/#/deve6f78a8e2).

### [Configure advanced App Clip experiences](https://developer.apple.com/documentation/appclip/configuring-the-launch-experience-of-your-app-clip\#Configure-advanced-App-Clip-experiences)

To support additional invocations (for example, from scanning an App Clip Code), create an advanced App Clip experience in [App Store Connect](https://appstoreconnect.apple.com/login).

In App Store Connect, select your App, and then select the iOS app version for which you want to add an advanced App Clip experience. Then, click Edit Advanced Experiences and create an advanced App Clip experience. For more information, refer to [Set up an App Clip experience](https://help.apple.com/app-store-connect/#/dev43c15c696) in the App Store Connect Help.

In your Xcode project, add or modify code for both your App Clip and your full app to respond to the new URL you registered. For more information, refer to [Responding to invocations](https://developer.apple.com/documentation/appclip/responding-to-invocations).

Consider the previous example for a coffee shop’s App Clip: It would use the default App Clip experience with `https://example.com` because that’s the domain associated with the App Clip. In addition, it would use one advanced App Clip experience with `https://example.com` as its invocation URL, and generate an App Clip Code for the advanced App Clip experience. In its code, the App Clip handles the invocation from an App Clip Code just like an invocation from Smart App Banners, the App Clip card on a website, and the Messages app.

### [Take advantage of URL prefix matching](https://developer.apple.com/documentation/appclip/configuring-the-launch-experience-of-your-app-clip\#Take-advantage-of-URL-prefix-matching)

In general, try to register as few URLs as possible, and register generic URLs to take advantage of _URL prefix matching_. Upon invocation, the system matches the invocation URL against URLs you registered as part of your advanced App Clip experiences. The system then chooses the App Clip experience with the URL that has the most specific matching prefix. This means that you can register one URL to cover many cases.

Consider the example for a coffee shop. By registering one advanced App Clip experience with `https://example.com` as its invocation URL, it’s possible to handle invocation URLs, for example:

Upon launch, the App Clip receives a URL, then extracts path components and query parameters and uses them to update its UI so that it corresponds to the URL and matches the person’s context.

If the coffee shop has multiple physical locations, its App Clip could use one advanced App Clip experience for each location with a different header image, metadata, and invocation URL — for example, `https://example.com/location1`, `https://example.com/location2`, and so on. The App Clip could then, similar to the previous example, extract path components and query parameters to update its UI for each App Clip experience.

For additional information, refer to [WWDC20: Configure and Link Your App Clips](https://developer.apple.com/wwdc20/10146).

### [Choose URLs to encode in an App Clip Code](https://developer.apple.com/documentation/appclip/configuring-the-launch-experience-of-your-app-clip\#Choose-URLs-to-encode-in-an-App-Clip-Code)

An App Clip Code is immediately recognizable to people and lets them know that an App Clip is available. The App Clip Code offers a fast and secure launch experience for your App Clip that people trust. Although App Clip Codes are a great way to launch your App Clip, an App Clip Code can only contain a limited amount of information in its visual code or NFC tag. If you plan to support invocations from App Clip Codes, refer to [Creating App Clip Codes](https://developer.apple.com/documentation/appclip/creating-app-clip-codes) and [Encoding a URL in an App Clip Code](https://developer.apple.com/documentation/appclip/encoding-a-url-in-an-app-clip-code).

### [Use short URLs or redirects](https://developer.apple.com/documentation/appclip/configuring-the-launch-experience-of-your-app-clip\#Use-short-URLs-or-redirects)

In some cases — for example, if you already use shortened URLs to deep link into your app — you may want to launch your App Clip from a short URL in addition to a long URL. In other cases, you may want to redirect from the short URL to a URL with a long path or many query parameters.

You may create both short and long URLs, as well as make URL redirects to launch App Clips. However, you need to set up both the short URL and the long URL to invoke your App Clip. For example, you may want to use `https://some.subdomain.example.com/path/to/thing?query=1234` as the invocation URL for your App Clip and a shorter URL — for example, `https://appclip.example.com?id=1` — that redirects to the long URL. For the URL forwarding to work, add both `https://some.subdomain.example.com` and `https://appclip.example.com` to your list of associated domains. Make sure to place an AASA file into the corresponding `.well-known` directory for each subdomain. Then, create App Clip experiences for both URLs.

For additional information, refer to [Associating your App Clip with your website](https://developer.apple.com/documentation/appclip/associating-your-app-clip-with-your-website) and [Supporting associated domains](https://developer.apple.com/documentation/Xcode/supporting-associated-domains).

### [Creating App Clip experiences using the App Store Connect API](https://developer.apple.com/documentation/appclip/configuring-the-launch-experience-of-your-app-clip\#Creating-App-Clip-experiences-using-the-App-Store-Connect-API)

The App Store Connect website offers a convenient way to create and manage your default and advanced App Clip experiences. However, if you need to manage a large number of App Clip experiences, using the website may be too cumbersome. For example, say your App Clip allows people to order food at a chain restaurant with dozens, hundreds, or even thousands of locations. For each location, you likely want to display imagery on the App Clip card for that specific restaurant. As a result, you need to create an advanced App Clip experience for each location.

To help you create and manage a large number of App Clip experiences, use the App Store Connect API to automate these tasks. For more information, refer to [App Clips and App Clip Experiences](https://developer.apple.com/documentation/AppStoreConnectAPI/app-clips-and-app-clip-experiences).

## [See Also](https://developer.apple.com/documentation/appclip/configuring-the-launch-experience-of-your-app-clip\#see-also)

### [Essentials](https://developer.apple.com/documentation/appclip/configuring-the-launch-experience-of-your-app-clip\#Essentials)

[Choosing the right functionality for your App Clip](https://developer.apple.com/documentation/appclip/choosing-the-right-functionality-for-your-app-clip)

Review frameworks available to App Clips and identify functionality that makes a great App Clip.

[App Clips updates](https://developer.apple.com/documentation/Updates/AppClips)

Learn about important changes in App Clips.

---

# https://developer.apple.com/documentation/appclip/launching-another-app-s-app-clip-from-your-app

- [App Clips](https://developer.apple.com/documentation/appclip)
- Launching another app’s App Clip from your app

Article

# Launching another app’s App Clip from your app

Enable people to launch another app’s App Clip from your app with App Clip links and offer a rich preview of it with the Link Presentation framework.

## [Overview](https://developer.apple.com/documentation/appclip/launching-another-app-s-app-clip-from-your-app\#overview)

Starting with iOS 17, an app can launch another app’s App Clip using the invocation URL of the App Clip. For example, if you develop several apps, your apps can launch your other apps’ App Clips to allow people to use their functionality without requiring an app installation. Or, your app could offer to launch another developer’s App Clip if your app offers workflows that involve usage of the other app. Depending on the App Clip and its invocation URL, choose from the following options to allow people to invoke an App Clip from your app:

- To display a rich preview and allow people to launch default or advanced App Clip experiences, use the [Link Presentation](https://developer.apple.com/documentation/LinkPresentation) framework.

- To allow people to launch a default App Clip experience that makes use of the autogenerated default App Clip link, use [`Link`](https://developer.apple.com/documentation/SwiftUI/Link) or [`open(_:options:completionHandler:)`](https://developer.apple.com/documentation/UIKit/UIApplication/open(_:options:completionHandler:)).

### [Display a preview of the App Clip](https://developer.apple.com/documentation/appclip/launching-another-app-s-app-clip-from-your-app\#Display-a-preview-of-the-App-Clip)

Use the [Link Presentation](https://developer.apple.com/documentation/LinkPresentation) framework to include a rich preview of the App Clip in your app that people tap to launch the App Clip directly:

1. To fetch metadata using the invokation URL of the App Clip, use [`LPMetadataProvider`](https://developer.apple.com/documentation/LinkPresentation/LPMetadataProvider).

2. To display the App Clip preview, use the metadata you receive in an [`LPLinkView`](https://developer.apple.com/documentation/LinkPresentation/LPLinkView).

The following example fetches the metadata and then passes it to a link view.

let provider = LPMetadataProvider()
let url = URL(string: "https://appclip.example.com/")!
var linkView = ... // A reference to the link view. This could also be a custom view that contains the LPLinkView.

provider.startFetchingMetadata(for: url) { (metadata, error) in
guard let metadata = metadata else {
// The fetch failed; handle the error.
return
}

DispatchQueue.main.async {
// Create the LPLinkView using the metadata. If you use a custom view, you could pass the metadata to the custom view and let it handle the creation or formatting of the LPLinkView.
linkView = LPLinkView(metadata: metadata)
}
}

### [Display a direct link to an App Clip](https://developer.apple.com/documentation/appclip/launching-another-app-s-app-clip-from-your-app\#Display-a-direct-link-to-an-App-Clip)

If the App Clip uses the default App Clip link for its default App Clip experience, you can display a direct link that launches the App Clip. In a [SwiftUI](https://developer.apple.com/documentation/SwiftUI) app, use [`Link`](https://developer.apple.com/documentation/SwiftUI/Link) as shown in the following example that displays a link to the [Backyard Birds: Building an app with SwiftData and widgets](https://developer.apple.com/documentation/SwiftUI/Backyard-birds-sample) app:

var body: some View {
let appClipURL = URL(
string: "https://appclip.apple.com/id?p=com.example.naturelab.backyardbirds.Clip"
)!

Link("Backyard Birds", destination: appClipURL)
}

If you use UIKit, use [`open(_:options:completionHandler:)`](https://developer.apple.com/documentation/UIKit/UIApplication/open(_:options:completionHandler:)) to allow people to invoke the App Clip:

func launchAppClip() {
let appClipURL = URL(
string: "https://appclip.apple.com/id?p=com.example.naturelab.backyardbirds.Clip"
)!

UIApplication.shared.open(appClipURL)
}

## [See Also](https://developer.apple.com/documentation/appclip/launching-another-app-s-app-clip-from-your-app\#see-also)

### [Launch](https://developer.apple.com/documentation/appclip/launching-another-app-s-app-clip-from-your-app\#Launch)

[Responding to invocations](https://developer.apple.com/documentation/appclip/responding-to-invocations)

Add code to respond to invocations and offer a focused launch experience.

[Associating your App Clip with your website](https://developer.apple.com/documentation/appclip/associating-your-app-clip-with-your-website)

Enable the system to verify your App Clip to support invocations from your website and devices running iOS 16.3 or earlier.

[Supporting invocations from your website and the Messages app](https://developer.apple.com/documentation/appclip/supporting-invocations-from-your-website-and-the-messages-app)

Display a Smart App Banner and the App Clip card on your website that people tap to launch your App Clip, and add support for invocations from the Messages app.

[Confirming a person’s physical location](https://developer.apple.com/documentation/appclip/confirming-a-person-s-physical-location)

Add code to quickly confirm a person’s physical location while respecting their privacy.

[`class APActivationPayload`](https://developer.apple.com/documentation/appclip/apactivationpayload)

Information that’s passed to an App Clip on launch.

[`NSAppClip`](https://developer.apple.com/documentation/BundleResources/Information-Property-List/NSAppClip)

A collection of keys that an App Clip uses to get additional capabilities.

---

# https://developer.apple.com/documentation/appclip/choosing-the-right-functionality-for-your-app-clip

- [App Clips](https://developer.apple.com/documentation/appclip)
- Choosing the right functionality for your App Clip

Article

# Choosing the right functionality for your App Clip

Review frameworks available to App Clips and identify functionality that makes a great App Clip.

## [Overview](https://developer.apple.com/documentation/appclip/choosing-the-right-functionality-for-your-app-clip\#overview)

An App Clip is a lightweight version of your app that offers some of its functionality when and where it’s needed, or gives people a way to try a demo version of your app. App Clips offer a focused feature set, and are designed to launch instantly, protect user privacy, and preserve resources. As a result, an App Clip comes with some limitations. Before you create your App Clip, first review the technology available, and identify the functionality that makes a great App Clip.

### [Keep your App Clip within size limitations](https://developer.apple.com/documentation/appclip/choosing-the-right-functionality-for-your-app-clip\#Keep-your-App-Clip-within-size-limitations)

To ensure a fast launch experience, App Clips must be small. Aim to keep your App Clip binary well below the applicable limit:

| iOS version | Maximum size of the uncompressed App Clip binary |
| --- | --- |
| iOS 15 and earlier | 10 MB |
| iOS 16 and earlier | 15 MB |
| iOS 17 and later | 100 MB, with additional requirements and limitations (see below) |

On devices running iOS 17 and later, the uncompressed App Clip binary can be up to 100 MB in size if you meet the following conditions:

- The App Clip only supports digital invocations — for example, from your website or Spotlight search.

- The App Clip doesn’t support physical invocations such as App Clip Codes, QR codes, or NFC tags.

- People use your App Clip in situations where a reliable internet connection is likely; for example, at home.

- Your App Clip doesn’t support iOS 16 and earlier.

Additionally, you can use the App Clip demo link that App Store Connect generates to use the 100 MB size limit and support physical invocations from App Clip Codes, NFC tags, and QR codes.

For more information, refer to [Configuring App Clip experiences](https://developer.apple.com/documentation/appclip/configuring-the-launch-experience-of-your-app-clip) and [Verify the size of your App Clip](https://developer.apple.com/documentation/appclip/creating-an-app-clip-with-xcode#Verify-the-size-of-your-App-Clip).

If your App Clip needs to download additional assets; for example, if you offer a demo version of your game; use [Background Assets](https://developer.apple.com/documentation/BackgroundAssets) to download additional assets. For more information, refer to [Download additional assets](https://developer.apple.com/documentation/appclip/creating-an-app-clip-with-xcode#Download-additional-assets).

### [Review available frameworks and APIs](https://developer.apple.com/documentation/appclip/choosing-the-right-functionality-for-your-app-clip\#Review-available-frameworks-and-APIs)

App Clips make use of [SwiftUI](https://developer.apple.com/documentation/SwiftUI) and [UIKit](https://developer.apple.com/documentation/UIKit), and have access to the same frameworks as your full app. However, the following frameworks provide no functionality at runtime: [App Intents](https://developer.apple.com/documentation/AppIntents), [Assets Library](https://developer.apple.com/documentation/AssetsLibrary), [Background Tasks](https://developer.apple.com/documentation/BackgroundTasks), [CallKit](https://developer.apple.com/documentation/CallKit), [CareKit](https://www.researchandcare.org/) [Contacts](https://developer.apple.com/documentation/Contacts), [Contacts UI](https://developer.apple.com/documentation/ContactsUI), [Core Motion](https://developer.apple.com/documentation/CoreMotion), [EventKit](https://developer.apple.com/documentation/EventKit), [EventKit UI](https://developer.apple.com/documentation/EventKitUI), [File Provider](https://developer.apple.com/documentation/FileProvider), [File Provider UI](https://developer.apple.com/documentation/FileProviderUI), [HealthKit](https://developer.apple.com/documentation/HealthKit), [HomeKit](https://developer.apple.com/documentation/HomeKit), [Media Player](https://developer.apple.com/documentation/MediaPlayer), [Messages](https://developer.apple.com/documentation/Messages), [Message UI](https://developer.apple.com/documentation/MessageUI), [Nearby Interaction](https://developer.apple.com/documentation/NearbyInteraction), [PhotoKit](https://developer.apple.com/documentation/PhotoKit), [ResearchKit](https://www.researchandcare.org/), [SensorKit](https://developer.apple.com/documentation/SensorKit), and [Speech](https://developer.apple.com/documentation/Speech).

For most unavailable frameworks, using them in an App Clip doesn’t result in compile-time errors, but their APIs return values that indicate unavailability, empty data, or error codes at runtime. For example, HealthKit’s [`isHealthDataAvailable()`](https://developer.apple.com/documentation/HealthKit/HKHealthStore/isHealthDataAvailable()) returns `false` when you call it from an App Clip.

App Clips can’t perform background activity. For example, they can’t make use of:

- Background networking with [`URLSession`](https://developer.apple.com/documentation/Foundation/URLSession)

- Functionality enabled by the Background Modes capability as described in [Pushing background updates to your App](https://developer.apple.com/documentation/UserNotifications/pushing-background-updates-to-your-app)

- The ability to maintain Bluetooth connections while the App Clip isn’t in use

Some frameworks are available to App Clips but offer only limited functionality, or using them requires special consideration:

Advanced networking features and low-level networking APIs

Advanced networking features like [Bonjour](https://developer.apple.com/documentation/Foundation/bonjour) and low-level networking APIs like [`CFSocket`](https://developer.apple.com/documentation/CoreFoundation/CFSocket) or POSIX functions aren’t available to App Clips. Instead, use [`URLSession`](https://developer.apple.com/documentation/Foundation/URLSession) or the [Network](https://developer.apple.com/documentation/Network) framework.

App extensions

App Clips can’t include app extensions, but they can include a widget extension to offer Live Activities. For more information, refer to [Offering Live Activities with your App Clip](https://developer.apple.com/documentation/appclip/offering-live-activities-with-your-app-clip).

[Core Telephony](https://developer.apple.com/documentation/CoreTelephony)

Functionality provided by [Core Telephony](https://developer.apple.com/documentation/CoreTelephony) is available to App Clips. However, they can’t provision cellular plan eSIMs or use functionality that carrier apps with suitable entitlements use. For example, an App Clip can’t use [`CTCellularPlanProvisioning`](https://developer.apple.com/documentation/CoreTelephony/CTCellularPlanProvisioning) and [`CTCellularPlanProvisioningRequest`](https://developer.apple.com/documentation/CoreTelephony/CTCellularPlanProvisioningRequest).

[CloudKit](https://developer.apple.com/documentation/CloudKit)

[CloudKit](https://developer.apple.com/documentation/CloudKit) isn’t available to App Clips in iOS 14 or 15. Starting with iOS 16, App Clips can read their public iCloud database. However, App Clips can’t write data to a public database or use private or shared containers. Additionally, they can’t use iCloud Documents or iCloud key-value storage. To learn more about using CloudKit in your App Clip, refer to the [Access your public iCloud database](https://developer.apple.com/documentation/appclip/sharing-data-between-your-app-clip-and-your-full-app#Access-your-public-iCloud-database) section of [Sharing data between your App Clip and your full app](https://developer.apple.com/documentation/appclip/sharing-data-between-your-app-clip-and-your-full-app).

Face ID

App Clips can’t use Face ID because the [`NSFaceIDUsageDescription`](https://developer.apple.com/documentation/BundleResources/Information-Property-List/NSFaceIDUsageDescription) entitlement isn’t available to them. However, you can use the [Local Authentication](https://developer.apple.com/documentation/LocalAuthentication) framework to authenticate people with Touch ID.

Note that App Clips may configure Wi-Fi networks using the [`Hotspot Configuration Entitlement`](https://developer.apple.com/documentation/BundleResources/Entitlements/com.apple.developer.networking.HotspotConfiguration). Additionally, to connect to an authentication provider, they may initialize an [`ASWebAuthenticationSession`](https://developer.apple.com/documentation/AuthenticationServices/ASWebAuthenticationSession) using [`init(url:callback:completionHandler:)`](https://developer.apple.com/documentation/AuthenticationServices/ASWebAuthenticationSession/init(url:callback:completionHandler:)).

### [Preserve user privacy](https://developer.apple.com/documentation/appclip/choosing-the-right-functionality-for-your-app-clip\#Preserve-user-privacy)

App Clips come with limitations that help to protect user privacy and prevent user tracking across apps and App Clips, for example:

- Functionality provided by [`SKAdNetwork`](https://developer.apple.com/documentation/StoreKit/SKAdNetwork) isn’t available.

- App Clips can’t request authorization to track a person with [App Tracking Transparency](https://developer.apple.com/documentation/AppTrackingTransparency).

- Both [`name`](https://developer.apple.com/documentation/UIKit/UIDevice/name) and [`identifierForVendor`](https://developer.apple.com/documentation/UIKit/UIDevice/identifierForVendor) return an empty string.

- App Clips can’t request continuous location access. However, you can call [`requestWhenInUseAuthorization()`](https://developer.apple.com/documentation/CoreLocation/CLLocationManager/requestWhenInUseAuthorization()) to request the When In Use authorization, which resets automatically the next day at 4:00 a.m.

- In iOS 17 and later, App Clips can request the [`Pass Type IDs Entitlement`](https://developer.apple.com/documentation/BundleResources/Entitlements/com.apple.developer.pass-type-identifiers) to read passes stored in the Wallet app. On devices that run iOS 16 or earlier, where App Clips can’t read passes stored in the Wallet app, App Clips can add a pass to the Wallet app and check if this pass is already present. For more information, refer to [Checking Whether a Pass Is in the Library](https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/PassKit_PG/Apps.html#//apple_ref/doc/uid/TP40012195-CH6-SW3).

- App Clips can’t share data with any other app except its corresponding full app. For more information, refer to [Sharing data between your App Clip and your full app](https://developer.apple.com/documentation/appclip/sharing-data-between-your-app-clip-and-your-full-app).

To help protect user data, App Clips can’t access:

- Apple Music and Media

- Data from apps like Calendar, Contacts, Files, Health, Messages, Reminders, and Photos

- Motion and fitness data

### [Reserve certain functionality for your full app](https://developer.apple.com/documentation/appclip/choosing-the-right-functionality-for-your-app-clip\#Reserve-certain-functionality-for-your-full-app)

App Clips that aren’t demo versions of full apps provide an in-the-moment experience and focus on offering the quickest possible solution to an everyday task, so some functionality works best in your full app. If your App Clip offers an in-the-moment experience, reserve the following functionality for the full app:

- App extensions

- Customization and settings, for example, creation of a settings bundle

- Data handoff and document opening

- In-app purchases

- Low-level UNIX functionality, for example, BSD notifications

- Multiple scenes on iPad

- On-demand resources and [Background Assets](https://developer.apple.com/documentation/BackgroundAssets)

- Promoting other apps

- Registration of custom URL schemes

- Requests for reviews of the full app by using StoreKit’s [`requestReview(in:)`](https://developer.apple.com/documentation/StoreKit/AppStore/requestReview(in:)-1q8qs) method

- Searching for paired Bluetooth devices

## [See Also](https://developer.apple.com/documentation/appclip/choosing-the-right-functionality-for-your-app-clip\#see-also)

### [Essentials](https://developer.apple.com/documentation/appclip/choosing-the-right-functionality-for-your-app-clip\#Essentials)

[Configuring App Clip experiences](https://developer.apple.com/documentation/appclip/configuring-the-launch-experience-of-your-app-clip)

Review how people launch your App Clip with invocation URLs, default and demo links, and advanced App Clip experiences.

[App Clips updates](https://developer.apple.com/documentation/Updates/AppClips)

Learn about important changes in App Clips.

---

# https://developer.apple.com/documentation/appclip/fruta-building-a-feature-rich-app-with-swiftui

- [App Clips](https://developer.apple.com/documentation/appclip)
- Fruta: Building a feature-rich app with SwiftUI

Sample Code

# Fruta: Building a feature-rich app with SwiftUI

Create a shared codebase to build a multiplatform app that offers widgets and an App Clip.

[Download](https://docs-assets.developer.apple.com/published/15035f283d6a/FrutaBuildingAFeatureRichAppWithSwiftUI.zip)

iOS 15.4+iPadOS 15.4+macOS 12.3+Xcode 13.3+

## [Overview](https://developer.apple.com/documentation/appclip/fruta-building-a-feature-rich-app-with-swiftui\#Overview)

The Fruta sample project builds an app for macOS, iOS, and iPadOS that implements [SwiftUI](https://developer.apple.com/documentation/SwiftUI) platform features like widgets, App Clips, and localization. Users can order smoothies, save favorite drinks, collect rewards, and browse recipes. It contains two flavors of app targets:

- Simple iOS and macOS app targets that you build using [Personal Team](https://help.apple.com/xcode/mac/11.4/#/dev17411c009) signing. This iOS app runs in Simulator, and only requires a standard Apple ID to install on a device. The simple app implements a rich, localized [SwiftUI](https://developer.apple.com/documentation/SwiftUI) interface. Users can browse and order smoothies, and save favorite drinks.

- Full featured iOS All and macOS All app targets. The full iOS app runs in Simulator, and on devices with an Apple Developer membership. This app includes widget extensions that enable users to add a widget to their iOS Home Screen or the macOS Notification Center, and to view their rewards or a favorite smoothie. This app also embeds an App Clip. With the App Clip, users can discover and instantly launch some of the app’s functionality on their iPhone or iPad without installing the app.

The Fruta sample app leverages [Sign in with Apple](https://developer.apple.com/documentation/SigninwithApple) and [PassKit (Apple Pay and Wallet)](https://developer.apple.com/documentation/PassKit) to provide a streamlined user experience.

### [Configure the sample code project](https://developer.apple.com/documentation/appclip/fruta-building-a-feature-rich-app-with-swiftui\#Configure-the-sample-code-project)

To build this project for iOS 15.4, use Xcode 13.3. The runtime requirement is iOS 15.4. To build this project for macOS 12.3, use Xcode 13.3.

To configure the iOS and macOS app targets without an Apple Developer account, follow these steps:

1. In the targets’ Signing & Capabilities panes click Add Account, and log in with your Apple ID.

2. Chose the Your Name (Personal Team) from the team drop down menu.

3. Click build-and-run.

To configure the iOS All and macOS All apps, follow these steps:

1. To run on your devices, including on macOS, set your team in the targets’ Signing & Capabilities panes. Xcode manages the provisioning profiles for you.

2. To run on an iOS or iPadOS device, open the `iOSClip.entitlements` file and update the value of the [`Parent Application Identifiers Entitlement`](https://developer.apple.com/documentation/BundleResources/Entitlements/com.apple.developer.parent-application-identifiers) to match the iOS app’s bundle identifier.

3. Make a note of the App Group name on the iOS target’s Signing & Capabilities tab in Project Settings. Substitute this value for group.example.fruta in the `Model.swift` file.

4. To enable the in-app-purchase flow, edit the Fruta iOS “Run” scheme, and select `Configuration.storekit` for StoreKit Configuration.

### [Create a shared codebase in SwiftUI](https://developer.apple.com/documentation/appclip/fruta-building-a-feature-rich-app-with-swiftui\#Create-a-shared-codebase-in-SwiftUI)

To create a single app definition that works for multiple platforms, the project defines a structure that conforms to the [`App`](https://developer.apple.com/documentation/SwiftUI/App) protocol. Because the `@main` attribute precedes the structure definition, the system recognizes the structure as the entry point into the app. Its computed body property returns a [`WindowGroup`](https://developer.apple.com/documentation/SwiftUI/WindowGroup) scene that contains the view hierarchy displayed by the app to the user. SwiftUI manages the presentation of the scene and its contents in a platform-appropriate manner.

@main
struct FrutaApp: App {
@StateObject private var model = Model()

var body: some Scene {
WindowGroup {
ContentView()
.environmentObject(model)
}
.commands {
SidebarCommands()
SmoothieCommands(model: model)
}
}
}

For more information, see [App organization](https://developer.apple.com/documentation/SwiftUI/App-organization).

### [Offer an App Clip](https://developer.apple.com/documentation/appclip/fruta-building-a-feature-rich-app-with-swiftui\#Offer-an-App-Clip)

On iOS and iPadOS, the Fruta app offers some of its functionality to users who don’t have the full app installed as an App Clip. The app’s Xcode project contains an App Clip target, and, instead of duplicating code, reuses code that’s shared across all platforms to build the App Clip. In shared code, the project makes use of the Active Compilation Condition build setting to exclude code for targets that don’t define the `APPCLIP` value. For example, only the App Clip target presents an App Store overlay to prompt the user to get the full app.

VStack(spacing: 0) {
Spacer()

orderStatusCard

Spacer()

#if EXTENDED_ALL
if presentingBottomBanner {
bottomBanner
}

#if APPCLIP
Text(verbatim: "App Store Overlay")
.hidden()
.appStoreOverlay(isPresented: $presentingAppStoreOverlay) {
SKOverlay.AppClipConfiguration(position: .bottom)
}
#endif
}
.onChange(of: model.hasAccount) { _ in
#if APPCLIP
if model.hasAccount {
presentingAppStoreOverlay = true
}
#endif
}

For more information, see [Creating an App Clip with Xcode](https://developer.apple.com/documentation/appclip/creating-an-app-clip-with-xcode) and [Choosing the right functionality for your App Clip](https://developer.apple.com/documentation/appclip/choosing-the-right-functionality-for-your-app-clip).

### [Create a widget](https://developer.apple.com/documentation/appclip/fruta-building-a-feature-rich-app-with-swiftui\#Create-a-widget)

To allow users to see some of the app’s content as a widget on their iOS Home screen or in the macOS Notification Center, the Xcode project contains targets for widget extensions. Both use code that’s shared across all targets.

For more information, see [WidgetKit](https://developer.apple.com/documentation/WidgetKit).

## [See Also](https://developer.apple.com/documentation/appclip/fruta-building-a-feature-rich-app-with-swiftui\#see-also)

### [Creation](https://developer.apple.com/documentation/appclip/fruta-building-a-feature-rich-app-with-swiftui\#Creation)

[Creating an App Clip with Xcode](https://developer.apple.com/documentation/appclip/creating-an-app-clip-with-xcode)

Add an App Clip target to your Xcode project and share code between the App Clip and its corresponding full app.

[`Parent Application Identifiers Entitlement`](https://developer.apple.com/documentation/BundleResources/Entitlements/com.apple.developer.parent-application-identifiers)

A list of parent application identifiers for an App Clip with exactly one entry.

[`com.apple.developer.associated-appclip-app-identifiers`](https://developer.apple.com/documentation/BundleResources/Entitlements/com.apple.developer.associated-appclip-app-identifiers)

A list of App Clip identifiers for an app with exactly one entry.

[`com.apple.developer.on-demand-install-capable`](https://developer.apple.com/documentation/BundleResources/Entitlements/com.apple.developer.on-demand-install-capable)

A Boolean value that indicates whether a bundle represents an App Clip.

---

# https://developer.apple.com/documentation/appclip/testing-the-launch-experience-of-your-app-clip

- [App Clips](https://developer.apple.com/documentation/appclip)
- Testing the launch experience of your App Clip

Article

# Testing the launch experience of your App Clip

Debug App Clip invocations, test the launch experience, and verify the configuration of your released App Clip.

## [Overview](https://developer.apple.com/documentation/appclip/testing-the-launch-experience-of-your-app-clip\#overview)

A fast launch experience is crucial to the experience your App Clip provides. As a result, you’ll spend a significant amount of time choosing invocation URLs, configuring App Clip experiences in App Store Connect, and writing code to handle the invocation URL.

To ensure your App Clip offers a smooth launch experience and that you properly configured your App Clip experiences, use the following tests and verifications:

- During development, use the `_XCAppClipURL` environment variable to configure an invocation URL for debugging.

- Verify the design of the App Clip card and the launch experience of your App Clip from invocations by creating a local experience on your test device.

- When you’re ready to share a beta version with others, create an App Clip experience for testers in [TestFlight](https://developer.apple.com/testflight/).

- When you’ve published your App Clip on the App Store, verify your App Clip configuration by using the App Clip diagnostics on iPhone.

### [Debug your App Clip](https://developer.apple.com/documentation/appclip/testing-the-launch-experience-of-your-app-clip\#Debug-your-App-Clip)

The invocation URL plays a key role to offering a fast and instant launch experience for your App Clip because you can use it to update the user interface of your App Clip to match the user’s context. Testing this code is especially important. In Xcode, provide an invocation URL for debugging. Then, make sure your code handles your invocation URLs — including unexpected invocation URLs — and updates the user interface of your App Clip to match the user’s context.

To configure an invocation URL for debugging:

2. Select the Run action.

3. In the Arguments tab, check whether the `_XCAppClipURL` environment variable is present. When you add an App Clip target to your project, Xcode adds it for you. If it’s missing, add the environment variable.

4. Set the environment variable’s value to the invocation URL you want to test.

5. Enable the variable by selecting the checkbox next to it.

6. Build and run the App Clip to access the test URL you configured from an [`NSUserActivity`](https://developer.apple.com/documentation/Foundation/NSUserActivity) object. For more information on accessing the invocation URL, refer to [Responding to invocations](https://developer.apple.com/documentation/appclip/responding-to-invocations).

The following screenshot shows the sheet to configure an App Clip target’s Run action with a value for the `_XCAppClipURL` environment variable:

When you debug your App Clip with Xcode, the App Clip launches right away with the value you set for the `_XCAppClipURL` variable. Note that the App Clip card doesn’t appear. To see the App Clip card on invocation when testing and test your entire launch experience, register a local experience on your test device.

### [Test App Clip invocations with a local experience](https://developer.apple.com/documentation/appclip/testing-the-launch-experience-of-your-app-clip\#Test-App-Clip-invocations-with-a-local-experience)

Leveraging the `_XCAppClipURL` environment variable is helpful when you debug the code that handles the invocation URL. However, you need to ensure your App Clip provides a fast and reliable launch experience from various invocations. In addition, exploring imagery, text, and a call-to-action verb for the App Clip card is especially important because the App Clip card is the user’s first interaction when they launch your App Clip.

To test invocations and explore the design of your App Clip card during development, configure a local experience on your test device. With a local experience, you can launch your App Clip by:

- Scanning an App Clip Code, QR code, or NFC tag you’ve created to launch the local experience. For information on creating App Clip Codes for testing, refer to [Creating App Clip Codes with the App Clip Code Generator](https://developer.apple.com/documentation/appclip/creating-app-clip-codes-with-the-app-clip-code-generator). To create a QR code or write an NFC tag, use your favorite tool.

- Tapping a Smart Banner you added to your website or an App Clip card that appears in Safari or an [`SFSafariViewController`](https://developer.apple.com/documentation/SafariServices/SFSafariViewController).

- Sharing a link to the website that displays a Smart App Banner. Make sure to add the sender of the message as a contact on the test device.

Note that you don’t need to configure the [`Associated Domains Entitlement`](https://developer.apple.com/documentation/BundleResources/Entitlements/com.apple.developer.associated-domains) or associate the App Clip with your website to launch a local experience from App Clip Codes, QR codes, or NFC tags. However, testing invocations from a Smart App Banner or the App Clip card in Safari comes with prerequisites; for example, you need to associate your website with your App Clip, submit a version of your app with an App Clip for review to App Store Connect, and release it in the App Store after approval. To learn more about when the Smart App Banner appears and for information on supporting invocations from your website or the Messages app, refer to [Supporting invocations from your website and the Messages app](https://developer.apple.com/documentation/appclip/supporting-invocations-from-your-website-and-the-messages-app). To verify your configured App Clip experiences for a released app and App Clip, refer to [Verify the configuration of your released App Clip](https://developer.apple.com/documentation/appclip/testing-the-launch-experience-of-your-app-clip#Verify-the-configuration-of-your-released-App-Clip) below.

To test your launch experience with a local experience:

1. Build and run your App Clip on your test device to make sure it’s cached on the test device. For example, with the Fruta sample code project, follow the instructions to configure it, then run the `Fruta iOS Clip` scheme. To download the sample code project, visit [Fruta: Building a feature-rich app with SwiftUI](https://developer.apple.com/documentation/appclip/fruta-building-a-feature-rich-app-with-swiftui).

3. Enter the invocation URL you want to test. In some cases, it may be a simple URL prefix like `https://fruta.example.com`. It can also be a longer invocation URL with path and query parameters.

4. Enter the bundle ID of your App Clip.

5. Provide a title and a subtitle. For the Fruta sample code project, you could enter `Order a smoothie.` as the title and `It’s yummy!` as the subtitle.

6. Select a call-to-action; for example `Open`.

7. Choose a photo you want to use as the App Clip card’s header image.

The following screenshot shows the interface you use to configure a local experience on iPhone:

When you configure a local experience on a device, the local experience takes precedence over App Clip experiences you configure in [App Store Connect](https://appstoreconnect.apple.com/login). However, local experiences only launch an App Clip that’s signed for Development, Ad Hoc, or TestFlight distribution. They don’t launch an App Clip or full app that’s published on the App Store. Remember to remove the local experience before testing App Clip experiences you configure in App Store Connect.

### [Test the launch experience of the full app during development](https://developer.apple.com/documentation/appclip/testing-the-launch-experience-of-your-app-clip\#Test-the-launch-experience-of-the-full-app-during-development)

Local App Clip invocations help you test the launch experience of your App Clip while you develop it in Xcode. However, local invocations don’t allow you to test the launch experience of the full app from an App Clip invocation. The best way to verify that your full app can handle App Clip invocations as you would expect is to use universal links and the invocation URL of your App Clip as the link’s URL. Both App Clips and universal links make the launch URL available as part of the user activity object. If a Universal Link opens your app to the App Clip experience you expect, you can be sure that the launch experience from the App Clip card to your full app works correctly.

For more information about debugging and testing universal links, refer to [TN3155: Debugging universal links](https://developer.apple.com/documentation/Technotes/tn3155-debugging-universal-links). For general information about universal links, refer to [Supporting universal links in your app](https://developer.apple.com/documentation/Xcode/supporting-universal-links-in-your-app).

### [Create App Clip experiences for testers in TestFlight](https://developer.apple.com/documentation/appclip/testing-the-launch-experience-of-your-app-clip\#Create-App-Clip-experiences-for-testers-in-TestFlight)

A reliable user experience is crucial to App Clips and requires spending time to test all user flows and supported invocations. To help make sure your App Clip works as expected, you can make your App Clip available to testers in [TestFlight](https://developer.apple.com/testflight/). First, upload an app with an App Clip to [App Store Connect](https://appstoreconnect.apple.com/login). Then, in App Store Connect, navigate to the uploaded build. In the App Clip section, you can configure up to three different App Clip experiences for testing. Note that the App Clip card doesn’t appear for App Clip experiences you create in TestFlight.

Users don’t install App Clips, and App Clips don’t appear on the Home Screen. Similarly, testers don’t install the beta version of your App Clip, and it also doesn’t appear on the Home Screen either. Instead, testers launch the App Clip experiences you configure for testing through the [TestFlight app](https://apps.apple.com/us/app/testflight/id899247664) on their device.

For more information on configuring experiences for testing in App Store Connect, refer to [Testing an App Clip Experience](https://help.apple.com/app-store-connect/#/devbc57e2ec6).

Testers can also configure a local experience to launch the App Clip you distribute with TestFlight. However, you must still associate your App Clip with your website so testers can launch it from the TestFlight app. In addition, testers must launch the App Clip from an App Clip experience you configure for testing in App Store Connect at least once to ensure that the App Clip is cached on the device.

### [Remove cached advanced App Clip experiences](https://developer.apple.com/documentation/appclip/testing-the-launch-experience-of-your-app-clip\#Remove-cached-advanced-App-Clip-experiences)

When you create a new advanced App Clip experience in App Store Connect, the new experience may not work right away because iOS caches App Clip experiences. To make sure an invocation launches a new App Clip experience, open the Settings app, navigate to the Developer section, and choose Clear Experience Cache.

### [Verify the configuration of your released App Clip](https://developer.apple.com/documentation/appclip/testing-the-launch-experience-of-your-app-clip\#Verify-the-configuration-of-your-released-App-Clip)

When you’ve uploaded your app version with an App Clip, it has passed App Store review, and you’ve released the version in the App Store, verify the configuration of your App Clip experiences to be sure that your website displays the Smart App Banner and that the App Clip appears on users’ devices:

1. Configure a default and optional advanced App Clip experiences in [App Store Connect](https://appstoreconnect.apple.com/login) and release the version of your app that contains the App Clip on the App Store.

2. On iPhone, open the Settings app, and navigate to the iOS developer settings by choosing Developer.

3. Choose Diagnostics in the App Clips Testing section.

4. Enter the URL of the website you associated with your App Clip and that you use for your App Clip experiences — for example, `https://fruta.example.com`.

When you enter a URL, the system verifies your App Clip configuration and indicates whether you:

- Registered an advanced App Clip experience

- Published your App Clip on the App Store

- Associated your App Clip with the entered URL

- Picked an invocation URL that fits into an App Clip Code

- Added a Smart App Banner to your website

If the system found issues with your configuration, the App Clip diagnostics functionality on iPhone indicates errors and offers links to App Clip documentation to help resolve issues. Note that advanced App Clip experiences and displaying a Smart App Banner on your website are optional but recommended steps that help users discover your App Clip.

---

# https://developer.apple.com/documentation/appclip/creating-app-clip-codes

Collection

- [App Clips](https://developer.apple.com/documentation/appclip)
- Creating App Clip Codes

# Creating App Clip Codes

Help users discover your App Clip by using an NFC-integrated or scan-only App Clip Code.

## [Overview](https://developer.apple.com/documentation/appclip/creating-app-clip-codes\#overview)

An App Clip Code is immediately recognizable to users and lets them know an App Clip is available. The App Clip Code offers a fast and secure launch experience for your App Clip that users trust.

The visual design of an App Clip Code encodes your App Clip’s _invocation URL_. Optionally, you can embed an NFC tag that also encodes the invocation URL. An App Clip Code with an embedded NFC tag is called an _NFC-integrated_ App Clip Code, while a code without an NFC tag is called a _scan-only_ App Clip Code.

The image at the center of an App Clip Code icon lets users know how to interact with the code. If they discover an NFC-integrated App Clip Code, they hold their device close to the code or scan it with the NFC Tag Reader in Control Center to launch your App Clip. They can also scan an NFC-integrated App Clip Code with the Camera app or the Code Scanner in Control Center. If they discover a scan-only App Clip Code, they scan it with the Camera or the Code Scanner in Control Center to launch your App Clip.

In addition to providing a great launch experience for your App Clip, you can also use an App Clip Code to offer a context-aware augmented reality experience. For more information, see [Interacting with App Clip Codes in AR](https://developer.apple.com/documentation/appclip/interacting-with-app-clip-codes-in-ar).

Creating an App Clip Code requires the following tasks:

1. Choosing an invocation URL and configuring an _advanced App Clip experience_ in [App Store Connect](https://appstoreconnect.apple.com/login). To learn more, see [Configuring App Clip experiences](https://developer.apple.com/documentation/appclip/configuring-the-launch-experience-of-your-app-clip).

3. Generating App Clip Codes with App Store Connect or with the App Clip Code Generator command-line tool. For more information, see [Pick a tool to create App Clip Codes](https://developer.apple.com/documentation/appclip/creating-app-clip-codes#Pick-a-tool-to-create-App-Clip-Codes) below.

For more information, see [Encoding a URL in an App Clip Code](https://developer.apple.com/documentation/appclip/encoding-a-url-in-an-app-clip-code).

### [Pick a tool to create App Clip Codes](https://developer.apple.com/documentation/appclip/creating-app-clip-codes\#Pick-a-tool-to-create-App-Clip-Codes)

App Clip Codes always use the design Apple provides to ensure users instantly recognize them. You can create an App Clip Code by selecting an advanced App Clip experience in [App Store Connect](https://appstoreconnect.apple.com/login) or by installing the [App Clip Code Generator](https://developer.apple.com/app-clips/resources/) command-line tool. Both have similar features and it’s up to you to pick the tool that best fits your needs.

Consider using App Store Connect if:

- You’ve already created an advanced App Clip experience in App Store Connect.

- You prefer an instantaneous preview while you experiment with colors.

- You’re comfortable using a tool that offers a more visual interface compared to a command-line tool.

Consider using the App Clip Code Generator command-line tool if:

- You haven’t created an advanced App Clip experience in App Store Connect — for example, during development of your App Clip.

- You need to create a lot of App Clip Codes and want to automate their creation with a script.

- You’re comfortable using a command-line tool.

For more information, see [Creating App Clip Codes with App Store Connect](https://developer.apple.com/documentation/appclip/creating-app-clip-codes-with-app-store-connect) and [Creating App Clip Codes with the App Clip Code Generator](https://developer.apple.com/documentation/appclip/creating-app-clip-codes-with-the-app-clip-code-generator).

## [Topics](https://developer.apple.com/documentation/appclip/creating-app-clip-codes\#topics)

### [App Clip Code creation](https://developer.apple.com/documentation/appclip/creating-app-clip-codes\#App-Clip-Code-creation)

[Creating App Clip Codes with App Store Connect](https://developer.apple.com/documentation/appclip/creating-app-clip-codes-with-app-store-connect)

Select one or more advanced App Clip experiences in App Store Connect and create App Clip Codes for users to scan to launch your App Clip.

[Creating App Clip Codes with the App Clip Code Generator](https://developer.apple.com/documentation/appclip/creating-app-clip-codes-with-the-app-clip-code-generator)

Use the App Clip Code Generator command-line tool to verify your code’s colors, get color suggestions, and create App Clip Codes.

## [See Also](https://developer.apple.com/documentation/appclip/creating-app-clip-codes\#see-also)

### [App Clip Codes](https://developer.apple.com/documentation/appclip/creating-app-clip-codes\#App-Clip-Codes)

[Encoding a URL in an App Clip Code](https://developer.apple.com/documentation/appclip/encoding-a-url-in-an-app-clip-code)

Choose an invocation URL for your App Clip Code that you can encode efficiently.

[Preparing multiple App Clip Codes for production](https://developer.apple.com/documentation/appclip/preparing-multiple-app-clip-codes-for-production)

Prepare your App Clip Codes to send to a professional printing service.

[Interacting with App Clip Codes in AR](https://developer.apple.com/documentation/appclip/interacting-with-app-clip-codes-in-ar)

Display content and provide services in an AR experience with App Clip Codes.

---

# https://developer.apple.com/documentation/appclip/interacting-with-app-clip-codes-in-ar

- [App Clips](https://developer.apple.com/documentation/appclip)
- Interacting with App Clip Codes in AR

Sample Code

# Interacting with App Clip Codes in AR

Display content and provide services in an AR experience with App Clip Codes.

[Download](https://docs-assets.developer.apple.com/published/84b24fc9087a/InteractingWithAppClipCodesInAR.zip)

iOS 14.5+iPadOS 14.5+Xcode 12.5+

## [Overview](https://developer.apple.com/documentation/appclip/interacting-with-app-clip-codes-in-ar\#Overview)

The sample app Seed Shop provides gardeners with previews of fully grown plants. At the nursery, Seed Shop identifies the plant from an App Clip Code on a seed packet, and displays the adult plant in 3D. With the help of AR, the buyer can see, for example, the real height of a typical Mammoth sunflower by inspecting the virtual plant at scale, relative to real objects in the camera feed.

When a user with a device running iOS & iPad OS 14.3 or later scans the seed packet’s App Clip Code with their camera or Code Scanner, the sample project’s App Clip provides a virtual image of the plant.

If the user indicates they may buy a particular plant in the App Clip experience, Seed Shop suggests the user download the full version of the app to preview the plant in their own garden. This sample project builds the App Clip Code provided on the seed packet at the garden store, allowing the user to view an AR version of the plant before purchase.

### [Configure the Sample Code Project](https://developer.apple.com/documentation/appclip/interacting-with-app-clip-codes-in-ar\#Configure-the-Sample-Code-Project)

To configure Seed Shop for code signing, first set a development team on each target. Define a unique bundle ID for the targets, and set the App Clip’s parent application identifiers entitlement.

Next, set the hostname for the App Clip experience URL in the Associated Domains entitlement. The process of setting the hostname requires an explicit App ID, provided by a development team member with Admin permission. For more information on setting a development team, bundle ID, and entitlements, see [Creating an App Clip with Xcode](https://developer.apple.com/documentation/AppClip/creating-an-app-clip-with-xcode).

Run the following command to generate an App Clip Code from the [App Clip Code Generator](https://developer.apple.com/app-clips/resources/):

AppClipCodeGenerator generate --url https://developer.apple.com/sunfl --index 0 --output ~/Downloads/AppClipCode-sunflower.svg --logo badge

To add the sample’s App Clip Codes to the environment, you can display them on another device or print them out. For more on creating App Clip Codes, see [Creating App Clip Codes](https://developer.apple.com/documentation/AppClip/creating-app-clip-codes).

The App Clip Codes in Seed Shop display on a package of seeds. Add this [image of a seed packet](https://developer.apple.com/sample-code/ar/sunflower.jpg) to your physical environment by displaying it on another device or printing it out.

### [Ensure Device Support and Run a Session](https://developer.apple.com/documentation/appclip/interacting-with-app-clip-codes-in-ar\#Ensure-Device-Support-and-Run-a-Session)

In [`viewDidLoad`](x-source-tag://ViewDidLoad), the sample app calls [`supportsAppClipCodeTracking`](https://developer.apple.com/documentation/ARKit/ARWorldTrackingConfiguration/supportsAppClipCodeTracking) to check if the device contains the Apple Neural Engine (ANE), which App Clip Code tracking requires.

guard ARWorldTrackingConfiguration.supportsAppClipCodeTracking else {
displayUnsupportedDevicePrompt()
return

To search the environment for physical codes, the sample sets [`appClipCodeTrackingEnabled`](https://developer.apple.com/documentation/ARKit/ARWorldTrackingConfiguration/appClipCodeTrackingEnabled) to `true` before running the session.

newConfiguration.appClipCodeTrackingEnabled = true
arView.session.run(newConfiguration)

### [Identify the App Clip Code that Launched the Experience](https://developer.apple.com/documentation/appclip/interacting-with-app-clip-codes-in-ar\#Identify-the-App-Clip-Code-that-Launched-the-Experience)

When the user points the device at an App Clip Code using the camera or Code Scanner, the system launches its associated App Clip, or if present, the full app.

In the AR experience, the sample code checks the [`NSUserActivity`](https://developer.apple.com/documentation/Foundation/NSUserActivity) invocation URL to identify the App Clip Code that invoked the app or App Clip.

func scene(_ scene: UIScene, willConnectTo session: UISceneSession, options connectionOptions: UIScene.ConnectionOptions) {
for activity in connectionOptions.userActivities where activity.activityType == NSUserActivityTypeBrowsingWeb {
appClipCodeURL = activity.webpageURL

The source of the URL depends on how the App Clip launched:

- The invocation URL is the `_XCAppClipURL` scheme environment variable when Xcode launches the app or App Clip. For more information, see [Testing Your App Clip’s Launch Experience](https://developer.apple.com/documentation/AppClip/testing-the-launch-experience-of-your-app-clip#Debug-your-App-Clip).

- The invocation URL is the invoking App Clip Code’s URL when the system launches the app or App Clip in the device’s camera feed or through the Code Scanner.

There may be multiple App Clip Codes visible in the camera feed that share the same [`url`](https://developer.apple.com/documentation/ARKit/ARAppClipCodeAnchor/url); for more information, see [`ARAppClipCodeAnchor`](https://developer.apple.com/documentation/ARKit/ARAppClipCodeAnchor).

If an app interacts with a single App Clip Code, the app can limit its interaction with App Clip Codes that encode the invocation URL. For simplicity, the sample allows the user to scan any associated App Clip Code. However, because the sample app downloads custom assets over the web per App Clip Code, the sample app begins downloading assets for the invocation URL immediately, in anticipation that ARKit will recognize the invoking App Clip Code in the camera feed.

process(productKey: getProductKey(from: appClipCodeLaunchURL), initializePreview: false)

### [Guide the User with Messaging](https://developer.apple.com/documentation/appclip/interacting-with-app-clip-codes-in-ar\#Guide-the-User-with-Messaging)

The device may pan away from the App Clip Code that launched the experience in the time it takes for the system to transition from the camera or Code Scanner to the app or App Clip. In the event ARKit doesn’t immediately find the App Clip Code in the camera feed, the sample app displays text instructing the user what to do.

class AppClipCodeCoachingOverlayView: UILabel {
init(parentView: UIView) {
super.init(frame: .zero)
text = "Scan code to start"

### [Launch the App Clip in Code Scanner](https://developer.apple.com/documentation/appclip/interacting-with-app-clip-codes-in-ar\#Launch-the-App-Clip-in-Code-Scanner)

During development, the sample project can launch the App Clip target in Xcode to test the AR experience. After the target launches once, the device scans the test App Clip Code with Code Scanner to invoke the App Clip.

To associate an App Clip Code to the App Clip during development, Seed Shop sets up an App Clip local experience. The sample app requires a local experience URL prefix of `https://developer.apple.com`, and a bundle ID of `com.example.apple-samplecode.AppClipCodesExampleApp1.Clip`.

For more on local experiences, see [Testing Your App Clip’s Launch Experience](https://developer.apple.com/documentation/AppClip/testing-the-launch-experience-of-your-app-clip#Test-invocations-with-a-local-experience).

### [Set Up an App Clip Experience in App Store Connect](https://developer.apple.com/documentation/appclip/interacting-with-app-clip-codes-in-ar\#Set-Up-an-App-Clip-Experience-in-App-Store-Connect)

At runtime, the system checks the App Clip registry in App Store Connect to ensure an App Clip associates to an App Clip Code before allowing the app access to the App Clip Code URL. For more information, see [`url`](https://developer.apple.com/documentation/ARKit/ARAppClipCodeAnchor/url).

To decode App Clip Code URLs, Seed Shop sets up an App Clip experience in App Store Connect, and defines the App Clip experience URL of `https://developer.apple.com`. The value of the App Clip experience URL maps to a server that’s unique and depends on the development team. For more information, see [Set up an App Clip experience](https://help.apple.com/app-store-connect/#/dev5b665db74).

The app generates App Clip Codes that associate to the App Clip experience in App Store Connect by uploading a CSV file containing the App Clip Code URLs. The fully qualified domain name of each URL matches the App Clip experience URL. The URL suffix identifies the context-specific items or locations with which the App Clip interacts. The sample app identifies a seed packet for a sunflower. To create an App Clip Code for the sunflower, the sample requires a CSV file containing the URL:

https://developer.apple.com/sunfl

When testers view App Clip Codes to launch the App Clip or decode [`ARAppClipCodeAnchor`](https://developer.apple.com/documentation/ARKit/ARAppClipCodeAnchor) URLs in an AR experience, the framework refers to the device’s local experience. Otherwise, the system displays the App Clip card in the device camera, and allows [`ARAppClipCodeAnchor`](https://developer.apple.com/documentation/ARKit/ARAppClipCodeAnchor) URL decoding, only for App Clip experience URLs of app-review approved App Clips. For more information, see [Test an App Clip Experience](https://help.apple.com/app-store-connect/#/devbc57e2ec6).

### [Configure the Server and Targets for App Site Association](https://developer.apple.com/documentation/appclip/interacting-with-app-clip-codes-in-ar\#Configure-the-Server-and-Targets-for-App-Site-Association)

App Store Connect allows an app to define a particular App Clip experience URL if the server hosting the URL’s domain approves of it via Apple App Site Association. In addition, the framework performs an equivalent runtime check before allowing the App Clip or parent app to decode [`ARAppClipCodeAnchor`](https://developer.apple.com/documentation/ARKit/ARAppClipCodeAnchor) URLs that are within the App Clip experience’s domain. This check occurs for local and App Store Connect experiences. To express approval, the server provides the App Clip’s and parent app’s fully qualified application identifiers in an Apple App Site Association (AASA) file’s `appclips` node.

"appclips": {
"apps": [\
"A93A5CM278.com.example.apple-samplecode.AppClipCodesExampleApp1.Clip",\
"A93A5CM278.com.example.apple-samplecode.AppClipCodesExampleApp1"\
]
}

Seed Shop requires the AASA file that the Apple Developer website hosts at [https://developer.apple.com/.well-known/apple-app-site-association](https://developer.apple.com/.well-known/apple-app-site-association). Navigate the URL in Safari and inspect its `appclips` node to see the sample app’s AASA configuration.

The sample project enables the Associated Domains capability on both targets. The key’s value is the fully qualified domain of the sample project’s App Clip experience URL.

For more on configuring AASA for App Clips, see [Associating Your App Clip with Your Website](https://developer.apple.com/documentation/AppClip/associating-your-app-clip-with-your-website).

### [Recognize an App Clip Code and Decode the URL](https://developer.apple.com/documentation/appclip/interacting-with-app-clip-codes-in-ar\#Recognize-an-App-Clip-Code-and-Decode-the-URL)

When ARKit recognizes an App Clip Code in the camera feed, it instantiates an [`ARAppClipCodeAnchor`](https://developer.apple.com/documentation/ARKit/ARAppClipCodeAnchor) and passes it to the [`session:didAdd:anchors:`](https://developer.apple.com/documentation/ARKit/ARSessionDelegate/session(_:didAdd:)) callback. Since the user succeeded in scanning a code, the sample app hides the instructional text.

func session(_ session: ARSession, didAdd anchors: [ARAnchor]) {
for anchor in anchors {
if anchor is ARAppClipCodeAnchor {
// Hide the coaching overlay since ARKit recognized an App Clip Code.
appClipCodeCoachingOverlay.setCoachingViewHidden(true)

Access the anchor’s URL for context-specific information about the recognized App Clip Code. The URL is `nil` until the anchor’s [`urlDecodingState`](https://developer.apple.com/documentation/ARKit/ARAppClipCodeAnchor/urlDecodingState-swift.property) is [`decoded`](https://developer.apple.com/documentation/ARKit/ARAppClipCodeAnchor/URLDecodingState-swift.enum/decoded). To check for decoding state changes, the sample app monitors the [`session:didUpdate:anchors:`](https://developer.apple.com/documentation/ARKit/ARSessionDelegate/session(_:didUpdate:)-3qtt8) callback.

func session(_ session: ARSession, didUpdate anchors: [ARAnchor]) {
for anchor in anchors {
if let appClipCodeAnchor = anchor as? ARAppClipCodeAnchor, appClipCodeAnchor.urlDecodingState != .decoding {
let decodedURL: URL
switch appClipCodeAnchor.urlDecodingState {
case .decoded:
decodedURL = appClipCodeAnchor.url!
if !decodedURLs.contains(decodedURL) {
decodedURLs.append(decodedURL)
process(productKey: getProductKey(from: decodedURL))

If Seed Shop fails to decode the URL, the sample project uses a test URL.

var testAppClipCodeURL = URL(string: "https://developer.apple.com/sunfl")!

For more on URL decoding failure, see [`failed`](https://developer.apple.com/documentation/ARKit/ARAppClipCodeAnchor/URLDecodingState-swift.enum/failed).

### [Retrieve a Product’s 3D Model](https://developer.apple.com/documentation/appclip/interacting-with-app-clip-codes-in-ar\#Retrieve-a-Products-3D-Model)

When ARKit decodes an App Clip Code’s URL, the sample app parses the URL suffix to get the product name.

The app implements a custom URL mapping system using the project’s `modelURLFor` dictionary. Each dictionary key is an App Clip Code’s URL suffix, and the value represents the seed packet’s corresponding grown plant 3D asset.

let modelURLFor: [String: URL] = [\
"sunfl": URL(string: "https://developer.apple.com/sample-code/ar/sunflower.usdz")!\
]

The sample app downloads the asset and prepares the 3D model using the mapped `contentURL`.

extension ViewController {
func process(productKey: String, initializePreview: Bool = true) {
if let modelURL = modelURLFor[productKey] {
process(modelURL: modelURL, productKey: productKey)

func process(modelURL: URL, productKey: String) {
let contentLoad = CachingWebLoader.shared.cachedWebLoad(url: modelURL)

### [Search for Product Packaging](https://developer.apple.com/documentation/appclip/interacting-with-app-clip-codes-in-ar\#Search-for-Product-Packaging)

The sample project’s URL mapping system includes an image of the product’s packaging material on which to place the product’s 3D model in the environment.

let imageURLFor: [String: URL] = [\
"sunfl": URL(string: "https://developer.apple.com/sample-code/ar/sunflower.jpg")!\
]

ARKit estimates the 3D position and orientation of each [`ARAppClipCodeAnchor`](https://developer.apple.com/documentation/ARKit/ARAppClipCodeAnchor), but [`ARImageAnchor`](https://developer.apple.com/documentation/ARKit/ARImageAnchor) serves as a better platform on which to place virtual content for several reasons:

- Small physical size impacts ARKit’s tracking accuracy, and App Clip Codes typically run small on product packaging or in an advertisement.

- ARKit manages the removal of App Clip Code anchors from the session whereas the app controls whether to remove an image anchor. As a result, the image anchor is less likely to go away.

To search the environment for the product’s packaging image, the sample downloads the image that the mapping URL references and then creates an [`ARReferenceImage`](https://developer.apple.com/documentation/ARKit/ARReferenceImage).

func process(imageURL: URL, productKey: String, initializeImageAnchor: Bool) {
if initializeImageAnchor {
let imageLoader = CachingWebLoader.shared.cachedWebLoad(url: imageURL) { [weak self] url in
DispatchQueue.global(qos: .userInitiated).async {
if
let dataProvider = CGDataProvider(url: url as CFURL),
let image = CGImage(
jpegDataProviderSource: dataProvider,
decode: nil,
shouldInterpolate: false,
intent: .absoluteColorimetric
)
{
let modelAnchorImage = ARReferenceImage(
image,
orientation: .up,
// Note: the width of the sample seed packet is about 8cm.
physicalWidth: 0.08
)

For more information about image tracking, see [Tracking and Altering Images](https://developer.apple.com/documentation/ARKit/tracking-and-altering-images).

### [Display the 3D Asset](https://developer.apple.com/documentation/appclip/interacting-with-app-clip-codes-in-ar\#Display-the-3D-Asset)

When the user pans the device from the scanned App Clip Code to its downloaded packaging image, ARKit identifies the seed packet’s real-world location and displays the full-grown plant on top.

When ARKit recognizes the packaging image, the session creates an image anchor and passes it into the [`session:didAdd:anchors:`](https://developer.apple.com/documentation/ARKit/ARSessionDelegate/session(_:didAdd:)) callback. The app displays the virtual product on top of the image by calling its `present(_:on)` function.

if let imageAnchorForModel = self?.imageAnchorFor[productKey], let self = self {
self.modelFor[productKey]!.present(on: imageAnchorForModel)

As the user views the virtual plant, the App Clip waits for the user to scan another seed packet. During this time, the App Clip can provide information about the features of the full app. For example, the Seed Shop App Clip might offer the user the ability to download the full app to preview the full-grown plant in their garden. For recommendations about showcasing an app in an App Clip, see [App Clip Human Interface Guidelines](https://developer.apple.com/design/human-interface-guidelines/app-clips/overview/).

## [See Also](https://developer.apple.com/documentation/appclip/interacting-with-app-clip-codes-in-ar\#see-also)

### [App Clip Codes](https://developer.apple.com/documentation/appclip/interacting-with-app-clip-codes-in-ar\#App-Clip-Codes)

Help users discover your App Clip by using an NFC-integrated or scan-only App Clip Code.

[Encoding a URL in an App Clip Code](https://developer.apple.com/documentation/appclip/encoding-a-url-in-an-app-clip-code)

Choose an invocation URL for your App Clip Code that you can encode efficiently.

[Preparing multiple App Clip Codes for production](https://developer.apple.com/documentation/appclip/preparing-multiple-app-clip-codes-for-production)

Prepare your App Clip Codes to send to a professional printing service.

---

# https://developer.apple.com/documentation/appclip/distributing-your-app-clip

- [App Clips](https://developer.apple.com/documentation/appclip)
- Distributing your App Clip

Article

# Distributing your App Clip

Archive the full app for your App Clip, upload it to App Store Connect, and distribute it to testers or publish it on the App Store.

## [Overview](https://developer.apple.com/documentation/appclip/distributing-your-app-clip\#overview)

When you submit an App Clip for distribution to testers with [TestFlight](https://developer.apple.com/testflight/) or for publishing in the App Store, you don’t submit the App Clip on its own; you export and submit the app bundle of the full app that includes the App Clip.

### [Archive your app and upload it to App Store Connect](https://developer.apple.com/documentation/appclip/distributing-your-app-clip\#Archive-your-app-and-upload-it-to-App-Store-Connect)

Uploading an app archive that contains the full app and the App Clip works just like for an app that doesn’t come with an App Clip. To export an App Clip for distribution to testers:

1. In Xcode, archive the App Clip’s corresponding app, open the Organizer window, select the archive, and click Distribute App.

2. Choose App Store Connect as the distribution method, then upload the app.

3. To distribute the app that features an App Clip to testers with [TestFlight](https://developer.apple.com/testflight/) or publish it on the App Store, visit [App Store Connect](https://appstoreconnect.apple.com/login).

For additional information, see [Testing the launch experience of your App Clip](https://developer.apple.com/documentation/appclip/testing-the-launch-experience-of-your-app-clip) and [Distributing your app for beta testing and releases](https://developer.apple.com/documentation/Xcode/distributing-your-app-for-beta-testing-and-releases).

---

# https://developer.apple.com/documentation/appclip/sharing-data-between-your-app-clip-and-your-full-app

- [App Clips](https://developer.apple.com/documentation/appclip)
- Sharing data between your App Clip and your full app

Article

# Sharing data between your App Clip and your full app

Use CloudKit, Sign in with Apple, shared user defaults or containers, and the keychain to offer a smooth transition from your App Clip to your app.

## [Overview](https://developer.apple.com/documentation/appclip/sharing-data-between-your-app-clip-and-your-full-app\#overview)

When users of your App Clip install your full app, the full app replaces the App Clip and receives all invocations in its place. It’s important you provide a good user experience to users who have become familiar with the App Clip and are now starting to use the full app; for example:

- Show information in the app that the user entered when they used the App Clip.

- Make downloaded data available to the app.

- Don’t require users to log in to their account again.

Making App Clip data accessible to your full app is key to offering a smooth transition from App Clip to full app. Choose from the following technologies:

- Access your public iCloud database in your App Clip.

- Store App Clip data and assets in a shared container and access them in your full app.

- Store sensitive App Clip data in the keychain and access it in your full app.

- Use Sign in with Apple to offer a seamless login experience.

### [Access your public iCloud database](https://developer.apple.com/documentation/appclip/sharing-data-between-your-app-clip-and-your-full-app\#Access-your-public-iCloud-database)

Making sure your App Clip has access to the same data as your full app and keeping its data up to date are important things to consider when you create your App Clip. For example, an App Clip for restaurants needs to always show the latest weekly lunch menu that’s also available to users of your full app. Starting with iOS 16, your App Clip can use [CloudKit](https://developer.apple.com/documentation/CloudKit) to read data you store in a public iCloud database with [CloudKit](https://developer.apple.com/documentation/CloudKit) — including a Core Data store you mirror with a public [CloudKit](https://developer.apple.com/documentation/CloudKit) database. This enables your App Clip to access information that’s available to all users of your app — like the previously mentioned lunch menu for a restaurant app and App Clip.

To read your app’s public iCloud database, add the iCloud capability to your App Clip as described in [Configuring iCloud services](https://developer.apple.com/documentation/Xcode/configuring-icloud-services). The process is the same as for your full app. However, your App Clip can only set the `CloudKit-Anonymous` value for the [`iCloud Services Entitlement`](https://developer.apple.com/documentation/BundleResources/Entitlements/com.apple.developer.icloud-services). Xcode chooses this value for you when you add the iCloud capability to your App Clip target. After you’ve added the iCloud capability to your App Clip target, specify the container your App Clip should access, and access your data just like you do in your regular app.

For more information on iCloud and public databases, refer to [Build Apps Using CloudKit](https://developer.apple.com/icloud/cloudkit/) and [Designing apps using CloudKit](https://developer.apple.com/icloud/cloudkit/designing/).

### [Make local App Clip data available to the full app](https://developer.apple.com/documentation/appclip/sharing-data-between-your-app-clip-and-your-full-app\#Make-local-App-Clip-data-available-to-the-full-app)

Your App Clip can make its local data accessible to your corresponding full app by storing data in a shared container. The full app can then access this local data when it replaces the App Clip, providing a positive user experience.

To store local data in a shared container:

1. Add the App Groups capability to the targets of both the App Clip and the full app. For more information about configuring App Groups, refer to [Configuring app groups](https://developer.apple.com/documentation/Xcode/configuring-app-groups).

2. For both targets, add the same app group to the capability; for example, `group.exampleApp.appClipMigration`.

3. Add code to your App Clip target that obtains the URL of the shared container using [`containerURL(forSecurityApplicationGroupIdentifier:)`](https://developer.apple.com/documentation/Foundation/FileManager/containerURL(forSecurityApplicationGroupIdentifier:)) and store data using this URL; for example, by using [`write(to:atomically:encoding:)`](https://developer.apple.com/documentation/Foundation/NSString/write(to:atomically:encoding:)).

4. In your full app’s code, use the same function to obtain the URL of the shared container and access its content; for example, by using [`init(contentsOfURL:encoding:)`](https://developer.apple.com/documentation/Foundation/NSString/init(contentsOfURL:encoding:)-715fw).

In addition to a shared container, the App Clip can also store information in a shared [`UserDefaults`](https://developer.apple.com/documentation/Foundation/UserDefaults) instance that’s accessible to the full app. The following code uses the configured app group to create the shared `UserDefaults` instance and store a string:

guard let sharedUserDefaults = UserDefaults(suiteName: "group.exampleApp.appClipMigration") else {
// Error handling
}
sharedUserDefaults.set("A sample string", forKey: "sharedText")

When users install the full app, it can access the shared user defaults. For example, access the string stored in the previous code using the following code snippet:

guard let sharedUserDefaults = UserDefaults(suiteName: "group.exampleApp.appClipDataMigration") else {
// Error handling
}
guard let migratedData = sharedUserDefaults.string(forKey: "sharedText") else { return }

To preserve user privacy across apps and App Clips, an App Clip can only share its data with its corresponding app. Don’t store sensitive user information, such as passwords, in a shared app container or in user defaults. However, if your App Clip requires people to log in to an account to offer its functionality, you likely want to offer a seamless upgrade experience to the full app. In this case, you might store an API key, hashed user ID, or similarly anonymized identifier in the shared app container or in user defaults. Then, you can use the identifier when the user launches the full app to offer a more seamless upgrade experience that doesn’t require them to again log in.

### [Review keychain usage](https://developer.apple.com/documentation/appclip/sharing-data-between-your-app-clip-and-your-full-app\#Review-keychain-usage)

The keychain offers a secure way to store sensitive information. Storing and reading App Clip data in the keychain generally works the same as for your full app. However, be aware of the following behavior when using the keychain:

- Your App Clip can’t access data your full app stores in the keychain. For example, say your app stores login information in the keychain. A user later uninstalls the app only to later launch your App Clip from an invocation. In the App Clip, they’ll need to log in again because your App Clip can’t access the stored login information that may have remained in the keychain.

- On devices that run iOS 15.3 or earlier, you can’t make information the App Clip stores in the keychain accessible to its corresponding full app. If your App Clip requires people to log in to an account to offer its functionality, don’t make the user sign in a second time in the full app. Instead, store an API key or hashed user ID in the shared app container as described above, or offer Sign in with Apple.

- Starting with iOS 15.4, information that the App Clip stores in the keychain is accessible to its corresponding full app. To make sure only the corresponding full app receives access to keychain items stored by the App Clip, the system uses the [`com.apple.developer.associated-appclip-app-identifiers`](https://developer.apple.com/documentation/BundleResources/Entitlements/com.apple.developer.associated-appclip-app-identifiers) and [`Parent Application Identifiers Entitlement`](https://developer.apple.com/documentation/BundleResources/Entitlements/com.apple.developer.parent-application-identifiers) entitlements. When you create an App Clip with Xcode, it adds the [`Parent Application Identifiers Entitlement`](https://developer.apple.com/documentation/BundleResources/Entitlements/com.apple.developer.parent-application-identifiers). It automatically adds the [`com.apple.developer.associated-appclip-app-identifiers`](https://developer.apple.com/documentation/BundleResources/Entitlements/com.apple.developer.associated-appclip-app-identifiers) entitlement when you archive the app that contains the App Clip.

A user may frequently install and uninstall your app and use the App Clip before reinstalling your app. If your full app and your App Clip write the same data to the keychain, make sure your code handles the following cases:

- The keychain may contain multiple copies of the same data and they’re accessible to the full app, especially if you use [`kSecClassKey`](https://developer.apple.com/documentation/Security/kSecClassKey) because the entries have different public key hash values.

- A keychain item by the App Clip might overwrite an item that a previous installation of the full app created.

These cases are especially common when a person frequently installs and uninstalls the full app and launches the App Clip in between — for example, when you develop your app and your App Clip at the same time. To avoid errors caused by duplicated or overwritten keychain data, add code that:

- Checks if more than one copy of an item exists in the keychain

- Uses different values for [`kSecAttrLabel`](https://developer.apple.com/documentation/Security/kSecAttrLabel) to distinguish between items stored by your app and your App Clip

- Decides which information to use if there’s a duplicate

- Deletes any unneeded items stored in the keychain

The following example shows how your App Clip can store a sensitive string in the keychain. Note how the code sets the [`kSecAttrLabel`](https://developer.apple.com/documentation/Security/kSecAttrLabel) attribute to the `fruta-appclip` value to distinguish it from a keychain entry that the app creates.

// Write sensitive information you use in your App Clip to the keychain — for example, an authentication token.
let addSecretsQuery: [String: Any] = [\
kSecClass as String: kSecClassGenericPassword,\
kSecValueData as String: "smoothie-secret".data(using: .utf8),\
kSecAttrLabel as String: "fruta-appclip"\
]
SecItemAdd(addSecretsQuery as CFDictionary, nil)

When a user installs the full app, read the sensitive information that the App Clip stored as shown in the following example:

// Read the sensitive information from the keychain that your App Clip stored.
var readSecretsQuery: [String: Any] = [\
kSecClass as String: kSecClassGenericPassword,\
kSecReturnAttributes as String: true,\
kSecAttrLabel as String: "fruta-appclip",\
kSecReturnData as String: true\
]
var secretsCopy: AnyObject?
SecItemCopyMatching(readSecretsQuery as CFDictionary, &secretsCopy)

For more information on using the keychain to store sensitive information, refer to [Using the keychain to manage user secrets](https://developer.apple.com/documentation/Security/using-the-keychain-to-manage-user-secrets) and [Keychain services](https://developer.apple.com/documentation/Security/keychain-services).

### [Offer Sign in with Apple](https://developer.apple.com/documentation/appclip/sharing-data-between-your-app-clip-and-your-full-app\#Offer-Sign-in-with-Apple)

App Clips may use any technology to allow users to sign in to their account or create one. However, if your App Clip requires users to log in to an account, consider offering [Sign in with Apple](https://developer.apple.com/documentation/SigninwithApple). In addition to helping provide a simple, secure, and privacy-preserving account creation and sign-in experience, it offers a positive experience when a user starts using the full app.

If you offer Sign in with Apple and create a shared data container, create a user experience that doesn’t require users to log in again when they start using the full app. The following code stores the [`ASAuthorizationAppleIDCredential`](https://developer.apple.com/documentation/AuthenticationServices/ASAuthorizationAppleIDCredential) in a shared [`UserDefaults`](https://developer.apple.com/documentation/Foundation/UserDefaults) instance:

let groupUserDefaults = UserDefaults(suiteName: "group.com.example.appClipDataMigration")
guard let credential = authorization.credential as ASAuthorizationAppleIDCredential else { return }
groupUserDefaults?.set(credential.user, forKey: "SavedUserID")

In the app’s code, retrieve the stored Apple ID authorization credential and use it to sign in the user:

let provider = ASAuthorizationAppleIDProvider()
let groupUserDefaults = UserDefaults(suiteName: "group.com.example.appClipDataMigration")
let user = groupUserDefaults?.get("SavedUserID")
provider.getCredentialState(forUserID: user) { state, error in
if state == .authorized {
readFavoriteSmoothies(user)
}
}

## [See Also](https://developer.apple.com/documentation/appclip/sharing-data-between-your-app-clip-and-your-full-app\#see-also)

### [App Clip to full app transition](https://developer.apple.com/documentation/appclip/sharing-data-between-your-app-clip-and-your-full-app\#App-Clip-to-full-app-transition)

[Recommending your app to App Clip users](https://developer.apple.com/documentation/appclip/recommending-your-app-to-app-clip-users)

Display an overlay in your App Clip to recommend your app to users.

---

# https://developer.apple.com/documentation/appclip/preparing-multiple-app-clip-codes-for-production

- [App Clips](https://developer.apple.com/documentation/appclip)
- Preparing multiple App Clip Codes for production

Article

# Preparing multiple App Clip Codes for production

Prepare your App Clip Codes to send to a professional printing service.

## [Overview](https://developer.apple.com/documentation/appclip/preparing-multiple-app-clip-codes-for-production\#overview)

After you create your App Clip Codes, you can print them yourself, or work with a professional printing service — for example, [RR Donnelley](https://touchless.acc.rrd.com/). However, if you have a lot of App Clip Codes, printing them yourself doesn’t scale well, and you’ll have more success working with a professional printing service.

Because you can’t see which invocation URL your App Clip Code contains just by looking at it, you need to keep track of your SVG files and their corresponding URLs. Careful file management, versioning, and change tracking are key to avoiding faulty print runs.

### [Map SVG filenames to invocation URLs](https://developer.apple.com/documentation/appclip/preparing-multiple-app-clip-codes-for-production\#Map-SVG-filenames-to-invocation-URLs)

In general, it’s up to you to decide how to keep track of changes and which SVG files map to which invocation URLs. In most cases, a _mapping file_ that uses the comma-separated values (CSV) file format is the preferred option.

To reduce the risk of human error and simplify change tracking, consider using a single mapping file to create your SVG files before sending them to a printing service.

If you’re working with [RR Donnelley](https://touchless.acc.rrd.com/) to produce App Clip Codes:

- Create a ZIP file that contains the SVG files for your App Clip Codes and the mapping file in its root folder.

- The mapping file must be a CSV file with one field named `SVG File Name` and another named `URL`, with each row representing one App Clip Code.

- The ZIP file may contain up to 10,000 SVG files, and the mapping file may contain up to 10,000 corresponding entries.

- The maximum length for any filename (ZIP file, SVG files, or mapping file) is 188 characters.

The following code shows the contents of a mapping file with entries for two App Clip Codes:

SVG File Name, URL
AppClipCode1.svg, https://example.com
AppClipCode2.svg, https://appclip.example.com/

## [See Also](https://developer.apple.com/documentation/appclip/preparing-multiple-app-clip-codes-for-production\#see-also)

### [App Clip Codes](https://developer.apple.com/documentation/appclip/preparing-multiple-app-clip-codes-for-production\#App-Clip-Codes)

Help users discover your App Clip by using an NFC-integrated or scan-only App Clip Code.

[Encoding a URL in an App Clip Code](https://developer.apple.com/documentation/appclip/encoding-a-url-in-an-app-clip-code)

Choose an invocation URL for your App Clip Code that you can encode efficiently.

[Interacting with App Clip Codes in AR](https://developer.apple.com/documentation/appclip/interacting-with-app-clip-codes-in-ar)

Display content and provide services in an AR experience with App Clip Codes.

---

# https://developer.apple.com/documentation/appclip/encoding-a-url-in-an-app-clip-code

- [App Clips](https://developer.apple.com/documentation/appclip)
- Encoding a URL in an App Clip Code

Article

# Encoding a URL in an App Clip Code

Choose an invocation URL for your App Clip Code that you can encode efficiently.

## [Overview](https://developer.apple.com/documentation/appclip/encoding-a-url-in-an-app-clip-code\#overview)

Creating an App Clip Code involves the following key tasks:

- Choosing invocations to support

- Choosing invocation URLs to use in your App Clip Code

- Setting up advanced App Clip experiences

Although App Clip Codes are a great way to launch your App Clip, an App Clip Code can only contain a limited amount of information in its visual code or NFC tag. At the same time, it’s important you choose invocation URLs with additional parameters or attributes that lead to the best possible launch experience for users. This additional information could make your invocation URL too long to encode.

When you create an App Clip Code, you need to find the best tradeoff between the limited capacity to store information in the App Clip Code and the need to encode more information. Therefore, choosing the right URLs to launch your App Clip from an App Clip Code is important.

### [Review App Clip experiences and invocation URLs](https://developer.apple.com/documentation/appclip/encoding-a-url-in-an-app-clip-code\#Review-App-Clip-experiences-and-invocation-URLs)

Users launch your App Clip with an invocation; for example, by tapping a link in the Messages app, by scanning a QR code, or by scanning an App Clip Code. To support invocations from App Clip Codes:

App Clip demo URL

You don’t have to associate your App Clip with your website or create an advanced App Clip experience to use the App Clip demo URL in an App Clip Code. However, you can’t use launch parameters with the demo URL.

default App Clip URL

You can’t use the default App Clip URL in your App Clip Code.

advanced App Clip experiences

Create at least one advanced App Clip experience and associate your App Clip with your website to enable the system to verify your App Clip upon launch. For more information, see [Associating your App Clip with your website](https://developer.apple.com/documentation/appclip/associating-your-app-clip-with-your-website).

When you create an advanced App Clip experience, use a custom URL for your default App Clip experience and your advanced App Clip experiences. For example, create a default App Clip experience that uses `https://example.com` as its invocation URL, and one advanced App Clip experience. The advanced experience’s registered invocation URL might be `https://appclip.example.com`, and takes advantage of prefix matching.

When you use the advanced App Clip experience, you support invocations from QR codes, NFC tags, and App Clip Codes. These invocations use `https://appclip.example.com` as their URL prefix and encode additional information with URL path components or queries. For example, you can encode `https://appclip.example.com/shop?p=123&p1=ab` in an App Clip Code.

For more information, refer to [Configuring App Clip experiences](https://developer.apple.com/documentation/appclip/configuring-the-launch-experience-of-your-app-clip).

### [Choose a valid invocation URL](https://developer.apple.com/documentation/appclip/encoding-a-url-in-an-app-clip-code\#Choose-a-valid-invocation-URL)

- The invocation URL must use the `https` scheme in lowercase.

- The `host` segment is the invocation URL’s _authority component_ and can only contain the lowercase ASCII characters `a` to `z`, `.`, and `-`.

- The invocation URL may have zero or more path and query components, followed by an optional fragment. They can use the following ASCII characters: `a` to `z`, `A` to `Z`, `0` to `9`, and `/#?=%-._,+;:&`.

### [Follow practices that allow for efficient encoding](https://developer.apple.com/documentation/appclip/encoding-a-url-in-an-app-clip-code\#Follow-practices-that-allow-for-efficient-encoding)

An App Clip Code can only contain a limited amount of information, and as a result, the tools you use to create the code compress the encoded invocation URL. The underlying encoding algorithm can encode some words efficiently, while some characters may reduce the algorithm’s efficiency. As a result, the exact length of an invocation URL you can encode in an App Clip Code varies based on the ASCII characters and words you use.

When you create an App Clip Code, both [App Store Connect](https://appstoreconnect.apple.com/) and the [App Clip Code Generator](https://developer.apple.com/app-clips/resources/) command-line tool inform you if your invocation URL is too long.

To ensure you can encode your invocation URL in an App Clip Code:

- Use the minimum number of characters you need to uniquely identify a resource. Long unique identifiers (UUIDs) lower the effectiveness of the encoding.

- Use a short host name with as few subdomains as possible.

- If possible, remove the `www` subdomain from your host name.

- Use decimal numbers as values for query components.

- Replace long query string argument names and values with short strings. For example, use `https://example.com/?p=0` instead of `https://example.com/?status=view`.

- Omit a trailing slash (`/`) character at the end of the URL. For example, use `https://example.com` instead of `https://example.com/`.

### [Use a separate subdomain](https://developer.apple.com/documentation/appclip/encoding-a-url-in-an-app-clip-code\#Use-a-separate-subdomain)

Optionally, you can use the special subdomain `appclip` to define URLs specific to App Clip Codes; for example, `https://appclip.example.com`. The algorithm that generates App Clip Codes encodes this subdomain more efficiently than others. Choosing `appclip` as a subdomain also allows URLs to have short path and query components by eliminating the possibility of conflicts with an unrelated functionality of your website. If you use this subdomain, it must appear as the first subdomain of the URL’s host.

### [Choose a single-word path component](https://developer.apple.com/documentation/appclip/encoding-a-url-in-an-app-clip-code\#Choose-a-single-word-path-component)

If possible, don’t use any path components at all. However, if you must use them, choose from the list below so the algorithm that creates the App Clip Code can encode the path components more efficiently. For example, you might use `https://example.com/brand`.

Always use the fewest possible path components.

- about, access, account, add, app, archives, article, attraction, author

- bag, biz, book, brand, brands, browse, buy

- cancel, cart, cat, catalog, category, categories, channel, charts, checkin, checkout, collection, collections, company, compare, connect, contact, content, contents, cost, coupons, create

- data, demo, destinations, detail, discover, download

- entry, event, events, explore

- faq, fetch, finance, find, food, fund

- game, gift, goods, guide

- health, help, home, hotel, hotels

- id, index, info, item, item\_id

- join

- lifestyle, list, listen, live, local, location, locations, locator, login

- manage, menu, more, music

- name, news, note, open

- order, overview

- park, part, pay, payment, payments, play, post, posts, preview, product, product\_id, products, profile, promotion, purchase

- rate, recipe, recipes, reservation, reservations, reserve, retail, review, rewards

- sale, scan, schedule, search, sell, send, service, share, shop, show, showtime, site, song, special, stations, status, store, store-locator, stores, stories, story

- tag, tags, terms, tickets, tips, title, today, top, topic, tours, track, transaction, travel, try

- update, upload, use, user

- vehicles, video, view, visit

- watch, wiki

Note that the words in the list above don’t lead to more efficient encoding if you use them as a subdomain or query parameter.

### [Use ordered argument names for query components](https://developer.apple.com/documentation/appclip/encoding-a-url-in-an-app-clip-code\#Use-ordered-argument-names-for-query-components)

If you use no path component, or a single-word path component from the above list of special words and query components, use the special ordered argument names `p`, `p1`, `p2`, `p3`, and so on. Doing so increases the likelihood of the URL fitting in an App Clip Code. For example, instead of `https://appclip.example.com/shop?a=123&b=456&c=789`, use `https://appclip.example.com/shop?p=123&p1=456&p2=789`.

### [Hash long URLs](https://developer.apple.com/documentation/appclip/encoding-a-url-in-an-app-clip-code\#Hash-long-URLs)

In some cases, you may need to pass long query strings to the App Clip upon launch that result in a URL that’s too long to encode in an App Clip Code. In this case, you can use a hashing algorithm to shorten the long query string. Upon launch, your app and App Clip can then expand the hash

You may want to reuse URLs you previously created for other purposes in your App Clip Codes; for example, if you created your own tool to create short URLs for use in QR codes. If you do so, you also need to:

- Register each domain that can launch your App Clip in the list of associated domains.

- Set up the AASA file for each domain you use.

- Configure advanced App Clip experiences for both the short and long URLs.

## [See Also](https://developer.apple.com/documentation/appclip/encoding-a-url-in-an-app-clip-code\#see-also)

### [App Clip Codes](https://developer.apple.com/documentation/appclip/encoding-a-url-in-an-app-clip-code\#App-Clip-Codes)

Help users discover your App Clip by using an NFC-integrated or scan-only App Clip Code.

[Preparing multiple App Clip Codes for production](https://developer.apple.com/documentation/appclip/preparing-multiple-app-clip-codes-for-production)

Prepare your App Clip Codes to send to a professional printing service.

[Interacting with App Clip Codes in AR](https://developer.apple.com/documentation/appclip/interacting-with-app-clip-codes-in-ar)

Display content and provide services in an AR experience with App Clip Codes.

---

# https://developer.apple.com/documentation/appclip/enabling-notifications-in-app-clips

- [App Clips](https://developer.apple.com/documentation/appclip)
- Enabling notifications in App Clips

Article

# Enabling notifications in App Clips

Enable your App Clip to schedule and receive notifications for a short or extended time period.

## [Overview](https://developer.apple.com/documentation/appclip/enabling-notifications-in-app-clips\#overview)

Some App Clips may need to schedule or receive notifications to provide value. Consider an App Clip that allows users to order food for delivery: By sending notifications, the App Clip informs the user about an upcoming delivery. If notifications are important for the functionality provided by your App Clip, enable it to schedule or receive notifications for up to 8 hours after each launch. Additionally, if you create an App Clip for multiple businesses, be sure to make changes to your notification payloads.

### [Schedule or receive notifications temporarily](https://developer.apple.com/documentation/appclip/enabling-notifications-in-app-clips\#Schedule-or-receive-notifications-temporarily)

To enable your App Clip to schedule or receive notifications for up to 8 hours after each launch, first add the [`NSAppClip`](https://developer.apple.com/documentation/BundleResources/Information-Property-List/NSAppClip) key to your App Clip’s `Info.plist` file and set its type to `Dictionary`. Then, add an entry to the dictionary with the [`NSAppClipRequestEphemeralUserNotification`](https://developer.apple.com/documentation/BundleResources/Information-Property-List/NSAppClip/NSAppClipRequestEphemeralUserNotification) key. Set its type to `Boolean` and its value to `true`.

Alternatively, open the `Info.plist` file in the property list editor and add the entry by selecting App Clip from the list of keys. This adds the `NSAppClip` key and two entries of type `Boolean` to its dictionary: “Requests ephemeral user notifications” and “Requests location confirmation”. By default, the value for both entries is `NO`. Change the value for “Requests ephemeral user notifications” to `YES`.

As a result, the App Clip card that’s displayed upon invocation of the App Clip contains a note that tells the user about the App Clip’s ability to receive or schedule notifications. This permission is enabled by default, but users can disable it by tapping the note on the App Clip card.

Because users can disable notifications in the App Clip card, add code to check whether the App Clip has permission to schedule and receive notifications. The following code checks whether the user has granted permission to send notifications for a short amount of time:

let center = UNUserNotificationCenter.current()
center.getNotificationSettings { (settings) in {
if settings.authorizationStatus == .ephemeral {

// The user didn’t disable notifications in the App Clip card.
// Add code for scheduling or receiving notifications here.
return
}
}

### [Request explicit permission to send notifications](https://developer.apple.com/documentation/appclip/enabling-notifications-in-app-clips\#Request-explicit-permission-to-send-notifications)

If your App Clip’s functionality spans more than a day, explicitly request the user’s permission to send notifications. For example, a car rental company’s App Clip can ask for permission to receive notifications that remind users when they need to return a rented car.

However, carefully consider whether you should ask for this permission. Users could deny the request, overriding the App Clip’s ability to receive and schedule notifications for up to 8 hours after each launch.

For more information, see [Asking permission to use notifications](https://developer.apple.com/documentation/UserNotifications/asking-permission-to-use-notifications).

### [Make changes to your notification payload](https://developer.apple.com/documentation/appclip/enabling-notifications-in-app-clips\#Make-changes-to-your-notification-payload)

You may create an App Clip for multiple businesses. For example, you may be a platform provider for restaurants and create an App Clip that serves many different restaurants. If a user launches the App Clip consecutively for several different businesses within a short amount of time, multiple instances of the App Clip may exist on their device.

In this case, when it receives a notification, the system needs to route the notification to the appropriate App Clip instance. As a result, the system requires notification payloads to contain a URL as the target content identifier. The following code shows the notification payload for an App Clip that serves multiple businesses:

{
"aps" : {
"alert" : {
"title" : "Order Status",
"subtitle" : "Restaurant A",
"body" : "Your order is ready."
},
"category" : "order_status",
"target-content-id" : "https://example.com/restaurants/restaurant_a/order/1234"
}
}

The value for the `target-content-id` must be a URL that matches a corresponding advanced App Clip experience. For the restaurant example, you’d register both URLs in [App Store Connect](https://appstoreconnect.apple.com/login):

- `https://example.com/restaurants/restaurant_a`

- `https://example.com/restaurants/restaurant_b`

The invocation URLs and target content identifiers could then be:

- `https://example.com/restaurants/restaurant_a/order/1234`

- `https://example.com/restaurants/restaurant_b/order/5678`

In general, use a target content identifier that’s as specific as possible. Similarly, if you enable your App Clip to schedule local notifications, set the target content identifier for the notification payload; for example, using [`targetContentIdentifier`](https://developer.apple.com/documentation/UserNotifications/UNNotificationContent/targetContentIdentifier).

For more information, see [Configuring App Clip experiences](https://developer.apple.com/documentation/appclip/configuring-the-launch-experience-of-your-app-clip), [Generating a remote notification](https://developer.apple.com/documentation/UserNotifications/generating-a-remote-notification), and [Scheduling a notification locally from your app](https://developer.apple.com/documentation/UserNotifications/scheduling-a-notification-locally-from-your-app).

---

# https://developer.apple.com/documentation/appclip/recommending-your-app-to-app-clip-users

- [App Clips](https://developer.apple.com/documentation/appclip)
- Recommending your app to App Clip users

Article

# Recommending your app to App Clip users

Display an overlay in your App Clip to recommend your app to users.

## [Overview](https://developer.apple.com/documentation/appclip/recommending-your-app-to-app-clip-users\#overview)

App Clips only remain on a device for a limited amount of time. If someone uses an App Clip regularly, they might want to get the corresponding app to use additional features and have the app on their home screen. With [`SKOverlay`](https://developer.apple.com/documentation/StoreKit/SKOverlay), you can recommend your full app to users and enable them to install it from within your App Clip.

If you’re using SwiftUI, make use of the [`appStoreOverlay(isPresented:configuration:)`](https://developer.apple.com/documentation/SwiftUI/View/appStoreOverlay(isPresented:configuration:)) modifier. For example usage, see [Fruta: Building a feature-rich app with SwiftUI](https://developer.apple.com/documentation/appclip/fruta-building-a-feature-rich-app-with-swiftui).

To display an overlay when using [UIKit](https://developer.apple.com/documentation/UIKit):

1. Create an [`SKOverlay.AppClipConfiguration`](https://developer.apple.com/documentation/StoreKit/SKOverlay/AppClipConfiguration) object.

2. Initialize [`SKOverlay`](https://developer.apple.com/documentation/StoreKit/SKOverlay) with the configuration object.

3. Present the overlay.

The following code displays the overlay at the bottom of the visible scene:

func displayOverlay() {
guard let scene = view.window?.windowScene else { return }

let config = SKOverlay.AppClipConfiguration(position: .bottom)
let overlay = SKOverlay(configuration: config)
overlay.present(in: scene)
}

To respond to the overlay’s appearance, dismissal, or failure to load, set the [`delegate`](https://developer.apple.com/documentation/StoreKit/SKOverlay/delegate), and implement the methods defined in [`SKOverlayDelegate`](https://developer.apple.com/documentation/StoreKit/SKOverlayDelegate).

## [See Also](https://developer.apple.com/documentation/appclip/recommending-your-app-to-app-clip-users\#see-also)

### [App Clip to full app transition](https://developer.apple.com/documentation/appclip/recommending-your-app-to-app-clip-users\#App-Clip-to-full-app-transition)

[Sharing data between your App Clip and your full app](https://developer.apple.com/documentation/appclip/sharing-data-between-your-app-clip-and-your-full-app)

Use CloudKit, Sign in with Apple, shared user defaults or containers, and the keychain to offer a smooth transition from your App Clip to your app.

---

# https://developer.apple.com/documentation/appclip/creating-an-app-clip-with-xcode

- [App Clips](https://developer.apple.com/documentation/appclip)
- Creating an App Clip with Xcode

Article

# Creating an App Clip with Xcode

Add an App Clip target to your Xcode project and share code between the App Clip and its corresponding full app.

## [Overview](https://developer.apple.com/documentation/appclip/creating-an-app-clip-with-xcode\#overview)

An _App Clip_ is a lightweight version of your app that offers some of its functionality when and where people need it or that people use to try out your full app. With Xcode, you can add an App Clip target to your app’s project, share code and assets between the App Clip and the full app, and build, run, and debug your App Clip.

### [Add an App Clip target](https://developer.apple.com/documentation/appclip/creating-an-app-clip-with-xcode\#Add-an-App-Clip-target)

App Clips require a corresponding full app that offers at least the same functionality as the App Clip; you use the same Xcode project for your full app and your App Clip. If you’re starting a new app project, first create a new iOS project with Xcode. If you want to add an App Clip to your existing iOS app, open its Xcode project. Then, add an App Clip target to the Xcode project:

1. Add a new target using the App Clip template.

2. Choose a product name, select applicable options for your App Clip, and click Finish.

Xcode creates all required files for the options you choose and adds a target for your App Clip with:

- A scheme to build and run your App Clip and its tests

- A new capability named On Demand Install Capable that adds the [`com.apple.developer.on-demand-install-capable`](https://developer.apple.com/documentation/BundleResources/Entitlements/com.apple.developer.on-demand-install-capable) entitlement

- The [`Parent Application Identifiers Entitlement`](https://developer.apple.com/documentation/BundleResources/Entitlements/com.apple.developer.parent-application-identifiers)

- An app identifier for the App Clip, using the full app’s app identifier as its prefix, followed by a string. For example, if your full app’s app identifier is `$(AppIdentifierPrefix)com.example.MyApp`, the app identifier for your App Clip would be `$(AppIdentifierPrefix)com.example.MyApp.Clip`

- The `_XCAppClipURL` environment variable for the scheme of your App Clip that allows you to debug invocations

- Support for the same devices as the full app, not including macOS

Additionally, Xcode creates a new build phase for the app target that embeds the App Clip in the app.

Before you add code to the App Clip target, run the App Clip in Simulator or on a device. At this point, the App Clip shows an empty white screen because you haven’t yet added any code and assets to the App Clip target.

### [Add code and assets](https://developer.apple.com/documentation/appclip/creating-an-app-clip-with-xcode\#Add-code-and-assets)

App Clips make use of the same frameworks as full apps, and adding code or assets to an App Clip target works just like it does for any other target. Create new source files and assets, or use existing source files and assets, and add them as members to the App Clip target. To ensure the project’s maintainability, both the full app and the App Clip should share as much code as possible:

- If you create a new app, build it with creating an App Clip in mind, and follow best practices that promote a modular code base. For example, create reusable components, bundle them as [Swift packages](https://developer.apple.com/documentation/Xcode/swift-packages), and use the packages in both the full app and the App Clip. For more information, see [Organizing your code with local packages](https://developer.apple.com/documentation/Xcode/organizing-your-code-with-local-packages).

- If you add an App Clip to an existing app, set aside time to refactor the app’s code base to be modular and share code between the App Clip and the full app to avoid duplicating code.

- Add shared assets to a new asset catalog, and use the catalog in both the full app and the App Clip. For more information about asset catalogs, see [Managing assets with asset catalogs](https://developer.apple.com/documentation/Xcode/managing-assets-with-asset-catalogs).

### [Verify the size of your App Clip](https://developer.apple.com/documentation/appclip/creating-an-app-clip-with-xcode\#Verify-the-size-of-your-App-Clip)

Your App Clips must be small to launch instantly. Aim to keep your App Clip well below the applicable limits outlined in [Choosing the right functionality for your App Clip](https://developer.apple.com/documentation/appclip/choosing-the-right-functionality-for-your-app-clip).

To measure the size of your App Clip, create an app-size report for your App Clip:

1. In Xcode, archive the app that belongs to your App Clip, open the Organizer window, select the archive, and click Distribute App.

2. Export the App Clip as an Ad Hoc or Development build with App Thinning enabled.

The output folder for your exported App Clip contains its size report, a file named `App Thinning Size Report.txt`. Open the text file, note the uncompressed size of your App Clip for each variant, and then make adjustments to your project to keep the uncompressed size for each variant below the applicable size limit.

For more information on measuring your app’s size, see [Reducing your app’s size](https://developer.apple.com/documentation/Xcode/reducing-your-app-s-size).

### [Download additional assets](https://developer.apple.com/documentation/appclip/creating-an-app-clip-with-xcode\#Download-additional-assets)

App Clips can use [Background Assets](https://developer.apple.com/documentation/BackgroundAssets) to download additional content. If your App Clip offers an in-the-moment experience, ensure instant availability by keeping the App Clip as small as possible and avoiding usage of Background Assets.

If you create an App Clip to offer a demo version of your app or your game, and are confident that people have a reliable and fast network connection when they invoke your App Clip, use Background Assets to down additional content. For example, the App Clip demo of a game might include assets needed for people to start the demo and create their in-game hero. To keep the App Clip small, it might not include the assets needed to play the first three levels of the game but downloads them while people create their hero.

To download additional assets in the background, make sure you configure Background Assets for your app and App Clip targets. Note that your App Clip can’t set a background asset download’s priority to essential with [`isEssential`](https://developer.apple.com/documentation/BackgroundAssets/BADownload/isEssential).

### [Use active compilation conditions](https://developer.apple.com/documentation/appclip/creating-an-app-clip-with-xcode\#Use-active-compilation-conditions)

Adding an App Clip to your app is a good opportunity to refactor your app’s code to be modular and reusable. Most functionality and frameworks available to your full app are available to your App Clip. However, you may encounter cases where you can’t use some of your app’s code in the App Clip, and creating separate modules for your app and App Clip code isn’t feasible. In these cases, take advantage of the Active Compilation Conditions build setting, where you can declare a condition to exclude code.

Start by navigating to your App Clip target’s build settings and creating a new value for the Active Compilation Condition build setting (for example, `APPCLIP`). Then, add a check in your shared code where needed, to exclude code you don’t want to use in your App Clip.

The following code checks for the `APPCLIP` value you added to the Active Compilation Conditions build setting:

#if !APPCLIP
// Code you don’t want to use in your App Clip.
#else
// Code your App Clip may access.
#endif

### [Review next steps](https://developer.apple.com/documentation/appclip/creating-an-app-clip-with-xcode\#Review-next-steps)

Adding an App Clip target to your app’s Xcode project and modifying the project are only the first steps in offering an App Clip. Next, plan to spend time designing the launch experience of your App Clip by:

- Reviewing how invocations work

- Identifying invocations you want to support

- Planning which URLs launch your App Clip

- Changing your code to respond to invocations

Based on the decisions you make, you’ll use [App Store Connect](https://appstoreconnect.apple.com/) to:

- Configure the required default App Clip experience

- Use the default App Clip link or the App Clip demo link

- Configure optional advanced App Clip experience

- Add code to respond to different invocation URLs

- Create App Clip Codes

To learn more about the App Clip launch experience for your App Clip, see [Configuring App Clip experiences](https://developer.apple.com/documentation/appclip/configuring-the-launch-experience-of-your-app-clip) and [Responding to invocations](https://developer.apple.com/documentation/appclip/responding-to-invocations).

You may also have to associate your App Clip with your website and make changes to your server. For more information, refer to [Associating your App Clip with your website](https://developer.apple.com/documentation/appclip/associating-your-app-clip-with-your-website).

When it’s time to test your App Clip, use Xcode to test the launch experience locally or test it with [TestFlight](https://developer.apple.com/testflight/). For more information, see [Testing the launch experience of your App Clip](https://developer.apple.com/documentation/appclip/testing-the-launch-experience-of-your-app-clip).

## [See Also](https://developer.apple.com/documentation/appclip/creating-an-app-clip-with-xcode\#see-also)

### [Creation](https://developer.apple.com/documentation/appclip/creating-an-app-clip-with-xcode\#Creation)

[Fruta: Building a feature-rich app with SwiftUI](https://developer.apple.com/documentation/appclip/fruta-building-a-feature-rich-app-with-swiftui)

Create a shared codebase to build a multiplatform app that offers widgets and an App Clip.

[`Parent Application Identifiers Entitlement`](https://developer.apple.com/documentation/BundleResources/Entitlements/com.apple.developer.parent-application-identifiers)

A list of parent application identifiers for an App Clip with exactly one entry.

[`com.apple.developer.associated-appclip-app-identifiers`](https://developer.apple.com/documentation/BundleResources/Entitlements/com.apple.developer.associated-appclip-app-identifiers)

A list of App Clip identifiers for an app with exactly one entry.

[`com.apple.developer.on-demand-install-capable`](https://developer.apple.com/documentation/BundleResources/Entitlements/com.apple.developer.on-demand-install-capable)

A Boolean value that indicates whether a bundle represents an App Clip.

---

# https://developer.apple.com/documentation/appclip/confirming-a-person-s-physical-location

- [App Clips](https://developer.apple.com/documentation/appclip)
- Confirming a person’s physical location

Article

# Confirming a person’s physical location

Add code to quickly confirm a person’s physical location while respecting their privacy.

## [Overview](https://developer.apple.com/documentation/appclip/confirming-a-person-s-physical-location\#overview)

If you create an App Clip that people invoke at a physical location, you may need to confirm a person’s location before allowing them to perform a task. For a quick launch and to preserve user privacy, App Clips use a lightweight mechanism in which the system verifies that a person is at a specific, expected location. When you adopt this mechanism, and when people allow it, the _App Clip card_ contains a note that tells people that the App Clip can verify their location. They can disable location verification by tapping the note on the App Clip card.

### [Enable your App Clip to verify a person’s location](https://developer.apple.com/documentation/appclip/confirming-a-person-s-physical-location\#Enable-your-App-Clip-to-verify-a-persons-location)

To enable your App Clip to verify the person’s location, modify your App Clip’s `Info.plist` file:

1. Open your App Clip’s `Info.plist`, add the [`NSAppClip`](https://developer.apple.com/documentation/BundleResources/Information-Property-List/NSAppClip) key, and set its type to `Dictionary`.

2. Add an entry to the dictionary with [`NSAppClipRequestLocationConfirmation`](https://developer.apple.com/documentation/BundleResources/Information-Property-List/NSAppClip/NSAppClipRequestLocationConfirmation) as the key, select `Boolean` as its type, and set its value to `true`.

Alternatively, open the `Info.plist` file in the property list editor and add the entry by selecting App Clip from the list of keys. This adds the [`NSAppClip`](https://developer.apple.com/documentation/BundleResources/Information-Property-List/NSAppClip) key and the following entries of type `Boolean` to its dictionary: “Requests ephemeral user notifications” and “Requests location confirmation.” Per default, the value for both entries is `NO`. Change the value for “Requests location confirmation” to `YES`.

### [Add code that verifies the physical location](https://developer.apple.com/documentation/appclip/confirming-a-person-s-physical-location\#Add-code-that-verifies-the-physical-location)

After you modify your App Clip’s `Info.plist` file, add code to provide the expected physical location information to the App Clip. To retrieve this information, encode an identifier in the URL that launches the App Clip, and use the identifier to look up the location information for a business in your database. Alternatively, encode the location information in the URL that launches the App Clip.

On launch, access the location information, use it to create a [`CLCircularRegion`](https://developer.apple.com/documentation/CoreLocation/CLCircularRegion) object with a radius of up to 500 meters, and pass it to the [`confirmAcquired(in:completionHandler:)`](https://developer.apple.com/documentation/appclip/apactivationpayload/confirmacquired(in:completionhandler:)) function.

The following code verifies a person’s location when they launch the App Clip. Make sure to update your user interface for each possible result, including the case where a person denies access to location services on their device.

import UIKit
import AppClip
import CoreLocation

class SceneDelegate: UIResponder, UIWindowSceneDelegate {

var window: UIWindow?

// Call the verifyUserLocation(_:) function in all applicable lifecycle callbacks.

func verifyUserLocation(_ activity: NSUserActivity?) {

// Guard against faulty data.
guard activity != nil else { return }
guard activity!.activityType == NSUserActivityTypeBrowsingWeb else { return }
guard let payload = activity!.appClipActivationPayload else { return }
guard let incomingURL = activity?.webpageURL else { return }

// Create a CLRegion object.
guard let region = location(from: incomingURL) else {
// Respond to parsing errors here.
return
}

// Verify that the invocation happened at the expected location.
payload.confirmAcquired(in: region) { (inRegion, error) in
guard let confirmationError = error as? APActivationPayloadError else {
if inRegion {
// The location of the NFC tag matches a person's location.
} else {
// The location of the NFC tag doesn't match the records,
// for example, if someone moved the NFC tag.
}
return
}

if confirmationError.code == .doesNotMatch {
// The scanned URL isn't registered for the App Clip.
} else {
// A person denied location access, or the source of the
// App Clip’s invocation isn't an NFC tag or visual code.
}
}
}

let coordinates = CLLocationCoordinate2D(latitude: 37.334722,
longitude: 122.008889)
return CLCircularRegion(center: coordinates,
radius: 100,
identifier: "Apple Park")
}
}

For more information on how you can access the App Clip’s invocation URL, refer to [Responding to invocations](https://developer.apple.com/documentation/appclip/responding-to-invocations).

## [See Also](https://developer.apple.com/documentation/appclip/confirming-a-person-s-physical-location\#see-also)

### [Launch](https://developer.apple.com/documentation/appclip/confirming-a-person-s-physical-location\#Launch)

[Responding to invocations](https://developer.apple.com/documentation/appclip/responding-to-invocations)

Add code to respond to invocations and offer a focused launch experience.

[Associating your App Clip with your website](https://developer.apple.com/documentation/appclip/associating-your-app-clip-with-your-website)

Enable the system to verify your App Clip to support invocations from your website and devices running iOS 16.3 or earlier.

[Supporting invocations from your website and the Messages app](https://developer.apple.com/documentation/appclip/supporting-invocations-from-your-website-and-the-messages-app)

Display a Smart App Banner and the App Clip card on your website that people tap to launch your App Clip, and add support for invocations from the Messages app.

[Launching another app’s App Clip from your app](https://developer.apple.com/documentation/appclip/launching-another-app-s-app-clip-from-your-app)

Enable people to launch another app’s App Clip from your app with App Clip links and offer a rich preview of it with the Link Presentation framework.

[`class APActivationPayload`](https://developer.apple.com/documentation/appclip/apactivationpayload)

Information that’s passed to an App Clip on launch.

[`NSAppClip`](https://developer.apple.com/documentation/BundleResources/Information-Property-List/NSAppClip)

A collection of keys that an App Clip uses to get additional capabilities.

---

# https://developer.apple.com/documentation/appclip/associating-your-app-clip-with-your-website

- [App Clips](https://developer.apple.com/documentation/appclip)
- Associating your App Clip with your website

Article

# Associating your App Clip with your website

Enable the system to verify your App Clip to support invocations from your website and devices running iOS 16.3 or earlier.

## [Overview](https://developer.apple.com/documentation/appclip/associating-your-app-clip-with-your-website\#overview)

An App Clip gives people quick access to a particular workflow in your app, even when a person hasn’t installed your app. NFC readers, App Clip Codes, or QR codes define an _invocation URL_ that specifies which App Clip, or workflow within your full app, the system needs to run. If you want to support invocations from your website or support iOS 16.3 and earlier, enable the system to verify your App Clip. The system’s verification checks that the App Clip includes the URL in its code signature as the [`Associated Domains Entitlement`](https://developer.apple.com/documentation/BundleResources/Entitlements/com.apple.developer.associated-domains), which cites the invocation URL’s domain. The system also verifies that the server of the domain agrees to launch the App Clip, by citing the App Clip within an Apple App Site Association (AASA) file that it hosts.

To associate your app and App Clip with your website:

- Specify your invocation URL’s domain within an [`Associated Domains Entitlement`](https://developer.apple.com/documentation/BundleResources/Entitlements/com.apple.developer.associated-domains) on both your app and App Clip targets in Xcode.

- Add or modify an AASA file on the domain’s server.

The system verifies that both the entitlement and the configuration in the AASA file match before it permits the invocation of the App Clip. App Store Connect also verifies the match when you create an App Clip experience; for more information, refer to [Set up an App Clip experience](https://help.apple.com/app-store-connect/#/dev43c15c696).

### [Add the Associated Domains entitlement](https://developer.apple.com/documentation/appclip/associating-your-app-clip-with-your-website\#Add-the-Associated-Domains-entitlement)

To associate your App Clip with your website, you must add the [`Associated Domains Entitlement`](https://developer.apple.com/documentation/BundleResources/Entitlements/com.apple.developer.associated-domains) to the app and the App Clip targets.

First, open your project in Xcode; then, in your project settings, enable the Associated Domains capability to add the [`Associated Domains Entitlement`](https://developer.apple.com/documentation/BundleResources/Entitlements/com.apple.developer.associated-domains).

### [Make changes to your server](https://developer.apple.com/documentation/appclip/associating-your-app-clip-with-your-website\#Make-changes-to-your-server)

In addition to adding the [`Associated Domains Entitlement`](https://developer.apple.com/documentation/BundleResources/Entitlements/com.apple.developer.associated-domains) to your Xcode project, you need to make changes to your server to associate your App Clip with your server and allow the system to verify the URL that tries to invoke your App Clip.

First, create an AASA file as described in [Supporting associated domains](https://developer.apple.com/documentation/Xcode/supporting-associated-domains). Next, add an entry for the App Clip with the `appclips` key to the file.

The following code shows the content to add. Note how the value for the `apps` key is an array that contains the app identifier of the App Clip. In many cases, the array contains only one entry. However, it can contain entries for multiple App Clips.

{
"appclips": {
"apps": ["ABCDE12345.com.example.MyApp.Clip"]
}
...
}

Then, add the AASA file to your website’s `.well-known` directory. If you previously added an AASA file to your server, add the entry for the `appclips` key to the existing file.

Finally, to make sure the system can validate the association between your App Clip and the AASA file on your server, check your server’s configuration and make sure it allows `AASA-Bot` and `CFNetwork` as user agents.

### [Check the validation status of your App Clip](https://developer.apple.com/documentation/appclip/associating-your-app-clip-with-your-website\#Check-the-validation-status-of-your-App-Clip)

App Store Connect verifies the AASA file configuration of your App Clip after you’ve uploaded a build to App Store Connect and created an App Clip experience. To check the verification status:

1. Open [App Store Connect](https://appstoreconnect.apple.com/) in your browser and navigate to a build’s details page.

2. Click View Status in the App Clip section to show the domain validation status. It shows the validation status for each domain that’s associated with your App Clip.

For example, you could configure the default App Clip experience to use `https://example.com` as its invocation URL and configure an advanced App Clip experience to use `https://appclip.example.com`. In this example, you’d place an AASA file in the `.well-known` directories for each URL’s domain, and App Store Connect would show the verification status for both domains.

The Cache Status column shows the validation status for your App Clip as the system performs the validation on people’s devices. As you develop your App Clip, you may make frequent changes to your AASA file. To check the verification status in real time, click Load Debug Status in the modal view that shows the verification status of your App Clip. If a configuration error occurs, App Store Connect shows information about the error in the Debug Status column.

For more information, refer to [WWDC20: What’s New in App Store Connect](https://developer.apple.com/videos/play/wwdc2020/10651/).

## [See Also](https://developer.apple.com/documentation/appclip/associating-your-app-clip-with-your-website\#see-also)

### [Launch](https://developer.apple.com/documentation/appclip/associating-your-app-clip-with-your-website\#Launch)

[Responding to invocations](https://developer.apple.com/documentation/appclip/responding-to-invocations)

Add code to respond to invocations and offer a focused launch experience.

[Supporting invocations from your website and the Messages app](https://developer.apple.com/documentation/appclip/supporting-invocations-from-your-website-and-the-messages-app)

Display a Smart App Banner and the App Clip card on your website that people tap to launch your App Clip, and add support for invocations from the Messages app.

[Confirming a person’s physical location](https://developer.apple.com/documentation/appclip/confirming-a-person-s-physical-location)

Add code to quickly confirm a person’s physical location while respecting their privacy.

[Launching another app’s App Clip from your app](https://developer.apple.com/documentation/appclip/launching-another-app-s-app-clip-from-your-app)

Enable people to launch another app’s App Clip from your app with App Clip links and offer a rich preview of it with the Link Presentation framework.

[`class APActivationPayload`](https://developer.apple.com/documentation/appclip/apactivationpayload)

Information that’s passed to an App Clip on launch.

[`NSAppClip`](https://developer.apple.com/documentation/BundleResources/Information-Property-List/NSAppClip)

A collection of keys that an App Clip uses to get additional capabilities.

---

# https://developer.apple.com/documentation/appclip/apactivationpayload

- [App Clips](https://developer.apple.com/documentation/appclip)
- APActivationPayload

Class

# APActivationPayload

Information that’s passed to an App Clip on launch.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+

class APActivationPayload

## [Overview](https://developer.apple.com/documentation/appclip/apactivationpayload\#overview)

When users launch an App Clip, the platform passes an activation payload to the App Clip as part of an [`NSUserActivity`](https://developer.apple.com/documentation/Foundation/NSUserActivity) object. When the App Clip receives the payload, confirm the user’s physical location at the time of the invocation.

For more information, see [Responding to invocations](https://developer.apple.com/documentation/appclip/responding-to-invocations).

## [Topics](https://developer.apple.com/documentation/appclip/apactivationpayload\#topics)

### [Passing data to the App Clip](https://developer.apple.com/documentation/appclip/apactivationpayload\#Passing-data-to-the-App-Clip)

[`var url: URL?`](https://developer.apple.com/documentation/appclip/apactivationpayload/url)

The URL of the link that launched the App Clip.

### [Confirming a person’s physical location](https://developer.apple.com/documentation/appclip/apactivationpayload\#Confirming-a-persons-physical-location)

Checks whether an App Clip invocation happened at an expected physical location.

### [Understanding errors](https://developer.apple.com/documentation/appclip/apactivationpayload\#Understanding-errors)

[`let APActivationPayloadErrorDomain: String`](https://developer.apple.com/documentation/appclip/apactivationpayloaderrordomain)

A string that identifies the activation payload’s error domain.

[`struct APActivationPayloadError`](https://developer.apple.com/documentation/appclip/apactivationpayloaderror)

An error that an App Clip activation payload returns.

[`enum Code`](https://developer.apple.com/documentation/appclip/apactivationpayloaderror/code)

Error codes that an App Clip activation payload returns.

## [Relationships](https://developer.apple.com/documentation/appclip/apactivationpayload\#relationships)

### [Inherits From](https://developer.apple.com/documentation/appclip/apactivationpayload\#inherits-from)

- [`NSObject`](https://developer.apple.com/documentation/ObjectiveC/NSObject-swift.class)

### [Conforms To](https://developer.apple.com/documentation/appclip/apactivationpayload\#conforms-to)

- [`CVarArg`](https://developer.apple.com/documentation/Swift/CVarArg)
- [`CustomDebugStringConvertible`](https://developer.apple.com/documentation/Swift/CustomDebugStringConvertible)
- [`CustomStringConvertible`](https://developer.apple.com/documentation/Swift/CustomStringConvertible)
- [`Equatable`](https://developer.apple.com/documentation/Swift/Equatable)
- [`Hashable`](https://developer.apple.com/documentation/Swift/Hashable)
- [`NSCoding`](https://developer.apple.com/documentation/Foundation/NSCoding)
- [`NSCopying`](https://developer.apple.com/documentation/Foundation/NSCopying)
- [`NSObjectProtocol`](https://developer.apple.com/documentation/ObjectiveC/NSObjectProtocol)
- [`NSSecureCoding`](https://developer.apple.com/documentation/Foundation/NSSecureCoding)

## [See Also](https://developer.apple.com/documentation/appclip/apactivationpayload\#see-also)

### [Launch](https://developer.apple.com/documentation/appclip/apactivationpayload\#Launch)

[Responding to invocations](https://developer.apple.com/documentation/appclip/responding-to-invocations)

Add code to respond to invocations and offer a focused launch experience.

[Associating your App Clip with your website](https://developer.apple.com/documentation/appclip/associating-your-app-clip-with-your-website)

Enable the system to verify your App Clip to support invocations from your website and devices running iOS 16.3 or earlier.

[Supporting invocations from your website and the Messages app](https://developer.apple.com/documentation/appclip/supporting-invocations-from-your-website-and-the-messages-app)

Display a Smart App Banner and the App Clip card on your website that people tap to launch your App Clip, and add support for invocations from the Messages app.

[Confirming a person’s physical location](https://developer.apple.com/documentation/appclip/confirming-a-person-s-physical-location)

Add code to quickly confirm a person’s physical location while respecting their privacy.

[Launching another app’s App Clip from your app](https://developer.apple.com/documentation/appclip/launching-another-app-s-app-clip-from-your-app)

Enable people to launch another app’s App Clip from your app with App Clip links and offer a rich preview of it with the Link Presentation framework.

[`NSAppClip`](https://developer.apple.com/documentation/BundleResources/Information-Property-List/NSAppClip)

A collection of keys that an App Clip uses to get additional capabilities.

---

# https://developer.apple.com/documentation/appclip/offering-live-activities-with-your-app-clip

- [App Clips](https://developer.apple.com/documentation/appclip)
- Offering Live Activities with your App Clip

Article

# Offering Live Activities with your App Clip

Add a widget extension to your App Clip target and use ActivityKit to display Live Activities on the Lock Screen and in the Dynamic Island.

## [Overview](https://developer.apple.com/documentation/appclip/offering-live-activities-with-your-app-clip\#overview)

With Live Activities, you can display live event data on the iPhone Lock Screen and in the Dynamic Island on supported devices. Your App Clip can’t typically include app extensions, but starting with iOS 16 you can include a widget extension that offers Live Activities and displays live event data without requiring people to install your full app. For example, a sports app could display App Clip Codes at a game location to offer an App Clip to attendees of the current game. When a person launches the App Clip from the App Clip Code, the App Clip could offer a Live Activity to track a game that happens at the same time but in another city. The Live Activity enables people who watch the game in person to stay informed about another team’s game that happens in parallel.

To offer a Live Activity from your App Clip:

1. Open your project in Xcode.

2. Add a widget extension target to your project and make sure to only add it to the App Clip target.

3. Make sure the widget extension only contains the Live Activity — widgets for the Home Screen, Lock Screen, or Today View aren’t available to App Clips. Remove any widget code that the Xcode template generates and only keep the Live Activity code. For example, remove the widget from the widget bundle that the template creates and only include the Live Activity in the widget bundle.

4. Add the App Clip Extension capability to your new widget extension. It adds the [`com.apple.developer.on-demand-install-capable`](https://developer.apple.com/documentation/BundleResources/Entitlements/com.apple.developer.on-demand-install-capable) entitlement to the widget extension target. This capability is a requirement that allows the App Clip to include the widget extension.

5. Make sure the widget extension target uses the bundle identifier of the App Clip as a prefix to fulfill the bundle ID requirements for extensions. For example, if your App Clip has the bundle ID `com.example.exampleapp.clip`, the widget extension must use `com.example.exampleapp.clip.$thing`, where `$thing` is something like `widgetextension` or `liveactivities`.

When you’ve added the widget extension to your App Clip to offer Live Activities, add code for your Live Activity as described in [Displaying live data with Live Activities](https://developer.apple.com/documentation/ActivityKit/displaying-live-data-with-live-activities). For more information about Live Activities, refer to [ActivityKit](https://developer.apple.com/documentation/ActivityKit).

---

# https://developer.apple.com/documentation/appclip/supporting-invocations-from-your-website-and-the-messages-app

- [App Clips](https://developer.apple.com/documentation/appclip)
- Supporting invocations from your website and the Messages app

Article

# Supporting invocations from your website and the Messages app

Display a Smart App Banner and the App Clip card on your website that people tap to launch your App Clip, and add support for invocations from the Messages app.

## [Overview](https://developer.apple.com/documentation/appclip/supporting-invocations-from-your-website-and-the-messages-app\#overview)

When you create your App Clip, register a _default App Clip experience_. By creating a default App Clip experience, you lay the foundation for supporting _invocations_ from a Smart App Banner on your website. This has an added benefit: If a person shares a link to your website in the Messages app and the website displays a Smart App Banner, the recipient can tap the link to instantly launch your App Clip.

Additionally, you can display the App Clip card on your website if a person’s device runs iOS 15 or later. This makes your App Clip even more discoverable and reduces the number of taps required to launch your App Clip.

Note that the Smart App Banner only appears on your website if:

- You associated your App Clip with the website where you want to display the banner.

- You added the banner to your website’s source code.

- You configured the default App Clip experience.

- You published a version of your app that offers an App Clip.

- A person opens the website in an [`SFSafariViewController`](https://developer.apple.com/documentation/SafariServices/SFSafariViewController) or in Safari without Private Browsing enabled.

With the App Clip card on your website, people don’t need to tap the Smart App Banner for the card to appear. Alternatively, they can choose to view the website with the Smart App Banner instead of launching the App Clip. Both Safari and an [`SFSafariViewController`](https://developer.apple.com/documentation/SafariServices/SFSafariViewController) remember the person’s decision and won’t display the App Clip card when they visit the site again.

### [Add code to display the Smart App Banner and the App Clip Card on your website](https://developer.apple.com/documentation/appclip/supporting-invocations-from-your-website-and-the-messages-app\#Add-code-to-display-the-Smart-App-Banner-and-the-App-Clip-Card-on-your-website)

In most cases, the best time to add the Smart App Banner and the App Clip card to your website is while you associate your App Clip with your website. Add both by including the following HTML `meta` tag and replacing all placeholders with the appropriate values:

Note how the `meta` tag’s `content` attribute includes the `app-clip-bundle-id`, `app-id`, and `app-clip-display` parameters. By including the `app-id` parameter, you enable the Smart App Banner to open the full app on devices that run iOS 13 or earlier and on devices where Screen Time or a mobile device management (MDM) profile don’t allow App Clips. By including the `app-clip-display` parameter, you display the App Clip card in Safari or an [`SFSafariViewController`](https://developer.apple.com/documentation/SafariServices/SFSafariViewController) on devices running iOS 15 or later.

Note that the value of a Smart App Banner’s `app-argument` attribute isn’t available to App Clips.

### [Support invocations from links people share in Messages](https://developer.apple.com/documentation/appclip/supporting-invocations-from-your-website-and-the-messages-app\#Support-invocations-from-links-people-share-in-Messages)

When you add the `meta` tag to your webpage to support invocations from Safari or an [`SFSafariViewController`](https://developer.apple.com/documentation/SafariServices/SFSafariViewController), you automatically add support for invocations from links people share with others in the Messages app. When a person shares a link to the website that displays the banner or App Clip card, the recipient can tap the link to instantly launch your App Clip.

Sharing your App Clip in Messages requires that the recipient’s device:

- Runs iOS 14 or later

- Contains the sender as a contact in the Contacts app

If a person shares the link with someone else as an SMS, the recipient must opt to load the rich link before they can tap the preview to launch the App Clip.

In addition to the above requirements, you must provide the preview image that appears in the Messages app. To provide the preview image:

2. Replace the value of the `content` attribute with the URL of the preview image. Typically, this is the same image you use on the App Clip card. For additional information on displaying link previews in Messages, see [Best Practices for Link Previews in Messages](https://developer.apple.com/library/archive/technotes/tn2444/_index.html).

To enable your App Clip or full app to respond to the invocation from a website that displays the Smart App Banner or the App Clip card in Safari, retrieve the website’s URL upon invocation. Then, use the URL to update the interface of your App Clip to best match the content on the website. For more information on accessing the invocation URL, see [Responding to invocations](https://developer.apple.com/documentation/appclip/responding-to-invocations).

### [Add the Smart App Banner and App Clip card to multiple websites](https://developer.apple.com/documentation/appclip/supporting-invocations-from-your-website-and-the-messages-app\#Add-the-Smart-App-Banner-and-App-Clip-card-to-multiple-websites)

In some cases, you may want to add the App Clip card and the Smart App Banner to several websites where each site uses its own domain — for example, if your App Clip serves several individual businesses. However, the default App Clip experience offers only one set of metadata. If you want to display the Smart App Banner on multiple websites where tapping each website’s banner displays a different App Clip card for your App Clip:

1. Add the `meta` tags for the Smart App Banner and App Clip card and for the link previews in the Messages app to each website, for example, `https://example.com`, `https://example2.com`, `https://example3.com`, and so on.

2. Associate each website with your App Clip as described in [Associating your App Clip with your website](https://developer.apple.com/documentation/appclip/associating-your-app-clip-with-your-website).

3. Configure the default App Clip experience for one website, likely for a more generic landing page. When people launch the App Clip from the landing page, the App Clip could then allow them to choose a business.

4. Create separate advanced App Clip experiences for `https://example2.com`, `https://example3.com`, and so on, as described in [Configuring App Clip experiences](https://developer.apple.com/documentation/appclip/configuring-the-launch-experience-of-your-app-clip).

5. Use different metadata for each advanced experience you configure; for example, choose custom imagery for the App Clip card.

6. Add code to handle the invocation of your App Clip and to update the interface of your App Clip using the invocation URL — the URL of the website that displays the Smart App Banner or App Clip card. For more information on accessing the invocation URL, see [Responding to invocations](https://developer.apple.com/documentation/appclip/responding-to-invocations).

To avoid associating your App Clip with multiple domains, consider using one domain and use URLs like `https://example.com/business1` or `https://example.com/business2`. By using one domain, you’ll only have to associate your app and App Clip with `https://example.com` and configure an advanced App Clip experience for each URL.

## [See Also](https://developer.apple.com/documentation/appclip/supporting-invocations-from-your-website-and-the-messages-app\#see-also)

### [Launch](https://developer.apple.com/documentation/appclip/supporting-invocations-from-your-website-and-the-messages-app\#Launch)

[Responding to invocations](https://developer.apple.com/documentation/appclip/responding-to-invocations)

Add code to respond to invocations and offer a focused launch experience.

[Associating your App Clip with your website](https://developer.apple.com/documentation/appclip/associating-your-app-clip-with-your-website)

Enable the system to verify your App Clip to support invocations from your website and devices running iOS 16.3 or earlier.

[Confirming a person’s physical location](https://developer.apple.com/documentation/appclip/confirming-a-person-s-physical-location)

Add code to quickly confirm a person’s physical location while respecting their privacy.

[Launching another app’s App Clip from your app](https://developer.apple.com/documentation/appclip/launching-another-app-s-app-clip-from-your-app)

Enable people to launch another app’s App Clip from your app with App Clip links and offer a rich preview of it with the Link Presentation framework.

[`class APActivationPayload`](https://developer.apple.com/documentation/appclip/apactivationpayload)

Information that’s passed to an App Clip on launch.

[`NSAppClip`](https://developer.apple.com/documentation/BundleResources/Information-Property-List/NSAppClip)

A collection of keys that an App Clip uses to get additional capabilities.

---

# https://developer.apple.com/documentation/appclip/creating-app-clip-codes-with-app-store-connect

- [App Clips](https://developer.apple.com/documentation/appclip)
- [Creating App Clip Codes](https://developer.apple.com/documentation/appclip/creating-app-clip-codes)
- Creating App Clip Codes with App Store Connect

Article

# Creating App Clip Codes with App Store Connect

Select one or more advanced App Clip experiences in App Store Connect and create App Clip Codes for users to scan to launch your App Clip.

## [Overview](https://developer.apple.com/documentation/appclip/creating-app-clip-codes-with-app-store-connect\#overview)

By placing an App Clip Code at a physical location or using it in printed or digital marketing materials, you make your App Clip more discoverable. An App Clip Code always uses a design Apple provides, and users instantly recognize and scan it to launch your App Clip. You can generate an App Clip Code with the [App Clip Code Generator](https://developer.apple.com/app-clips/resources/) command-line tool or [App Store Connect](https://appstoreconnect.apple.com/). The latter is especially useful if you prefer a tool that offers a visual interface and lets you:

- Create App Clip Codes for one or more existing advanced App Clip experiences.

- Get color suggestions.

- Experiment with color patterns, verify custom colors, and instantly preview the generated App Clip Code.

- Save your generated App Clip Codes as Scalable Vector Graphics (SVG) files.

### [Select one or more advanced App Clip experiences](https://developer.apple.com/documentation/appclip/creating-app-clip-codes-with-app-store-connect\#Select-one-or-more-advanced-App-Clip-experiences)

[App Store Connect](https://appstoreconnect.apple.com/) offers functionality to create an App Clip Code for one or more advanced App Clip experiences. First, select your app’s latest version; then, under Advanced App Clip Experiences, click Edit Advanced Experiences. Next, click Get App Clip Codes. Select one or more advanced App Clip experiences. (Note that you can only select App Clip experiences with invocation URLs that fit in an App Clip Code.) Finally, click Get Started.

For more information, refer to [Configuring App Clip experiences](https://developer.apple.com/documentation/appclip/configuring-the-launch-experience-of-your-app-clip), [Encoding a URL in an App Clip Code](https://developer.apple.com/documentation/appclip/encoding-a-url-in-an-app-clip-code), and [App Store Connect Help](https://help.apple.com/app-store-connect/#/dev43c15c696).

### [Create one or more App Clip Codes](https://developer.apple.com/documentation/appclip/creating-app-clip-codes-with-app-store-connect\#Create-one-or-more-App-Clip-Codes)

[App Store Connect](https://appstoreconnect.apple.com/) guides you through the process of creating an App Clip Code for each selected experience. If you select more than one advanced App Clip experience and click Get Started, App Store Connect generates an App Clip Code for each experience with the same type, color, and design.

If you select a single advanced App Clip experience and click Get Started, you can do either of the following:

- Create just one App Clip Code that encodes the experience’s registered invocation URL.

- Create multiple App Clip Codes for the experience where each encodes a different invocation URL.

The second option is especially useful if you only register one advanced App Clip experience and take advantage of URL prefix matching, and you use URL parameters to update the interface of your App Clip upon launch.

If you want to create a single App Clip Code or you selected several App Clip experiences, click Next. Otherwise, to create multiple App Clip Codes for the selected experience, click Yes for that option. On your Mac, choose the URLs you want App Store Connect to use, and store them in a file that uses the comma-separated values (CSV) file format. Each of the file’s rows represents one generated App Clip Code, and each value in a row represents one URL. Upload the CSV file to App Store Connect by clicking Upload URLs and choosing the file on your Mac.

The following code snippet shows the example content of a CSV file. [App Store Connect](https://appstoreconnect.apple.com/) creates one App Clip Code for each row in the file.

https://appclip.example.com/about
https://appclip.example.com/buy
https://appclip.example.com/buy?id=123
https://appclip.example.com/buy?id=456
https://appclip.example.com/buy?id=789

Note that each URL in the CSV file must match the selected App Clip experience.

### [Configure your App Clip Code appearance](https://developer.apple.com/documentation/appclip/creating-app-clip-codes-with-app-store-connect\#Configure-your-App-Clip-Code-appearance)

On the next screen, choose a default color pattern or experiment with custom colors and instantly preview and verify them. App Clip Codes use three different colors: a foreground color and a background color you choose, and a third color that [App Store Connect](https://appstoreconnect.apple.com/) generates for you based on the other two colors.

To ensure users can reliably scan an App Clip Code, the color combination must offer enough contrast. Apple offers default color pairs, but you can experiment and choose a custom pair. If your color selection doesn’t offer enough contrast, App Store Connect suggests different foreground colors based on your custom background color.

Next, select whether you want to create an NFC-integrated or scan-only App Clip Code. Then, choose the App Clip badge design with the App Clip logo or, if space is at a premium, use the design without the App Clip logo. Click Next and follow the workflow to finish creating your App Clip Code.

## [See Also](https://developer.apple.com/documentation/appclip/creating-app-clip-codes-with-app-store-connect\#see-also)

### [App Clip Code creation](https://developer.apple.com/documentation/appclip/creating-app-clip-codes-with-app-store-connect\#App-Clip-Code-creation)

[Creating App Clip Codes with the App Clip Code Generator](https://developer.apple.com/documentation/appclip/creating-app-clip-codes-with-the-app-clip-code-generator)

Use the App Clip Code Generator command-line tool to verify your code’s colors, get color suggestions, and create App Clip Codes.

---

# https://developer.apple.com/documentation/appclip/creating-app-clip-codes-with-the-app-clip-code-generator

- [App Clips](https://developer.apple.com/documentation/appclip)
- [Creating App Clip Codes](https://developer.apple.com/documentation/appclip/creating-app-clip-codes)
- Creating App Clip Codes with the App Clip Code Generator

Article

# Creating App Clip Codes with the App Clip Code Generator

Use the App Clip Code Generator command-line tool to verify your code’s colors, get color suggestions, and create App Clip Codes.

## [Overview](https://developer.apple.com/documentation/appclip/creating-app-clip-codes-with-the-app-clip-code-generator\#overview)

By placing an App Clip Code at a physical location or using it in printed or digital marketing materials, you make your App Clip more discoverable. An App Clip Code always uses a design Apple provides, and users instantly recognize and scan it to launch your App Clip. Use the App Clip Code generator command-line tool to create App Clip Codes during development of your App Clip or to automate the creation of App Clip Codes.

With the App Clip Code Generator command-line tool, you can:

- Get color suggestions for your App Clip Code.

- Experiment with custom colors.

- Verify a custom color pair.

- Save your generated App Clip Codes as Scalable Vector Graphics (SVG) files.

If you already created an advanced App Clip experience in [App Store Connect](https://appstoreconnect.apple.com/) or prefer a tool with a more visual interface, you can use App Store Connect to create the App Clip Code. For more information, see [Creating App Clip Codes with App Store Connect](https://developer.apple.com/documentation/appclip/creating-app-clip-codes-with-app-store-connect).

### [Install the App Clip Code Generator](https://developer.apple.com/documentation/appclip/creating-app-clip-codes-with-the-app-clip-code-generator\#Install-the-App-Clip-Code-Generator)

To download and install the App Clip Code Generator, visit [App Clips Resources](https://developer.apple.com/app-clips/resources/) and log into your Apple Developer account. After you download the App Clip Code Generator, open the downloaded disk image and run the package installer. You can find the installed tool at `/Library/Developer/AppClipCodeGenerator`.

### [Choose a default color pair](https://developer.apple.com/documentation/appclip/creating-app-clip-codes-with-the-app-clip-code-generator\#Choose-a-default-color-pair)

App Clip Codes use three different colors: a foreground color and a background color you choose, and a third color that the command-line tool generates for you based on the other two colors. To ensure that users can reliably scan the App Clip Code, the color combination must offer enough contrast. Apple offers default color templates to help you choose a color pair.

To see the list of default color pairs, open the Terminal app and run the `templates` command:

% AppClipCodeGenerator templates

This command prints an index and a hexadecimal representation of the foreground and background colors for each default color pair.

Index: 0 Foreground: FFFFFF Background: 000000
Index: 1 Foreground: 000000 Background: FFFFFF
Index: 2 Foreground: FFFFFF Background: 777777
Index: 3 Foreground: 777777 Background: FFFFFF
Index: 4 Foreground: FFFFFF Background: FF3B30
Index: 5 Foreground: FF3B30 Background: FFFFFF
Index: 6 Foreground: FFFFFF Background: EE7733
Index: 7 Foreground: EE7733 Background: FFFFFF
Index: 8 Foreground: FFFFFF Background: 33AA22
Index: 9 Foreground: 33AA22 Background: FFFFFF
Index: 10 Foreground: FFFFFF Background: 00A6A1
Index: 11 Foreground: 00A6A1 Background: FFFFFF
Index: 12 Foreground: FFFFFF Background: 007AFF
Index: 13 Foreground: 007AFF Background: FFFFFF
Index: 14 Foreground: FFFFFF Background: 5856D6
Index: 15 Foreground: 5856D6 Background: FFFFFF
Index: 16 Foreground: FFFFFF Background: CC73E1
Index: 17 Foreground: CC73E1 Background: FFFFFF

To see a preview of App Clip Codes for each default color pair as a PNG file, use the Finder or Terminal app to navigate to `/Library/Developer/AppClipCodeGenerator/SampleTemplates`.

### [Experiment with custom colors](https://developer.apple.com/documentation/appclip/creating-app-clip-codes-with-the-app-clip-code-generator\#Experiment-with-custom-colors)

In addition to choosing a default color pair, you can choose custom foreground and background colors. To help you choose a color pair that offers high contrast, the App Clip Code Generator tool includes functionality to verify your custom color pair. It also suggests alternative colors in case the ones you initially choose don’t offer enough contrast.

To verify your custom color pair, run the `suggest` command in Terminal:

% AppClipCodeGenerator suggest --foreground $foregroundColor --background $backgroundColor

Replace the values for the `--foreground` and `--background` arguments with your RGB color’s hexadecimal representation; for example:

% AppClipCodeGenerator suggest --foreground 65D212 --background 5B1637

Doing so prints the color combination you entered as `Foreground: 65D212 Background: 5B1637` to confirm that the chosen color pair offers enough contrast to allow for reliable scanning of the App Clip Code.

If you provide a color pair that doesn’t offer enough contrast (for example, if you run `AppClipCodeGenerator suggest --foreground 123456 --background 345678`), the tool prints a list of suggested color pairs.

Foreground: FFFFFF Background: 345678
Foreground: 44DDDD Background: 345678
Foreground: 55DDFF Background: 345678
Foreground: AABBCC Background: 345678
Foreground: BBCCBB Background: 345678
Foreground: FFBBEE Background: 345678
Foreground: 33DDFF Background: 345678
Foreground: CCBB33 Background: 345678

Note how the tool suggests foreground colors based on the chosen background color.

### [Generate your App Clip Code](https://developer.apple.com/documentation/appclip/creating-app-clip-codes-with-the-app-clip-code-generator\#Generate-your-App-Clip-Code)

When you’ve decided on the invocation URL and the color pair, use the App Clip Code Generator tool to create an App Clip Code and save it as an SVG vector graphic file. Open the Terminal app, then create an App Clip Code with the tool’s `generate` command, using one of the following options:

- To generate a scan-only App Clip Code that uses the badge design and a default color pair, use the `--index` option with the index of the default color pair as its value; for example:

% AppClipCodeGenerator generate --url https://appclip.example.com --index 9 --output ~/path/to/filename.svg

- To generate an App Clip Code without the App Clip logo, use the `--logo` option and pass `none` to it; for example:

% AppClipCodeGenerator generate --url https://appclip.example.com --index 9 --logo none --output ~/path/to/filename.svg

- To generate an SVG file for an NFC-integrated App Clip Code, set the `--type` option to `nfc`; for example:

% AppClipCodeGenerator generate --url https://appclip.example.com --index 9 --output ~/path/to/filename.svg --type nfc

- To generate an App Clip Code with a custom color pair, set both the `--foreground` and `--background` options to use your custom colors; for example:

% AppClipCodeGenerator generate --url https://appclip.example.com --foreground 123456 --background FFFFFF --output ~/path/to/filename.svg

To see all available commands and options, run `AppClipCodeGenerator --help`.

App Clip Codes can only encode a limited amount of information. The App Clip Code Generator displays an error message if you choose an invocation URL that exceeds the amount of encodable information or if it contains invalid characters. For more information, see [Encoding a URL in an App Clip Code](https://developer.apple.com/documentation/appclip/encoding-a-url-in-an-app-clip-code). For general information about choosing the invocation URL for your App Clip, see [Configuring App Clip experiences](https://developer.apple.com/documentation/appclip/configuring-the-launch-experience-of-your-app-clip).

### [Automate the creation of App Clip Codes](https://developer.apple.com/documentation/appclip/creating-app-clip-codes-with-the-app-clip-code-generator\#Automate-the-creation-of-App-Clip-Codes)

If you need to create many different App Clip Codes, consider automating their creation. The App Clip Code Generator comes with a Python script and a comma-separated values (CSV) file to use with it. The CSV file contains sample data to use to create App Clip Codes. You can find the script and the CSV file at `/Library/Developer/AppClipCodeGenerator/Scripts`.

The following code shows a CSV file that contains the information for four App Clip Codes:

SVG File Name,URL,Background Color,Foreground Color,Type,Logo
camera_standalone.svg,https://appclip.example.com,FFFFFF,000000,cam,none
nfc_standalone.svg,https://appclip.example.com,FFFFFF,000000,nfc,none
camera_badge.svg,https://appclip.example.com,FFFFFF,000000,cam,badge
nfc_badge.svg,https://appclip.example.com,FFFFFF,000000,nfc,badge

To create a batch of App Clip Codes:

1. Navigate to `/Library/Developer/AppClipCodeGenerator/Scripts` in the Finder or Terminal app, and copy its contents to a location of your choice; for example, a directory named `AppClipCodes` in your app’s Git repository.

2. Navigate to the directory that contains the copied files and review its contents. Then, create a new directory where you want to save the App Clip Codes you’ll create in the next step. For example, you might create a directory named `GeneratedCodes`.

3. In the Terminal app, navigate to the directory that contains the copied files.

4. From within the directory, run the Python script:

% python batch_generator.py $filename.csv $directory

Replace the placeholders with the actual file and directory names. If you used the file and directory names mentioned in the previous steps, run the following command:

% python batch_generator.py sample_list.csv GeneratedCodes

Doing so generates four App Clip Codes using the data in the CSV file and saves them in the `GeneratedCodes` directory. 5. Review the generated App Clip Codes, then modify the `sample_list.csv` file as necessary to generate your App Clip Codes. Note that for the script to work, you can’t change the names of the CSV file’s fields.

## [See Also](https://developer.apple.com/documentation/appclip/creating-app-clip-codes-with-the-app-clip-code-generator\#see-also)

### [App Clip Code creation](https://developer.apple.com/documentation/appclip/creating-app-clip-codes-with-the-app-clip-code-generator\#App-Clip-Code-creation)

[Creating App Clip Codes with App Store Connect](https://developer.apple.com/documentation/appclip/creating-app-clip-codes-with-app-store-connect)

Select one or more advanced App Clip experiences in App Store Connect and create App Clip Codes for users to scan to launch your App Clip.

---

# https://developer.apple.com/documentation/appclip/apactivationpayload/url

- [App Clips](https://developer.apple.com/documentation/appclip)
- [APActivationPayload](https://developer.apple.com/documentation/appclip/apactivationpayload)
- url

Instance Property

# url

The URL of the link that launched the App Clip.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+

var url: URL? { get }

## [Discussion](https://developer.apple.com/documentation/appclip/apactivationpayload/url\#Discussion)

Use `url` to retrieve data that’s passed to an App Clip on launch, and use the data to update the user interface of the App Clip.

The value of `url` is the same as the [`NSUserActivity`](https://developer.apple.com/documentation/Foundation/NSUserActivity) [`webpageURL`](https://developer.apple.com/documentation/Foundation/NSUserActivity/webpageURL) property. If you don’t need to verify the user’s location when they launch your App Clip, use `webpageURL` instead.

For more information, see [Responding to invocations](https://developer.apple.com/documentation/appclip/responding-to-invocations).

---

# https://developer.apple.com/documentation/appclip/apactivationpayloaderror

- [App Clips](https://developer.apple.com/documentation/appclip)
- APActivationPayloadError

Structure

# APActivationPayloadError

An error that an App Clip activation payload returns.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+

struct APActivationPayloadError

## [Topics](https://developer.apple.com/documentation/appclip/apactivationpayloaderror\#topics)

### [Getting information about the error](https://developer.apple.com/documentation/appclip/apactivationpayloaderror\#Getting-information-about-the-error)

[`static var errorDomain: String`](https://developer.apple.com/documentation/appclip/apactivationpayloaderror/errordomain)

### [Interpreting errors](https://developer.apple.com/documentation/appclip/apactivationpayloaderror\#Interpreting-errors)

[`static var doesNotMatch: APActivationPayloadError.Code`](https://developer.apple.com/documentation/appclip/apactivationpayloaderror/doesnotmatch)

The provided URL doesn’t match the invocation URL you registered for the App Clip.

[`static var disallowed: APActivationPayloadError.Code`](https://developer.apple.com/documentation/appclip/apactivationpayloaderror/disallowed)

The user denied location access, or the source of the App Clip invocation wasn’t an NFC tag or visual code.

[`enum Code`](https://developer.apple.com/documentation/appclip/apactivationpayloaderror/code)

Error codes that an App Clip activation payload returns.

## [Relationships](https://developer.apple.com/documentation/appclip/apactivationpayloaderror\#relationships)

### [Conforms To](https://developer.apple.com/documentation/appclip/apactivationpayloaderror\#conforms-to)

- [`CustomNSError`](https://developer.apple.com/documentation/Foundation/CustomNSError)
- [`Equatable`](https://developer.apple.com/documentation/Swift/Equatable)
- [`Error`](https://developer.apple.com/documentation/Swift/Error)
- [`Hashable`](https://developer.apple.com/documentation/Swift/Hashable)
- [`Sendable`](https://developer.apple.com/documentation/Swift/Sendable)
- [`SendableMetatype`](https://developer.apple.com/documentation/Swift/SendableMetatype)

## [See Also](https://developer.apple.com/documentation/appclip/apactivationpayloaderror\#see-also)

### [Understanding errors](https://developer.apple.com/documentation/appclip/apactivationpayloaderror\#Understanding-errors)

[`let APActivationPayloadErrorDomain: String`](https://developer.apple.com/documentation/appclip/apactivationpayloaderrordomain)

A string that identifies the activation payload’s error domain.

---

# https://developer.apple.com/documentation/appclip/apactivationpayloaderrordomain

- [App Clips](https://developer.apple.com/documentation/appclip)
- APActivationPayloadErrorDomain

Global Variable

# APActivationPayloadErrorDomain

A string that identifies the activation payload’s error domain.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+

let APActivationPayloadErrorDomain: String

## [See Also](https://developer.apple.com/documentation/appclip/apactivationpayloaderrordomain\#see-also)

### [Understanding errors](https://developer.apple.com/documentation/appclip/apactivationpayloaderrordomain\#Understanding-errors)

[`struct APActivationPayloadError`](https://developer.apple.com/documentation/appclip/apactivationpayloaderror)

An error that an App Clip activation payload returns.

[`enum Code`](https://developer.apple.com/documentation/appclip/apactivationpayloaderror/code)

Error codes that an App Clip activation payload returns.

---

# https://developer.apple.com/documentation/appclip/apactivationpayloaderror/code

- [App Clips](https://developer.apple.com/documentation/appclip)
- [APActivationPayloadError](https://developer.apple.com/documentation/appclip/apactivationpayloaderror)
- APActivationPayloadError.Code

Enumeration

# APActivationPayloadError.Code

Error codes that an App Clip activation payload returns.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+

enum Code

## [Topics](https://developer.apple.com/documentation/appclip/apactivationpayloaderror/code\#topics)

### [Error types](https://developer.apple.com/documentation/appclip/apactivationpayloaderror/code\#Error-types)

[`case doesNotMatch`](https://developer.apple.com/documentation/appclip/apactivationpayloaderror/code/doesnotmatch)

The provided URL doesn’t match the registered App Clip URL.

[`case disallowed`](https://developer.apple.com/documentation/appclip/apactivationpayloaderror/code/disallowed)

The user denied location access, or the source of the App Clip invocation wasn’t from an NFC tag or visual code.

### [Initializers](https://developer.apple.com/documentation/appclip/apactivationpayloaderror/code\#Initializers)

[`init?(rawValue: Int)`](https://developer.apple.com/documentation/appclip/apactivationpayloaderror/code/init(rawvalue:))

## [Relationships](https://developer.apple.com/documentation/appclip/apactivationpayloaderror/code\#relationships)

### [Conforms To](https://developer.apple.com/documentation/appclip/apactivationpayloaderror/code\#conforms-to)

- [`BitwiseCopyable`](https://developer.apple.com/documentation/Swift/BitwiseCopyable)
- [`Equatable`](https://developer.apple.com/documentation/Swift/Equatable)
- [`Hashable`](https://developer.apple.com/documentation/Swift/Hashable)
- [`RawRepresentable`](https://developer.apple.com/documentation/Swift/RawRepresentable)
- [`Sendable`](https://developer.apple.com/documentation/Swift/Sendable)
- [`SendableMetatype`](https://developer.apple.com/documentation/Swift/SendableMetatype)

## [See Also](https://developer.apple.com/documentation/appclip/apactivationpayloaderror/code\#see-also)

### [Understanding errors](https://developer.apple.com/documentation/appclip/apactivationpayloaderror/code\#Understanding-errors)

[`let APActivationPayloadErrorDomain: String`](https://developer.apple.com/documentation/appclip/apactivationpayloaderrordomain)

A string that identifies the activation payload’s error domain.

[`struct APActivationPayloadError`](https://developer.apple.com/documentation/appclip/apactivationpayloaderror)

An error that an App Clip activation payload returns.

---

# https://developer.apple.com/documentation/appclip/apactivationpayload/confirmacquired(in:completionhandler:)

#app-main)

- [App Clips](https://developer.apple.com/documentation/appclip)
- [APActivationPayload](https://developer.apple.com/documentation/appclip/apactivationpayload)
- confirmAcquired(in:completionHandler:)

Instance Method

# confirmAcquired(in:completionHandler:)

Checks whether an App Clip invocation happened at an expected physical location.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+

func confirmAcquired(
in region: CLRegion,

)

## [Parameters](https://developer.apple.com/documentation/appclip/apactivationpayload/confirmacquired(in:completionhandler:)\#parameters)

`region`

The expected physical location at the time of the App Clip invocation.

`completionHandler`

A closure called when the platform confirms the expected physical location at the time of the App Clip invocation.

The closure takes the following parameters:

inRegion

A Boolean value that indicates whether the App Clip invocation happened at the expected physical location.

error

The error object that describes why the platform couldn’t confirm the user’s physical location.

This parameter is `nil` if the platform was able to determine the user’s physical location at the time of the App Clip invocation.

## [Mentioned in](https://developer.apple.com/documentation/appclip/apactivationpayload/confirmacquired(in:completionhandler:)\#mentions)

[Confirming a person’s physical location](https://developer.apple.com/documentation/appclip/confirming-a-person-s-physical-location)

## [Discussion](https://developer.apple.com/documentation/appclip/apactivationpayload/confirmacquired(in:completionhandler:)\#Discussion)

Confirm the user’s location at the time of the App Clip invocation if the App Clip is associated with a physical location. The request to confirm the location fails with [`disallowed`](https://developer.apple.com/documentation/appclip/apactivationpayloaderror/disallowed) if the source of the invocation isn’t an NFC tag or visual code.

For the platform to accept the request to confirm the user’s location, you need to make modifications to the `Info.plist` file of the App Clip. For more information, see [Enabling notifications in App Clips](https://developer.apple.com/documentation/appclip/enabling-notifications-in-app-clips).

---

# https://developer.apple.com/documentation/appclip/apactivationpayloaderror/errordomain

- [App Clips](https://developer.apple.com/documentation/appclip)
- [APActivationPayloadError](https://developer.apple.com/documentation/appclip/apactivationpayloaderror)
- errorDomain

Type Property

# errorDomain

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+

static var errorDomain: String { get }

---

# https://developer.apple.com/documentation/appclip/apactivationpayloaderror/code/doesnotmatch

- [App Clips](https://developer.apple.com/documentation/appclip)
- [APActivationPayloadError](https://developer.apple.com/documentation/appclip/apactivationpayloaderror)
- [APActivationPayloadError.Code](https://developer.apple.com/documentation/appclip/apactivationpayloaderror/code)
- APActivationPayloadError.Code.doesNotMatch

Case

# APActivationPayloadError.Code.doesNotMatch

The provided URL doesn’t match the registered App Clip URL.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+

case doesNotMatch

## [See Also](https://developer.apple.com/documentation/appclip/apactivationpayloaderror/code/doesnotmatch\#see-also)

### [Error types](https://developer.apple.com/documentation/appclip/apactivationpayloaderror/code/doesnotmatch\#Error-types)

[`case disallowed`](https://developer.apple.com/documentation/appclip/apactivationpayloaderror/code/disallowed)

The user denied location access, or the source of the App Clip invocation wasn’t from an NFC tag or visual code.

---

# https://developer.apple.com/documentation/appclip/apactivationpayloaderror/disallowed

- [App Clips](https://developer.apple.com/documentation/appclip)
- [APActivationPayloadError](https://developer.apple.com/documentation/appclip/apactivationpayloaderror)
- disallowed

Type Property

# disallowed

The user denied location access, or the source of the App Clip invocation wasn’t an NFC tag or visual code.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+

static var disallowed: APActivationPayloadError.Code { get }

## [See Also](https://developer.apple.com/documentation/appclip/apactivationpayloaderror/disallowed\#see-also)

### [Interpreting errors](https://developer.apple.com/documentation/appclip/apactivationpayloaderror/disallowed\#Interpreting-errors)

[`static var doesNotMatch: APActivationPayloadError.Code`](https://developer.apple.com/documentation/appclip/apactivationpayloaderror/doesnotmatch)

The provided URL doesn’t match the invocation URL you registered for the App Clip.

[`enum Code`](https://developer.apple.com/documentation/appclip/apactivationpayloaderror/code)

Error codes that an App Clip activation payload returns.

---

# https://developer.apple.com/documentation/appclip/apactivationpayloaderror/code/disallowed

- [App Clips](https://developer.apple.com/documentation/appclip)
- [APActivationPayloadError](https://developer.apple.com/documentation/appclip/apactivationpayloaderror)
- [APActivationPayloadError.Code](https://developer.apple.com/documentation/appclip/apactivationpayloaderror/code)
- APActivationPayloadError.Code.disallowed

Case

# APActivationPayloadError.Code.disallowed

The user denied location access, or the source of the App Clip invocation wasn’t from an NFC tag or visual code.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+

case disallowed

## [See Also](https://developer.apple.com/documentation/appclip/apactivationpayloaderror/code/disallowed\#see-also)

### [Error types](https://developer.apple.com/documentation/appclip/apactivationpayloaderror/code/disallowed\#Error-types)

[`case doesNotMatch`](https://developer.apple.com/documentation/appclip/apactivationpayloaderror/code/doesnotmatch)

The provided URL doesn’t match the registered App Clip URL.

---

# https://developer.apple.com/documentation/appclip/apactivationpayloaderror/doesnotmatch

- [App Clips](https://developer.apple.com/documentation/appclip)
- [APActivationPayloadError](https://developer.apple.com/documentation/appclip/apactivationpayloaderror)
- doesNotMatch

Type Property

# doesNotMatch

The provided URL doesn’t match the invocation URL you registered for the App Clip.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+

static var doesNotMatch: APActivationPayloadError.Code { get }

## [See Also](https://developer.apple.com/documentation/appclip/apactivationpayloaderror/doesnotmatch\#see-also)

### [Interpreting errors](https://developer.apple.com/documentation/appclip/apactivationpayloaderror/doesnotmatch\#Interpreting-errors)

[`static var disallowed: APActivationPayloadError.Code`](https://developer.apple.com/documentation/appclip/apactivationpayloaderror/disallowed)

The user denied location access, or the source of the App Clip invocation wasn’t an NFC tag or visual code.

[`enum Code`](https://developer.apple.com/documentation/appclip/apactivationpayloaderror/code)

Error codes that an App Clip activation payload returns.

---

# https://developer.apple.com/documentation/appclip/apactivationpayloaderror/code/init(rawvalue:)

#app-main)

- [App Clips](https://developer.apple.com/documentation/appclip)
- [APActivationPayloadError](https://developer.apple.com/documentation/appclip/apactivationpayloaderror)
- [APActivationPayloadError.Code](https://developer.apple.com/documentation/appclip/apactivationpayloaderror/code)
- init(rawValue:)

Initializer

# init(rawValue:)

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+

init?(rawValue: Int)

---

