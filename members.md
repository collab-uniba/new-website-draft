---
layout: default
title: "Members"
---

<main id="main" class="page-content" aria-label="Content">
  <div class="index inner">

    <h2>Faculty</h2>
    {% for member in site.data.members %}
      {% if member.level == 'Faculty' %}
        <div>
          <img src="assets/images/{{ member.photo }}" alt="{{ member.name }} photo">
          <p>{{ member.name }}</p>
        </div>
      {% endif %}
    {% endfor %}

    <h2>Researchers</h2>
    {% for member in site.data.members %}
      {% if member.level == 'Researcher' %}
        <div>
          <img src="assets/images/{{ member.photo }}" alt="{{ member.name }} photo">
          <p>{{ member.name }}</p>
        </div>
      {% endif %}
    {% endfor %}

    <h2>PhD Students</h2>
    {% for member in site.data.members %}
      {% if member.level == 'PhD Student' %}
        <div>
          <img src="assets/images/{{ member.photo }}" alt="{{ member.name }} photo">
          <p>{{ member.name }}</p>
        </div>
      {% endif %}
    {% endfor %}

    {% if page.title == 'Home' and site.posts.size > 0 %}
      <div>
        <header class="section-title">
          <h2>{{ site.data.theme.t.posts | default: 'Posts' }}{% if paginator.page > 1 %}{{ site.data.theme.t.page | default: 'Page' | prepend: ' - ' | append: ' ' }}{{ paginator.page }} {{ site.data.theme.t.of | default: 'of' }} {{ paginator.total_pages }}{% endif %}</h2>
        </header>
        <div class="entries-{{ page.entries_layout | default: 'list' }}">
          {% if site.plugins contains 'jekyll-paginate' and page.paginate or site.gems contains 'jekyll-paginate' and page.paginate %}
            {% comment %}
              Add paginator.posts loop if jekyll-paginate plugin is enabled
              and page.paginate == true
            {% endcomment %}
            {% include posts-paginated.html %}
          {% else %}
            {% include posts-all.html %}
          {% endif %}
        </div>
      </div>
    {% endif %}
  </div>
</main>
