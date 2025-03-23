---
title: Wiki
layout: default
permalink: wiki
---

# Wiki

<table class="wikilinks">
  {% for file in site.html_pages %}
    {% if file.url contains '/wiki/' %}
      <tr>
        <td>{{ file.dir }}</td>
        <td><a href="{{ file.url | relative_url }}">
          {{ file.title }}
        </a></td>
        <td>{{ file.excerpt }}</td>
      </tr>
    {%endif %}
  {% endfor %}
</table>
