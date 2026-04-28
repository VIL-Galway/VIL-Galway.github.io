---
layout: page
title: Projects
permalink: /projects/
description:
nav: true
nav_order: 4
display_categories: [Computer Vision, Respossible AI, Others]
horizontal: false
---

<!-- pages/projects.md -->
<div class="projects">

{% if site.enable_project_categories and page.display_categories %}

  <!-- Display categorized projects -->
  {% for category in page.display_categories %}
  
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>

  {% assign categorized_projects = site.projects
    | where: "category", category
    | where_exp: "p", "p.hidden != true"
    | sort: "importance" %}

  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
      {% for project in categorized_projects %}
        {% include projects_horizontal.liquid %}
      {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in categorized_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}

  {% endfor %}

{% else %}

  <!-- Display projects without categories -->

  {% assign visible_projects = site.projects | where_exp: "p", "p.hidden != true" %}
  {% assign sorted_projects = visible_projects | sort: "importance" %}

  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
      {% for project in sorted_projects %}
        {% include projects_horizontal.liquid %}
      {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}

{% endif %}

</div>