---
layout: archive
title:  "깃허브 블로그 포스팅하는 방법"
excerpt: "md 파일에 마크다운 문법으로 작성하여 Github 원격 저장소에 업로드 해보자. 에디터는 Visual Studio code 사용! 로컬 서버에서 확인도 해보자. "
permalink: /categories/GitHub Blog
categories:
  - Blog
tags:
  - [Blog, jekyll, Github, Git]
toc: true
toc_sticky: true
date: 2021-06-01
last_modified_at: 2021-06-01
---

첫 게시물 등록

{% for category in site.categories %}
  {% if category[0] == "GitHub Blog" %}
    {% for post in category[1] %}
      {% include archive-single.html type=list %}
    {% endfor %}
  {% endif %}  
{% endfor %}