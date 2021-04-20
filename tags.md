---
layout: page
title: Tags
permalink: /tags/
---

<section class="tags">

  {% for tag in site.tags %}
    <div id="{{ tag[0] }}" class="tag-container">
      <div class="tag-name"> {{ tag[0] }} </div>
      <div class="tagged-posts">
        {% for post in tag[1] %}
          <div><a href="{{ post.url }}">{{ post.title }}</a></div>
        {% endfor %}
      </div>
    </div>
  {% endfor %}

</section>