---
layout: default
title: "For-in"
description: A Swift 5.1 for-in loop reference guide for, with a simple example and an example with an index.
redirect_from:
  - /for/
---
{::options parse_block_html="true" /}

The common for loop `for (i = a; i < b; i++)` does not exist in Swift. Instead, the **for-in** can be modified to have an index using tuples and _[enumerated](https://developer.apple.com/documentation/swift/array/1687832-enumerated)_:

{% include opencol.html size=6 newrow=true %}

### Simple for-in

```swift
let birds = ["Owl", "Crane"]
for bird in birds {
  print(bird)
}
// Output: 
// Owl
// Crane
```

{% include closecol.html %}{% include opencol.html size=6 %}

### For-in with index

```swift
let birds = ["Owl", "Crane"]
for (i, bird) in birds.enumerated() {
  print("[\(i)]: \(bird)")
}
// Output: 
// [0]: Owl
// [1]: Crane
```

{% include closecol.html closerow=true %}

### For-in-where

```swift
struct Player {
  let name: String
  let level: Int
}

let players = [
  Player(name: "Rashida", level: 1),
  Player(name: "Tomoko", level: 1),
  Player(name: "Isabella", level: 20)
]

for player in players where player.level == 1 {
  print("\(player.name) is a beginner.")
}

// Output:
// Rashida is a novice.
// Tomoko is a novice.
```

### See also

* [forEach](/foreach)