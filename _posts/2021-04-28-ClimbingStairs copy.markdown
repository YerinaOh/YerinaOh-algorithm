---
layout: post
title:  ClimbingStairs
date:   2021-04-28 23:26:12 +0300
categories: Algorithm
cover:  "/assets/09.jpg"
tags:   Algorithm
---

## URL
https://leetcode.com/problems/climbing-stairs/

### 주요내용: 
DP 문제풀기

### Rule:
계단을 오르고 있습니다. 정상에 도달하려면 n 단계가 필요합니다.
매번 1 단계 또는 2 단계를 오를 수 있습니다. 얼마나 많은 방법으로 정상에 올라갈 수 있는지 구하시오

### Constraints:
1 <= n <= 45

### time complexity
O(n)
dp[i] = dp[i - 1] + dp[i - 2]

### Example
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
