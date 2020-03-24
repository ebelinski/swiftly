---
layout: default
title: "Tuples"
description: A Swift 5.2 tuples reference guide, covering composition and decomposition.
redirect_from:
  - /tuple/
---
{::options parse_block_html="true" /}

**Tuples** are compound types made up of multiple values. They are used to group related bits of information, for simpler things that don't need [structs or classes](/structs-and-classes) The values in a tuple don't have to be of the same type.

### Composing a tuple

```swift
let player = (name: "Maya", level: 5, score: 150)

print(player) // (name: "Maya", level: 5, score: 150)
print("\(player.name): level \(player.level), \(player.score) pts") // Maya: level 5, 150 pts
```

The labels are optional:

```swift
let player = ("Maya", 5, 150)

print(player) // ("Maya", 5, 150)
print("\(player.0): level \(player.1), \(player.2) pts") // Maya: level 5, 150 pts
```

### Decomposing a tuple

A tuple can be decomposed into separate variables with any name:

```swift
let player = (name: "Maya", level: 5, score: 150)

let (currentName, currentLevel, currentScore) = player
print("\(currentName): level \(currentLevel), \(currentScore) pts") // Maya: level 5, 150 pts
```

If only some values are needed, `_` may be used to avoid creating a variable for unused values:

```swift
let player = (name: "Maya", level: 5, score: 150)

let (currentName, _, _) = player
print("The current player is \(currentName).") // The current player is Maya.
```

