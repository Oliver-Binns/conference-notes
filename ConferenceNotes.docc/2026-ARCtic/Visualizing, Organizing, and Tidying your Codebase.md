# Visualizing, Organizing, and Tidying your Codebase

@Metadata {
    @TitleHeading("Talk")
}

Dan Wood

## Abstract

Maintaining a clean, well-organised codebase becomes increasingly challenging as projects grow and as more people try vibe coding. This talk explores how to leverage static analysis tools like Periphery to not only identify unused code, but to actively guide better code organisation and encapsulation practices. We'll start with an introduction to Periphery and its benefits, then demonstrate how extending it with custom analysis and visualization can help developers identify naming inconsistencies, understand hierarchical relationships between SwiftUI views, and make informed decisions about file organisation. With author's new PeripheryTree, we'll see how visualizing code relationships can reveal opportunities for better encapsulation, suggest file reorganisation based on view hierarchies, and ultimately help maintain a cleaner, more maintainable codebase.

## Key Takeaways

### Make sure that code is not too long

Senior level skills.
Good rules for LLMs.
SwiftLint.

### Remove code that's not used

Swift Compiler does some things here.

Periphery is better: https://github.com/peripheryapp/periphery

It can report:
- unused functions
- unused function parameters
- redundant protocols
- assign-only properties
- redundant public accessors

Cleaning up codebase, including junk left behind from vibe-coding.
Reduces technical debt.

TreeSwift is built on top of this to provide a UI: https://github.com/danwood/Treeswift
TreeSwift can autofix (Periphery can't) and can ignore warnings.

#### Strategies to use:

1. Start with top-level / unused
2. Ignore when there's code you want to keep.
3. Remove individual code fragments 
4. Rebuild your code in Xcode, work a bit at a time
5. Then enable more warnings.

15% of code removed from a vibe-coded project.

### Encapsulation

Keep access levels as private as possible. AI is really bad at this!

Periphery includes functionality to suggest encapsulation improvements ([PR](https://github.com/peripheryapp/periphery/pull/1042)):

- Identify internal declarations that should be more private
- Identify fileprivate declarations that should be private

and more.

### Organise into subfolders

TreeSwift can detect that code is "folder private" and recommend changes.
This helps to reduce coupling without needing to split things into modules.

### Structure of your code

Categories of code: 
- Tree
- Extensions
- Shared Utilities
- Unused

#### Tree: 

Visualise code structures and folders.

#### Extensions:

Extensions are not really anchored to anything.

## Links

- [TreeSwift](https://github.com/danwood/Treeswift)
- [Periphery](https://github.com/peripheryapp/periphery)
