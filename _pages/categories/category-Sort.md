---
title: "정렬"
layout: archive
permalink: categories/Sort
author_profile: true
sidebar:
    nav: "[Sort]"
---


{% assign posts = site.categories.Sort %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}
