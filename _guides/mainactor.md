---
layout: default
title: "@MainActor"
description: A Swift 5.6 @MainActor reference guide, covering declaring async functions, calling them with await, performing parallel work, using async/await with URLSession, and more.
redirect_from:
  - /main-actor/
---
{::options parse_block_html="true" /}

**@MainActor** is a keyword that is used to ensure a function or class only runs on the main thread. This can be used to ensure that UI updates are only done on the main thread, and not on a background thread.

* TOC
{:toc}

