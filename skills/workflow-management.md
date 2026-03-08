# Workflow Management — Team Graham

## 개발 프로세스

### 스프린트 구조 (1주 Scrum)
```
월요일:  Graham → 스프린트 목표 확정, 작업 분배
화~목:   Sam+Peter Pair 개발, 일일 진행 공유
목요일:  Tank QA 시작 (구현 완료 기준)
금요일:  Tank 리포트 → Graham 리뷰 → Go/No-Go
```

### 작업 핸드오프 흐름
```
Graham: "기능 X 개발 필요"
    ↓
Sam: docs/prd-X.md 작성 (요구사항 명확화)
Sam+Peter: docs/architecture-X.md 합의
    ↓
Graham 승인: "PRD/아키텍처 OK, 구현 진행"
    ↓
Sam: Frontend + AI 모델 구현
Peter: Backend + 인프라 구현
(동시 진행, 일 2회 sync)
    ↓
Sam↔Peter: 상호 코드리뷰 완료
    ↓
Tank: 테스트 실행 → docs/test-reports/ 저장
    ↓
Graham: 최종 승인 → 배포
```

## 산출물 관리 규칙

### 파일 네이밍 컨벤션
```
docs/prd-{feature-kebab-case}.md
docs/architecture-{feature-kebab-case}.md
docs/api-spec-{feature-kebab-case}.yaml
docs/db-schema-{feature-kebab-case}.md
docs/test-reports/qa-{feature-kebab-case}-{YYYYMMDD}.md
docs/sprint-notes.md  ← 진행 중 의사결정 기록
```

### 스프린트 노트 형식 (docs/sprint-notes.md)
```markdown
# Sprint {번호} - {YYYY-MM-DD} ~ {YYYY-MM-DD}

## 목표
- [ ] 기능 A
- [ ] 기능 B

## 일일 진행
### {날짜}
- **Sam**: [작업 내용, 블로커]
- **Peter**: [작업 내용, 블로커]
- **결정사항**: [중요 기술/설계 결정]

## 완료 기준 (DoD)
- [ ] 코드 리뷰 완료
- [ ] 테스트 커버리지 ≥ 80%
- [ ] Tank QA 통과
- [ ] Graham 승인
```

## Sam-Peter Pair 프로토콜

### 작업 시작 시
```
"Sam here. [작업명] 시작. 
 내가 담당: [Frontend/AI 파트]
 Peter 필요: [Backend 엔드포인트 / DB 스키마 등]
 예상 완료: [시간]"
```

```
"Peter here. [작업명] 시작.
 Sam의 API spec @docs/api-spec-X.yaml 확인 완료.
 내가 담당: [Backend/인프라 파트]
 질문: [모호한 설계 결정 사항]"
```

### 코드리뷰 요청 형식
```
"[Sam→Peter 리뷰 요청]
 PR: src/frontend/features/oee-dashboard/
 중점 확인: API 연동 부분 (useOEEData hook)
 특이사항: WebSocket 재연결 로직 처음 구현함"
```

## 에스컬레이션 규칙

Sam 또는 Peter가 Graham에게 보고해야 할 상황:
1. 설계 결정이 PRD 범위를 벗어날 때
2. 기술 스택 변경이 필요할 때  
3. 스프린트 목표 달성 불가 예측 시 (수요일까지 보고)
4. 외부 시스템 연동 이슈 (MES, OPC-UA 등)

Tank가 Graham에게 즉시 보고:
- Critical 결함 발견 시
- 성능 목표 2배 초과 시
- 보안 취약점 발견 시
