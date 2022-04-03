---
layout: default
title: "@MainActor"
description: A Swift 5.6 @MainActor reference guide, covering declaring functions, structs, and classes with @MainActor, and its limitations.
redirect_from:
  - /main-actor/
---
{::options parse_block_html="true" /}

**@MainActor** is a keyword that is used to ensure a function or class only runs on the main thread. This can be used to ensure that UI updates are only done on the main thread, and not on a background thread.

* TOC
{:toc}

### `@MainActor` functions

You can ensure that a function only runs on the main thread by marking it with `@MainActor`:

```swift
import _Concurrency // If using Playgrounds

@MainActor
func someFunction() {
  print("This function is running on the main thread.")
}

Task {
  await someFunction()
}

// Output: This function is running on the main thread.
```

### `@MainActor` structs and classes

You can also ensure an entire [struct or class](/structs-and-classes) runs on the main thread with `@MainActor`:

```swift
import _Concurrency // If using Playgrounds

@MainActor
struct SomeStruct {
  func someFunction() {
    print("This function is running on the main thread.")
  }
}

Task {
  let someStruct = await SomeStruct()
  await someStruct.someFunction()
}
```

### Limitations

A piece of code marked with `@MainActor` might still contain additional logic that runs on a different threat if it is sent to a different [dispatch](/dispatch) queue:

```swift
import Foundation
import _Concurrency // If using Playgrounds

@MainActor
func someFunction() {
  print("1️⃣ On main thread: \(Thread.isMainThread)")

  DispatchQueue.global(qos: .background).async {
    print("2️⃣ On main thread: \(Thread.isMainThread)")
  }
}

Task {
  await someFunction()
}

// Output:
// 1️⃣ On main thread: true
// 2️⃣ On main thread: false
```

### See also

* [Dispatch](/dispatch)
* [async/await](/async-await)
* [isMainThread](/ismainthread)

### Further reading

* [MainActor documentation](https://developer.apple.com/documentation/swift/mainactor)
