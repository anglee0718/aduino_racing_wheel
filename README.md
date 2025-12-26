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
```
// 방향, 엑셀, 브레이크, 패들 쉬프트 구현 코드
#include <Joystick.h>

/*
 Joystick_(
   hidReportId,
   joystickType,
   buttonCount,
   hatSwitchCount,
   xAxis, yAxis, zAxis,
   rxAxis, ryAxis, rzAxis,
   rudder, throttle,
   accelerator, brake, steering
 )
*/

/*
 버튼 번호:
 0 = 쉬프트 업
 1 = 쉬프트 다운
*/

Joystick_ joystick(
  0x03,
  JOYSTICK_TYPE_JOYSTICK,
  2,    // 버튼 2개
  0,
  true,  // X (조향)
  false, false,
  false, false, false,
  false,
  true,  // Throttle
  false,
  true,  // Brake
  false
);

const int SHIFT_UP_PIN   = 4;
const int SHIFT_DOWN_PIN = 5;

const int SteerPin = A0;
const int FSRsensor1 = A5;
const int FSRsensor2 = A4;

void setup() {
  joystick.begin();

  pinMode(SHIFT_UP_PIN, INPUT_PULLUP);
  pinMode(SHIFT_DOWN_PIN, INPUT_PULLUP);
}

void loop() {
  int steer = analogRead(SteerPin);
  joystick.setXAxis(steer);

  int accel = analogRead(FSRsensor1);
  joystick.setThrottle(accel);

  int brake = analogRead(FSRsensor2);
  joystick.setBrake(brake);

  joystick.setButton(0, digitalRead(SHIFT_UP_PIN) == LOW);
  joystick.setButton(1, digitalRead(SHIFT_DOWN_PIN) == LOW);

  delay(5);
}
```
***
### 작동테스트 하는법]
* window + R
* * joy.cpl 검색
* * * 속성 확인
