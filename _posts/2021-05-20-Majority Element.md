---
layout: post
title:  "Majority Element"
date:   2021-05-20T00:25:52-05:00
author: Yerina Oh
categories: Algorithm
tags:	Algorithm
cover:  "/assets/08.png"
---

## URL
코테코테 사이트들에서 줍줍

### 주요내용: 
가장 많은 element 를 리턴한다.

### Rule:


### Example


```swift
var linesCnt = Int(readLine()!) ?? 0
var sampleList = readLine()?.split(separator: " ")

func mostFrequent(array: [Int]) -> (value: Int, count: Int)? {
    var counts = [Int: Int]()
    array.forEach {
        print("before: \(counts)")
        counts[$0] = (counts[$0] ?? 0) + 1
    }

    if let (value, count) = counts.max(by: {$0.1 < $1.1}) {
        return (value, count)
    }
    return nil
}

if let result = mostFrequent(array: sampleList) {
    print("\(result.value) occurs \(result.count) times")
}
```