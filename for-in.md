---
layout: default
title: "For-in"
description: 
redirect_from:
  - /for/
---
{::options parse_block_html="true" /}

The common for loop `for (i = a; i < b; i++)` does not exist in Swift. Instead, the **for-in** can be modified to have an index using tuples and _[enumerated](https://developer.apple.com/documentation/swift/array/1687832-enumerated)_:

{% include opencol.html size=6 newrow=true %}

### Simple for-in

```swift
let birds = ["Owl", "Crane"]
for bird in birds {
  print(bird)
}
// Output: 
// Owl
// Crane
```

{% include closecol.html %}{% include opencol.html size=6 %}

### For-in with index

```swift
let birds = ["Owl", "Crane"]
for (i, bird) in birds.enumerated() {
  print("[\(i)]: \(bird)")
}
// Output: 
// [0]: Owl
// [1]: Crane
```

{% include closecol.html closerow=true %}

### See also

* [forEach](/foreach)