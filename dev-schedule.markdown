---
layout: page
title: 단계별 개발 일정
permalink: /dev-schedule/
---

개발 기간은 **2026년 8월 20일(목) ~ 10월 27일(화), 총 69일(약 10주)**이며, 2주 단위 스프린트로 애자일 스크럼 방식으로 진행한다. 각 스프린트는 스프린트 목표를 기준으로 팀원별 작업을 배분하고, 스프린트 종료 시점마다 리뷰·회고를 거쳐 다음 스프린트에 반영한다.

<div class="kanban-legend">
  <div class="legend-item"><span class="legend-dot owner-jw"></span>이재우 <small>백엔드·총괄</small></div>
  <div class="legend-item"><span class="legend-dot owner-wj"></span>이우정 <small>검색·데이터</small></div>
  <div class="legend-item"><span class="legend-dot owner-ma"></span>김민아 <small>파일·알림</small></div>
  <div class="legend-item"><span class="legend-dot owner-sy"></span>박소연 <small>프론트엔드</small></div>
  <div class="legend-item"><span class="legend-dot owner-st"></span>진수택 <small>인프라·품질</small></div>
</div>

<div class="kanban-board">

  <div class="kanban-col">
    <a class="kanban-col-header kanban-col-header-link" href="/sprint-1/">
      <span class="kanban-sprint">Sprint 1</span>
      <span class="kanban-date">8.20 ~ 9.2</span>
      <p class="kanban-goal">개발 환경 및 기반 설계</p>
    </a>
    <div class="kanban-card owner-jw"><span class="card-owner">이재우</span>DB 스키마 1차 설계, FastAPI 프로젝트 구조 세팅</div>
    <div class="kanban-card owner-wj"><span class="card-owner">이우정</span>검색 인덱스 전략 설계, 개발 DB 구성</div>
    <div class="kanban-card owner-ma"><span class="card-owner">김민아</span>S3 / SES / SQS 리소스 프로비저닝</div>
    <div class="kanban-card owner-sy"><span class="card-owner">박소연</span>React·TS 프로젝트 스캐폴딩, 로그인 화면</div>
    <div class="kanban-card owner-st"><span class="card-owner">진수택</span>Docker 개발 환경, GitHub Actions CI 초기 세팅</div>
  </div>

  <div class="kanban-col">
    <div class="kanban-col-header">
      <span class="kanban-sprint">Sprint 2</span>
      <span class="kanban-date">9.3 ~ 9.16</span>
      <p class="kanban-goal">핵심 기능 1차 구현</p>
    </div>
    <div class="kanban-card owner-jw"><span class="card-owner">이재우</span>공고 / 지원자 CRUD API 구현</div>
    <div class="kanban-card owner-wj"><span class="card-owner">이우정</span>검색·필터 API 1차 구현</div>
    <div class="kanban-card owner-ma"><span class="card-owner">김민아</span>이력서 S3 업로드 API, 지원 폼 연동</div>
    <div class="kanban-card owner-sy"><span class="card-owner">박소연</span>지원자 목록·상세, 공고 관리 화면</div>
    <div class="kanban-card owner-st"><span class="card-owner">진수택</span>EC2 배포 파이프라인 구축</div>
  </div>

  <div class="kanban-col">
    <div class="kanban-col-header">
      <span class="kanban-sprint">Sprint 3</span>
      <span class="kanban-date">9.17 ~ 9.30</span>
      <p class="kanban-goal">단계 전환 · 알림 · 대용량 데이터</p>
    </div>
    <div class="kanban-card owner-jw"><span class="card-owner">이재우</span>지원자 단계 전환(상태 머신) 로직 구현</div>
    <div class="kanban-card owner-wj"><span class="card-owner">이우정</span>더미 지원자 10만 건 적재, 인덱스 튜닝</div>
    <div class="kanban-card owner-ma"><span class="card-owner">김민아</span>SQS 메일 발송 큐 연동</div>
    <div class="kanban-card owner-sy"><span class="card-owner">박소연</span>모바일 반응형 화면 대응</div>
    <div class="kanban-card owner-st"><span class="card-owner">진수택</span>API 자동화 테스트 구축</div>
  </div>

  <div class="kanban-col">
    <div class="kanban-col-header">
      <span class="kanban-sprint">Sprint 4</span>
      <span class="kanban-date">10.1 ~ 10.14</span>
      <p class="kanban-goal">GraphRAG 통합 · QA</p>
    </div>
    <div class="kanban-card owner-jw"><span class="card-owner">이재우</span>GraphRAG 파이프라인 연동 지원</div>
    <div class="kanban-card owner-wj"><span class="card-owner">이우정</span>검색 응답 속도 튜닝</div>
    <div class="kanban-card owner-ma"><span class="card-owner">김민아</span>알림 발송 안정화·재시도 로직</div>
    <div class="kanban-card owner-sy"><span class="card-owner">박소연</span>프론트-백엔드 통합 테스트, UX 개선</div>
    <div class="kanban-card owner-st"><span class="card-owner">진수택</span>QA 시나리오 작성 및 회귀 테스트</div>
  </div>

  <div class="kanban-col">
    <div class="kanban-col-header">
      <span class="kanban-sprint">Sprint 5</span>
      <span class="kanban-date">10.15 ~ 10.27</span>
      <p class="kanban-goal">배포 및 데모 준비</p>
    </div>
    <div class="kanban-card owner-jw"><span class="card-owner">이재우</span>전체 기능 점검, 릴리즈 노트 작성</div>
    <div class="kanban-card owner-wj"><span class="card-owner">이우정</span>최종 쿼리·인덱스 점검</div>
    <div class="kanban-card owner-ma"><span class="card-owner">김민아</span>파일·알림 최종 점검</div>
    <div class="kanban-card owner-sy"><span class="card-owner">박소연</span>데모 시나리오 UI 마무리</div>
    <div class="kanban-card owner-st"><span class="card-owner">진수택</span>프로덕션 배포 및 모니터링 세팅</div>
  </div>

