---
layout: article
title: "[git rebase] 과거 커밋메세지 변경하기"
subtitle: "How to change past commit message of git"
date: 2020-11-27 01:30:00 +0900
lastmod: 2021-01-16 20:30:00 +0900
tags: 
    - git
---

<br>

git을 사용할 때, 과거 커밋 메세지만 변경하는 방법이다.

<br>

---

# 1. 해시값 확인하기

변경하고 싶은 커밋보다 이전 커밋의 해시값을 확인하고 아래 명령어를 입력한다. *(첫번째 커밋을 포함하고 싶은경우 `해시값` 대신 `--root` 옵션 입력)*

```
git rebase -i 해시값
```

<br>

---

# 2. `pick` => `reword` 수정

vi에디터에 들어가게 되고, `i`를 눌러 입력모드로 전환 후, 아래와 같이 변경하고 싶은 커밋 앞에 `pick`을 `reword`로 변경한 뒤, `esc` => `:wq` => `엔터`를 눌러 빠져나온다.

![image](https://user-images.githubusercontent.com/59393359/104812093-3d558500-5843-11eb-9c6f-e05f708148a8.png){:.border.rounded}

<br>

---

# 3. 커밋메세지 수정

이후 기존의 커밋메세지가 뜨게 되는데, `i`를 누르고 커밋메세지를 변경한 뒤, `esc` => `:wq` => `엔터`를 눌러 빠져나온다.

![image](https://user-images.githubusercontent.com/59393359/104812144-b359ec00-5843-11eb-95ee-e0692d1f133d.png){:.border.rounded}

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