---
layout: post
title:  Triangle
date:   2021-03-31 23:10:35
categories: Algorithm
cover:  "/assets/06.jpg"
tags:   Algorithm
---


## Array
https://leetcode.com/problems/triangle/


### 주요내용: 
DP 로 문제풀기

### Rule:
삼각형 배열이 주어지면 위에서 아래로 최소 경로 합계를 반환합니다.

각 단계에 대해 아래 행의 인접한 번호로 이동할 수 있습니다. 보다 공식적으로 현재 행의 인덱스 i에있는 경우 다음 행의 인덱스 i 또는 인덱스 i + 1로 이동할 수 있습니다.

### Constraints:
1 <= triangle.length <= 200
triangle[0].length == 1
triangle[i].length == triangle[i - 1].length + 1
-104 <= triangle[i][j] <= 104

### time complexity
O(nlogn)

### Example
Example 1:
Input: triangle = [[2],[3,4],[6,5,7],[4,1,8,3]]
Output: 11
Explanation: The triangle looks like:
   2
  3 4
 6 5 7
4 1 8 3
The minimum path sum from top to bottom is 2 + 3 + 5 + 1 = 11 (underlined above).

Example 2:
Input: triangle = [[-10]]
Output: -10

```swift
 class Triangle {
    func minimumTotal(_ triangle: [[Int]]) -> Int {
        guard triangle.count > 0 else {
            return 0
        }
        
        var dp = triangle.last!
        
        for i in stride(from: triangle.count - 2, through: 0, by: -1) {
            for j in 0...i {
                dp[j] = min(dp[j], dp[j + 1]) + triangle[i][j]
            }
        }
        
        return dp[0]
    }
}
```
