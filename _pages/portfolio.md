---
layout: archive
title: "PhD Research in High-Performance Computing"
permalink: /portfolio/
author_profile: true
---

{% assign phd_projects = site.portfolio | where: "stage", "phd" | sort: "order" %}
{% for post in phd_projects %}
  {% include archive-single.html %}
{% endfor %}
