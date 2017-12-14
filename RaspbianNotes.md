# Overview

Notes on the Raspbian OS (Stretch at time of writing) for the Raspberry Pi

# References

* [Raspbian Stretch download page](https://www.raspberrypi.org/downloads/raspbian/)

# Issues

## Unable to Connect to default mirror for apt-get

In attempting to install **vim** with **sudo apt-get install vim**, I received and error that it could not connect to **https://mirrordirector.raspbian.org/**.  To resolve I did the following

1. Edit **/etc/apt/sources.list**
2. Commented out the line for **https://mirrordirector.raspbian.org/**
3. Added **http://mirror.sjc02.svwh.net/raspbian/raspbian/**, matching the same syntax for the command as the one I commented out.  I got this mirror from list at [Raspbian Mirrors](http://www.raspbian.org/RaspbianMirrors)
4. Ran **sudo apt-get dist-upgrade** to update the sources
5. Ran **sudo apt-get update**
6. Successfully re-ran **sudo apt-get install vim**
