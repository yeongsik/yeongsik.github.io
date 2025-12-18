---
layout: page
title: 태그
---

<nav class="tag-cloud">
{% assign tags = site.tags | sort %}
{% for tag in tags %}
  <a href="#{{ tag[0] | slugify }}" class="tag-link">
    {{ tag[0] }} <span class="tag-count">({{ tag[1] | size }})</span>
  </a>
{% endfor %}
</nav>

{% for tag in tags %}
<section class="tag-item">
  <h2 id="{{ tag[0] | slugify }}">{{ tag[0] }}</h2>
  <p class="tag-count-text">{{ tag[1] | size }}개 글</p>
  <ul class="post-list">
    {% assign posts = tag[1] | sort: 'date' | reverse %}
    {% for post in posts %}
    <li>
      <time class="post-date" datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%Y.%m.%d" }}</time>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
    {% endfor %}
  </ul>
</section>
{% endfor %}