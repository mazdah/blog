---
layout: post
title: "지킬(jekyll)의 clean blog 테마에서 코드블럭 설정하기"
subtitle: "지킬(jekyll) 자동 줄바꿈 설정하기"
date: 2020-02-08 18:30:00 +0900
background: '/img/posts/01.jpg'
---

최근 깃허브를 이용해서 블로그를 시작하였는데, 지킬 무료 테마를 찾던중에 [Clean Blog Theme](http://jekyllthemes.org/themes/clean-blog/) 가 맘에 들어서 적용하게 되었습니다.

하지만 사이트를 동작시켜보니 코드블럭을 쓰더라도 자동으로 하이라이팅이 되지 않아서 구글링으로 찾아보면서 해결한 결과를 올려봅니다.

<img src="https://i.imgur.com/uTQxyHj.png" style="border-style: dashed; border-color: black;">

적용전

***
# 1. ruby 다운로드 및 설치
설치후 터미널 실행후 `rouge` 설치
```
> gem install rouge
```

***

# 2. 코드블럭 테마 선택
rougify help style 을 입력하고 테마 중 하나 선택
```
> rougify help style

available themes:
  base16, base16.dark, base16.light, base16.monokai, base16.monokai.dark, base16.monokai.light, base16.solarized, base16.solarized.dark, base16.solarized.light, bw, colorful, github, gruvbox, gruvbox.dark, gruvbox.light, igorpro, magritte, molokai, monokai, monokai.sublime, pastie, thankful_eyes, tulip
```

***

# 3. 테마, 경로, 파일이름 설정
```
> rougify style base16.dark > highligter.css
```
css 내용만 복붙할거라 저장경로는 어디로 하든 상관없음

***

# 4. 파일 수정
`assets/vendor/startbootstrap-clean-blog/scss/_bootstrap-overrides.scss`

위의 경로로 들어가서 _bootstrap-overrides.scss 내용 하단에 다운받은 css 코드를 전부 복붙한다.

***

# 5. _config.yml 에 코드 추가
```yml
highlighter: rouge
```
이후 사이트에 들어가보면 코드블럭이 적용되있는 것을 확인할 수 있다.

<img src="https://i.imgur.com/XWvWEMy.png" style="border-style: dashed; border-color: black;">

***

***

### 추가로 아래의 사진과 같이 코드블럭의 스크롤을 없애고 싶다면(자동줄바꿈 기능 추가)
<img src="https://i.imgur.com/KnUuPMY.png" style="border-style: dashed; border-color: gray;">

`_bootstrap-overrides.scss`에 추가로 밑의 코드를 넣어주면 된다.

```scss
pre.highlight {
  white-space: pre-wrap;
}
```

***

## 적용후

<img src="https://i.imgur.com/K23N8Lc.png" style="border-style: dashed; border-color: gray;">

***

## 참조 블로그

[https://moon9342.github.io/jekyll-rouge](https://moon9342.github.io/jekyll-rouge)

[https://renakim.github.io/2019/04/03/modify-highlighter/](https://renakim.github.io/2019/04/03/modify-highlighter/)




![](./1.png)