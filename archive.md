---
layout: page
title: Archive
---

{% for post in site.posts %}
       {% assign currentDate = post.date | date: "%Y" %}
       {% if currentDate != myDate %}
           {% unless forloop.first %}<br/>{% endunless %}
           ##{{ currentDate }}
           <br/>
           {% assign myDate = currentDate %}
       {% endif %}
       [{{ post.date | date: "%B %-d, %Y" }} - {{ post.title }}]{{ post.url }}
       {% if forloop.last %}<br/>{% endif %}
{% endfor %}
