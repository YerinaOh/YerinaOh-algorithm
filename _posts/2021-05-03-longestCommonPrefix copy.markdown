---
layout: post
title:  longestCommonPrefix
date:   2021-05-03 23:56:12 +0300
image:  05.jpg
tags:   Algorithm
---

## URL
https://leetcode.com/problems/longest-common-prefix/submissions/

### Rule:
서로 다른 문자열들이 공유하는 가장 긴 접두사를 찾기.

### time complexity
O(n)


```swift

var longestCommonPrefix = function(strs) {
    if(strs.length === 0) return '';
    let standard = strs[0];
    for(let i = 1; i < strs.length; i++) {
        let count = 0;
        let prefix = ''
        while(standard[count] && strs[i][count]) {
            if(standard[count] === strs[i][count]) {
                prefix += standard[count];
                count++;
            } else {
                if(!prefix) return prefix;
                else break;
            }
        }
        standard = prefix
    }
    return standard;
};
```
