---
layout: article
title: "써드파티 프로그램 없이 키보드 매핑 바꾸기"
subtitle: "using scancode map"
date: 2020-07-31 23:00:00 +0900
lastmod: 2020-07-31 23:00:00 +0900
tags: 
    - scancode map
---

<br>

[autohotkey를 이용한 키보드 매핑 변경하는 법](https://syki66.github.io/blog/2020/07/28/ahk.html)은 이미 포스팅을 하였는데, 만약 써드 파티 소프트웨어를 사용하는 것을 별로 좋아하지 않는 사용자들도 많은데, 이때 `Scancode Map`을 사용하면 간편하게 키보드 매핑을 바꿀 수 있다.

<br>

---

# 1. `레지스트리 편집기` 실행

검색창에서 `regedit`를 검색하여 레지스트리 편집기를 실행시켜 준다.

![image](https://user-images.githubusercontent.com/59393359/89047967-1e912e00-d38a-11ea-87df-045aa0dfad38.png){:.border.rounded}

<br>

---

# 2. 아래 경로로 이동후 `이진값` 생성

아래 경로로 먼저 이동 후

> HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Keyboard Layout

<br>

마우스 오른쪽 버튼을 눌러 `새로 만들기` -> `이진값`을  생성해주고 이름을 `Scancode Map`으로 변경해준다.

![image](https://user-images.githubusercontent.com/59393359/89048692-22718000-d38b-11ea-90e4-216cef655f12.png){:.border.rounded}

<br>

---

# 3. `Scancode Map` 키 값 확인

표를 확인하여, 자신이 바꾸고 싶은 값을 찾으면 된다. (`Set1` 열 확인, `KP`는 키패드 쪽 키를 의미함)

예를 들어 `S`는 `1F`가 매칭이 되며, 주변에 `E0`이 써있지 않을경우에는 뒤에 `00`을 붙여주면 되어, 결국 `S`키는 `1F 00`으로 사용하면 된다.

<style>
    .enlarge{
        transition: transform .2s;
    }
    .enlarge:hover{
        transform: scale(1.3);
    }
</style>

<a href="https://user-images.githubusercontent.com/59393359/89050114-3b7b3080-d38d-11ea-8472-676e43243234.png"><img src="https://user-images.githubusercontent.com/59393359/89050114-3b7b3080-d38d-11ea-8472-676e43243234.png" class="border rounded enlarge"/></a>

<br>

---

# 4. `Scancode Map` 작성

우선 `Scancode Map`을 실행하고 아래 규칙에 맞게 작성을 해주면 된다.

먼저 첫째줄에서 `00 00 00 00 00 00 00 00`을 입력해주어 초기화 해준다.

<br>

두번째줄에서는 먼저 `02 00 00 00` 을 입력해준다. *(바꾸려는 키의 개수 +1을 의미하는데, 숫자를 올리면 한번에 더 많은 키를 바꿀수 있지만 그냥 하나씩 바꾸어 주는게 보기에 더 편하다.)*

두번째줄의 나머지 칸에는 바꿀 키들을 입력해주면 된다.

(예를 들어 A키를 Z키로 바꾸고 싶을경우 `1E 00 2C 00`으로 적어주면 된다.)

<br>

이후 세번째 줄에서는 `00 00 00 00`을 입력해주어 종료 해준다.

![image](https://user-images.githubusercontent.com/59393359/89052243-62873180-d390-11ea-849e-b9cf0d5ede78.png){:.border.rounded}

<br>

---

여러키를 한번에 변경하고 싶다면 아래와 같이 하면된다. **(`Home` <-> `Page Up`, `End` <-> `Page Down`)**

<br>

1번 라인 : `초기화`

2번 라인 : `Home` -> `PgUp`

3번 라인 : `PgUp` -> `Home`

4번 라인 : `End` -> `PgDn`

5번 라인 : `PgDn` -> `End`

6번 라인 : `종료`

![image](https://user-images.githubusercontent.com/59393359/89054129-4638c400-d393-11ea-9368-df95d98821ae.png){:.border.rounded}

<br>

이후 재부팅을 하게되면 키가 제대로 바뀌어 있는 것을 확인 할 수 있다.

<br>

---

## 참고링크

- [https://www.linkedin.com/pulse/remap-keyboard-keys-third-party-software-tutorial-mitch-dampier/](https://www.linkedin.com/pulse/remap-keyboard-keys-third-party-software-tutorial-mitch-dampier/)

<br><br><br><br>