---
layout: page
title: Recipes
permalink: /recipes/
---

Things I like to cook (or drink).

<ul>
{% assign items = site.recipes | sort: "title" %}
{% for r in items %}
  <li><a href="{{ r.url | relative_url }}">{{ r.title }}</a></li>
{% endfor %}
</ul>
