---
layout: article
title: "[ffmpeg] 사진들을 동영상으로, 타임랩스 동영상 만들기"
subtitle: "How to make pictures to timelapse video"
date: 2021-04-19 00:30:00 +0900
lastmod: 2021-04-19 00:30:00 +0900
tags: 
    - ffmpeg
---

<br>

타임랩스로 찍은 사진들을 동영상으로 변환시키고 싶을때, 아래 방법을 이용하면 간단하게 해결할 수 있다.

<br>

---

# 1. ffmpeg 다운로드

[여기](https://www.gyan.dev/ffmpeg/builds/)로 이동하여 zip 파일을 다운받고 압축을 풀어준다.

![image](https://user-images.githubusercontent.com/59393359/115149806-b9f53b00-a0a0-11eb-9716-e57afbb9912c.png){:.border.rounded}

<br>

---

# 2. cmd 실행

압축을 풀은 디렉토리의 `bin` 경로까지 복사하고 `cmd`를 실행시켜 이동한다.

```
cd C:\경로\ffmpeg-4.4-essentials_build\bin
```

<br>

---

# 3. ffmpeg 명령어 입력

아래 명령어를 입력하면 이미지들이 한 개의 동영상으로 변환된다.

> 사진폴더에 있는 사진들을 *(img000.jpg ~ img999.jpg, 연속된 이름만 가능)* 15프레임, H264 코덱으로 output.mp4로 출력하겠다.

```
ffmpeg -r 15 -i "C:\경로\사진폴더\img%03d.jpg" -vcodec libx264 "C:\출력\경로\output.mp4"
```

- `-r` : 초당 프레임 수
- `-i` : 입력 파일 경로
- `-vcodec` : 비디오 코덱 설정

<br>

---

## 참고 자료

- [https://agiantmind.tistory.com/190](https://agiantmind.tistory.com/190)
- [http://ffmpeg.org/ffmpeg.html](http://ffmpeg.org/ffmpeg.html)

<br><br><br><br>