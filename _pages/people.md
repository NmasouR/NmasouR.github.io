---
layout: page
title: people
permalink: /people/
description: members of the lab or group
nav: true
nav_order: 3
display_categories: [cat1, cat2]
horizontal: false
---

<!-- pages/people.md -->
<div class="people">
{% if site.enable_people_categories and page.display_categories %}
  <!-- Display categorized people -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_people = site.people | where: "category", category %}
  {% assign sorted_people = categorized_people | sort: "importance" %}
  <!-- Generate cards for each person -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for person in sorted_people %}
      {% include people_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for person in sorted_people %}
      {% include people.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display people without categories -->

{% assign sorted_people = site.people | sort: "importance" %}

  <!-- Generate cards for each person -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for person in sorted_people %}
      {% include people_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for person in sorted_people %}
      {% include people.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>
