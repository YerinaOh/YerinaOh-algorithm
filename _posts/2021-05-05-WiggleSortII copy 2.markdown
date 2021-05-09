---
layout: post
title:  WiggleSortII
date:   2021-05-05 23:57:12 +0300
categories: Algorithm
cover:  "/assets/04.jpg"
tags:   Algorithm
---

## URL
https://leetcode.com/problems/wiggle-sort-ii/

### 주요내용: 
Sort 문제풀기

### Rule:
정수 배열 nums가 주어지면 nums [0] <nums [1]> nums [2] <nums [3] ....이되도록 재정렬하십시오.

### Constraints:
1 <= nums.length <= 5 * 104
0 <= nums[i] <= 5000

### time complexity
O(nlogn)

### Example
Example 1:

Input: nums = [1,5,1,1,6,4]
Output: [1,6,1,5,1,4]
Explanation: [1,4,1,5,1,6] is also accepted.
Example 2:

Input: nums = [1,3,2,2,3,1]
Output: [2,3,1,3,1,2]

```swift

class WiggleSortII {
    func wiggleSort(_ nums: inout [Int]) {
        let temp = nums.sorted()
        
        var m = temp.count
        var n = (m + 1) / 2
        
        for i in 0..<nums.count {
            if i & 1 == 0 {
                n = n - 1
                nums[i] = temp[n]
            } else {
                m = m - 1
                nums[i] = temp[m]
            }
        }
    }
}
```
