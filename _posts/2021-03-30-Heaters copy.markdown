---
layout: post
title:  Heaters
date:   2021-03-30 23:31:35
categories: Algorithm
cover:  "/assets/05.jpg"
tags:   Algorithm
---


## Array
https://leetcode.com/problems/heaters/


### 주요내용: 
array 로 문제풀기

### Rule:
모든 집을 데우기 위해 따뜻한 반경이 고정 된 표준 히터를 설계하는 것입니다.
집이 히터의 따뜻한 반경 범위 내에있는 한 모든 집을 데울 수 있습니다.
가로선에 주택과 히터의 위치가 주어지면 히터의 최소 반경 표준을 반환하여 해당 히터가 모든 주택을 덮을 수 있도록합니다.

### Constraints:
1 <= houses.length, heaters.length <= 3 * 104
1 <= houses[i], heaters[i] <= 109

### time complexity
O(nlogn)

Example 1:

Input: houses = [1,2,3], heaters = [2]
Output: 1
Explanation: The only heater was placed in the position 2, and if we use the radius 1 standard, then all the houses can be warmed.

Example 2:

Input: houses = [1,2,3,4], heaters = [1,4]
Output: 1
Explanation: The two heater was placed in the position 1 and 4. We need to use radius 1 standard, then all the houses can be warmed.

Example 3:

Input: houses = [1,5], heaters = [2]
Output: 3

```swift
class FindPeakElement {
  func findRadius(_ houses: [Int], _ heaters: [Int]) -> Int {
        var i = 0, radius = 0
        let houses = houses.sorted(), heaters = heaters.sorted()
        
        for house in houses {
            while i < heaters.count - 1 && 2 * house >= heaters[i] + heaters[i + 1]  {
                i += 1
            }
            
            radius = max(radius, abs(house - heaters[i]))
        }
        
        return radius
    }
}
```
