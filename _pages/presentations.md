---
title: "Presentations"
layout: page
permalink: /presentations/
---

# Presentations

{% if site.data.talks.size > 0 %}
{% assign current_year = "" %}
{% for talk in site.data.talks %}
{% capture talk_year %}{{ talk.year }}{% endcapture %}
{% if talk_year != current_year %}
{% unless forloop.first %}</div>{% endunless %}
{% assign current_year = talk_year %}
<div class="section-card" markdown="0">
<h2>{{ current_year }}</h2>
{% endif %}
{% include talk.html talk=talk %}
{% if forloop.last %}</div>{% endif %}
{% endfor %}
{% else %}
<p class="text-muted">No talks listed yet. Add entries to <code>_data/talks.yml</code>.</p>
{% endif %}
