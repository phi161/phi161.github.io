---
layout: bookmark
author: phi161
title: "Networking"
categories: [dev]
tags:
  - bookmarks
  - ios
  - networking
---

* **2021.02** [URLSessionConfiguration Quick Guide](https://useyourloaf.com/blog/urlsessionconfiguration-quick-guide/) Interesting properties: `allowsCellularAccess`, `httpAdditionalHeaders` and `urlCache`.
* **2020.08** [Working with an Internet Connection on iOS with Swift: Best Practices](https://www.vadimbulavin.com/network-connectivity-on-ios-with-swift/) explains how to use **Adaptable Connectivity APIs**, [Low Data mode](https://support.apple.com/en-us/HT210596)
* **2020.06** [HTTP in Swift](https://davedelong.com/blog/2020/06/27/http-in-swift-part-1/) Building a Swift HTTP framework (18 parts)
* **2020.03** [Going Deep With Decodable](https://martiancraft.com/blog/2020/03/going-deep-with-decodable/) explains how to solve some edge cases while parsing a network response (The data I actually care about is nested inside the response, I want some decoding to be able to fail without bringing down the whole process, and without ending up with lots of optionals, My type is decodable, but the JSON keys for some fields are different depending on which API endpoint I’m calling, I need to know about decoded data item X, when I’m decoding data item Y)
* **2019.08** [Writing an Elegant and Extensible Network Stack in Swift](https://medium.com/device-blogs/writing-an-elegant-and-extensible-network-stack-in-swift-e2f5d9ab3ea9). Also has 2nd part: [Adding Advanced Features to your Network Stack in Swift](https://medium.com/device-blogs/adding-advanced-features-to-your-network-stack-in-swift-941ecfff8dc3)
* **2019.05** [Building Breather (Part 3)](https://medium.com/@alexandrosbaramilis/building-breather-part-3-managing-networking-with-rxmoya-and-handling-errors-with-rxswifts-c300648858b8) Managing networking with RxMoya and handling errors with RxSwift’s retry and materialize
* **2017.09** [A Simple Approach to Thread-Safe Networking in iOS Apps](https://robots.thoughtbot.com/a-simple-approach-to-thread-safe-networking-in-ios-apps)
* **2017.03** [Network Layers in Swift](https://medium.com/@danielemargutti/network-layers-in-swift-7fc5628ff789) Well written, nice use of protocols. Separates networking in _Building the request_, _Executing the request_, _Parsing the response_ and _Performing Operations_.
* **2017.02** [Isolating tasks in Swift, or how to create a testable networking layer](https://medium.com/ios-os-x-development/isolating-tasks-in-swift-or-how-to-create-a-testable-networking-layer-d0380e69f7e3) Uses RXSwift
* **2016.07** [How do I build a Network Layer](http://szulctomasz.com/how-do-I-build-a-network-layer/) Refers to `NSOperationQueue`s and Core Data. [Sample code](https://github.com/tomkowz/NetworkLayerExample).
* **2015.08** [Lightweight networking in Objective-C](http://ilya.puchka.me/networking-use-case/) Writen in "Swifty" Objective-C with protocols and extensions, very similar to Moya (without the enums). Created as a framework, also provides unit tests.

### Handling tokens / 401 errors

* **2019.09** [Handling 401 status w/ RxSwift & URLSession](https://stackoverflow.com/a/58126527/289501)
* **2019.12** [Lessons learned from handling JWT on mobile](https://tech.just-eat.com/2019/12/04/lessons-learned-from-handling-jwt-on-mobile/)
* **2018.09** [The easy way to refresh session token of Auth0 with RxSwift and Moya](https://datarockets.com/blog/refresh-token-moya-rxswift/)
