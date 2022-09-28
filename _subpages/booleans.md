---
layout: default
title: "Booleans"
description: A Swift 5.6 booleans reference guide, covering declaration, mutating, and toggling.
redirect_from:
  - /boolean/
  - /bool/
---

A **boolean** (`Bool`) is a type that stores a `true` or `false` value:

```swift
let lightIsOn = true
```

### Mutating

A mutable `Bool`'s value can be changed:

```swift
var lightIsOn = true
lightIsOn = false
print(lightIsOn) // false
```

### Toggling

A convenient way to change a `Bool`'s value is with the [toggle](https://developer.apple.com/documentation/swift/bool/2994863-toggle) method:

```swift
var lightIsOn = true
lightIsOn.toggle()
print(lightIsOn) // false
lightIsOn.toggle()
print(lightIsOn) // true
```