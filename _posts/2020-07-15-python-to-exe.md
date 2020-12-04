---
layout: article
title: "[pyinstaller] 파이썬 파일을 exe로 변환시키기"
subtitle: "'.py' to '.exe'"
date: 2020-07-15 00:30:00 +0900
lastmod: 2020-12-04 18:00:00 +0900
tags: 
    - python
    - pyinstaller
    - exe
---

<br>

일반적인 파이썬 코드들은 `.py` 확장자를 가지며, 파이썬이 설치된 환경에서만 작동을 하게된다. 하지만 파이썬이 설치되어 있지 않은 환경에서도 작동되게 하려면 다른 확장자로 변경을 시켜줘야 하는데, 윈도우 환경에서는 대표적으로 `.exe` 확장자가 있다.

<br>

아래 순서대로 따라하게 되면, `.py` 파일을 `.exe` 파일로 변환시킬 수 있다.

<br>

---

# 1. `cmd` 실행

`cmd`를 실행하고서 아래의 명령어를 입력해준다. *(만약 `pip`가 설치되어 있지 않다고 나오면, [파이썬 환경변수설정](https://syki66.github.io/blog/2020/07/14/python-env-setting.html) 참고)*

```
pip install pyinstaller
```

<br>

---

# 2. 변환할 파이썬 경로로 이동

`cmd`에서 변환시킬 파이썬 파일이 있는 디렉토리로 이동한 후, 아래 명령어를 입력해준다. (*절대 경로도 상관없음*)

```
pyinstaller 변환될_파일.py
```

<br>

> 옵션

```c
--icon 파일아이콘.ico // 파일의 아이콘 설정
--noconsole // 파일 실행시 콘솔창을 안뜨게함
--onefile // 단일 파일로 만들기
--add-data 리소스파일.png // 파일을 내부에 넣어줌
```

<br>

---

# 3. 만약 `--add-data`, `--onefile` 옵션 중복 사용시

두 옵션을 중복으로 사용했을시, 파이썬 코드에서 경로를 제대로 읽어올 수 있도록 아래 `함수를 추가`해주고, 아래 함수를 통해서 경로가 입력되도록 코드를 수정해야한다.

```python
def resource_path(relative_path):
    try:
        base_path = sys._MEIPASS
    except Exception:
        base_path = os.path.abspath(".")
    return os.path.join(base_path, relative_path)
```

<br>

---

# 4. `dist` 폴더 이동

명령어를 실행하고 나서, `dist` 디렉토리로 들어가면 변환된 `단일 폴더` 또는 `단일 파일`이 있다.

또한 변환 작업을 한 디렉토리에 여러 디렉토리 및 파일이 생성되는데 `.exe`로 변환하는데 쓰인 파일들이며, 삭제해도 무방하다.

<br>

---

# 5. 일부 모듈이 정상적으로 작동하지 않을때

만약 써드파티 모듈을 사용했을때, 이 모듈이 외부 바이너리를 참고한다고 하면 `pyinstaller`한테 알려주어야 하는데, 이때 옵션을 아래 형식처럼 넣으면 된다.

```
--add-binary "C:/Users/윈도우유저이름/AppData/Local/Programs/Python/Python38-32/Lib/site-packages/특정모듈이름/바이너리파일.dll;."
```

<br>

---

## 참고 자료

- [https://stackoverflow.com/questions/7674790/bundling-data-files-with-pyinstaller-onefile/13790741#13790741](https://stackoverflow.com/questions/7674790/bundling-data-files-with-pyinstaller-onefile/13790741#13790741)

<br><br><br><br>