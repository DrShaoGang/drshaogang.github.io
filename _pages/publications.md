---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

{% include base_path %}

<div class="publications-intro">
  <div>
    <p class="publications-eyebrow">Research output</p>
    <p class="publications-summary">{{ site.publications | size }} selected publications in data science, remote sensing, forestry, and information studies.</p>
  </div>
  <a class="publications-scholar" href="https://scholar.google.com/citations?user=VcnCIEcAAAAJ&hl=en" target="_blank" rel="noopener noreferrer">Google Scholar <span aria-hidden="true">↗</span></a>
</div>

<div class="publications-list">
{% assign current_year = "" %}
{% for post in site.publications reversed %}
  {% assign publication_year = post.date | date: "%Y" %}
  {% if publication_year != current_year %}
    {% unless current_year == "" %}</div>{% endunless %}
    <div class="publication-year-group">
      <h2 class="publication-year">{{ publication_year }}</h2>
    {% assign current_year = publication_year %}
  {% endif %}
  {% include archive-single-publication.html %}
{% endfor %}
{% unless current_year == "" %}</div>{% endunless %}
</div>
