# CLAUDE.md — demo.cocerky.cloud

이 프로젝트는 제안서/보고서를 Jekyll 정적 사이트로 문서화하는 작업이다.
보고서의 각 페이지(장)를 Jekyll page로 1:1 매핑한다.

## 프로젝트 정체성

- 사업명: Eval-ATS : GraphRAG 파이프라인 및 정량 평가 기반 지원자 관리 시스템
- 개발기간: 2026-08-20 ~ 2026-10-27
- 개발팀: SEUK
- 개발자: 박소연, 김민아, 이재우, 진수택, 이우정
- 깃허브 주소: https://github.com/cloverky/ats.cloverky.cloud
- 데모 사이트: https://ats.cloverky.cloud

## 환경

- WSL2 Ubuntu, 경로 `~/projects/demo.cocerky.cloud`
- Ruby 3.4.10 (rbenv), Jekyll 4.4.1, Bundler, theme: minima
- 로컬 미리보기: `bundle exec jekyll serve --host 0.0.0.0 --port 4000` (백그라운드 실행)
- `_config.yml` 변경 시 서버 재시작 필수 (자동 리로드 안 됨)
- sudo가 필요한 `apt` 설치는 에이전트가 대신 실행 불가 (TTY 없음) — 사용자가 WSL 터미널에서 직접 실행해야 함

## 페이지 구조 규칙 (Report-as-Site)

보고서의 각 페이지는 Jekyll page(.markdown) 하나로 매핑한다.

| 순서 | 내용 | 파일 | permalink |
|---|---|---|---|
| 1 | 표지(사업명) | index.markdown (layout: cover) | / |
| 2 | 목차 | toc.markdown | /toc/ |
| 3+ | 각 장 | 0N-<슬러그>.markdown (예: 03-사업개요.markdown) | /0N-<슬러그>/ |
| - | 개발 로그 | devlog.markdown | /devlog/ |
| - | 미결항목 | open-items.markdown | /open-items/ |

표지(index.markdown)는 `_layouts/cover.html`을 사용하며, 개발 기간/개발팀/문서 작성일/깃허브 주소/데모 사이트를 front matter 필드로 관리한다.
상단 네비게이션은 `_config.yml`의 `header_pages`로 명시적으로 고정한다 (목차 → 개발 로그 → 미결항목 순, about.markdown은 제외).

새 장을 추가할 때:

1. `toc.markdown`의 대분류/소분류 번호를 그대로 파일명 슬러그로 사용한다.
2. front matter에 `layout: page`, `title`, `permalink`를 반드시 넣는다.
3. `toc.markdown`에 해당 장으로의 링크를 추가해 목차와 실제 페이지를 항상 동기화한다.

## 세션 간 진행상황 기록 규칙

다음 세션에서 이어서 작업할 수 있도록 진행 상황은 두 곳에 기록한다.

1. 이 문서의 진행상황 섹션 — 완료/미완료를 최신 상태로 덮어쓴다 (히스토리 나열 아님).
2. `toc.markdown` — 아직 작성되지 않은 장은 항목 옆에 `(작성 예정)`을 표시한다.

작업 시작 전: 이 문서와 `toc.markdown`을 먼저 읽고 현재 상태를 파악한다.
작업 종료 시: 새로 추가/완성된 장을 목차에 반영하고, 이 문서의 진행상황 섹션을 갱신한다.

## 진행상황

- [x] Ruby/rbenv/Jekyll 환경 구축 (2026-08-20)
- [x] 표지(index.markdown) 작성 — ATS 플랫폼 주제로 전환, cover 레이아웃 적용 (2026-08-21)
- [x] 목차(toc.markdown) 작성 — 4개 대분류
- [x] 상단 네비 목차/개발 로그/미결항목으로 재구성, devlog.markdown·open-items.markdown 빈 페이지 생성 (2026-08-21)
- [x] toc.markdown을 RFP 응답 양식(4개 대분류)에서 기술 개발문서 스타일(5개 대분류)로 전면 재구성 — 2번 대분류를 "개발 요구 사항"으로 바꿔 ATS 기술 요건 반영, "개발 일정 및 추진 체계"·"부록" 신규 추가 (2026-08-21)
- [ ] 1. 사업 개요 (사업 목적 / 주요 사업 내용 / 기대 효과) — 미작성
- [ ] 2. 개발 요구 사항 (목적 / 개발 범위 / 지원자 데이터 수집 및 연계 / GraphRAG 파이프라인 구축 / 정량 평가 기반 지원자 관리 기능 / 시스템 아키텍처 / 보안 및 개인정보 보호) — 미작성
- [ ] 3. 주요 개발 수행 지침 (일반사항 / 개발 표준 및 산출물 / 품질 관리 및 테스트) — 미작성
- [ ] 4. 개발 일정 및 추진 체계 (단계별 개발 일정 / 조직 구성 및 역할 분담 / 위험 관리 방안) — 미작성
- [ ] 5. 부록 (용어 정의 / 관련 서식) — 미작성
