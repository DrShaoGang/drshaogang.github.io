---
layout: archive
title: "Teaching"
permalink: /teaching/
author_profile: true
---

{% include base_path %}

<div class="teaching-intro">
  <p class="teaching-eyebrow">Course portfolio</p>
  <p>Graduate and undergraduate teaching in data science, natural language processing, geospatial analysis, remote sensing, and data management.</p>
</div>

<section class="teaching-section" aria-labelledby="current-courses">
  <div class="teaching-section__heading">
    <span class="teaching-section__marker">Current</span>
    <h2 id="current-courses">Courses</h2>
  </div>
  <div class="teaching-grid">
    {% assign current_courses = site.teaching | where: "status", "current" | sort: "date" | reverse %}
    {% for post in current_courses %}{% include teaching-card.html %}{% endfor %}
  </div>
</section>

<section class="teaching-section" aria-labelledby="independent-study">
  <div class="teaching-section__heading teaching-section__heading--independent">
    <span class="teaching-section__marker">Mentored learning</span>
    <h2 id="independent-study">Independent Study</h2>
  </div>
  <div class="teaching-grid">
    {% assign independent_courses = site.teaching | where: "status", "independent" | sort: "date" | reverse %}
    {% for post in independent_courses %}{% include teaching-card.html %}{% endfor %}
  </div>
</section>

<section class="teaching-section" aria-labelledby="past-teaching">
  <div class="teaching-section__heading teaching-section__heading--past">
    <span class="teaching-section__marker">Archive</span>
    <h2 id="past-teaching">Teaching (Past)</h2>
  </div>
  <div class="teaching-grid">
    {% assign past_courses = site.teaching | where: "status", "past" | sort: "date" | reverse %}
    {% for post in past_courses %}{% include teaching-card.html %}{% endfor %}
  </div>
</section>
