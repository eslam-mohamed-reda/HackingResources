# SSRF

SSRF - Server Side Request Forgery attacks. The ability to create requests from the vulnerable server to intra/internet. Using a protocol supported by available URI schemas, you can communicate with services running on other protocols. Here we collect the various options and examples (exploits) of such interaction.

### SSRF Resources

* [HOW TO: SERVER-SIDE REQUEST FORGERY (SSRF)](https://www.hackerone.com/blog-How-To-Server-Side-Request-Forgery-SSRF){:target="_blank"}
		
* [SSRF - Server Side Request Forgery (Types and ways to exploit it) Part-1](https://medium.com/@madrobot/ssrf-server-side-request-forgery-types-and-ways-to-exploit-it-part-1-29d034c27978){:target="_blank"}
		
* [Escalating SSRF to RCE](https://generaleg0x01.com/2019/03/10/escalating-ssrf-to-rce/){:target="_blank"}
		
* [A New Era Of SSRF - Exploiting Url Parsers - Orange Tsai](https://www.youtube.com/watch?v=D1S-G8rJrEk){:target="_blank"}

* [How I Chained 4 vulnerabilities on GitHub Enterprise, From SSRF Execution Chain to RCE!](http://blog.orange.tw/2017/07/how-i-chained-4-vulnerabilities-on.html){:target="_blank"}

* [SSRF Protocol Smuggling in Plaintext Credential Handlers : LDAP](https://www.silentrobots.com/blog/2019/02/06/ssrf-protocol-smuggling-in-plaintext-credential-handlers-ldap/){:target="_blank"}

### SSRF Tools

* [Gopherus : This tool generates gopher link for exploiting SSRF and gaining RCE in various servers](https://github.com/tarunkant/Gopherus){:target="_blank"}

* [SSRF Proxy : Facilitates tunneling HTTP communications through servers vulnerable to Server-Side Request Forgery](https://github.com/bcoles/ssrf_proxy){:target="_blank"}

* [SSRFmap : Automatic SSRF fuzzer and exploitation tool](https://github.com/bcoles/ssrf_proxy){:target="_blank"}

[For Manual Testing SSRF Payloads List in here](https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/Server%20Side%20Request%20Forgery){:target="_blank"}

***

* ### Disclosed SSRF Reports
		
	* [Reverse Proxy misroute leading to steal X-Shopify-Access-Token header](https://hackerone.com/reports/429617){:target="_blank"}
		
	* [Bypass of the SSRF protection in Event Subscriptions parameter.](https://hackerone.com/reports/386292){:target="_blank"}
		
	* [SSRF in Exchange leads to ROOT access in all instances](https://hackerone.com/reports/341876){:target="_blank"}
		
	* [Blind SSRF on errors.hackerone.net due to Sentry misconfiguration](https://hackerone.com/reports/374737){:target="_blank"}
		
	* [Unauthenticated blind SSRF in OAuth Jira authorization controller](https://hackerone.com/reports/398799){:target="_blank"}
	
	* [Evaluating Ruby code by injecting Rescue job on the system_hook_push queue through web hook](https://hackerone.com/reports/299473){:target="_blank"}
		
	* [Blind SSRF in emblem editor (2)](https://hackerone.com/reports/265050){:target="_blank"}
		
	* [Upload profile photo from URL](https://hackerone.com/reports/713){:target="_blank"}
		
	* [Blind SSRF at https://chaturbate.com/notifications/update_push/](https://hackerone.com/reports/411865){:target="_blank"}
		
	* [Unauthenticated blind SSRF in OAuth Jira authorization controller](https://hackerone.com/reports/398799){:target="_blank"}
		
	* [SVG Server Side Request Forgery (SSRF)](https://hackerone.com/reports/223203){:target="_blank"}
	
	* [SSRF at iris.lystit.com](https://hackerone.com/reports/206894){:target="_blank"}
		
	* [Lack of input sanitization in Marketo form leads to execution of HTML in lead emails](https://hackerone.com/reports/220009){:target="_blank"}
		
	* [SSRF in api.slack.com, using slash commands and bypassing the protections.](https://hackerone.com/reports/381129){:target="_blank"}
		
	* [Infrastructure - Photon - SSRF](https://hackerone.com/reports/204513){:target="_blank"}
		
	* [SSRF in https://cards-dev.twitter.com/validator](https://hackerone.com/reports/178184){:target="_blank"}
		
	* [SSRF in proxy.duckduckgo.com via the image_host parameter](https://hackerone.com/reports/358119){:target="_blank"}

