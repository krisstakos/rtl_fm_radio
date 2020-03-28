# RTL SDR FM Player
Fork from: https://github.com/ktb83/rtl_sdr_fm_player/n
A simple GUI front end player for rtl_fm and RTL SDR FM Streamer.

### Description

Developed to be used on Raspbain with the official Rpi 7 inch touch screen in full screen mode, but should work with any Linux OS in a 800x480 window.

![gui](gui.png?raw=true)
## Prerequisites

### RTL-SDR
https://osmocom.org/projects/rtl-sdr/wiki/Rtl-sdr

Turns your Realtek RTL2832 based DVB dongle into a SDR receiver.
rtl_fm is part of this package.

For Raspbain you can install with apt.

```
      sudo apt install rtl-sdr
```   

### Python keyboard module

For now we’re using Pythons keyboard module to control the volume. Because of this dependency the program must be run with sudo. Maybe there is a better solution?
```
     sudo pip3 install keyboard
```

### RTL SDR FM Streamer
https://github.com/AlbrechtL/rtl_fm_streamer/

rtl_fm will work without any additional installation but it’s mono only as far as I can tell.
 RTL SDR Streamer provides stereo and seems, to me, to have better sound quality.
Couple options to set before make command if you have problems with the driver:
```
cmake ../ -DINSTALL_UDEV_RULES=ON -DDETACH_KERNEL_DRIVER=ON
```
To install you’ll have to build and make it.
```
	$ sudo apt-get install build-essential libusb-1.0-0-dev libev-dev cmake
	$ git clone https://github.com/AlbrechtL/rtl_fm_streamer.git
	$ cd rtl_fm_streamer/
	rtl_fm_streamer$ mkdir build
	rtl_fm_streamer$ cd build
	rtl_fm_streamer/build$ cmake ../
	rtl_fm_streamer/build$ make
	rtl_fm_streamer/build$ sudo make install
	rtl_fm_streamer/build$ sudo ldconfig
```

## Setup

Setup and settings are controlled via the settings.ini file.
You have to add your stations to this file manually. Read the comments, it’s easy.

## Usage 

From the command line cd into the cloned directory and enter
```
    sudo python3 rtl_sdr_player.py
```
