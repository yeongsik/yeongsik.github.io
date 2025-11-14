---
layout: page
title: 카테고리
---

<div class="category-list">
{% assign categories = site.categories | sort %}
{% for category in categories %}
  <div class="category-item">
    <h3 id="{{ category[0] | slugify }}">{{ category[0] }}</h3>
    <p class="category-count">{{ category[1] | size }}개의 포스트</p>
    <ul class="post-list">
      {% assign posts = category[1] | sort: 'date' | reverse %}
      {% for post in posts %}
        <li>
          <span class="post-date">{{ post.date | date: "%Y-%m-%d" }}</span>
          <a href="{{ post.url }}">{{ post.title }}</a>
        </li>
      {% endfor %}
    </ul>
  </div>
{% endfor %}
</div>

<style>
.category-list {
  margin-top: 2rem;
}

.category-item {
  margin-bottom: 3rem;
  padding-bottom: 2rem;
  border-bottom: 1px solid #eee;
}

.category-item h3 {
  color: #333;
  margin-bottom: 0.5rem;
}

.category-count {
  color: #666;
  font-size: 0.9rem;
  margin-bottom: 1rem;
}

.post-list {
  list-style: none;
  padding: 0;
}

.post-list li {
  margin-bottom: 0.5rem;
  padding: 0.5rem 0;
  border-bottom: 1px solid #f5f5f5;
}

.post-date {
  color: #666;
  font-size: 0.85rem;
  margin-right: 1rem;
}

.post-list a {
  color: #333;
  text-decoration: none;
}

.post-list a:hover {
  color: #268bd2;
  text-decoration: underline;
}
</style>