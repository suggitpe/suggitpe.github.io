---
layout: page
title: Presentations
permalink: /presentations/
---

<ul>
{% assign talks = site.presentations | sort: "date" | reverse %}
{% for talk in talks %}
  <li>
    <a href="{{ talk.url | relative_url }}">{{ talk.title }}</a>
    {% if talk.event %} — {{ talk.event }}{% endif %}
    {% if talk.date %} ({{ talk.date | date: "%b %d, %Y" }}){% endif %}
  </li>
{% endfor %}
</ul>
