---
layout: default
title: CODIGUIN
permalink: /
---

<h2>Recentes</h2>
<div class="container_latest">
    {% for post in site.posts limit: 2 %}
        <div class="posts_latest">
            <div> 
                <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
                <h3> {{ post.subtitle }} </h3>
                <span class="date"> {{post.author}} | {{ post.date | date: "%d %b %Y" }} </span>
                <div class="tags-container">
                    {% for tag in post.tags %}
                        <span class="tag">{{ tag }}</span>
                    {% endfor %}
                </div>
            </div>
        </div>
    {% endfor %}
</div>

<h2>Posts</h2>
<div class="container_posts">
    {% for post in site.posts %}
        {% if forloop.index0 >= 2 %}
            <div class="posts_order">
                <div>
                    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
                    <h3> {{ post.subtitle }} </h3>
                    <span class="date"> {{post.author}} | {{ post.date | date: "%d %b %Y" }} </span>
                    <div class="tags-container">
                        {% for tag in post.tags %}
                            <span class="tag">{{ tag }}</span>
                        {% endfor %}
                    </div>
                </div>
            </div>
        {% endif %}
    {% endfor %}
</div>