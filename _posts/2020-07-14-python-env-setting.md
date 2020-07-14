---
layout: article
title: "파이썬 pip 환경변수 설정하기"
subtitle: "set python pip env setting"
date: 2020-07-14 11:30:00 +0900
lastmod: 2020-07-14 11:30:00 +0900
tags: 
    - python
    - pip
    - env
---

<br>

파이썬을 처음 설치하거나 다시 설치하였을때, `cmd`에서 파이썬 `pip`를 사용하려고 하면 아래와 같이 에러가 난다.

![image](https://user-images.githubusercontent.com/59393359/87446178-eb356c00-c633-11ea-866f-51e312b30cc2.png){:.border.rounded}

<br>

이때 `pip`를 사용하기 위해서는 매번 파이썬이 설치가 되있는 경로로 이동해줘야되는 번거로움이 있는데, 아래의 순서대로 따라하면 굳이 경로를 찾아들어가지 않아도 손쉽게 `pip`를 사용할 수 있다.

<br>

---

# 1. `시스템 환경 변수 편집` 실행

작업표시줄에 있는 검색창을 이용해서 쉽게 들어갈 수 있다.

![image](https://user-images.githubusercontent.com/59393359/87445443-0653ac00-c633-11ea-897c-be92308e41a0.png){:.border.rounded}

<br>

---

# 2. `환경 변수 `클릭

![image](https://user-images.githubusercontent.com/59393359/87446809-c2fa3d00-c634-11ea-88fc-a9387015ba5c.png){:.border.rounded}

<br>

---

# 3. `Path` 더블 클릭

*또는 Path 한번 클릭 후 `편집` 클릭*

![image](https://user-images.githubusercontent.com/59393359/87448618-0a81c880-c637-11ea-945f-fe78c2f6b219.png){:.border.rounded}

<br>

---

# 4. 새로 만들기 클릭 후 `pip.py` 파일 경로 입력

![image](https://user-images.githubusercontent.com/59393359/87448877-63516100-c637-11ea-83a7-5a9a637a23f8.png){:.border.rounded}

<br>

일반적인 경로는 아래와 같다.

> C:\Users\syki66\AppData\Local\Programs\Python\Python38\Scripts

<br>

---

이후 확인을 누르고, `cmd`를 재실행하면 `pip`가 정상적으로 작동하게 된다.

![image](https://user-images.githubusercontent.com/59393359/87449310-fbe7e100-c637-11ea-9499-cc7fb604c079.png){:.border.rounded}

<br><br><br><br>