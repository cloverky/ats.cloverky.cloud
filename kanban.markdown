---
layout: page
title: 팀 칸반
permalink: /kanban/
---

<style>
.kb-board { display: grid; grid-template-columns: repeat(3, 1fr); gap: 12px; margin: 1rem 0 2rem; }
@media (max-width: 700px) { .kb-board { grid-template-columns: 1fr; } }
.kb-col { background: #f7f7f7; border: 1px solid #eee; border-radius: 8px; padding: 10px; }
.kb-col-title { font-weight: 700; font-size: 0.8rem; letter-spacing: 0.05em; text-transform: uppercase; color: #828282; margin: 2px 0 10px 4px; }
.kb-card { border: 1px solid #eee; border-left-width: 4px; border-radius: 6px; padding: 8px 10px; margin-bottom: 8px; background: #fff; }
.kb-card-title { font-size: 0.82rem; line-height: 1.45; margin-bottom: 5px; color: #12141c; }
.kb-meta { display: flex; flex-wrap: wrap; gap: 5px; align-items: center; }
.kb-owner { font-size: 0.66rem; font-weight: 700; padding: 1px 8px; border-radius: 999px; color: #fff; }
.kb-tag { font-size: 0.66rem; padding: 1px 7px; border-radius: 4px; border: 1px solid #ddd; color: #555; }
.kb-due { font-size: 0.66rem; color: #aaa; }
.kb-note { font-size: 0.7rem; color: #888; margin-top: 4px; }
.kb-legend { display: flex; flex-wrap: wrap; gap: 8px; margin-bottom: 1rem; }
.kb-count { color: #aaa; font-weight: 400; }
details { margin-top: 1.5rem; }
details summary { cursor: pointer; font-size: 0.78rem; color: #828282; }
details summary:hover { color: #2451FF; text-decoration: underline; }
</style>

<div class="kb-legend">
{% for member in site.data.kanban %}{% assign m = member[1] %}
  <span class="kb-owner" style="background: {{ m.color }};">{{ m.name | default: m.owner }} · {{ m.domain }}</span>
{% endfor %}
</div>

<div class="kb-board">
{% assign columns = "todo:할 일,doing:진행 중,done:완료" | split: "," %}
{% for col in columns %}
  {% assign parts = col | split: ":" %}
  {% assign status = parts[0] %}
  <div class="kb-col">
    {% assign total = 0 %}
    {% for member in site.data.kanban %}{% assign m = member[1] %}{% for card in m.cards %}{% if card.status == status %}{% assign total = total | plus: 1 %}{% endif %}{% endfor %}{% endfor %}
    <div class="kb-col-title">{{ parts[1] }} <span class="kb-count">({{ total }})</span></div>
    {% for member in site.data.kanban %}
      {% assign m = member[1] %}
      {% for card in m.cards %}
        {% if card.status == status %}
        <div class="kb-card" style="border-left-color: {{ m.color }};">
          <div class="kb-card-title">{{ card.title }}</div>
          <div class="kb-meta">
            <span class="kb-owner" style="background: {{ m.color }};">{{ m.name | default: m.owner }}</span>
            {% if card.feature %}<span class="kb-tag">{{ card.feature }}</span>{% endif %}
            {% if card.due %}<span class="kb-due">~{{ card.due }}</span>{% endif %}
          </div>
          {% if card.note %}<div class="kb-note">{{ card.note }}</div>{% endif %}
        </div>
        {% endif %}
      {% endfor %}
    {% endfor %}
  </div>
{% endfor %}
</div>

<details markdown="1">
<summary>사용 규칙 보기 (카드 편집 방법 · 충돌 방지)</summary>

카드는 `_data/kanban/<자기 GitHub 아이디>.yml`에서만 편집한다 — 한 사람이 파일 하나를 소유하므로 5명이 동시에 작업해도 git 충돌이 나지 않는다.

1. **자기 파일만 수정한다.** 남의 카드에 할 말이 있으면 팀 채널로.
2. **카드 형식**은 파일 안 기존 항목을 복사해서 쓴다. `status`는 `todo | doing | done` 세 값만.
   ```yaml
   - title: "카드 제목"
     feature: "D3"
     status: todo
     done: 2026-09-02
     due: 2026-09-04
     note: ""
   ```
3. **push 전 `git pull --rebase`.**
4. **`done`으로 바꿀 때 `done: 날짜`를 함께 기입한다** — [개발 로그](/devlog/) 완료 타임라인이 이 날짜로 집계된다.

</details>
