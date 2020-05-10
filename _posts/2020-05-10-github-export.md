---
layout: article
title: "깃허브 export 이후, 작업파일 복구 및 원격저장소 연결하기"
subtitle: "how to use github-export.tar.gz"
date: 2020-05-10 00:30:00 +0900
lastmod: 2020-05-10 00:30:00 +0900
tags: 
    - github
    - export
---

<br>

# 1. 깃허브 export 압축풀기

깃허브에서 백업이나 마이그레이션 등의 용도로 `export` 하게 되면 `.tar.gz` 형식의 압축파일을 다운로드 할 수 있다.

이때 압축을 풀고서 계정 이름이 써있는 디렉토리를 들어가게 되면, 백업했을 당시의 레포지토리들이 아래 형식으로 나오게 된다.

> 레포지토리이름.git

<br>

---

# 2. 레포지토리 확인 후 이름 변경

아래와 같이 이 폴더의 이름을 `.git`으로 변경하고서 새로운 디렉토리를 만들고, 그 디렉토리 안에 `.git` 파일을 복사한다.

![image](https://user-images.githubusercontent.com/59393359/81478176-97cf2800-9256-11ea-9522-bea0270b7f75.png){:.border.rounded}

<br>

---

# 3. `git bash` 실행

새 디렉토리에서 `git bash` 를 실행하고, git log를 해보게 되면 정상적으로 커밋 히스토리가 출력 되는 것을 알 수 있다.

![image](https://user-images.githubusercontent.com/59393359/81478301-58550b80-9257-11ea-9f82-5a4c943f3f99.png){:.border.rounded}

<br>

---

# 4. 작업 파일 생성

디렉토리에 작업 파일들을 생성하기 위해서 먼저 `git init` 명령어를 입력해주고, `git checkout 커밋해시`를 입력해준다. *(최신파일을 가져오겠다 하는 경우는 커밋해시 대신 `master`를 입력해줘도 된다.)*

```
git init
git checkout 585d7305810adf3f331b2455a1cb34a775389fcd
```

![image](https://user-images.githubusercontent.com/59393359/81478417-4758ca00-9258-11ea-8455-3032c1f33374.png){:.border.rounded}

<br>

---

# 5. 원격 저장소 주소 바꾸기

이제 원격저장소와 연결하기 위해서, 먼저 저장되어있는 원격 저장소 주소를 삭제한다.

```
git remote remove origin
```

이후 새로운 원격 저장소 주소에 연결해준다.

```
git remote add origin https://github.com/syki66/second_project.git
```

<br>

---

# 6. 원격저장소로 푸시하기

이제 로컬저장소에 있는 작업파일들을 원격저장소로 푸시하고 싶다면 아래 명령어를 쓰면된다.

```
git push origin master
```

만약 싱크가 꼬여서 푸시 에러가 난다면, 아래 명령어로 수정해서 입력해주면 해결된다.

```
git push origin +master
```

<br><br><br><br>