---
layout: default
title: "Logical operators (!, &&, ||)"
description: A Swift 5.6 logical operators reference guide, covering logical NOT (!),n logical AND (&&), logical OR (||), and examples combining logical operators.
redirect_from:
  - /logical-not/
  - /logical-and/
  - /logical-or/
  - /not/
  - /and/
  - /or/
  - /!/
  - /&&/
---
{::options parse_block_html="true" /}

**Logical** operators return a [`Bool`](/bool) to indicate whether or not a given statement is true. They are used heavily in [if](/if) statements.

### Logical NOT `!`

```swift
let name = "Tomoko"
print(name.isEmpty) // false
print(!name.isEmpty) // true
if !name.isEmpty { 
  print("name is not empty") // name is not empty
}
```

{% include opencol.html size=6 newrow=true %}

### Logical AND `&&`

```swift
let loggedIn = true
let accountConfirmed = true
if loggedIn && accountConfirmed {
  print("The user is logged in and their account is confirmed.")
} else {
  print("Either not logged in, account not confirmed, or both.")
}
// The user is logged in, and their account is confirmed.
```

{% include closecol.html %}{% include opencol.html size=6 %}

### Logical OR `||`

```swift
let loggedIn = true
let accountConfirmed = false
if loggedIn || accountConfirmed {
  print("Either logged in, account confirmed, or both.")
} else {
  print("Not logged in and account not confirmed.")
}
// Either logged in, account confirmed, or both.
```

{% include closecol.html closerow=true %}

### Combining logical operators

Multiple logical operators can be combined to create longer expressions. Although operators `&&` and `||` are left-associative, it is usually beneficial to include parentheses for readability.

```swift
let loggedIn = true
let accountConfirmed = true
let browsingAsGuest = false
if (loggedIn && accountConfirmed) || browsingAsGuest {
  print("The user is logged in with a confirmed account, or they are browsing as guest.")
}
// The user is logged in with a confirmed account, or they are browsing as guest.
```

### Further reading

* [Basic Operators § Logical Operators `📖 Official Swift Book`](https://docs.swift.org/swift-book/LanguageGuide/BasicOperators.html#ID76)
