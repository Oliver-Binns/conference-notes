#  SwiftUI + UIKit Interoperability - Beyond the Basics

@Metadata {
    @TitleHeading("Talk")
}

John Sundell

## Abstract

When adopting SwiftUI, it's very common to mix it with UIKit, either to be able to use existing UIKit components, to work around SwiftUI issues and missing features, or to handle tasks like navigation and coordination. In this talk, John will explore how we can make the most out of the SwiftUI + UIKit interoperability APIs, how to ensure that SwiftUI's layout system works well with tools like Auto Layout, how to pass configuration properties, events, and data between the two UI frameworks in a smooth way, and much more.

## Key Takeaways

### Somewhat mixed experience?

> Less about one being old and new: they are peers within the Apple technology stack.

```
---------------
| UIKit | SwiftUI |
---------------
| Core Animation  |
------------------
|      Metal      |
------------------
```

Using SwiftUI as a default, like UIKit is a default over CoreAnimation & Metal for most apps.
Using UIKit doesn't mean we're writing legacy code.

UIKit → UIViewRepresentable / UIViewControllerRepresentable → SwiftUI
SwiftUI → UIHostingController / UIHostingConfiguration → UIKit

### Connecting SwiftUI data to UIKit based controls

Be sure to only create the UIView in the makeUIView function, and only update the UIView in the updateUIView function

```swift
struct TextView: UIViewRepresentable {
    @Binding var text: String

    func makeUIView(context: Context) -> UITextView {
        UITextView()
    }

    func updateUIView(_ uiView: UITextView, context: Context) {
        uiView.text = text
        ...
        uiView.delegate = context.coordinator
    }

    ...
    func makeCoordinator() -> Coordinator {
        Coordinator()
    }
}
}
```

```
extension TextView {

}
```

### Connecting UIKit data model to SwiftUI views

Make our model class observable:
```swift
@Observable
final class User {
    let id: UUID
    var name: String
}
```

```swift
final class ProfileViewController: UIViewController {
    private var user: User

    viewWillLayoutSubviews() {
        // respond to model updates
        // called automatically because of the observation
    }


    private func showUserEditingSheet() {
        present(
            UIHostingController(rootView: UsernameEditingSheet(user: user)),
        )
    }
}
```

### Sharing stylings and configuration

This is not a SwiftUI convention, colour should use modifiers:

```
struct TextView: UIViewRepresentable {
    var foregroundColor: UIView

    // colour changes here, so they are updated if the underlying values change
    func updateUIView() {

    }
}
```

Constraints:
- Foreground style is not available to `UIViewRepresentable`.
- Background is a view, not just a colour.
- `Font.resolve(in:)` is iOS 26 only

#### We could implement a theme:

```swift
struct Theme {
    var foregroundColour = UIColor.label
    var backgroundColor = UIColor.systemBackground

}
```

For SwiftUI:
```swift
extension View {
    func themeForegroundColor()...
}
```

We can retrieve this from the environment in UIViewRepresentable:
```swift
struct TextView: UIViewRepresentable {
    @Environment var theme: Theme
}
```

### Connecting SwiftUI and UIKit layout systems:

In UIKit, using intrinsicContentSize
```swift
final class LogoView: UIView {
    override var intrinsicContentSize: CGSize {
        ...
    }
}
```

```swift
struct Logo: UIViewRepresentable {
    func makeUIView(context: Context) -> UIView {
        LogoView()
    }
}
```

By default, UIView is flexible in size.
Add the `fixedSize()` modifier?

Size that fits method in UIViewRepresentable:
```
func sizeThatFits() {
    let proposedSize = proposal.replayingUnspecifiedDimensions(...)
}
```

### Managing the safe area when mixing SwiftUI and UIKit

```
HomeViewController->

func showWelcomeSheet() {
    let sheet = UIHostingController(rootView: WelcomeView())


    NSLayoutConstraint.activate([
        sheet.view.leadingAnchor..
    ])
}
```

View is cut off at the bottom because `UIHostingController` always avoids safe-area by default:

```
sheet.safeAreaRegions.remove(.container)
```

Pass in the safe area insets to handle scroll view

## Links

- [Swift by Sundell](https://swiftbysundell.com)
