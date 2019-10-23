---
layout: default
title: "Collection types comparison"
description: 
redirect_from: 
  - /collection/
  - /collection-types/
---
{::options parse_block_html="true" /}

* TOC
{:toc}

### Basic example

| **[Arrays](/arrays)** | `let numbers = [1, 2, 3, 4]` |
| **[Sets](/sets)** | `let numbers: Set = [1, 2, 3, 4]` |
| **[Dictionaries](/dictionaries)** | `let points = ["Ava": 150, "Eve": 275, "Kim": 115]` |

### Example with explicit type annotation

| **Arrays** | `let numbers: [Int] = [1, 2, 3, 4]` |
| **Set** | `let numbers: Set<Int> = [1, 2, 3, 4]` |
| **Dictionaries** | `let points: [String: Int] = ["Ava": 150, "Eve": 275, "Kim": 115]` |

### Empty example

| **Arrays** | `let numbers: [Int] = []` or `let numbers = [Int]()` |
| **Set** | `let numbers: Set<Int> = []` or `let numbers = Set<Int>()` |
| **Dictionaries** | `let points: [String: Int] = []` or `let points = [String: Int]()` |

### Order

| **Arrays** | Arrays are ordered, each element has its own index. |
| **Set** | Sets are unordered. |
| **Dictionaries** | Dictionaries are unordered. |

### Unique values?

| **Arrays** | Can have repeating values. |
| **Set** | May not have repeating values. Each value is unique. |
| **Dictionaries** | Keys are unique but values can be repeating. |
