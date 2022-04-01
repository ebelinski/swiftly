---
layout: default
title: "async/await"
description: A Swift 5.6 async/await reference guide.
redirect_from:
  - /async/
  - /await/
---
{::options parse_block_html="true" /}

**async** and **await** are keywords used to run asynchronous code as if it was synchronous.

* TOC
{:toc}

{% include opencol.html size=6 newrow=true %}

### Declaring `async` functions

Async function declarations must be marked with `async`:

```swift
func getGames() async -> [String] {
  let games = // async networking code...
  return games
}

func getPlayers() async -> [String] {
  let players = // async networking code...
  return players
}

func getScores() async -> [Int] {
  let scores = // async networking code...
  return scores
}
```

{% include closecol.html %}{% include opencol.html size=6 %}

### Calling async functions with `await`

Async functions need to be awaited with `await`:

```swift
// These will execute sequentially. Once getGames() finishes, getPlayers() will start, and so on.

let games = await getGames()
let players = await getPlayers()
let scores = await getScores()

print(games)
print(players)
print(scores)
```

{% include closecol.html closerow=true %}

### Use `Task` outside of an async context

Unless an `async` function is being called from another `async` function, it must be wrapped in a `Task`:

```swift
Task {
  let games = await getGames()
  print(games)
}
```

### Calling async functions in parallel with `async`

`async`/`await` can be combined to call multiple `async` methods at the same time, and then continue execution when all parallel methods have finished.

```swift
// These 3 methods will start at the same time, but may finish at different times.
async let games = getGames()
async let players = getPlayers()
async let scores = getScores()

let everything = await [games, players, scores]
// This line won't execute until all 3 methods above have finished.
print(everything)
```

### URLSession example

The following compares a `GET` request via URLSession using `async`/`await` on the left and using the more traditional [closure](/closures)-based completion block syntax on the right.

Notice how on the left, `getGames` is executed from top to bottom. In comparison on the right, `getGames` execution jumps from creating `task` to calling `task.resume()`, then jumps back up to execute the completion block.

{% include opencol.html size=6 newrow=true %}

#### `async`/`await` version

```swift
import Foundation
import _Concurrency // If using Playgrounds

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
```

{% include closecol.html %}{% include opencol.html size=6 %}

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
    let games = try! decoder.decode(
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
```

{% include closecol.html closerow=true %}

### Calling completion block functions from an `async` function

Legacy functions that still use completion blocks can still be called from `async` methods using `withCheckedContinuation`. In this example, `continuation.resume(returning:)` must be called **exactly one time**.

```swift
import Foundation
import _Concurrency // If using Playgrounds

func legacyGetGames(completion: @escaping ([String]) -> Void) {
  URLSession.shared.dataTask(with: URL(string: "https://swiftly.dev/api/games")!) { data, _, _ in
    let games = try! JSONDecoder().decode([String].self, from: data!)
    completion(games)
  }.resume()
}

func getGames() async -> [String] {
  return await withCheckedContinuation { continuation in
    legacyGetGames() { games in
      continuation.resume(returning: games)
    }
  }
}

Task {
  let games = await getGames()
  print(games)
}

// Output: ["Backgammon", "Chess", "Go", "Mahjong"]
```

### Combining `async` with `throws`

Async functions can still throw errors, but they must be called with `try await`:

```swift
import Foundation
import _Concurrency // If using Playgrounds

func getGames() async throws -> [String] {
  let (data, _) = try await URLSession.shared.data(from: URL(string: "tel:5555555555")!)
  let games = try JSONDecoder().decode([String].self, from: data)

  return games
}

Task {
  do {
    let games = try await getGames()
    print(games)
  } catch {
    print("Could not get games: \(error.localizedDescription)")
  }
}

// Output: Could not get games: unsupported URL
```

### Further reading

* [Concurrency `📖 Official Swift Book`](https://docs.swift.org/swift-book/LanguageGuide/Concurrency.html)
