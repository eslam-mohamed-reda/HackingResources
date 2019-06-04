---
layout: page
title: "Contact"
meta_title: "Contact Us"
subheadline: ""
teaser: "We are open to any additions, any articles or any suggestions, Get in touch with us"
permalink: "/contact/"
---
<form id="formaction" method="POST">
    <p>Name: </p><textarea type="text" name="name" style="resize:none;"></textarea><br />
	<p>Message: </p><textarea type="text" name="Message" style="resize:none; height:200px; width:400px;"></textarea><br />
    <p>Email: </p><textarea type="email" name="email" style="resize:none;"></textarea><br />
	<input type="hidden" name="_next" value="/thanks" />
	<input type="text" name="_gotcha" style="display:none" />
    <input type="submit" value="Send">
</form>
<script>
    var contactform =  document.getElementById('formaction');
    contactform.setAttribute('action', '//formspree.io/' + 'resourceshacking' + '@' + 'gmail' + '.' + 'com');
</script>