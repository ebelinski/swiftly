---
layout: default
title: "In-out parameters"
description: A Swift 5.6 nil-coalescing operator (??) reference guide, with an example and a comparison to let-else.
redirect_from:
  - /inout/
---
{::options parse_block_html="true" /}

**In-out parameters** are [function](/functions) parameters whose values can be modified, with those modifications persisting after the function ends.

{% include opencol.html size=6 newrow=true %}

### Function with an `inout` parameter

```swift
func haveBirthday(age: inout Int) {
  print("Happy birthday!")
  age += 1
}
```

{% include closecol.html %}{% include opencol.html size=6 %}

### Passing in an `inout` parameter with `&`

```swift
var myAge = 50
print("I am \(myAge).")

haveBirthday(age: &myAge)
print("Now I am \(myAge).")

// Output:
// I am 50.
// Happy birthday!
// Now I am 51.
```

{% include closecol.html closerow=true %}

### Further reading

* [Functions `📖 Official Swift Book`](https://docs.swift.org/swift-book/LanguageGuide/Functions.html)
