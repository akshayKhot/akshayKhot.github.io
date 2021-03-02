---
layout: page
title: Archive
permalink: /archive/
---

<section class="archive">

  {% for post in site.posts %}
  {% assign currentdate = post.date | date: "%Y" %}
  {% if currentdate != date %}
    {% unless forloop.first %}</ul>{% endunless %}
    <div class="year" id="y{{post.date | date: "%Y"}}">{{ currentdate }}</div>
    <ul>
    {% assign date = currentdate %}
  {% endif %}
    <li><a href="{{ post.url }}">{{ post.title }}</a></li>
  {% if forloop.last %}</ul>{% endif %}
  {% endfor %}

</section>