---
title: Matebook X Pro Hackintosh Mojave Update 10.14.3
layout: post
use_code: true
excerpt: The Mojave 10.14.3 update is the third major update for macOS Mojave and is recommended by Apple for _All_ users.
---

<div class="row content-row">
	<div class="col-4 col-sm-2">
		<img src="{{ site.baseurl }}/images/mojave/matebook-x-pro-grey-resized.png">
	</div>
	<div class="col-4 col-sm-8">
		<p>This guide is currently for the i7 EU model with MX150. This blog post is <b>only</b> for personal reference.</p>
		<p>Official <b>Matebook X Pro</b> (MACH-W29) <a href="https://consumer.huawei.com/it/support/laptops/matebook-x-pro/">Support Page</a></p>
	</div>
</div>

> This update improves the security, stability, and compatibility of your Mac and includes the following enterprise content: 
> when making a file-sharing connection that uses a valid Kerberos TGT to authenticate, users are no longer prompted to enter credentials.

## Credits

*   [Hackintosh Mojave 10.14.3 Update Guide](https://hackintosher.com/guides/hackintosh-mojave-10-14-3-update-guide/)
*   [gnodipac886's guide for Mojave 10.14.3 Update](https://www.reddit.com/r/MatebookXPro/comments/am046y/its_february_bois_hackintosh_feb_update/)
*   [gnodipac886's GitHub Rep](https://github.com/gnodipac886/MatebookXPro-hackintosh)

## My Matebook X Pro's Hardware Configuration

*   CPU i7-8550U @ 1.8GHz
*   8 GB RAM
*   Nvidia GTX MX 150 / Intel UHD 620
*   3k Display @ 3000 x 2000
*   512 GB LiteON SSD

## Requirements

*   USB Mouse
*   USB flash drive for "_update stuffs_"

## Overview

* * *

Clover should handle the update automatically after rebooting, if not when the computer requests a reboot after installing 
in the app store you will have to manually select: **Install macOS from “Hackintosh”** to complete the update in Clover EFI Menu on boot.

**Nvidia Graphics**: Nvidia Drivers still aren’t available for macOS Mojave, however Nvidia has stated they’re working with Apple 
to make that happen, but that could take months.

**Graphics Injection**: since you are coming from an earlier version (Mojave 10.14 fresh install ) you need to adapt the new 
version graphics which is handled in clover by setting the proper property values and no longer using **Inject Intel**: it's mandatory 
setting **ig-platform-id** properly and updating graphical related kexts.

## Software

* * *

#### Latest kexts and GitHub Repository

- [AppleALC.kext](https://github.com/acidanthera/AppleALC/releases)
- [Lilu.kext](https://github.com/acidanthera/Lilu/releases)
- [WhateverGreen.kext](https://github.com/acidanthera/WhateverGreen/releases)
- [gnodipac886's GitHub Rep](https://github.com/gnodipac886/MatebookXPro-hackintosh)

#### Downloading Mojave 10.14.3 (Build 18D42)

The latest update of Mojave can be downloaded from the [App Store](https://itunes.apple.com/us/app/macos-mojave/id1398502828?mt=12) 
by going to the Mojave page or through **Software Update** in **System Preferences**.

Otherwise you can alternatively update by downloading and running the **.dmg** version of the update from Apple’s support page:
- [Mojave 10.14.3 Update](https://support.apple.com/kb/DL1991)
- [Mojave 10.14.3 Combo Update](https://support.apple.com/kb/DL1992)

## Install macOS Mojave 10.14.3 Update

* * *

You can manage to update the original installation to this updated (10.14.3) version just following these detailed steps:
- Download 10.14.3 update in MacOS - it will reboot the system and you will notice a new entry in Clover - Install MacOS
- Before proceeding, go to Clover options and set in Graphics - Platform id: `0x12345678`, Fake ID: `0x12345678`. Run Install MacOS option
- System will reboot. Again set options as in step 2, boot MacOS (install option should be gone now)
- System will start in basic version (everything very small, touchpad may be not working). Mount EFI partition (with app EFI mounter from tools) and replace `EFI/Clover` folder with the one from GitHub. Rename either config-toshiba.plist or config-liteon.plist to config.plist. Unmount EFI
- In terminal type "open /System/Library/Extensions" (without _double quotes_ "")- it will open Finder on this folder. Copy there file "AppleIntelCFLGraphicsFramebuffer.kext" from GitHub (it's in folder "Original Vanilla Kexts"). Run Kext Utility: don't do anything after running, just wait until it finishes (it repairs permissions for "/Library/Extensions" and "/System/Library/Extensions", updates the system cache files and syncs disk cache) and then click _Quit_
- Reboot - should work now ;).

## Hackintosh 10.14.3 USB Patch

* * *

You also need [USBInjectAll.kext](https://github.com/RehabMan/OS-X-USB-Inject-All) and a USB patch to get all USB/USB3 ports 
recognized and working. For proper USB3 speeds you may need to create your own SSDT following these steps:
- Mount EFI Partition with Clover Configurator
- Navigate to `/Volumes/EFI/EFI/Clover/`
- Right-click open **config.plist** with Clover Configurator
- Click **Kernel and Kext Patches** under **SECTIONS** of Clover Configurator
- Click the "**+**" button near the bottom to add this patch:
```
        Name*: com.apple.driver.usb.AppleUSBXHCI
        Find* [HEX]:83FB0F0F 83030400 00
        Replace* [HEX]: 83FB0F90 90909090 90​​
        Comment: USB 10.14.1+ by PMHeart
        MatchOS: 10.14.x
```
- Save **config.plist**
- Download the latest release of [Lilu.kext](https://github.com/acidanthera/Lilu/releases)
- Paste **Lilu.kext** into `/Volumes/EFI/EFI/Clover/kexts/Other`

![]({{ site.baseurl }}/images/mojave/Clover-Hackintosh-10.14.1-USB-Patch.png)

