---
layout: page
title: "XSS"
meta_title: "XSS"
subheadline: "Cross site scripting"
teaser: "Cross-Site Scripting (XSS) attacks are a type of injection, in which malicious scripts are injected into otherwise benign and trusted websites. XSS attacks occur when an attacker uses a web application to send malicious code, generally in the form of a browser side script, to a different end user."
header:
   image_fullwidth: "XSS.gif"
permalink: "/XSS/"
---
<p align="center">
  <img width="460" height="300" src="https://raw.githubusercontent.com/eslam-mohamed-reda/hacking-resources/master/media/XSS.gif">
</p>

Cross-Site Scripting (XSS) attacks are a type of injection, in which malicious scripts are injected into otherwise benign and trusted websites. XSS attacks occur when an attacker uses a web application to send malicious code, generally in the form of a browser side script, to a different end user.

> #### Getting Your XSS to Work
[Turning self XSS to reflected](https://eredasecurity.wordpress.com/2018/03/07/getting-your-xss-to-work/){:target="_blank"}

> #### Brute XSS blog
[Some good resources for XSS](https://brutelogic.com.br/blog/){:target="_blank"}

## **XSS Tools:**

### [Brute XSS](https://github.com/rajeshmajumdar/BruteXSS){:target="_blank"}
GUI Tool written in Python

#### [XSS-Radar](https://github.com/bugbountyforum/XSS-Radar){:target="_blank"}
A Chrome extension for finding XSS

#### [domxssscanner](https://github.com/yaph/domxssscanner){:target="_blank"}
A tool to find DOM based XSS


[For Manual Testing you can use payloads in here](https://github.com/eslam-mohamed-reda/hacking-resources/blob/master/XSS%20Payloads){:target="_blank"}

***

* ### Disclosed XSS Reports

	* #### Disclosed Reflected XSS Reports
		
		* [XSS in $shop$.myshopify.com/admin/ via twine template injection in "Shopify.API.Modal.input" method when using a malicious app](https://hackerone.com/reports/217790){:target="_blank"}
		
		* [xss filter bypass [polldaddy]](https://hackerone.com/reports/264832){:target="_blank"}
		
		* [Cross-Site Scripting Reflected On Main Domain](https://hackerone.com/reports/104917){:target="_blank"}
		
		* [XSS on codex.wordpress.org](https://hackerone.com/reports/104559){:target="_blank"}
		
		* [https://polldaddy.com storage.swf XSS](https://hackerone.com/reports/9522){:target="_blank"}
		
		* [Content spoofing and potential Cross-Site Scripting vulnerability on www.hackerone.com](https://hackerone.com/reports/374919){:target="_blank"}
		
		* [[marketplace.informatica.com] Search XSS](https://hackerone.com/reports/200034){:target="_blank"}
		
		* [[account.mail.ru] XSS на странице восстановления пароля](https://hackerone.com/reports/360787){:target="_blank"}
		
		* [Reflected XSS of bbe-child-starter Theme via "value"-GET-parameter](https://hackerone.com/reports/335735){:target="_blank"}
		
		* [XSS on redirection page( Bypassed)](https://hackerone.com/reports/316319){:target="_blank"}
		
		* [XSS *.myshopify.com/collections/vendors?q=](https://hackerone.com/reports/324136){:target="_blank"}
		
		* [Reflected XSS+CSRF on secure.lahitapiola.fi](https://hackerone.com/reports/314518){:target="_blank"}
		
		* [XSS account.mail.ru in state JSON script](https://hackerone.com/reports/344112){:target="_blank"}
		
		* [Reflected XSS on https://www.zomato.com](https://hackerone.com/reports/311639){:target="_blank"}
		
		* [Query parameter reordering causes redirect page to render unsafe URL](https://hackerone.com/reports/293689){:target="_blank"}
		
		* [Reflected XSS on $Any$.myshopify.com/admin](https://hackerone.com/reports/422707){:target="_blank"}
		
		* [Reflected XSS in *.myshopify.com/account/register](https://hackerone.com/reports/470206){:target="_blank"}
		
		* [[mercantile.wordpress.org] Reflected XSS via AngularJS Template Injection](https://hackerone.com/reports/230234){:target="_blank"}

	* #### Disclosed Stored XSS Reports

		* [Stored XSS via transloadit.com and imageproxy](https://hackerone.com/reports/216822){:target="_blank"}

		* [XSS when replying / forwarding to a malicious email on iOS](https://hackerone.com/reports/264177){:target="_blank"}
		
		* [Stored XSS Using Media](https://hackerone.com/reports/275386){:target="_blank"}
		
		* [ads.twitter.com xss](https://hackerone.com/reports/27511){:target="_blank"}
		
		* [Stored XSS on chaturbate.com (wish list)](https://hackerone.com/reports/425048){:target="_blank"}
		
		* [XSS in steam react chat client](https://hackerone.com/reports/409850){:target="_blank"}
		
		* [Stored XSS Deleting Menu Links in the Shopify Admin](https://hackerone.com/reports/263876){:target="_blank"}

		* [Persistent XSS on keybase.io via "payload" field in `/user/sigchain_signature.toffee` template](https://hackerone.com/reports/245296){:target="_blank"}

		* [XSS on $shop$.myshopify.com/admin/ and partners.shopify.com via whitelist bypass in SVG icon for sales channel applications](https://hackerone.com/reports/232174){:target="_blank"}

		* [Double Stored Cross-Site scripting in the admin panel](https://hackerone.com/reports/245172){:target="_blank"}

		* [[Markdown] Stored XSS via character encoding parser bypass](https://hackerone.com/reports/270999){:target="_blank"}

		* [Stored XSS in Pages SEO dialog Name field (concrete5 8.1.0)](https://hackerone.com/reports/230029){:target="_blank"}

		* [[demo.weblate.org] Stored Self-XSS via Editor Link in Profile](https://hackerone.com/reports/223331){:target="_blank"}

		* [Stored XSS in *.myshopify.com](https://hackerone.com/reports/241008){:target="_blank"}

		* [Stored XSS in Name field in User Groups/Group Details form](https://hackerone.com/reports/247521){:target="_blank"}

		* [Stored XSS on Add Event in Calendar](https://hackerone.com/reports/300532){:target="_blank"}

		* [Stored XSS On Wordpress Infogram plugin](https://hackerone.com/reports/287688){:target="_blank"}
		
		* [[gem server] Stored XSS via crafted JavaScript URL inclusion in Gemspec](https://hackerone.com/reports/289313){:target="_blank"}
		
		* [Stored XSS in the Custom Logo link (non-Basic plan required)](https://hackerone.com/reports/282209){:target="_blank"}
		
		* [Stored XSS in dev-ucrm-billing-demo.ubnt.com In Client Custom Attribute](https://hackerone.com/reports/275515){:target="_blank"}
		
		* [XSS in OLX.pl ("title" in new advertisement)](https://hackerone.com/reports/267473){:target="_blank"}
		
		* [stored xss in invited team member via email parameter](https://hackerone.com/reports/267177){:target="_blank"}
		
		* [Blind stored xss [parcel.grab.com] > name parameter](https://hackerone.com/reports/251224){:target="_blank"}
		
		* [Stored XSS in content when Graph is created via API](https://hackerone.com/reports/287562){:target="_blank"}
		
		* [Stored XSS in learnboost.com via the lesson[goals] parameter](https://hackerone.com/reports/300270){:target="_blank"}
		
		* [Javascript Payload reflected Back in Report Embed Code](https://hackerone.com/reports/284082){:target="_blank"}
		
		* [Stored Cross-Site scripting in the infographics using links](https://hackerone.com/reports/280495){:target="_blank"}
		
		* [Cross-site scripting in "Contact customer" form](https://hackerone.com/reports/294505){:target="_blank"}
		
	* #### Disclosed DOM XSS Reports

		* [DOM XSS vulnerability in search dialogue](https://labs.detectify.com/2015/02/20/finding-an-xss-in-an-html-based-android-application/){:target="_blank"}

		* [Persistent DOM-based XSS in https://help.twitter.com via localStorage](https://hackerone.com/reports/297968){:target="_blank"}
		
		* [Report Design Critical Stored DOM XSS Vulnerability](https://hackerone.com/reports/282909){:target="_blank"}
		
		* [DOM Based XSS in mycrypto.com](https://hackerone.com/reports/324303){:target="_blank"}
		
		* [DOM Based XSS charting_library](https://hackerone.com/reports/351275){:target="_blank"}
		
		* [OX Guard: DOM Based Cross-Site Scripting](https://hackerone.com/reports/164821){:target="_blank"}
		
		* [DOM Based XSS in www.hackerone.com via PostMessage](https://hackerone.com/reports/398054){:target="_blank"}
		
		* [Dom Based Xss](https://hackerone.com/reports/125498){:target="_blank"}
		
		* [DOM Based XSS In mercantile.wordpress.org](https://hackerone.com/reports/230435){:target="_blank"}
		
		* [Account Recovery XSS : Google](https://sites.google.com/site/bughunteruniversity/best-reports/account-recovery-xss){:target="_blank"}

















