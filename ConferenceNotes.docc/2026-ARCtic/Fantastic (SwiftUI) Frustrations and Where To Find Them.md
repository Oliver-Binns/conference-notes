#  Fantastic (SwiftUI) Frustrations and Where to Find Them

Danijela Vrzan

SwiftUI _looks_ easy.

### Some key tips:

- Keyboard toolbar 

- Sheet always dismisses when presented for the first time.
Fix by attaching to the upper-most view.

- Be careful when you add searchable. It can’t be attached to the upper-most view.

- `Compiler is unable to render in time` -> most of the time the problem is you.

- Apple docs say you need to access `isSearching` from inside the searched view, rather than its parent.

## []

### Flash updated regions

Xcode -> Debug -> View Debugging -> Rendering -> Flash Updated Regions

Only works on a real device.

Demonstration: multiple pickers in a single view -> all pickers are updated when scrolling and updating the state.

A state change _can_ cause SwiftUI to re-evaluate the entire view.
It’s really important to split SwiftUI views into separate scopes: extract into new reusable view.

## The Illusion of Interaction

Modifiers change behaviour- not just the appearance.
You should design for the behaviour and then modify it.

### Example 1

Content shape - rectangle.

### Example 2

Hold-down button works, even though it is disabled..
On-tap gesture modifier intercepts the button action: use button action.

## Sometimes... the problem really is SwiftUI...

SwiftUI feels magical, but its magic lives in rules we can’t see.

How do we minimise frustrations?

- Read the documentation

