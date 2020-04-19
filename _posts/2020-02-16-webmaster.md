---
layout: article
title: "구글에서 지킬 블로그가 검색되도록 설정하기"
subtitle: "using Google Search Console"
date: 2020-02-16 14:30:00 +0900
lastmod: 2020-04-08 15:00:00 +0900
tags: 
    - webmaster
    - blog
    - sitemap.xml
    - robots.txt
---

<br>

# 1. `google seach console` 접속 & 인증

[google search console](https://search.google.com/search-console/welcome?utm_source=about-page){:.border.rounded} 로 들어가서 본인 소유 블로그의 url 입력

![캡처](https://user-images.githubusercontent.com/59393359/74607293-1ebea980-511b-11ea-8724-9213904f89fe.PNG){:.border.rounded}

<br>

구글에서 제공하는 인증용 html 파일 다운로드 (본인 소유인지 확인하기 위해)

![캡처1](https://user-images.githubusercontent.com/59393359/74607335-7ceb8c80-511b-11ea-96d3-516b1b64bf4d.PNG){:.border.rounded}

<br>

html을 본인 블로그 디렉토리의 `루트폴더`에 집어넣고 깃허브 업로드 후 인증하면

소유권이 자동으로 확인되었다는 창이 뜨게된다.

![캡처2](https://user-images.githubusercontent.com/59393359/74607306-431a8600-511b-11ea-9071-fcd7ee8f0c83.PNG){:.border.rounded}

<br>

---

# 2. `sitemap.xml` 생성

루트 디렉토리에 `sitemap.xml` 파일을 생성하고 아래의 내용을 넣어준다.

<div class="language-xml highlighter-rouge"><div class="highlight"><pre class="highlight"><code>---
layout: null
---
<span class="cp">&lt;?xml version="1.0" encoding="UTF-8"?&gt;</span>
<span class="nt">&lt;urlset</span> <span class="na">xmlns:xsi=</span><span class="s">"http://www.w3.org/2001/XMLSchema-instance"</span> <span class="na">xsi:schemaLocation=</span><span class="s">"http://www.sitemaps.org/schemas/sitemap/0.9 http://www.sitemaps.org/schemas/sitemap/0.9/sitemap.xsd"</span> <span class="na">xmlns=</span><span class="s">"http://www.sitemaps.org/schemas/sitemap/0.9"</span><span class="nt">&gt;</span>
  &#123;&#37; for post in site.posts &#37;&#125;
    <span class="nt">&lt;url&gt;</span>
      <span class="nt">&lt;loc&gt;</span>{{ site.url }}{{ post.url }}<span class="nt">&lt;/loc&gt;</span>
      &#123;&#37; if post.lastmod == null &#37;&#125;
        <span class="nt">&lt;lastmod&gt;</span>{{ post.date | date_to_xmlschema }}<span class="nt">&lt;/lastmod&gt;</span>
      &#123;&#37; else &#37;&#125;
        <span class="nt">&lt;lastmod&gt;</span>{{ post.lastmod | date_to_xmlschema }}<span class="nt">&lt;/lastmod&gt;</span>
      &#123;&#37; endif &#37;&#125;

      &#123;&#37; if post.sitemap.changefreq == null &#37;&#125;
        <span class="nt">&lt;changefreq&gt;</span>weekly<span class="nt">&lt;/changefreq&gt;</span>
      &#123;&#37; else &#37;&#125;
        <span class="nt">&lt;changefreq&gt;</span>{{ post.sitemap.changefreq }}<span class="nt">&lt;/changefreq&gt;</span>
      &#123;&#37; endif &#37;&#125;

      &#123;&#37; if post.sitemap.priority == null &#37;&#125;
          <span class="nt">&lt;priority&gt;</span>0.5<span class="nt">&lt;/priority&gt;</span>
      &#123;&#37; else &#37;&#125;
        <span class="nt">&lt;priority&gt;</span>{{ post.sitemap.priority }}<span class="nt">&lt;/priority&gt;</span>
      &#123;&#37; endif &#37;&#125;

    <span class="nt">&lt;/url&gt;</span>
  &#123;&#37; endfor &#37;&#125;
<span class="nt">&lt;/urlset&gt;</span>
</code></pre></div></div>

<br>

만약 `baseurl`을 사용하고 있다면 `loc` 태그 부분에 아래와 같이 쓰면 된다.

```xml
{% raw %}<loc>{{ site.url }}{{ site.baseurl }}{{ post.url }}</loc>{% endraw %}
```

<br>

---

# 3. `robots.txt` 생성

루트 폴더에 `robots.txt` 파일을 생성하고 아래의 내용을 넣어준다.

```
User-agent: *
Allow: /

Sitemap: https://syki66.github.io/blog/sitemap.xml
```

<br>

*`sitemap.xml`은 사이트를 크롤링 하기 쉽게 만들어주고, `robot.txt`로 크롤링 허용 범위 설정 및 사이트맵을 쉽게 가져가도록 해준다. ([robots.txt 사용법](https://support.google.com/webmasters/answer/6062596?hl=ko))*

<br>

---

# 4. `sitemap.xml` 제출

`google search console` 의 `Sitemaps` 메뉴에 들어가서 `sitemap.xml`을 제출

![image](https://user-images.githubusercontent.com/59393359/74607755-c5f11000-511e-11ea-877a-6e19e9cac1ef.png){:.border.rounded}

<br>

그러면 아래의 사진처럼 성공했다고 표시가 되며, 몇시간 안에 구글 검색으로 블로그가 노출되게 된다.

![image](https://user-images.githubusercontent.com/59393359/74607783-14061380-511f-11ea-8b04-da84a428b232.png){:.border.rounded}

<br>

---

## 참고링크

- [http://dveamer.github.io/homepage/Sitemap.html](http://dveamer.github.io/homepage/Sitemap.html)

<br><br><br><br>