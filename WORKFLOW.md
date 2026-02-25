# Team Graham — Workflow & 업무 프로세스

## 1. 팀 계층구조 (Hierarchy)

```
┌─────────────────────────────────────────────────────────────┐
│                    Graham (PM)                              │
│         프로젝트 전체 관리 / 최종 승인권자                       │
└──────────────────────┬──────────────────────────────────────┘
                       │
        ┌──────────────┴──────────────┐
        │                            │
┌───────▼────────┐          ┌────────▼───────┐
│  Max (PO/SA)   │          │  Tank (QA/QC)  │
│ 제품기획/아키텍처│          │  품질보증/검증  │
└───────┬────────┘          └────────────────┘
        │
   ┌────┴──────────────┐
   │                   │
┌──▼───────┐   ┌───────▼──┐   ┌──────────┐
│Sam (FSE) │   │Peter(FSE)│   │Alex(AI)  │
│풀스택개발 │   │풀스택개발 │   │AI/ML/DL  │
└──────────┘   └──────────┘   └──────────┘
```

### 역할 요약

| 이름   | 직책            | 권한 레벨 | 주요 책임                         |
|--------|-----------------|-----------|-----------------------------------|
| Graham | PM              | L1 (최고) | 프로젝트 전체 관리, 최종 승인      |
| Max    | PO / SW Architect | L2      | 제품기획, 아키텍처 설계, 기술 결정 |
| Tank   | QA/QC Lead      | L2        | 품질 보증, 테스트 전략, 릴리스 승인 |
| Sam    | Full Stack Engineer | L3    | Frontend / Backend / Cloud 개발    |
| Peter  | Full Stack Engineer | L3    | Frontend / Backend / Cloud 개발    |
| Alex   | AI/ML/DL Engineer | L3     | AI 모델링, 데이터 파이프라인       |

---

## 2. 개발 사이클 (Development Cycle)

Team Graham은 **2주 스프린트** 기반의 Agile 방식으로 운영됩니다.

```
스프린트 계획          개발 기간              스프린트 리뷰/회고
(월요일, Day 1)      (Day 1 ~ Day 9)        (금요일, Day 10)
     │                    │                       │
     ▼                    ▼                       ▼
  Graham/Max           Sam / Peter            Tank 검증
  목표 수립            Alex 구현              Graham 승인
  백로그 정의          Daily Standup          회고 및 개선
```

### 스프린트 일정

| 이벤트              | 주기         | 참여자              | 시간    |
|---------------------|--------------|---------------------|---------|
| Sprint Planning     | 격주 월요일   | 전체 팀             | 2시간   |
| Daily Standup       | 매일 오전     | 전체 팀             | 15분    |
| Tech Review         | 주 1회 수요일 | Max, Sam, Peter, Alex | 1시간 |
| QA Sync             | 주 1회 목요일 | Tank, Sam, Peter, Alex | 1시간|
| Sprint Review       | 격주 금요일   | 전체 팀             | 1시간   |
| Sprint Retrospective| 격주 금요일   | 전체 팀             | 1시간   |

---

## 3. 업무 흐름 (Task Workflow)

### 3.1 기능 개발 프로세스

```
1. 기획 단계
   Graham ──→ Max
   요구사항 전달  요구사항 분석 / 백로그 작성 / 아키텍처 설계
                  └──→ Graham 승인

2. 개발 단계
   Max ──→ Sam / Peter / Alex
   설계 전달      각 도메인별 구현
                  ├── Sam  : Frontend + Backend
                  ├── Peter: Frontend + Backend
                  └── Alex : AI/ML/DL

3. 검증 단계
   Sam / Peter / Alex ──→ Tank
   개발 완료              통합 테스트 / E2E 테스트
                          품질 KPI 검증
                          └── 통과 시 PR Approve

4. 승인 단계
   Tank ──→ Graham
   검증 완료    최종 확인 및 릴리스 승인
```

### 3.2 이슈 처리 흐름

```
이슈 발생
   │
   ├── 개발 이슈  ──→ Sam / Peter / Alex 자체 해결
   │                  └── 미해결 시 Max에 에스컬레이션
   │
   ├── 품질 이슈  ──→ Tank 주도 분석
   │                  └── 개발팀 협업 수정 → 재검증
   │
   ├── 기술 이슈  ──→ Max 의사결정
   │                  └── 필요 시 Graham 보고
   │
   └── 리스크/블로커 ──→ Graham 즉시 보고 및 조정
```

---

## 4. 산출물 승인 프로세스 (Approval Process)

### 4.1 산출물 유형별 승인 경로

