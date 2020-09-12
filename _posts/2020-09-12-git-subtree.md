---
layout: article
title: "[git subtree] 깃, 서브디렉토리를 변경이력과 함께 분리하기"
subtitle: "git, split subdirectory with history"
date: 2020-09-12 17:30:00 +0900
lastmod: 2020-09-12 17:30:00 +0900
tags: 
    - git
    - git subtree
---

<br>

git을 사용하면서 편의상 작은 여러 프로젝트들을 동일한 레포지토리에서 다룰 때가 있는데, 점점 규모가 커지는 등의 이유로 하나의 독립된 레포지토리로 변경이력을 포함하여 분리하고 싶다면, 아래 방법을 순서대로 따라하면 된다.

<br>

---

# 1. 기존 프로젝트 저장소에 진입

하위 디렉토리를 옮길 프로젝트 디렉토리에 들어가서 아래 명령어를 입력하여 `brandch`를 하나 `생성`한다.

```
git subtree split -P 서브디렉토리이름 -b 새로생성할브랜치이름
```

<br>

---

# 2. 분리할 프로젝트 디렉토리 생성

디렉토리를 새로 생성해 주고, `git init`을 입력해 초기화를 시켜준뒤 `git pull`을 사용하여 생성했던 `branch`를 복사해온다.

```
git init
git pull 기존프로젝트경로 생성했던브랜치이름
```

<br>

---

# 3. 원격 저장소 연결하기

하위디렉토리 복사가 정상적으로 완료되었다면, `원격 저장소에 연결` 후 `push` 해준다.

```
git remote add origin 원격저장소주소
git push origin master
```

<br>

---

# 4. `옮긴 디렉토리` 및 `branch` 삭제하기

기존 프로젝트 디렉토리에서 추출한 하위 디렉토리를 및 `branch`를 삭제하고 싶다면 아래 명령어를 입력하여 삭제하면 된다. *(단, 변경이력은 남게됨)*

```
git branch -D 생성했던브런치이름
git rm -rf 서브디렉토리이름
```

<br>

---

## 참고링크

- [https://stackoverflow.com/questions/359424/detach-move-subdirectory-into-separate-git-repository/17864475#17864475](https://stackoverflow.com/questions/359424/detach-move-subdirectory-into-separate-git-repository/17864475#17864475)

<br><br><br><br>