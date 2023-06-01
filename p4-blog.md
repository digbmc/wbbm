---
title: Blog
layout: page
phase: P4
permalink: /2023-2026/blog/
---

{% include post-list.html %}

<!-- <ul class="list-group-flush">
    {% for post in site.posts %}
        <li class="list-group-item bg-dark row">
            {% if post.key_image %}
                <div class="col-3">
                <img src="{{ post.key_image.url }}" class="img-thumbnail" width="200px">
                </div>
            {% endif %}
            <div class="col-9">
            <h3><a href="{{ post.url }}">{{ post.title }}</a></h3>
            <p>{{ post.author }}</p>
            <p>{{ post.date | date: "%b %d, %Y" }}</p>
            <p>{{ post.description }}</p>
            </div>
        </li>
    {% endfor %}
</ul> -->