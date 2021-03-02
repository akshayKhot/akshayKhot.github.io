---
layout: page
title: Archive
permalink: /archive/
---

<section class="archive">

  {% for post in site.posts  %}
    {% capture this_year %}{{ post.date | date: "%Y" }}{% endcapture %}
    {% capture next_year %}{{ post.previous.date | date: "%Y" }}{% endcapture %}

    {% if forloop.first %}
    <div class="year" id="{{ this_year }}-ref">{{this_year}}</div>
    <ul>
    {% endif %}

    <li><a href="{{ post.url }}">{{ post.title }}</a></li>

    {% if forloop.last %}
    </ul>
    {% else %}
        {% if this_year != next_year %}
        </ul>
        <div class="year" id="{{ next_year }}-ref">{{next_year}}</div>
        <ul>
        {% endif %}
    {% endif %}
  {% endfor %}

</section>