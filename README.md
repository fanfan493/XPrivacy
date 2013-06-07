XPrivacy
========

Privacy manager using the [Xposed framework](http://forum.xda-developers.com/showthread.php?t=1574401)

Module to return no or fake data for any application, simply managed from the *Manage apps* menu.

Permissions
-----------

Currently implemented:

* APN info
* Boot start (0.7)
* Browser (bookmarks, searches, etc)
* Calendar
* Contacts
* Identification (Android ID, Wi-Fi MAC address)
* Location (coarse/fine, cell location/info)
* Messages (SMS/MMS, voicemail: **untested**, ICC SMS)
* Phone (call log, in/outgoing/voicemail number, phone ID/number, subscriber ID, SIM info, ISIM, IMPI, IMPU, MSISDN, network details)
* Take photos (Media)
* Record audio (Media)
* Record video (Media)
* Accounts (auth token)
* Read sdcard (revoke permission)
* Restriction management
* Batch edit restrictions
* Default restrict new apps

Planned:

* System log
* CM10.1 support

**Tested with CyanogenMod 10**

Reported to work with CyanogenMod 10.1 at least partly.

Installation
------------

* Root your device
* **Make a backup**
* Install the [Xposed framework](http://forum.xda-developers.com/showthread.php?t=1574401)
* Install XPrivacy from [here](http://goo.im/devs/M66B/xprivacy)
* Enable XPrivacy from the Xposed Installer app
* Flash the Xposed fix from [here](http://goo.im/devs/M66B/xprivacy) **CM10 only**
* Reboot

Usage
-----

* Select *Manage apps* from the main menu
* Select an app
* Press the XPrivacy button

To see it in action: try disabling *Identification* for [Android Id Info](https://play.google.com/store/apps/details?id=com.bzgames.androidid)
or try disabling *Contacts* for the Contacts app.

**Applying some restrictions requires an app restart**

Enabling storage restriction means blocking access to external storage (typically the SD card).
Because of the nature of this restriction, there is no usage data for this restriction.
All other restrictions have usage data and send no or fake data.
The only exception is boot complete: this is not really a restriction,
but makes it possible to block an application for doing things when the system starts.

Frequently asked questions
--------------------------

* Will you restrict internet access? No, you can use a firewall app, like [AFWall+](https://play.google.com/store/apps/details?id=dev.ukanth.ufirewall).
* Will you block outgoing SMS/MMS, the iptables command or force online state? No, XPrivacy is about restricting information, not about blocking actions.
* Will you make it possible to enter fake information? No, I want to keep things as simple as possible for maximum stability.
* Which functions are exactly restricted? See [here](https://github.com/M66B/XPrivacy/blob/master/src/biz/bokhorst/xprivacy/XPrivacy.java).

Similar solutions
-----------------

* [PDroid](http://forum.xda-developers.com/showthread.php?t=1357056)
* [PDroid 2.0](http://forum.xda-developers.com/showthread.php?t=1923576)
* [OpenPDroid](http://forum.xda-developers.com/showthread.php?t=2098156)

Developers
----------

To restrict new info:

* Find the package/class/method that exposes the info (look into the Android documentation/sources)
* Figure out a way to get a context (see existing code for examples)
* Create a class that extends [XHook](https://github.com/M66B/XPrivacy/blob/master/src/biz/bokhorst/xprivacy/XHook.java)
* Hook the method in [XPrivacy](https://github.com/M66B/XPrivacy/blob/master/src/biz/bokhorst/xprivacy/XPrivacy.java)
* Write a before and/or after method to restrict the info
* Do a [pull request](https://help.github.com/articles/using-pull-requests) if you want to contribute

License
-------

GNU General Public License version 3

Copyright (c) 2013 [Marcel Bokhorst](http://blog.bokhorst.biz/about/)

This program is free software; you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation; either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program; if not, write to the Free Software
Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA  02110-1301  USA
