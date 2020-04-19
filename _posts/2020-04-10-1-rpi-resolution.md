---
layout: article
title: "라즈베리파이 해상도 2560x1080으로 설정하기"
subtitle: "ultra wide monitor resolution setting"
date: 2020-04-09 11:50:00 +0900
lastmod: 2020-04-09 11:50:00 +0900
tags: 
    - raspberry pi
    - resolution
---

<br>

라즈베리파이를 설치하고나서 21:9 모니터를 쓰는 사람들은 해상도가 이상하게 맞지 않는 현상이 발생하는데 이는 자동으로 라즈비안에서 2560x1080 해상도를 잡아주지 못하기때문이다. 따라서 수동으로 설정해야한다.

<br>

---

# 1. `config.txt`에 들어가기

`/boot/config.txt`로 sudo를 이용해서 들어가거나 루트 사용자로 들어가야 수정을 할수 있다.

<br>

---

# 2. `config.txt` 파일 수정

아래 명령어들을 추가해준다.

```
# uncomment to force a specific HDMI mode (this will force VGA)
hdmi_timings=2560 0 48 32 80 1080 0 7 20 12 0 0 0 52 0 159838855 7
hdmi_group=2
hdmi_mode=87
hdmi_drive=2
framebuffer_width=2560
max_framebuffer_width=2560
framebuffer_height=1080
hdmi_pixel_freq_limit=160000000
```

<br>

---

# 3. 재부팅

재부팅하게되면 정상적으로 2560x1080 해상도로 변경된다.

<br><br><br><br>