---
layout: page
title: Archive
---

{% for post in site.posts %}
       {% assign currentDate = post.date | date: "%Y" %}
       {% if currentDate != myDate %}
           ##{{ currentDate }}<br/>
           {% assign myDate = currentDate %}
       {% endif %}
       [{{ post.date | date: "%B %-d, %Y" }} - {{ post.title }}]({{site.url}}{{ post.url }})
{% endfor %}
