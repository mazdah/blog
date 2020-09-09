---
layout: article
title: "최애 git 명령어"
subtitle: "all time git command favorites"
date: 2020-05-17 03:00:00 +0900
lastmod: 2020-09-09 16:30:00 +0900
tags: 
    - git
    - git command
---

<br>

`git`을 쓰면서 나중에 일부 명령어를 잊어버렸을 때, 이 포스트를 다시 보면서 쓸 수 있도록 유용하다고 생각했던 명령어들을 적어보았다.

<br>

---

# 0. 기본적인 명령어

```
git init # git 생성
git clone 레포지토리주소 # 원격저장소 복사하기
git status # 현재 디렉토리 변화점 추적
git add # 커밋 전 파일 추가
git commit -m "커밋메세지" # 커밋 및 메세지 넣기
git push origin master # 로컬저장소에서 원격저장소로 보내기
git push origin 브런치이름 # 브런치를 푸시
git pull origin master # 원격저장소에서 로컬저장소로 변경사항 가져오기
git remote add origin 레포지토리주소 # 원격저장소 주소 추가
git remote remove origin 레포지토리주소 # 원격저장소 주소 삭제
git diff # 변경된 부분 보기
history # 깃 명령어는 아니지만, 최근에 실행했던 명령어 한눈에 볼수 있음
```

<br>

---

# 1. 원격 저장소로 강제 푸시

싱크가 꼬여서 로컬 저장소를 원격 저장소에 덮어 씌울때 쓰인다.

```
git push origin +master
```

또는

```
git push --force
```

<br>

---

# 2. 과거 커밋 파일들 열람하기

과거에 커밋했던 작업공간을 그 당시 그대로 열람하고 싶을때 쓰인다.

```
git checkout 커밋해시
```

<br>

또는 브런치를 열람할 수도 있다.

```
git checkout 브런치이름
```

<br>

열람이후 최신 커밋으로 돌아가고 싶으면 아래와 같이 입력해준다.

```
git checkout master
```

<br>

---

# 3. 과거 커밋으로 되돌아가기

내가 작업했던 파일 및 폴더들은 그대로 살려두고, 커밋만 과거로 변경하고 싶다. *(기본값)*

```
git reset 커밋해시
```

<br>

내가 작업했던 공간을 모조리 없애버리고 과거 커밋상태 그대로 돌아가고 싶다.

```
git reset --hard 커밋해시
```

<br>

---

# 4. 하위 디렉토리 또는 파일에서 특정 문자열 찾기

문자열 또는 정규표현식을 넣어서 찾을 수 있다.

```
git grep 정규표현식
```

<br>

또한 아래 명령어를 이용하게 되면 과거 커밋에 있는 내용까지도 삳삳히 조회할 수 있다.

```
git grep 정규표현식 $(git rev-list --all)
```

<br>

---

# 5. 커밋 기록 보기

과거에 커밋을 했던 기록들을 보고 싶다면 아래 명령어를 입력하면 된다.

```
git log
```

<br>

만약 특정 파일이 변경되었던 커밋들만 보고 싶다면 아래 명령어를 입력하면 된다.

```
git log --follow ./파일의경로 # 특정파일이 변경되었을때의 커밋들 표시
```

<br>

---

# 6. 과거 시점에 커밋하기

과거의 시점으로 커밋을 하고 싶을때에는 아래와 같이 명령어를 입력해주면 된다.

```
git commit -m "커밋메세지" --date="Fri Apr 24 23:20:00 2020 +0900"
```

<br>

일일히 요일과 달을 쓰기 번거롭다면 아래와 명령어처럼 써도 무방하다.

```
git commit -m "커밋메세지" --date=2020-03-26T15:30:00+0900
```

<br>

다만 `author date`만 변경되는 것으로 `committer date`도 변경하고 싶을때는 아래와 같이 `git filter`를 이용해야 한다.

<br>

---

# 7. GIT_COMMITTER_DATE 수정하기

아래의 명령어를 입력하게 되면 모든 committer date가 author date와 똑같아진다. *(참고: [깃, 과거 커밋했던 내용 수정하기](https://syki66.github.io/blog/2020/05/01/git-amend-past-commit.html))*

```
git filter-branch --env-filter \
    'if [ "$GIT_AUTHOR_DATE" != "$GIT_COMMITTER_DATE" ]
     then
         export GIT_COMMITTER_DATE="$GIT_AUTHOR_DATE"
     fi'
```

<br>

만약 단지 몇 개의 커밋만 수정하고 싶을경우에는 아래 코드를 커밋해시와 날짜만 수동으로 바꾸어 가면서 적어주면 된다.

```
git filter-branch --env-filter \
    'if [ $GIT_COMMIT = 커밋해시 ]
     then
         export GIT_AUTHOR_DATE="Fri Apr 24 23:20:00 2020 +0900"
         export GIT_COMMITTER_DATE="Fri Apr 24 23:20:00 2020 +0900"
     fi'
```

<br>

---

# 8. 이메일 및 이름 변경하기

아래 명령어를 형식에 맞게 넣어주면 새 이름과 새 이메일로 변경된다. *(참고: [깃, 커밋 이메일 변경하기](https://syki66.github.io/blog/2020/05/10/git-change-email.html))*

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

<br><br><br><br>