---
layout: post
title:  "isAlphaNumeric"
date:   2021-06-06T00:25:52-05:00
author: Yerina Oh
categories: Algorithm
tags:	Algorithm
cover:  "/assets/07.png"
---

## URL
코테사이트에서 줍줍 

### 주요내용: 

### Rule:

### Example


```swift
func isAlphaNumeric(item: String) -> Bool {
    let set = CharacterSet(charactersIn: "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLKMNOPQRSTUVWXYZ0123456789 ")
    if item.rangeOfCharacter(from: set.inverted) != nil {
        print("false - \(item)")
        return false
    }
    return true
}

let userInput = "%1http://h.ka.o"//"http://page.kakao.com /store?12314"
var list = userInput.map { String($0) }
var filtered = list
var idx = 0

for i in list {
    if !isAlphaNumeric(item: i) {
        if idx > 1, filtered[idx - 1] == " " || filtered[idx - 1] == "" { //이전에도 공백으로 처리됐으면
            filtered[idx] = ""
        } else {
            filtered[idx] = " "
        }
    }
    idx += 1
}
filtered.filter { $0 != "" }

//var filtered = list.filter { isAlphaNumeric(item: $0) }
print(filtered.joined())

```