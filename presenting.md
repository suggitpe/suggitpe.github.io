---
layout: page
title: Presenting
permalink: /presenting/
---

<ul>
{% assign talks = site.presenting | sort: "date" | reverse %}
{% for talk in talks %}
  <li>
    <a href="{{ talk.url | relative_url }}">{{ talk.title }}</a>
    {% if talk.event %} — {{ talk.event }}{% endif %}
    {% if talk.date %} ({{ talk.date | date: "%b %d, %Y" }}){% endif %}
  </li>
{% endfor %}
</ul>
