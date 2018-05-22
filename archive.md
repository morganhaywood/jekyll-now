---
layout: page
title: Archive
permalink: /archive/
---

{% for post in site.posts %}{% assign currentDate = post.date | date: "%B %Y" %}{% if currentDate != myDate %}### {{ currentDate }}

{% assign myDate = currentDate %}{% endif %}[{{ post.date | date: "%Y-%m-%d" }} : {{ post.title }}]({{site.url}}{{ post.url }})

{% endfor %}
