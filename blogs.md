---
layout: single
title: "Blog"
permalink: /blogs/
classes: wide
---

这里整理了我已经发布的文章，内容以开发、工具使用和学习记录为主。

{% for post in site.posts %}
### [{{ post.title }}]({{ post.url }})

发布日期：{{ post.date | date: "%Y-%m-%d" }}

{{ post.excerpt }}

---
{% endfor %}
