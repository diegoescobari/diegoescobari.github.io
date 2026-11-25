---
title: "Publications"
layout: page
permalink: /publications/
---

# Publications

{::nomarkdown}
<div id="pub-filters" class="section-card pub-filters">
  <div class="filter-group" data-cat="topic"><strong>Topic:</strong> <span class="filter-pills"></span></div>
  <div class="filter-group" data-cat="method"><strong>Econometric Method:</strong> <span class="filter-pills"></span></div>
  <div class="filter-group" data-cat="year"><strong>Year:</strong> <span class="filter-pills"></span></div>
  <div class="filter-group" data-cat="other"><strong>Other:</strong> <span class="filter-pills"></span></div>
  <button type="button" id="reset-filters" class="reset-btn">Reset All Filters</button>
</div>

<style>

#pubList,
.pub-entry {
  opacity: 1 !important;
  transform: none !important;
  visibility: visible !important;
  overflow: visible !important;
  max-height: none !important;
}
  
  .pub-filters {
    margin: 16px 0 24px;
  }
  .filter-group {
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    gap: 6px;
    margin-bottom: 10px;
    font-size: 0.88rem;
  }
  .filter-group strong { min-width: 148px; color: #334155; }
  .filter-pills { display: flex; flex-wrap: wrap; gap: 6px; }
  .pub-tags { display: flex; flex-wrap: wrap; gap: 6px; margin-top: 8px; }

  .filter-pill, .pub-tag-btn {
    border: 1px solid #2d6a4f;
    background: transparent;
    color: #2d6a4f;
    padding: 2px 9px;
    border-radius: 999px;
    font-size: 0.78rem;
    cursor: pointer;
    transition: all 0.15s ease;
  }
  .tag-method, .filter-group[data-cat="method"] .filter-pill { border-color: #1d4ed8; color: #1d4ed8; }
  .filter-group[data-cat="year"] .filter-pill { border-color: #475569; color: #475569; }
  .tag-other, .filter-group[data-cat="other"] .filter-pill { border-color: #b45309; color: #b45309; }

  .filter-pill:hover, .pub-tag-btn:hover,
  .filter-pill.active, .pub-tag-btn.active {
    background: #2d6a4f; color: #fff;
  }
  .tag-method.active, .tag-method:hover,
  .filter-group[data-cat="method"] .filter-pill.active,
  .filter-group[data-cat="method"] .filter-pill:hover { background: #1d4ed8; color: #fff; }

  .filter-group[data-cat="year"] .filter-pill.active,
  .filter-group[data-cat="year"] .filter-pill:hover { background: #475569; color: #fff; }

  .tag-other.active, .tag-other:hover,
  .filter-group[data-cat="other"] .filter-pill.active,
  .filter-group[data-cat="other"] .filter-pill:hover { background: #b45309; color: #fff; }

  .reset-btn {
    margin-top: 4px;
    border: none;
    background: #334155;
    color: #fff;
    padding: 4px 12px;
    border-radius: 6px;
    font-size: 0.8rem;
    cursor: pointer;
  }
  .reset-btn:hover { background: #0f172a; }
</style>

<script>
document.addEventListener("DOMContentLoaded", function () {
  const categories = ["topic", "method", "year", "other"];
  const active = { topic: null, method: null, year: null, other: null };
  const entries = document.querySelectorAll(".pub-entry");

  function getYearInterval(yearStr) {
    const y = parseInt(yearStr, 10);
    if (isNaN(y)) return "";
    const start = Math.floor((y - 1) / 5) * 5 + 1;
    const end = start + 4;
    return `${start}-${end}`;
  }

  const maps = { topic: new Map(), method: new Map(), year: new Map(), other: new Map() };

  entries.forEach(entry => {
    const interval = getYearInterval(entry.dataset.year);
    entry.dataset.yearInterval = interval;
    if (interval) {
      maps.year.set(interval, interval);
    }

    ["topic", "method", "other"].forEach(cat => {
      const raw = entry.dataset[cat] || "";
      raw.split(",").map(v => v.trim()).filter(Boolean).forEach(val => {
        if (!maps[cat].has(val)) {
          const btn = entry.querySelector(`.pub-tag-btn[data-cat="${cat}"][data-val="${val}"]`);
          maps[cat].set(val, btn ? btn.textContent.trim() : val);
        }
      });
    });
  });

  categories.forEach(cat => {
    const group = document.querySelector(`.filter-group[data-cat="${cat}"]`);
    const container = group.querySelector(".filter-pills");
    const items = Array.from(maps[cat].entries());

    if (items.length === 0) {
      group.style.display = "none";
      return;
    }

    items.sort((a, b) => cat === "year" ? b[0].localeCompare(a[0]) : a[1].localeCompare(b[1]));

    items.forEach(([val, label]) => {
      const btn = document.createElement("button");
      btn.type = "button";
      btn.className = "filter-pill";
      btn.dataset.cat = cat;
      btn.dataset.val = val;
      btn.textContent = label;
      container.appendChild(btn);
    });
  });

  function applyFilters() {
    entries.forEach(entry => {
      const listItem = entry.closest("li") || entry;
      const matches = categories.every(cat => {
        if (!active[cat]) return true;
        if (cat === "year") {
          return entry.dataset.yearInterval === active.year;
        }
        const vals = (entry.dataset[cat] || "").split(",").map(v => v.trim());
        return vals.includes(active[cat]);
      });
      listItem.style.display = matches ? "" : "none";
    });

    document.querySelectorAll(".filter-pill, .pub-tag-btn").forEach(btn => {
      const cat = btn.dataset.cat;
      btn.classList.toggle("active", active[cat] === btn.dataset.val);
    });
  }

  document.addEventListener("click", function (e) {
    const btn = e.target.closest(".filter-pill, .pub-tag-btn");
    if (btn) {
      const { cat, val } = btn.dataset;
      active[cat] = active[cat] === val ? null : val;
      applyFilters();
    }
  });

  document.getElementById("reset-filters").addEventListener("click", function () {
    categories.forEach(cat => active[cat] = null);
    applyFilters();
  });
});
</script>
{:/}

<input type="text" class="pub-search" id="pubSearch" placeholder="Filter by title, author, or year...">

<div class="section-card" id="pubList">
<h2>Preprints</h2>

{% bibliography --query @unpublished %}

<h2>Refereed Journal Articles</h2>

{% bibliography --query @article %}

<h2>Refereed Conference Proceedings</h2>

{% bibliography --query @inproceedings %}
</div>
