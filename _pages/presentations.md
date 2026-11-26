---
title: "Presentations"
layout: page
permalink: /presentations/
---

# Presentations

{% if site.data.talks.size > 0 %}
<div class="section-card" markdown="0">
<h2>Conference Presentations and Invited Seminars</h2>
{% for talk in site.data.talks %}{% include talk.html talk=talk %}{% endfor %}
</div>
{% endif %}

{% unless site.data.talks.size > 0 %}
<p class="text-muted">No talks listed yet. Add entries to <code>_data/talks.yml</code>.</p>
{% endunless %}

