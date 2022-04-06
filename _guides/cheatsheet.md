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
let myString = "5.5"
```

### [Variables](/variables)

```swift
var myInt = 5
myInt = myInt + 5
```

### Type annotations

```swift
let myInt: Int = 5
let myString: String = "5.5"
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
if let unwrappedInt = myInt {
  print("myInt is \(unwrappedInt)")
}
// Output: "myInt is 5"
```

{% include closecol.html %}{% include opencol.html size=4 %}

### [Enum](/enums)

```swift
enum CompassPoint {
  case north, south, east, west
}
var direction: CompassPoint = .north
```

### [Switch](/switch) statement

```swift
switch direction {
case .north: print("Going north!")
case .south: print("Going south...")
default: print("Going east or west.")
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
print("Square of 6 is: \(squareOf6)")
// Output: "Square of 6 is: 36"
```

{% include closecol.html %}{% include opencol.html size=4 %}

### Declaring a [struct](/structs-and-classes)

```swift
struct MyStruct {
  var myInt: Int
  let myStr: String
  mutating func squareMyInt() {
    myInt = myInt * myInt
  }
}
```

### Instantiating a [struct](/structs-and-classes)

```swift
var obj = MyStruct(myInt: 5,
                   myStr: "Hi! 👋")
obj.squareMyInt()
print("\(obj.myStr) \(obj.myInt)")
// Output: "Hi! 👋 25"
```

### [Array](/arrays)

```swift
var myArr = [1, 3]
myArr.append(5)
```

### Loop over [array](/arrays)

```swift
var sum = 0
for element in myArr {
  sum += element
}
print(sum)
// Output: "9"
```

{% include closecol.html closerow=true %}
