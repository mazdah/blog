---
layout: post
title: "깃허브 지킬 블로그 구글 검색 기능"
date: 2020-02-16 14:30:00 +0900
background: '/img/posts/03.jpg'

---



# 1. google seach console 접속 후 본인인증
[google search console](https://search.google.com/search-console/welcome?utm_source=about-page) 로 들어가서 본인 소유 블로그의 url 입력
![캡처](https://user-images.githubusercontent.com/59393359/74607293-1ebea980-511b-11ea-8724-9213904f89fe.PNG)


이후 구글에서 제공하는 인증용 html 파일 다운로드 (본인 소유 사이트인지 확인하기 위해서)
![캡처1](https://user-images.githubusercontent.com/59393359/74607335-7ceb8c80-511b-11ea-96d3-516b1b64bf4d.PNG)


그후 인증용 html 파일을 다운받아 본인 블로그의 루트폴더에 집어넣고 깃허브 커밋하고 인증
![캡처2](https://user-images.githubusercontent.com/59393359/74607306-431a8600-511b-11ea-9071-fcd7ee8f0c83.PNG)

그러고 `google seach console`에서 확인해보면 인증되었다고 나오게됨

# 2. 

루비 터미널에 들어가서 아래 코드 입력하여 설치하면 자동으로 `sitemap.xml`과 `robot.txt`가 생성됨
(sitemap.xml은 사이트를 크롤링 하기 쉽게 만들어주고, robot.txt로 크롤링 허용 범위 설정함)
```
> gem install jekyll-sitemap
```

설치가 된 이후 `_config.yml` 에 들어가서 밑에 코드 추가 (이미 url 추가되있다면 `plugins` 만 추가하면됨)

```yml
url: "https://syki66.github.io"
plugins:
  - jekyll-sitemap
```

그후 `google search console` 의 `Sitemaps` 메뉴에 들어가서 `sitemap.xml`을 제출
![image](https://user-images.githubusercontent.com/59393359/74607755-c5f11000-511e-11ea-877a-6e19e9cac1ef.png)

그러면 아래의 사진처럼 성공했다고 표시가 되며, 몇시간 안에 구글 검색으로 블로그가 노출되게됨
![image](https://user-images.githubusercontent.com/59393359/74607783-14061380-511f-11ea-8b04-da84a428b232.png)

