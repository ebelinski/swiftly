---
layout: default
title: "Strings"
description: A Swift 5.6 strings reference guide, covering basic strings, multiline strings, string length, and string interpolation.
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
let myString = "Swift is my favorite language!"
```

{% include opencol.html size=6 newrow=true %}

### String with line breaks

```swift
let myString = "Swift?\nIt's my favorite language!"

print(myString)
// Output:
// "Swift?
// It's my favorite language!"
```

{% include closecol.html %}{% include opencol.html size=6 %}

### Multiline string

```swift
let myLongString = """
Swift?
It's my favorite language!
"""

print(myString)
// Output:
// "Swift?
// It's my favorite language!"
```

{% include closecol.html closerow=true %}

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

### Search within a String with `.contains(_:)`

```swift
import Foundation

let sentence = "Swift is my favorite language!"

print(sentence.contains("Swift")) // true
print(sentence.contains("my favorite")) // true

print(sentence.contains("swift")) // false
print(sentence.contains("charming")) // false
```

### Case-insensitive search with `.contains(_:)` or `range(of:options:)`

```swift
import Foundation

let sentence = "Swift is my favorite language!"
print(sentence.lowercased().contains("swift")) // true
print(sentence.range(of: "swift", options: .caseInsensitive) != nil) // true
```

### Find-and-replace with `replacingOccurrences(of:with:)`

```swift
import Foundation

let sentence = "Swift is my favorite language!"
let newSentence = sentence.replacingOccurrences(of: "Swift", with: "VBA")
print(newSentence) // VBA is my favorite language!
```

### Trimming whitespace and new lines with `trimmingCharacters(in:)`

```swift
import Foundation

let sentence = "   Swift is my favorite language!\n\n  "
let newSentence = sentence.trimmingCharacters(in: .whitespacesAndNewlines)
print(newSentence) // Swift is my favorite language!
```

### Further reading

* [Strings and Characters `📖 Official Swift Book`](https://docs.swift.org/swift-book/LanguageGuide/StringsAndCharacters.html)
