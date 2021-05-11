---
layout: post
title:  GaryCode
date:   2021-04-12 23:46:35 +0300
categories: Algorithm
cover:  "/assets/01.jpg"
tags:   Algorithm
---


## Array
https://leetcode.com/problems/gray-code/

### 주요내용: 
MATH로 문제풀기

### Rule:
회색 코드는 2 개의 연속 된 값이 1 비트에서만 다른 이진 숫자 시스템입니다.
코드의 총 비트 수를 나타내는 정수 n이 주어지면 모든 회색 코드 시퀀스를 반환합니다.
회색 코드 시퀀스는 0으로 시작해야합니다.

### Constraints:
1 <= n <= 16

### time complexity
O(n)

### Example
Example 1:
Input: n = 2
Output: [0,1,3,2]
Explanation:
00 - 0
01 - 1
11 - 3
10 - 2
[0,2,3,1] is also a valid gray code sequence.
00 - 0
10 - 2
11 - 3
01 - 1

Example 2:
Input: n = 1
Output: [0,1]

```swift
class GaryCode {
    func grayCode(_ n: Int) -> [Int] {
        var codes = [0]
        for i in 0..<n {
            codes += codes.reversed().map { $0 | 1 << i }
        }
        return codes
    }
}
```
