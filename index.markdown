---
layout: cover
title: "Eval-ATS : GraphRAG 파이프라인 및 정량 평가 기반 지원자 관리 시스템"
title_l1: "Eval-ATS : GraphRAG 파이프라인 및"
title_l2: "정량 평가 기반 지원자 관리 시스템"
permalink: /
eyebrow: 개 발 제 안 서
subtitle_en: "Eval-ATS: An Applicant Management System Based on a GraphRAG Pipeline and Quantitative Evaluation"
project_name: "AI 기반 채용 프로세스 자동화 및 지원자 통합 관리 플랫폼"
system_name: "Arda (Eval-ATS)"
dev_period: "2026년 8월 20일 (목) ~ 2026년 10월 27일 (화)"
dev_period_note: "총 69일 · 10주, 애자일 스크럼 (2주 1스프린트 · 총 5스프린트)"
dev_team_name: SEUK
dev_team_members: "진수택 · 이재우 · 이우정 · 김민아 · 박소연"
dev_team_count: "5명"
github_url: "https://github.com/Seuk-Team/Arda"
doc_repo_url: "https://github.com/cloverky/ats.cloverky.cloud"
doc_url: "https://ats.cloverky.cloud"
demo_url: "https://arda.seuk.cloud"
demo_note: "Vercel 배포 · API api.arda.seuk.cloud"
---

## 주요 기능

| 기능 | 설명 |
|------|------|
| 지원자 칸반 보드 | 카드 드래그로 단계 이동, 모든 이동 이력 기록 |
| 단계 변경 자동 메일 | SQS 큐 + SES 비동기 발송, 실패 시 재시도 |
| AI 이력서 파싱 | PDF/DOCX → 이름·학력·경력·기술스택 자동 추출 |
| Tool-Calling Agent | 자연어 명령으로 지원자 검색·통계 처리 |
| RAG 질의응답 | 이력서·공고 임베딩 기반 자연어 답변 (pgvector) |
| 공개 지원 링크 | 로그인 없이 외부 링크로 지원서 제출 |
| 인증·권한 | JWT + RBAC 3종 (관리자/채용담당자/면접관) |
