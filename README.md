# aduino_racing_wheel
##### 아두이노 레이싱 휠
***
# 중요
###### 아두이노 IDE필수 , 아두이노 IDE에서 " Joystick 라이브러리 "를 필수로 설치
#### [조이스틱_라이브러리_최신버전_다운링크_깃허브](https://github.com/MHeironimus/ArduinoJoystickLibrary/archive/master.zip)
위의 링크를 다운로드 (원래 아두이노 Joystick 라이브러리 지울것)
***
* 코드
```
#include <Joystick.h>

Joystick_ joystick;

const int SteerPin = A0;
const int FSRsensor = A5;

void setup() {
  joystick.begin();
}

void loop() {
  int steer = analogRead(SteerPin);
  joystick.setXAxis(steer);

  int accel = analogRead(FSRsensor);
  joystick.setThrottle(accel);

  delay(5);
}
// 기본 코드
```
***
