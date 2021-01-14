---
layout: default
title: "Identity operators (===, !==) "
description: A Swift 5.3 identity operators reference guide, with an example comparing two class instances.
redirect_from:
  - /identity-operator/
  - /identity-operators/
  - /===/
  - /!==/
---
{::options parse_block_html="true" /}

**Identity** operators return a [`Bool`](/bool) to indicate whether or not two variables are pointing to (referencing) the exact same class instance in memory. They are used heavily in [if](/if) statements.

They cannot be used on struct instances, because structs are value types, not reference types.

### Comparing two class instances

```swift
class Player {
  var name: String
  var score: Int

  init(name: String, score: Int) {
    self.name = name
    self.score = score
  }
}

let player1 = Player(name: "Tomoko", score: 100)
let player2 = Player(name: "Tomoko", score: 100)
let player3 = Player(name: "Isabella", score: 350)
let player4 = player1

print(player1 === player2) // false
print(player1 === player3) // false
print(player1 === player4) // true

print(player1 !== player2) // true
print(player1 !== player3) // true
print(player1 !== player4) // false
```

### Further reading

* [Structures and Classes § Identity Operators `📖 Official Swift Book`](https://docs.swift.org/swift-book/LanguageGuide/ClassesAndStructures.html#ID90)
