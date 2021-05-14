---
layout: post
title:  "rotLeft"
date:   2021-05-12T00:25:52-05:00
author: Yerina Oh
categories: Algorithm
tags:	Algorithm
cover:  "/assets/04.png"
---

## URL
https://www.hackerrank.com/challenges/sock-merchant/problem?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=warmup

### 주요내용: 
Array 문제풀기

### Rule:
배열에 대한 왼쪽 회전 연산은 배열의 각 요소 단위를 왼쪽으로 이동합니다. 예를 들어, 왼쪽 회전이 array에서 수행되면 배열은. 가장 낮은 인덱스 항목은 회전에서 가장 높은 인덱스로 이동합니다. 이를 원형 배열이라고합니다.
정수 배열과 숫자가 주어지면 배열에서 왼쪽 회전을 수행합니다. 인쇄 할 업데이트 된 배열을 공백으로 구분 된 한 줄의 정수로 반환합니다.

### Constraints:
0 <= nums <= 100

### Example
Sample Input
5 4
1 2 3 4 5
Sample Output
5 1 2 3 4

```swift
func rotLeft(a: [Int], d: Int) -> [Int] {
    // Write your code here
    var rotatedArray = a
    for _ in 0..<d {
        if let first = rotatedArray.first {
            rotatedArray.remove(at: 0)
            rotatedArray.append(first)
        }
        print(rotatedArray)
    }
    return rotatedArray
}

rotLeft(a: [1,2,3,4,5], d: 4)
```
