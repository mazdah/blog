---
layout: article
title: "깃허브 지킬 블로그 포스트 배경화면 랜덤하게 변경하기"
subtitle: "깃허브 지킬(github, jekyll) 블로그 커스터마이징"
date: 2020-02-18 16:30:00 +0900
lastmod: 2020-02-18 16:30:00 +0900
author_profile: false
---

지킬을 이용하여 블로그 포스트 작성할때, 매번 배경화면을 뭘로 설정할까 고민하기가 귀찮아져서 포스트의 배경화면이 랜덤으로 뜰수 있게 블로그를 커스터마이징 해보았다.

<br/>

---

# 1. `post.html` 수정

먼저 `_layouts/post.html`에 들어가고

js파일을 따로 관리하기 위해서 `<script>`와 경로 추가

자바스크립트로 태그의 style을 바꾸기기 위해서 header 태그의 class에 `random_BG` 추가

<div style="background-color:#272822; padding:5px; color:#f1ffff; font-size:18px;">
&#123;&#37; if page.background &#37;&#125;<br/>
&#60;header class="masthead" style="background-image: url('&#123;&#123; page.background | prepend: site.baseurl | replace: '//', '/' &#125;&#125;')"&#62;<br/>
&#160;&#160;  &#123;&#37; else &#37;&#125;<br/>
&#160;&#160;  &#60;header class="masthead <span style="color:red">random_BG</span>"&#62;<br/>
<span style="color:red">&#160;&#160;  &#60;script src="&#123;&#123;'/assets/customJS/randomBgImg.js' | relative_url &#125;&#125;"&#62;&#60;/script&#62;</span>
</div>

else문에 스크립트를 넣음으로써, 개별 포스트 상단 헤더(`yml`)에 `background` 항목이 없다면 스크립트를 실행하도록 했다.

#### 즉, 최종적으로 개별 포스트에서 따로 배경화면을 설정하지 않는다면, 랜덤한 배경화면이 자동으로 적용된다.

<br/>

---

# 2. `javascript` 파일 수정

우선은 `querySelector`를 이용하여 `"random_BG"` 라는 클래스를 사용하는 첫 번째 요소를 가져온다.

```js
const bg = document.querySelector(".random_BG");
```

---

그리고 가져온 요소의 style 변경

- 특정 색상을 원할때
```js
bg.style.backgroundColor="red"
```

- 이미지 주소를 사용할때는 `'url(이미지주소)'` 형식으로 사용하면 된다.
```js
bg.style.backgroundImage = 'url("https://cdn.pixabay.com/photo/2013/08/28/12/03/plumage-176723_960_720.jpg")';
```

<br/>

---

# 3. 랜덤 배경화면 만들기

- 우선 주소값을 넣을 리스트를 하나 만든다.

```js
const bg = document.querySelector(".random_BG");

const bgList = [
    "https://user-images.githubusercontent.com/59393359/74718667-0adb8a80-5276-11ea-8bc3-0e36c67cf28a.jpg",
    "https://user-images.githubusercontent.com/59393359/74718765-30689400-5276-11ea-8a91-dd7ce797074b.jpg",
    "https://user-images.githubusercontent.com/59393359/74718795-3f4f4680-5276-11ea-9f52-58bb99cb2db0.jpg"
];
```

---

- 이후 리스트 크기보다 작은 크기의 랜덤 정수를 생성하는 `randNum` 변수를 하나 만들고, `backtick`, `${}`를 이용해서 url안에 리스트를 넣어주게 되면 해당 포스트에 들어갈때 마다 배경화면이 바뀌게 된다.

```js
const randNum = Math.floor(Math.random() * bgList.length);

bg.style.backgroundImage = `url(${bgList[randNum]})`;
```

<br/>

---

# 결과 (새로고침)

![changeBG.gif](https://user-images.githubusercontent.com/59393359/74720122-9d7d2900-5278-11ea-9683-be4098a74a21.gif)

<br/>

---

이미지를 더 추가하고 싶다면 `bgList`에 주소값만 계속 추가해주면 된다.

<br/>

---

## 무료 배경화면 사이트

- [pixabay.com](https://pixabay.com/ko/)
- [pexels.com](https://www.pexels.com/)
- [unsplash.com](https://unsplash.com/)

<br/>