---
layout:      post
author:      phi161
title:       "Debugging [bookmarks]"
date:        2019-03-23
categories:  [dev]
tags:
  - bookmarks
  - ios
  - debugging
---

# Debugging

* **2019.08** [Advanced lldb tricks for Swift - Injecting and changing code on the fly](https://swiftrocks.com/using-lldb-manually-xcode-console-tricks.html)
* **2019.04** [iOS Debugging Tips & Tricks](https://www.netguru.com/codestories/ios-debugging-tips-tricks) Provides examples of **watchpoints** and **symbolic** breakpoints
* **2019.01** 👍 [Debugging iOS network traffic](https://blog.kulman.sk/debugging-ios-network-traffic/) using [mitmproxy](https://mitmproxy.org/) (for apps that do not use certificate pinning)
* **2018.10** [Xcode and LLDB Advanced Debugging Tutorial: Part 2](https://medium.com/@fadiderias/xcode-and-lldb-advanced-debugging-tutorial-part-2-8bfeae4cdfdb) Watchpoints & Symbolic breakpoints briefly explained
* **2017.12** [UIDebuggingInformationOverlay](http://ryanipete.com/blog/ios/swift/objective-c/uidebugginginformationoverlay/) is a private UIWindow subclass created by Apple, presumably to help developers and designers debug Apple’s own iOS apps.
* **2017.09** [Debugging Swift code with LLDB](https://medium.com/flawless-app-stories/debugging-swift-code-with-lldb-b30c5cf2fd49)
* **2017.08** [Useful Xcode breakpoint](https://twitter.com/0xced/status/900692839557992449): When you dismiss a controller and you don’t hear the pop sound (or see the log), you probably have a retain cycle.
* **2017.06** [DeallocationChecker](https://github.com/fastred/DeallocationChecker) Tool by [Arek Holko](https://holko.pl/)
* **2017.06** [Catching Leaky View Controllers Without Instruments](http://holko.pl/2017/06/26/checking-uiviewcontroller-deallocation/)
* **2017.03** [System Level Breakpoints in Swift](http://indiestack.com/2017/03/system-level-breakpoints-in-swift/)
* **2016.08** [Easy Optimization Wins](https://samhuri.net/posts/2016/08/easy-optimization-wins)
* **2011.01** [How debuggers work](https://eli.thegreenplace.net/tag/debuggers) (three parts, not iOS specific)

# Logging

* **2019.04** [Migrating to Unified Logging: Console and Instruments](https://www.raywenderlich.com/605079-migrating-to-unified-logging-console-and-instruments)
* **2018.09** [Migrating to Unified Logging, Swift Edition](https://www.bignerdranch.com/blog/migrating-to-unified-logging-swift-edition/)
* [XCGLogger](https://github.com/DaveWoodCom/XCGLogger) allows you to log details to the console (and optionally a file, or other custom destinations), just like you would have with NSLog() or print(), but with additional information, such as the date, function name, filename and line number.
* [NSLogger](https://github.com/fpillet/NSLogger) is a high performance logging utility which displays traces emitted by client applications running on macOS, iOS and Android. It replaces traditional console logging traces (NSLog(), Java Log).
