---
layout: article
title: "지킬 TeXt 테마 초기 설정하기"
subtitle: ""
date: 2020-04-17 13:50:00 +0900
lastmod: 2020-04-17 13:50:00 +0900
tags: 
    - customize
    - jekyll
    - blog
    - theme
---

<br>

원래 minimal mistake theme 을 사용하려고 해서 적용했는데 막상 적용하고 나니까 디자인이 아쉬워서 세부적으로 커스터마이징 하다가 보니 맘에 안드는 곳이 한둘이 아니라서 굳이 이렇게까지 해야되나 급 현타가 왔고, 결국 다른 완성도 높은 테마를 찾아봤는데, 마침 TeXt 라는 테마를 찾아서 적용해보았다.

<br>

---

# 1. TeXt 테마 다운로드

[TeXt 공식문서](https://tianqi.name/jekyll-TeXt-theme/docs/en/quick-start)에 들어가보면 다양한 방법으로 지원하는데 `ruby gem`, `git clone`, `zip파일` 등 자신이 편리한 방법으로 하면된다.

<br>

---

# 2. 로컬 개발환경 구성

`docker` 또는 `ruby`를 사용해서 로컬 서버를 구성할 수 있으며, 아래 방법은 루비를 이용하는 방법이다. [루비를 설치](https://syki66.github.io/blog/2020/02/06/jekyll-local-server.html)하고 아래 명령어를 입력하면 `127.0.0.1:4000`의 주소에 서버가 생성된다.

```
bundle exec jekyll serve
```

로컬서버에서만 보이는 초안 작성을 하고 싶으면 `_drafts` 디렉토리 생성후 여기에 마크다운 파일을 작성해주면 된다. *(`--drafts` 옵션을 넣어주어야 보임)*

<br>

---

# 3. `_config.yml` 수정

본인의 기호대로 아래 설정들을 채워주면 되지만, 만약 댓글 공급자를 disqus로 설정할 경우, 반드시 `key: anything`이라는 키워드를 넣어주어야만 각 포스트에서 디스커스가 활성화된다.

```yml
text_skin: "dark" # 사이트 테마 "default" (default), "dark", "forest", "ocean", "chocolate", "orange"
highlight_theme: "tomorrow-night-bright" # 코드블럭 테마 "default" (default), "tomorrow", "tomorrow-night", "tomorrow-night-eighties", "tomorrow-night-blue", "tomorrow-night-bright"
url     : "https://syki66.github.io"
baseurl : "/blog" # baseurl이 존재하면 적기
title   : "syki blog" # 사이트 이름
description: > # 사이트 상세정보
  셀프 참고하는 블로그

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
      layout: article # 포스트의 레이아웃, article로 설정해야됨
      sharing: false # 공유 표시
      license: false # 라이센스 표시
      aside:
        toc: true # 사이드 메뉴 활성화
      show_edit_on_github: false
      show_subscribe: true # feed.xml 하단부에 띄울건지
      key: anything # 반드시 이 구문을 넣어야 disqus 댓글이 각 post 마다 실행됨
      mode: immersive # 백그라운드 이미지 위에 헤더와 타이틀 올리기
      header:
        theme: dark # dark는 헤더의 배경을 어둡게 하고 글씨를 밝게함. light는 반대
      article_header:
        type: overlay # 포스트 내부에서 헤더 오버레이 적용여부
        theme: dark
        background_image: # 포스트 헤더 배경이미지 경로 및 그라데이션 설정
          src: https://user-images.githubusercontent.com/59393359/74720914-e4b7e980-5279-11ea-9532-c262caf64f00.jpg
          gradient: 'linear-gradient(rgba(0, 0, 0, .3), rgba(0, 0, 0, .0))'
```

<br>

---

# 4. 로고 및 favicon 변경하기

favicon 변경은 [RealFaviconGenerator](https://realfavicongenerator.net/)로 들어가서 favicon 및 기타 파일들을 다운로드 받고, `/assets` 에다가 덮어씌우고 `favicon.ico` 파일은 루트폴더에도 추가하면되며

로고 변경은 `/assets/safari-pinned-tab.svg`의 svg 태그를 복사해서 `assets/images/logo/logo.svg`에 붙여넣으면 된다.

<br>

---

# 5. 세부 커스터마이징

좀 더 세부적인 커스터마이징 하려면 [여기를 클릭](https://syki66.github.io/blog/2020/04/17/TeXt-theme-detailed-customization.html)

<br><br><br><br>