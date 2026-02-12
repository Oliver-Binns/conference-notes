# From Storytime to Scalability: Growing an iOS Team at Yoto

@Metadata {
    @TitleHeading("Talk")
}

Niamh Power

## Abstract

What happens when your user base doubles year after year, your company almost triples in size, and your iOS app has to keep up with it all? At Yoto, an audio platform for kids, we've been riding that wave, and it hasn't always been smooth sailing.

In this talk, I'll share the growing pains of scaling both an iOS app and the team behind it. From monolithic beginnings and "just ship it" hacks to modularisation, improved CI/CD, and building an iOS chapter, I'll cover the hard lessons we learned along the way. We'll also look at what we can expect in the future and how we're proactively preparing for it.

You'll hear about the technical challenges (offline downloads, CarPlay, in-app purchasing), the human challenges (avoiding silos, maintaining quality, empowering engineers), and how we adapt to massive seasonal traffic spikes around Black Friday and Christmas without burning out.

Whether you're an indie developer preparing for growth, or part of a larger team wondering how to keep moving fast without breaking everything, this talk will give you practical insights into scaling code, people, and processes... without losing your sanity.

## Key Takeaways

Growing the team through a sustained period of growth.

Launched as Kickstarter in 2019 with a launch in 2020.

Grown from 30k → 1.2 million monthly users.
Crash-free rate, and user ratings have stayed high during this period.

Market viability proven → freedom to think longer term: architecture, testing, shared standards and design system.

Started by optimising for speed, but not planning for an uncertain future.

Then team started to grow and explore new things:
- MVVM+C (View - ViewController - ViewModel - Service)
- Testing pyramid
- SwiftUI experiments

Initially in platform teams: iOS - Android - Backend.
New features were fairly waterfall, taking time to plan across teams.
Created shared components and design system to reduce duplicated UI and speed up iteration.

Logic was spread across the UI layer which made it harder to implement new features like CarPlay.
Refactored, redesigned and changed the architecture _with_ a business justification.

Lessons learnt:
- Jumped into feature flagging too early - this left unnecessary complexity to clean up later
- Underestimated scope
- Comms & planning: communication to the wider team business on progress

Userbase has almost doubled each Christmas: peak activation of 4-5 players every second.

Memory doesn't scale: documentation does.
Meeting notes by AI stored centrally.
Make space for tech debt, or tech debt will make space for itself.

Tooling:
- XcodeGen for project file pain (Tuist was too heavy, but might be more useful with modularisation)
- modularisation
- localisation

Slack → Zapier (adds device UUIDs to profiles) → fastlane.

Build the team you'll need next year.
Create a culture with learning time for junior developers.

Scaling carefully: shared ownership, shared engineering principles.
Make sure all teams get roughly the same workload.
Better cross-functional alignment.

## Links

- [Yoto](https://uk.yotoplay.com)
