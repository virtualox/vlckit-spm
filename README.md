# VLCKitSPM

Swift Package Manager wrapper for VLCKit 4.0.0a18.

## Features

- VLCKit 4.0.0a18 (December 2025)
- Picture-in-Picture support on iOS and macOS
- Unified framework for all Apple platforms
- Supports iOS, tvOS, macOS, watchOS, and visionOS

## Installation

Add to your `Package.swift`:

```swift
dependencies: [
    .package(url: "https://github.com/virtualox/vlckit-spm", from: "4.0.0-alpha.18")
]
```

Or in Xcode: File → Add Package Dependencies → Enter URL.

## Usage

```swift
import VLCKitSPM

let player = VLCMediaPlayer()
let media = VLCMedia(url: URL(string: "https://example.com/stream.m3u8")!)
player.media = media
player.play()
```

## Platform Support

| Platform | Minimum Version |
|----------|-----------------|
| iOS | 13.0 |
| tvOS | 13.0 |
| macOS | 10.15 |
| watchOS | 6.0 |
| visionOS | 1.0 |

## What's New in 4.0

- Added support for Picture-in-Picture playback on iOS and macOS
- Unified VLCKit for all Apple platforms
- Added support for visionOS and watchOS
- Dual subtitle track support
- Complete rewrite of event management
- Full C API exposure

## License

VLCKit is licensed under LGPLv2.1. See [COPYING.txt](https://code.videolan.org/videolan/VLCKit/-/blob/master/COPYING) for details.

## Credits

- [VideoLAN](https://www.videolan.org/) - VLCKit developers
- [VirtualOx B.V.](https://virtualox.io) - SPM wrapper maintainer
