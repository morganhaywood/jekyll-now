---
layout: page
title: Learnings
permalink: /learnings/
---

{% for post in site.posts %}{% for tag in post.tags}{% if tag == "learnings" %}[{{ post.title }}]({{site.url}}{{ post.url }})

{% endif %}{% endfor %}{% endfor %}
