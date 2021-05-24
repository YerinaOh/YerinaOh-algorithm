---
layout: post
title:  "Vowel Reverse"
date:   2021-05-24T00:25:52-05:00
author: Yerina Oh
categories: Algorithm
tags:	Algorithm
cover:  "/assets/01.png"
---

## URL
https://www.geeksforgeeks.org/reverse-vowels-given-string/

### 주요내용: 
텍스트 내 모음만 순서바꾸기

### Rule:


### Example


```swift
func isVowel(str: String) -> Bool {
    switch str {
    case "a", "A", "e", "E", "i", "I", "o", "O", "u", "U":
        return true
    default:
        return false
    }
}
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