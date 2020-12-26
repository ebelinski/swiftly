---
layout: default
title: "map"
description: A Swift 5.3 map method reference guide, with examples mapping over [Int] and [String].
---
{::options parse_block_html="true" /}

**map** is a [functional method](/functional-methods-comparison) that returns an [array](/arrays) that contains the results of mapping a given [closure](/closures) over the elements of a sequence. Similar methods are [compactMap](/compactmap) and [flatMap](/flatmap).

{% include opencol.html size=6 newrow=true %}

### `map` over array of `Ints`

```swift
let numbers = [1, 2, 3, 4]
let numbersSquared = numbers.map { $0 * $0 }
print(numbersSquared) // [1, 4, 9, 16]
```

{% include closecol.html %}{% include opencol.html size=6 %}

### `map` over array of `Strings`

```swift
let players = ["Ava", "Beatrix", "Chris"]
let lowercased = players.map { $0.lowercased() }
print(lowercased) // ["ava", "beatrix", "chris"]
```

{% include closecol.html closerow=true %}