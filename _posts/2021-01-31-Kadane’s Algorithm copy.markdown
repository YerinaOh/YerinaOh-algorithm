---
layout: post
title:  Kadane’s Algorithm
date:   2021-01-31 20:28:35 +0300
image:  01.png
tags:   Algorithm
---


## DP
https://leetcode.com/problems/maximum-subarray/


### 주요내용: 
DP 로 문제풀기

### Rule:
정수 배열 nums가 주어지면 합계가 가장 큰 연속 하위 배열 (최소 하나의 숫자 포함)을 찾아 합계를 반환한다.
max([i], [i] + [i - 1])


### time complexity
O(N)


Example 1:

Input: nums = [-2,1,-3,4,-1,2,1,-5,4]
Output: 6
Explanation: [4,-1,2,1] has the largest sum = 6.

Example 2:

Input: nums = [1]
Output: 1

```swift
import UIKit

class MaximumSubarray {
    func maxSubArray(nums: [Int]) -> Int {
        var max_current = nums[0]
        var max_global = nums[0]
        
        for i in 1..<nums.count {
            max_current = max(max_current + nums[i], nums[i])
            max_global = max(max_current, max_global)
        }
        
        return max_global
    }
}
```
