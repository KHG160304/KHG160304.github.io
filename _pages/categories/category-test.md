---
title: "test"
layout: archive
permalink: /categories/test
---


{% assign posts = site.categories.test %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}