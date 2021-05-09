---
layout: post
title:  Climbing Stairs
date:   2021-03-24 23:27:35
categories: Algorithm
cover:  "/assets/02.jpg"
tags:   Algorithm
---


## DP
https://leetcode.com/explore/featured/card/top-interview-questions-easy/97/dynamic-programming/569/


### 주요내용: 
DP 로 문제풀기

### Rule:
한번 혹은 두번의 걸음으로 정상에 도달할 가지의 수를 구하여라

### Constraints:
1 <= n <= 45

### time complexity
O(N)

Example 1:
Input: n = 2
Output: 2
Explanation: There are two ways to climb to the top.
1. 1 step + 1 step
2. 2 steps

Example 2:
Input: n = 3
Output: 3
Explanation: There are three ways to climb to the top.
1. 1 step + 1 step + 1 step
2. 1 step + 2 steps
3. 2 steps + 1 step

```swift
class ClimbingStairs {
    func climbStairs(_ n: Int) -> Int {
        if n < 0 {
            return 0
        }
        if n == 0 || n == 1 {
            return 1
        }
        
        var prev = 0, post = 1, total = 0
        
        for i in 1...n {
            total = prev + post
            
            prev = post
            post = total
        }
       
        return total
    }
}
```
