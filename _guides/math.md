---
layout: default
title: "Math (+, -, *, /, %)"
description: A Swift 5.5 math operations reference guide, covering addition, subtraction, multiplication, division, and remainder (modulo).
redirect_from:
  - /addition/
  - /add/
  - /plus/
  - /subtraction/
  - /minus/
  - /division/
  - /divide/
  - /multiplication/
  - /multiply/
  - /times/
  - /remainder/
  - /modulo/
  - /unary/
  - /unary-plus/
  - /unary-minus/
  - /+/
  - /-/
  - /*/
---
{::options parse_block_html="true" /}

* TOC
{:toc}

{% include opencol.html size=6 newrow=true %}

### Addition (`+`)

```swift
print(5 + 10) // 15
print(100 + 25) // 125
// Strings can be added too:
print("foo" + "bar") // "foobar"
```

{% include closecol.html %}{% include opencol.html size=6 %}

### Subtraction (`-`)

```swift
print(5 - 10) // -5
print(100 - 25) // 75
```

{% include closecol.html closerow=true %}

{% include opencol.html size=6 newrow=true %}

### Multiplication (`*`)

```swift
print(5 * 10) // 50
print(100 * 25) // 2500
```

{% include closecol.html %}{% include opencol.html size=6 %}

### Division (`/`)

```swift
print(5 / 10) // 0
print(100 / 25) // 4
```

{% include closecol.html closerow=true %}

### Remainder (`%`)

The remainder operator can be used to find the _modulus_: the remainder after division of one number by another.

```swift
print(9 % 2) // 1
print(100 % 10) // 0
print(100 % 95) // 5
```

### Unary operators

A prefixed `-` can be used to toggle the sign of a value. A prefixed `+` does nothing, but can be used for code symmetry. No space is allowed between the operator and the value.

{% include opencol.html size=6 newrow=true %}

#### Unary minus (`-`)

```swift
let a = 5
let b = -a
print(b) // -5
```

{% include closecol.html %}{% include opencol.html size=6 %}

#### Unary plus (`+`)

```swift
let a = 5
let b = +a
print(b) // 5
```

{% include closecol.html closerow=true %}

### Further reading

* [Basic Operators § Arithmetic Operators `📖 Official Swift Book`](https://docs.swift.org/swift-book/LanguageGuide/BasicOperators.html#ID63)
