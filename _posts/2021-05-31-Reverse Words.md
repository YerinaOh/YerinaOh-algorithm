---
layout: post
title:  "Reverse Words"
date:   2021-05-31T00:25:52-05:00
author: Yerina Oh
categories: Algorithm
tags:	Algorithm
cover:  "/assets/05.png"
---

## URL
코테사이트에서 줍줍 

### 주요내용: 
단어 뒤집기
(사실 오늘은 좀 귀찮네여 ㅠㅠㅠㅠ)

### Rule:

### Example


```swift
/* Reverse Words */
let str = "hello world"
let result = str.components(separatedBy: " ").reversed().map { String($0.reversed()) }.joined()
print(result)
```