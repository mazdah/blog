---
layout: article
title: "[git rebase] 깃, 커밋 사이에 커밋 삽입하기"
subtitle: "How to inject a new commit between old commits"
date: 2021-04-11 20:00:00 +0900
lastmod: 2021-04-11 20:00:00 +0900
tags: 
    - git
    - git rebase
---

<br>

과거 커밋 사이에 커밋을 추가로 삽입하고 싶을때 아래 방법을 따라하면 된다.

> 2번 커밋과 3번 커밋 사이에 새 커밋을 삽입할때 기준으로 설명

![image](https://user-images.githubusercontent.com/59393359/114300528-b4757f00-9afb-11eb-9f59-7dbd70df76a9.png){:.border.rounded}

<br>

---

# 1. 해시값 확인하기

삽입하려는 위치의 직전 커밋 보다 이전의 해시값을 확인하고, 아래 명령어를 입력한다. *(첫번째 커밋을 포함하고 싶은경우 `해시값` 대신 `--root` 옵션 입력)*

> 예시에서 2번과 3번 커밋 사이에 새 커밋을 삽입하고 싶은 경우, 1번 커밋의 해시값을 입력해주면 된다.)

```
git rebase -i 해시값
```

<br>

---

# 2. `pick` -> `edit` 수정

`i`를 눌러 삽입모드로 전환하고, 삽입할 위치의 직전 커밋의 `pick`을 `edit`로 수정하고, `esc` -> `:wq` -> `엔터`를 눌러 빠져나온다.

> 예시에서는 2번의 커밋의 `pick`을 `edit`로 수정한다.

![image](https://user-images.githubusercontent.com/59393359/114300991-a4f73580-9afd-11eb-9c8e-5e1f05d0ccb4.png){:.border.rounded}

<br>

---

# 3. 삽입할 커밋 작성

삽입할 새로운 커밋을 작성한다.

> 2번과 3번 사이에 새롭게 들어갈 커밋을 작성한다.

```
git add .
```

```
git commit -m "새 커밋" --date=2021-04-11T12:00:00+0900
```

<br>

---

# 4. rebase 진행

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

# 5. `COMMITTER_DATE` 수정

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

# 6. 결과

> 정상적으로 2번과 3번 사이에 새로운 커밋이 삽입된 것을 볼 수 있다.

![image](https://user-images.githubusercontent.com/59393359/114301700-efc67c80-9b00-11eb-8eec-62d7bdb33fd4.png){:.border.rounded}

<br><br><br><br>