---
layout: default
title: "reduce"
description: A Swift 5.4 reduce method reference guide, with a reduce [Int] example.
---
{::options parse_block_html="true" /}

**reduce** is a [functional method](/functional-methods-comparison) that returns the result of combining the elements of a sequence using a given [closure](/closures). It takes in two parameters:

* An initial value
* A closure to produce the next result

### `reduce` an array of `Ints`

```swift
let numbers = [1, 2, 3, 4]
let numbersSum = numbers.reduce(0) {
  $0 + $1
}
let numbersProduct = numbers.reduce(1) {
  $0 * $1
}
print(numbersSum) // 10
print(numbersProduct) // 24
```

The example above can be shortened to the following:

```swift
let numbers = [1, 2, 3, 4]
let numbersSum = numbers.reduce(0, +)
let numbersProduct = numbers.reduce(1, *)
print(numbersSum) // 10
print(numbersProduct) // 24
```