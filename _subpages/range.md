---
layout: default
title: "Range operator (1...5)"
description: A Swift 5.6 range operator reference guide, covering closed ranges, half-open ranges, one-sided ranges, and including an array example.
redirect_from:
  - /ranges/
  - /range-operator/
  - /range-operators/
  - /closed-range/
  - /closed-range-operator/
  - /half-open-range/
  - /half-open-range-operator/
  - /one-sided-range/
  - /one-sided-range-operator/
---
{::options parse_block_html="true" /}

**Range** operators is a shortcuts for expressing a range of values.

* TOC
{:toc}

{% include opencol.html size=6 newrow=true %}

### Closed range `a...b`

```swift
for i in 1...4 {
  print(i)
}
// 1
// 2
// 3
// 4
```

{% include closecol.html %}{% include opencol.html size=6 %}

### Half-open range `a..<b`

```swift
for i in 1..<4 {
  print(i)
}
// 1
// 2
// 3
```

{% include closecol.html closerow=true %}

### Half-open range used on an array

```swift
let players = ["Ayesha", "Beatrix", "Chris", "Daisy"]
for i in 0..<players.count {
  print("Player \(i + 1) is \(players[i])")
}
// Player 1 is Ayesha
// Player 2 is Beatrix
// Player 3 is Chris
// Player 4 is Daisy
```

### One-sided-ranges `[a...]` and `[...a]`

```swift
let players = ["Ayesha", "Beatrix", "Chris", "Daisy"]
print(players[2...]) // ["Chris", "Daisy"]
print(players[...2]) // ["Ayesha", "Beatrix", "Chris"]
print(players[..<2]) // ["Ayesha", "Beatrix"]
```

### Further reading

* [Basic Operators § Range Operators `📖 Official Swift Book`](https://docs.swift.org/swift-book/LanguageGuide/BasicOperators.html#ID73)
