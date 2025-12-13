<p align="center">
  <img src="assets/banner.jpg" alt="Banner">
</p>

<p align="center">
  <a href="https://docs.google.com/presentation/d/1-Q_TZLXfFrFoZFN47uKtgcyI_h5BXLpoyHWAMogy4Dw/edit?slide=id.p#slide=id.p">
    <img src="https://img.shields.io/badge/PRESENTATION-GoogleSlides-yellow?style=for-the-badge&logo=google-slides&logoColor=white" alt="발표자료">
  </a>
  <a href="LICENSE">
    <img src="https://img.shields.io/badge/License-Apache_2.0-blue.svg?style=for-the-badge" alt="License">
  </a>
</p>

# 📚 목차
- [1. 팀 소개](#1-팀-소개)
- [2. 프로젝트 개요](#2-프로젝트-개요)
- [3. 주요 기능](#3-주요-기능)
- [4. 핵심 기술](#4-핵심-기술)
- [5. 기술적 문제 및 해결](#5-기술적-문제-및-해결)
- [6. 시스템 설계 및 문서](#6-시스템-설계-및-문서)
- [7. 프로젝트 구조](#7-프로젝트-구조)
- [8. 기술 스택](#8-기술-스택)
- [9. 실행·개발 가이드](#9-실행·개발-가이드)
- [10. 프로젝트 관리](#10-프로젝트-관리)
- [11. 라이선스](#11-라이선스)

---

# 1. 팀 소개
<div align="center">
  <table>
    <tr>
      <th width="15%">팀 (Team)</th>
      <th width="15%">이름 (Name)</th>
      <th width="70%">담당 역할 (Role & Responsibility)</th>
    </tr>
    <tr>
      <td align="center"><b>Main</b></td>
      <td align="center">장진혁</td>
      <td><b>기술 총괄</b>, 전체 시스템 및 통신 인터페이스 설계, Main Server (Backend) 구현, 관제 시스템 설계 및 구현</td>
    </tr>
    <tr>
      <td align="center"><b>App</b></td>
      <td align="center">김윤재</td>
      <td>GUI, QT</td>
    </tr>
    <tr>
      <td align="center"><b>LLM</b></td>
      <td align="center">김재형</td>
      <td>STT, TTS, LLM, VLA</td>
    </tr>
    <tr>
      <td align="center" rowspan="4"><b>Pickee</b><br>(주행 + 상품선택)</td>
      <td align="center">최원호</td>
      <td>SLAM, Nav2, 직원 학습, 직원 추종</td>
    </tr>
    <tr>
      <td align="center">임어진</td>
      <td>ArUco 탐지, 정밀 주차, PD 제어</td>
    </tr>
    <tr>
      <td align="center">이승한</td>
      <td>YOLO, CNN, 데이터 라벨링, IBVS 제어, PID 제어</td>
    </tr>
    <tr>
      <td align="center">류혜진</td>
      <td>Arm 제어, CNN, 데이터 라벨링, IBVS 제어, PID 제어</td>
    </tr>
    <tr>
      <td align="center" rowspan="3"><b>Packee</b><br>(상품적재)</td>
      <td align="center">송원준</td>
      <td>C++ ROS2, 듀얼 로봇팔 제어, CNN 모델 제작/학습, IBVS 제어</td>
    </tr>
    <tr>
      <td align="center">이한수</td>
      <td>객체인식, BPP, MoveIt, MTC</td>
    </tr>
    <tr>
      <td align="center">박대준</td>
      <td>데이터셋 구성 & Arm</td>
    </tr>
  </table>
</div>

---

# 2. 프로젝트 개요

<div align="center">
  <table>
    <tr>
      <td align="center">
        <img src="assets/Chap1/1%20원격%20로봇%20쇼핑%20%26%20오토%20피킹.jpg" width="260"><br>
        <sub>원격 로봇 쇼핑 & 오토 피킹</sub>
      </td>
      <td align="center">
        <img src="assets/Chap1/2%20무인%20자동%20포장%20서비스.jpg" width="260"><br>
        <sub>무인 자동 포장 서비스</sub>
      </td>
      <td align="center">
        <img src="assets/Chap1/3%20AI%20파트너%20%26%20스마트%20직원%20보조.jpg" width="260"><br>
        <sub>AI 파트너 & 스마트 직원 보조</sub>
      </td>
      <td align="center">
        <img src="assets/Chap1/4%20실시간%20통합%20관제%20시스템.jpg" width="260"><br>
        <sub>실시간 통합 관제 시스템</sub>
      </td>
    </tr>
  </table>
</div>

- **프로젝트 목적**
  - 매장 내 쇼핑 과정을 앱과 로봇으로 원격화·자동화하여 고객에게는 실시간 선택·모니터링 경험을 제공하고, 운영 측면에서는 피킹·포장 업무를 효율화
- **프로젝트 기간**
  - 2025.09.10 ~ 2025.11.18 (10주, Sprint1~10)

---

# 3. 주요 기능

## 3-1. 원격 쇼핑 & 피킹

<p align="center">
  <img src="assets/video/pickee.gif" width="20%">
  <br>
  <sub>원격 쇼핑 및 피킹 시연</sub>
</p>

<div align="center">
<table>
  <tr>
    <th style="width:18%">주요 단계</th>
    <th style="width:60%">설명</th>
  </tr>
  <tr>
    <td valign="top">상품 선택</td>
    <td valign="top">고객이 Shopee App/영상으로 상품을 선택하고 주문을 전송합니다.</td>
  </tr>
  <tr>
    <td valign="top">매대 이동</td>
    <td valign="top">Pickee가 Nav2로 매대로 이동하고 장애물을 회피합니다.</td>
  </tr>
  <tr>
    <td valign="top">상품 담기</td>
    <td valign="top">비전/팔 제어로 상품을 집어 장바구니에 담고 완료를 보고합니다.</td>
  </tr>
</table>
</div>


## 3-2. 포장 시나리오

<p align="center">
  <img src="assets/video/packee_packaging.gif" width="40%">
  <br>
  <sub>자동 포장 시연</sub>
</p>

<div align="center">
<table>
  <tr>
    <th style="width:18%">주요 단계</th>
    <th style="width:60%">설명</th>
  </tr>
  <tr>
    <td valign="top">포장대 이동</td>
    <td valign="top">Pickee가 포장대로 이동해 Packee와 장바구니를 교체합니다.</td>
  </tr>
  <tr>
    <td valign="top">장바구니 교체</td>
    <td valign="top">장바구니 상태를 확인하고 Packee에게 포장 준비 완료를 전달합니다.</td>
  </tr>
  <tr>
    <td valign="top">듀얼암 포장</td>
    <td valign="top">Packee 듀얼암이 포장 시퀀스를 수행하고 결과를 보고합니다.</td>
  </tr>
</table>
</div>


## 3-3. 관리자 모니터링

<p align="center">
  <img src="assets/video/monitor.gif" width="60%">
  <br>
  <sub>실시간 모니터링 시연</sub>
</p>

<div align="center">
<table>
  <tr>
    <th style="width:18%">주요 기능</th>
    <th style="width:60%">설명</th>
  </tr>
  <tr>
    <td valign="top">대시보드</td>
    <td valign="top">현재 작업 수·로봇 수, 2D 맵 위치를 실시간 표시합니다.</td>
  </tr>
  <tr>
    <td valign="top">로봇 상태</td>
    <td valign="top">위치·배터리·진행율·현재 작업을 조회합니다.</td>    
  </tr>
  <tr>
    <td valign="top">재고/작업 이력</td>
    <td valign="top">재고 관리, 작업 히스토리 조회를 지원합니다.</td>
  </tr>
</table>
</div>

### 🖥️ 관제 시스템 주요 기능 예시 (Main Service Dashboard Examples)
**Modular UI 기반 통합 관제 시스템**
*(본 대시보드는 로봇 상태, 주문 관리, ROS2/TCP 모니터링 등 다양한 기능을 탭 형태로 제공하며, 아래는 그 중 일부 핵심 기능의 예시입니다.)*

<div align="center">
<table>
  <tr>
    <td align="center" width="100%">
      <img src="assets/images/admin_dashboard_status.png" width="95%"><br>
      <b>1. 로봇 통합 상태 모니터링 (Robot Status)</b>
    </td>
  </tr>
  <tr>
    <td>
      <ul>
        <li><b>실시간 연결 상태</b>: 모든 Pickee/Packee 로봇의 온라인/오프라인/IDLE 상태를 Heartbeat 기반으로 실시간 감시.</li>
        <li><b>상태/위치 정보</b>: 배터리 잔량, 현재 위치(Navigation 좌표), 장바구니 결합 여부 등을 한눈에 파악.</li>
        <li><b>작업 추적</b>: 각 로봇에 할당된 주문 ID(Order ID)와 마지막 통신 시간을 추적하여 시스템 프리징이나 이탈을 즉시 감지.</li>
      </ul>
    </td>
  </tr>
</table>

<table>
  <tr>
    <td align="center" width="50%">
      <img src="assets/images/admin_dashboard_ros2.png" width="100%"><br>
      <b>2. ROS2 서비스/토픽 심층 분석</b>
    </td>
    <td align="center" width="50%">
      <img src="assets/images/admin_dashboard_tcp.png" width="100%"><br>
      <b>3. TCP/IP 데이터 패킷 디버깅</b>
    </td>
  </tr>
  <tr>
    <td valign="top">
      <ul>
        <li><b>서비스 호출 이력</b>: <code>get_location_pose</code>, <code>workflow</code> 등 핵심 로직의 Request/Response 및 수행 시간(Latency)을 기록.</li>
        <li><b>실시간 디버깅</b>: 서비스 실패(Fail) 시 Error Message를 즉시 포착하여 로봇 원격 디버깅 지원.</li>
      </ul>
    </td>
    <td valign="top">
      <ul>
        <li><b>JSON 패킷 모니터링</b>: App-Server-Robot 간 교환되는 <code>order_create</code> 등의 JSON 패킷을 로우 레벨에서 캡처.</li>
        <li><b>데이터 무결성 검증</b>: 송수신 데이터의 스키마 정합성을 실시간으로 확인하여 통신 신뢰성 확보.</li>
      </ul>
    </td>
  </tr>
</table>
</div>

## 3-4. 직원 보조(야간/재고 보충)

<p align="center">
  <img src="assets/video/following.gif" height="300">
  <img src="assets/images/follow.png" height="300">
  <br>
  <sub>직원 추종 및 보조 시연</sub>
</p>

<div align="center">
<table>
  <tr>
    <th style="width:18%">주요 기능</th>
    <th style="width:60%">설명</th>
  </tr>
  <tr>
    <td valign="top">모드 시작</td>
    <td valign="top">야간 모드 시작 및 보조 기능 활성화.</td>
  </tr>
  <tr>
    <td valign="top">Following</td>
    <td valign="top">음성 명령을 LLM이 해석해 follow 모드 전환, 직원 추종.</td>
  </tr>
  <tr>
    <td valign="top">음성 주행</td>
    <td valign="top">장소 명령을 추출해 주행 토픽 발행, Nav2로 지정 위치 이동.</td>
  </tr>
</table>
</div>


---

# 4. 핵심 기술

## 4-1. 자율주행 & 정밀주차 (Pickee Mobile)

<div align="center">
  <table>
    <tr>
      <td align="center">
        <img src="assets/images/정밀주차_순서도_3.png" height="300"><br>
        <sub>정밀 주차 로직</sub>
      </td>
      <td align="center">
        <img src="assets/images/aruco_after.png" height="300"><br>
        <sub>ArUco 인식 전처리 (Grayscale)</sub>
      </td>
    </tr>
  </table>
</div>

- **Nav2 기반 자율 주행**: 목적지까지의 경로 생성 및 장애물 회피 주행. `vel_modifier` 노드를 통해 Nav2의 `/cmd_vel`을 구독, 상황(장애물, 정밀 진입)에 따라 속도를 동적으로 제어하여 안전성 확보.
- **ArUco 마커 정밀 주차**: Nav2 도착 후, 매대에 부착된 ArUco 마커를 인식하여 정밀 위치 보정.
    - **이미지 전처리**: RGB 인식 실패 시, Grayscale 변환 및 이진화를 통해 인식률 향상.
    - **RTR 주행**: Rotate-Translate-Rotate 패턴으로 정밀하게 마커 정렬 수행, 오차 최소화.

## 4-2. 로봇팔 제어 & 보정 (Robot Arm)

<div align="center">
  <table>
    <tr>
      <td align="center">
        <img src="assets/images/vision2.png" height="200"><br>
        <sub>Two-Stream Network Pose 추정</sub>
      </td>
      <td align="center">
        <img src="assets/images/arm5.png" height="200"><br>
        <sub>좌표 보정 및 PD 제어</sub>
      </td>
    </tr>
  </table>
</div>

- **Visual Servoing**: Two-Stream Network를 활용하여 목표 이미지(Target)와 실시간 이미지(Current)의 차이를 최소화하는 방식으로 제어.
- **좌표 보정 및 PD 제어**: 로봇팔이 장착된 카트의 위치가 가변적이므로, 학습된 모델의 목표 좌표와 실제 좌표 간 오차(Error)를 실시간 계산하여 보정. Gaussian 기반 속도 프로파일 적용으로 진동 최소화.

## 4-3. AI & LLM (Vision/Voice)

<div align="center">
  <table>
    <tr>
      <td align="center">
        <img src="assets/images/yolo.png" height="200"><br>
        <sub>YOLOv11 기반 상품 인식</sub>
      </td>
      <td align="center">
        <img src="assets/images/CNN.png" height="200"><br>
        <sub>PoseCNN 6D Pose 추정</sub>
      </td>
    </tr>
  </table>
</div>

- **객체 인식 (Vision)**: YOLOv11 모델을 사용하여 18종의 상품 및 장애물 정밀 탐지. PoseCNN으로 객체의 6D Pose(위치+자세)를 추정하여 로봇팔 파지 좌표 생성.
- **음성 인식 및 안내 (LLM)**: Whisper STT로 노이즈 환경에서도 정확한 발화 인식. Qwen 모델을 QLoRA로 SFT(Fine-tuning)하여, "과자 코너로 가줘"와 같은 불명확한 명령에서도 정확한 장소/의도를 추출, 할루시네이션 방지.



---

# 5. 기술적 문제 및 해결

## 5-1. 아루코 마커 인식 불안정 (정밀 주차)

<div align="center">
  <table>
    <tr>
      <td align="center">
        <img src="assets/images/aruco_before.png" width="300"><br>
        <sub>RGB 원본 (인식 실패)</sub>
      </td>
      <td align="center">
        <img src="assets/images/aruco_after.png" width="300"><br>
        <sub>Grayscale+이진화 (인식 성공)</sub>
      </td>
    </tr>
  </table>
</div>

- **문제**: 조명이나 각도에 따라 RGB 카메라가 마커를 인식하지 못하여 정밀 주차에 실패하는 현상 발생.
- **해결**: 인식 실패 시 **Grayscale 변환 및 이진화 전처리**를 수행하는 폴백(Fallback) 로직 추가. 대비(Contrast)를 높여 마커 인식률을 대폭 향상.

## 5-2. 로봇팔 피킹 오차 및 떨림

<div align="center">
  <table>
    <tr>
      <td align="center">
        <img src="assets/images/arm3.png" width="300"><br>
        <sub>이동형 로봇의 위치 오차 발생</sub>
      </td>
      <td align="center">
        <img src="assets/images/arm4.png" width="300"><br>
        <sub>좌표 차이 계산 및 보정</sub>
      </td>
    </tr>
  </table>
</div>

- **문제**: 로봇(Cart)이 매번 미세하게 다른 위치에 정차하기 때문에, 고정된 학습 좌표를 사용할 경우 피킹 위치가 어긋나는 문제. 팔 끝의 미세한 떨림(Jittering) 발생.
- **해결**:
    1. **실시간 보정**: (현재 로봇 좌표 - 학습된 로봇 좌표) 차이를 계산하여 목표 좌표를 동적으로 수정.
    2. **PD 제어**: Gaussian 기반 가속도 프로파일을 적용하여 부드러운 감속을 유도, 떨림 최소화.

## 5-3. LLM 할루시네이션 (음성 주행)

- **문제**: Base LLM 모델이 "과자 코너"와 같은 모호한 장소 명령을 처리할 때, 존재하지 않는 좌표나 엉뚱한 장소를 반환하는 할루시네이션 발생.
- **해결**: 장소 이동과 관련된 특화 데이터셋 **527건**을 구축하고 **QLoRA SFT (Fine-tuning)** 진행.

| 구분 | 사용자 발화 | LLM 응답 (Action) | 결과 |
| :---: | :--- | :--- | :---: |
| **Before** | "과자로 가줘" | "네, 과자를 드시러 가시나요?" (잡담) | ❌ 실패 |
| **After** | "과자로 가줘" | `{"action": "move", "target": "snack_corner"}` | ✅ 성공 |

## 5-4. 주행 중 동적 속도 제어 한계

- **문제**: Nav2의 기본 설정만으로는 사람이나 장애물 발견 시 즉각적이고 자연스러운 감속/정지가 어려움.
- **해결**: `/cmd_vel` 토픽을 중간에서 가로채는 **`vel_modifier` 노드** 개발. 장애물 거리나 정밀 주차 단계에 따라 속도를 선형적으로 감속하거나 강제 정지시키는 로직 주입.

## 5-5. 직원 인식 및 추종 (Person Tracking)

<p align="center">
  <img src="assets/images/직원복탐지.png" width="80%">
  <br>
  <sub>Shopee 유니폼 YOLO 학습 데이터 및 인식 결과</sub>
</p>

- **문제**: 일반적인 Person Detection 모델 사용 시, 고객과 직원을 구분하지 못해 로봇이 고객을 따라가는 오작동 발생.
- **해결**: Shopee 로고가 부착된 **직원 유니폼** 자체 데이터셋을 구축하여 YOLO 추가 학습(Fine-tuning). 직원(Staff)만 특정하여 인식하고 추종하도록 개선.

---

# 6. 시스템 설계 및 문서

## 6-1. SW Architecture
<div align="center">
  <img src="assets/images/SW_Arc.png" width="80%">
</div>

## 6-2. HW Architecture
<div align="center">
  <img src="assets/images/HW_Arc.png" width="80%">
</div>

## 6-3. Service Flow
<div align="center">
  <table>
    <tr>
      <td align="center">
        <img src="assets/images/서비스흐름_영업중.png" width="80%"><br>
        <sub>주간 (영업 중)</sub>
      </td>
    </tr>
    <tr>
      <td align="center">
        <img src="assets/images/서비스흐름_영업후.png" width="80%"><br>
        <sub>야간 (영업 종료 후)</sub>
      </td>
    </tr>
  </table>
</div>
<br>

## 6-4. State Diagram
<div align="center">
  <img src="assets/images/상태_다이어그램.png" width="80%">
</div>

## 6-5. Sequence Diagram
<details>
<summary> SC01: 상품 주문</summary>
SC-01-01: 로그인

![로그인](assets/images/SC-01-01.png)

SC-01-02: 상품 검색

![상품 검색](assets/images/SC-01-02.png)

SC-01-03: 결제

![결제](assets/images/SC-01-03.png)

</details>
<details>
<summary> SC02: 쇼핑</summary>
SC-02-01: 매대 이동

![매대 이동](assets/images/SC-02-01.png)

SC-02-02: 장애물 회피

![장애물회피1](assets/images/SC-02-02_1.png)

![장애물회피2](assets/images/SC-02-02_2.png)

SC-02-03: 매대 상품 선택

![매대 상품 선택1](assets/images/SC-02-03_1.png)

![매대 상품 선택2](assets/images/SC-02-03_2.png)

SC-02-04: 상품 장바구니 담기

![상품 장바구니 담기](assets/images/SC-02-04.png)

SC-02-05: 쇼핑 종료

![쇼핑 종료](assets/images/SC-02-05.png)

</details>
<details>
<summary> SC03: 상품 포장</summary>
SC-03-01: 포장대 이동

![포장대 이동](assets/images/SC-03-01.png)

SC-03-02: 장바구니 교체

![장바구니 교체](assets/images/SC-03-02.png)

SC-03-03: Packee 작업 가능 확인

![작업 가능 확인](assets/images/SC-03-03.png)

SC-03-04: 상품 포장

![상품 포장](assets/images/SC-03-04.png)

</details>
<details>
<summary> SC04: 복귀 및 충전</summary>

![복귀 및 충전](assets/images/SC-04.png)

</details>
<details>
<summary> SC05: 관리자 기능</summary>
SC-05-01: 관리자 모니터링

로봇 정보 표시

![관리자 모니터링1](assets/images/SC-05-01_1로봇정보표시.png)

로봇 위치 표시

![관리자 모니터링2](assets/images/SC-05-01_2로봇위치표시.png)

로봇 시야 확인

![관리자 모니터링3](assets/images/SC-05-01_3로봇시야확인.png)

로봇 시야 송출 종료

![관리자 모니터링4](assets/images/SC-05-01_4로봇시야송출종료.png)

로봇 상태 조회

![관리자 모니터링5](assets/images/SC-05-01_5로봇상태조회.png)

진행율 확인

![관리자 모니터링6](assets/images/SC-05-01_6진행율확인.png)

SC-05-02: 관리자 재고 관리

재고 정보 조회

![관리자 재고 관리1](assets/images/SC-05-02_1재고정보조회.png)

재고 정보 수정

![관리자 재고 관리2](assets/images/SC-05-02_2재고정보수정.png)

재고 정보 추가

![관리자 재고 관리3](assets/images/SC-05-02_3재고정보추가.png)

재고 정보 삭제

![관리자 재고 관리4](assets/images/SC-05-02_4재고정보삭제.png)

SC-05-03: 관리자 작업 이력 조회

![관리자 작업 이력 조회](assets/images/SC-05-03.png)

</details>
<details>
<summary> SC06: 직원 보조 기능</summary>
SC-06-01: 모드 시작

![모드 시작](assets/images/SC-06-01.png)

SC-06-02: 인식 및 추종

![인식 및 추종1](assets/images/SC-06-02_1.png)

![인식 및 추종1](assets/images/SC-06-02_2.png)

SC-06-03: 음성 명령

![음성 명령](assets/images/SC-06-03.png)

SC-06-04: 목적지 이동

![목적지 이동](assets/images/SC-06-04.png)

SC-06-05: 임무 완료 확인

![임무 완료 확인](assets/images/SC-06-05.png)

</details>

## 6-6. ERD
<div align="center">
  <img src="assets/images/erd.png" width="80%">
</div>

## 6-7. Interface Specification

<details>
<summary> TCP 통신</summary>

| Function | From | To | Message Type | Schema |
|---------|------|----|--------------|--------|
| 사용자 로그인 요청 | App | Main Service | user_login | ```json { "type": "user_login", "data": { "user_id": "string", "password": "string" } }``` |
(표 내용 생략 - 전체 내용은 InterfaceSpecification/App_vs_Main.md 등을 참고)

*상세 내용은 [Interface Specification Document](docs/InterfaceSpecification)를 참고하세요.*
</details>

<details>
<summary> UDP 통신</summary>

#### 통신규약
| 항목 | 내용 |
|------|------|
| Port | 6000 |
| Protocol | UDP |
| Data Format | JSON (메타데이터) + Binary (이미지 데이터) |
| Max Packet Size | 1,600 bytes |

#### 패킷 구조
[ JSON Header (≈200 bytes) ] + [ Binary Image Data (max 1,400 bytes) ]
</details>

<details>
<summary> HTTP 통신 (LLM)</summary>

| Function | Endpoint | Request | Response |
|---|---|---|---|
| 상품 검색 쿼리 | GET /llm/search_query | `{"text": "사과 찾아줘"}` | `{"sql_query": "name LIKE '%사과%'"}` |
| 발화 의도 분석 | GET /llm/intent_detection | `{"text": "피키야 이리로 와"}` | `{"intent": "Move_place", ...}` |

</details>

<details>
<summary> ROS2 통신</summary>

### Main <-> Pic Main
| Function | Topic | Message Type | From | To |
|---|---|---|---|---|
| 이동 시작 알림 | /pickee/moving_status | PickeeMoveStatus | Pic Main | Main |
| 도착 보고 | /pickee/arrival_notice | PickeeArrival | Pic Main | Main |
| 로봇 상태 전송 | /pickee/robot_status | PickeeRobotStatus | Pic Main | Main |
| 작업 시작 명령 | /pickee/workflow/start_task | PickeeWorkflowStartTask (Srv) | Main | Pic Main |

### Pic Main <-> Pic Vision
| Function | Topic | Message Type |
|---|---|---|
| 매대 상품 인식 | /pickee/vision/detection_result | PickeeVisionDetection |
| 장애물 감지 | /pickee/vision/obstacle_detected | PickeeVisionObstacles |

### Pic Main <-> Pac Main
| Function | Topic | Message Type |
|---|---|---|
| 포장 완료 알림 | /packee/packing_complete | PackeePackingComplete |
| 작업 가능 확인 | /packee/packing/check_availability | PackeePackingCheckAvailability (Srv) |

</details>

---

# 7. 프로젝트 구조
```
Shopee/
├── README.md                # Shopee 개요 (영문 Main)
├── README_kr.md             # Shopee 개요 (국문 Backup)
├── shopee_ros2/             # ROS2 워크스페이스 (주행·팔·비전·Main·App·인터페이스)
├── shopee_llm/              # LLM/STT 학습·서빙 리소스
├── docs/                    # 요구사항/설계/인터페이스/다이어그램/코딩 표준
├── assets/                  # 배너/이미지/GIF
└── AGENTS.md                # 작업 지침
```

---

# 8. 기술 스택

| 분류 | 사용 기술 |
|------|-----------|
| **OS / Platform** | [![Ubuntu](https://img.shields.io/badge/Ubuntu%2022.04-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)](https://ubuntu.com/) [![ROS2](https://img.shields.io/badge/ROS2%20Humble-22314E?style=for-the-badge&logo=ros&logoColor=white)](https://docs.ros.org/en/humble/) |
| **Language** | [![Python](https://img.shields.io/badge/Python%203.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/) [![C++](https://img.shields.io/badge/C++%2017-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white)](https://isocpp.org/) |
| **AI / LLM** | [![YOLOv11](https://img.shields.io/badge/YOLOv11-00FFFF?style=for-the-badge&logo=yolo&logoColor=black)](https://github.com/ultralytics/ultralytics) ![PoseCNN](https://img.shields.io/badge/PoseCNN-FF6F00?style=for-the-badge) ![Whisper](https://img.shields.io/badge/OpenAI%20Whisper-412991?style=for-the-badge&logo=openai&logoColor=white) ![Qwen](https://img.shields.io/badge/Qwen_2.5_7B-000000?style=for-the-badge) |
| **Robotics** | [![Nav2](https://img.shields.io/badge/Nav2-D33825?style=for-the-badge)](https://navigation.ros.org/) [![MoveIt 2](https://img.shields.io/badge/MoveIt%202-5C4EE5?style=for-the-badge)](https://moveit.ros.org/) [![OpenCV](https://img.shields.io/badge/OpenCV-5C3EE8?style=for-the-badge&logo=opencv&logoColor=white)](https://opencv.org/) ![Visual Servoing](https://img.shields.io/badge/Visual%20Servoing-008000?style=for-the-badge) |
| **DB / Server** | [![MySQL](https://img.shields.io/badge/MySQL%208.0-4479A1?style=for-the-badge&logo=mysql&logoColor=white)](https://www.mysql.com/) [![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com/) ![TCP/IP](https://img.shields.io/badge/TCP%2FIP-000000?style=for-the-badge) |
| **Tools** | [![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)](https://git-scm.com/) [![Jira](https://img.shields.io/badge/Jira-0052CC?style=for-the-badge&logo=jira&logoColor=white)](https://www.atlassian.com/software/jira) [![Confluence](https://img.shields.io/badge/Confluence-172B4D?style=for-the-badge&logo=confluence&logoColor=white)](https://www.atlassian.com/software/confluence) [![Slack](https://img.shields.io/badge/Slack-4A154B?style=for-the-badge&logo=slack&logoColor=white)](https://slack.com/) [![Qt](https://img.shields.io/badge/Qt_(PySide6)-41CD52?style=for-the-badge&logo=qt&logoColor=white)](https://www.qt.io/) |

---

# 9. 실행·개발 가이드
- ROS2 워크스페이스 빌드/실행/테스트는 `shopee_ros2/README.md` 참고
  ```bash
  cd shopee_ros2
  rosdep install --from-paths src --ignore-src -r -y
  colcon build
  source install/setup.bash
  ```
- 패키지별 상세 가이드는 `shopee_ros2/src/<패키지>/README.md`에서 확인
- 코딩 표준: `docs/CodingStandard/standard.md` (ROS2/Python/C++ 네이밍·주석 규칙 준수)

---

# 10. 프로젝트 관리

## 1. 프로젝트 일정 관리 (Jira)

<table>
  <tr>
    <td align="center" width="400" valign="top">
      <img src="assets/images/jira.png" width="500">
    </td>
    <td align="left" valign="top">
      ▪ <b>총 10주 (2024.09.10 ~ 2024.11.18)</b><br>
      ▪ <b>Sprint 1</b>: 주제 선정 / 기획 / 요구사항 정의<br>
      ▪ <b>Sprint 2~4</b>: 설계 / 기술조사<br>
      ▪ <b>Sprint 5</b>: 통신 구현<br>
      ▪ <b>Sprint 6~9</b>: 기능 구현 및 연동 테스트<br>
      ▪ <b>Sprint 10</b>: 발표 자료
    </td>
  </tr>
</table>

## 2. 프로젝트 문서 관리 (Confluence)

<table>
  <tr>
    <td align="center" width="400" valign="top">
      <img src="assets/images/confluence.png" width="500">
    </td>
    <td align="left" valign="top">
      ▪ <b>Confluence 문서 관리</b><br>
      ▪ 기획서, 설계서, 회의록 등 프로젝트 산출물 통합 관리<br>
      ▪ 팀원 간 기술 공유 및 트러블 슈팅 기록
    </td>
  </tr>
</table>

---

# 11. 라이선스

이 프로젝트는 [Apache License 2.0](LICENSE)에 따라 오픈소스로 제공됩니다.
자세한 사항은 [`LICENSE`](LICENSE) 파일을 참고해주세요.
