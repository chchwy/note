---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
title: Welcome
---

<input type="text" placeholder="Search..">

{% for pg in site.notes %}
  <h1 id="{{ pg.anchor }}">{{ pg.title }}</h1>
  <section class="note-content">
    {{ pg.content | markdownify }}
  </section>
  <br>
  <hr>
  <br>
{% endfor %}
