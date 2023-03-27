---
layout: page
title: Some Thoughts
permalink: /Blog/
---

Some thoughts, as and when I have them.

<ul>
  {% for post in site.posts %}
    {% assign postyear = post.date | date: "%Y" | plus: 0 %}
    {% if postyear > 2018 and postyear < 3000 %}
      <li>  
      {{ post.date | date: "%d/%m/%Y" }} 
      </li>
      <a href="{{ post.url }}">{{ post.title }}</a>
        
    {% endif %}   
  {% endfor %}
</ul>
