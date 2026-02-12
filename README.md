# K-Stay

**AI 기반 한국 비자 서류 자동 작성 플랫폼**

<br/>
<div align="center">
  <h2 K-E Audio Benchmark Project</h2>
  <p><strong>외국인의 한국 체류와 관련된 복잡한 행정 절차를 AI 기반 자동화로 단순화하는 서비스</strong></p>
</div>

<br/>




## 👥 타겟 사용자

### Primary Target

| 페르소나  | 특징                      | Pain Point              |
| ----- | ----------------------- | ----------------------- |
| 유학생   | D-2/D-4 비자, 아르바이트·연장 필요 | 한국어 서류 작성 어려움, 행정 절차 복잡 |
| 구직자   | D-10 비자 신청/연장           | 구직활동계획서 작성 방법 이해 부족     |
| 결혼이민자 | F-6 비자, 가족 초청 필요        | 초청장·필수서류 구조 파악 어려움      |

### Secondary Target

* 긴급 의료 대상자 (C-3-3 / G-1-10)
* 국적 귀화 신청자
* 단기 방문자 (K-ETA 대상)

---

## 🧱 서비스 구조 아키텍처

### 1. Universal Fact (1회 입력, 전 서류 자동 반영)

* 인적사항: 성명, 생년월일, 성별, 국적
* 여권정보: 여권번호, 발급일, 만료일
* 연락처: 한국주소, 전화번호

### 2. Variable Fact (시나리오별 입력)

* 체류정보
* 신청정보
* 보증인 정보
* 시나리오 전용 항목

### 3. Narrative Layer (AI 서술 검토 영역)

* 체류 목적
* 월별 계획
* 구직 활동 서술
* 초청 사유

### 4. Document Output

* 통합신청서
* 구직활동계획서
* 신원보증서
* 초청장
* 기타 비자별 서류

---

## 🔁 데이터 매핑 로직

| 구분             | 입력 시점     | 재사용성         | 예시        |
| -------------- | --------- | ------------ | --------- |
| Universal Fact | 회원가입      | 모든 서류 자동 반영  | 성명, 여권번호  |
| Variable Fact  | 시나리오 선택 후 | 해당 시나리오 내 공유 | 체류기간, 보증인 |
| Narrative      | STEP 3    | 단일 문서 반영     | 체류목적, 계획서 |

---

## 🧭 사용자 플로우

```
Landing
  ↓
회원가입 → Universal Fact 입력
  ↓
메인 대시보드
  ├ K-ETA 안내
  ├ 시나리오 선택
  │   ↓
  │ STEP 1 Universal Fact 확인
  │ STEP 2 Variable Fact 입력
  │ STEP 3 Narrative + AI 검토
  │ STEP 4 결제 & 서류 생성
  │
  └ AI 상담사 (RAG 기반)
```

---

## 🤖 AI 검토 시스템

### 검토 항목

* 문법·맞춤법 검사
* 필수 키워드 포함 여부
* 분량 기준 충족 여부
* 논리적 일관성 분석

### 결과 구조

* ✅ 통과
* ⚠️ 수정 권장 (구체적 피드백)
* ❌ 재작성 필요 (문제점 구조화 제시)

---

## 🗂 시나리오 카탈로그

### Track 우선순위 구조

| Track | 시나리오  | 서류 수 | 우선순위 |
| ----- | ----- | ---- | ---- |
| 구직 준비 | D-10  | 3    | P0   |
| 아르바이트 | 허가 신청 | 3    | P0   |
| 가족 초청 | F-1-5 | 3    | P1   |
| 긴급 의료 | 의료 체류 | 3    | P1   |
| 국적 귀화 | 귀화    | 2    | P2   |

---

## 📄 D-10 시나리오 구조 예시

### 포함 서류

* 통합신청서
* 구직활동계획서
* 신원보증서
* 이력서
* 자기소개서

### Variable Fact (32개)

* 통합신청서: 11개
* 구직활동계획서: 10개
* 신원보증서: 11개

### Narrative (7개)

* 체류목적
* 1~6개월차 계획

---

## 🧠 AI 상담사 (RAG 시스템)

### 지원 비자 범위

* D-2, D-4, D-10, F-6, C-4, K-ETA 등

### 구조

```
사용자 질문
 → Query 분류
 → Vector DB 검색 (법령/고시/FAQ)
 → Context 구성
 → LLM 응답 생성
 → Citation 포함 출력
```



---

## 🧩 기술 스택 개념 구조

* LLM 기반 서술 검토
* RAG 기반 법령 QA
* 시나리오 기반 데이터 구조화
* 문서 자동 생성 파이프라인
* 다국어 입력 처리 구조

---

## 🚀 확장 로드맵

### Phase 1

* D-10 / D-2 / F-6 핵심 시나리오

### Phase 2

* 의료, 귀화, 초청 자동화

### Phase 3

* 출입국 시스템 연동 API
* 공공기관 연계

---


## 🏷️ 키워드

`AI Document Automation`
`Visa Process Automation`
`Immigration Tech`
`RAG System`
`Scenario-based AI`
`Administrative AI`

---

---

## ▶ 실행 방법 (Run)

```bash
# 1. 저장소 클론
git clone https://github.com/your-org/k-stay.git
cd k-stay

# 2. 가상환경 생성
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# 3. 서버 실행
python main.py
```

---



© K-Stay Project
