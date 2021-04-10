---
layout: article
title: "[github contributions graph] 깃허브에서 잘못 카운트된 컨트리뷰션 그래프 고치기"
subtitle: "How to fix wrong count of contributions graph on Github"
date: 2021-04-10 19:00:00 +0900
lastmod: 2021-04-10 19:00:00 +0900
tags: 
    - github
---

<br>

`git rebase`, `git cherry-pick`, `git reset`, `git filter-branch` 등을 사용한 커밋들을 깃허브에 재 업로드를 하게 되면, 깃허브의 `contributions graph`에서 카운트가 계속 누적되서 카운팅 되는 문제가 생긴다.

<br>

예를들어 이 날짜의 실제 커밋 개수는 `4개`이지만, 깃허브에서는 `8개`로 `카운팅`이 기록되어있다.

<div>
    <img src="https://user-images.githubusercontent.com/59393359/114268691-68fc9b80-9a3d-11eb-8954-f707fad1c463.png" style="width:64%" class="border rounded">
    <img src="https://user-images.githubusercontent.com/59393359/114268715-892c5a80-9a3d-11eb-839e-1fbf1c6bebcc.png" style="width:34%" class="border rounded">
</div>

<br>

이를 고치려면 아래의 순서대로 따라하게 된다.

<br>

---

# 1. 디폴트 브랜치의 이름 확인 및 수정

먼저 고치고 싶은 레포지토리의 `기본 브랜치의 이름`을 확인하고, `깃허브 홈페이지` -> `Settings` -> `Repositories` 탭에 들어가서 `Repository default branch`에 고치고 싶은 `기본 브랜치의 이름`으로 바꿔주고 `Update`를 클릭한다.

![image](https://user-images.githubusercontent.com/59393359/114267289-9a716900-9a35-11eb-90eb-d8fd472ff096.png){:.border.rounded}

<br>

---

# 2. 레포지토리 `clone` 및 `재생성`

깃허브 레포지토리를 로컬로 `clone` 해준 뒤, 깃허브의 레포지토리를 `삭제`하고 `재생성`한다.

<br>

이후 로컬에서 깃허브 레포지토리로 `업로드` 해주면 된다.

```
git clone 레포지토리주소
```

```
깃허브 레포지토리 삭제 -> 재생성
```

```
git push origin 브랜치이름
```

<br>

---

# 3. 결과

이제 정상적으로 기여 개수가 카운팅 되는것을 볼 수 있다.

![image](https://user-images.githubusercontent.com/59393359/114268565-a876b800-9a3c-11eb-9e36-1f2c530ebcd9.png){:.border.rounded}

<br><br><br><br>