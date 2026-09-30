---
layout: default
title: Entertainment
description: Entertainment news, celebrities, music, movies and popular culture from Das Profil.
---

<div class="homepage">

  <h1>Entertainment</h1>

  {% assign entertainment_posts = site.posts | where: "category", "Entertainment" %}

  <div id="entertainment-posts">

    {% for post in entertainment_posts %}

    <article class="post-card entertainment-pagination-item">

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

  <div id="entertainment-pagination" class="pagination"></div>

</div>

<script>
document.addEventListener("DOMContentLoaded", function () {

  const posts = document.querySelectorAll(".entertainment-pagination-item");
  const pagination = document.getElementById("entertainment-pagination");

  const postsPerPage = 5;
  const totalPages = Math.ceil(posts.length / postsPerPage);

  function showPage(page) {

    posts.forEach((post, index) => {

      const start = (page - 1) * postsPerPage;
      const end = start + postsPerPage;

      post.style.display =
        index >= start && index < end ? "block" : "none";

    });

    pagination.innerHTML = "";

    if (totalPages <= 1) {
      return;
    }

    for (let i = 1; i <= totalPages; i++) {

      const button = document.createElement("a");

      button.href = "#";
      button.textContent = i;
      button.className = i === page ? "active" : "";

      button.addEventListener("click", function (event) {
        event.preventDefault();
        showPage(i);
        window.scrollTo({ top: 0, behavior: "smooth" });
      });

      pagination.appendChild(button);
    }

  }

  showPage(1);

});
</script>
