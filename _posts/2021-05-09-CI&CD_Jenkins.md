---
layout: post
title:  "CI&CD_Jenkins"
date:   2021-03-30T14:25:52-05:00
author: Yerina Oh
categories: CI
tags:	CI
cover:  "/assets/02.png"
---


## Jenkins

### Installing Jenkins

다운로드 링크 - https://jenkins.io/download/ 
brew 로 설치

`
brew install jenkins-lts
`

### cmd 접속
http://localhost:8080

### Jenkins login

password 획득
`
sudo cat /Users/{YOUR_USER_NAME}/.jenkins/secrets/initialAdminPassword
`

### Jekins plugins install

Install suggested plugins 선택

### Jenkins Setup

새작업>프로젝트 명 입력 > Freestyle project 선택 > 소스코드 관리에 Github 주소입력

### shell 명령어 입력
`
xcodebuild -scheme HttpRequest -configuration Debug build test -destination 'platform=iOS Simulator,name=iPhone 8'
`

빌드 완료되면 자동으로 앱 실행 후 unit test 실행 확인