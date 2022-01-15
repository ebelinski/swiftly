---
layout: default
title: "Closures"
description: A Swift 5.5 closures reference guide, covering inline closures, closures as variables, closure typealiases, and @escaping closures.
redirect_from:
  - /closure/
  - /fuckingswiftblocksyntax/
  - /block/
  - /blocks/
  - /lambda/
  - /lambdas/
---

**Closures** are blocks of functionality that are self-contained, and can be passed around. They are similar to _blocks_ in C and Objective-C, as well as _lambdas_ in other languages. [Functions](/functions) are a special type of closures.

* TOC
{:toc}

### Closure expression syntax

Closures can be defined with _closure expression syntax_, which has the general form:

<pre class="with-placeholders">
{ (<span class="placeholder">parameters</span>) -> <span class="placeholder">return type</span> in
  <span class="placeholder">statements</span>
}
</pre>

### Closure inline

Using **closure expression syntax**:

```swift
let sortedInts = [4, 30, 7, 9, 1].sorted(by: { (x: Int, y: Int) -> Bool in
  return x < y
})
```

Because this closure is the last and only argument,[^1] **trailing closure syntax** may be used and the **parentheses** are optional:

```swift
let sortedInts = [4, 30, 7, 9, 1].sorted { (x: Int, y: Int) -> Bool in
  return x < y
}
```

When the argument and/or return types are known, the **type annotations** are optional:

```swift
let sortedInts = [4, 30, 7, 9, 1].sorted { x, y in return x < y }
```

Also, closure parameters can be referenced by **position** instead of by name:

```swift
let sortedInts = [4, 30, 7, 9, 1].sorted { $0 < $1 }
```

### Closure as a variable

A closure can be stored as a [variable](/variables) and used later. Using closure expression syntax:

```swift
let myClosure = { (x: Int, y: Int) -> Bool in
  return x < y
}
let sortedInts = [4, 30, 7, 9, 1].sorted(by: myClosure)
```

### Closure as a function

A [function](/functions") is a type of closure, so a closure can be stored as a function to be used later.

```swift
func myClosure(x: Int, y: Int) -> Bool {
  return x < y
}
let sortedInts = [4, 30, 7, 9, 1].sorted(by: myClosure)
```

### Function with a closure parameter

A function can be created with a closure parameter:

```swift
func multiply(x: Int, y: Int, completion: (Int) -> Void) {
  completion(x * y)
}
multiply(x: 5, y: 6) { print($0) } // Output: 30
```

A closure parameter may be **optional**:

```swift
func multiply(x: Int, y: Int, completion: ((Int) -> Void)?) {
  completion?(x * y)
}
multiply(x: 5, y: 6) { print($0) } // Output: 30
```

It may have **labeled** arguments for readability:[^2]

```swift
func multiply(x: Int, y: Int, completion: (_ result: Int) -> Void) {
  completion(x * y)
}
multiply(x: 5, y: 6) { print($0) } // Output: 30
```

Or **multiple** arguments: 

```swift
func multiply(x: Int, y: Int, completion: (Int, Error?) -> Void) {
  completion(x * y, nil)
}
multiply(x: 5, y: 6) { print($1 ?? $0) } // Output: 30
```

Or **no** arguments:

```swift
func multiply(x: Int, y: Int, completion: () -> Void) {
  completion()
}
multiply(x: 5, y: 6) { print("Hello") } // Output: Hello
```

### Typealias for a closure parameter

To improve readability and reduce duplicate code, a closure **typealias** may be used:

```swift
typealias MultiplyCompletion = (_ result: Int, _ error: Error?) -> Void
func multiply(x: Int, y: Int, completion: MultiplyCompletion) {
  completion(x * y, nil)
}
multiply(x: 5, y: 6) { print($1 ?? $0) } // Output: 30
```

### Function with an `@escaping` closure parameter

An escaping closure can be called even after the function has returned:[^3]

```swift
func multiplyRemotely(x: Int, y: Int, completion: @escaping (Int) -> Void) {
  APIManager.shared.multiply(x: x, y: y, completion: completion)
}
multiplyRemotely(x: 5, y: 6) { print($0) }
// Output: 30
```

### Closure that captures variables

A closure can _capture_ a variable. This closure captures `greeting`:

```swift
var greeting = "Hello"
let greet = { print(greeting) }

greet() // Hello
greeting = "Bonjour"
greet() // Bonjour
```

A **capture list**, such as `[greeting]`, can be used to capture a _copy_ of a variable:

```swift
var greeting = "Hello"
let greet = { [greeting] in print(greeting) }

greet() // Hello
greeting = "Bonjour"
greet() // Hello
```

A closure can have both a capture list and parameters:

```swift
var greeting = "Hello"
let greet = { [greeting] (name: String) in print("\(greeting), \(name)") }

greet("Isabella") // Isabella
```

### Further reading

* [Closures `📖 Official Swift Book`](https://docs.swift.org/swift-book/LanguageGuide/Closures.html)

### Notes

[^1]: When a closure is the last parameter of a function, it is called a **trailing closure**.
[^2]: It is commonly asked why the argument names don't appear in the closure call, like `completion(result: x * y)`. The reason for this is that as of Swift 3, closure argument labels are [no longer part of the closure type](https://github.com/apple/swift-evolution/blob/master/proposals/0111-remove-arg-label-type-significance.md).
[^3]: This makes it possible to make a network call to a remote server, return the function, then have the closure get executed when the server response is received. The benefit of this is that the rest of the execution of the function, and subsequently parent functions, do not have to get blocked while the app waits for a response.
