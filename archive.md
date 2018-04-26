---
layout: page
title: Archive
permalink: /archive/
---

Here is some text.

## Heading

here is some more text

## Start dynamic content

{% for post in site.posts %}{% assign currentDate = post.date | date: "%Y" %}{% if currentDate != myDate %}## {{ currentDate }}{% assign myDate = currentDate %}{% endif %}[{{ post.date | date: "%B %-d, %Y" }} - {{ post.title }}]({{site.url}}{{ post.url }}){% endfor %}
