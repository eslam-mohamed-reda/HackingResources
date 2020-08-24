---
layout: page
title:  "How to Bypass SSL Pinning"
header: no
subheadline:  "Android"
teaser: "So you can start testing."
categories:
    - Mobile-Hacking
breadcrumb: true
sidebar: right
tags:
    - Android
---
### What is SSL/certificate pinning?
<br>

<b>Pinning is the process of associating a host with their expected X509 certificate or public key. It’s a technique used by apps to defend against multiple attacks including MiTM attacks and identity theft attacks. In this context, pinning is a term that refers to the process of authenticating the identity of a host (provided by a remote server in the form of an SSL certificate) against a local, trusted copy of the legitimate certificate. Therefore, a connection with the remote server will only be established if the server can prove its identity by means of a certificate that matches the app's expectations.</b><br>

For you to start testing applications one of the ways is to intercept the requests using a proxy like <b>(Burp suite, ZAP, etc.)</b>. For that to happen properly you need to get the app to trust the self-signed certificate provided by the used proxy but despite that these certificates can be trusted by the devices they will not match the pinned certificate that the app expects. So if you install the proxy certificate properly on the device you still need to figure out a way to bypass SSL pinning for the app. Let’s have a look at different ways to accomplish that:

*	#### <mark>Adding a Custom CA to the User Certificate Store</mark>

The first way to avoid SSL errors is to have a valid trusted certificate. 

Android has two built-in certificate stores for CAs trusted by the operating system – the system store (pre-installed CAs) and the user store (user-installed CAs).
By default, secure connections from all apps trust the pre-installed system CAs, and apps targeting Android 6.0 (API level 23) and lower also trust the user-added CA store by default. So if Android Version is 6.0 or less the applications will trust certificates we add to the user store but later versions won’t. 

And knowing the fact that some applications only run on certain versions of Android so we know above way won't work unless we edit the application to target Android version 6.0 or lower we can do that by editing manifest element in the file AndroidManifest.xml and changing 'platformBuildVersionCode' attribute to API level 23

`<manifest xmlns:android="http://schemas.android.com/apk/res/android" package="com.test.app" platformBuildVersionCode="23">`

*For tools to reverse the app and edit the file check <a href="https://hacking-resources.com/Android-Applications-Security.html">Android Application Resources</a>*

When the application is repackaged with this updated manifest, it will trust the user-added CA store.

But if the application must run on specific platform, According to https://developer.android.com/training/articles/security-config.html we can define specific trust anchors in the `/res/xml/network_security_config.xml` configuration file of the APK. For example, the following file defines a new trusted CA that needs to be stored at `/res/raw/my_ca` 

~~~
<?xml version="1.0" encoding="utf-8"?>
<network-security-config>
    <domain-config>
        <domain includeSubdomains="true">example.com</domain>
        <trust-anchors>
            <certificates src="@raw/my_ca"/>
        </trust-anchors>
    </domain-config>
</network-security-config>
~~~

If the application is only validating that the presented certificate is valid, this way will allow you to intercept the app’s traffic.

*	####	<mark>Frida</mark>

Frida is a tool that let you inject scripts to native apps to modify the application behavoir and make dynamic test in real time.

The first thing you need to do is get Frida, there are two parts to it the first part is the frida-tools, which you can install on your machine with the next command:

`pip install frida-tools`

The second part is an executable file that you have to download and copy into your virtual device. 

you can download it from <a href="https://github.com/frida/frida/releases">here</a> then decompress it.

connect to your device using adb

`./adb connect "IP address"`

<img src="https://i.imgur.com/HI8vSyG.jpg" alt="connecting to device">

Move the file into the virtual device (default path is /data/local/tmp/) replace `x.x.x` with the version you downloaded

`./adb push frida-server-x.x.x-android-x86 /data/local/tmp/frida-server`

<img src="https://i.imgur.com/HctYbeD.png" alt="connecting to device">

Give execution permissions to frida-server:

`./adb shell chmod 755 /data/local/tmp/frida-server`

And then go to the device to the above directory and run the frida-server with the next command:

`./frida-server &`

<img src="https://i.imgur.com/q7UTAqm.png" alt="connecting to device">

Now export the proxy certificate and push it to the device

`./adb push burp.der /data/local/tmp/burp.crt`

Then download <a href="https://codeshare.frida.re/@pcipolloni/universal-android-ssl-pinning-bypass-with-frida/">frida ssl pinning bypass script</a> and use it as follows

`frida -U -f com.test.android -l sslpinning.js` com.test.android is the app you're testing

Done! The app should work smoothly with your proxy.

This method won’t work with applications that uses HSTS (HTTP Strict Transport Security).

#### Conclusion

Bypassing SSL pinning is a small part of pen testing mobile applications the methods above is just to get you familiar with how things work and you should find the method that works best for the app you're testing. Good Luck!

<br>
<br>

{% include share.html %}

<br>
<h6>References</h6>
*	<h8>Portswigger.net</h8>
*	<h8>netspi.com</h8>



### Related Posts 
{: .t60 }
{% include list-posts tag='Android' %}