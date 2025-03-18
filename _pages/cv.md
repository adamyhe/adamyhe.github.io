---
layout: archive
title: "CV"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}

Education
======

* Ph.D. in Computational Biology, Cornell University, 2025 (expected)
* B.A. in Biology and Mathematics, Pomona College, 2017

Work experience
======

* 2022: PhD Intern
  * Medical Affairs, Regeneron Pharmaceuticals
  * Developed machine learning models to identify predictors of NSCLC patient outcomes.

Publications
======
  <ul>{% for post in site.publications reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>
  
Talks
======
  <ul>{% for post in site.talks reversed %}
    {% include archive-single-talk-cv.html  %}
  {% endfor %}</ul>
