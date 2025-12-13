<p align="center">
  <img src="https://github.com/addinedu-roscamp-7th/roscamp-repo-1/blob/main/assets/images/banner.jpg?raw=true" alt="Banner">
</p>

<p align="center">
  <a href="https://docs.google.com/presentation/d/1-Q_TZLXfFrFoZFN47uKtgcyI_h5BXLpoyHWAMogy4Dw/edit?slide=id.p#slide=id.p">
    <img src="https://img.shields.io/badge/PRESENTATION-GoogleSlides-yellow?style=for-the-badge&logo=google-slides&logoColor=white" alt="발표자료">
  </a>
  <a href="docs/README.md">
    <img src="https://img.shields.io/badge/DOCS-Architecture%20%26%20Requirements-blue?style=for-the-badge" alt="설계문서">
  </a>
</p>

# 원격 쇼핑 로봇 플랫폼 Shopee

## 📚 목차
- [1. 프로젝트 개요](#1-프로젝트-개요)
- [2. 주요 기능](#2-주요-기능)
- [3. 핵심 기술](#3-핵심-기술)
- [4. 기술적 문제 및 해결](#4-기술적-문제-및-해결)
- [5. 시스템 설계 및 문서](#5-시스템-설계-및-문서)
- [6. 프로젝트 구조](#6-프로젝트-구조)
- [7. 기술 스택](#7-기술-스택)
- [8. 실행·개발 가이드](#8-실행·개발-가이드)
- [9. 프로젝트 관리](#9-프로젝트-관리)
- [10. 팀](#10-팀)

---

# 1. 프로젝트 개요

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

# 2. 주요 기능

## 2-1. 원격 쇼핑 & 피킹

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


## 2-2. 포장 시나리오

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


## 2-3. 관리자 모니터링

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

## 2-4. 직원 보조(야간/재고 보충)

<p align="center">
  <img src="assets/video/following.gif" width="30%">
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

# 3. 핵심 기술

## 3-1. 자율주행 & 정밀주차 (Pickee Mobile)

<div align="center">
  <table>
    <tr>
      <td align="center">
        <img src="assets/images/정밀주차_순서도_3.png" height="200"><br>
        <sub>정밀 주차 로직</sub>
      </td>
      <td align="center">
        <img src="assets/images/aruco_after.png" height="200"><br>
        <sub>ArUco 인식 전처리 (Grayscale)</sub>
      </td>
    </tr>
  </table>
</div>

- **Nav2 기반 자율 주행**: 목적지까지의 경로 생성 및 장애물 회피 주행. `vel_modifier` 노드를 통해 Nav2의 `/cmd_vel`을 구독, 상황(장애물, 정밀 진입)에 따라 속도를 동적으로 제어하여 안전성 확보.
- **ArUco 마커 정밀 주차**: Nav2 도착 후, 매대에 부착된 ArUco 마커를 인식하여 정밀 위치 보정.
    - **이미지 전처리**: RGB 인식 실패 시, Grayscale 변환 및 이진화를 통해 인식률 향상.
    - **RTR 주행**: Rotate-Translate-Rotate 패턴으로 정밀하게 마커 정렬 수행, 오차 최소화.

## 3-2. 로봇팔 제어 & 보정 (Robot Arm)

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

## 3-3. AI & LLM (Vision/Voice)

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

# 4. 기술적 문제 및 해결
- **아루코 인식 불안정** → RGB 실패 시 Grayscale+이진화 재시도, 재인식률 향상.
- **동적 속도 제어** → Nav2 출력을 변환해 감속·정지 토픽 제공, 장애물 대응성 개선.
- **피킹 오차** → 현재 좌표-목표 좌표 차이 기반 보정 + PD 제어로 미세 오차 감소.
- **LLM 할루시네이션** → 장소 이동 데이터 527건으로 QLoRA SFT, 명령 추출 안정화.

---

# 5. 시스템 설계 및 문서

<div align="center">
  <img src="assets/images/SW_Arc.png" width="80%"><br>
  <sub>SW 아키텍처 다이어그램</sub>
</div>

- **마이크로서비스 구조**: Main, Pickee, Packee, App이 독립적인 서비스로 동작하며 유연한 연결 지원.
- **복합 통신 인터페이스**:
    - **ROS2**: 로봇 내부 노드 간 고속 통신 (Nav2, MoveIt, Vision).
    - **TCP/UDP**: App-Server 간 신뢰성 데이터 전송 및 영상 스트리밍.
    - **REST API**: LLM 서비스 등 외부 모듈 연동.

<br>

- 요구사항: [사용자 요구사항](docs/Requirements/UserRequirements.md), [시스템 요구사항](docs/Requirements/SystemRequirements.md)
- 아키텍처: [SW 아키텍처](docs/Architecture/SWArchitecture.md), [HW 아키텍처](docs/Architecture/HWArchitecture.md)
- 인터페이스: [App ↔ Main](docs/InterfaceSpecification/App_vs_Main.md), [Main ↔ Pickee](docs/InterfaceSpecification/Main_vs_Pic_Main.md), [Main ↔ Packee](docs/InterfaceSpecification/Main_vs_Pac_Main.md), [Pac Main ↔ Pac Arm](docs/InterfaceSpecification/Pac_Main_vs_Pac_Arm.md) 등
- 시퀀스/상태/ERD: [시퀀스 다이어그램](docs/SequenceDiagram), [상태 다이어그램](docs/StateDiagram), [ERD](docs/ERDiagram/ERDiagram.md)
- 개발 계획: [Main Service](docs/DevelopmentPlan/MainService), [Pickee](docs/DevelopmentPlan/PickeeMain), [Packee](docs/DevelopmentPlan/PackeeMain)

---

# 6. 프로젝트 구조
```
Shopee/
├── README.md                # Shopee 개요 (본 문서)
├── README_legacy.md         # 이전 버전 백업
├── README_roomie.md         # Roomie(호텔 로봇) 별도 프로젝트 문서
├── shopee_ros2/             # ROS2 워크스페이스 (주행·팔·비전·Main·App·인터페이스)
├── shopee_llm/              # LLM/STT 학습·서빙 리소스
├── docs/                    # 요구사항/설계/인터페이스/다이어그램/코딩 표준
├── assets/                  # 배너/이미지/GIF
└── AGENTS.md                # 작업 지침
```

---

# 7. 기술 스택
| 분류 | 내용 |
| --- | --- |
| OS/플랫폼 | Ubuntu, ROS2 |
| 언어 | Python, C++ |
| AI/LLM | YOLOv8/YOLOv11, PoseCNN, Two-Stream Network, Whisper, Qwen + QLoRA |
| 로봇 | Nav2, MoveIt, ArUco, Visual Servoing |
| DB/서버 | MySQL, TCP/UDP 브릿지, FastAPI |
| UI/도구 | Qt(Python), Slack/Jira/Confluence |

---

# 8. 실행·개발 가이드
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

# 9. 프로젝트 관리
- Sprint: 10주(기획→설계→통신→기능 구현/연동→발표)
- 협업: GitHub, Slack, Jira, Confluence
- 산출물: 요구사항/설계/인터페이스 명세, 시퀀스/상태/ERD, 테스트/데모

---

# 10. 팀
| 파트 | 이름 |
| --- | --- |
| App | 김윤재 |
| Main | 장진혁 |
| LLM | 김재형 |
| Pickee 주행 | 최원호, 임어진 |
| Pickee 상품선택 | 이승한, 류혜진 |
| Packee | 송원준, 이한수, 박대준 |
