---
layout: page
title: Home
permalink: /
---

# 👋 Welcome

Hi, I’m **suggitpe** — I build things, break them (on purpose), and write about what I learn.  
This site collects my notes, talks, and experiments.

---

## 🧠 Latest Blog Posts
<ul>
{% for post in site.posts limit:3 %}
  <li>
    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    <span> — {{ post.date | date: "%b %d, %Y" }}</span>
  </li>
{% endfor %}
</ul>

👉 [See all blog posts →]({{ '/blog/' | relative_url }})

---

## 🎤 Recent Presenting
<ul>
{% assign talks = site.presenting | sort: "date" | reverse | slice: 0, 3 %}
{% for talk in talks %}
  <li>
    <a href="{{ talk.url | relative_url }}">{{ talk.title }}</a>
    {% if talk.event %}<span> — {{ talk.event }}</span>{% endif %}
    {% if talk.date %}<span> ({{ talk.date | date: "%b %Y" }})</span>{% endif %}
  </li>
{% endfor %}
</ul>

👉 [See all talks →]({{ '/presenting/' | relative_url }})

---

## 🍳 New Recipes
<ul>
{% assign recipes = site.recipes | sort: "title" | slice: 0, 3 %}
{% for r in recipes %}
  <li>
    <a href="{{ r.url | relative_url }}">{{ r.title }}</a>
  </li>
{% endfor %}
</ul>

👉 [See all recipes →]({{ '/recipes/' | relative_url }})

---

## 📫 About
Curious who’s behind all this? [Learn more about me →]({{ '/about/' | relative_url }})
