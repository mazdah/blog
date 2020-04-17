---
layout: article
title: "지킬 TeXt 테마 세부 커스터마이징 하기"
subtitle: "커스터마이징"
date: 2020-04-17 13:50:00 +0900
lastmod: 2020-04-17 13:50:00 +0900
tags: 
    - blog
    - theme
    - customize
    - jekyll
    - text
mode: immersive
header:
  theme: dark
article_header:
  type: overlay
  theme: dark
  background_image:
    src: https://user-images.githubusercontent.com/59393359/74718667-0adb8a80-5276-11ea-8bc3-0e36c67cf28a.jpg
    gradient: 'linear-gradient(rgba(0, 0, 0, .3), rgba(0, 0, 0, .0))'
---

# 1. 홈페이지 하단의 Powered by 글귀 제거

아래 디렉토리로 들어가 아래코드를 삭제한다.

> `_includes/footer.html`

```html
, Powered by <a title="Jekyll is a simple, blog-aware, static site generator." href="http://jekyllrb.com/">Jekyll</a> & <a title="TeXt is a super customizable Jekyll theme." href="https://github.com/kitian616/jekyll-TeXt-theme">TeXt Theme</a>.
```

<br/>

---

# 2. 본문 헤더의 발췌 제거 후 부제목 띄우기

`_layouts/page.html`로 들어가서 두 줄 변경

> 변경전

```html
{% raw %}
{%- if page.excerpt -%}
  <p class="overlay__excerpt">{{ page.excerpt | strip_html | strip_newlines | strip | truncate: _article_header_excerpt_truncate }}</p>
{%- endif -%}
{% endraw %}
```

> 변경후

```html
{% raw %}
{%- if page.subtitle -%}
  <p class="overlay__excerpt">{{ page.subtitle }}</p>
{%- endif -%}
{% endraw %}
```

<br/>

---

# 3. 각 테마색 변경

아래의 디렉토리로 들어가면 각 기능별로 색을 정해놓았는데 여기서 기호에 맞게 알아서 변경하면된다.

> _sass/skins/_dark.scss

```scss
$main-color-1: #ff006a; // title-hover, read more, archive-tag, 블록지정 등 대표색 변경
$text-color-theme-dark-l:  #ff006a; // 마크다운 가로선 색변경
$mail-color: #000; //footer 부분 (메일) 로고 색변경
$text-background-color: #000; // 인라인(inline) 코드의 배경색 변경
```

<br/>

---

# 4. 하이라이터 변경

기본적인 설정으로는 마크다운에서 헤더를 적용해도 크기가 그대로이며, 코드 태그는 같은 하얀색 글씨라서 가시성이 떨어지는데 이를 수정하려면 아래와 같이 하면 된다. 

> _sass/common/_reset.scss

```scss
code {
  font-size: map-get($base, font-size-xs); // 이 라인 삭제하면 인라인 코드에서 마크다운의 헤더 크기가 정상적으로 적용됨
  line-height: map-get($base, line-height-sm);
  font-weight: map-get($base, font-weight-bold); // 인라인, 블록 코드의 폰트 굵기 변경 가능
  color: #ff006a; // 인라인 코드의 폰트 색상 변경
}
```

# 헤더 이미지 높이 변경
# 코드블럭 자동줄바꿈 적용하기
# 본문 중앙정렬