</div>

<style>
  .kanban-legend {
    display: flex;
    flex-wrap: wrap;
    gap: 8px 20px;
    margin: 24px 0 32px;
    padding-bottom: 16px;
    border-bottom: 1px solid #eee;
  }
  .legend-item {
    display: flex;
    align-items: center;
    gap: 8px;
    font-size: 14px;
    font-weight: 700;
  }
  .legend-item small {
    font-weight: 400;
    color: #828282;
  }
  .legend-dot {
    display: inline-block;
    width: 10px;
    height: 10px;
    border-radius: 50%;
    flex-shrink: 0;
  }
  .owner-jw { background-color: #2a7ae2; }
  .owner-wj { background-color: #16a394; }
  .owner-ma { background-color: #e2972a; }
  .owner-sy { background-color: #7c5cbf; }
  .owner-st { background-color: #e2572a; }

  .kanban-board {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(230px, 1fr));
    gap: 20px;
    margin-bottom: 40px;
  }
  .kanban-col {
    display: flex;
    flex-direction: column;
    gap: 10px;
  }
  .kanban-col-header {
    display: block;
    background-color: #f7f7f7;
    border-radius: 6px;
    padding: 12px 14px;
    margin-bottom: 4px;
  }
  .kanban-col-header-link {
    color: inherit;
    text-decoration: none;
    transition: background-color 0.15s ease;
  }
  .kanban-col-header-link:hover {
    background-color: #eef4fd;
  }
  .kanban-sprint {
    display: block;
    font-size: 13px;
    font-weight: 700;
    color: #2a7ae2;
  }
  .kanban-date {
    display: block;
    font-size: 12px;
    color: #828282;
    margin-top: 2px;
  }
  .kanban-goal {
    font-size: 13px;
    font-weight: 700;
    margin: 8px 0 0;
    word-break: keep-all;
  }
  .kanban-card {
    background-color: #fff;
    border: 1px solid #eee;
    border-left: 4px solid #ccc;
    border-radius: 6px;
    padding: 10px 12px;
    font-size: 13px;
    line-height: 1.5;
    word-break: keep-all;
  }
  .kanban-card.owner-jw { border-left-color: #2a7ae2; }
  .kanban-card.owner-wj { border-left-color: #16a394; }
  .kanban-card.owner-ma { border-left-color: #e2972a; }
  .kanban-card.owner-sy { border-left-color: #7c5cbf; }
  .kanban-card.owner-st { border-left-color: #e2572a; }
  .card-owner {
    display: block;
    font-size: 11px;
    font-weight: 700;
    color: #828282;
    margin-bottom: 3px;
  }
</style>
