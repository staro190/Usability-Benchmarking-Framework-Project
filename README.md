# Usability-Benchmarking-Framework-Project
Evaluation of Software Manuals Using LLM-Powered GUI Agents: A Usability Benchmarking Framework

## 프로젝트 목적
1. 소프트웨어 설명서를 따라 GUI 소프트웨어를 사용할 수 있는 LLM 기반 GUI 에이전트 개발(HTML 등 사용 안함, 비전 중심)
2. 모듈형으로 LLM, GUI 인식 비전 모델 등을 교체할 수 있도록 설계
3. 소프트웨어 설명서, GUI 소프트웨어(web 포함) 쌍 한국어 평가셋 수집(유사 태스크 조건 n=5)
4. 소프트웨어 사용성 평가 자동화 벤치마크 시행 및 사람과 비교

## LLM GUI 에이전트
에이전트 구조
1. 구성요소
- 비전 모델(VLM, UI 인식 모델 등)
- LLM
- 에이전트

2. 동작 흐름(자료 추가 조사중)
- 에이전트 : 설명서의 사용 절차를 제외한 일반 내용(소프트웨어 목적 등) 전달 -> LLM
- LLM : 소프트웨어의 내용에 대한 프롬프트 입력(사전 정보 제공)
- 에이전트 : 설명서 인식 및 세부 작업 분할 요청 -> LLM
- LLM : 최소 단위까지 작업 분할 및 내용 전달
- 에이전트 : 소프트웨어 화면 인식 요청 -> 비전 모델
- 비전 모델 : 소프트웨어 GUI 화면의 각 요소 인식 및 위치/상세(VLM) 정보 반환
- 에이전트 : 최소 단위 작업을 확인하며 현재 가장 필요한 상호작용 UI가 무엇인지 확인함
- IF 복잡한 UI ==> 입력폼, 콤보박스 등 유저의 입력이 필요한 UI의 경우
- IF 원하는 UI 없음 ==> LLM이 지시한 UI 중 적절한 정보가 없을 경우
- 위 2개의 케이스의 경우 비전 모델의 정보를 LLM에 피드백하여 작업을 수정할 것을 요청
  
3. 모듈형
- LLM 교체 가능하도록 설계(강한 연결을 하지 않고 자연어로 데이터만 주고받도록 설계)
- 비전 모델 교체 가능하도록 설계(표준 데이터 송수신 형식을 설정하여 범용적으로 사용하도록 설계)

## 평가 프레임워크
ISO/IEC 25023 Usability 기준(대응 국내 표준 KS X ISO/IEC 25023)
1. 평가 항목
- KS X ISO/IEC 25023, 8.5.2 Learnability Measures, ULe-1-G User Guidance Completeness [사용자 문서화, 도움말 등에서 사용자가 그 기능을 적용하기 쉽도록 충분히 자세하게 설명되어 있는 기능의 비율]
- KS X ISO/IEC 25023, 8.5.2 Learnability Measures, ULe-4-S Self-Explanatory User Interface [사전 학습 및 훈련 없이 통상 태스크를 완료할 수 있도록 사용자에게 제시되는 정보 요소 및 단계의 비율]

2. 평가셋 구성
- 수집 중

3. 평가 요소
- 에이전트 수행 시간
- 에이전트 피드백 요청 횟수
