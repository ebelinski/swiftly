---
layout: default
title: "Comparison operators (==, !=, >, <, >=, <=)"
description: 
redirect_from:
  - /range/
  - /range-operator/
  - /range-operators/
  - /closed-range/
  - /closed-range-operator/
  - /half-open-range/
  - /half-open-range-operator/
  - /one-sided-range/
  - /one-sided-range-operator/
---
{::options parse_block_html="true" /}

**Comparison** operators return a [`Bool`](/bool) to indicate whether or not a given statement is true. They are used heavily in [if](/if) statements.

{% include opencol.html size=6 newrow=true %}

### Equal to `==`

```swift
print(5 + 5 == 10) // true
print(1 + 1 == 11) // false
```

{% include closecol.html %}{% include opencol.html size=6 %}

### Not equal to `!=`

```swift
print(5 + 5 != 10) // false
print(1 + 1 != 11) // true
```

{% include closecol.html closerow=true %}

{% include opencol.html size=6 newrow=true %}

### Greater than `>`

```swift
print(5 > 10) // false
print(10 > 2) // true
```

{% include closecol.html %}{% include opencol.html size=6 %}

### Less than `<`

```swift
print(5 < 10) // true
print(10 < 2) // false
```

{% include closecol.html closerow=true %}

{% include opencol.html size=6 newrow=true %}

### Greater than or equal to `>=`

```swift
print(10 >= 10) // true
print(15 >= 16) // false
print(18 >= 12) // true
```

{% include closecol.html %}{% include opencol.html size=6 %}

### Less than or equal to `<=`

```swift
print(10 <= 10) // true
print(15 <= 16) // true
print(18 <= 12) // false
```

{% include closecol.html closerow=true %}
