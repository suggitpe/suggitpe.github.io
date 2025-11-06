---
layout: page
title: Recipes
permalink: /recipes/
---

{% assign grouped = site.recipes | group_by_exp: "item", "item.relative_path | split: '/' | slice: 1, 1 | first" %}

{% for group in grouped %}
{% assign folder = group.name %}
{% if folder != "" %}
<h2>{{ folder | capitalize }}</h2>
<ul>
{% for recipe in group.items %}
<li><a href="{{ recipe.url }}">{{ recipe.title }}</a></li>
{% endfor %}
</ul>
{% endif %}
{% endfor %}
