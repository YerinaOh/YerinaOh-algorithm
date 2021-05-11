---
layout: post
title:  MergeSortedArray
date:   2021-04-06 22:34:25 +0300
categories: Algorithm
cover:  "/assets/10.jpg"
tags:   Algorithm
---


## Array
https://leetcode.com/problems/merge-sorted-array/

### 주요내용: 
ARRAY 로 문제풀기

### Rule:
두 개의 정렬 된 정수 배열 nums1 및 nums2가 주어지면 nums2를 하나의 정렬 된 배열로 nums1에 병합합니다.

### Constraints:
nums1.length == m + n
nums2.length == n
0 <= m, n <= 200
1 <= m + n <= 200
-109 <= nums1[i], nums2[i] <= 109

### time complexity
O(n)

### Example
Example 1:
Input: nums1 = [1,2,3,0,0,0], m = 3, nums2 = [2,5,6], n = 3
Output: [1,2,2,3,5,6]

Example 2:
Input: nums1 = [1], m = 1, nums2 = [], n = 0
Output: [1]

```swift
 class MergeSortedArray {
    func merge(_ nums1: inout [Int], _ m: Int, _ nums2: [Int], _ n: Int) {
        var i = m - 1, j = n - 1
        
        while i >= 0 || j >= 0 {
            if j < 0 || (i >= 0 && nums1[i] > nums2[j]) {
                nums1[i + j + 1] = nums1[i]
                i -= 1
            } else {
                nums1[i + j + 1] = nums2[j]
                j -= 1
            }
        }
    }
}
```
