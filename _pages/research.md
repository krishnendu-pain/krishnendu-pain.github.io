---
layout: page
permalink: /research/
title: Research
description:
nav: true
nav_order: 2

# Turn each section on (true) or off (false). Each section reads its own BibTeX file in _bibliography/.
sections:
  publications: false # _bibliography/papers.bib
  working_papers: false # _bibliography/working_papers.bib
  works_in_progress: true # _bibliography/works_in_progress.bib
  pre_phd: true # _bibliography/pre_phd.bib

# Show the "Type to filter" search box above the sections (true) or hide it (false).
search_box: false
---

<!-- _pages/research.md -->

<!-- Entries without an abbr (venue badge) leave an empty left column that indents the text; hide it so entries align with the headings. -->
<style>
  .publications ol.bibliography li .row > .abbr:not(:has(*)) {
    display: none;
  }
  .publications ol.bibliography li .row:not(:has(.abbr *)) > .col-sm-8 {
    flex: 0 0 100%;
    max-width: 100%;
  }
  /* Space between research sections */
  .publications + h2 {
    margin-top: 3rem;
  }
</style>

{% if page.search_box %}
{% include bib_search.liquid %}
{% endif %}

{% if page.sections.publications %}

<h2 id="publications">Publications</h2>
<div class="publications">
{% bibliography --file papers.bib %}
</div>
{% endif %}

{% if page.sections.working_papers %}

<h2 id="working-papers">Working Papers</h2>
<div class="publications">
{% bibliography --file working_papers.bib %}
</div>
{% endif %}

{% if page.sections.works_in_progress %}

<h2 id="works-in-progress">Works in Progress</h2>
<div class="publications">
{% bibliography --file works_in_progress.bib %}
</div>
{% endif %}

{% if page.sections.pre_phd %}

<h2 id="pre-phd">Pre-PhD RA Work</h2>
<div class="publications">
{% bibliography --file pre_phd.bib %}
</div>
{% endif %}