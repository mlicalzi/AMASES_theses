---
layout: default
title: PhD Theses | AMASES
description: >
  Discover PhD theses written by scientists related to AMASES
title: PhD Theses
---

# PhD Theses

This is an (incomplete) list of PhD theses in fields related to AMASES (Association for Mathematics Applied to Economic and Social Sciences).
Suggestions for further additions are very welcome.
You can also [download the YAML](_data/theses.yml).

{% assign years = site.data.theses | group_by: "year" | sort: "name" | reverse %}
{% for group in years %}[{{ group.name }}](#{{ group.name }}) {% endfor %}

{% for group in years %}
## {{ group.name }} {: id="{{ group.name }}" }

{% assign items = group.items | sort: "name" %}
{% for t in items %}
- **{{ t.name }}** ({{ t.affiliation }}, {{ t.year }})  
  [{{ t.title }}]({{ t.url }})  
  {% if t.supervisors.size == 1 %}Supervisor: {{ t.supervisors[0] }}
  {% else %}Supervisors:
  {% for s in t.supervisors %}{{ s }}{% unless forloop.last %} and{% endunless %} {% endfor %}
  {% endif %}
{% endfor %}
{% endfor %}
