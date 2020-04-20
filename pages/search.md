---
permalink: /search/
layout: page
title: "Search"
sitemap: false
---



<h3>Search on Hacking Resources blog</h3>
<form action="/search" method="get">
  <input type="text" id="search-box" name="query">
  <input type="submit" value="search">
</form>

<ul id="search-results"></ul>

<script>
  window.store = {
    {% for post in site.posts %}
      "{{ post.url | slugify }}": {
        "title": "{{ post.title | xml_escape }}",
        "author": "{{ post.author | xml_escape }}",
        "category": "{{ post.category | xml_escape }}",
        "content": {{ post.content | strip_html | strip_newlines | jsonify }},
        "url": "{{ post.url | xml_escape }}"
      }
      {% unless forloop.last %},{% endunless %}
    {% endfor %}
  };
</script>
<script src="../assets/js/lunr.min.js"></script>
<script src="../assets/js/search.js"></script>

<h3>Search on Google</h3>
{% include _google_search.html %}
