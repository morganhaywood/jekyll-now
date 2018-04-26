---
layout: page
title: Posts by Tag
permalink: /tags/
---

Here's some text!

{% assign rawtags = "" %}{% for post in site.posts %}{% assign posttags = post.tags | join:'|' | append:'|' %}{% assign rawtags = alltags | append:posttags %}{% endfor %}{% assign rawtags = rawtags | split:'|' | sort %}{% for tag in rawtags %}## {{tag}}

{% for post in site.posts %}{% if post.tags contains tag %}[{{post.title}}]({{site.url}}{{ post.url }})

{% endif %}{% endfor %}{% endfor %}


