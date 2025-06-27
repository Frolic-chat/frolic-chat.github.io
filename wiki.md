---
title: Wiki
layout: default
permalink: wiki
---

# Wiki

<table class="wikilinks">
  <tr>
    <th>Category</th>
    <th>Page</th>
    <th>About</th>
  </tr>

  {% assign wiki_pages = site.html_pages | where_exp: "page", "page.dir contains '/wiki/'" %}
  {% assign blank_pgs = wiki_pages | where_exp: "page", "page.dir == '/wiki/'" %}
  {% assign feature_pgs = wiki_pages | where_exp: "page", "page.dir == '/wiki/features/'" %}
  {% assign dev_pgs = wiki_pages | where_exp: "page", "page.dir == '/wiki/development/'" %}
  {% assign indev_pgs = wiki_pages | where_exp: "page", "page.dir == '/wiki/development/in-dev/'" %}

  {% for file in feature_pgs %}
    {% assign folder = file.dir | remove_first: '/wiki/' %}
    {% assign length = folder | size | minus: 1 %}
    <tr>
      <td>{{ folder | slice: 0, length | capitalize }}</td>
      <td><a href="{{ file.url | relative_url }}">
        {{ file.title }}
      </a></td>
      <td>{{ file.excerpt }}</td>
    </tr>
  {% endfor %}
  <tr></tr>

  {% for file in blank_pgs %}
    <tr>
      <td>&nbsp;</td>
      <td><a href="{{ file.url | relative_url }}">
        {{ file.title }}
      </a></td>
      <td>{{ file.excerpt }}</td>
    </tr>
  {% endfor %}
  <tr></tr>

  {% for file in dev_pgs %}
    {% assign folder = file.dir | remove_first: '/wiki/' %}
    {% assign length = folder | size | minus: 1 %}
    <tr>
      <td>{{ folder | slice: 0, length | capitalize }}</td>
      <td><a href="{{ file.url | relative_url }}">
        {{ file.title }}
      </a></td>
      <td>{{ file.excerpt }}</td>
    </tr>
  {% endfor %}
  <tr></tr>

  {% for file in indev_pgs %}
    {% assign folder = file.dir | remove_first: '/wiki/' %}
    {% assign length = folder | size | minus: 1 %}
    <tr>
      <td>{{ folder | slice: 0, length | capitalize }}</td>
      <td><a href="{{ file.url | relative_url }}">
        {{ file.title }}
      </a></td>
      <td>{{ file.excerpt }}</td>
    </tr>
  {% endfor %}
</table>
