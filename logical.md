---
layout: default
title: "Logical operators (!, &&, ||)"
description: 
redirect_from:
  - /logical-not/
  - /logical-and/
  - /logical-or/
  - /not/
  - /and/
  - /or/
---
{::options parse_block_html="true" /}

**Logical** operators return a [`Bool`](/bool) to indicate whether or not a given statement is true. They are used heavily in [if](/if) statements.

### Logical NOT `!`

```swift
let name = "Tomoko"
print(name.isEmpty)
print(!name.isEmpty)
if !name.isEmpty { 
  print("name is not empty")
}
// false
// true
// name is not empty
```
