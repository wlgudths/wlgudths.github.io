---
title: "Shooting"
layout: archive
permalink: categories/shooting
author_profile: true
sidebar_main: true
---

## 제목 규칙

- [기술명 / 도구명] : Issue 요약

### 예시

- **`[Pytorch]` : Model Fails to Converge**

- **`[Python]` : TypeError in Data Processing Script**


<br>

{% assign posts = site.categories.Shooting %}
{% for post in posts %} {% include archive-single2.html type=page.entries_layout %} {% endfor %}
