---
layout: article
title: "라즈베리파이에 라즈비안 설치하기"
subtitle: "using Raspberry Pi Imager"
date: 2020-04-09 11:50:00 +0900
lastmod: 2020-09-09 21:00:00 +0900
tags: 
    - raspberry pi
    - raspbian
    - imager
---

<br>

몇년전 쯤만 해도 라즈베리파이에 운영체제를 설치하려면 ISO 파일을 받고, sd카드가 exfat이면 강제로 fat32로 변환시켜준다음 win32diskimager로 이미지를 구워야 했는데, 최근에 Raspberry Pi Imager를 출시하면서 상당히 간편해진 사용법을 소개한다.

<br>

---

# 1. Raspberry Pi Imager 설치

[Raspberry Pi Imager](https://www.raspberrypi.org/downloads/)로 들어가서 자신의 운영체제에 맞는 이미저를 설치하면 된다.

<br>

---

# 2. sd카드 준비 및 굽기

`Raspberry Pi Imager`를 실행한 후에 원하는 운영체제를 선택하고 설치할 sd카드를 선택하고 `WRITE`를 클릭하고 기다리면 굉장히 간단하게 설치가 마무리된다.

<br>

---

# 3. 라즈비안 부팅

굽기가 완료되면 sd카드를 라즈베리파이에 삽입하고서 초반에 설정하는 창에서 거의 기본값으로 해주면 되는데 `여기서 wifi 지역 설정을 미국`으로 해야 `wifi 신호`가 잡히게 된다.

<br>

---

# 4. 업데이트 실행

아래 명령어를 입력하여 업데이트 및 업그레이드를 진행하게 되면 초기 설정이 끝나게 된다.

```
sudo apt-get update && sudo apt-get upgrade
```

<br><br><br><br>