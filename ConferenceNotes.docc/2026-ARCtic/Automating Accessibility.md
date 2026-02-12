# Automating Accessibility

@Metadata {
    @TitleHeading("Talk")
}

Soroush Khanlou

## Abstract

Making your app accessible is crucial to ensuring that a wide array of users can use your app to its fullest potential. However, for sighted users, accessibility is often a hidden layer. Because sighted users don't interact with this representation of their app, its polish can sometimes fall out of sync with the rest of the app.

Validating that your accessible experiences are working the way you expect can often be an arduous process, sometimes even involving running your app on physical devices. Ensuring that those experiences don't regress is even more of a challenge.

In this talk, Soroush will discuss tools for rapidly iterating on accessibility code, easily spotting bugs, and ensuring that accessible interactions stay working the way you expect, so that all your users can get the most out of your app.

## Key Takeaways

Permanent, temporary and situational disability.

Accessibility is different things to different people.

**Vision:**
- Glasses to accommodate vision
- Uncorrectable vision issues so she uses really large text on a larger phone.
- Turns on bold text and Show Borders because he likes how they look.

Two ends of a spectrum:
Some people prefer dark mode: light sensitivity.
Some people prefer light mode: astigmatism.

**Motion**
Some people use assistive touch.
Some people need keyboard shortcuts.

> Accessibility is a broad umbrella.

Making your app accessible is making it usable.
Give your users the tools to decide for themselves.

We need to provide features we do not use ourselves.

### Where does that leave our work?

The software always changes, and accessibility needs to change with it:

Example 1: Date reads as "8/2" rather than "February 8th."
Example 2: Changing image from flag to checkmark introduces the "selected" trait.
Example 3: Missing values from accessibility rotors.

Accessibility snapshot library shows labels in the preview with `.accessibilityPreview(size:)`.
Can be used in diffs to quickly check accessibility changes in code review.

## Links

- [Accessibility Snapshot](https://github.com/cashapp/AccessibilitySnapshot)
