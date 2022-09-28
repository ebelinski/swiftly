---
layout: default
title: "isMainThread"
description: A Swift 5.6 isMainThread reference guide, with a simple example, an example using Dispatch, and an example using @MainActor and Dispatch.
redirect_from:
  - /ismain/
  - /is-main-thread/
  - /is-main/
  - /mainthread/
  - /main-thread/
---
{::options parse_block_html="true" /}

**isMainThread** (part of Foundation) can be used to check to see if the current `Thread` is the main thread.

{% include opencol.html size=6 newrow=true %}

### Simple example

```swift
import Foundation

print(Thread.isMainThread)

// Output: true
```

{% include closecol.html %}{% include opencol.html size=6 %}

### Example with [Dispatch](/dispatch)

```swift
import Foundation

print(Thread.isMainThread) // true

DispatchQueue.global(qos: .background).async {
  print(Thread.isMainThread) // false

  DispatchQueue.main.async {
    print(Thread.isMainThread) // true
  }
}
```

{% include closecol.html closerow=true %}

### Example with [@MainActor](/mainactor) function and [Dispatch](/dispatch)

```swift
import Foundation
import _Concurrency // If using Playgrounds

func someFunction() {
  print("1️⃣ On main thread: \(Thread.isMainThread)")
}

@MainActor
func someOtherFunction() {
  print("2️⃣ On main thread: \(Thread.isMainThread)")
}

DispatchQueue.global(qos: .background).async {
  Task {
    someFunction()
    await someOtherFunction()
  }
}

// Output:
// 1️⃣ On main thread: false
// 2️⃣ On main thread: true
```

### See also

* [Dispatch](/dispatch)
* [async/await](/async-await)
* [@MainActor](/mainactor)

### Further reading

* [isMainThread documentation](https://developer.apple.com/documentation/foundation/nsthread/1412704-ismainthread)
