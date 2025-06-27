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

  {% assign wiki_pages = site.html_pages | where_exp: "page", "page.url | slice: 0, 6 == '/wiki/'" %}

  {% for file in wiki_pages | where: "page", "page.dir == '/wiki/'" %}
    <tr>
      <td>&nbsp;</td>
      <td><a href="{{ file.url | relative_url }}">
        {{ file.title }}
      </a></td>
      <td>{{ file.excerpt }}</td>
    </tr>
  {% endfor %}
  <tr></tr>
  {% for file in wiki_pages | where: "page", "page.dir == '/wiki/features/'" %}
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
  {% for file in wiki_pages | where: "page", "page.dir == '/wiki/development/'" %}
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
  {% for file in wiki_pages | where: "page", "page.dir == '/wiki/development/in-dev'" %}
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
