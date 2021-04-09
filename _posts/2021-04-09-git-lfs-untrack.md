---
layout: article
title: "[git lfs untrack] 깃, lfs 추적 해제, 원격 저장소 lfs 저장공간 확보"
subtitle: "How to untrack git lfs files"
date: 2021-04-09 16:30:00 +0900
lastmod: 2021-04-09 16:30:00 +0900
tags: 
    - git
    - git lfs
---

<br>

`git lfs` 추적을 `해제`하고, 원격 저장소의 `저장공간`을 `확보`하는 방법이다.

<br>

---

# 1. `git lfs` 파일 추적

아래 명령어를 통하여, 모든 커밋에서 git lfs로 관리되는 파일들을 확인할 수 있다.

```
git lfs ls-files --all
```

<br>

---

# 2. 현재 커밋에서 `git lfs` 추적 해제

`.ext` 확장자를 가진 파일들의 `git lfs` 추적 해제

```
git lfs untrack '*.ext'
```

<br>

원격저장소에서 `.ext` 확장자를 가진 파일들 삭제

```
git rm --cached '*.ext'
```

<br>

기존 git 추적에 다시 추가

```
git add '*.ext'
```

<br>

이후 커밋해주면 된다.

<br>

---

# 3. 모든 커밋에서 `git lfs` 추적 해제

`.ext` 확장자를 가진 파일들의 `git lfs` 추적 해제

```
git lfs migrate export --everything --include='*.ext'
```

<br>

`lfs hook` 제거

```
git lfs uninstall
```

<br>

커밋 히스토리에서 `.gitattributes` 파일 제거

```
git filter-branch -f --prune-empty --tree-filter '
  git rm -f .gitattributes --ignore-unmatch
' --tag-name-filter cat -- --all
```

<br>

---

# 4. `COMMITTER_DATE` 수정

참고 : [깃, COMMITTER_DATE 변경하기](https://syki66.github.io/blog/2020/12/30/git-change-committer-date.html)

```
git filter-branch --env-filter \
    'if [ "$GIT_AUTHOR_DATE" != "$GIT_COMMITTER_DATE" ]
     then
         export GIT_COMMITTER_DATE="$GIT_AUTHOR_DATE"
     fi'
```

```
git push origin +브랜치이름
```

<br>

---

# 5. Github LFS 저장공간 확보하기

깃허브에서는 추후에 모든 히스토리에서 `lfs 추적이 해제된다 해도 lfs 저장공간은 그대로 차지`하게되며, 현재로서 유일하게 저장공간을 비울 수 있는 방법은 깃허브에서 `레포지토리를 삭제하고 다시 생성`하는 방법 밖에 없다. 이 방법을 택하게 되면 `issue`, `star`, `fork` 등이 전부 `초기화` 되기 때문에 lfs를 적용하기에 앞서 주의가 필요하다.

<br>

---

## 참고 자료

- [https://stackoverflow.com/questions/35011366/move-git-lfs-tracked-files-under-regular-git](https://stackoverflow.com/questions/35011366/move-git-lfs-tracked-files-under-regular-git)
- [https://stackoverflow.com/questions/59551850/remove-git-lfs-with-filter-branch-cant-re-add-unchanged-file-to-index](https://stackoverflow.com/questions/59551850/remove-git-lfs-with-filter-branch-cant-re-add-unchanged-file-to-index)
- [https://docs.github.com/en/github/managing-large-files/removing-files-from-git-large-file-storage#git-lfs-objects-in-your-repository](https://docs.github.com/en/github/managing-large-files/removing-files-from-git-large-file-storage#git-lfs-objects-in-your-repository)

<br><br><br><br>