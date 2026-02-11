#  Fantastic (SwiftUI) Frustrations and Where to Find Them

@Metadata {
    @TitleHeading("Talk")
}

Danijela Vrzan

## Abstract

SwiftUI has redefined the way we build user interfaces across Apple platforms. While its declarative syntax is powerful, it's not without challenges. In this talk, we will dive into the common frustrations developers face when using SwiftUI, such as unexpected behavior and the constraints of state management. Using real-world examples, we'll highlight these challenges and offer practical strategies to overcome them, emphasizing the importance of breaking down views into smaller components.

You'll leave equipped to navigate SwiftUI more effectively, leveraging its strengths and transforming frustrations into opportunities for better app design and a smoother user experience.

## Key Takeaways

#### Some key tips:

- Keyboard toolbar

- Sheet always dismisses when presented for the first time.
Fix by attaching to the upper-most view.

- Be careful when you add searchable. It can't be attached to the upper-most view.

- `Compiler is unable to render in time` → most of the time the problem is you.

- Apple docs say you need to access `isSearching` from inside the searched view, rather than its parent.

#### Flash updated regions

Xcode → Debug → View Debugging → Rendering → Flash Updated Regions

Only works on a real device.

Demonstration: multiple pickers in a single view → all pickers are updated when scrolling and updating the state.

A state change _can_ cause SwiftUI to re-evaluate the entire view.
It's really important to split SwiftUI views into separate scopes: extract into new reusable view.

### The Illusion of Interaction

Modifiers change behaviour- not just the appearance.
You should design for the behaviour and then modify it.

#### Example 1

Content shape - rectangle.

#### Example 2

Hold-down button works, even though it is disabled..
On-tap gesture modifier intercepts the button action: use button action.

### Sometimes... the problem really is SwiftUI...

SwiftUI feels magical, but its magic lives in rules we can't see.

How do we minimise frustrations?

- Read the documentation

