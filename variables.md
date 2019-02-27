---
layout: default
title: "Variables"
description: 
redirect_from:
  - /var/
  - /variable/
  - /constant/
  - /constants/
  - /let/
  - /val/
---

**Variables and constants** are used to hold pieces of data. Variables can change over time (mutable), while constants must stay the same (immutable). Sometimes, the word "variables" is used to describe both variables and constants.

### Variables

Variables are declared with `var`:

```swift
var greeting "Hello"
var numberOfToys = 8
var isMorning = true
```

Variable declarations can include [type annotations](/type-annotations) for clarity:

```swift
var greeting: String "Hello"
var numberOfToys: Int = 8
var isMorning: Bool = true
```

Variables are mutable. Their values can change:

```swift
var numberOfToys: Int = 8
numberOfToys += 1
print(numberOfToys) // Prints "9"
```

### Constants

Constants are declared with `let`:

```swift
let greeting "Hello"
let numberOfToys = 8
let isMorning = true
```

Constant declarations can include [type annotations](/type-annotations) for clarity:

```swift
let greeting: String "Hello"
let numberOfToys: Int = 8
let isMorning: Bool = true
```

Constants are **not** mutable. Their values cannot change:

```swift
let numberOfToys: Int = 8
numberOfToys += 1 // ❌ Error: numberOfToys is not mutable
```
