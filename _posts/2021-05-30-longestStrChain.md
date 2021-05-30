---
layout: post
title:  "longestStrChain"
date:   2021-05-30T00:25:52-05:00
author: Yerina Oh
categories: Algorithm
tags:	Algorithm
cover:  "/assets/04.png"
---

## URL
코테사이트에서 줍줍 

### 주요내용: 
가장 긴 끝말잇기 배열 리턴

### Rule:

### Example


```swift
var result = 1
func longestStrChain(list: [String]) -> Int {
    guard list.count > 0 else { return 0 }

    var memo = [String: Int]()
    var dict = [Int: [String]]()
    for word in list {
        dict[word.count] = dict[word.count, default: [String]()]
        dict[word.count]?.append(word)
        memo[word] = 1
    }
    let sortedWords = list.sorted(by: { $0.count < $1.count })

    for word in sortedWords {
        for i in 0..<word.count {
            var chars = Array(word)
            chars.remove(at: i)
            let last = String(chars)
            print(" last - \(last)")
            if let value = dict[last.count], value.contains(last) {

                memo[word] = max(memo[word]!, memo[last]! + 1)
                print(memo[word]!)
                result = max(memo[word]!, result)
            }
        }
    }
    return result
}

longestStrChain(list: ["a", "b", "ba", "bca", "bda", "bdca"])
```