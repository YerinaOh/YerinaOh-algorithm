---
layout: post
title:  HouseRobber
date:   2021-03-25 23:29:35 +0300
image:  03.jpg
tags:   Algorithm
---


## DP
https://leetcode.com/explore/featured/card/top-interview-questions-easy/97/dynamic-programming/576/


### 주요내용: 
DP 로 문제풀기

### Rule:
당신은 강도이다. 
각 집에는 일정 금액의 돈이 숨겨져 있으며, 각 집을 강탈하는 것을 막는 유일한 제약은 
/인접한 집에 보안 시스템이 연결되어 있고 /같은 밤에 인접한 두 집이 침입하면 경찰에 자동으로 연락한다는 것이다.

각 집의 금액을 나타내는 정수 배열 숫자가 주어지면 경찰에 알리지 않고 오늘 밤 훔칠 수 있는 최대 금액을 반환하시오.

### Constraints:
1 <= nums.length <= 100
0 <= nums[i] <= 400

### time complexity
O(N)

Example 1:
Input: nums = [1,2,3,1]
Output: 4
Explanation: Rob house 1 (money = 1) and then rob house 3 (money = 3).
Total amount you can rob = 1 + 3 = 4.

Example 2:
Input: nums = [2,7,9,3,1]
Output: 12
Explanation: Rob house 1 (money = 2), rob house 3 (money = 9) and rob house 5 (money = 1).
Total amount you can rob = 2 + 9 + 1 = 12.

```swift
class HouseRobber {
    func rob(nums: [Int]) -> Int {
        var curt = 0, prev = 0
        
        for num in nums {
            (curt, prev) = (max(curt, prev + num), curt)
        }
        
        return curt
    }
}
```
