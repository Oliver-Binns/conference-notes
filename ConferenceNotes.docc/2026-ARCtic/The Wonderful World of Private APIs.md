#  The Wonderful World of Private APIs

Quentin Fasquel

## Abstract

Ever wondered what Apple keeps behind the velvet rope? Let's sneak a peek at private APIs, see how we can reach them from Swift and Objective-C, and uncover some of the magic that powers iOS behind the scenes.

## Key Takeaways

### Trying to recreate the camera app in SwiftUI

Internal SFSymbols are present in the simulator private frameworks
`SFSCoreGlyphsBundle`
`camera.nightmode`

#### How to use a private Objective-C API?

Declare the header-file of the private APIs and it should compile:
`#import "_UIAssetManager.h"`

explicitly:
```objc
_UIAssetManager * assetManager = [_UIAssetManager]
```

or a runtime look-up:
```objc
Class bundleClass = NSClassFromString(@"SFSCoreGlyphsBundle");
```

#### How to *find* a private Objective-C API?

`YourObject.h`
`YourObject+Private.h`
`YourObject.m`

Compile: we only get the public headers file.
Can't find it in the shipped binary.
Could find it in DYLD_SHARED_CACHE


Or.. we can disassemble the simulator framework?
`class-dump`: recover Objective-C headers from a compiled binary? Broken in iOS 15

`ipsw` iOS / macOS research swiss Army knife


Or even easier at runtime:

```
objc_copyClassList()
objc_
```

CAPackage - Core Animation

CABackdropLayer: applies a filter to what's behind it.
Filters: `CIFilter` is not supported on iOS.
`CAFilter` similar to `CoreImage.CIFilter`
`setValue(value: Any?)`

Not type-safe, but available as a package from Quentin.
`CAFilterBuiltins`


`CAMeshTransform`
`CAMutableMeshTransform`

### What about Swift?
Swift doesn't have header files? So how do we find private Swift APIs?

`swiftmodule`:
 contains a file for each architecture (swiftinterface)
`@_spi` private swift interface

Some APIs that are not public and not documented do end up in the swift interface:

TBD file (Text-Base stub)

`swiftdemangle`?

