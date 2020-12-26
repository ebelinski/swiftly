---
layout: default
title: "Switch (case)"
description: A Swift 5.3 switch statement reference guide, with a switch with equality and a switch with tuples example.
redirect_from: 
  - /case/
---
{::options parse_block_html="true" /}

{% include opencol.html size=6 newrow=true %}

### Switch with equality

A `default` case is necessary when not all cases are covered.

```swift
func describe(animal: String) {
  switch animal {
  case "Owl", "Crane": print("A bird")
  case "Lion": print("A feline")
  case "Ant": print("An insect")
  default: print("Something else")
  }
}
describe(animal: "Owl") // "A bird"
describe(animal: "Bear") // "Something else"
```

{% include closecol.html %}{% include opencol.html size=6 %}

### Switch with tuples

Here, all cases are covered, so a `default` case is unnecessary.

```swift
func describe(point: (Int, Int)) {
  switch point {
  case (0, 0): print("At origin")
  case (_, 0): print("On x-axis")
  case (0, _): print("On y-axis")
  case (_, _): print("Elsewhere")
  }
}
describe(point: (5, 0)) // "On x-axis"
describe(point: (11, 9)) // "Elsewhere"
```

{% include closecol.html closerow=true %}

### Switch with [enum](/enums)

```swift
enum Beatle {
  case john, paul, george, ringo
}

var myFavoriteBeatle = Beatle.john

switch myFavoriteBeatle {
case .john: print("My favorite beatle played vocals and lead guitar.")
case .paul: print("My favorite beatle played vocals and bass guitar.")
case .george: print("My favorite beatle played lead and rhythm guitar.")
case .ringo: print("My favorite beatle played the drums.")
}
// Output: "My favorite beatle played vocals and lead guitar."
```

### See also

* [Switch (case let)](/switch-case-let)
