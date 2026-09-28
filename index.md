---
layout: default
title: Home
description: Celebrity biographies, entertainment, lifestyle, news and trending stories from Das Profil.
---

<div class="homepage">

  {% assign featured_post = site.posts.first %}

  {% if featured_post %}

  <!-- FEATURED STORY -->

  <section class="featured-story">

    {% if featured_post.image %}
    <a href="{{ featured_post.url | relative_url }}">
      <img
        src="{{ featured_post.image | relative_url }}"
        alt="{{ featured_post.title }}"
        class="featured-image"
      >
    </a>
    {% endif %}

    <div class="featured-content">

      <div class="story-category">
        {{ featured_post.category | default: "Featured" }}
      </div>

      <h1>
        <a href="{{ featured_post.url | relative_url }}">
          {{ featured_post.title }}
        </a>
      </h1>

      <div class="post-date">
        {{ featured_post.date | date: "%B %d, %Y" }}
      </div>

      <p>
        {{ featured_post.excerpt | strip_html | truncate: 250 }}
      </p>

      <a class="featured-read-more" href="{{ featured_post.url | relative_url }}">
        Read Story →
      </a>

    </div>

  </section>

  {% endif %}


  <!-- LATEST STORIES -->

  <section class="latest-section">

    <h2 class="section-title">Latest Stories</h2>

    <div class="story-grid">

      {% for post in site.posts offset:1 %}

      <article class="story-card">

        {% if post.image %}
        <a href="{{ post.url | relative_url }}">
          <img
            src="{{ post.image | relative_url }}"
            alt="{{ post.title }}"
            class="story-card-image"
          >
        </a>
        {% endif %}

        <div class="story-card-content">

          <div class="story-category">
            {{ post.category | default: "Story" }}
          </div>

          <h3>
            <a href="{{ post.url | relative_url }}">
              {{ post.title }}
            </a>
          </h3>

          <div class="post-date">
            {{ post.date | date: "%B %d, %Y" }}
          </div>

          <p>
            {{ post.excerpt | strip_html | truncate: 140 }}
          </p>

          <a class="read-more" href="{{ post.url | relative_url }}">
            Read more →
          </a>

        </div>

      </article>

      {% endfor %}

    </div>

  </section>

</div>
