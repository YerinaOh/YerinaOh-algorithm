---
layout: post
title:  "codingtest_prepare"
date:   2021-05-14T00:25:52-05:00
author: Yerina Oh
categories: Algorithm
tags:	Algorithm
cover:  "/assets/05.png"
---

## URL
https://www.hackerrank.com/challenges/sock-merchant/problem?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=warmup

### 주요내용: 
Array 문제풀기

### Rule:
A Fibonacci-like sequence is a sequence of integers a1, a2, ... for which an = an-1+an-2 for all n > 2. You are given the first two elements of the sequence a1 and a2, and the 1-based index n. Output the n-th element of the sequence.

The input data consists of a single line which contains integers a1, a2 and n separated by single spaces.

### Constraints:
0 < a1, a2, n <= 10.

### Example
input

1 2 3

output

3

```swift
let intArr = "1 2 3".split(separator: " ").map { Int($0)! }
let arr = intArr

let length: Int = arr[2]

func fibonacci(n: Int) {

    var num1 = arr[0]
    var num2 = arr[1]

    for _ in 0 ..< n {

        let num = num1 + num2
        num1 = num2
        num2 = num
    }

    print(num2)
}
```
