---
layout: page
title: Tags
permalink: /tags/
---

<section class="tags">

{% for tag in site.tags reversed %}
  <ul id="{{ tag[0] }}">
    <div class="tag-name">{{ tag[0] }}</div>
    {% for post in tag[1] %}
      <li><a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
  </ul>
{% endfor %}

</section>