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
      <a href="#" class="card-title">{{ project.title }}</a>

      <p class="card-desc">
        {{ project.description }}
      </p>

      <div class="card-links">
        <a href="#">{{ project.status }}</a>
      </div>

      <div class="skill-icons">
        {% for skill in project.skills %}
          <div class="skill-badge">
            <span>{{ skill }}</span>
          </div>
        {% endfor %}
      </div>
    </div>

  </div>

{% endfor %}

</div>
