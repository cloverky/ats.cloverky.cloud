---
layout: page
title: 사업 개요
permalink: /business-overview/
---

<p class="bo-name">AI 기반 채용 프로세스 자동화 및 지원자 통합 관리 플랫폼</p>

<h2 id="purpose" class="bo-h2">1. 사업 목적</h2>
<p class="bo-body">채용 과정에서 발생하는 반복 업무를 자동화하고, 흩어진 지원자 정보를 하나의 플랫폼으로 통합하여 채용 담당자의 업무 효율성을 높인다. 채용담당자가 공고를 올리고 지원자가 외부 링크로 지원서·이력서를 제출하면, 담당자·면접관이 칸반 보드에서 단계별로 심사·평가한다.</p>

<h2 id="content" class="bo-h2">2. 주요 사업 내용</h2>
<div class="bo-grid">
  <div class="bo-card">
    <p class="bo-card-title">채용 프로세스 자동화</p>
    <p class="bo-card-desc">칸반 보드 기반 단계 관리, 단계 변경 시 자동 메일 발송, 단계 이력 기록</p>
  </div>
  <div class="bo-card">
    <p class="bo-card-title">AI 기반 이력서 분석</p>
    <p class="bo-card-desc">PDF/DOCX 이력서 구조화 추출, RAG 기반 질의응답</p>
  </div>
  <div class="bo-card">
    <p class="bo-card-title">지원자 통합 관리</p>
    <p class="bo-card-desc">지원자 CRUD, 검색·필터, 면접관 배정, 평가 기록, 공고별 지원 현황</p>
  </div>
  <div class="bo-card">
    <p class="bo-card-title">공개 지원 시스템</p>
    <p class="bo-card-desc">외부 공개 링크를 통한 지원서 접수, 이력서 S3 직접 업로드</p>
  </div>
  <div class="bo-card">
    <p class="bo-card-title">인증·권한 체계</p>
    <p class="bo-card-desc">JWT 인증, 역할 3종(관리자 / 채용담당자 / 면접관) 기반 접근 제어</p>
  </div>
</div>

<h2 id="effect" class="bo-h2">3. 기대 효과</h2>
<ul class="bo-list">
  <li><strong>업무 효율</strong> — 반복적인 채용 행정 업무를 자동화해 담당자가 심사·평가에 집중할 수 있다.</li>
  <li><strong>정보 통합</strong> — 흩어져 있던 공고·지원자·평가 데이터를 하나의 시스템으로 모은다.</li>
  <li><strong>의사결정 지원</strong> — AI 기반 이력서 분석과 검색으로 채용담당자의 판단을 보조한다.</li>
  <li><strong>투명성 확보</strong> — 모든 단계 이동과 평가가 이력으로 남아 추후 추적이 가능하다.</li>
  <li><strong>접근성 향상</strong> — 지원자는 로그인 없이 공개 링크만으로 지원할 수 있다.</li>
</ul>

<style>
  .bo-name {
    font-size: 16px;
    font-weight: 700;
    color: #828282;
    margin: 0 0 36px;
    padding-bottom: 16px;
    border-bottom: 1px solid #eee;
    word-break: keep-all;
  }
  h2.bo-h2 {
    font-size: 17px;
    font-weight: 700;
    color: #2451FF;
    margin: 40px 0 16px;
    padding-bottom: 10px;
    border-bottom: 1px solid #eee;
  }
  .bo-body {
    font-size: 15px;
    line-height: 1.75;
    word-break: keep-all;
    margin: 0;
  }
  .bo-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
    gap: 14px;
  }
  .bo-card {
    border: 1px solid #eee;
    border-radius: 8px;
    padding: 16px 18px;
  }
  .bo-card-title {
    font-size: 14px;
    font-weight: 700;
    margin: 0 0 6px;
  }
  .bo-card-desc {
    font-size: 13.5px;
    color: #55575c;
    line-height: 1.6;
    margin: 0;
    word-break: keep-all;
  }
  .bo-list {
    margin: 0 0 40px;
    padding-left: 20px;
    font-size: 14.5px;
    line-height: 1.8;
    word-break: keep-all;
  }
  .bo-list li {
    margin-bottom: 6px;
  }
</style>
