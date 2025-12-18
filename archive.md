---
layout: page
title: 아카이브
---

<p class="archive-intro">시간순으로 정리된 모든 포스트입니다.</p>

<section class="archive-stats">
  <div class="stat-item">
    <strong class="stat-number">{{ site.posts | size }}</strong>
    <span class="stat-label">글</span>
  </div>
  <div class="stat-item">
    <strong class="stat-number">{{ site.categories | size }}</strong>
    <span class="stat-label">카테고리</span>
  </div>
  <div class="stat-item">
    <strong class="stat-number">{{ site.tags | size }}</strong>
    <span class="stat-label">태그</span>
  </div>
</section>

{% assign posts_by_year = site.posts | group_by_exp: "post", "post.date | date: '%Y'" %}
{% for year_group in posts_by_year %}
<section class="year-section">
  <h2 class="year-header">{{ year_group.name }}</h2>
  <p class="year-stats">{{ year_group.items | size }}개 글</p>

  {% assign posts_by_month = year_group.items | group_by_exp: "post", "post.date | date: '%m'" %}
  {% for month_group in posts_by_month %}
  <section class="month-section">
    <h3 class="month-header">
      {{ month_group.items.first.date | date: '%B' }}
      <span class="month-count">({{ month_group.items | size }})</span>
    </h3>

    <ul class="post-list">
      {% for post in month_group.items %}
      <li class="post-item">
        <time class="post-date" datetime="{{ post.date | date_to_xmlschema }}">
          {{ post.date | date: "%m.%d" }}
        </time>
        <div class="post-content">
          <a href="{{ post.url }}" class="post-title">{{ post.title }}</a>
          {% if post.excerpt %}
          <p class="post-excerpt">{{ post.excerpt | strip_html | truncatewords: 20 }}</p>
          {% endif %}
        </div>
      </li>
      {% endfor %}
    </ul>
  </section>
  {% endfor %}
</section>
{% endfor %}

{% if site.posts.size == 0 %}
<section class="empty-archive">
  <p>아직 작성된 글이 없습니다.</p>
</section>
{% endif %}