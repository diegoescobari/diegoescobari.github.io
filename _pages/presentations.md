---
title: "Presentations"
layout: page
permalink: /presentations/
---

# Presentations

{% assign talks_by_year = site.data.talks | group_by: "year" | sort: "name" | reverse %}

{% for year_group in talks_by_year %}
<div class="section-card" markdown="0">
<h2>{{ year_group.name }}</h2>
{% for talk in year_group.items %}{% include talk.html talk=talk %}{% endfor %}
</div>
{% endfor %}

{% unless site.data.talks.size > 0 %}
<p class="text-muted">No talks listed yet. Add entries to <code>_data/talks.yml</code>.</p>
{% endunless %}
