---
layout: page
title: 프로젝트 소개
permalink: /about/
---

<h1 class="pi-h1">프로젝트 소개 — Arda</h1>
<p class="pi-lead">채용 지원자 관리 시스템(ATS) — 공고 등록부터 지원 접수, 단계별 심사·평가, 합불 통보까지</p>

<h2 class="pi-h2">핵심 소주제</h2>

<div class="pi-topics">

<div class="pi-topic">
  <p class="pi-topic-num">1</p>
  <div>
    <p class="pi-topic-title">채용 프로세스 통합 관리 파이프라인</p>
    <p class="pi-topic-body">'합불 등의 핵심 결정은 항상 사람이 한다'라는 원칙을 기반으로, [공고 등록 → 접수 → 단계별 심사 → 결과 통보]까지의 채용 전 과정을 하나의 시스템으로 통합한다. 메인 화면은 지원자 칸반 보드로, 카드를 드래그해 단계를 이동하면 이력이 자동 기록되고 안내 메일이 큐 기반 비동기(+재시도)로 발송된다. JWT 기반 3역할(관리자·채용담당자·면접관) 접근 제어와 더미 지원자 10만 건 기준의 검색과 필터 성능 튜닝을 포함한다.</p>
  </div>
</div>

<div class="pi-topic">
  <p class="pi-topic-num">2</p>
  <div>
    <p class="pi-topic-title">보안에 강한 로컬 AI 에이전트</p>
    <p class="pi-topic-body">경량 모델로 온프레미스 구현. 이력서/면접 기록 등 지원자 개인정보가 외부 API로 전송되지 않도록, 경량 LLM(sLLM)과 STT 모두를 온프레미스 환경에서 구동하는 로컬 에이전트를 구현한다. [입력 → 모델 추론 → 출력]의 모든 과정을 내부망 안에서 완결시켜 '데이터 반출 없는 채용 에이전트'라는 보안 차별점을 확보한다.</p>
  </div>
</div>

<div class="pi-topic">
  <p class="pi-topic-num">3</p>
  <div>
    <p class="pi-topic-title">지원자가 24시간 접근 가능한 면접 일정 자동화 서비스</p>
    <p class="pi-topic-body">면접관들의 가용 일정을 파악해 지원자에게 후보 시간을 제안하고, 선택을 받아 일정을 확정·통보하는 조율 과정을 에이전트가 자동화한다. 지원자는 안내 이메일의 링크로 24시간 언제든 접속해 전형 진행 현황과 면접 일정을 실시간으로 확인·선택할 수 있다.</p>
  </div>
</div>

<div class="pi-topic">
  <p class="pi-topic-num">4</p>
  <div>
    <p class="pi-topic-title">LLM 도구 호출 에이전트 및 RAG 기반 STT 면접 분석</p>
    <p class="pi-topic-body">"김도현 찾아줘 → 면접 안내 이메일 만들어줘"처럼 자연어 대화만으로 지원자 검색/조회/단계 변경/이메일 초안을 수행하는 도구 호출(Tool-Use) 에이전트를 개발하며, 실행성 작업은 초안(pending_action)까지만 만들어 사람의 확인을 거친다. 면접 분석은 [STT → RAG → sLLM] 파이프라인으로 구성한다.</p>
  </div>
</div>

<div class="pi-topic">
  <p class="pi-topic-num">5</p>
  <div>
    <p class="pi-topic-title">웹/모바일 멀티 클라이언트 및 운영 체계</p>
    <p class="pi-topic-body">React(Vite/TS) 웹과 Flutter 모바일 앱이 동일한 FastAPI API를 사용하는 계약 중심 설계로, API/ERD 문서를 코드와 같은 커밋에서 갱신하는 규칙으로 5인 병렬 개발의 정합성을 유지한다. Docker, AWS(EC2/S3/SES/SQS), GitHub Actions 기반 배포와 함께 ADR 15건, 팀원별 소유 파일 기반 무충돌 칸반 운영까지 포함한다.</p>
  </div>
</div>

</div>

<h2 class="pi-h2">주요 기능</h2>
<div class="pi-table-wrap">
<table class="pi-table">
  <thead>
    <tr><th>기능</th><th>설명</th></tr>
  </thead>
  <tbody>
    <tr><td>지원자 칸반 보드</td><td>카드를 드래그해 단계 이동(지원 접수 → 서류 검토 → 면접 → 최종 합격/불합격). 모든 이동은 단계 이력으로 기록</td></tr>
    <tr><td>단계 변경 자동 메일</td><td>단계 이동 시 지원자에게 메일 자동 발송. SQS 큐 + 워커로 비동기 처리, 실패 시 재시도</td></tr>
    <tr><td>공고 관리 · 공개 지원 링크</td><td>채용 공고 등록·관리. 지원자는 로그인 없이 외부 공개 링크로 지원서 제출</td></tr>
    <tr><td>이력서 S3 업로드</td><td>presigned URL로 브라우저에서 S3에 직접 업로드 — 파일이 API 서버를 거치지 않는다</td></tr>
    <tr><td>지원자 검색·필터</td><td>이름·학교·기술스택 검색과 필터. 더미 데이터 10만 건 기준으로 인덱스 튜닝</td></tr>
    <tr><td>평가 · 면접관 배정</td><td>면접관 배정, 단계별 점수·코멘트 평가 기록</td></tr>
    <tr><td>인증 · 권한</td><td>JWT 인증, 역할 3종(관리자 / 채용담당자 / 면접관)</td></tr>
  </tbody>
