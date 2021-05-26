---
layout: post
title:  "boxandfiles"
date:   2021-05-25T00:25:52-05:00
author: Yerina Oh
categories: Algorithm
tags:	Algorithm
cover:  "/assets/02.png"
---

## URL
코테사이트에서 줍줍 

### 주요내용: 
풀로 담아서 옮기는 박스의 갯수와 나머지의 개수를 더한 값을 return
그리디알고리즘으로 풀면 쉽다.

### Rule:

### Example


```swift
var finalCount = 0

func boxandfiles(boxes: Int, pieces: Int, minimum: Int) -> Int {

    if boxes <= minimum {
        return boxes
    }

    let mot = boxes / pieces
    var namo = boxes % pieces
    var files: [Int] = []

    for i in 0..<pieces {
        if i == 0, namo > 0 {
            files.append(mot + 1)
            namo -= 1
        } else {
            files.append(mot) // 6, 5
        }
    }
    for item in files {

        if item > minimum {
            boxandfiles(boxes: item, pieces: pieces, minimum: minimum)
        } else {
            finalCount += 1
        }
    }
    return finalCount
}

var dp: [Int] = []
dp.append(boxandfiles(boxes: 3, pieces: 2, minimum: 5))
print(dp.last!)
```