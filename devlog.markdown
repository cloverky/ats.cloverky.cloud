---
layout: page
title: 개발 로그
permalink: /devlog/
---

스프린트별 일자 단위 작업 기록. 각 스프린트를 클릭하면 날짜·담당·진행 상태가 담긴 상세 로그로 이동한다.

<ul class="devlog-list">
  <li class="devlog-row">
    <a class="devlog-link" href="/sprint-1/">
      <span class="devlog-sprint">Sprint 1</span>
      <span class="devlog-date">8.20 ~ 9.2</span>
      <span class="devlog-goal">개발 환경 및 기반 설계</span>
    </a>
  </li>
  <li class="devlog-row disabled">
    <span class="devlog-sprint">Sprint 2</span>
    <span class="devlog-date">9.3 ~ 9.16</span>
    <span class="devlog-goal">핵심 기능 1차 구현</span>
    <span class="devlog-pending">작성 예정</span>
  </li>
  <li class="devlog-row disabled">
    <span class="devlog-sprint">Sprint 3</span>
    <span class="devlog-date">9.17 ~ 9.30</span>
    <span class="devlog-goal">단계 전환 · 알림 · 대용량 데이터</span>
    <span class="devlog-pending">작성 예정</span>
  </li>
  <li class="devlog-row disabled">
    <span class="devlog-sprint">Sprint 4</span>
    <span class="devlog-date">10.1 ~ 10.14</span>
    <span class="devlog-goal">GraphRAG 통합 · QA</span>
    <span class="devlog-pending">작성 예정</span>
  </li>
  <li class="devlog-row disabled">
    <span class="devlog-sprint">Sprint 5</span>
    <span class="devlog-date">10.15 ~ 10.27</span>
    <span class="devlog-goal">배포 및 데모 준비</span>
    <span class="devlog-pending">작성 예정</span>
  </li>
</ul>

<h2 class="devlog-h2">역할별 로그</h2>
<ul class="devlog-list">
  <li class="devlog-row">
    <a class="devlog-link" href="/role-frontend/">
      <span class="devlog-sprint">FE</span>
      <span class="devlog-date">cloverky</span>
      <span class="devlog-goal">프론트엔드 로드맵 — 주간 계획·작업 큐·리스크·작업 로그</span>
    </a>
  </li>
  <li class="devlog-row">
    <a class="devlog-link" href="/team-log/">
      <span class="devlog-sprint">팀</span>
      <span class="devlog-date">팀원</span>
      <span class="devlog-goal">이재우·김민아·suvisdev 등 팀원별 작업 로그</span>
    </a>
  </li>
</ul>

<style>
  h2.devlog-h2 {
    font-size: 15px;
    font-weight: 700;
    color: #828282;
    margin: 0 0 8px;
  }
  .devlog-list {
    list-style: none;
    margin: 0 0 40px;
    padding: 0;
  }
  .devlog-row {
    display: flex;
    align-items: center;
    gap: 20px;
    padding: 16px 4px;
    border-top: 1px solid #eee;
  }
  .devlog-row:first-child {
    border-top: 0;
  }
  .devlog-link {
    display: flex;
    align-items: center;
    gap: 20px;
    flex: 1;
    color: inherit;
    text-decoration: none;
  }
  .devlog-link:hover .devlog-sprint {
    text-decoration: underline;
  }
  .devlog-row.disabled {
    color: #aaa;
  }
  .devlog-sprint {
    flex: 0 0 72px;
    font-size: 14px;
    font-weight: 700;
    color: #2451FF;
  }
  .devlog-row.disabled .devlog-sprint {
    color: #aaa;
  }
  .devlog-date {
    flex: 0 0 100px;
    font-size: 12.5px;
    color: #828282;
  }
  .devlog-goal {
    flex: 1;
    font-size: 14px;
    word-break: keep-all;
  }
  .devlog-pending {
    flex: 0 0 auto;
    font-size: 12px;
    font-weight: 700;
    color: #aaa;
    background: #f5f5f5;
    padding: 3px 10px;
    border-radius: 10px;
  }
</style>
