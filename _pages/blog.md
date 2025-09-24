---
layout: blog
title: Blog
permalink: /blog/
include_in_header: true
---

{% assign localized_posts = site.posts | where: 'lang', site.lang %}
{% if localized_posts.size > 0 %}
{% for post in localized_posts %}
<div class="post-list">
  <div class="post-card">
    <a href="{{ post.url | relative_url }}" class="index-anchor">
      <div class="panel-body">
        <h3 class="post-title">{{ post.title }}</h3>
      </div>
      <div class="post-meta">
        {% if post.categories %}
        <span class="post-category">{{ post.categories | join: ', ' }}</span>
        {% endif %}
        <span class="post-date">{{ post.date | date: "%b %-d, %Y" }}</span>
      </div>
      <div class="post-excerpt">
        {{ post.excerpt | strip_html | truncatewords: 30 }}
      </div>
      {% if post.tags %}
      <div class="panel-body post-tags pull-right">
        {% for tag in post.tags %}
        <span>#{{ tag }}</span>
        {% endfor %}
      </div>
      {% endif %}
    </a>
  </div>
</div>
{% endfor %}
{% else %}
<p>{{ 'posts.no_posts' | t }}</p>
{% endif %}
