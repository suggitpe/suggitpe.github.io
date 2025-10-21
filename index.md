---
layout: default
title: Home
permalink: /
---

Welcome! Here’s a quick snapshot.

### Latest Blog Posts
{% assign latest_posts = site.posts | slice: 0, 3 %}
<ul>
  {% for post in latest_posts %}
    <li>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      <span>— {{ post.date | date: "%b %d, %Y" }}</span>
    </li>
  {% endfor %}
</ul>
<p><a href="{{ '/blog/' | relative_url }}">See all posts →</a></p>

### Recent Presentations
{% assign latest_talks = site.presentations | sort: "date" | reverse | slice: 0, 3 %}
<ul>
  {% for talk in latest_talks %}
    <li>
      <a href="{{ talk.url | relative_url }}">{{ talk.title }}</a>
      {% if talk.event %} — {{ talk.event }}{% endif %}
      {% if talk.date %} ({{ talk.date | date: "%b %Y" }}){% endif %}
    </li>
  {% endfor %}
</ul>
<p><a href="{{ '/presentations/' | relative_url }}">All presentations →</a></p>

### New Recipes
{% assign latest_recipes = site.recipes | sort: "title" | slice: 0, 3 %}
<ul>
  {% for r in latest_recipes %}
    <li><a href="{{ r.url | relative_url }}">{{ r.title }}</a></li>
  {% endfor %}
</ul>
<p><a href="{{ '/recipes/' | relative_url }}">All recipes →</a></p>
