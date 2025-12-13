![Banner](https://github.com/addinedu-roscamp-7th/roscamp-repo-1/blob/main/assets/images/banner.jpg?raw=true)

<p align="center">
  <a href="https://docs.google.com/presentation/d/1-Q_TZLXfFrFoZFN47uKtgcyI_h5BXLpoyHWAMogy4Dw/edit?slide=id.p#slide=id.p">
    <img src="https://img.shields.io/badge/PRESENTATION-GoogleSlides-yellow?style=for-the-badge&logo=google-slides&logoColor=white" alt="발표자료">
  </a>
  <a href="docs/README.md">
    <img src="https://img.shields.io/badge/DOCS-Architecture%20%26%20Requirements-blue?style=for-the-badge" alt="설계문서">
  </a>
</p>

# Shopee 로봇 쇼핑 시스템

원격 쇼핑·상품 피킹·포장을 통합 제공하는 ROS2 기반 쇼핑 로봇 플랫폼입니다. Shopee App(고객/관리자), Main Service(중앙 제어), Pickee(주행·피킹), Packee(포장), LLM 서비스가 연동되어 요구사항 전주기를 지원합니다.

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

| 항목 | 내용 |
| --- | --- |
| 기간 | 2025.09.10 ~ 2025.11.18 (10주, Sprint1~10) |
| 목표 | 쇼핑몰 내 원격 쇼핑 경험 제공: 상품 탐색 → 실시간 선택 → 자동 피킹 → 포장/배송 |
| 구성 | Shopee App, Main Service, Pickee(주행·피킹), Packee(포장), LLM 서비스 |
| 요구사항 요약 | 고객: 상품 탐색·선택·모니터링 / 직원: 포장·재고 보충 / 관리자: 주문·작업·로봇 관리 |

---

# 2. 주요 기능

## 2-1. 원격 쇼핑 & 피킹

<table>
  <tr>
    <th style="width:18%">주요 단계</th>
    <th style="width:60%">설명</th>
    <th style="width:22%">이미지</th>
  </tr>
  <tr>
    <td valign="top">상품 선택</td>
    <td valign="top">고객이 Shopee App/영상으로 상품을 선택하고 주문을 전송합니다.</td>
    <td valign="top" align="center"><img src="assets/images/SC-02-03_1.png" width="220"></td>
  </tr>
  <tr>
    <td valign="top">매대 이동</td>
    <td valign="top">Pickee가 Nav2로 매대로 이동하고 장애물을 회피합니다.</td>
    <td valign="top" align="center"><img src="assets/images/SC-02-01.png" width="220"></td>
  </tr>
  <tr>
    <td valign="top">상품 담기</td>
    <td valign="top">비전/팔 제어로 상품을 집어 장바구니에 담고 완료를 보고합니다.</td>
    <td valign="top" align="center"><img src="assets/images/SC-02-04.png" width="220"></td>
  </tr>
</table>

## 2-2. 포장 시나리오

<table>
  <tr>
    <th style="width:18%">주요 단계</th>
    <th style="width:60%">설명</th>
    <th style="width:22%">이미지</th>
  </tr>
  <tr>
    <td valign="top">포장대 이동</td>
    <td valign="top">Pickee가 포장대로 이동해 Packee와 장바구니를 교체합니다.</td>
    <td valign="top" align="center"><img src="assets/images/SC-03-01.png" width="220"></td>
  </tr>
  <tr>
    <td valign="top">장바구니 교체</td>
    <td valign="top">장바구니 상태를 확인하고 Packee에게 포장 준비 완료를 전달합니다.</td>
    <td valign="top" align="center"><img src="assets/images/SC-03-02.png" width="220"></td>
  </tr>
  <tr>
    <td valign="top">듀얼암 포장</td>
    <td valign="top">Packee 듀얼암이 포장 시퀀스를 수행하고 결과를 보고합니다.</td>
    <td valign="top" align="center"><img src="assets/images/SC-03-04.png" width="220"></td>
  </tr>
</table>

## 2-3. 관리자 모니터링

<table>
  <tr>
    <th style="width:18%">주요 기능</th>
    <th style="width:60%">설명</th>
    <th style="width:22%">이미지</th>
  </tr>
  <tr>
    <td valign="top">대시보드</td>
    <td valign="top">현재 작업 수·로봇 수, 2D 맵 위치를 실시간 표시합니다.</td>
    <td valign="top" align="center"><img src="assets/images/SC-05-01_1로봇정보표시.png" width="220"></td>
  </tr>
  <tr>
    <td valign="top">로봇 상태</td>
    <td valign="top">위치·배터리·진행율·현재 작업을 조회합니다.</td>
    <td valign="top" align="center"><img src="assets/images/SC-05-01_6진행율확인.png" width="220"></td>
  </tr>
  <tr>
    <td valign="top">재고/작업 이력</td>
    <td valign="top">재고 관리, 작업 히스토리 조회를 지원합니다.</td>
    <td valign="top" align="center"><img src="assets/images/SC-05-02_1재고정보조회.png" width="220"></td>
  </tr>
</table>

## 2-4. 직원 보조(야간/재고 보충)

<table>
  <tr>
    <th style="width:18%">주요 기능</th>
    <th style="width:60%">설명</th>
    <th style="width:22%">이미지</th>
  </tr>
  <tr>
    <td valign="top">모드 시작</td>
    <td valign="top">야간 모드 시작 및 보조 기능 활성화.</td>
    <td valign="top" align="center"><img src="assets/images/SC-06-01.png" width="220"></td>
  </tr>
  <tr>
    <td valign="top">Following</td>
    <td valign="top">음성 명령을 LLM이 해석해 follow 모드 전환, 직원 추종.</td>
    <td valign="top" align="center"><img src="assets/images/SC-06-02_2.png" width="220"></td>
  </tr>
  <tr>
    <td valign="top">음성 주행</td>
    <td valign="top">장소 명령을 추출해 주행 토픽 발행, Nav2로 지정 위치 이동.</td>
    <td valign="top" align="center"><img src="assets/images/SC-06-04.png" width="220"></td>
  </tr>
</table>

---

# 3. 핵심 기술
- **자율주행**: Nav2 전역/지역 경로 계획, RTR(Rotate–Translate–Rotate) 정밀 정렬, /cmd_vel → /cmd_vel_modified 변환 노드로 동적 감속/정지.
- **정밀 주차**: 아루코 마커 인식 실패 시 Grayscale+이진화 재시도, 마커 좌표계 변환으로 x/y/yaw 오차 최소화.
- **비전/포즈 추정**: YOLOv8/YOLOv11 상품·장애물 감지, PoseCNN+Two-Stream Network로 6D Pose 추정 및 Visual Servoing(동일 시야 달성까지 반복 제어).
- **로봇팔 제어**: 목표 좌표 보정 후 PD 제어, 듀얼암 시퀀스 기반 포장, 버튼/시퀀스 안전 제어.
- **LLM/STT**: Whisper STT, QLoRA SFT(Qwen)로 장소 추출 정확도 개선, Tool Calling 기반 서비스/토픽 호출.
- **인터페이스**: shopee_interfaces 메시지/서비스 정의, App/Main/Pickee/Packee 간 TCP/UDP/ROS2 브릿지.

---

# 4. 기술적 문제 및 해결
- **아루코 인식 불안정** → RGB 실패 시 Grayscale+이진화 재시도, 재인식률 향상.
- **동적 속도 제어** → Nav2 출력을 변환해 감속·정지 토픽 제공, 장애물 대응성 개선.
- **피킹 오차** → 현재 좌표-목표 좌표 차이 기반 보정 + PD 제어로 미세 오차 감소.
- **LLM 할루시네이션** → 장소 이동 데이터 527건으로 QLoRA SFT, 명령 추출 안정화.

---

# 5. 시스템 설계 및 문서
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
