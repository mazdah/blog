---
layout: single

title: "minimal mistake theme 지킬 블로그 초기 설정하기"
# excerpt: ""

date: 2020-04-11 20:50:00 +0900
lastmod: 2020-04-12 11:50:00 +0900

author_profile: false

header:
  overlay_image: https://images.unsplash.com/photo-1501785888041-af3ef285b470?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1350&q=80
  overlay_filter: 0.5

categories: 
  - blog

tags: 
    - test
    - theme

# table of content
toc: true
toc_label: "Contents"
toc_icon: "bars"
toc_sticky: true
---

clean-blog 테마가 질리기도 하고 수동으로 바꾸어야 되는 설정들이 꽤 많고 귀찮아서, 가장 인기있고 커스터마이징 및 기타 관리가 쉬운 minimal-mistakes 테마로 바꾸게 되었다.

<br/>

---

# 1. 테마 가져오기

깃허브의 `Fork`를 이용하거나, 깃의 `clone`를 이용하거나, 또는 정식 릴리즈가 된 압축파일을 다운로드 받는다.

<br />

---

# 2. `_config.yml` 수정

루트 디렉토리의 `_config.yml`에 들어가서 수정한다.

```yml
# 기본정보
minimal_mistakes_skin    : "default" # "default", "air", "aqua", "contrast", "dark", "dirt", "neon", "mint", "plum", "sunrise" 중에 원하는 스킨으로 선택한다.
locale                   : "en-US" # 언어 설정이며 ko-KR 로 설정하면 한국어로 바뀐다.
title                    : "syki blog" # 블로그 이름
subtitle                 : # 부제목으로, 블로그 이름 밑에 작게 표시된다.
name                     : "syki66" # 이름
description              : "셀프 참조 블로그" # 설명
url                      : "https://syki66.github.io" # https://깃허브유저네임.github.io 형식으로 입력하면된다.
baseurl                  : "/blog" # baseurl을 사용하고 있으면 입력하면된다.
teaser                   : # 연관포스트나 검색 등에서 미리보기 사진을 설정하고 싶으면 넣으면된다.
logo                     : # 블로그 타이틀 옆에 들어가는 로고

# disqus 댓글기능 활성화
comments:
  provider               : "disqus"
  disqus:
    shortname            : "syki66"

# 블로그 검색기능 설정
search                   : true # true로 해야 활성화됨
search_full_content      : true # 내용까지 검색되게 하려면 true

# 웹마스터 인증할때 쓰면된다.
google_site_verification :
naver_site_verification  :

# 저자 설정
author:
  name             : "syki66"
  avatar           : "https://avatars0.githubusercontent.com/u/59393359?s=460&v=4" # 사진
  bio              : "I am a person."
  location         : "Somewhere"
  email            : # 밑의 이메일과 이것중에 하나만 설정하면 된다.
  links:
    - label: "Email"
      icon: "fas fa-fw fa-envelope-square"
      url: mailto:test@gmail.com
    - label: "Website"
      icon: "fas fa-fw fa-link"
      url: "https://syki66.github.io/blog/"
# Site Footer
footer:
  links:
      # url:
    - label: "GitHub"
      icon: "fab fa-fw fa-github"
      url: "https://github.com/syki66"

# syntax 하이라이터 설정
highlighter: rouge

# 발췌 부분 뽑아내는 기준을 어떻게 정할건지
excerpt_separator: "\n\n"

# _posts와 _pages 불러오기
defaults:
  # _posts
  - scope:
      path: ""
      type: posts
    values:
      layout: single
      author_profile: true
      read_time: false
      comments: true
      share: false
      related: false
  # _pages
  - scope:
      path: ""
      type: pages
    values:
      layout: single
      author_profile: true
```

<br/>

---

# 3. `_pages` 디렉토리 생성

상단 네비게이션을 사용하기 위해서 루트 디렉토리에 `_pages` 디렉토리를 생성하고, `docs/_pages/` 경로로 들어가서 `404.md` `category-archive.md` `tag-archive.md` `year-archive.md` 파일을 루트폴더의 `_pages`로 가져온다.

<br/>

---

# 4. `navigation.yml` 수정

`_date` 디렉토리의 `navigation.yml`을 아래와 같이 수정한다.

```yml
main:
  - title: "About"
    url: /about/
  - title: "Category"
    url: /categories/
  - title: "Tag"
    url: /tags/
  - title: "Archive"
    url: /year-archive/
```

<br/>

---

# 5. 불필요한 파일 및 폴더 삭제

이제 아래 목록은 더이상 필요치 않기에 삭제해도 상관없다.

- .editorconfig

- .gitattributes

- .github

- /docs

- /test

- CHANGELOG.md

- minimal-mistakes-jekyll.gemspec

- README.md

- screenshot-layouts.png

- screenshot.png

<br/>

---

# 5. 포스트 개별 front matter 설정

기본적으로 아래와 같이 설정하면 되며, 본인의 취향에 맞게 추가 설정을 하면 되며, toc 아이콘 설정은 [fontawesome](https://fontawesome.com/icons?d=gallery&s=solid&m=free) 링크로 들어가서 원하는 아이콘으로 설정하면 된다.

```yml
layout: single

title: "포스트의 제목"
excerpt: "발췌부분 설정하면 이 글이 들어가고, 설정하지 않는다면 글의 첫 문단이 들어가게됨"

date: 2020-04-09 16:50:00 +0900
lastmod: 2020-04-09 16:50:00 +0900 # sitemap.xml에서 사용됨

author_profile: false # 왼쪽부분 프로필을 띄울건지

header:
  overlay_image: https://images.unsplash.com/photo-1501785888041-af3ef285b470?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1350&q=80
  overlay_filter: 0.5 # 투명도

categories: 
  - test post

tags: 
    - test
    - theme

# table of contents
toc: true # 오른쪽 부분에 목차를 자동 생성해준다.
toc_label: "table of content" # toc 이름 설정
toc_icon: "bars" # 아이콘 설정
toc_sticky: true # 마우스 스크롤과 함께 내려갈 것인지 설정
```

<br/>

---