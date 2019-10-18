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

**Structs** and **classes** are flexible, general-purpose constructs. In Swift, structs and classes are very similar to each other, but contain important differences. Instances are created from structs and classes in similar ways.

{% include opencol.html size=6 newrow=true %}

### Struct declaration

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

### Class declaration

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

{% include opencol.html size=6 newrow=true %}

### Struct usage

```swift
let player1 = PlayerStruct(name: "Tomoko", level: 1)
print(player1) // PlayerStruct(name: "Tomoko", level: 1)
print(player1.name) // Tomoko
```

{% include closecol.html %}{% include opencol.html size=6 %}

### Class usage

```swift
let player2 = PlayerClass(name: "Isabella", level: 1)
print(player2) // main.Player
print(player2.name) // Isabella
```

{% include closecol.html closerow=true %}