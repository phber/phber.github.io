---
layout: page
permalink: /creations/
title: creations
description: A list of some of my creative projects, such as compositions, performances and experiments. 
years: [2023]
nav: true
nav_order: 1
---
<!-- _pages/creations.md -->
<div class="publications">

{%- for y in page.years %}
  <h2 class="year">{{y}}</h2>
  {% bibliography -f {{ site.scholar.bibliography }} -q @*[year={{y}}]* %}
{% endfor %}

</div>
