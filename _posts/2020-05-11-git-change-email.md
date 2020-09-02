---
layout: article
title: "git, 커밋 이메일 및 이름 변경하기"
subtitle: "change git commit email"
date: 2020-05-11 00:18:20 +0900
lastmod: 2020-09-02 20:30:00 +0900
tags: 
    - git
    - email
---

<br>

깃허브에서 이메일을 수정하게 되거나, 커밋한 사람의 유저네임이나 이메일이 같지 않다면 본인이 아닌걸로 인식되어 깃허브 contribution 그래프에서 초록박스가 사라지게 된다. 이를 해결하려면 레포지토리 커밋의 이메일과 유저네임을 깃허브 계정과 동일하게 변경해주면 된다.

<br>

---

# 1. `git bash` 실행

bash를 실행하고서 아래 코드를 입력해준다.

이때 둘 중 하나만 바꾸고 싶다면, 바꾸고 싶은 곳의 변수의 문자열만 입력해주고 나머지는 그대로 두면 된다.

```
git filter-branch --env-filter '

WRONG_EMAIL="변경전 이메일"
NEW_EMAIL="변경후 이메일"

WRONG_NAME="변경전 유저네임"
NEW_NAME="변경후 유저네임"

if [ "$GIT_COMMITTER_EMAIL" = "$WRONG_EMAIL" ]
then
    export GIT_COMMITTER_EMAIL="$NEW_EMAIL"
fi

if [ "$GIT_AUTHOR_EMAIL" = "$WRONG_EMAIL" ]
then
    export GIT_AUTHOR_EMAIL="$NEW_EMAIL"
fi

if [ "$GIT_COMMITTER_NAME" = "$WRONG_NAME" ]
then
    export GIT_COMMITTER_NAME="$NEW_NAME"
fi

if [ "$GIT_AUTHOR_NAME" = "$WRONG_NAME" ]
then
    export GIT_AUTHOR_NAME="$NEW_NAME"
fi

' --tag-name-filter cat -- --branches --tags
```

<br>

---

# 2. 강제로 `git push` 하기

로컬 저장소에 있는 커밋들을 원격 저장소로 덮어씌우기 위해서 아래 명령어를 입력해주면 된다.

```
git push origin +master
```

<br>

---

## 참고링크

- [How can I change the author name / email of a commit?](https://www.git-tower.com/learn/git/faq/change-author-name-email)

<br><br><br><br>