---
layout: page
title: 
permalink: /ideas/
---

Some thoughts, as and when.



<ul>
  {% for post in site.posts %}
    {% assign postyear = post.date | date: "%Y" | plus: 0 %}
    {% if postyear == 8888 %}
      <li>  
        <a href="{{ post.url }}">{{ post.title }}</a>
      </li>
      
    {% endif %}   
  {% endfor %}
</ul>
