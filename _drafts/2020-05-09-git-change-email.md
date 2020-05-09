---
layout: article
title: "깃 커밋 이메일 변경하기"
subtitle: ""
date: 2020-05-09 00:01:50 +0900
lastmod: 2020-05-09 00:01:50 +0900
tags: 
    - git
---




```
git filter-branch --env-filter '
WRONG_EMAIL="변경전 이메일"
NEW_NAME="유저네임"
NEW_EMAIL="변경후 이메일"

if [ "$GIT_COMMITTER_EMAIL" = "$WRONG_EMAIL" ]
then
    export GIT_COMMITTER_NAME="$NEW_NAME"
    export GIT_COMMITTER_EMAIL="$NEW_EMAIL"
fi
if [ "$GIT_AUTHOR_EMAIL" = "$WRONG_EMAIL" ]
then
    export GIT_AUTHOR_NAME="$NEW_NAME"
    export GIT_AUTHOR_EMAIL="$NEW_EMAIL"
fi
' --tag-name-filter cat -- --branches --tags
```



<br><br><br><br>