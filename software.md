---
layout: content
title: "Software"
---
Instructions for the old bullseye can be found [here](/software-bullseye). 

Kiosk mode instructions for Chromium on Raspberry Pi is described [here](https://www.raspberrypi.com/tutorials/how-to-use-a-raspberry-pi-in-kiosk-mode/).

Righ click on the sound icon, click Device Profiles, set Audio Jack to `Off`. This will cause wayland to use HDMI when connected to output audio

You may use `sudo raspi-config` and set audio driver from `Pipewire` to `PulseAudio` in `Advanced Options -> Audio Config` if speakers don't work for you properly.

Right click on the speaker icon in the top right tool bar, then choose HDMI from the list of the available audio devices. You can do the same on the microphone icon to set the default mic. 

Set default locale to `en_US.utf-8` by running `sudo raspi-config` in `Localisation Options` section.

Make your HDMI display always connected, this will prevent [labWC from crashing](https://forums.raspberrypi.com/viewtopic.php?t=328439#p1969811). Add the following to the beginning of the line `/boot/firmware/cmdline.txt`:

```
video=HDMI-A-1:1920x1200@60D
```

Disable AV audio jack, this will prevent audio to go to AV jack (snd_bcm2835) rather than HDMI. Edit `/boot/firmware/config.txt` and [update the following parameter](https://www.raspberrypi.com/documentation/computers/config_txt.html#file-format):
```
dtparam=audio=off
```

You may need to enable HDMI-CEC in the settings of your TV e.g. on LG TVs.

Install cec-utils and wtype

cec-utils is used to control the TV using HDMI-CEC

Screen blanking needs to be disabled in Raspberry Pi configuration as it sometimes causes the speakers to have no voice.

wtype is used to press a key whenever needed

```
apt-get install cec-utils wtype -y
```

configure `/usr/local/bin/tv`

```
#!/bin/bash

case $1 in

on)
  echo 'on 0' | cec-client -s -d 1
;;
hdmi)
  echo 'as' | cec-client -s -d 1
;;
status)
  echo 'pow 0' | cec-client -s -d 1
;;
off)
  echo 'standby 0' | cec-client -s -d 1
;;
scan)
  echo 'scan' | cec-client -s -d 1
;;
*)
  echo "usage: tv status|on|hdmi|off|scan"
;;
esac
```
Install required python modules:

```
# create python virtualenv
python -m venv /home/pi/python
/home/pi/python/bin/pip install pychrome requests
```

Grant access of the pi user to cec hdmi port in /etc/udev/rules.d/50-udev-default.rules

```
KERNEL=="cec*", GROUP="pi", OWNER="pi"
```

Finally, you need to have access to the internet plan you use remotely to check the remaining amount of your internet package and recharge it if needed.

It’s best to connect your Brio camera and your other USB devices to a powered USB 3.0 hub such as TP-Link UH700 or TP-Link UH720 to avoid hitting the power limit in Raspberry Pi USB ports.

You may need to add the following to /boot/cmdline.txt if your [bluetooth mouse is laggy](https://forums.raspberrypi.com/viewtopic.php?t=84999#p600742).


```
usbhid.mousepoll=0
```

Check the Input/Output of your sound device in Chromium / VLC and ensure it is set to HDMI. Sometimes the default sound output is set to DVI which causes HDMI to have no sound.

To-check list

- Check if there is any difference in CPU usage among 30Hz vs 60Hz HDMI output
- Check the performance on 32bit OS vs 64bit
