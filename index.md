---
title: PhD Theses
---

<style>
  /* Styling for headings and tags */
  h3 {
    margin-bottom: 0.3rem;
    color: #0366d6;
  }

  code {
    background-color: #f1f8ff;
    color: #0366d6;
    padding: 2px 6px;
    border-radius: 4px;
    font-size: 0.85em;
  }

  /* Collapsible abstract styling */
  details {
    margin-top: 0.5rem;
    padding: 0.5rem;
    background-color: #f6f8fa;
    border-radius: 6px;
    border: 1px solid #e1e4e8;
  }

  details summary {
    cursor: pointer;
    color: #24292e;
  }
</style>

# PhD Theses

This is an (incomplete) list of PhD theses in AMASES-related fields.
Suggestions for further additions are very welcome — [download the YAML](theses.yml)
or open a pull request on [GitHub](https://github.com/mlicalzi/AMASES_theses).

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
