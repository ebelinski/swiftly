---
layout: default
title: "Switch (case let)"
description: A Swift 5.1 switch case let statement reference guide, with a switch case let example and its if case let equivalent.
redirect_from: 
  - /switchcaselet/
---
{::options parse_block_html="true" /}

**[Switch](/switch) case let** can be used with [enums](/enums) with associated values.

{% include opencol.html size=6 newrow=true %}

Example:

```swift
enum Barcode {
  case qr(String)
  case upc(Int, Int, Int, Int)
}

func describe(_ code: Barcode) {
  switch code {
  case let .qr(value):
    print("QR: \(value)")
  case let .upc(ns, m, i, c):
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

[If case let](/if-case-let) equivalent:

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

{% include closecol.html closerow=true %}

Alternatively, `let` can be written before each variable name:

{% include opencol.html size=6 newrow=true %}

Same example as above:

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

{% include closecol.html %}{% include opencol.html size=6 %}

[If case let](/if-case-let) equivalent:

```swift
enum Barcode {
  case qr(String)
  case upc(Int, Int, Int, Int)
}

func describe(_ code: Barcode) {
  if case .qr(let value) = code {
    print("QR: \(value)")
  } else if case .upc(let ns, let m, let i, let c) = code {
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

### See also

* [Switch (case)](/switch)
