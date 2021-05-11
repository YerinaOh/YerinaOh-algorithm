---
layout: post
title:  MeetingRoomsII
date:   2021-04-16 23:26:12 +0300
categories: Algorithm
cover:  "/assets/04.jpg"
tags:   Algorithm
---


## Link
https://leetcode.com/problems/meeting-rooms-ii/

### 주요내용: 
Sort 문제풀기

### Rule:
Sort start and end separately, then count conflicts

### time complexity
O(nlogn)


```swift
class MeetingRoomsII {
    func minMeetingRooms(_ intervals: [[Int]]) -> Int {
        let startingTimes = intervals.map { interval in interval[0] }.sorted()
        let endingTimes = intervals.map { interval in interval[1] }.sorted()
        let intervalsCount = intervals.count
        
        var i = 0, j = 0, meetingRoomsNum = 0
        
        while i < intervalsCount && j < intervalsCount {
            if startingTimes[i] < endingTimes[j] {
                meetingRoomsNum += 1
            } else {
                j += 1
            }
            
            i += 1
        }
        
        return meetingRoomsNum
    }
}
```
