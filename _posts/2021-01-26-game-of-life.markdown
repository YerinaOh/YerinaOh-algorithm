---
layout: post
title:  Game-of-Life
date:   2021-01-26 20:01:35 +0300
image:  02.jpg
tags:   Algorithm
---


## Sorted Array 
https://leetcode.com/problems/game-of-life/


### 주요내용: 
이진배열 탐색하기

### Rule:
1. 살아있는 이웃이 두 개 미만인 모든 살아있는 세포는 인구 부족으로 인한 것처럼 죽습니다.
2. 2 ~ 3 명의 살아있는 이웃이있는 모든 살아있는 세포는 다음 세대를 위해 살아갑니다.
3. 세 개 초과의 살아있는 이웃이있는 모든 살아있는 세포는 인구 과잉처럼 죽습니다.
4. 정확히 세 개의 살아있는 이웃이있는 죽은 세포는 마치 번식에 의한 것처럼 살아있는 세포가됩니다.

### 풀이법 (블로그 참고하였음)

여기서 다음세대로 갈 때 변경되는 사항들은 아래와같이 정리.

현재 죽음 - 다음 세대 생존 ⇒ 3
현재 생존 - 다음 세대 죽음 ⇒ 2


Example1:
Input: board = [[0,1,0],[0,0,1],[1,1,1],[0,0,0]]
Output: [[0,0,0],[1,0,1],[0,1,1],[0,1,0]]

Example2:
Input: board = [[1,1],[1,0]]
Output: [[1,1],[1,1]]

```swift
import UIKit

class Solution {
    func gameOfLife(_ board: inout [[Int]]) { // 2진배열 array
        guard board.count > 0 else {
            return
        }
        
        let m = board.count, n = board[0].count
        
        for i in 0..<m {
            for j in 0..<n {
                changeStatus(&board, i, j, m, n)
            }
        }
        board = board.map { $0.map { $0 % 2 } }
    }
    
    private func changeStatus(_ board: inout [[Int]], _ i: Int, _ j: Int, _ m: Int, _ n: Int) {
        var population = 0 // next generation 의 값
    
        for x in i - 1...i + 1 { // 앞의 값과 비교
            for y in j - 1...j + 1 { // 위의 값과 비교
                if x < 0 || x >= m || y < 0 || y >= n { // 모서리에 도달하면 contiunue
                    print("i : \(i), j : \(j),x: \(x),y: \(y), popu:\(population)")
                    continue
                }
                if x == i && y == j { // 모서리에 도달하면 contiunue
                    continue
                }
                // 조건 2 : pop이 1이거나 / 2 이면 상태를 변경, 나머지는 유지
                population = board[x][y] == 1 || board[x][y] == 2 ? population + 1 : population
            }
        }
        
        if board[i][j] == 1 { //현재 살아있는 상태
            // 조건 1,3 : pop이 가뭄이거나 / 홍수이면 사망으로 설정, 나머지는 생존
            board[i][j] = population < 2 || population > 3 ? 2 : 1
        } else { //현재 죽어있는 상태
            // 조건 4 : 3개의 이웃을 가지고있는 경우는 생존, 이외는 사망
            board[i][j] = population == 3 ? 3 : 0
        }
    }
}

let solution = Solution.init()
var board = [[0,1,1],[0,0,1],[1,1,1],[0,0,0]]
solution.gameOfLife(&board)

print(board)
```
