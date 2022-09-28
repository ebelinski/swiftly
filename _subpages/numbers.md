---
layout: default
title: "Numbers"
description: A Swift 5.6 numbers reference guide, covering Ints, Floats, Doubles, and converting between them.
redirect_from:
  - /integer/
  - /integers/
  - /int/
  - /ints/
  - /double/
  - /doubles/
  - /float/
  - /floats/
  - /number/
  - /num/
---

Swift contains three main number types: `Int`, `Double`, and `Float`.

* TOC
{:toc}

### Integers (`Int`)

By default, numbers without fractional components are inferred to be `Ints`:

```swift
let myNumber = 5 // Inferred to be of type Int
```

`Ints` cannot have decimal values:

```swift
let myNumber: Int = 5.75 // ❌ error: cannot convert value of type 'Double' to specified type 'Int'
```

[Arithmetic](/math) can be performed on integers, but decimal values will be ignored and rounded _down_.

```swift
print(20 / 3)   // 6 (not ~6.666666667)
print(9 / 4)    // 2 (not 2.25)
print(100 / 99) // 1 (not ~1.01010101)
```

### Doubles (`Double`)

`Doubles` are floating-point numbers that are represented as 64-bits. They are similar to `Floats`. By default, numbers with fractional components are usually inferred to be `Doubles`:

```swift
let myNumber = 5.0
```

[Arithmetic](/math) can be performed on `Doubles` and is more accurate than arithmetic on `Ints`:

```swift
print(20.0 / 3.0)   // 6.666666666666667
print(9.0 / 4.0)    // 2.25
print(100.0 / 99.0) // 1.0101010101010102
```

### Floats (`Float`)

`Floats` are floating-point numbers that are represented as 32-bits. They are similar to `Doubles`, but they take up _less space_ and are _less precise_.

```swift
let myNumber: Float = 5.0
```

### Converting between `Int`, `Float`, and `Double`

A `Double` can be converted to a `Float`, but precision may be lost:

```swift
let myDouble: Double = 834.4938247489
let myFloat = Float(myDouble)
print(myFloat) // 834.49384
```

A `Float` or `Double` can be converted to an `Int` but the fractional component is rounded _down_:

```swift
let myFloat = 9.999
let myInt = Int(myFloat)
print(myInt) // 9
```

An `Int` can be converted to a `Float` or `Double`:

```swift
let myInt = 5
print(Float(myInt))  // 5.0
print(Double(myInt)) // 5.0
```
