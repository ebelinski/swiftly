---
layout: default
title: "Properties"
description: 
redirect_from: 
  - /property/
---
{::options parse_block_html="true" /}

**Properties** are values that belong to a [struct](/structs-and-classes), [class](/structs-and-classes), or [enum](/enums). There are two types:

- Stored properties
- Computed properties

* TOC
{:toc}

### Stored properties (instance)

Stored properties are [variables or constants](/variables) that belong to an instance of a struct, class, or enum. Example:

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

### Computed properties (instance)

_Computed properties_ are like stored properties, but instead of actually storing a value, they provide a getter and (optional) setter that returns a value and set other properties indirectly.

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

