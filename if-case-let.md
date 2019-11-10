---
layout: default
title: "If case let"
description: A Swift 5.1 if case let statement reference guide, with an if case let example and its switch case let equivalent.
redirect_from: 
  - /ifcaselet/
  - /ifcase/
---
{::options parse_block_html="true" /}

**If case let** can be used with [enums](/enums) with associated values.

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

### [Switch case let](/switch-case-let) equivalent

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
