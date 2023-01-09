---
layout: default
title: Home
nav_order: 1
description: " Cкоро здесь будет город-сад!"
permalink: /
---

А пока почитайте это:
<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
