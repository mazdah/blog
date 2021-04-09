---
layout: article
title: "[git cherry-pick] 깃, 특정 커밋들만 추출하기"
subtitle: "How to pick only specific commits"
date: 2021-04-08 21:00:00 +0900
lastmod: 2021-04-08 21:00:00 +0900
tags: 
    - git
    - git cherry-pick
---

<br>

하나의 브랜치에서 다른 브랜치로 몇개의 커밋만 가져가고 싶을 경우 `git cherry-pick`을 이용하면 된다.

<br>

사진과 같이 커밋이 되어있을때, 다른 브랜치에 `a`와 `b` 커밋만 가져가고 싶은 경우, 아래 순서대로 따라하면 된다. *(기존브랜치에서 커밋이 제거되지 않음)*

![image](https://user-images.githubusercontent.com/59393359/114024360-e940c680-98ae-11eb-80de-3c3a20352595.png){:.border.rounded}

<br>

---

# 1. 브랜치 이동

아래 명령어를 입력하여 커밋을 받을 브랜치로 이동한다.

```
git checkout 브랜치이름
```

<br>

---

# 2. 명령어 입력

만약 하나만 옮길 경우

```
git cherry-pick 해시값
```

<br>

두개 이상의 커밋을 옮길 경우

```
git chrry-pick 해시값1 해시값2 해시값3
```

<br>

커밋과 커밋 사이 범위를 전부 이동할 경우 *(첫 커밋은 포함되지 않으며, 마지막 커밋은 포함됨)*

```
git cherry-pick 해시값1..해시값5
```

<br>

---

# 3. 충돌 해결

만약 충돌이 발생한다면, `git status`로 상황을 살펴보면서 `git add`와 `git rm`을 이용하면서 충돌을 해결한다.

```
git status
git add 파일.ext
git rm 파일.ext
```

<br>

충돌을 해결했으면 아래 명령어를 입력하여 계속 진행한다.

```
git cherry-pick --continue
```

<br>

커밋 수정 창이 뜨게되면 수정해도 되며, 필요없다면 `:q` -> `엔터` 를 누르고 빠져나오고, 모든 충돌을 해결할때까지 이 과정을 반복한다.

<br>

---

# 4. `COMMITTER_DATE` 수정

참고 : [깃, COMMITTER_DATE 변경하기](https://syki66.github.io/blog/2020/12/30/git-change-committer-date.html)

```
git filter-branch --env-filter \
    'if [ "$GIT_AUTHOR_DATE" != "$GIT_COMMITTER_DATE" ]
     then
         export GIT_COMMITTER_DATE="$GIT_AUTHOR_DATE"
     fi'
```

```
git push origin +브랜치이름
```

<br>

---

## 참고 자료

- [https://stackoverflow.com/questions/1670970/how-to-cherry-pick-multiple-commits](https://stackoverflow.com/questions/1670970/how-to-cherry-pick-multiple-commits)
- [https://stackoverflow.com/questions/1994463/how-to-cherry-pick-a-range-of-commits-and-merge-into-another-branch](https://stackoverflow.com/questions/1994463/how-to-cherry-pick-a-range-of-commits-and-merge-into-another-branch)

<br><br><br><br>