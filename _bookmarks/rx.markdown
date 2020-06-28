---
layout: bookmark
author: phi161
title:  "Rx"
date:   2016-09-12 21:33:00 +0300
categories: learning
---

## ReactorKit

* When binding an action, it is possible to manipulate the source stream (that's usually RxCocoa), like [this example](https://github.com/ReactorKit/ReactorKit/blob/master/Examples/GitHubSearch/GitHubSearch/GitHubSearchViewController.swift#L40).
* Actions can have a [payload](https://github.com/ReactorKit/ReactorKit/blob/master/Examples/GitHubSearch/GitHubSearch/GitHubSearchViewReactor.swift#L15).

## Operators

### `flatMap` and `flatMapLatest`

```
    Observable<String>.from(["😍", "😎"]).flatMapLatest { (str) -> Observable<String> in
        return Observable<String>.from(["\(str)1️⃣", "\(str)2️⃣", "\(str)3️⃣"])
    }.debug("🔴").subscribe().disposed(by: disposeBag)
```

produces:

```
2019-04-14 11:31:38.056: 🔴 -> subscribed
2019-04-14 11:31:38.060: 🔴 -> Event next(😍1️⃣)
2019-04-14 11:31:38.060: 🔴 -> Event next(😎1️⃣)
2019-04-14 11:31:38.060: 🔴 -> Event next(😎2️⃣)
2019-04-14 11:31:38.061: 🔴 -> Event next(😎3️⃣)
2019-04-14 11:31:38.061: 🔴 -> Event completed
2019-04-14 11:31:38.061: 🔴 -> isDisposed
```

Changing `flatMapLatest` to `flatMap` will print all events for 😍:

```
2019-04-14 11:36:22.624: 🔴 -> subscribed
2019-04-14 11:36:22.627: 🔴 -> Event next(😍1️⃣)
2019-04-14 11:36:22.628: 🔴 -> Event next(😍2️⃣)
2019-04-14 11:36:22.628: 🔴 -> Event next(😎1️⃣)
2019-04-14 11:36:22.628: 🔴 -> Event next(😍3️⃣)
2019-04-14 11:36:22.629: 🔴 -> Event next(😎2️⃣)
2019-04-14 11:36:22.629: 🔴 -> Event next(😎3️⃣)
2019-04-14 11:36:22.629: 🔴 -> Event completed
2019-04-14 11:36:22.629: 🔴 -> isDisposed
```

See how 😎1️⃣ is emmitted asynchronously, before 😍3️⃣

### `takeUntil`

Returns the elements from the source observable sequence until the other observable sequence produces an element. Or, from [RxMarbles](http://reactivex.io/documentation/operators/takeuntil.html): discard any items emitted by an Observable after a second Observable emits an item or terminates. See [example](https://github.com/ReactorKit/ReactorKit/blob/master/Examples/GitHubSearch/GitHubSearch/GitHubSearchViewReactor.swift#L45).

### `withLatestFrom`

TODO


## Other notes

* ..the most obvious way to stop a completed event is `single.concat(Observable.never())` [source](https://stackoverflow.com/a/54121297/289501)

# Summary

## Subjects

Subjects act as **both an observable and an observer**. You saw earlier how they can receive events and also be subscribed to. The subject received `.next` events, and each time it received an event, it turned around and emitted it to its subscriber.

Actually, **every subject type, once terminated, will re-emit its stop event to future subscribers**. So it’s a good idea to include handlers for stop events in your code, not just to be notified when it terminates, but also in case it is already terminated when you subscribe to it.

Because it wraps a behavior subject, a ==Variable (BehaviorRelay)== is created with an initial value, and it will replay its latest or initial value to new subscribers. In order to access a variable’s underlying behavior subject, you call `asObservable()` on it. Also unique to Variable, as compared to other subjects, is that **it is guaranteed not to emit an error**.

You’d like to add a `PublishSubject` to expose the photos being selected. However, you don’t want to necessarily make the subject publicly accessible, as that would allow other classes to call `onNext(_)` and make the subject emit values. You sometimes might want to do that, but not in this case:

```
fileprivate let selectedPhotosSubject = PublishSubject<UIImage>()
var selectedPhotos: Observable<UIImage> {
  return selectedPhotosSubject.asObservable()
}
```


### Examples of usage

* You might use a **publish subject** when you’re modeling time-sensitive data, such as in an online bidding app. It wouldn’t make sense to alert the user who joined at 10:01 am that at 9:59 am there was only 1 minute left in the auction.
* **Behavior subjects** are useful when you want to pre-populate a view with the most recent data. For example, you could bind controls in a user profile screen to a behavior subject, so that the latest values can be used to pre-populate the display while the app fetches fresh data.
* For example, on a search screen, you may want to show the most recent five search terms used. This is where **replay subjects** come in.


# Links

* **2019.08** [Guarantee Rx memory leaks absence](https://medium.com/flawless-app-stories/guarantee-rx-memory-leaks-absence-3a90636ec49e)
* **2019.03** Integrating RxSwift Into Your Brain and Code Base ([part 1](https://medium.com/@danielt1263/integrating-rxswift-into-your-brain-and-code-base-1a790c36c36d), [part 2](https://medium.com/@danielt1263/integrating-rxswift-into-your-brain-and-code-base-part-2-a4f16de628bf)) Rx-ify a traditional project
* **2019.01** ⭐️ [RxSwift and Retrying a Network Request Despite Having an Invalid Token](https://medium.com/@danielt1263/retrying-a-network-request-despite-having-an-invalid-token-b8b89340d29) Explains the steps to create a JWT mechanism & test it
* **2018.09** [The easy way to refresh session token of Auth0 with RxSwift and Moya](https://datarockets.com/blog/refresh-token-moya-rxswift/)
* **2017.11** ⭐️⭐️ [RxSwift Deep Cuts](https://academy.realm.io/posts/krzysztof-siejkowski-mobilization-2017-rxswift-deep-cuts/) Goes deep into memory management, schedulers and the internals of `Observable`s (_video, 40'_)
* **2017.06** [Top mistakes in RxSwift you want to avoid](http://adamborek.com/top-7-rxswift-mistakes/)
* **2017.04** [Managing State with RxJava by Jake Wharton](https://www.youtube.com/watch?v=0IKHxjkgop4) (_video, 52'_)
* **2017.05** [UIKonf 2017 – Day 1 –Thomas Visser – Reactive Programming From Scratch](https://youtu.be/sEQiMCiMgpc)
* **2017.03** [Learn & Master ⚔️ the Basics of RxSwift in 10 Minutes](https://medium.com/ios-os-x-development/learn-and-master-%EF%B8%8F-the-basics-of-rxswift-in-10-minutes-818ea6e0a05b)
* **2016.12** ⭐️ [RxSwift Primer](https://www.caseyliss.com/2016/12/15/rxswift-primer-part-1) (3 parts) Goes from MVC to an Rx-based aproach, getting rid of local state
* **2016.11** [Thinking in RxSwift](http://adamborek.com/thinking-rxswift/)
* **2016.09** [The introduction to RxSwift you've been missing](https://github.com/orakaro/The-introduction-to-RxSwift-you-have-been-missing)


# Functional Programming

* 📺 [Point Free](https://www.pointfree.co/)
* **2019.02** [An Introduction to Functional Programming in Swift](https://www.raywenderlich.com/9222-an-introduction-to-functional-programming-in-swift)
* [The best FRP iOS resources](https://gist.github.com/JaviLorbada/4a7bd6129275ebefd5a6). Collection of many videos, articles etc
