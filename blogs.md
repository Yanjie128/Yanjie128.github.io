---
layout: single
title: "Blogs"
permalink: /blogs/
---

# 📚 My blog

{% for post in site.posts %}

### [{{ post.title }}]({{ post.url }})

🗓 {{ post.date | date: "%Y-%m-%d" }}

{{ post.excerpt }}

---

{% endfor %}