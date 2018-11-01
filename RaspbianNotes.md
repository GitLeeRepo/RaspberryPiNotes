# Overview

Notes on the Raspbian OS (Stretch at time of writing) for the Raspberry Pi

# References

* [Raspbian Stretch download page](https://www.raspberrypi.org/downloads/raspbian/)

## My Other Notes

* [LinuxSecurityNotes](https://github.com/GitLeeRepo/LinuxSecurityNotes/blob/master/LinuxSecurityNotes.md#overview)
* [UbuntuNotes](https://github.com/GitLeeRepo/UbuntuNotes/blob/master/UbuntuNotes.md#overview)
* [DebianNotes](https://github.com/GitLeeRepo/DebianNotes/blob/master/DebianNotes.md#overview)

# Kit Purchased

* [CanaKit Raspberry Pi 3 Complete Starter Kit - 32 GB Edition](https://www.amazon.com/gp/product/B01C6Q2GSY/ref=oh_aui_search_detailpage?ie=UTF8&psc=1)
* Purchased: 2017-11-08
* For \$75 on Amazon
* 32 GB Micro SD Card (Class 10) -- pre-installed with NOOBS


# Installation/Upgrades/Configurations

## Micro SD Card Supported Formats

### Raspberry Pi and SDXC cards

The **Raspberry Pi's boot loader**, built into the GPU and non-updatable, **only has support for reading from FAT file systems** (both **FAT16** and **FAT32**), and is **unable to boot from an exFAT filesystem**. So if you want to use NOOBS on a card that is **64GB or larger**, you need to **reformat it as FAT32** first **before copying the NOOBS files** to it.


## Installed Raspbian (Full Desktop) -- on approx 2017-11-10

Installed **Raspbian (Full Desktop)** from the **NOOBS** installer on the **32GB Micro SD card** included in the kit.

Note this ends up being the same **SD card** mounted as the **file system** for the **Raspbian installation**

### Booting to NOOBS SD Card after OS Installed

It says **hold down the shift key** when booting (it briefly flashes across the screen when booting).  But I found I had to **rapidly tap shift** while booting to get to the **NOOBS utility**.  Pressing **Esc** will continue to **boot to the OS**.

### Selecting Boot Options from the raspi-config terminal utility

Entering the **`sudo raspi-config`** command brings up a text based menu.  **Option 3** is for the **Boot Options**

```bash
sudo raspi-config
```

**Initial Menu**:

```
1 Change User Password - Change password for the current user
2 Network Options- Configure network settings
3 Boot Options - Configure options for start-up
4 Localization Options - Set up language and regional settings to match your location
5 Interfacing Options- Configure connections to peripherals
6 Overclock - Configure overclocking for your Pi
7 Advanced Options - Configure advanced settings
8 Update - Update this tool to the latest version
9 About raspi-config - Information about this configuration tool 
```

**Boot Options**:

```
B1 Desktop / CLI - Choose whether to boot into a desktop environment or the command line
B2 Wait for Network at Boot- Choose whether to wait for network connection during boot
B3 Splash Screen - Choose graphical splash screen or text boot
```

**B1 Desktop / CLI**:

```
B1 Console - Text console, requiring user to login
B2 Console Autologin - Text console, automatically logged in as 'lee' user
B3 Desktop - Desktop GUI, requiring user to login
B4 Desktop Autologin - Desktop GUI, automatically logged in as 'lee' user
```

### Booting to a Console (No Desktop)

It acts like it is going to go into the **GUI** since a couple of graphical screens pop up, but it does go to the **command line**

**Initial memory used comparison**:

* **Console** -- **46.7MB out of 923MB**
* **Desktop** -- **104MB of 923MB**

Some other **comparisons**:

* **odb1** -- **Debian Stretch** - **Azure** - minimum additional software installs
  * **127MB out of 1.88GB**
* **oub1** -- **Ubuntu 18.04** - **Azure** - minimum additional software installs
  * **206MB out of 1.86GB**
* **aub2** -- **Ubuntu 18.04** -- **Hyper-V** - **Desktop install** - **Docker running but no containers**
  * **1.83GB out of 7.83GB** 
* **aub3** -- **Ubuntu 18.04** -- **Hyper-V** - **Server install** - **Docker running but no containers**
  * **1.4GB out of 3.83GB** - after closing **Docker Containers**
  * **200MB out of 3.83GB**  - after **rebooting the system**
* **adb1** -- **Debian Stretch** -- **Hyper-V** -- **Desktop install** -- **No Docker** -- **Gnome biggest memory user**
  * **294MB out of 3.86GB** --  after **rebooting the system**
 **acn1** -- **CentOS** -- **Hyper-V** -- **Desktop install** -- **No Docker** -- **Gnome biggest memory user**
  * **454MB out of 3.68GB** --  after **rebooting the system**  

## Raspbian Stretch Lite Install 2018-11-01

### Started with

*  [**Sandisk Ultra 32GB Micro SD Card**](https://www.amazon.com/gp/product/B073JWXGNT/ref=oh_aui_detailpage_o00_s00?ie=UTF8&psc=1)
* **2018-10-09-raspbian-stretch-lite.img** file downloaded from [Raspbian Stretch download page](https://www.raspberrypi.org/downloads/raspbian/)

### Installed Etcher on my laptop

* **Downloaded Etcher** from [www.balena.io](https://www.balena.io/etcher/)
* Its a simple three step **flash** process
  * **Select** the **.img file** -- using the **2018-10-09-raspbian-stretch-lite.img**
  * **Insert Micro SD card** using an **adapter** to full sized SD card (comes with [**Sandisk Ultra 32GB Micro SD Card**](https://www.amazon.com/gp/product/B073JWXGNT/ref=oh_aui_detailpage_o00_s00?ie=UTF8&psc=1)
  * **Flash** the card -- straight forward but relatively slow process (probably 1.5 to 2 minutes to do the 32GB)

### Install on Pi

* Power down Pi
* **Remove the old Micro SD** card.  It is kind of hard to see, but the back of the case has a small notch, where the **micro sd** card is.  You need a good light to see it.
* **Insert new Micro SD** card.
* **Power on and let it boot**.  Nothing really to do, just wait for the command prompt.  Default login is **pi** with password **raspberry**.
* Type **passwd** to **change the password**
* Assign any **users** you want to use (refer to Linux/Debian docs).

## Return to the Pi on 2018-10-24

Return to the Pi after almost one year, needed 325 upgraded packages.  Noted it is using **Raspbian OS** which is based on **Debian Stretch** which is still current and which I currently use in a full OS VM.  I was disappointed that I hardly made any notes, with nothing on my install and software configurations.  It does have **gcc** on there, which I suspect I added, since it is rarely installed by default. I will now try to starting updating them.  

After **updates** applied, it informed me in the **UI** that some config files were changed and the old ones were backed up to **`~/oldconffiles/`** with most in the hidden **`.config/`** subdirectory.  Didn't see anything in their I had configured.

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
