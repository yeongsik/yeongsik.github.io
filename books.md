---
layout: page
title: 독서
---

<p class="books-intro">개발 서적을 읽으며 정리한 내용입니다.</p>

<section class="reading-status">
  <h2>읽는 중</h2>
  <article class="current-book">
    <h3><a href="https://product.kyobobook.co.kr/detail/S000212650856">컴퓨터 밑바닥의 비밀</a></h3>
  </article>
</section>

{% assign book_posts = "" | split: "" %}
{% for post in site.posts %}
  {% if post.tags contains 'book' or post.tags contains 'reading' %}
    {% assign book_posts = book_posts | push: post %}
  {% endif %}
{% endfor %}

<section class="all-book-posts">
  <h2>독서 기록</h2>
  {% if book_posts.size > 0 %}
  <ul class="book-list">
    {% for post in book_posts %}
    <li class="book-item">
      <time class="book-date" datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%Y.%m.%d" }}</time>
      <a href="{{ post.url }}">{{ post.title }}</a>
      {% if post.book_author %}<span class="book-author"> — {{ post.book_author }}</span>{% endif %}
    </li>
    {% endfor %}
  </ul>
  {% else %}
  <p class="no-books">아직 작성된 글이 없습니다.</p>
  {% endif %}
</section>