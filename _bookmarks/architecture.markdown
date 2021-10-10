---
layout: bookmark
author: phi161
title: "Architecture"
categories: learning
---

## Links

* **2020.05** [Understanding Creational Design Patterns](https://lickability.com/blog/understanding-creational-design-patterns/)
* **2020.04** [RIBs](https://github.com/uber/RIBs/wiki) is Uber’s cross-platform architecture framework. This framework is designed for large mobile applications that contain many nested states.
* **2020.04** [Design Patterns implemented in Swift 5.0](https://github.com/ochococo/Design-Patterns-In-Swift)
* **2017.11** [View-state driven applications](https://www.cocoawithlove.com/blog/view-state-driven-applications.html)
* **2017.10** [iOS Architecture: A State Container based approach](https://jobandtalent.engineering/ios-architecture-an-state-container-based-approach-4f1a9b00b82e) (2 parts)
* **2017.09** [Highly maintainable app architecture](http://aplus.rs/2017/highly-maintainable-app-architecture/)
* **2017.09** [Managing different environments in your Swift project with ease](https://medium.com/flawless-app-stories/manage-different-environments-in-your-swift-project-with-ease-659f7f3fb1a6)
* **2017.08** [Design Patterns on iOS using Swift](https://www.raywenderlich.com/160653/design-patterns-ios-using-swift-part-22)
* **2017.03** [IB Free in Practice 1: Managing a Modal](https://www.raizlabs.com/dev/2017/03/ibfree-practice-1-managing-modal/)
* **2016.06** [SOLID Principles in Swift](https://www.youtube.com/watch?v=gkxmeWvGEpU)
* **2015.11** [iOS Architecture Patterns](https://medium.com/ios-os-x-development/ios-architecture-patterns-ecba4c38de52#.qoafphl7f) _Demystifying MVC, MVP, MVVM and VIPER_


# Sample Code

* **2020.10** ⭐️ [iOS-Clean-Architecture-MVVM](https://github.com/kudoleh/iOS-Clean-Architecture-MVVM)
* **2020.05** [CleanArchitectureRxSwift](https://github.com/sergdort/CleanArchitectureRxSwift)


# Refactoring

* **2018.08** [Refactoring Massive App Delegate](https://www.vadimbulavin.com/refactoring-massive-app-delegate/) using 3 different patterns: _Command_, _Composite_ and _Mediator_
* **2017.10** [Avoiding singletons in Swift](https://www.swiftbysundell.com/posts/avoiding-singletons-in-swift)
* **2017.08** [Replacing legacy code using Swift protocols](https://www.swiftbysundell.com/posts/replacing-legacy-code-using-swift-protocols)
* **2017.03** [The Recipe for Singletons Removal](https://albertodebortoli.com/2017/03/15/the-recipe-for-singletons-removal/)

### Lighter view controllers

* [Protocol-oriented, type-safe data source objects that keep your view controllers light](https://github.com/jessesquires/JSQDataSourcesKit) (with [video](https://www.skilled.io/u/swiftsummit/pushing-the-limits-of-protocol-oriented-programming))
* [Avoiding Massive View Controllers by refactoring](https://medium.com/cocoaacademymag/avoiding-massive-view-controllers-by-refactoring-ffb6a55dfa42)

### Dependency Injection

* **2021.07** [Resolver for iOS Dependency Injection: Getting Started](https://www.raywenderlich.com/22203552-resolver-for-ios-dependency-injection-getting-started)
* **2020.04** [Dependency Injection via Property Wrappers](https://www.kiloloco.com/articles/004-dependency-injection-via-property-wrappers/)
* **2019.12** [Practical Dependency Inversion in Swift](https://medium.com/flawless-app-stories/practical-dependency-inversion-in-swift-1c1142161a8)
* **2019.07** [Better Storyboards with Xcode 11](https://useyourloaf.com/blog/better-storyboards-with-xcode-11/) explains how to use `@IBSegueAction` to support DI using Storyboards
* **2018.11** [Dependency Injection on iOS](https://medium.com/@fernandodelrio/dependency-injection-on-ios-part-1-4-8847f302b3d9) (4 parts)
* **2016.11** [SwinjectMVVMExample](https://github.com/Swinject/SwinjectMVVMExample) 
An example to use Swinject in MVVM architecture with ReactiveCococa
* **2015.11** [Dependency Injection Framework for Swift - Introduction to Swinject](https://yoichitgy.github.io/post/dependency-injection-framework-for-swift-introduction-to-swinject/). Very nice intro to DI.

### Modular Design

* **2020.07** [Modern Modular Apps With Xcode 12 and Swift Package Manager](https://medium.com/kinandcartacreated/modern-modular-apps-with-xcode-12-and-swift-package-manager-a84aedace575) (and also [Modern modular apps with Xcode 11 and Swift Package Manager](https://medium.com/kinandcartacreated/modern-modular-apps-with-xcode-11-and-swift-package-manager-6b4afa0125be))
* **2019.12** [Modular iOS Architecture @ Just Eat](https://tech.just-eat.com/2019/12/18/modular-ios-architecture-just-eat/)
* **2019.12** [Breaking an app up into modules](https://www.donnywals.com/breaking-an-app-up-into-modules/)
* **2019.08** [Modular Architecture in iOS](https://medium.com/flawless-app-stories/a-modular-architecture-in-swift-aafd9026aa99) Interesting aproach of using CocoaPods for maintaining internal and external modules
* **2018.05** Modular iOS. [Part 1: Strangling the Monolith](https://medium.com/kinandcartacreated/modular-ios-strangling-the-monolith-4a6843a28992), [Part 2: Splitting A Workspace into Modules](https://medium.com/kinandcartacreated/modular-ios-splitting-a-workspace-into-modules-331293f1090), [Part 3: Configuration & Testing of Modules](https://medium.com/kinandcartacreated/modular-ios-part-3-configuration-testing-of-modules-2f287b19eeef), [Part 4: Sharing Configuration Between Modules](https://medium.com/kinandcartacreated/modular-ios-part-4-sharing-configuration-between-modules-b08a31490447)


# MVC

Apple's MVC is not the same with _traditional_ MVC, the main difference being that Apple does __not__ allow the direct connection between view and model (this is assigned to the controller instead, which acts as the mediator). Whenever a cell updates itself using a model reference, the MVC pattern breaks (since this communication should have been done by the controller).

* **2019.04** [Model-View-Controller (MVC) in iOS: A Modern Approach](https://www.raywenderlich.com/132662/mvc-in-ios-a-modern-approach)
* **2017.11** [A Better MVC](https://davedelong.com/blog/2017/11/06/a-better-mvc-part-1-the-problems/) (5 parts)
* **2017.10** [The worst possible application](https://www.cocoawithlove.com/blog/worst-possible-application.html)
* **2017.05** [#41 Architecture Wars – MVC strikes back & takes a photo with AVFoundation](https://swifting.io/blog/2017/05/06/41-architecture-wars-mvc-strikes-back-takes-a-photo-with-avfoundation/)
* **2017.02** [Looking at Model-View-Controller in Cocoa](https://www.cocoawithlove.com/blog/mvc-and-cocoa.html)


# MVVM

* **2020.04** [Modern MVVM iOS App Architecture with Combine and SwiftUI](https://www.vadimbulavin.com/modern-mvvm-ios-app-architecture-with-combine-and-swiftui/)
* **2019.09** [Learn RxSwift From This Production App](https://andreaslydemann.com/learn-rxswift-from-this-production-app/)
* **2019.08** [Simplifying RxSwift code](https://medium.com/flawless-app-stories/simplifying-rxswift-code-78071d5b780): some different approaches of creating VMs, refers to ReactorKit in the end.
* **2019.05** [RxSwift and Production-Level Code](https://betterprogramming.pub/rxswift-github-search-done-right-d57aa042f97f) Takes GitHub Search from the RxSwift repository and refactors with a number of interesting techniques
* **2019.02** [Modeling Your View Models as Functions](https://medium.com/grailed-engineering/modeling-your-view-models-as-functions-65b58525717f) - also check related videos from [Stephen Celis](https://www.youtube.com/watch?v=uTLG_LgjWGA) and [Danny Hertz](https://www.youtube.com/watch?v=9UqDk33pkKA).
* **2019.02** ⭐️ [Anatomy of an RxSwift View Model](https://medium.com/@chuck.krutsinger/anatomy-of-an-rxswift-view-model-cd45d35a710) (read the comments!)
* **2018.11** [Danny Hertz - From Sketch to Xcode: Building Functional Reactive View Models from the Ground Up](https://www.youtube.com/watch?v=9UqDk33pkKA) 30' video, taken from [Modeling Your View Models as Functions](https://medium.com/grailed-engineering/modeling-your-view-models-as-functions-65b58525717f). Comes with a [gist](https://gist.github.com/dannyhertz/9eb4247e784e0c3b2ff8ec60098630a2) and [example project](https://github.com/pablobarcos/RxSwiftReactiveViewModel).
* **2017.09** ⭐️ [RxSwift + MVVM: how to feed ViewModels](https://medium.com/blablacar/rxswift-mvvm-66827b8b3f10) Converting ViewModel inputs to outputs, with and without Subjects. Refers to the problem of having cells where the view is lazy loaded, thus not ready for the view model.
* **2017.06** [Taming Great Complexity: MVVM, Coordinators and RxSwift](https://blog.uptech.team/taming-great-complexity-mvvm-coordinators-and-rxswift-8daf8a76e7fd)


# VIPER

* **2020.04** [Getting Started with the VIPER Architecture Pattern](https://www.raywenderlich.com/8440907-getting-started-with-the-viper-architecture-pattern)
* **2019.11** [VIPER, RxSwift-ified](https://medium.com/@danielt1263/viper-rxswift-ified-1ec3ae8ab9a6)


# Coordinators / Routing

* **2021.09** [RxMyCoordinator](https://github.com/danielt1263/RxMyCoordinator) by  Daniel Tartaglia
* **2020.04** [Coordinator pattern in iOS 13 world](https://aplus.rs/2020/coordinator-pattern-for-ios13/)
* **2020.03** [The Navigator - Another twist to iOS navigations](https://jobandtalent.engineering/the-navigator-420b24fc57da)
* **2020.02** [XCoordinator](https://github.com/quickbirdstudios/XCoordinator) on GitHub and [accompanying article](https://quickbirdstudios.com/blog/ios-navigation-library-based-on-the-coordinator-pattern/)
* **2020.01** [Using Type Erasure to Build a Dependency Injecting Routing Framework in Swift](https://swiftrocks.com/using-type-erasure-to-build-a-dependency-injector-in-swift.html)
* **2019.12** [Routing for iOS: universal navigation without rewriting the app](https://badootech.badoo.com/routing-for-ios-universal-navigation-without-rewriting-the-app-215b52a37cf2)
* **2019.06** [How to implement Coordinator pattern with RxSwift](https://benoitpasquier.com/integrate-coordinator-pattern-in-rxswift/)
* **2019.03** [Navigation Problem](http://kean.github.io/post/navigation-problem) and [Controller Hierarchies](https://sandofsky.com/blog/controller-hierarchies.html) challenge the need for coordinators, describing other "pure" UIKit alternatives.
* **2019.02** [Advanced coordinators in iOS](https://www.hackingwithswift.com/articles/175/advanced-coordinator-pattern-tutorial-ios)
* **2018.04** [The C in MVVM-C.](https://medium.com/@myurieff/the-c-in-mvvm-c-2b18ff26e195)
* **2017.05** [MVC-C · Injecting Coordinator pattern in UIKit](http://aplus.rs/2017/mvc-c-injecting-coordinator-pattern-in-uikit/). Uses the `UIResponder` chain and associated objects to achieve communication among coordinators. [Another article](http://aplus.rs/2018/coordinator-missing-pattern-uikit/) from the same author.
* **2017.01** Coordinators Essential tutorial: [part I](https://medium.com/blacklane-engineering/coordinators-essential-tutorial-part-i-376c836e9ba7) & [part II](https://medium.com/@panovdev/coordinators-essential-tutorial-part-ii-b5ab3eb4a74). Lengthy and more advanced, comes with [example project](https://github.com/AndreyPanov/ApplicationCoordinator)
* **2016.12** [An iOS Coordinator Pattern](https://will.townsend.io/2016/an-ios-coordinator-pattern). Uses a (not very nice) `Services` struct and comes with [Github example](https://github.com/wtsnz/Coordinator-Example)
* **2016.07** [The Coordinator Pattern](https://www.iamsim.me/the-coordinator-pattern/). Simple implementation with an [example gist](https://gist.github.com/simme/ea0918d534f13ace3445e84ec043ed99). Good starting point.
* **2016.02** [Swift - Coordinators](http://skyefreeman.io/programming/2016/02/23/playing_with_app_coordinators.html). Starts even before setting the window's `rootViewController`
* **2016.01** [Navigation coordinators](http://irace.me/navigation-coordinators) _Here’s the problem: while this works great so long as the user keeps moving forward through our onboarding flow, what would happen if they tapped the navigation controller’s back button?_ (more links about "back" in [this issue](https://github.com/ReSwift/ReSwift-Router/issues/17)).
* **2015.10** [Coordinators Redux](http://khanlou.com/2015/10/coordinators-redux/)
