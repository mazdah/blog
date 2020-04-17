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

`_includes/footer.html`에서 하단에 아래코드를 삭제한다.

```html
, Powered by <a title="Jekyll is a simple, blog-aware, static site generator." href="http://jekyllrb.com/">Jekyll</a> & <a title="TeXt is a super customizable Jekyll theme." href="https://github.com/kitian616/jekyll-TeXt-theme">TeXt Theme</a>.
```

<br/>

---

# 2. 배경 헤더의 발췌문 제거 후 부제목으로 변경

`_layouts/page.html`에서 아래 코드 중에 `page.excerpt` 부분을 `page.subtitle`로 변경하기

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

# 3. 각종 색 변경

아래의 디렉토리로 들어가면 각 테마별로 색을 정해져있는데 여기서 기호에 맞게 알아서 변경하면된다.

> _sass/skins

```scss
$main-color-1: #ff006a; // 예를들어 dark 스킨을 사용하고 있으면 `_dark.scss`로 들어가서 아래 코드의 색깔 부분을 변경하게 되면 title-hover, read more, archive-tag, 블록지정 등 대표 색을 변경할수 있다.
$text-color-theme-dark-l:  #ff006a; // 마크다운 가로선 색변경
$mail-color: #000; //footer (메일) 로고 색변경
$text-background-color: #000; // <code> 태그의 배경색이 바뀌게됨
```

<br/>

---

# 4. 하이라이터 변경

기본적인 설정으로는 마크다운에서 헤더를 적용해도 크기가 그대로이며, 코드 태그는 같은 하얀색 글씨라서 가시성이 떨어지는데 이를 수정하려면 아래와 같이 하면 된다. 

> _sass/common/_reset.scss

```scss
code {
  font-size: map-get($base, font-size-xs); // 이 라인 삭제하면 <code> 태그에서 마크다운의 헤더 크기가 정상적으로 적용됨
  line-height: map-get($base, line-height-sm);
  font-weight: map-get($base, font-weight-bold); // 이 라인 추가시 <code> 태그의 폰트 굵기 바꿀수 있음
  color: #ff006a; // <code> 태그의 폰트 색상
}
```