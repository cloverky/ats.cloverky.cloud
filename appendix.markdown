---
layout: page
title: 부록
permalink: /appendix/
---

<h2 id="terms" class="ap-h2">1. 용어 정의</h2>

<p class="ap-body">시스템명 <strong>Arda</strong>는 톨킨의 요정어(Quenya)로 "왕국·터전"을 뜻한다. 두 가지 이유로 이 이름을 택했다.</p>
<ul class="ap-list">
  <li>"사람이 모이는 자리"라는 개념이 채용과 직결된다 — 사람을 회사로 불러들이는 일이 그 터전을 만드는 일이다.</li>
  <li>심판하지 않는다는 철학을 담는다. 심판 그 자체를 상징하는 이름(아르고스·테미스 등)은 피했다. 시스템은 무대를 제공할 뿐, 결정은 사람이 한다 — AI 도구는 채용 과정을 돕지만 최종 권한은 채용담당자에게 있다.</li>
</ul>

<div class="ap-table-wrap">
<table class="ap-table">
  <thead>
    <tr><th>용어</th><th>정의</th></tr>
  </thead>
  <tbody>
    <tr><td>ATS</td><td>Applicant Tracking System — 지원자 추적·관리 시스템</td></tr>
    <tr><td>Arda</td><td>이 프로젝트의 코드명 (Quenya로 "왕국·터전")</td></tr>
    <tr><td>칸반 보드</td><td>지원자 카드를 채용 단계별로 시각화해 관리하는 UI</td></tr>
    <tr><td>RAG</td><td>Retrieval-Augmented Generation — 검색 결과를 근거로 답변을 생성하는 방식</td></tr>
    <tr><td>Tool-Calling Agent</td><td>자연어 명령을 해석해 API를 호출하는 AI 에이전트</td></tr>
    <tr><td>Presigned URL</td><td>AWS S3에 임시로 직접 업로드·다운로드할 수 있게 해주는 인증 URL</td></tr>
    <tr><td>SES</td><td>AWS의 이메일 발송 서비스</td></tr>
    <tr><td>SQS</td><td>AWS의 비동기 처리용 메시지 큐 서비스</td></tr>
    <tr><td>pgvector</td><td>벡터 임베딩을 저장·검색하는 PostgreSQL 확장</td></tr>
    <tr><td>ADR / RBAC</td><td>Architecture Decision Record(아키텍처 결정 기록) / Role-Based Access Control(역할 기반 접근 제어)</td></tr>
  </tbody>
</table>
</div>

<h2 id="forms" class="ap-h2">2. 관련 서식 (작성 예정)</h2>
<p class="ap-body">추후 추가 예정.</p>

<style>
  h2.ap-h2 {
    font-size: 17px;
    font-weight: 700;
    color: #2451FF;
    margin: 40px 0 16px;
    padding-bottom: 10px;
    border-bottom: 1px solid #eee;
  }
  .ap-h2:first-child {
    margin-top: 0;
  }
  .ap-body {
    font-size: 15px;
    line-height: 1.75;
    word-break: keep-all;
    margin: 0 0 12px;
  }
  .ap-list {
    margin: 0 0 12px;
    padding-left: 20px;
    font-size: 14.5px;
    line-height: 1.8;
    word-break: keep-all;
  }
  .ap-list li {
    margin-bottom: 6px;
  }
  .ap-table-wrap {
    overflow-x: auto;
    margin-bottom: 40px;
  }
  table.ap-table {
    width: 100%;
    border-collapse: collapse;
    font-size: 13px;
  }
  table.ap-table th,
  table.ap-table td {
    border: 1px solid #eee;
    padding: 10px 12px;
    text-align: left;
    vertical-align: top;
    word-break: keep-all;
  }
  table.ap-table th {
    background: #f7f7f7;
    font-size: 12px;
    color: #828282;
    white-space: nowrap;
  }
</style>
