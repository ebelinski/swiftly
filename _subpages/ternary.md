---
layout: default
title: "Ternary conditional operator (_ ? _ : _)"
description: A Swift 5.6 ternary conditional operator reference guide, with an example and a comparison to if-else.
redirect_from:
  - /ternary-conditional-operator/
  - /ternary-operator/
---
{::options parse_block_html="true" /}

The **ternary conditional operator** is a shorthand alternative to [if-else](/if).

{% include opencol.html size=6 newrow=true %}

### Example [if-else](\if)

```swift
if 5 > 6 {
  print("5 is more than 6")
} else {
  print("5 is not more than 6")
}
// Output: "5 is not more than 6"
```

{% include closecol.html %}{% include opencol.html size=6 %}

### Equivalent ternary

```swift
5 > 6 ? print("5 is more than 6")
      : print("5 is not more than 6")
// Output: "5 is not more than 6"
```

{% include closecol.html closerow=true %}

### See also

* [If](/if)

### Further reading

* [Basic Operators § Ternary Conditional Operator `📖 Official Swift Book`](https://docs.swift.org/swift-book/LanguageGuide/BasicOperators.html#ID63)
