---
layout: post
title:  Coin Change
date:   2021-03-23 23:22:35
categories: Algorithm
cover:  "/assets/05.jpg"
tags:   Algorithm
---


## DP
https://leetcode.com/explore/interview/card/top-interview-questions-medium/111/dynamic-programming/


### 주요내용: 
DP 로 문제풀기

### Rule:
1원, 2원, 5원 짜리 동전을 가지고 11원을 만든다
이 때, 최소 동전의 개수를 구하라
a(n) = a(n-1)+ a(n-2)

### time complexity
O(N)


Example 1:
Input: coins = [1,2,5], amount = 11
Output: 3
Explanation: 11 = 5 + 5 + 1

Example 2:
Input: coins = [2], amount = 3
Output: -1

Example 3:
Input: coins = [1], amount = 0
Output: 0

Example 4:
Input: coins = [1], amount = 1
Output: 1

Example 5:
Input: coins = [1], amount = 2
Output: 2

```swift

class CoinChange {
    func coinChange(_ coins: [Int], _ amount: Int) -> Int {
        guard amount > 0 else {
            return 0
        }
        
        let coins = coins.sorted()
        var minAmounts = Array(repeating: -1, count: amount + 1)
        minAmounts[0] = 0
        
        for i in 1...amount {
            for coin in coins {
                if coin > i {
                    break
                }
                
                if minAmounts[i - coin] == -1 {
                    continue
                }
                
                minAmounts[i] = minAmounts[i] == -1 ? minAmounts[i - coin] + 1 : min(minAmounts[i - coin] + 1, minAmounts[i])  
            }
        }
        
        return minAmounts[amount]
    }
}
```
