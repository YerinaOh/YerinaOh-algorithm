---
layout: post
title:  "Sentences"
date:   2021-05-16T00:25:52-05:00
author: Yerina Oh
categories: Algorithm
tags:	Algorithm
cover:  "/assets/07.png"
---

## URL
코테코테 사이트들에서 줍줍

### 주요내용: 
sentences 를 가지고 노는 문제들을 가져와보았다.

### Rule:
- reverse sentences
- reverseVowel

### Example


```swift
var linesCnt = Int(readLine()!) ?? 0
var resultList: [String] = []

(0..<linesCnt).forEach { _ in
    let sentence = readLine() ?? ""
    let reversed = sentence.split(separator: " ").reversed()
    let joined = reversed.joined(separator: " ")
    print(joined)
}
```
```swift
func reverseVowel(text: String) {
    var strArr = text.map { String($0) }
    var vowelArr: [String] = []

    for i in strArr {
        if isVowel(str: i) {
            vowelArr.append(i)
        }
    }

    var idx: Int = 0
    for i in strArr {
        if isVowel(str: i), vowelArr.count > 0, let last = vowelArr.popLast() {
            strArr[idx] = last
        }
        idx += 1
    }
    print(strArr.joined())
}

reverseVowel(text: "hello world")
```