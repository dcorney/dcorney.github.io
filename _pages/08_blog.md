---
layout: page
title: Thoughts
permalink: /Blog/
---

Testing even more 9...

<ul>
  {% for post in site.posts %}
    {% assign postyear = post.date | date: "%Y" | plus: 0 %}
    {% if {{postyear}} > 2018 %}
    <li>
        <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
        
    {% endif %}   
  {% endfor %}
</ul>
