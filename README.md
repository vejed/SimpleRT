# SimpleRT
Reverse [Tethering](https://en.wikipedia.org/wiki/Tethering) utility for Android.

Allows you to share your computer's internet connection with your Android device via a USB cable.

Development is still in progress, bugs and errors can occur.

### No root, no adb required!

## This is multi-tethering version. Allows to connect several android devices to one Linux (only linux supports at this time) host into one virtual network!

### Multi-tethering version supports only Linux host, OSX is in progress.

- Android part:

   Implemented as standalone service, no gui, no activities. Simplicity!

   Dependencies:
   - Android 4.0 and higher.

   Build system based on gradle + gradle experimental android plugin (supporting ndk). For build you need both sdk & ndk.
Create local.properties file in root dir, it should be looks like that:
   ```
   ndk.dir=/home/viper/Android/Sdk/ndk-bundle
   sdk.dir=/home/viper/Android/Sdk
   ```
   build:
   ```
   ./gradlew assembleDebug
   ```
   app/build/outputs/apk/app-debug.apk is your apk.

   #### There is already built multi-tether [apk](https://github.com/vvviperrr/SimpleRT/releases/download/1.1/simple-rt-1.1.apk.zip)
   
   <!---
   ## Now available in [f-droid](https://f-droid.org/repository/browse/?fdfilter=simplert&fdid=com.viper.simplert)
   --->

- Desktop part:

   Dependencies:
   - libusb-1.0
   - tun/tap kernel module. osx version is [here](http://tuntaposx.sourceforge.net/).

   #### FIrst of all, check out iface_up.sh and change LOCAL_INTERFACE, if you need.

   Makefile is universal for both linux and osx, just type make.

Usage:

- run console util as root
- connect your android device

First connection requires some trivial steps:

![First step](screens/accessory.png)

![Second step](screens/vpn.png)

![Third step](screens/connected.png)

Issues: Some apps do not recognize the reverse tethered internet connection due to ConnectivityManager policy. Just leave WiFi or 3g connection active, connection will go through SimpleRT anyway.

Partially used code from [linux-adk](https://github.com/gibsson/linux-adk), which is licensed under the GNU GPLv2 or later. This project is under the GNU GPLv3 or later, which is compatible with the license of linux-adk.

##### License: GNU GPL v3

```
SimpleRT: Reverse tethering utility for Android
Copyright (C) 2016 Konstantin Menyaev

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.
```
