---
layout: page
title: Blog Archive
---

{% assign postsByYear = site.posts | group_by_exp:"post", "post.date | date: '%Y'" %}
{% assign sortedPostsByYear = postsByYear | sort: "name" | reverse %}

{% for year in sortedPostsByYear %}
  <h2>{{ year.name }}</h2>
  <ul>
    {% assign sortedPosts = year.items | sort: "date" | reverse %}
    {% for post in sortedPosts %}
      <li><a href="{{ post.url }}">{{ post.date | date: "%B" }} - {{ post.title }}</a></li>
    {% endfor %}
  </ul>
{% endfor %}