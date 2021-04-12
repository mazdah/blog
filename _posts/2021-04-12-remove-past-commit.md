---
layout: article
title: "[git rebase] 깃, 과거 커밋 삭제하기"
subtitle: "How to remove past commit of git"
date: 2021-04-12 21:00:00 +0900
lastmod: 2021-04-12 21:00:00 +0900
tags: 
    - git
    - git rebase
---

<br>

git을 사용할때 과거의 커밋을 삭제하는 방법이며, 이때 변경이력은 삭제가 된다.

> 2번 커밋과 3번 커밋 사이에 있는 커밋을 삭제할때를 기준으로 설명

![image](https://user-images.githubusercontent.com/59393359/114390370-223faa80-9bd1-11eb-90e1-f16e442e6b9e.png){:.border.rounded}

<br>

---

# 1. 해시값 확인하기

삭제하고 싶은 커밋보다 이전 커밋의 해시값을 확인하고 아래 명령어를 입력한다. *(첫번째 커밋을 포함하고 싶은경우 `해시값` 대신 `--root` 옵션 입력)*

> 예시에서는 2번 커밋의 해시값을 입력해준다.

```
git rebase -i 해시값
```

<br>

---

# 2. 커밋 확인 후 삭제

삭제하고 싶은 커밋에 커서를 놓고 `dd`를 입력하여 한 줄을 삭제하고 `:wq`를 입력하여 빠져나온다.면 된다. *(또는 `pick` -> `drop`으로 변경해도됨)*

> 예시에서는 wrong 커밋에 커서를 놓고서 `dd`를 입력하여 삭제한다.

![image](https://user-images.githubusercontent.com/59393359/114390941-d5100880-9bd1-11eb-8697-66c0311d80a2.gif){:.border.rounded}

<br>

---

# 3. rebase 진행

아래 명령어를 이용하여 리베이스를 진행하고, 충돌이 일어나면 *(`git add`, `git rm`, `파일 수정` 등으로)* 충돌을 해결해주고 다시 리베이스를 진행한다.

```
git rebase --continue
```

```
git add
```

```
git rm
```

<br>

---

# 4. `COMMITTER_DATE` 수정

정상적으로 리베이스가 끝났다면 `COMMITTER_DATE`를 수정한다.

깃허브에서는 커밋날짜 기준이 `COMMITTER_DATE` 기준으로 들어가기 때문에 `AUTHOR_DATE`로 덮어 씌어주어야 한다. *(참고 : [깃, COMMITTER_DATE 변경하기](https://syki66.github.io/blog/2020/12/30/git-change-committer-date.html))*

```
git filter-branch --env-filter \
    'if [ "$GIT_AUTHOR_DATE" != "$GIT_COMMITTER_DATE" ]
     then
         export GIT_COMMITTER_DATE="$GIT_AUTHOR_DATE"
     fi'
```

<br>

---

# 5. 결과

> 정상적으로 wrong 커밋이 삭제된 것을 볼 수 있다.

![image](https://user-images.githubusercontent.com/59393359/114390527-5915c080-9bd1-11eb-8e11-f8077b6b4d8c.png){:.border.rounded}

<br><br><br><br>