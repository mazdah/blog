---
layout: article
title: "[git rebase] 과거 커밋메세지 변경하기"
subtitle: "How to change past commit of git"
date: 2020-11-27 01:30:00 +0900
lastmod: 2020-11-27 01:30:00 +0900
tags: 
    - git
---

<br>

git을 사용할 때, 과거에 커밋했던 메세지를 변경하는 방법이다.

<br>

---

# 1. 해시값 확인하기

커밋 메세지를 변경하고 싶은 커밋의 직전 커밋의 해시값을 가져와서 git rebase를 실행한다. *(만약 첫 커밋 메세지를 바꾸고 싶다면 `해시값` 대신 `--root`를 입력한다.)*

```
git rebase -i 해시값
```

<br>

---

# 2. `pick` => `edit` 수정

이후 vi에디터에 들어가지고, 가장 최상단에 변경할 커밋이 뜨게 되는데 `i`를 눌러 입력모드로 전환하고, `pick`을 `edit`로 변경후, `esc` => `:wq` => `엔터`를 눌러 빠져나온다.

![image](https://user-images.githubusercontent.com/59393359/81479254-234bb780-925d-11ea-84ca-7bb64850e1f3.png)

<br>

---

# 3. 커밋메세지 수정

아래 명령어를 입력하면 vi에디터로 다시 들어가게 되는데, 이때 `i`를 눌러 입력모드로 전환하고, 커밋 메세지를 수정한뒤, `esc` => `:wq` => `엔터`를 눌러서 빠져나온다.

```
git commit --amend
```

<br>

---

# 4. git rebase 진행

이후 아래 명령어를 입력하게 되면 성공적으로 과거의 커밋메세지가 변경된다.

```
git rebase --continue
```

<br><br><br><br>