---
layout: default
title: "Math (+, -, *, /, %)"
description: A Swift 5.1 math operations reference guide, covering addition, subtraction, multiplication, division, and remainder (modulo).
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
---
{::options parse_block_html="true" /}

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
print(5 / 10) // -5
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
