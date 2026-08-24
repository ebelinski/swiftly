---
layout: default
title: "If let"
description: A Swift if let statement reference guide, with an if let-else example and its nil-coalescing equivalent.
redirect_from:
  - /iflet/
---
{::options parse_block_html="true" /}

**If let** is used with [optionals](/optionals).

{% include opencol.html size=6 newrow=true %}

### If let-else

```swift
func greet(name: String?) {
  if let name {
    print("Hello \(name)!")
  } else {
    print("Hello guest!")
  }
}
greet(name: "Asma") // Hello Asma!
greet(name: nil) // Hello guest!
```

{% include closecol.html %}{% include opencol.html size=6 %}

### [Nil-coalescing](/nil-coalescing) equivalent

```swift
func greet(name: String?) {
  let unwrappedName = name ?? "guest"
  print("Hello \(unwrappedName)!")
}
greet(name: "Asma") // Hello Asma!
greet(name: nil) // Hello guest!
```

{% include closecol.html closerow=true %}

`if let name` is shorthand for `if let name = name`: it unwraps the optional into a constant of the same name. The unwrapped value can also be given a different name, as in `if let unwrappedName = name`.

### See also

* [If](/if)
* [If case let](/if-case-let)

### Further reading

* [Control Flow `📖 Official Swift Book`](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/controlflow/)