---
layout: default
title: "async/await"
description: A Swift 5.6 async/await reference guide.
redirect_from:
  - /async/
  - /await/
---
{::options parse_block_html="true" /}

<<<<<<< HEAD
**async** and **await** are keywords used to run asynchronous code as if it was synchronous.
=======
**async** and **await** are flexible, general-purpose constructs. In Swift, structs and classes are very similar to each other, but contain important differences. Instances are created from structs and classes in similar ways.
>>>>>>> main

* TOC
{:toc}

<<<<<<< HEAD
### URLSession example

The following compares a `GET` request via URLSession using `async`/`await` on the left and using the more traditional [closure](/closures)-based completion block syntax on the right.

Notice how on the left, `getGames` is executed from top to bottom. In comparison on the right, `getGames` execution jumps from creating `task` to calling `task.resume()`, then jumps back up to execute the completion block.

{% include opencol.html size=6 newrow=true %}

#### `async`/`await` version

```swift
import Foundation

func getGames() async -> [String] {
  let urlString = "https://swiftly.dev/api/games"
  let url = URL(string: urlString)!
  let session = URLSession.shared
  let decoder = JSONDecoder()

  let (data, _) = try! await session.data(from: url)
  let games = try! decoder.decode(
    [String].self,
    from: data
  )

  return games
}

Task {
  let games = await getGames()
  print(games)
}

// Output: ["Backgammon", "Chess", "Go", "Mahjong"]
=======
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
>>>>>>> main
```

{% include closecol.html %}{% include opencol.html size=6 %}

<<<<<<< HEAD
#### [Closure](/closures) version

```swift
import Foundation

func getGames(
  completion: @escaping ([String]) -> Void
) {
  let urlString = "https://swiftly.dev/api/games"
  let url = URL(string: urlString)!
  let session = URLSession.shared
  let decoder = JSONDecoder()

  let task = session.dataTask(with: url) {
    data, _, _ in
    let games = try! ecoder.decode(
      [String].self,
      from: data!
    )

    completion(games)
  }

  task.resume()
}

getGames() { games in
  print(games)
}

// Output: ["Backgammon", "Chess", "Go", "Mahjong"]
=======
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
>>>>>>> main
```

{% include closecol.html closerow=true %}

### Further reading

<<<<<<< HEAD
* [Concurrency `📖 Official Swift Book`](https://docs.swift.org/swift-book/LanguageGuide/Concurrency.html)
=======
* [Structures and Classes `📖 Official Swift Book`](https://docs.swift.org/swift-book/LanguageGuide/ClassesAndStructures.html)
>>>>>>> main
