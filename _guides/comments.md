---
layout: default
title: "Comments"
description: A Swift 5.1 comments reference guide, covering simple comments, multiline comments, MARK, TODO, and FIXME.
redirect_from:
  - /comment/
  - /commenting/
  - /coment/
  - /mark/
  - /pragma/
  - /pragmamark/
  - /todo/
  - /fixme/
---

**Comments** are used to include nonexecutable code in text, such as notes and reminders.

### Simple comment

```swift
// This is a simple comment.
```

### Multiline comment

A multiline comment can be started with `/*` and ended with `*/`.

```swift
/* This is a comment written 
over a whole big long
bunch of lines. */
```

### Special comment syntax

Xcode recognizes special comment syntax and can display these comments in a file's quick-jump dropdown bar.

#### MARK

`MARK` can be used to display a comment in the bar:

```swift
// MARK: View Set Up
```

A dash (-) can be added to display a line above the comment:

```swift
// MARK: - View Set Up
```

A bar without a comment can be added with a simple dash:

```swift
// MARK: -
```

#### TODO

`TODO` is used to display a reminder of something that needs to be done:

```swift
// TODO: Update logic to accommodate data changes.
```

#### FIXME

`FIXME` is used to display a reminder of something that needs to be fixed:

```swift
// FIXME: Fix glitchy behavior when making changes to an existing entry.
```