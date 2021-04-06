---
layout: article
title: "[git checkout --orphan] 깃, 부모 없이 완전 비어있는 독립 브랜치 만들기"
subtitle: "How to create an empty branch"
date: 2021-04-07 01:00:00 +0900
lastmod: 2021-04-07 01:00:00 +0900
tags: 
    - git
    - git checkout
    - orphan
---

<br>

일반적으로 브랜치를 생성하게 되면 기존 커밋 내역을 가져오는데, 아래의 방법을 이용하면 비어있는 독립된 브랜치를 만들 수 있다.

<br>

---

# 1. `orphan branch` 생성 및 이동

아래의 명령어를 입력하게 되면, 기존 커밋들은 하나도 복제되지 않으며, 가장 최근 커밋의 파일들만 `staging area`에 들어간 상태가 된다.

```
git checkout --orphan 브랜치이름
```

<br>

---

# 2. `staging area` 초기화

아래 명령어를 입력하게 되면, `staging area`에 들어간 파일들의 추적이 삭제된다.

```
git rm -rf .
```

<br>

---

이제 완전히 비어있는 독립된 브랜치가 되며, 원하는 커밋을 추가시켜주면 된다.

<br>

---

## 참고 자료

- [https://stackoverflow.com/questions/1994463/how-to-cherry-pick-a-range-of-commits-and-merge-into-another-branch](https://stackoverflow.com/questions/1994463/how-to-cherry-pick-a-range-of-commits-and-merge-into-another-branch)

<br><br><br><br>