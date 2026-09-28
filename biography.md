---
layout: default
title: Biography
description: Celebrity biographies, profiles and life stories from Das Profil.
---

<div class="homepage">

  <h1>Biography</h1>

  {% assign biography_posts = site.posts | where: "category", "Biography" %}

  {% for post in biography_posts %}

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
