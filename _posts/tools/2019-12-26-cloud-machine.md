---
layout: page
subheadline: 
title:  "How To Build Your Cloud Pen Testing Machine"
header: no
subheadline:  "Tools"
teaser: "Hack from the cloud"
breadcrumb: true
tags:
    - tools
categories:
    - tools
image:
    thumb: mrrob.jpg
    title: 
    caption_url: http://hacking-resources.com
---

<p align="center">
  <img src="https://raw.githubusercontent.com/eslam-mohamed-reda/HackingResources/master/images/mrrob.jpg">
</p>

<p>As a penetration tester or security professional you always consider enhancing your tools to save effort, time and to increase effectiveness of what you do. One of the ways to do that is to have your own cloud ready to engage machine. </p>
<p><strong>Why?</strong></p>
<ul>
<li>Control over bandwidth and power.</li>
<li>Privacy for your own network. You will use it at minimum.</li>
<li>Always available from any location.</li>
<li>You can leave your tools running safely (with cautious).</li>
<li>Perfect for web and external pen testing you can easily start (reverse shell listener, web server, FTP).</li>
</ul>
<p><strong>Where and How?</strong></p>
<p>Of course it depends on which environment you’re comfortable with and which platform will allow you to perform pen testing from their infrastructure. But there are some platforms that are known to do so and checking pen testing community feedback I think the best with no specific order are:</p>
<ul>
<li><a href="https://www.kali.org/news/kali-linux-in-the-digitalocean-cloud/" target="_blank">DigitalOcean</a></li>
<li><a href="https://aws.amazon.com/marketplace/pp/B01M26MMTT" target="_blank">AWS</a></li>
<li><a href="https://blogs.msdn.microsoft.com/azuresecurity/2016/08/29/pen-testing-from-azure-virtual-machines/" target="_blank">MS Azure</a></li>
<li><a href="https://www.vultr.com/" target="_blank">Vultr</a></li>
<li><a href="https://www.linode.com/distributions/" target="_blank">Linode</a></li>
<li><a href="https://onehostcloud.hosting/kali-linux-vps-hosting/" target="_blank">Onehostcloud</a></li>
</ul>
<p><strong>Gearing up your machine:</strong></p>
<p>Before you start using the machine make sure you don’t get hacked while hacking. Start hardening the system, <a href="https://kali.training/lessons/7-securing-and-monitoring-kali/" target="_blank">Kali security training.</a></p>
<p>I chose Kali Linux as it’s the most common pen testing OS. But you can always use another OS and add the tools on it.</p>
<p>In addition to tools already on kali check below ones to gear it up.</p>
<p><strong>Recon tools:</strong></p>
<p><a href="https://hacking-resources.com/Red-Team-Arsenal.html#web-penetration-testing-tools" target="_blank">Hacking resources tools list</a></p>
<p>You will need some configuration to get it up and running for example you need to <a href="https://github.com/lanmaster53/recon-ng-marketplace/wiki/API-Keys" target="_blank">add your API keys </a> to recon-ng to make it more effective.</p>
<p>After adjusting configuration of individual tools you can automate your reconnaissance by tools like:</p>
<ul>
<li><a href="https://github.com/leebaird/discover" target="_blank">Discover</a></li>
<li><a href="https://github.com/EdOverflow/megplus" target="_blank">megplus</a></li>
<li><a href="https://github.com/nahamsec/lazyrecon" target="_blank">lazyrecon</a></li>
</ul>
<p><strong>Exploitation tools:</strong></p>
<p>Update OS and update databases of tools like Metasploit, SQLmap etc.</p>
<p>Keep your payload files ready to go and download:</p>
<ul>
<li><a href="https://github.com/swisskyrepo/PayloadsAllTheThings" target="_blank">PayloadAllThings</a></li>
<li><a href="https://github.com/danielmiessler/SecLists" target="_blank">SecLists</a></li>
<li><a href="http://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet" target="_blank">Pentestmonkey</a></li>
</ul>
<p><strong>Privilege escalation: </strong></p>
<p><a href="https://hacking-resources.com/Red-Team-Arsenal.html#privilege-escalation" target="_blank">Download </a> privilege escalation enumeration scripts to be ready to push to targets.</p>
<p><strong>Additional services:</strong></p>
<p>Working on external network is more exposed than working on internal networks. Here are some tips to keep in mind for any pen test in general:</p>
<ul>
<li>If you’re planning to host some payloads using web service.
Make sure you restrict access and harden the web server and keep it running only while executing the attack.
</li>
<li>Use secure services to transfer files such as SFTP.</li>
<li>Use encrypted shells with authentication.</li>
<li>Be very careful with customer data and make sure you delete all files and traces on your machine after the engagement.</li>
</ul>

<p><strong>Work Smart: </strong></p>
<p>What are your most common targets? I know you want your machine to be ready for work whatever the target 
But consider the machine performance and storage, Always keep or add tools relevant to what you’re usually attacking. Do not fill your machine with tools you will never use.
</p>
<br>
<p>Please feel free provide feedback about your cloud pen testing experience or additional ideas to make it more effective.</p>

{% include share.html %}

## Related Posts 
{: .t60 }
{% include list-posts tag='tools' %}
{% include chat.html %}
