---
layout: page
title: Books I've Read
permalink: /books/
---

<section class="books">

<p class="summary">
  This is a collection of books I have read or am reading right now. It's not my summary or an opinion piece, but a list of passages and highlights from the book that resonated. 
</p>

{% for post in site.categories["books"] %}
    
  <article class="post b">

    <div class="post-title"><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></div>

    <div class="date">
      {{ post.date | date: "%B %e, %Y" }}
      {% if post.tags.size > 0 %}
      in
        {% for tag in post.tags %}
          <strong><a href="/tags/#{{ tag }}">{{ tag }}{% if forloop.last %}{% else %},{% endif %}</a></strong>
        {% endfor %}
      {% endif %}
    </div>

    <div class="entry">
      {{ post.excerpt }}
    </div>

    <a href="{{ site.baseurl }}{{ post.url }}" class="read-more">Read More</a>

  </article>
  
{% endfor %}

</section>