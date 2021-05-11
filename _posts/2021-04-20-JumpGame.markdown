---
layout: post
title:  JumpGame
date:   2021-04-20 23:48:12 +0300
categories: Algorithm
cover:  "/assets/06.jpg"
tags:   Algorithm
---

## URL
https://leetcode.com/problems/jump-game/

### 주요내용: 
DP 문제풀기

### Rule:
그니까 이게.. 개구리가 점프 가능한지 bool 값으로 return 하라는건데 내용은 이렇구먼..
음이 아닌 정수 숫자의 배열이 주어지면 처음에 배열의 첫 번째 인덱스에 배치됩니다.
배열의 각 요소는 해당 위치에서 최대 점프 길이를 나타냅니다.
마지막 INDEX에 도달 할 수 있는지 확인하십시오.

### Constraints:
1 <= nums.length <= 3 * 104
0 <= nums[i] <= 105

### time complexity
O(n)

### Example
Example 1:
Input: nums = [2,3,1,1,4]
Output: true
Explanation: Jump 1 step from index 0 to 1, then 3 steps to the last index.

Example 2:
Input: nums = [3,2,1,0,4]
Output: false
Explanation: You will always arrive at index 3 no matter what. Its maximum jump length is 0, which makes it impossible to reach the last index.

```swift
class JumpGame {
    func canJump(_ nums: [Int]) -> Bool {
        var maximumIndex = nums[0]
        
        for (currentIndex, value) in nums.enumerated(){
            
            if currentIndex > maximumIndex{
                return false
            }
            
            maximumIndex = max(maximumIndex, currentIndex + value)
        }
        
        return true
    }
}
```
