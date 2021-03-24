---
layout: page
title: Personal Blog
permalink: /blog/
---

<section class="blog">

{% assign posts = site.blog | sort: 'date' | reverse %}
{% for post in posts %}

  <article class="post b">

    <div class="post-title"><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></div>
    
    <div class="date">
      {{ post.date | date: "%B %e, %Y" }}
      <!-- {% if post.tags.size > 0 %}
      in
        {% for tag in post.tags %}
          <strong><a href="/tags/#{{ tag }}">{{ tag }}{% if forloop.last %}{% else %},{% endif %}</a></strong>
        {% endfor %}
      {% endif %} -->
    </div>

	<div class="entry">
      {{ post.excerpt }}
    </div>

    <a href="{{ site.baseurl }}{{ post.url }}" class="read-more">Read More</a>

  </article>

{% endfor %}

</section>