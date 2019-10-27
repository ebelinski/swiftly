---
layout: default
title: "Enums"
description: 
redirect_from:
  - /enum/
  - /enumeration/
  - /enumerations/
  - /case/
  - /cases/
  - /enumerated/
  - /enumerating/
---
{::options parse_block_html="true" /}

**Enums** (short for _enumerations_) define a type-safe common type for a group of related values.

* TOC
{:toc}

{% include opencol.html size=6 newrow=true %}

### Basic enum

```swift
enum Beatle {
  case john
  case paul
  case george
  case ringo
}
```

{% include closecol.html %}{% include opencol.html size=6 %}

### Cases declared on the same line

```swift
enum Beatle {
  case john, paul, george, ringo
}
```

{% include closecol.html closerow=true %}

### Using an enum

```swift
var myFavoriteBeatle = Beatle.john
print(myFavoriteBeatle) // john

myFavoriteBeatle = .ringo
print(myFavoriteBeatle) // ringo
```

### Matching an enum variable with [`switch`](/switch)

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

### Associated values

Enums can have associated values, and the type of each value can be different:

```swift
enum Shape {
  case triangleWithSides(Int, Int, Int)
  case circleWithRadius(Float)
}

let shape1 = Shape.triangleWithSides(2, 3, 4)
let shape2 = Shape.circleWithRadius(12.5)

switch shape1 {
  case .triangleWithSides(let side1, let side2, let side3):
    print("The shape is a triangle with side lenghts \(side1), \(side2), and \(side3).")
  case .circleWithRadius(let radius):
    print("The shape is a circle with radius \(radius).")
}
// Output: "The shape is a triangle with side lenghts 2, 3, and 4."
```

### Raw values



### Implicit raw values



### Initializing from raw values



### Iterating over cases

If an enum conforms to `CaseIterable`, its cases can be iterated over:

```swift
enum Beatle: String, CaseIterable {
  case john, paul, george, ringo
}

for beatle in Beatle.allCases {
  print("\(beatle) is a Beatle.")
}
// Output:
// "john is a Beatle.
// paul is a Beatle.
// george is a Beatle.
// ringo is a Beatle."
```
