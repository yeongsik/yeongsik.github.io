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

<style>
.archive-intro {
  margin-bottom: 2rem;
  padding: 1.5rem;
  background-color: #f8f9fa;
  border-radius: 5px;
  border-left: 4px solid #268bd2;
}

.archive-stats {
  display: flex;
  gap: 2rem;
  margin-bottom: 3rem;
  padding: 1.5rem;
  background-color: #fff;
  border: 1px solid #e9ecef;
  border-radius: 5px;
}

.stat-item {
  text-align: center;
  flex: 1;
}

.stat-number {
  display: block;
  font-size: 2rem;
  font-weight: bold;
  color: #268bd2;
  line-height: 1;
}

.stat-label {
  display: block;
  margin-top: 0.5rem;
  color: #666;
  font-size: 0.9rem;
}

.archive-timeline {
  position: relative;
}

.year-section {
  margin-bottom: 3rem;
  position: relative;
}

.year-header {
  font-size: 2rem;
  color: #333;
  margin-bottom: 0.5rem;
  padding-bottom: 0.5rem;
  border-bottom: 2px solid #268bd2;
}

.year-stats {
  color: #666;
  font-size: 0.9rem;
  margin-bottom: 2rem;
}

.month-section {
  margin-bottom: 2rem;
  margin-left: 1rem;
  position: relative;
}

.month-section::before {
  content: '';
  position: absolute;
  left: -1rem;
  top: 0;
  bottom: 0;
  width: 2px;
  background-color: #e9ecef;
}

.month-header {
  font-size: 1.2rem;
  color: #495057;
  margin-bottom: 1rem;
  position: relative;
}

.month-header::before {
  content: '';
  position: absolute;
  left: -1.4rem;
  top: 0.6rem;
  width: 8px;
  height: 8px;
  background-color: #268bd2;
  border-radius: 50%;
}

.month-count {
  font-size: 0.8rem;
  color: #666;
  font-weight: normal;
}

.post-list {
  margin-left: 1rem;
}

.post-item {
  display: flex;
  gap: 1rem;
  margin-bottom: 1.5rem;
  padding: 1rem;
  background-color: #fafafa;
  border-radius: 5px;
  border-left: 3px solid transparent;
  transition: all 0.2s ease;
}

.post-item:hover {
  background-color: #f0f8ff;
  border-left-color: #268bd2;
}

.post-meta {
  flex-shrink: 0;
  width: 120px;
}

.post-date {
  display: block;
  color: #666;
  font-family: monospace;
  font-size: 0.9rem;
  margin-bottom: 0.5rem;
}

.post-category {
  display: inline-block;
  background-color: #e9ecef;
  color: #495057;
  padding: 0.2rem 0.5rem;
  border-radius: 3px;
  font-size: 0.8rem;
  margin-bottom: 0.5rem;
}

.post-tags {
  margin-top: 0.5rem;
}

.tag {
  display: inline-block;
  background-color: #268bd2;
  color: white;
  padding: 0.1rem 0.4rem;
  border-radius: 2px;
  font-size: 0.7rem;
  margin-right: 0.2rem;
  margin-bottom: 0.2rem;
}

.tag-more {
  display: inline-block;
  color: #666;
  font-size: 0.7rem;
  margin-left: 0.2rem;
}

.post-content {
  flex: 1;
}

.post-title {
  color: #333;
  text-decoration: none;
  font-weight: 500;
  display: block;
  margin-bottom: 0.5rem;
}

.post-title:hover {
  color: #268bd2;
  text-decoration: underline;
}

.post-excerpt {
  color: #666;
  font-size: 0.9rem;
  line-height: 1.4;
  margin: 0;
}

.empty-archive {
  text-align: center;
  padding: 3rem;
  color: #666;
}

.empty-archive h3 {
  color: #333;
  margin-bottom: 1rem;
}

@media (max-width: 768px) {
  .archive-stats {
    flex-direction: column;
    gap: 1rem;
  }
  
  .post-item {
    flex-direction: column;
    gap: 0.5rem;
  }
  
  .post-meta {
    width: auto;
  }
  
  .month-section {
    margin-left: 0;
  }
  
  .month-section::before,
  .month-header::before {
    display: none;
  }
}
</style>