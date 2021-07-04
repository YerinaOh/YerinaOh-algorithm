---
layout: post
title:  "RGB거리"
date:   2021-07-04T00:25:52-05:00
author: Yerina Oh
categories: Algorithm
tags:	Algorithm
cover:  "/assets/07.png"
---

## URL
https://www.acmicpc.net/problem/1149

### 주요내용: 
RGB거리에는 집이 N개 있다. 거리는 선분으로 나타낼 수 있고, 1번 집부터 N번 집이 순서대로 있다.

집은 빨강, 초록, 파랑 중 하나의 색으로 칠해야 한다. 각각의 집을 빨강, 초록, 파랑으로 칠하는 비용이 주어졌을 때, 아래 규칙을 만족하면서 모든 집을 칠하는 비용의 최솟값을 구해보자.

1번 집의 색은 2번 집의 색과 같지 않아야 한다.
N번 집의 색은 N-1번 집의 색과 같지 않아야 한다.
i(2 ≤ i ≤ N-1)번 집의 색은 i-1번, i+1번 집의 색과 같지 않아야 한다.
### Rule:
첫째 줄에 집의 수 N(2 ≤ N ≤ 1,000)이 주어진다. 둘째 줄부터 N개의 줄에는 각 집을 빨강, 초록, 파랑으로 칠하는 비용이 1번 집부터 한 줄에 하나씩 주어진다. 집을 칠하는 비용은 1,000보다 작거나 같은 자연수이다.
### Example
3
26 40 83
49 60 57
13 89 99

예제 출력:
96

```swift

func solution() {
    let n = Int(readLine()!)!
    let firstRGB = readLine()!.split(separator: " ").map{Int(String($0))!}
    var R = firstRGB[0]
    var G = firstRGB[1]
    var B = firstRGB[2]

    for i in 1..<n {
        let RGB = readLine()!.split(separator: " ").map{Int(String($0))!}
        let minR = min(G+RGB[0], B+RGB[0])
        let minG = min(R+RGB[1], B+RGB[1])
        let minB = min(R+RGB[2], G+RGB[2])
        R = minR
        G = minG
        B = minB
    }
    print(min(R,G,B))
}
```