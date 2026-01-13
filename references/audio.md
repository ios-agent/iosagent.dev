# CarPlay Audio Apps

Audio apps provide music, podcasts, audiobooks, and other audio content for playback in CarPlay. They use `CPNowPlayingTemplate` and integrate with `MPNowPlayingInfoCenter`.

## Requirements

- Entitlement: `com.apple.developer.carplay-audio`
- iOS 14.0+
- Background audio capability

## Project Setup

### Info.plist Configuration

```xml
<key>UIBackgroundModes</key>
<array>
    <string>audio</string>
</array>
```

## Basic Audio App Structure

```swift
import CarPlay
import MediaPlayer
import AVFoundation

class CarPlaySceneDelegate: UIResponder, CPTemplateApplicationSceneDelegate {
    var interfaceController: CPInterfaceController?
    var audioPlayer: AVAudioPlayer?

    func templateApplicationScene(
        _ templateApplicationScene: CPTemplateApplicationScene,
        didConnect interfaceController: CPInterfaceController
    ) {
        self.interfaceController = interfaceController

        // Set up audio session
        setupAudioSession()

        // Create content browser
        let rootTemplate = createBrowseTemplate()
        interfaceController.setRootTemplate(rootTemplate, animated: true)
    }

    private func setupAudioSession() {
        do {
            try AVAudioSession.sharedInstance().setCategory(
                .playback,
                mode: .default,
                options: []
            )
            try AVAudioSession.sharedInstance().setActive(true)
        } catch {
            print("Failed to set up audio session: \(error)")
        }
    }
}
```

## Browse Template

### Creating Content Browser

```swift
func createBrowseTemplate() -> CPTabBarTemplate {
    // Library tab
    let libraryTemplate = createLibraryTemplate()
    libraryTemplate.tabTitle = "Library"
    libraryTemplate.tabImage = UIImage(systemName: "music.note.house")

    // Browse tab
    let browseTemplate = createDiscoverTemplate()
    browseTemplate.tabTitle = "Browse"
    browseTemplate.tabImage = UIImage(systemName: "square.grid.2x2")

    // Search tab
    let searchTemplate = createSearchTemplate()
    searchTemplate.tabTitle = "Search"
    searchTemplate.tabImage = UIImage(systemName: "magnifyingglass")

    let tabBar = CPTabBarTemplate(templates: [libraryTemplate, browseTemplate, searchTemplate])
    return tabBar
}

func createLibraryTemplate() -> CPListTemplate {
    let items = [
        createListItem(title: "Playlists", icon: "music.note.list", action: showPlaylists),
        createListItem(title: "Artists", icon: "music.mic", action: showArtists),
        createListItem(title: "Albums", icon: "square.stack", action: showAlbums),
        createListItem(title: "Songs", icon: "music.note", action: showSongs),
        createListItem(title: "Recently Played", icon: "clock", action: showRecent)
    ]

    let section = CPListSection(items: items)
    return CPListTemplate(title: "Library", sections: [section])
}

func createListItem(
    title: String,
    icon: String,
    action: @escaping () -> Void
) -> CPListItem {
    let item = CPListItem(
        text: title,
        detailText: nil,
        image: UIImage(systemName: icon)
    )
    item.accessoryType = .disclosureIndicator
    item.handler = { _, completion in
        action()
        completion()
    }
    return item
}
```

### Album Art Row Items

```swift
func createRecentlyPlayedSection() -> CPListSection {
    // Load album art images
    let albumImages = recentAlbums.compactMap { $0.artwork }

    let imageRowItem = CPListImageRowItem(
        text: "Recently Played",
        images: albumImages
    )
    imageRowItem.listImageRowHandler = { item, index, completion in
        self.playAlbum(at: index)
        completion()
    }

    return CPListSection(items: [imageRowItem])
}
```

## Now Playing Template

### Setting Up Now Playing

```swift
func showNowPlaying() {
    let nowPlayingTemplate = CPNowPlayingTemplate.shared

    // Configure buttons
    nowPlayingTemplate.updateNowPlayingButtons([
        CPNowPlayingShuffleButton { button in
            self.toggleShuffle()
        },
        CPNowPlayingRepeatButton { button in
            self.toggleRepeat()
        },
        CPNowPlayingPlaybackRateButton { button in
            self.cyclePlaybackRate()
        }
    ])

    // Enable additional features
    nowPlayingTemplate.isUpNextButtonEnabled = true
    nowPlayingTemplate.upNextButtonTitle = "Up Next"

    nowPlayingTemplate.isAlbumArtistButtonEnabled = true

    // Push template
    interfaceController?.pushTemplate(nowPlayingTemplate, animated: true)
}
```

### Now Playing Observers

```swift
func setupNowPlayingObservers() {
    let nowPlaying = CPNowPlayingTemplate.shared

    // Up Next button tapped
    nowPlaying.add(self)
}

extension CarPlaySceneDelegate: CPNowPlayingTemplateObserver {
    func nowPlayingTemplateUpNextButtonTapped(_ nowPlayingTemplate: CPNowPlayingTemplate) {
        showUpNextList()
    }

    func nowPlayingTemplateAlbumArtistButtonTapped(_ nowPlayingTemplate: CPNowPlayingTemplate) {
        showArtistPage()
    }
}
```

