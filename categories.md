---
layout: page
title: 카테고리
---

{% assign categories = site.categories | sort %}
{% for category in categories %}
<section class="category-item">
  <h2 id="{{ category[0] | slugify }}">{{ category[0] }}</h2>
  <p class="category-count">{{ category[1] | size }}개 글</p>
  <ul class="post-list">
    {% assign posts = category[1] | sort: 'date' | reverse %}
    {% for post in posts %}
    <li>
      <time class="post-date" datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%Y.%m.%d" }}</time>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
    {% endfor %}
  </ul>
</section>
{% endfor %}