---
layout: page
title: "Resources"
permalink: /resources/
---

{% assign resource_files = site.static_files | sort: "path" | reverse %}
<ul>
{% for file in resource_files %}
  {% assign asset_path = file.path | downcase %}
  {% if asset_path contains "assets/resources/" and file.extname == ".pdf" %}
    {% assign filename = file.path | split: "/" | last %}
    {% assign date = filename | slice: 0, 10 %}
    {% assign title = filename | remove_first: date | remove_first: "-" | remove: ".pdf" | replace: "_", " " %}
    {% assign pdf_path = "/assets/resources/" | append: filename %}
    <li><time>{{ date }}</time> · <a href="{{ pdf_path | relative_url }}">{{ title | escape }}</a></li>
  {% endif %}
{% endfor %}
</ul>
