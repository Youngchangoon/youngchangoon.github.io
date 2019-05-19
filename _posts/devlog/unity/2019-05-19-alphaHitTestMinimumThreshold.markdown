---
layout: post
title:  "유니티 UGUI 이미지의 투명부분이 터치되지 않게 하는 방법"
subtitle:   "UGUI 이미지에서 Sprite투명부분을 처리하는 방법"
categories: devlog
tags: unity
comments: true
---

![alpha_issue](https://user-images.githubusercontent.com/10609257/57977965-f85dc780-7a3d-11e9-92e7-eb85bdb45ed3.png)

## 문제

---

UGUI의 이미지는 기본적으로 투명한 부분이 있어도 **무조건 네모 전체 영역**이 터치가 됩니다.

따라서 위의 이미지처럼 투명한 부분이 있는 스프라이트가 오는 경우, 눌리지 않아야할 투명한 부분도 눌리게 되는 문제입니다.

## 해결

---

### Image.alphaHitTestMinimumThreshold ( default = 0 )

- 이 임계값보다 작은 Sprite의 알파값은 레이케스트가 통과하게 됩니다.
- **기본값이 0**이므로 투명한 부분까지도 터치가 가능합니다.

이 값을 간단하게 1로 만든다면 불투명한 Sprite만 터치가 가능하게 됩니다!

## 주의점

---

- Sprite에 대한 알파만 체크하고, Image 자체 Color에서 알파가 줄어드는건 무시됩니다.
- 0보다 큰 값을 사용하려면 해당 Sprite의 Texture Read/Write를 활성화 해야하고 해당 스프라이트가 아틀라스를 사용중이라면 아틀라스에서 제외시켜야 합니다.
- 이 설정은 이미지 개별 적용입니다.

## 출처

---

[UI.Image-alphaHitTestMinimumThreshold](https://docs.unity3d.com/ScriptReference/UI.Image-alphaHitTestMinimumThreshold.html)