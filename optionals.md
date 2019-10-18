---
layout: default
title: "Optionals"
description: 
redirect_from:
  - /optional/
---

**Optionals** are [variables](/variables) that can have a value of `nil` (nothing). More specifically, `Optional` is a type that represents either a wrapped value of a specific type, or `nil`. For example, an optional String is a variable that holds either a wrapped String or `nil`.

An optional is denoted with a `?` or a `!`.

### Simple example

```swift
func divide(x: Int, y: Int) -> Int? {
  if y == 0 {
    return nil
  } else {
    return x / y  
  }
}

print(divide(x: 16, y: 2))
// Prints "Optional(8)"

print(divide(x: 16, y: 0))
// Prints "nil"
```

