---
layout: default
title: "compactMap"
description: 
---
{::options parse_block_html="true" /}

**compactMap** is a [functional method](/functional-methods-comparison) that returns an [array](/arrays) that contains the results of mapping a given [closure](/closures) over the elements of a sequence. Similar methods are [map](/map) and [flatMap](/flatMap).

### `compactMap` over array of `Strings`

Here, `Int()` is an initializer that returns an optional `Int`: an `Int` if the string can be converted to one, and `nil` otherwise. Importantly, the resulting array is of type `[Int]` (not `[Int?]`).

```swift
let numberStrings = ["1", "2", "3", "four"]
let numbers = numberStrings.compactMap { Int($0) }
print(numbers) // [1, 2, 3]
```

For reference, here is what would happen if we used [map](/map) with this example instead:

```swift
let numberStrings = ["1", "2", "3", "four"]
let numbers = numberStrings.map { Int($0) }
print(numbers) // [Optional(1), Optional(2), Optional(3), nil]
```
