---
layout: page
title: Archive
permalink: /archive/
---

{% for post in site.posts %}{% assign currentDate = post.date | date: "%Y" %}{% if currentDate != myDate %}## {{ currentDate }}

{% assign myDate = currentDate %}{% endif %}[{{ post.date | date: "%B %-d, %Y" }} - {{ post.title }}]({{site.url}}{{ post.url }})<br/>{% endfor %}
