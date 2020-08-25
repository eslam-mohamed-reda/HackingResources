---
layout: page
show_meta: false
title: "Sections"
subheadline: "Explore"
teaser: ""
permalink: "/sections/"
---

<html>
<style>
.btn-group button {
  background-color: #4CAF50; /* Green background */
  border: 1px solid green; /* Green border */
  color: white; /* White text */
  padding: 10px 24px; /* Some padding */
  cursor: pointer; /* Pointer/hand icon */
  width: 50%; /* Set a width if needed */
  display: block; /* Make the buttons appear below each other */
}

.btn-group button:not(:last-child) {
  border-bottom: none; /* Prevent double borders */
}

/* Add a background color on hover */
.btn-group button:hover {
  background-color: #3e8e41;
}
</style>
<div class="btn-group">
  <button><a href="{{ site.url }}/Red-Team.html">Red Team</a></button>
  <button><a href="{{ site.url }}/Blue-Team-Arsenal.html">Blue Team</a></button>
  <button><a href="{{ site.url }}/Web-Applications-Security.html">Web</a></button>
  <button><a href="{{ site.url }}/Android-Applications-Security.html">Android</a></button>
  <button><a href="{{ site.url }}/security-awareness.html">Awareness</a></button>
</div>
</html>

{% include share.html %}
{% include chat.html %}