---
layout: default
title: "Variables"
description: A Swift 5.1 reference sheet for variables and constants, covering declaration, mutability, computed variables, willSet, and didSet.
redirect_from:
  - /var/
  - /variable/
  - /constant/
  - /constants/
  - /let/
  - /computed-variable/
  - /computed-variables/
  - /didset/
  - /willset/
  - /get/
  - /set/
---
{::options parse_block_html="true" /}

**Variables and constants** are used to hold pieces of data. Variables can change over time (mutable), while constants must stay the same (immutable). The word "variables" is usually used to describe both variables and constants. Variables that belong to a [struct](/structs-and-classes), [class](/structs-and-classes), or [enum](/enums) are [properties](/properties).

* TOC
{:toc}

### Variables

Variables are declared with `var`:

```swift
var greeting "Hello"
var numberOfToys = 8
var isMorning = true
```

Variable declarations can include [type annotations](/type-annotations) for clarity:

```swift
var greeting: String "Hello"
var numberOfToys: Int = 8
var isMorning: Bool = true
```

Variables are mutable. Their values can change:

```swift
var numberOfToys: Int = 8
numberOfToys += 1
print(numberOfToys) // Prints "9"
```

### Constants

Constants are declared with `let`:

```swift
let greeting "Hello"
let numberOfToys = 8
let isMorning = true
```

Constant declarations can include [type annotations](/type-annotations) for clarity:

```swift
let greeting: String "Hello"
let numberOfToys: Int = 8
let isMorning: Bool = true
```

Constants are **not** mutable. Their values cannot change:

```swift
let numberOfToys: Int = 8
numberOfToys += 1 // ❌ Error: numberOfToys is not mutable
```

### Computed variables (`get` and `set`)

_Computed variables_ are like normal variables, but instead of actually storing a value, they provide a getter and (optional) setter that returns a value and set other properties indirectly.

In the example below, `age` is computed from `birthday` when it's requested. Because there is no setter, the keyword `get` can be omitted:

```swift
import Foundation

let df = DateFormatter()
df.dateFormat = "d MMMM yyyy"

var birthday = df.date(from: "5 June 1999")!

var age: Int {
  Calendar.current
    .dateComponents([.year],
                    from: birthday,
                    to: Date()).year!
}

print(age) // 20
birthday = df.date(from: "5 June 2002")!
print(age) // 17
```

In the example below, `distanceInFeet` has both a getter and a setter. Because there is a setter, the keyword `get` is required for the getter:

```swift
var distanceInMeters: Float = 100

var distanceInFeet: Float {
  get {
    distanceInMeters * 3.28
  }

  set(newDistanceInFeet) {
    distanceInMeters = newDistanceInFeet / 3.28
  }
}

print(distanceInMeters) // 100.0
print(distanceInFeet) // 328.0

distanceInFeet = 250
print(distanceInMeters) // 76.21951
print(distanceInFeet) // 250.0

distanceInMeters = 800
print(distanceInMeters) // 800.0
print(distanceInFeet) // 2624.0
```

### `willSet`

`willSet` can be used to execute some code before a variable's value is set:

{% include opencol.html size=7 newrow=true %}

```swift
var distance = 5 {
  willSet {
    print("distance will be set")
  }
}

distance = 10
```

{% include closecol.html %}{% include opencol.html size=5 %}

```
Output:

distance will be set
```

{% include closecol.html closerow=true %}

The new value can be accessed in `willSet`:

{% include opencol.html size=7 newrow=true %}

```swift
var distance = 5 {
  willSet(newDistance) {
    print("distance will be set to \(newDistance)")
  }
}

distance = 10
```

{% include closecol.html %}{% include opencol.html size=5 %}

```
Output:

distance will be set to 10
```

{% include closecol.html closerow=true %}

### `didSet`

`didSet` can be used to execute some code after a variable's value is set. The old value can still be accessed in this code block with `oldValue`:

{% include opencol.html size=7 newrow=true %}

```swift
var distance = 5 {
  didSet {
    print("distance was set to \(distance)")
    print("its old value was: \(oldValue)")
  }
}

distance = 10
```

{% include closecol.html %}{% include opencol.html size=5 %}

```
Output:

distance was set to 10
its old value was: 5
```

{% include closecol.html closerow=true %}

### `willSet` with `didSet`

`willSet` with `didSet` can be used together:

{% include opencol.html size=7 newrow=true %}

```swift
var distance = 5 {
  willSet(newDistance) {
    print("distance will be set to \(newDistance)")
  }

  didSet {
    print("distance was set to \(distance)")
    print("its old value was: \(oldValue)")
  }
}

distance = 10
```

{% include closecol.html %}{% include opencol.html size=5 %}

```
Output:

distance will be set to 10
distance was set to 10
its old value was: 5
```

{% include closecol.html closerow=true %}
