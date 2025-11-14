---
layout: page
title: 태그
---

<div class="tag-cloud">
{% assign tags = site.tags | sort %}
{% for tag in tags %}
  <a href="#{{ tag[0] | slugify }}" class="tag-link" data-count="{{ tag[1] | size }}">
    {{ tag[0] }} <span class="tag-count">({{ tag[1] | size }})</span>
  </a>
{% endfor %}
</div>

<div class="tag-list">
{% for tag in tags %}
  <div class="tag-item">
    <h3 id="{{ tag[0] | slugify }}">{{ tag[0] }}</h3>
    <p class="tag-count-text">{{ tag[1] | size }}개의 포스트</p>
    <ul class="post-list">
      {% assign posts = tag[1] | sort: 'date' | reverse %}
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
.tag-cloud {
  margin: 2rem 0;
  padding: 1.5rem;
  background-color: #f8f9fa;
  border-radius: 5px;
  line-height: 2;
}

.tag-link {
  display: inline-block;
  margin: 0.2rem 0.5rem;
  padding: 0.3rem 0.8rem;
  background-color: #e9ecef;
  color: #495057;
  text-decoration: none;
  border-radius: 15px;
  font-size: 0.9rem;
  transition: all 0.2s ease;
}

.tag-link:hover {
  background-color: #268bd2;
  color: white;
  text-decoration: none;
}

.tag-count {
  font-size: 0.8rem;
  color: #6c757d;
}

.tag-link:hover .tag-count {
  color: rgba(255, 255, 255, 0.8);
}

.tag-list {
  margin-top: 3rem;
}

.tag-item {
  margin-bottom: 3rem;
  padding-bottom: 2rem;
  border-bottom: 1px solid #eee;
}

.tag-item h3 {
  color: #333;
  margin-bottom: 0.5rem;
}

.tag-count-text {
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