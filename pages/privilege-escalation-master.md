---
layout: page
title: "Privilege Escalation Master"
meta_title: "Privilege Escalation Master"
subheadline: "Find an Exploit"
teaser: "Here you will find a quick reference for Windows and Linux privilege escalation vulnerabilities within every type of vulnerability there's a link to database of vulnerbilities of that type to guide you quick to the right exploit."
header:
   image_fullwidth: "Red.jpg"
permalink: "/privesc-master"
---

{% include alert info='Windows' %}	

{% include alert warning='<a href="https://hacking-resources.com/privesc-master/windows-kernel"><strong>Search Kernel </strong>Exploits Here</a>' %}

{% include alert warning='<strong>Unquoted Service Path</strong><br>enumeration command:<br>
<code>wmic service get name,displayname,pathname,startmode 2>nul |findstr /i "Auto" 2>nul |findstr /i /v "C:\Windows\\" 2>nul |findstr /i /v """</code><br><br><a href="https://hacking-resources.com/privesc-master/windows-unquoted">List of applications that will possibly have this issue click here </a><br>Check Permissions:

<code>icacls "C:\Program Files\*" 2>nul | findstr "(F)" | findstr "Everyone"<br><br>
icacls "C:\Program Files (x86)\*" 2>nul | findstr "(F)" | findstr "Everyone"<br><br>
icacls "C:\Program Files\*" 2>nul | findstr "(F)" | findstr "BUILTIN\Users"<br><br>
icacls "C:\Program Files (x86)\*" 2>nul | findstr "(F)" | findstr "BUILTIN\Users"</code>' %}

{% include alert terminal='Linux' %}

{% include alert warning='Coming Soon' %}





	
{% include share.html %}	
	
	
