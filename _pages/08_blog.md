---
layout: page
title: Thoughts
permalink: /Blog/
---


<ul>
  {% for post in site.posts %}
    {% assign postyear = post.date | date: "%Y" %}
    {{postyear}}
    {% if {{postyear}} > 2018 %}
        <li>    
        <a href="{{ post.url }}">{{ post.title }}</a>
        </li>
      {% endif %}
    
  {% endfor %}
</ul>