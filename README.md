# VLCKitSPM

Swift Package Manager wrapper for VLCKit 4.0.0a21.

> ## This package is winding down - VLCKit is getting official SPM support
>
> This wrapper exists for one reason: VideoLAN publishes VLCKit for CocoaPods, but not as a
> unified `XCFramework` you can consume with Swift Package Manager. So we built one and hosted
> it here.
>
> **That reason is going away.** VideoLAN merge request
> [!394 "Packaging: add Swift Package Manager support"](https://code.videolan.org/videolan/VLCKit/-/merge_requests/394)
> **was merged on 2026-07-20**. It adds a `Package.swift` to VLCKit itself, pointing at a
> VideoLAN-hosted binary target, plus the tooling to build, checksum and publish it. It takes the
> same approach this package does: one monolithic universal `VLCKit.xcframework` covering every
> Apple platform.
>
> **Where it stands right now (2026-07-20):**
>
> - The manifest is on VLCKit's `master`, but its `url` and `checksum` are still the
>   `REPLACEWITHVERSION` / `REPLACEWITHCHECKSUM` placeholders that VideoLAN's deploy tooling fills
>   in when a release is cut.
> - **No tagged VLCKit release carries it yet** - `4.0.0a21` does not, and `4.0.0a22` does not exist
>   at the time of writing. So the official package is not something you can depend on today.
> - Until it is, **`4.0.0-alpha.21` from this repository remains the working option**, and it is
>   expected to be the last release published here.
>
> **When the official package becomes available**, depend on VideoLAN's instead: upstream-maintained,
> canonical, and released in lockstep with VLCKit rather than whenever we get around to a rebuild.
> Note two differences when you migrate: the upstream product is named **`VLCKit`** rather than
> `VLCKitSPM`, so your `import` changes, and its minimum deployment targets are lower
> (iOS 12, macOS 10.13, tvOS 12, watchOS 7.4, visionOS 1).
>
> Nothing breaks today: `4.0.0-alpha.21` and the earlier tags stay available, and existing
> `.package(url:)` references keep resolving. We would rather point you at the real thing than keep
> a parallel copy alive.

## Features

- VLCKit 4.0.0a21 (July 2026)
- Picture-in-Picture support on iOS and macOS
- Unified framework for all Apple platforms
- Supports iOS, tvOS, macOS, watchOS, and visionOS

## Installation

Add to your `Package.swift`:

```swift
dependencies: [
    .package(url: "https://github.com/virtualox/vlckit-spm", from: "4.0.0-alpha.21")
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

## What's New in 4.0.0a21

- libVLC updated to `c9628afc`
- Radio service discovery: stations are now exposed as streams, and results are sorted by votes in descending order

## What's New in 4.0

- Added support for Picture-in-Picture playback on iOS and macOS
- Unified VLCKit for all Apple platforms
- Added support for visionOS and watchOS
- Dual subtitle track support
- Complete rewrite of event management
- Full C API exposure

## Versions

| Package version | VLCKit tag | Released |
|-----------------|------------|----------|
| 4.0.0-alpha.21 | `4.0.0a21` | July 2026 |
| 4.0.0-alpha.20 | `4.0.0a20` | July 2026 |
| 4.0.0-alpha.19 | `4.0.0a19` | April 2026 |
| 4.0.0-alpha.18 | `4.0.0a18` | December 2025 |

## About this package

This is a build of the official VideoLAN VLCKit sources at the tag above, packaged as a binary
Swift Package because VideoLAN has not published a unified `XCFramework` of its own. **No patches
are applied on top of upstream** - this is stock VLCKit, built and repackaged, nothing more.

That gap is being closed upstream (see the notice at the top), so this package is expected to stop
at `4.0.0-alpha.21`. Prefer VideoLAN's own Swift Package as soon as a tagged release carries it.

## License

VLCKit is licensed under LGPLv2.1. See [COPYING.txt](https://code.videolan.org/videolan/VLCKit/-/blob/master/COPYING) for details.

## Credits

- [VideoLAN](https://www.videolan.org/) - VLCKit developers
- [VirtualOx B.V.](https://virtualox.io) - SPM wrapper maintainer
