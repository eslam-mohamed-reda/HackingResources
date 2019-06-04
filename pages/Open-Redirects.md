---
layout: page
title: "Open Redirects"
meta_title: "Open Redirects"
subheadline: ""
teaser: ""
header:
   image_fullwidth: ""
permalink: "/Open-Redirects"
---

<p align="center">
  <img width="460" height="300" src="https://raw.githubusercontent.com/eslam-mohamed-reda/hacking-resources/master/media/openredirect.gif">
</p>

Open redirection vulnerabilities arise when an application incorporates user-controllable data into the target of a redirection in an unsafe way. An attacker can construct a URL within the application that causes a redirection to an arbitrary external domain.


* **tools**

  * [Open-Redirection-Scanner by KendoClaw1](https://github.com/KendoClaw1/Open-Redirection-Scanner/){:target="_blank"}




* **Possible Vulnerable Parameters**

    dest=

    continue=

    redirect=

    url=

    window=

    next=

    ?next=

    ?url=

    /redirect/

    /cgi-bin/redirect.cgi?

    ?view=

    login?to=



* [For Manual Testing](https://github.com/eslam-mohamed-reda/hacking-resources/blob/master/Open%20redirection%20fuzzing%20list){:target="_blank"}

* [Referer Open Redirect POC](https://github.com/eslam-mohamed-reda/hacking-resources/blob/master/Referer%20Open%20Redirect%20POC){:target="_blank"}  Use it to exploit vulnerable referer parameters


***

* ### Disclosed open redirect reports

  * [URL redirection flaw](https://hackerone.com/reports/2622){:target="_blank"}

  * [OAuth access_token stealing in Phabricator](https://hackerone.com/reports/3596){:target="_blank"}

  * [OAuth Stealing Attack (New)](https://hackerone.com/reports/3930){:target="_blank"}

  * [Header injection on rmaitrack.ads.vip.bf1.yahoo.com](https://hackerone.com/reports/6322){:target="_blank"}

  * [Open redirection on secure.phabricator.com](https://hackerone.com/reports/25160){:target="_blank"}

  * [Cross-domain AJAX request](https://hackerone.com/reports/97948){:target="_blank"}

  * [Trick make all fixed open redirect links vulnerable again](https://hackerone.com/reports/104087){:target="_blank"}

  * [Bypassing callback_url validation on Digits](https://hackerone.com/reports/108113){:target="_blank"}

  * [Identity Login Page Redirect Can Be Manipulated](https://hackerone.com/reports/243474){:target="_blank"}

  * [Link filter protection bypass](https://hackerone.com/reports/291750){:target="_blank"}

  * [Open Redirect bypass and cookie leakage on www.lahitapiola.com](https://hackerone.com/reports/190188){:target="_blank"}

  * [Open Redirect (verkkopalvelu.lahitapiola.fi)](https://hackerone.com/reports/179328){:target="_blank"}

  * [[ecommerce.shopify.com] Invalidated redirection](https://hackerone.com/reports/175168){:target="_blank"}

  * [Open redirect in bulk edit](https://hackerone.com/reports/169759){:target="_blank"}

  * [Open redirect allows changing iframe content](https://hackerone.com/reports/165046){:target="_blank"}

  * [Open Redirection on Uber.com](https://hackerone.com/reports/119236){:target="_blank"}

  * [Open redirect using theme install](https://hackerone.com/reports/101962){:target="_blank"}

  * [[keybase.io] Open Redirect](https://hackerone.com/reports/87027){:target="_blank"}

  * [Interstitial redirect bypass / open redirect in https://hackerone.com/zendesk_session](https://hackerone.com/reports/111968){:target="_blank"}

  * [Open Redirect after login at http://ecommerce.shopify.com](https://hackerone.com/reports/55546){:target="_blank"}

  * [Open Redirect leak of authenticity_token lead to full account take over](https://hackerone.com/reports/49759){:target="_blank"}

  * [open redirect in rfc6749](https://hackerone.com/reports/26962){:target="_blank"}

  * [Facebook Takeover using Slack using 302 from files.slack.com with access_token](https://hackerone.com/reports/6017){:target="_blank"}

  * [Redirect while opening links in new tabs](https://hackerone.com/reports/23386){:target="_blank"}

  * [(BYPASS) Open Redirect after login at http://ecommerce.shopify.com](https://hackerone.com/reports/155222){:target="_blank"}

  * [https://windsor.shopify.com/ takeover](https://hackerone.com/reports/150374){:target="_blank"}

  * [[apps.shopify.com] Open Redirect](https://hackerone.com/reports/160047){:target="_blank"}
  
  * [Open redirects that matter : Google open redirect](https://sites.google.com/site/bughunteruniversity/best-reports/openredirectsthatmatter){:target="_blank"}
  
  
{% include share.html %}
