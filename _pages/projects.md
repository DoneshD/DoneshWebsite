---
layout: page
title: Portforlio
permalink: /projects/
description: An expanding collection of my game projects.
nav: true
nav_order: 3
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
  {% assign categorized_projects = site.projects | where: "category", category %}
  {% assign sorted_projects = categorized_projects | sort: "importance" %}
  <!-- Generate cards for each project -->
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
  {% endfor %}

{% else %}

<!-- Display projects without categories -->

{% assign sorted_projects = site.projects | sort: "importance" %}

  <!-- Generate cards for each project -->

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

<div style="display: flex; flex-wrap: wrap; gap: 2rem; margin-top: 1.5rem;"> 
<div style="flex: 1; min-width: 250px;"> <h3>Contributions</h3> <ul> 
<li>Implemented a custom combo system supporting chaining and branching inspired by DMC and Metal Gear Rising</li> 
<li>Created a weapon-centric character architecture where each equipped weapon dynamically define the players playstyle</li> 
<li>Engineered a AI system inspired by DOOM-style token system to enable a one-vs-many feeling</li> </ul> </div> 

<div style="flex: 1; min-width: 250px;"> <h3>Technical Features</h3> <ul> 
<li>Uses a custom Gameplay Ability System framework in C++ to use Unreal Engine data structures, such as data assets, UObjects, and gameplay tags for a data-driven ability architecture</li> 
<li>Utilizes Unreal Engine's State Trees for modular AI behavior capable of scaling as new attack patterns emerge and grow</li> 
<li>Built primarily with Unreal Engine C++, hosted with a Perforce Server and backup with Git Version Control</li> 
