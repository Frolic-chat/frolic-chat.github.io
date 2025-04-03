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
  {% for file in site.html_pages %}
    {% if file.url contains '/wiki/' %}
      <tr>{% assign folder = file.dir | remove: '/wiki/' %}{% assign length = folder | size | minus: 1 %}
        <td>{{ folder | slice: 0, length | capitalize }}</td>
        <td><a href="{{ file.url | relative_url }}">
          {{ file.title }}
        </a></td>
        <td>{{ file.excerpt }}</td>
      </tr>
    {%endif %}
  {% endfor %}
</table>
