---
layout: default
title: "Members"
---

{% include page-intro.html %}

<style>
.members-container {
  display: flex;
  justify-content: center;
  align-items: center;
}
.member {
  text-align: center;
  margin: 0 20px;
}
.member img {
  margin-bottom: 20px; /* Added margin between image and name */
  transition: transform 0.3s ease-in-out, box-shadow 1s ease-in-out;
}
.member img:hover {
  transform: scale(1.1); /* Enlarge the image on hover */
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
}
.member p {
  margin-bottom: 5px;
}
.member .buttons {
  display: flex;
  justify-content: center;
}
.member .buttons a {
  margin: 5px;
  padding: 10px 15px;
  border: 1px solid #ccc;
  border-radius: 5px;
  text-decoration: none;
  color: #333;
}
</style>

<main id="main" class="page-content" aria-label="Content">

  <div class="index inner">

    <h2>Faculty</h2>
    <div class="members-container">
    {% for member in site.data.members %}
      {% if member.level == 'Faculty' %}
        <div class="member">
          <img src="assets/images/{{ member.photo }}" alt="{{ member.name }} photo" style="width: 200px; height: 200px; object-fit: cover; object-position: center; border-radius: 50%;">
          <p>{{ member.name }}</p>
        </div>
      {% endif %}
    {% endfor %}
    </div>

    <h2>Researchers</h2>
    <div class="members-container">
    {% for member in site.data.members %}
      {% if member.level == 'Researcher' %}
        <div class="member">
          <img src="assets/images/{{ member.photo }}" alt="{{ member.name }} photo" class="circle-image" style="width: 200px; height: 200px; object-fit: cover; object-position: center; border-radius: 50%;">
          <p>{{ member.name }}</p>
        </div>
      {% endif %}
    {% endfor %}
    </div>

    <h2>PhD Students</h2>
    <div class="members-container">
    {% for member in site.data.members %}
      {% if member.level == 'PhD Student' %}
        <div class="member">
          <img src="assets/images/{{ member.photo }}" alt="{{ member.name }} photo" class="circle-image" style="width: 200px; height: 200px; object-fit: cover; object-position: center; border-radius: 50%;">
          <p>{{ member.name }}</p>
        </div>
      {% endif %}
    {% endfor %}
    </div>

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
