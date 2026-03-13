---
layout: single
title: "Blogs"
permalink: /blogs/
---

# 📚 My blog

Below are my blog posts:

{% raw %}
{% for post in site.posts %}
### [{{ post.title }}]({{ post.url }})

🗓 {{ post.date | date: "%Y-%m-%d" }}

{{ post.excerpt }}

---

{% endfor %}
{% endraw %}