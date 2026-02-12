# Create a custom control with SwiftUI

@Metadata {
    @TitleHeading("Talk")
}

Andrew Walker

## Abstract

This session explores the decision-making process behind building custom controls in SwiftUI. It starts by examining the benefits of using built-in components, and why they are often the right choice for familiarity, accessibility, and platform consistency.

For situations where a custom control meaningfully enhances the user experience, we'll use a case study of a custom radial filter menu. This example demonstrates how to design and implement a delightful custom control, covering advanced layout techniques, expressive animations, accessibility best practices, and modern design paradigms such as Liquid Glass.

## Key Takeaways

Choose between built-in and custom controls.

Create a custom control that is great for developer and users.

Consider users to ensure familiarity.

Looking at a filter button:
By default this pops up a menu.


Strongly consider built-in controls first provide familiarity to users and developers.
They provide accessibility, localisation, animations, adaptive styling and are supported across Apple's platform.

In this case we can:
- Show more content
- immediately reversible.
- whimsy

Demo lesser-used SwiftUI details

```swift
#Preview {
    RadialMenu(anchor: .bottomTrailing) {
        ForEach(sixBest.dropFirst()) {
            // add snippet here
        }
    }
}
```

### Layout the views

Layout calculation is done locally:
1. Container view proposes view size to its subviews.
2. Subview responds with its preferred size.
3. Layout is recursize

Different views behave differently:
Color: claims what's offered.
Image: claims actual size regardless of what is available
Text: Truncates if space is too small. If larger, only claims the space it needs.

You can create custom layouts using the `Layout` protocol.


### Add animations

Be careful- too much animation can be overwhelming.

Rope animation

add layout value:
```
extension LayoutSubview {
    var isExpanded: Bool {
        ...
    }
}
```

Custom containers..
Group: content

### Finish the control

Evaluate accessibility
- Reduce motion
- Prefers cross-fade

Adopt Liquid Glass
- GlassEffectContainer..


Style toggles:
- add `.radial` style to menu

## Links

- Building Custom controls WWDC19
- Demystify SwiftUI Containers 24
- Explore SwiftUI animation
- Animate with springs 23
- Build with new design 25
