---
layout: default
title: "Strings"
description: 
redirect_from:
  - /string/
  - /str/
  - /characters/
  - /character/
  - /char/
---
{::options parse_block_html="true" /}

* TOC
{:toc}

### Basic string

```swift
let myString = "Swift is my favorite programming language!"
```

### String with line breaks

```swift
let myString = "Swift?\nIt's my favorite programming language!"

print(myString)
// Output:
// "Swift?
// It's my favorite programming language!"
```

### Multiline string

```swift
let myLongString = """
Swift?
It's my favorite programming language!
"""

print(myString)
// Output:
// "Swift?
// It's my favorite programming language!"
```

### Determining string length with `.count()` and `.isEmpty`

{% include opencol.html size=6 newrow=true %}

```swift
let myString = "Hello world!"
print(myString.count) // 12
print(myString.isEmpty) // false
```

{% include closecol.html %}{% include opencol.html size=6 %}

```swift
let emptyString = ""
print(emptyString.count) // 0
print(emptyString.isEmpty) // true
```

{% include closecol.html closerow=true %}

### String interpolation with `\(stringName)`

String interpolation is a more efficient way of combining strings than by adding strings with the `+` operator.

```swift
let name = "Tomoko"
let location = "Sydney"
print("Hi, I'm \(name), from \(location).")
// Output: "Hi, I'm Tomoko, from Sydney."
```
