---
layout: post
title:  MoveZeroes
date:   2021-04-24 23:50:12 +0300
categories: Algorithm
cover:  "/assets/08.jpg"
tags:   Algorithm
---

## URL
https://leetcode.com/problems/move-zeroes/

### 주요내용: 
ARRAY 문제풀기

### Rule:
정수 배열 번호가 주어지면 0이 아닌 요소의 상대적 순서를 유지하면서 
모두 0을 끝으로 이동합니다.

### Constraints:
1 <= nums.length <= 104
-231 <= nums[i] <= 231 - 1

### time complexity
O(n)

### Example
Example 1:

Input: nums = [0,1,0,3,12]
Output: [1,3,12,0,0]
Example 2:

Input: nums = [0]
Output: [0]

```swift
class MoveZeroes {
    func moveZeroes(_ nums: inout [Int]) {
        var nonZeroIdx = 0
        
        for num in nums where num != 0 {
            nums[nonZeroIdx] = num
            nonZeroIdx += 1
        }
        
        while nonZeroIdx < nums.count {
            nums[nonZeroIdx] = 0
            nonZeroIdx += 1
        }
    }
}
```
