---
layout: default
title: "Nil-coalescing operator (??)"
description: A Swift 5.4 nil-coalescing operator (??) reference guide, with an example and a comparison to let-else.
redirect_from:
  - /ternary-conditional-operator/
  - /ternary-operator/
---
{::options parse_block_html="true" /}

The **nil-coalescing  operator** is a shorthand alternative to [if let-else](/if).

{% include opencol.html size=6 newrow=true %}

### Example if let-else

```swift
func greet(name: String?) {
  if let unwrappedName = name {
    print("Hello \(unwrappedName)!")
  } else {
    print("Hello guest!")
  }  
}
greet(name: "Asma") // Hello Asma!
greet(name: nil) // Hello guest!
```

{% include closecol.html %}{% include opencol.html size=6 %}

### Nil-coalescing equivalent

```swift
func greet(name: String?) {
  let unwrappedName = name ?? "guest"
  print("Hello \(unwrappedName)!")
}
greet(name: "Asma") // Hello Asma!
greet(name: nil) // Hello guest!
```

{% include closecol.html closerow=true %}

### Further reading

* [Basic Operators § Nil-Coalescing Operator `📖 Official Swift Book`](https://docs.swift.org/swift-book/LanguageGuide/BasicOperators.html#ID72)
