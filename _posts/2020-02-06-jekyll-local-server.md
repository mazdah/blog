---
layout: single
title: "깃허브 지킬(jekyll) 블로그 로컬 서버 구성하기"
subtitle: "with Ruby"
date: 2020-02-06 11:30:00 +0900
lastmod: 2020-04-12 11:30:00 +0900
background: '/img/posts/05.jpg'
author_profile: false
---

이미 테마를 적용한 상태에서 깃허브에 계속 퍼블리시 해서 확인하기가 번거로울때 사용하는 방법이다.

<br/>

---

## 1. 루비 다운로드

자신의 운영체제에 맞는 DEVKIT이 포함된 인스톨러를 다운받고 기본값으로 설치한다.  

![루비 다운로드](https://user-images.githubusercontent.com/59393359/74086021-5649a800-4ac2-11ea-916a-0fa9b518936b.PNG)

<br/>

---

## 2. 윈도우 검색창에서 Start Command with Ruby 클릭

![cmd 실행](https://user-images.githubusercontent.com/59393359/74086033-695c7800-4ac2-11ea-8ab1-94c303a84d8f.PNG)

<br/>

---

# 3. 폴더로 이동

지킬을 설치한 디렉토리로 이동한다.

```
> cd C:\Users\syki\Desktop\test
```

<br/>

---

# 4. 명령창 입력

jekyll과 bundler 패키지를 설치한다.

```
> gem install jekyll
```

```
> gem install bundler  
```

<br/>

---

# 5. 로컬 서버 실행

아래 명령어를 입력하면 `127.0.0.1:4000` 또는 `localhost:4000` 으로 접속하면 된다. *(baseurl이 있을경우에는 주소 뒤에 추가해야됨)*

```
> bundle exec jekyll serve
```

<br/>

---