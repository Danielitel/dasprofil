---
layout: default
title: Entertainment
description: Entertainment news, celebrities, music, movies and popular culture from Das Profil.
---

<div class="homepage">

  <h1>Entertainment</h1>

  {% assign entertainment_posts = site.posts | where: "category", "Entertainment" %}

  {% for post in entertainment_posts %}

  <article class="post-card">

    {% if post.image %}
    <a href="{{ post.url | relative_url }}">
      <img
        src="{{ post.image | relative_url }}"
        alt="{{ post.title }}"
        class="post-card-image"
      >
    </a>
    {% endif %}

    <div class="post-card-content">

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

    </div>

  </article>

  {% endfor %}

</div>
