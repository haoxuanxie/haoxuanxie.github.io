---
layout: default_zh-CN
title: 博客
---

# 博客

<ul>
  {% for blog in site.blogs %}
    <li>
      <a href="{{ blog.url }}">{{ blog.title }}</a> - <small>{{ blog.date | date: "%B %d, %Y" }}</small>
    </li>
  {% endfor %}
</ul>