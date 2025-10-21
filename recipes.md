---
layout: default
title: Recipes
permalink: /recipes/
---

# Recipes

<ul>
{% assign items = site.recipes | sort: "title" %}
{% for r in items %}
  <li><a href="{{ r.url | relative_url }}">{{ r.title }}</a></li>
{% endfor %}
</ul>
