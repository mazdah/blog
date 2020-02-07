---
layout: post
title: "지킬(jekyll) 로컬 서버 구성하기"
subtitle: "with Ruby"
date: 2020-02-06 11:30:00 +0900
background: '/img/posts/01.jpg'
---

# 지킬(jekyll) 로컬 서버 구성하기

---

이미 테마를 적용한 상태에서 깃허브에 계속 커밋해서 확인하기가 번거로워져서 방법을 알아보다가 성공했던 방법 올려봄니다.

---
## 1. 루비 다운로드
![루비 다운로드](https://i.imgur.com/kLn21Pa.png)
자신의 운영체제에 맞는 DEVKIT이 포함된 인스톨러를 다운받고 기본값들로 설치한다.  


## 2. 윈도우 검색창에서 Start Command with Ruby 클릭
![cmd 실행](https://i.imgur.com/TJcH3Kp.png)


## 3. 명령창 입력
```
> gem install jekyll
```
```
> gem install bundler  
```
jekyll과 bundler 패키지를 설치해줍니다.


## 4. 폴더로 이동
```
> cd C:\Users\syki\Desktop\test
```
작업중인 디렉토리로 이동합니다.


## 5. 서버 실행
```
> bundle exec jekyll serve
```


***
혹시나 실패했다면, 먼저 터미널에서 작업폴더로 경로 이동후 처음부터 다시해보기 바람