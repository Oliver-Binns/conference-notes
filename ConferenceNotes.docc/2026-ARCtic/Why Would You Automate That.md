# Why the F#@ Would You Automate That? A Love Letter to Over-Engineering from a nerd

@Metadata {
    @TitleHeading("Talk")
}

Noam Efergan

## Abstract

Ever spent 4 hours automating a 5-minute task? Congratulations, you're a developer! As developers, we're told to "move fast and ship," but what if I told you that spending time on automation could actually save your sanity AND your app store ratings?

Join me for a humorous journey through the wonderful world of iOS automation - from simple git hooks that prevent you from committing broken code at 2 AM, to full CI/CD pipelines that deploy to TestFlight while you sleep. We'll explore when automation makes sense (hint: more often than you think), when it doesn't (yes, that's a thing), and how to convince yourself that yes, you DO deserve nice things, even as a solo developer.

Through real-world examples, war stories, and the occasional existential crisis about whether robots will replace us (spoiler: they already have, and we built them), you'll learn practical automation strategies that work for teams of one to one hundred. Because life's too short to manually increment build numbers, and your users deserve better than "oops, I forgot to run the tests."

## Key Takeaways

- Time
- Consistency
- Security
- It’s Cool

### Common Automations

- Unit Tests on PRs
- Build on merge to main
- Auto TestFlight releases

### Choosing a Provider

#### Xcode Cloud

Apple owned.

*The Bad*:

- Limited customisation
- Painfully Slow
- 25 free hours

#### Fastlane & Friends

- Docs everywhere
- Portable
- Test locally
- Nice UIs (Bitrise, CodeMagic)

*The bad*:

- Required Ruby knowledge
- Maintenance overhead
- Debugging is difficult
- Each CI has their own configuration (usually yaml based)

### AI to the rescue?

AI can generate Fastfile ations, CI/CD YAML and even entire automation scripts.

### Mix & match

Use each tool for what it does best:
- Fill gaps, Fastlane can overcome Xcode's
- Maximise usage of multiple free tiers

### Don't overdo it

Diminishing returns:
Automating a task that takes 5 minutes once a month might cost more than it saves.

### Identify prime candidates for automation:

Things you don't want to do: uninteresting or frustrating tasks
Things you don't care about: necessary tasks that don't contribute to your product
Things you forget: incrementing build number

**Example- setting up App Store listing:**

UI test target: create new UI tests
Fastlane snapshot: run `fastlane init`
Deliver initialisation: 
Local validation: 
On-demand trigger: enable it to be run on the CI

Run everything locally until it's boring (no issues occur)

Other examples:
- App Store review task management and draft responses
- Automated localisations
- Dead code detection
- Code signing using Fastlane matc
- Effortless release notes

## Links

- [Blog](https://nowham.dev/)
