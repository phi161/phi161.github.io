---
layout: post
author: phi161
title:  "Architecture"
date:   2016-09-12 21:33:00 +0300
categories: learning
---

# Links

* [Design Patterns implemented in Swift 3.0](https://github.com/ochococo/Design-Patterns-In-Swift)
* [iOS Architecture Patterns](https://medium.com/ios-os-x-development/ios-architecture-patterns-ecba4c38de52#.qoafphl7f)
* [IB Free in Practice 1: Managing a Modal](https://www.raizlabs.com/dev/2017/03/ibfree-practice-1-managing-modal/)
* [Managing different environments in your Swift project with ease](https://medium.com/flawless-app-stories/manage-different-environments-in-your-swift-project-with-ease-659f7f3fb1a6)
* [Design Patterns on iOS using Swift](https://www.raywenderlich.com/160653/design-patterns-ios-using-swift-part-22)
* 📚 [Highly maintainable app architecture](http://aplus.rs/2017/highly-maintainable-app-architecture/)
* 📚 [View-state driven applications](https://www.cocoawithlove.com/blog/view-state-driven-applications.html)
* [Ending the debate: MVC vs MVP vs MVVM for iOS application development](https://www.simform.com/mvc-mvp-mvvm-ios-app-development/)


# Refactoring

* [Replacing legacy code using Swift protocols](https://www.swiftbysundell.com/posts/replacing-legacy-code-using-swift-protocols)
* [The Recipe for Singletons Removal](https://albertodebortoli.com/2017/03/15/the-recipe-for-singletons-removal/)
* [Avoiding singletons in Swift](https://www.swiftbysundell.com/posts/avoiding-singletons-in-swift)

### Lighter view controllers

* [Protocol-oriented, type-safe data source objects that keep your view controllers light](https://github.com/jessesquires/JSQDataSourcesKit) (with [video](https://www.skilled.io/u/swiftsummit/pushing-the-limits-of-protocol-oriented-programming))
* [Avoiding Massive View Controllers by refactoring](https://medium.com/cocoaacademymag/avoiding-massive-view-controllers-by-refactoring-ffb6a55dfa42)

### Dependency Injection

* **2019.12** [Practical Dependency Inversion in Swift](https://medium.com/flawless-app-stories/practical-dependency-inversion-in-swift-1c1142161a8)
* **2018.11** [Dependency Injection on iOS — part 1/4](https://medium.com/@fernandodelrio/dependency-injection-on-ios-part-1-4-8847f302b3d9)
* **2016.11** [SwinjectMVVMExample](https://github.com/Swinject/SwinjectMVVMExample) 
An example to use Swinject in MVVM architecture with ReactiveCococa
* **2015.11** [Dependency Injection Framework for Swift - Introduction to Swinject](https://yoichitgy.github.io/post/dependency-injection-framework-for-swift-introduction-to-swinject/). Very nice intro to DI.

### Modules

* **2019.12** [Modular iOS Architecture @ Just Eat](https://tech.just-eat.com/2019/12/18/modular-ios-architecture-just-eat/)
* **2019.12** [Breaking an app up into modules](https://www.donnywals.com/breaking-an-app-up-into-modules/)


# MVC

Apple's MVC is not the same with _traditional_ MVC, the main difference being that Apple does __not__ allow the direct connection between view and model (this is assigned to the controller instead, which acts as the mediator). Whenever a cell updates itself using a model reference, the MVC pattern breaks (since this communication should have been done by the controller).

* 📚 [The worst possible application](https://www.cocoawithlove.com/blog/worst-possible-application.html)
* [Looking at Model-View-Controller in Cocoa](https://www.cocoawithlove.com/blog/mvc-and-cocoa.html)
* [Model-View-Controller (MVC) in iOS: A Modern Approach](https://www.raywenderlich.com/132662/mvc-in-ios-a-modern-approach)
* [A Better MVC](https://davedelong.com/blog/2017/11/06/a-better-mvc-part-1-the-problems/) (5 parts)
* [#41 Architecture Wars – MVC strikes back & takes a photo with AVFoundation](https://swifting.io/blog/2017/05/06/41-architecture-wars-mvc-strikes-back-takes-a-photo-with-avfoundation/)
* 📚 [MVC.](http://codeplease.io/2017/11/19/mvc/)


# MVVM

* [Github tag: mvvm-architecture](https://github.com/topics/mvvm-architecture?l=swift)
* [Taming Great Complexity: MVVM, Coordinators and RxSwift](https://blog.uptech.team/taming-great-complexity-mvvm-coordinators-and-rxswift-8daf8a76e7fd)
* [MVVM with ReactiveCocoa 3, in Swift](http://www.martinrichter.net/blog/2015/08/12/mvvm-with-reactivecocoa-3-in-swift/). Series, one post is about passing data among views.


# Coordinators / Routing

* **2020.01** [Using Type Erasure to Build a Dependency Injecting Routing Framework in Swift](https://swiftrocks.com/using-type-erasure-to-build-a-dependency-injector-in-swift.html)
* **2019.12** [Routing for iOS: universal navigation without rewriting the app](https://badootech.badoo.com/routing-for-ios-universal-navigation-without-rewriting-the-app-215b52a37cf2)
* [XCoordinator](https://github.com/quickbirdstudios/XCoordinator) on GitHub
* [Advanced coordinators in iOS](https://www.hackingwithswift.com/articles/175/advanced-coordinator-pattern-tutorial-ios) covers the following:
    1. How and when do you use child coordinators?
    1. How do you handle moving back from a navigation controller?
    1. How do you pass data between view controllers?
    1. How do you use tab bar controllers with coordinators?
    1. How do you handle segues?
    1. How do you use protocols or closures instead?
* [Navigation Problem](http://kean.github.io/post/navigation-problem) and [Controller Hierarchies](https://sandofsky.com/blog/controller-hierarchies.html) challenge the need for coordinators, describing other "pure" UIKit alternatives.
* [Coordinators Redux](http://khanlou.com/2015/10/coordinators-redux/)
* [The Coordinator Pattern](https://www.iamsim.me/the-coordinator-pattern/)  
Simple implementation with an [example gist](https://gist.github.com/simme/ea0918d534f13ace3445e84ec043ed99). Good starting point.
* Coordinators Essential tutorial: [part I](https://medium.com/blacklane-engineering/coordinators-essential-tutorial-part-i-376c836e9ba7) & [part II](https://medium.com/@panovdev/coordinators-essential-tutorial-part-ii-b5ab3eb4a74)  
Lengthy and more advanced, comes with [example project](https://github.com/AndreyPanov/ApplicationCoordinator)
* [An iOS Coordinator Pattern](https://will.townsend.io/2016/an-ios-coordinator-pattern)  
Uses a (not very nice) `Services` struct and comes with [Github example](https://github.com/wtsnz/Coordinator-Example)
* [MVC-C · Injecting Coordinator pattern in UIKit](http://aplus.rs/2017/mvc-c-injecting-coordinator-pattern-in-uikit/)  
Uses the `UIResponder` chain and associated objects to achieve communication among coordinators. [Another article](http://aplus.rs/2018/coordinator-missing-pattern-uikit/) from the same author.
* [Swift - Coordinators](http://skyefreeman.io/programming/2016/02/23/playing_with_app_coordinators.html)  
Starts even before setting the window's `rootViewController`
* [Navigation coordinators](http://irace.me/navigation-coordinators) _Here’s the problem: while this works great so long as the user keeps moving forward through our onboarding flow, what would happen if they tapped the navigation controller’s back button?_ (more links about "back" in [this issue](https://github.com/ReSwift/ReSwift-Router/issues/17)).
* [The C in MVVM-C.](https://medium.com/@myurieff/the-c-in-mvvm-c-2b18ff26e195)
* [Coordinator Tutorial for iOS: Getting Started](https://www.raywenderlich.com/177538/coordinator-tutorial-ios-getting-started)
