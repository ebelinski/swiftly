---
layout: default
title: "If"
description: A Swift 5.3 if statement reference guide, with an if-else example and its ternary conditional equivalent.
redirect_from:
  - /if-else/
---
{::options parse_block_html="true" /}

{% include opencol.html size=6 newrow=true %}

### If-else

```swift
if 5 > 6 {
  print("5 is more than 6")
} else {
  print("5 is not more than 6")
}
// Output: "5 is not more than 6"
```

{% include closecol.html %}{% include opencol.html size=6 %}

### [Ternary conditional](/ternary) equivalent

```swift
5 > 6 ? print("5 is more than 6")
      : print("5 is not more than 6")
// Output: "5 is not more than 6"
```

{% include closecol.html closerow=true %}

### See also

* [If let](/if-let)
* [If case let](/if-case-let)

### Further reading

* [Control Flow `📖 Official Swift Book`](https://docs.swift.org/swift-book/LanguageGuide/ControlFlow.html)