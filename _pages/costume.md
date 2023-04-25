---
layout: page
permalink: /costume/
title: costume
# description: Materials for courses you taught. Replace this text with your description.
nav: false
nav_order: 5
display_categories: [theatre, musical, tv]
horizontal: false
---

<!-- pages/costume.md -->
<div class="costume">
{%- if site.enable_costume_categories and page.display_categories %}
  <!-- Display categorized costume -->
  {%- for category in page.display_categories %}
  <h2 class="category">{{ category }}</h2>
  {%- assign categorized_costume = site.costume | where: "category", category -%}
  {%- assign sorted_costume = categorized_costume | sort: "importance" %}
  <!-- Generate cards for each costume -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for costume in sorted_costume -%}
      {% include costume_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for costume in sorted_costume -%}
      {% include costume.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
  {% endfor %}

{%- else -%}
<!-- Display costume without categories -->
  {%- assign sorted_costume = site.costume | sort: "importance" -%}
  <!-- Generate cards for each costume -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for costume in sorted_costume -%}
      {% include costume_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for costume in sorted_costume -%}
      {% include costume.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
{%- endif -%}
</div>
