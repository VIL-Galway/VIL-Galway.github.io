---
layout: page
title: Publications
permalink: /publications/
nav: true
nav_order: 2
---

<div class="publications">

  <!-- FEATURED -->
  <h2>Featured Publications</h2>
  <div class="pub-grid">
    {% bibliography --query @*[selected=true] %}
  </div>

  <!-- ALL -->
  <h2>All Publications</h2>
  <div class="pub-list">
    {% bibliography %}
  </div>

</div>