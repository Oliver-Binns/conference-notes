# Swift Beyond Apple - Building Android Apps & Backends in Swift

@Metadata {
    @TitleHeading("Talk")
}

Joannis Orlandos

## Abstract

Swift is no longer an Apple-only language. It's used by both Apple and others for a variety of purposed, including Linux, Cloud, Embedded Systems and Android.

In this talk we'll look at the status of Swift on non-Apple platforms. We'll demonstrate what tools are available, what works great today and what you can expect to improve.

By the end of this talk, you'll be equipped to start your full-stack adventures in Swift.

## Key Takeaways

Started out as an Android developer.

Two apps, one codebase: why write the same app twice?

You could migrate to a single codebase, but we really just want to share business logic.
One core, two UIs: existing solutions aren't interoperable.
Kotlin Native bridges through Objective-C: you lose value semantics - which is what Swift is all about.

### Swift supports a variety of platforms:

- FreeBSD
- OpenBSD
- Linux-
- Windows
- Embedded
- WASM
- Android

Swift is safe, fast and easy.

Swift is interoperable with C, C++ and Objective-C.

### Android

Write business logic once: state machine, network requests.
Compiles to native code: not a different compilation mode.
All the power of Swift, on Android.

~80% of Linux package support Android.
~30% of all Swift Packages support Android.

#### Tooling

Swift SDK for Android: direct cross-compilation
Swift-Java
Skip: bring SwiftUI views to Android

### Embedded Swift

Doesn't support Foundation, typed throws or 

Supports Microcontrollers: including Apple's Secure Enclave, already in production
WebAssembly

### WebAssembly

Run Swift in web browsers: ElementaryUI
Cloud-Hosted Plugins
Microcontrollers
