---
layout: page
title: "hello lepffm public"
permalink: /
---
# branch : gh_pages from proposal
# blog
<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }} {{ post.categories}} {{ post.date}} </a>
    </li>
  {% endfor %}
</ul>
