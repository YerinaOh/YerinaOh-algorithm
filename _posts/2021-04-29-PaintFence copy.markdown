---
layout: post
title:  PaintFence
date:   2021-04-29 23:46:12 +0300
categories: Algorithm
cover:  "/assets/10.jpg"
tags:   Algorithm
---

## URL
https://leetcode.com/problems/paint-fence/

### 주요내용: 
DP 문제풀기

### Rule:
n 개의 기둥이있는 울타리가 있으며 각 기둥은 k 색상 중 하나로 칠할 수 있습니다.
인접한 두 개 이상의 울타리 기둥이 같은 색을 갖지 않도록 모든 기둥을 페인트해야합니다.
울타리를 칠할 수있는 총 방법 수를 반환합니다.

### Constraints:
n과 k는 0이상의 정수입니다. (마이너스가 아님!)

### time complexity
O(n)

### Example
Example 1:

Input: n=3, k=2  
Output: 6
Explanation:
          post 1,   post 2, post 3
    way1    0         0       1 
    way2    0         1       0
    way3    0         1       1
    way4    1         0       0
    way5    1         0       1
    way6    1         1       0
Example 2:

Input: n=2, k=2  
Output: 4
Explanation:
          post 1,   post 2
    way1    0         0       
    way2    0         1            
    way3    1         0          
    way4    1         1       
    
```swift
class PaintFence {
    func numWays(_ n: Int, _ k: Int) -> Int {
        if n == 0 || k == 0 {
            return 0
        }
        if n == 1 {
            return k
        }
        
        var lastSame = k
        var lastDiff = k * (k - 1)
        
        for i in 2..<n {
            (lastSame, lastDiff) = (lastDiff, (k - 1) * (lastSame + lastDiff))
        }
        
        return lastSame + lastDiff
    }
}
```
