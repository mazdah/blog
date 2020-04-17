---
layout: article
title: "texttheme"
date: 2020-04-17 13:50:00 +0900
lastmod: 2020-04-17 13:50:00 +0900
tags: 
    - blog
    - theme
    - customize
    - jekyll
    - text
---

원래 minimal mistake theme 을 사용하려고 해서 적용했는데 막상 적용하고 나니까 디자인이 아쉬워서 세부적으로 커스터마이징 하다가 굳이 이렇게까지 해야되나 급 현타가 와서 다른 테마 그냥 찾아봤는데, 마침 TeXt 라는 테마를 찾아서 적용해보았다.

<br/>

---

# 1. TeXt 테마 다운로드

[TeXt 공식문서](https://tianqi.name/jekyll-TeXt-theme/docs/en/quick-start)에 들어가보면 다양한 방법으로 지원하는데. clone, zip파일 다운로드 등 자신이 편리한 방법으로 하면된다. 

<br/>

---

# 2. 로컬 개발환경 구성

docker를 사용하거나 루비와 지킬을 설치하고 아래 명령어를 입력하면 127.0.0.1:4000 로컬 구성 완료됨

참고

`bundle exec jekyll serve` 하면 끝

<br/>

---

# 3. `_config.yml` 수정

본인의 기호대로 아래 설정들을 채워주면 되지만, 만약 댓글 공급자를 disqus로 설정할 경우, 반드시 `key: anything`이라는 키워드를 넣어주어야 각 article에 표시된다.

```yml
text_skin: "dark" # 사이트 테마 "default" (default), "dark", "forest", "ocean", "chocolate", "orange"
highlight_theme: "tomorrow-night-bright" # 코드블럭 테마 "default" (default), "tomorrow", "tomorrow-night", "tomorrow-night-eighties", "tomorrow-night-blue", "tomorrow-night-bright"
url     : "https://syki66.github.io"
baseurl : "/blog" # baseurl이 존재하면 적기
title   : "syki blog" # 사이트 이름
description: > # 사이트 상세정보
  혼자 참고하는 블로그

# 저자 정보를 알맞게 쓰면됨
author:
  name      : "syki66"
  url       : "https://syki66.github.io/blog"
  avatar    : "https://avatars0.githubusercontent.com/u/59393359?s=460&v=4"
  bio       : I am an person.
  email     : "abcdefg@kakao.com"
  github    : "syki66"


# => 블로그의 깃허브 레포지토리 적기
repository: syki66/blog
repository_tree: master

# 자동으로 본문 발췌시 구분점을 어떤것으로 할지 정하기
excerpt_separator: \n\n

# 사이드 네비게이션에 넣을 태그 선택
toc:
  selectors: "h1,h2"

paginate: 8 # 한 페이지에 보여줄 article 개수

comments:
  provider: "disqus" # 댓글 공급자 선택하기, "disqus", "gitalk", "valine", "custom"

  disqus:
    shortname: "syki66"

# 기본 article 레이아웃 설정 (자신의 기호에 맞게 넣으면됨)
defaults:
  - scope:
      path: ""
      type: posts
    values:
      layout: article
      sharing: false
      license: false
      aside:
        toc: true
      show_edit_on_github: false
      show_subscribe: true
      key: anything # 반드시 이 구문을 넣어야 disqus 댓글이 각 article 마다 실행됨
      mode: immersive 
      header:
        theme: dark
      article_header:
        type: overlay
        theme: dark
        background_image:
          src: https://user-images.githubusercontent.com/59393359/74720914-e4b7e980-5279-11ea-9532-c262caf64f00.jpg
          gradient: 'linear-gradient(rgba(0, 0, 0, .3), rgba(0, 0, 0, .0))'
```

<br/>

---

# 4. 로고 및 favicon 변경하기

favicon 변경은 [RealFaviconGenerator](https://realfavicongenerator.net/)로 들어가서 favicon 및 기타 파일들을 다운로드 받고, `/assets` 에다가 덮어씌우고 `favicon.ico` 파일은 루트폴더에도 추가하면되며

로고 변경은 `/assets/safari-pinned-tab.svg`의 svg 태그를 복사해서 `assets/images/logo/logo.svg`에 붙여넣으면 된다.

<br/>

---

세부적인 커스터마이징 하려면