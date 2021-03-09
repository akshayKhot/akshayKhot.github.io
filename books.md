---
layout: page
title: Books I've Read
permalink: /books/
---

<section class="books">

<div class="summary">I love reading. Mostly non-fiction. This page contains a brief summary and my highlights from the books I read and found interesting. Check out my reading list for <a href="/books-I-read-in-2018">2018</a>, <a href="/books-I-read-in-2019">2019</a>, <a href="/books-I-read-in-2020">2020</a>, and <a href="https://public.3.basecamp.com/p/eyqQGbQ2ZqMEWRrmw6x19XGN">2021</a>.
</div>
{% assign books = site.books | sort: 'date' | reverse %}
{% for book in books %}
    

  <article class="post b">

    <div class="post-title">
      <a href="{{ site.baseurl }}{{ book.url }}">{{ book.title }}</a>
    </div>
    
    <div class="book centered">
      <a target="_blank" href="{{ site.baseurl }}{{ book.url }}">
        <img src="/images/books/{{ book.imglink }}" alt="{{ book.title }}">
      </a>
    </div> 
        
    <div class="entry">
      {{ book.excerpt }}
    </div>
    
    <a href="{{ site.baseurl }}{{ book.url }}" class="read-more">Read More</a>

  </article>

{% endfor %}

</section>