---
layout: default
title: "Sets"
description: A Swift 5.6 sets reference guide, covering declaration, mutability, type annotations, iteration, and manipulation.
redirect_from:
  - /set/
---
{::options parse_block_html="true" /}

**Sets** store unique values of a certain type in an unordered list. Examples:

```swift
let numbers: Set<Int> = [1, 3, 5]
let planets: Set<String> = ["Mars", "Jupiter", "Earth"]
```

Sets do not guarantee a specific order, and each value can appear only once:

```swift
let numbers: Set<Int> = [1, 3, 5, 5, 5]
print(numbers) // [3, 1, 5]
```

* TOC
{:toc}

### Mutability

Sets defined with **var** are mutable:

```swift
var planets: Set = ["Mars", "Jupiter", "Earth"]
planets.insert("Neptune")
planets.remove("Earth")
print(planets) // ["Mars", "Neptune", "Jupiter"]
```

### Type

The type of a set's elements is not required:

```swift
let numbers: Set = [1, 3, 5] // Inferred to be type Set<Int>
let planets: Set = ["Mars", "Jupiter", "Earth"] // Inferred to be Set<String>
```

But the type can also be explicitly declared:

```swift
let numbers: Set<Int> = [1, 3, 5]
let planets: Set<String> = ["Mars", "Jupiter", "Earth"]
```

### Iteration and manipulation

Sets can be iterated over using [for-in](/for-in). They can be manipulated using [map](/map), [flatMap](/flatmap), and [reduce](/reduce). They can be sorted into an [array](/arrays) using [sorted](/).

### See also

* [Collection types comparison](/collection-types-comparison)
* [Arrays](/arrays)
* [Dictionaries](/dictionaries)

### Further reading

* [Collection Types `📖 Official Swift Book`](https://docs.swift.org/swift-book/LanguageGuide/CollectionTypes.html)
