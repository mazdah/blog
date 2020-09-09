---
layout: article
title: "HDMI 없이 라즈베리파이에 원격 연결하기"
subtitle: "raspberry pi control without HDMI"
date: 2020-08-31 01:00:00 +0900
lastmod: 2020-09-09 21:00:00 +0900
tags: 
    - raspberry pi
    - wifi
    - ssh
---

<br>

보통 라즈베리파이를 구매하고 OS를 설치한다음 모니터 및 키보드, 마우스에 연결하여 쓰는 경우가 일반적이지만 만약에 이런 추가적인 장비들이 없을 경우에는 아래와 같은 방법으로 원격으로 제어해서 사용할 수 있다.

<br>

---

# 1. 부팅시 `wifi` 자동 연결

먼저 [SD카드에 라즈비안을 굽고 나서](https://syki66.github.io/blog/2020/04/09/rpi-install.html) SD카드 디렉토리로 이동하게 되면 부팅을 위한 여러 시스템 파일들이 존재하는데, 여기에 부팅이 되면 자동으로 와이파이 연결을 할 수 있도록 파일을 하나 추가해주고, 텍스트 편집기로 열어서 아래 내용을 입력해준다. *(`ssid` 부분과 `psk` 부분만 수정해주면 된다.)*

> wpa_supplicant.conf

```
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
country=KR

network={
 ssid="와이파이_이름"
 psk="와이파이_비밀번호"
}
```

<br>

---

# 2. `SSH 활성화` 해주기

와이파이 설정이 끝났다면, 다시 파일을 추가해주는데 확장자 없이 그냥 `ssh` 파일을 추가해주면 SSH가 부팅시에 활성화되며, 원격으로 연결이 가능해진다.

> ssh

<br>

---

# 3. 라즈베리파이 `부팅` 및 `putty` 실행

이제 sd카드를 제거하고 라즈베리파이에 장착하여 부팅을 하고, 충분히 부팅이 되었다 생각하면 [putty](https://www.putty.org/)를 실행한다.

<br>

이후 `Host Name`에 `raspberrypi`를 입력해주고 `Open`을 클릭하게 되면 `SSH`로 접속이 된다.

![image](https://user-images.githubusercontent.com/59393359/91664075-b1f38580-eb27-11ea-8778-d589afe9fbcf.png){:.border.rounded}

<br>

초기 사용자 이름은 `pi`이며, 비밀번호는 `raspberry`를 입력해주면 정상적으로 로그인이 되게된다.

![image](https://user-images.githubusercontent.com/59393359/91664165-583f8b00-eb28-11ea-8f52-dda1cb918fb0.png){:.border.rounded}

<br>

---

# 4. GUI로 접속하기

먼저 아래 명령어를 입력하여 `xrdp`를 설치한다.

```
sudo apt-get install xrdp
```

<br>

이후 윈도우에서 `원격 데스크톱 연결`을 실행한 뒤 `raspberrypi` 또는 `ip주소`를 입력하고서 연결을 누르면 GUI환경으로 접속할수 있다.

![image](https://user-images.githubusercontent.com/48711215/92594402-ab120300-f2dd-11ea-9518-f02cea2a059f.png){:.border.rounded}

<br><br><br><br>