</table>
</div>

<h2 class="pi-h2">기술 스택</h2>
<div class="pi-stack">
  <div class="pi-stack-item"><span class="pi-stack-label">BACKEND</span>Python · FastAPI · PostgreSQL</div>
  <div class="pi-stack-item"><span class="pi-stack-label">FRONTEND</span>React · Vite · TypeScript</div>
  <div class="pi-stack-item"><span class="pi-stack-label">INFRA</span>Docker · AWS (EC2 · S3 · SES · SQS) · GitHub Actions · Vercel</div>
  <div class="pi-stack-item"><span class="pi-stack-label">AI</span>Claude API · pgvector · LangGraph</div>
</div>

<h2 class="pi-h2">아키텍처</h2>
<div class="pi-table-wrap">
<table class="pi-table">
  <thead>
    <tr><th>계층</th><th>기술</th><th>배포</th></tr>
  </thead>
  <tbody>
    <tr><td>Frontend</td><td>React + TypeScript + Vite</td><td>Vercel</td></tr>
    <tr><td>Backend API</td><td>FastAPI (Python)</td><td>EC2 · Docker</td></tr>
    <tr><td>Database</td><td>PostgreSQL + pgvector</td><td>Aurora Serverless v2</td></tr>
    <tr><td>파일 저장</td><td>S3 (presigned URL 업로드, SSE 암호화)</td><td>AWS S3</td></tr>
    <tr><td>메일 발송</td><td>SES + SQS (비동기 큐)</td><td>AWS SES/SQS</td></tr>
    <tr><td>CI/CD</td><td>GitHub Actions</td><td>자동 배포</td></tr>
  </tbody>
</table>
</div>

<style>
  .pi-h1 {
    font-size: 24px;
    font-weight: 800;
    margin: 0 0 8px;
    word-break: keep-all;
  }
  .pi-lead {
    font-size: 15px;
    color: #828282;
    margin: 0 0 40px;
    word-break: keep-all;
  }
  h2.pi-h2 {
    font-size: 17px;
    font-weight: 700;
    color: #2451FF;
    margin: 40px 0 16px;
    padding-bottom: 10px;
    border-bottom: 1px solid #eee;
  }
  .pi-topics {
    display: flex;
    flex-direction: column;
    gap: 20px;
    margin-bottom: 8px;
  }
  .pi-topic {
    display: flex;
    gap: 16px;
    align-items: flex-start;
  }
  .pi-topic-num {
    flex-shrink: 0;
    width: 28px;
    height: 28px;
    background: #2451FF;
    color: #fff;
    font-size: 13px;
    font-weight: 700;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    margin: 2px 0 0;
  }
  .pi-topic-title {
    font-size: 15px;
    font-weight: 700;
    margin: 0 0 6px;
    word-break: keep-all;
  }
  .pi-topic-body {
    font-size: 14px;
    line-height: 1.75;
    color: #4b5563;
    margin: 0;
    word-break: keep-all;
  }
  .pi-table-wrap {
    overflow-x: auto;
    margin-bottom: 8px;
  }
  table.pi-table {
    width: 100%;
    border-collapse: collapse;
    font-size: 13px;
  }
  table.pi-table th,
  table.pi-table td {
    border: 1px solid #eee;
    padding: 10px 12px;
    text-align: left;
    vertical-align: top;
    word-break: keep-all;
  }
  table.pi-table th {
    background: #f7f7f7;
    font-size: 12px;
    color: #828282;
    white-space: nowrap;
  }
  .pi-stack {
    display: flex;
    flex-direction: column;
    gap: 8px;
    margin-bottom: 8px;
  }
  .pi-stack-item {
    font-size: 14px;
    line-height: 1.6;
    word-break: keep-all;
  }
  .pi-stack-label {
    display: inline-block;
    font-size: 11px;
    font-weight: 700;
    color: #2451FF;
    background: #eff3ff;
    border-radius: 4px;
    padding: 1px 7px;
    margin-right: 8px;
    letter-spacing: 0.04em;
  }
</style>
