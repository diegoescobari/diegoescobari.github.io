---
title: "Home"
layout: homelay
permalink: /
---

<h1 class="home-hero">{{ site.name }}</h1>
<p class="home-hero-sub">{{ site.title }}, {{ site.institution }}</p>

<div class="chip-container" markdown="0">
<a href="{{ '/research' | relative_url }}" class="chip">Quantum Electrodynamics</a>
<a href="{{ '/research' | relative_url }}" class="chip">Path Integrals</a>
<a href="{{ '/research' | relative_url }}" class="chip">Superfluidity</a>
<a href="{{ '/research' | relative_url }}" class="chip">Parton Model</a>
<a href="{{ '/research' | relative_url }}" class="chip">Quantum Computing</a>
<a href="{{ '/research' | relative_url }}" class="chip">Nanotechnology</a>
</div>

I am an applied econometrician who is fascinated with working with data to draw inferences and explore economic questions. Most of my research focuses on studying demand, as well as explaining pricing and interactions in markets with individual level data. I have empirical and theoretical work on various aspects of pricing, including pricing under uncertainty, peak-load pricing, dynamic pricing, refund contracts, dynamic price discrimination, spatial competition, asymmetric pricing, bundling, loyalty programs, and explosiveness and bubbles.

Many of the tools and insights in my work to understand pricing and demand uses data from airlines. I also explored other markets, including contributions to explain behavior in real estate markets and investments. I am also interested on peer-to-peer lending markets and information systems.

I obtained my PhD in Economics from Texas A&M University. I am currently the Vice President and President-elect of the Society of Bolivian Economists as well as the PhD Program Director and Professor of Economics in the Robert C. Vackar College of Business & Entrepreneurship at The University of Texas Rio Grande Valley. I regularly teach undergraduate and PhD econometrics classes.

Please use this website to find the links to my research papers and learn about my teaching. Thank you for taking the time.

<div class="callout callout-success" markdown="0">
<div class="callout-title">{% include icon.html name="award" class="callout-icon" %} Nobel Prize in Physics, 1965</div>
<p>Awarded the Nobel Prize jointly with Julian Schwinger and Shin'ichiro Tomonaga for fundamental work in quantum electrodynamics, with deep-ploughing consequences for the physics of elementary particles.</p>
</div>

<div class="banner-frame" markdown="0">
<img src="{{ '/images/banner.webp' | relative_url }}" alt="Feynman diagrams" width="1400" height="449" loading="lazy">
<div class="banner-caption">Examples of Feynman diagrams. Feynman R., <em>The theory of positrons. Phys. Rev.</em> (1949)</div>
</div>

{% capture selected %}{% bibliography --query @*[selected=true] %}{% endcapture %}
{% if selected contains "pub-entry" %}
## Selected publications

<div class="section-card selected-pubs" markdown="0">
{{ selected }}
<p style="margin: var(--space-4) 0 0;"><a href="{{ '/publications' | relative_url }}">All publications &rarr;</a></p>
</div>
{% endif %}

## About me

I am a physicist working in the field of quantum mechanics and quantum electrodynamics.
I received my undergraduate degree in physics from the Massachusetts Institute of Technology (MIT) in 1939 and went on to earn my PhD from Princeton University in 1942.
After completing my doctoral studies, I worked on the Manhattan Project, where I helped develop the first atomic bombs.
After the war, I returned to academia, holding teaching and research positions at Cornell and now at the California Institute of Technology.
