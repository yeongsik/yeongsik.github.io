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