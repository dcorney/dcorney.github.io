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
    
   
  {% endfor %}
</ul>
