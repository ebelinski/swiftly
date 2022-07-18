---
layout: default
title: "async/await"
description: A Swift 5.6 async/await reference guide, covering declaring async functions, calling them with await, performing parallel work, using async/await with URLSession, and more.
redirect_from:
  - /async/
  - /await/
  - /asyncawait/
  - /await-async/
  - /awaitasync/
---
{::options parse_block_html="true" /}

**async** and **await** are keywords used to run asynchronous code as if it was synchronous. A function can be marked with `async` to make it asynchronous, and an asyncronous function can be called with `await` to halt execution until the asynchronous function returns.

On Apple platforms, `async`/`await` requires iOS 13+, macOS Monterey+, watchOS 6+, or tvOS 13+. Apple-provided async/await APIs such as URLSession's async methods require iOS 15+, but can be [backported](https://www.swiftbysundell.com/articles/making-async-system-apis-backward-compatible/). [Dispatch](/dispatch) remains as an alternative for older platforms.

* TOC
{:toc}

{% include opencol.html size=6 newrow=true %}

### Declaring `async` functions

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

Calling an `async` function from a synchronous context requires must be done in a `Task`:

```swift
Task {
  let games = await getGames()
  print(games)
}
```

### Calling async functions in parallel

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

### Combining `async` with `throws`

Async functions can still throw [errors](/errors), but they must be called with `try await`:

```swift
import Foundation
import _Concurrency // If using Playgrounds

func getGames() async throws -> [String] {
  let 📞 = URL(string: "tel:5555555555")!
  let (data, _) = try await URLSession.shared.data(from: 📞)
  return try JSONDecoder().decode([String].self, from: data)
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

### Calling completion block functions from an `async` function

#### Using `withCheckedContinuation`

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

#### Using `withCheckedThrowingContinuation`

```swift
import Foundation
import _Concurrency // If using Playgrounds

func legacyGetGames(completion: @escaping (Result<[String], Error>) -> Void) {
  let 📞 = URL(string: "tel:5555555555")!
  URLSession.shared.dataTask(with: 📞) { data, _, error in
    if let error = error {
      completion(.failure(error))
      return
    }
    let games = try! JSONDecoder().decode([String].self, from: data!)
    completion(.success(games))
  }.resume()
}

func getGames() async throws -> [String] {
  return try await withCheckedThrowingContinuation { continuation in
    legacyGetGames() { result in
      switch result {
      case .success(let games): continuation.resume(returning: games)
      case .failure(let error): continuation.resume(throwing: error)
      }
    }
  }
}

Task {
  do {
    let games = try await getGames()
    print(games)
  } catch {
    print("Could not get games: \(error.localizedDescription)")
  }
}

// Output: ["Backgammon", "Chess", "Go", "Mahjong"]
```

### See also

* [@MainActor](/mainactor)
* [Dispatch](/dispatch)
* [isMainActor](/ismainactor)

### Further reading

* [Concurrency `📖 Official Swift Book`](https://docs.swift.org/swift-book/LanguageGuide/Concurrency.html)
* [Connecting async/await to other Swift code](https://www.swiftbysundell.com/articles/connecting-async-await-with-other-swift-code/)
