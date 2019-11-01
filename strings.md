---
layout: default
title: "Strings"
description: A Swift 5.1 strings reference guide, covering basic strings, multiline strings, string length, and string interpolation.
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

### String length with `.count()` and `.isEmpty`

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

### Searching within a String with `.contains(_:)`

```swift
import Foundation

let sentence = "Swift is my favorite programming language!"

print(sentence.contains("my favorite")) // true
print(sentence.contains("language")) // true
print(sentence.contains("intend")) // false
print(sentence.contains("charming")) // false

print(sentence.contains("you're")) // false
print(sentence.lowercased().contains("you're")) // true
```

### Find-and-replace with `replacingOccurrences(of:with:)`

```swift
import Foundation

let sentence = "Swift is my favorite programming language!"
let newSentence = sentence.replacingOccurrences(of: "Swift", with: "VBA")
print(newSentence) // VBA is my favorite programming language!
```

### Further reading

* [Strings and Characters (The Swift Programming Language)](https://docs.swift.org/swift-book/LanguageGuide/StringsAndCharacters.html)
