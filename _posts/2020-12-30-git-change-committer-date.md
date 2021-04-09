---
layout: article
title: "[git filter-branch] 깃, COMMITTER_DATE 변경하기"
subtitle: "git, change COMMITTER_DATE"
date: 2020-12-30 21:00:00 +0900
lastmod: 2020-12-30 21:00:00 +0900
tags: 
    - git
    - git filter-branch
---

<br>

`git rebase` 또는 `git cherry-pick` 등을 이용하여 과거 커밋을 수정하고, github에 push 후 히스토리를 보게되면 아래와 같이 커밋이 수정시간 기준으로 바뀌어있다.

![image](https://user-images.githubusercontent.com/59393359/103347281-e1b49900-4ad9-11eb-92d8-6ca77a514f47.png){:.border.rounded}

<br>

`COMMITTER_DATE` 값이 수정시간으로 변경되었기 때문인데, 이를 `git filter-branch`를 사용하여 `AUTHOR_DATE`로 덮어씌우게 되면 아래처럼 해결이 된다.

![image](https://user-images.githubusercontent.com/59393359/103347369-23ddda80-4ada-11eb-8008-21d382ac7ca7.png){:.border.rounded}

<br>

---

# 1. 모든 `COMMITTER_DATE` 한번에 수정하기

`git`에서 아래 명령어를 입력하게 되면, 모든 커밋에서 `COMMITTER_DATE`가 `AUTHOR_DATE`의 값으로 바뀌게 된다.

```
git filter-branch --env-filter \
    'if [ "$GIT_AUTHOR_DATE" != "$GIT_COMMITTER_DATE" ]
     then
         export GIT_COMMITTER_DATE="$GIT_AUTHOR_DATE"
     fi'
```

<br>

---

# 2. 하나의 커밋만 수정하기

만약 한개의 커밋만 수정하고 싶다면, 아래 명령어를 입력하면 된다.

```
git filter-branch --env-filter \
    'if [ $GIT_COMMIT = 커밋해시값 ]
     then
         export GIT_COMMITTER_DATE="$GIT_AUTHOR_DATE"
     fi'
```

<br>

---

# 3. 커밋의 날짜를 직접 변경하기

커밋의 날짜를 직접 지정하고 싶다면, 아래 명령어를 입력하면 된다.

```
git filter-branch --env-filter \
    'if [ $GIT_COMMIT = 커밋해시값 ]
     then
         export GIT_AUTHOR_DATE=2020-12-01T18:30:00+0900
         export GIT_COMMITTER_DATE=2020-12-01T18:30:00+0900
     fi'
```

<br>

---

# 4. 원격저장소에 업로드하기

`git push` 할 때 충돌이 나기 때문에, 아래 명령어를 입력하여 강제로 로컬 저장소를 원격 저장소에 덮어 씌운다.

```
git push origin +브랜치이름
```

<br><br><br><br>