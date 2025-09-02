---
layout: default
title: CODIGUIN
---

<div class="container_latest">
    {% for post in site.posts limit: 2 %}
        <div class="posts_latest">
            <img src="{{ site.baseurl}}/{{ post.image }}">
            <div> 
                <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
                <h3> {{ post.subtitle }} </h3>
                <p> {{post.author}} | {{ post.date | date: "%d %b %Y" }} </p>
            </div>
        </div>
    {% endfor %}
</div>

<h2>Recentes</h2>
<div class="container_posts">
    {% for post in site.posts %}
        <div class="posts_order">
            {% if post != 1%}
                <img src="{{ post.image | relative_url }}">
                <div> 
                    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
                    <h3> {{ post.subtitle }} </h3>
                    <p> {{post.author}} | {{ post.date | date: "%d %b %Y" }} </p>
                </div>
            {% endif %}
        </div>
    {% endfor %}
</div>
