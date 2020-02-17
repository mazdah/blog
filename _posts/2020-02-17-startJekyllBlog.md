---
layout: post
title: "깃허브 블로그 지킬을 이용하여 시작하기"
subtitle: ""
date: 2020-02-17 01:30:00 +0900
background: '/img/posts/03.jpg'

---

먼저 원하는 테마 선택

나는 jasper와 clean blog theme 중에서 고민하다가 결국 clean blog 테마를 선택하게 되었다.

http://jekyllthemes.org/
https://jekyllthemes.io/

다운로드 후 압축풀고 `_config.yml` 파일 수정

```yml
title:              혼공
email:              test@naver.com
description:        혼자 공부하는 블로그
author:             SyKi
baseurl:            "/SyKi_blog"
url:                "https://syki66.github.io"
```

### 여기서 baseurl과 url은 반드시 수정해주어야함.

url은 `"https://깃허브유저네임.github.io"`

baseurl은 `"/디렉토리명"`

이렇게 입력해주면된다. (여기서 유저네임은 소문자로 적어야됨)


그후 Settings에 들어가서

![image](https://user-images.githubusercontent.com/59393359/74637788-021f8180-51ae-11ea-82b7-dd132d511f4f.png)


GitHub Pages 로 내려가서 Source 항목에서 None 대신 master branch를 체크하게 되면 `your site is published at ~` 이렇게 표시가 되게 된다. 이후 옆에 링크를 누르게 되면 정상적으로 블로그 호스팅이 성공한 것을 확인할수 있다.

![image](https://user-images.githubusercontent.com/59393359/74637891-3b57f180-51ae-11ea-81b6-99bc0c85a418.png)

이후 포스트 생성은 _posts 폴더에서 `html` 또는 `markdown` 파일을 만들어서 블로그를 작성하면 되며, md 파일의 경우 상단에 아래코드를 추가하고서 포스트를 작성하면됨

```yml
---
layout: post
title: "제목"
subtitle: "부제목"
date: 2020-02-05 16:30:00 +0900
background: '/img/posts/01.jpg'
---
```

작성이 완료되고 나면 깃허브 커밋을 하면 얼마뒤에 업데이트가 반영됨.