---
layout: post
title: "Brbbot: Full Malware analysis"
date: 2026-02-05 12:00:00 +0200
categories: [Malware Analysis]
---

## Brbbot 
functions as a trojan or bot, it can also be used as a backdoor.<br>
*sample hash: `f9227a44ea25a7ee8148e2d0532b14bb640f6dc52cb5b22a9f4fa7fa037417fa`* 

### Quick triage
by frisking strings, it gave me a pretty good idea about how the malware would behave.
![image](/assets/images/brbbot/s1.PNG)
![image](/assets/images/brbbot/s3.PNG)
a lot of networking-related strings. these `encode` ,`sleep` ,`exit` ,`conf` ,`file` ,`exec`. we will find out later that they're c2 cmds. 
<br>
<br>
![image](/assets/images/brbbot/s2.PNG)
beside, there were encryption-related functions, which means we will have to deal with later.

using procmon, here we can see persistency-related behaviors(setting reg keys etc..), besides that, creating this `brbbotconfig.tmp`.
![image](/assets/images/brbbot/procmon.PNG)

and it's most likely encrypted, but we will come to decrypting it later.
![image](/assets/images/brbbot/tmpfile.PNG)

also, while searching resources, i found this, it may be related to the `brbbotconfig.tmp` artifact i found earlier.
![image](/assets/images/brbbot/rcs.PNG)


### Network analysis & C2 communication
after a couple of minuets 
![image](/assets/images/brbbot/nt1.PNG)

### Code analysis & Capabilities & Deciphering artifacts

