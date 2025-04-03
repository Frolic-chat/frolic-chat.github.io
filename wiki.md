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
      <tr>
        <td>{{ file.dir | remove: '/wiki/' | remove_last: '/'  }}</td>
        <td><a href="{{ file.url | relative_url }}">
          {{ file.title }}
        </a></td>
        <td>{{ file.excerpt }}</td>
      </tr>
    {%endif %}
  {% endfor %}
</table>
