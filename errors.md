---
layout: default
title: "Errors"
description: A Swift 5.1 errors reference guide, covering .
redirect_from: 
  - /method/
---
{::options parse_block_html="true" /}

**Errors** in Swift are represented by values that conform to the `Error` protocol. They can be thrown, caught, propagated, and recovered.

### Complete example

```swift
// Error declaration
enum DownloadError: Error {
  case unauthorized
  case notEnoughSpace(mbNeeded: Int)
}

// Function that throws errors
func downloadFile(mbFree: Int) throws {
  let apiManager = APIManager()

  if !apiManager.userIsAuthorized {
    throw DownloadError.unauthorized
  } else if mbFree < apiManager.mbFileSize {
    throw DownloadError.notEnoughSpace(mbNeeded: apiManager.mbFileSize)
  } else {
    apiManager.downloadFile()
  }
}

// Function that catches errors
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

// Helper struct
struct APIManager {
  var userIsAuthorized = true
  var mbFileSize = 1000

  func downloadFile() {
    // File download logic goes here
  }
}

// Usage
didPressDownloadFileButton() // Output: The user needs 1000 MB to download this file.
```