## MPNowPlayingInfoCenter Integration

### Updating Now Playing Info

```swift
func updateNowPlayingInfo(for track: Track) {
    var nowPlayingInfo = [String: Any]()

    nowPlayingInfo[MPMediaItemPropertyTitle] = track.title
    nowPlayingInfo[MPMediaItemPropertyArtist] = track.artist
    nowPlayingInfo[MPMediaItemPropertyAlbumTitle] = track.album
    nowPlayingInfo[MPMediaItemPropertyPlaybackDuration] = track.duration
    nowPlayingInfo[MPNowPlayingInfoPropertyElapsedPlaybackTime] = currentPlaybackTime
    nowPlayingInfo[MPNowPlayingInfoPropertyPlaybackRate] = isPlaying ? 1.0 : 0.0

    // Album artwork
    if let artworkImage = track.artwork {
        let artwork = MPMediaItemArtwork(boundsSize: artworkImage.size) { _ in
            return artworkImage
        }
        nowPlayingInfo[MPMediaItemPropertyArtwork] = artwork
    }

    MPNowPlayingInfoCenter.default().nowPlayingInfo = nowPlayingInfo
}
```

### Remote Command Center

```swift
func setupRemoteCommandCenter() {
    let commandCenter = MPRemoteCommandCenter.shared()

    // Play/Pause
    commandCenter.playCommand.addTarget { event in
        self.play()
        return .success
    }

    commandCenter.pauseCommand.addTarget { event in
        self.pause()
        return .success
    }

    // Previous/Next
    commandCenter.previousTrackCommand.addTarget { event in
        self.previousTrack()
        return .success
    }

    commandCenter.nextTrackCommand.addTarget { event in
        self.nextTrack()
        return .success
    }

    // Seeking
    commandCenter.changePlaybackPositionCommand.addTarget { event in
        guard let positionEvent = event as? MPChangePlaybackPositionCommandEvent else {
            return .commandFailed
        }
        self.seek(to: positionEvent.positionTime)
        return .success
    }

    // Shuffle/Repeat
    commandCenter.changeShuffleModeCommand.addTarget { event in
        guard let shuffleEvent = event as? MPChangeShuffleModeCommandEvent else {
            return .commandFailed
        }
        self.setShuffleMode(shuffleEvent.shuffleType)
        return .success
    }

    commandCenter.changeRepeatModeCommand.addTarget { event in
        guard let repeatEvent = event as? MPChangeRepeatModeCommandEvent else {
            return .commandFailed
        }
        self.setRepeatMode(repeatEvent.repeatType)
        return .success
    }
}
```

## Queue Management

### Up Next List

```swift
func showUpNextList() {
    let items = upNextTracks.enumerated().map { index, track in
        let item = CPListItem(
            text: track.title,
            detailText: track.artist,
            image: track.artwork
        )
        item.handler = { _, completion in
            self.playTrack(at: index)
            completion()
        }
        return item
    }

    let section = CPListSection(items: items, header: "Up Next")
    let template = CPListTemplate(title: "Up Next", sections: [section])

    interfaceController?.pushTemplate(template, animated: true)
}
```

## Search

### Content Search

```swift
func createSearchTemplate() -> CPListTemplate {
    let template = CPListTemplate(title: "Search", sections: [])
    template.emptyViewTitleVariants = ["Search for music"]
    return template
}

func performSearch(query: String) {
    // Search implementation
    let results = searchMusic(query: query)

    let items = results.map { result in
        let item = CPListItem(
            text: result.title,
            detailText: result.subtitle,
            image: result.image
        )
        item.handler = { _, completion in
            self.handleSearchResult(result)
            completion()
        }
        return item
    }

    let section = CPListSection(items: items, header: "Results")
    searchTemplate?.updateSections([section])
}
```

## Playback Controls

### Basic Playback

```swift
func play() {
    audioPlayer?.play()
    updateNowPlayingPlaybackState(playing: true)
}

func pause() {
    audioPlayer?.pause()
    updateNowPlayingPlaybackState(playing: false)
}

func nextTrack() {
    currentIndex = (currentIndex + 1) % playlist.count
    loadAndPlay(track: playlist[currentIndex])
}

func previousTrack() {
    if currentPlaybackTime < 3 {
        currentIndex = (currentIndex - 1 + playlist.count) % playlist.count
    }
    loadAndPlay(track: playlist[currentIndex])
}

func seek(to time: TimeInterval) {
    audioPlayer?.currentTime = time
    updateNowPlayingInfo(for: currentTrack)
}
```

## Best Practices

1. **Update Now Playing info frequently** - Keep time and state accurate
2. **Handle interruptions** - Respond to phone calls, Siri, etc.
3. **Support background playback** - Continue playing when app is backgrounded
4. **Use appropriate artwork sizes** - 600x600 pixels recommended
5. **Implement all remote commands** - Support full playback control
6. **Handle CarPlay disconnection** - Continue playback on iPhone
7. **Optimize loading** - Pre-fetch album art and metadata
