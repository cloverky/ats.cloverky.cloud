---
layout: page
title: 프로젝트 소개
permalink: /project-intro/
---

{%- assign p = site.data.project -%}

<p class="pi-tagline">{{ p.tagline }}</p>
<p class="pi-meta">{{ p.period }} · 개발팀 {{ p.team_size }}</p>

<h2 id="problem" class="pi-h2">해결하려는 문제</h2>
<p class="pi-body">{{ p.problem }}</p>

<h2 id="features" class="pi-h2">주요 기능</h2>
<div class="pi-grid">
  {%- for f in p.features -%}
  <div class="pi-card">
    <p class="pi-card-title">{{ f.title }}</p>
    <p class="pi-card-desc">{{ f.description }}</p>
  </div>
  {%- endfor -%}
</div>

<h2 id="tech" class="pi-h2">기술 스택</h2>
<div class="pi-tech">
  {%- for t in p.tech -%}
  <div class="pi-tech-row">
    <span class="pi-tech-label">
      {%- case t.category -%}
        {%- when "backend" -%}백엔드
        {%- when "frontend" -%}프론트엔드
        {%- when "infra" -%}인프라
        {%- when "ai" -%}AI
        {%- else -%}{{ t.category }}
      {%- endcase -%}
    </span>
    <span class="pi-tech-items">
      {%- for item in t.items -%}<span class="pi-chip">{{ item }}</span>{%- endfor -%}
    </span>
  </div>
  {%- endfor -%}
</div>

{%- if p.architecture -%}
<h2 id="architecture" class="pi-h2">아키텍처</h2>
<img class="pi-figure" src="{{ p.architecture.image | relative_url }}" alt="아키텍처 다이어그램">
<p class="pi-caption">{{ p.architecture.description }}</p>
{%- endif -%}

{%- if p.erd -%}
<h2 id="erd" class="pi-h2">ERD</h2>
<img class="pi-figure" src="{{ p.erd.image | relative_url }}" alt="ERD">
<p class="pi-caption">{{ p.erd.description }}</p>
{%- endif -%}

{%- if p.screenshots -%}
<h2 id="screenshots" class="pi-h2">스크린샷</h2>
<div class="pi-shots">
  {%- for s in p.screenshots -%}
  <figure class="pi-shot">
    <img src="{{ s.path | relative_url }}" alt="{{ s.caption }}">
    <figcaption>{{ s.caption }}</figcaption>
  </figure>
  {%- endfor -%}
</div>
{%- endif -%}

<h2 id="links" class="pi-h2">링크</h2>
<ul class="pi-links">
  {%- if p.links.repo -%}<li><span class="pi-link-label">Repo</span><a href="{{ p.links.repo }}">{{ p.links.repo }}</a></li>{%- endif -%}
  {%- if p.links.demo != "" -%}<li><span class="pi-link-label">Demo</span><a href="{{ p.links.demo }}">{{ p.links.demo }}</a></li>{%- endif -%}
  {%- if p.links.docs != "" -%}<li><span class="pi-link-label">Docs</span><a href="{{ p.links.docs }}">{{ p.links.docs }}</a></li>{%- endif -%}
</ul>

<style>
  .pi-tagline {
    font-size: 17px;
    font-weight: 700;
    margin: 0 0 6px;
    word-break: keep-all;
  }
  .pi-meta {
    font-size: 13px;
    color: #828282;
    margin: 0 0 32px;
  }
  h2.pi-h2 {
    font-size: 17px;
    font-weight: 700;
    color: #2451FF;
    margin: 44px 0 16px;
    padding-bottom: 10px;
    border-bottom: 1px solid #eee;
  }
  .pi-body {
    font-size: 15px;
    line-height: 1.75;
    word-break: keep-all;
    margin: 0;
  }

  .pi-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
    gap: 14px;
  }
  .pi-card {
    border: 1px solid #eee;
    border-radius: 8px;
    padding: 16px 18px;
  }
  .pi-card-title {
    font-size: 14px;
    font-weight: 700;
    margin: 0 0 6px;
  }
  .pi-card-desc {
    font-size: 13.5px;
    color: #55575c;
    line-height: 1.6;
    margin: 0;
    word-break: keep-all;
  }

  .pi-tech-row {
    display: flex;
    align-items: baseline;
    gap: 16px;
    padding: 12px 0;
    border-top: 1px solid #eee;
  }
  .pi-tech-row:first-child {
    border-top: 0;
  }
  .pi-tech-label {
    flex: 0 0 84px;
    font-size: 13px;
    font-weight: 700;
    color: #828282;
  }
  .pi-tech-items {
    flex: 1;
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }
  .pi-chip {
    display: inline-block;
    font-size: 12.5px;
    font-weight: 600;
    background: #eef2ff;
    color: #2451FF;
    padding: 4px 10px;
    border-radius: 999px;
  }

  .pi-figure {
    display: block;
    max-width: 100%;
    height: auto;
    border: 1px solid #eee;
    border-radius: 8px;
    margin: 0 0 10px;
  }
  .pi-caption {
    font-size: 13px;
    color: #828282;
    line-height: 1.6;
    margin: 0;
    word-break: keep-all;
  }

  .pi-shots {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
    gap: 20px;
  }
  .pi-shot {
    margin: 0;
  }
  .pi-shot img {
    display: block;
    max-width: 100%;
    height: auto;
    border: 1px solid #eee;
    border-radius: 8px;
    margin: 0 0 8px;
  }
  .pi-shot figcaption {
    font-size: 13px;
    color: #828282;
    line-height: 1.6;
    word-break: keep-all;
  }

  .pi-links {
    list-style: none;
    margin: 0 0 40px;
    padding: 0;
  }
  .pi-links li {
    display: flex;
    gap: 16px;
    padding: 10px 0;
    border-top: 1px solid #eee;
    font-size: 14px;
  }
  .pi-links li:first-child {
    border-top: 0;
  }
  .pi-link-label {
    flex: 0 0 60px;
    font-weight: 700;
    color: #828282;
  }
  .pi-links a {
    word-break: break-all;
  }
</style>
