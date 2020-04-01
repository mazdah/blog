---
layout: post
title: "지킬(jekyll)의 clean blog 테마에서 코드블럭, 하이라이터 설정하기"
subtitle: "+ 지킬(jekyll) 코드블럭 자동 줄바꿈 설정하기"
date: 2020-02-08 18:30:00 +0900
lastmod: 2020-04-02 00:30:00 +0900
background: '/img/posts/03.jpg'
---

최근 깃허브를 이용해서 블로그를 시작하였는데, 지킬 무료 테마를 찾던중에 [Clean Blog Theme](http://jekyllthemes.org/themes/clean-blog/) 가 맘에 들어서 적용했다.

하지만 사이트를 동작시켜보니 코드블럭을 쓰더라도 자동으로 하이라이팅이 되지 않는 문제가 있어서 구글링을 통해 해결해 보았다.

---

#### 적용전

<img src="https://user-images.githubusercontent.com/59393359/74085994-25697300-4ac2-11ea-832e-44d74969b154.PNG" style="border-style: dashed; border-color: black;">

<br/>

***

# 1. ruby 다운로드 및 설치

설치후 터미널 실행후 `rouge` 설치

```
> gem install rouge
```

<br/>

***

# 2. 코드블럭 테마 선택

rougify help style 을 입력하고 테마 중 하나 선택

```
> rougify help style

available themes:
  base16, base16.dark, base16.light, base16.monokai, base16.monokai.dark, base16.monokai.light, base16.solarized, base16.solarized.dark, base16.solarized.light, bw, colorful, github, gruvbox, gruvbox.dark, gruvbox.light, igorpro, magritte, molokai, monokai, monokai.sublime, pastie, thankful_eyes, tulip
```

<br/>

***

# 3. 테마, 경로, 파일이름 설정

css 내용만 복붙할거라 저장경로는 어디로 하든 상관 없다.

```
> rougify style base16.dark > highligter.css
```

<br/>

***

# 4. 파일 수정

```
> assets/vendor/startbootstrap-clean-blog/scss/_bootstrap-overrides.scss
```

위의 경로로 들어가서 `_bootstrap-overrides.scss` 파일 하단에, 다운받은 css 코드를 전부 복붙한다.

<br/>

***

# 5. _config.yml 에 코드 추가

```yml
highlighter: rouge
```

<br/>

---

이후 사이트에 들어가보면 하이라이터가 적용되있는 것을 확인할 수 있다.

---

#### 적용후

<img src="https://user-images.githubusercontent.com/59393359/74085888-13d39b80-4ac1-11ea-8ac1-c662c9edb3f7.PNG" style="border-style: dashed; border-color: black;">

<br/>

***

### 추가1 : 코드블럭의 스크롤을 없애고 자동 줄바꿈 기능을 넣고 싶다면

<img src="https://user-images.githubusercontent.com/59393359/74085871-ec7cce80-4ac0-11ea-8d0f-7fc9ea363121.PNG" style="border-style: dashed; border-color: gray;">

---

`_bootstrap-overrides.scss`에 추가로 아래의 코드를 넣어주면 된다.

```scss
pre.highlight {
  white-space: pre-wrap;
}
```

<br/>

***

#### 줄바꿈 적용후

<img src="https://user-images.githubusercontent.com/59393359/74085840-a293e880-4ac0-11ea-9864-efe7601dfdc3.PNG" style="border-style: dashed; border-color: gray;">

<br/>

***

### 추가2 : xml, html 등에서 코드블럭 익스케이프

그냥 구문을 작성하다 보면 코드블럭에서 그 구문이 실행되 버리는 경우가 있는데 그럴땐 아래 방법으로 이스케이프 구문을 사용하면 된다.

<p style="color:#e83e9b">
  &emsp;&#123;&#37; raw &#37;&#125; ~ &emsp;&#123;&#37; endraw 	&#37;&#125;
</p>

<div style="background-color:#272822; color:white; padding:5px">
  &emsp;&#123;&#37; raw &#37;&#125;<br />
  &emsp;&emsp;&#60;div id="post-disqus" class="container"&#62;<br />
  &emsp;&emsp;&emsp;&#123;&#37; include disqus.html &#37;&#125;<br />
  &emsp;&emsp;&#60;/div&#62;<br />
  &emsp;&#123;&#37; endraw 	&#37;&#125;<br />
</div>

코드블럭 구문으로 코드를 덮어주면 하이라이트도 가능하다.

<br />

---

## 참고 링크

[https://moon9342.github.io/jekyll-rouge](https://moon9342.github.io/jekyll-rouge)

[https://renakim.github.io/2019/04/03/modify-highlighter/](https://renakim.github.io/2019/04/03/modify-highlighter/)