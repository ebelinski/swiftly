---
layout: default
title: "Properties"
description: A Swift 5.1 reference guide for properties of structs, classes, and enums, covering instance properties, static/class properties, and computed properties.
redirect_from: 
  - /property/
---
{::options parse_block_html="true" /}

**Properties** are [variables or constants](/variables) that belong to a [struct](/structs-and-classes), [class](/structs-and-classes), or [enum](/enums). Properties can belong either to an instance or a type.

* TOC
{:toc}

### Instance properties

Instance properties are [variables or constants](/variables) that belong to an instance of a struct, class, or enum. Example:

```swift
struct Person {
  let name: String
}

let person = Person(name: "Amy")
print("person's stored property 'name' is \(person.name)") // person's stored property 'name' is Amy
```

A stored property can have an initial value and change over time:

```swift
struct Person {
  var name: String = "No Name"
}

var person = Person()
print(person.name) // No Name
person.name = "Amy"
print(person.name) // Amy
```

If a stored property is of an [optional](/optionals) type, the default value is nil:

```swift
struct Person {
  var name: String?
}

var person = Person()
print(person.name) // nil
```

### Static/class properties

Static and class properties (also known as _type properties_) belong to a struct/class type itself, rather than an instance of a struct/class. If a type property is a stored property, it must have an initial value. They are declared with `static`:

{% include opencol.html size=6 newrow=true %}

```swift
struct Person {
  static let greeting = "Hello"
  let name: String

  init(name: String) {
    self.name = name
  }
}

print(Person.greeting) // Hello
```

{% include closecol.html %}{% include opencol.html size=6 %}

```swift
class Person {
  static let greeting = "Hello"
  let name: String

  init(name: String) {
    self.name = name
  }
}

print(Person.greeting) // Hello
```

{% include closecol.html closerow=true %}

### Computed properties

_Computed properties_ are [variables](/variables) that are computed instead of holding a stored value. See [Variables § Computed variables (get and set)](/variables/#computed-variables-get-and-set) for more information.
