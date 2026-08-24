---
layout: default
title: "Protocols"
description: A Swift 5.6 protocols reference guide.
redirect_from: 
  - /protocol/
---
{::options parse_block_html="true" /}

**Protocols** are blueprints that define [properties](/properties) and [methods](/methods) required for a certain purpose. 

* TOC
{:toc}

### Declaring a protocol

```swift

```

### Instance methods

Instance methods belong to an instance of a struct, class, or enum. They may access the instance's variables. Below are examples of an instance method `intro()`:

{% include opencol.html size=4 newrow=true %}

#### Struct example

```swift
struct Person {
  let name: String

  init(name: String) {
    self.name = name
  }

  func intro() {
    print("I'm \(name).")
  }
}

let amy = Person(name: "Amy")
amy.intro() // I'm Amy.
```

{% include closecol.html %}{% include opencol.html size=4 %}

#### Class example

```swift
class Person {
  let name: String

  init(name: String) {
    self.name = name
  }

  func intro() {
    print("I'm \(name).")
  }
}

let amy = Person(name: "Amy")
amy.intro() // I'm Amy.
```

{% include closecol.html %}{% include opencol.html size=4 %}

#### Enum example

```swift
enum Beatle: String {
  case john
  case paul
  case george
  case ringo

  func intro() {
    print("I'm \(rawValue).")
  }
}

let john = Beatle.john
john.intro() // I'm john.
```

{% include closecol.html closerow=true %}

#### Mutating instance methods

Because structs are value types, an instance method that modifies its instance must be marked as `mutating`:

```swift
struct Player {
  var name: String
  var level: Int

  mutating func levelUp() {
    level += 1
  }
}

var player = Player(name: "Amy", level: 1)
player.levelUp()
print(player.level) // 2
```

### Static/class methods

Static and class methods (also known as _type methods_) belong to a struct/class type itself, rather than an instance of a struct/class. They are declared with `static` for a struct or `class` for a class:

{% include opencol.html size=6 newrow=true %}

```swift
struct Person {
  let name: String

  init(name: String) {
    self.name = name
  }

  static func intro() {
    print("I'm a static method.")
  }
}

Person.intro() // I'm a static method.
```

{% include closecol.html %}{% include opencol.html size=6 %}

```swift
class Person {
  let name: String

  init(name: String) {
    self.name = name
  }

  class func intro() {
    print("I'm a class method.")
  }
}

Person.intro() // I'm a class method.
```

{% include closecol.html closerow=true %}

### Further reading

* [Methods `📖 Official Swift Book`](https://docs.swift.org/swift-book/LanguageGuide/Methods.html)
