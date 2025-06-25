---
layout: default
title: Welcome
---

# 👋 Welcome to My Coding Quiz Blog

Here you'll find my personal notes and solutions for various coding quizzes.

# 📝 All Quizzes

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a> - {{ post.date | date: "%b %-d, %Y" }}
    </li>
  {% endfor %}
</ul>

