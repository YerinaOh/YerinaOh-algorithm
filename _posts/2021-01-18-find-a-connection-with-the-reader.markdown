---
layout: post
title:  Remove Duplicates from Sorted Array
date:   2021-01-18 15:01:35 +0300
image:  02.jpg
tags:   Algorithm
---


## Sorted Array 


### Why not indeed!

```swift
class RemoveDuplicatesFromSortedArray {
    func removeDuplicates(inout nums: [Int]) -> Int {
        guard nums.count > 0 else {
            return 0
        }
        
        var index = 0
        
        for num in nums where num != nums[index] {
            index += 1
            nums[index] = num
        }
        
        return index + 1
    }
}
```
