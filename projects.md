---
layout: default
title: Projects
---

# Selected Projects

A visual collection of my research implementations, software tools, and technical experiments.

<div class="project-grid">
{% for project in site.data.projects %}

  <div class="project-card">

    <div class="thumbnail-container">
      {% if project.video %}
        <video autoplay loop muted playsinline>
          <source src="{{ project.video }}" type="video/mp4">
        </video>
      {% else %}
        <img src="{{ project.image }}" alt="{{ project.title }}">
      {% endif %}
    </div>

    <div class="card-content">

      <div class="card-title">
        {{ project.title }}
      </div>

      <p class="card-desc">
        {{ project.description }}
      </p>

      <div class="card-links">
        <span class="status">{{ project.status }}</span>
      </div>

      <div class="skill-icons">
        {% for skill in project.skills %}
          <div class="skill-badge">
            {% if skill.icon contains "/" %}
              <img src="{{ skill.icon }}" class="skill-icon">
            {% else %}
              <i class="devicon-{{ skill.icon }}-plain"></i>
            {% endif %}
            <span>{{ skill.name }}</span>
          </div>
        {% endfor %}
      </div>

    </div>

  </div>

{% endfor %}
</div>
