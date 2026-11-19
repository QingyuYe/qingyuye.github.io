---
layout: page
title: "Resources"
permalink: /resources/
---

{% assign resource_files = site.static_files | sort: "path" | reverse %}
<ul>
{% for file in resource_files %}
  {% assign asset_path = file.path | downcase %}
  {% assign ext = file.extname | downcase %}
  {% if asset_path contains "assets/resources/" %}
    {% if ext == ".pdf" or ext == ".docx" %}
      {% assign filename = file.path | split: "/" | last %}
      {% assign date = filename | slice: 0, 10 %}
      {% assign title = filename | remove_first: date | remove_first: "-" | remove: ext | replace: "_", " " %}
      {% assign resource_url = "/assets/resources/" | append: filename %}

      {% if ext == ".docx" %}
        {% assign public_file_url = site.url | append: resource_url %}
        {% assign encoded_file_url = public_file_url | url_encode %}
        {% assign link_url = "https://view.officeapps.live.com/op/view.aspx?src=" | append: encoded_file_url %}
      {% else %}
        {% assign link_url = resource_url | relative_url %}
      {% endif %}

      <li>
        <time>{{ date }}</time> ·
        <a href="{{ link_url }}"{% if ext == ".docx" %} target="_blank" rel="noopener"{% endif %}>
          {{ title | escape }}
        </a>
      </li>
    {% endif %}
  {% endif %}
{% endfor %}
</ul>
