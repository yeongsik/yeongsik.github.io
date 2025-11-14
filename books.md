---
layout: page
title: 독서
---

<div class="books-intro">
  <p>개발자로 성장하는 데 도움이 된 책들과 읽으면서 정리한 내용들을 모아두었습니다.</p>
</div>

<div class="reading-status">
  <h2>현재 읽고 있는 책</h2>
  <div class="current-books">
    <div class="current-book">
      <div class="book-info">
        <h4><a href="https://product.kyobobook.co.kr/detail/S000212650856">컴퓨터 밑바닥의 비밀</a></h4>
      </div>
    </div>
  </div>
</div>

<div class="all-book-posts">
  <h2>모든 독서 포스트</h2>
  <div class="book-list">
    {% assign book_posts = "" | split: "" %}
    {% for post in site.posts %}
      {% if post.tags contains 'book' or post.tags contains 'reading' %}
        {% assign book_posts = book_posts | push: post %}
      {% endif %}
    {% endfor %}
    {% if book_posts.size > 0 %}
      {% for post in book_posts %}
        <div class="book-item">
          <span class="book-date">{{ post.date | date: "%Y-%m-%d" }}</span>
          <a href="{{ post.url }}">{{ post.title }}</a>
          {% if post.book_author %}<span class="book-author"> - {{ post.book_author }}</span>{% endif %}
          {% if post.category %}<span class="book-category">[{{ post.category }}]</span>{% endif %}
        </div>
      {% endfor %}
    {% else %}
      <p class="no-books">아직 독서 관련 포스트가 없습니다. 첫 번째 책 리뷰를 작성해보세요!</p>
    {% endif %}
  </div>
</div>

<style>
.books-intro {
  margin-bottom: 2rem;
  padding: 1.5rem;
  background-color: #f8f9fa;
  border-radius: 5px;
  border-left: 4px solid #268bd2;
}

.reading-status {
  margin-bottom: 3rem;
}

.current-books {
  margin-left: 1rem;
}

.category-section {
  margin-bottom: 2.5rem;
  padding-bottom: 1.5rem;
  border-bottom: 1px solid #eee;
}

.category-section h3 {
  color: #333;
  margin-bottom: 1rem;
  font-size: 1.2rem;
}

.book-list {
  margin-left: 1rem;
}

.book-item {
  margin-bottom: 0.8rem;
  padding: 0.8rem 0;
  border-bottom: 1px solid #f5f5f5;
  line-height: 1.6;
}

.book-date {
  color: #666;
  font-size: 0.85rem;
  margin-right: 1rem;
  font-family: monospace;
}

.book-item a {
  color: #333;
  text-decoration: none;
  font-weight: 500;
}

.book-item a:hover {
  color: #268bd2;
  text-decoration: underline;
}

.book-author {
  color: #666;
  font-size: 0.9rem;
  font-style: italic;
}

.book-category {
  color: #888;
  font-size: 0.8rem;
  margin-left: 0.5rem;
}

.no-books {
  color: #666;
  font-style: italic;
  margin: 1rem 0;
}

.all-book-posts {
  margin-top: 3rem;
  padding-top: 2rem;
  border-top: 2px solid #eee;
}
</style>