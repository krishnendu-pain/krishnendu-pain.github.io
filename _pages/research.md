---
layout: page
permalink: /research/
title: research
description:
nav: true
nav_order: 2

# Turn each section on (true) or off (false). Each section reads its own BibTeX file in _bibliography/.
sections:
  works_in_progress: true # _bibliography/works_in_progress.bib
  working_papers: true # _bibliography/working_papers.bib
  publications: true # _bibliography/papers.bib
---

<!-- _pages/research.md -->

{% include bib_search.liquid %}

{% if page.sections.works_in_progress %}

<h2 id="works-in-progress">Works in Progress</h2>
<div class="publications">
{% bibliography --file works_in_progress.bib %}
</div>
{% endif %}

{% if page.sections.working_papers %}

<h2 id="working-papers">Working Papers</h2>
<div class="publications">
{% bibliography --file working_papers.bib %}
</div>
{% endif %}

{% if page.sections.publications %}

<h2 id="publications">Publications</h2>
<div class="publications">
{% bibliography --file papers.bib %}
</div>
{% endif %}
