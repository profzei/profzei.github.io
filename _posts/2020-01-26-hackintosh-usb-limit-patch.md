---
title: Hackintosh USB port limit patches for macOS Mojave 10.14.6
layout: post
use_code: true
excerpt: How to set in Clover config.plist USB port limit patches for macOS Mojave 10.14.6
---

## Credits

*   [MacOs86](https://www.macos86.it/topic/890-raccolta-lista-usb-xhci-patch-port-limit/)
*   [Tonymacx86 Mojave](https://www.tonymacx86.com/threads/usb-port-limit-patch-for-14-1-14-2-14-3-14-5-14-6.268893/)
*   [Tonymacx86 Catalina](https://www.tonymacx86.com/threads/macos-catalina-10-15-0-usb-port-limit-removal-patch.285098/)
*   [Hackintosher](https://hackintosher.com/forums/thread/list-of-hackintosh-usb-port-limit-patches-10-15-updated.467/)

## USB port limit patches and USBInjectAll.kext

For hackintoshing macOS requires USB patch to get all USB/USB3 ports recognized and working along with USBInjectAll.kext. 
In Apple hardware there is a port limit on the number of USB ports in macOS that can be gotten around by either: 
* making a custom DSDT for your specific motherboard
* or using the USB patch which is much simpler and easier for a first stage in hackintoshing.
What you will need to do is mount your EFI partition using a EFI mounter (like Clover Configurator) and add ```USBInjectAll.kext```.
Then, open up your ```config.plist``` located in ```EFI/Clover/```, click ''Kernel and Kext Patches'' under ''SECTIONS'' of 
Clover Configurator and, finally, add the patch by copy-pasting from the list below.

## List for Mojave 10.14.6
```
Name*: IOUSBHostFamily
Find*[Hex]: c20200e0 83fb0f
Replace*[Hex]: c20200e0 83fb3f
Comment: USB Port limit patch (1) 10.14.x (credit ydeng)
MatchOS: 10.14.x
```

```
Name*: com.apple.driver.usb.AppleUSBXHCI
Find*[Hex]: 4183ff0f 0f839404 0000
Replace*[Hex]: 4183ff3f 0f839404 0000
Comment: USB Port limit patch (2) 10.14.6
MatchOS: 10.14.x
```

```
Name*: com.apple.iokit.IOUSBHostFamily
Find*[Hex]: 83e30fd3 e34109df
Replace*[Hex]: 83e33fd3 e34109df
Comment: USB Port limit patch (3) 10.14.4+
MatchOS: 10.14.x
```

## Alternative List for Mojave 10.14.6
What is the difference from these which are well known? Take a look at the last one.
In case you wonder how to fix USB and have 100% it working at full speed of USB 2.0/3.0/3.1:
```
Name*: com.apple.iokit.IOUSBHostFamily
Find* [HEX]: 83FB0F0F
Replace* [HEX]: 83FB3F0F
Comment: USB Port limit patch (1) 10.14.6 DalianSky
MatchOS: 10.14.x
```

```
Name*: com.apple.iokit.IOUSBHostFamily
Find* [HEX]: 83E30FD3
Replace* [HEX]: 83E33FD3
Comment: USB Port limit patch (2) 10.14.6 DalianSky
MatchOS: 10.14.x
```

```
Name*: com.apple.driver.usb.AppleUSBXHCI
Find* [HEX]: 83FB0F0F
Replace* [HEX]: 83FB3F0F
Comment: USB Port limit patch (3) 10.14.6 DalianSky
MatchOS: 10.14.x
```

```
Name*: com.apple.driver.usb.AppleUSBXHCI
Find* [HEX]: 83FF0F0F
Replace* [HEX]: 83FF3F0F
Comment: USB Port limit patch (4) 10.14.6 DalianSky
MatchOS: 10.14.x
```

```
Name*: com.apple.driver.usb.AppleUSBXHCI
Find* [HEX]: 4183FF0F
Replace* [HEX]: 4183FF3F
Comment: USB Port limit patch (2) 10.14.6 PMHeart
MatchOS: 10.14.x
```

## List for Catalina 10.15.2
```
Name*: com.apple.iokit.IOUSBHostFamily
Find*[Hex]: 83FB0F0F
Replace*[Hex]: 83FB3F0F
Comment: USB Port limit patch (1) 10.15.x (credit Daliansky)
MatchOS: 10.15.x
```

```
Name*: com.apple.driver.usb.AppleUSBXHCI
Find*[Hex]: 83F90F0F
Replace*[Hex]: 83F93F0F
Comment: USB Port limit patch (2) 10.15.x (credit Daliansky)
MatchOS: 10.15.x
```