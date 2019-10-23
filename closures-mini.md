---
layout: default
title: "Closures (mini version)"
description: A Swift 5.1 closures mini-guide, covering inline closures and closures as function parameters.
redirect_from: 
  - /closure-mini/
  - /block-mini/
  - /blocks-mini/
  - /lambda-mini/
  - /lambdas-mini/
---

The mini version of the [closures guide](/closures).

### Closure inline

```swift
let sorted1 = [4, 30, 7].sorted(by: { (x: Int, y: Int) -> Bool in 
  return x < y 
})
// Equivalent shorter version:
let sorted2 = [4, 30, 7].sorted { $0 < $1 }
```

### Closure as a function parameter

```swift
func multiply(x: Int, y: Int, completion: @escaping (Int, Error?) -> Void) {
  completion(x * y, nil)
}
multiply(x: 5, y: 6) { print($1 ?? $0) } // Output: 30
```

Note: Because this closure is escaping, it could be called even after the function returns.