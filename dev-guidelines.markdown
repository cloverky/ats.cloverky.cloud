---
layout: page
title: 주요 개발 수행 지침
permalink: /dev-guidelines/
---

<h2 id="general" class="dg-h2">1. 일반사항</h2>
<p class="dg-body">애자일 스크럼 방법론을 따르며, 총 10주를 2주 단위 5개 스프린트로 나눠 진행한다. 각 스프린트는 동작하는 산출물을 목표로 한다.</p>
<div class="dg-table-wrap">
<table class="dg-table">
  <thead>
    <tr><th>스프린트</th><th>기간</th><th>내용</th></tr>
  </thead>
  <tbody>
    <tr><td>Sprint 1</td><td>08/20 ~ 09/02</td><td>인프라 기반 구축 — DB 스키마, 개발 환경 세팅</td></tr>
    <tr><td>Sprint 2</td><td>09/03 ~ 09/16</td><td>공고·지원자 핵심 CRUD</td></tr>
    <tr><td>Sprint 3</td><td>09/17 ~ 09/30</td><td>칸반 인터페이스 · 알림 시스템</td></tr>
    <tr><td>Sprint 4</td><td>10/01 ~ 10/14</td><td>AI 기반 이력서 파싱 · 지능형 기능</td></tr>
    <tr><td>Sprint 5</td><td>10/15 ~ 10/27</td><td>통합 테스트 · 배포</td></tr>
  </tbody>
</table>
</div>
<p class="dg-note">세부 일자별 진행 현황은 <a href="/dev-schedule/">단계별 개발 일정</a>·<a href="/devlog/">개발 로그</a> 참고.</p>

<p class="dg-note">스프린트 운영: 데일리 스크럼(매일 10분) · 스프린트 리뷰(종료일 결과물 시연) · 스프린트 회고(리뷰 직후, 다음 스프린트에 개선 반영)</p>

<h2 id="standards" class="dg-h2">2. 개발 표준 및 산출물</h2>
<p class="dg-sub">기술 스택</p>
<ul class="dg-list">
  <li><strong>BACKEND</strong> — Python · FastAPI · PostgreSQL</li>
  <li><strong>FRONTEND</strong> — React · Vite · TypeScript</li>
  <li><strong>INFRA</strong> — Docker · AWS (EC2 · S3 · SES · SQS) · GitHub Actions · Vercel</li>
  <li><strong>AI</strong> — Claude API · pgvector · LangGraph</li>
</ul>
<p class="dg-sub">코드 관리 규칙</p>
<div class="dg-table-wrap">
<table class="dg-table">
  <thead>
    <tr><th>항목</th><th>기준</th></tr>
  </thead>
  <tbody>
    <tr><td>버전 관리</td><td>Git (GitHub)</td></tr>
    <tr><td>브랜치 전략</td><td>feature 브랜치 → PR → main 머지</td></tr>
    <tr><td>코드 리뷰</td><td>PR 머지 전 최소 1인 리뷰 필수</td></tr>
    <tr><td>커밋 메시지</td><td>Conventional Commits (<code>feat:</code>, <code>fix:</code>, <code>docs:</code>, <code>ci:</code>)</td></tr>
  </tbody>
</table>
</div>
<p class="dg-sub">주요 산출물</p>
<div class="dg-table-wrap">
<table class="dg-table">
  <thead>
    <tr><th>구분</th><th>산출물</th><th>비고</th></tr>
  </thead>
  <tbody>
    <tr><td>설계</td><td>시스템 아키텍처 다이어그램</td><td>architecture.svg</td></tr>
    <tr><td>설계</td><td>ERD (테이블 정의서)</td><td>erd.png</td></tr>
    <tr><td>개발</td><td>소스 코드 (Frontend + Backend + AI)</td><td>GitHub 저장소</td></tr>
    <tr><td>개발</td><td>API 명세 (Swagger)</td><td>FastAPI <code>/docs</code> 자동 생성</td></tr>
    <tr><td>문서</td><td>개발 진행 보고서</td><td>본 Jekyll 사이트</td></tr>
    <tr><td>인프라</td><td>Docker 컨테이너 구성</td><td>Dockerfile, docker-compose</td></tr>
    <tr><td>인프라</td><td>CI/CD 파이프라인</td><td>GitHub Actions</td></tr>
  </tbody>
