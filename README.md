# MQTT 기반 실내 환경 제어 & 센서 모니터링 시스템

STM32 보드와 센서 데이터를 수집하고, 데스크탑 Qt 애플리케이션에서 실시간 제어 및 모니터링이 가능한 MQTT 기반의 임베디드 시스템 프로젝트입니다.

---

## ✅ 프로젝트 개요

- **MCU**: STM32 Nucleo-F103RB
- **통신 계층**: Python 기반 MQTT ↔ UART 브리지
- **응용 계층**: Qt C++ GUI (제어, 시각화)
- **브로커**: Mosquitto (로컬 또는 외부)
- **확장성**: 향후 통신 계층을 임베디드 리눅스 (Raspberry Pi 등) 기반으로 이식 가능

---

## ⚙️ 시스템 구성도
```
[Qt GUI]
↑↓ MQTT
[Python Bridge App]
↑↓ UART
[STM32 + 센서/액터]
```

- **센서**: LM35 온도 센서, CdS 조도 센서
- **액터**: LED, 부저, 서보모터

---

## 🎯 주요 기능

### 1️⃣ 센서 모니터링
- 온도, 조도 값 실시간 표시 (MQTT 수신 기반)
- 실시간 로그 출력

### 2️⃣ 장치 제어
- LED / 부저 ON/OFF 제어
- 서보모터 각도 제어 (슬라이더)

### 3️⃣ 통신 구조
- `stm32/command`: 제어 명령 발행
- `stm32/temp`: 온도 데이터 수신
- `stm32/light`: 조도 데이터 수신
- `stm32/ack`: 명령 수행 결과 응답

### 4️⃣ 확장 기능 (예정)
- 실외 날씨 정보 연동 (OpenWeather API)
- 조건 기반 자동 제어
- 실시간 차트 시각화
- CSV 로그 저장

---

## 📁 디렉토리 구조
```
mqtt-embedded-system/
├── qt_gui/ # Qt GUI 애플리케이션 (C++)
├── bridge/ # MQTT ↔ UART 브리지 앱 (Python)
├── stm32/ # STM32CubeIDE 프로젝트 (FreeRTOS)
├── docs/ # 명세서 및 설계 문서
├── README.md
├── LICENSE
└── .gitignore
```

---

## 📦 기술 스택

| 계층 | 기술 |
|------|------|
| MCU | STM32 HAL, FreeRTOS |
| 브리지 앱 | Python, paho-mqtt, pyserial |
| GUI | Qt 6.x (C++), QMqttClient |
| 브로커 | Mosquitto (Local) |
| 확장 가능성 | Embedded Linux, ESP32, Web UI 등 |

---

## 🚧 개발 진행 플랜

- [✔️] 프로젝트 구조 및 명세 정리
- [ ] Qt UI 구성 및 MQTT 연결
- [ ] Python 브리지 앱 구현
- [ ] STM32 RTOS 기반 UART 처리
- [ ] 전체 통합 및 테스트
- [ ] 문서화 및 포트폴리오 구성

---

## 📌 프로젝트 목표

이 프로젝트는 단순한 디바이스 제어나 화면 구현에 그치지 않고,
**임베디드 시스템의 전체 흐름(센서 제어 → 통신 → 응용)** 을 직접 구성해보며
개발자 스스로 시스템을 설계하고 연결하는 경험을 목표로 합니다.

특히 MCU, 브리지, MQTT, GUI를 모두 다뤄보며 하드웨어 제어와 소프트웨어 시스템 간의 연결고리를 이해하고,
실무에서 마주할 다양한 구조를 직접 구축하고 시도해보는 과정 그 자체에 학습의 핵심이 있습니다.

완성된 시스템은 이후 임베디드 리눅스, 네트워크 시스템, IoT 서비스 설계로의 확장도 염두에 둔 구조로 구성되어 있습니다.

---

## 📚 참고

- [Qt QMqttClient 공식 문서](https://doc.qt.io/qt-6/qmqttclient.html)
- [Mosquitto MQTT 브로커](https://mosquitto.org/)
- [STM32 Nucleo 보드 문서](https://www.st.com/en/evaluation-tools/nucleo-f103rb.html)