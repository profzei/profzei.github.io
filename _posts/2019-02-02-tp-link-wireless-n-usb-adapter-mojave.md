---
title: TP-Link 300Mbps Mini Wireless N USB Adapter on macOS Mojave
layout: post
use_code: true
excerpt: Here is a brief summary of how I set up a working TL-WN823N v3 Wireless N USB adapter on Mojave.
---

## Credits

*   [Wireless USB Adapter Clover GitHub Rep](https://github.com/chris1111/Wireless-USB-Adapter-Clover)
*   [TP-Link Mini Scheda Wireless N300 USB TL-WN823N](https://www.tp-link.com/it/products/details/cat-11_TL-WN823N.html)

## Overview

* * *

*   300Mbps wireless speed ideal for smooth HD video, voice streaming and online gaming
*   Mini-sized design for convenient portability with a reliable high performance
*   SoftAP Mode – Turn a wired internet connection to a PC or Laptop into a Wi-Fi hotspot
*   Easily setup a secure wireless connection with one-touch WPS button

## Download latest release 

- [Wireless USB Adapter Clover](https://github.com/chris1111/Wireless-USB-Adapter-Clover)

## Install 

* * *

>You need a UEFI or ESP Clover installation to use this program, this does not install Clover, 
>it will install only both kext RtWlanU1827.kext, RtWlanU.kext in the Other folder.

![]({{ site.baseurl }}/images/mojave/tp-link-wireless-install.png)

This driver runs for macOS Mojave 10.14.x . The system is required to reboot after the driver is installed, so please 
close all the other applications before installing this software. After the system boots up and you enter the system, 
please follow the following steps to configure the network:
- Connect to the WLAN from the status bar Icons.
- Select the **System Preferences** from the System Menu.
- Select and launch the **Network** item in the **System Preferences** folder.
- From the _Configure_ list, select the correct adapter and configure it.
- Configure the settings.
- Click the _Save_ button.

![]({{ site.baseurl }}/images/mojave/tp-link-wireless-configure.png)