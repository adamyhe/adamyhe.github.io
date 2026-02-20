---
layout: archive
title: "CV"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}

Work experience
======

* 2026-：Postdoctoral Scholar, Department of Genetics, Stanford School of Medicine
* 2022: PhD Intern, Medical Affairs, Regeneron Pharmaceuticals

Education
======

* Ph.D. in Computational Biology, Cornell University, 2025
* B.A. in Biology and Mathematics, Pomona College, 2017

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
