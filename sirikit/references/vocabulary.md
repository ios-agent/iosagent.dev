# Custom Vocabulary Reference

## Table of Contents
1. [Overview](#overview)
2. [Global Vocabulary](#global-vocabulary)
3. [User-Specific Vocabulary](#user-specific-vocabulary)
4. [Intent Phrases](#intent-phrases)
5. [App Name Synonyms](#app-name-synonyms)
6. [Localization](#localization)

---

## Overview

Custom vocabulary improves Siri's speech recognition for app-specific terms.

| Type | Defined In | Scope |
|------|-----------|-------|
| Global Vocabulary | `AppIntentVocabulary.plist` | All users |
| User-Specific | Runtime via `INVocabulary` | Individual user |
| Intent Phrases | `AppIntentVocabulary.plist` | Example phrases |

---

## Global Vocabulary

### Create Vocabulary File
1. File → New → Property List
2. Name: `AppIntentVocabulary.plist`
3. Add to iOS app target (not extension)
4. Place in language `.lproj` folder

### File Structure

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "...">
<plist version="1.0">
<dict>
    <key>ParameterVocabularies</key>
    <array>
        <!-- Custom terms for parameters -->
    </array>
    <key>IntentPhrases</key>
    <array>
        <!-- Example phrases -->
    </array>
</dict>
</plist>
```

### Parameter Vocabularies

Define custom terms for intent parameters:

```xml
<key>ParameterVocabularies</key>
<array>
    <dict>
        <key>ParameterNames</key>
        <array>
            <string>INRequestRideIntent.rideOptionName</string>
        </array>
        <key>ParameterVocabulary</key>
        <array>
            <dict>
                <key>VocabularyItemIdentifier</key>
                <string>premium</string>
                <key>VocabularyItemSynonyms</key>
                <array>
                    <dict>
                        <key>VocabularyItemPhrase</key>
                        <string>Premium Ride</string>
                    </dict>
                    <dict>
                        <key>VocabularyItemPhrase</key>
                        <string>Luxury</string>
                    </dict>
                </array>
            </dict>
        </array>
    </dict>
</array>
```

### Vocabulary Item Keys

| Key | Description |
|-----|-------------|
| `VocabularyItemIdentifier` | Unique identifier returned to your code |
| `VocabularyItemSynonyms` | Array of phrases Siri recognizes |
| `VocabularyItemPhrase` | Spoken phrase |
| `VocabularyItemPronunciation` | IPA pronunciation hint |
| `VocabularyItemExamples` | Example usage contexts |

---

## User-Specific Vocabulary

Register at runtime for terms unique to each user.

### Supported Categories

```swift
enum INVocabularyStringType {
    case contactName              // App-specific contacts
    case contactGroupName         // Contact groups
    case photoTag                 // Photo tags
    case photoAlbumName           // Album names
    case workoutActivityName      // Custom workout names
    case carProfileName           // Vehicle profiles
    case carName                  // Car nicknames
    case paymentsOrganizationName // Payment recipients
    case paymentsAccountNickname  // Account nicknames
    case notebookItemTitle        // Note titles
    case notebookItemGroupName    // Notebook names
    case mediaPlaylistTitle       // Playlist names
    case mediaArtistName          // Artist names
    case mediaAlbumTitle          // Album titles
    case mediaShowTitle           // Show/podcast names
    case mediaMusicArtistName     // Music artists
    case mediaAudiobookTitle      // Audiobook titles
    case mediaAudiobookAuthorName // Audiobook authors
}
```

### Register Vocabulary

```swift
import Intents

func registerUserVocabulary() {
    let vocabulary = INVocabulary.shared()
    
    // Register playlist names
    let playlists: Set<String> = ["Morning Jams", "Workout Mix", "Chill Vibes"]
    vocabulary.setVocabularyStrings(playlists, of: .mediaPlaylistTitle)
    
    // Register contact groups
    let groups: Set<String> = ["Family", "Work Team", "Book Club"]
    vocabulary.setVocabularyStrings(groups, of: .contactGroupName)
}
```

### Order Matters

```swift
// Ordered set - first items have higher priority
let orderedPlaylists = NSOrderedSet(array: [
    "Favorites",      // Highest priority
    "Recently Played",
    "Workout Mix"     // Lowest priority
])
vocabulary.setVocabulary(orderedPlaylists, of: .mediaPlaylistTitle)
```

### Remove Vocabulary

```swift
// Remove all for a type
vocabulary.removeAllVocabularyStrings()

// The vocabulary is per-type, so set empty to clear specific type
vocabulary.setVocabularyStrings([], of: .mediaPlaylistTitle)
```

---

## Intent Phrases

Example phrases teach users how to invoke your app via Siri.

```xml
<key>IntentPhrases</key>
<array>
    <dict>
        <key>IntentName</key>
        <string>OrderSoupIntent</string>
        <key>IntentExamples</key>
        <array>
            <string>Order tomato soup from SoupChef</string>
            <string>Get me a large chowder</string>
            <string>I want soup from SoupChef</string>
        </array>
    </dict>
    <dict>
        <key>IntentName</key>
        <string>INStartWorkoutIntent</string>
        <key>IntentExamples</key>
        <array>
            <string>Start my morning run with FitApp</string>
            <string>Begin a 30 minute workout</string>
        </array>
    </dict>
</array>
```

### Phrase Guidelines
- Include your app name naturally
- Use realistic spoken language
- Include custom vocabulary terms
- Provide 3-5 examples per intent

---

## App Name Synonyms

Allow alternative names for your app.

### In Info.plist (App Target)

```xml
<key>INAlternativeAppNames</key>
<array>
    <dict>
        <key>INAlternativeAppName</key>
        <string>Soup Chef</string>
        <key>INAlternativeAppNamePronunciationHint</key>
        <string>soup shef</string>
    </dict>
    <dict>
        <key>INAlternativeAppName</key>
        <string>Soupy</string>
    </dict>
</array>
```

---

## Localization

### Localize Vocabulary File

```
en.lproj/
└── AppIntentVocabulary.plist

de.lproj/
└── AppIntentVocabulary.plist

ja.lproj/
└── AppIntentVocabulary.plist
```

### Pronunciation Hints

For languages with complex pronunciation:

```xml
<dict>
    <key>VocabularyItemPhrase</key>
    <string>抹茶</string>
    <key>VocabularyItemPronunciation</key>
    <string>ma3 cha2</string>
</dict>
```

### Chinese Dialect Rules

**Mandarin (zh_CN, zh_TW)**:
- Tones: 1, 2, 3, 4, 5 (neutral)
- Place after each character: `ping2 guo3`
- Replace ü with yu: `nyu` for `nü`

**Cantonese (zh_HK)**:
- Use Jyutping romanization
- Tones: 1-6
- Example: `dik1 si2` for 的士

---

## Best Practices

1. **Register early**: Call `setVocabularyStrings` at app launch
2. **Update when data changes**: Refresh when user adds/removes content
3. **Prioritize important terms**: Order matters in registered sets
4. **Don't over-register**: Only truly custom terms
5. **Test with Siri**: Verify recognition accuracy
6. **Localize completely**: Include all supported languages
