---
layout: page
title: 개발 요구 사항
permalink: /dev-requirements/
---

<h2 id="purpose" class="dr-h2">1. 목적</h2>
<p class="dr-body">채용 프로세스 전 과정(공고 등록 → 지원 접수 → 서류 검토 → 면접 → 합불 통보)을 하나의 웹 플랫폼으로 구현하고, AI 기술을 접목하여 이력서 분석과 정보 검색을 자동화한다.</p>

<h2 id="scope" class="dr-h2">2. 개발 범위</h2>
<div class="dr-table-wrap">
<table class="dr-table">
  <thead>
    <tr><th>요구 ID</th><th>기능</th><th>검수 기준</th></tr>
  </thead>
  <tbody>
    <tr><td>SFR-001</td><td><strong>이력서 파싱</strong> — PDF/DOCX 업로드 시 이름·학력·경력·기술스택 자동 추출</td><td>주요 필드 추출 정확도 90% 이상</td></tr>
    <tr><td>SFR-002</td><td><strong>칸반 보드</strong> — 지원자 카드를 드래그하여 채용 단계 전환</td><td>상태 전환 시 DB 반영 200ms 이내</td></tr>
    <tr><td>SFR-003</td><td><strong>Tool-Calling Agent</strong> — 자연어 명령으로 지원자 검색·일정 조회·통계 요청 처리</td><td>도구 호출 정확도 85% 이상, 지원 도구 5종 이상</td></tr>
    <tr><td>SFR-004</td><td><strong>RAG 질의응답</strong> — 이력서·채용 공고 기반 자연어 질의응답 (pgvector)</td><td>Top-5 문서 추출 Recall@5 90% 이상</td></tr>
    <tr><td>SFR-005</td><td><strong>지원자 관리</strong> — 지원자 CRUD, 검색·필터링, 채용 단계별 목록 조회</td><td>전체 CRUD 정상 동작, 페이지네이션 지원</td></tr>
    <tr><td>SFR-006</td><td><strong>이메일 알림</strong> — 채용 단계 변경 시 SES 기반 자동 이메일 발송</td><td>SQS 큐 연동, 발송 성공률 99% 이상</td></tr>
  </tbody>
</table>
</div>

<h2 id="applicant-data" class="dr-h2">3. 지원자 데이터 수집 및 연계</h2>
<p class="dr-body">지원자는 로그인 없이 외부 공개 링크로 지원서를 제출한다. 이력서 파일은 presigned URL로 브라우저에서 S3에 직접 업로드해 API 서버를 거치지 않는다. 접수된 데이터는 단계 흐름을 따라 담당자·면접관에게 연계된다.</p>
<p class="dr-body">단계 흐름: 지원 접수 → 서류 검토 → 1차 면접 → 2차 면접 → 최종 합격 / 불합격</p>
<ul class="dr-list">
  <li>각 단계 전환 시 단계 이력이 자동으로 기록됨</li>
  <li>단계 변경 시 자동 메일 발송 (SQS + SES 비동기 처리)</li>
  <li>면접관 배정 및 단계별 평가 기록</li>
  <li>모든 이동과 평가는 이력으로 남아 추후 감사 추적 가능</li>
</ul>

<h2 id="ai-pipeline" class="dr-h2">4. GraphRAG 파이프라인 구축</h2>
<p class="dr-body">이력서·공고 데이터를 pgvector에 임베딩하고, 자연어 질의를 도구 호출(Tool-Calling)로 변환해 검색·통계·일정 조회를 처리한다.</p>
<div class="dr-table-wrap">
<table class="dr-table">
  <thead>
    <tr><th>기능</th><th>설명</th><th>기술</th></tr>
  </thead>
  <tbody>
    <tr><td>이력서 파싱</td><td>PDF/DOCX에서 이름·학력·경력·기술스택을 구조화 데이터로 추출</td><td>Python, LLM</td></tr>
    <tr><td>RAG 질의응답</td><td>이력서와 공고 내용을 임베딩하여 자연어 질의에 답변</td><td>pgvector, Claude API</td></tr>
    <tr><td>Tool-Calling Agent</td><td>자연어 명령을 도구 호출로 변환하여 검색·통계 처리</td><td>Claude Tool Use</td></tr>
  </tbody>
</table>
</div>
<p class="dr-note">AI가 합불을 결정하지 않는다. 합불 확정은 항상 사람이 한다 (ADR-0003).</p>

