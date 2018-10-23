---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
title: Welcome
---

{% for pg in site.notes %}
  <h1 id="{{ pg.anchor }}" class="note-title">{{ pg.title }}</h1>
  <div class="note-content">
    {{ pg.content | markdownify }}
  </div>
  
  <div class="note-footer">
  <hr>
  </div>
{% endfor %}
