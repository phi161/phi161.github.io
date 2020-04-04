---
layout: post
author: phi161
title:  "Closures"
date:   2016-09-12 21:33:00 +0300
categories: learning
---

# Notes

## Capture Lists

* *The lesson [here](https://www.objc.io/blog/2018/04/03/caputure-lists/) is to consider carefully what you actually need to capture in your closure. Do you really need a reference to self? Or do you just need a reference to an object on self? If you can capture something more specific, you can often avoid dealing with weak or unowned references.*
* [This code](https://www.raywenderlich.com/762435-swift-interview-questions-and-answers):

```
var thing = "cars"

let closure = { [thing] in
  print("I love \(thing)")
}

thing = "airplanes"

closure()
```
will print `I love cars`: *The capture list creates a copy of `thing` when you declare the closure. This means that captured value doesn't change even if you assign a new value to `thing`*.

See also [Can You Answer This Simple Swift Question Correctly?](https://medium.com/swlh/can-you-answer-this-simple-swift-question-correctly-3d2836cff7b1) and [Capture Lists](https://www.objc.io/blog/2018/04/03/caputure-lists/)

# Links

* **2019.06** [You don’t (always) need `[weak self]`](https://medium.com/flawless-app-stories/you-dont-always-need-weak-self-a778bec505ef)
* **2018.09** [Capturing Self with Swift 4.2](https://benscheirman.com/2018/09/capturing-self-with-swift-4-2/)
* **2017.11** Explains `@escaping` very well: [CocoaCasts](https://cocoacasts.com/what-do-escaping-and-noescaping-mean-in-swift-3/)  
(summary: `@noescape` is the default in swift3 [for performance and for safely using `self`], `@noescaping` means that the closure can run after the func returns)
* **2017.09** [Why Coroutines](http://www.figure.ink/blog/2017/9/4/expressive-coroutines)
* **2017.05** [Why Do We Need to Annotate Escaping Closures in Swift?](https://www.andrewcbancroft.com/2017/05/11/why-do-we-need-to-annotate-escaping-closures-in-swift/)
* **2017.04** [Introduction to Closures in Swift 4](https://medium.com/ios-os-x-development/introduction-to-closures-in-swift-3-1d46dfaf8a20#.d8wyvl8cr)
* **2017.01** [Understanding memory leaks in closures](https://medium.com/compileswift/understanding-memory-leaks-in-closures-48207214cba#.8ia4ezx6g)
* **2016.10** [Optional Non-Escaping Closures](https://oleb.net/blog/2016/10/optional-non-escaping-closures/)