<h2 id="agent-expansion" class="dr-h2">4-1. AI 에이전트 확장</h2>
<p class="dr-body">지원자 개인정보가 외부 API로 나가지 않도록, 경량 언어모델과 STT를 사내망 안에서 직접 구동하는 방향으로 에이전트 범위를 넓힌다. "입력 → 모델 추론 → 출력"이 전부 내부망에서 끝난다.</p>
<div class="dr-table-wrap">
<table class="dr-table">
  <thead>
    <tr><th>기능</th><th>설명</th></tr>
  </thead>
  <tbody>
    <tr><td>24시간 면접 일정 자동화</td><td>면접관 가능 시간과 지원자 선택을 에이전트가 조율. 지원자는 메일 링크로 언제든 상태·일정 확인 (반복 연락 불필요)</td></tr>
    <tr><td>면접 분석 (STT → RAG → 경량 LLM)</td><td>면접 음성을 텍스트로 변환 후 RAG로 근거를 찾아 요약. 1건당 약 $0.045 수준으로 비용 추적</td></tr>
    <tr><td>지원자 대화형 문의 (FAQ)</td><td>지원자가 자연어로 일정·상태를 물으면 답변. 급여 등 민감 질문 차단, 프롬프트 인젝션 방어</td></tr>
  </tbody>
</table>
</div>
<p class="dr-note">모바일 앱(Flutter)도 데모 범위에 포함한다 — iOS는 제외.</p>

<h2 id="management" class="dr-h2">5. 정량 평가 기반 지원자 관리 기능</h2>
<ul class="dr-list">
  <li>지원자 CRUD</li>
  <li>검색·필터 기능 (이름·학교·기술스택 기반)</li>
  <li>면접관 배정 및 평가 기록</li>
  <li>공개 지원 폼 (로그인 없이 외부 링크로 지원)</li>
  <li>모바일 반응형 UI</li>
</ul>

<h2 id="security" class="dr-h2">7. 보안 및 개인정보 보호</h2>
<div class="dr-table-wrap">
<table class="dr-table">
  <thead>
    <tr><th>요구 ID</th><th>항목</th><th>검수 기준</th></tr>
  </thead>
  <tbody>
    <tr><td>SEC-001</td><td>인증·인가 (JWT, CORS, 암호화)</td><td>미인증 요청 401/403 차단, AES-256 암호화</td></tr>
    <tr><td>SEC-002</td><td>데이터 보안 (S3 암호화, IAM 제어)</td><td>S3 SSE 활성화, IAM 정책 적용</td></tr>
  </tbody>
</table>
</div>
<p class="dr-sub">역할 기반 접근 제어 (RBAC)</p>
<div class="dr-table-wrap">
<table class="dr-table">
  <thead>
    <tr><th>역할</th><th>권한 범위</th></tr>
  </thead>
  <tbody>
    <tr><td>관리자</td><td>전체 시스템 설정, 사용자 관리, 모든 데이터 접근</td></tr>
    <tr><td>채용담당자</td><td>공고 관리, 지원자 관리, 단계 전환, 면접관 배정</td></tr>
    <tr><td>면접관</td><td>배정된 지원자 조회, 평가 입력</td></tr>
  </tbody>
</table>
</div>

<style>
  h2.dr-h2 {
    font-size: 17px;
    font-weight: 700;
    color: #2451FF;
    margin: 40px 0 16px;
    padding-bottom: 10px;
    border-bottom: 1px solid #eee;
  }
  .dr-h2:first-child {
    margin-top: 0;
  }
  .dr-body {
    font-size: 15px;
    line-height: 1.75;
    word-break: keep-all;
    margin: 0 0 10px;
  }
  .dr-note {
    font-size: 13px;
    color: #828282;
    line-height: 1.7;
    word-break: keep-all;
    margin: 10px 0 0;
  }
  .dr-sub {
    font-size: 13px;
    font-weight: 700;
    color: #828282;
    margin: 24px 0 10px;
  }
  .dr-list {
    margin: 0;
    padding-left: 20px;
    font-size: 14.5px;
    line-height: 1.8;
    word-break: keep-all;
  }
  .dr-list li {
    margin-bottom: 6px;
  }
  .dr-table-wrap {
    overflow-x: auto;
    margin-bottom: 8px;
  }
  table.dr-table {
    width: 100%;
    border-collapse: collapse;
    font-size: 13px;
  }
  table.dr-table th,
  table.dr-table td {
    border: 1px solid #eee;
    padding: 10px 12px;
    text-align: left;
    vertical-align: top;
    word-break: keep-all;
  }
  table.dr-table th {
    background: #f7f7f7;
    font-size: 12px;
    color: #828282;
    white-space: nowrap;
  }
</style>
