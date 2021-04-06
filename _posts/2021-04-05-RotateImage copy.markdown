---
layout: post
title:  RotateImage
date:   2021-04-05 22:38:54 +0300
image:  09.jpg
tags:   Algorithm
---


## Array
https://leetcode.com/problems/rotate-image/


### 주요내용: 
ARRAY 로 문제풀기

### Rule:
이미지를 나타내는 n x n 2D 행렬이 주어지고 이미지를 90도 (시계 방향) 회전합니다.

이미지를 제자리에서 회전해야하므로 입력 2D 매트릭스를 직접 수정해야합니다. 다른 2D 매트릭스를 할당하지 말고 회전하십시오.

### Constraints:
matrix.length == n
matrix[i].length == n
1 <= n <= 20
-1000 <= matrix[i][j] <= 1000

### time complexity
O(n^2)

### Example
Example 1:
Input: matrix = [[1,2,3],[4,5,6],[7,8,9]]
Output: [[7,4,1],[8,5,2],[9,6,3]]

Example 2:
Input: matrix = [[5,1,9,11],[2,4,8,10],[13,3,6,7],[15,14,12,16]]
Output: [[15,13,2,5],[14,3,4,1],[12,6,8,9],[16,7,10,11]]

```swift
class RotateImage {
    func rotate(_ matrix: inout [[Int]]) {
        let n = matrix.count
        
        for layer in 0..<n / 2 {
            let start = layer, end = n - layer - 1
            for i in start..<end {
                let offset = i - start
                
                (matrix[start][i], matrix[i][end], matrix[end][end - offset], matrix[end - offset][start]) = (matrix[end - offset][start], matrix[start][i], matrix[i][end], matrix[end][end - offset])
            }
        }
    }
}
```
