---
title: Implicit Optional Initialization
ShowShareButtons: false
hideMeta: true
tags: ["Tips", "Swift"]
---

An optional var defaults to nil (`p1`), but not when its type is `Optional` (like `p3`)

```swift
struct Demo {
    var p1: String? // defaults to `nil`
    let p2: String? // compiler error
    var p3: Optional<String> // compiler error
    let p4: Optional<String> // compiler error
}
```

[Source](https://belkadan.com/blog/2021/09/Swift-Regret-Implicit-Optional-Initialization/)
