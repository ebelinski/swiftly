---
layout: default
title: "Ternary conditional operator (_ ? _ : _)"
description: A Swift 5.1 reference sheet for the ternary conditional operator, with an example and a comparison to if-else.
redirect_from:
  - /ternary-conditional-operator/
  - /ternary-operator/
---
{::options parse_block_html="true" /}

The **ternary conditional operator** is a shorthand alternative to [if-else](/if).

{% include opencol.html size=6 newrow=true %}

### Example if-else

```swift
if 5 > 6 {
  print("5 is more than 6")
} else {
  print("5 is not more than 6")
}
// Output: "5 is not more than 6"
```

{% include closecol.html %}{% include opencol.html size=6 %}

### Equivalent ternary

```swift
5 > 6 ? print("5 is more than 6")
      : print("5 is not more than 6")
// Output: "5 is not more than 6"
```

{% include closecol.html closerow=true %}
