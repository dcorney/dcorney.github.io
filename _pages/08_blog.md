---
layout: page
title: Thoughts
permalink: /Blog/
---


<ul>
  {% for post in site.posts %}
    Title {{post.title}}
    {% assign postyear = post.date | date: "%Y" %}
    year {{postyear}}
    {% if {{postyear}} > 2018 %}
        <li>    
        <a href="{{ post.url }}">{{ post.title }}</a>
        </li>
    {% endif %}
    
  {% endfor %}
</ul>