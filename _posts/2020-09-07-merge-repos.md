---
layout: article
title: "git, 두개의 레포지토리 변경 이력까지 병합하기"
subtitle: "git merge repos"
date: 2020-09-07 17:00:00 +0900
lastmod: 2020-09-07 17:00:00 +0900
tags: 
    - git
    - merge
---

<br>

하나 또는 여러개의 레포지토리를 다른 레포지토리에 병합하고 싶으면 아래 방법대로 따라하면 되며, `프로젝트1`을 `프로젝트2` 안에다가 병합하는 기준으로 서술하였다.

<br>

---

# 1. 레포지토리 주소 연결

`프로젝트2`에서 아래 명령어를 입력하여, 가져올 `프로젝트1`의 깃 주소를 연결해준다.

```
git remote add -f 프로젝트1 https://github.com/syki66/프로젝트1.git
```

<br>

---

# 2. 레포지토리 병합

아래 명령어를 입력하여 레포지토리를 병합한다.

```
git merge 프로젝트1/master --allow-unrelated-histories
```

<br>

이후 vi 에디터가 뜨게되고, 병합에 대한 커밋 메세지를 적고 나서 `esc` -> `:wq` 를 입력하고 빠져나오게 되면, `프로젝트1`의 변경 이력들이 모두 병합된 것을 확인할 수 있다.

<br>

---

# 3. 연결된 주소 제거

더이상 `프로젝트1`의 주소가 필요 없다면 삭제해주도록 한다.

```
git remote remove 프로젝트1
```

<br>

이후 원격 저장소로 `git push`를 해주면 된다.

<br>

## 참고링크

- [https://medium.com/altcampus/how-to-merge-two-or-multiple-git-repositories-into-one-9f8a5209913f](https://medium.com/altcampus/how-to-merge-two-or-multiple-git-repositories-into-one-9f8a5209913f)

<br><br><br><br>