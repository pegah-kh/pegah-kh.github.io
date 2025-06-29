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
{% for link in project.links %}
[{{ link.text }}]({{ link.url }}),
{% endfor %}

{{ project.excerpt }}

<img src="{{ project.image }}" width="400">
{% endfor %}
