---
layout: article
title: "지킬 블로그 배경화면 랜덤하게 변경하기"
subtitle: "using template language"
date: 2020-02-18 16:30:00 +0900
lastmod: 2020-02-18 16:30:00 +0900
tags: 
    - random background
    - template language
    - customize
    - jekyll
    - blog
---

<br>

지킬을 이용하여 블로그 포스트 작성할때, 매번 배경화면을 뭘로 설정할까 고민하기가 귀찮아져서 포스트의 배경화면이 랜덤으로 뜰수 있게 블로그를 커스터마이징 해보았다. <a href="#무료-배경화면-사이트">(무료 배경화면 사이트)</a>

<br>

---

# 1. `post.html` 수정

자바스크립트 파일을 따로 관리하기 위해서 `<script>`와 경로 추가하고 header 태그의 class에 `random_BG` 추가 *(포스트에 배경화면이 없다면 스크립트가 실행되게됨)*

> `_layouts/post.html`

```html
{% raw %}{% if page.background %}
<header class="masthead" style="background-image: url('{{ page.background | prepend: site.baseurl | replace: '//', '/' }}')">
   {% else %}
   <header class="masthead random_BG">
   <script src="{{'/assets/customJS/randomBgImg.js' | relative_url }}"></script>
    {% endif %}{% endraw %}
```

<br>

---

# 2. 자바스크립트 코드 수정

위에 설정한 경로에 디렉토리와 파일을 생성해 준뒤, `querySelector`를 이용하여 `"random_BG"` 라는 클래스를 사용하는 첫 번째 요소를 가져온다.

```js
const bg = document.querySelector(".random_BG");
```

<br>

style 변경하기

> 특정 색상을 원할때
```js
bg.style.backgroundColor="red"
```

> 이미지 주소를 사용할때는 `'url(이미지주소)'` 형식으로 사용하면 된다.
```js
bg.style.backgroundImage = 'url("https://cdn.pixabay.com/photo/2013/08/28/12/03/plumage-176723_960_720.jpg")';
```

<br>

랜덤 배경화면 만들기

> 우선 주소값을 넣을 리스트를 하나 만든다.

```js
const bg = document.querySelector(".random_BG");

const bgList = [
    "https://user-images.githubusercontent.com/59393359/74718667-0adb8a80-5276-11ea-8bc3-0e36c67cf28a.jpg",
    "https://user-images.githubusercontent.com/59393359/74718765-30689400-5276-11ea-8a91-dd7ce797074b.jpg",
    "https://user-images.githubusercontent.com/59393359/74718795-3f4f4680-5276-11ea-9f52-58bb99cb2db0.jpg"
];
```

<br>

> 이후 리스트 크기보다 작은 크기의 랜덤 정수를 생성하는 `randNum` 변수를 하나 만들고, `backtick`, `${}`를 이용해서 url안에 리스트를 넣어주게 되면 해당 포스트에 들어갈때 마다 배경화면이 바뀌게 된다.

```js
const randNum = Math.floor(Math.random() * bgList.length);

bg.style.backgroundImage = `url(${bgList[randNum]})`;
```

<br>

전체코드

> /assets/customJS/randomBgImg.js

```js
const bg = document.querySelector(".random_BG");

const bgList = [
    "https://user-images.githubusercontent.com/59393359/74718667-0adb8a80-5276-11ea-8bc3-0e36c67cf28a.jpg",
    "https://user-images.githubusercontent.com/59393359/74718765-30689400-5276-11ea-8a91-dd7ce797074b.jpg",
    "https://user-images.githubusercontent.com/59393359/74718795-3f4f4680-5276-11ea-9f52-58bb99cb2db0.jpg",
    "https://user-images.githubusercontent.com/59393359/74720865-cb16a200-5279-11ea-9318-05e4f75b1106.jpg",
    "https://user-images.githubusercontent.com/59393359/74720904-e2ee2600-5279-11ea-9440-3b3eb9904c22.jpg",
    "https://user-images.githubusercontent.com/59393359/74720910-e41f5300-5279-11ea-9c63-ff84698e3c7f.jpg",
    "https://user-images.githubusercontent.com/59393359/74720914-e4b7e980-5279-11ea-9532-c262caf64f00.jpg"
];

const randNum = Math.floor(Math.random() * bgList.length);

bg.style.backgroundImage = `url(${bgList[randNum]})`;
```

<br>

이미지를 더 추가하고 싶다면 `bgList`에 주소값만 계속 추가해주면 자동으로 적용된다.

<br>

---

# 3. 결과 (새로고침)

![changeBG.gif](https://user-images.githubusercontent.com/59393359/74720122-9d7d2900-5278-11ea-9683-be4098a74a21.gif){:.border.rounded}

<br>

---

## 무료 배경화면 사이트

- [pixabay.com](https://pixabay.com/ko/)
- [pexels.com](https://www.pexels.com/)
- [unsplash.com](https://unsplash.com/)

<br><br><br><br>