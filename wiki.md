---
title: Wiki
layout: default
permalink: wiki
---

# Wiki

<div class="wikilinks">
  {% assign wiki_pages = site.html_pages | where_exp: "page", "page.dir contains '/wiki/'" %}
  {% assign blank_pgs = wiki_pages | where_exp: "page", "page.dir == '/wiki/'" %}
  {% assign feature_pgs = wiki_pages | where_exp: "page", "page.dir == '/wiki/features/'" %}
  {% assign dev_pgs = wiki_pages | where_exp: "page", "page.dir == '/wiki/development/'" %}
  {% assign indev_pgs = wiki_pages | where_exp: "page", "page.dir == '/wiki/development/in-dev/'" %}

  {% for file in feature_pgs %}
    {% assign folder = file.dir | remove_first: '/wiki/' %}
    {% assign length = folder | size | minus: 1 %}
    <div>
      <h6>{{ folder | slice: 0, length | capitalize }}</h6>
      <h3><a href="{{ file.url | relative_url }}">
        {{ file.title }}
      </a></h3>
      <div>{{ file.excerpt }}</div>
    </div>
  {% endfor %}
  <br />

  {% for file in blank_pgs %}
    <div>
      <h6>&nbsp;</h6>
      <h3><a href="{{ file.url | relative_url }}">
        {{ file.title }}
      </a></h3>
      <div>{{ file.excerpt }}</div>
    </div>
  {% endfor %}
  <br />

  {% for file in dev_pgs %}
    {% assign folder = file.dir | remove_first: '/wiki/' %}
    {% assign length = folder | size | minus: 1 %}
    <div>
      <h6>{{ folder | slice: 0, length | capitalize }}</h6>
      <h3><a href="{{ file.url | relative_url }}">
        {{ file.title }}
      </a></h3>
      <div>{{ file.excerpt }}</div>
    </div>
  {% endfor %}
  <br />

  {% for file in indev_pgs %}
    {% assign folder = file.dir | remove_first: '/wiki/' %}
    {% assign length = folder | size | minus: 1 %}
    <div>
      <h6>{{ folder | slice: 0, length | capitalize }}</h6>
      <h3><a href="{{ file.url | relative_url }}">
        {{ file.title }}
      </a></h3>
      <div>{{ file.excerpt }}</div>
    </div>
  {% endfor %}
</div>
