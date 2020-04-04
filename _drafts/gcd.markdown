---
layout: post
author: phi161
title:  "Grand Central Dispatch"
date:   2017-03-19 18:00:00
categories: learning
---

# GCD Queues

## Creating a queue

A dispatch queue is a lightweight object to which your application submits blocks for subsequent execution. Blocks submitted to it are invoked serially in FIFO order.

Use `dispatch_queue_create` in order to create concurrent or serial queues.

In Objective-C:

{% highlight objc %}
// Concurrent
dispatch_queue_t concurrentQueue = dispatch_queue_create("io.github.phi161.concurrent", DISPATCH_QUEUE_CONCURRENT);

// Serial
dispatch_queue_t serialQueue = dispatch_queue_create("io.github.phi161.serial", DISPATCH_QUEUE_SERIAL);
{% endhighlight %}

and in Swift 3:

{% highlight swift %}
let serialQueue = DispatchQueue(label: "io.github.phi161.serial", qos: .default) // serial is the default so no attributes need to be specified
let concurrentQueue = DispatchQueue(label: "io.github.phi161.concurrent", qos: .default, attributes: .concurrent)
{% endhighlight %}

Serial queues invoke submtted blocks in the same order they are added whereas concurrent queues can invoke them in parallel. It is important to note that [in both cases the blocks will be started in the same order they were added](http://stackoverflow.com/a/33623006/289501). 

It is also possible to ask for a system-defined global concurrent queue with the specified quality of service:

{% highlight objc %}
dispatch_queue_t globalQueue = dispatch_get_global_queue(DISPATCH_QUEUE_PRIORITY_DEFAULT, 0);
{% endhighlight %}

The first parameter defines the _quality of service_ for this queue and can take the following values (according to the comments on [queue.h](https://opensource.apple.com/source/libdispatch/libdispatch-187.5/dispatch/queue.h.auto.html)):

* `DISPATCH_QUEUE_PRIORITY_LOW`: the queue will be scheduled for execution after all default priority and high priority queues have been scheduled
* `DISPATCH_QUEUE_PRIORITY_DEFAULT`: the queue will be scheduled for execution after all high priority queues have been scheduled, but before any low priority queues have been scheduled
* `DISPATCH_QUEUE_PRIORITY_HIGH`: the queue will be scheduled for execution before any default priority or low priority queue.
* `DISPATCH_QUEUE_PRIORITY_BACKGROUND`: the queue will be scheduled for execution after all higher priority queues have been scheduled and the system will run items on this queue on a thread with background status as per setpriority(2) (i.e. disk I/O is throttled and the thread's scheduling priority is set to lowest value)

The second parameter is _reserved for future use_ and should be `0`.

The system automatically creates a special queue called the _main queue_. Work items enqueued to the main queue execute __serially__ on the __main thread__. The main queue can be accessed using the `main` type property. It is important to note that the [_main queue and the main thread are not the same thing, but have subtle differences_](https://github.com/ReactiveCocoa/ReactiveCocoa/issues/2635#issuecomment-170215083). That means [it is not safe](https://twitter.com/olebegemann/status/738656609824559104) to assume the application is on the __main queue__ if `NSThread.isMainThread()` is true. In other words, [any queue could use the main thread if the system decides to do so](blog.krzyzanowskim.com/2016/06/03/queues-are-not-bound-to-any-specific-thread). This can be demonstrated with [this playground](https://gist.github.com/kommen/524ca1ce72df1f5d0b96) and is explained well [here](http://blog.benjamin-encz.de/post/main-queue-vs-main-thread/).


## Dispatching

A task can be dispatched either synchornously or asynchronously, using `sync` and `async` respectively. The main difference is that using `async` will return immediatelly to the caller, whereas `sync` will wait until the task is finished. This, together with the concept of serial and concurrent queues can be confusing but this example demonstrates the different scenarios:

{% highlight swift %}
import Foundation

let serialQueue = DispatchQueue(label: "io.github.phi161.serial", qos: .default)
let concurrentQueue = DispatchQueue(label: "io.github.phi161.concurrent", qos: .default, attributes: .concurrent)

func testWithQueue(_ queue: DispatchQueue) {
    queue.sync {
        for i in 0...5 {
            print("A (\(i))")
        }
    }
    
    print("between A and B")
    
    queue.sync {
        for i in 0...5 {
            print("B (\(i))")
        }
    }
    
    queue.async {
        for i in 0...5 {
            print("C (\(i))")
        }
    }
    
    print("between C and D")
    
    queue.async {
        for i in 0...5 {
            print("D (\(i))")
        }
    }
}

testWithQueue(serialQueue)
/*
 Prints:
 
 A (0)
 A (1)
 A (2)
 A (3)
 A (4)
 A (5) // sync will wait until the for loop in A finishes
 between A and B
 B (0)
 B (1)
 B (2)
 B (3)
 B (4)
 B (5)
 C (0) // async will return immediately. sometimes this line might even appear after the next
 between C and D
 C (1)
 C (2)
 C (3)
 C (4)
 C (5)
 D (0)
 D (1)
 D (2)
 D (3)
 D (4)
 D (5)
*/

testWithQueue(concurrentQueue)
/*
 Prints:

A (0) // sync works similarly to the serial queue
A (1)
A (2)
A (3)
A (4)
A (5)
between A and B
B (0)
B (1)
B (2)
B (3)
B (4)
B (5)
C (0) // From here on, async with concurrent give these random results
between C and D
C (1)
D (0)
C (2)
C (3)
C (4)
C (5)
D (1)
D (2)
D (3)
D (4)
D (5)
*/
{% endhighlight %}

Another good explanation of using `sync` and `async` in a serial queue can be found [here](http://stackoverflow.com/a/19822753).


## TODO

- Threading
- GCD
- NSOperation
- Run Loops


## Links

* [Concurrency Programming Guide](https://developer.apple.com/library/content/documentation/General/Conceptual/ConcurrencyProgrammingGuide/Introduction/Introduction.html)
* [iOS Multithreading: Thread Safety in iOS Applications](http://sodecon.blogspot.gr/2012/08/ios-multithreading-thread-safety-in-ios.html)
* [Thread-Safe Class Design](https://www.objc.io/issues/2-concurrency/thread-safe-class-design/)
* [Comparative Asynchronous Programming](https://ashfurrow.com/blog/comparative-asynchronous-programming/)
* [Run, RunLoop, Run!](http://bou.io/RunRunLoopRun.html)
* [Friday Q&A 2015-02-06: Locks, Thread Safety, and Swift](https://www.mikeash.com/pyblog/friday-qa-2015-02-06-locks-thread-safety-and-swift.html)
* [iOS 10 Day by Day :: Day 2 :: Thread Sanitizer](https://www.shinobicontrols.com/blog/ios-10-day-by-day-day-2-thread-sanitizer)
* [Rob Pike - 'Concurrency Is Not Parallelism'](https://www.youtube.com/watch?v=cN_DpYBzKso)
* [The 10 Most Common Mistakes iOS Developers Don't Know They're Making](https://www.toptal.com/ios/top-ios-development-mistakes)
* [dispatch_sync vs. dispatch_async](http://developmentinswift.blogspot.gr/2016/01/dispatchsync-vs-dispatchasync.html)
* [Grand Central Dispatch Tutorial for Swift 3: Part 1/2](https://www.raywenderlich.com/148513/grand-central-dispatch-tutorial-swift-3-part-1)
* [A deep dive into Grand Central Dispatch in Swift](https://www.swiftbysundell.com/posts/a-deep-dive-into-grand-central-dispatch-in-swift)
