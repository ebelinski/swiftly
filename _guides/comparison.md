---
layout: default
title: "Comparison operators (==, !=, >, <, >=, <=)"
description: A Swift 5.3 comparison operators reference guide, covering equal to ==, not equal to !=, greater than >, less than <, greater than or equal to >=, and less than or equal to <=.
redirect_from:
  - /more-than/
  - /less-than/
  - /more/
  - /less/
  - /equal-to/
  - /not-equal-to/
  - /more-than-or-equal-to/
  - /less-than-or-equal-to/
  - /==/
  - /!=/
  - />/
  - /</
  - />=/
  - /<=/
---
{::options parse_block_html="true" /}

**Comparison** operators return a [`Bool`](/bool) to indicate whether or not a given statement is true. They are used heavily in [if](/if) statements.

* TOC
{:toc}

{% include opencol.html size=6 newrow=true %}

### Equal to `==`

```swift
print(5 + 5 == 10) // true
print(1 + 1 == 11) // false
```

{% include closecol.html %}{% include opencol.html size=6 %}

### Not equal to `!=`

```swift
print(5 + 5 != 10) // false
print(1 + 1 != 11) // true
```

{% include closecol.html closerow=true %}

{% include opencol.html size=6 newrow=true %}

### Greater than `>`

```swift
print(5 > 10) // false
print(10 > 2) // true
```

{% include closecol.html %}{% include opencol.html size=6 %}

### Less than `<`

```swift
print(5 < 10) // true
print(10 < 2) // false
```

{% include closecol.html closerow=true %}

{% include opencol.html size=6 newrow=true %}

### Greater than or equal to `>=`

```swift
print(10 >= 10) // true
print(15 >= 16) // false
print(18 >= 12) // true
```

{% include closecol.html %}{% include opencol.html size=6 %}

### Less than or equal to `<=`

```swift
print(10 <= 10) // true
print(15 <= 16) // true
print(18 <= 12) // false
```

{% include closecol.html closerow=true %}

### Comparing equality of two struct instances

The `==` and `!=` may also be used to check to see if two struct instances have the same values. For this, the struct must conform to [`Equatable`](https://developer.apple.com/documentation/swift/equatable).

```swift
struct Player: Equatable {
  var name: String
  var score: Int
}

let player1 = Player(name: "Tomoko", score: 100)
let player2 = Player(name: "Tomoko", score: 100)
let player3 = Player(name: "Isabella", score: 350)
let player4 = player1

print(player1 == player2) // true
print(player1 == player3) // false
print(player1 == player4) // true

print(player1 != player2) // false
print(player1 != player3) // true
print(player1 != player4) // false
```

### Comparing equality of two class instances

The `==` and `!=` may also be used to check to see if two class instances have the same values. For this, the class must also conform to [`Equatable`](https://developer.apple.com/documentation/swift/equatable), which involves more work than if it was a struct.

```swift
class Player: Equatable {
  var name: String
  var score: Int

  init(name: String, score: Int) {
    self.name = name
    self.score = score
  }

  static func == (lhs: Player, rhs: Player) -> Bool {
    return lhs.name == rhs.name && lhs.score == rhs.score
  }
}

let player1 = Player(name: "Tomoko", score: 100)
let player2 = Player(name: "Tomoko", score: 100)
let player3 = Player(name: "Isabella", score: 350)
let player4 = player1

print(player1 == player2) // true
print(player1 == player3) // false
print(player1 == player4) // true

print(player1 != player2) // false
print(player1 != player3) // true
print(player1 != player4) // false
```

**Note**: While `==` and `!=` compare class instance equality, [`===` and `!==`](/identity) compare identity, which is a similar, but different concept.

### Further reading

* [Basic Operators § Comparison Operators `📖 Official Swift Book`](https://docs.swift.org/swift-book/LanguageGuide/BasicOperators.html#ID70)
