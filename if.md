---
layout: default
title: "If"
description: 
redirect_from: 
  - /if-let/
  - /iflet/
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

### [Ternary conditional operator](/ternary)

```swift
5 > 6 ? print("5 is more than 6")
      : print("5 is not more than 6")
// Output: "5 is not more than 6"
```

{% include closecol.html closerow=true %}

{% include opencol.html size=6 newrow=true %}

### If let

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

### [Nil-coalescing operator](/nil-coalescing)

```swift
func greet(name: String?) {
  let unwrappedName = name ?? "guest"
  print("Hello \(unwrappedName)!")
}
greet(name: "Asma") // Hello Asma!
greet(name: nil) // Hello guest!
```

{% include closecol.html closerow=true %}
