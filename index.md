---
layout: default
title: PhD Theses | COMSOC
description: >-
  Discover PhD theses that have been written by scholars related to AMASES.
---

<section markdown="1" class="section-with-navs">

# PhD Theses

This is an (incomplete) list of PhD theses in fields related to [AMASES](https://www.amases.org) (Association for Mathematics Applied to Economic and Social Sciences).

Suggestions for further additions are very welcome. 

 You can ping [GitHub]({{ site.github.repository_url | default: site.github_url | default: '#' }}) or [download the YAML database](_data/theses.yml).


{% assign theses_by_year = site.data.theses | group_by: 'year' %}
{% assign theses_by_year_sorted = theses_by_year | sort: 'name' | reverse %}
<div class="page-navigation-wrap">
  <div class="page-navigation">
    {% for year in theses_by_year_sorted %}
      <span><a href="#{{ year.name }}">{{ year.name }}</a></span>
    {% endfor %}
  </div>
</div>
</section>

{% for year in theses_by_year_sorted %}
<section id="{{ year.name }}">
  <h2>{{ year.name }}</h2>
  <ul>
    {% for thesis in year.items %}
      <li>
        <p>
          <strong>{{ thesis.name }}</strong> ({{ thesis.affiliation }}, {{ thesis.year }})<br>
          <a href="{{ thesis.url }}" target="_blank" rel="noreferrer">{{ thesis.title }}</a><br>
          {% if thesis.supervisors and thesis.supervisors.size > 0 %}
            {% if thesis.supervisors.size == 1 %}
              Supervisor: {{ thesis.supervisors[0] }}
            {% else %}
              Supervisors: 
              {% for supervisor in thesis.supervisors %}
                {{ supervisor }}{% unless forloop.last %}{% if forloop.rindex == 2 %} and {% else %}, {% endif %}{% endunless %}
              {% endfor %}
            {% endif %}
          {% endif %}
        </p>
      </li>
    {% endfor %}
  </ul>
</section>
{% endfor %}
