---
layout: post
title: "깃허브 지킬 블로그 디스커스 추가 "
subtitle: ""
date: 2020-02-17 01:30:00 +0900
background: '/img/posts/04.jpg'

---




일단 _include에 disqus.html 작성

post.html로 들어가서 아래부분에 댓글 추가 하기 위해

맨아래 부분에 
```html
  <div id="post-disqus" class="container">
    {% include disqus.html %}
  </div>
```
  추가



  _config.yml 에 들어가서
```yml
  disqus_shortname: syki66
```




지킬 가입후 



![image](https://user-images.githubusercontent.com/59393359/74631860-69830480-51a1-11ea-9136-44614d5e8b18.png)

Add Disqus To site 클릭

밑에가서 get started 클릭
![image](https://user-images.githubusercontent.com/59393359/74631991-b36bea80-51a1-11ea-9179-59f7cba03309.png)


![image](https://user-images.githubusercontent.com/59393359/74631531-89fe8f00-51a0-11ea-8c8a-f07962e4d507.png)

i want to install disqus on my site 클릭

![image](https://user-images.githubusercontent.com/59393359/74640976-dacbb300-51b3-11ea-9001-6ca15808d1eb.png)

website name과 category와 language 선택
(website name은 나중에 shorname에 쓰임.)


그러면 요금제를 무엇으로 할지 select plan 이 뜨는데 우선 무료로 이용할 것이므로 Basic 선택

![image](https://user-images.githubusercontent.com/59393359/74641222-4746b200-51b4-11ea-9360-b0a20ca74698.png)

그후 지킬 선택

![image](https://user-images.githubusercontent.com/59393359/74641391-8d9c1100-51b4-11ea-8f91-f44dad0dfcc2.png)


Universal Embed Code 클릭
![image](https://user-images.githubusercontent.com/59393359/74641580-e4a1e600-51b4-11ea-8427-2a21e24b7e5a.png)


코드 복사
![image](https://user-images.githubusercontent.com/59393359/74641740-229f0a00-51b5-11ea-9b3f-1dc2742327e0.png)


_includes 폴더에 disqus.html 생성후 복붙


그뒤 사이트로 돌아가 configure 클릭



![image](https://user-images.githubusercontent.com/59393359/74642225-efa94600-51b5-11ea-98f9-859ba4f44342.png)