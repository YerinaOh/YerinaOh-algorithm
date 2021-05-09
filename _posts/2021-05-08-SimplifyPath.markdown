---
layout: post
title:  SimplifyPath
date:   2021-05-08 23:57:12 +0300
image:  07.jpg
tags:   Algorithm
---

## URL
https://leetcode.com/problems/wiggle-sort-ii/

### 주요내용: 
Stack 문제풀기

### Rule:
문자열 경로가 주어지면 이를 단순화 된 표준 경로로 변환하십시오.

Unix 파일 시스템에서 마침표 '.' 현재 디렉토리를 나타내며, 이중 마침표 '..'는 한 수준 위로 디렉토리를 나타내며, 여러 연속 슬래시 (예 : '//')는 단일 슬래시 '/'로 처리됩니다. 이 문제의 경우 '...'와 같은 다른 형식의 마침표는 파일 / 디렉토리 이름으로 처리됩니다.

### Constraints:
1 <= path.length <= 3000
path consists of English letters, digits, period '.', slash '/' or '_'.
path is a valid absolute Unix path.

### time complexity
O(n)

### Example
Example 1:

Input: path = "/home/"
Output: "/home"
Explanation: Note that there is no trailing slash after the last directory name.
Example 2:

Input: path = "/../"
Output: "/"
Explanation: Going one level up from the root directory is a no-op, as the root level is the highest level you can go.
Example 3:

Input: path = "/home//foo/"
Output: "/home/foo"
Explanation: In the canonical path, multiple consecutive slashes are replaced by a single one.
Example 4: ; 

Input: path = "/a/./b/../../c/"
Output: "/c"
   
```swift

class SimplifyPath {
    func simplifyPath(_ path: String) -> String {
        var directories = [String]()
        let components = path.split(separator: "/")
        for component in components {
            switch component {
            case "": break // do nothing
            case ".": break // do nothing, pointing to the current directory
            case "..":
                directories.popLast() // if empty, does nothing
            default:
                directories.append(String(component))
            }
        }
        return "/" + String(directories.joined(separator: "/"))
    }
}
```
