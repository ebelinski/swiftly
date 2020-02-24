---
layout: default
title: "Assignment (=, +=. -=, *=, /=)"
description: A Swift 5.1 assignment operations reference guide, covering assignment and compound assignment.
redirect_from:
  - /assign/
  - /compound-assignment/
  - /compound-assign/
  - /=/
  - /+=/
  - /-=/
  - /*=/
---
{::options parse_block_html="true" /}

### Assignment operator (`=`)

```swift
var a = 10
var b = a
print("\(a), \(b)") // 10, 10
b = 15
print("\(a), \(b)") // 10, 15
```

### Compound assignment operators

{% include opencol.html size=3 newrow=true %}

#### Addition (`+=`)

```swift
var a = 10
a += 5
print(a) // 15
```

{% include closecol.html %}{% include opencol.html size=3 %}

#### Subtraction (`-=`)

```swift
var a = 10
a -= 5
print(a) // 5
```

{% include closecol.html %}{% include opencol.html size=3 %}

#### Multiplication (`*=`)

```swift
var a = 10
a *= 5
print(a) // 50
```

{% include closecol.html %}{% include opencol.html size=3 %}

#### Division (`/=`)

```swift
var a = 10
a /= 5
print(a) // 2
```

{% include closecol.html closerow=true %}
