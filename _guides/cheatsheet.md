---
layout: default
title: Swift 5.6 cheatsheet
description: A beautiful and clutter-free Swift 5.6 cheatsheet, covering constants, variables, type annontations, if statements, optionals, enums, switch statements, functions, structs, and arrays.
redirect_from:
  - /swift-cheatsheet/
---
{::options parse_block_html="true" /}

{% include opencol.html size=4 newrow=true %}

### [Constants](/variables)

```swift
let myInt = 5
let myString = "Five"
```

### [Variables](/variables)

```swift
var myInt = 5
myInt = myInt + 5
```

### Type annotations

```swift
let myInt: Int = 5
let myString: String = "Five"
```

### [If](/if) statement

```swift
if 5 > 3 {
  print("5 is more than 3")
} else {
  print("5 is not more than 3")
}
// Output: "5 is more than 3"
```

### [Optionals](/optionals)

```swift
let myInt: Int? = 5
if let myInt = myInt {
  print("myInt is \(myInt)")
}
// Output: "myInt is 5"
```

{% include closecol.html %}{% include opencol.html size=4 %}

### [Enum](/enums)

```swift
enum Direction {
  case north, south, east, west
}
var direction = Direction.north
```

### [Switch](/switch) statement

```swift
switch direction {
case .north:
  print("Going north!")
case .south:
  print("Going south...")
default:
  print("Going east or west.")
}
// Output: "Going north!"
```

### Declaring a [function](/functions)

```swift
func square(x: Int) -> Int {
  let squaredValue = x * x
  return squaredValue
}
```

### Calling a [function](/functions)

```swift
let squareOf6 = square(x: 6)
print("6^2 is: \(squareOf6)")
// Output: "6^2 is: 36"
```

{% include closecol.html %}{% include opencol.html size=4 %}

### Declaring a [struct](/structs-and-classes)

```swift
struct Player {
  let name: String
  var score: Int
  mutating func doubleScore() {
    score *= 2
  }
}
```

### Instantiating a [struct](/structs-and-classes)

```swift
var sam = Player(name: "Sam", score: 5)
sam.doubleScore()
print("\(sam.name)'s score: \(sam.score)")
// Output: "Sam's score: 10"
```

### [Array](/arrays)

```swift
var myArr = [10, 20]
myArr.append(30)
```

### Loop over [array](/arrays)

```swift
var sum = 0
for element in myArr {
  sum += element
}
print(sum)
// Output: "60"
```

{% include closecol.html closerow=true %}
