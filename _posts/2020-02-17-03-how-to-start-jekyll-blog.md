---
layout: post
title: "무료 깃허브 블로그, 지킬을 이용하여 시작하기"
subtitle: "github pages, blog with jekyll"
date: 2020-02-17 15:30:00 +0900
lastmod: 2020-02-17 15:30:00 +0900
---

jekyll 은 ruby 로 제작되어진 정적 웹사이트 개발 툴이며, `markdown` 을 지원하여 편하게 블로그 포스팅을 할 수 있게 해준다.

또한 깃허브의 호스팅 기능(github pages)을 이용하여 무료로 사용 가능하다.

<br />

---

# 1. 깃허브 레포지토리 생성

깃허브에서 블로그용 새 레포지토리를 생성한다.

<br />

---

# 2. 원하는 테마 선택

나는 [jasper](https://jekyller.github.io/jasper/)와 [clean blog](http://blackrockdigital.github.io/startbootstrap-clean-blog-jekyll/) 중에서 고민하다가 조금 더 깔끔한 clean blog 테마를 선택하게 되었다.

- #### 지킬테마 검색 사이트
    - [jekyllthemes.org](http://jekyllthemes.org/)
    - [jekyllthemes.io](https://jekyllthemes.io/)

<br />

---

# 3. `_config.yml` 수정

원하는 테마 zip파일 다운로드 & 압축풀고 `_config.yml`을 아래와 같이 수정

```yml
title:              혼공
email:              test@naver.com
description:        혼자 공부하는 블로그
author:             SyKi
baseurl:            "/SyKi_blog"
url:                "https://syki66.github.io"
```

- ### 여기서 `baseurl`과 `url`은 반드시 수정해주어야함.

`url` -> `"https://깃허브유저네임.github.io"`

`baseurl` -> `"/디렉토리명"`

이렇게 입력해주면된다. (여기서 유저네임은 소문자로 적어야됨)

<br />

---

# 4. 웹사이트 무료 호스팅

생성된 레포지토리의 `Settings` -> `GitHub Pages` -> `Source`에서 `master branch`를 체크

`your site is published at ~~` 이렇게 표시가 되게 된다. 이후 옆에 링크를 누르게 되면 정상적으로 블로그 호스팅이 성공한 것을 확인할수 있다.

![image](https://user-images.githubusercontent.com/59393359/74637891-3b57f180-51ae-11ea-81b6-99bc0c85a418.png)

<br />

---

# 5. 블로그 포스팅

포스트 생성은 `_posts` 폴더에서 `markdown` 파일을 만들어서 블로그를 작성하면 되며 이름은 아래와 같은 규칙으로 하면된다.

`YYYY-MM-DD-title.md`

```
> 2020-02-17-how-to-start-jekyll-blog.md
```

markdown 파일 상단에 아래의 `yml`코드를 추가하고 알맞게 수정한 뒤, 밑에 `markdown` 문법을 이용하여 포스트를 작성하면됨 - ([markdown 사용법](https://gist.github.com/ihoneymon/652be052a0727ad59601))

```yml
---
layout: post
title: "제목"
subtitle: "부제목"
date: 2020-02-05 16:30:00 +0900 # +0900은 서울 표준시
background: '/img/posts/01.jpg' # 포스트 배경사진
---
```

포스트 작성을 완료한 후 깃허브에 업로드 하고, 얼마뒤에 퍼블리시된 url 주소로 들어가면 정상정으로 포스트가 추가된 것을 볼수있음

<br />
