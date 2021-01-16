---
layout: article
title: "[git rebase] 깃, 커밋 순서 변경하기"
subtitle: "How to change order of commit of git"
date: 2021-01-10 23:30:00 +0900
lastmod: 2021-01-10 23:30:00 +0900
tags: 
    - git
---

<br>

git을 사용할 때, 커밋의 순서를 변경하는 방법이다.

<br>

---

# 1. 해시값 확인하기

변경하고 싶은 커밋보다 이전 커밋의 해시값을 확인하고 아래 명령어를 입력한다. *(첫번째 커밋을 포함하고 싶은경우 `해시값` 대신 `--root` 옵션 입력)*

```
git rebase -i 해시값
```

<br>

---

# 2. `pick` 순서 변경

vi에디터에 들어가지게 되며, `i`를 눌러 입력모드로 전환 후, 아래와 같이 커밋의 순서를 변경해준 뒤, `esc` => `:wq` => `엔터`를 눌러 빠져나온다.

![image](https://user-images.githubusercontent.com/59393359/104125783-60dc8380-539c-11eb-8748-0753a79013f3.png){:.border.rounded}

<br>

---

# 3. `COMMITTER_DATE` 수정

깃허브에서는 커밋날짜 기준이 `COMMITTER_DATE` 기준으로 들어가기 때문에 `AUTHOR_DATE`로 덮어 씌어주어야 한다. *(참고 : [깃, COMMITTER_DATE 변경하기](https://syki66.github.io/blog/2020/12/30/git-change-committer-date.html))*

```
git filter-branch --env-filter \
    'if [ "$GIT_AUTHOR_DATE" != "$GIT_COMMITTER_DATE" ]
     then
         export GIT_COMMITTER_DATE="$GIT_AUTHOR_DATE"
     fi'
```

<br><br><br><br>