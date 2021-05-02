---
layout: post
title:  BestTimeBuySellStock
date:   2021-04-30 23:57:12 +0300
image:  03.jpg
tags:   Algorithm
---

## URL
https://leetcode.com/problems/best-time-to-buy-and-sell-stock/

### 주요내용: 
DP 문제풀기

### Rule:
PaintFence

### Constraints:
1 <= prices.length <= 105
0 <= prices[i] <= 104

### time complexity
O(n)

### Example
Example 1:

Input: prices = [7,1,5,3,6,4]
Output: 5
Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
Note that buying on day 2 and selling on day 1 is not allowed because you must buy before you sell.
Example 2:

Input: prices = [7,6,4,3,1]
Output: 0
Explanation: In this case, no transactions are done and the max profit = 0.
```swift

class BestTimeBuySellStock {
    func maxProfit(prices: [Int]) -> Int {
        guard prices.count > 0 else {return 0}
        var maxProfit = 0
        var buyDay = 0
        
        for i in 1 ..< prices.count {
            let profit = prices[i] - prices[buyDay]
            if profit < 0 {
                buyDay = i
            }
            maxProfit = max(profit, maxProfit)
        }
        
        return maxProfit
    }
}
```
