---
layout: post
title:  PaintFence
date:   2021-04-29 23:46:12 +0300
image:  02.jpg
tags:   Algorithm
---

## URL
https://leetcode.com/problems/paint-fence/

### 주요내용: 
DP 문제풀기

### time complexity
O(n)


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
