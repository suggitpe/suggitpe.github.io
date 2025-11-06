---
layout: page
title: Recipes
permalink: /recipes/
---



<h2>Boozey Stuff</h2>
<ul>
{% assign items = site.recipes.boozey | sort: "title" %}
{% for r in items %}
  <li><a href="{{ r.url | relative_url }}">{{ r.title }}</a></li>
{% endfor %}
</ul>




<ul>
{% assign items = site.recipes | sort: "title" %}
{% for r in items %}
  <li><a href="{{ r.url | relative_url }}">{{ r.title }}</a></li>
{% endfor %}
</ul>
