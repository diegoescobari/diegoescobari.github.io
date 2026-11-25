---
title: "Publications"
layout: page
permalink: /publications/
---

# Publications

<div id="tag-filter-bar" class="tag-filter-bar">
  <button type="button" class="filter-pill active" data-tag="all">All</button>
</div>

<style>
  .tag-filter-bar {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    margin: 16px 0 24px;
  }
  .pub-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
    margin-top: 8px;
  }
  .filter-pill, .pub-tag-btn {
    border: 1px solid #2d6a4f;
    background: transparent;
    color: #2d6a4f;
    padding: 3px 10px;
    border-radius: 999px;
    font-size: 0.82rem;
    cursor: pointer;
    transition: all 0.15s ease;
  }
  .filter-pill:hover, .pub-tag-btn:hover,
  .filter-pill.active, .pub-tag-btn.active {
    background: #2d6a4f;
    color: #ffffff;
  }
</style>

<script>
document.addEventListener("DOMContentLoaded", function () {
  const filterBar = document.getElementById("tag-filter-bar");
  const entries = document.querySelectorAll(".pub-entry");
  const tagMap = new Map();

  // 1. Collect all unique tags from the papers
  document.querySelectorAll(".pub-tag-btn").forEach(btn => {
    const key = btn.dataset.tag;
    if (key && !tagMap.has(key)) {
      tagMap.set(key, btn.textContent.trim());
    }
  });

  // 2. Sort tags alphabetically and add them to the top filter bar
  Array.from(tagMap.entries())
    .sort((a, b) => a[1].localeCompare(b[1]))
    .forEach(([key, label]) => {
      const btn = document.createElement("button");
      btn.type = "button";
      btn.className = "filter-pill";
      btn.dataset.tag = key;
      btn.textContent = label;
      filterBar.appendChild(btn);
    });

  // 3. Filtering function
  function applyFilter(selectedTag) {
    entries.forEach(entry => {
      const listItem = entry.closest("li") || entry;
      const tags = (entry.dataset.tags || "")
        .split(",")
        .map(t => t.trim())
        .filter(Boolean);

      if (selectedTag === "all" || tags.includes(selectedTag)) {
        listItem.style.display = "";
      } else {
        listItem.style.display = "none";
      }
    });

    // Update active state on all buttons
    document.querySelectorAll(".filter-pill, .pub-tag-btn").forEach(btn => {
      btn.classList.toggle("active", btn.dataset.tag === selectedTag);
    });
  }

  // 4. Listen for clicks on both the top bar and individual paper tags
  document.addEventListener("click", function (e) {
    const btn = e.target.closest(".filter-pill, .pub-tag-btn");
    if (!btn) return;
    const tag = btn.dataset.tag;
    const isAlreadyActive = btn.classList.contains("active") && tag !== "all";
    applyFilter(isAlreadyActive ? "all" : tag);
  });
});
</script>





<input type="text" class="pub-search" id="pubSearch" placeholder="Filter by title, author, or year...">

<div class="section-card" id="pubList">
<h2>Preprints</h2>

{% bibliography --query @unpublished %}

<h2>Refereed Journal Articles</h2>

{% bibliography --query @article %}

<h2>Refereed Conference Proceedings</h2>

{% bibliography --query @inproceedings %}
</div>
