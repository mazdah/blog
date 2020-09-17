---
layout: article
title: "TeXt theme 지킬 블로그 세부적인 커스터마이징"
subtitle: "customizing jekyll-TeXt-theme"
date: 2020-04-17 13:50:00 +0900
lastmod: 2020-09-15 17:00:00 +0900
tags: 
    - customize
    - jekyll
    - blog
    - theme
---

<br>

# 1. 하단의 "Powered by" 문구 제거

아래 디렉토리로 들어가 하단의 코드를 삭제한다.

> `_includes/footer.html`

```html
, Powered by <a title="Jekyll is a simple, blog-aware, static site generator." href="http://jekyllrb.com/">Jekyll</a> & <a title="TeXt is a super customizable Jekyll theme." href="https://github.com/kitian616/jekyll-TeXt-theme">TeXt Theme</a>.
```

<br>

---

# 2. 본문 헤더의 발췌문 제거 후 부제목 띄우기

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
  line-height: map-get($base, line-height-sm); // 높이 설정
  font-weight: map-get($base, font-weight-bold); // 인라인, 블록 코드의 폰트 굵기 변경 가능
  color: #ff006a; // 인라인 코드의 폰트 색상 변경
}

// 여기 부분을 추가해줘야 인라인 코드와 블록 코드의 색을 다르게 설정 할수 있다.
pre code {
  color: #eaeaea; // 블록 코드 색상 변경
}
```

<br>

---

# 5. 헤더 이미지 높이 변경

[Page - Article Header Overlay Background Image](https://tianqi.name/jekyll-TeXt-theme/page/article-header-overlay-background-image-immersive-translucent-header.html)와 같이 타이틀을 이미지 위에 띄우게 설정했을 경우, 창 하단부분까지 이미지가 확대되있지 않는데, 창의 높이만큼 이미지를 확대하고 싶다면 아래와 같이 하면된다.

<br>

아래 경로로 들어가서 하단의 코드를 찾고, 스타일 속성에 `height:100vh`을 추가해주면 딱 화면 높이만큼 이미지 크기가 맞춰진다.

> _layouts/page.html

```html
{% raw %}<div class="hero hero--dark overlay" style="{{ _header_style }} height:100vh;">{% endraw %}
```

<br>

---

# 6. 헤더 네비게이션 색 변경

[Page - Article Header Overlay Background Image](https://tianqi.name/jekyll-TeXt-theme/page/article-header-overlay-background-image-immersive-translucent-header.html)에서 보이는 것처럼 기본적으로 투명한 검정색 오버레이가 적용되어 있지만 아래에서 `rgba`값을 수정하면 색과 투명도를 변경할 수 있다.

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

# 7. 랜덤 배경화면 설정하기

[코드](https://syki66.github.io/blog/2020/02/18/random-header-background.html)를 복사해서 아래 경로에 디렉토리와 파일을 하나 추가해준다.

> _includes/scripts/customJS/randomBgImg.js

<br>

아래 코드에 random_BG 속성을 하나 추가해준다.

> _layouts/page.html

```html
<div class="hero hero--dark overlay random_BG" style="{{ _header_style }} height:100vh;">
```

<br>

이후 코드 바로 아래부분에 하단의 코드를 추가해주면 방문할때마다 배경화면 이미지가 랜덤으로 바뀌게 된다.

```html
{% raw %}<div class="hero hero--dark overlay random_BG" style="{{ _header_style }} height:100vh;">
<script>{%- include scripts/customJS/randomBgImg.js -%}</script>{% endraw %}
```

<br>

---

# 8. 스크롤바 커스터마이징

사이트의 세로 스크롤바, 코드블록의 가로 스크롤바가 테마에 비해 투박하게 기본값으로 설정되어있는데 이를 바꾸려면 아래 경로로 들어가서 하단의 코드를 추가 후 알맞게 수정해주면 된다.

> _sass/common/_reset.scss

```scss
::-webkit-scrollbar{
  width: 6px; // 세로 스크롤의 너비
  height: 3px; // 가로 스크롤의 너비
  background-color: #121212; // 스크롤의 기본 배경색상
  
}
::-webkit-scrollbar-thumb{
  border-radius: 3px; // 스크롤바 곡률
  background-color: #ff006a; // 스크롤바 색상
}

::-webkit-scrollbar-track:horizontal{
  background-color: #000000; // 가로 스크롤바 색상
}
```

<br>

---

# 9. 툴팁 효과 만들기

텍스트에 `hover`시 말풍선이 뜨게 하고 싶다면, 아래 경로들에 각 코드를 생성 또는 추가해주면 된다.

<br>

> _includes/scripts/customJS/tooltip.js

```js
document.querySelectorAll("tooltip").forEach(e => {
    e.style.color = (e.childNodes.length > 1) ? "#ff006a" : "rgba(255,255,255, 0.7)";
})

function setTooltip() {
    let innerWidth = document.querySelector(".tooltip").offsetWidth;
    let tooltip = document.querySelector(".tooltip");
    let style = getComputedStyle(tooltip);
    let marginLeft = parseInt(style.marginLeft);
    let width = innerWidth + marginLeft;
    
    document.querySelectorAll(".tooltip").forEach((element) => {
        element.querySelectorAll("tooltip").forEach((e, i) => {
            let text = e.querySelector("text");
            if (text != null){
                text.style.width = `${width / 2}px`;
                text.style.left = `${(width / 2) - marginLeft}px`;
                text.style.transform = `translateY(-${tooltip.childNodes[1].offsetHeight * i}px)`;
            }
        })
    })
};

setTooltip();

window.onresize = function () {
    setTooltip();
}
```

<br>

`page.html` 하단부에 아래 코드 추가

> _layouts/page.html

```html
{% raw %}<script>{%- include scripts/customJS/tooltip.js -%}</script>{% endraw %}
```

<br>

> _sass/common/_reset.scss

```scss
// 툴팁 관련 설정
tooltip {
  position: relative;
  color: #ff006a;
}

tooltip text {
  /* 툴팁 속성 */
  visibility: hidden;
  background-color: black;
  color: #eaeaea;
  opacity: 0;

  line-height: map-get($base, line-height-sm);
  border-radius: map-get($base, border-radius);
  padding: map-get($spacers, 3);
  
  /* 툴팁 위치 */
  position: absolute;
  z-index: 1;
  top: 0;
  
  /* 툴팁 효과 */
  transition: opacity 0.1s;
}

tooltip:hover text {
  visibility: visible;
  opacity: 1;
}

// 툴팁에 들어가는 이미지 설정
tooltip img{
  margin-top: map-get($spacers, 3);
  border: 1px solid $border-color-l;
  border-radius: map-get($base, border-radius);
  width: 100%;
}
```

<br>

이제 본문에서 아래 형식으로 글을 작성하게 되면 툴팁 효과가 적용되게 된다.

```html
<ul class="tooltip">
  <li><tooltip>설명
    <text>여기에 상세 설명을 적으면 말풍선 효과가 적용됨</text>
  </tooltip></li>

  <li><tooltip>그림
    <text>여기에 상세설명을 적고, 아래에 이미지를 추가해주면 이미지와 같이 말풍선에 들어가게됨
        <img src="주소 입력" />
    </text>
  </tooltip></li>
</ul>
```

<br>

---

# 본문 중앙정렬
# 후크 걸기

<br><br><br><br>