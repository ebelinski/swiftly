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
```

{% include closecol.html closerow=true %}

### Further reading

* [Concurrency `📖 Official Swift Book`](https://docs.swift.org/swift-book/LanguageGuide/Concurrency.html)
