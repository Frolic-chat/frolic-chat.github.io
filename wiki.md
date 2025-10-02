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

  {% if feature_pgs.size > 0 %}
    {% assign folder = feature_pgs.first.dir | remove_first: '/wiki/' %}
    {% assign length = folder | size | minus: 1 %}
    <div class="wiki-section feature">
      <h2>{{ folder | slice: 0, length | capitalize }}</h2>
      {% for file in feature_pgs %}
        <div class="wiki-entry">
          <a class="header" href="{{ file.url | relative_url }}">
            <h3><span class="pepicons-chain"></span> {{ file.title }}</h3>
            <div>{{ file.excerpt }}</div>
          </a>
        </div>
      {% endfor %}
    </div>
  {% endif %}
  <br />

  {% if blank_pgs.size > 0 %}
    <div class="wiki-section blank">
      <h2>General</h2>
      {% for file in blank_pgs %}
        <div class="wiki-entry">
          <a class="header" href="{{ file.url | relative_url }}">
            <h3><span class="pepicons-chain"></span> {{ file.title }}</h3>
            <div>{{ file.excerpt }}</div>
          </a>
        </div>
      {% endfor %}
    </div>
  {% endif %}
  <br />

  {% if dev_pgs.size > 0 %}
    {% assign folder = dev_pgs.first.dir | remove_first: '/wiki/' %}
    {% assign length = folder | size | minus: 1 %}
    <div class="wiki-section dev">
      <h2>{{ folder | slice: 0, length | capitalize }}</h2>
      {% for file in dev_pgs %}
        <div class="wiki-entry">
          <a class="header" href="{{ file.url | relative_url }}">
            <h3><span class="pepicons-chain"></span> {{ file.title }}</h3>
            <div>{{ file.excerpt }}</div>
          </a>
        </div>
      {% endfor %}
    </div>
  {% endif %}
  <br />

  {% if indev_pgs.size > 0 %}
    {% assign folder = indev_pgs.first.dir | remove_first: '/wiki/' %}
    {% assign length = folder | size | minus: 1 %}
    <div class="wiki-section indev">
      <h2>{{ folder | slice: 0, length | capitalize }}</h2>
      {% for file in indev_pgs %}
        <div class="wiki-entry">
          <a class="header" href="{{ file.url | relative_url }}">
            <h3><span class="pepicons-chain"></span> {{ file.title }}</h3>
            <div>{{ file.excerpt }}</div>
          </a>
        </div>
      {% endfor %}
    </div>
  {% endif %}
</div>
