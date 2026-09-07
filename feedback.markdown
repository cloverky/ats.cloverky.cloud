---
layout: page
title: 피드백 트래커
permalink: /feedback/
---

<p class="fb-meta">멘토·강사로부터 받은 피드백과 반영 여부를 기록한다. 아직 피드백이 없는 팀원은 표시하지 않는다.</p>

<div class="fb-entry">
  <p class="fb-head">
    <span class="fb-owner"><i class="fb-dot" style="background:#7aa2f7"></i>진수택 · suvisdev</span>
    <span class="status-badge status-todo">대기</span>
  </p>
  <p class="fb-received"><strong>받은 날짜</strong> 2026-09-04 · <strong>출처</strong> IBM 강사님 멘토링</p>
  <div class="fb-block">
    <p class="fb-label">피드백</p>
    <p class="fb-body">이번 주 숙제 — 기능 레벨의 설계 및 전체적인 아키텍처(혹은 서비스 진행 흐름)를 조금 더 구체적으로 완성해올 것. 기술 스택까지 고려하여 구현 가능성을 염두에 두어야 하며, 어떻게 구현할지가 안 떠오른다면 간단하게 실험해볼 것</p>
  </div>
</div>

<div class="fb-entry">
  <p class="fb-head">
    <span class="fb-owner"><i class="fb-dot" style="background:#7aa2f7"></i>진수택 · suvisdev</span>
    <span class="status-badge status-done">반영 완료</span>
  </p>
  <p class="fb-received"><strong>받은 날짜</strong> 2026-08-27 · <strong>출처</strong> IBM 강사님 멘토링</p>
  <div class="fb-block">
    <p class="fb-label">피드백</p>
    <p class="fb-body">프로젝트 소개가 기능 나열에 그쳐 매력과 핵심 포인트가 드러나지 않고, 실무(현업) 관점과의 접점이 약함 — 실제 채용 현장의 문제를 해결하는 서사로 더 가까워질 것</p>
  </div>
  <div class="fb-block">
    <p class="fb-label">반영 (2026-08-28)</p>
    <p class="fb-body">소주제를 '현업 pain point 해결' 중심으로 전면 재구성 — ① 보안에 강한 로컬 AI 에이전트 신설(채용 데이터 반출 우려 → 온프레미스 sLLM·STT로 내부망 완결), ② 면접 일정 자동화 신설(수 회 메일 왕복 조율 제거), ③ 24시간 지원자 셀프서비스 신설(전형 현황 실시간 확인·챗봇 응대로 반복 문의 제거), ④ STT를 [STT→RAG→sLLM] 근거 인용 분석 파이프라인으로 확장. 기능 나열이 아닌 '누구의 어떤 비효율을 없애는가' 구조로 재작성</p>
  </div>
</div>

<p class="fb-none">그 외 팀원(박소연·이재우·김민아·이우정)은 아직 기록된 피드백 없음.</p>

<style>
  .fb-meta {
    font-size: 13px;
    color: #828282;
    margin: 0 0 36px;
    padding-bottom: 16px;
    border-bottom: 1px solid #eee;
  }
  .fb-entry {
    border: 1px solid #eee;
    border-radius: 8px;
    padding: 20px 22px;
    margin-bottom: 20px;
  }
  .fb-head {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin: 0 0 10px;
  }
  .fb-owner {
    display: flex;
    align-items: center;
    gap: 8px;
    font-size: 14px;
    font-weight: 700;
  }
  .fb-dot {
    display: inline-block;
    width: 9px;
    height: 9px;
    border-radius: 50%;
    flex-shrink: 0;
  }
  .fb-received {
    font-size: 13px;
    color: #828282;
    margin: 0 0 16px;
  }
  .fb-block {
    margin-bottom: 14px;
  }
  .fb-block:last-child {
    margin-bottom: 0;
  }
  .fb-label {
    font-size: 12px;
    font-weight: 700;
    color: #2451FF;
    text-transform: uppercase;
    letter-spacing: 0.04em;
    margin: 0 0 6px;
  }
  .fb-body {
    font-size: 14px;
    line-height: 1.7;
    word-break: keep-all;
    margin: 0;
  }
  .fb-none {
    font-size: 13px;
    color: #828282;
    margin: 0 0 40px;
  }
  .status-badge {
    display: inline-block;
    font-size: 12px;
    font-weight: 700;
    padding: 2px 10px;
    border-radius: 10px;
    white-space: nowrap;
  }
  .status-done {
    background-color: #e8f7ee;
    color: #1a8f4c;
  }
  .status-todo {
    background-color: #f5f5f5;
    color: #828282;
  }
</style>
