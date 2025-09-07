---
layout: default
title: Categorias
permalink: /categorias/
---

<div class="categories-container">
  {% for category in site.categories %}
    <div class="category-block">
      <h2>{{ category[0] }}</h2>
      <div class="posts-list">
        {% for post in category[1] %}
          <div class="post-item">
            <h3><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></h3>
            <p>{{ post.date | date: "%d %b %Y" }}</p>
            <p>{{ post.excerpt }}</p>
          </div>
        {% endfor %}
      </div>
      ---
    </div>
  {% endfor %}
</div>