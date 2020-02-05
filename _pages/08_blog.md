---
layout: page
title: Thoughts
permalink: /Blog/
---

Testing even more 8...

<ul>
  {% for post in site.posts %}
    <li>
    Title {{post.title}} 
    </li>
    {% assign postyear = post.date | date: "%Y" %}
    year: {{postyear | plus: 100}}
    {% if {{postyear}} > 2018 %}
        wow
        <a href="{{ post.url }}">{{ post.title }}</a>
        
    {% endif %}
    
    
   
  {% endfor %}
</ul>
