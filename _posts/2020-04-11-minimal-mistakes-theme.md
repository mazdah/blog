---
layout: single
title: "minimal mistake theme 지킬 블로그 초기 설정하기"
date: 2020-04-09 16:50:00 +0900
lastmod: 2020-04-09 16:50:00 +0900

author_profile: false

header:
  overlay_image: https://images.unsplash.com/photo-1501785888041-af3ef285b470?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1350&q=80
  overlay_filter: 0.5 # same as adding an opacity of 0.5 to a black background

categories: 
  - raspberry pi

tags: 
    - jekyll
    - github

excerpt: ""
---

clean-blog 테마가 질려서 가장 인기있고, 커스터마이징 및 기타 관리가 쉬운 minimal-mistakes 테마로 바꾸게 됨

# 1. 테마 가져오기

깃허브의 `Fork`를 이용하거나, 깃의 `clone`를 이용하거나, 또는 정식 릴리즈가 된 압축파일을 다운로드 받는다.

<br />

---

# 2. `_config.yml` 수정

`_config.yml`에 들어가서 수정한다.

```yml
minimal_mistakes_skin    : "default"
locale                   : "en-US"
title                    : "syki blog"
subtitle                 : # site tagline that appears below site title in masthead
name                     : "syki66"
description              : "셀프 참조 블로그"
url                      : "https://syki66.github.io" # the base hostname & protocol for your site e.g. "https://mmistakes.github.io"
baseurl                  : "/blog" # the subpath of your site, e.g. "/blog"
repository               : "syki66/blog"
teaser                   : # path of fallback teaser image, e.g. "/assets/images/500x300.png"
logo                     : # path of logo image to display in the masthead, e.g. "/assets/images/88x88.png"


comments:
  provider               : "disqus" # false (default), "disqus", "discourse", "facebook", "staticman", "staticman_v2", "utterances", "custom"
  disqus:
    shortname            : "syki66"


search                   : true # true, false (default)
search_full_content      : true

# SEO Related
google_site_verification :
bing_site_verification   :
yandex_site_verification :
naver_site_verification  :

author:
  name             : "syki66"
  avatar           : "https://avatars0.githubusercontent.com/u/59393359?s=460&v=4" # path of avatar image, e.g. "/assets/images/bio-photo.jpg"
  bio              : "I am a person."
  location         : "Somewhere"
  email            : # "syeonki66@gmail.com"
  links:
    - label: "Email"
      icon: "fas fa-fw fa-envelope-square"
      url: mailto:syeonki66@gmail.com
    - label: "Website"
      icon: "fas fa-fw fa-link"
      url: "https://syki66.github.io/blog/"
# Site Footer
footer:
  links:
    - label: "Twitter"
      icon: "fab fa-fw fa-twitter-square"
      # url:
    - label: "Facebook"
      icon: "fab fa-fw fa-facebook-square"
      # url:
    - label: "GitHub"
      icon: "fab fa-fw fa-github"
      url: "https://github.com/syki66"

highlighter: rouge

excerpt_separator: "\n\n"

# Defaults
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

네비게이션을 사용하기 위해서 루트 디렉토리에 `_pages` 디렉토리를 생성하고, `docs/_pages/` 경로로 들어가서 `404.md` `category-archive.md` `tag-archive.md` `year-archive.md` 파일을 루트폴더의 `_pages`로 가져온다.

<br/>

---

# 4. 

`_date` 디렉토리의 `navigation.yml`

```yml
# main links
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

이제 아래 목록은 더이상 필요치 않기에 삭제해도 무관하다.

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


# 5. 포스트 개별 front matter 설정

```yml

layout: single
title: "라즈베리파이에서 윈도우10으로 원격 데스크톱 연결하기 (xfreerdp)"
date: 2020-04-09 16:50:00 +0900
lastmod: 2020-04-09 16:50:00 +0900

show_overlay_excerpt: false
show_excerpts: false
show_overlay_excerpt: false
header:
  overlay_image: https://images.unsplash.com/photo-1501785888041-af3ef285b470?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1350&q=80
  overlay_filter: 0.5 # same as adding an opacity of 0.5 to a black background

categories: 
  - raspberry pi

tags: 
    - rdp
    - xfree

toc: true
toc_sticky: true
author_profile: false
```