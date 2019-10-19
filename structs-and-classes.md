---
layout: default
title: "Structs & classes"
description: 
redirect_from: 
  - /structs/
  - /struct/
  - /classes/
  - /class/
  - /structs-classes/
  - /struct-class/
---
{::options parse_block_html="true" /}

* TOC
{:toc}

**Structs** and **classes** are flexible, general-purpose constructs. In Swift, structs and classes are very similar to each other, but contain important differences. Instances are created from structs and classes in similar ways.

### Declaration comparison

{% include opencol.html size=6 newrow=true %}

#### Struct declaration

```swift
struct PlayerStruct {
  var name: String
  var level: Int

  init(name: String, level: Int) {
    self.name = name
    self.level = level
  }
}
```

{% include closecol.html %}{% include opencol.html size=6 %}

#### Class declaration

```swift
class PlayerClass {
  var name: String
  var level: Int

  init(name: String, level: Int) {
    self.name = name
    self.level = level
  }
}
```

{% include closecol.html closerow=true %}

### Usage comparison

{% include opencol.html size=6 newrow=true %}

#### Struct usage

```swift
let player1 = PlayerStruct(name: "Tomoko", 
                           level: 1)
print(player1) // PlayerStruct(name: "Tomoko", level: 1)
print(player1.name) // Tomoko
```

{% include closecol.html %}{% include opencol.html size=6 %}

#### Class usage

```swift
let player2 = PlayerClass(name: "Isabella", 
                          level: 1)
print(player2) // main.Player
print(player2.name) // Isabella
```

{% include closecol.html closerow=true %}

### Value types (Structs) versus reference types (Classes)

Structs are _value types_, like `Int` and `String`, so when a struct instance is assigned to a new variable or passed to a function, the whole instance value is _copied_.

In contrast, classes are _reference types_, so when a class instance is assigned to a new variable or passed to a function, a reference to the same existing instance is used. The instance is not actually copied.

The example below demonstrates this in practice:

{% include opencol.html size=6 newrow=true %}

```swift
struct Player {
  var name: String

  init(name: String) {
    self.name = name
  }
}

var player1 = Player(name: "Tomoko")
var player2 = player1
player2.name = "Isabella"

print(player1.name) // Tomoko
print(player2.name) // Isabella
```

{% include closecol.html %}{% include opencol.html size=6 %}

```swift
class Player {
  var name: String

  init(name: String) {
    self.name = name
  }
}

var player1 = Player(name: "Tomoko")
var player2 = player1
player2.name = "Isabella"

print(player1.name) // Isabella
print(player2.name) // Isabella
```

{% include closecol.html closerow=true %}