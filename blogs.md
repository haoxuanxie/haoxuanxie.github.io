---
layout: default
title: Blogs
---

# Blogs

<ul>
  {% for blog in site.blogs %}
    <li>
      <a href="{{ blog.url }}">{{ blog.title }}</a> - <small>{{ blog.date | date: "%B %d, %Y" }}</small>
    </li>
  {% endfor %}
</ul>
