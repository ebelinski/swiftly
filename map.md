---
layout: default
title: "map"
description: 
---
{::options parse_block_html="true" /}

**map** is a [functional method](/functional-methods-comparison) that returns an [array](/arrays) that contains the results of mapping a given [closure](/closures) over the elements of a sequence. Similar methods are [compactMap](/compactmap) and [flatMap](/flatmap).

### `map` over array of `Ints`

```swift
let numbers = [1, 2, 3, 4]
let numbersSquared = numbers.map { $0 * $0 }
print(numbersSquared) // [1, 4, 9, 16]
```

### `map` over array of `Strings`

```swift
let players = ["Ayesha", "Beatrix", "Chris", "Daisy"]
let playersLowercased = players.map { $0.lowercased() }
print(playersLowercased) // ["ayesha", "beatrix", "chris", "daisy"]
```
