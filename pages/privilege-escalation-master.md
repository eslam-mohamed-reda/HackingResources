---
layout: page
title: "Privilege Escalation Master"
meta_title: "Master"
subheadline: "Privilege Escalation"
teaser: "Find an exploit"
header:
   image_fullwidth: "Red.jpg"
permalink: "/privesc-master"
---

{% include alert info='Windows' %}	

{% include alert warning='<a href="https://hacking-resources.com/privesc-master/windows-kernel"><strong>Search Kernel </strong>Exploits Here</a>' %}

{% include alert warning='<strong>Unquoted Service Path</strong><br>enumeration command:
<code>wmic service get name,displayname,pathname,startmode 2>nul |findstr /i "Auto" 2>nul |findstr /i /v "C:\Windows\\" 2>nul |findstr /i /v """</code><br><a href="https://hacking-resources.com/privesc-master/windows-unquoted">List of applications that will possibly have this issue click here </a>' %}

{% include alert terminal='Linux' %}

{% include alert warning='Coming Soon' %}





	
{% include share.html %}	
	
	
