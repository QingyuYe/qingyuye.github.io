---
layout: page
title: "资料"
permalink: /resources/
---

{% assign resource_files = site.static_files | sort: "path" | reverse %}
{% for file in resource_files %}
  {% assign asset_path = file.path | downcase %}
  {% if asset_path contains "assets/resources/" and file.extname == ".pdf" %}
    {% assign filename = file.path | split: "/" | last %}
    {% assign date = filename | slice: 0, 10 %}
    {% assign title = filename | remove_first: date | remove_first: "-" | remove_last: ".pdf" %}
    {% assign pdf_path = "/assets/resources/" | append: filename %}
- {{ date }} · [{{ title }}]({{ pdf_path | relative_url }})
  {% endif %}
{% endfor %}
