---
layout: default
title: "filter"
description: A Swift 5.1 filter method reference guide, with examples filtering over [Int] and [String].
---
{::options parse_block_html="true" /}

**filter** is a [functional method](/functional-methods-comparison) that returns an [array](/arrays) containing only the elements of a sequence that satisfy a given predicate, in their original order.

### `filter` over array of `Ints`

```swift
let numbers = [1, 2, 3, 4, 5, 6, 7]
let numbersLessThan5 = numbers.filter { $0 < 5 }
print(numbersLessThan5) // [1, 2, 3, 4]
```

### `filter` over array of `Strings`

```swift
import Foundation // Required for `String.contains()` method

let words = ["pineapple", "grapple", "banana", "applet"]
let wordsContainingApple = words.filter { $0.contains("apple") }
print(wordsContainingApple) // ["pineapple", "grapple", "applet"]
```
