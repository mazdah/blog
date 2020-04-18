---
layout: article
title: "라즈베리파이에서 윈도우10으로 원격 데스크톱 연결하기 (xfreerdp)"
date: 2020-04-09 16:50:00 +0900
lastmod: 2020-04-09 16:50:00 +0900
tags: 
    - rdp
    - xfree
---

<br>

관련포스트 : 

라즈베리파이에서 윈도우10 pc로 연결하는 방법은 rdesktop과 xfreerdp를 이용하면 되는디 이중에 xfreerdp가 지원을 많이 해주는것으로 보여서 xfreerdp를 설치했다.

# 1. freerdp 설치

터미널을 실행하고 아래 명령어를 입력하여 xfreerdp 설치

```
sudo apt-get install freerdp2-x11
```

# 2. 윈도우 pc에 원격 연결

윈도우10에 원격 데스크톱을 허용시키고 나서 아래 명령어를 터미널에 입력하게되면 사용자를 선택해서 들어갈 수 있다.

```
xfreerdp 호스트ip
```

# 옵션 추가

풀스크린으로 하려면 `/f`을 쓰면되고,

`/u`와 `/p` 옵션를 사용해서 사용자 이름과 비밀번호를 직접 치고 들어가서 로그인 단계를 생략할 수 있다.

```
xfreerdp -f /v:211.22.211.22 /u:syki /p:123456
```

<br><br><br><br>