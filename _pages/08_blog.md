---
layout: page
title: Thoughts
permalink: /Blog/
---


<ul>
  {% for post in site.posts %}
      {% if post.year > 2018%}
        <li>    
        <a href="{{ post.url }}">{{ post.title }}</a>
        </li>
      {% endif %}
    
  {% endfor %}
</ul>