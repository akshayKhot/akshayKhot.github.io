---
layout: page
title: Archive
permalink: /archive/
---

<section class="archive">

  {% for post in site.posts %}
    <div class="link">
      <a href="{{ post.url }}">{{ post.title }}</a>
    <div class="date">{{ post.date | date: "%B %e, %Y" }}
    {% if post.tags.size > 0 %}
      in
        {% for tag in post.tags %}
          <strong><a href="/tags/#{{ tag }}">{{ tag }}{% if forloop.last %}{% else %},{% endif %}</a></strong>
        {% endfor %}
      {% endif %}
    </div>
    </div>
  {% endfor %}

</section>