---
layout: default
title: Welcome
---

# 👋 Welcome to My Coding Quiz Blog

Here you'll find my personal notes and solutions for various coding quizzes.

# 💼 Coding Quiz Notes

Welcome! Here’s a list of all coding quizzes I’ve written up, organized by company and position:

---

<ul>
  {% for post in site.posts %}
    {% assign parts = post.title | split: "-" %}
    {% assign company = parts[0] | strip %}
    {% assign position = parts[1] | strip %}
    <li>
      <a href="{{ post.url }}">
        {{ company }} – {{ position | default: "Unknown Role" }} ({{ post.date | date: "%Y-%m-%d" }})
      </a>
    </li>
  {% endfor %}
</ul>
