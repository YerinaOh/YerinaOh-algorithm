---
layout: post
title:  "Smooth Array"
date:   2021-05-22T00:25:52-05:00
author: Yerina Oh
categories: Algorithm
tags:	Algorithm
cover:  "/assets/09.png"
---

## URL
코테코테 사이트들에서 줍줍

### 주요내용: 
계수에 따른 어레이 평균률 구하기

### Rule:


### Example


```swift
var array: [Double] = [10.0, 13.0, 7.0, 11.0, 12.0, 9.0, 6.0, 5.0]

func smooth(values: [Double], alpha: Double) -> [Double] {
    print(average(array: values))
    let t_avg = average(array: values) * alpha
    var ret = values

    (0..<values.count).forEach { i in
        var prev = i>0 ? ret[i-1] : values[i]
        var next = i<values.count ? values[i] : values[i-1]
        ret[i] = average(array: [t_avg, average(array: [prev, values[i], next])])
    }
    return ret
}
```