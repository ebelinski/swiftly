---
layout: default
title: "sorted() and sorted(by:)"
description: A Swift 5.4 sorted() and sorted(by:) methods reference guide, with examples for both.
redirect_from:
  - /sort/
  - /sorting/
  - /sort-by/
  - /sorted-by/
---
{::options parse_block_html="true" /}

**sorted()** and **sorted(by:)** are [functional methods](/functional-methods-comparison) that return the elements of a sequence sorted using a particular predicate.

* TOC
{:toc}

### `sorted()`

Sorts a sequence of elements without a custom predicate. Requires that the elements are of a type that conforms to `Comparable`.

```swift
let numbers = [4, 200, 75, 0]
let numbersSorted = numbers.sorted()
print(numbersSorted) // [0, 4, 75, 200]
```

### `sorted(by:)`

Sorts a sequence of elements with a custom predicate.

#### `Int` examples

```swift
let numbers = [4, 200, 75, 0]
let numbersAsceniding = numbers.sorted(by: <)
let numbersDescending = numbers.sorted(by: >)
print(numbersAsceniding) // [0, 4, 75, 200]
print(numbersDescending) // [200, 75, 4, 0]
```

#### `Player` example

```swift
struct Player {
  var name: String
  var score: Int
}

let players = [
  Player(name: "Louis", score: 100)
  Player(name: "Tomoko", score: 775)
  Player(name: "Isabella", score: 350)
]

let playersSortedByScore = players.sorted() {
  $0.score < $1.score
}
print(playersSortedByScore) // [main.Player(name: "Louis", score: 100), main.Player(name: "Isabella", score: 350), main.Player(name: "Tomoko", score: 775)]
```

In this example, it would not be possible to use `.sorted()`, `.sorted(by: <)`, or `.sorted(by: >)` because `Player` does not conform to `Comparable`.
