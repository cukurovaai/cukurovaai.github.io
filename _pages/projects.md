---
layout: page
title: titles.projects
description: descriptions.projects
permalink: /projects/
nav: true
nav_order: 2
display_categories: [eu, tubitak, tagem, bap]
horizontal: false
---

<!-- pages/projects.md -->
<div class="projects">
{%- if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {%- for category in page.display_categories %}
  {% capture localized_category %}projects.categories.{{category}}{% endcapture %}
  <h2 class="category">{% t localized_category %}</h2>
  {%- assign categorized_projects = site.projects | where: "category", category -%}
  {%- assign sorted_projects = categorized_projects | sort: "importance" %}
  <div class="table-responsive">
    <table class="table table-sm table-borderless">
     {%- for project in sorted_projects -%}
     <tr>
        <td>
          <a  href="{{ project.url | prepend: site.baseurl }}">{% t project.title %}</a> - {% t project.description %}
        </td>
       </tr>
      {%- endfor %}
    </table>
  </div>
  {%- endif -%}
  {% endfor %}
{%- endif -%}
</div>
