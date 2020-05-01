---
layout: article
title: "깃, 과거 커밋했던 내용 수정하기"
subtitle: "amend past commit using git"
date: 2020-05-01 23:20:00 +0900
lastmod: 2020-05-01 23:20:00 +0900
tags: 
    - git
    - git rebase
    - git amend
---

아래와 같은 방법을 이용하게 되면 과거에 잘못 커밋했던 중요한 과거 개인정보들을 수정할수 있게된다.

<br>

---

# 1. 커밋 해시 확인

수정하고 싶은 커밋의 바로 직전의 커밋 해시를 복사한다.

<br>

---

# 2. `git rebase --interactive`

`git rebase --interactive 커밋 해시`를 입력한다.

> 예시

```
git rebase --interactive 896fd2887bda7eb9533b3bf5144b321aceea5e5c
```

<br>

# 3. `pick` => `edit` 수정

이후 vi 에디터가 실행되게 되는데, 가장 최상단줄의 pick을 edit로 바꾸고 :wq를 입력해서 저장하고 빠져나온다.

<br>

---

# 4. 변경하고 싶은 파일 수정

디렉토리에 들어가서 잘못 커밋한 내용들을 바로잡는다.

<br>

---

# 5. 다시 커밋하기

`git status`로 변경사항을 한번 확인해주고

```
git status
```

`git add`를 사용한 다음

```
git add .
```

`git commit --amend` 를 입력하여 날짜 또는 커밋메세지 등을 수정한다. 변경할 사항이 없으면 그냥 나오면 된다.

```
git commit --amend
```

이후 `git rebase --continue`를 입력하게되면 수정한 커밋부터 현재의 커밋까지 내용과 해시값이 전부 바뀌게 된다.

```
git rebase --continue
```

<br>

---

# 6. `git push`

이제 깃허브에 푸시하게 되면 원격 저장소와 다른 내용이 들어가 있게 되어 충돌이 일어나는데 이럴때는 `git push origin +master` 를 이용하게 되면 강제로 로컬에 있는 자료로 덮어 씌우게 된다.

```
git push origin +master
```

<br><br><br><br>