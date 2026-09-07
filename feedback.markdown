---
layout: page
title: 피드백 트래커
permalink: /feedback/
---

**멘토·강사님 피드백**의 접수와 반영 이력을 추적한다 — 언제 어떤 피드백을 받았고, 언제 무엇을 수정했는지.

<style>
.fb-item { border: 1px solid #eee; border-radius: 10px; margin: 1rem 0; overflow: hidden; }
.fb-head { display: flex; flex-wrap: wrap; align-items: center; gap: 8px; padding: 10px 14px; background: #f7f7f7; border-bottom: 1px solid #eee; }
.fb-owner { font-size: 0.7rem; font-weight: 700; padding: 2px 10px; border-radius: 999px; color: #fff; white-space: nowrap; }
.fb-status { font-size: 0.7rem; font-weight: 700; padding: 2px 10px; border-radius: 5px; white-space: nowrap; }
.fb-todo { background: #fef2f2; color: #dc2626; }
.fb-doing { background: #fffbeb; color: #d97706; }
.fb-done { background: #f0fdf4; color: #16a34a; }
.fb-dates { font-size: 0.74rem; color: #aaa; margin-left: auto; white-space: nowrap; }
.fb-block { padding: 12px 14px; }
.fb-block + .fb-block { border-top: 1px dashed #eee; }
.fb-label { font-size: 0.68rem; font-weight: 700; letter-spacing: 0.06em; color: #aaa; margin-bottom: 4px; }
.fb-block p { margin: 0; font-size: 0.86rem; line-height: 1.7; color: #374151; }
.fb-fix { border-left: 3px solid #16a34a; background: #f0fdf4; }
.fb-empty { color: #aaa; text-align: center; padding: 2rem 0; font-size: 0.85rem; }
details { margin-top: 1.5rem; }
details summary { cursor: pointer; font-size: 0.78rem; color: #828282; }
details summary:hover { color: #2451FF; text-decoration: underline; }
</style>

{% assign total = 0 %}{% for member in site.data.feedback %}{% assign m = member[1] %}{% assign total = total | plus: m.feedback.size %}{% endfor %}
{% if total == 0 %}
<div class="fb-empty">아직 기록된 피드백이 없습니다.</div>
{% endif %}
{% for member in site.data.feedback %}{% assign m = member[1] %}{% for item in m.feedback %}
<div class="fb-item">
  <div class="fb-head">
    <span class="fb-owner" style="background: {{ m.color }};">{{ m.name | default: m.owner }}</span>
    {% case item.status %}{% when "done" %}<span class="fb-status fb-done">반영 완료</span>{% when "doing" %}<span class="fb-status fb-doing">수정 중</span>{% else %}<span class="fb-status fb-todo">대기</span>{% endcase %}
    <span class="fb-dates">접수 {{ item.received }}{% if item.from %} · {{ item.from }}{% endif %}{% if item.fixed %} → 반영 {{ item.fixed }}{% endif %}</span>
  </div>
  <div class="fb-block">
    <div class="fb-label">피드백</div>
    <p>{{ item.content }}</p>
  </div>
  {% if item.fix and item.fix != "" %}
  <div class="fb-block fb-fix">
    <div class="fb-label">반영 내용</div>
    <p>{{ item.fix }}</p>
  </div>
  {% endif %}
</div>
{% endfor %}{% endfor %}

<details markdown="1">
<summary>사용 규칙 보기 (기록 방법)</summary>

멘토링·강의에서 받은 피드백을, **반영을 담당하는 팀원**이 `_data/feedback/<자기 GitHub 아이디>.yml`에 기록한다 — 칸반과 같은 원칙(한 사람 = 파일 하나)이라 git 충돌이 없다.

```yaml
- received: 2026-09-01
  from: "09/04 중간점검"
  content: "피드백 내용"
  status: todo
  fixed:
  fix: ""
```

반영이 끝나면 같은 항목에 `fixed`·`fix`를 채우고 `status: done`으로 바꾼다.

</details>
