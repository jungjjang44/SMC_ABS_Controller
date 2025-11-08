# Sliding Mode 기반 ABS 제어기 (Electric 4WD Vehicle) - 작업 중

전기차(4륜 독립 구동)를 대상으로 슬라이딩 모드 제어(SMC)를 활용한 ABS(Antilock Brake System)를 구현한 내용임. 휠 슬립 값이나 노면 마찰계수를 사용하지 않으며, 타이어 힘 변화의 방향성과 휠 감속 패턴만으로 제어함.

---

## 구현 개요

### 1. 논문 기반 제어 구조 (핵심 아이디어)
- 참고 논문: *Development of an ABS for Electric Vehicles Without Wheel Slip and Road Friction Information*  
- 주요 특징:
  - 휠 슬립이나 마찰계수 없이도 최적 제동점 근처를 탐색
  - 전륜은 모터를 이용해 토크를 빠르게 증·감 → 최적 슬립 근처에서 반복적으로 진동시키며 탐색 (Cycling Control)
  - 후륜은 유압 브레이크를 사용해 전륜에서 얻은 목표 휠속도를 따라감 (Continuous Tracking)
  - 타이어 힘 증가/감소와 휠 감속 방향(sign)만으로 제어 판단

---

### 2. MATLAB Vehicle Dynamics Blockset
- 참고한 기본 모델:  
  `Scene Interrogation Reference Application`  
  https://kr.mathworks.com/help/vdynblks/ug/scene-interrogation-reference-application.html
- 변경점:
  - 내연기관 파워트레인 -> 전기차 4륜 독립 구동 (IWM)  
---
