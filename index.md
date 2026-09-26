---
layout: default
title: Home
description: News, stories and useful information from Das Profil.
---

<h2>Latest Stories</h2>

{% for post in site.posts %}

<article class="post-card">

  {% if post.image %}
  <a href="{{ post.url | relative_url }}">
    <img src="{{ post.image | relative_url }}" alt="{{ post.title }}">
  </a>
  {% endif %}

  <h2>
    <a href="{{ post.url | relative_url }}">
      {{ post.title }}
    </a>
  </h2>

  <div class="post-date">
    {{ post.date | date: "%B %d, %Y" }}
  </div>

  <p>
    {{ post.excerpt | strip_html | truncate: 220 }}
  </p>

  <a class="read-more" href="{{ post.url | relative_url }}">
    Read more →
  </a>

</article>

{% endfor %}
