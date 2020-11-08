---
title: Authors
feature_image: "assets/feature_images/kristen-macadams-9FuMXAwBa0Y-unsplash.jpg"
excerpt: "The blog authors"
aside: true
---

<ul>
  {% for author in site.authors %}
    <li>
      <h2>{{ author.name }}</h2>
      <p>{{ author.content | markdownify }}</p>
    </li>
  {% endfor %}
</ul>