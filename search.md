---
layout: default
title: Search
description: Search stories and articles on Das Profil.
---

<div class="search-page">

  <h1>Search Das Profil</h1>

  <div class="search-box">
    <input
      type="search"
      id="search-input"
      placeholder="Search stories..."
      aria-label="Search stories"
    >
  </div>

  <div id="search-results"></div>

</div>

<script>
const searchInput = document.getElementById("search-input");
const results = document.getElementById("search-results");

let posts = [];

fetch("{{ '/search.json' | relative_url }}")
  .then(response => response.json())
  .then(data => {
    posts = data;
  })
  .catch(error => {
    results.innerHTML = "<p>Unable to load search results.</p>";
  });

searchInput.addEventListener("input", function () {

  const query = this.value.toLowerCase().trim();

  if (!query) {
    results.innerHTML = "";
    return;
  }

  const matches = posts.filter(post =>
    post.title.toLowerCase().includes(query) ||
    post.description.toLowerCase().includes(query) ||
    post.content.toLowerCase().includes(query)
  );

  if (matches.length === 0) {
    results.innerHTML = "<p>No stories found.</p>";
    return;
  }

  results.innerHTML = matches.map(post => `
    <article class="search-result">
      <h2>
        <a href="${post.url}">${post.title}</a>
      </h2>

      <div class="post-date">${post.date}</div>

      <p>${post.description}</p>
    </article>
  `).join("");

});
</script>
