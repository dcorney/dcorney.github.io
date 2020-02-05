---
layout: page
title: Thoughts
permalink: /Blog/
---

Some thoughts, as and when.

<ul>
  {% for post in site.posts %}
    {% assign postyear = post.date | date: "%Y" | plus: 0 %}
    {% if {{postyear}} > 2018 %}
      <li>  
      {{ post.date | date: "%d/%m/%Y" }} 
      </li>
      <a href="{{ post.url }}">{{ post.title }}</a>
        
    {% endif %}   
  {% endfor %}
</ul>
