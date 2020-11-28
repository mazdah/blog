---
layout: article
title: "[git rebase] 과거 커밋 삭제하기"
subtitle: "How to remove past commit of git"
date: 2020-11-28 20:00:00 +0900
lastmod: 2020-11-28 20:00:00 +0900
tags: 
    - git
---

<br>

git을 사용할때 과거의 커밋을 삭제하는 방법이다.

<br>

---

# 1. 해시값 확인하기

커밋을 삭제하고 싶은 커밋보다 이전 커밋의 해시값을 확인하고 아래 명령어를 입력한다. *(직전 커밋은 불가능)*

```
git rebase -i 해시값
```

<br>

---

# 2. `pick` => `squash` 수정

이후 vi에디터에 들어가지고, 변경할 커밋으로 가서 `i`를 눌러 입력모드로 전환 후, 삭제할 커밋 앞에 `squash`를 입력해주고 , `esc` => `:wq` => `엔터`를 눌러 빠져나온다. *(`squash`를 실행한 직전 커밋으로 내용이 병합이 된다.)*

![image](https://user-images.githubusercontent.com/59393359/100379855-fc1dd180-3058-11eb-886e-ed4f1bc266fd.png){:.border.rounded}

<br>

---

# 3. 커밋메세지 지정

커밋이 병합될때 커밋메세지는 어떤것으로 할지 선택할수 있는데, 주석처리해서 원하는 커밋 메세지만 남기거나 수정하면 되며, `esc` => `:wq` => `엔터`를 눌러 빠져나온다.

![image](https://user-images.githubusercontent.com/59393359/100380266-de9d3780-3059-11eb-8012-840fe180f44d.png){:.border.rounded}

<br>

---

# 4. `COMMITTER_DATE` 수정

깃허브에서는 커밋날짜 기준이 `COMMITTER_DATE` 기준으로 들어가기 때문에 `AUTHOR_DATE`로 덮어 씌어주어야 한다.

```
git filter-branch --env-filter \
    'if [ "$GIT_AUTHOR_DATE" != "$GIT_COMMITTER_DATE" ]
     then
         export GIT_COMMITTER_DATE="$GIT_AUTHOR_DATE"
     fi'
```

<br>

---

## 참고 자료

- [https://stackoverflow.com/questions/9725156/remove-old-git-commits](https://stackoverflow.com/questions/9725156/remove-old-git-commits)

<br><br><br><br>