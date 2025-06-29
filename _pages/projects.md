<!-- ---
layout: archive
title: "Projects"
permalink: /projects/
author_profile: true
redirect_from:
  - /projects
---

{% include base_path %}

 -->


---
layout: default
title: Projects
permalink: /projects/
---
{% for project in site.projects %}
### [{{ project.title }}]({{ project.url }})

{% if project.links %}
{% for link in project.links %}
[{{ link.text }}]({{ link.url }}),
{% endfor %}
{% endif %}

{{ project.excerpt }}

{% if project.image %}
  <img src="{{ project.image }}" alt="{{ project.title }}" width="400">
{% endif %}


<hr>
{% endfor %}
