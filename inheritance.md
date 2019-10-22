---
layout: default
title: "Inheritance"
description: 
redirect_from: 
  - /property/
---
{::options parse_block_html="true" /}

[Classes](structs-and-classes) can **inherit** [methods](/methods), [properties](/properties), and other characteristics from other classes.

* TOC
{:toc}

### Subclassing example

```swift
class Instrument {
  var name: String

  init(name: String) {
    self.name = name
  }
}

class StringInstrument: Instrument {
  var numberOfStrings: Int

  init(name: String, numberOfStrings: Int) {
    self.numberOfStrings = numberOfStrings
    super.init(name: name)
  }
}

let guitar = StringInstrument(name: "Guitar", numberOfStrings: 6)
```

### Overriding properties

### Overriding methods

### Preventing overrides

It is possible to prevent a class from being subclassed by marking it as `final`:

```swift
final class Instrument {
  // ...
}

class StringInstrument: Instrument {
  // ...
}

// ❌ error: inheritance from a final class 'Instrument'
```
