---
layout: page
title: Thoughts
permalink: /Blog/
---

Testing some more...

<ul>
  {% for post in site.posts %}
    <li>
    Title {{post.title}} 
    </li>
    {% assign postyear = post.date | date: "%Y" %}
    year: {{postyear}}
    {% if {{postyear}} > 2018 %}
        <li>    
        <a href="{{ post.url }}">{{ post.title }}</a>
        </li>
    {% endif %}
    
    
   
  {% endfor %}
</ul>
