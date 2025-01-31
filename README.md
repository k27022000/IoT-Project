# 프로젝트 개요
이 프로젝트는 다양한 센서 데이터를 측정하고 LoRa 통신을 통해 데이터를 송수신하는 IoT 시스템입니다.<br> 
주로 심박수, 온도, 습도 및 GPS 위치 정보를 처리하며, STM32 마이크로컨트롤러와 LoRa 모듈을 사용하여 데이터를 송수신합니다. <br>
또한, 아날로그 온도 센서를 이용해 온도를 측정하고, PulseSensor와 DHT11 센서를 통해 심박수와 온도/습도 값을 읽습니다. <br>

## 센서 데이터 읽기

### 심박수 측정: PulseSensor를 사용해 심박수를 측정.
온도 및 습도: DHT11 센서로 온도와 습도 읽기.<br>
아날로그 온도 센서: ADC1을 사용해 온도를 측정하고, Thermister() 함수를 통해 온도 계산.<br>

### LoRa 통신
송신: Radio.Send()를 사용해 데이터를 전송. 이 데이터는 온도, 습도, 심박수 등의 정보를 포함.<br>
수신: LoRa 모듈은 수신 데이터를 처리하고, 이를 통해 GPS 데이터를 추출하거나 다른 센서 데이터를 처리.<br>
위치 정보 추출: GPS 데이터를 수신하고, "GPGLL" 메시지를 통해 위도와 경도 추출 후 출력.<br>

### 하드웨어 설정
ADC 초기화: 온도 측정을 위해 ADC1과 ADC2 설정.<br>
UART 초기화: UART 포트를 통해 센서 데이터와 GPS 데이터 송수신.<br>
타이머 설정: TIM2와 TIM6을 사용해 일정 시간 간격으로 주기 설정.<br>

### 상태 관리
상태 관리: LOWPOWER, IDLE, RX, TX 등의 상태를 관리하여 송수신 상태 추적.<br>
