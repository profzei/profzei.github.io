---
title: Installing CERN ROOT on macOS Mojave 10.14.x
layout: post
use_code: true
excerpt: How to install CERN’s ROOT data analysis framework on macOS Mojave 10.14.x
---

![]({{ site.baseurl }}/images/cern_root.png)

## Credits

*   [Installing CERN ROOT (2017)](http://tylern4.github.io/InstallRoot/)
*   [ROOT @ CERN](https://root.cern.ch/)

## ROOT

ROOT is very handy when trying to make plots and it is used by nuclear physicists, particle physicists and even 
some astronomers to store, view and report data.

## Dependencies

Fist thing to do it to install ROOT is to get the proper dependencies. Dependencies are the underlying programs a computer needs 
for building new programs. One of the most important ones we will need to install ROOT is _GCC_ (GNU Compiler Collection). 
As the name might imply _GCC_ is the collection of programs which are used to make the _C/C++_, _Objective-C_, _Fortan_ and other 
code compile so that it can be run on your computer. In order to install this and some other useful tools on macOS X you can use 
the **Xcode command line tools**. In order to install ROOT you _don’t need the full version of Xcode_, just a small portion of the 
tools which can be installed by opening a terminal and typing:

```
xcode-select --install
```
