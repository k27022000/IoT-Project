# 프로젝트 개요
온습도센서, 체온센서, 심박센서, GPS센서를 이용해서 온열환자를 식별하고 근처 병원에 자동으로 전화를 거는 프로그램<br>

## 센서 데이터 읽기

### 심박수 측정: PulseSensor를 사용해 심박수를 측정.
온도 및 습도: DHT11 센서로 온도와 습도 읽기.<br>
아날로그 온도 센서: ADC1을 사용해 온도를 측정하고, Thermister() 함수를 통해 온도 계산.<br>

## LoRa 통신
송신: Radio.Send()를 사용해 데이터를 전송. 이 데이터는 온도, 습도, 심박수 등의 정보를 포함.<br>
수신: LoRa 모듈은 수신 데이터를 처리하고, 이를 통해 GPS 데이터를 추출하거나 다른 센서 데이터를 처리.<br>
위치 정보 추출: GPS 데이터를 수신하고, "GPGLL" 메시지를 통해 위도와 경도 추출 후 출력.<br>

## 하드웨어 설정
ADC 초기화: 온도 측정을 위해 ADC1과 ADC2 설정.<br>
UART 초기화: UART 포트를 통해 센서 데이터와 GPS 데이터 송수신.<br>
타이머 설정: TIM2와 TIM6을 사용해 일정 시간 간격으로 주기 설정.<br>

## 상태 관리
상태 관리: LOWPOWER, IDLE, RX, TX 등의 상태를 관리하여 송수신 상태 추적.<br>
