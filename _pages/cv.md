---
title: "Curriculum Vitae"
layout: page
sitemap: false
permalink: /cv/
---

# C.V.

# <h3>Curriculum Vitae</h3>
<p>
  <a href="{{ '/DiegoCV.pdf' | relative_url }}" target="_blank" rel="noopener">
    Click here to download the PDF file.
  </a>
</p>

<object data="{{ '/DiegoCV.pdf' | relative_url }}" type="application/pdf" width="100%" height="900px" style="border: 1px solid #ddd; border-radius: 6px;">
  <p>
    It appears you don't have a PDF plugin for this browser.
    <a href="{{ '/DiegoCV.pdf' | relative_url }}" target="_blank" rel="noopener">
      Click here to download the PDF file.
    </a>
  </p>
</object>

{% if site.data.grants %}
<div class="section-card">
<h3>Grants</h3>
<ul>
{% for grant in site.data.grants %}
<li>{{ grant.name }}</li>
{% endfor %}
</ul>
</div>
{% endif %}

{% if site.data.awards %}
<div class="section-card">
<h3>Awards</h3>
<ul>
{% for award in site.data.awards %}
<li>{{ award.name | replace: "-","&#8211;" }}</li>
{% endfor %}
</ul>
</div>
{% endif %}

{% if site.data.funders %}
<div class="section-card">
<h4>Sponsors</h4>
<div class="sponsor-logos" style="display: flex; flex-wrap: wrap; align-items: center; justify-content: center; gap: var(--space-6);">
{% for funder in site.data.funders %}
<a href="{{ funder.url }}" target="_blank"><img src="{{ funder.image | prepend: '/images/' | relative_url }}" alt="Funder logo" style="max-height: 80px; max-width: 200px; border-radius: 0;" loading="lazy"></a>
{% endfor %}
</div>
</div>
{% endif %}
