---
layout: default
title: "Swift 4 guide: control flow"
description: A quick reference guide for control flow in Swift 4, with if, if-else, if-let, guard, for-in, while, and switch examples.
redirect_from: 
  - /control/
  - /while/
---
{::options parse_block_html="true" /}

<div id="compact-toc">
* TOC
{:toc}
</div>

### While

A while loop will run the code block each time the conditional is true. A repeat-while loop will run the block first without checking the conditional, then keep on running it as long as the conditional is true.

{% include opencol.html size=6 newrow=true %}

#### Simple while

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

#### Repeat-while

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

* ["Control Flow" in _The Swift Programming Language_ by Apple](https://developer.apple.com/library/content/documentation/Swift/Conceptual/Swift_Programming_Language/ControlFlow.html#//apple_ref/doc/uid/TP40014097-CH9-ID120)