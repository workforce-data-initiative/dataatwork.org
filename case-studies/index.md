---
title: Case Studies
layout: page
lead: true
---

We're curious to learn about some of the common issues users face when
working with skills and training outcomes data.  In our Case Study series, we are highlighting
projects and organisations who are working with the Data@Work
APIs and tooling in interesting and innovative ways.

{% for case_study in site.case_studies %}
* [{{ case_study.authors }}: {{case_study.title}}]({{ case_study.url }})
{% endfor %}
