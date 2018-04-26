---
layout: page
title: Posts by Tag
permalink: /tags/
---

{% assign rawtags = "" %}{% for post in site.posts %}{% assign posttags = post.tags | join:'|' | append:'|' %}{% assign rawtags = rawtags | append:posttags %}{% endfor %}{% assign rawtags = rawtags | split:'|' | sort %}{% assign tags = "" %}{% for tag in rawtags %}{% if tag != "" %}{% if tags == "" %}{% assign tags = tag | split:'|' %}{% endif %}{% unless tags contains tag %}{% assign tags = tags | join:'|' | append:'|' | append:tag | split:'|' %}{% endunless %}{% endif %}{% endfor %}{% for tag in tags %}## {{tag}}

{% endfor %}


