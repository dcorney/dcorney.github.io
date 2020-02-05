---
layout: page
title: Thoughts
permalink: /Blog/
---




  {% for post in site.posts %}
    {% assign postyear = post.date | date: "%Y" | plus: 0 %}
    {% if {{postyear}} > 2018 %}
        <p>{{ post.date | date: "%d/%m/%Y" }}</p>
        <p><a href="{{ post.url }}">{{ post.title }}</a></p>
        
    {% endif %}   
  {% endfor %}

