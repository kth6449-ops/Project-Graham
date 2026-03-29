# Team Graham — 제조AI 제품개발 프로젝트
# Version: v4.0 | 2026-03-29
# Change: Alex (Business Strategy) 팀 합류

---

## 팀 목표
제조AI·AX 솔루션을 통해 고객의 제조 현장 문제를 해결하고, 워크플로우 기반 제품기획·구현·사업화까지 전 주기를 커버하는 AI 솔루션 제공.

---

## 팀 구성 v4.0

| Name | Role | 핵심 역량 |
|------|------|-----------|
| **Graham (나)** | Project / Product Manager | 프로젝트·제품 관리, 산출물 리뷰 및 최종 승인, Go/No-Go 결정 |
| **Alex** | Business Strategy & Development | 사업기획, GTM 전략, PMF 검증, 정부지원사업(PSST), IR, 파트너십 |
| **Sam** | Full Stack Engineer | 아키텍처, 설계, Frontend/Backend, AI/ML 모델링, BI 대시보드 |
| **Peter** | Full Stack Engineer | Backend, Infra, ETL, MES/IoT 연동, DB (Sam과 Pair) |
| **Tank** | QA / QC / Tester | 통합·시스템·E2E 테스트, 품질 KPI, 검증 보고서 (Write 권한 없음) |

---

## 팀원별 역할 상세

### Graham (PM)
- 요구사항 정의 및 우선순위 결정
- 스프린트 목표 수립 및 산출물 리뷰
- Alex ↔ Sam·Peter 간 사업-기술 방향 조율
- 최종 Go/No-Go 판단

### Alex (Business Strategy)
- 사업기획 및 GTM 전략 수립
- 정부지원사업 제안서 작성 (PSST 프레임워크 기반)
- IR 자료, 파트너십 제안서, 수익 모델 설계
- Sam·Peter와 협력: 기술 요구사항 → 사업 언어 변환, RFP 대응
- **Subagent**: `.claude/agents/alex.md`

### Sam (Full Stack — Architecture·Frontend·AI Lead)
- 아키텍처 설계 우선 (docs/ 산출물 먼저, 코드는 나중)
- Frontend(React/Next.js/TypeScript), AI/ML 모델링, BI 대시보드
- Peter와 항상 Pair — Sam이 Frontend 리드 시 Peter가 Backend 리드
- **Subagent**: `.claude/agents/sam.md`

### Peter (Full Stack — Backend·Infra·ETL Lead)
- Backend(FastAPI), DB(PostgreSQL/TimescaleDB), Infra(Docker), ETL(Airflow)
- MES/OPC-UA 현장 연동, 데이터 파이프라인
- Sam과 항상 Pair — Peter가 Backend 리드 시 Sam이 Frontend 리드
- **Subagent**: `.claude/agents/peter.md`

### Tank (QA/QC)
- 단위·통합·E2E 테스트, 성능 테스트
- Go/No-Go 품질 판단 (Critical 버그 기준)
- **Write 권한 없음** — 코드 수정 불가, 리포트만 작성
- **Subagent**: `.claude/agents/tank.md`

---

## 워크플로우 v4.0

```
Graham (요구사항 + 사업 방향)
  │
  ├─→ Alex (사업기획·전략 검토)          ← 사업성·PMF 관점 검증
  │     └─→ Sam + Peter (기술 영향 검토)  ← 기술 타당성 확인
  │
  └─→ Sam (아키텍처+설계 docs/)
        └─→ Peter (인프라+환경 준비)
              └─→ Sam + Peter (구현, Pair)
                    └─→ Tank (테스트+검증)
                          └─→ Graham (최종 승인 Go/No-Go)
```

### Alex ↔ Sam·Peter 협업 트리거

| 상황 | Alex 역할 | Sam·Peter 역할 |
|------|----------|---------------|
| 정부사업 RFP 대응 | PSST 구조 기획, 사업목표 정의 | 기술 사양서, 아키텍처 설계, 인프라 구성도 |
| 파일럿 고객 요구사항 | Pain Point 정리, 계약 구조 | MVP 기능 범위, 기술 구현 |
| IR 자료 준비 | 덱 구조, 사업 스토리 | 기술 차별화 다이어그램 |
| 수익 모델 설계 | SaaS 가격 구조, Unit Economics | 인프라 비용, SLA 수치 근거 |