</table>
</div>

<h2 id="quality" class="dg-h2">3. 품질 관리 및 테스트</h2>
<div class="dg-table-wrap">
<table class="dg-table">
  <thead>
    <tr><th>요구 ID</th><th>항목</th><th>검수 기준</th></tr>
  </thead>
  <tbody>
    <tr><td>PER-001</td><td><strong>성능</strong> — 이력서 파싱 E2E 3초 이내, RAG 응답 First Token 2초 이내</td><td>부하 테스트 시 목표 달성</td></tr>
    <tr><td>QUA-001</td><td><strong>테스트</strong> — 요구사항 ID별 PyTest 및 Vitest 자동화 단위 테스트</td><td>핵심 로직 코드 커버리지 80% 이상</td></tr>
    <tr><td>QUA-002</td><td><strong>문서화</strong> — API 엔드포인트 자동 문서화 (FastAPI Swagger)</td><td>/docs 접속 시 전체 API 명세 조회 가능</td></tr>
  </tbody>
</table>
</div>
<p class="dg-sub">테스트 전략</p>
<div class="dg-table-wrap">
<table class="dg-table">
  <thead>
    <tr><th>단계</th><th>대상</th><th>도구</th><th>시점</th></tr>
  </thead>
  <tbody>
    <tr><td>단위 테스트</td><td>API 엔드포인트, AI 모듈</td><td>PyTest</td><td>PR 머지 전</td></tr>
    <tr><td>단위 테스트</td><td>React 컴포넌트</td><td>Vitest</td><td>PR 머지 전</td></tr>
    <tr><td>통합 테스트</td><td>API ↔ DB 연동</td><td>PyTest</td><td>스프린트 종료 시</td></tr>
    <tr><td>E2E 테스트</td><td>주요 사용자 시나리오</td><td>수동 QA 체크리스트</td><td>스프린트 리뷰</td></tr>
    <tr><td>성능 테스트</td><td>이력서 파싱, RAG 응답, 검색</td><td>더미 10만 건 기준</td><td>Sprint 5</td></tr>
  </tbody>
</table>
</div>

<style>
  h2.dg-h2 {
    font-size: 17px;
    font-weight: 700;
    color: #2451FF;
    margin: 40px 0 16px;
    padding-bottom: 10px;
    border-bottom: 1px solid #eee;
  }
  .dg-h2:first-child {
    margin-top: 0;
  }
  .dg-body {
    font-size: 15px;
    line-height: 1.75;
    word-break: keep-all;
    margin: 0 0 16px;
  }
  .dg-note {
    font-size: 13px;
    color: #828282;
    line-height: 1.7;
    word-break: keep-all;
    margin: 10px 0 0;
  }
  .dg-sub {
    font-size: 13px;
    font-weight: 700;
    color: #828282;
    margin: 24px 0 10px;
  }
  .dg-list {
    margin: 0 0 40px;
    padding-left: 20px;
    font-size: 14.5px;
    line-height: 1.8;
    word-break: keep-all;
  }
  .dg-list li {
    margin-bottom: 6px;
  }
  .dg-table-wrap {
    overflow-x: auto;
    margin-bottom: 8px;
  }
  table.dg-table {
    width: 100%;
    border-collapse: collapse;
    font-size: 13px;
  }
  table.dg-table th,
  table.dg-table td {
    border: 1px solid #eee;
    padding: 10px 12px;
    text-align: left;
    vertical-align: top;
    word-break: keep-all;
  }
  table.dg-table th {
    background: #f7f7f7;
    font-size: 12px;
    color: #828282;
    white-space: nowrap;
  }
</style>
