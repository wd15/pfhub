---
layout: essay
title: Test Wiki
comment: Testing a wiki
published: true
---

{% assign len = page.url | size | minus: 1 %}
{% assign file_path = page.url | truncate: len, "" | append: ".md" %}

[edit this page]({{ site.prose_base }}{{ file_path }})

Here is some text, which I have added.