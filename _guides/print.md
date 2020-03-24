---
layout: default
title: "Print"
description: A Swift 5.2 print method reference guide, covering usage and string interpolation.
redirect_from:
  - /write/
  - /writeln/
  - /println/
---

The `print` method is used to display a value on the console.

```swift
print("Hello world!")
// Prints "Hello world!"
```

### Printing variables

```swift
let mySentence = "I am from China."
print(mySentence)
// Prints "I am from China."

let life = 42
print(life)
// Prints "42"
```

### String interpolation

```swift
let country = "China"
print("I am from \(country).")
// Prints "I am from China."

let appleCount = 5
print("I have \(appleCount) apples.")
// Prints "I have 5 apples."
```