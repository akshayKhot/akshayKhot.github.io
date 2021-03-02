---
layout: page
title: Tags
permalink: /tags/
---

<section class="tags">

  {% for tag in site.tags reversed %}
    <div id="{{ tag[0] }}" class="tag-container">
      <div class="tag-name"> {{ tag[0] }} </div>
      <ul>
        {% for post in tag[1] %}
          <li><a href="{{ post.url }}">{{ post.title }}</a></li>
        {% endfor %}
      </ul>
    </div>
  {% endfor %}

</section>