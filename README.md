# VLCKitSPM

Swift Package Manager wrapper for VLCKit 4.0.0a21.

> ## This package is winding down - VLCKit is getting official SPM support
>
> This wrapper exists for one reason: VideoLAN publishes VLCKit for CocoaPods, but not as a
> unified `XCFramework` you can consume with Swift Package Manager. So we built one and hosted
> it here.
>
> **That reason is gone**, in two merge requests on 2026-07-20:
>
> - [!394 "Packaging: add Swift Package Manager support"](https://code.videolan.org/videolan/VLCKit/-/merge_requests/394)
>   added a `Package.swift` to VLCKit itself, pointing at a VideoLAN-hosted binary target, plus the
>   tooling to build, checksum and publish it. It takes the same approach this package does: one
>   monolithic universal `VLCKit.xcframework` covering every Apple platform.
> - [!395 "Distribute 4.0.0a22 via cocoapods and SPM"](https://code.videolan.org/videolan/VLCKit/-/merge_requests/395)
>   replaced that manifest's placeholder `url` and `checksum` with real values and cut the release.
>   This is the one that made it usable.
>
> **It is available now.** VideoLAN tagged `4.0.0-a22` carrying that fully populated manifest, with
> the same platform coverage this package ships.
>
> **Use it instead of this package:**
>
> ```swift
> dependencies: [
>     .package(url: "https://code.videolan.org/videolan/VLCKit.git", exact: "4.0.0-a22")
> ]
> ```
>
> **Three things to know when you migrate:**
>
> 1. **The tag naming changed.** It is `4.0.0-a22`, **with a hyphen** - unlike `4.0.0a21` and
>    `4.0.0a20`. `4.0.0a22` does not exist and returns a 404. Extrapolating the old pattern fetches
>    nothing.
> 2. **The product is named `VLCKit`, not `VLCKitSPM`**, so your `import` and your target dependency
>    both change.
> 3. **Minimum deployment targets are lower** upstream: iOS 12, macOS 10.13, tvOS 12, watchOS 7.4,
>    visionOS 1.
>
> **`4.0.0-alpha.21` is the last release published here.** It and the earlier tags stay available and
> existing `.package(url:)` references keep resolving, so nothing breaks if you are not ready to move.
> But new work should go to VideoLAN's package: it is upstream-maintained, canonical, and released in
> lockstep with VLCKit rather than whenever we get around to a rebuild. We would rather point you at
> the real thing than keep a parallel copy alive.

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

That gap is now closed upstream (see the notice at the top). `4.0.0-alpha.21` is the last release
published here - use VideoLAN's own Swift Package at tag `4.0.0-a22` or later.

## License

VLCKit is licensed under LGPLv2.1. See [COPYING.txt](https://code.videolan.org/videolan/VLCKit/-/blob/master/COPYING) for details.

## Credits

- [VideoLAN](https://www.videolan.org/) - VLCKit developers
- [VirtualOx B.V.](https://virtualox.io) - SPM wrapper maintainer
