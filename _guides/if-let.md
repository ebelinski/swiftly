---
layout: default
title: "If let"
description: A Swift 5.3 if let statement reference guide, with an if let-else example and its nil-coalescing equivalent.
redirect_from:
  - /iflet/
---
{::options parse_block_html="true" /}

**If let** is used with [optionals](/optionals).

{% include opencol.html size=6 newrow=true %}

### If let-else

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

### See also

* [If](/if)
* [If case let](/if-case-let)