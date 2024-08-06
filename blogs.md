---
layout: default
title: Blogs
---

# Blogs

<ul>
  {% for blog in site.blogs %}
    <div class="blog-item">
      <li>
        <a href="{{ blog.url }}">{{ blog.title }}</a> - <small>{{ blog.date | date: "%B %d, %Y" }}</small>
      </li>
    </div>
  {% endfor %}
</ul>