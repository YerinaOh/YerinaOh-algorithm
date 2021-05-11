---
layout: post
title:  Array Partition
date:   2021-04-04 23:12:10 +0300
categories: Algorithm
cover:  "/assets/08.jpg"
tags:   Algorithm
---


## Array
https://leetcode.com/problems/array-partition-i/


### 주요내용: 
SORT 로 문제풀기

### Rule:
가장 큰 정수 subarray 의 합을 구하여라

### Constraints:
1 <= n <= 104
nums.length == 2 * n
-104 <= nums[i] <= 104

### time complexity
O(n)

### Example
Example 1:
Input: nums = [1,4,3,2]
Output: 4
Explanation: All possible pairings (ignoring the ordering of elements) are:
1. (1, 4), (2, 3) -> min(1, 4) + min(2, 3) = 1 + 2 = 3
2. (1, 3), (2, 4) -> min(1, 3) + min(2, 4) = 1 + 2 = 3
3. (1, 2), (3, 4) -> min(1, 2) + min(3, 4) = 1 + 3 = 4
So the maximum possible sum is 4.

Example 2:
Input: nums = [6,2,6,5,1,2]
Output: 9
Explanation: The optimal pairing is (2, 1), (2, 5), (6, 6). min(2, 1) + min(2, 5) + min(6, 6) = 1 + 2 + 6 = 9.

```swift
class ArrayPartition {
    func arrayPairSum(_ nums: [Int]) -> Int {
        return nums.sorted(by: <).enumerated()
            .flatMap { $0 % 2 == 0 ? $1 : nil }
            .reduce(0) { $0 + $1 }
    }
}
```
