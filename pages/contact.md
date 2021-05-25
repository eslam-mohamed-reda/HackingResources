---
layout: page
title: "Contact"
meta_title: "Contact Us"
subheadline: ""
teaser: "We are open to any additions, any articles or any suggestions, Get in touch with us"
permalink: "/contact/"
header: no
---
<form
  action="https://formspree.io/myynavjd"
  method="POST"
>
 <label>
    Name:
    <input type="text" name="name">
  </label>
 <label>
    Email:
    <input type="text" name="_replyto">
  </label>
  <label>
    Message:
    <textarea name="message" style="resize:none; height:200px; width:400px;"></textarea>
  </label>

<input type="hidden" name="_next" value="/thanks" />
<input type="text" name="_gotcha" style="display:none" />

  <button type="submit">Send</button>
</form>


{% include share.html %}
{% include chat.html %}