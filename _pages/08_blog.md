---
layout: page
title: Thoughts
permalink: /Blog/
---


<ul>
  {% for post in site.posts %}
    <li>
      {% if post.year > 2018>%}
        <a href="{{ post.url }}">{{ post.title }}</a>
      {% endif %}
    </li>
  {% endfor %}
</ul>