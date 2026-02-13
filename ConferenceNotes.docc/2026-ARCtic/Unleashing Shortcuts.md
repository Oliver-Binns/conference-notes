# Unleashing Shortcuts: Intent on improving your workflow

@Metadata {
    @TitleHeading("Workshop")
}

Benno Kress

## Abstract

Shortcuts have been part of Apple's ecosystem since 2017, yet many developers barely scratch the surface of what's possible. In this hands-on workshop, you'll discover how to automate your daily workflows – from simple one-tap actions like opening the Updates Section inside the App Store to complex multi-app orchestrations powered by custom App Intents written in Swift. Whether you're new to Shortcuts or ready to level up shortcuts you already created, you'll leave with practical automations tailored to your needs. No prior Shortcuts experience required, just bring your iPhone, your MacBook, and curiosity!

## Key Takeaways

The workshop focused on the user side of the Shortcuts app. The developer side (implementing App Intents to surface actions in Shortcuts) was only touched on in a "Where to go from here" section at the end.

### History

- 2014 → The app Workflow started as a Hackathon project at the University of Michigan
- 2017 → Apple acquired the app after giving it a Design Award in 2015
- 2018 → Workflow was rebranded as Shortcuts and presented at WWDC, released alongside iOS 12

The core concept never changed, but originally Workflow relied solely on URL Schemes. Nowadays app developers typically donate their actions to Shortcuts (and other system functionality) using App Intents, though URL Schemes can still be used if you know them.

### Basics

- All Shortcuts consist of one or more Actions
- Actions can have Input and Output (e.g. Artist Name → [Search iTunes] → Result)
- Actions can be interactive (Ask for Input, …)
- Actions can have an effect (Play Music, …)

### Level 1: Starting Easy

Simple shortcuts triggered from a convenient place in the system. Available trigger points:

- Spotlight
- Action Button
- Control Centre Widgets
- The Shortcuts Widget
- Lock Screen Widgets
- The Share Sheet
- Siri
- Less common: Home Screen Icon or the Shortcuts URL Scheme

### Level 2: Getting Lazy

Rather than triggering shortcuts manually, the Automation tab provides triggers that can be roughly categorised as:

- Timed Events
- Location
- Connectivity Events
- System Events
- Focus Modes

> Note: Multiple Date & Time Automations for the same action
>
> There is no "every x minutes" trigger available, so replicating cron-like behaviour requires creating many separate automations – cumbersome and hard to maintain.

> Tip: Combining Triggers
>
> The Shortcuts app doesn't provide combined triggers like "at a location on weekdays between 6am and 6pm". The workaround is to use one trigger and check the second condition inside the shortcut itself – e.g. use the location trigger and exit early if the date & time condition fails.

### Exercise: Automated Notification

We built a shortcut called "ARCtic Reminder" that fires a notification when a workshop session ends. It used a _Text_ action for the attendee's name and a _Show Notification_ action to display e.g. "{Name}, the brainstorming session ended".

This was then wired up to a _Time of Day_ automation set to run immediately – a good first demonstration of combining a reusable shortcut with automations.

### Brainstorming

> Important: Goal of the Brainstorming
>
> The brainstorming sessions were about finding personal use cases. Shortcuts should support how each person uses their phone day to day, and that will be different for everyone.

### Utility Apps

Utility apps exist solely to provide the Shortcuts app with convenient functionality – things that would require combining multiple standard actions or would be impossible otherwise. Some have standalone features of their own but become much more useful when integrated into shortcuts.

### Level 3: Adding Complexity

From this level on, shortcuts grow into multi-app connections, conditional paths, and more advanced concepts like API calls. They often evolve from smaller shortcuts or from tedious manual procedures.

Refactoring tips (same principles as in code):

- Extract reusable parts into separate shortcuts, callable via _Run Shortcut_ (which supports input and output)
- Use the _Comment_ action to document expected input structure, output, and complex logic
- Rename the smart variables produced by each action's output – tap the variable at any call site and fill in a recognisable name
- Debug with _Stop and Output_ or a combination of _Quick Look_ and _Show Alert_

#### Useful concepts at this level

- Focus Modes → can be automated, can be an automation trigger and can be used as conditions in shortcuts
- REST Calls → can be done using the _Get Contents of URL_ action

### Exercise: Making the Notification More Flexible

We refactored the earlier shortcut to accept a structured dictionary input containing the session name (previously hardcoded). Key steps:

- Added _Get Dictionary from Input_ at the top, sourcing from Shortcut Input
- Used _Get Value for Key_ with the key "Session Name"
- Added an _If_ action to provide a fallback value ("session") when no input is given
- Updated the notification text to use the dynamic session name

For the automation side, the trick was to select "Create New Shortcut" in the automation's Do block and use a _Dictionary_ action to pass structured input into _Run Shortcut_. These inline automation shortcuts stay tied to the automation and don't clutter the Library – convenient but less maintainable, so best reserved for defining input to existing shortcuts.

### Level 4: Being Nerdy

An outlook on going deeper. Benno showed his fully automated Focus Modes and an Action Button shortcut with context-dependent menus. Some examples:

- Home Wi-Fi → adds Smart Home Scenes (further filtered by Smart Home state)
- Work Focus + Office Location → adds canteen menu
- Sleep Focus → option to set an alarm based on morning calendar events
- Phone in Landscape Orientation → skips the menu entirely and opens a [specialist camera app](https://apps.apple.com/app/65-24-mk0/id6447838860)

### Level 5: Boss Level

When shortcuts become too complex to maintain, it may be easier to build a personal Utility app that replaces frequently used functionality with a dedicated action. Good candidates are helper shortcuts extracted at Level 3 and REST calls where the response is nicer to parse as a custom type. The [shared starter project Työkalu](https://github.com/bennokress/Tyokalu) provides a starting point.

## Links

- [Työkalu - App Intents Starter Project](https://github.com/bennokress/Tyokalu)
- [Workshop Material](https://github.com/bennokress/Tyokalu/blob/main/Workshop%20Material/README.md)
