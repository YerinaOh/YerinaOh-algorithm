---
layout: post
title:  "Image Cache Manager"
date:   2022-01-31T14:25:00-05:00
author: Yerina Oh
categories: Develop
tags:	GIT
cover:  "/assets/01.png"
---

# Image Cache Manager
매번 load 하기보다 캐싱으로 이미지 받아와서 처리하는 방법

## 해결 과정
url을 키값으로, image를 value 로 세팅하여 그때그때 꺼내쓰는 방법 고안

```Swift
class ImageCacheManager {
    static let shared = NSCache<NSString, UIImage>()
    private init() {}
}

extension UIImageView {
    
    /// image load
    /// - Parameter urlString: url 경로 string타입
    public func imageFromUrlString(urlString: String?) {
        guard let url: String = urlString else {
            return
        }
        
        let cacheKey = NSString(string: url)
        if let cachedImage = ImageCacheManager.shared.object(forKey: cacheKey) {
            self.image = cachedImage
            return
        }
        
        DispatchQueue.global().async {
            NetworkManager.shared.loadImage(urlString: url) { image in
                DispatchQueue.main.async {
                    if let cacheImage = image {
                        ImageCacheManager.shared.setObject(cacheImage, forKey: url as NSString)
                    }
                    
                    self.image = image
                }
            }
        }
    }
}
```

## 문제점
같은 경로의 이미지가 변경되었을 경우는 어떻게 해야할까?
리서치 결과, 헤더에 있는 Etag값으로 확인 가능하다.
리소스의 id값과 같은 개념이다
서버 구현 필수!

->
ETag HTTP 응답 헤더는 특정 버전의 리소스를 식별하는 식별자입니다. 웹 서버가 내용을 확인하고 변하지 않았으면, 웹 서버로 full 요청을 보내지 않기 때문에, 캐쉬가 더 효율적이게 되고, 대역폭도 아낄 수 있습니다. 허나, 만약 내용이 변경되었다면, "mid-air collisions" 이라는 리소스 간의 동시 다발적 수정 및 덮어쓰기 현상을 막는데 유용하게 사용됩니다.

만약 특정 URL 의 리소스가 변경된다면, 새로운 ETag 가 생성됩니다. ETag 는 지문과 같은 역할을 하면서 다른 서버들이 추적하는 용도에 이용되기도 합니다. ETag 를 비교하여 리소스가 서로 같은지의 여부를 빠르게 판단할 수 있지만, 서버에서 무기한으로 지속될 수 있도록 설정할 수도 있습니다.

Request Header에 "If-None-Match" 라는 key값으로 저장된 ETag값을 넣어서 통신을 요청하고 만약에 리소스에 변경이없다면
응답코드가 다르게 온다.

