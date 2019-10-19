---
layout: default
title: "Identity operators (===, !==) "
description: 
redirect_from:
  - /identity-operator/
  - /identity-operators/
---
{::options parse_block_html="true" /}

**Identity** operators return a [`Bool`](/bool) to indicate whether or not two variables are pointing to (referencing) the exact same class instance in memory. They are used heavily in [if](/if) statements.

They cannot be used on struct instances, because structs are value types, not reference types.

### Comparing two class instances

Instances of classes that conform to [`Equatable`](https://developer.apple.com/documentation/swift/equatable) can be compared with `===` and `!===`:

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
