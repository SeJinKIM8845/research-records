# Ground Control Station 
GCS_Project/
├── README.md                     # 프로젝트 설명, 설치 방법, 사용법 등
├── requirements.txt              # 필요한 Python 패키지 목록
├── setup.py                      # 패키지 설치 스크립트
├── version.py                    # 버전 정보 및 릴리스 노트
├── .gitignore                    # Git 무시 파일 목록
├── docs/                         # 문서화
│   ├── protocol_specification.md # 프로토콜 명세
│   ├── architecture.md           # 시스템 아키텍처 문서
│   ├── api_docs.md               # API 문서
│   └── user_manual.md            # 사용자 매뉴얼
│
├── gcs/                          # 메인 패키지
│   ├── __init__.py               # 패키지 초기화, 버전 정보
│   ├── main.py                   # 프로그램 진입점
│   ├── config.py                 # 전역 설정 및 기본값
│   │
│   ├── communication/            # 통신 관련 모듈
│   │   ├── __init__.py
│   │   ├── serial_manager.py     # 시리얼 통신 관리
│   │   ├── async_serial.py       # 비동기 시리얼 통신 지원
│   │   └── message_queue.py      # 메시지 큐 관리
│   │
│   ├── protocol/                 # 프로토콜 인코딩/디코딩
│   │   ├── __init__.py
│   │   ├── parser.py             # 기본 프레임 파서
│   │   ├── frame.py              # 프레임 구조 정의
│   │   ├── message_types.py      # 메시지 타입 정의
│   │   ├── ahrs.py               # AHRS 데이터 처리
│   │   ├── gps.py                # GPS 데이터 처리
│   │   ├── pid.py                # PID 게인 메시지 처리
│   │   ├── motor.py              # 모터 제어 메시지 처리
│   │   ├── rc.py                 # RC 입력 메시지 처리
│   │   └── checksum.py           # 체크섬 계산 및 검증
│   │
│   ├── models/                   # 데이터 모델
│   │   ├── __init__.py
│   │   ├── drone_state.py        # 드론 상태 모델
│   │   ├── telemetry.py          # 텔레메트리 데이터 모델
│   │   ├── flight_modes.py       # 비행 모드 정의
│   │   └── config_model.py       # 설정 데이터 모델
│   │
│   ├── ui/                       # 사용자 인터페이스
│   │   ├── __init__.py
│   │   ├── main_window.py        # 메인 윈도우 클래스
│   │   ├── connection_panel.py   # 연결 설정 패널
│   │   ├── data_view.py          # 데이터 표시 뷰
│   │   ├── command_panel.py      # 명령 입력 패널
│   │   ├── styles.py             # UI 스타일 정의
│   │   ├── dialogs/              # 대화상자
│   │   │   ├── __init__.py
│   │   │   ├── settings_dialog.py  # 설정 대화상자
│   │   │   └── about_dialog.py     # 정보 대화상자
│   │   │
│   │   └── widgets/              # 사용자 정의 위젯
│   │       ├── __init__.py
│   │       ├── attitude_indicator.py  # 자세 표시 위젯
│   │       ├── graph_widget.py        # 그래프 위젯
│   │       ├── map_widget.py          # 지도 위젯
│   │       ├── pid_tuning_widget.py   # PID 튜닝 위젯
│   │       └── status_bar.py          # 상태 표시줄
│   │
│   ├── logic/                    # 비즈니스 로직
│   │   ├── __init__.py
│   │   ├── data_manager.py       # 데이터 관리 및 처리
│   │   ├── command_manager.py    # 명령 생성 및 처리
│   │   ├── flight_controller.py  # 비행 제어 로직
│   │   ├── mission_planner.py    # 미션 계획 로직
│   │   └── state_monitor.py      # 상태 모니터링 및 알림
│   │
│   ├── plugins/                  # 플러그인 시스템
│   │   ├── __init__.py
│   │   ├── plugin_manager.py     # 플러그인 로딩 및 관리
│   │   ├── plugin_interface.py   # 플러그인 인터페이스 정의
│   │   └── default_plugins/      # 기본 제공 플러그인
│   │       ├── __init__.py
│   │       ├── data_recorder.py  # 데이터 기록 플러그인
│   │       └── simulator.py      # 시뮬레이터 플러그인
│   │
│   └── utils/                    # 유틸리티 모듈
│       ├── __init__.py
│       ├── logger.py             # 로깅 유틸리티
│       ├── validators.py         # 데이터 검증 유틸리티
│       ├── unit_conversion.py    # 단위 변환 유틸리티
│       ├── math_utils.py         # 수학 관련 유틸리티
│       └── file_utils.py         # 파일 처리 유틸리티
│
├── resources/                    # 리소스 파일
│   ├── icons/                    # 아이콘
│   ├── config/                   # 설정 파일 템플릿
│   │   ├── default_config.json   # 기본 설정
│   │   └── protocol_defs.json    # 프로토콜 정의
│   └── sample_data/              # 샘플 데이터 파일
│
├── logs/                         # 로그 디렉토리
│   └── .gitkeep                  # Git에서 빈 디렉토리 유지용
│
└── tests/                        # 테스트 코드
    ├── __init__.py
    ├── conftest.py               # pytest 설정
    ├── test_protocol/            # 프로토콜 테스트
    │   ├── __init__.py
    │   ├── test_parser.py
    │   ├── test_frame.py
    │   └── test_checksum.py
    ├── test_communication/       # 통신 테스트
    │   ├── __init__.py
    │   ├── test_serial_manager.py
    │   └── test_message_queue.py
    ├── test_logic/               # 로직 테스트
    │   ├── __init__.py
    │   ├── test_data_manager.py
    │   └── test_command_manager.py
    ├── test_models/              # 모델 테스트
    │   ├── __init__.py
    │   └── test_drone_state.py
    ├── test_ui/                  # UI 테스트
    │   ├── __init__.py
    │   └── test_widgets.py
    ├── test_utils/               # 유틸리티 테스트
    │   ├── __init__.py
    │   └── test_validators.py
    └── integration_tests/        # 통합 테스트
        ├── __init__.py
        └── test_full_workflow.py
