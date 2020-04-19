---
layout: article
title: "깃허브 서버에 사진 업로드하기"
subtitle: "using github issue comment"
date: 2020-02-17 01:30:00 +0900
lastmod: 2020-02-17 01:30:00 +0900
tags: 
    - github
    - cdn
    - image upload
---

<br>

마크다운 파일을 작성하다 보면 사진들을 업로드 해야하는 경우가 종종 있는데, 이 사진들을 로컬에서 직접 관리하기가 복잡해져서 [imgur](https://imgur.com/)을 쓰다가 좀더 안정적으로 쓰고 싶어 `github`의 `issues`페이지를 이용해 사진 올리는 법을 적어본다.

<br>

---

# 1. 레포지토리 입장

아무 레포지토리 상관없이 들어가서 `Issues` 탭 클릭

![image](https://user-images.githubusercontent.com/59393359/74649540-233e9d00-51c3-11ea-819d-4f0e54f54fd2.png){:.border.rounded}

<br>

---

# 2. New issue 클릭
![image](https://user-images.githubusercontent.com/59393359/74649583-35204000-51c3-11ea-9e97-39ddba6083c4.png){:.border.rounded}

<br>

---

# 3. 깃허브 서버에 사진 올리기

`Drog and Drop` 또는 `복사 붙여넣기` 로 텍스트 필드에 사진을 올리면 아래와 같은 글이 뜨는데 잠시 대기하면

![image](https://user-images.githubusercontent.com/59393359/74649658-54b76880-51c3-11ea-93c4-f0c737d117a3.png){:.border.rounded}

<br>

아래 이미지와 같이 뜨게된다.

![image](https://user-images.githubusercontent.com/59393359/74649696-6dc01980-51c3-11ea-979c-24a267cb8773.png){:.border.rounded}

<br>

---

# 4. 복사해서 `markdown` 에 적용

그대로 복사해서 `markdown`에 적용하거나, url만 가져와서 `html`의 `img` 태그에 사용해도 되며, github에서 issue를 취소 해도 이미 만들어진 사진의 주소는 계속 유효하다.

#### `링크를 잃어버리면 다시는 사진을 찾을 수 없기 때문에 유의해서 사용해야한다.`

<br><br><br><br>