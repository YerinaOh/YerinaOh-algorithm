---
layout: post
title:  ReverseWordsString
date:   2021-04-18 23:24:12 +0300
image:  06.jpg
tags:   Algorithm
---

## URL
https://leetcode.com/problems/reverse-words-in-a-string/

### 주요내용: 
Split으로 문제풀기
열심히 풀었는데 
너무 심플하고 정확한 예제가 있어 가져옴!

### Rule:
입력 문자열 s가 주어지면 단어의 순서를 반대로합니다. (설명하기가 어렵네유.. 밑에 example 보면 이해가 빠를듯.. 단순 문자를 reverse 하는 게 아닌, 말그대로 Word를 reverse 하고, 공백은 자간만 허용하고..이렇게 생각해야 할 듯.)

### Constraints:
 1 <= s.length <= 104
s contains English letters (upper-case and lower-case), digits, and spaces ' '.
There is at least one word in s.

### time complexity
O(n)

### Example
Example 1:
Input: s = "the sky is blue"
Output: "blue is sky the"

Example 2:
Input: s = "  hello world  "
Output: "world hello"

Example 3:
Input: s = "a good   example"
Output: "example good a"

Example 4:
Input: s = "  Bob    Loves  Alice   "
Output: "Alice Loves Bob"

Example 5:
Input: s = "Alice does not even like bob"
Output: "bob like even not does Alice"

```swift
class ReverseWordsString {
	func reverseWords(_ s: String) -> String {
	  	return s.split(separator: " ").reversed().joined(separator: " ")
	}
}
```
