---
layout: post
title:  FindPeakElement
date:   2021-03-28 23:19:35
categories: Algorithm
cover:  "/assets/04.jpg"
tags:   Algorithm
---


## DP
https://leetcode.com/problems/find-peak-element/


### 주요내용: 
DP 로 문제풀기

### Rule:
정수 배열 nums가 주어지면 Pick 요소를 찾고 인덱스를 반환합니다. 배열에 여러 개의 Pick이있는 경우 인덱스를 Pick에 반환합니다.

### Constraints:
1 <= nums.length <= 1000
-231 <= nums[i] <= 231 - 1
nums[i] != nums[i + 1] for all valid i.

### time complexity
O(logn)

Example 1:
Input: nums = [1,2,3,1]
Output: 2
Explanation: 3 is a peak element and your function should return the index number 2.

Example 2:
Input: nums = [1,2,1,3,5,6,4]
Output: 5
Explanation: Your function can return either index number 1 where the peak element is 2, or index number 5 where the peak element is 6.

```swift
class FindPeakElement {
    func findPeakElement(_ nums: [Int]) -> Int {
        var left = 0, right = nums.count - 1, mid = 0
        
        while left < right {
            mid = (right - left) / 2 + left
            
            if nums[mid] > nums[mid + 1] {
                right = mid
            } else {
                left = mid + 1
            }
        }
        return left
    }
}
```
