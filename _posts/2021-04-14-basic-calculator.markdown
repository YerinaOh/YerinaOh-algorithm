---
layout: post
title:  basic calculator
date:   2021-04-14 23:42:10 +0300
image:  04.jpg
tags:   Algorithm
---


## Array
https://leetcode.com/problems/basic-calculator/

### 주요내용: 
Stack으로 문제풀기

### Rule:
문자열 s를 입력하고 평가할 기본 계산기를 구현하기!

### Constraints:
1 <= s.length <= 3 * 105
s consists of digits, '+', '-', '(', ')', and ' '.
s represents a valid expression.

### time complexity
O(n)

### Example
Example 1:
Input: s = "1 + 1"
Output: 2

Example 2:
Input: s = " 2-1 + 2 "
Output: 3

Example 3:
Input: s = "(1+(4+5+2)-3)+(6+8)"
Output: 23

```swift
class BasicCalculator {
    func calculate(_ s: String) -> Int {
        var result = 0
        var num = 0
        var sign = 1
        var stack = [sign]
        
        for char in s {
            switch char {
            case "+", "-":
                result += num * sign
                sign = stack.last! * (char == "+" ? 1 : -1)
                num = 0
            case "(":
                stack.append(sign)
            case ")":
                stack.removeLast()
            case " ":
                break
            default:
                num = num * 10 + char.wholeNumberValue!
            }
        }
        
        return result + num * sign
    }
}
```
