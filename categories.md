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