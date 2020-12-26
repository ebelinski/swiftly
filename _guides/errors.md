---
layout: default
title: "Errors"
description: A Swift 5.3 errors reference guide, covering error declaration, throwing errors, and catching errors.
redirect_from: 
  - /error/
---
{::options parse_block_html="true" /}

**Errors** are represented by values that conform to the `Error` protocol. They can be thrown, caught, propagated, and recovered.

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
  var userIsAuthorized = true
  var mbFileSize = 1000

  if !userIsAuthorized {
    throw DownloadError.unauthorized
  } else if mbFree < mbFileSize {
    throw DownloadError.notEnoughSpace(mbNeeded: apiManager.mbFileSize)
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
