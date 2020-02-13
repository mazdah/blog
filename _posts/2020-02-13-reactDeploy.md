---
layout: post
title: "리액트(React JS) 깃허브 무료 호스팅하기"
date: 2020-02-13 17:30:00 +0900
background: '/img/posts/01.jpg'
---

우선 깃허브 무료 private에서는 호스팅이 불가능하기 때문데 깃허브 레포지토리를 public으로 바꾸어야 됩니다. (유료요금제면 private 호스팅 가능)

# 1. package.json 수정

먼저 React JS로 작업한 레포지토리에 들어간 후 `package.json` 파일로 들어가서 하단부에 `homepage` 항목을 추가해줍니다.


### 형식 : "homepage": "https://유저네임.github.io/프로젝트네임/"


### 유저네임은 소문자로 써야되며, 프로젝트네임은 그대로 적어주면 됩니다.

```json
"homepage": "https://syki66.github.io/tEsT/"
```

# 2. gh-pages 설치

깃허브의 무료 호스팅을 이용하기 위해 아래 모듈을 설치한다.

```
> npm install gh-pages
```

# 3. "scripts" 수정

scripts 안에 deploy와 predeploy를 추가시켜 줍니다.

```json
"deploy": "gh-pages -d build",
"predeploy": "npm run build"
```

완료후
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

# 4. deploy

```
> npm run deploy
```

위 코드를 실행하게 되면 `predeploy`가 먼저호출되어 `build` 된 후 `build` 디렉토리에 있는 파일들을 깃허브 페이지로 호스팅하게 됩니다.