| 산출물              | 작성자             | 1차 리뷰     | 최종 승인 |
|---------------------|--------------------|--------------|-----------|
| 요구사항 명세서     | Max                | Graham 검토  | Graham    |
| 아키텍처 설계서     | Max                | Sam/Peter 검토 | Graham  |
| API 설계서          | Max / Sam / Peter  | Max 검토     | Graham    |
| 코드 (PR)           | Sam / Peter / Alex | Max 코드리뷰 | Tank 승인 후 Merge |
| AI 모델 설계서      | Alex               | Max 검토     | Graham    |
| 테스트 계획서       | Tank               | Max 검토     | Graham    |
| 품질 보고서         | Tank               | Graham 검토  | Graham    |
| 릴리스 노트         | Max / Tank         | Graham 검토  | Graham    |

### 4.2 PR (Pull Request) 규칙

```
브랜치 전략:
  main        ── 프로덕션 배포 브랜치 (Graham 승인 필수)
  develop     ── 통합 개발 브랜치 (Tank 검증 필수)
  feature/**  ── 기능 개발 브랜치 (Max 코드리뷰 필수)
  hotfix/**   ── 긴급 수정 브랜치 (Max + Graham 승인 필수)
  release/**  ── 릴리스 준비 브랜치 (Tank QA 통과 필수)

PR 체크리스트:
  ☐ 코드 리뷰어 지정 (최소 1명: Max 또는 동료 엔지니어)
  ☐ 관련 테스트 코드 포함
  ☐ CI/CD 파이프라인 통과
  ☐ 컨벤션 / 린팅 통과
  ☐ 기능 명세와의 일치 여부 확인
```

---

## 5. 커뮤니케이션 프로토콜

### 5.1 채널별 용도

| 채널              | 용도                                      | 대상              |
|-------------------|-------------------------------------------|-------------------|
| #graham-daily     | 일일 스탠드업, 블로커 공유                | 전체 팀           |
| #graham-dev       | 개발 관련 기술 논의                       | Max, Sam, Peter, Alex |
| #graham-qa        | QA 이슈 및 품질 관련 논의                 | Tank + 개발팀     |
| #graham-pm        | 프로젝트 일정, 리스크, 의사결정           | Graham, Max       |
| #graham-alerts    | CI/CD, 모니터링 자동 알림                 | 전체 팀           |

### 5.2 에스컬레이션 원칙

```
Level 1 (자체 해결): 개발자 간 협의로 해결 (24시간 내)
Level 2 (Max 결정): 기술/설계 의사결정 필요 시 (48시간 내)
Level 3 (Graham 보고): 일정/리소스/방향성 영향 시 (즉시)
```

---

## 6. 품질 기준 (Quality Standards)

### 6.1 개발 품질 KPI (Tank 관리)

| 항목                  | 목표         |
|-----------------------|--------------|
| 코드 커버리지          | ≥ 80%        |
| 빌드 성공률            | ≥ 99%        |
| Critical 버그 0-day 대응 | 24시간 내   |
| E2E 테스트 통과율      | ≥ 95%        |
| 스프린트 Velocity 달성률 | ≥ 85%      |

### 6.2 코드 컨벤션

- **공통**: ESLint / Prettier (Frontend), Black / isort (Python)
- **커밋 메시지**: `type(scope): message` 형식 준수
  - `feat`, `fix`, `docs`, `refactor`, `test`, `chore`
- **브랜치 네이밍**: `feature/`, `fix/`, `hotfix/`, `release/` 접두사 사용

---

## 7. 의사결정 구조 (Decision Making)

```
┌──────────────────────────────────────────────────────────┐
│ 의사결정 유형          │ 결정권자      │ 협의 대상         │
├──────────────────────────────────────────────────────────┤
│ 제품 방향 / 전략       │ Graham       │ Max              │
│ 기술 스택 / 아키텍처   │ Max          │ Sam, Peter, Alex │
│ 릴리스 가능 여부       │ Graham       │ Tank, Max        │
│ 품질 기준 / 테스트 전략│ Tank         │ Max              │
│ 구현 방식 (Feature)    │ Max          │ 담당 개발자       │
│ AI 모델 선택 / 전략    │ Alex         │ Max              │
└──────────────────────────────────────────────────────────┘
```

---

## 8. 도구 스택 (Tool Stack)

| 카테고리        | 도구                              | 관리자        |
|-----------------|-----------------------------------|---------------|
| 프로젝트 관리   | Jira / GitHub Issues              | Graham, Max   |
| 버전 관리       | GitHub                            | Max           |
| CI/CD           | GitHub Actions                    | Sam / Peter   |
| 커뮤니케이션    | Slack                             | Graham        |
| 문서            | Confluence / GitHub Wiki          | Max           |
| 모니터링        | Datadog / Sentry                  | Sam / Peter   |
| AI/ML 실험 추적 | MLflow / Weights & Biases         | Alex          |
| QA 관리         | TestRail / Jira                   | Tank          |

---

*최종 수정일: 2026-02-25 | 관리자: Graham (PM)*
