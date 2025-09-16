---
layout: blog
title: Blog
permalink: /blog/
include_in_header: true
---

<nav>
  <a href="/blog/">🇧🇷 Blog</a>
  <a href="/blog-en/">🇺🇸 Blog</a>
</nav>

{% for post in site.posts %}
    {% if post.lang == "pt" %}
        <div class="post-list">
            <div class="post-card">
                <a href="{{ post.url | prepend: site.baseurl }}" class="index-anchor">
                    <div class="panel-body">
                        <h3 class="post-title">{{ post.title }}</h3>
                    </div>
                    <div class="post-meta">
                        <span class="post-category">{{ post.category }}</span>
                        <span class="post-date">{{ post.date | date: "%b %-d, %Y" }}</span>
                    </div>
                    <div class="post-excerpt">
                        {{ post.content | remove: '<h1>' | remove: '</h1>' | remove: '<h2>' | remove: '</h2>' | remove: '<h3>' | remove: '</h3>' | remove: '<h4>' | remove: '</h4>' | split: '</p>' | first | strip_html }}
                    </div>
                    <div class="panel-body post-tags pull-right">
                        {% for tag in post.tags %}
                        <span>#{{ tag }}</span>
                        {% endfor %}
                    </div>
                </a>
            </div>
        </div>
    {% endif %}
{% endfor %}
