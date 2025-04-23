---
layout: page
icon: fas fa-project-diagram
title: Projects
order: 2
---

# Our Supported Projects

The SPWF Foundation is proud to support the following worthwhile projects and charitable initiatives:

{% assign projects = site.projects | sort: 'date' | reverse %}
{% if projects.size > 0 %}
<div class="projects-grid">
  {% for project in projects %}
  <div class="project-card">
    <a href="{{ project.url | relative_url }}" class="project-link">
      {% if project.image %}
      <div class="project-image">
        <img src="{{ project.image | relative_url }}" alt="{{ project.title }}">
      </div>
      {% endif %}
      <div class="project-details">
        <h3 class="project-title">{{ project.title }}</h3>
        {% if project.description %}
        <p class="project-description">{{ project.description }}</p>
        {% endif %}
      </div>
    </a>
  </div>
  {% endfor %}
</div>
{% else %}
<p>No projects have been added yet. Check back soon!</p>
{% endif %}