---
title: Intel Power Gadget & macOS freezes after login
layout: post
use_code: true
excerpt: How to fix the issue
---

![]({{ site.baseurl }}/images/hackbook/intel-power-gadget.png)

## How to fix the issue

When you install or update Intel Power Gadget (IPG) on Catalina, setup fails, opens the window that says macOS is behaving badly and 
asks you to open Terminal and enter ```sudo touch /Library/Extensions``` and then restart.
After booting macOS, it freezes right after login.
It's awful because you don't get any kernel panic (KP) warning and there is no indication about what causing it. Googling helped to identify the cause and other guides to activate ```r / w mode``` properly and remove the kext.

Here how to fix the issue:

1.	**Reset and boot into Single User Mode**
	- You can do so by pressing ```space bar``` in Clover boot screen then select Single User (```-s```).
	- You can also add boot flag ```-s```. Since this issue does not only affect Hackintosh, Macintosh users can boot into ```Single User Mode``` by holding down ```COMMAND + S``` keys together right after turning their Mac on.
2. 	**In Single User Mode**
	- type ```mount -uw /```
	- then type ```mount -uw /System/Volumes/Data```
	- now we'll go into /L/E ```cd /Library/Extensions```
	- delete the offending kext ```rm -rf EnergyDriver.kext```
	- clear the kext cache ```sudo rm -rf /Library/Caches/*```
	- and finally restart ```shutdown -r now```

Now you can boot into macOS without freezing.



