---
layout: page
title: Learnings
---

{% for post in site.posts %}{% for tag in post.tags}{% if tag == "learnings" %}[{{ post.title }}]({{site.url}}{{ post.url }})

{% endif %}

{% endfor %}
