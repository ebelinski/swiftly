---
layout: default
title: "Arrays"
description: 
redirect_from: 
  - /array/
---
{::options parse_block_html="true" /}

Arrays store values of a certain type in an ordered list. Examples:

```swift
let someInts = [1, 3, 5]
let someStrings = ["Hello", "Planet", "Earth"]
let someArraysOfInts = [[1, 2], [10, 20]]
```

### Mutability

Arrays defined with **var** are mutable:

```swift
var someStrings = ["Hello", "Planet", "Earth"]
someStrings.append("Neptune")
someStrings.remove(at: 2)
print(someStrings) // ["Hello", "Planet", "Neptune"]
```

### Type

The type of an array can be determined without type annotations:

```swift
let someInts = [1, 3, 5] // Inferred to be type [Int]
let someStrings = ["Hello", "Planet", "Earth"] // Inferred to be [String]
```

But the type can also be explicitly declared:

```swift
let someInts: [Int] = [1, 3, 5]
let someStrings: [String] = ["Hello", "Planet", "Earth"]
```

### Arrays that allow any element type

Arrays can be declared to be of type `[Any]` in order to allow the insertion of any type of element:

```swift
var myArray1: [Any] = [1, 2, 3]
myArray1.append("Moon")
print(myArray1) // [1, 2, 3, "Moon"]

var myArray2 = [1, 2, 3]
myArray2.append("Moon") // ❌ Error: Unexpected type
```

### Iteration and manipulation

Arrays can be iterated over using [for-in](/for-in) and [forEach](/foreach). They can be manipulated using [map](/map), [flatMap](/flatmap), [reduce](/reduce), and [sorted](/).

...
