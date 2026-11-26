---
title: "Home"
layout: homelay
permalink: /
---

<h1 class="home-hero">{{ site.name }}</h1>
<p class="home-hero-sub">{{ site.title }}, {{ site.institution }}</p>

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

<div class="chip-container" markdown="0">
<a href="{{ '/research' | relative_url }}" class="chip">Quantum Electrodynamics</a>
<a href="{{ '/research' | relative_url }}" class="chip">Path Integrals</a>
<a href="{{ '/research' | relative_url }}" class="chip">Superfluidity</a>
<a href="{{ '/research' | relative_url }}" class="chip">Parton Model</a>
<a href="{{ '/research' | relative_url }}" class="chip">Quantum Computing</a>
<a href="{{ '/research' | relative_url }}" class="chip">Nanotechnology</a>
</div>

<div class="research-grid">

<div class="research-card">
<img src="{{ '/images/research/slide_me.jpg' | relative_url }}" class="research-thumb" width="600" height="300" alt="Fall 2026 Office Hours">
<div class="research-body">
<h2 class="research-title">Fall 2026 Office Hours</h2>
<p class="research-desc">TR 10:00 a.m. – 12:00 p.m. and by appointment.</p>
<p class="research-desc">Class material is posted on Brightspace.</p>
</div>
</div>

<div class="research-card">
<img src="{{ '/images/research/slide_ecmt1.jpg' | relative_url }}" class="research-thumb" width="600" height="300" alt="Econometrics I">
<div class="research-body">
<h2 class="research-title">Econometrics I (PhD)</h2>
<p class="research-desc">This course introduces core econometric tools and their implementation in empirical research and practical applications. Emphasizing methodological foundations and real-world relevance, students learn to analyze data using statistical software, interpret empirical output, and confidently conduct independent quantitative analysis.</p>
</div>
</div>

<div class="research-card">
<img src="{{ '/images/research/slide_ecmt2.jpg' | relative_url }}" class="research-thumb" width="600" height="300" alt="Econometrics II">
<div class="research-body">
<h2 class="research-title">Econometrics II (PhD)</h2>
<p class="research-desc">This course covers the core methods of modern time series analysis, emphasizing their underlying foundations and real-world applications. Through lectures, readings, and hands-on statistical software exercises, students learn to evaluate applied research, interpret econometric output, and conduct independent empirical analysis.</p>
</div>
</div>

</div>
