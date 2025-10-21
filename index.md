---
layout: page
title: Home
permalink: /
---

Welcome! Here’s a snapshot.

### Latest Blog Posts
<ul>
{% for post in site.posts limit:3 %}
  <li>
    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    — {{ post.date | date: "%b %d, %Y" }}
  </li>
{% endfor %}
</ul>

[All posts →]({{ '/blog/' | relative_url }})
