---
layout: article
title: "지킬 TeXt 테마 세부 커스터마이징 하기"
subtitle: "커스터마이징"
date: 2020-04-17 13:50:00 +0900
lastmod: 2020-04-18 23:20:00 +0900
tags: 
    - blog
    - theme
    - customize
    - jekyll
---

<br>

# 1. 하단의 "Powered by" 제거

아래 디렉토리로 들어가 하단의 코드를 삭제한다.

> `_includes/footer.html`

```html
, Powered by <a title="Jekyll is a simple, blog-aware, static site generator." href="http://jekyllrb.com/">Jekyll</a> & <a title="TeXt is a super customizable Jekyll theme." href="https://github.com/kitian616/jekyll-TeXt-theme">TeXt Theme</a>.
```

<br>

---

# 2. 본문 헤더의 발췌 제거 후 부제목 띄우기

`_layouts/page.html`로 들어가서 두 줄 변경

<br>

> 변경전

```html
{% raw %}{%- if page.excerpt -%}
  <p class="overlay__excerpt">{{ page.excerpt | strip_html | strip_newlines | strip | truncate: _article_header_excerpt_truncate }}</p>
{%- endif -%}{% endraw %}
```

<br>

> 변경후

```html
{% raw %}{%- if page.subtitle -%}
  <p class="overlay__excerpt">{{ page.subtitle }}</p>
{%- endif -%}{% endraw %}
```

<br>

---

# 3. 각 테마색 변경

아래의 디렉토리로 들어가면 각 기능별로 색을 정해놓았는데 여기서 기호에 맞게 알아서 변경하면된다.

> _sass/skins/_dark.scss

```scss
$main-color-1: #ff006a; // title-hover, read more, archive-tag, 블록지정색 등 대표색 변경
$text-color-theme-dark-l:  #ff006a; // 마크다운 가로선 색변경
$mail-color: #000; //footer 부분 (메일) 로고 색변경
$text-background-color: #000; // 인라인(inline) 코드의 배경색 변경
```

<br>

---

# 4. 하이라이터 변경

기본적인 설정으로는 마크다운에서 인라인 코드를 적용한다면 마크다운에서 `#`을 적용해도 폰트 크기가 그대로이고, 색도 하얀색 글씨라서 가시성이 떨어지는데 이를 수정하려면 아래와 같이 하면 된다. 

> _sass/common/_reset.scss

```scss
code {
  font-size: map-get($base, font-size-xs); // 이 라인 삭제하면 인라인 코드에서 마크다운의 헤더 크기가 정상적으로 적용됨
  line-height: map-get($base, line-height-sm);
  font-weight: map-get($base, font-weight-bold); // 인라인, 블록 코드의 폰트 굵기 변경 가능
  color: #ff006a; // 인라인 코드의 폰트 색상 변경
}
```

<br>

---

# 5. 헤더 이미지 높이 변경

[Page - Article Header Overlay Background Image](https://tianqi.name/jekyll-TeXt-theme/page/article-header-overlay-background-image-immersive-translucent-header.html)와 같이 타이틀을 이미지 위에 띄우게 설정했을 경우, 창 하단부분까지 이미지가 확대되있지 않는데, 창의 높이만큼 이미지를 확대하고 싶다면 아래와 같이 하면된다.

> _layouts/page.html

아래 코드를 찾아서 스타일 속성에 `height:100vh`을 추가해주면 딱 화면 높이만큼 이미지 크기가 늘어나게 된다.

```html
{% raw %}<div class="hero hero--dark overlay" style="{{ _header_style }} height:100vh;">{% endraw %}
```

<br>

---

# 6. 헤더 네비게이션 색 변경

[Page - Article Header Overlay Background Image](https://tianqi.name/jekyll-TeXt-theme/page/article-header-overlay-background-image-immersive-translucent-header.html)에서 보이는 것처럼 기본적으로 투명한 검정색이 적용되어 있지만 아래에서 `rgba`값을 수정하면 색과 투명도를 변경할 수 있다.

> _sass/components/_header.scss

```scss
.header--dark {
  @extend .text--dark;
  background: rgba(#202020, .15); // 여기 부분을 수정하면됨
  .navigation__item--active {
    &::after {
      @include split-line(bottom, 4px, $text-color-theme-dark);
    }
  }
}
```

<br>

---

# 7. 랜덤 배경화면

[코드](https://syki66.github.io/blog/2020/02/18/random-header-background.html)를 복사해서 아래 경로에 디렉토리와 파일을 하나 추가해준다.

> _includes/scripts/customJS/randomBgImg.js

<br>

아래 코드에 random_BG 속성을 하나 추가해준다.

> _layouts/page.html

```html
<div class="hero hero--dark overlay random_BG" style="{{ _header_style }} height:100vh;">
```

<br>

이후 `page.html` 하단부에 아래 코드를 추가해주면 방문할때마다 배경화면 이미지가 변경되게 된다.

```html
{% raw %}<script>{%- include scripts/customJS/randomBgImg.js -%}</script>{% endraw %}
```

<br>

---

# 코드블럭 자동줄바꿈 적용하기
# 본문 중앙정렬