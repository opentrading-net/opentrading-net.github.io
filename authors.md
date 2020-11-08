---
title: Authors
feature_image: "assets/feature_images/kristen-macadams-9FuMXAwBa0Y-unsplash.jpg"
excerpt: "The blog authors"
aside: true
---

<ul>
  {% for author in site.authors %}
      <h3>{{ author.name }}</h3>
      <p>{{ author.content | markdownify }}</p>
  {% endfor %}
</ul>