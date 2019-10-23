---
layout: default
title: "Guard"
description: A Swift 5.1 guard statement reference guide, with a simple guard and a guard let example.
redirect_from: 
  - /guard-let/
---
{::options parse_block_html="true" /}

**Guard** can be used to reduce indentation on the happy path. In a guard statement, the _else_ branch _must_ transfer control to exit the code block containing the guard statement. This can be done with _return_, _break_, _continue_, or _throw_.

{% include opencol.html size=6 newrow=true %}

### Simple guard

```swift
func divide(x: Int, y: Int) -> Int? {
  guard y != 0 else {
    print("You cannot divide by 0.")
    return nil
  }
  let answer = x / y
  return answer
}
print(divide(x: 5, y: 0))
// Output: 
// You cannot divide by 0.
// nil
```

{% include closecol.html %}{% include opencol.html size=6 %}

### Guard let

```swift
func greet(name: String?) {
  guard let unwrapped = name else {
    print("Hello guest!")
    return
  }
  print("Hello \(unwrapped)!")
}
greet(name: "Asma")
greet(name: nil)
// Output: 
// Hello Asma!
// Hello guest!
```

{% include closecol.html closerow=true %}