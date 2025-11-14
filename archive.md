---
layout: page
title: 아카이브
---

<div class="archive-intro">
  <p>시간순으로 정리된 모든 포스트들입니다. 개발 여정을 되돌아보며 성장 과정을 확인할 수 있습니다.</p>
</div>

<div class="archive-stats">
  <div class="stat-item">
    <span class="stat-number">{{ site.posts | size }}</span>
    <span class="stat-label">총 포스트</span>
  </div>
  <div class="stat-item">
    <span class="stat-number">{{ site.categories | size }}</span>
    <span class="stat-label">카테고리</span>
  </div>
  <div class="stat-item">
    <span class="stat-number">{{ site.tags | size }}</span>
    <span class="stat-label">태그</span>
  </div>
</div>

<div class="archive-timeline">
  {% assign posts_by_year = site.posts | group_by_exp: "post", "post.date | date: '%Y'" %}
  {% for year_group in posts_by_year %}
    <div class="year-section">
      <h2 class="year-header">{{ year_group.name }}</h2>
      <div class="year-stats">{{ year_group.items | size }}개의 포스트</div>
      
      {% assign posts_by_month = year_group.items | group_by_exp: "post", "post.date | date: '%m'" %}
      {% for month_group in posts_by_month %}
        <div class="month-section">
          <h3 class="month-header">
            {{ month_group.items.first.date | date: '%B' }}
            <span class="month-count">({{ month_group.items | size }})</span>
          </h3>
          
          <div class="post-list">
            {% for post in month_group.items %}
              <div class="post-item">
                <div class="post-meta">
                  <span class="post-date">{{ post.date | date: "%m-%d" }}</span>
                  {% if post.category %}
                    <span class="post-category">{{ post.category }}</span>
                  {% endif %}
                  {% if post.tags.size > 0 %}
                    <div class="post-tags">
                      {% for tag in post.tags limit: 3 %}
                        <span class="tag">{{ tag }}</span>
                      {% endfor %}
                      {% if post.tags.size > 3 %}
                        <span class="tag-more">+{{ post.tags.size | minus: 3 }}</span>
                      {% endif %}
                    </div>
                  {% endif %}
                </div>
                <div class="post-content">
                  <a href="{{ post.url }}" class="post-title">{{ post.title }}</a>
                  {% if post.excerpt %}
                    <p class="post-excerpt">{{ post.excerpt | strip_html | truncatewords: 15 }}</p>
                  {% endif %}
                </div>
              </div>
            {% endfor %}
          </div>
        </div>
      {% endfor %}
    </div>
  {% endfor %}
</div>

{% if site.posts.size == 0 %}
<div class="empty-archive">
  <h3>아직 포스트가 없습니다</h3>
  <p>첫 번째 포스트를 작성해서 개발 여정을 시작해보세요!</p>
</div>
{% endif %}