---
layout: page
title: "Hangar"
permalink: /models/
---

My models

<ul>
  {% for plane in site.planes %}
    <li>
      <a href="{{ plane.url }}">{{ plane.title }}</a>
      <!-- Możesz tu wyciągnąć dodatkowe dane z Front Matter, np.: -->
      <!-- <small>(Rozpiętość: {{ plane.rozpietosc }})</small> -->
    </li>
  {% endfor %}
</ul>
