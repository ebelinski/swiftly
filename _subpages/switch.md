---
layout: default
title: "Switch (case)"
description: A Swift 5.6 switch statement reference guide, with a switch with equality and a switch with tuples example.
redirect_from:
  - /case/
---
{::options parse_block_html="true" /}

* TOC
{:toc}

{% include opencol.html size=6 newrow=true %}

### Switch with equality

A `default` case is necessary when not all cases are covered.

```swift
func describe(animal: String) {
  switch animal {
  case "Owl", "Crane":
    print("\(animal) is a bird")
  case "Lion":
    print("\(animal) is a feline")
  case "Ant":
    print("\(animal) is an insect")
  default:
    print("\(animal) is something else")
  }
}

describe(animal: "Owl") // "A bird"
describe(animal: "Bear") // "Something else"
```

{% include closecol.html %}{% include opencol.html size=6 %}

### Switch with tuples

A `default` case is unnecessary when all cases are covered.

```swift
func describe(point: (Int, Int)) {
  switch point {
  case (0, 0):
    print("\(point) is at the origin")
  case (_, 0):
    print("\(point) is on the x-axis")
  case (0, _):
    print("\(point) is on the y-axis")
  case (_, _):
    print("\(point) is somewhere else")
  }
}

describe(point: (5, 0)) // "On x-axis"
describe(point: (11, 9)) // "Elsewhere"
```

{% include closecol.html closerow=true %}

{% include opencol.html size=6 newrow=true %}

### Switch with [enum](/enums)

```swift
enum Beatle { case john, paul, george, ringo }

var myFavoriteBeatle = Beatle.john

switch myFavoriteBeatle {
case .john:
  print("My favorite played vocals & lead guitar.")
case .paul:
  print("My favorite played vocals & bass guitar.")
case .george:
  print("My favorite played lead & rhythm guitar.")
case .ringo:
  print("My favorite played the drums.")
}
// Output: "My favorite played vocals & lead guitar."
```

{% include closecol.html %}{% include opencol.html size=6 %}

### Switch with [range](/range)

```swift
let userAge = 25

switch userAge {
case 0..<13:
  print("The user is a child.")
case 13..<18:
  print("The user is a teenager.")
case 18...Int.max:
  print("The user is an adult.")
default:
  print("Invalid age.")
}

// Output: "The user is an adult."
```

{% include closecol.html closerow=true %}

### See also

* [Switch (case let)](/switch-case-let)

### Further reading

* [Control Flow `📖 Official Swift Book`](https://docs.swift.org/swift-book/LanguageGuide/ControlFlow.html)
