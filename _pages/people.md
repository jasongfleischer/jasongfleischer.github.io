---
layout: page
title: people
permalink: /people/
description: the people who have all the research fun!
nav: true
display_categories: [research undergraduates, alumni]
horizontal: false
---
<div class="people">
  {% if site.enable_people_categories and page.display_categories %}
  <!-- Display categorized people -->
    {% for category in page.display_categories %}
      <h2 class="category">{{category}}</h2>
      {% assign categorized_people = site.people | where: "category", category %}
      {% assign sorted_people = categorized_people | sort: "importance" %}
      <!-- Generate cards for each people -->
      {% if page.horizontal %}
        <div class="container">
          <div class="row row-cols-2">
          {% for people in sorted_people %}
            {% include people_horizontal.html %}
          {% endfor %}
          </div>
        </div>
      {% else %}
        <div class="grid">
          {% for people in sorted_people %}
            {% include people.html %}
          {% endfor %}
        </div>
      {% endif %}
    {% endfor %}

  {% else %}
  <!-- Display people without categories -->
    {% assign sorted_people = site.people | sort: "importance" %}
    <!-- Generate cards for each people -->
    {% if page.horizontal %}
      <div class="container">
        <div class="row row-cols-2">
        {% for people in sorted_people %}
          {% include people_horizontal.html %}
        {% endfor %}
        </div>
      </div>
    {% else %}
      <div class="grid">
        {% for people in sorted_people %}
          {% include people.html %}
        {% endfor %}
      </div>
    {% endif %}

  {% endif %}

</div>
