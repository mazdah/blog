---
layout: article
title: "[git rebase] 깃, 과거 커밋 합치기"
subtitle: "How to squash past commit of git"
date: 2020-11-28 20:00:00 +0900
lastmod: 2021-04-12 23:00:00 +0900
tags: 
    - git
    - git rebase
---

<br>

git을 사용할때 과거의 커밋을 합치는 방법이며, 변경이력이 하나의 커밋으로 합쳐지게 된다.

> 2, 3, 4번 커밋을 합칠때 기준으로 설명

![image](https://user-images.githubusercontent.com/59393359/114401575-0393e080-9bde-11eb-884b-ca2f71736f6f.png){:.border.rounded}

<br>

---

# 1. 해시값 확인하기

합치고 싶은 커밋보다 이전 커밋의 해시값을 확인하고 아래 명령어를 입력한다. *(첫번째 커밋을 포함하고 싶은경우 `해시값` 대신 `--root` 옵션 입력)*

> 예시에서는 2, 3, 4번 커밋을 합치기 위해서 1번 커밋의 해시값 또는 `--root`를 입력한다.

```
git rebase -i 해시값
```

<br>

---

# 2. `pick` -> `squash` 수정

이후 vi에디터에 들어가지고, 변경할 커밋으로 가서 `i`를 눌러 입력모드로 진입 후, 합칠 커밋들 중 첫번째 커밋을 제외한 커밋들에 `squash`를 입력해주고 , `esc` => `:wq` => `엔터`를 눌러 빠져나온다.

> 예시에서는 3, 4번 커밋 앞에 `squash`를 입력해주면 된다.

![image](https://user-images.githubusercontent.com/59393359/114402111-7b620b00-9bde-11eb-96ea-b277690a1396.png){:.border.rounded}

<br>

---

# 3. 커밋메세지 지정

커밋이 병합될때 커밋메세지는 합쳐지는 커밋들의 모든 메세지를 선택할 수도 있으며, 주석을 사용하여 합쳐지는 커밋들 중 하나 또는 일부의 메세지만 선택할 수 있다. 또는 모두 주석처리 하고 새 커밋 메세지를 작성해도 된다.

이후 `esc` => `:wq` => `엔터`를 눌러 빠져나온다.

> 예시에서는 2번, 4번 커밋 메세지를 주석처리하고 3번 커밋메세지로 정함

![image](https://user-images.githubusercontent.com/59393359/114404209-743bfc80-9be0-11eb-89b4-9b4a2305ffc2.png){:.border.rounded}

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

> 정상적으로 2, 3, 4번 커밋이 합쳐진 것을 것을 볼 수 있다.

![image](https://user-images.githubusercontent.com/59393359/114404665-deed3800-9be0-11eb-8ac5-e9ad7d3f9686.png){:.border.rounded}

<br>

---

## 참고 자료

- [https://stackoverflow.com/questions/9725156/remove-old-git-commits](https://stackoverflow.com/questions/9725156/remove-old-git-commits)

<br><br><br><br>