---
layout: content
title: "Software"
---
Disable analog audio port on Raspberrypi, and also disabe hdmi_cec_init to avoid the TV turning on when the Pi is restarted. Enable overclocking on the pi.

```
# Disable audio 
dtparam=audio=off

# Fix HDMI Audio and set HDMI to always on
# https://mlagerberg.gitbooks.io/raspberry-pi/content/3.4-HDMI-output.html
hdmi_force_hotplug=1
hdmi_drive=2

# disable CEC init
hdmi_ignore_cec_init=1

#uncomment to overclock the arm. 700 MHz is the default.
#arm_freq=800
over_voltage=6
arm_freq=2000
gpu_freq=700
```

You may also need to enable HDMI-CEC in the settings of your TV e.g. on LG TVs.

Disable xcompmgr composition manager to reduce screen tearing as mentioned [here](https://lemariva.com/blog/2020/08/raspberry-pi-4-video-acceleration-decode-chromium): 


```
sudo mv /etc/xdg/autostart/xcompmgr.desktop /home/pi/backup.xcompmgr.deskto
```

Install cec-utils and xautomation

cec-utils is used to control the TV using HDMI-CEC

Screen blanking needs to be disabled in Raspberry Pi configuration as it sometimes causes the speakers to have no voice.

xautomation is used to press a key whenever needed

```
apt-get install cec-utils xautomation -y
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

grant pi user to run the following commands in `/etc/sudoers.d/pi`

```
pi ALL=(ALL) NOPASSWD:SETENV: /usr/bin/xte
```

Install required python modules:

```
pip3 install selenium pychrome
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