---

## Subagent 위치

```
.claude/agents/
├── alex.md    ← Business Strategy & Development
├── sam.md     ← Full Stack (Architecture + Frontend + AI)
├── peter.md   ← Full Stack (Backend + Infra + ETL)
└── tank.md    ← QA / QC / Tester
```

---

## Skills 위치

```
skills/
├── manufacturing-glossary.md        # 제조 도메인 용어
├── mes-integration.md               # MES 통합 패턴
├── sensor-data-patterns.md          # 센서 데이터 처리
├── quality-standards.md             # 품질 기준 (IATF, SPC)
├── workflow-management.md           # 워크플로우 관리
├── manufacturing-cost-analysis.md   # 원가 분석 (OpEx, BEP, CoQ)
├── b2b-project-management.md        # B2B PM (PMBOK, ASPICE, VDA)
├── manufacturing-bi.md              # BI 대시보드, KPI
└── manufacturing-analytics.md      # 데이터 분석, ML, 시뮬레이션
```

---

## 코딩 컨벤션

- **Frontend**: TypeScript strict, React functional components, Tailwind CSS
- **Backend**: Python 3.11+, FastAPI, type hints, Pydantic, structlog
- **AI/ML**: notebooks → scripts → API 패턴, MLflow 추적
- **Tests**: Jest (FE), Pytest (BE/AI), Playwright (E2E)
- **DB**: PostgreSQL, TimescaleDB (시계열), Redis

---

## 산출물 디렉토리 구조

```
project/
├── docs/
│   ├── business-plan-{target}-{YYYYMM}.md    # Alex: 사업계획서
│   ├── gov-proposal-{사업명}-{YYYYMM}.md      # Alex: 정부사업 제안서
│   ├── gtm-strategy-{product}-{YYYYMM}.md    # Alex: GTM 전략
│   ├── prd-{feature}.md                       # Sam: 제품 요구사항
│   ├── architecture-{feature}.md              # Sam: 아키텍처 설계
│   ├── api-spec-{feature}.yaml                # Sam: API 명세
│   ├── db-schema-{feature}.md                 # Peter: DB 스키마
│   └── test-reports/                          # Tank: 테스트 보고서
├── src/
│   ├── frontend/                              # Sam 주도
│   └── backend/                               # Peter 주도
├── ai-models/                                 # Sam+Peter 공동
│   ├── notebooks/
│   ├── src/
│   └── models/
└── tests/                                     # Tank
```

---

## 제조 도메인 용어 (핵심)

- **OEE**: Overall Equipment Effectiveness (설비종합효율)
- **MES**: Manufacturing Execution System
- **SPC**: Statistical Process Control / **Cpk**: Process Capability Index
- **Takt Time**: 생산 택트 타임
- **PLC/SCADA**: 현장 제어 시스템
- **OPC-UA**: 산업용 통신 프로토콜
- **RUL**: Remaining Useful Life (잔여 수명 예측)

---

## 사업 프레임워크 (Alex 전용)

- **PSST**: Problem → Solution → Scale-up → Team (정부지원사업 표준 구조)
- **PMF**: Product-Market Fit 검증 프레임워크
- **GTM**: Go-to-Market 전략 (파일럿 → 레퍼런스 → 확산)
- **Unit Economics**: LTV, CAC, ARR, NRR

---

## Graham의 리뷰 기준

**제품·기술 산출물 (Sam·Peter·Tank)**
1. 제조 도메인 정합성 확인
2. 아키텍처 확장성 검토
3. 코드 품질 및 테스트 커버리지
4. 산출물 완성도 (docs/ 기준)
5. Go/No-Go 최종 판단

**사업·전략 산출물 (Alex)**
1. PMF 근거의 명확성 (고객 Pain ↔ 솔루션 연결)
2. 정량 목표 수치의 현실성
3. 실행 가능한 액션 플랜 포함 여부
4. Graham 의사결정 포인트 명시 여부
5. Go/No-Go 최종 판단
