# Swift's Hidden Gems: Practical Techniques for Any Codebase

@Metadata {
    @TitleHeading("Talk")
}

Natalia Panferova

## Abstract

Swift evolves constantly, and while new big features like concurrency get most of the attention, the language also keeps refining in smaller, quieter ways. Some features often go unnoticed, yet they are the ones that can add clarity and a touch of delight to the everyday Swift code we write. In this talk, we'll explore some of these hidden gems, and look into small improvements that can be integrated into any project on any platform. I'll share a collection of my favourite Swift techniques and language details that make code cleaner, or even faster, and easier to reason about.

## Key Takeaways

Swift milestones:

- Swift Package Manager
- ABI and module stability
- Structured concurrency
- Swift Macros
- Embedded Swift

### Optionals:

Transform optional values:
```
let dailyWalkMinutesString = "30"
let dailyWalkMinutesInt: Int? = Int(dailyWalkMinutesString)

// verbose
let walkMinutesPerWeek: Int?
if let dailyWalkMinutesInt {
    walkMinutesPerWeek = dailyWalkMinutesInt * 7
} else {
    walkMinutesPerWeek = nil
}

// concise:
walkMinutesPerWeek = dailyWalkMinutesInt.map { $0 * 7 }
```

Take optional values:
```
let voucherCode: String? = "TDSAW-FAWER"
voucherCode..take()
```

Switch on multiple optionals simultaneously:

```swift
switch (puppyAgeInMonths, puppyWeightInKg) {
case let (age?, weight?):  // unwraps the optional!
    break
case let (nil, weight?):
    break
}
```

Execute loop options on non-nil elements
```
for case let? in puppyNames where name.hasPrefix("L") {
    ...
}
```

### Collections

Sort arrays using comparison operators as closures:

```swift
let registrationNumbersByIssueOrder = registrationNumbers
    .sorted(by: <)
```

Simplify array mapping:

```swift
let dogNames = dogs.map(\.name)
```

Accumulate collection elements:

```swift
let dogBreeds = ["Daschund"]

let frequency = dogBreeds.reduce(into: [:)) { counts, breed in
    counts[breed, default: 0] += 1
}
```

Count the elements that pass a test:

```swift
let temperatures = []
let numOfVeryColdDays = temperatures
    .count(where: { $0 < -20 })
```

### Strings

Bypass the need to escape special characters:
```
let jsonString = #"""
{"name": "Marley", "age": 5, "breed": "Flat-coated Retriever"}
"""#
```

Validate encoded input when creating a string:

Provide a default value in string interpolation:

```swift
let description = "The dog's age is \(age, default: "unknown")."
```

Define custom string interpolation

```swift
extension String.StringInterpolation {
    ...
}
```

Enhance your types with custom string representation

```swift
extension TrackerCoordinates: CustomStringConvertible {
    var description: String { ... }
}
```

Allow custom types to be initialised with literal values.

```swift
extension EnergyLevel: ExpressibleByIntegerLiteral {
    init(integerLiteral v: Int) { 
        ...
    }
}
```

Enable range creation for custom types:

```swift
extension TimeSlot: Comparable {
    ...
}
```

Transform your types into callable entities

```swift
struct TrainingDiet {
    let baseAmount: Double
 
    func adjustedAmount...

    func callAsFunction(activity: ActivityLevel) -> Double {
        ...
    }
}
```

## Links

- [Blog](http://nilcoalescing.com/blog/ARCtic2026)
