---
layout: post
title: "리액트, 깃허브 페이지를 이용하여 무료 웹호스팅하기"
subtitle: "React js, deploy github pages"
date: 2020-02-13 17:30:00 +0900
background: '/img/posts/02.jpg'
---

우선 깃허브의 private 무료버전에서는 호스팅이 불가능하기 때문에 깃허브 레포지토리가 public으로 설정 되어있어야 한다. (유료요금제를 쓰고 있다면 private 호스팅 가능)

<br/>

***

# 1. package.json 수정

먼저 React JS로 작업한 레포지토리에 들어간 후 `package.json` 파일 하단부에 `homepage` 항목을 추가해준다.

##### 형식 : `"homepage": "https://유저네임.github.io/프로젝트네임/"`

##### 유저네임은 소문자로 써야되며, 프로젝트네임은 그대로 적어준다.

```json
"homepage": "https://syki66.github.io/tEsT/"
```

<br/>

***

# 2. gh-pages 설치

깃허브의 무료 호스팅을 이용하기 위해 아래 모듈을 설치한다.

```
> npm install gh-pages
```

<br/>

***

# 3. `"scripts"` 수정

scripts 안에 deploy와 predeploy를 추가시킨다.

```json
"deploy": "gh-pages -d build",
"predeploy": "npm run build"
```

***

#### 완료후

```json
  "scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject",
    "deploy": "gh-pages -d build",
    "predeploy": "npm run build"
  }
```

<br/>

***

# 4. deploy

```
> npm run deploy
```

위 코드를 실행하게 되면 `predeploy`가 먼저호출되어 `build` 디렉토리를 만들고, 이후 `deploy`가 실행되어 `build` 디렉토리에 있는 파일들을 깃허브 페이지로 웹호스팅 시켜준다.