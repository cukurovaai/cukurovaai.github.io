---
layout: page
title: titles.team
description: descriptions.team
permalink: /team/
nav: true
nav_order: 5
display_categories: [faculty]
---

<!-- pages/team.md -->
<div class="projects">
{%- if site.enable_team_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {%- for category in page.display_categories %}
  {% capture localized_category %}members.categories.{{category}}{% endcapture %}
  {%- assign categorized_members = site.team | where: "category", category -%}
  {%- assign sorted_members = categorized_members | sort: "importance" %}
  {%- if sorted_members.size != 0 %} <h2 class="category">{% t localized_category %}</h2> {%- endif -%}

  <!-- Generate cards for each project -->
  <div class="container">
  <div class="row">
    {%- for member in sorted_members -%}
    <div class="col-md-4">
      {% include member.html %}
    </div>
    {%- endfor %}
  </div>
  </div>
  {% endfor %}

{%- else -%}
<!-- Display projects without categories -->
  {%- assign sorted_members = site.group | sort: "importance" -%}
  <!-- Generate cards for each project -->
  <div class="grid">
    {%- for member in sorted_members -%}
      {% include member.html %}
    {%- endfor %}
  </div>
{%- endif -%}
</div>
