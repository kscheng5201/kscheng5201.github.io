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
    {% assign parts = post.title | split: "_" %}
    {% assign company = parts[0] %}
    {% assign position = parts[1] | default: "Unknown Role" %}
    <li>
      <a href="{{ post.url }}">
        <strong>{{ company }}</strong> – {{ position }}
      </a>
      <small>({{ post.date | date: "%Y-%m-%d" }})</small>
    </li>
  {% endfor %}
</ul>
