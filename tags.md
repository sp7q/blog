---
layout: page
title: Tags
permalink: /tags/
---

**Tags:**
{% for tag in site.tags %}
  <a href="#tag-{{ tag[0] | slugify }}">{{ tag[0] }}</a> ({{ tag[1].size }}){% unless forloop.last %}, {% endunless %}
{% endfor %}

----

## Posts by tags

{% for tag in site.tags %}
  <h3 id="tag-{{ tag[0] | slugify }}">{{ tag[0] }}</h3>
  <ul>
    {% for post in tag[1] %}
      <li>
        <a href="{{ post.url }}">{{ post.title }}</a> 
        <small>({{ post.date | date: "%d.%m.%Y" }})</small>
      </li>
    {% endfor %}
  </ul>
{% endfor %}
