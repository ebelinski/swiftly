---
layout: default
title: "Errors"
description: A Swift errors reference guide, covering error declaration, throwing errors, catching errors, and typed throws.
redirect_from: 
  - /error/
---

**Errors** are represented by values that conform to the `Error` protocol. They can be thrown, caught, propagated, and recovered.

* TOC
{:toc}

### Complete example

#### Error declaration

```swift
enum DownloadError: Error {
  case unauthorized
  case notEnoughSpace(mbNeeded: Int)
}
```

#### Throwing errors

```swift
func downloadFile(mbFree: Int) throws {
  let userIsAuthorized = true
  let mbFileSize = 1000

  if !userIsAuthorized {
    throw DownloadError.unauthorized
  } else if mbFree < mbFileSize {
    throw DownloadError.notEnoughSpace(mbNeeded: mbFileSize)
  } else {
    // File download logic goes here
  }
}
```

#### Catching errors

```swift
func didPressDownloadFileButton() {
  do {
    try downloadFile(mbFree: 500)
  } catch DownloadError.unauthorized {
    print("The user is not authorized to download this file.")
  } catch DownloadError.notEnoughSpace(let mbNeeded) {
    print("The user needs \(mbNeeded) MB to download this file.")
  } catch {
    print("Unknown error: \(error).")
  }
}
```

#### Usage

```swift
didPressDownloadFileButton() // The user needs 1000 MB to download this file.
```

### Typed throws

Since Swift 6.0, a function can declare exactly which [error](/errors) type it throws with `throws(...)`. Inside the function, `throw` can use shorthand member syntax, and at the call site the compiler knows the concrete error type, so a `switch` over it is exhaustive without a fallback clause:

```swift
func downloadFile(mbFree: Int) throws(DownloadError) {
  guard mbFree >= 1000 else {
    throw .notEnoughSpace(mbNeeded: 1000)
  }
  // File download logic goes here
}

do {
  try downloadFile(mbFree: 500)
} catch {
  // error is a DownloadError here, not `any Error`
  switch error {
  case .unauthorized:
    print("The user is not authorized to download this file.")
  case .notEnoughSpace(let mbNeeded):
    print("The user needs \(mbNeeded) MB to download this file.")
  }
}

// Output: The user needs 1000 MB to download this file.
```

Untyped `throws` remains the right default for most code; typed throws is most useful in generic code and constrained environments like Embedded Swift.

### Further reading

* [Error Handling `📖 Official Swift Book`](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/errorhandling/)
