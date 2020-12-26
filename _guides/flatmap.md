---
layout: default
title: "flatMap"
description: A Swift 5.3 flatMap reference guide, with a flatMap over [Int] example.
---
{::options parse_block_html="true" /}

**flatMap** is a [functional method](/functional-methods-comparison) that returns an [array](/arrays) that contains the results of mapping a given [closure](/closures) over the elements of a sequence, with the exception that if the results are arrays, they are concatenated to one array. Similar methods are [map](/map) and [compactMap](/compactmap).

### `flatMap` over array of `Ints`

```swift
let numbers = [1, 2, 3, 4]
let eachNumber3Times = numbers.flatMap { Array(repeating: $0, count: 3) }
print(eachNumber3Times) // [1, 1, 1, 2, 2, 2, 3, 3, 3, 4, 4, 4]
```

For reference, here is what would happen if we used [map](/map) with this example instead:

```swift
let numbers = [1, 2, 3, 4]
let eachNumber3Times = numbers.map { Array(repeating: $0, count: 3) }
print(eachNumber3Times) // [[1, 1, 1], [2, 2, 2], [3, 3, 3], [4, 4, 4]]
```
