---
layout: default
title: "Enums"
description: A Swift 5.3 enums reference guide, covering basic enums, basic usage, switch usage, associated values, raw values, and iterating over cases.
redirect_from:
  - /enum/
  - /enumeration/
  - /enumerations/
  - /case/
  - /cases/
  - /enumerated/
  - /enumerating/
---
{::options parse_block_html="true" /}

**Enums** (short for _enumerations_) define a type-safe common type for a group of related values.

* TOC
{:toc}

{% include opencol.html size=6 newrow=true %}

### Basic enum

```swift
enum Beatle {
  case john
  case paul
  case george
  case ringo
}
```

{% include closecol.html %}{% include opencol.html size=6 %}

### Cases declared on the same line

```swift
enum Beatle {
  case john, paul, george, ringo
}
```

{% include closecol.html closerow=true %}

### Using an enum

```swift
var myFavoriteBeatle = Beatle.john
print(myFavoriteBeatle) // john

myFavoriteBeatle = .ringo
print(myFavoriteBeatle) // ringo
```

### Matching an enum variable with [`switch`](/switch)

```swift
enum Beatle {
  case john, paul, george, ringo
}

var myFavoriteBeatle = Beatle.john

switch myFavoriteBeatle {
case .john: print("My favorite beatle played vocals and lead guitar.")
case .paul: print("My favorite beatle played vocals and bass guitar.")
case .george: print("My favorite beatle played lead and rhythm guitar.")
case .ringo: print("My favorite beatle played the drums.")
}
// Output: "My favorite beatle played vocals and lead guitar."
```

### Associated values

Enum cases can have associated values, and the type of each value can be different:

```swift
enum Barcode {
  case qr(String)
  case upc(Int, Int, Int, Int)
}

let barcode1 = Barcode.qr("example.com")
let barcode2 = Barcode.upc(0, 12345, 67890, 5)

switch barcode2 {
case .qr(let value):
  print("QR barcode with value \(value)")
case .upc(let numberSystem, let manufacturer, let item, let check):
  print("UPC barcode with value \(numberSystem) \(manufacturer) \(item) \(check)")
}
// Output: "UPC barcode with value 0 12345 67890 5"
```

### Raw values

Enum cases can also have raw values. These are similar to associated values above, but they are prepopulated with default values:

```swift
enum Hello: String {
  case english = "Hello"
  case japanese = "こんにちは"
  case emoji = "👋"
}

print(Hello.japanese.rawValue) // こんにちは
```

### Implicit raw values

Raw values can be implicitly assigned:

```swift
enum Beatle: String {
  case john, paul, george, ringo
}

print("My favorite beatle is \(Beatle.john.rawValue).") // My favorite beatle is john.
```

### Initializing from raw values

An enum case can be initialized from a raw value, and the initializer returns an optional:

```swift
enum Hello: String {
  case english = "Hello"
  case japanese = "こんにちは"
  case emoji = "👋"
}

let hello1 = Hello(rawValue: "こんにちは")
let hello2 = Hello(rawValue: "Привет")

print(hello1) // Optional(Hello.japanese)
print(hello2) // nil
```

### Iterating over cases

If an enum conforms to `CaseIterable`, its cases can be iterated over:

```swift
enum Beatle: String, CaseIterable {
  case john, paul, george, ringo
}

for beatle in Beatle.allCases {
  print("\(beatle) is a Beatle.")
}
// Output:
// "john is a Beatle.
// paul is a Beatle.
// george is a Beatle.
// ringo is a Beatle."
```
