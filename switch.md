---
layout: default
title: "Switch"
description: 
redirect_from: 
  - /case/
---
{::options parse_block_html="true" /}

{% include opencol.html size=6 newrow=true %}

#### Switch with equality

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
describe(animal: "Owl")
describe(animal: "Giraffe")
// Output: 
// "A bird"
// "Something else"
```

{% include closecol.html %}{% include opencol.html size=6 %}

#### Switch with tuples

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
describe(point: (5, 0))
describe(point: (11, 9))
// Output: 
// "On x-axis"
// "Elsewhere"
```

{% include closecol.html closerow=true %}
