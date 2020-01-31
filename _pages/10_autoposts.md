---
layout: page
title: Algorithmic texts
permalink: /Posts/
---

I've recently started working on some code that generates readable texts, with the ultimate goal of algorithmic generation of a whole novel. Realistically, I'd love to generate a page or two of readable text... 

Inspired by [NaNoGenMo](https://github.com/NaNoGenMo/2016) (though I'm not actually participating - maybe in 2017?).

Below are some samples of what I've produced so far, combining bi-directional Markov chains, snippets from Wikipedia and chunks of Project Gutenberg texts. I've also put in a few notes about methods I've explored.

<ul>
  {% for post in site.posts %}
    <li>
      {% if post.category == 'explanation' %}
      <i>	
      {% endif %}
       <a href="{{ post.url }}">{{ post.title }}</a>
      {% if post.category == 'explanation' %}
      </i>	
      {% endif %}
    </li>
  {% endfor %}
</ul>