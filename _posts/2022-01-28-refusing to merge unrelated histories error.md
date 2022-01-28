---
layout: post
title:  "refusing to merge unrelated histories error 해결법"
date:   2022-01-28T14:25:00-05:00
author: Yerina Oh
categories: Develop
tags:	GIT
cover:  "/assets/09.png"
---

# refusing to merge unrelated histories error 해결법
로컬저장소 먼저 설정 후,
git 에 원격 저장소 설정을 한 뒤
위 두 저장소를 합치는 작업을 하려다가 난 error이다
두 branch가 서로의 root를 찾지 못하기 때문에 강제 병합을 해 주어야 함.


## 해결 과정
터미널 > cd {project repository}
아래 코드 실행

```Swift
git pull origin {branch명 ex) main} --allow-unrelated-histories
```
