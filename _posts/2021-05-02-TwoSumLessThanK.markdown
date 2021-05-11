---
layout: post
title:  TwoSumLessThanK
date:   2021-05-02 23:20:12 +0300
categories: Algorithm
cover:  "/assets/02.jpg"
tags:   Algorithm
---

## URL
https://leetcode.com/problems/two-sum-less-than-k/

### 주요내용: 
ARRAY 문제풀기

### Rule:
정수 배열 A와 정수 K가 주어지면 A [i] + A [j] = S 및 S <K 인 i <j가 존재하도록 최대 S를 반환합니다.

### time complexity
O(n)

### Example
Example 1:

Input: A = [34,23,1,24,75,33,54,8], K = 60
Output: 58
Explanation: 
We can use 34 and 24 to sum 58 which is less than 60.

Example 2:

Input: A = [10,20,30], K = 15
Output: -1
Explanation: 
In this case it's not possible to get a pair sum less that 15.

```swift

class TwoSumLessThanK {
    func twoSumLessThanK(_ A: [Int], _ K: Int) -> Int {
        let sortedA = A.sorted()
        var left = 0, right = sortedA.count - 1
        var closest = -1
        
        while left < right {
            if sortedA[left] + sortedA[right] < K {
                closest = max(sortedA[left] + sortedA[right], closest)
                left += 1
            } else {
                right -= 1
            }
        }
        
        return closest
    }
}
```
