---
title: "Presentations"
layout: page
permalink: /presentations/
---

# Presentations

{% assign items = site.data.presentations %}
{% if items and items.size > 0 %}
<div class="section-card" markdown="0">
{% assign current_year = "" %}
{% for item in items %}
  {% capture item_year %}{{ item.year }}{% endcapture %}
  {% if item_year != current_year %}
    {% assign current_year = item_year %}
    <h2>{{ current_year }}</h2>
  {% endif %}
  {% include presentations.html item=item %}
{% endfor %}
</div>
{% else %}
<p class="text-muted">No presentations listed yet. Add entries to <code>_data/presentations.yml</code>.</p>
{% endif %}
