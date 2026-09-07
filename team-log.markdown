---
layout: page
title: 개발 로그 · 팀원
permalink: /team-log/
---

<p class="tl-meta">cloverky(프론트엔드) 본인 로그는 <a href="/role-frontend/">/role-frontend/</a> 참고. 아래는 나머지 팀원 로그.</p>

<div class="tl-entry">
  <p class="tl-date">2026-09-04 <span class="tl-owner">suvisdev · 인프라·에이전트</span></p>
  <p class="tl-title">인프라 완전 이전 — 개인 AWS·자동 배포·팀 셀프서비스 개통</p>
  <ul class="tl-list">
    <li>팀장 이탈로 남의 명의에 얹혀 있던 운영 전부를 개인 AWS(서울)로 하루 만에 이전</li>
    <li>신규 EC2 <code>arda-api</code>(t3.small) · S3 <code>arda-resumes-seuk</code> · SQS <code>arda-mail</code> · SES DKIM 인증, Caddy HTTPS(<code>api.seuk.suvisdev.cloud</code>)</li>
    <li>권한 3단 분리 — 콘솔 관리(MFA) / 팀 열람(이력서 다운로드 불가) / 서버 키(Arda 리소스 한정)</li>
    <li>저장소를 <code>Seuk-Team</code> org로 통합 (Arda 앱 저장소 + 이 문서 사이트)</li>
    <li>자동 배포 개통 — 서버가 2분마다 main 폴링, pull→build→up→헬스체크. main 직접 푸시 금지·PR 셀프 머지로 브랜치 규칙 확정</li>
    <li>더미 지원자 15명 리허설로 presign 글로벌 호스트 서명 버그 실전 검출·수정 (PR #4) — 15/15 관통</li>
    <li>pytest 24분 침묵 사건 — Docker Desktop 다운으로 인한 DB connect 무한 대기, <code>pytest-timeout</code> 60초로 방지 (PR #5)</li>
  </ul>
</div>

<div class="tl-entry">
  <p class="tl-date">2026-09-03 <span class="tl-owner">suvisdev · 백엔드·에이전트</span></p>
  <p class="tl-title">인적성 설문 E2E 검증과 운영 AI 복구 1단계</p>
  <ul class="tl-list">
    <li>API → 메일 감사 → 공개 링크 → 10문항 응답 → 통계까지 E2E 검증 완료</li>
    <li>Anthropic API 키 이슈 해결 (identity key trap)</li>
    <li>Haiku 모델 첫 측정: 채팅 6.8초, 요약 9.1초</li>
    <li>일일 API 비용 약 $0.03</li>
  </ul>
</div>

<div class="tl-entry">
  <p class="tl-date">2026-09-01 <span class="tl-owner">suvisdev · 백엔드·에이전트</span></p>
  <p class="tl-title">지원자 대화형 페이지 · 이력서 반영 · FAQ 챗봇</p>
  <ul class="tl-list">
    <li>지원자 일정 페이지를 대화형 AI 인터페이스로 재설계</li>
    <li>이력서·자소서 텍스트를 AI 요약에 반영</li>
    <li>PR 3건 머지, 실 호출로 전체 파이프라인 검증</li>
    <li><strong>PR #159</strong> 지원자 FAQ API — 무상태 토큰 인증, 급여 등 민감 질문 차단, 프롬프트 인젝션 방어, 테스트 5개 통과</li>
    <li><strong>PR #158</strong> 이력서 파일 추출 — PDF·DOCX·HWPX 지원, 실패 시 None 폴백(LLM 비용 없음)</li>
    <li><strong>PR #157</strong> 대화형 일정 페이지 — PC 2열(AI 캐릭터+채팅) / 모바일 고정 카드+채팅, JSON 노출 버그 수정</li>
  </ul>
</div>

<div class="tl-entry">
  <p class="tl-date">2026-08-31 <span class="tl-owner">suvisdev · 백엔드·에이전트</span></p>
  <ul class="tl-list">
    <li><strong>PR #153</strong> search_users 툴 + 권한 분리 — 이름·이메일 검색+역할 필터, user_role 프롬프트 주입으로 일반 멤버의 관리자 전용 툴 접근 차단</li>
  </ul>
</div>

<div class="tl-entry">
  <p class="tl-date">2026-08-28 <span class="tl-owner">김민아 · QA·모바일</span></p>
  <ul class="tl-list">
    <li>UI 개발 — 지원자 상세(상태변경 버튼), 로그인, 지원자 목록(단계 탭+카드)</li>
    <li><strong>PR #146</strong> 단계 변경 확인 시트, 전환 규칙, 메일 경고</li>
    <li><strong>PR #145</strong> 공고 목록을 앱 진입점으로</li>
    <li><strong>PR #144</strong> 퍼널 바·탭 카운트</li>
    <li><strong>PR #143</strong> 치수 조정, 알약형 단계 칩, 카드형 정보 표시</li>
    <li>Flutter 모바일 앱 — 디자인 토큰 Dart 이식, IBM Plex Sans KR 폰트, 내비게이션 뼈대, 앱 이름 "Arda"로 변경</li>
    <li><strong>ADR-0010</strong> 앱 스택 Flutter로 확정 (데모 범위에서 iOS 제외)</li>
  </ul>
</div>

<div class="tl-entry">
  <p class="tl-date">2026-08-28 <span class="tl-owner">suvisdev · 백엔드·에이전트</span></p>
  <ul class="tl-list">
    <li>STT 비용 로깅 통합 (Whisper)</li>
    <li>E2E 엣지 케이스 8개 시나리오 검증 (결과 0건, 모호한 요청, 잘못된 단계명, 삭제 요청, 멀티턴 ID 추적 등)</li>
    <li>E2E 데모 — 검색→조회→상태변경→메일초안 4단계, 비용 $0.045</li>
    <li><strong>PR #141</strong> 엣지 케이스 API 테스트 41개 (엔드포인트 4종)</li>
    <li><strong>PR #136</strong> 프롬프트 튜닝 — 참조 규칙으로 ID 혼동 수정</li>
    <li><strong>PR #130</strong> 한글 숫자 오탐 방지, 텍스트 채팅 재연결 (ADR-0015)</li>
    <li>테스트 커버리지 총 185개로 확장</li>
  </ul>
</div>

<div class="tl-entry">
  <p class="tl-date">2026-08-27 <span class="tl-owner">이재우 · 인프라</span></p>
  <ul class="tl-list">
    <li>첫 프로덕션 배포 (W2 목표 조기 완료)</li>
    <li>EC2(서울, t3.micro + 2G swap), 컨테이너 4개: db · api · worker · caddy</li>
    <li>API 엔드포인트: <code>https://api.arda.seuk.cloud</code> (Caddy HTTPS)</li>
    <li>메일 파이프라인: api → SQS → worker → SES</li>
  </ul>
</div>

<div class="tl-entry">
  <p class="tl-date">2026-08-26 <span class="tl-owner">팀 전체</span></p>
  <p class="tl-title">Arda ATS 1주차 팀 활동 보고 (08/20~26)</p>
  <ul class="tl-list">
    <li>5인 팀 — 기반 구축, 목업, API·인프라, 백엔드 담당, 에이전트 코어</li>
  </ul>
</div>

<div class="tl-entry">
  <p class="tl-date">2026-08-25 <span class="tl-owner">김민아</span></p>
  <ul class="tl-list">
    <li>백엔드 인수 큐 완료 (3건 머지)</li>
  </ul>
</div>

<style>
  .tl-meta {
    font-size: 13px;
    color: #828282;
    margin: 0 0 36px;
    padding-bottom: 16px;
    border-bottom: 1px solid #eee;
  }
  .tl-entry {
    border-left: 3px solid #ddd;
    padding: 2px 0 2px 16px;
    margin-bottom: 28px;
  }
  .tl-date {
    display: flex;
    align-items: baseline;
    gap: 10px;
    font-size: 13px;
    font-weight: 700;
    color: #12141C;
    margin: 0 0 6px;
  }
  .tl-owner {
    font-size: 12px;
    font-weight: 600;
    color: #2451FF;
    background: #eef2ff;
    padding: 1px 8px;
    border-radius: 10px;
  }
  .tl-title {
    font-size: 14.5px;
    font-weight: 700;
    margin: 0 0 8px;
    word-break: keep-all;
  }
  .tl-list {
    margin: 0;
    padding-left: 20px;
    font-size: 13.5px;
    line-height: 1.7;
    word-break: keep-all;
  }
  .tl-list li {
    margin-bottom: 4px;
  }
  .tl-list code {
    font-size: 12px;
    background: #f2f4f8;
    padding: 1px 5px;
    border-radius: 4px;
  }
</style>
