---
title: "Presentations"
layout: page
permalink: /presentations/
---

# Presentations

{% assign items = site.data.presentations | sort_natural: "event" %}
{% if items and items.size > 0 %}
<div class="section-card" markdown="0">
{% for item in items %}
  {% include presentations.html item=item %}
{% endfor %}
</div>
{% else %}
<p class="text-muted">No presentations listed yet. Add entries to <code>_data/presentations.yml</code>.</p>
{% endif %}
