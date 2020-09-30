---
layout: article
title: "[라즈베리파이, 파이썬] 서보모터 제어하기"
subtitle: "How to control the servo motor using python"
date: 2020-09-27 16:00:00 +0900
lastmod: 2020-09-27 16:00:00 +0900
tags: 
    - raspberry pi
    - python
    - gpio
    - servo motor
---

<br>

라즈베리파이 같이 파이썬으로 제어 가능한 장치가 있을때 서보모터를 제어하는 기초적인 방법이다.

<br>

---

# 1. 회로도

서보모터의 경우 아래와 같이 연결시켜주면 된다.

- `VCC => 빨강`
- `GND => 검정 or 갈색`
- `신호선 => 노랑 or 주황`

![image](https://user-images.githubusercontent.com/59393359/94357962-40800600-00d8-11eb-8d9f-580acb5d2de1.png){:.border.rounded}

<br>

---

# 2. 파이썬 코드

`pwm.ChangeDutyCycle` 인자에다가 값을 변경해주면 서보모터가 해당 위치로 변경되며, 이후에는 반드시 `time.sleep` 값을 넣어주어야 작동이 된다.

<br>

`pwm.ChangeDutyCycle` 의 인자로, 서보모터는 보통 `2~12`사이에서 (0%~100%)를 이동할 수 있는 값을 가지며, 서보모터마다 값이 조금씩 다르기에 직접 파이썬 쉘을 이용해서 값을 넣어주면서 최대 최소값을 알아내면 되고, 이에 따라 각도로 조절을 하고 싶을때는 변환식을 만드는 등, 코드를 변경해서 쓰면된다.

```python
import RPi.GPIO as GPIO # 라즈베리파이 GPIO 핀을 쓰기위해 임포트
import time # 시간 간격으로 제어하기 위해 임포트

def servoMotor(pin, degree, t):
    GPIO.setmode(GPIO.BOARD) # 핀의 번호를 보드 기준으로 설정, BCM은 GPIO 번호로 호출함
    GPIO.setup(pin, GPIO.OUT) # GPIO 통신할 핀 설정
    pwm=GPIO.PWM(pin, 50) # 서보모터는 PWM을 이용해야됨. 16번핀을 50Hz 주기로 설정

    pwm.start(3) # 초기 시작값, 반드시 입력해야됨
    time.sleep(t) # 초기 시작값으로 이동하고 싶지 않으면 이 라인을 삭제하면 된다.
    
    pwm.ChangeDutyCycle(4) # 보통 2~12 사이의 값을 입력하면됨
    time.sleep(t) # 서보모터가 이동할만큼의 충분한 시간을 입력. 너무 작은 값을 입력하면 이동하다가 멈춤

    # 아래 두줄로 깨끗하게 정리해줘야 다음번 실행할때 런타임 에러가 안남
    pwm.stop() 
    GPIO.cleanup(pin)

servoMotor(16, 8, 1) # 신호선을 16번 핀에 연결, 8의 각도로 1초동안 실행
```

<br>

---

## 참고 자료

- [https://www.youtube.com/watch?v=SGwhx1MYXUs](https://www.youtube.com/watch?v=SGwhx1MYXUs)

<br><br><br><br>