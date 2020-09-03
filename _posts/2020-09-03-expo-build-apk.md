---
layout: article
title: "expo를 사용하여 apk 파일 생성하기"
subtitle: "build apk using expo"
date: 2020-09-03 18:00:00 +0900
lastmod: 2020-09-03 18:00:00 +0900
tags: 
    - expo
    - build
    - apk
---

<br>

`expo`를 활용해서 `react native` 프로젝트를 완료 하였다면 아래의 방법으로 `apk` 파일을 생성할 수 있다.

<br>

---

# 1. `app.json` 수정

`app.json`으로 들어가서 아래 항목들을 수정해준다.

> app.json

```json
 {
   "expo": {
    "name": "Your App Name",
    "icon": "./path/to/your/app-icon.png",
    "version": "1.0.0",
    "slug": "your-app-slug",
    "ios": {
      "bundleIdentifier": "com.yourcompany.yourappname",
      "buildNumber": "1.0.0"
    },
    "android": {
      "package": "com.yourcompany.yourappname",
      "versionCode": 1
    }
   }
 }
```

<br>

---

# 2. `cmd` 실행

`cmd`를 실행시킨 뒤 해당 프로젝트 디렉토리로 들어가서 아래 명령어를 입력해준다.

```
expo build:android
```

<br>

그럼 `apk`와 `app-bundle` 중에 선택하라는 창이 뜨는데, 이때 단일 파일로 만들어 안드로이드폰에서 직접 설치도 가능하게 하려면 `apk`를 선택하고, 스토어에만 최적하되게 빌드하려면 `app-bundle`를 선택하면 된다.

![image](https://user-images.githubusercontent.com/59393359/92098356-18242500-ee14-11ea-8ddd-0b7b88777f16.png){:.border.rounded}

<br>

---

# 3. `keystore` 저장

이후 `keystore`를 `(1) expo에서 관리하게 할지`, `(2) 사용자가 직접 관리할지`, 묻는 창이 뜨게 되는데, 원하는 옵션을 선택하면 된다.

<br>

1번 옵션을 선택했다면, 아래 명령어를 입력하여 복사본을 만들어야 한다.

```
expo fetch:android:keystore
```

<br>

이후 생성된 `.jks` 파일을 안전한 장소에 보관하면 된다. *`(키를 잃어버리게 되면 플레이 스토어에서 본인 계정일지라 하더라도 수정 및 업데이트가 불가능해진다.)`*

<br>

추후에 expo 서버에서 `keystore`를 `삭제`하고 싶으면 아래 명령어를 입력하여 빌드를 진행하면 된다.

```
expo build:android --clear-credentials
```

<br>

---

# 4. `.apk` 다운로드

이후 빌드가 자동으로 진행되게 되는데, 이때 expo에서 동시 빌드 인원을 제한시켜 놨기 때문에 사람이 많으면 좀 기다려야한다. *(돈을 내면 우선권을 받을수 있으나 권장하지 않으며, 보통 낮 시간대가 빨리 진행된다.)*

<br>

작업이 다 완료되었다고 뜨면, 제공해주는 링크로 들어가 `.apk` 파일을 30일간 다운로드 받을 수 있게 된다.

<br>

---

## 참고링크

- [https://docs.expo.io/distribution/building-standalone-apps/](https://docs.expo.io/distribution/building-standalone-apps/)

<br><br><br><br>