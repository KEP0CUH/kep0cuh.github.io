---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
---
<div class="home">
  <h1 class="post-heading">Основное</h1>
  <ul class="post-list">
    {% include course_item.html permalink='/ps1/' %}
    {% include course_item.html permalink='/opengl/' %}
    {% include course_item.html permalink='/compilers/' %}
    {% include course_item.html permalink='/opr_js/' %}
    {% include course_item.html permalink='/opr_cxx/' %}
<!--     {% include course_item.html permalink='/os/' %} -->
    {% include course_item.html permalink='/resume/' %}
    {% include course_item.html permalink='/resume/pages/' %}
    {% include course_item.html permalink='/pages/' %}
  </ul>
  <h1 class="post-heading">Разное</h1>
  <ul class="post-list">
    {% include course_item.html permalink='/js/' %}
    {% include course_item.html permalink='/cxx/' %}
    {% include course_item.html permalink='/sfml/' %}
  </ul>
</div>