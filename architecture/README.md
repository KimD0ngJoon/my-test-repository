# 한화생명 CMP 고도화 - 아키텍처 다이어그램

## 파일 구성

| 파일 | 뷰 | 설명 |
|---|---|---|
| `system.drawio` | 시스템 아키텍처 | IDC(Tanzu) + CSP 영역 + 망분리(중요망/업무망) |
| `application.drawio` | 애플리케이션 아키텍처 | 런타임 의존성 (Web → API → DB / Batch → CSP) |
| `software.drawio` | 소프트웨어 아키텍처 | 레이어 구조 (Presentation/API/Batch/Infra) |
| `topology.drawio` | 배포 토폴로지 | Tanzu K8s 네임스페이스 구성 (cmp-app / cmp-batch / devos-prod / infra) |

## 편집 방법

### 방법 1: 웹 draw.io에서 GitLab 직접 열기
1. https://app.diagrams.net/ 접속
2. **Open Existing Diagram → GitLab**
3. 이 저장소 선택 → 파일 열기
4. 편집 후 저장하면 자동 커밋

### 방법 2: 파일 다운로드 후 편집
1. 저장소에서 `.drawio` 파일 Raw 다운로드
2. 웹 draw.io 또는 VS Code Draw.io 확장에서 편집
3. 저장 후 Git 커밋/푸시

## 범위 (대상 프로젝트)

### Frontend / API
- `hanwha-cmp-web`, `hanwha-cmp-api`, `asset-api`
- `cost-common-api`, `cost-360-common-api`
- `plat-360-api`, `plat-360-portal-api`, `plat-360-sso`

### Asset 배치
- `asset-aws-scheduler/collector/dataprocess`
- `asset-azure-scheduler/collector/dataprocess`
- `asset-ncp-scheduler/collector/dataprocess`
- `asset-common-scheduler/dataprocess`
- `asset-es-dataprocess`, `asset-resourceopti-dataprocess`
- `asset-server-scheduling-batch`

### Cost 배치
- `cost-aws-billing-collector/legacy-batch/mart-batch`
- `cost-aws-spark-batch`
- `cost-azure-billing-collector/aggregator`
- `cost-360-nbs-billing-batch`

### 공통
- `hanwha-cmp-batch`

### DevOS (NCP → Tanzu 이전 대상)
- DevOS v2.13 기반 (운영자 가이드 참조)
- 네임스페이스: `devops-prod`

## 초안 가정 (미정의 → 일반 구성)

- 인증: Keycloak OIDC
- DB: MySQL Enterprise + Redis
- 메시징: Kafka
- 시크릿: Vault
- 로깅/모니터링: ELK + Prometheus/Grafana
- CI/CD: GitLab + Jenkins + Harbor (+ ArgoCD 가정)

## 버전

- v0.1 (2026-04-24) 최초 초안
