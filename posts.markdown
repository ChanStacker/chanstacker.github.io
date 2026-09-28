---
layout: default
title: Posts
permalink: /posts/
---

{% assign posts_oldest_first = site.posts | reverse %}
{% assign posts_by_year = posts_oldest_first | group_by_exp: "post", "post.date | date: '%Y'" %}

<ul>
  {% for year in posts_by_year %}
    <li>
      <strong>{{ year.name }}</strong>
      <ul>
        {% for post in year.items %}
          <li>
            <a href="{{ post.url }}">{{ post.title }}</a>
          </li>
        {% endfor %}
      </ul>
    </li>
  {% endfor %}
</ul>
