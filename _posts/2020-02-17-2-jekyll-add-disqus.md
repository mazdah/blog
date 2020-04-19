---
layout: article
title: "지킬 블로그에 디스커스 추가하기"
subtitle: "add blog comments"
date: 2020-02-17 13:30:00 +0900
lastmod: 2020-02-17 13:30:00 +0900
tags: 
    - disqus
    - blog
    - jekyll
---

<br>

# 1. Disqus 가입하기

[disqus.com](https://disqus.com/)에 들어가서 회원가입 한다.

<br>

---

# 2. `Settings` 클릭

`Add Disqus To Site` 클릭

![image](https://user-images.githubusercontent.com/59393359/74631860-69830480-51a1-11ea-9136-44614d5e8b18.png){:.border.rounded}

<br>

밑으로 가서 `GET STARTED` 클릭

![image](https://user-images.githubusercontent.com/59393359/74631991-b36bea80-51a1-11ea-9179-59f7cba03309.png){:.border.rounded}

<br>

`I want to install Disqus on my site` 클릭

![image](https://user-images.githubusercontent.com/59393359/74631531-89fe8f00-51a0-11ea-8c8a-f07962e4d507.png){:.border.rounded}

<br>

`website name`, `category`, `language` 입력

![image](https://user-images.githubusercontent.com/59393359/74640976-dacbb300-51b3-11ea-9001-6ca15808d1eb.png){:.border.rounded}

<br>

요금제 선택 `(우선 무료로 이용할 것이므로 Basic 선택)`

![image](https://user-images.githubusercontent.com/59393359/74641222-4746b200-51b4-11ea-9360-b0a20ca74698.png){:.border.rounded}

<br>

지킬 선택

![image](https://user-images.githubusercontent.com/59393359/74641391-8d9c1100-51b4-11ea-8f91-f44dad0dfcc2.png){:.border.rounded}

<br>

Universal Embed Code 클릭

![image](https://user-images.githubusercontent.com/59393359/74641580-e4a1e600-51b4-11ea-8427-2a21e24b7e5a.png){:.border.rounded}

<br>

코드 복사

![image](https://user-images.githubusercontent.com/59393359/74641740-229f0a00-51b5-11ea-9b3f-1dc2742327e0.png){:.border.rounded}

<br>

---

# 3. `disqus.html` 생성하기

`_includes` 폴더에 `disqus.html` 생성후 `Universal Embed Code` 붙여넣고, 사이트로 돌아가 `configure` 클릭 후, `Website Name`과 `Website URL` 정확하게 입력 후 `Complete Setup` 클릭

![image](https://user-images.githubusercontent.com/59393359/74642225-efa94600-51b5-11ea-98f9-859ba4f44342.png){:.border.rounded}

<br>

---

# 4. post.html 파일 변경

`_layouts` 폴더의 `post.html`의 맨 아래에다가 아래의 코드 추가하고 블로그에 다시 들어가보면 disqus 댓글 기능이 적용 된것을 볼수 있다.

```html
{% raw %}<div id="post-disqus" class="container">
  {% include disqus.html %}
</div>{% endraw %}
```

<br><br><br><br>