---
layout: article
title: "리액트에서 GIT 푸시 할때 API KEY 숨기기"
subtitle: "using environment variable"
date: 2020-02-23 18:30:00 +0900
lastmod: 2020-02-23 18:30:00 +0900
tags: 
    - env
    - gitignore
    - github
    - api key
    - react JS
---

<br>

# 1. 프로젝트의 루트폴더에 `.env` 파일 생성

루트폴더에 `.env` 파일 생성후, 들어가서 변수명 앞에 반드시 `REACT_APP_` 붙여서 변수명을 설정하고 API 키를 입력한다.

```
REACT_APP_API_KEY=AbCdEfG
```

<br>

---

# 2. `.gitignore` 파일에 `.env` 추가

아래쪽에 `.env` 를 추가해준다.

<br>

---

# 3. 코드작성시

코드 작성시에는 `process.env.REACT_APP_API_KEY` 를 이용해서 API 키를 불러오면 되며

로컬서버를 다시 실행시키면 적용된 것을 볼수있다.

<br>

##### `이미 올라간 파일은 무시가 안되기때문에, 이미 올렸으면 지웠다가 다시 올려야된다.`

<br><br><br><br>