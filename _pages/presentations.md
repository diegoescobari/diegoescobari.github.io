---

title: "Presentations"

layout: page

permalink: /presentations/

---



# Presentations


{% assign invited = site.data.presentations | where: "type", "invited" %}
{% assign contributed = site.data.presentations | where_exp: "t", "t.type != 'invited'" %}



{% if invited.size > 0 %}

<div class="section-card" markdown="0">

<h2>Invited Presentations</h2>

{% for presentations in invited %}{% include presentations.html presentations=presentations %}{% endfor %}

</div>

{% endif %}



{% if contributed.size > 0 %}

<div class="section-card" markdown="0">

<h2>Contributed Presentations</h2>

{% for presentations in contributed %}{% include presentations.html presentations=presentations %}{% endfor %}

</div>

{% endif %}



{% unless site.data.presentations.size > 0 %}

<p class="text-muted">No presentations listed yet. Add entries to <code>_data/presentations.yml</code>.</p>

{% endunless %}
