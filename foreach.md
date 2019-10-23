---
layout: default
title: "forEach"
description: A Swift 5.1 forEach reference guide, with examples examples and comparisons to for-in.
---
{::options parse_block_html="true" /}

**forEach** is a [functional method](/functional-methods-comparison) that calls a [closure](/closures) on each element in a sequence in the same order as a [for-in](/for-in) loop. It does not return anything

### Similarities to `for-in`

{% include opencol.html size=6 newrow=true %}

`forEach` loop:

```swift
let birds = ["Owl", "Crane"]
birds.forEach {
  print(bird)
}
// Output: 
// Owl
// Crane
```

{% include closecol.html %}{% include opencol.html size=6 %}

[`for-in`](/for-in) equivalent:

```swift
let birds = ["Owl", "Crane"]
for bird in birds {
  print(bird)
}
// Output: 
// Owl
// Crane
```

{% include closecol.html closerow=true %}

### Differences to `for-in`

`forEach` calls a closure on each element. This means that unlike [`for-in`](/for-in), you cannot use `break` or `continue`, and using `return` will only exit from the current closure call, not the encompassing method. The following example demonstrates this:

{% include opencol.html size=6 newrow=true %}

```swift
func findFirstNegativeNumber(numbers: [Int]) -> Int? {
  for number in numbers {
    if number < 0 { return number }
  }
  
  return nil
}

let numbers = [82, 5, -25, 10, -99]
print(findFirstNegativeNumber(numbers: numbers)) 
// Prints Optional(-25)
```

{% include closecol.html %}{% include opencol.html size=6 %}

```swift
func findFirstNegativeNumber(numbers: [Int]) -> Int? {
  numbers.forEach {
    if $0 < 0 { return $0 }
  }
  
  return nil
}

let numbers = [82, 5, -25, 10, -99]
print(findFirstNegativeNumber(numbers: numbers))
// ❌ compilation error: unexpected non-void return value in void function
// if $0 < 0 { return $0 }
//                    ^
```

{% include closecol.html closerow=true %}

What happened here? In the `for-in` loop, calling `return number` returns the method `findFirstNegativeNumber` with our value. But in the `forEach` loop, calling `return $0` actually has the effect of attempting to return the `forEach` closure, not the method `findFirstNegativeNumber`, with our value. The closure does not allow a non-void return type, so the code cannot be compiled. (Even if it could, the `findFirstNegativeNumber` method would then always return `nil`.)
