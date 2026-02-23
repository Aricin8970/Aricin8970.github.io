---
layout: page
title: Projects
permalink: /projects/
---

## My Projects

{% for project in site.projects %}
- [{{project.title }}]({{ project.url }})
{% endfor %}
