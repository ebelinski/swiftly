---
layout: default
title: "While"
description: A Swift 5.5 while loop reference guide, with a simple while and a repeat-while example.
---
{::options parse_block_html="true" /}

A **while** loop will run the code block each time the conditional is true. A repeat-while loop will run the block first without checking the conditional, then keep on running it as long as the conditional is true.

{% include opencol.html size=6 newrow=true %}

### Simple while

```swift
var steps = 2
while steps > 0 {
  print("\(steps) steps left")
  steps -= 1
}
// Output:
// 2 steps left
// 1 steps left
```
```swift
var steps = -999
while steps > 0 {
  print("\(steps) steps left")
  steps -= 1
}
// Output: nothing
```

{% include closecol.html %}{% include opencol.html size=6 %}

### Repeat-while

```swift
var steps = 2
repeat {
  print("\(steps) steps left")
  steps -= 1
} while steps > 0
// Output:
// 2 steps left
// 1 steps left
```
```swift
var steps = -999
repeat {
  print("\(steps) steps left")
  steps -= 1
} while steps > 0
// Output: "-999 steps left"
```

{% include closecol.html closerow=true %}

### Further reading

* [Control Flow `📖 Official Swift Book`](https://docs.swift.org/swift-book/LanguageGuide/ControlFlow.html)