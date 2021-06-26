---
layout: post
title:  "Protocol extensions can provide default property values"
date:   2021-06-26T00:25:52-05:00
author: Yerina Oh
categories: Development
tags:	Development
cover:  "/assets/02.png"
---

## URL
https://www.hackingwithswift.com/articles/106/10-quick-swift-tips


### Rule:

2. Protocol extensions can provide default property values
Protocol extensions are a great way of providing default method implementations that can then be overridden as needed by conforming types, but you can also use them to provide default values for properties.

For example, we might create a Fadeable protocol that fades out views over a set number of seconds, like this:
```swift
protocol Fadeable {
    var fadeSpeed: TimeInterval { get }
    func fadeOut()
}

```
Rather than make all conforming types add their own fade speed and fadeOut() method, we can provide defaults for both inside a protocol extension:

```swift
extension Fadeable where Self: UIView {
    var fadeSpeed: TimeInterval {
        return 1.0
    }

    func fadeOut() {
        UIView.animate(withDuration: fadeSpeed) {
            self.alpha = 0
        }
    }
}

```
As a result, you can make new subclass conform to that without worrying about writing the same default value repeatedly:
```swift
class MyViewClass: UIView, Fadeable { }

```