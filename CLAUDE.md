# Team Graham - 제조AI 제품개발 프로젝트

## 팀 목표
제조AI, AX를 위해 고객의 문제 해결을 위한 워크플로우 기반의 제품기획과 구현 등 AI솔루션 제공.

## 팀 구성 (수정본 기준)
| Name | Role | 핵심 역량 |
|------|------|-----------|
| **Graham (나)** | Project/Product Manager | 프로젝트/제품 관리, 산출물 리뷰 및 승인 |
| **Sam** | Full Stack Engineer | 아키텍처, 설계, Frontend/Backend, AI/ML 모델링 |
| **Peter** | Full Stack Engineer | 아키텍처, 설계, Frontend/Backend, AI/ML 모델링 (Sam과 Pair) |
| **Tank** | QA/QC/Tester | 통합/시스템/E2E 테스트, 품질 KPI, 검증 보고서 |

## Sam & Peter 협업 방식
- **Pair Programming**: 항상 쌍으로 개발
- **상호 코드리뷰**: 각자 작성한 코드를 상호 검증
- **역할 분담**: 작업별로 Lead/Reviewer 역할 교대
- Sam이 Frontend 리드 시 → Peter가 Backend 리드 (또는 반대)
- AI/ML 모델링은 공동 설계, 구현은 분담

## 워크플로우
```
Graham (요구사항) 
  → Sam (아키텍처+설계) + Peter (아키텍처+설계) [동시 검토, 합의]
  → Sam+Peter (구현, Pair) 
  → Tank (테스트+검증) 
  → Graham (최종 승인)
```

## Subagent 위치
- Sam: `.claude/agents/sam.md`
- Peter: `.claude/agents/peter.md`
- Tank: `.claude/agents/tank.md`

## Skills 위치
- 제조 도메인: `skills/manufacturing-glossary.md`
- MES 통합: `skills/mes-integration.md`
- 센서 데이터: `skills/sensor-data-patterns.md`
- 품질 기준: `skills/quality-standards.md`
- 워크플로우: `skills/workflow-management.md`

## 코딩 컨벤션
- **Frontend**: TypeScript strict, React functional components, Tailwind CSS
- **Backend**: Python 3.11+, FastAPI, type hints, Pydantic, structlog
- **AI/ML**: notebooks → scripts → API 패턴, MLflow 추적
- **Tests**: Jest (FE), Pytest (BE/AI), Playwright (E2E)
- **DB**: PostgreSQL, TimescaleDB (시계열), Redis

## 산출물 디렉토리 구조
```
project/
├── docs/
│   ├── prd-{feature}.md          # 제품 요구사항
│   ├── architecture-{feature}.md  # 아키텍처 설계
│   ├── api-spec-{feature}.yaml    # API 명세
│   ├── db-schema-{feature}.md     # DB 스키마
│   └── test-reports/              # Tank 테스트 보고서
├── src/
│   ├── frontend/                  # Sam 주도
│   └── backend/                   # Peter 주도
├── ai-models/                     # Sam+Peter 공동
│   ├── notebooks/
│   ├── src/
│   └── models/
└── tests/                         # Tank
```

## 제조 도메인 용어 (핵심)
- **OEE**: Overall Equipment Effectiveness (설비종합효율)
- **MES**: Manufacturing Execution System
- **SPC**: Statistical Process Control / Cpk: Process Capability Index
- **Takt Time**: 생산 택트 타임
- **PLC/SCADA**: 현장 제어 시스템
- **OPC-UA**: 산업용 통신 프로토콜
- **RUL**: Remaining Useful Life (잔여 수명 예측)

## Graham의 리뷰 기준
1. 제조 도메인 정합성 확인
2. 아키텍처 확장성 검토
3. 코드 품질 및 테스트 커버리지
4. 산출물 완성도 (docs/ 기준)
5. Go/No-Go 최종 판단
