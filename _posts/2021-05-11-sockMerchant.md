---
layout: post
title:  "sockMerchant"
date:   2021-05-11T22:25:52-05:00
author: Yerina Oh
categories: Algorithm
tags:	Algorithm
cover:  "/assets/03.png"
---


## URL
https://www.hackerrank.com/challenges/sock-merchant/problem?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=warmup

### 주요내용: 
Sort 문제풀기

### Rule:
John은 옷가게에서 일합니다. 그는 판매를 위해 색상별로 짝을 지어야 할 양말 더미를 가지고 있습니다. 각 양말의 색상을 나타내는 정수 배열이 주어지면 일치하는 색상의 양말 쌍이 몇 쌍인지 결정하십시오.

### Constraints:
0 <= nums <= 100

### time complexity
O(nlogn)

### Example
Sample Input

9
10 20 20 10 10 30 50 10 20
Sample Output

3

```swift
func sockMerchant(n: Int, ar: [Int]) -> Int {
    let sortedArr = ar.sorted()
    let matching = 0

    return findFriend(arr: sortedArr, index: 0, mp: matching)
}

func findFriend(arr: [Int], index: Int, mp: Int) -> Int {
    guard arr.count > index + 1 else { return mp }
    print(arr)
    var array = arr
    var matchingPoint = mp
    var idx = index
    if arr[index] == arr[index + 1] {
        array.remove(at: index)
        array.remove(at: index)
        matchingPoint += 1
    } else {
        idx += 1
    }
    return findFriend(arr: array, index: idx, mp: matchingPoint)
}
```
