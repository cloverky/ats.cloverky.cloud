---
layout: page
title: 개발 로그 · 프론트엔드
permalink: /role-frontend/
---

<p class="rf-meta">오너 <strong>cloverky</strong> · 폴더 <code>frontend/</code> · 상태 <strong>확정 v1.0</strong> (2026-08-24, #16·#18 머지)</p>

<h2 class="rf-h2">작업 로그</h2>
<div class="rf-log-entry">
  <p class="rf-log-date">2026-08-28</p>
  <ul class="rf-list">
    <li>백엔드 API 연동 (로그인 · 공고 · 대시보드 · 지원자 · 평가)</li>
    <li>React·Vite·TypeScript 라우팅 및 레이아웃 뼈대 구축</li>
    <li>지원자 칸반 보드 — 드래그로 단계 이동</li>
    <li>공고의 지원자 화면 — 상세 패널, 일괄 단계 변경</li>
  </ul>
</div>
<div class="rf-log-entry">
  <p class="rf-log-date">2026-08-27 · <code>front-applicants</code></p>
  <ul class="rf-list">
    <li>대시보드 — 면접 일정 슬롯 그룹핑, 전형 현황 펀넬 추가</li>
    <li>면접 일정 페이지 신규 (mockup + React, 슬롯 필터링)</li>
    <li>목업 12개 화면 번들 → localhost:5500 단일 접근</li>
    <li>React 앱 셸 목업 규격 맞춤 (사이드바 아이콘·아르DA·제목 띠)</li>
    <li>빈 화면 3개 구현: 지원자 / 평가 현황 / 설정</li>
    <li>아르DA 패널 부제·Ctrl K 라벨 제거</li>
    <li>아르DA 패널 상태 페이지 이동 간 유지 (localStorage)</li>
  </ul>
</div>

<h2 class="rf-h2">일정 · 운영 (전 도메인 공통)</h2>
<ul class="rf-list">
  <li><strong>초기 버전: 09/04(금) · 1차 완성: 09/30(수).</strong> 주차 기준: W1 08/24~28 · W2 08/31~09/04 · W3 09/07~11 · W4 09/14~18 · W5 09/21~25 · 09/28~30 통합 버퍼.</li>
  <li>주 단위로 스스로 계획하고 진행한다. 조정 시 이 문서를 갱신하고, 타 도메인에 걸리는 변경은 06-weekly.md에 기록해 팀장과 맞춘다.</li>
  <li>팀장 머지·검수는 매주 금요일 최소 1회. 팀장 승인이 필요한 PR은 목요일까지 올린다. 도메인 내부 PR은 수시 셀프 머지.</li>
</ul>

<h2 class="rf-h2">1. 미션</h2>
<p class="rf-body">목업 8장을 실제 React 제품으로. "UI가 스펙이다"의 그 UI를 최종 제품까지 끌고 간다. 칸반 드래그·낙관적 업데이트가 이 프로젝트의 얼굴이다.</p>

<h2 class="rf-h2">2. 범위</h2>
<div class="rf-scope-grid">
  <div>
    <p class="rf-scope-label in">포함</p>
    <ul class="rf-list">
      <li>React 앱 뼈대: Vite·TS·라우팅·토큰 CSS 변수 이식·공통 컴포넌트(사이드바·테이블·뱃지·버튼·인풋·토스트) — 팀장 전담에서 이관</li>
      <li>목업 잔여 1장: B1 공고 목록 — minahdev로부터 인수</li>
      <li>전 화면의 페이지 컴포넌트화 + API 연동</li>
      <li>칸반 뷰 D2 · 드래그 단계 이동 D3 · 낙관적 업데이트·롤백 — 팀장 전담에서 이관</li>
      <li>일괄 단계 변경 D9 · 업로드 진행률 F4 · 반응형(768px 모바일 웹)</li>
      <li>에이전트 UI 시안 협업 (suvisdev 주도, agent.md M1)</li>
      <li>Vercel 배포 설정 (프로젝트 연결은 인프라, 빌드 설정은 프론트)</li>
    </ul>
  </div>
  <div>
    <p class="rf-scope-label out">제외</p>
    <ul class="rf-list">
      <li>mockup.html 색 리터럴 정리 — 팀장 (W1-2 별건). 그 전까지 토큰 :root 블록 복사 규칙 유지</li>
      <li>대시보드 화면 — 보류 유지 (W1-2 결정, 3주차 이후 여유 시)</li>
      <li>모바일 네이티브 앱 — 앱 도메인. 여기서는 반응형 웹까지만</li>
    </ul>
  </div>
</div>

<h2 class="rf-h2">3. 인터페이스 계약</h2>
<p class="rf-body"><strong>의존</strong> — 백엔드 API(02-api.md). M1·M2는 목데이터로 진행하므로 백엔드를 기다리지 않는다. 목데이터 필드명은 01-erd.md와 동일하게.</p>
<p class="rf-body"><strong>제공</strong> — 공통 컴포넌트·토큰. 에이전트 UI가 프론트 화면 안에 들어오므로, suvisdev의 UI 코드 PR은 프론트 오너 승인을 거친다.</p>

<h2 class="rf-h2">4. 주간 계획</h2>
<div class="rf-table-wrap">
<table class="rf-table">
  <thead>
    <tr><th>주차</th><th>단계</th><th>내용</th><th>완료 기준</th></tr>
  </thead>
  <tbody>
    <tr>
      <td>W1<br><span class="rf-td-note">~08/28</span></td>
      <td>M1 뼈대</td>
      <td>B1 목업 인수 완성 · React 뼈대(라우팅·토큰 이식·공통 컴포넌트) · 로그인+공고 목록 페이지(목데이터)</td>
      <td>목업 8장 전부 존재. <code>npm run dev</code>로 로그인→공고 목록 이동. 토큰이 CSS 변수 파일 하나로 모임</td>
    </tr>
    <tr>
      <td>W2<br><span class="rf-td-note">~09/04</span></td>
      <td>M2 전 화면 정적<br><span class="rf-flag">🚩초기 버전</span></td>
      <td>지원자 통합검색 · 공고의 지원자(테이블+상세 패널+"다음 지원자") · 평가 현황 · 설정 · 지원 폼(공개 라우트) · Vercel 프리뷰 배포 · 지원 폼만 실 API 제출 연동</td>
      <td>전 화면이 목데이터로 동작하고 Vercel URL로 접근 가능. 목업과 나란히 놓고 구분 안 됨. 각 화면 loading/empty/error 3종</td>
    </tr>
    <tr>
      <td>W3<br><span class="rf-td-note">~09/11</span></td>
      <td>M3 API 연동</td>
      <td>JWT 로그인 플로우 · 목록·상세·평가·검색·단계 필터 · 지원 제출+업로드 진행률 F4</td>
      <td>목데이터 import 0개. 검색·필터가 실제 10만 건을 친다. 업로드 진행률이 S3 직행 전송을 표시</td>
    </tr>
    <tr>
      <td>W4<br><span class="rf-td-note">~09/18</span></td>
      <td>M4 칸반</td>
      <td>칸반 뷰 토글 D2 · 드래그 D3(낙관적 업데이트, 실패 롤백 + 토스트) · 일괄 변경 D9 · 에이전트 UI 구현 협업</td>
      <td>드래그 실패 시 카드가 원위치로 롤백되고 토스트가 뜬다(네트워크 차단으로 시연 가능)</td>
    </tr>
    <tr>
      <td>W5<br><span class="rf-td-note">~09/25</span></td>
      <td>배포·마감</td>
      <td>Vercel 배포 · 극단값·반응형·접근성 마감</td>
      <td>프로덕션 URL에서 전 시나리오 동작</td>
    </tr>
    <tr>
      <td>09/28~30</td>
      <td>버퍼</td>
      <td>폴리시 · 잔여 버그</td>
      <td><strong>09/30 1차 완성</strong></td>
    </tr>
  </tbody>
</table>
</div>

<h2 class="rf-h2">5. 작업 큐 — 위에서부터 순서대로</h2>
<div class="rf-table-wrap">
<table class="rf-table">
  <thead>
    <tr><th>#</th><th>작업</th><th>기능</th><th>지시서</th><th>선행</th></tr>
  </thead>
  <tbody>
    <tr><td>1</td><td>B1 공고 목록 화면 목업 (인수)</td><td>B1</td><td>있음</td><td>없음</td></tr>
    <tr><td>2</td><td>React 뼈대 — 라우팅·토큰·공통 컴포넌트</td><td>—</td><td>없음 — 오너 작성</td><td>없음</td></tr>
    <tr><td>3</td><td>로그인·공고 목록 페이지화</td><td>A1·B1</td><td>없음 — 오너 작성</td><td>2번</td></tr>
    <tr><td>4</td><td>공고의 지원자 화면 (테이블+상세 패널)</td><td>D1·D4</td><td>없음 — 오너 작성</td><td>2번</td></tr>
    <tr><td>5</td><td>통합검색·평가·설정·지원 폼 페이지화</td><td>H1·E1·A2·C1</td><td>없음 — 오너 작성</td><td>2번</td></tr>
    <tr><td>6</td><td>에이전트 UI — ⌘K 콘솔 + 콘솔 내 확인 카드 (ADR-0009, 08/25 확정). 시안 불필요, 구현 협업만 남음(W4)</td><td>—</td><td>agent.md M1</td><td>4번</td></tr>
    <tr><td>7</td><td>API 연동 (M3 전체)</td><td>—</td><td>없음 — 오너 작성</td><td>백엔드 M1</td></tr>
    <tr><td>8</td><td>칸반 + 드래그 + 낙관적 업데이트</td><td>D2·D3·D9</td><td>없음 — 오너 작성</td><td>7번</td></tr>
    <tr><td>9</td><td>Vercel 배포</td><td>—</td><td>인프라와 협업</td><td>7번</td></tr>
  </tbody>
</table>
</div>
<p class="rf-note">지시서 없는 항목은 오너가 직접 쪼개 진행한다. React 이식 시에도 화면 하나 = PR 하나, 목업에 없는 요소·토큰에 없는 값이 필요하면 멈추고 팀장에게.</p>

<h2 class="rf-h2">6. 리스크</h2>
<ul class="rf-list">
  <li><strong>목업→React 이식에서 룩이 미묘하게 틀어지는 것.</strong> 완료 기준을 "나란히 놓고 구분 안 됨"으로 고정하고, PR마다 스크린샷 비교를 붙인다.</li>
  <li><strong>칸반 낙관적 업데이트가 마지막 주에 몰림.</strong> M4를 W3 후반에 시작하도록 M3에서 상세 패널까지 끝내둔다.</li>
  <li>색 리터럴 정리(팀장) 전에 공통 CSS 파일을 만들면 두 번 일한다 — 정리 머지 후에 토큰 파일화한다.</li>
</ul>

<h2 class="rf-h2">7. 면접 스토리</h2>
<ul class="rf-list">
  <li>드래그 실패 시 낙관적 업데이트를 어떻게 롤백했는가 (D3 — 실패 주입 시연 포함)</li>
  <li>정적 목업 8장을 컴포넌트로 이식한 전략 — 공통 조각을 어떻게 추출했고 토큰이 왜 전부 CSS 변수인가</li>
</ul>

<style>
  .rf-meta {
    font-size: 13px;
    color: #828282;
    margin: 0 0 36px;
    padding-bottom: 16px;
    border-bottom: 1px solid #eee;
  }
  .rf-meta code {
    font-size: 12px;
  }
  .rf-log-entry {
    border-left: 3px solid #2451FF;
    padding: 2px 0 2px 16px;
    margin-bottom: 8px;
  }
  .rf-log-date {
    font-size: 13px;
    font-weight: 700;
    color: #12141C;
    margin: 0 0 8px;
  }
  .rf-log-date code {
    font-size: 12px;
    font-weight: 500;
    color: #2451FF;
    background: #eef2ff;
    padding: 1px 6px;
    border-radius: 4px;
  }
  h2.rf-h2 {
    font-size: 17px;
    font-weight: 700;
    color: #2451FF;
    margin: 40px 0 14px;
    padding-bottom: 10px;
    border-bottom: 1px solid #eee;
  }
  .rf-body {
    font-size: 15px;
    line-height: 1.75;
    word-break: keep-all;
    margin: 0 0 10px;
  }
  .rf-list {
    margin: 0;
    padding-left: 20px;
    font-size: 14.5px;
    line-height: 1.75;
    word-break: keep-all;
  }
  .rf-list li {
    margin-bottom: 6px;
  }

  .rf-scope-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
    gap: 24px;
  }
  .rf-scope-label {
    font-size: 12.5px;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 0.04em;
    margin: 0 0 8px;
  }
  .rf-scope-label.in { color: #1a8f4c; }
  .rf-scope-label.out { color: #aaa; }

  .rf-table-wrap {
    overflow-x: auto;
    margin-bottom: 8px;
  }
  table.rf-table {
    width: 100%;
    border-collapse: collapse;
    font-size: 13px;
  }
  table.rf-table th,
  table.rf-table td {
    border: 1px solid #eee;
    padding: 10px 12px;
    text-align: left;
    vertical-align: top;
    word-break: keep-all;
  }
  table.rf-table th {
    background: #f7f7f7;
    font-size: 12px;
    color: #828282;
    white-space: nowrap;
  }
  table.rf-table code {
    font-size: 12px;
    background: #f2f4f8;
    padding: 1px 5px;
    border-radius: 4px;
  }
  .rf-td-note {
    font-size: 11.5px;
    color: #828282;
  }
  .rf-flag {
    display: block;
    margin-top: 4px;
    font-size: 11.5px;
    color: #2451FF;
    font-weight: 700;
  }
  .rf-note {
    font-size: 13px;
    color: #828282;
    line-height: 1.7;
    word-break: keep-all;
    margin: 0 0 8px;
  }
</style>
