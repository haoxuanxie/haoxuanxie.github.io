---
layout: default
title: Blogs
---

# Blogs

<h1>Blogs</h1>
<ul>
  {% for blog in site.blogs %}
    <li>
      <a href="{{ blog.url }}">{{ blog.title }}</a> - <small>{{ blog.date | date: "%B %d, %Y" }}</small>
    </li>
  {% endfor %}
</ul>
