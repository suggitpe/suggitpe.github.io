---
layout: page
title: Home
permalink: /
---

Welcome — I’m **Pete**. I build things, break them (on purpose), and write about what I learn.

### Latest Blog Posts
<ul>
{% for post in site.posts limit:3 %}
  <li><a href="{{ post.url | relative_url }}">{{ post.title }}</a> — {{ post.date | date: "%b %d, %Y" }}</li>
{% endfor %}
</ul>
[All posts →]({{ '/blog/' | relative_url }})

### Recent Presenting
<ul>
{% assign talks = site.presenting | sort: "date" | reverse | slice: 0, 3 %}
{% for talk in talks %}
  <li>
    <a href="{{ talk.url | relative_url }}">{{ talk.title }}</a>
    {% if talk.event %} — {{ talk.event }}{% endif %}
    {% if talk.date %} ({{ talk.date | date: "%b %Y" }}){% endif %}
  </li>
{% endfor %}
</ul>
[All talks →]({{ '/presenting/' | relative_url }})

### New Recipes
<ul>
{% assign rs = site.recipes | sort: "title" | slice: 0, 3 %}
{% for r in rs %}
  <li><a href="{{ r.url | relative_url }}">{{ r.title }}</a></li>
{% endfor %}
</ul>
[All recipes →]({{ '/recipes/' | relative_url }})
