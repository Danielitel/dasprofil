---
layout: default
title: Home
description: News, stories and useful information from Das Profil.
---

<h2>Latest Stories</h2>

{% for post in site.posts %}
<article style="margin-bottom: 30px;">
  <h2>
    <a href="{{ post.url | relative_url }}">
      {{ post.title }}
    </a>
  </h2>

  <p>
    <small>{{ post.date | date: "%B %d, %Y" }}</small>
  </p>

  <p>
    {{ post.excerpt | strip_html | truncate: 180 }}
  </p>

  <a href="{{ post.url | relative_url }}">Read more →</a>
</article>
{% endfor %}
