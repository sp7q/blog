---
layout: page
title: Categories
permalink: /categories/
---

**Categories:**
{% for category in site.categories %}
  <a href="#cat-{{ category[0] | slugify }}">{{ category[0] }}</a> ({{ category[1].size }}){% unless forloop.last %}, {% endunless %}
{% endfor %}

----------------------

## Posts by categories

{% for category in site.categories %}
  <!-- Nagłówek z unikalnym ID, do którego skacze link z góry strony -->
  <h3 id="cat-{{ category[0] | slugify }}">{{ category[0] }}</h3>
  <ul>
    {% for post in category[1] %}
      <li>
        <a href="{{ post.url }}">{{ post.title }}</a> 
        <small>({{ post.date | date: "%d.%m.%Y" }})</small>
      </li>
    {% endfor %}
  </ul>
{% endfor %}

