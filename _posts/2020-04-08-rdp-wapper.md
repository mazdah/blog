---
layout: article
title: "윈도우 10에서 사용자 다중접속하여 컴퓨터 성능 나누어 쓰기"
subtitle: "RDP Wrapper, 다중접속 원격데스크톱, windows 10 pro"
date: 2020-04-08 15:50:00 +0900
lastmod: 2020-04-08 15:50:00 +0900
author_profile: false
---

<br>

일반적으로 윈도우 10 pro 이상에서 원격 데스크톱 모드를 지원한다. 하지만 pc당 한명의 사용자만 접속할수 있고, 다른 사용자가 접속할시 자동으로 나머지 pc에서 강제 로그아웃이 된다.

따라서 컴퓨터 하나를 이용해서 사용자 여러명이서 동시에 쓰고싶을때는 간단하게 아래와 같은 방법으로 따라하면 된다.

*(메인 컴퓨터는 이용하면서 동시에 다른 사용자가 여러명 원격으로 들어올수있다.)*

<br>

---

# 1. RDP Wrapper 다운로드

아래 링크로 들어가서 RDP Wrapper를 설치한다.

zip파일을 권장하며, 크롬에서는 악성파일로 인식하기 때문에 `세이프 브라우징` 기능을 설정에서 꺼주고 다운로드 받아야한다.

[RDP Wrapper](https://github.com/stascorp/rdpwrap/releases)

<br>

---

# 2. RDP Wrapper 설치

다운로드를 완료했으면 압축을 풀고 차례대로 `install.bat`, `update.bat`을 클릭하여 설치와 업데이트를 진행한다. *(안되면 관리자 권한으로 하기)*

<br>

---

# 3. `RDPConf.exe` 실행

`RDPConf.exe`를 실행하고 버전 밑에 빨간색으로 `not supported`라고 쓰여있으면 구글에 자기 버전을 입력하고, 본인의 버전에 맞는 `rdpwrap.ini` 파일을 다운로드 받을때까지 계속 찾는다.

![image](https://user-images.githubusercontent.com/59393359/78757468-8379e000-79b7-11ea-8cdb-eb749d3ee030.png){:.border.rounded}

<br>

---

# 4. `rdpwrap.ini` 파일 교체

**CMD를 관리자 권한으로 실행** 후 아래 명령어를 입력한다. (Y/N 선택창이 나오면 무조건 Yes)

```
> net stop termservice
```

이후 `C:\Program Files\RDP Wrapper`로 들어가서 다운로드 받은 `rdpwrap.ini` 파일로 교체하고 아래 CMD에 아래 명령어를 입력한다.

```
> net start termservice
```

완료가 되었으면 재부팅을 권장하며 `RDPConf.exe`를 들어가보면 버전 밑에 `fully supported`라고 바뀌어 있으면 이제 잘 작동된다.

![image](https://user-images.githubusercontent.com/59393359/78759027-f8e6b000-79b9-11ea-8121-0e4fa068c261.png){:.border.rounded}

<br>

---

# 5. 메인 컴퓨터에 접속해 있는 사용자 확인

이제 메인 컴퓨터를 로그아웃 없이 계속 사용하면서도, 여러명이서 원격 사용자로 들어올 수 있으며, 메인 컴퓨터의 리소스 (CPU, RAM, GPU) 등을 공유하게 된다.

작업관리자를 키고 사용자 탭에 들어가면 접속한 유저 목록과 리소스 사용량을 확인할 수 있으며, 원치 않은 사용자가 들어왔을 경우 마우스 오른쪽 버튼을 눌러 메세지를 보내거나 강제로 연결을 끊을 수 있다.

![image](https://user-images.githubusercontent.com/59393359/78761323-6cd68780-79bd-11ea-95b0-318ae7fabe45.png){:.border.rounded}

<br><br><br><br>