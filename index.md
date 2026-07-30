---
title: PhD Theses
---

# PhD Theses

This is an (incomplete) list of PhD theses in AMASES-related fields.
Suggestions for further additions are very welcome — [download the YAML](_data/theses.yml)
or open a pull request on [GitHub](https://github.com/mlicalzi/AMASES_theses/_data/theses.yaml).

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
