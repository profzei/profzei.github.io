---
title: Installing ICM profile on macOS
layout: post
use_code: true
excerpt: How to load a display calibration ICC-ICM Profile using the Mac
---

## Credits

*   [TrueColor](https://truecolor.us/tutorials/installing-icc-profiles-mac/)

## USB port limit patches and USBInjectAll.kext

Default ICC Profile Location: ```/Library/ColorSync/Profiles/Displays```
Some third-party apps (like screen dimming) will need to be disabled before loading a new ICC-ICM Profile 
(or else the computer will need to be restarted afterwards for the changes to take effect).

1.	**ColorSync Utility**: 
	- Press Command + Spacebar to open spotlight (default shortcut). 
	- Type “ColorSync Utility” and open the application.
2.	**Apply ICC-ICM Profile**:
	- Go to the “Devices” tab and select your display. 
	- Under “Current Profile”, select “Other”. 
	- Locate the ICC Profile and select it.
3.	**Login Screen: Note**: This is an optional step to load the ICC Profile to the computer’s login screen. 
	- Press Command + Spacebar to open spotlight (default shortcut). 
	- Type “Directory Utility” and open the application. 
	- Unlock the application using your administrator’s password. 
	- Select Edit > “Enable Root User”. 
	- Create a new password for the root account. 
	- Switch users and log in as “Other”. 
	- Type in “root” as the username and enter your newly created password. 
	- Repeat Steps 1-2 and apply the ICC Profile in the root account, then log out. 
	- Back in your regular user account, open the “Directory Utility” application again and unlock it. 
	- Finally, select Edit > “Disable Root User”.
