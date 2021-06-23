---
layout: post
title:  "Avoiding Massive View Controllers"
date:   2021-06-20T00:25:52-05:00
author: Yerina Oh
categories: Development
tags:	Development
cover:  "/assets/01.png"
---

## URL
https://github.com/johnsundell/swifttips#49-avoiding-massive-view-controllers\
### 주요내용: 
masisive한 vc의 사용을 막기 위해

### Rule:


```swift
// BEFORE

class LoginViewController: UIViewController {
    private lazy var signUpLabel = UILabel()
    private lazy var signUpImageView = UIImageView()
    private lazy var signUpButton = UIButton()
}

// AFTER

class LoginViewController: UIViewController {
    private lazy var signUpView = SignUpView()
}

class SignUpView: UIView {
    private lazy var label = UILabel()
    private lazy var imageView = UIImageView()
    private lazy var button = UIButton()
}
```