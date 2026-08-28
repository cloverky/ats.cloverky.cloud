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

<h2 id="standards" class="dg-h2">2. 개발 표준 및 산출물</h2>
<ul class="dg-list">
  <li><strong>기술 스택</strong> — 백엔드 Python·FastAPI, 프론트엔드 React·TypeScript, 데이터베이스 PostgreSQL, 인프라 AWS(EC2·S3·SES·SQS)</li>
  <li><strong>API 문서</strong> — FastAPI 내장 기능으로 API 명세를 자동 생성한다.</li>
  <li><strong>형상 관리</strong> — Git 워크플로우를 따르며, 병합 전 동료 리뷰(PR review)를 필수로 한다.</li>
</ul>

<h2 id="quality" class="dg-h2">3. 품질 관리 및 테스트</h2>
<ul class="dg-list">
  <li><strong>성능 기준</strong> — 이력서 파싱 E2E 처리 3초 이내</li>
  <li><strong>테스트 커버리지</strong> — 핵심 로직 자동화 테스트 커버리지 80% 이상</li>
  <li><strong>리뷰 절차</strong> — 모든 PR은 병합 전 최소 1인 이상의 리뷰를 거친다.</li>
</ul>

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
