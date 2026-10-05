---
layout: page
title: "RadioShack"
permalink: /radios/
---

My radio shack equipment

<ul>
  {% for radio in site.radios %}
    <li>
      <a href="{{ radio.url }}">{{ radio.title }}</a>
    </li>
  {% endfor %}
</ul>
