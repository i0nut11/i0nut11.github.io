---
title: "THM-SOURCE Writeup"
date: 2022-04-18T05:21:45-04:00
draft: false
---

TryHackMe-Source: Exploit a recent vulnerability and hack Webmin, a web-based system configuration tool

10.10.38.68 - > source.thm
I'm going to start the challenge by scanning the ip with nmap as in every challenge.

![image1](/images/image1.png)

The output:
Port 22 for ssh and 10000 is the default port for Webmin
And the link would be https://10.10.38.68:10000

![image2](/images/image2.png)

Unfortunately we don't know the username and password to ssh and webmin and I tried to search directories with gobuster, but nothing ☹.

![image3](/images/image3.png)

The last option was to look for an exploit on Metasploit.

![image4](/images/image4.png)

And yep, there are more vulnerabilities, and the exploit which I used is 5 “exploit/linux/http/webmin_backdoor”

![image5](/images/image5.png)

And now is need to set the LPORT, RHOSTS and ssl to true

![image6](/images/image6.png)

and to run the exploit, simply type run or exploit
-to have a stable shell we need to run the following commands 
echo "import pty; pty.spawn('/bin/bash')" > /tmp/anyname.py
python /tmp/filename.py
 Now we got the shell, and all we need to do now is to find the flags.

![image7](/images/image7.jpg)

