---
layout: page
permalink: /tags/
---

<section class="tags">

{% for tag in site.tags %}
  <strong>{{ tag[0] }}</strong>
  <ul>
    {% for post in tag[1] %}
      <li><a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
  </ul>
{% endfor %}

</section>