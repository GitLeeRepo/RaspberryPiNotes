# Overview

Notes on the Raspbian OS (Stretch at time of writing) for the Raspberry Pi

# References

* [Raspbian Stretch download page](https://www.raspberrypi.org/downloads/raspbian/)

## My Other Notes

* [LinuxSecurityNotes](https://github.com/GitLeeRepo/LinuxSecurityNotes/blob/master/LinuxSecurityNotes.md#overview)
* [UbuntuNotes](https://github.com/GitLeeRepo/UbuntuNotes/blob/master/UbuntuNotes.md#overview)
* [DebianNotes](https://github.com/GitLeeRepo/DebianNotes/blob/master/DebianNotes.md#overview)

# Installation/Upgrades/Configurations

## Return to the Pi on 2018-10-24

Return to the Pi after almost one year, needed 325 upgraded packages.  Noted it is using **Raspian OS** which is based on **Debian Stretch** which is still current and which I currently use in a full OS VM.  I was disappointed that I hardly made any notes, with nothing on my install and software configurations.  It does have **gcc** on there, which I suspect I added, since it is rarely installed by default. I will now try to starting updating them.  

After **updates** applied, it informed me in the **UI** that some config files were changed and the old ones were backed up to **`~/oldconffiles/`** with most in the hiddent **`.config/`** subdirectory.  Didn't see anything in their I had configured.

## Software Installs

The following are installed:

* **gcc** -- **version: Raspbian 6.3.0** -- probably installed when I set it up back in **2018-11**
* **python 3.5.3** -- current version, pre-installed
* **ufw (uncomplicated firewall)** -- installed **2018-10-24**
  * installed with: **`**sudo apt-get install ufw`**
  * configured: **`sudo ufw allow proto tcp from 192.168.0.0/24 to any port 22`**

# Issues

## Unable to Connect to default mirror for apt-get **Approx 2017-11**

In attempting to install **vim** with **sudo apt-get install vim**, I received and error that it could not connect to **https://mirrordirector.raspbian.org/**.  To resolve I did the following

1. Edit **/etc/apt/sources.list**
2. Commented out the line for **https://mirrordirector.raspbian.org/**
3. Added **http://mirror.sjc02.svwh.net/raspbian/raspbian/**, matching the same syntax for the command as the one I commented out.  I got this mirror from list at [Raspbian Mirrors](http://www.raspbian.org/RaspbianMirrors)
4. Ran **sudo apt-get dist-upgrade** to update the sources
5. Ran **sudo apt-get update**
6. Successfully re-ran **sudo apt-get install vim**
