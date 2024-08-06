---
layout: default
title: Blogs
---

# Blogs

This page is still under construction. We are sorry for the inconvenience. 
<ul>
  {% for blog in site.blogs %}
    <div class="blog-item">
      <li>
        <a href="{{ blog.url }}" target="_blank">{{ blog.title }}</a> - <small>{{ blog.date | date: "%B %d, %Y" }}</small>
      </li>
    </div>
  {% endfor %}
</ul>