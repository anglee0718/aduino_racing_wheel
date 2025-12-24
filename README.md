# aduino_racing_wheel
##### 아두이노 레이싱 휠
***
# 중요
###### 아두이노 IDE필수 , 아두이노 IDE에서 " Joystic 라이브러리 "를 필수로 설치
***
* 코드
```
int FSRsensor = A0;
int value = 0; 

void setup() {
  Serial.begin(9600);
}

void loop() {
  int readValue = analogRead(A0);
  value = analogRead(FSRsensor);

  Serial.println(readValue);

  value = map(value, 0, 1023, 0, 255);

  delay(1000);


```
***
