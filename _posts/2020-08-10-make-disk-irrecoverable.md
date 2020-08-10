---
layout: article
title: "저장장치에서 포렌식으로도 복구 불가능하게 파일 및 폴더 완전 삭제하기"
subtitle: "How to make disk irrecoverable"
date: 2020-08-10 22:00:00 +0900
lastmod: 2020-08-10 22:00:00 +0900
tags: 
    - irrecoverable
    - SSD
    - HDD
    - USB flash drive
    - SD card
    - cipher
    - bitlocker
---

<br>

일반적인 상황에서는 파일을 삭제하거나 저장장치의 포맷을 진행하였을 때, 그 파일을 완전 삭제하는게 아니라 저장장치에 연결된 주소값만 삭제함으로써 불필요한 속도 저하를 일으키는 것을 방지한다.

사용자는 삭제했다고 생각하고, 저장장치를 버리거나 팔았지만, 다른 사람이 악의를 가지고 저장장치의 데이터를 복구해서 쓸 가능성이 있다.

따라서 개인정보, 회사의 기밀정보 등 민감한 데이터가 들어있을 경우에는 아래와 같은 방법으로 확실하게 복구하지 못하도록 작업을 진행한 후에 처리하는 것이 좋다.

<br>

---

# 1. `SSD` 및 `USB flash drive` 및 `SD card`

`SSD(Solid-State Drive)`는 자체적인 수명 향상을 위해서 [TRIM](https://ko.wikipedia.org/wiki/TRIM) 기능이 주기적으로 실행되기 때문에, 시간이 지날수록 복구 확률은 줄어들게 된다.

`USB flash drive` 및 `SD card `는 SSD에서 [TRIM](https://ko.wikipedia.org/wiki/TRIM) 기능만 빠졌다고 보면 된다.

위의 세 저장장치는 물리적으로 `0` 또는 `1`의 값으로 밖에 표현되지 않기 때문에, 다른 데이터를 1회만 덮어 씌우는 것 만으로도 절대 복구를 할 수 없게 된다.

<br>

이 저장장치들을 완전 삭제하기 위해서는 먼저 윈도우의 `빠른 포맷` 기능으로 내부의 파일을 모두 삭제하고, 이후 cmd에서 간단하게 `cipher` 명령어만 입력해 주어도 3회 덮어쓰기(0, 1, 난수)를 해주기 때문에 데이터가 완전히 삭제된다.

<br>

```
cipher /w:드라이브명:
```

<br>

명령어를 입력하게 되면 1회에서는 `0`으로 데이터를 덮어씌우고, 2회는 `1`, 3회는 `난수` 값을 순차적으로 3번 덮어 씌우게 되는데, 이 작업을 끝내면 더 이상 데이터를 복구할 수 없게된다.

*(cipher 명령어는 빈 공간에서만 덮어쓰기가 동작하게 되어 삭제되지 않은 파일은 건드리지 않는다.)*

![image](https://user-images.githubusercontent.com/59393359/89796429-9f0f1600-db64-11ea-893b-5ce43e664633.png){:.border.rounded}

<br>

---

# 2. `HDD`

`HDD(Hard disk drive)`는 먼저 소개한 저장장치들과 같이 0 또는 1로 데이터를 기록하는 것은 동일하지만, HDD는 자기를 이용해서 기록을 하는데 이때 데이터를 다시 덮어 씌웠을 경우 정확히 0과 1의 값을 가지는 것이 아니라 0.03, 1.05, 0.98 같이 이전 데이터의 흔적을 추적할 수 있게 된다.

물론 이렇게 데이터의 기록이 남아있다 해도 특수 장비가 필요하기 때문에, 일반인 수준에서는 복구하기가 굉장히 어려워 크게 신경 쓰지 않아도 되지만, 그래도 꺼림칙한 것은 어쩔 수 없다.

그래서 데이터를 완전히 삭제하기 위해서 여러 방법들을 찾아보면 수많은 알고리즘이 존재하는데, 가장 유명한 알고리즘으로는 [Peter Gutmann](http://forensic.korea.ac.kr/DFWIKI/index.php/Peter_Gutmann) 알고리즘이 존재한다.

이 알고리즘을 사용하게 되면 절대로 파일 복구를 할 수 없는 것은 맞긴 하나, 35회의 덮어쓰기 시간이 필요하게 되어, 100MB/s 이상의 속도를 가진 1TB HDD로 진행을 하여도 60시간 이상이 소요되며, HDD에도 무리가 가게 된다.

<br>

그래서 시간이 비교적 빠르면서 마음 편한 삭제를 하려면, (물론 써드파티 프로그램을 이용해도 되지만) windows 10 pro에 기본으로 탑재되어 있는 `BitLocker`를 이용해서 먼저 HDD를 [AES암호화](https://namu.wiki/w/AES)를 시켜주고서, 이후 `빠른 포맷` 후 `cipher` 명령어로 한번 더 덮어 씌어주면 된다.

<br>

먼저 암호화할 저장장치를 선택하고 `BitLocker 켜기`를 클릭한다.

![image](https://user-images.githubusercontent.com/59393359/89797647-21e4a080-db66-11ea-864d-0b7841ffd781.png){:.border.rounded}

<br>

이후 암호를 입력해주고 다음으로 넘어간 뒤, 복구키는 파일로 저장시킨 후, 필요가 없으므로 바로 삭제해주고 삭제한 위치에서 `cipher` 명령어를 한 번 실행해준다.

```
cipher /w:삭제한파일경로
```

<br>

다음 페이지에서 `전체 드라이브 암호화`를 클릭해준다.

![image](https://user-images.githubusercontent.com/59393359/89798554-455c1b00-db67-11ea-8f85-b4dac9de2027.png){:.border.rounded}

<br>

이후 `새 암호화 모드`를 클릭하고 암호화를 진행하면 아래와 같이 진행이 된다.

![image](https://user-images.githubusercontent.com/59393359/89798300-f7471780-db66-11ea-9fa8-9ee60fce4882.png){:.border.rounded}

<br>

암호화가 완료되면 재부팅 후 빠른 포맷을 실행한다.

![image](https://user-images.githubusercontent.com/59393359/89798832-a71c8500-db67-11ea-9793-17021a8418cc.png){:.border.rounded}

<br>

*(빠른 포맷에서는 데이터를 전혀 소멸시키지 않지만, cipher 명령어를 사용하기 용이하게 해준다.)*

![image](https://user-images.githubusercontent.com/59393359/89799170-11352a00-db68-11ea-9f50-24eaa5f28a71.png){:.border.rounded}

<br>

사실 여기까지만 해도 복구키 또는 암호를 알고 있지 않는 이상 복구가 굉장히 힘들지만, `cipher` 명령어를 이용해서 한 번 더 데이터를 소멸 시킨다.

```
cipher /w:드라이브명:
```

<br>

---

# 3. 결론

위의 내용들을 한 줄로 요약하자면 아래와 같다.

<br>

`BitLocker 암호화` -> `빠른 포맷` -> `cipher`

<br>

이 정도로 데이터를 소멸시켰을 경우, 유명한 복구업체 수준에서는 데이터의 일부 조차 복구가 불가능 할 것으로 보이며, 국가 차원에서도 의미있는 데이터를 복구해내기란 정말 쉽지 않을 것이다.

<br><br><br><br>