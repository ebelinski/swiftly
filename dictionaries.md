---
layout: default
title: "Dictionaries"
description: A Swift 5.1 reference sheet for dictionaries, covering declaration, mutability, type annotations, iteration, and counting elements.
redirect_from: 
  - /dictionary/
  - /dict/
  - /hashmap/
---
{::options parse_block_html="true" /}

**Dictionaries** store associations between keys of the same type and values of the same type in a collection with no defined ordering. Example:

```swift
let pointsPerPlayer = ["Rashida": 150, "Isabella": 275, "Tomoko": 115]
let nicknamePerPlayer = ["Rashida": "Ida", "Isabella": "Isa", "Tomoko": "Ko"]
```

* TOC
{:toc}

### Mutability

Dictionaries defined with **var** are mutable:

```swift
var pointsPerPlayer = ["Rashida": 150, "Isabella": 275, "Tomoko": 115]
pointsPerPlayer["Louis"] = 85
pointsPerPlayer["Rashida"] = nil
print(pointsPerPlayer) // ["Isabella": 275, "Louis": 85, "Tomoko": 115]
```

### Type

The type of a dictionary can be determined without type annotations:

```swift
let pointsPerPlayer = ["Rashida": 150, "Isabella": 275, "Tomoko": 115] // Inferred to be type [String: Int]
let nicknamePerPlayer = ["Rashida": "Ida", "Isabella": "Isa", "Tomoko": "Ko"] // Inferred to be [String : String]
```

But the type can also be explicitly declared:

```swift
let pointsPerPlayer: [String: Int] = ["Rashida": 150, "Isabella": 275, "Tomoko": 115]
let nicknamePerPlayer: [String: String] = ["Rashida": "Ida", "Isabella": "Isa", "Tomoko": "Ko"]
```

### Empty dictionaries

An empty dictionary must be defined with a type:

```swift
var pointsPerPlayer: [String: Int] = [:]
print(pointsPerPlayer) // [:]
```

Alternatively, initializer syntax may be used:

```swift
var pointsPerPlayer = [String: Int]()
print(pointsPerPlayer) // [:]
```

A dictionary can be emptied after creation:

```swift
var pointsPerPlayer = ["Rashida": 150, "Isabella": 275, "Tomoko": 115]
pointsPerPlayer = [:]
print(pointsPerPlayer) // [:]
```

### Iterating over dictionaries

A dictionary may be interated over using [for-in](/for-in).

```swift
var pointsPerPlayer = ["Rashida": 150, "Isabella": 275, "Tomoko": 115]
for (player, points) in pointsPerPlayer {
  print("\(player) has \(points) points.")
}
// Output:
// Tomoko has 115 points.
// Rashida has 150 points.
// Isabella has 275 points.
```

### `count` and `isEmpty`

`count` returns the number of elements in the dictionary. `isEmpty` can be used to determine if the dictionary has no elements.

```swift
var pointsPerPlayer = ["Rashida": 150, "Isabella": 275, "Tomoko": 115]
print(pointsPerPlayer.count) // 3
print(pointsPerPlayer.isEmpty) // false
pointsPerPlayer = [:]
print(pointsPerPlayer.count) // 0
print(pointsPerPlayer.isEmpty) // true
```
