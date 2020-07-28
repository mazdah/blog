---
layout: article
title: "깃, 로그아웃하기"
subtitle: "git logout"
date: 2020-05-08 18:00:00 +0900
lastmod: 2020-05-08 18:00:00 +0900
tags: 
    - git
    - logout
---

<br>

`git`에서 로그아웃을 하고 싶을때 제대로 로그아웃이 실행이 안되는 경우가 있는데, 아래의 순서대로 따라하게 되면 정상적으로 로그아웃을 할 수 있게된다.

---

# 1. `제어판` 실행

제어판 실행 이후 `사용자 계정` 클릭

![image](https://user-images.githubusercontent.com/59393359/81506084-f1a32100-932e-11ea-8657-acf9d8c09917.png){:.border.rounded}

<br>

---

# 2. `자격 증명 관리` 클릭

![image](https://user-images.githubusercontent.com/59393359/81506133-329b3580-932f-11ea-86b7-12b420d19cdf.png){:.border.rounded}

<br>

---

# 3. `Windows 자격 증명` 클릭

![image](https://user-images.githubusercontent.com/59393359/81506171-73934a00-932f-11ea-8a3e-bf41ed66b90a.png){:.border.rounded}

<br>

---

# 4. 깃허브 관련 자격 증명 클릭 후 제거

![image](https://user-images.githubusercontent.com/59393359/81506254-f9af9080-932f-11ea-9a22-46cc2b8c723c.png){:.border.rounded}

<br>

---

# 5. 재 로그임

이제 `git`에서 `commit`를 수행 할 때, 새로 사용자 이름과 비밀번호를 입력하라는 메시지가 표시되는데 다른 계정으로 로그인을 진행하고, 아래 명령어를 사용하여 사용자 이름과 이메일을 전역으로 입력해준다.

```
git config --global user.name "syki66"
git config --global user.email example@gmail.com
```

<br><br><br><br>