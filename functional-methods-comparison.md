---
layout: default
title: "Functional methods comparison"
description: 
redirect_from: 
  - /functional/
  - /functional-methods/
---
{::options parse_block_html="true" /}

| Method | Description |
|--------|-------------|
| [map](/map) | Returns an array that contains the results of mapping a given closure over the elements of a sequence. |
| [compactMap](/compactmap) | Just like [map](/map), except that `nil` results are filtered out. |
| [flatMap](/flatmap) | Just like [map](/map), but if the result is an array of arrays, the arrays are concatenated (flattened) into a single array. |
| [filter](/filter) | Returns an array containing only the elements of a sequence that satisfy a given predicate, in their original order. |
| [reduce](/reduce) | Returns the result of combining the elements of a sequence using a given closure. |
| [sorted](/sorted) | Returns the elements of a sequence sorted using a particular predicate. |
| [forEach](/foreach) | Calls a closure on each element in a sequence in the same order as a [for-in](/for-in) loop. Does not return anything. |