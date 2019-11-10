---
layout: default
title: "If"
description: A Swift 5.1 if statement reference guide, covering if-else, if let, the ternary conditional operator, and the nil-coalescing operator.
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

### [Ternary conditional](/ternary) equivalent

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

{% include opencol.html size=6 newrow=true %}

### If case let

```swift
enum Barcode {
  case qr(String)
  case upc(Int, Int, Int, Int)
}

func describe(_ code: Barcode) {
  if case let .qr(value) = code {
    print("QR: \(value)")
  } else if case let .upc(ns, m, i, c) = code {
    print("UPC: \(ns) \(m) \(i) \(c)")
  }
}

describe(Barcode.qr("example.com"))
describe(Barcode.upc(0, 12345, 67890, 5))
// Output:
// QR: example.com
// UPC: 0 12345 67890 5
```

{% include closecol.html %}{% include opencol.html size=6 %}

### [Switch](/switch) equivalent

```swift
enum Barcode {
  case qr(String)
  case upc(Int, Int, Int, Int)
}

func describe(_ code: Barcode) {
  switch code {
    case .qr(let value):
      print("QR: \(value)")
    case .upc(let ns, let m, let i, let c):
      print("UPC: \(ns) \(m) \(i) \(c)")
  }
}

describe(Barcode.qr("example.com"))
describe(Barcode.upc(0, 12345, 67890, 5))
// Output:
// QR: example.com
// UPC: 0 12345 67890 5
```

{% include closecol.html closerow=true %}
