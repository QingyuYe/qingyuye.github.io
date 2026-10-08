---
layout: default
title: Tags
permalink: /tags/
hide_sidebar: true
---

<section class="tags-directory">

  <h1 class="page-title">Tags</h1>

  <p class="tags-description">
    按主题整理的科研笔记与文章归档。
  </p>

  {% assign sorted_tags = site.tags | sort %}

  <div class="tag-index">

    {% for entry in sorted_tags %}

      <a href="#tag-{{ forloop.index }}">
        # {{ entry[0] | escape }}
      </a>

    {% endfor %}

  </div>

  {% for entry in sorted_tags %}

    {% assign tag_name = entry[0] %}
    {% assign tag_posts = entry[1] %}

    <section class="tags-directory-group"
             id="tag-{{ forloop.index }}">

      <h2>
        # {{ tag_name | escape }}
        <span class="tag-count">{{ tag_posts.size }}</span>
      </h2>

      <ul class="directory-post-list">

        {% for post in tag_posts %}

          <li>

            <span class="type-badge">
              {{ post.type | default: '未分类' | escape }}
            </span>

            <a href="{{ post.url | relative_url }}">
              {{ post.title | escape }}
            </a>

            <time datetime="{{ post.date | date: '%Y-%m-%d' }}">
              {{ post.date | date: '%Y-%m-%d' }}
            </time>

          </li>

        {% endfor %}

      </ul>

    </section>

  {% endfor %}

</section>
