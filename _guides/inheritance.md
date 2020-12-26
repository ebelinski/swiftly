---
layout: default
title: "Inheritance"
description: A Swift 5.3 class inheritance reference guide, covering subclassing, overriding properties, overriding methods, preventing overrides, and accessing superclass properties and methods.
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

### Overriding methods

[Methods](/methods) of a superclass can be overridden in a subclass with `override`:

```swift
class Instrument {
  var name: String

  init(name: String) {
    self.name = name
  }

  func describe() {
    print("This instrument is called a \(name).")
  }
}

class StringInstrument: Instrument {
  var numberOfStrings: Int

  init(name: String, numberOfStrings: Int) {
    self.numberOfStrings = numberOfStrings
    super.init(name: name)
  }

  override func describe() {
    print("This \(numberOfStrings)-string instrument is called a \(name).")
  }
}

let guitar = StringInstrument(name: "Guitar", numberOfStrings: 6)
guitar.describe() // This 6-string instrument is called a Guitar.
```

### Overriding properties

[Computed variables](/variables/#computed-variables-get-and-set) can be overridden with `override`:

```swift
class Circle {
  var radiusInMeters: Float = 100

  var radiusInFeet: Float {
    get {
      radiusInMeters * 3.28
    }
    set(newradiusInFeet) {
      radiusInMeters = newradiusInFeet / 3.28
    }
  }
}

class MoreAccurateCircle: Circle {
  override var radiusInFeet: Float {
    get {
      radiusInMeters * 3.28084
    }
    set(newradiusInFeet) {
      radiusInMeters = newradiusInFeet / 3.28084
    }
  }
}
```

### Preventing overrides

It is possible to prevent a class from being subclassed by marking it as `final`:

```swift
final class Instrument {}
class StringInstrument: Instrument {}
// ❌ error: inheritance from a final class 'Instrument'
```

`final` may also be used on properties and methods to prevent overriding:

```swift
class Instrument {
  final var name: String

  init(name: String) {
    self.name = name
  }

  final func describe() {
    print("This instrument is called a \(name).")
  }
}
```

### Accessing superclass properties and methods

Properties and methods belonging to a superclass can be accessed with `super`:

```swift
class Instrument {
  var name: String

  init(name: String) {
    self.name = name
  }

  func describe() {
    print("This instrument is called a \(name).")
  }
}

class StringInstrument: Instrument {
  var numberOfStrings: Int

  init(name: String, numberOfStrings: Int) {
    self.numberOfStrings = numberOfStrings
    super.init(name: name)
  }

  override func describe() {
    super.describe()
    print("...and it has \(numberOfStrings) strings.")
  }
}

let guitar = StringInstrument(name: "Guitar", numberOfStrings: 6)
guitar.describe() 
// This instrument is called a Guitar.
// ...and it has 6 strings.
```