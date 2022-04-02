---
layout: default
title: "isMainThread"
description: A Swift 5.6 @MainActor reference guide, covering declaring async functions, calling them with await, performing parallel work, using async/await with URLSession, and more.
redirect_from:
  - /ismain/
  - /is-main-thread/
  - /is-main/
  - /mainthread/
  - /main-thread/
---
{::options parse_block_html="true" /}

**isMainThread** (part of Foundation) can be used to check to see if the current `Thread` is the main thread.

* TOC
{:toc}

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
  print("someFunction() is \(Thread.isMainThread ? "running" : "not running") in the main thread.")
}

@MainActor
func someOtherFunction() {
  print("someOtherFunc() is \(Thread.isMainThread ? "running" : "not running") in the main thread.")
}


DispatchQueue.global(qos: .background).async {
  Task {
    someFunction()
    await someOtherFunction()
  }
}

// Output:
// someFunction() is not running in the main thread.
// someOtherFunc() is running in the main thread.
```

### See also

* [Dispatch](/dispatch)
* [async/await](/async-await)

### Further reading

* [isMainThread documentation](https://developer.apple.com/documentation/foundation/nsthread/1412704-ismainthread)
